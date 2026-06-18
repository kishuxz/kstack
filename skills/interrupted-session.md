# Interrupted Session Skill

## Purpose

Recover safely after a crash, context loss, branch switch, or inherited partial work.

## Use when

Use this when resuming an unclear worktree state or taking over from another session.

## Instructions to the agent

1. Do not edit files at first.
2. Run `git status --short`.
3. Run `git diff --stat`.
4. Run `git log --oneline -5`.
5. Inspect changed files relevant to the suspected goal.
6. Classify the state as committed, uncommitted-complete, uncommitted-partial, or nothing changed.
7. Identify broken, partial, conflicting, or unexplained work.
8. Run relevant tests before continuing when changes exist.
9. Do not build on broken or partial work.
10. Produce a recovery plan.

Ask before continuing implementation.

## Required stop condition

Stop after the recovery plan and approval question. Do not modify files until approved.

## Template reference

Use `templates/interrupted-session.md` for the full copy-paste prompt.
