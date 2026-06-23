# AI Quality Review Skill

## Purpose

Review user-facing AI behavior for quality, trust, and safety.

## When to Use

Use when prompts, models, retrieval, memory, fallback behavior, or AI output changes.

## Inputs Expected

- Feature summary
- Example prompts and outputs
- Evaluation results if available
- Safety or product constraints

## Process

1. Review model behavior against user expectations.
2. Check hallucination and grounding risk.
3. Check safety boundaries and fallback behavior.
4. Review eval coverage.
5. Identify user trust risks.

## Required Checks

- Model behavior
- Hallucination risk
- Grounding
- Safety boundaries
- Eval coverage
- Fallback behavior
- User trust

## Scorecard

Rate each relevant dimension from 1-10:

- Grounding
- Reliability
- Safety
- User trust
- Eval coverage
- Fallback quality

Verdict: Pass / Needs fixes / Block

## Output Format

- Verdict
- Scorecard
- Blockers
- Fixes needed
- Eval gaps

## Stop Conditions

Block if output can mislead users, violate safety boundaries, or lacks required grounding.
