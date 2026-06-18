# Docs Release Template

## Purpose

Update only stale documentation needed for a completed change or release.

## When to use

Use this after implementation or before release when docs may no longer match behavior, setup, architecture, or operations.

## Prompt template

```txt
Review docs for release readiness. Edit only stale docs.

Change or release scope:
<summary of shipped change or release>

Docs to check:
- README.md
- AGENTS.md
- CLAUDE.md
- PROGRESS.md
- docs/runbook.md
- docs/architecture.md
- env examples: <.env.example paths>

Allowed docs:
- <docs paths allowed for this pass>

Forbidden files:
- <product code, deployment files, generated files, unrelated docs>

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Docs rules:
1. Read the changed behavior and relevant docs.
2. Update only docs that are stale or misleading.
3. Keep docs concise and operational.
4. Avoid docs sprawl: do not create new docs unless necessary.
5. Keep env examples accurate without adding secrets.
6. Do not change product code.
7. Report docs checked, docs changed, and docs intentionally left unchanged.
```

## Required output

- Docs checked
- Docs changed
- Reason each changed doc was stale
- Docs intentionally left unchanged
- Env example changes, if any
- Remaining docs gaps
- Final `git diff --stat`

## Stop condition

Stop after updating stale docs and reporting results. Do not create new documentation categories without approval.

## Safety rules

- No product code edits.
- No secrets in docs or env examples.
- No speculative roadmap promises.
- No duplicate docs covering the same process.
- Do not rewrite stable docs for style alone.
