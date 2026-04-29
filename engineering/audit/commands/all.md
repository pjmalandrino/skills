---
description: Run the full audit master (all 12 audits) on a given release branch
argument-hint: <release-target>  e.g. release/0.5.0
---
**Required argument**: the release branch to audit, e.g. `release/0.5.0`. Stop and ask the user if missing.

Argument received: `$ARGUMENTS`

## Pre-flight (mandatory — do not skip)

Before reading any audit fiche or spawning any agent:

1. Run `git rev-parse --abbrev-ref HEAD` and `git rev-parse HEAD`. If the current branch is **not** the requested release target, STOP and ask the user to `git checkout <release-target>` themselves. Do **not** checkout on their behalf — their working tree may have untracked files that conflict.
2. Run `git rev-parse --verify <release-target>` to confirm the branch exists. If it doesn't, stop and tell the user.
3. State explicitly in the response: "Auditing branch `<release-target>` at commit `<short-sha>`". This is your contract with the user — every report you write must match this branch.
4. Extract the version from the target name (`release/X.Y.Z` → `X.Y.Z`). Reports go to `docs/audit/reports/release-X.Y.Z/`.

If pre-flight fails, do not run any audit.

## Execution

Read @docs/audit/master.md and run every referenced audit in order.

For each audit:
- Score the items per the master.md weighting formula.
- Write a per-audit report to `docs/audit/reports/release-X.Y.Z/NN-name.md` following the format in master.md section 5.
- Source files must be read from the working tree on the release branch — never from a different branch via `git show`. Spawned agents inherit the working tree, so verify the branch is correct before delegating.
- Cite file paths with line numbers; verify each citation exists at the audited commit.

After all 12 audits, write a consolidated `docs/audit/reports/release-X.Y.Z/summary.md` with:
- the dashboard table (score / CRIT / MAJ / MIN / INFO / verdict per audit)
- top blockers (weight 3 failures first)
- quick wins (weight 1 failures that are easy fixes)
- the global verdict (NO-GO if any unresolved CRIT)

This is a long task — checkpoint to the user after each audit (one or two lines: score, verdict, deltas vs prior baseline if any) instead of dumping everything at the end.
