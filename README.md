# CRAFT — Context-Reusable Agentic Folder Tree

> An open standard for organizing projects where humans and AI ship together.

AI output is bounded by input quality, so context deserves the same discipline as code. CRAFT splits **slow-moving human signal** (vision, domain, references) from **fast-moving AI output** (plans, builds) and keeps each at a stable, predictable path. Agents find what they need by `cat`, not by search.

## The tree

```text
your-project/
├── AGENTS.md       # entry point for agents — directory map + conventions
├── specs/          # what & why — vision, domain, scope          (human)
├── references/     # supporting inputs — docs, data, feeds       (human)
├── prompts/        # reusable patterns — skills, jobs, QA        (human)
├── plans/          # plans, reports, drafts (TLDR-first)         (AI)
└── build/          # shippable code repos                        (AI)
```

## Quick start

Use this repo as a scaffold — top-level directories ship empty, each with a short README explaining what goes there:

```bash
git clone <this-repo> my-project
cd my-project && rm -rf .git && git init
```

For a fully-populated worked example, see [`references/example-projects/lighthouse/`](references/example-projects/lighthouse/) — a fictional invoice-management SaaS that fills in every directory.

*Still iterating — feedback welcome via GH issues.*

---

## `specs/`

These are markdown files that provide a high degree of human signal in the what and why of the project. 

Example files for software product projects:

- `specs/vision.md`: The business and product vision of the project.
- `specs/domain.md`: Important domain knowledge, terminlogy and industry context.
- `specs/product/mvp-scope.md`: A definition of the Minimum Viable Product.
- `specs/marketing/value-proposition.md`: An outline of the marketing message

*Note: We can imagine certain tooling that creates a write-only file (e.g. a Google Doc vision doc that outputs to specs/vision.md)*

## `references/`

These can be a combination of static or dynamic artifacts. They can be documents, data sets or feeds from external systems.

Example files for Rekall organization:

- `references/datasets/example-customer-export/`: Data sets that can be relevant (e.g. for data model planning)
- `references/slack/<channel>/`: Append-only feed/dump of Slack channel.
- `references/linear/<board>/`: Append-only feed/dump of Linear tickets.
- `references/google-docs/<file>.md`: Markdown representation of Google Docs.
- `references/google-meets/<meeting-date>.md`: Transcripts from relevant Google Meets.
- `references/figma/<project>/`: Figma export.
- `references/claude-design/branding/`: Example export of a design project.
- `references/claude-design/marketing-website/`: Example export of a design project.

## `prompts/`

This folder could hold generic prompting templates, but would have specific folders for skills and jobs.

- `prompts/jobs/`: Schedulable AI prompts with triggers.
- `prompts/skills/`: Reusable agent capabilities.
- `prompts/checklists/`: Checklists for agents (e.g. project-kickoff-requirements.md)
- `prompts/qa/`: Quality assurance routines (e.g. mvp-golden-path-acceptance-test.md).

## `plans/`

This is the place for agentic planning (with skills). 

Examples:

- `plans/engineering/mvp-data-model.md`: Data model used downstream.
- `plans/marketing-website/implementation-plan.md`: Full plan in md, TLDR at the top.
- `plans/marketing-website/implementation-plan.html`: Visualized plan in rich HTML.
- `plans/style.css`: Common styles for HTML plans

## `build/`

Agenticly produced artifacts. Examples:

- Apps
- Services
- Infrastructure
- Libraries
- Plugins

