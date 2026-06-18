# KishoreStack: AI Engineering Workflow for EchoPersona / Living Forever AI

## 1. Purpose

This document defines the AI-assisted engineering workflow for EchoPersona / Living Forever AI.

The goal is not to use AI agents as autocomplete. The goal is to operate AI agents like a small engineering team while keeping the human in control of product judgment, architecture decisions, security decisions, and final shipping.

This workflow borrows the best ideas from Blueprint, gstack, Claude Code, Codex, CodeGraph, and Conductor, but adapts them to this project.

For this repo, correctness matters more than raw speed because the product handles:

* personal memories
* voice/persona identity
* family access
* consent and succession
* private user data
* posthumous or legacy interactions
* real-time conversations

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

Do not ask an agent to “just build the feature” unless the feature is small and low-risk.

---

## 3. Project-Specific Non-Negotiables

These rules override generic AI-agent workflows.

### Product/runtime rules

* No autonomous agents in the live product runtime.
* No unbounded agent loops in user-facing flows.
* Live reply path must stay low-latency.
* Persona replies must not fabricate facts outside verified memory.
* Ingestion and memory transformation happen off the hot path.
* Persona memory must remain auditable through provenance.
* Corrections must preserve history instead of overwriting it.
* Consent and succession decisions must be explicit, reviewable, and reversible where appropriate.

### Infrastructure rules

* Primary deployment target is private VPC / VPS with Docker Compose and nginx.
* Vercel/Render are secondary or experimental only unless explicitly changed.
* Supabase is used for auth, Postgres, and storage.
* Redis and arq worker are part of the real ingestion architecture.
* No paid APIs unless explicitly approved.
* Groq free tier is the default LLM/STT/vision provider.
* ElevenLabs and D-ID/Tavus are optional media layers.
* Stripe setup is paused unless explicitly resumed.

### Safety rules

* Do not touch migrations without explicit approval.
* Do not touch RLS/security policies without explicit approval.
* Do not touch billing/webhook logic without explicit approval.
* Do not touch WebSocket auth/live path without explicit approval.
* Do not run destructive commands without asking.
* Do not force-push unless explicitly instructed.
* Do not create large multi-file changes without a plan.
* Do not edit unrelated files to “clean things up” during a feature slice.

---

## 4. Source-of-Truth Files

Agents must read the right source files before starting.

### Always read

```txt
CLAUDE.md
PROGRESS.md
README.md
```

### Persona, memory, ingestion, retrieval

```txt
PERSONA_SPEC.md
backend/services/creation.py
backend/services/ingestion/
backend/worker/tasks/ingestion.py
backend/services/rag.py
backend/models/
backend/migrations/
```

### Deployment

```txt
docker-compose.yml
backend/Dockerfile
frontend/Dockerfile
nginx config
docs/runbook.md
backend/.env.example
frontend/.env.example
```

### Frontend and demo flow

```txt
frontend/src/router.tsx
frontend/src/pages/
frontend/src/components/
frontend/src/lib/api.ts
frontend/src/constants.ts
```

---

## 5. When to Spec

Create or update a spec when the work touches:

* database schema
* auth
* RLS
* consent
* succession
* billing
* WebSocket/live path
* ingestion
* persona memory
* retrieval
* correction/versioning
* deployment architecture
* multiple frontend/backend flows

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
Add one frontend page polish
Add one migration + model update
Add one deployment doc correction
```

A bad slice:

```txt
Build correction loop + consent + UI + deployment together
Refactor backend while adding a feature
Touch billing while fixing persona creation
Change schema, retrieval, and WebSocket logic in one pass
```

During implementation:

* obey allowed/forbidden files
* keep changes minimal
* do not add unrelated abstractions
* do not rewrite working systems without approval
* add tests for behavior, not implementation noise

---

## 8. Testing and Verification

### Backend

```bash
cd backend
python -m pytest tests/ -q
```

### Frontend

```bash
cd frontend
npx tsc --noEmit
npm run build
```

### Docker/VPC

```bash
docker compose config
docker compose build
docker compose up -d
curl https://kishoreai.online/health
```

### Browser-facing work

Browser-facing work needs browser verification, not only `npm run build`.

Check:

```txt
landing page
signup/login
dashboard
persona creation
persona detail
live chat
consent/succession
billing paused state
privacy/terms/404
mobile viewport
console errors
network errors
WebSocket connection
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
Does this break private VPC deployment?
Does this break WebSocket/live path?
Does this break persona fidelity?
Does this create unsupported facts or memory fabrication risk?
```

For risky backend work, use a second model or separate reviewer.

---

## 10. Documentation Rules

After meaningful changes, update relevant docs.

Common docs:

```txt
PROGRESS.md
README.md
CLAUDE.md
PERSONA_SPEC.md
docs/runbook.md
docs/architecture.md
backend/.env.example
frontend/.env.example
```

Do not create new markdown files unless the new document has a clear long-term role.

Avoid docs sprawl.

---

## 11. Specialist Review Modes

Use these lightweight modes instead of generic prompting.

### Product Review

Use before ambiguous product work.

```txt
Act as a product reviewer for Living Forever AI.

Check:
1. What user pain does this solve?
2. Is it needed for the next demo?
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

### Persona Fidelity Review

Use for memory, ingestion, correction, and retrieval.

