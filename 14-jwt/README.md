# 14 — JWT

## Overview

Issue a signed token and use it to protect a route. This follows API keys because it introduces structured, expiring credentials without yet bringing in third-party providers.

**Why this order:** It adds signed tokens and expiry handling before the larger redirect flow of OAuth.

## Required contract

- Read `JWT_SECRET` from the environment.
- Expose:
  - `POST /login`
  - `GET /protected`
- `POST /login` accepts `{"username":"demo","password":"demo"}` and returns a signed JWT with an expiration claim.
- `GET /protected` requires `Authorization: Bearer <jwt>` and returns `200` with `{"ok":true}` when the token is valid.

## Acceptance checks

- Valid login returns a token.
- Supplying that token to `GET /protected` returns `200`.
- An expired or tampered token returns `401`.

## Failure cases

- Invalid credentials return `401`.
- Missing bearer token returns `401`.
- Missing `JWT_SECRET` fails clearly at startup.

## Extensions

- Add additional claims such as `sub` or roles.
- Add refresh tokens.
- Use asymmetric signing after the shared-secret baseline works.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: PyJWT. |
| **JavaScript** | Recommended: `jsonwebtoken`. |
| **Go** | Recommended: `golang-jwt/jwt`. |
| **Java** | Recommended: `jjwt` or `auth0 java-jwt`. |
| **Rust** | Recommended: `jsonwebtoken`. |
| **Zig** | Prefer a JWT or JOSE library path over hand-building the token. |
| **C++** | Prefer `jwt-cpp` or a similar library. |
| **C** | Prefer `libjwt` or another small JWT library. |
