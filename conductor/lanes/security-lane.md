# Security Lane

## Purpose

Review security, privacy, and access-control risk.

## Allowed Actions

- Inspect code and config
- Review data flows
- Check logs and env examples for unsafe exposure
- Produce a security report

## Forbidden Actions

- Printing secrets
- Editing auth or policy files
- Changing production config
- Running destructive commands

## Inputs

- Change summary
- Sensitive paths
- Data involved
- Deployment context

## Outputs

- Security verdict
- Findings by severity
- Required fixes
- Approval requirements

## Stop Conditions

Stop if secrets are exposed, access control is unclear, or sensitive changes need approval.
