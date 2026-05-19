# Skill — Code Review

## When to invoke

Before merging a PR into `build/lighthouse-app/`. Either manually (`/review`) or automatically on PR open.

## Inputs

- The diff being reviewed
- The PR description and title
- Relevant files in `specs/` (especially `domain.md` for terminology)
- The MVP scope in `specs/product/mvp-scope.md` — flag if the PR adds anything outside scope

## What to check

1. **Scope alignment.** Does this PR match what `specs/product/mvp-scope.md` says belongs in MVP? If it's adding something from the "should" or "won't" list, surface that as the first comment.
2. **Domain terminology.** Are domain terms used as defined in `specs/domain.md`? Flag inconsistencies (e.g. a variable named `late_invoice` when the domain term is `overdue`).
3. **Test coverage.** Every new behavior in `src/` should have a corresponding test. New API endpoints especially.
4. **Reconciliation correctness.** If the diff touches `src/reconciliation/`, run through the deposit-matching edge cases: partial payments, wire-fee deductions, deposits matching multiple invoices.
5. **Error handling at boundaries.** Stripe and Plaid responses can fail in surprising ways. New code calling them should handle network errors, rate limits, and the documented error codes.
6. **No surprise dependencies.** Flag any new package in `package.json` and ask whether it's necessary.

## Output format

Post a single PR comment with:

- **Verdict:** `approve`, `request-changes`, or `comment`
- **Scope check:** one line, e.g. "In MVP scope ✅" or "Adds recurring invoices — that's in 'should', not 'must'. Confirm with PM."
- **Findings:** bulleted list, most important first. Each finding cites the file and line.
- **Nits:** optional, separately bulleted, prefixed `nit:`.

## What to skip

- Style nits a formatter would catch (Prettier handles it)
- Bikeshedding on naming if the chosen name is reasonable
- Speculative "what if in the future…" — we ship MVP first
