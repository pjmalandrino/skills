# Frontend Layout

Project-specific shape of the frontend (`frontend/`).

## Stack

Vue 3 · TypeScript (strict) · Vite · Pinia · Vitest

## Layout

Feature-based: each feature lives in `src/features/<name>/` with three sub-folders:

- `api/`   — HTTP calls (shared client in `shared/api/`)
- `store/` — Pinia store
- `ui/`    — Vue components

Other top-level directories:

- `src/pages/`  — routed pages
- `src/app/`    — app shell (router, root component, app-wide providers)
- `src/shared/` — code reused across features

## Validation pipeline

Run before considering any change done:

```bash
PATH="/usr/local/bin:$PATH" npm run lint:fix       # 1. ESLint auto-fix
PATH="/usr/local/bin:$PATH" npm run format         # 2. Prettier format
PATH="/usr/local/bin:$PATH" npm run lint           # 3. verify zero violations
PATH="/usr/local/bin:$PATH" npm run format:check   # 4. verify zero format diff
PATH="/usr/local/bin:$PATH" npm run type-check     # 5. vue-tsc --noEmit
PATH="/usr/local/bin:$PATH" npm run test:run       # 6. all tests pass
```

Every new code path must have tests. Zero violations tolerated.

## Conventions

- **Path alias**: `@/` → `src/`.
- **ESLint**: flat config (ESLint 9+), `eslint-plugin-vue`, `typescript-eslint`. No formatting rules — Prettier owns that.
- **Prettier**: no semicolons, single quotes, trailing commas, 100 chars, 2 spaces.
- **Security**: always sanitize user-rendered HTML via DOMPurify. Markdown parsed with `marked`.
- **Tests**: colocated with source (`*.test.ts`), Vitest as runner.
- **TypeScript**: strict mode. `no-explicit-any` disabled but prefer precise types when possible.
- **Components**: `vue/multi-word-component-names` disabled. `no-console` is warn (warn/error allowed).
- **Unused vars**: prefix with `_` to mark intent.

## See also

- Coding standards (cross-stack): [`../rules/coding-standards.md`](../rules/coding-standards.md)
- High-level architecture overview: [`architecture-overview.md`](architecture-overview.md)
- Backend counterpart: [`backend-layout.md`](backend-layout.md)
