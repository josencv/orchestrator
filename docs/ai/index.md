# AI Docs

This folder is the human-facing guide to AI workflow in this repository.

The operative Copilot files live in:

- `.github/copilot-instructions.md`
- `.github/agents/*.agent.md`
- `AGENTS.md`

This folder explains how those operative files should be used inside the repo workflow.

## Read Order

1. `.github/copilot-instructions.md`
2. `AGENTS.md`
3. `.github/agents/*.agent.md`
4. `docs/ai/repo-navigability.md`
5. `docs/ai/coordination-workflow.md`
6. `docs/ai/dev-workflow-roadmap.md`

## Purpose

- keep the operative Copilot files easy to find,
- define the human-facing navigation layer for agent work,
- explain the linear shaping-to-delivery workflow used in this repo,
- avoid duplicating the canonical Copilot instruction file in a second doc path,
- keep work aligned with the orchestrator spec and planning process,
- keep the human-facing AI docs readable without pretending they are the only executable rules.

## File Roles

- `repo-navigability.md`: defines what documentation quality and indexing standard agents should expect.
- `coordination-workflow.md`: defines the linear idea-to-delivery workflow for this repo.
- `dev-workflow-roadmap.md`: reserved place for future workflow expansion beyond the current contract.

Role definitions live in `AGENTS.md` and `.github/agents/`, not in `docs/ai/`.

## Canonical Rule

The canonical repository instruction file for Copilot is `.github/copilot-instructions.md`.

Do not create a second quasi-operative instruction file under `docs/ai/` unless it serves a clearly different explanatory purpose that does not duplicate the canonical instruction set.
