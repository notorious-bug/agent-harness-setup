# Shared Agent Guide

Status: draft
Owner: TODO
Last reviewed: YYYY-MM-DD
Review by: YYYY-MM-DD

This is the vendor-neutral operating contract for humans and coding agents. Agent-specific
entrypoints route here and must not duplicate or weaken these rules.

## Repository map and sources of truth

| Area | Source of truth |
|---|---|
| Architecture and product behavior | `TODO` |
| Delivery state | `TODO` |
| Security and privacy | `TODO` |
| Reliability and operations | `TODO` |
| Component behavior and verification | `TODO` |

When documentation conflicts with executable behavior, stop and record the discrepancy. Fix the
source of truth and its enforcement in the same change; do not silently choose the easier version.

## Safety boundaries

- Preserve user changes. Inspect `git status` before editing and do not revert unrelated work.
- Never commit credentials, private keys, personal data, or unfiltered production data/logs.
- Validate external input at trust boundaries and preserve data during migrations or recovery.
- Keep CI, required review, and branch protections authoritative; agents must not waive or weaken
  them.
- Add project-specific security and data-loss invariants here.

## Planning and decisions

- Small, local changes may use an ephemeral plan in the agent session.
- Complex, cross-component, security-sensitive, or migration work requires a durable plan under
  `docs/exec-plans/active/`, following `docs/exec-plans/PLAN.template.md`.
- Record durable decisions in the repository. Conversation history is not a source of truth.
- Use specialist agents only when work is independent or benefits from isolated expertise; the
  coordinating agent remains accountable for integration and validation.

## Validation by component

Run the narrowest useful checks during development and all applicable checks before handoff.

| Change | Required checks |
|---|---|
| Repository policy and docs | `TODO` |
| Component A | `TODO` |
| Component B | `TODO` |

If a dependency or environment is unavailable, report the exact missing prerequisite. Do not
describe an unrun check as passed.

## Pull-request evidence

Every implementation change must state the problem, observable behavior before and after, exact
validation commands and results, and relevant security, compatibility, migration, and rollback
considerations. Store small, sanitized proof under `TODO: evidence directory` when the change's
risk calls for it. Never include secrets, personal data, or raw production material. Human review
is required.

## Completion standard

A task is complete when behavior, tests, documentation, evidence, and review findings agree.
Report changed files, checks and results, known limitations, and follow-up work.
