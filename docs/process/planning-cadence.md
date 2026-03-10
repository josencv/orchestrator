# Planning Cadence

## Purpose

This document defines the default cadence for planning work in this repo.

It explains how a feature moves from early shaping into implementation preparation as part of one linear repo workflow without mixing all work into one giant artifact.

## Default Cadence

Use this sequence unless a feature needs something stricter:

1. capture or import the initial brief,
2. explore or reshape the problem,
3. lock only the decisions that are expensive to revisit,
4. shape or amend the repo-native spec,
5. review the diff with severity labels,
6. prepare authoritative phase-ready work,
7. execute one delivery phase,
8. update the affected docs and indexes,
9. run any needed post-session audit.

## Phase Meanings

### Exploration

Human-led and open-ended.
Capture the problem, goals, non-goals, constraints, and candidate directions.

### Decision Locking

Human-led and narrowing.
Freeze the risky choices and the boundaries of the solution space.
Do not freeze every detail.

### Spec Shaping

Agent-assisted and artifact-driven.
Turn the accepted direction into small repo-native docs and identify the first safe slice.

### Refinement Review

Mixed human and agent review.
Review changed sections, not the entire world again.
Tag comments with the review severity labels in `docs/process/review-severity.md`.

### Implementation Preparation

Structured and execution-oriented.
Convert candidate work into issue-ready tasks with dependencies, acceptance criteria, evidence, and designated roles.

### Delivery Phase Execution

Bounded and artifact-driven.
Execute one prepared phase against the accepted spec and implementation-preparation output.

### Documentation And Audit

Close the phase by updating affected committed docs and running any separate high-level audit that the operator wants.

## Repo Rule

Candidate tasks are not yet authoritative until implementation preparation.
See `docs/process/planning-contract.md` and `docs/process/implementation-preparation.md` for the authoritative definitions.

## Boundary Rule

This cadence is about planning any feature in this repo.
It connects into delivery preparation, but it is not the same thing as the orchestrator runtime workflow for operating on tracker issues.

## Reserved Future Work

A fuller development workflow for operating the orchestrator on itself may be added later.
That work should extend this cadence, not replace it.
See `docs/ai/coordination-workflow.md` for the current repo workflow and `docs/ai/dev-workflow-roadmap.md` for reserved future expansion.
