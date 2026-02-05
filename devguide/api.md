# Sentinel API (Sketch)

## POST /ingest
Receives anonymized events.

Payload (example):
```json
{
  "library": "molsysmt",
  "version": "1.2.0",
  "python_version": "3.12",
  "platform": "linux",
  "code": "MSM-W010",
  "category": "SelectionWarning",
  "level": "WARNING",
  "trace_hash": "abc123",
  "timestamp": "2026-02-05T12:00:00Z",
  "profile": "user",
  "performance": {"p50_ms": 1.2, "p95_ms": 5.4}
}
```

Responses:
- 200 OK
- 400 invalid schema
```
