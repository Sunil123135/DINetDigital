# Reference patterns (Fareed Khan corpus)

Use with `SKILL.md`. Sources: bundled `digests/` in this skill.

## Supervisor multi-agent

Specialists own tools; supervisor owns routing. Shared `State` carries identity, messages, memory, step budget. Trace with LangSmith. (Digest 01)

## Contextual engineering

Treat context window as RAM. Strategies: write scratchpad, select relevant items, compress history, isolate sub-agents. (Digest 02)

## Agentic RAG cognition

Gatekeeper (ambiguity) → Planner → specialist tools (Librarian/Analyst/Scout) → Auditor → Strategist. Structure-aware ingestion before vectors. (Digest 04, 03)

## Guardrail stack

L1 input async · L2 action-plan policy · L3 output verify. Red-team after wiring. (Digest 05)

## Memory

Thread checkpoint ≠ cross-thread store. Namespace memories; graduate InMemory → Postgres/pgvector. HITL corrections write long-term prefs. (Digest 06)

## Parallelism pillars

Parallel tools, hierarchical teams, ensembles, blackboard, speculative/redundant execution, multi-hop retrieval. Measure I/O wait. (Digest 07)

## Loop engineering

Discover → act → verify against external signal → continue. Maker–checker and CI/PR patterns. (Digest 15)

## Eval

Twelve+ techniques; notebook + LangSmith; trajectory and tool metrics. (Digest 08)

## Production + training

Layered infra (auth, abuse, resilience). Training wraps graph rollouts with multi-criteria rewards; train selected nodes only. (Digests 09, 16)

## Threat detection

Transcript-level detection; Sifter escalate / Inspector convict; MCP evidence tools; open weights on-box. (Digest 12)
