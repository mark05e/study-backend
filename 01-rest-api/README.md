# 01 — REST API

## Overview

Build a minimal JSON API with one collection and one write path. This is the first milestone because it teaches routing, JSON encoding, request parsing, and basic HTTP status handling without external services.

**Why this order:** It is the smallest useful backend shape and gives every later HTTP-based topic a familiar baseline.

## Required contract

- Start an HTTP server on a configurable port.
- `GET /users` returns `200` with a JSON array. The initial response is `[]`.
- `POST /users` accepts `{"name":"<non-empty string>"}` and returns `201` with `{"id":<integer>,"name":"<string>"}`.
- Store users in memory for the lifetime of the process only.

## Acceptance checks

- `GET /users` before any writes returns `200` and `[]`.
- `POST /users` with `{"name":"Alice"}` returns `201` and a created user object.
- `GET /users` after the insert returns an array containing the created user.

## Failure cases

- Missing or invalid JSON body returns `400`.
- Empty or whitespace-only `name` returns `400`.
- Unknown routes return `404`.

## Extensions

- Add `GET /users/{id}`.
- Add update or delete routes.
- Add simple request logging.

## Per-language notes


| Language       | Notes                                                        |
| -------------- | ------------------------------------------------------------ |
| **Python**     | Recommended: FastAPI. Simpler alternative: Flask.            |
| **JavaScript** | Recommended: Express or Fastify (Node).                      |
| **Go**         | Recommended: `net/http`. Alternative: Gin.                   |
| **Java**       | Recommended: Spring Web. Alternative: JAX-RS.                |
| **Rust**       | Recommended: Axum. Alternative: Actix.                       |
| **Zig**        | Use `std.http` or a small HTTP library.                      |
| **C++**        | Recommended: Drogon or cpp-httplib.                          |
| **C**          | Build a tiny server with sockets plus a minimal HTTP parser. |


