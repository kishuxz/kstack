# Adoption Guide

## Purpose

This guide explains how another project can consume kstack without copying the whole repo into its codebase.

## When to Use kstack

Use kstack when a project needs repeatable AI-assisted engineering workflows: scoped planning, safe implementation, reviews, verification reports, and handoffs.

Do not use kstack as a runtime dependency. It is a workflow reference, not a framework.

## Reference Pattern

Consumer projects should keep a small local `AGENTS.md` or `CLAUDE.md` that references kstack:

```md
Use kstack as the workflow source of truth:
- Read <path-or-url-to-kstack>/docs/ai-operating-system.md
- Use <path-or-url-to-kstack>/templates for prompt templates
- Use <path-or-url-to-kstack>/skills for role and workflow skills

Local project rules override generic kstack rules when they are stricter.
```

## Keep Local

Project-specific rules should stay in the consumer repo:

- Architecture boundaries
- Test commands
- Deployment commands
- Security-sensitive files
- Allowed and forbidden paths
- Product-specific quality gates
- Environment and secret handling

## Recommended Adoption Path

1. Read `docs/ai-operating-system.md`.
2. Add a small project-specific `AGENTS.md`.
3. Copy or reference only the templates needed.
4. Use read-only review lanes first.
5. Allow implementation lanes only after the workflow is stable.

## Minimal Adoption

- Add a local `AGENTS.md`.
- Reference kstack's default loop.
- Use `templates/feature-plan.md` and `templates/review-before-commit.md`.
- Require `git status`, `git diff --stat`, and relevant tests before commit.

## Full Adoption

- Add local agent rules.
- Adopt spec, plan, implement, review, QA, ship, and handoff templates.
- Use role-based reviews for security, QA, release, and technical writing.
- Add project-specific review gates.
- Track progress and verification reports.

## Product Repo Example

A product repo should reference kstack for process, then define local rules for routes, UI areas, API contracts, tests, auth, billing, deployment, and forbidden files.

## AI/RAG Product Example

An AI/RAG product should add local rules for retrieval quality, grounded responses, eval datasets, latency targets, user data boundaries, and fallback behavior.
