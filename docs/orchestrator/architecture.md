# Architecture

## Architecture Definition

The orchestrator is a local CLI application with a small coordination core and explicit adapter boundaries.

In v0 it should be able to run a single issue loop end to end without requiring a persistent service process or a database.

## Primary Components

### CLI Entry

Responsible for:

- loading config,
- selecting command mode,
- starting one orchestration cycle.

Planned command shape:

- `orchestrator run-once`
- `orchestrator loop` later in stage 1
- `orchestrator inspect-run <run-id>` later if useful

### Run Coordinator

Responsible for:

- polling or fetching eligible tracker issues,
- deciding whether one issue can be claimed,
- invoking the run lifecycle,
- deciding the final tracker handoff state,
- recording a run manifest.

This is the product core.

### Tracker Adapter

Responsible for:

- listing eligible issues,
- claiming an issue through agreed tracker mutation,
- posting run comments and summaries,
- moving an issue into the next workflow state.

v0 adapter target:

- `LinearTrackerAdapter`

### Workspace Manager

Responsible for:

- mapping issue identity to a deterministic local directory,
- creating or reusing the directory,
- preparing repo contents or worktrees,
- enforcing path safety constraints,
- exposing cleanup operations.

### Broker Adapter

Responsible for:

- receiving a prepared run contract,
- executing the broker in the issue workspace,
- streaming stdout and stderr into artifacts,
- returning normalized outcome data.

v0 adapter target:

- `CopilotCliBrokerAdapter`

### Artifact Store

Responsible for:

- writing structured metadata,
- writing stdout and stderr logs,
- storing prompt inputs and post-run summaries,
- making each run inspectable after completion.

### Post-Run Evaluator

Responsible for:

- running optional validation commands,
- collecting exit codes and outputs,
- attaching evidence to the run result.

This remains simple in v0 and should not become a workflow engine.

## Boundary Rules

- The coordinator knows workflow state, not tracker-specific API details.
- The tracker adapter knows tracker payloads, not broker execution details.
- The broker adapter knows broker invocation details, not tracker mutation policy.
- The workspace manager knows filesystem and worktree rules, not business prioritization.
- The artifact store never decides workflow outcomes; it only records them.

## v0 Data Flow

1. Load config for one target project.
2. Ask the tracker adapter for the next eligible issue.
3. Claim the issue.
4. Prepare the issue workspace.
5. Build the broker input bundle.
6. Run the broker.
7. Optionally run post-run validation commands.
8. Persist artifacts and summary.
9. Comment on the issue and move it to human review or failure triage.

## Chosen Simplifications For v0

- One active issue at a time.
- One broker invocation per run attempt.
- No internal event bus requirement.
- No distributed coordination.
- No hot config reload requirement for the first milestone.

## Provisional Choices

### Workflow Contract File

The long-term product should keep repo-owned workflow policy.

The initial v0 repo-owned workflow contract is now:

- `.orchestrator/config.json`
- `.orchestrator/prompt.md`

Reason:

- it is easier to evolve in a Node.js and TypeScript codebase,
- separates structured machine config from human-authored prompt text,
- avoids cloning Symphony's `WORKFLOW.md` shape before it proves necessary here.

This is still a v0 choice, not a forever format guarantee.

### Worktree Strategy

The orchestrator should support deterministic issue-isolated work directories. Whether v0 always uses `git worktree`, sometimes uses a plain clone, or supports both behind a small strategy interface remains provisional pending implementation constraints.

### Command Surface

The command names above are recommended, not frozen.

## Decision Classification Snapshot

- `Inherited from Symphony`: coordination core plus adapters, repo-owned workflow policy, isolated per-issue execution.
- `Adapted from Symphony`: simplified broker subprocess contract, orchestrator-owned tracker transitions, CLI-first entry.
- `New for this project`: first-class artifact store and run manifest tailored to self-development and later repo reuse.
