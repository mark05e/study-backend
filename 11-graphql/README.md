# 11 — GraphQL

## Overview

Expose the same basic user data through a schema-driven API instead of fixed REST routes. This topic compares a different API style while keeping the domain model intentionally small.

**Why this order:** It reuses familiar data operations but introduces schema design, resolvers, and a single endpoint.

## Required contract

- Expose `POST /graphql`.
- Define a `User` type with `id` and `name`.
- Support:
  - query `users`
  - query `user(id)`
  - mutation `createUser(name)`
- Use an in-memory store for the baseline implementation.

## Acceptance checks

- `query { users { id name } }` returns an empty list initially.
- `mutation { createUser(name: "Alice") { id name } }` returns a created user.
- `query { user(id: 1) { id name } }` returns the created user.

## Failure cases

- Invalid queries return a GraphQL error response.
- Empty names in `createUser` return an error response.
- The baseline should not require building a GraphQL engine by hand.

## Extensions

- Add update or delete mutations.
- Add schema-first code generation where the stack supports it.
- Add persistence behind the resolvers.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: Strawberry or Ariadne. |
| **JavaScript** | Recommended: Apollo Server or `graphql-js`. |
| **Go** | Recommended: `gqlgen` or `graphql-go`. |
| **Java** | Recommended: GraphQL Java. |
| **Rust** | Recommended: `async-graphql` or `juniper`. |
| **Zig** | Prefer an existing library or parser plus a thin execution layer; avoid full hand-rolled GraphQL for the baseline. |
| **C++** | Prefer an existing library stack over building the execution engine yourself. |
| **C** | Treat a C implementation as advanced unless you have a clear library path. |
