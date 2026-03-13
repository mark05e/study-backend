# 18 — Metrics

## Overview

Expose a `/metrics` (or similar) endpoint in Prometheus text format: counters, gauges, optional histograms.

**Why this order:** Prometheus or similar; counters/gauges, scrape endpoint per service.

**Minimal spec:** GET /metrics returns Prometheus text format with at least one counter and one gauge.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | prometheus-client. |
| **JavaScript** | prom-client. |
| **Go** | prometheus/client_golang. |
| **Java** | Micrometer (Prometheus registry). |
| **Rust** | metrics + metrics-exporter-prometheus. |
| **Zig** | Hand-roll text output or small lib. |
| **C++** | Hand-roll or small Prometheus client. |
| **C** | Hand-roll text output. |
