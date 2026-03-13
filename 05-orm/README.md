# 05 — ORM

## Overview

CRUD over a database; builds on "talking to a service." Introduces migrations and models. Pick one DB (e.g. SQLite or Postgres).

**Why this order:** CRUD over a DB; builds on "talking to a service." Introduces migrations and models.

**Minimal spec:** One entity (e.g. User); create, read, update, delete; use migrations for schema.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | SQLAlchemy or Django ORM. |
| **JavaScript** | Prisma or Drizzle. |
| **Go** | GORM or sqlx. |
| **Java** | JPA/Hibernate. |
| **Rust** | Diesel or SQLx. |
| **Zig** | SQLite C API or thin wrapper. |
| **C++** | SQLite C API or thin wrapper (e.g. sqlite3). |
| **C** | SQLite C API (sqlite3). |
