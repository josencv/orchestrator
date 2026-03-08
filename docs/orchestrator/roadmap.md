# Roadmap

## V0

Goal:

Deliver one practical issue loop for one project, one tracker, one broker, and one operator.

Included:

- CLI-first command surface
- Linear adapter
- Copilot CLI adapter
- deterministic workspace management
- run artifacts and summaries
- optional validation commands
- human-review handoff

Excluded:

- multi-worker scheduling
- multi-project operation in one process
- richer broker protocol support
- daemon-only lifecycle features
- advanced dashboards

## Later Phases

### Phase 1.1: Stabilize The First Loop

- add `loop` mode on top of the `run-once` core
- improve retry behavior
- improve claim robustness
- add manual cleanup and inspection commands

### Phase 1.2: Strengthen Repo Contracts

- formalize the repo-owned workflow config shape
- strengthen prompt and instruction composition
- improve validation command configuration
- refine target-repo onboarding docs

### Phase 1.3: Operate On The Orchestrator Repo

- use the tool on its own implementation backlog
- improve artifact browsing and failure triage
- tighten agent-role instructions from real usage

### Phase 1.4: Broaden Carefully

- second broker adapter
- second tracker adapter only if truly needed
- stronger recovery and daemon supervision

## Future Concerns Borrowed From Symphony

These remain visible because Symphony is directionally right about them, but they are intentionally deferred.

- bounded concurrency
- reconciliation of in-flight work
- retry and backoff policy
- runtime config reload
- richer observability surfaces
- stronger restart recovery without a database
- more expressive workflow contracts

## Stage 2 And 3 Notes

The orchestrator should eventually support the Godot harness and the game repos, but stage 1 should not absorb their implementation complexity.

The only current requirement from later stages is architectural cleanliness:

- tracker and broker boundaries should stay explicit,
- workspace identity should not assume one forever repo shape,
- artifact design should be reusable.
