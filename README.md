# Context-Reusable Agentic Folder Tree (CRAFT)

CRAFT is an open standard for structuring agentic projects — where humans and AI collaborate on everything from product vision to shipped code. It rests on a simple premise: the quality of AI output is bounded by the quality of its inputs, so context deserves the same care as code. CRAFT separates slow-moving human signal (vision, domain knowledge, references) from fast-moving AI output (plans, drafts, repositories), and keeps each at a stable, predictable path. The result is a working environment where context is reusable across plans, human intent stays legible, and agents can find what they need without MCP overhead or search gymnastics — just flat files in a tree designed for the way agentic work actually flows.

This repository is itself a CRAFT-shaped scaffold: the top-level `specs/`, `references/`, `prompts/`, `plans/`, and `build/` directories ship empty (each with a short README explaining what belongs there), so you can clone it and start filling in your own project. A worked example of a fully populated CRAFT tree lives in [`references/example-projects/lighthouse/`](references/example-projects/lighthouse/) — a fictional invoice-management SaaS — to show the standard in practice without polluting your checkout.

*Note: We are still iterating on this - feedback actively wanted - just open a GH issue*

## Top-level Directory Structure


| Path          | Purpose                                                  | Authorship   |
| ------------- | -------------------------------------------------------- | ------------ |
| `specs/`      | High-signal project specifications                       | Mostly Human |
| `references/` | Additional inputs such as docs, data or feeds            | Mostly Human |
| `prompts/`    | Known patterns for agents to run                         | Mostly Human |
| `plans/`      | AI-collaborated well organized plans, reports and drafts | Mostly AI    |
| `build/`      | Github code repositories                                 | Mostly AI    |


*Note: Supplemented with a top level AGENTS.md for agent context loading of directory structure and common conventions*

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

