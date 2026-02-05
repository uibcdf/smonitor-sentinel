# smonitor-sentinel

SMonitor Sentinel is the opt-in telemetry and triage backend for `smonitor`.
It collects anonymized events, aggregates health metrics, and powers a public status dashboard.

## Goals

- **Privacy-first telemetry** (opt-in only).
- **Aggregation and deduplication** of errors/warnings/performance signals.
- **Public dashboard** showing health status by library/version.
- **LLM-assisted triage** on anonymized data (optional).

## Naming and Imports

- Repo/package name: `smonitor-sentinel`
- Public name: **SMonitor Sentinel** (Signal Monitor Sentinel)
- Import (internal/admin only): `import smonitor_sentinel`
- Do **not** document imports for end users.

## Structure

- `api/` – API service (e.g., FastAPI)
- `web/` – Dashboard frontend
- `storage/` – Schema and migrations
- `docs/` – API + privacy docs
- `devguide/` – Development plan and workflows

## Non-Goals (initial)

- No sensitive user data collection.
- No raw stack traces or user inputs by default.
- No automatic fixes without human approval.

## Roadmap

See `SPEC_SMONITOR_SENTINEL.md` and `devguide/`.
