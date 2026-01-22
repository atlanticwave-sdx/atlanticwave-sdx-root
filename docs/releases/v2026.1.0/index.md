---
title: 2026.1.0
parent: Releases
nav_order: 2026010
---

# AW-SDX 2026.1.0

**Release Date:** 01/22/2026  
**Component Baseline:** v3.2.0  
**Automation:** GitHub Actions (CI/CD)  
**Distribution:** Versioned source + container images  
**Scope:** SDX Controller, SDX-LC, Kytos-SDX, OESS-SDX, PCE, Data Models, Messaging/Telemetry

---

## Major Changes

AW-SDX 2026.1.0 is a coordinated software release of the AtlanticWave-SDX stack that strengthens multi-domain topology exchange and point-to-point L2VPN service provisioning across integrated controller environments. This release emphasizes interoperability through the official Topology Data Model, operational compatibility through versioned and legacy APIs, and improved robustness in topology loading, error handling, and control-plane messaging. Release artifacts are built and published through automated CI/CD workflows.

---

## Packages and Components

### SDX Controller

- Supports versioned L2VPN service lifecycle APIs, including `/l2vpn/1.0` and legacy `/v1/l2vpn_ptp`.
- Enhanced error handling, including protection against non-JSON responses.
- Improved RabbitMQ-based control-plane messaging robustness.
- Non-blocking topology initialization.

### SDX Local Controller (SDX-LC)

- Domain-facing endpoints for controller integrations and orchestration.
- Improved exception handling in LC message processing.
- Updated controller API usage when placing connections.
- Correct topology return handling.

### Kytos-SDX NApp

- Topology export from Kytos-ng to SDX-LC using the official Topology Data Model.
- Point-to-point L2VPN provisioning (MEF EVCs) via SDX-LC.
- New and legacy L2VPN APIs retained for compatibility.
- SDX Port/Link modeling with rich metadata.
- Support for `sdx_vlan_range` and `sdx_nni` metadata.
- CI workflows, coverage reporting, and unit tests.

### OESS-SDX

- Integration of AW-SDX capabilities into OESS-MPLS environments.
- Topology export to SDX-LC using the official Topology Data Model.
- L2VPN provisioning via SDX-LC with legacy compatibility.
- VLAN range and NNI metadata support.

### Path Computation Engine (PCE)

- Constrained shortest-path computation and domain-aware path breakdowns.
- Refactored PCE logic with improved modularity and deployability.
- CI linting, formatting, and coverage improvements.

### Messaging and Telemetry (RabbitMQ / BAPM)

- RabbitMQ-based messaging for SDX control-plane communications.
- Improved consumer robustness and error handling.
- Telemetry and BAPM integration points.

### Data Models and APIs

- Official SDX Topology Data Model.
- SDX Port and SDX Link abstractions.
- Improved MongoDB document consistency.
- Topology parsing, validation, and exchange utilities.

---

## Future Enhancements (Non-Claims)

- Additional service models beyond point-to-point L2VPN.
- Expanded measurement and telemetry workflows.
- Further scalability optimizations for large-scale TE requests.
- Continued improvements to testing and deployment automation.

---

## Appendix A — Component Traceability (Changelog → Release Claims)

### SDX Controller

| Changelog Evidence | Release Claim |
|---|---|
| New and legacy L2VPN APIs | Stable, versioned service APIs with backward compatibility |
| Non-JSON error handling | Improved controller robustness |
| RabbitMQ consumer fixes | Enhanced messaging reliability |
| Non-blocking startup | Improved initialization behavior |
| MongoDB usage | Persistent state management |

### SDX Local Controller (SDX-LC)

| Changelog Evidence | Release Claim |
|---|---|
| Updated Kytos API usage | Domain-specific orchestration |
| Exception handling | Robust control-plane messaging |
| Correct topology returns | Consistent topology representation |

### Kytos-SDX NApp

| Changelog Evidence | Release Claim |
|---|---|
| Topology export | SDX Topology Data Model usage |
| L2VPN provisioning | MEF EVC support |
| VLAN / NNI metadata | Flexible inter-domain connectivity |

### OESS-SDX

| Changelog Evidence | Release Claim |
|---|---|
| OESS integration | Operational SDX interoperability |
| Topology export | Cross-controller topology exchange |

### Path Computation Engine (PCE)

| Changelog Evidence | Release Claim |
|---|---|
| PCE refactor | Multi-domain path computation |
| CI improvements | Reliability and maintainability |

### CI/CD and Packaging

| Changelog Evidence | Release Claim |
|---|---|
| GitHub Actions | Automated CI/CD |
| Container publishing | Reproducible distribution |
EOF

