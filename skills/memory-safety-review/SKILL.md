# Memory Safety Review Skill

## Purpose

Review how AI memory is stored, accessed, deleted, and audited.

## When to Use

Use when a change affects user memory, long-term context, profiles, personalization, or data retention.

## Inputs Expected

- Memory data model
- Access rules
- Delete/export behavior
- Audit/provenance design
- Sensitive data constraints

## Process

1. Identify what memory is stored.
2. Check who can access it.
3. Review delete and export behavior.
4. Check sensitive data handling.
5. Review cross-user leakage risk.
6. Check auditability.

## Required Checks

- What memory is stored
- Who can access it
- Delete/export behavior
- Sensitive data handling
- Cross-user leakage risk
- Family-member access rules when applicable
- Auditability

## Scorecard

Rate each relevant dimension from 1-10:

- Access safety
- Deletion/export clarity
- Sensitive data handling
- Leakage prevention
- Auditability
- User trust

Verdict: Pass / Needs fixes / Block

## Output Format

- Verdict
- Scorecard
- Data reviewed
- Blockers
- Fixes needed
- Approval requirements

## Stop Conditions

Block if memory can leak across users, cannot be deleted as required, or lacks clear access boundaries.
