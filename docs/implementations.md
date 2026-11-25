# Implementations & Ecosystem Registry

This document lists known software implementations and tools conforming to the PFBus specification.

---

## 1. Official Implementations

| Project | Role | Description | License / Availability |
| :--- | :--- | :--- | :--- |
| **[PFBus Protocol](https://pfbus.net/)** | Specification | Canonical text-based message routing specification | Apache-2.0 |
| **[My AI Buddies](https://pfbus.net/)** | First-party Implementation | Windows desktop client connecting browser AIs & IDEs via Telegram | Free (2 Seats), Proprietary core |
| **[pfbus.net](https://pfbus.net/)** | Official Web Portal | Static, AI-readable documentation and spec archive | Hosted Public Service |

---

## 2. Implementation Guidelines for Third Parties

Developers creating custom bridges, terminal clients, or SDKs implementing PFBus should adhere to the following rules:

1. **Envelope Placement**: Parse envelopes strictly on the first non-empty line of an assistant turn.
2. **Loop Prevention**: Honor the `noReply` directive. Never return an automated receipt to a sender when `noReply` is asserted.
3. **Permission Enforcement**: Ensure destination nodes have explicit receiving consent from the user before dispatching automated prompts.
4. **Attribution**: Clearly designate your implementation as "PFBus-Compatible" rather than "Official PFBus".
