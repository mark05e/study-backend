# 17 — MQTT

## Overview

Pub/sub protocol; broker (e.g. Mosquitto), QoS, retained messages.

**Why this order:** Pub/sub protocol; broker, QoS, retained messages.

**Minimal spec:** Publish to a topic; subscribe to same topic; optional QoS and retained message.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | paho-mqtt. |
| **JavaScript** | mqtt.js. |
| **Go** | eclipse/paho.golang. |
| **Java** | Eclipse Paho. |
| **Rust** | rumqtt. |
| **Zig** | paho.c or similar. |
| **C++** | paho.mqtt.c or paho.mqtt.cpp. |
| **C** | paho.c. |
