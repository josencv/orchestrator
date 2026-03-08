# Isolation And Safety

## Core Safety Posture

This is a local high-trust tool, but not a careless one.

The orchestrator should enforce the small set of invariants that prevent the most expensive mistakes.

## Required Invariants

- Broker execution must happen inside the resolved issue workspace.
- Workspace paths must stay inside the configured workspace root.
- Issue identifiers used in paths must be sanitized.
- Tracker claim and handoff actions must be explicit and logged.
- Artifact writes must never overwrite committed docs or source files by default.

## Trust Model

The first implementation is expected to run on a trusted local machine with normal developer credentials.

This does not eliminate the need for guardrails.

It means the guardrails should focus on:

- path correctness,
- bounded execution location,
- auditability,
- avoiding silent state mutation.

## Destructive Operations

V0 should avoid destructive cleanup behavior by default.

Examples:

- do not hard reset reused workspaces unless explicitly configured,
- do not auto-delete workspaces after success,
- do not auto-merge or auto-close issues.

## Tracker Safety

Tracker mutations should be limited to:

- claim transition,
- run comments,
- final handoff state changes.

Anything broader belongs in later phases after operational experience exists.

## Command Safety

Optional validation commands should be explicit project configuration, not ad hoc shell text generated at runtime by the orchestrator.

This keeps the orchestrator small and auditable.

## Classification

- `Inherited from Symphony`: workspace isolation and explicit safety posture matter.
- `Adapted from Symphony`: early safety centers on filesystem and tracker invariants rather than protocol-level sandbox features.
- `New for this project`: conservative default stance against destructive workspace cleanup in self-development scenarios.
