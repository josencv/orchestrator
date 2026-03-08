# Stage Boundaries

## Active Stage

This repository is currently about stage 1: the orchestrator.

## Allowed References To Later Stages

Later stages may be referenced only when they materially affect stage 1 design.

Allowed examples:

- keeping adapter boundaries reusable,
- avoiding obvious OS lock-in,
- preserving room for future broker growth,
- noting that the Godot harness will be a separate repo.

## Not Allowed As Current Scope

- designing the Godot harness runtime protocol,
- designing game systems,
- broadening v0 to solve stage 2 concerns,
- mixing game feature planning into core orchestrator implementation tasks.

## Practical Rule

If a proposal does not make the first issue loop better, safer, or easier to reach, it probably does not belong in active stage 1 scope.
