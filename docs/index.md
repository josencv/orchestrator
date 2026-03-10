# Docs Index

This repo uses a split documentation model:

- `docs/orchestrator/` is the product source of truth for the orchestrator.
- `docs/process/` defines how feature planning and planning review should work in this repo.
- `docs/ai/` is a human-facing guide to repo AI workflows, navigability rules, and the shaping-to-delivery process.
- `AGENTS.md` and `.github/agents/` are the executable repo rules and role definitions for Copilot.
- `local/` is intentionally non-committed scratch space for shaping outputs, temporary notes, and review artifacts.

## How To Read This Set

If you are new to the repo, read these in order:

1. `docs/orchestrator/product-overview.md`
2. `docs/orchestrator/scope-v0.md`
3. `docs/orchestrator/architecture.md`
4. `docs/orchestrator/run-lifecycle-v0.md`
5. `docs/orchestrator/decision-log.md`
6. `docs/process/planning-contract.md`
7. `docs/process/decision-taxonomy.md`
8. `docs/process/review-severity.md`
9. `docs/process/planning-cadence.md`
10. `docs/process/implementation-preparation.md`
11. `docs/ai/index.md`
12. `docs/ai/repo-navigability.md`
13. `docs/ai/coordination-workflow.md`
14. `AGENTS.md`

## Reading Rules

- Treat `docs/orchestrator/` as the stable product spec unless a doc marks a section as provisional.
- Treat `docs/process/` as the planning-process source of truth for shaping and reviewing feature plans.
- Treat `docs/ai/` and `.github/` files as guidance for humans and coding agents working from that spec and process.
- Treat `local/` files as non-authoritative working outputs unless they are promoted into `docs/`.

## Scope

This doc set covers the orchestrator product only.
It does not define unrelated projects, game systems, or hosted services.
