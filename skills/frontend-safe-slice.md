# Frontend Safe Slice Skill

## Purpose

Implement one bounded frontend change while preserving routing, build health, and responsive behavior.

## Use when

Use this for pages, components, hooks, API clients, frontend types, styling, and frontend tests.

## Instructions to the agent

1. Work on one frontend slice only.
2. Inspect existing frontend patterns before editing.
3. Modify only the allowed frontend files.
4. Do not edit backend code.
5. Preserve existing routing and navigation.
6. Do not hardcode localhost URLs for production behavior.
7. Keep API client and type changes compatible with backend contracts.
8. Check responsive and mobile behavior for changed screens.
9. Run typecheck and build commands.
10. Recommend browser QA for user-facing changes.

Report changed files, verification commands, results, and any residual UI risk.

## Required stop condition

Stop after one frontend slice is implemented and typecheck/build have run. Do not begin another slice without approval.

## Template reference

Use `templates/frontend-safe-slice.md` for the full copy-paste prompt.
