# 05 — Persistence / Data Access

## Overview

Persist the user data model to a real database instead of keeping it only in memory. The folder name remains `05-orm` for repo stability, but the topic is intentionally broader than ORM because some languages fit better with lightweight SQL access than full object mapping.

**Why this order:** It introduces durable storage, schema management, and CRUD semantics after the basic HTTP topics are already familiar.

## Required contract

- Use **SQLite** for the baseline implementation.
- Create a `users` table with at least `id` and `name`.
- Expose these routes:
  - `GET /users`
  - `GET /users/{id}`
  - `POST /users`
  - `DELETE /users/{id}`
- Initialize the schema on startup or through a small migration/bootstrap step.

## Acceptance checks

- `POST /users` creates a user in SQLite.
- `GET /users/{id}` returns that user.
- Restarting the service with the same SQLite file keeps the data.
- `DELETE /users/{id}` removes the user and later reads return `404`.

## Failure cases

- Empty or invalid `name` returns `400`.
- Reading or deleting a missing user returns `404`.
- If the database file cannot be opened or initialized, fail clearly at startup.

## Extensions

- Add `PUT /users/{id}`.
- Add a query builder or ORM layer where it makes sense for the language.
- Swap SQLite for Postgres after the baseline is working.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: SQLAlchemy. Alternative: Django ORM. |
| **JavaScript** | Recommended: Prisma or Drizzle. |
| **Go** | Recommended: `sqlx` or GORM depending on how much abstraction you want. |
| **Java** | Recommended: JPA/Hibernate. |
| **Rust** | Recommended: SQLx or Diesel. |
| **Zig** | Use the SQLite C API or a very thin wrapper. |
| **C++** | Use the SQLite C API or a thin wrapper. |
| **C** | Use the SQLite C API directly. |
