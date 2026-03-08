# Copilot Working Instructions

## Purpose

These instructions explain how coding agents should operate in the orchestrator repository.

## Primary Rule

Stage 1 is the active focus.

Agents should improve the orchestrator itself, its docs, tests, and repo contracts before expanding into stage 2 or stage 3 concerns.

## Source Of Truth Order

When working in this repo, prefer sources in this order:

1. `docs/orchestrator/`
2. `docs/ai/`
3. `AGENTS.md`
4. `.github/agents/`
5. `local/` working notes only when explicitly referenced

## Working Posture

- Prefer the smallest change that moves the stage 1 product forward.
- Preserve explicit adapter boundaries.
- Do not reintroduce Symphony complexity without a concrete need.
- Mark provisional decisions honestly instead of pretending certainty.
- Keep documentation and implementation in sync.

## Stage 1 Bias

Good tasks:

- config and CLI design
- tracker integration
- workspace isolation
- broker integration
- artifacts and summaries
- tests and smoke tests
- repo instructions and agent roles

Bad tasks for now:

- Godot runtime automation
- distributed orchestration
- speculative multi-broker frameworks
- broad UI work
- abstract concurrency systems

## Design Rules

- Preserve issue-driven orchestration.
- Preserve isolated per-issue workspaces.
- Prefer CLI-first implementation in v0.
- Treat Node.js plus TypeScript plus `pnpm` as the default path unless a reviewed decision changes it.
- Keep tracker semantics configurable instead of hardcoding one Linear workflow forever.

## Documentation Rules

When a change affects product behavior, update the relevant doc in `docs/orchestrator/`.

When a change affects agent behavior, update `docs/ai/`, `AGENTS.md`, or `.github/agents/` as needed.

## Output Expectation

Agent work should leave behind clear evidence:

- code changes,
- tests,
- doc updates,
- or explicit rationale for why a doc-only change was correct.
