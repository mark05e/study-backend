# 13 — gRPC

## Overview

Use protobuf and HTTP/2 to define a typed RPC service with generated clients and servers. This topic standardizes on one small unary service so the focus stays on tooling and transport rather than business logic.

**Why this order:** It introduces code generation and typed RPC after the raw socket and HTTP-based topics are already familiar.

## Required contract

- Define a single `echo.proto` file.
- Include one unary RPC:
  - service `EchoService`
  - rpc `Echo(EchoRequest) returns (EchoReply)`
- `EchoRequest` contains `string text`.
- `EchoReply` contains `string text`.
- The server returns the same text it receives.

## Acceptance checks

- Generate code from the shared `.proto`.
- Start a gRPC server.
- A client call with `text = "hello"` returns `text = "hello"`.

## Failure cases

- An empty `text` value should return an `INVALID_ARGUMENT`-style error if the stack makes that practical; otherwise document the chosen behavior.
- The baseline should not require handwritten protobuf serialization.
- Client and server must use the same shared `.proto` contract.

## Extensions

- Add a streaming RPC.
- Add a second service or method.
- Add transport security once the plaintext local baseline works.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Use `grpcio` and `grpcio-tools`. |
| **JavaScript** | Use `@grpc/grpc-js` with `@grpc/proto-loader` or generated stubs. |
| **Go** | Use `google.golang.org/grpc` and `protoc-gen-go`. |
| **Java** | Use `grpc-java` and a protobuf build plugin. |
| **Rust** | Recommended: `tonic`. |
| **Zig** | Use generated protobuf output plus an existing gRPC path or C bindings; pin the toolchain early. |
| **C++** | Use the official gRPC C++ stack. |
| **C** | Use a C-compatible gRPC library only if the build path is clear; otherwise treat as stretch. |
