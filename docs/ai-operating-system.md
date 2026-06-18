# KishoreStack: AI Engineering Workflow

## 1. Purpose

This document defines the AI-assisted engineering workflow for projects using kstack.

The goal is not to use AI agents as autocomplete. The goal is to operate AI agents like a small engineering team while keeping the human in control of product judgment, architecture decisions, security decisions, and final shipping.

This workflow borrows the best ideas from Blueprint, gstack, Claude Code, Codex, CodeGraph, and Conductor, and is designed to be adapted to each consumer project.

A fast AI workflow is useful only if it produces reliable, reviewable, and trustworthy changes.

---

## 2. Core Operating Model

Default workflow:

```txt
Think → Spec → Plan → Implement → Test → Review → Document → Commit → Verify
```

Every meaningful change should have:

1. Clear goal
2. Small scope
3. Files allowed
4. Files forbidden
5. Tests or verification proof
6. Review before commit
7. Progress update

Do not ask an agent to "just build the feature" unless the feature is small and low-risk.

---

## 3. Project-Specific Non-Negotiables

These rules are defined per consumer project and override generic AI-agent workflows. Consumer projects must define their own version of this section in their `AGENTS.md` or `CLAUDE.md`.

A consumer project's non-negotiables should cover:

### Product/runtime rules

Define constraints specific to your product's reliability, correctness, and user trust requirements. Examples:

* No autonomous agents in the live product runtime.
* No unbounded agent loops in user-facing flows.
* Data mutations must be auditable.
* Domain-critical logic must not produce results outside verified sources.

### Infrastructure rules

Define your deployment target, required services, approved external APIs, and any cost constraints. Examples:

* Primary deployment target (cloud provider, container platform, managed service, etc.)
* Required backing services (database, cache, queue, etc.)
* Approved and forbidden external APIs
* Cost guardrails

### Safety rules

Define the actions agents must never take without explicit human approval. Examples:

* Do not touch migrations without explicit approval.
* Do not touch auth/security policies without explicit approval.
* Do not touch billing/webhook logic without explicit approval.
* Do not run destructive commands without asking.
* Do not force-push unless explicitly instructed.
* Do not create large multi-file changes without a plan.
* Do not edit unrelated files to "clean things up" during a feature slice.

---

## 4. Source-of-Truth Files

Agents must read the right source files before starting. Consumer projects should define their own list. A typical set includes:

### Always read

```txt
CLAUDE.md (or AGENTS.md)
PROGRESS.md
README.md
```

### Domain-critical paths

List the files that define your project's core domain logic, data models, and configuration. This will vary by project.

### Deployment

```txt
docker-compose.yml (or equivalent)
Dockerfile(s)
reverse-proxy config
docs/runbook.md
.env.example files
```

### Application entry points

List your project's key routing, page, and API files here.

---

## 5. When to Spec

Create or update a spec when the work touches:

* database schema
* auth or access control
* billing or payments
* real-time or live-path logic
* data ingestion or transformation
* domain-critical retrieval or ranking
* correction or versioning logic
* deployment architecture
* multiple interconnected flows

A spec should include:

```txt
Goal
Non-goals
User flow
Data model changes
API changes
Failure modes
Test strategy
Rollout plan
```

Do not create specs for trivial copy changes or tiny UI fixes.

---

## 6. Planning Rules

Before coding, the agent must produce a plan.

The plan should include:

```txt
Files to inspect
Files likely to change
Files forbidden
Implementation slices
Tests to run
Manual verification
Risks
Stop condition
```

The agent should not code during the planning step.

If the plan reveals that the instruction is wrong or stale, stop and update the task/spec before implementing.

---

## 7. Implementation Rules

Implement one slice at a time.

A good slice:

```txt
Add one backend service + tests
Add one endpoint + tests
Add one frontend page or component
Add one migration + model update
Add one deployment doc correction
```

A bad slice:

```txt
Build multiple interconnected features together
Refactor backend while adding a feature
Touch billing while fixing unrelated logic
Change schema, retrieval, and live-path logic in one pass
```

During implementation:

* obey allowed/forbidden files
* keep changes minimal
* do not add unrelated abstractions
* do not rewrite working systems without approval
* add tests for behavior, not implementation noise

---

## 8. Testing and Verification

Consumer projects should define their own test commands. The general pattern:

### Backend

```bash
# Run project backend tests
<project test command>
```

### Frontend

```bash
# Run type checks and build
<project type check command>
<project build command>
```

### Deployment

```bash
# Validate and start services
<project compose or deploy command>
curl <project health endpoint>
```

### Browser-facing work

Browser-facing work needs browser verification, not only a build check.

Check:

