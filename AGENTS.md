# Agent Instructions for kstack

Read `docs/ai-operating-system.md` first.

This repo contains reusable workflow docs, prompts, and templates only. Do not add product-specific code here.

Do not install or configure external tools unless explicitly asked. That includes gstack, Blueprint, Conductor, or tool-specific generated files.

Keep files concise, generic, and reusable across projects. Mention project-specific details only when they are examples, not requirements.

## kstack Rules

- kstack must stay lightweight, reusable, generic, and Markdown-first.
- Do not vendor project-specific product rules into core docs.
- Project-specific examples must stay under `examples/`.
- Prefer small Markdown workflows before adding tooling.
- Avoid copying gstack directly; use external tools only as inspiration.
- Keep naming consistent across docs, skills, templates, agents, and conductor lanes.

## Skill Requirements

Every `SKILL.md` should include:

- Purpose
- When to use
- Inputs expected
- Process
- Output format
- Stop conditions

## Change Expectations

Every meaningful change should update relevant docs, templates, or index files when behavior or structure changes. Do not add scripts, dependencies, generated config, or tool setup unless explicitly asked.
