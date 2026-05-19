# specs/

High-signal project specifications. Mostly human-authored. Treat as read-mostly input — agents should not write here without explicit instruction.

This directory holds the **what** and **why** of the project. Vision changes slowly; domain knowledge changes slowly; scope changes occasionally. Putting them at stable paths means every plan, every agent run, every new collaborator can pull them up the same way.

## Suggested files

- `vision.md` — business and product vision
- `domain.md` — terminology, industry context, glossary
- `product/mvp-scope.md` — must / should / won't list
- `product/north-star-metric.md` — the single number you're optimizing
- `marketing/value-proposition.md` — positioning statement
- `marketing/icp.md` — ideal customer profile

## Conventions

- One concept per file. Keep them short enough to read end-to-end.
- Markdown only. No frontmatter required.
- If a spec gets long, split by sub-topic (e.g. `product/pricing.md`) rather than nesting headings deeper.

See [`../references/example-projects/lighthouse/specs/`](../references/example-projects/lighthouse/specs/) for a worked example.
