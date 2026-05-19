# MVP Data Model — Lighthouse

## TLDR

Five core tables: `workspaces`, `operators`, `customers`, `invoices`, `payments`. One table for the dunning state machine: `reminders`. One for the reconciliation surface: `deposits`. No GL, no chart of accounts, no double-entry. Foreign keys are explicit; soft-deletes everywhere via `deleted_at`. Money is stored as integer cents in a single currency column to make multi-currency tractable later without a migration storm.

## Goals

- Support every behavior in `specs/product/mvp-scope.md` ("Must" section) and nothing more.
- Make multi-currency a future additive change, not a migration nightmare.
- Keep the reconciliation surface (ambiguous deposits) modeled as a first-class concept, not a side effect.

## Non-goals

- Recurring invoices (deferred to post-MVP)
- Multi-currency
- Multi-tenant beyond the workspace boundary
- Audit log (deferred — `created_at` / `updated_at` are sufficient for MVP)

## Tables

### `workspaces`
- `id` (uuid, pk)
- `name` (text)
- `created_at`, `updated_at`, `deleted_at`

### `operators`
- `id` (uuid, pk)
- `workspace_id` (uuid, fk → workspaces)
- `email` (text, unique within workspace)
- `role` (enum: `owner`, `admin`, `member`)
- `created_at`, `updated_at`, `deleted_at`

### `customers`
- `id` (uuid, pk)
- `workspace_id` (uuid, fk → workspaces)
- `name` (text)
- `email` (text)
- `default_terms_days` (int, default 30)
- `created_at`, `updated_at`, `deleted_at`

### `invoices`
- `id` (uuid, pk)
- `workspace_id` (uuid, fk)
- `customer_id` (uuid, fk → customers)
- `number` (text, unique per workspace — `INV-0001`)
- `status` (enum: `draft`, `sent`, `viewed`, `paid`, `overdue`, `void`)
- `issue_date`, `due_date` (date)
- `amount_cents` (bigint)
- `currency` (char(3), default `'USD'`)
- `line_items` (jsonb — denormalized, MVP only)
- `sent_at`, `viewed_at`, `paid_at` (timestamps, nullable)
- `created_at`, `updated_at`, `deleted_at`

### `payments`
- `id` (uuid, pk)
- `workspace_id` (uuid, fk)
- `invoice_id` (uuid, fk → invoices, nullable until reconciled)
- `amount_cents` (bigint)
- `currency` (char(3))
- `method` (enum: `card`, `ach`)
- `stripe_payment_id` (text)
- `received_at` (timestamp)
- `created_at`, `updated_at`

### `reminders`
- `id` (uuid, pk)
- `invoice_id` (uuid, fk → invoices)
- `kind` (enum: `pre_due_t3`, `post_due_t1`, `post_due_t14`)
- `scheduled_at` (timestamp)
- `sent_at` (timestamp, nullable)
- `canceled_at` (timestamp, nullable — set when invoice is paid before reminder fires)
- `created_at`, `updated_at`

### `deposits`
- `id` (uuid, pk)
- `workspace_id` (uuid, fk)
- `amount_cents` (bigint)
- `currency` (char(3))
- `received_at` (timestamp)
- `plaid_transaction_id` (text)
- `matched_invoice_id` (uuid, fk → invoices, nullable)
- `match_confidence` (float, 0–1)
- `surfaced_to_operator_at` (timestamp, nullable — set when confidence is below threshold)
- `resolved_at` (timestamp, nullable)
- `created_at`, `updated_at`

## Key decisions

- **`line_items` as `jsonb`, not a separate table.** Reduces joins for the MVP. We'll normalize later if reporting needs it.
- **Money as integer cents.** No floats. Single `currency` column on each money-holding table reserves the slot for future multi-currency without rewriting every row.
- **Soft delete via `deleted_at`.** All queries filter `WHERE deleted_at IS NULL`. Easier audit, easier undo, costs us nothing for MVP volume.
- **Reminders are pre-materialized.** When an invoice is sent, all three reminders are inserted with future `scheduled_at`. A worker fires them on schedule. Cancellation = set `canceled_at`. This is simpler than computing reminders on demand.
- **Deposits are first-class.** Even when matched cleanly, the `deposits` row exists for audit and for surfacing ambiguous cases. Don't collapse `deposits` into `payments`.

## Open questions

- Do we need a `customer_email_overrides` table for invoices sent to a different address than the customer default? Probably yes post-MVP. Deferring.
- Stripe payment-intent IDs vs Stripe charge IDs — going with payment-intent for forward-compatibility.
