<!-- mhoo-os-context:start -->
### Mhoo OS Organization Profile: Mhoo OS context

This repository is the public organization profile and shared community-health repository.

- **Owns:** the public organization entrypoint; shared community-health files.
- **Does not own:** system architecture; application behavior; deployment or production status.
- **Architecture authority:** [accepted Mhoo OS blueprint](https://github.com/mhoo-os/mhoo/blob/1374bbbe2a059320c29c8268ff971efbd9dfa256/docs/architecture/SYSTEM_BLUEPRINT.md) and [ADR-0006](https://github.com/mhoo-os/mhoo/blob/1374bbbe2a059320c29c8268ff971efbd9dfa256/ADR/0006-mhoo-os-system-architecture-blueprint.md).
- **Current implementation evidence:** [repository-owned source and records](https://github.com/mhoo-os/.github/tree/main).
- **Deployment and production evidence:** owned separately by [Mhoo OS Infrastructure](https://github.com/mhoo-os/infrastructure/tree/main/docs); source, CI, publication, and rehearsal are not deployment or cutover proof.
- **Upstream context:** Mhoo-native organization repository; not an upstream product fork.
- **Contributors:** start with the [repository instructions](https://github.com/mhoo-os/.github/blob/main/AGENTS.md). Generated context is governed by [README governance](https://github.com/mhoo-os/mhoo/blob/main/docs/architecture/README_GOVERNANCE.md).
<!-- mhoo-os-context:end -->

# Mhoo OS

Mhoo OS is the engineering organization for Mhoo, an AI-native Business
Operating System. The system is composed of bounded repositories with separate
architecture, implementation, and operational evidence.

## Repositories

- [`mhoo-twenty`](https://github.com/mhoo-os/mhoo-twenty) — maintained
  Twenty-based human application and Workspace layer. Twenty is the sole human
  identity, authentication, session, membership, authorization, active-Workspace,
  and Workspace-lifecycle authority.
- [`core`](https://github.com/mhoo-os/core) — tenant-scoped durable state,
  knowledge, evidence, provenance, relationships, retrieval structures,
  model-output custody, and bounded execution. Core does not reason.
- [`connectors`](https://github.com/mhoo-os/connectors) — provider authorization,
  APIs, webhooks, cursors, retries, identifiers, and semantics. External
  providers remain authoritative for provider facts.
- Models and agents perform interpretation, reasoning, planning, synthesis,
  classification, recommendations, and natural-language generation.
- [`codex-lb`](https://github.com/mhoo-os/codex-lb) — model-routing and gateway
  behavior, not reasoning or business-state authority.
- [`infrastructure`](https://github.com/mhoo-os/infrastructure) — environments,
  deployment, networking, DNS, secret delivery, backups, recovery, monitoring,
  rollback, and cutover controls.

Platform coordination and cross-repository architecture live in [`mhoo`](https://github.com/mhoo-os/mhoo).

The internal control plane is a private Mhoo-owned Twenty Workspace/App. It is
not Core, a second identity system, or a second Workspace authority. The
immutable Twenty Workspace ID to Core `tenant_id` mapping is only for isolation
and correlation; it never grants authorization.

For current implementation state, follow each repository's source and evidence
links. For deployment, recovery, production, and cutover state, use the scoped
records owned by Infrastructure. A README, merged source, green CI, publication,
or rehearsal does not prove a later state.
