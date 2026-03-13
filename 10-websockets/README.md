# 10 — WebSockets

## Overview

Open a bidirectional connection and exchange framed messages after an HTTP upgrade. This follows SSE because it adds full two-way messaging and explicit connection lifecycle handling.

**Why this order:** It builds on long-lived connections while adding framing and duplex communication.

## Required contract

- Expose a WebSocket endpoint at `/ws`.
- Accept text frames only for the baseline contract.
- Echo each received text message back to the same client unchanged.
- Keep the connection open for multiple messages until the client disconnects.

## Acceptance checks

- A client can connect to `/ws`.
- Sending `hello` receives `hello` back.
- Sending multiple messages on one connection echoes each message in order.

## Failure cases

- A plain HTTP request to `/ws` must not return `200` as if it were a normal REST route.
- Binary-frame support is not required for the baseline.
- Unknown routes return `404`.

## Extensions

- Broadcast chat messages to all connected clients.
- Add connection IDs and logging.
- Add ping/pong or idle timeout handling.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use FastAPI WebSockets or the `websockets` library. |
| **JavaScript** | Recommended: `ws`. |
| **Go** | Recommended: `gorilla/websocket`. |
| **Java** | Use JSR 356 or Spring WebSocket. |
| **Rust** | Recommended: `tokio-tungstenite`. |
| **Zig** | Use `libwebsockets` or another small WebSocket library. |
| **C++** | Use `libwebsockets` or a comparable library. |
| **C** | Use `libwebsockets` or a similar C library. |
