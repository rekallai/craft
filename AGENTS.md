# AGENTS.md

This project follows the **CRAFT** standard — Context-Reusable Agentic Folder Tree. See `README.md` for the full specification.

CRAFT separates slow-moving human signal (vision, domain, references) from fast-moving AI output (plans, drafts, repositories). Each lives at a stable, predictable path so agents can find context without MCP overhead or search gymnastics.

## Directory Map

| Path          | Purpose                                                  | Authorship   |
| ------------- | -------------------------------------------------------- | ------------ |
| `specs/`      | High-signal project specifications                       | Mostly Human |
| `references/` | Supporting inputs — docs, data, transcripts, exports     | Mostly Human |
| `prompts/`    | Reusable agent patterns — skills, jobs, checklists, QA   | Mostly Human |
| `plans/`      | AI-collaborated plans, reports, and drafts               | Mostly AI    |
| `build/`      | Shippable code repositories and artifacts                | Mostly AI    |

## Where to Read

When you need to understand **what** and **why** — start in `specs/`:
- `specs/vision.md` — business and product vision
- `specs/domain.md` — terminology, industry context
- `specs/product/` — scoped product definitions
- `specs/marketing/` — positioning and messaging

When you need supporting inputs — look in `references/`:
- `references/datasets/<name>/` — data relevant for modeling
- `references/slack/<channel>/`, `references/linear/<board>/` — exports and feeds
- `references/google-docs/<file>.md`, `references/google-meets/<date>.md` — documents and transcripts
- `references/figma/<project>/` — design exports

When you need a reusable capability or routine — look in `prompts/`:
- `prompts/skills/` — reusable agent capabilities
- `prompts/jobs/` — schedulable prompts with triggers
- `prompts/checklists/` — checklists (e.g. project-kickoff-requirements.md)
- `prompts/qa/` — quality assurance routines

## Where to Write

- **Plans, reports, drafts** → `plans/<area>/<name>.md`
  - Every plan starts with a TLDR at the top
  - Optional `plans/<area>/<name>.html` for a visualized version using `plans/style.css`
- **Code, services, infrastructure, libraries** → `build/<repo-name>/`
- **Do not write to `specs/` or `references/`** without an explicit instruction — these are human-owned inputs

## Conventions

- Flat files at stable paths beat clever nesting. CRAFT relies on predictability.
- Every plan markdown begins with a TLDR.
- Treat `specs/` and `references/` as read-mostly inputs; treat `plans/` and `build/` as your output surface.
- When unsure where something belongs, ask:
  is this **human signal** (`specs/`),
  **supporting input** (`references/`),
  **reusable pattern** (`prompts/`),
  **AI work product** (`plans/`),
  or **shippable artifact** (`build/`)?
