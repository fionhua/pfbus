# PFBus Architecture & Execution Model

This document outlines the architectural principles behind PFBus message routing, session governance, and multi-agent coordination.

---

## 1. The Core Problem: The Silo Problem of AI Chats

Modern software engineers frequently use multiple distinct AI assistants simultaneously—for example, ChatGPT for high-level design, Claude for deep code refactoring, Gemini for multi-modal reasoning, and DeepSeek for mathematical logic.

Traditionally, each AI runs as an isolated web tab or local process. Moving context, tasks, and critiques between these models requires repetitive, error-prone manual copying and pasting.

PFBus solves this by defining a lightweight, human-readable text envelope that transforms isolated AI sessions into an orchestrated fleet.

---

## 2. The 5-Layer Coordination Pipeline

In a standard PFBus deployment (such as My AI Buddies), messages flow through five clear layers:

```text
Human in Telegram Group
        ↓
Local Coordination Bridge (Windows)
        ↓
Browser Extension / Native Accessibility (UIA)
        ↓
Target AI Sessions (Web tabs / IDE workspaces)
        ↓
Output Parsing & Deterministic Dispatch
```

1. **Human Instruction Layer (Telegram Group)**:
   Telegram serves as the human-facing conversation hub, review feed, and audit ledger.
2. **Local Bridge**:
   A local desktop process manages active sessions, verifies Chat Bus permissions, and resolves model nicknames to physical windows.
3. **Native Delivery**:
   Messages are injected cleanly into the target AI's input box via standard accessibility APIs (UIA) or browser extension DOM bindings, preserving native chat history.
4. **Autonomous AI Turn**:
   The receiving AI processes the context and responds. If it wishes to delegate a subtask or address another peer, it prepends the `[PFBus][mailto:...]` envelope.
5. **Deterministic Dispatch**:
   The bridge extracts the completed response turn, verifies envelope validity, and dispatches the payload to the designated recipient.

---

## 3. Core Design Principles

### Single Source of Truth (SSOT)
The bridge adheres strictly to deterministic state transitions. A message is only dispatched when an AI model completes its generation turn, preventing speculative interruptions during active thinking (Chain of Thought).

### Human Sovereignty & Permission Gates
- **Meeting Gate**: Formal meetings can only be initiated by a human sending `/meet` in Telegram. Models cannot spontaneously trigger meeting locks.
- **Chat Bus Seat Gate**: An AI node can only receive messages if the human administrator has granted it an active seat. Delivery to unauthorized nodes is blocked at the bridge layer.

### Zero-Privilege Security Guarantee
PFBus envelopes are strictly text strings. An AI assistant reading or emitting a PFBus envelope is never required to execute shell scripts, open network sockets, or bypass container sandboxes.
