# QA Skill

## Purpose

Define and run practical QA for changed behavior.

## When to Use

Use for user-facing changes, API behavior changes, bug fixes, and releases.

## Inputs Expected

- Change summary
- Affected flows
- Test environment
- Known risks

## Process

1. Build a small test matrix.
2. Test happy paths.
3. Test edge cases and error states.
4. Test regression cases.
5. Capture screenshots or notes when useful.
6. Verify fixes after bugs are addressed.

## Required Checks

- Happy path
- Edge cases
- Regression cases
- UI behavior if applicable
- API behavior if applicable
- Error states

## Output Format

- Test matrix
- Results
- Bugs found
- Reproduction steps
- Fix verification

## Stop Conditions

Stop and report if a blocker is found or the environment cannot verify the change.
