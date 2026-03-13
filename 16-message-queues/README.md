# 16 — Message Queues (AMQP)

## Overview

Send work through a broker instead of directly between caller and worker. This topic standardizes on RabbitMQ so every language exercises the same queue-based delivery pattern.

**Why this order:** It introduces brokered communication and acknowledgements after direct request/response topics are already familiar.

## Required contract

- Connect to RabbitMQ using `AMQP_URL`.
- Publish JSON messages to a queue named `jobs`.
- Run one consumer that reads from `jobs`, logs or prints the payload, and acknowledges the message.
- Use a message shape of `{"text":"<string>"}` for the baseline.

## Acceptance checks

- Publishing `{"text":"hello"}` places a message on the queue.
- The consumer receives the message and processes it once.
- The message is acknowledged and does not remain stuck unacked.

## Failure cases

- If RabbitMQ is unavailable, fail clearly at startup or connection time.
- Invalid message payloads should be rejected or logged clearly.
- The baseline should not depend on a vendor-specific broker extension.

## Extensions

- Add dead-letter handling.
- Add request/reply correlation IDs.
- Run multiple consumers to observe work distribution.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `pika`. |
| **JavaScript** | Recommended: `amqplib`. |
| **Go** | Use a maintained AMQP client library. |
| **Java** | Recommended: Spring AMQP or the RabbitMQ Java client. |
| **Rust** | Recommended: `lapin`. |
| **Zig** | Use `rabbitmq-c` or clear C bindings. |
| **C++** | Use `rabbitmq-c` bindings or another maintained client. |
| **C** | Recommended: `rabbitmq-c`. |
