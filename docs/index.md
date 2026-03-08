# Docs Index

This repo uses a split documentation model:

- `docs/orchestrator/` is the stage 1 source of truth for the orchestrator product.
- `docs/ai/` explains how coding agents should work in this repo.
- `AGENTS.md` and `.github/agents/` are the executable repo rules and role definitions for Copilot.
- `local/` is intentionally non-committed scratch space for shaping outputs, temporary notes, and review artifacts.

## How To Read This Set

If you are new to the repo, read these in order:

1. `docs/orchestrator/product-overview.md`
2. `docs/orchestrator/scope-v0.md`
3. `docs/orchestrator/architecture.md`
4. `docs/orchestrator/run-lifecycle-v0.md`
5. `docs/orchestrator/decision-log.md`
6. `docs/orchestrator/roadmap.md`
7. `docs/orchestrator/implementation-tasks.md`
8. `docs/ai/copilot-working-instructions.md`
9. `AGENTS.md`

## Reading Rules

- Treat `docs/orchestrator/` as the stable spec for stage 1 unless a doc marks a section as provisional.
- Treat `docs/ai/` and `.github/` files as implementation guidance for coding agents working from that spec.
- Treat `local/` files as non-authoritative working outputs unless they are promoted into `docs/`.

## Stage Boundary

This doc set is intentionally narrow.

- Stage 1: covered here.
- Stage 2 and stage 3: referenced only where they affect stage 1 decisions.
- No runtime Godot harness design is specified here beyond boundary notes.
