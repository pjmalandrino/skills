# Performance Budget

## Decision

Every shippable feature respects a performance budget. Regressions block merges until justified by an ADR or compensated elsewhere.

## Budgets

### Backend

- API endpoint **p95** latency: **< 300 ms** (synchronous endpoints)
- API endpoint **p99** latency: **< 1 s**
- Background job: warn if a single job exceeds **30 s**
- DB queries per request: **< 10**. N+1 patterns are forbidden.
- Memory per worker: warn at **512 MB**, kill at **1 GB**

### Frontend

- Initial JS bundle (compressed): **< 250 KB**
- Time-to-interactive on cold load (4G simulation): **< 3 s**
- Largest Contentful Paint: **< 2.5 s**
- Cumulative Layout Shift: **< 0.1**

## Rules

- Adding a new endpoint or page → add a benchmark in the same PR.
- Regression > 10 % on any budget → PR blocked unless an ADR explains the trade-off.
- Performance tests run in CI on every PR (smoke level) and on every release branch (full level).

## Forbidden

- Synchronous external calls inside a request handler without timeout + circuit breaker.
- Importing an entire library when a tree-shakable subset suffices (frontend).
- N+1 query patterns. Use eager loading or `IN` queries.
- Loading large blobs into memory when streaming suffices.

## Why

Without explicit budgets, performance rots silently. Each individual regression seems small; the cumulative effect destroys user experience. Budgets make the trade-off visible at PR time, when fixing it is cheap.

## See also

- Audit: [`../../audit/commands/performance.md`](../../audit/commands/performance.md)
- Checklist: [`../../audit/references/12-performance-checklist.md`](../../audit/references/12-performance-checklist.md)
- Hosting and capacity decisions: [`../../ops-run/specs/`](../../ops-run/specs/)
