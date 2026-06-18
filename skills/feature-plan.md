# Feature Plan Skill

## Purpose

Create a scoped implementation plan before any code changes.

## Use when

Use this when a user asks for a new feature, behavior change, integration, or meaningful refactor and the next safe step is planning.

## Instructions to the agent

1. Do not edit files.
2. Read the project source-of-truth docs first.
3. Inspect relevant code before proposing a plan.
4. Identify the current behavior and architecture touchpoints.
5. List risks, edge cases, and unknowns.
6. Define allowed files and forbidden files.
7. Split the work into small implementation slices.
8. Define tests and verification for each slice.
9. Include any project overrides provided by the user.
10. Ask for approval before coding.

Keep the plan concrete. Use file paths, commands, and explicit assumptions.

## Required stop condition

Stop after delivering the plan and asking for approval. Do not code until approval is given.

## Template reference

Use `templates/feature-plan.md` for the full copy-paste prompt.
