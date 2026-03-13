# 09 — SSE (Server-Sent Events)

## Overview

One HTTP response, `Content-Type: text/event-stream`; keep connection open and send events (e.g. `data: {...}\n\n`). Simpler than WebSockets; long-lived response.

**Why this order:** One-way server→client over HTTP; simpler than WebSockets. Long-lived response.

**Minimal spec:** GET endpoint that streams events (e.g. timestamp every second); client receives with EventSource or similar.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | sse-starlette or Flask-SSE. |
| **JavaScript** | express: res.write with text/event-stream, chunked. |
| **Go** | net/http with Flusher; set headers and write event lines. |
| **Java** | SseEmitter (Spring). |
| **Rust** | axum or actix SSE support. |
| **Zig** | Chunked response + manual flush. |
| **C++** | Chunked transfer; flush after each event. |
| **C** | Chunked response; manual flush. |
