# Release Process

## Purpose

This process defines how kstack expects a change to move from finished work to a reviewed handoff.

## Steps

1. Sync main or confirm the branch is current enough for the release.
2. Confirm the approved scope and non-goals.
3. Run relevant tests and checks.
4. Run review using `templates/review-before-commit.md`.
5. Run QA for affected user flows.
6. Update only stale docs.
7. Prepare a change summary.
8. Commit only when explicitly approved or when the repo workflow requires it.
9. Verify the committed state or final working tree.
10. Write handoff notes for remaining risk or follow-up work.

## Required Artifacts

- Change summary
- Verification report
- QA notes when user-facing behavior changed
- Rollback notes when deployment, schema, or runtime behavior changed
- Decision record when an important tradeoff was made
