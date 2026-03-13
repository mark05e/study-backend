# 13 — gRPC

## Overview

HTTP/2 + protobuf; tooling and codegen in each language to learn. Use same service (e.g. echo or user CRUD) across all.

**Why this order:** HTTP/2 + protobuf; tooling and codegen in each language to learn.

**Minimal spec:** One .proto with a service (e.g. Echo or UserService); implement server and client in each language.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | grpcio, grpcio-tools (codegen). |
| **JavaScript** | @grpc/grpc-js, @grpc/proto-loader. |
| **Go** | google.golang.org/grpc, protoc-gen-go. |
| **Java** | grpc-java, protobuf-maven-plugin. |
| **Rust** | tonic. |
| **Zig** | protoc output + zig gRPC or C bindings. |
| **C++** | gRPC C++ (protobuf + grpc). |
| **C** | gRPC C (grpc_c library). |
