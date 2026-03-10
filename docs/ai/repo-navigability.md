# Repo Navigability

## Purpose

This document defines what it means for this repo to be navigable for humans and agents.

Navigability is a repo contract.
It is not a vague preference for having more docs.

## Navigability Standard

This repo is navigable when an agent can determine, from committed files alone:

- what the product is,
- which docs are authoritative,
- what stage is active,
- what the current implementation slice is,
- which decisions are locked versus provisional,
- what evidence is required,
- and where documentation should be updated when behavior changes.

If an agent must depend on chat memory to answer those questions safely, the repo is not navigable enough yet.

## Required Navigation Surfaces

The repo should always maintain these navigation surfaces:

1. a root docs index in `docs/index.md`,
2. a product index for the orchestrator spec in `docs/orchestrator/index.md`,
3. a planning-process set in `docs/process/`,
4. a human-facing AI workflow index in `docs/ai/index.md`,
5. operative repo rules in `.github/copilot-instructions.md`, `AGENTS.md`, and `.github/agents/`,
6. decision history in `docs/orchestrator/decision-log.md`.

## Structure Rules

Prefer small seam-oriented docs over long mixed documents.

Each committed doc should answer one of these questions clearly:

- product behavior,
- planning discipline,
- agent workflow,
- role expectations,
- or decision history.

Do not mix all of them into one file.

## Index Rules

Indexes are mandatory, not decorative.

An index should:

- state what folder is for,
- define how to read the docs,
- link to the current authoritative files,
- and avoid duplicating the content of those files.

## Documentation Update Rule

Every implementation phase should end with a documentation check.

At minimum, confirm whether the change requires updates to:

- `docs/orchestrator/` for product behavior,
- `docs/process/` for planning discipline,
- `docs/ai/` for agent workflow,
- `AGENTS.md` or `.github/agents/` for operative role expectations,
- and any relevant index file.

If the answer is no, say so explicitly in the phase output.

## Promotion Rule

Use `local/` for draft artifacts, external briefs, shaping notes, and temporary review outputs.

Promote content into committed docs when either is true:

- agents must rely on it directly to act safely,
- or the information defines a stable repo contract.

## Style And Enforcement Guidance

Repo navigability is stronger when style and architecture rules are easy to find.

Those rules should live in committed repo docs or config, not in ad hoc chat instructions.

Prefer enforcement through:

- documented architecture seams,
- linting and formatting config,
- test and validation commands,
- and explicit acceptance evidence in plans and implementation preparation.

## Anti-Patterns

Avoid these failure modes:

- hiding real rules in `local/` only,
- duplicating the same taxonomy in many files,
- using one giant evolving planning note as the only source of truth,
- leaving indexes stale,
- or treating documentation as optional after code changes.
