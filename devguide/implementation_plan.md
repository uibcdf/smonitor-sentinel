# Sentinel Implementation Plan

## Phase A — Ingestion MVP
- Minimal API endpoint for /ingest
- Schema validation
- Store raw events (anonymized)

## Phase B — Aggregation
- Deduplicate by code+trace_hash
- Aggregate by library/version

## Phase C — Dashboard
- Basic status page
- Top errors/warnings

## Phase D — LLM Triage (Optional)
- Summaries from aggregates
- Human approval

## Phase E — Auto-Issue Creation (Optional)
- GitHub App integration
- Dedup + rate limit
- Human-readable summary + JSON payload
