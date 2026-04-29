# Ops & Run

## Purpose

Running the system in production: deploy, rollback, monitoring, alerting, on-call, and incident response. Owned by SRE / ops leads, used by anyone touching anything that runs in production.

## When Claude should look here

- A user asks about deploying, rolling back, monitoring, alerts, or incidents.
- A change is being released or an incident is in progress.
- A user mentions: *deploy*, *rollback*, *release*, *monitoring*, *alert*, *PagerDuty*, *on-call*, *incident*, *outage*, *post-mortem*, *runbook*, *SLO*, *SLA*, *observability*, *Grafana*, *Prometheus*.

## Layout

- `rules/`      — ops choices (deploy strategy, rollback policy, on-call rotation, SLO targets)
- `specs/`      — current monitoring dashboards, alert routes, runbook index
- `references/` — generic theory (SRE practices, SLO design, blameless post-mortems, deployment patterns)
- `commands/`   — invocable skills (deploy checklist, rollback playbook, incident facilitator, monitoring scan)
- `templates/`  — runbook template, post-mortem template, change-request template

## Cross-references

- Release planning that feeds deploys: [`product/delivery/`](../../product/delivery/).
- Security incident response (subset of incidents): [`engineering/security/`](../security/).
