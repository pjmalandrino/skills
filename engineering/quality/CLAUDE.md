# Quality

## Purpose

Test strategy, automation, QA practices, and the definition of "good enough to ship". Owned by QA leads and the engineering team collectively.

## When Claude should look here

- A user asks about test pyramid, what to test where, test naming, or coverage targets.
- A change is missing tests or needs new test coverage.
- A user mentions: *unit test*, *integration test*, *e2e*, *end-to-end*, *test pyramid*, *coverage*, *flaky*, *Karate*, *Playwright*, *fixture*, *mock*, *stub*, *contract test*.

## Layout

- `rules/`      — testing choices (test pyramid shape, coverage thresholds, e2e tool, mocking policy)
- `specs/`      — current test suites layout, coverage report links, e2e scenarios catalog
- `references/` — generic theory (test pyramid, given-when-then, mutation testing, contract testing)
- `commands/`   — invocable skills (test scaffolder, flaky-test detector, coverage diff)
- `templates/`  — test plan, e2e scenario, bug report

## Cross-references

- Tests run in CI configured under: [`engineering/dev-flow/`](../dev-flow/).
- Quality audit (coverage, flakes, etc.): [`engineering/audit/commands/`](../audit/commands/).
