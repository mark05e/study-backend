# 12 — TCP Echo Server

## Overview

Drop down below HTTP and work directly with sockets. The baseline is intentionally TCP-only so every language implements the same connection-oriented protocol before exploring variants.

**Why this order:** It is the first topic where you manage sockets, reads, writes, and connection lifecycle directly.

## Required contract

- Start a TCP server on a configurable port.
- Accept multiple client connections, whether sequentially or concurrently.
- Treat input as newline-delimited UTF-8 text.
- Echo each received line back to the same client, including the newline.

## Acceptance checks

- Connecting with a TCP client works.
- Sending `hello\n` returns `hello\n`.
- A second client can connect after or alongside the first and receive the same echo behavior.

## Failure cases

- The server must keep running after one client disconnects.
- Unknown or partial binary protocol support is not required for the baseline.
- Crashing on a normal disconnect is a failure.

## Extensions

- Add a UDP echo server.
- Add multi-client broadcast chat.
- Add connection logging and idle timeouts.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use `asyncio` or the `socket` module. |
| **JavaScript** | Use Node `net`. Save `dgram` for the UDP extension. |
| **Go** | Use the `net` package. |
| **Java** | Use `java.net` or `java.nio`. |
| **Rust** | Use `tokio::net` or standard sockets. |
| **Zig** | Use `std.net`. |
| **C++** | Use BSD sockets or Asio. |
| **C** | Use raw sockets with `socket`, `bind`, `listen`, `accept`, `read`, and `write`. |
