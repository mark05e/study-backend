# 02 — Health Checks

## Overview

Add a tiny operational endpoint that lets a caller confirm the service is up. This comes right after REST because it is a small, practical addition to any server.

**Why this order:** It introduces an operational contract without adding new infrastructure or protocol complexity.

## Required contract

- Start an HTTP server on a configurable port.
- `GET /health` returns `200` with the exact JSON body `{"status":"ok"}`.
- Set `Content-Type: application/json` on the health response.
- Keep this topic standalone even if you reuse patterns from `01-rest-api`.

## Acceptance checks

- `GET /health` returns `200`.
- The response body is exactly `{"status":"ok"}`.
- Repeated requests return the same success response.

## Failure cases

- Unsupported methods on `/health` must not return `200`.
- Unknown routes return `404`.

## Extensions

- Add separate `/ready` and `/live` endpoints.
- Include dependency checks in readiness only.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Add one route in FastAPI or Flask. |
| **JavaScript** | Add one route in Express or Fastify. |
| **Go** | Use `net/http` with a dedicated `/health` handler. |
| **Java** | Use a custom endpoint or Spring Actuator if you want extras later. |
| **Rust** | Add one route in Axum or Actix. |
| **Zig** | Add one route in your HTTP server. |
| **C++** | Add one handler in Drogon or cpp-httplib. |
| **C** | Add one path branch in your HTTP handler. |
