# 11 — GraphQL

## Overview

Single POST endpoint; parse query/mutation, resolve against schema. Alternative API style to REST.

**Why this order:** Single endpoint, schema, queries/mutations; alternative API style to REST.

**Minimal spec:** One type (e.g. User), query (list/get) and mutation (create); use same data as REST topic.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Strawberry or Ariadne. |
| **JavaScript** | Apollo Server or graphql-js. |
| **Go** | gqlgen or graphql-go. |
| **Java** | GraphQL Java. |
| **Rust** | async-graphql or juniper. |
| **Zig** | Embed lib (e.g. libgraphqlparser) or minimal hand-rolled. |
| **C++** | libgraphqlparser or minimal hand-rolled. |
| **C** | libgraphqlparser or minimal hand-rolled. |
