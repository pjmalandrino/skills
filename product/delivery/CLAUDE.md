# Delivery

## Purpose

Sprint planning, release cadence, milestones, and project tracking. Owned by the delivery manager / scrum master / project lead, used by anyone coordinating *when* work happens.

## When Claude should look here

- A user asks about sprint planning, release dates, milestones, or capacity.
- A release is being prepared, deferred, or post-mortemed.
- A user mentions: *sprint*, *release*, *milestone*, *capacity*, *velocity*, *retro*, *standup*, *Gantt*, *change freeze*, *cut-off*.

## Layout

- `rules/`      — delivery process choices (sprint length, release cadence, change-freeze policy, definition of done)
- `specs/`      — current release plan, milestone calendar, freeze windows
- `references/` — generic theory (Scrum, Kanban, release-train patterns)
- `commands/`   — invocable skills (release-prep checklist runner, retro facilitator…)
- `templates/`  — release-notes template, retro template, project post-mortem template

## Cross-references

- Operational release execution (deploy, rollback): [`engineering/ops-run/`](../../engineering/ops-run/).
- Product priorities feeding the plan: [`product/discovery/`](../discovery/).
