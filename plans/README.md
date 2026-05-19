# plans/

AI-collaborated plans, reports, and drafts. Mostly AI-authored, human-reviewed. This is the main output surface for planning work — the place where back-and-forth with an agent crystallizes into something durable.

A mature agentic workflow lives or dies on the quality of its plans. Keeping them here, at predictable paths, means later runs can build on earlier ones instead of reinventing context every time.

## Suggested layout

- `engineering/<name>.md` — technical plans (data models, architecture, migrations)
- `marketing-website/<name>.md` — site plans, IA, copy decks
- `product/<name>.md` — product plans, feature breakdowns
- `<area>/<name>.html` — optional rich-HTML visualization of a plan
- `style.css` — shared stylesheet for HTML plans

## Conventions

- **Every plan starts with a TLDR** at the very top. If a reader only reads the TLDR, they should know what the plan proposes.
- Use markdown by default. Add an `.html` sibling when a visual layout helps (timelines, diagrams, comparison tables).
- Date-stamp drafts when iteration matters: `mvp-data-model-2026-04.md`.

See [`../references/example-projects/lighthouse/plans/`](../references/example-projects/lighthouse/plans/) for examples.
