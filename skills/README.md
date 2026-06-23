# Skills

This folder will contain reusable skill prompts for AI-assisted engineering workflows.

Skills should encode process, review standards, and execution patterns. They should not encode project-specific knowledge that belongs in a consumer repo.

## Structure

- Root `*.md` files are short skill wrappers that point to matching templates.
- `*/SKILL.md` directories are reusable skill definitions for tools or agents that expect skill folders.

## Wrapper Skills

- `backend-safe-slice.md`
- `docs-release.md`
- `feature-plan.md`
- `frontend-safe-slice.md`
- `interrupted-session.md`
- `review-before-commit.md`
- `vpc-deploy-check.md`

## Core Skill Directories

- `spec/`
- `plan/`
- `implement/`
- `review/`
- `qa/`
- `ship/`
- `investigate/`
- `code-quality/`
- `security-review/`
- `document-release/`
- `retro/`

## AI Product Skill Directories

- `ai-quality-review/`
- `rag-review/`
- `persona-fidelity-review/`
- `latency-review/`
- `memory-safety-review/`
