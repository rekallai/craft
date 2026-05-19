# AGENTS.md

## Directory map

| Path          | Contents                                                 | Write here? |
| ------------- | -------------------------------------------------------- | ----------- |
| `specs/`      | Project specs — vision, domain, scope, positioning       | No          |
| `references/` | Supporting inputs — docs, data, transcripts, exports     | No          |
| `prompts/`    | Reusable patterns — skills, jobs, checklists, QA         | No          |
| `plans/`      | Plans, reports, drafts                                   | Yes         |
| `build/`      | Shippable code repositories and artifacts                | Yes         |

## Where to read

- `specs/vision.md`, `specs/domain.md` — product and terminology
- `specs/product/` — scope, MVP definitions
- `specs/marketing/` — positioning, messaging
- `references/datasets/<name>/` — datasets
- `references/slack/<channel>/`, `references/linear/<board>/` — feeds and exports
- `references/google-docs/<file>.md`, `references/google-meets/<date>.md` — documents and transcripts
- `references/figma/<project>/` — design exports
- `prompts/skills/`, `prompts/jobs/`, `prompts/checklists/`, `prompts/qa/` — reusable patterns

## Where to write

- Plans → `plans/<area>/<name>.md`. Every plan starts with a TLDR.
- Optional rich-HTML sibling → `plans/<area>/<name>.html` using `plans/style.css`.
- Code → `build/<repo-name>/`.

## Rules

- Do not modify files in `specs/` or `references/` without an explicit instruction.
- Every plan markdown begins with a TLDR.
- Prefer flat files at stable paths over deep nesting.
