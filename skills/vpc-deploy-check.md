# VPC Deploy Check Skill

## Purpose

Review private VPC/VPS deployment readiness for Docker, nginx, app containers, workers, and runtime config.

## Use when

Use this for deployment review before or after a private VPC/VPS deploy.

## Instructions to the agent

1. Prefer read-only inspection unless edits are explicitly approved.
2. Check Docker Compose services.
3. Check nginx reverse proxy configuration.
4. Check frontend and backend container configuration.
5. Check Redis and arq worker configuration when applicable.
6. Check Supabase env names without printing secrets.
7. Check CORS and public URL configuration.
8. Check WebSocket upgrade headers where needed.
9. Check health verification and logs.
10. Recommend browser verification and rollback notes.

Report findings, risks, and any edit approvals needed.

## Required stop condition

Stop after the deployment review report. Do not edit config, restart services, or run destructive commands without approval.

## Template reference

Use `templates/vpc-deploy-check.md` for the full copy-paste prompt.