```txt
Act as the persona fidelity reviewer.

Check:
1. no fabrication outside verified memory
2. source provenance
3. correction audit trail
4. listener-aware behavior
5. no-memory fallback
6. separation between ingestion-time and live-time logic

Flag any behavior that could make the twin say unsupported facts.
Do not code.
```

### Security Review

Use for auth, Supabase, uploads, billing, and deployment.

```txt
Act as a security reviewer.

Check:
1. auth bypass risk
2. service-role key exposure
3. Supabase RLS assumptions
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
3. dashboard
4. create persona
5. persona detail
6. live chat
7. consent/succession
8. billing paused state
9. privacy/terms/404
10. mobile viewport

Check:
- console errors
- network errors
- broken routes
- localhost URLs in production
- layout issues
- WebSocket connection
- broken buttons

Report only unless explicitly told to fix.
```

### VPC Deployment Review

Use before deploy/redeploy.

```txt
Act as VPC deployment reviewer.

Primary deployment target:
- private VPC/VPS
- Docker Compose
- nginx
- FastAPI backend
- React frontend
- Redis
- arq worker
- Supabase hosted
- kishoreai.online

Check:
1. Docker Compose services
2. nginx proxy routes
3. WebSocket upgrade headers
4. frontend env URLs
5. backend CORS
6. PUBLIC_BASE_URL
7. Redis/arq worker
8. health endpoint
9. secrets not committed
10. deployment docs match reality

Do not assume Vercel or Render.
```

### Documentation Release Review

Use after major changes.

```txt
Act as documentation release reviewer.

Inspect changed files and update only stale docs.

Check:
1. README
2. PROGRESS.md
3. CLAUDE.md
4. PERSONA_SPEC.md
5. docs/runbook.md
6. docs/architecture.md
7. backend/frontend .env.example files

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
RLS/auth changes
billing/webhooks
WebSocket/live path
persona memory schema
correction/versioning logic
ingestion worker changes
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
billing
RLS
WebSocket auth
persona memory correction
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
persona-fidelity-review
security-review
browser-qa
vpc-deploy-review
document-release
backend-safe-slice
frontend-safe-slice
```

Skills should encode process, not all project knowledge.

Project knowledge belongs in:

```txt
PERSONA_SPEC.md
docs/architecture.md
docs/runbook.md
PROGRESS.md
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
feature/correction-loop
feature/consent-succession
fix/vpc-deploy-docs
test/retrieval-supersedes
docs/ai-workflow
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

Run relevant checks.

Backend:

```bash
cd backend
python -m pytest tests/ -q
```

Frontend:

```bash
cd frontend
npx tsc --noEmit
npm run build
```

Commit only intended files:

```bash
git add <intended files only>
git commit -m "<type>: <clear message>"
```

Examples:

```txt
feat: add correction loop source records
fix: exclude superseded memory units from retrieval
docs: reconcile private VPC deployment guide
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

4. Run tests before building on top:

```bash
cd backend && python -m pytest tests/ -q
cd frontend && npx tsc --noEmit && npm run build
```

5. Continue only if the tree is clean or the partial state is understood.

---

## 18. Production Deployment Checklist

Primary deployment target:

```txt
private VPC / VPS
Docker Compose
nginx
kishoreai.online
```

Required services:

```txt
frontend
backend
redis
arq worker
nginx
```

Required backend env:

```txt
SUPABASE_URL
SUPABASE_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY
GROQ_API_KEY
ELEVENLABS_API_KEY
ELEVENLABS_VOICE_ID
REDIS_URL
CORS_ORIGINS=https://kishoreai.online
PUBLIC_BASE_URL=https://kishoreai.online
ENVIRONMENT=production
```

Optional backend env:

```txt
DID_API_KEY
SIMLI_API_KEY
TAVUS_API_KEY
DEEPGRAM_API_KEY
STRIPE_SECRET_KEY
STRIPE_WEBHOOK_SECRET
```

Required frontend env:

```txt
VITE_SUPABASE_URL
VITE_SUPABASE_ANON_KEY
VITE_API_BASE_URL=https://kishoreai.online
VITE_WS_BASE_URL=wss://kishoreai.online
```

nginx must support WebSockets:

```nginx
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
```

---

## 19. Demo Verification Script

Run after deployment.

```txt
1. Open https://kishoreai.online
2. Sign up or log in
3. Open dashboard
4. Create persona
5. Open persona detail
6. Start live chat
7. Confirm WebSocket connects
8. Confirm response appears
9. Confirm voice output if configured
10. Open consent/succession page
11. Open billing page but do not click Upgrade if Stripe is paused
12. Open privacy/terms
13. Open invalid route and confirm 404
14. Test mobile viewport
15. Check console/network errors
```

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
persona correction logic
retrieval rewrite
billing webhook changes
production deploy merge
```

---

## 21. Immediate Setup Plan

### Phase 1 — Add this workflow doc

Create:

```txt
docs/ai-operating-system.md
```

### Phase 2 — Add a short AGENTS.md

Create:

```txt
AGENTS.md
```

It should point agents to:

```txt
CLAUDE.md
PROGRESS.md
PERSONA_SPEC.md
docs/ai-operating-system.md
```

### Phase 3 — Add small project skills

Create lightweight local skills for:

```txt
product-review
eng-review
persona-fidelity-review
browser-qa
vpc-deploy-review
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

For this product:

```txt
speed is good
proof is better
user trust is mandatory
```

Agents can move fast.

The human still owns product judgment, architecture, security, schema decisions, and final deployment.
