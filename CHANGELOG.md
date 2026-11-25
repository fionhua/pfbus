# PFBus Protocol Changelog

All notable changes to the PFBus specification are documented in this file.

---

## [v1.5] - 2026-11-25

### Changed
- Standardized Code AI response handling: Code AIs reply using standard plain text in their native chat session to complete collaboration, eliminating private queue callbacks.
- Fully unified daily 1:1 conversation and meeting mode envelopes under canonical `[PFBus][mailto:%s];[waitReply|noReply]` syntax.
- Removed legacy `(ref: pfcr-...)` noise tokens and deprecated `[onceMode]` experimental tags.
- Verified byte-level synchronization with the official edge portal at `https://pfbus.net/PFBus-Protocol.txt`.

---

## [v1.4] - 2026-11-18

### Added
- Explicit guidance for multi-envelope parallel parsing within a single model output turn.
- Clarified `waitReply` vs `noReply` semantics to prevent conversational infinite loops between models.

---

## [v1.3] - 2026-11-08

### Changed
- Deprecated local curl terminal execution instructions in favor of native UI accessibility and browser extension stream extraction.
- Formalized zero-network privilege guarantee for evaluating Code AIs.

---

## [v1.2] - 2026-10-25

### Added
- Explicit distinction between Telegram `/meet` meeting states and non-meeting point-to-point daily conversation routing.
- Added Chat Bus receive permission gates.

---

## [v1.1] - 2026-10-15

### Added
- `[PFBus][signup:%s]` roll-call check-in syntax for multi-agent meetings.
- Enhanced JSON structure definition for `[PFBus]/rules` host tasks.

---

## [v1.0] - 2026-10-07

### Added
- Initial public release of PFBus (PocketFleet Bus) protocol specification.
- Core envelope syntax: `[PFBus][mailto:%s];[cc:%s];[waitReply|noReply]`.
- Baseline meeting lifecycle commands: `/rules`, `/meetover`.
