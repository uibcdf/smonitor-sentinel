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

## 3. Naming & Imports

- Repo/package name: `smonitor-sentinel`
- Public name: **SMonitor Sentinel** (Signal Monitor Sentinel)
- Import (internal/admin only): `import smonitor_sentinel`
- Do **not** document imports for end users.

## 4. Ingestion API

Minimal payload (safe schema):
- `library`, `version`, `python_version`, `platform`
- `code`, `category`, `level`
- `trace_hash`
- `timestamp`
- `profile`
- `performance` (aggregated)

## 5. Processing Pipeline

1. Validate schema
2. Normalize and deduplicate
3. Aggregate by library/version/code
4. Emit summaries for dashboard
5. Optional LLM triage on aggregates

## 6. Dashboard

- Status by library and version
- Top errors/warnings
- Performance regressions
- Trend charts

## 7. LLM Triage (Optional)

- Inputs: aggregated, anonymized signals
- Outputs: probable cause, suggested fix, impact
- Human approval required before action

## 8. Auto-Issue Creation (Optional)

- Sentinel may create GitHub issues for actionable, deduplicated errors.
- **Opt-in** per repository.
- **Rate-limited** and **deduplicated** by `code + trace_hash`.
- Issues include:
  - human-readable summary
  - technical details
  - JSON payload for agents

**Auth model:**
- Recommended: GitHub App "SMonitor Sentinel" (per-repo install)
- Alternative: bot account + PAT

## 9. Security & Privacy

- Opt-in only
- Strict schema validation
- Rate limiting and abuse protection
- Retention policy

## 10. Roadmap

- Phase A: local bundle upload + ingestion API
- Phase B: dashboard MVP
- Phase C: LLM triage
- Phase D: auto-issue creation

---

> Sentinel is a separate service and repository from smonitor.
