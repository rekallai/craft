# MVP Scope — Lighthouse

## Goal

Ship a product a small-business owner can sign up for, connect to a bank account, and use to send and collect on their first invoice — within 10 minutes of landing on the marketing site.

## Must

- Email + Google sign-up; workspace creation in one step
- Stripe-backed payment capture (card + ACH)
- Plaid bank-account connection for deposit reconciliation
- Create, send, and track a single invoice (PDF + hosted payment page)
- Automated 3-step dunning sequence: 3 days before due, day after due, +14 days
- Reconciliation: auto-match deposits to invoices when the amount and timing line up; surface ambiguous deposits for operator resolution
- Hours-saved counter on the dashboard

## Should

- Recurring invoices (weekly, monthly)
- Custom dunning schedules per customer
- Team members (additional operators on the workspace)
- CSV export of invoices and payments

## Won't (this version)

- Multi-currency
- Tax filing or sales-tax automation
- Accounting integrations (QuickBooks, Xero) — explicitly out of scope to protect the positioning
- Mobile app — web only, mobile-responsive
- Custom invoice templates / branding beyond logo + accent color
- Marketplace, public API, or third-party integrations

## Acceptance signal

A new user can complete the golden path in `prompts/qa/mvp-golden-path-acceptance-test.md` end-to-end in under 10 minutes with no operator help.
