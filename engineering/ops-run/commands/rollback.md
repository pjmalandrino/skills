---
description: Execute the rollback playbook step by step
argument-hint: [target-version]
---
Read @engineering/ops-run/specs/rollback-playbook.md and apply it.

If $1 is provided, treat it as the target version to rollback to; otherwise help me pick one.
Ask confirmation before every destructive step (docker compose down, image pin change, git reset, tag move).
Stop and report if any step fails — do not auto-continue.
