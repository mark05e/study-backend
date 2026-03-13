# 15 — OAuth

## Overview

Implement "login with provider" (e.g. GitHub or Google). Use existing REST server; add redirect route and token exchange. Libraries per language for OAuth2.

**Why this order:** Flows, tokens, redirects; combine REST + crypto + state.

**Minimal spec:** OAuth2 authorization code flow: redirect to provider, callback route, exchange code for token; optional: call provider API with token.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | authlib or requests-oauthlib. |
| **JavaScript** | passport (with strategy) or simple redirect + axios for token exchange. |
| **Go** | golang.org/x/oauth2. |
| **Java** | Spring Security OAuth2 or ScribeJava. |
| **Rust** | oauth2 crate. |
| **Zig** | Hand-roll HTTP redirect + token request. |
| **C++** | liboauth or hand-roll. |
| **C** | liboauth or libcurl for token exchange. |
