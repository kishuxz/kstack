# Review Before Commit Template

## Purpose

Review a completed change before committing so scope, safety, tests, and docs are checked.

## When to use

Use this after implementation and before `git commit`.

## Prompt template

```txt
Review the current working tree before commit. Do not commit yet.

Original goal:
<goal or ticket>

Allowed files:
- <allowed files or directories>

Forbidden files:
- <forbidden files or directories>

Expected verification:
- <test/typecheck/build/manual QA commands>

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Review checklist:
1. Compare the diff against the original goal.
2. Confirm no forbidden files were changed.
3. Confirm tests are meaningful and related to the change.
4. Check for secrets, tokens, credentials, and accidental env values.
5. Check migrations and schema changes.
6. Check auth, security, permissions, and access control impact.
7. Check deployment/config/runtime impact.
8. Check docs drift and whether docs updates are needed.
9. Run final `git status --short`.
10. Run final `git diff --stat`.

Report findings before any commit.
```

## Required output

- Scope match: pass/fail with notes
- Forbidden files: pass/fail with paths
- Tests: commands and results
- Secrets check: pass/fail
- Migrations/schema: pass/fail
- Auth/security: pass/fail
- Deployment impact: pass/fail
- Docs drift: pass/fail
- Final `git status --short`
- Final `git diff --stat`
- Commit readiness recommendation

## Stop condition

Stop after the review report. Do not commit unless explicitly asked.

## Safety rules

- Do not hide failing tests.
- Do not ignore unexpected file changes.
- Do not approve changes that modify forbidden files.
- Do not commit secrets or generated tool artifacts.
- Treat migrations, auth, billing, and deployment changes as high risk.
