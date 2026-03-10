# Implementation Preparation

## Purpose

This document defines the handoff from accepted plan to executable delivery phase.

It exists because shaped specs and candidate tasks are not enough for safe implementation.

## Role In The Workflow

Implementation preparation happens after plan review and before delivery execution.

It is the step where candidate tasks become authoritative for a bounded phase.

## Required Output

Every implementation-preparation artifact should include:

### 1. Phase Objective

State the exact slice being executed now.

### 2. Relevant Spec References

List the committed docs and sections that govern the phase.

### 3. Included Scope

List what the current phase must deliver.

### 4. Explicit Non-Goals

List what the phase must not expand into.

### 5. Acceptance Criteria

State the concrete conditions that define completion.

### 6. Required Evidence

State the tests, artifacts, screenshots, logs, or rationale expected at the end.

### 7. Expected Change Surface

List the files, modules, seams, or doc areas expected to change.

### 8. Validation Commands

List the commands or checks that should run if the phase lands successfully.

### 9. Documentation Expectations

List which committed docs and indexes must be checked or updated.

### 10. Assigned Roles

State which roles are expected for the phase.

Typical roles:

- `Delivery Coordinator`
- `Implementer`
- `Reviewer`
- `Tester`
- `Documenter`

## Readiness Rule

A phase is ready for delivery only when:

- the first safe slice remains intact,
- the current phase scope is bounded,
- acceptance criteria are testable or inspectable,
- documentation expectations are explicit,
- and unresolved items are classified instead of hidden.

## Escalation Rule

Return from implementation preparation to planning or reshaping only when one of these is true:

- the first safe slice changed,
- a locked decision was reopened,
- the expected change surface is far larger than planned,
- or the acceptance criteria can no longer prove the intended slice.

Otherwise keep momentum and execute the bounded phase.

## Anti-Patterns

Avoid these mistakes:

- turning the phase into the whole roadmap,
- leaving validation implicit,
- hiding documentation work under a later vague follow-up,
- or treating candidate tasks as already authoritative before this step.
