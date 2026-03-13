# 20 — WebRTC

## Overview

Signaling via your REST or WebSockets server; use each language's WebRTC lib. Browser as second peer. Signaling + STUN/TURN + media; hardest conceptually and in setup.

**Why this order:** Signaling + STUN/TURN + media; hardest conceptually and in setup.

**Minimal spec:** Server-side signaling (offer/answer, ICE candidates); data channel or media; browser as other peer.

---

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | aiortc or pywebrtc. |
| **JavaScript** | Node: node-webrtc or use browser as peer; signaling in Node. |
| **Go** | Pion. |
| **Java** | Webrtc-java or JNI to native. |
| **Rust** | webrtc-rs. |
| **Zig** | C bindings to libwebrtc or GStreamer. |
| **C++** | libwebrtc or GStreamer. |
| **C** | libwebrtc C API or GStreamer. |
