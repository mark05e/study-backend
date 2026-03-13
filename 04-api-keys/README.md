# 04 — API Keys

## Overview

Protect one route with a shared secret read from configuration. This is the simplest auth mechanism in the sequence and sets up later signature- and token-based topics.

**Why this order:** It adds request authentication without sessions, crypto handshakes, or third-party providers.

## Required contract

- Read the valid key from the `API_KEY` environment variable.
- Expose `GET /protected`.
- Require the exact header `X-API-Key: <value>`.
- Return `200` with `{"ok":true}` when the header matches the configured key.

## Acceptance checks

- Missing `X-API-Key` returns `401`.
- Wrong `X-API-Key` returns `401`.
- Correct `X-API-Key` returns `200` with `{"ok":true}`.

## Failure cases

- If `API_KEY` is unset, fail clearly at startup or document the fallback in the language-specific README.
- Do not accept the key in a query string for the baseline contract.
- Unknown routes return `404`.

## Extensions

- Add bearer-token support as an alternate header format.
- Protect multiple routes with shared middleware.
- Return a structured JSON error body.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use middleware or a dependency that reads `os.environ`. |
| **JavaScript** | Use middleware that checks `req.headers['x-api-key']`. |
| **Go** | Use middleware around the handler. |
| **Java** | Use a filter or interceptor backed by config. |
| **Rust** | Use Axum or Actix middleware/extractors. |
| **Zig** | Check the header in the handler before processing. |
| **C++** | Use middleware if the framework supports it, otherwise validate in the handler. |
| **C** | Parse `X-API-Key` explicitly in your HTTP request handling. |
