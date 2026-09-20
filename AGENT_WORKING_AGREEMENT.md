# Agent working agreement

This is the shared baseline for AI-assisted work in Mhoo repositories. A
repository's own `AGENTS.md`, accepted issue or mission, and applicable security
policy add the concrete instructions for that repository.

## Work from bounded authority

- Treat the accepted issue or revisioned mission as scope. Do not turn a useful
  follow-up into an implicit new assignment.
- Inspect the repository's existing source, documentation, and primitives before
  proposing another service or framework.
- Preserve repository ownership boundaries. A task, model choice, branch name,
  passing check, or final agent message does not grant additional authority.
- Stop for explicit authorization before merge, deployment, credentials, DNS,
  restart, destructive cleanup, customer-data access, or production mutation.

## Produce reviewable evidence

- Bind claims to an exact repository, base, head, command or observation, result,
  and evidence location. Keep unknown or stale state explicit.
- Reuse matching evidence. Re-run checks only when changed inputs, missing proof,
  or an explicit freshness requirement justify it.
- Separate implementation, validation, publication, deployment, and production
  acceptance. Evidence for one state does not prove the next.
- Preserve failures and rejected attempts. Never rewrite them into success.

## Keep review independent

- The implementation author may prepare evidence but may not independently
  accept its own result.
- Use deterministic code for exact facts. Typed classifiers may route bounded
  work, but they do not grant authority or establish acceptance.
- Review the source result and, when relevant, the execution trajectory. Route
  defects back to the implementation owner and re-run only affected checks.
- Human authorization remains required for merge and operational changes unless
  a narrower, explicit policy says otherwise.

## Finish clearly

Report the exact head, changed files, checks run or reused, independent review
state, unresolved risks, and smallest next action. State separately whether the
change is committed, pushed, under review, merged, published, or deployed.
