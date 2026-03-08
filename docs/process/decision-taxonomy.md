# Decision Taxonomy

## Purpose

This document defines the shared status labels used in planning and planning review.

Use these labels in plans, refinement reviews, and implementation-preparation inputs.
Do not redefine them inside feature-specific docs.

## Decision Status

Every meaningful planning decision should be classified as one of:

- `Locked`: expensive to change; do not reopen casually.
- `Preferred`: currently favored; can change with bounded cost.
- `Provisional`: chosen for v0 momentum; expected to be revisited if implementation teaches something.
- `Deferred`: explicitly not decided yet.

## Blocker Taxonomy

A question is a `True blocker` only if implementation cannot begin safely without it.

Otherwise classify it as one of:

- `Operator-owned choice`: a human preference or direction choice that should be answered before shaping or before a specific implementation slice.
- `Provisional choice`: safe to choose now and revise later.
- `Delegated implementation decision`: can be decided by the implementer inside documented constraints.
- `Deferred choice`: belongs to a later phase and must not block v0.

Do not inflate ordinary pending decisions into blockers.

## Source Classification

For each major architectural or workflow choice, classify it as one of:

- `Inherited`: preserved directly from a reference or source spec.
- `Adapted`: carried forward from a reference or source spec, but intentionally reshaped for this repo.
- `New`: introduced for this repo.

Any significant deviation from a source spec should include a reason.

## How To Use These Labels

Use decision status in:

- feature plans,
- repo decision registers,
- refinement reports,
- implementation-preparation outputs when a choice is still open.

Use blocker taxonomy in:

- plan review,
- open-question lists,
- implementation-readiness checks.

Use source classification in:

- spec shaping,
- architecture notes,
- deviation reports from a reference design.
