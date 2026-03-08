# AGENTS

## Purpose

This file defines the repository-wide rules and role boundaries for coding agents working in this repo.

## Source Of Truth

Use these sources in order:

1. `docs/orchestrator/`
2. `docs/process/`
3. `docs/ai/`
4. `AGENTS.md`
5. `.github/agents/`
6. `local/` only when explicitly requested or referenced

## Repo Rules

- Focus on stage 1 only.
- Do not implement stage 2 or stage 3 systems here.
- Prefer small, reviewable changes.
- Keep architecture aligned with the coordinator plus adapters model.
- Preserve workspace isolation and explicit tracker handoff behavior.
- Avoid premature generalization for concurrency, multi-broker support, and multi-project orchestration.
- Treat Node.js plus TypeScript plus `pnpm` as the default implementation path unless the docs change.
- Put non-committed shaping outputs, scratch notes, and temporary delivery files under `local/`.

## Role Definitions

### Planner

Responsible for:

- task shaping,
- dependency mapping,
- spec alignment,
- implementation breakdown.

Planner outputs should follow `docs/process/planning-contract.md`.
Open questions should use the blocker taxonomy in `docs/process/decision-taxonomy.md`.

Should avoid:

- speculative redesign,
- broad code changes.

### Implementer

Responsible for:

- making bounded code and doc changes,
- updating tests,
- following the spec set.

Should avoid:

- silently changing product direction,
- skipping docs when behavior changes.

### Reviewer

Responsible for:

- finding bugs,
- finding regressions,
- finding spec drift,
- identifying missing tests and evidence.

Should avoid:

- rewriting code during review unless explicitly asked,
- burying findings behind long summaries.

When reviewing a plan, reviewers should use the severity labels in `docs/process/review-severity.md`.

## Default Working Pattern

1. Read the relevant spec docs.
2. Confirm the task is in stage 1 scope.
3. Decide whether planner, implementer, or reviewer behavior is appropriate.
4. Make the smallest useful change.
5. Update docs if behavior or repo rules changed.
6. Leave evidence through tests, artifacts, or a clear rationale.
