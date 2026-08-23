# Mhoo Maintainer v0

Mhoo Maintainer is a GitHub-native, organization-level custom agent for
engineering-health review. It is not a deployment system, organization
administrator, autonomous merge bot, custom GitHub App, service, database,
queue, MCP server, or cross-repository platform.

Its operating model is **detect -> report -> recommend -> optionally open one
reviewable repository-local PR**. It never merges its own work.

## Organization configuration

GitHub's supported organization-level custom-agent location is
`/agents/<agent>.md` in this special `.github` repository. The profile is
[`/agents/mhoo-maintainer.md`](../agents/mhoo-maintainer.md).

GitHub organization custom instructions and automatic Copilot review are
settings, not repository YAML. An organization owner must make the settings
changes described below; this repository does not pretend to enable them.

### Current platform blocker

On 2026-08-24, the `mhoo-os` organization settings displayed: **"New Copilot
Business signups are currently paused for organizations on the Free or Team
plans."** The organization Copilot settings route redirected to General
Settings, with no custom-instruction, custom-agent, or automatic-review control
available. The agent profile and health workflow remain valid source
configuration, but Copilot activation is blocked until GitHub makes an eligible
Copilot organization plan/settings surface available.

### Organization custom instructions

In **Organization settings -> Copilot -> Custom instructions**, add the
following compact instruction set:

```text
Inspect the repository's AGENTS.md and applicable path instructions before
changing or reviewing code. Prefer the smallest correct, evidence-backed change.
Do not introduce secrets, weaken CI or governance, silently deploy, or assume
production, administrative, or authority permission. Respect repository
ownership and document material contract changes. Treat source, CI, runtime,
persisted data, and production readiness as distinct claims. Flag material
security, provenance, architecture, and authority risks; do not create style
noise. Repository-local contracts remain authoritative for detailed rules.
```

This instruction is intentionally organization-wide only. It must not replace
repository contracts.

### Automatic Copilot review

An organization owner should use GitHub's **Organization settings -> Copilot ->
Code review** controls to enable automatic Copilot review for this organization,
then exclude any repository only when its local contract or upstream policy
requires it. This cannot be enabled by a workflow or agent profile.

Copilot review is advisory. It is not a human approval, cannot satisfy an
independent-review requirement, and must not be used to self-approve policy
changes made by the Maintainer.

## Instruction hierarchy

1. GitHub organization custom instructions supply the small shared baseline.
2. The Mhoo Maintainer profile supplies the reviewer role and its safety limit.
3. A repository's root `AGENTS.md`, `.github/copilot-instructions.md`, and
   `.github/instructions/*.instructions.md` supply repository and path-specific
   rules. The most specific applicable local contract governs.
4. Current source, accepted repository-owned decisions, current CI, and scoped
   operational evidence establish what is actually true.

Do not copy these organization rules into every repository. Add path-specific
instructions only when an actual path has a durable, different contract.

## Repository role map and audit snapshot

Audit date: 2026-08-24. The organization has seven active public repositories;
no archived repository was included. Current open PRs and branches are evidence
for review, not a reason to delete or close work automatically.

