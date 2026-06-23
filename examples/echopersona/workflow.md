# EchoPersona Example Workflow

This example shows one way EchoPersona could apply kstack.

## Default Loop

```txt
Think -> Spec -> Plan -> Implement -> Test -> Review -> Document -> Commit -> Verify
```

## Suggested Flow

1. Write a spec for the user-facing or AI behavior change.
2. Define allowed files, forbidden files, and sensitive approval areas.
3. Implement one slice at a time.
4. Run backend, frontend, and browser verification relevant to the slice.
5. Run AI quality review when prompts, memory, retrieval, or persona behavior changes.
6. Update docs only when stale.
7. Produce a change summary and verification report.

## Recommended kstack Templates

- `templates/feature-plan.md`
- `templates/backend-safe-slice.md`
- `templates/frontend-safe-slice.md`
- `templates/review-before-commit.md`
- `templates/AI_EVAL_REPORT.md`
- `templates/PERSONA_FIDELITY_REPORT.md`
- `templates/RAG_REVIEW_REPORT.md`

## Handoff

Every interrupted or risky session should leave a handoff with current state, tests run, gaps, and next safe step.
