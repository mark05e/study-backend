# 03 — CORS

## Overview

Allow a browser app on another origin to call your API safely. This fits early in the sequence because it builds directly on the REST shape without changing the core data model.

**Why this order:** It introduces browser-facing HTTP behavior and preflight handling while staying close to the REST baseline.

## Required contract

- Start an HTTP server that exposes `GET /users` and `POST /users`.
- Allow cross-origin requests from exactly `http://localhost:3000`.
- Support `OPTIONS /users` preflight with these headers:
  - `Access-Control-Allow-Origin: http://localhost:3000`
  - `Access-Control-Allow-Methods: GET, POST, OPTIONS`
  - `Access-Control-Allow-Headers: Content-Type`
- Include `Access-Control-Allow-Origin: http://localhost:3000` on successful `GET /users` and `POST /users` responses.

## Acceptance checks

- `OPTIONS /users` returns a non-error response with the required CORS headers.
- `GET /users` includes the allow-origin header.
- `POST /users` includes the allow-origin header.

## Failure cases

- Requests from other origins must not receive a wildcard allow-origin header.
- Unknown routes return `404`.
- Preflight responses must not omit the required method or header declarations.

## Extensions

- Add support for credentials.
- Add per-route CORS configuration.
- Add `Access-Control-Expose-Headers` for custom response headers.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: FastAPI `CORSMiddleware` or Flask-CORS. |
| **JavaScript** | Recommended: `cors` middleware in Express or built-in Fastify handling. |
| **Go** | Use `gorilla/handlers` or a small custom middleware. |
| **Java** | Use Spring CORS config or a filter. |
| **Rust** | Use `tower-http` CORS support. |
| **Zig** | Add the headers directly in your response builder. |
| **C++** | Add the headers directly in Drogon or cpp-httplib responses. |
| **C** | Set the CORS headers explicitly in your HTTP response. |
