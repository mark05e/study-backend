# 06 — Webhooks

## Overview

Implement an inbound webhook receiver that accepts signed JSON payloads. This follows the early HTTP topics because it reuses request parsing while introducing message authenticity checks.

**Why this order:** It adds request verification and raw-body handling without introducing long-lived connections.

## Required contract

- Start an HTTP server and expose `POST /webhook`.
- Read the shared secret from `WEBHOOK_SECRET`.
- Accept a JSON request body.
- Require `X-Signature` to contain the lowercase hex HMAC-SHA256 of the **raw request body** using `WEBHOOK_SECRET`.
- Return `200` with `{"received":true}` for a valid payload and signature.

## Acceptance checks

- A valid signed JSON payload returns `200`.
- The same payload with a bad signature returns `401`.
- The same payload with no signature header returns `401`.

## Failure cases

- Invalid JSON returns `400`.
- Signature verification must use the raw request bytes, not a re-serialized JSON body.
- Unknown routes return `404`.

## Extensions

- Add event-type routing with a header such as `X-Event-Type`.
- Queue webhook processing asynchronously after signature verification.
- Add replay protection with timestamps and nonces.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use FastAPI or Flask; verify HMAC with the standard `hmac` module. |
| **JavaScript** | Use Express or Fastify; verify HMAC with `crypto.createHmac`. |
| **Go** | Use `net/http` and `crypto/hmac`. |
| **Java** | Use Spring plus `Mac` for HMAC verification. |
| **Rust** | Use Axum or Actix with an `hmac` crate. |
| **Zig** | Use `std.crypto` if practical. |
| **C++** | Use OpenSSL or another small crypto library. |
| **C** | Use OpenSSL HMAC utilities and preserve the raw request body. |
