# Frontend Safe Slice Template

## Purpose

Implement one small frontend slice while preserving routing, responsiveness, and production-safe configuration.

## When to use

Use this for pages, components, API clients, hooks, frontend types, styling, and frontend tests.

## Prompt template

```txt
You are implementing one frontend slice only.

Goal:
<specific frontend change>

Allowed files:
- <pages/components/API client/types/test paths>

Forbidden files:
- <backend paths>
- <deployment files unless explicitly allowed>
- <database/migration/security files>

Verification commands:
- Typecheck: <command>
- Build: <command>
- Tests: <command or "not applicable">

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Implementation rules:
1. Inspect existing frontend patterns before editing.
2. Modify only allowed frontend files.
3. Do not edit backend code.
4. Preserve existing routes and navigation.
5. Do not hardcode localhost URLs for production behavior.
6. Keep API client and type changes compatible with existing backend contracts.
7. Check responsive/mobile layout for changed screens.
8. Run typecheck and build commands.
9. Recommend browser QA for changed user-facing flows.
10. Report changed files, commands, and results.
```

## Required output

- Files changed
- UI behavior changed
- API client/type changes
- Responsive/mobile checks performed
- Typecheck/build/test command results
- Browser QA recommendation or result
- Residual risks

## Stop condition

Stop after one frontend slice is implemented and verified. Do not edit backend files or begin another slice without approval.

## Safety rules

- No backend edits.
- No broken routing.
- No production localhost URLs.
- No unrelated restyling.
- No secrets or credentials.
- Do not suppress type errors without explaining why.
