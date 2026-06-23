# Release Lane

## Purpose

Check release readiness and prepare handoff.

## Allowed Actions

- Review status and diff
- Run approved verification
- Check docs and QA artifacts
- Prepare release notes and handoff

## Forbidden Actions

- Deploying without approval
- Restarting services without approval
- Committing without approval
- Ignoring failed checks

## Inputs

- Release scope
- Verification commands
- QA results
- Review results
- Rollback requirements

## Outputs

- Release verdict
- Verification summary
- Rollback notes
- Handoff

## Stop Conditions

Stop if required tests, reviews, docs, or rollback notes are missing.
