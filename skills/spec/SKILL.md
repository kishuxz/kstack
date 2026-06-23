# Spec Skill

## Purpose

Turn vague intent into a precise implementation spec.

## When to Use

Use before planning when the request is broad, ambiguous, user-facing, risky, or crosses multiple files.

## Inputs Expected

- Goal or problem statement
- Relevant user context
- Known constraints
- Source-of-truth docs and code paths

## Process

1. Read relevant docs and existing code.
2. Restate the problem in concrete terms.
3. Define scope and non-goals.
4. Identify likely files and systems involved.
5. Name risks, unknowns, and approval needs.
6. Write acceptance criteria.

## Required Checks

- Scope is small enough to plan.
- Non-goals are explicit.
- Sensitive areas are named.
- Acceptance criteria are testable.

## Output Format

- Problem
- User impact
- Scope
- Non-goals
- Files likely involved
- Risks
- Acceptance criteria

## Stop Conditions

Stop if the goal is unclear, source-of-truth files conflict, or sensitive areas need approval.
