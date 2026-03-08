# Orchestrator Repo Instructions

- Treat `docs/orchestrator/` as the stage 1 source of truth.
- Treat `docs/ai/` and `AGENTS.md` as the repo's agent-behavior contract.
- Keep changes focused on stage 1 unless a later-stage note is explicitly needed for boundary clarity.
- Preserve these architectural seams: coordinator, tracker adapter, workspace manager, broker adapter, artifact store.
- Prefer the CLI-first v0 shape over a daemon-first redesign.
- Preserve isolated per-issue workspaces and explicit tracker claim and handoff behavior.
- Avoid broad abstractions for multi-project, multi-broker, concurrency, or distributed execution in v0.
- When behavior changes, update the relevant doc in `docs/orchestrator/`.
- When agent expectations change, update `docs/ai/`, `AGENTS.md`, or `.github/agents/`.
- Use `local/` for non-committed working outputs and temporary artifacts.
