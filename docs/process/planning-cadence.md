# Planning Cadence

## Purpose

This document defines the default cadence for planning work in this repo.

It explains how a feature moves from early shaping into implementation preparation without mixing all planning work into one giant artifact.

## Default Cadence

Use this sequence unless a feature needs something stricter:

1. explore or reshape the problem,
2. lock only the decisions that are expensive to revisit,
3. shape or amend the repo-native spec,
4. review the diff with severity labels,
5. prepare issue-ready work,
6. implement one slice,
7. learn from implementation and update only the affected docs.

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

## Repo Rule

Candidate tasks produced during shaping are not yet authoritative issue plans.
They become authoritative only after implementation preparation.

## Boundary Rule

This cadence is about planning any feature in this repo.
It is not the same thing as the orchestrator runtime workflow for operating on tracker issues.

## Reserved Future Work

A fuller development workflow for operating the orchestrator on itself may be added later.
That work should extend this cadence, not replace it.
See `docs/ai/dev-workflow-roadmap.md` for the reserved placeholder.
