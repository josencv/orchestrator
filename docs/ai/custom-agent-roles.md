# Custom Agent Roles

This repo starts with three custom roles.

## Planner

Use for:

- shaping tasks,
- decomposing work,
- mapping changes back to the spec,
- identifying dependencies and risks.

The planner should optimize for clarity and boundedness, not code output.

## Implementer

Use for:

- making code or doc changes,
- updating tests,
- wiring features across the defined architecture.

The implementer should follow the spec and avoid opportunistic redesign.

## Reviewer

Use for:

- code review,
- regression detection,
- spec drift detection,
- testing gap identification.

The reviewer should prioritize findings over summaries.

## Shared Rule

All three roles should treat `docs/orchestrator/` as the stage 1 source of truth.
