# Dev Workflow Roadmap

## Purpose

This document reserves a clear place for future repo guidance beyond the current implementation and development workflow.

The current repo workflow is defined in `docs/ai/coordination-workflow.md`.

This file is intentionally about later expansion, not the current baseline.

## What This File Is For

Use this file later to document repo-wide guidance for topics such as:

- multi-session coordination patterns,
- post-session audit policies,
- stronger automation around implementation preparation,
- self-development runbooks once the tool can operate on itself more routinely,
- evidence and artifact handling during active development,
- model-selection strategy across different review passes,
- and planner, delivery coordinator, implementer, reviewer, tester, and documenter coordination at larger scales.

## What This File Does Not Do Yet

This file does not define:

- the planning contract,
- the current implementation-preparation contract,
- the current coordination workflow,
- decision or blocker taxonomy,
- review severity,
- or the runtime behavior of the orchestrator product.

Those belong in:

- `docs/process/`
- `docs/ai/coordination-workflow.md`
- `docs/orchestrator/`
- `.github/copilot-instructions.md`
- `AGENTS.md`
- `.github/agents/*.agent.md`

## Current Rule

Until this roadmap is expanded:

- planning guidance lives in `docs/process/`,
- current delivery workflow guidance lives in `docs/ai/coordination-workflow.md`,
- and product behavior lives in `docs/orchestrator/`.

Any future development-workflow doc should stay scoped to the orchestrator product and avoid silently redefining the product spec.
