# build/

Shippable artifacts — apps, services, infrastructure, libraries, plugins. Mostly AI-authored. Each subdirectory is typically its own GitHub repository (often a submodule or independently cloned).

If `specs/` is the "what and why" and `plans/` is the "how," then `build/` is the "what got shipped." Code lives here so the rest of CRAFT (specs, plans, references) can be loaded into an agent alongside it for grounded work.

## Suggested layout

- `<repo-name>/` — one directory per shippable artifact (often a git repo of its own)
- Common examples: `app/`, `marketing-website/`, `infra/`, `cli/`, `sdk/`

## Conventions

- One repo per directory. Don't mix multiple shippable artifacts in one folder.
- Each `build/<repo-name>/` should have its own README, license, and CI as a normal repository would.
- Treat as AI work-surface, but with the same engineering discipline you'd apply to any production codebase — tests, reviews, deploys.

See [`../references/example-projects/lighthouse/build/`](../references/example-projects/lighthouse/build/) for an example pointer.