| Repository | Role and authority | Local instruction / automation state | Maintainer treatment |
| --- | --- | --- | --- |
| `.github` | Organization profile, shared health files, and Maintainer configuration | No local `AGENTS.md`, Copilot instructions, or Actions before this change | Organization-wide agent and health report belong here; policy changes require human review. |
| `mhoo` | Cross-repository architecture, decisions, and roadmap | `AGENTS.md` is proposed in open PR #8; active solo-maintainer policy issue #9; PR template exists; no workflow or Dependabot configuration | Treat accepted ADRs and ownership records as cross-repository constraints, not operational proof. |
| `core` | Future Mhoo business-state/services foundation | `AGENTS.md` is proposed in PR #5; Phase 0D work is PR #6; no workflow or Dependabot configuration | Preserve tenant/isolation proof boundaries; do not claim production authority. |
| `mhoo-twenty` | Forked Twenty workspace source | Upstream: `twentyhq/twenty`; root contract is proposed in PR #13 and a provenance overlay in PR #14; extensive upstream CI and constrained Dependabot configuration | Preserve upstream provenance and local fork governance. Do not enable upstream automation or Twenty upgrades by default. |
| `infrastructure` | Deployment, environment, recovery, security, and cutover definitions | `AGENTS.md` is proposed in PR #22; PR template exists; no workflow or Dependabot configuration | Source change, validation, candidate deployment, production mutation, and cutover remain separate permissions. |
| `connectors` | Future provider adapter boundary | `AGENTS.md` is proposed in PR #2; PR template exists; no workflow or Dependabot configuration | Provider facts stay provider-authoritative; no credentials or provider effects without explicit approval. |
| `codex-lb` | Forked model/provider-routing component | Root `AGENTS.md`, CI, stale workflow, and Dependabot configuration exist; upstream: `Soju06/codex-lb`; open contract PR #2 | Follow its OpenSpec and merge-gate contract; do not treat routing source as infrastructure or production-network authority. |

Six repositories had no open issues at audit time. `mhoo` issue #9 records the
temporary solo-maintainer review policy. `mhoo-twenty` had the only observed
main-branch GitHub Actions activity; its latest successful and skipped runs are
not proof that the other repositories' absent workflows are broken. The
Maintainer should report that state as unclassified rather than inventing a
uniform CI requirement.

Only `mhoo-twenty` had a protected `main` branch at audit time: one required PR
approval, required latest-push approval, required current branch, required
conversations resolved, admin enforcement, and force-push/deletion disabled. No
other repository had a branch-protection response. Issue #9 says the temporary
policy had set the approval count to zero and disabled latest-push approval,
which conflicts with the current protection API. Treat the current API as the
effective state and reconcile the issue before using it as governance evidence.
This v0 change does not alter protections.

Dependabot version-update configuration exists in `mhoo-twenty` and `codex-lb`.
Automated Dependabot security updates and secret-scanning push protection were
reported disabled across the organization snapshot. These are settings-level
findings to review deliberately, not changes made by this agent.

## Health workflow

[`/workflows/mhoo-maintainer-health.yml`](../workflows/mhoo-maintainer-health.yml)
runs manually or each Monday at 03:17 UTC. It uses only `contents: read` and
the workflow token to list visible, active repositories and summarize open PRs,
issues, branch candidates, and the latest GitHub Actions result.

It writes only the GitHub Actions job summary. It opens no issue or PR, changes
no repository, performs no deployment, and has no administration, secret,
package, or write permission. It deliberately does not infer flaky CI, stale
branch ownership, dependency safety, or documentation drift from a shallow API
snapshot.

The standard read-only workflow is used instead of an Agentic Workflow because
v0 needs a deterministic, organization-wide report and no agent runtime is
needed to produce it. Use the custom agent for the repository-aware follow-up.

## Review and approval policy

The Maintainer distinguishes **BLOCKER**, **IMPORTANT**, and **NOTE** findings
and otherwise leaves no review comment. It must read local instructions before
reviewing a PR and must explicitly request human review for its own profile,
organization instructions, `AGENTS.md`, governance, CI, provenance, branch
policy, or security-policy edits.

During the solo-maintainer phase, the recommended target is a required PR,
stable required CI, up-to-date branches, resolved conversations, disabled
force-push and deletion, and admin enforcement. Do not create a fake second
identity merely to require a second approval. Once there is an independent human
maintainer, require their approval for protected branches. Repositories with
stronger existing rules must retain them.

## Deferred v0 capabilities

- Automatic or autonomous merges, policy/ruleset changes, repository deletion,
  deployments, DNS/network changes, database mutation, credential rotation, and
  Twenty upgrades.
- Blind major-version upgrades or cross-repository dependency campaigns.
- Cross-repository write tokens, custom GitHub Apps, external services,
  databases, queues, webhooks, MCP servers, and external control planes.
- Automatic stale-branch/PR closure and any claim that a Copilot review equals
  human approval.
