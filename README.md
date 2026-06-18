# kstack

kstack is a lightweight, reusable AI engineering operating system for running AI-assisted software work with clear scope, review, and verification.

It is a personal workflow repo inspired by Blueprint, gstack-style workflows, Claude Code, Codex, CodeGraph, and Conductor. The goal is not to vendor or install those tools here. The goal is to keep a small set of durable operating rules, prompts, and templates that other projects can reference.

EchoPersona / Living Forever AI is the first example consumer project, but kstack should remain generic enough for future projects.

## Default Loop

```txt
Think -> Spec -> Plan -> Implement -> Test -> Review -> Document -> Commit -> Verify
```

Every meaningful change should have a clear goal, small scope, allowed files, forbidden files, verification proof, and review before shipping.

## How Projects Consume kstack

Consumer projects should reference this repo from their own `AGENTS.md`, `CLAUDE.md`, or equivalent agent instruction file instead of copying the entire workflow into each project.

Project-specific files should stay small. They should point to kstack for the general process, then add only the local rules that matter for that codebase, such as architecture boundaries, deployment constraints, security-sensitive areas, and test commands.

## Recommended Adoption Path

1. Read `docs/ai-operating-system.md`.
2. Add a small project-specific `AGENTS.md`.
3. Create only the skills/templates needed.
4. Use Conductor first for read-only review lanes.
5. Allow code-editing lanes only after workflow is stable.

## Current Status

kstack is an early personal workflow repo. Expect the structure to stay lightweight while the process is tested against real project work.
