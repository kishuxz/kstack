# Backend Safe Slice Skill

## Purpose

Implement one bounded backend change with focused tests and minimal blast radius.

## Use when

Use this for backend routes, services, models, schemas, workers, backend utilities, and backend tests.

## Instructions to the agent

1. Work on one backend slice only.
2. Inspect existing backend patterns before editing.
3. Modify only the allowed backend files.
4. Do not edit frontend or deployment files.
5. Do not create or edit migrations unless explicitly approved.
6. Do not edit RLS, auth, or security policies unless explicitly approved.
7. Mock external APIs in tests.
8. Do not add secrets, credentials, or real API keys.
9. Avoid unrelated refactors.
10. Run the required backend test command.

Report changed files, tests run, test results, and remaining risk.

## Required stop condition

Stop after one backend slice is implemented and tested. Do not begin another slice without approval.

## Template reference

Use `templates/backend-safe-slice.md` for the full copy-paste prompt.
