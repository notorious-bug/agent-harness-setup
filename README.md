# Repository agent harness

This repository is a starter for adding the agent-harness practices used by the OraFisco repository to another Git project. It provides a shared operating contract, thin agent entrypoints, a durable execution-plan format, and a pull-request evidence template. Adapt the starter to the target project's real architecture, risks, tools, and CI before relying on it.

## Set up a target repository

1. **Inspect the target first.** Check its working tree, existing agent instructions, CI, branch protections, security rules, and source-of-truth documents. Preserve local changes and merge useful existing policy instead of replacing it blindly.
2. **Copy the starter files.** Copy `AGENTS.md`, `CLAUDE.md`, `docs/AGENT_GUIDE.md`, `docs/exec-plans/`, and `.github/pull_request_template.md` into the target repository, preserving their paths. Do not copy this repository's `.git` directory. Keep only entrypoints for agent tools the team uses.
3. **Map the real sources of truth.** In `docs/AGENT_GUIDE.md`, replace every `TODO` and placeholder. Link the actual architecture/product contract, delivery plan, security and reliability policy, and component guides. Add a component guide only when a directory has its own rules or verification commands.
4. **Set the operating contract.** Keep `docs/AGENT_GUIDE.md` as the single vendor-neutral policy for people and agents. Fill in its owner and review dates. Define repository-specific safety boundaries, when durable plans are required, how decisions are recorded, exact validation commands, evidence expectations, and the completion standard. Documentation must agree with executable behavior; fix the source and enforcement together when they drift.
5. **Keep tool adapters thin.** Make `AGENTS.md` and `CLAUDE.md` route to the shared guide. Add only tool-specific setup and links there. Remove unused adapters. Keep agent roles optional and focused on real independent expertise; do not require delegation for every task.
6. **Add durable planning paths.** Create `docs/exec-plans/active/` and `docs/exec-plans/completed/`. Use `docs/exec-plans/PLAN.template.md` for cross-component, security-sensitive, migration, or otherwise complex work. Record the final outcome and verification before moving a plan to `completed/`.
7. **Set evidence and review rules.** Adapt `.github/pull_request_template.md` to require the task/problem, observable behavior before and after, implementation impact, exact check results, and relevant security/compatibility/recovery concerns. Store only small, sanitized evidence in the target project's chosen evidence directory. Require human review; agent authors must not approve or merge their own changes.
8. **Enforce policy in CI.** Add a harness check using tools already present in the target repo. Make CI run the same documented checks. Good drift checks include entrypoint routing, internal links, active-plan ownership/review dates, evidence size and secret scans, and required PR sections when the hosting platform exposes that data. Keep project builds and security tests in their owning CI jobs.
9. **Verify adoption.** Search for remaining `TODO`/placeholder text, resolve links, run every documented harness and component command, and confirm CI protects the same requirements. Report any missing dependency or platform as unverified; do not claim a check passed if it did not run.

## Suggested target layout

```text
AGENTS.md                         Codex and general agent entrypoint
CLAUDE.md                         Claude Code adapter (optional)
docs/AGENT_GUIDE.md               Shared operating contract
docs/exec-plans/README.md         Plan lifecycle
docs/exec-plans/PLAN.template.md  Durable plan structure
docs/exec-plans/active/           Current complex work
docs/exec-plans/completed/        Completed plans
.github/pull_request_template.md Evidence and review contract
```

Add `docs/evidence/`, issue templates, role definitions, or component guides only when they solve a need in the target project. Keep secrets, personal data, and raw production material out of Git and evidence files. Preserve the target repo's CI, required reviews, and branch protections as the authoritative gates.

## What is intentionally project-specific

The OraFisco repo also has PostgreSQL/RLS rules, Rust and Flutter checks, specialist role catalogs, Symphony automation, ECC integration, and GitHub-specific issue workflows. They are not part of this starter; adopt them only if the target project's architecture and risk profile call for them.
