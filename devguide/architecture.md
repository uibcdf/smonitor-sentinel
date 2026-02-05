# Sentinel Architecture

## Overview
Sentinel is a separate service from smonitor. It receives anonymized signals and
produces a public dashboard and optional LLM triage outputs.

## Core components
- Ingestion API
- Aggregation pipeline
- Storage (event + aggregates)
- Dashboard UI
- Triage module (optional)

## Principles
- Privacy-first and opt-in
- Minimal safe schema
- Observability and auditability
