# references/

Supporting inputs — documents, data, transcripts, exports, feeds. Mostly human-curated (or piped in from external systems). Treat as read-only material that agents draw on but don't author.

This is where context-from-the-world lives: the Slack thread that explains a design choice, the customer interview that motivated a feature, the dataset behind a data-model plan, the Figma export that a marketing site is built from.

## Suggested layout

- `datasets/<name>/` — CSVs, JSON, samples relevant for modeling
- `slack/<channel>/` — append-only Slack dumps
- `linear/<board>/` — Linear ticket exports
- `google-docs/<file>.md` — markdown representations of Google Docs
- `google-meets/<date>.md` — meeting transcripts
- `figma/<project>/` — Figma exports
- `example-projects/<name>/` — fully worked example CRAFT trees

## Conventions

- Append-only when the source is a feed (Slack, Linear). Never rewrite history.
- Prefer markdown for human-readable artifacts so they grep cleanly.
- Large binary assets (PDFs, design files) are fine here, but reference them from text files when possible so agents can navigate via text.

For a fully populated CRAFT tree to study, see [`example-projects/lighthouse/`](example-projects/lighthouse/).
