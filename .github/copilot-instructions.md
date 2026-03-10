# Orchestrator Repo Instructions

- Start from `docs/index.md` when orienting in the repo.
- Treat `docs/orchestrator/` as the product source of truth.
- Treat `docs/process/` as the planning-process source of truth.
- Treat `AGENTS.md` and `.github/agents/` as the repo's operative agent-behavior contract.
- Treat `docs/ai/` as the human-facing guide to that agent behavior.
- Keep the repo navigable for agents by maintaining indexes, explicit decision records, and updated workflow docs.
- Keep changes focused on the orchestrator product. Do not broaden scope into unrelated projects.
- Preserve these architectural seams: coordinator, tracker adapter, workspace manager, broker adapter, artifact store.
- Prefer the CLI-first v0 shape over a daemon-first redesign.
- Preserve isolated per-issue workspaces and explicit tracker claim and handoff behavior.
- Avoid broad abstractions for multi-project, multi-broker, concurrency, or distributed execution in v0.
- Treat implementation preparation as the step that turns candidate tasks into authoritative delivery scope.
- Treat delivery work as phase-bounded execution against an accepted spec and plan.
- When behavior changes, update the relevant doc in `docs/orchestrator/`.
- When planning discipline changes, update the relevant doc in `docs/process/`.
- When agent expectations change, update `docs/ai/`, `AGENTS.md`, or `.github/agents/`.
- Before closing meaningful work, check whether `docs/index.md`, `docs/ai/index.md`, or another relevant index should change.
- Use `local/` for non-committed working outputs and temporary artifacts.
