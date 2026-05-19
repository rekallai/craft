# Job — Daily PR Summary

## Trigger

**Cron:** `0 17 * * 1-5` (every weekday at 5pm local)
**Posts to:** Slack `#engineering`

## Purpose

End each weekday with a one-message summary of what moved in `build/lighthouse-app/` that day, so the team gets a single-glance view of progress without having to scroll GitHub.

## Inputs

- GitHub PRs for `build/lighthouse-app/` opened, updated, merged, or closed in the last 24 hours
- The current MVP scope from `specs/product/mvp-scope.md` — used to tag PRs by area

## Output

A single Slack message in this format:

```
📦 Lighthouse — daily PR summary

Merged today (N)
  • #123 [reconciliation] Match partial-payment deposits — @priya
  • #124 [dunning] Add T-3 reminder template — @sam

Opened today (N)
  • #125 [billing] Stripe webhook retry on 5xx — @dom (needs review)

In flight (N)
  • #119 [auth] Magic-link sign-in (open 4d, last update yesterday) — @sam

Stale (>3 days no activity)
  • #112 [reconciliation] Surface ambiguous deposits UI — @priya
```

## Rules

- Group by status: merged → opened → in flight → stale.
- Tag each PR by area (reconciliation, dunning, billing, auth, marketing) using its files-changed paths.
- Always include PR author.
- Stale = no commit, comment, or review in 72 hours.
- If nothing moved, post: "📦 Lighthouse — quiet day, no PR activity."

## Don't

- Don't summarize PR contents beyond the title.
- Don't @-mention people unless they have a PR awaiting review (then mention the reviewer, not the author).
