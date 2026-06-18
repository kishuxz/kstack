# Interrupted Session Template

## Purpose

Recover safely from an interrupted or inherited work session before continuing.

## When to use

Use this when resuming work after a crash, handoff, context loss, branch switch, or unfinished agent session.

## Prompt template

```txt
Recover the current repo state before continuing. Do not edit files yet.

Original or suspected goal:
<goal if known, otherwise "unknown">

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Recovery steps:
1. Run `git status --short`.
2. Run `git diff --stat`.
3. Run `git log --oneline -5`.
4. Inspect changed files relevant to the suspected goal.
5. Classify the state as one of:
   - committed
   - uncommitted-complete
   - uncommitted-partial
   - nothing changed
6. Identify any broken, partial, conflicting, or unexplained work.
7. Run relevant tests before continuing if there are changes.
8. Do not build on broken or partial work.
9. Produce a recovery plan with next safe actions.

Do not modify files until the recovery plan is accepted.
```

## Required output

- `git status --short`
- `git diff --stat`
- `git log --oneline -5`
- State classification
- Changed files summary
- Test commands run and results
- Broken or partial work found
- Recovery plan
- Approval question before continuing

## Stop condition

Stop after the recovery plan and approval question. Do not continue implementation until approved.

## Safety rules

- Do not overwrite unexplained changes.
- Do not revert user work unless explicitly asked.
- Do not continue from failing tests without reporting them.
- Do not assume uncommitted work is complete.
- Do not commit during recovery.
