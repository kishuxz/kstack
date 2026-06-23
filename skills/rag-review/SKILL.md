# RAG Review Skill

## Purpose

Review retrieval-augmented generation quality and data boundaries.

## When to Use

Use when ingestion, chunking, embeddings, retrieval, citations, or grounded answers change.

## Inputs Expected

- Documents or data sources
- Retrieval configuration
- Example queries
- Example answers
- Privacy constraints

## Process

1. Review ingestion and chunking.
2. Check embedding and retrieval strategy.
3. Test relevance and empty retrieval behavior.
4. Review citation and grounding behavior.
5. Check stale data and privacy boundaries.

## Required Checks

- Document ingestion
- Chunking
- Embedding strategy
- Retrieval quality
- Citation/grounding behavior
- Stale data risk
- Empty retrieval behavior
- Privacy boundaries

## Scorecard

Rate each relevant dimension from 1-10:

- Retrieval relevance
- Grounding
- Citation quality
- Freshness handling
- Empty-state behavior
- Privacy safety

Verdict: Pass / Needs fixes / Block

## Output Format

- Verdict
- Scorecard
- Query results reviewed
- Blockers
- Fixes needed
- Eval gaps

## Stop Conditions

Block if answers are ungrounded, leak private data, or fabricate citations.
