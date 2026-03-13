# 22 — HTTPS / TLS

## Overview

Serve a small HTTP API over TLS so clients connect with HTTPS instead of plaintext HTTP. This topic focuses on certificate loading, encrypted transport, and basic local-development trust setup.

**Why this order:** Conceptually, this fits with the early HTTP topics, but it is kept as a standalone topic so the existing folder numbering stays stable.

## Required contract

- Start an HTTPS server on a configurable port.
- Load the certificate and private key from:
  - `TLS_CERT_FILE`
  - `TLS_KEY_FILE`
- Expose `GET /health`.
- `GET /health` returns `200` with `{"status":"ok"}` over HTTPS.
- Use a self-signed certificate or a locally trusted development certificate for the baseline.

## Acceptance checks

- Starting the server with valid cert and key files succeeds.
- `curl -k https://localhost:<port>/health` returns `200` with `{"status":"ok"}`.
- A browser or client that trusts the certificate can load the same endpoint over HTTPS without plaintext fallback.

## Failure cases

- Missing or unreadable certificate or key files fail clearly at startup.
- A certificate and key mismatch fails clearly at startup.
- The baseline does not require automatic HTTP-to-HTTPS redirect.

## Extensions

- Add an HTTP listener that redirects to HTTPS.
- Generate local development certificates with `mkcert` or `openssl`.
- Restrict TLS versions or cipher suites.
- Add mutual TLS (mTLS).

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use framework TLS support or `ssl.SSLContext`; for ASGI servers, use built-in cert/key options when available. |
| **JavaScript** | Use Node's `https` module or framework TLS support. |
| **Go** | Use `http.ListenAndServeTLS` or an explicit `tls.Config`. |
| **Java** | Use Spring Boot, Jetty, or another server with keystore-based TLS configuration. |
| **Rust** | Prefer `rustls`-based integrations or framework TLS support. |
| **Zig** | Use a TLS-capable HTTP server path or stable C bindings if native support is limited. |
| **C++** | Prefer a library stack with OpenSSL support, such as Boost.Asio/Beast or a TLS-capable web framework. |
| **C** | Use OpenSSL, wolfSSL, or another TLS library rather than building TLS primitives yourself. |