```txt
landing page
signup/login
primary user flows
main app view
mobile viewport
console errors
network errors
real-time connections (if applicable)
```

---

## 9. Review Rules

Before committing, run a fresh review.

Review checklist:

```txt
Did the change match the requested scope?
Were forbidden files untouched?
Are tests meaningful?
Are migrations safe/idempotent?
Are secrets exposed?
Does this break the deployment target?
Does this break any real-time or live-path logic?
Does this violate any domain-critical correctness rules?
```

For risky backend work, use a second model or separate reviewer.

---

## 10. Documentation Rules

After meaningful changes, update relevant docs.

Common docs:

```txt
PROGRESS.md
README.md
CLAUDE.md or AGENTS.md
docs/runbook.md
docs/architecture.md
.env.example files
```

Do not create new markdown files unless the new document has a clear long-term role.

Avoid docs sprawl.

---

## 11. Specialist Review Modes

Use these lightweight modes instead of generic prompting.

### Product Review

Use before ambiguous product work.

```txt
Act as a product reviewer for this project.

Check:
1. What user pain does this solve?
2. Is it needed for the next milestone?
3. What is the smallest useful version?
4. What trust/safety risk does it create?
5. What can be deferred?
6. What acceptance criteria prove it worked?

Return: Build / Defer / Reject.
Do not code.
```

### Engineering Review

Use before backend/schema/live-path work.

```txt
Act as the engineering reviewer.

Review:
1. architecture correctness
2. data flow
3. failure modes
4. testability
5. rollback safety
6. latency impact
7. security boundaries
8. deployment impact

Return blockers, risks, and implementation slices.
Do not code.
```

### Domain Integrity Review

Use for domain-critical logic, data correctness, and retrieval or transformation pipelines.

```txt
Act as the domain integrity reviewer.

Check:
1. no fabrication or output outside verified sources
2. source provenance and traceability
3. correction and audit trail
4. fallback behavior when data is missing
5. separation between write-time and read-time logic

Flag any behavior that violates the project's domain correctness rules.
Do not code.
```

### Security Review

Use for auth, data access, uploads, billing, and deployment.

```txt
Act as a security reviewer.

Check:
1. auth bypass risk
2. credential or key exposure
3. access control assumptions
4. unsafe file upload paths
5. webhook spoofing
6. CORS mistakes
7. secrets in git
8. destructive SQL
9. user data leakage
10. privilege escalation

Return severity-ranked findings.
Do not code unless explicitly approved.
```

### Browser QA

Use after frontend/demo-facing changes.

```txt
Act as browser QA.

Test the app in a real browser.

Flows:
1. landing page
2. signup/login
3. primary user flows
4. main app view
5. error states and 404
6. mobile viewport

Check:
- console errors
- network errors
- broken routes
- localhost URLs in production
- layout issues
- real-time connections (if applicable)
- broken buttons

Report only unless explicitly told to fix.
```

### Deployment Review

Use before deploy/redeploy.

```txt
Act as deployment reviewer.

Check:
1. all required services are defined
2. reverse-proxy routes are correct
3. real-time upgrade headers (if applicable)
4. frontend env URLs point to production
5. backend CORS is correct
6. health endpoint is reachable
7. secrets are not committed
8. deployment docs match reality

Adapt checks to the project's actual deployment target.
Do not assume a specific cloud provider or platform.
```

### Documentation Release Review

Use after major changes.

```txt
Act as documentation release reviewer.

Inspect changed files and update only stale docs.

Check:
1. README
2. PROGRESS.md
3. CLAUDE.md or AGENTS.md
4. docs/runbook.md
5. docs/architecture.md
6. .env.example files

Do not invent new architecture.
Do not create new docs unless necessary.
Report what changed and why.
```

---

## 12. Conductor Usage

Conductor is allowed, but it must be used carefully.

Default rule:

```txt
Use one primary coding agent for implementation.
Use Conductor mostly for independent review/reporting lanes.
```

Conductor is useful when work can be separated cleanly.

### Good Conductor lanes

Use Conductor for:

```txt
browser QA report
docs drift review
security review
deployment audit
test gap report
design feedback
performance review
copy polish suggestions
```

These are mostly read-only or isolated.

### Avoid Conductor for core stateful work

Do not run multiple coding agents in parallel on:

```txt
database migrations
auth/access control changes
billing/webhooks
real-time or live-path logic
domain-critical schema changes
correction/versioning logic
data ingestion pipeline changes
retrieval/ranking logic
```

These require one coding agent, one reviewer, and human approval.

### Conductor coordinator rule

When using Conductor, one session should act as coordinator.

Coordinator responsibilities:

```txt
1. read PROGRESS.md and current goal
2. split work into independent lanes
3. ensure no file overlap
4. assign clear worker prompts
5. collect reports
6. recommend next action
```

