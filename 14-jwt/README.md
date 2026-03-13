# 14 — JWT

## Overview

Issue (sign) and validate (verify signature + exp) tokens; use with a small REST endpoint (e.g. POST /login returns JWT, GET /protected requires Bearer).

**Why this order:** Issue and validate tokens; often used with APIs or before OAuth.

**Minimal spec:** POST /login returns JWT; GET /protected requires Authorization: Bearer <jwt>; validate signature and exp.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | PyJWT. |
| **JavaScript** | jsonwebtoken. |
| **Go** | golang-jwt/jwt. |
| **Java** | jjwt or auth0 java-jwt. |
| **Rust** | jsonwebtoken. |
| **Zig** | Custom or C lib (e.g. libjwt) / OpenSSL. |
| **C++** | jwt-cpp or OpenSSL + base64. |
| **C** | libjwt or OpenSSL + manual base64. |
