# Multi-Language Backend Learning Plan

A structured curriculum to implement the same backend/API topics in **8 languages**, ordered from easy to hard. Each topic has one folder; inside it you implement the same minimal spec in every language so you can compare idioms, tooling, and patterns.

## Languages (implementation order per topic)

1. **Python** — Start here to learn the topic with minimal syntax friction.
2. **JavaScript (Node)** — Same idea; optionally try Deno/Bun for a topic or two.
3. **Go** — Strong stdlib and tooling for APIs and networking.
4. **Java** — Typed, mature ecosystem (e.g. Spring).
5. **Rust** — Ownership, async, and explicit error handling.
6. **Zig** — C interop and manual memory; good for low-level (TCP, UDP).
7. **C++** — Mix of C-style and higher-level abstractions.
8. **C** — Minimal abstractions; full control with libcurl, sockets, etc.

## Topics (easy → hard)

| #  | Topic                     |
|----|---------------------------|
| 01 | [REST API](01-rest-api/) |
| 02 | [Health checks](02-health-checks/) |
| 03 | [CORS](03-cors/) |
| 04 | [API keys](04-api-keys/) |
| 05 | [ORM](05-orm/) |
| 06 | [Webhooks](06-webhooks/) |
| 07 | [KV store](07-kv/) |
| 08 | [S3](08-s3/) |
| 09 | [SSE](09-sse/) |
| 10 | [WebSockets](10-websockets/) |
| 11 | [GraphQL](11-graphql/) |
| 12 | [UDP/TCP](12-udp-tcp/) |
| 13 | [gRPC](13-grpc/) |
| 14 | [JWT](14-jwt/) |
| 15 | [OAuth](15-oauth/) |
| 16 | [Message queues (AMQP)](16-message-queues/) |
| 17 | [MQTT](17-mqtt/) |
| 18 | [Metrics](18-metrics/) |
| 19 | [Graceful shutdown](19-graceful-shutdown/) |
| 20 | [WebRTC](20-webrtc/) |
| 21 | [CI (Just + GitHub Actions)](21-ci/) |

## Repo layout

- **`XX-topic-name/`** — One folder per topic (e.g. `01-rest-api`, `10-websockets`).
- **`XX-topic-name/README.md`** — Overview, “why this order,” minimal spec, and **per-language notes** (libs and hints) so you have everything in one place for that topic.
- **`XX-topic-name/python/`, `javascript/`, `go/`, …** — One subfolder per language. Put your implementation here (and optionally a small README with run instructions and “what was different”).

Topic **21-ci** has no language subfolders; it’s for a single Justfile and GitHub Actions workflow that build/test all languages.

## How to use it

1. **One topic at a time** — Finish all 8 languages for that topic before moving on.
2. **Same spec** — Use the minimal spec in each topic’s README so implementations are comparable (e.g. REST: GET/POST `/users`, JSON, in-memory store).
3. **Start with the topic README** — It has the overview and per-language notes (FastAPI, Express, Gin, etc.) so you know what to reach for in each language.
4. When you implement a language, add a short README in that language’s subfolder: how to run, install deps, and one “what was different” note vs another language.

## Quick start

Pick a topic (e.g. REST API), open its README, then implement the minimal spec in `01-rest-api/python/`, then `01-rest-api/javascript/`, and so on. Repeat for the next topic.
