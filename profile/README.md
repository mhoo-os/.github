# Mhoo OS

<p align="center">
  <img src="./assets/mhoo-snout-transparent-1024.png" width="160" alt="Mhoo Snout logo" />
</p>

Mhoo OS is the engineering organization for Mhoo, an AI-native Business Operating System.

## Repositories

- [`mhoo-twenty`](https://github.com/mhoo-os/mhoo-twenty) — maintained Twenty UI and Workspace layer; clean-bootstrap source inputs preserve Twenty `v2.30.1` while production cutover remains NO-GO.
- [`codex-lb`](https://github.com/mhoo-os/codex-lb) — AI routing infrastructure.
- [`core`](https://github.com/mhoo-os/core) — tenant-scoped business-state layer with local-only Phase 0 proofs; it has no production authority.
- [`connectors`](https://github.com/mhoo-os/connectors) — future external integrations, with Clover planned through Nango.
- [`infrastructure`](https://github.com/mhoo-os/infrastructure) — deployment, environments, security, and operations.

Platform coordination and cross-repository architecture live in [`mhoo`](https://github.com/mhoo-os/mhoo).

## Current phase

The organization is building a fresh, local-only bootstrap. There is no production cutover, old database import, customer migration, Clover credential setup, or hosted Core authority. Core's Phase 0 proofs are local-only and do not establish production deployment, provider ingestion, or an authority transfer.
