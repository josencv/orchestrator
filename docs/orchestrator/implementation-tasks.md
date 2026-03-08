# Initial Implementation Tasks

These are the first ten concrete tasks implied by the adjusted spec.

The implementation sequence below reflects practical uncertainty, not just architectural neatness.

## 1. Scaffold The CLI Workspace

Create the Node.js and TypeScript project with `pnpm`, the initial source layout, linting, test runner, and a minimal CLI entrypoint.

Acceptance:

- install works,
- typecheck works,
- tests can run,
- CLI prints help.

## 2. Define The Typed Config Model

Implement config loading for the orchestrator process and one target project, including tracker settings, workspace root, broker settings, and artifact root.

Acceptance:

- invalid config is rejected clearly,
- typed config object is available to the coordinator.

## 3. Implement The Run Manifest Schema

Create the normalized run manifest shape and file-writing helpers for per-run artifact bundles.

Acceptance:

- a test can write and read a manifest bundle deterministically.

## 4. Build A Thin Copilot Runner Spike

Before the full broker adapter and before deeper tracker write-path work, prove the minimum Copilot CLI contract in isolation.

Acceptance:

- a subprocess can launch in a test workspace,
- prompt material can be passed inline or by file,
- stdout and stderr are captured,
- timeout behavior is understood.

## 5. Build The Linear Adapter Read Path

Implement issue listing, normalization, and semantic-state mapping for eligible issue selection.

Acceptance:

- mocked Linear responses normalize into the coordinator issue model,
- eligible issue filtering is deterministic.

## 6. Implement The Workspace Manager

Implement workspace key derivation, safe path resolution, workspace creation or reuse, and the preferred or fallback population strategy hook point.

Acceptance:

- path safety invariants are enforced,
- a workspace can be prepared in tests,
- the manager can choose worktree or prepared working copy strategy.

## 7. Build The Linear Adapter Write Path

Implement issue claim, comment, and handoff transitions.

Acceptance:

- guarded claim flow exists,
- summary comment payload is testable,
- semantic state mapping is configurable.

## 8. Implement The Coordinator Happy Path

Wire config, tracker adapter, workspace manager, the validated Copilot broker integration, artifact writing, and tracker handoff into one `run-once` command.

Acceptance:

- one eligible issue can complete the full loop in an integration-style test with doubles,
- broker output paths are written into the manifest,
- the thin Copilot spike has been folded into the real runtime path.

## 9. Add Optional Validation Command Execution

Allow configured post-run validation commands and capture their outputs without turning the orchestrator into a full workflow engine.

Acceptance:

- validation results are attached to the manifest and summary,
- validation failure is distinguishable from broker failure.

## 10. Add A Local Smoke-Test Harness

Provide one repeatable smoke-test path that proves the first end-to-end loop works with safe local doubles.

Acceptance:

- a documented command produces a sample run bundle and summary,
- the repo has a clear definition of v0 readiness.
