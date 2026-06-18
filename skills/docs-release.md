# Docs Release Skill

## Purpose

Update only documentation that is stale after a change or release.

## Use when

Use this before release, after implementation, or when setup, architecture, runbooks, or env examples may be outdated.

## Instructions to the agent

1. Review the release or change scope.
2. Check relevant docs such as README, agent instructions, runbooks, architecture docs, progress notes, and env examples.
3. Edit only docs that are stale or misleading.
4. Keep changes concise and operational.
5. Do not create new docs unless necessary.
6. Do not duplicate existing docs.
7. Do not edit product code.
8. Do not add secrets to docs or env examples.
9. Report docs checked and docs changed.
10. Note docs intentionally left unchanged.

Avoid docs sprawl. Prefer updating existing docs.

## Required stop condition

Stop after stale docs are updated and the docs review is reported.

## Template reference

Use `templates/docs-release.md` for the full copy-paste prompt.
