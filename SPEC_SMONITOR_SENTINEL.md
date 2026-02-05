# SPEC_SMONITOR_SENTINEL.md — Telemetry & Sentinel Backend

**Version:** v0.1 (Draft)  
**Status:** CONCEPT  
**Author:** UIBCDF Development Team  

## 1. Purpose

`smonitor-sentinel` is the opt-in telemetry backend for `smonitor`. It ingests anonymized signals,
aggregates health metrics, and provides a public dashboard and triage pipeline.

## 2. Core Principles

- **Privacy-first**: opt-in only, no sensitive data by default.
- **Aggregation**: deduplicate and summarize events.
- **Transparency**: public health dashboard.
- **Guardrails**: LLMs operate only on anonymized aggregates.

## 3. Ingestion API

Minimal payload (safe schema):
- `library`, `version`, `python_version`, `platform`
- `code`, `category`, `level`
- `trace_hash`
- `timestamp`
- `profile`
- `performance` (aggregated)

## 4. Processing Pipeline

1. Validate schema
2. Normalize and deduplicate
3. Aggregate by library/version/code
4. Emit summaries for dashboard
5. Optional LLM triage on aggregates

## 5. Dashboard

- Status by library and version
- Top errors/warnings
- Performance regressions
- Trend charts

## 6. LLM Triage (Optional)

- Inputs: aggregated, anonymized signals
- Outputs: probable cause, suggested fix, impact
- Human approval required before action

## 7. Security & Privacy

- Opt-in only
- Strict schema validation
- Rate limiting and abuse protection
- Retention policy

## 8. Roadmap

- Phase A: local bundle upload + ingestion API
- Phase B: dashboard MVP
- Phase C: LLM triage

---

> Sentinel is a separate service and repository from smonitor.
