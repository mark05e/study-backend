# 12 — UDP/TCP

## Overview

Raw sockets; no HTTP. More manual I/O and (for TCP) connection handling. Small echo or chat server.

**Why this order:** Raw sockets; no HTTP. More manual I/O and (for TCP) connection handling.

**Minimal spec:** TCP echo server (and optionally client); or UDP echo. Optional: simple multi-client chat.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | asyncio or socket. |
| **JavaScript** | net (TCP) / dgram (UDP). |
| **Go** | net (Listen, Accept, Read, Write). |
| **Java** | java.nio (SocketChannel, ServerSocketChannel) or java.net. |
| **Rust** | tokio::net (TcpListener, TcpStream). |
| **Zig** | std.net (raw sockets). |
| **C++** | BSD sockets or asio. |
| **C** | Raw sockets (socket, bind, listen, accept, read, write). |
