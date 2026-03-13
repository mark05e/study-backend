# 06 — Webhooks

## Overview

HTTP POST endpoint that receives a payload; optionally verify signature (e.g. HMAC). Reuse REST server from topic 1.

**Why this order:** Outbound HTTP; reuses REST skills. No long-lived connections.

**Minimal spec:** POST endpoint that accepts JSON body; optionally verify HMAC signature from header; log or process payload.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | FastAPI/Flask POST route; verify HMAC with hmac module. |
| **JavaScript** | Express/Fastify POST route; crypto.createHmac for verification. |
| **Go** | net/http Handler; crypto/hmac for verification. |
| **Java** | Spring endpoint; Mac for HMAC. |
| **Rust** | Axum/Actix handler; ring or hmac crate. |
| **Zig** | std.crypto or custom HMAC in handler. |
| **C++** | POST handler; OpenSSL or similar for HMAC. |
| **C** | Parse POST body; OpenSSL HMAC for verification. |
