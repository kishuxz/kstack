# Review Gates

## Purpose

Review gates define what must be true before a change ships.

## Required Gates

### Scope Gate

- The diff matches the approved goal.
- Allowed files were respected.
- Forbidden files were not changed.
- No unrelated refactors were included.

### Architecture Gate

- The change fits existing boundaries.
- Shared contracts remain compatible.
- New abstractions are justified by real complexity.

### Test Gate

- Relevant automated tests ran.
- Manual QA is documented when needed.
- Untested risk is named.

### Security Gate

- No secrets are committed.
- Auth, authorization, data access, and logging risks are reviewed.
- Sensitive files are changed only with explicit approval.

### AI Quality Gate

Required when model behavior, retrieval, memory, persona, or user trust is affected.

- Outputs are grounded where required.
- Fallback behavior is defined.
- Hallucination and unsafe behavior risks are reviewed.
- Evaluation coverage is documented.

### Documentation Gate

- User-facing behavior changes are documented.
- Setup, environment, deployment, and architecture docs are updated only when stale.

### Release Gate

- Verification report exists.
- Rollback notes are included when runtime behavior changes.
- Handoff notes exist for incomplete or risky work.

## Human Approval Required

Require explicit human approval for destructive commands, migrations, auth/security policy changes, billing/webhook changes, deployment changes, secrets handling, and production data access.

## Shipping Blockers

- Failing required tests
- Unexplained changes
- Secret exposure
- Unapproved sensitive-area changes
- Missing rollback notes for migrations or deployment changes
- Known critical bug without a mitigation
