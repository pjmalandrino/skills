# Documentation Standards

## Decision

Documentation is part of the change, not a follow-up. Every PR ships with the docs needed to understand and operate the change.

## What must be documented

- **Public function / class / endpoint** — docstring with purpose, params, return, raises (or JSDoc / TSDoc equivalent).
- **Architectural decision** — recorded as ADR (`engineering/architecture/specs/adrs-and-design/ADR-NNN-*.md`) before the change merges.
- **Cross-cutting feature** — design doc (`engineering/architecture/templates/design-doc-template.md`) before implementation.
- **Public API change** — OpenAPI / equivalent spec updated in the same PR.
- **Operational change** (deploy, monitoring, alerts) — runbook updated in `engineering/ops-run/specs/`.
- **Each top-level package** — has a `CLAUDE.md` describing its purpose, triggers, and layout.
- **User-facing change** — changelog entry in the same PR.

## Conventions

- Markdown is the canonical format. Diagrams as Mermaid in markdown when possible.
- Code examples in docs must be runnable, or clearly marked pseudo-code.
- Cross-link related docs explicitly (`See also` sections).
- One topic per file. Long files split by topic, not by length.
- Headings are noun phrases, not sentences.

## Forbidden

- Merging a public API change without updating the spec.
- "Will be documented later" — comments in PR descriptions don't replace docs in the repo.
- Stale docs. If a doc is wrong, fix or delete it.
- Documentation in commit messages instead of in `*.md` files. Commit messages explain *this commit*; docs explain the *system*.

## Why

Docs that ship with the change are the docs that get written. Anything queued "for later" is queued forever. Writing the doc once at PR time is far cheaper than N developers reverse-engineering the change later.

## See also

- Audit: [`../../audit/commands/documentation.md`](../../audit/commands/documentation.md)
- Checklist: [`../../audit/references/11-documentation-checklist.md`](../../audit/references/11-documentation-checklist.md)
- ADR template: [`../../architecture/templates/adr-template.md`](../../architecture/templates/adr-template.md)
- Design doc template: [`../../architecture/templates/design-doc-template.md`](../../architecture/templates/design-doc-template.md)
