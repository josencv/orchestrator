# Run Lifecycle V0

## Purpose

This document defines the first working loop for one issue.

## Lifecycle States

Internal run states for v0:

1. `discovered`
2. `claimed`
3. `workspace_prepared`
4. `broker_running`
5. `validation_running`
6. `summarizing`
7. `handed_off`
8. `failed`

These are orchestrator states, not tracker states.

## Happy Path

1. The coordinator fetches eligible issues from Linear.
2. The coordinator selects one issue using configured priority rules.
3. The tracker adapter claims the issue.
4. The workspace manager creates or reuses the issue workspace.
5. The coordinator builds the broker input bundle.
6. The broker adapter runs Copilot CLI inside the issue workspace.
7. The artifact store captures process output.
8. Optional validation commands run in the same workspace.
9. The coordinator builds a summary.
10. The tracker adapter posts a comment and moves the issue to human review.
11. The run is marked complete.

## Failure Paths

### Claim Failure

If claim fails, the run ends before workspace preparation and another issue may be considered on the next cycle.

### Workspace Failure

If workspace preparation fails:

- write a failed manifest,
- comment on the issue if possible,
- move the issue according to configured failure policy.

### Broker Failure

If broker execution fails:

- preserve all logs,
- write a failed manifest,
- comment the failure summary,
- move the issue to intake retry or failure triage.

### Validation Failure

Validation failure should not erase broker success.

Instead it should:

- mark the run as completed with failed validation,
- include the result in the summary,
- hand off to a human with explicit warning.

## Priority Rule

Recommended initial issue ordering:

1. explicit priority
2. oldest updated or created issue
3. stable identifier tie-breaker

The exact sort can be refined during implementation, but it should be deterministic.

## Human Review Handoff

A successful v0 run ends at human review, not done.

That preserves the product boundary:

- the orchestrator prepares work,
- a human accepts or rejects it.

## Why The Lifecycle Is Simpler Than Symphony

Symphony includes richer concepts around long-lived worker loops, retries, reconciliation, and session continuation.

V0 intentionally starts smaller:

- one issue at a time,
- one broker invocation per attempt,
- explicit handoff at the end.

Those features can be layered in later once the core loop is real.

## Classification

- `Inherited from Symphony`: issue selection, isolated run, observable lifecycle, human-review handoff.
- `Adapted from Symphony`: simpler single-attempt broker execution flow.
- `New for this project`: explicit validation stage after broker execution in the first loop.
