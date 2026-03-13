# 10 — WebSockets

## Overview

Bidirectional, long-lived connection; introduces connection lifecycle and framing.

**Why this order:** Bidirectional, long-lived; introduces connection lifecycle and framing.

**Minimal spec:** WS server that echoes messages; optional simple chat (broadcast to all clients).

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | FastAPI websockets or websockets. |
| **JavaScript** | ws. |
| **Go** | gorilla/websocket. |
| **Java** | JSR 356 or Spring WebSocket. |
| **Rust** | tokio-tungstenite. |
| **Zig** | libwebsockets or similar. |
| **C++** | libwebsockets or similar. |
| **C** | libwebsockets or similar. |
