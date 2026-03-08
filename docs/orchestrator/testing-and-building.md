# Testing And Building Expectations

## Build Expectation

If the repo proceeds with Node.js and TypeScript, the baseline toolchain should be:

- `pnpm` for package management,
- TypeScript for source and type checking,
- a small CLI entry surface,
- linting and formatting wired into normal development.

## Test Layers

### Unit Tests

Required for:

- config parsing,
- issue normalization,
- workspace path derivation,
- broker result normalization,
- artifact manifest creation.

### Integration Tests

Required for:

- Linear adapter behavior against mocked API responses,
- workspace manager behavior in temp directories,
- broker adapter behavior with a fake subprocess,
- end-to-end run coordination with test doubles.

### Smoke Test

Before calling v0 complete, the repo should support one local smoke test that proves:

- one issue can be selected,
- one workspace can be prepared,
- one broker run can complete,
- artifacts are written,
- a tracker summary can be produced.

This can start with test doubles before a live tracker environment is used.

## Evidence Expectation

Every task that changes orchestration behavior should leave behind one or more of:

- unit tests,
- integration tests,
- sample manifests or snapshots,
- documented manual smoke-test evidence.

## CI Expectation

CI is useful but not a v0 blocker for spec completion.

Once implementation starts, the repo should at least run:

- install,
- typecheck,
- test,
- lint.

## Classification

- `Inherited from Symphony`: observability and reliability require more than raw code execution.
- `Adapted from Symphony`: testing emphasizes CLI and adapter seams rather than daemon recovery first.
- `New for this project`: explicit smoke-test evidence is required before treating v0 as usable.
