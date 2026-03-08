# Broker Model

## Purpose

The broker adapter turns an issue run contract into one bounded coding-agent execution.

## V0 Broker Choice

The first broker is Copilot CLI.

This is a product decision, not an incidental implementation detail.

For v0, the Copilot integration contract is now locked at a simple subprocess level.

## Why This Differs From Symphony

Symphony is centered on a richer coding-agent protocol and live session model.

That remains a useful reference, but it is too heavyweight for a Copilot CLI-first v0.

The retained principle is:

- the orchestrator speaks to a broker boundary,
- not directly to one forever-hardcoded execution path.

## Run Contract

The coordinator should hand the broker adapter a normalized contract containing:

- run identifier,
- issue summary and description,
- workspace path,
- repo-owned instructions or prompt inputs,
- optional validation command list,
- timeout settings,
- artifact output directory.

## Broker Result Contract

The broker adapter should return:

- `status`: `succeeded`, `failed`, `timed_out`, or `canceled`
- `startedAt`
- `endedAt`
- `exitCode`
- `stdoutPath`
- `stderrPath`
- `summary`
- `brokerMetadata`

`brokerMetadata` is intentionally open-ended so future brokers can expose more detail without forcing the coordinator to know broker internals.

## Capability Flags

A future-safe broker interface should allow capability checks such as:

- supports streaming output,
- supports structured usage metrics,
- supports persistent sessions,
- supports tool approvals,
- supports custom prompt file input.

v0 does not need to use every capability. It only needs the interface shape to avoid painting the architecture into a corner.

## Prompt And Instruction Model

The broker adapter should receive prebuilt prompt material from the coordinator or a dedicated prompt builder.

The broker adapter should not be responsible for deciding product workflow policy.

For v0, prompt material may be passed either:

- inline on the subprocess command line when the broker supports it safely, or
- through a prompt file written into the run artifact bundle or workspace.

The prompt-file path is the safer default because it is easier to inspect and less fragile for long prompts.

## Failure Semantics

Broker failures should be reported as normalized outcomes rather than raw process trivia alone.

Examples:

- executable not found,
- non-zero exit,
- timeout,
- interrupted by operator,
- malformed result artifact if the broker promises one.

## Copilot CLI V0 Contract

The first implementation should assume only this:

- Copilot CLI is launched as a subprocess.
- The subprocess runs with `cwd` set to the resolved issue workspace.
- Prompt material is supplied inline or by file.
- Stdout and stderr are both captured as artifacts.
- Exit code and timeout are the primary machine-readable signals.

Anything richer is an enhancement, not a prerequisite for v0.

## Copilot CLI Spike Requirement

Because the broker contract is one of the highest-uncertainty seams, implementation should include a thin Copilot runner spike early in the sequence.

That spike should prove only:

- launch works,
- prompt passing works,
- output capture works,
- timeout handling works.

Only after that proof should the full broker adapter be treated as stable.

## Classification

- `Inherited from Symphony`: explicit agent execution boundary.
- `Adapted from Symphony`: broker integration starts as a subprocess adapter driven by exit code and timeout instead of a session protocol client.
- `New for this project`: Copilot CLI is the first-class initial broker target.
