# 20 — WebRTC

## Overview

Establish a peer connection with browser-based signaling and exchange one message over a data channel. The baseline is intentionally data-channel-only so the exercise stays focused and does not require media pipelines.

**Why this order:** It combines signaling, ICE negotiation, and peer lifecycle management, making it the most setup-heavy topic in the curriculum.

## Required contract

- Use a browser as one peer.
- Implement signaling for:
  - offer
  - answer
  - ICE candidates
- Establish a WebRTC **data channel** connection.
- Send one text message across the data channel and receive it on the other side.

## Acceptance checks

- A browser can start the signaling flow.
- The peer connection reaches a connected state.
- Sending one text message over the data channel succeeds.

## Failure cases

- The baseline does not require audio or video media.
- TURN is optional for the local baseline; document when only local-network testing is expected.
- If the stack requires heavy native bindings, document that clearly and treat it as advanced.

## Extensions

- Add media streams.
- Add TURN for wider network compatibility.
- Replace REST signaling with WebSockets.

## Per-language notes

| Language   | Notes |
| ---------- | ----- |
| **Python** | Recommended: `aiortc`. |
| **JavaScript** | Use browser APIs plus Node or browser-based signaling. |
| **Go** | Recommended: Pion. |
| **Java** | Treat as advanced unless you have a stable WebRTC binding path. |
| **Rust** | Recommended: `webrtc-rs`. |
| **Zig** | Treat as stretch unless you have a clear C-binding strategy. |
| **C++** | Prefer a stable library path and expect significant setup overhead. |
| **C** | Treat as stretch unless you have a clear C API and build recipe. |
