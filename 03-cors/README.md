# 03 — CORS

## Overview

Add CORS headers (e.g. `Access-Control-Allow-Origin`) to your REST server and handle preflight OPTIONS. One config per stack.

**Why this order:** Browser cross-origin; add middleware to REST. One config per stack.

**Minimal spec:** Respond to OPTIONS with appropriate CORS headers; add CORS headers to GET/POST responses so a browser on another origin can call your API.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Middleware (e.g. FastAPI CORSMiddleware, Flask-CORS). |
| **JavaScript** | cors middleware in Express; handle OPTIONS in Fastify. |
| **Go** | gorilla/handlers CORS or custom middleware. |
| **Java** | Spring CORS config or filter. |
| **Rust** | tower or tower-http CORS layer. |
| **Zig** | Add CORS headers in response builder. |
| **C++** | Add headers in Drogon/cpp-httplib response. |
| **C** | Set CORS headers in your HTTP response. |
