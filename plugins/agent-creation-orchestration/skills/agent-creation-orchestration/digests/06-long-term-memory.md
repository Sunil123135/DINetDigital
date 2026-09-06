# Digest 06 — Long-term memory in Agentic AI

**Source:** Fareed Khan · 2025-10-10  
**URL:** https://levelup.gitconnected.com/building-long-term-memory-in-agentic-ai-2941b0cca3bf  
**Repo:** https://github.com/FareedKhan-dev/langgraph-long-memory

## Two memory layers

| Layer | Scope | Mechanism |
|-------|-------|-----------|
| Thread / short-term | One conversation | Checkpoints (`MemorySaver` / `InMemorySaver`) |
| Cross-thread / long-term | Across sessions | Store with **namespace + key** (`InMemoryStore` → Postgres/pgvector in prod) |

## Store progression

1. In-memory (notebooks)  
2. `langgraph dev` local pickle persistence  
3. Production: Postgres + pgvector, cosine similarity  

## Pattern

- Namespace like `(user_id, "memories")`  
- `put` / `search` memories  
- Compile graph with `checkpointer=` + `store=`  
- HITL feedback loop writes corrected preferences  

## Skill mapping

→ Always design short vs long memory; never overload the prompt with everything.
