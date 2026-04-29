# Backend Layout

Project-specific shape of the backend (`document-parser/`).

## Stack

FastAPI · Python 3.12+ · Docling 2.x · aiosqlite · pytest

## Layers

Hexagonal layout, mapped onto the following directories:

- `domain/`      — pure business model (dataclasses, value objects, port interfaces). No external dependencies.
- `api/`         — HTTP layer: FastAPI routers, Pydantic DTOs. Camel-case wire format via `alias_generator`.
- `services/`    — use-case orchestration; wires domain, persistence, and infra.
- `persistence/` — Repository pattern over aiosqlite (SQLite). `database.py` owns connection and schema init.
- `infra/`       — adapters: `LocalConverter` (Docling in-process) and `ServeConverter` (remote Docling Serve). Settings from env vars.

## Validation pipeline

Run before considering any change done:

```bash
.venv/bin/ruff check . --fix        # 1. lint + auto-fix
.venv/bin/ruff format .             # 2. format
.venv/bin/ruff check .              # 3. verify zero violations
.venv/bin/ruff format --check .     # 4. verify zero format diff
.venv/bin/pytest tests/ -v          # 5. all tests pass
```

Every new code path must have tests. Zero violations tolerated.

## Conventions

- **Ruff rules**: E, W, F, I (isort), N, UP, B, SIM, TCH, RUF. Line length 100.
- **Ruff exceptions**: E501 (handled by formatter), B008 (FastAPI `Depends`), N815 (Pydantic camel-case), TC003 (`datetime` runtime for Pydantic).
- **isort first-party**: `api`, `domain`, `persistence`, `services`.
- **Naming**: `snake_case` everywhere in Python. `camelCase` only on Pydantic schemas (API contract).
- **Tests**: pytest-asyncio with `asyncio_mode = auto`, located in `tests/`.
- **Env vars**: see `.env.example`. Key vars: `CORS_ORIGINS`, `UPLOAD_DIR`, `DB_PATH`.

## See also

- Architectural decision: [`../rules/hexagonal-boundaries.md`](../rules/hexagonal-boundaries.md)
- Coding standards (cross-stack): [`../rules/coding-standards.md`](../rules/coding-standards.md)
- High-level architecture overview: [`architecture-overview.md`](architecture-overview.md)
