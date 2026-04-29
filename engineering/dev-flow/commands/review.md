---
description: Review current branch changes against the code review checklist
---
Read @docs/git-workflow/code-review-checklist.md.

Then inspect the current branch:
- `git status`
- `git diff` vs the base branch (usually `release/*` or `main`)

Apply the checklist item by item to the actual diff. Mark each item PASS / FAIL / N/A with a short justification referencing file:line.
End with a summary: blockers, nits, nothing-to-fix.
