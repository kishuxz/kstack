# Project AGENTS.md Template

Use kstack as the shared AI engineering workflow reference.

## kstack Reference

- Read `<path-or-url-to-kstack>/docs/ai-operating-system.md`.
- Use `<path-or-url-to-kstack>/templates/` for task prompts.
- Use `<path-or-url-to-kstack>/skills/` for workflow and review skills.

## Local Project Rules

- Project name: `<name>`
- Architecture docs: `<paths>`
- Test commands: `<commands>`
- Build commands: `<commands>`
- Deployment docs: `<paths>`
- Sensitive files: `<paths>`

## Required Workflow

Use:

```txt
Think -> Spec -> Plan -> Implement -> Test -> Review -> Document -> Commit -> Verify
```

For meaningful changes, define allowed files, forbidden files, tests, and stop conditions before implementation.

## Project Overrides

Local rules override kstack when stricter:

- `<auth rules>`
- `<data rules>`
- `<deployment rules>`
- `<AI quality rules>`

## Stop Conditions

Stop and ask before destructive commands, sensitive file changes, scope expansion, migrations, deployment changes, or unclear failures.
