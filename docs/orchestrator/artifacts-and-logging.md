# Artifacts And Logging

## Purpose

A run that cannot be inspected is not operationally trustworthy.

Artifacts are required in v0 even if the overall system is still small.

## Artifact Root

Artifacts should live in an orchestrator-managed local data root, not in committed source directories.

Recommended default shape:

`<dataRoot>/runs/<runId>/`

This keeps evidence local and keeps target repos clean.

## V0 Local Data Root

The local data root no longer counts as a true blocker.

Initial default for v0:

- macOS and Linux: `~/.orchestrator/`
- Windows later: `%LOCALAPPDATA%\\orchestrator`

This is a provisional operational default that can be revised later without changing the core product model.

## Required Files Per Run

Recommended minimum set:

- `manifest.json`: normalized run metadata and final outcome
- `issue.json`: captured normalized issue snapshot at dispatch time
- `prompt.md`: the final prompt or instruction bundle given to the broker
- `broker.stdout.log`
- `broker.stderr.log`
- `validation.json`: post-run command results if any
- `summary.md`: human-readable outcome summary

## Manifest Contents

`manifest.json` should include:

- run id
- issue id and identifier
- tracker kind
- broker kind
- workspace path
- timestamps
- final status
- validation status
- artifact paths
- tracker transition results
- error summary if present

## Logging Rules

Structured logs should exist in addition to per-run artifacts.

v0 logging expectations:

- stdout-friendly operator logs for normal usage,
- machine-readable JSON logs as an option,
- correlation by run id and issue identifier.

## Operator Value

Artifacts must answer these questions quickly:

- What issue was attempted?
- What instructions were given?
- What happened during broker execution?
- What validation ran?
- Why was the issue moved to its next state?

## Retention

Retention policy can remain simple in v0.

Safe starting rule:

- keep artifacts until manually cleaned up.

A pruning command can be added later once real usage patterns are known.

## Classification

- `Inherited from Symphony`: logs and observability are first-class requirements.
- `Adapted from Symphony`: per-run artifact bundles are emphasized over a live status surface.
- `New for this project`: explicit local run bundle format to support self-development and post-run review.
