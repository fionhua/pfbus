# PFBus Protocol

[![Specification: v1.5](https://img.shields.io/badge/spec-v1.5-blue.svg)](spec/v1.5/PFBus-Protocol.txt)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![Official Portal](https://img.shields.io/badge/portal-pfbus.net-orange.svg)](https://pfbus.net/)

[中文说明 (Chinese Readme)](README.zh-CN.md) | [Official Website (pfbus.net)](https://pfbus.net/) | [Latest Spec (v1.5)](spec/v1.5/PFBus-Protocol.txt)

---

**PFBus (PocketFleet Bus)** is an open, lightweight, text-based communication protocol designed for human–AI and multi-AI coordination. 

PFBus defines a standardized plain-text envelope that routes structured messages, orchestrates task handoffs between autonomous AI nodes, and conducts synchronized multi-agent meetings.

The PFBus protocol is independent of any single model provider, framework, or proprietary cloud service. Message delivery, session coordination, and seat access permissions are governed by compatible implementations.

> **"PFBus is the protocol. My AI Buddies is the product built on it."**

---

## 🚀 Quick Syntax (15 Seconds)

A PFBus envelope occupies the **very first line** of an output. The message body begins on the following line.

```text
[PFBus][mailto:@NodeA];[waitReply]
Please analyze this pull request and identify architectural risks.
```

### General Syntax
```text
[PFBus][mailto:%s];[cc:%s];[waitReply|noReply]
```
- **`mailto`**: Single primary recipient. Use `@NodeName` for AI nodes; use configured nicknames for human participants.
- **`cc`**: Optional carbon-copy recipients (valid in meeting mode, comma-separated). Omit the entire segment when unused.
- **`waitReply`**: Indicates a response is required to proceed.
- **`noReply`**: Marks notification-only messages or final handoffs, preventing infinite reply loops.

### Meeting Commands
- `[PFBus][signup:%s]`: Roll-call check-in, where `%s` is your meeting nickname.
- `[PFBus]/rules`: Host AI only, followed on the next line by task assignment JSON.
- `[PFBus]/meetover`: Sent by human or host AI to conclude the meeting with scored deliverables.

---

## 🛠️ Official First-Party Implementation

### **[My AI Buddies](https://pfbus.net/)**
My AI Buddies is the first-party desktop implementation developed by the PFBus authors. It connects supported browser AI web sessions (ChatGPT, Claude, Gemini, DeepSeek, Qwen, Grok, Doubao) and desktop Code AIs with human engineers via a local Windows bridge and Telegram.

- **Free Configuration**: Includes 2 AI seats for personal use out of the box.
- **Privacy-First**: Operates strictly via local accessibility injection (UIA) and browser extension integration, requiring zero API keys and zero cloud lock-in.

---

## 🛡️ Security & Non-Goals

PFBus is strictly a **text-level routing specification**.
- **No System Privileges**: PFBus does NOT grant operating system access, shell execution, or terminal command permissions.
- **No SSRF or Network Scans**: Compliant implementations never ask AI models to invoke `curl`, scan local sockets, or query `127.0.0.1`.
- **Pure Text Delimiters**: `[PFBus]` is parsed as plain text by the host bridge. Message payloads remain completely opaque and unmutated.

---

## 📂 Repository Structure

- [`spec/`](spec/): Immutable official protocol specifications categorized by version (`v1.0` through `v1.5`).
- [`docs/`](docs/): Architecture overview, workflow state machines, and implementation registry.
- [`examples/`](examples/): Verified text-envelope examples for direct talk and structured meetings.
- [`test-vectors/`](test-vectors/): Conformance test cases for parser validation.

---

## ⚖️ Governance & License

- **Specification License**: Licensed under the [Apache License, Version 2.0](LICENSE).
- **Governance**: Anyone may implement or derive independent protocols from PFBus. Official version publications and trademark governance are maintained by the project authors according to [GOVERNANCE.md](GOVERNANCE.md).
