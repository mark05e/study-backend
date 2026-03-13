# 19 — Graceful shutdown

## Overview

On SIGTERM/SIGINT: stop accepting new connections, drain in-flight requests/connections, then exit. Implement with the same server you use for WebSockets or gRPC; language-specific signal handling and shutdown APIs.

**Why this order:** Drain connections, finish in-flight requests, then exit. Use with WebSockets/TCP/gRPC.

**Minimal spec:** Server that handles SIGTERM/SIGINT; stops accepting new work, waits for in-flight to complete (with timeout), then exits.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | signal.signal for SIGTERM/SIGINT; asyncio shutdown or Flask/uvicorn shutdown hook. |
| **JavaScript** | process.on('SIGTERM', ...); close server, wait for connections. |
| **Go** | signal.Notify; context.WithCancel; srv.Shutdown(ctx). |
| **Java** | Runtime.addShutdownHook; Spring graceful shutdown. |
| **Rust** | tokio::signal; axum/actix shutdown. |
| **Zig** | std.os.sigaction or poll for signal; close listener, drain. |
| **C++** | signal handler or signalfd; close socket, join threads. |
| **C** | signal() or sigaction; close listen fd, drain accept loop. |
