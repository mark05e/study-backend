# 19 — Graceful Shutdown

## Overview

Stop accepting new work, let in-flight work finish, and then exit cleanly after a signal. This topic is most useful after you already have realistic servers and long-lived connections in mind.

**Why this order:** It focuses on lifecycle management and coordination rather than a new application protocol.

## Required contract

- Start a standalone HTTP server with:
  - `GET /health`
  - `GET /slow`
- `GET /slow` waits about 5 seconds before returning `200`.
- On `SIGINT` or `SIGTERM`, stop accepting new requests, allow in-flight work to finish, and exit with a timeout.
- Use a timeout of about 10 seconds for the baseline.

## Acceptance checks

- Start a `GET /slow` request.
- Send `SIGINT` or `SIGTERM` while that request is in flight.
- The in-flight request finishes successfully.
- The process exits cleanly after draining or timing out.

## Failure cases

- New requests should not be accepted after shutdown begins.
- In-flight requests should not be dropped immediately unless the timeout is reached.
- Signal handling should not leave the process hung indefinitely.

## Extensions

- Apply the same shutdown logic to WebSockets or gRPC servers.
- Track active connection counts.
- Add structured shutdown logging.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use `signal` plus framework shutdown hooks. |
| **JavaScript** | Use `process.on('SIGTERM')` or `process.on('SIGINT')` and close the server. |
| **Go** | Use `signal.Notify` and `srv.Shutdown(ctx)`. |
| **Java** | Use a shutdown hook or framework support. |
| **Rust** | Use `tokio::signal` and graceful server shutdown support. |
| **Zig** | Use `sigaction` or equivalent OS-level signal handling. |
| **C++** | Use a signal handler or `signalfd` and coordinate thread shutdown. |
| **C** | Use `signal()` or `sigaction()` and stop the accept loop cleanly. |
