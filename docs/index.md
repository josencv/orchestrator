# Docs Index

This repo uses a split documentation model:

- `docs/orchestrator/` is the stage 1 source of truth for the orchestrator product.
- `docs/process/` defines how feature planning and planning review should work in this repo.
- `docs/ai/` is a human-facing guide to repo AI workflows and operative Copilot files.
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
10. `docs/ai/index.md`
11. `AGENTS.md`

## Reading Rules

- Treat `docs/orchestrator/` as the stable spec for stage 1 unless a doc marks a section as provisional.
- Treat `docs/process/` as the planning-process source of truth for shaping and reviewing feature plans.
- Treat `docs/ai/` and `.github/` files as guidance for humans and coding agents working from that spec and process.
- Treat `local/` files as non-authoritative working outputs unless they are promoted into `docs/`.

## Stage Boundary

This doc set is intentionally narrow.

- Stage 1: covered here.
- Stage 2 and stage 3: referenced only where they affect stage 1 decisions.
- No runtime Godot harness design is specified here beyond boundary notes.
