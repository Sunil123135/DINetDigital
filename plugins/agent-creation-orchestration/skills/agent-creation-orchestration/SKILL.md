---
name: agent-creation-orchestration
description: >-
  Design and implement production-minded AI agents and multi-agent orchestration
  using patterns distilled from Fareed Khan's Medium/Level Up articles (LangGraph
  supervisors, contextual engineering, agentic RAG, memory, guardrails, loop
  engineering, eval, threat detection). Use when creating agents, orchestrating
  sub-agents, building agentic RAG, adding memory/HITL/guardrails, or planning
  agent evaluation and production layers.
---

# Agent Creation & Orchestration

**Plugin skill** — bundled in the `agent-creation-orchestration` plugin (`plugins/agent-creation-orchestration/`), distributed via this repo's marketplace (`.claude-plugin/marketplace.json`). Once installed with `/plugin install agent-creation-orchestration@dinetdigital-plugins`, it's invoked as `/agent-creation-orchestration:agent-creation-orchestration` and is available in every project on that machine, independent of which repo you're in.
Corpus: bundled `INDEX.md` + `digests/`. Prefer digests over re-scraping Medium.

> A copy of this same skill also lives at `.claude/skills/agent-creation-orchestration/` in this repo, for project-level auto-load when working directly in DINetDigital.

## When this skill applies

- Designing a single agent or multi-agent system
- Choosing supervisor vs swarm vs hierarchy vs ensemble
- Adding memory, HITL, tools, or agentic RAG
- Hardening with guardrails / threat detection
- Defining eval loops and production layers

## Workflow (follow in order)

```
Progress:
- [ ] 1. Frame the job (outcome, tools, risk)
- [ ] 2. Pick topology
- [ ] 3. Define State + memory split
- [ ] 4. Context engineering budget
- [ ] 5. Build specialists → compose
- [ ] 6. Guardrails L1→L2→L3
- [ ] 7. Verification loop signal
- [ ] 8. Eval + observability
- [ ] 9. Production layers
```

### 1. Frame the job

Write one sentence: **who** · **artifact** · **tools allowed** · **what must never happen**.

If the task needs retrieval + tools + clarification, default to **agentic RAG graph** (digest 04), not plain chat RAG.

### 2. Pick topology

| Need | Topology | Digest |
|------|----------|--------|
| Route among specialists | Supervisor | 01 |
| Independent parallel tools | Parallel tool use | 07 |
| Manager → workers | Hierarchical teams | 07 |
| Quality via competition | Ensembles | 07 |
| Shared workspace | Blackboard | 07 |
| High volume stages | Assembly line | 07 |

Start simple: **two specialists + supervisor**, then add nodes.

### 3. State + memory

Define a typed `State` shared across nodes:

- `messages` (reducer-append)
- domain IDs / loaded memory
- `remaining_steps` (anti-loop)

Memory split (digest 06):

- **Short-term:** checkpointer / thread
- **Long-term:** store with `(namespace, key)` — InMemory → Postgres/pgvector in prod

Never dump all history into every prompt; **select** what enters context (digest 02).

### 4. Context engineering

Apply Write / Select / Compress / Isolate:

- Scratchpad or state fields for plans
- Retrieve only relevant memories/docs
- Summarize long threads; drop stale tool noise
- Isolate sub-agents to avoid context clash

Watch for poisoning, distraction, confusion, clash.

### 5. Build specialists → compose

1. Implement each specialist ReAct agent with clear tools
2. Unit-test with LangSmith traces
3. Compose under supervisor / planner
4. Add HITL before irreversible actions (trades, emails, deletes)

Agentic RAG node order (digest 04):

`Gatekeeper → Planner → ToolExecutor → Auditor → Strategist`

### 6. Guardrails (mandatory for prod)

| Layer | Checks |
|-------|--------|
| L1 Input | topical, PII/secrets, threat model (parallel) |
| L2 Plan | structured action plan; groundedness; policy; HITL escalate |
| L3 Output | hallucination, compliance, citations |

See digest 05. For tool-using agents with sensitive transcripts, plan on-box threat detection (digest 12).

### 7. Verification loop

Autonomy only if wired to a **real signal** (digest 15): tests, schema validation, retrieved facts, eval harness — not "ask the model if it did well."

Patterns: maker–checker, CI sweeper, PR babysitter, daily triage.

### 8. Eval + observability

- Trace every run (LangSmith or equivalent)
- Score tool correctness, groundedness, trajectory, cost/latency
- Keep regression cases (digest 08)

### 9. Production layers

Beyond the demo graph (digest 09): auth, sanitization, rate limits, pooling, resilience, secure secret handling. Separate **orchestration graph** from **training loop** if self-improving (digest 16).

## Default build template (LangGraph-shaped)

```text
START
  → input_guard (L1)
  → verify_or_clarify
  → load_memory
  → supervisor / planner
       ├─ specialist_a (tools)
       └─ specialist_b (tools)
  → auditor (optional re-plan)
  → output_guard (L3)
  → write_memory
END
(+ checkpointer, store, HITL interrupt before risky tools)
```

## Anti-patterns

- One mega-prompt instead of specialists + state
- No step budget → infinite tool loops
- Parallelizing dependent tool calls
- Shipping without L2 plan checks
- Evaluating only final text, ignoring trajectory
- Sending raw agent transcripts to third-party APIs for "security"

## Dig deeper

- Catalog: [INDEX.md](INDEX.md)
- Digests: [digests/](digests/)
- Patterns: [reference-patterns.md](reference-patterns.md)
- Checklists: [checklists.md](checklists.md)
