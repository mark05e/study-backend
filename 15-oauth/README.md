# 15 — OAuth

## Overview

Implement an OAuth2 authorization-code login flow against a provider or a local mock provider. This topic is intentionally more opinionated than the earlier auth topics because redirects, state handling, and token exchange need a stable baseline.

**Why this order:** It combines browser redirects, callback handling, and token exchange after API keys and JWTs are already familiar.

## Required contract

- Expose:
  - `GET /auth/login`
  - `GET /auth/callback`
- Read configuration from:
  - `OAUTH_CLIENT_ID`
  - `OAUTH_CLIENT_SECRET`
  - `OAUTH_REDIRECT_URI`
- `GET /auth/login` redirects the browser to the provider authorization endpoint with a `state` value.
- `GET /auth/callback` validates `state`, exchanges the authorization code for a token, and returns a success response such as `{"authenticated":true}`.

## Acceptance checks

- Visiting `/auth/login` produces a redirect to the provider.
- Completing the provider flow reaches `/auth/callback`.
- A successful callback exchanges the code and returns a success response.

## Failure cases

- Missing or mismatched `state` returns `400`.
- Token exchange failure returns a clear auth or upstream error.
- Missing OAuth configuration fails clearly at startup.

## Extensions

- Call the provider user-info API after token exchange.
- Add PKCE.
- Replace the real provider with a local mock provider for automated testing.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `authlib` or `requests-oauthlib`. |
| **JavaScript** | Recommended: Passport strategy or a thin OAuth client library. |
| **Go** | Recommended: `golang.org/x/oauth2`. |
| **Java** | Recommended: Spring Security OAuth2 or ScribeJava. |
| **Rust** | Recommended: `oauth2` crate. |
| **Zig** | Treat as advanced; prefer a very small, well-defined library path if available. |
| **C++** | Prefer a small OAuth helper library rather than a full hand-rolled flow. |
| **C** | Treat as advanced unless you have a clear library-backed path. |
