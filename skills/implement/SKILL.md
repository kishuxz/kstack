# Implement Skill

## Purpose

Implement an approved scoped plan with minimal, reviewable changes.

## When to Use

Use only after a plan is approved.

## Inputs Expected

- Approved plan
- Allowed files
- Forbidden files
- Test commands
- Stop conditions

## Process

1. Re-read the approved scope.
2. Edit only allowed files.
3. Follow existing project patterns.
4. Keep changes atomic and focused.
5. Update docs when behavior changes.
6. Run required verification.
7. Report results and remaining risks.

## Required Checks

- Stay within allowed files.
- No opportunistic refactors.
- No secrets or generated config.
- Tests or manual verification ran.

## Output Format

- Files changed
- Implementation summary
- Verification run
- Risks or gaps
- Suggested next step

## Stop Conditions

Stop if scope becomes unclear, forbidden files are needed, tests fail unexpectedly, or sensitive areas are touched.
