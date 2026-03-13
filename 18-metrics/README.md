# 18 — Metrics

## Overview

Expose service metrics in a scrape-friendly format. This is a small observability topic that fits late in the sequence because it pairs well with the more realistic servers built earlier.

**Why this order:** It introduces operational instrumentation after you already have endpoints and background work worth measuring.

## Required contract

- Expose `GET /metrics`.
- Return Prometheus text format.
- Include at least these two metrics:
  - `app_requests_total`
  - `app_inprogress_requests`
- The counter must increase when handled requests occur.

## Acceptance checks

- `GET /metrics` returns `200`.
- The response contains both required metric names.
- After making at least one normal request to the app, `app_requests_total` increases.

## Failure cases

- The baseline should not return JSON for `/metrics`.
- Missing required metrics is a contract failure.
- Unknown routes return `404`.

## Extensions

- Add latency histograms.
- Add labels such as route or method.
- Add a Prometheus scrape config for local testing.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `prometheus-client`. |
| **JavaScript** | Recommended: `prom-client`. |
| **Go** | Recommended: `prometheus/client_golang`. |
| **Java** | Recommended: Micrometer with the Prometheus registry. |
| **Rust** | Use `metrics` plus a Prometheus exporter. |
| **Zig** | Hand-roll the text output only if no small client exists. |
| **C++** | Prefer a small Prometheus client library if available. |
| **C** | Hand-roll the text format only for the narrow baseline metrics. |
