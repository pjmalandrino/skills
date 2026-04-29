# CI Conventions

## Decision

CI runs on every push and every pull request. Red CI blocks merge. The same checks that run locally (lint, format, type-check, tests) also run in CI — no green-locally-red-CI surprises.

## Stages

Every PR runs, in order:

1. **Lint** — `ruff check` (backend) / `eslint` (frontend). Zero violations.
2. **Format** — `ruff format --check` / `prettier --check`. Zero diff.
3. **Type-check** — `mypy --strict` / `vue-tsc --noEmit`. Zero errors.
4. **Unit + integration tests** — `pytest tests/` / `vitest run`. All green.
5. **Build** — `vite build` / equivalent. Reproducible artifact.
6. **E2E** — Karate suite on key flows (only on PRs targeting `release/*` or `main`).

## Rules

- CI configuration lives in `.github/workflows/` (GitHub Actions).
- Tests must be deterministic. Flaky tests are quarantined within 24 h, fixed within a sprint.
- Build artifacts are reproducible: same commit → same hash.
- Secrets are read from CI secret stores, never committed.
- Cache: dependencies cached by lockfile hash, build outputs cached by source hash.

## Forbidden

- `--no-verify` to bypass pre-commit hooks (also covered by `commit-conventions.md`).
- Skipping CI to land a hotfix. If CI is broken, fix CI first; if truly urgent, document the bypass in the PR description.
- Tests that depend on wall-clock time, network availability, or filesystem ordering.
- Workflows that run on `pull_request_target` while reading secrets — security risk.

## Why

CI is the team's contract that "main is always green". Every shortcut taken in CI is paid back tenfold in flaky-test investigations and hotfix scrambles.

## See also

- Audit: [`../../audit/commands/ci-build.md`](../../audit/commands/ci-build.md)
- Checklist: [`../../audit/references/10-ci-build-checklist.md`](../../audit/references/10-ci-build-checklist.md)
- Commit & merge rules: [`commit-conventions.md`](commit-conventions.md), [`merge-policy.md`](merge-policy.md)
- Quality gates: [`../../quality/`](../../quality/)
