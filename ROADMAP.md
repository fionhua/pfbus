# PFBus Protocol Roadmap & Engineering Backlog

This document outlines the planned technical milestones for the PFBus Protocol and its official ecosystem tooling.

---

## 🎯 Current Status (v1.5.0 Released)

- [x] **Normative Protocol Specification (v1.5)**: Plain-text envelope syntax with zero cloud lock-in.
- [x] **Meeting Orchestration Specifications (v1.0 – v1.7)**: Complete lifecycle state machine from roll-call to final scoring.
- [x] **Bilingual Documentation Baseline**: English as the normative default (SSOT); Chinese original lineage preserved as `_zh.txt`.
- [x] **Initial Conformance Test Suite**: Basic test vectors staged in [`test-vectors/conformance.json`](test-vectors/conformance.json).
- [x] **Governance & Licensing**: Apache-2.0 open licensing with authorized specification release controls ([`GOVERNANCE.md`](GOVERNANCE.md)).

---

## 📋 Engineering Backlog (Release & Development Roadmap)

### Milestone 1: Multi-Language Reference Parsers & SDKs (The Core Leverage)
The defining characteristic of an industry-standard protocol is multi-platform software tooling.

- [ ] **Python Reference SDK (`pfbus-python`)**:
  - Pure-Python zero-dependency parser and serializer (`pip install pfbus`).
  - Strict line-1 envelope validation, `mailto`/`cc` extraction, and command handling.
  - Native integration with Python-based AI agent frameworks (LangChain, AutoGen, LlamaIndex, CrewAI).
- [ ] **TypeScript / JavaScript SDK (`@pfbus/core`)**:
  - Lightweight parser and validator for browser extensions, Node.js daemons, and Electron apps (`npm install @pfbus/core`).
  - Web-stream friendly with zero third-party dependencies.
- [ ] **Go Core Package (`github.com/fionhua/pfbus/pkg/pfbus`)**:
  - High-performance streaming envelope parser and broker dispatcher extracted from production bridge code.

### Milestone 2: Conformance Test Suite Expansion & CI Automation
- [ ] **Extended Test Vectors**:
  - Edge cases: whitespace tolerance, Unicode nicknames, multi-line JSON payload escaping, malformed tag rejection.
  - State machine transition vectors for meeting lifecycles (PREP ➔ RULES ➔ ACTIVE ➔ CLOSED).
- [ ] **Automated GitHub Actions CI**:
  - Automated test runner validating Python, TypeScript, and Go SDK implementations against `test-vectors/conformance.json`.

### Milestone 3: Ecosystem Adapters & DevTools
- [ ] **PFBus CLI (`pfbus-cli`)**:
  - Command-line linter and validator: `pfbus lint message.txt` / `pfbus format`.
- [ ] **Model Context Protocol (MCP) Bridge**:
  - Bi-directional bridge adapter connecting PFBus multi-agent message streams with Claude / Gemini MCP tools.

---

## 📝 Governance of Backlog Items

Feature proposals and implementation PRs are tracked via GitHub Issues. Please consult [GOVERNANCE.md](GOVERNANCE.md) for contribution and RFC procedures.
