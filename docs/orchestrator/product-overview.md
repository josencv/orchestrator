# Product Overview

## Product Statement

The orchestrator is a local issue-driven agent runner.

Its job is to take one eligible tracker issue, prepare an isolated working directory, invoke a coding-agent broker, capture evidence, update the tracker, and hand the result to a human reviewer.

## Scope

This repository defines the orchestrator product.

It does not define:

- the Godot AI harness implementation,
- the game architecture,
- distributed orchestration,
- a hosted service.

## Core Goals

- Make issue execution repeatable instead of ad hoc.
- Keep agent work isolated per issue.
- Keep workflow policy repo-owned and reviewable.
- Preserve enough logs and artifacts to understand what happened.
- Reach a practical first working loop quickly.
- Leave room for future self-development of the orchestrator.

## Explicit Non-Goals

- Building a multi-tenant platform.
- Solving multi-worker scheduling in v0.
- Designing full cross-platform support before one platform works.
- Supporting multiple trackers or brokers in v0.
- Encoding runtime automation from other projects into the orchestrator.

## Intended Users

- The repo owner operating the orchestrator locally.
- Future coding agents working on the orchestrator repo itself.
- Later project repos that want to adopt the same workflow shape.

## Implementation Stance

Node.js plus TypeScript with `pnpm` is the current recommended stack.

This is a strong recommendation, not an irrevocably frozen decision. It is preferred because it fits CLI tooling, typed adapter boundaries, process management, and future portability, but it may still be revised before implementation begins if a materially better option appears.

## Key Product Characteristics

- local-first
- CLI-first in v0
- deterministic enough to supervise
- adapter-aware without forcing broad abstractions too early
- designed to become a daemon later
- reusable beyond this single repo, but not generalized prematurely

## Decision Classification Snapshot

- `Inherited from Symphony`: issue-driven orchestration, isolated per-issue workspaces, repo-owned workflow policy, structured artifacts.
- `Adapted from Symphony`: simplify the runner around a broker subprocess instead of adopting Symphony's full app-server session model in v0.
- `New for this project`: CLI-first v0, Copilot CLI as first broker, and explicit self-development expectations for the orchestrator repo.
