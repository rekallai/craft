# Domain — Lighthouse

Glossary of terms that show up across the codebase, plans, and customer conversations. When in doubt about a word, look here first.

## Core invoicing

- **Invoice** — A request for payment issued by a business to a customer. In Lighthouse, an invoice has a unique number, a due date, line items, and a status (`draft`, `sent`, `viewed`, `paid`, `overdue`, `void`).
- **Line item** — A single billable entry on an invoice (description, quantity, unit price, tax).
- **Net N** — Payment terms meaning the full amount is due N days after the invoice date. "Net 30" is the most common.
- **Due date** — The calendar date by which payment is expected. Derived from issue date + payment terms.
- **Aging bucket** — How overdue an invoice is, in buckets: `current`, `1-30`, `31-60`, `61-90`, `90+`.

## Payments

- **ACH** — Automated Clearing House. Bank-to-bank transfers in the US, typically settling in 1–3 business days. Cheaper than cards.
- **Card payment** — Credit/debit card capture. Faster than ACH from the buyer's perspective, more expensive (~2.9% + $0.30).
- **Settlement** — The point at which money actually arrives in the recipient's bank account, distinct from the payment being initiated.
- **Reconciliation** — Matching incoming deposits to specific invoices.

## Dunning and follow-up

- **Dunning** — The process of communicating with customers about overdue invoices. A "dunning sequence" is an automated series of reminders.
- **Reminder cadence** — The schedule on which reminders are sent (e.g. 3 days before due, day of, +7, +14, +30).
- **Escalation** — Moving from automated reminders to a human-involved action (phone call, demand letter, collections).

## Lighthouse-specific

- **Workspace** — A single business's account. Workspaces are the top-level tenancy boundary.
- **Operator** — A human user inside a workspace. Roles: `owner`, `admin`, `member`.
- **Auto-pilot** — The feature set that handles sending, follow-up, and reconciliation without operator action. The product's center of gravity.
- **Surface** — A decision Lighthouse couldn't handle automatically that gets shown to the operator (e.g. "this $1,200 deposit doesn't match any open invoice — which one is it?").
