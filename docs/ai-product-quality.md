# AI Product Quality

## Purpose

AI features need product quality checks beyond ordinary correctness.

## RAG Quality

Check ingestion, chunking, retrieval relevance, stale data, empty retrieval behavior, citation quality, and whether answers stay grounded in retrieved context.

## Persona Fidelity

Check identity consistency, memory accuracy, tone, relationship handling, refusal when unknown, and boundaries against unsafe impersonation.

## Hallucination Handling

AI responses should say when information is unknown, unavailable, or unsupported. Do not present guesses as facts.

## Memory Safety

Review what is stored, who can access it, how memory can be deleted or exported, and whether provenance is auditable.

## Latency

Measure user-perceived latency. Review streaming, cold starts, model calls, database calls, and media pipelines when applicable.

## Evaluation Examples

- Golden prompt set for expected outputs
- RAG query set with expected sources
- Refusal tests for unsupported facts
- Regression tests for known failures
- Latency checks for core user flows

## Grounded Response Expectations

When grounding is required, responses should cite or reference available evidence, avoid unsupported claims, and expose uncertainty clearly.

## When AI Quality Review Is Required

Run AI quality review when a change affects prompts, models, retrieval, memory, ranking, persona behavior, moderation, fallback behavior, or user-facing AI output.
