# 16 — Message queues (AMQP)

## Overview

Producer/consumer with RabbitMQ (or similar). Request/reply or work queues; complements MQTT (pub/sub).

**Why this order:** Request/reply or work queues; RabbitMQ etc. Complements MQTT.

**Minimal spec:** Producer sends message to a queue; consumer reads and processes (e.g. echo or log).

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | pika. |
| **JavaScript** | amqplib. |
| **Go** | streadway/amqp. |
| **Java** | Spring AMQP or amqp-client. |
| **Rust** | lapin. |
| **Zig** | rabbitmq-c or similar. |
| **C++** | rabbitmq-c or similar. |
| **C** | rabbitmq-c. |
