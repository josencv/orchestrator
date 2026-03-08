# Process Docs

These docs define how planning and planning review should work in this repository.

They are process docs, not product specs.

## Scope

Use `docs/process/` for:

- shaping new features or significant changes,
- reviewing plans before implementation preparation,
- keeping decision status, blocker status, and review severity consistent.

Do not use `docs/process/` to redefine the orchestrator product silently.
That still belongs in `docs/orchestrator/`.

## Read Order

1. `docs/process/planning-contract.md`
2. `docs/process/decision-taxonomy.md`
3. `docs/process/review-severity.md`
4. `docs/process/planning-cadence.md`

## Relationship To Other Docs

- `docs/orchestrator/` remains the stage 1 product source of truth.
- `docs/process/` defines how plans are shaped and reviewed against that product spec.
- `docs/ai/` is a human-facing guide to repo AI workflows and operative Copilot files.
- `AGENTS.md` and `.github/agents/` are the repo-local execution rules for Copilot agents.
