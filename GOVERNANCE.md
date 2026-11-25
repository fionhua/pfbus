# PFBus Governance & Contribution Model

> "Anyone may build upon and extend PFBus. Only authorized maintainers may publish an official PFBus specification."

---

## 1. Principles & Rights Structure

PFBus is governed according to a clear, three-tier rights model:

### Tier 1: Public Use & Derivative Rights
Anyone is free to:
- Read, study, and implement the PFBus protocol specification.
- Build free or commercial applications conforming to PFBus without licensing fees.
- Fork this repository and create independent derivative protocols or experimental extensions under the terms of the Apache-2.0 License.
- Submit Issues and Pull Requests to improve the official specification.

### Tier 2: Official Governance & Maintenance
- Official specification releases and version numbers are exclusively maintained by the designated repository maintainers.
- Community Pull Requests are reviewed on merit (technical correctness, backwards compatibility, and cross-model feasibility) but do not automatically alter the official specification.
- Any official specification revision requires review by the core engineering fleet and formal authorization by the project maintainer (@fionhua).

### Tier 3: Original Author Rights & Brand Policy
- The original authors retain authorship, attribution, and trademark rights associated with the "PFBus" name and official logos.
- Derivative protocols must clearly identify their independent identity and must not claim official endorsement or certification by PFBus without explicit written authorization.

---

## 2. Specification Immutability & Versioning

- **Immutable Releases**: Once a specification version (e.g. `spec/v1.5/`) is published and tagged with a Git Release, its contents are frozen. No retroactive alterations are permitted.
- **New Revisions**: Future enhancements (e.g. `v1.6`) will be introduced in a distinct version directory (`spec/v1.6/`), accompanied by an updated changelog and migration guide.

---

## 3. How to Contribute (RFC Process)

1. **Discuss**: Open a GitHub Discussion or Issue describing the proposed improvement or ambiguous edge case.
2. **Draft**: Propose specific envelope grammar or state machine modifications.
3. **Review**: Maintainers evaluate cross-platform compatibility across both browser-hosted AIs and local terminal/IDE agents.
4. **Adoption**: Approved changes are staged for the next minor or major protocol version cut.
