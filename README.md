# Multi-Language Backend Learning Plan

A structured curriculum to implement the same backend and systems topics in **8 languages**, ordered from easier application-level work toward lower-level protocols and tooling. Each topic folder contains a single required contract so you can compare idioms, tooling, and trade-offs across languages.

## Core repo contract

- Every topic folder is a **standalone exercise**. You can reuse ideas or code from earlier topics, but the implementation for a topic should live entirely inside that topic's folder.
- Every topic README defines a **required contract**. Implement that contract in every language before attempting any optional extensions.
- Optional features belong in an **Extensions** section so the required behavior stays comparable across languages.
- Prefer one **recommended library or stack per language** for the baseline path. Treat hand-rolled implementations as extensions unless the topic is explicitly about low-level protocol work.

## Languages (implementation order per topic)

1. **Python** — Start here to learn the topic with minimal syntax friction.
2. **JavaScript (Node)** — Similar ergonomics with a different runtime and package ecosystem.
3. **Go** — Strong stdlib and tooling for APIs and networking.
4. **Java** — Typed, mature ecosystem with batteries included.
5. **Rust** — Ownership, async, and explicit error handling.
6. **Zig** — C interop and manual memory; best suited for lower-level exercises.
7. **C++** — Mix of C-style and higher-level abstractions.
8. **C** — Minimal abstractions; full control with sockets and C libraries.

## Topics (easy -> hard)

| #  | Topic |
|----|-------|
| 01 | [REST API](01-rest-api/) |
| 02 | [Health checks](02-health-checks/) |
| 03 | [CORS](03-cors/) |
| 04 | [API keys](04-api-keys/) |
| 05 | [Persistence / Data Access](05-orm/) |
| 06 | [Webhooks](06-webhooks/) |
| 07 | [KV store](07-kv/) |
| 08 | [S3 / Object storage](08-s3/) |
| 09 | [SSE](09-sse/) |
| 10 | [WebSockets](10-websockets/) |
| 11 | [GraphQL](11-graphql/) |
| 12 | [TCP echo server](12-udp-tcp/) |
| 13 | [gRPC](13-grpc/) |
| 14 | [JWT](14-jwt/) |
| 15 | [OAuth](15-oauth/) |
| 16 | [Message queues (AMQP)](16-message-queues/) |
| 17 | [MQTT](17-mqtt/) |
| 18 | [Metrics](18-metrics/) |
| 19 | [Graceful shutdown](19-graceful-shutdown/) |
| 20 | [WebRTC](20-webrtc/) |
| 21 | [CI (Just + GitHub Actions)](21-ci/) |
| 22 | [HTTPS / TLS](22-https-tls/) |

`22-https-tls` is appended to avoid renumbering the existing folders. Conceptually, it pairs well with the early HTTP topics.

## Repo layout

- **`XX-topic-name/`** — One folder per topic (for example `01-rest-api`, `10-websockets`).
- **`XX-topic-name/README.md`** — The topic contract, acceptance checks, failure cases, extensions, and per-language notes.
- **`XX-topic-name/python/`, `javascript/`, `go/`, ...** — One subfolder per language. Put the topic implementation here, plus an optional short language-specific README with run instructions and one "what was different" note.

Topic **21-ci** has no language subfolders; it is for a single repo-level `Justfile` and `.github/workflows/ci.yml`.

## Topic README template

Every topic README should use this structure:

1. **Overview** — What the topic teaches and why it appears in this position.
2. **Required contract** — The exact baseline behavior that every language must implement.
3. **Acceptance checks** — The minimum manual checks or tests that prove the baseline works.
4. **Failure cases** — Required error behavior so implementations stay comparable.
5. **Extensions** — Optional add-ons once the baseline is complete.
6. **Per-language notes** — Recommended libraries and any stack-specific caveats.

## Prerequisites matrix

| Topic | External services | Secrets / config | Extra tools | Manual / browser step | CI suitability |
|-------|-------------------|------------------|-------------|------------------------|----------------|
| `01-rest-api` | None | None | None | No | Yes |
| `02-health-checks` | None | None | None | No | Yes |
| `03-cors` | None | None | None | Optional browser or curl preflight check | Yes |
| `04-api-keys` | None | `API_KEY` | None | No | Yes |
| `05-orm` | SQLite file | DB path if configurable | Migration tool or schema bootstrap | No | Yes |
| `06-webhooks` | None | `WEBHOOK_SECRET` | None | No | Yes |
| `07-kv` | Redis | `REDIS_URL` | Redis locally or in CI service container | No | Yes with service container |
| `08-s3` | MinIO | Endpoint, bucket, access key, secret key | MinIO client optional | No | Yes with service container |
| `09-sse` | None | None | None | Optional browser `EventSource` client | Yes |
| `10-websockets` | None | None | None | Optional browser or CLI WS client | Yes |
| `11-graphql` | None | None | Codegen optional depending on stack | GraphQL client optional | Usually yes |
| `12-udp-tcp` | None | None | None | Optional second terminal as client | Usually yes |
| `13-grpc` | None | None | `protoc` and language plugins | Optional second process as client | Yes once toolchain is pinned |
| `14-jwt` | None | `JWT_SECRET` | None | No | Yes |
| `15-oauth` | OAuth provider or local mock | Client ID, client secret, redirect URI | None | Yes, browser redirect flow | Usually local/manual |
| `16-message-queues` | RabbitMQ | `AMQP_URL` | RabbitMQ locally or in CI service container | No | Yes with service container |
| `17-mqtt` | Mosquitto or other broker | Broker URL and topic names | Broker locally or in CI service container | Optional second client | Yes with service container |
| `18-metrics` | None | None | None | Optional Prometheus scrape check | Yes |
| `19-graceful-shutdown` | None | None | Signal support in test environment | Usually manual or integration-style | Limited on some CI runners |
| `20-webrtc` | STUN server at minimum; TURN optional for tougher networks | Signaling config if needed | Browser, WebRTC library stack | Yes, browser peer required | Usually local/manual |
| `21-ci` | Depends on earlier topics | Repo-level env wiring | `just`, GitHub Actions, language toolchains | No | This topic defines CI |
| `22-https-tls` | None | `TLS_CERT_FILE`, `TLS_KEY_FILE` | `openssl` or `mkcert` optional for local cert generation | Optional browser trust step or `curl -k` | Yes with generated or checked-in test certs |

## How to use it

1. Pick one topic and read its README first.
2. Implement the **required contract** in `python/`, then `javascript/`, then the remaining languages.
3. Run the topic's **acceptance checks** before moving to the next language.
4. Add optional extensions only after the baseline contract is working.
5. Add a short language-specific README when useful: install steps, run command, and one "what was different" note.

## Notes on advanced topics

- For advanced topics, prefer the recommended library path over hand-rolled implementations.
- If a low-level language lacks a mature library for a topic, treat that implementation as a **stretch goal** instead of blocking progress through the curriculum.
- Keep WebRTC, OAuth, and graceful shutdown expectations realistic: they often require local/manual verification even if the rest of the repo is CI-friendly.
- HTTPS/TLS is usually easiest with local self-signed certs first, then a trusted local CA or test cert automation once the baseline works.

## Quick start

Start with `01-rest-api/README.md`, implement the required contract in `01-rest-api/python/`, then repeat the same contract in the other languages. Move to the next topic only after the baseline checks pass.
