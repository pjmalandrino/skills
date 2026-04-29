---
description: Check current PR / branch against the merge policy
---
Read @docs/git-workflow/merge-policy.md.

Inspect the current branch (source, target, CI status, approvals if on GitHub via `gh pr view`) and verify each policy item.
Report which conditions are met and which are blocking the merge.
Do not run `git merge` or `gh pr merge` — just report.
