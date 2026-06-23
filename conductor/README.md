# Conductor

Conductor should initially be used for read-only and reporting lanes. Code-editing lanes should wait until the workflow is stable and explicitly approved.

## Safe Initial Lanes

- Browser QA
- Docs drift
- Security review
- Deployment audit
- Test gap review

## Unsafe Lanes Unless Explicitly Approved

- Migrations
- RLS/auth
- Billing/webhooks
- WebSocket/live path
- Persona memory schema
- Correction/versioning
- Ingestion worker

## Roles

The coordinator defines the goal, scope, allowed files, forbidden files, and expected report format.

Workers inspect assigned areas and return findings, risks, evidence, and suggested next steps. Workers should not make changes unless the lane explicitly allows editing.

## Lane Definitions

- `lanes/read-only-review.md`
- `lanes/implementation-lane.md`
- `lanes/qa-lane.md`
- `lanes/security-lane.md`
- `lanes/docs-lane.md`
- `lanes/release-lane.md`

## Playbooks

- `playbooks/feature-sprint.md`
- `playbooks/bug-fix-sprint.md`
- `playbooks/refactor-sprint.md`
- `playbooks/release-sprint.md`

These are workflow definitions only. They do not configure Conductor or install tooling.
