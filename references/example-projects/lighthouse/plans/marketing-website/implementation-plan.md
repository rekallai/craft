# Marketing Website — Implementation Plan

## TLDR

Ship a four-page marketing site — Home, How it works, Pricing, About — built on Next.js with shadcn/ui, deployed on Vercel. Hero leads with "Get paid without chasing." Three feature cards mirror the three lines in `specs/marketing/value-proposition.md`. Hours-saved counter appears in the nav of the in-product app but is referenced in the homepage proof section. No CMS — copy lives in the repo. Live in 10 working days.

## Goals

- Get a visitor from landing to "Get started" click in under 30 seconds.
- Tell the positioning story end-to-end on the homepage alone — the other pages exist for visitors who want more.
- Zero CMS complexity. Marketing copy lives in the repo and ships with code.

## Non-goals

- Blog (deferred — not a wedge for MVP)
- Customer-logo strip (we don't have customers yet)
- Interactive product demos (later — start with screenshots)
- Localization

## Pages

### Home (`/`)
- Hero: "Get paid without chasing." Sub-hero from `value-proposition.md`. CTA: "Get started".
- Three-card feature strip mirroring the three positioning lines.
- Proof section: hours-saved counter screenshot + a single Maria K. quote ("It's like a tab open in my brain.")
- Footer CTA: "Get started" repeated.

### How it works (`/how`)
- Three-step illustrated walkthrough: 1) send, 2) follow up, 3) reconcile.
- Inline screenshots of the actual product.
- Link to pricing.

### Pricing (`/pricing`)
- Single tier for MVP: $24/month, includes ACH + card, 50 invoices/month.
- FAQ accordion underneath: "What if I send more than 50?", "What about taxes?", "Does it replace QuickBooks?" (no), etc.

### About (`/about`)
- Short. Founders. Why we exist. One paragraph each.

## Stack

- **Framework:** Next.js 16 (App Router, Cache Components)
- **Styling:** Tailwind + shadcn/ui
- **Hosting:** Vercel
- **Analytics:** Vercel Web Analytics + a single custom event for `cta_clicked`
- **Forms:** None on the marketing site itself — "Get started" links straight into the app sign-up.

## Milestones

| # | Milestone                                  | Days |
| - | ------------------------------------------ | ---- |
| 1 | Design tokens, shadcn setup, layout shell  | 1    |
| 2 | Home page (hero + features + proof)        | 2    |
| 3 | How it works                               | 1.5  |
| 4 | Pricing + FAQ                              | 1    |
| 5 | About                                      | 0.5  |
| 6 | Mobile QA + accessibility pass             | 2    |
| 7 | Vercel deploy + custom domain + analytics  | 1    |
| 8 | Buffer for review and copy tightening      | 1    |
|   | **Total**                                  | **10** |

## Risks

- **Copy drift.** If marketing copy diverges from `specs/marketing/value-proposition.md`, the positioning fragments. Mitigation: copy in the repo gets reviewed against the spec on every PR.
- **Hero CTA dead-ends.** If "Get started" links to a half-finished sign-up, conversions die. Don't ship the marketing site before the in-product MVP signup is golden-path-clean.
