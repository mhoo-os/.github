<!-- mhoo-os-context:start -->
### Mhoo OS Organization Profile: Mhoo OS context

This repository is the public organization profile and shared community-health repository.

- **Owns:** the public organization entrypoint; shared community-health files.
- **Does not own:** system architecture; application behavior; deployment or production status.
- **Architecture authority:** [accepted Mhoo OS blueprint](https://github.com/mhoo-os/mhoo/blob/108662ffc8a6dac69ab777d720775ec9879b49d0/docs/architecture/SYSTEM_BLUEPRINT.md) and [ADR-0008](https://github.com/mhoo-os/mhoo/blob/108662ffc8a6dac69ab777d720775ec9879b49d0/ADR/0008-twenty-framework-platform.md).
- **Current implementation evidence:** [repository-owned source and records](https://github.com/mhoo-os/.github/tree/main).
- **Deployment and production evidence:** owned separately by [Mhoo OS Infrastructure](https://github.com/mhoo-os/infrastructure/tree/main/docs); source, CI, publication, and rehearsal are not deployment or cutover proof.
- **Upstream context:** Mhoo-native organization repository; not an upstream product fork.
- **Contributors:** start with the [repository instructions](https://github.com/mhoo-os/.github/blob/main/AGENTS.md). Generated context is governed by [README governance](https://github.com/mhoo-os/mhoo/blob/main/docs/architecture/README_GOVERNANCE.md).
<!-- mhoo-os-context:end -->

## Current Twenty framework architecture

[ADR-0008](https://github.com/mhoo-os/mhoo/blob/0e94e6b00a3033215e4df3ab197e5559652c2436/ADR/0008-twenty-framework-platform.md)
makes the governed Mhoo-Twenty distribution Mhoo's sole application and data
framework. `@mhoo/core` is the deterministic foundational Twenty App; later
domain Apps use Twenty's native objects, permissions, APIs, MCP, Connections,
jobs, files, and UI primitives.

This is an accepted architecture decision, not implementation or production
proof. The v2.37 source, Apps, image, deployment, recovery, VPS replacement,
cutover, and old-runtime retirement remain separately gated.

# Mhoo OS

Mhoo OS is the engineering organization for Mhoo, an AI-native Business
Operating System. The system is composed of bounded repositories with separate
architecture, implementation, and operational evidence.

## Repositories

- [`mhoo-twenty`](https://github.com/mhoo-os/mhoo-twenty) — maintained
  Twenty distribution, sole application/data framework, and source owner for
  Mhoo Apps including `@mhoo/core`.
- [`core`](https://github.com/mhoo-os/core) — preserved source and bounded proof
  history for the superseded separate-Core implementation; it receives no new
  target behavior.
- [`connectors`](https://github.com/mhoo-os/connectors) — conditional home for
  accepted shared or integration-heavy provider seams. App-local OAuth uses
  Twenty Connections by default.
- Models and agents perform interpretation, reasoning, planning, synthesis,
  classification, recommendations, and natural-language generation.
- [`codex-lb`](https://github.com/mhoo-os/codex-lb) — model-routing and gateway
  behavior, not reasoning or business-state authority.
- [`infrastructure`](https://github.com/mhoo-os/infrastructure) — environments,
  deployment, networking, DNS, secret delivery, backups, recovery, monitoring,
  rollback, and cutover controls.

Platform coordination and cross-repository architecture live in [`mhoo`](https://github.com/mhoo-os/mhoo).

The internal control plane is the deterministic `@mhoo/core` Twenty App. Core
does not reason; models and agents reason through authorized tools. External
providers remain authoritative for provider facts, and no identifier supplied
by a caller grants Workspace authority.

For current implementation state, follow each repository's source and evidence
links. For deployment, recovery, production, and cutover state, use the scoped
records owned by Infrastructure. A README, merged source, green CI, publication,
or rehearsal does not prove a later state.
