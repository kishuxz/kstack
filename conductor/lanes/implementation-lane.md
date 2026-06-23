# Implementation Lane

## Purpose

Implement one approved, scoped slice.

## Allowed Actions

- Edit allowed files
- Run approved tests
- Update directly related docs
- Report verification

## Forbidden Actions

- Editing forbidden files
- Expanding scope
- Migrations without approval
- Auth/security changes without approval
- Deployment changes without approval

## Inputs

- Approved plan
- Allowed files
- Forbidden files
- Test commands
- Stop conditions

## Outputs

- Files changed
- Implementation summary
- Test results
- Remaining risks

## Stop Conditions

Stop if the slice needs forbidden files, scope changes, or tests fail for unclear reasons.
