# 02 — Health checks

## Overview

Add a `/health` (or `/ready`, `/live`) route that returns 200 and optional JSON. Same server as REST; establishes readiness/liveness.

**Why this order:** `/health` endpoint; trivial add-on to any server. Establishes readiness/liveness.

**Minimal spec:** GET `/health` returns 200 and optionally `{"status":"ok"}`.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Same server as REST; middleware or single route (FastAPI/Flask). |
| **JavaScript** | Same server as REST; single route (Express/Fastify). |
| **Go** | net/http with a `/health` handler. |
| **Java** | Spring Actuator or custom endpoint. |
| **Rust** | Axum/Actix: one route. |
| **Zig** | Add route to std.http or zig-http server. |
| **C++** | Add handler in Drogon/cpp-httplib. |
| **C** | Add path check in your HTTP parser/handler. |
