# AGENTS

## Purpose

This file defines the repository-wide rules and role boundaries for coding agents working in this repo.

## Source Of Truth

Start from `docs/index.md` when orienting in the repo.

Use these sources in order:

1. `docs/orchestrator/`
2. `docs/process/`
3. `docs/ai/`
4. `AGENTS.md`
5. `.github/agents/`
6. `local/` only when explicitly requested or referenced

## Repo Rules

- Focus on the orchestrator product only. Do not broaden scope into unrelated projects.
- Prefer small, reviewable changes.
- Keep architecture aligned with the coordinator plus adapters model.
- Preserve workspace isolation and explicit tracker handoff behavior.
- Avoid premature generalization for concurrency, multi-broker support, and multi-project orchestration.
- Treat Node.js plus TypeScript plus `pnpm` as the default implementation path unless the docs change.
- Put non-committed shaping outputs, scratch notes, and temporary delivery files under `local/`.
- Keep committed docs and indexes navigable for agents; see `docs/ai/repo-navigability.md`.
- Treat implementation preparation as the handoff from shaping to authoritative delivery scope; see `docs/process/implementation-preparation.md`.
- Keep `Run Coordinator` as the product component name and `Delivery Coordinator` as the agent workflow role name.

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

### Delivery Coordinator

Responsible for:

- executing one prepared implementation phase,
- keeping work inside the accepted phase boundary,
- coordinating implementer, reviewer, tester, and documenter passes,
- and returning clear evidence and remaining risks.

Should avoid:

- reshaping the plan mid-flight,
- expanding scope because a later task looks adjacent,
- confusing the agent workflow role with the product `Run Coordinator` component.

### Tester

Responsible for:

- running the defined verification commands,
- checking whether acceptance evidence exists,
- and surfacing failures or missing evidence clearly.

Should avoid:

- inventing new product direction,
- treating optional checks as blocking without reason.

### Documenter

Responsible for:

- updating committed docs affected by the phase,
- keeping indexes and navigation surfaces current,
- and promoting stable workflow knowledge out of temporary artifacts when needed.

Should avoid:

- rewriting unrelated docs,
- leaving navigational drift for later by default.

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

1. Start from the relevant index (`docs/index.md`, `docs/orchestrator/index.md`, or `docs/ai/index.md`).
2. Confirm the task is in scope for the orchestrator product.
3. Use planning and review discipline from `docs/process/`.
4. Use implementation preparation before treating candidate tasks as authoritative execution scope.
5. Decide whether planner, delivery coordinator, implementer, reviewer, tester, or documenter behavior is appropriate.
6. Make the smallest useful change that satisfies the prepared phase.
7. Update docs and indexes if behavior or repo rules changed.
8. Leave evidence through tests, artifacts, or a clear rationale.
