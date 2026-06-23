# EchoPersona Example AGENTS.md

This is an example of how an AI-native product could consume kstack. It is not a core kstack rule.

## kstack Reference

- Read `docs/ai-operating-system.md` in the kstack repo.
- Use kstack templates for planning, safe slices, reviews, QA, and release handoff.
- Keep EchoPersona-specific rules in this example or in the real product repo.

## Local Product Rules

- Treat auth, Supabase, memory, persona behavior, family access, voice, and deployment as sensitive.
- Define allowed and forbidden files before implementation.
- Use read-only review lanes first for risky areas.
- Require human approval before migrations, RLS/auth changes, billing changes, deployment changes, or production data access.

## AI Quality Rules

- Persona replies should be grounded in known memory or clearly state uncertainty.
- Memory changes should preserve auditability.
- Family-member access rules should be explicit.
- Latency-sensitive conversation flows should be reviewed before release.

## Stop Conditions

Stop when a change touches sensitive data, live conversation paths, memory schema, deployment, or access control without approval.
