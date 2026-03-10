# Coordination Workflow

## Purpose

This document defines the linear idea-to-delivery workflow for work done in this repo.

It describes how a high-level artifact becomes repo-native specs, plans, implementation phases, review evidence, and documentation updates.

This is an agent workflow for building the orchestrator.
It is not the runtime tracker workflow implemented by the orchestrator product itself.

## Workflow Summary

Use this sequence for meaningful feature work:

1. external brief,
2. in-repo shaping,
3. plan review,
4. implementation preparation,
5. delivery phase execution,
6. documentation pass,
7. post-session audit.

The workflow is linear end to end, but each step produces a different artifact and uses different review rules.

## Step 1: External Brief

The initial brief may be produced outside this repo.

Examples:

- GPT web shaping notes,
- source specs,
- operator-authored product notes,
- comparative research.

That artifact is input, not source of truth.

Store temporary copies under `local/` when needed.

## Step 2: In-Repo Shaping

The planner turns the brief into repo-native shaping outputs.

Required outputs:

- spec changes or confirmations in committed docs,
- a plan that follows `docs/process/planning-contract.md`,
- source classification for major choices,
- and a defined first safe slice.

At this stage, task lists are still candidate tasks only (see `docs/process/planning-contract.md`).

## Step 3: Plan Review

Review the changed spec and plan using `docs/process/review-severity.md`.

Possible outcomes:

- accepted as-is,
- accepted with bounded amendments,
- returned for reshaping,
- escalated because a locked decision was disturbed.

Do not skip this review by treating the planner output as automatically ready.

## Step 4: Implementation Preparation

Implementation preparation converts the accepted plan into authoritative execution inputs.

Required outputs:

- a phase plan,
- the current phase objective,
- authoritative task scope for that phase,
- acceptance criteria,
- evidence requirements,
- expected files or modules touched,
- validation commands,
- and documentation-update expectations.

This is the step where candidate tasks become authoritative (see `docs/process/implementation-preparation.md`).

## Step 5: Delivery Phase Execution

One delivery phase should be executable in one bounded Copilot request.

The preferred operative role is `Delivery Coordinator`.

The delivery coordinator should:

1. read the accepted spec and phase plan,
2. launch an implementer for the bounded change,
3. launch a reviewer to inspect the result,
4. launch a tester when meaningful validation exists,
5. loop implementer and reviewer as needed within the phase boundary,
6. launch a documenter before closing the phase,
7. return a concise phase report with evidence and remaining risks.

This loop should stay phase-bounded.
If the phase must be re-scoped, return to implementation preparation instead of improvising a new plan mid-flight.

## Step 6: Documentation Pass

The documenter is responsible for checking whether the phase changed:

- product behavior,
- planning discipline,
- agent workflow,
- role expectations,
- or the relevant navigation indexes.

The default expectation is that every meaningful phase at least checks documentation impact explicitly.

## Step 7: Post-Session Audit

After a delivery session completes, a separate high-level audit may run.

Purpose:

- detect spec drift,
- catch architectural shortcuts,
- identify missing follow-up planning,
- and decide whether a new shaping or delivery cycle is required.

This audit is intentionally separate from the phase execution loop.

## Tracker Guidance For Human Workflow

If a tracker is used to manage this repo's own work, prefer a small linear flow:

- `Inbox`
- `Shaping`
- `Plan Review`
- `Ready for Delivery`
- `In Delivery`
- `Human Review`
- `Done`
- `Blocked` when truly needed

Do not create a column for every possible loop.
Revision usually means moving back to the previous meaningful state.

## Naming Rule

In this repo, `Run Coordinator` refers to the orchestrator product component.

`Delivery Coordinator` refers to the agent role that executes one implementation phase against a spec and plan.

Keep those names separate to avoid architectural confusion.

## Scope Boundary

This repository covers the orchestrator product only.

Allowed forward-looking references:

- keeping adapter boundaries reusable,
- avoiding obvious OS lock-in,
- preserving room for future broker growth,
- noting that the Godot harness will be a separate repo.

Not allowed as current scope:

- designing the Godot harness runtime protocol,
- designing game systems,
- broadening v0 to solve concerns from other projects,
- mixing game feature planning into core orchestrator implementation tasks.

Practical rule: if a proposal does not make the first issue loop better, safer, or easier to reach, it probably does not belong in active scope.

## Current Boundary

This workflow defines how this repo should be shaped and implemented.

It does not yet define the full future multi-model or multi-broker operating system for other repos.
That future work belongs in `docs/ai/dev-workflow-roadmap.md` unless it must affect the orchestrator now.
