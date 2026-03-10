# Planning Contract

## Purpose

This document defines how feature planning should work inside this repo.

It is operational. Humans and agents should use it directly when preparing or reviewing a feature plan.

## Planning Standard

A feature plan is good enough when:

- the next implementation slice is clear,
- the relevant spec sections are identified,
- major decisions are status-tagged,
- unresolved questions are visible,
- blockers are real blockers,
- and the first implementation issue can be executed without reopening the whole design.

## Planning Posture

Optimize for stable direction, not frozen detail.

Lock expensive decisions.
Keep cheap decisions explicit, bounded, and revisable.
Do not turn ordinary uncertainty into a reason to stop.

## Required Inputs For A Planner

A planner should be given, at minimum:

1. the relevant repo specs in `docs/orchestrator/`,
2. the repo decision register in `docs/orchestrator/decision-log.md`,
3. any relevant reference or source spec,
4. the feature request, issue, or change prompt,
5. any operator-owned choices that are already decided.

If a required operator-owned choice is still open, the plan must mark it explicitly.

## Required Sections In Every Plan

Every feature plan should include these sections.

### 1. Objective

What is being planned and why.

### 2. Relevant Source Docs

List the committed repo docs and external or reference docs that shaped the plan.

### 3. Decision Table

For each major decision, classify it using `docs/process/decision-taxonomy.md`.

### 4. Source Classification

For each major architectural or workflow choice, classify it as inherited, adapted, or new.

### 5. First Safe Slice

Define the smallest end-to-end slice that should be implemented first.

### 6. Out Of Scope

List what the plan explicitly does not include.

### 7. Candidate Work Breakdown

Break the feature into bounded implementation units.

Candidate tasks are not authoritative issue plans yet.
They become authoritative only during implementation preparation.

### 8. Blockers And Pending Choices

Classify open items using the blocker taxonomy in `docs/process/decision-taxonomy.md`.
Do not list everything under a generic blocker heading.

### 9. Acceptance Evidence

Describe what evidence should exist when the first safe slice is complete.

## First Safe Slice Rule

Every shaped spec must define the first safe slice:

- the smallest end-to-end implementation slice that proves the chosen direction,
- what must exist for that slice,
- what is explicitly out of scope,
- and what evidence shows the slice works.

If a spec cannot define a first safe slice, it is still too abstract.

## Planning Rules

### Rule 1

Do not reopen locked decisions casually.

### Rule 2

Do not move future concerns into v0 without explicit justification.

### Rule 3

Do not over-sequence work before the first safe slice is proven.

### Rule 4

Do not turn operator preferences into fake architecture questions.

### Rule 5

Prefer small navigable docs and bounded work units over a giant manifesto.

## Implementation Preparation

Once a plan is accepted, the next step is implementation preparation.

See `docs/process/implementation-preparation.md` for the authoritative output contract.

## Update Rule

Update this document only when the repo planning discipline changes materially.

Do not edit it for feature-specific preferences.
Those belong in the feature plan or decision register.
