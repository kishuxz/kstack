# kstack

kstack is a lightweight, reusable AI engineering operating system for running AI-assisted software work with clear scope, review, and verification.

It is a personal workflow repo inspired by Blueprint, gstack-style workflows, Claude Code, Codex, CodeGraph, and Conductor. The goal is not to vendor or install those tools here. The goal is to keep a small set of durable operating rules, prompts, and templates that other projects can reference.

Project-specific examples live under `examples/` and should not define the core identity of kstack.

## What kstack Is

- Markdown-first workflow docs
- Reusable skills and prompt templates
- Review gates for safer AI-assisted coding
- Lightweight conductor lane and playbook definitions
- Practical handoff, verification, and release artifacts

## What kstack Is Not

- Not a gstack clone
- Not a runtime framework
- Not an installer or toolchain manager
- Not a place for product-specific source code
- Not a substitute for human approval on risky changes

## Quick Start

1. Read `docs/ai-operating-system.md`.
2. Read `docs/adoption-guide.md`.
3. Add a small project-local `AGENTS.md` or `CLAUDE.md`.
4. Reference kstack templates instead of copying everything.
5. Start with planning and read-only review workflows.

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

## Core Skills

| Skill | Use |
| --- | --- |
| `skills/spec/SKILL.md` | Turn vague intent into a precise spec. |
| `skills/plan/SKILL.md` | Turn a spec into an implementation plan. |
| `skills/implement/SKILL.md` | Implement an approved safe slice. |
| `skills/review/SKILL.md` | Review correctness and maintainability. |
| `skills/qa/SKILL.md` | Run manual and automated QA. |
| `skills/ship/SKILL.md` | Prepare release and handoff. |
| `skills/investigate/SKILL.md` | Debug before fixing. |
| `skills/code-quality/SKILL.md` | Review code quality using project commands. |
| `skills/security-review/SKILL.md` | Review security and privacy risk. |

## AI Product Skills

| Skill | Use |
| --- | --- |
| `skills/ai-quality-review/SKILL.md` | Review model behavior and user trust. |
| `skills/rag-review/SKILL.md` | Review retrieval and grounding. |
| `skills/persona-fidelity-review/SKILL.md` | Review persona consistency and boundaries. |
| `skills/latency-review/SKILL.md` | Review user-perceived latency. |
| `skills/memory-safety-review/SKILL.md` | Review memory access, deletion, and leakage risk. |

## Review Gates

Use `docs/review-gates.md` before shipping meaningful changes. At minimum, check scope, architecture, tests, security, docs, release readiness, and AI quality when applicable.

## Consumer Project Example

Consumer projects should keep local rules local:

```md
Use kstack for process:
- docs/ai-operating-system.md
- templates/
- skills/

Local overrides:
- Test commands
- Sensitive files
- Deployment constraints
- Product-specific review gates
```

## Suggested First Use

Start by creating a project-local `AGENTS.md`, review gates, and verification commands. Use `examples/` only as isolated reference material for consumer projects.

## Roadmap

- Keep improving Markdown skills and templates.
- Add more examples only when they remain generic or clearly isolated.
- Add lightweight scripts later if repeated manual checks justify them.
- Avoid heavy runtime tooling until the workflow proves it needs it.

## Current Status

kstack is an early personal workflow repo. Expect the structure to stay lightweight while the process is tested against real project work.
