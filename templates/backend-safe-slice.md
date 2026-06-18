# Backend Safe Slice Template

## Purpose

Implement one small backend slice with bounded files, tests, and rollback-friendly changes.

## When to use

Use this for backend routes, services, models, schemas, workers, and backend tests.

## Prompt template

```txt
You are implementing one backend slice only.

Goal:
<specific backend change>

Allowed files:
- <routes/services/models/tests paths>

Forbidden files:
- <frontend paths>
- <deployment files>
- <migrations unless explicitly approved>
- <RLS/auth/security policies unless explicitly approved>

Backend test command:
<command, e.g. pytest backend/tests/...>

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Implementation rules:
1. Inspect existing backend patterns before editing.
2. Modify only allowed files.
3. Keep the slice minimal and avoid unrelated refactors.
4. Do not add secrets, tokens, credentials, or real API keys.
5. Mock external APIs in tests.
6. Do not create or edit migrations without explicit approval.
7. Do not edit RLS, auth, or security policies without explicit approval.
8. Add or update focused backend tests.
9. Run the backend test command.
10. Report changed files, test results, and any residual risk.
```

## Required output

- Files changed
- Behavior changed
- Tests added or updated
- Backend test command and result
- External APIs mocked
- Explicit note on migrations/RLS/auth status
- Residual risks

## Stop condition

Stop after one backend slice is implemented and tested. Do not start a second slice without approval.

## Safety rules

- No secrets.
- No unrelated refactors.
- No frontend edits.
- No deployment edits.
- No migrations/RLS/auth/security edits unless explicitly approved.
- No real calls to paid or production external APIs in tests.
