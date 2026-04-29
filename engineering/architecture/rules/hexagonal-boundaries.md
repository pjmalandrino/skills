# Hexagonal Boundaries

## Decision

Hexagonal architecture (ports & adapters). Three layers:

- `domain/` — business logic, pure
- `infra/`  — adapters that implement domain ports (DB, LLM, file I/O…)
- `api/`    — adapters that drive use cases (HTTP, CLI, scheduled jobs…)

## Imports

- `domain/` imports nothing outside `domain/`.
- `infra/` imports from `domain/` and implements `domain/ports`.
- `api/` imports from `domain/` and orchestrates use cases.
- `infra/` and `api/` never import each other.

## Domain purity

- No framework code in `domain/` (no FastAPI, no SQLAlchemy, no decorators tied to a stack).
- No I/O in `domain/` (no file reads, no HTTP, no DB).
- No third-party types in domain signatures — wrap them in value objects.

## Ports

- Every external boundary crossed by `domain/` is declared as a port (Protocol / ABC) in `domain/ports`.
- Each port has at least one adapter in `infra/`.
- Tests substitute ports with in-memory fakes; no DB or network required.

## Forbidden

- `from infra import …` inside `domain/`
- `from api import …` inside `domain/` or `infra/`
- Framework decorators on domain entities
- Direct DB or network calls in `domain/`

## Why

Inverting dependencies (infra depends on domain, not the reverse) lets the domain evolve without leaking framework choices, makes tests fast, and lets adapters be swapped (Postgres → SQLite, OpenAI → Anthropic) without touching business logic.

## See also

- Theory: [`references/hexagonal-architecture.md`](../references/hexagonal-architecture.md)
- C4 modeling decision: [`rules/c4-modeling.md`](./c4-modeling.md)
- Audit: [`engineering/audit/commands/audit-hexagonal.md`](../../audit/commands/audit-hexagonal.md)
