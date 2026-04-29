# Dev Flow

## Purpose

Day-to-day developer workflow: git branching, commit conventions, code review, CI/CD. Owned by the tech leads, applied by every developer on every change.

## When Claude should look here

- A user asks about how to branch, commit, open a PR, or review code.
- A change is being committed or pushed and needs to follow conventions.
- A user mentions: *git flow*, *trunk-based*, *branch naming*, *commit message*, *PR*, *pull request*, *code review*, *merge strategy*, *CI*, *pipeline*, *pre-commit hook*.

## Layout

- `rules/`      — workflow choices (branching model, conventional commits, PR template, review checklist)
- `specs/`      — current branch model diagram, CI pipeline shape, required checks
- `references/` — generic theory (git flow vs trunk-based, conventional commits spec, code-review research)
- `commands/`   — invocable skills (PR drafter, commit-message checker, review checklist runner)
- `templates/`  — PR template, commit message template, code-review checklist

## Cross-references

- Quality gates running in CI: [`engineering/quality/`](../quality/).
- Architecture rules enforced in review: [`engineering/architecture/rules/`](../architecture/rules/).
- Audits triggerable from the workflow: [`engineering/audit/`](../audit/).
