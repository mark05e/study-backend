# 09 — SSE (Server-Sent Events)

## Overview

Stream one-way events from server to client over plain HTTP. This comes before WebSockets because the connection stays HTTP-shaped and only the server writes messages.

**Why this order:** It introduces a long-lived response without requiring bidirectional framing.

## Required contract

- Expose `GET /events`.
- Respond with `Content-Type: text/event-stream`.
- Keep the connection open and send one event per second.
- Each event must use this format:
  - `event: tick`
  - `data: {"count":<integer>}`
  - blank line terminator

## Acceptance checks

- Connecting to `GET /events` starts a streaming response.
- The first three events are delivered in order with incrementing `count` values starting at `1`.
- The response uses `text/event-stream`.

## Failure cases

- Unsupported methods on `/events` must not return `200`.
- Do not buffer the whole response and send it at the end.
- Unknown routes return `404`.

## Extensions

- Add heartbeat comments.
- Add reconnection support with `id:` fields.
- Stream a real domain event instead of a counter.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use `sse-starlette` or plain streaming in FastAPI/Flask. |
| **JavaScript** | Use Express or Fastify with `res.write` and explicit flushing. |
| **Go** | Use `net/http` with `Flusher`. |
| **Java** | Use Spring `SseEmitter`. |
| **Rust** | Use Axum or Actix SSE support. |
| **Zig** | Use chunked responses and flush after each event. |
| **C++** | Use chunked transfer or streaming responses with explicit flushes. |
| **C** | Write the event stream manually and flush after each event. |
