# lighthouse-app

The shippable Lighthouse application — Next.js + Postgres + Stripe + Plaid.

## What lives here in a real project

In a real CRAFT project this directory would contain a full application repository — typically cloned or git-submoduled in. It would have its own:

- `package.json`, `tsconfig.json`, framework config
- `src/` — application code
- `tests/`, `e2e/`
- `migrations/` — database schema (matching `plans/engineering/mvp-data-model.md`)
- `.github/workflows/` — CI
- Its own `README.md`, `LICENSE`, and so on

This README exists as a placeholder so the example tree is navigable without shipping a fake codebase. The point of `build/` is that **the rest of CRAFT (specs, plans, references) wraps around the code** so an agent working in `build/lighthouse-app/` can pull context from one directory up.

## Reading order for an agent dropped into this repo

1. `../../README.md` — the Lighthouse example overview
2. `../../specs/vision.md` and `../../specs/domain.md` — what we're building and the words for it
3. `../../specs/product/mvp-scope.md` — what's in and out
4. `../../plans/engineering/mvp-data-model.md` — the schema this app implements
5. `../../prompts/skills/code-review.md` — what reviewers will check for
