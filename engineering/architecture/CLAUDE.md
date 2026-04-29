# Architecture

## Purpose

Architectural decisions, conventions, and the project's current architectural shape. Owned by tech leads and architects, used by every developer when designing new modules or reviewing PRs that cross layer boundaries.

## When Claude should look here

- A user asks about architectural style, layering, dependency direction, or modeling.
- A PR or change touches code that crosses the `domain ↔ infra ↔ api` boundary.
- A new feature is being designed and needs a design doc, ADR, or C4 update.
- A user mentions: *hexagonal*, *ports & adapters*, *C4*, *container diagram*, *component diagram*, *DDD*, *hexagonal architecture*.

## Layout

- `rules/`      — architectural decisions for this project (hexagonal boundaries, C4 modeling levels, DDD tactical patterns)
- `specs/`      — current architectural shape (C4 Container diagram, C4 Component diagrams, package map)
- `references/` — generic theory (hexagonal architecture, C4 model, DDD, SOLID)
- `commands/`   — invocable skills (e.g. `/design <package>` to generate a mermaid view)
- `templates/`  — design doc template, ADR template

## Cross-references

- Audits that enforce these rules live in [`engineering/audit/commands/`](../audit/commands/) — one audit per rule, plus `audit-all`.
- Code reviews that touch architecture must consult [`rules/hexagonal-boundaries.md`](rules/hexagonal-boundaries.md) and (once written) `rules/c4-modeling.md`.
- Generic theory deliberately stays in `references/` and is *not* duplicated into rules — rules state the project's choice and link out.
