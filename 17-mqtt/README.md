# 17 — MQTT

## Overview

Work with a lightweight pub/sub protocol and a topic-based broker. This follows AMQP because it keeps the broker model but shifts from queue semantics to topic fan-out.

**Why this order:** It introduces publish/subscribe messaging, topic routing, and broker-delivered events.

## Required contract

- Connect to an MQTT broker such as Mosquitto.
- Subscribe to topic `study/demo`.
- Publish a text message to `study/demo`.
- Use QoS `0` for the baseline.

## Acceptance checks

- A subscriber connected before publish receives the published message.
- Publishing `hello` results in the subscriber receiving `hello`.
- The publisher and subscriber can run as separate processes or tasks.

## Failure cases

- Broker connection failures must be surfaced clearly.
- The baseline does not require retained messages.
- Topic mismatches should not silently appear successful.

## Extensions

- Add retained messages.
- Add QoS `1`.
- Subscribe to multiple topics with wildcards.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `paho-mqtt`. |
| **JavaScript** | Recommended: `mqtt.js`. |
| **Go** | Recommended: Eclipse Paho for Go. |
| **Java** | Recommended: Eclipse Paho. |
| **Rust** | Recommended: `rumqtt`. |
| **Zig** | Use `paho.c` bindings or another clear MQTT client path. |
| **C++** | Use `paho.mqtt.cpp` or `paho.mqtt.c`. |
| **C** | Recommended: `paho.c`. |
