# Skills Repo

Curated project skills, organized **by audience persona** — not by discipline. PO/PM browse `product/`, developers browse `engineering/`.

## Layout

- `product/`     — PO, PM, designers, delivery managers
  - `product/`     product management (vision, roadmap, PRDs)
  - `design-ux/`   design and UX research
  - `delivery/`    planning, releases, sprint cadence
- `engineering/` — developers, architects, ops, security
  - `architecture/` architectural decisions, C4, hexagonal
  - `dev-flow/`     git workflow, code review, CI/CD
  - `quality/`      test strategy, e2e, QA
  - `security/`     threat modeling, audits, response
  - `ops-run/`      runbooks, monitoring, on-call, releases
  - `audit/`        aggregates rule audits into runnable commands (`audit-all` and per-rule)

Every sub-package shares the same **5-folder template**:

- `rules/`      — summary of choices for this project ("we use C4 Container + Component")
- `specs/`      — detailed project description (actual diagrams, actual layout)
- `references/` — generic theory ("what is C4 in general")
- `commands/`   — invocable skills (slash commands with frontmatter)
- `templates/`  — boilerplate to copy (design doc, ADR, runbook…)

## How to navigate

| Question                                            | Where to look              |
|-----------------------------------------------------|----------------------------|
| "How do we do X *here*?"                            | `<package>/rules/`         |
| "What's the actual current state of X in *this* project?" | `<package>/specs/`   |
| "What is X *in general*?"                           | `<package>/references/`    |
| "Run X for me"                                      | `<package>/commands/`      |
| "Give me a starting point for X"                    | `<package>/templates/`     |

## Conventions

- Each sub-package has its own `CLAUDE.md` describing its purpose, triggers, and contents. Read it before diving into the sub-package.
- Skills in `commands/` follow Claude Code skill format: frontmatter with `name`, `description`, optionally `allowed-tools`. The `description` field drives skill discoverability.
- Cross-persona skills (e.g. a release checklist used by both PM and dev) live with their primary owner; the other persona's package links to it rather than duplicating.

## Repository workflow

- Push directly to `main` (no PR/release flow on this repo).
