# Workspace And Worktree Model

## Purpose

Each issue run needs an isolated local directory so broker actions are bounded and inspectable.

## Terms

- `workspace`: the issue-specific working directory used by the broker.
- `population strategy`: how repository contents appear in that workspace.
- `worktree strategy`: a population strategy that uses `git worktree`.

## v0 Rule

The orchestrator owns workspace identity even if the underlying filesystem strategy changes later.

That means every run resolves a deterministic workspace key first, then asks the workspace manager how to materialize it.

## Recommended Path Shape

Recommended default:

`<workspaceRoot>/<projectKey>/<issueKey>/`

Where:

- `projectKey` is a sanitized stable project slug,
- `issueKey` is a sanitized tracker identifier such as `ORCH-12`.

This slightly exceeds the bare minimum for one project, but the extra directory level is cheap and avoids later collisions.

## Isolation Rules

- Workspace paths must be normalized to absolute paths before use.
- The resolved workspace path must remain under `workspaceRoot`.
- The broker must run with `cwd` set to the resolved workspace path.
- The orchestrator must never run broker commands in the orchestrator repo root by accident.

## Population Strategy

V0 should not require `git worktree` as a hard dependency.

Locked v0 strategy:

- preferred: use `git worktree` when the target project and environment support it,
- fallback: use a prepared working copy strategy behind the same workspace manager boundary.

This keeps the desired Git-native path visible without allowing it to block the first usable implementation.

## Branching Model

Branching should be deterministic but light.

Recommended branch name pattern:

`issue/<issueKey>-<slug>`

This is a convenience rule, not a strict product invariant.

## Reuse Model

Workspaces should be reused for repeated attempts on the same issue unless the operator explicitly requests cleanup.

Reason:

- it preserves agent-produced context,
- it reduces setup cost,
- it helps debugging.

## Cleanup Model

Automatic cleanup should be conservative in v0.

Safe default:

- do not auto-delete a workspace after a normal run,
- allow explicit cleanup commands later,
- allow cleanup on terminal issue states as a later enhancement.

## Provisional Areas

### Exact Git Preparation Steps

Whether v0 performs fetch, checkout, branch creation, reset, or dependency bootstrap inside the workspace should remain implementation-defined for now.

These steps should be explicit in code and docs once the first target repo workflow is tested.

### Multiple Repos Per Project

Not part of v0.

The path shape above is chosen to avoid blocking it later, not to implement it now.

## Classification

- `Inherited from Symphony`: deterministic per-issue isolated workspaces.
- `Adapted from Symphony`: workspace identity is kept stable while the actual population strategy remains swappable.
- `New for this project`: default path includes `projectKey` to prepare for future multi-project use at very low cost.
