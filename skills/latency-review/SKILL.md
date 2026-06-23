# Latency Review Skill

## Purpose

Review user-perceived latency and performance risks in AI or interactive flows.

## When to Use

Use when model calls, streaming, APIs, media pipelines, database calls, or interactive flows change.

## Inputs Expected

- Affected flow
- Timing data if available
- Architecture path
- Known latency targets

## Process

1. Map the user-perceived path.
2. Identify cold start and network costs.
3. Check model, API, database, and media latency.
4. Review streaming behavior.
5. Identify instrumentation gaps.

## Required Checks

- User-perceived latency
- Streaming behavior
- Cold start
- API latency
- Model latency
- TTS/STT latency if applicable
- Database latency
- Instrumentation gaps

## Scorecard

Rate each relevant dimension from 1-10:

- First response speed
- End-to-end latency
- Streaming quality
- Cold-start resilience
- Bottleneck visibility
- User experience

Verdict: Pass / Needs fixes / Block

## Output Format

- Verdict
- Scorecard
- Bottlenecks
- Measurements or missing measurements
- Fixes needed

## Stop Conditions

Block if latency makes the core user flow unusable or cannot be measured for a risky release.
