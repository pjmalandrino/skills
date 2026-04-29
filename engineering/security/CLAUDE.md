# Security

## Purpose

Threat modeling, secure-coding rules, dependency audits, secrets handling, and incident response for security events. Owned by the security lead, enforced by every developer.

## When Claude should look here

- A user asks about authn/authz, secrets, vulnerabilities, threat modeling, or compliance.
- A change touches authentication, authorization, secret handling, or external dependencies.
- A user mentions: *CVE*, *vulnerability*, *secret*, *credential*, *SAST*, *DAST*, *threat model*, *STRIDE*, *OWASP*, *compliance*, *RBAC*, *encryption*, *PII*.

## Layout

- `rules/`      — security choices (auth model, secret-storage rule, dependency policy, severity SLA)
- `specs/`      — current threat model, attack surface map, dependency inventory
- `references/` — generic theory (OWASP Top 10, STRIDE, secure coding patterns)
- `commands/`   — invocable skills (threat-model facilitator, dep-vuln scanner, security-review runner)
- `templates/`  — threat-model template, security-review checklist, vulnerability-disclosure template

## Cross-references

- Operational incident response (when an incident is happening): [`engineering/ops-run/`](../ops-run/).
- Security audit (rule compliance scan): [`engineering/audit/commands/`](../audit/commands/).
- CI security checks (SAST, dep-scan): [`engineering/dev-flow/`](../dev-flow/).
