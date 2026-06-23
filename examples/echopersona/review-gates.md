# EchoPersona Example Review Gates

These are example project-specific gates for an AI persona product.

## Required Gates

- Auth/Supabase review
- RAG review
- Persona fidelity review
- Memory safety review
- Latency review
- Voice pipeline review
- Family-member access review
- Deployment review

## Gate Expectations

### Auth/Supabase Review

Check auth flow, authorization, RLS policies, storage access, and environment variables.

### RAG Review

Check ingestion, chunking, retrieval quality, grounding, stale data, and privacy boundaries.

### Persona Fidelity Review

Check identity consistency, memory accuracy, tone, uncertainty handling, and hallucinated memories.

### Memory Safety Review

Check what is stored, who can access it, delete/export behavior, and cross-user leakage risk.

### Latency Review

Check conversation latency, streaming, model calls, database calls, and media pipeline delays.

### Voice Pipeline Review

Check STT/TTS quality, fallback behavior, consent, and user experience.

### Family-member Access Review

Check relationship permissions, succession rules, access revocation, and auditability.

### Deployment Review

Check Docker Compose, nginx, environment variables, CORS, WebSocket upgrades, workers, and rollback notes.
