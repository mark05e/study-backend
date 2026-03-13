# 07 — KV Store

## Overview

Use a dedicated key-value service instead of in-process memory or relational storage. This topic intentionally standardizes on Redis so every language targets the same external dependency.

**Why this order:** It introduces a networked data store with a small data model and very simple operations.

## Required contract

- Connect to Redis using `REDIS_URL`.
- Expose:
  - `PUT /kv/{key}` with JSON body `{"value":"<string>"}`
  - `GET /kv/{key}`
- `PUT /kv/{key}` stores the string value in Redis and returns `200`.
- `GET /kv/{key}` returns `200` with `{"key":"<key>","value":"<value>"}` when present.

## Acceptance checks

- Writing `{"value":"hello"}` to `PUT /kv/greeting` returns `200`.
- Reading `GET /kv/greeting` returns the same value from Redis.
- Restarting the app still allows the stored value to be read from the same Redis instance.

## Failure cases

- Missing or invalid JSON body returns `400`.
- Reading a missing key returns `404`.
- If Redis is unreachable, fail clearly at startup or return a clear dependency error.

## Extensions

- Add key expiration with TTL.
- Add `DELETE /kv/{key}`.
- Add namespacing or prefix support.

## Per-language notes


| Language       | Notes                                       |
| -------------- | ------------------------------------------- |
| **Python**     | Recommended: `redis-py`.                    |
| **JavaScript** | Recommended: `node-redis` or `ioredis`.     |
| **Go**         | Recommended: `go-redis`.                    |
| **Java**       | Recommended: Lettuce or Jedis.              |
| **Rust**       | Recommended: `redis` crate.                 |
| **Zig**        | Use a Redis client or C bindings if needed. |
| **C++**        | Use `hiredis` or `redis-plus-plus`.         |
| **C**          | Use `hiredis`.                              |


