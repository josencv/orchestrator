# Tracker Model

## Purpose

The tracker is the source of work and the public record of run handoffs.

In v0 the first tracker is Linear.

## Design Rule

The orchestrator should depend on tracker semantics, not on hardcoded tracker names.

That means the orchestrator should care about concepts such as:

- eligible work,
- claim transition,
- human review handoff,
- terminal completion,
- comments or run notes.

The Linear adapter maps those concepts to concrete Linear fields and transitions.

## Issue Shape Needed By The Coordinator

Minimum normalized fields:

- `id`
- `identifier`
- `title`
- `description`
- `state`
- `priority`
- `labels`
- `project`
- `url`
- `updatedAt`

Additional fields can be preserved, but these are enough for v0 dispatch and reporting.

## Eligibility Model

An issue is eligible for v0 orchestration only when all are true:

- it belongs to the configured project,
- it is in the configured intake state set,
- it is not already claimed by an active orchestrator run,
- it is not blocked by an explicit skip label,
- it has enough descriptive context for a meaningful broker prompt.

## Tracker State Semantics

This spec distinguishes semantic states from tracker concepts, but for v0 the initial Linear mapping is now locked.

### Semantic States

- `intake`: issue may be selected for orchestration.
- `claimed`: issue is currently reserved by the orchestrator.
- `human_review`: broker work has finished and a human should inspect the result.
- `done`: issue is complete.
- `canceled`: issue should no longer run.

### V0 Linear Mapping

The initial v0 Linear workflow uses these exact states:

- `Todo`
- `In Progress`
- `Human Review`
- `Done`

Semantic mapping for v0:

- `intake` -> `Todo`
- `claimed` -> `In Progress`
- `human_review` -> `Human Review`
- `done` -> `Done`

For v0, failure after a claim should move the issue back to `Todo` with a run comment that explains the failure.

This keeps the first workflow small and avoids inventing a dedicated triage state before there is operational evidence that it is needed.

### Future Flexibility

Later versions may make state mapping configurable again if multiple target projects need different workflows.

For the first implementation, exact state names are a feature, not a liability, because they reduce ambiguity.

## Claim Model

In v0 the orchestrator owns the claim transition.

Recommended claim behavior:

1. fetch one candidate issue,
2. attempt an atomic state change or guarded update in Linear,
3. record the claim in local run metadata,
4. proceed only if the claim succeeds.

If true atomic claim support proves awkward in Linear, v0 may use a best-effort guarded update plus a clear run comment. That is acceptable as a provisional compromise.

## Comment Model

Each run should leave a structured tracker comment that contains:

- run identifier,
- broker used,
- workspace path or workspace key,
- summary outcome,
- validation summary,
- artifact location reference,
- next expected human action.

The comment is not just noise. It is the human-facing audit trail.

## Failure Handling

If a run fails before the broker starts:

- release or move the issue according to configured failure policy,
- add a comment explaining the failure stage.

If the broker runs and fails:

- add a comment with the failure summary,
- move the issue either back to intake or to a failure triage state.

The exact failure-state mapping is no longer an implementation blocker for v0.

V0 rule:

- failed claimed runs return to `Todo` with a failure comment.

## Tracker Adapter Boundary

The v0 tracker adapter should expose capabilities equivalent to:

- `listEligibleIssues()`
- `claimIssue(issueId)`
- `refreshIssue(issueId)`
- `commentOnIssue(issueId, summary)`
- `moveIssue(issueId, semanticState)`

## Classification

- `Inherited from Symphony`: tracker-driven issue orchestration.
- `Adapted from Symphony`: orchestrator-owned claim and handoff transitions instead of delegating them to the agent.
- `New for this project`: a deliberately small first Linear workflow using `Todo`, `In Progress`, `Human Review`, and `Done`.
