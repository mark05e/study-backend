# 04 — API keys

## Overview

Validate `X-API-Key` or `Authorization: Bearer <key>` (or query param); reject with 401 if missing or invalid. Env var for valid key; optional HMAC for webhooks later.

**Why this order:** Authenticate requests via header/query; HMAC or static key. Simple auth baseline.

**Minimal spec:** One protected route; require valid API key from env; return 401 when missing/invalid.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Middleware or dependency that reads header, compares to os.environ. |
| **JavaScript** | Middleware that checks req.headers['x-api-key'] or Authorization. |
| **Go** | Middleware that reads header and validates. |
| **Java** | Filter or interceptor; read from env or config. |
| **Rust** | Axum/Actix middleware or extractor. |
| **Zig** | Check header in handler before processing. |
| **C++** | Middleware or handler that validates header. |
| **C** | Parse Authorization or X-API-Key and compare. |
