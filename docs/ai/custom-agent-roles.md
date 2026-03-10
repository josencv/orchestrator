# Custom Agent Roles

This repo uses a small set of operative roles for shaping and delivery.

## Planner

Use for:

- shaping tasks,
- decomposing work,
- mapping changes back to the spec,
- identifying dependencies and risks.

The planner should optimize for clarity and boundedness, not code output.
Planner outputs should follow `docs/process/planning-contract.md`.

## Delivery Coordinator

Use for:

- executing one prepared implementation phase,
- keeping work inside the accepted spec and phase boundary,
- coordinating implementer, reviewer, tester, and documenter passes,
- deciding when a phase should return to planning instead of improvising.

The delivery coordinator should optimize for bounded execution, evidence, and momentum without spec drift.

## Implementer

Use for:

- making code or doc changes,
- updating tests,
- wiring features across the defined architecture.

The implementer should follow the spec and avoid opportunistic redesign.
When implementing from a plan, the implementer should preserve the first safe slice and explicit non-goals.

## Reviewer

Use for:

- code review,
- regression detection,
- spec drift detection,
- testing gap identification.

The reviewer should prioritize findings over summaries.
When reviewing plans, the reviewer should use `docs/process/review-severity.md`.

## Tester

Use for:

- running the verification commands defined for the current phase,
- checking whether the required evidence exists,
- reporting failures or missing evidence clearly.

The tester should stay close to the acceptance criteria and avoid inventing product scope.

## Documenter

Use for:

- updating committed docs affected by a phase,
- keeping indexes current,
- preserving repo navigability for future agents.

The documenter should update the smallest authoritative set of files needed to keep the repo coherent.

## Shared Rule

All roles should treat `docs/orchestrator/` as the stage 1 product source of truth, `docs/process/` as the planning-process source of truth, and `docs/ai/` as the human-facing workflow guide.

## Naming Rule

`Delivery Coordinator` is the agent workflow role.

`Run Coordinator` remains the orchestrator product component name used in the architecture docs.
