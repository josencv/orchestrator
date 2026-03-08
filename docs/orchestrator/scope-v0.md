# V0 Scope

## V0 Goal

Reach one trustworthy end-to-end loop:

- select one eligible Linear issue,
- claim it,
- create or reuse its isolated workspace,
- invoke Copilot CLI with repo-owned instructions,
- capture artifacts,
- run optional validation commands,
- comment results back to the issue,
- move the issue to a human-review state.

## In Scope

- One target project at a time.
- One worker only.
- One tracker adapter: Linear.
- One broker adapter: Copilot CLI.
- Deterministic local workspace mapping per issue.
- Structured run artifacts on disk.
- Explicit tracker claim and handoff transitions.
- CLI operation, including a run-once path.
- Enough config to operate one project safely.

## Explicit Non-Goals

- Multi-worker concurrency.
- Multi-project orchestration in a single process.
- Multiple broker implementations.
- Full daemon lifecycle management.
- Broker-agnostic protocol layers broader than needed for one adapter boundary.
- Built-in PR automation.
- Automatic merge or deployment behavior.
- Godot runtime control.
- Strongly abstracted lease systems.
- Cross-platform parity beyond avoiding obvious lock-in.

## Success Criteria

A human should be able to point the orchestrator at one target repo and observe a complete run that leaves behind:

- a claimed issue history,
- an isolated working directory,
- broker output logs,
- a run manifest,
- optional validation results,
- a tracker comment summarizing outcome,
- a final issue handoff to human review.

## Why This Scope

This scope preserves the highest-value parts of Symphony while stripping away features that would delay the first useful result.

The v0 question is:

Can one local process turn one issue into one bounded, inspectable agent run?

If the answer is yes, later phases can expand from a real foundation instead of a speculative architecture.
