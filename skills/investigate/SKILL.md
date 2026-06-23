# Investigate Skill

## Purpose

Find root cause before attempting a fix.

## When to Use

Use for bugs, regressions, flaky behavior, production incidents, and unclear failures.

## Inputs Expected

- Symptom
- Reproduction steps
- Logs or errors
- Recent changes
- Expected behavior

## Process

1. Reproduce the issue first.
2. Record the observed behavior.
3. Form hypotheses.
4. Test one hypothesis at a time.
5. Identify the smallest credible fix.
6. Ask for review after repeated failed fixes.

## Required Checks

- No fix before investigation.
- Reproduction attempt is recorded.
- Evidence supports the root cause.
- Failed hypotheses are documented.

## Output Format

- Reproduction result
- Evidence
- Hypotheses tested
- Root cause
- Suggested fix
- Verification plan

## Stop Conditions

Stop after repeated failed fixes, unclear evidence, or discovery of sensitive-risk changes.
