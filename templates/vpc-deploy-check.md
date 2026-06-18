# VPC Deploy Check Template

## Purpose

Review a private VPC/VPS deployment setup before or after deployment.

## When to use

Use this for deployment reviews involving Docker Compose, nginx, app containers, workers, environment variables, health checks, and browser verification.

## Prompt template

```txt
Review the VPC/VPS deployment setup. Prefer read-only inspection unless explicitly approved to edit.

Deployment target:
<VPC/VPS provider, host, or environment>

Allowed files:
- <docker-compose files>
- <nginx config>
- <deployment docs>
- <env examples>

Forbidden files:
- <product code unless explicitly allowed>
- <database migrations>
- <auth/security policies>

Verification commands:
- <docker compose ps/logs/config commands>
- <health check command>
- <browser verification steps>

Project overrides:
- <optional constraints: private VPC, persona fidelity, Supabase, WebSocket, no paid APIs>

Deployment checklist:
1. Check Docker Compose services for frontend, backend, Redis, and arq worker.
2. Check nginx reverse proxy configuration.
3. Confirm WebSocket upgrade headers are present where needed.
4. Confirm CORS origins match deployed frontend/backend URLs.
5. Confirm `PUBLIC_BASE_URL` or equivalent public URL config is correct.
6. Confirm Supabase env names are present without exposing secrets.
7. Confirm containers have health checks or documented health verification.
8. Confirm logs are inspectable for frontend/backend/worker failures.
9. Run or define browser verification for the deployed site.
10. Write rollback notes for the deployment.
```

## Required output

- Docker Compose findings
- nginx findings
- Frontend/backend container findings
- Redis/arq worker findings
- Supabase env findings
- CORS findings
- `PUBLIC_BASE_URL` findings
- WebSocket upgrade findings
- Health check result or command
- Browser verification result or plan
- Rollback notes
- Risks requiring approval before edits

## Stop condition

Stop after the deployment check report. Do not edit deployment files, restart services, or run destructive commands unless explicitly approved.

## Safety rules

- Do not print secrets.
- Do not modify live deployment config without approval.
- Do not restart production services unless explicitly approved.
- Do not run destructive Docker commands.
- Treat auth, migrations, billing, WebSocket live paths, and private data flows as high risk.
