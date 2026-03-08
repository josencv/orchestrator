# Decision Log

This file classifies the major design choices that shape the stage 1 orchestrator.

## Decision Table

| Decision                                                                                                                       | Classification          | Grounding                                                                                                            | v0 Position                                         | Rationale                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------ | ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Issue-driven orchestration from a tracker is the core product loop.                                                            | Inherited from Symphony | Present in Symphony and project context.                                                                             | Fixed for v0.                                       | This is the central workflow value being preserved.                                                                       |
| Per-issue isolated workspaces remain mandatory.                                                                                | Inherited from Symphony | Present in Symphony and project context.                                                                             | Fixed for v0.                                       | Isolation is one of the highest-value operational constraints.                                                            |
| Workflow policy stays repo-owned and versioned.                                                                                | Inherited from Symphony | Present in Symphony as `WORKFLOW.md`.                                                                                | Fixed in principle; exact file contract is adapted. | Policy should travel with the target repo, not live in hidden local config.                                               |
| v0 is CLI-first, with a daemon mode coming later.                                                                              | Adapted from Symphony   | Project context favors a simpler first shape than a full long-running service.                                       | Fixed for v0.                                       | This gets to a real working loop faster and reduces early process-lifecycle complexity.                                   |
| v0 uses one active worker only.                                                                                                | Adapted from Symphony   | Project context explicitly says concurrency matters later, not first.                                                | Fixed for v0.                                       | One worker is easier to reason about, test, and operate.                                                                  |
| Linear is the first tracker adapter.                                                                                           | Adapted from Symphony   | Symphony is Linear-first; project context locks Linear as first tracker.                                             | Fixed for v0.                                       | It matches the intended workflow and keeps the first integration focused.                                                 |
| V0 Linear states are `Todo`, `In Progress`, `Human Review`, and `Done`.                                                        | New for this project    | Locked from review after the first shaping pass.                                                                     | Fixed for v0.                                       | Exact state names remove ambiguity and are sufficient for the first workflow loop.                                        |
| Copilot CLI is the first broker.                                                                                               | New for this project    | Project context names Copilot CLI first.                                                                             | Fixed for v0.                                       | The broker surface should match the tools actually intended to be used first.                                             |
| The broker contract is capability-based, but only one broker is implemented in v0.                                             | Adapted from Symphony   | Symphony assumes a specific coding-agent protocol; this repo needs broker evolution without full abstraction sprawl. | Fixed for v0.                                       | Explicit boundaries now prevent later hard-coding, but over-implementation is avoided.                                    |
| Copilot integration starts with a thin subprocess spike and uses exit code plus timeout as the primary machine signal.         | New for this project    | Locked from review after the first shaping pass.                                                                     | Fixed for v0.                                       | Broker uncertainty should be tested early with the simplest dependable contract.                                          |
| v0 should not adopt Symphony's multi-turn app-server thread lifecycle.                                                         | Adapted from Symphony   | Symphony's protocol is valuable, but mismatched to a Copilot CLI-first start.                                        | Fixed for v0.                                       | One broker invocation per claimed issue run is simpler and aligns with the preferred first broker.                        |
| The orchestrator, not the broker, owns tracker claim and handoff transitions in v0.                                            | Adapted from Symphony   | Symphony often leaves ticket writes to the coding agent.                                                             | Fixed for v0.                                       | Tracker mutation is too important to leave implicit in an early implementation.                                           |
| No persistent database is required for v0.                                                                                     | Inherited from Symphony | Symphony explicitly avoids requiring a DB for restart recovery.                                                      | Fixed for v0.                                       | File artifacts plus tracker truth are enough for the first milestone.                                                     |
| Local run manifests should exist even without a database.                                                                      | New for this project    | Needed because v0 is CLI-first and artifact-heavy.                                                                   | Fixed for v0.                                       | A small local manifest improves debuggability and future daemon recovery.                                                 |
| V0 workspace population prefers `git worktree` but permits a prepared working copy fallback.                                   | Adapted from Symphony   | Locked from review after the first shaping pass.                                                                     | Fixed for v0.                                       | Worktree remains the preferred direction without blocking implementation progress.                                        |
| The initial local data root is `~/.orchestrator/` on macOS and Linux, with `%LOCALAPPDATA%\\orchestrator` planned for Windows. | New for this project    | Locked from review after the first shaping pass.                                                                     | Provisional operational default.                    | A simple default is enough for v0 and can be revised later without architectural damage.                                  |
| The initial repo-owned workflow contract is `.orchestrator/config.json` plus `.orchestrator/prompt.md`.                        | New for this project    | Locked from review after the first shaping pass.                                                                     | Fixed for v0.                                       | Separate config and prompt files fit the planned Node.js and TypeScript implementation better than cloning `WORKFLOW.md`. |
| Node.js + TypeScript + `pnpm` is the preferred implementation stack.                                                           | New for this project    | Provided preference in the shaping prompt.                                                                           | Provisional until implementation starts.            | Strong fit for CLI and adapters, but not elevated to dogma yet.                                                           |
| Self-development is expected after a manually-built v0 exists.                                                                 | New for this project    | Project context explicitly describes this path.                                                                      | Fixed as a product expectation.                     | It shapes repo rules and task decomposition from the beginning.                                                           |

## Notable Departures From Symphony

### Tracker writes are orchestrator-owned in v0

Symphony leaves more workflow mutation to the coding agent. This spec moves the minimum required tracker state updates into the orchestrator for v0.

Reason:

- claim and handoff transitions are too central to reliability,
- Copilot CLI-first operation should not depend on hidden tool access,
- early auditability is better when state changes come from one process.

### Broker integration starts as simple subprocess execution

Symphony's app-server protocol remains a useful reference, but it is intentionally not the first implementation target.

Reason:

- the first broker is Copilot CLI,
- the first milestone is one practical issue loop,
- protocol complexity is not justified until the simpler path proves insufficient.

### CLI-first before daemon

Symphony is daemon-first. This repo adopts a smaller first shape.

Reason:

- it shortens time to the first end-to-end run,
- simplifies debugging,
- still leaves a clean path to a later long-running process.
