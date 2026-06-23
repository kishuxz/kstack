# Plan Skill

## Purpose

Turn an approved spec into a step-by-step implementation plan.

## When to Use

Use after a spec exists and before editing files.

## Inputs Expected

- Approved spec
- Allowed files
- Forbidden files
- Test commands
- Project constraints

## Process

1. Inspect relevant code before planning.
2. Confirm scope and non-goals.
3. Define allowed and forbidden files.
4. Split work into small steps.
5. Define tests and verification.
6. Add rollback notes for risky changes.
7. List open questions.

## Required Checks

- Plan fits the approved scope.
- Sensitive areas have explicit approval.
- Tests are concrete commands or manual checks.
- Rollback plan exists when runtime behavior changes.

## Output Format

- Plan summary
- Allowed files
- Forbidden files
- Steps
- Test plan
- Rollback plan
- Open questions

## Stop Conditions

Stop after the plan. Do not implement until approved.
