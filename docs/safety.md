# Safety Rules

## Purpose

These rules keep AI-assisted coding scoped, reviewable, and reversible.

## Core Rules

- Do not run destructive commands without explicit approval.
- Do not make unrelated refactors during scoped work.
- Do not touch auth, billing, database schema, deployment, or secrets without naming the risk first.
- Do not commit secrets, tokens, credentials, or private env values.
- Do not make silent behavior changes.
- Do not create migrations without rollback notes.

## Allowed and Forbidden Files

Every non-trivial task should define:

- Allowed files: paths the agent may edit.
- Forbidden files: paths the agent must not edit.
- Approval files: sensitive paths that require explicit approval before editing.

If the needed change falls outside allowed files, stop and ask.

## Stop Conditions

Stop when:

- Scope becomes unclear.
- A forbidden file appears necessary.
- Tests fail for unclear reasons.
- A change touches sensitive data, auth, billing, deployment, or schema unexpectedly.
- The agent has tried repeated fixes without understanding the cause.

## Review Before Commit

Before commit, run a scope review, test review, secret check, docs drift check, and final `git status --short` plus `git diff --stat`.
