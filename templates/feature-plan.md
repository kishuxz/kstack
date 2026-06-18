# Feature Plan Template

## Purpose

Plan a feature before implementation so scope, risks, files, and verification are explicit.

## When to use

Use this before coding any feature, behavior change, integration, or cross-file refactor.

## Prompt template

```txt
You are planning a feature. Do not edit files yet.

Goal:
<one-sentence goal>

Context:
- Project: <project name>
- User-facing behavior: <expected behavior>
- Non-goals: <what is explicitly out of scope>

Source of truth to read first:
- <README / AGENTS / CLAUDE / architecture docs>
- <relevant specs / tickets / docs>

Code to inspect before planning:
- <paths, modules, routes, components, tests, configs>

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Required planning steps:
1. Read the source-of-truth files listed above.
2. Inspect the relevant code before proposing implementation.
3. Summarize current behavior and relevant architecture.
4. Identify risks, edge cases, and security/privacy concerns.
5. List allowed files.
6. List forbidden files.
7. Split the work into small slices.
8. Define tests and verification commands for each slice.
9. Call out docs that may need updates.
10. Ask for approval before coding.

Do not implement until approval is given.
```

## Required output

- Current behavior summary
- Proposed approach
- Risks and mitigations
- Allowed files
- Forbidden files
- Work slices
- Test plan
- Docs impact
- Approval question

## Stop condition

Stop after the plan and approval question. Do not edit files, install tools, run migrations, or change configuration.

## Safety rules

- Do not code before approval.
- Do not expand scope beyond the stated goal.
- Do not touch forbidden files.
- Do not plan destructive commands.
- Mark unknowns clearly instead of guessing.
