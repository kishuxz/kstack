# Review Before Commit Skill

## Purpose

Review the current diff before commit and identify blockers, scope drift, or missing verification.

## Use when

Use this after implementation and before committing changes.

## Instructions to the agent

1. Review staged and unstaged changes.
2. Compare the diff against the original goal.
3. Confirm no forbidden files were changed.
4. Check whether tests are meaningful and related.
5. Check for secrets, tokens, credentials, and env leaks.
6. Check migrations and schema impact.
7. Check auth, security, permissions, and access control impact.
8. Check deployment and runtime impact.
9. Check documentation drift.
10. Report blockers before any commit.

Include final `git status --short` and `git diff --stat`.

## Required stop condition

Stop after the review report. Do not commit unless the user explicitly asks.

## Template reference

Use `templates/review-before-commit.md` for the full copy-paste prompt.
