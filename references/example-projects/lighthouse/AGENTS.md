# AGENTS.md — Lighthouse

This project follows the **CRAFT** standard. See the CRAFT spec for the canonical directory contract.

## Project-specific notes

- **Lighthouse** is an invoice-management SaaS for small-business owners. Domain terms (Net 30, ACH, dunning) live in `specs/domain.md`.
- The MVP scope is locked — see `specs/product/mvp-scope.md` before proposing features.
- Customer-research transcripts and product-Slack dumps in `references/` are the source of truth for what users actually said; prefer them over your own assumptions.

## Where to Read

- `specs/vision.md`, `specs/domain.md`, `specs/product/mvp-scope.md`, `specs/marketing/value-proposition.md`
- `references/google-meets/` — customer interviews
- `references/slack/product/` — internal product discussion
- `prompts/skills/`, `prompts/jobs/`, `prompts/qa/` — reusable patterns

## Where to Write

- Plans → `plans/<area>/<name>.md` (always TLDR-first)
- Code → `build/lighthouse-app/`
- Never write to `specs/` or `references/` without an explicit instruction
