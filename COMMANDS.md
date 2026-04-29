# Commands

Index of every invocable skill in this repo, grouped by sub-package. Each skill lives under `<sub-package>/commands/` and follows the Claude Code skill format (frontmatter + body).

## engineering/audit/commands/

| Skill                  | Description                                                              | Arg                              |
|------------------------|--------------------------------------------------------------------------|----------------------------------|
| `all`                  | Run the full audit master (all 12 audits) on a given release branch      | `<release-target>` (e.g. `release/0.5.0`) |
| `clean-architecture`   | Audit 01 — Hexagonal Architecture (ports & adapters)                     | —                                |
| `ddd`                  | Audit 02 — DDD                                                            | —                                |
| `clean-code`           | Audit 03 — Clean Code                                                     | —                                |
| `kiss`                 | Audit 04 — KISS                                                           | —                                |
| `dry`                  | Audit 05 — DRY                                                            | —                                |
| `solid`                | Audit 06 — SOLID                                                          | —                                |
| `decoupling`           | Audit 07 — Decoupling                                                     | —                                |
| `security`             | Audit 08 — Security                                                       | —                                |
| `tests`                | Audit 09 — Tests                                                          | —                                |
| `ci-build`             | Audit 10 — CI / Build                                                     | —                                |
| `documentation`        | Audit 11 — Documentation                                                  | —                                |
| `performance`          | Audit 12 — Performance                                                    | —                                |

## engineering/dev-flow/commands/

| Skill        | Description                                                |
|--------------|------------------------------------------------------------|
| `commits`    | Check staged/unstaged changes against commit conventions  |
| `merge`      | Check current PR / branch against the merge policy        |
| `review`     | Review current branch changes against the code review checklist |

## engineering/security/commands/

| Skill                | Description                                | Arg                          |
|----------------------|--------------------------------------------|------------------------------|
| `security-response`  | Walk through the security response playbook | `[short-issue-description]` |

## engineering/ops-run/commands/

| Skill        | Description                                  | Arg                              |
|--------------|----------------------------------------------|----------------------------------|
| `incident`   | Walk through the incident response playbook | `[short-incident-description]`  |
| `monitoring` | Run the monitoring checklist                | —                                |
| `deploy`     | Run the deployment checklist                | —                                |
| `rollback`   | Execute the rollback playbook step by step  | `[target-version]`              |

## How to invoke

These files follow Claude Code's skill format. When wired into a project's `.claude/commands/` (typically by symlink or copy), each becomes a slash command in Claude Code: `/<namespace>:<skill>`.

The original Docling-Studio namespacing (kept here for reference):

| Sub-package                       | Original namespace |
|-----------------------------------|--------------------|
| `engineering/audit/commands/`     | `audit:*`          |
| `engineering/dev-flow/commands/`  | `git:*`            |
| `engineering/ops-run/commands/`   | `ops:incident`, `ops:monitoring`, `release:deploy`, `release:rollback` |
| `engineering/security/commands/`  | `ops:security-response` |

The frontmatter does not pin a namespace — pick your own mapping when wiring into a project.

## Skill-to-rule mapping (audit chain)

Every audit skill enforces a rule documented elsewhere in the repo:

| Audit skill                                         | Checklist (reference)                                                  | Enforces rule                                            |
|-----------------------------------------------------|------------------------------------------------------------------------|----------------------------------------------------------|
| `audit/commands/clean-architecture.md`              | `audit/references/01-clean-architecture-checklist.md`                  | `architecture/rules/hexagonal-boundaries.md`             |
| `audit/commands/ddd.md`                             | `audit/references/02-ddd-checklist.md`                                 | (DDD tactical patterns — rule TBD)                       |
| `audit/commands/clean-code.md`                      | `audit/references/03-clean-code-checklist.md`                          | `architecture/rules/coding-standards.md`                 |
| `audit/commands/kiss.md`                            | `audit/references/04-kiss-checklist.md`                                | `architecture/rules/coding-standards.md`                 |
| `audit/commands/dry.md`                             | `audit/references/05-dry-checklist.md`                                 | `architecture/rules/coding-standards.md`                 |
| `audit/commands/solid.md`                           | `audit/references/06-solid-checklist.md`                               | (SOLID — rule TBD)                                       |
| `audit/commands/decoupling.md`                      | `audit/references/07-decoupling-checklist.md`                          | `architecture/rules/hexagonal-boundaries.md`             |
| `audit/commands/security.md`                        | `audit/references/08-security-checklist.md`                            | `security/rules/security-policy.md`                      |
| `audit/commands/tests.md`                           | `audit/references/09-tests-checklist.md`                               | `quality/rules/karate-e2e-conventions.md`                |
| `audit/commands/ci-build.md`                        | `audit/references/10-ci-build-checklist.md`                            | (CI conventions — rule TBD)                              |
| `audit/commands/documentation.md`                   | `audit/references/11-documentation-checklist.md`                       | (doc standards — rule TBD)                               |
| `audit/commands/performance.md`                     | `audit/references/12-performance-checklist.md`                         | (perf budget — rule TBD)                                 |

Run `audit/commands/all.md` to chain every audit on a release branch and produce a consolidated report.
