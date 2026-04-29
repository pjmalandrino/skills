# Audit

## Purpose

Aggregates rule audits across all sub-packages into runnable commands. Each rule defined in `<package>/rules/` is matched by an audit skill here that scans the codebase for compliance. The `audit-all` command chains every individual audit.

## When Claude should look here

- A user asks to "audit", "review compliance", "check the architecture", or run a quality scan.
- A release is being prepared (run `audit-all` as a gate).
- A user mentions: *audit*, *compliance*, *health check*, *quality gate*, *technical debt*, *architecture review*.

## Layout

- `rules/`      — audit-meta choices (severity levels, output format, scoring rubric, what counts as a finding)
- `specs/`      — catalog of audits and which rule each one enforces (mapping table)
- `references/` — generic theory (auditing methodology, scoring, prioritization)
- `commands/`   — invocable audits, one per rule (e.g. `audit-hexagonal`, `audit-c4`, `audit-tests`, `audit-security`) plus `audit-all`
- `templates/`  — audit report template, finding template

## Cross-references

- Each audit in `commands/` enforces a specific rule from another package's `rules/`. The mapping lives in `specs/`.
- Architecture rules audited here: [`engineering/architecture/rules/`](../architecture/rules/).
- Quality, security, dev-flow rules also feed audits.
