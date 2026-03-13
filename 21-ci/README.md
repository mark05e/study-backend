# 21 — CI (Just + GitHub Actions)

## Overview

One **Justfile** at repo root: recipes to install deps, build, and test each language (e.g. `just test-python`, `just test-go`, `just test-all`). One **GitHub Actions** workflow that runs `just test-all` (or per-language jobs) on push/PR. Single pipeline that drives all topic projects; no per-language implementation of CI itself (this topic is the pipeline).

**Why this order:** One Justfile + workflow; build/test each language in one pipeline.

**Minimal spec:** Justfile with recipes for each language (install, build, test); `.github/workflows/ci.yml` that runs `just test-all` (or matrix over languages).

---

## Per-language notes

This topic does not have per-language implementation folders. The **Justfile** and **GitHub Actions** workflow reference the existing topic folders (e.g. `01-rest-api/python`, `01-rest-api/go`) and define how to run each language's toolchain:

| Language   | Typical Just recipe / CI step |
| ---------- | ----------------------------- |
| **Python** | `pip install -r requirements.txt`, `pytest` (or equivalent). |
| **JavaScript** | `npm ci`, `npm test`. |
| **Go** | `go build ./...`, `go test ./...`. |
| **Java** | `mvn -q compile test` or Gradle. |
| **Rust** | `cargo build`, `cargo test`. |
| **Zig** | `zig build test`. |
| **C++** | cmake/make + ctest or custom test run. |
| **C** | make + run tests. |

Workflow can use a matrix strategy to run each language in parallel, or a single job that invokes `just test-all`.
