# Project CODEX.md Template

Use kstack as the process reference for Codex sessions.

## Required Context

- kstack workflow: `<path-or-url-to-kstack>/docs/ai-operating-system.md`
- Local agent rules: `AGENTS.md`
- Project docs: `<paths>`

## Codex Behavior

- Inspect code before planning.
- Ask approval before implementation when requested.
- Use `rg` for search when available.
- Avoid unrelated refactors.
- Preserve user changes.
- Run verification commands before final report.

## Standard Checks

```sh
git status --short
git diff --stat
<project test command>
```

## Local Overrides

- `<sensitive files>`
- `<forbidden commands>`
- `<test commands>`
- `<deployment constraints>`
