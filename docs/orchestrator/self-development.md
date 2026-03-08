# Self-Development Expectations

## Product Expectation

The orchestrator should eventually be able to operate on its own repository.

This is not a novelty feature. It is part of the intended operating model.

## Realistic Bootstrap Sequence

1. Build the first usable version manually.
2. Create implementation issues in the orchestrator's tracker.
3. Run the orchestrator against its own repo for bounded tasks.
4. Review resulting changes manually.
5. Restart or rerun the orchestrator manually when the tool itself changes.

## What Self-Development Does Not Mean

It does not require v0 to support:

- self-replacing binaries,
- zero-downtime process swaps,
- autonomous upgrade choreography,
- trustless self-modification.

## Repo Implications

Because self-development is expected:

- docs must be explicit enough for future agents to implement from them,
- artifacts must be inspectable,
- agent roles must be clearly separated,
- changes to repo rules must be reviewable like code.

## v0 Safety Stance

When the orchestrator works on itself:

- a human remains the merger and final reviewer,
- restart remains a manual operator action,
- destructive repo operations should remain tightly constrained.

## Future Expansion

Later phases may add:

- daemon restart wrappers,
- safer state recovery after self-modification,
- better bootstrap commands for working on this repo and target repos.

## Classification

- `Inherited from Symphony`: repo-owned workflow logic should make self-application feasible.
- `Adapted from Symphony`: self-development is treated as an operational milestone, not just an emergent property.
- `New for this project`: explicit manual bootstrap and restart model for the orchestrator working on itself.
