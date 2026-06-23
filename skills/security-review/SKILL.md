# Security Review Skill

## Purpose

Review security and privacy risk in a proposed or completed change.

## When to Use

Use when a change touches auth, authorization, data access, storage, logs, dependencies, deployment, or user data.

## Inputs Expected

- Change summary
- Diff or planned files
- Data involved
- Environment or deployment context

## Process

1. Identify sensitive data and actors.
2. Review access control and trust boundaries.
3. Check secrets and logs.
4. Check injection and dependency risk.
5. Check deployment exposure.
6. Report approval requirements.

## Required Checks

- Auth
- Authorization
- Secrets
- PII
- API keys
- RLS policies if Supabase/Postgres
- Injection risks
- Unsafe logs
- Dependency risk
- Deployment exposure

## Output Format

- Security verdict
- Findings by severity
- Required fixes
- Approval requirements
- Residual risk

## Stop Conditions

Stop if secrets are exposed, access control is unclear, or sensitive changes lack approval.
