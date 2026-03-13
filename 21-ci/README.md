# 21 — CI (Just + GitHub Actions)

## Overview

Define one repo-level way to build and test the curriculum. This topic is about automation, not a language-specific implementation, so it standardizes entrypoints for the rest of the repo.

**Why this order:** CI only works well after the repo has a clear contract for what each language and topic should run.

## Required contract

- Create one root `Justfile`.
- Define at least these recipes:
  - `test-python`
  - `test-javascript`
  - `test-go`
  - `test-java`
  - `test-rust`
  - `test-zig`
  - `test-cpp`
  - `test-c`
  - `test-all`
- Add `.github/workflows/ci.yml` that runs the same entrypoints used locally.
- Treat topics marked local/manual in the root prerequisites matrix as opt-in or separately gated.

## Acceptance checks

- `just test-all` runs locally.
- The GitHub Actions workflow triggers on push or pull request.
- CI output makes it clear which language or topic failed.

## Failure cases

- Do not require local-only topics such as OAuth or WebRTC on the default CI path unless a mock/test harness exists.
- Avoid hidden per-language commands that are not exposed through `Justfile`.
- Do not make CI depend on developer-specific machine paths.

## Extensions

- Add a matrix job per language.
- Add service containers for Redis, MinIO, RabbitMQ, and Mosquitto.
- Add formatting and lint recipes alongside test recipes.

## Per-language notes

This topic does not have per-language implementation folders. The root `Justfile` and workflow should reference the existing topic folders and provide one predictable entrypoint per language:

| Language   | Typical Just recipe / CI step |
| ---------- | ----------------------------- |
| **Python** | `pip install -r requirements.txt`, then `pytest` or equivalent. |
| **JavaScript** | `npm ci`, then `npm test`. |
| **Go** | `go build ./...`, then `go test ./...`. |
| **Java** | `mvn -q compile test` or the Gradle equivalent. |
| **Rust** | `cargo build`, then `cargo test`. |
| **Zig** | `zig build test`. |
| **C++** | `cmake`/`ctest` or a stable build-and-test wrapper. |
| **C** | `make` plus a stable test target. |
