# 07 — KV store

## Overview

Get/put/set semantics; simple mental model. Redis or SQLite are fine targets.

**Why this order:** Get/put/set semantics; simple mental model. Redis or SQLite are fine targets.

**Minimal spec:** Connect to Redis or SQLite; implement get(key), set(key, value); optional TTL for Redis.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | redis-py or sqlite3 for key-value usage. |
| **JavaScript** | ioredis or better-sqlite3 / node-redis. |
| **Go** | go-redis/redis or database/sql (SQLite). |
| **Java** | Jedis/Lettuce or JDBC SQLite. |
| **Rust** | redis crate or rusqlite. |
| **Zig** | Redis client or SQLite C API. |
| **C++** | hiredis or redis-plus-plus; sqlite3. |
| **C** | hiredis (Redis) or sqlite3. |