The coordinator should not edit code.

### Conductor worker rule

Each worker should:

```txt
1. work on exactly one lane
2. respect allowed/forbidden files
3. run relevant checks
4. report evidence
5. stop before commit unless instructed
```

Detailed Conductor lane prompts can live later in:

```txt
docs/conductor-playbook.md
```

Do not create that file until Conductor becomes part of regular workflow.

---

## 13. Loop Engineering

The goal is to reduce repetitive prompting by turning repeated workflows into loops.

A loop is:

```txt
input → plan → implement → verify → review → stop
```

A loop is not permission for the agent to do anything it wants.

### Good loop candidates

```txt
docs cleanup
browser QA report
test gap report
security review
deployment checklist
copy polish
small frontend fixes
non-critical refactors
```

### Bad loop candidates

```txt
migrations
billing changes
auth/access control changes
real-time or live-path logic
domain-critical data corrections
retrieval rewrite
production deploy merge
```

Those require explicit human approval.

---

## 14. Suggested Project Skills

Create short project-specific skills or prompt files.

Recommended:

```txt
product-review
eng-review
domain-integrity-review
security-review
browser-qa
deploy-review
document-release
backend-safe-slice
frontend-safe-slice
```

Skills should encode process, not all project knowledge.

Project knowledge belongs in:

```txt
docs/architecture.md
docs/runbook.md
PROGRESS.md
project-specific spec files
```

---

## 15. Branching Strategy

For solo development:

```txt
main = stable
feature branches = optional for risky features
small commits = required
```

Recommended branch names:

```txt
feature/<feature-name>
fix/<fix-description>
test/<test-area>
docs/<doc-topic>
```

For Conductor:

```txt
conductor/browser-qa
conductor/docs-drift
conductor/security-review
conductor/test-gap-review
```

Do not let multiple Conductor lanes edit the same files.

---

## 16. Commit Rules

Before commit:

```bash
git status
git diff --stat
```

Run relevant checks for your project (type checks, unit tests, build).

Commit only intended files:

```bash
git add <intended files only>
git commit -m "<type>: <clear message>"
```

Examples:

```txt
feat: add data correction records
fix: exclude stale entries from retrieval
docs: reconcile deployment guide
test: cover ingestion provenance handoff
```

---

## 17. Interrupted Session Protocol

If an agent crashes, hits context limit, or stops mid-task:

1. Do not continue blindly.
2. Run:

```bash
git status
git diff --stat
git log --oneline -5
```

3. Classify the state:

```txt
committed
uncommitted-complete
uncommitted-partial
nothing changed
```

4. Run project tests before building on top.

5. Continue only if the tree is clean or the partial state is understood.

---

## 18. Deployment Checklist

Consumer projects should define their own deployment checklist. A generic pattern:

```txt
Deployment target: <cloud/VPS/managed service>
Required services: <list>
Required env vars: <list>
Optional env vars: <list>
Health check: curl <health endpoint>
```

Define this in the consumer project's `docs/runbook.md` or deployment docs.

---

## 19. App Verification Checklist

Run after deployment.

```txt
1. Open the app root URL
2. Sign up or log in
3. Complete primary user flows
4. Confirm real-time connections (if applicable)
5. Open error/404 pages
6. Test mobile viewport
7. Check console and network errors
```

Consumer projects should expand this with product-specific flows.

---

## 20. What to Automate First

Automate first:

```txt
browser QA report
docs drift report
security review
test gap report
deployment checklist
```

Do not automate yet:

```txt
schema migrations
domain-critical data corrections
retrieval or ranking rewrites
billing/webhook changes
production deploy merge
```

---

## 21. Adoption Checklist

Use this when adopting kstack for a new project.

### Phase 1 — Reference this workflow doc

Add a reference to `docs/ai-operating-system.md` in the consumer project's `AGENTS.md`.

### Phase 2 — Add a short project AGENTS.md

The project `AGENTS.md` should point agents to:

```txt
CLAUDE.md
PROGRESS.md
docs/ai-operating-system.md
project-specific spec or architecture files
```

### Phase 3 — Add small project skills

Create lightweight local skills for:

```txt
product-review
eng-review
domain-integrity-review
browser-qa
deploy-review
document-release
```

### Phase 4 — Use Conductor only for reports first

Start with read-only lanes:

```txt
browser QA
docs drift
security review
deployment audit
test gap review
```

Only allow Conductor to edit code after the workflow is stable.

---

## 22. Golden Rule

A fast AI workflow is useful only if it creates less chaos than it removes.

```txt
speed is good
proof is better
user trust is mandatory
```

Agents can move fast.

The human still owns product judgment, architecture, security, schema decisions, and final deployment.
