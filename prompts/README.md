# prompts/

Reusable agent patterns — skills, scheduled jobs, checklists, QA routines. Mostly human-authored. These are the "verbs" of your agentic project: things you want to run more than once.

A skill changes slowly. A checklist changes slowly. Putting them at stable paths means you can wire them into automations, slash commands, or cron jobs without hunting through the repo.

## Suggested layout

- `skills/<name>.md` — reusable agent capabilities (e.g. `code-review.md`)
- `jobs/<name>.md` — schedulable prompts with triggers (e.g. `daily-pr-summary.md`)
- `checklists/<name>.md` — checklists (e.g. `project-kickoff-requirements.md`)
- `qa/<name>.md` — quality assurance routines (e.g. `mvp-golden-path-acceptance-test.md`)

## Conventions

- One prompt per file. Self-contained — the file should make sense without surrounding context.
- For jobs, include the trigger (cron expression, event, manual) at the top of the file.
- For skills, describe inputs, outputs, and when to invoke.

See [`../references/example-projects/lighthouse/prompts/`](../references/example-projects/lighthouse/prompts/) for examples.
