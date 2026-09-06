# Digest 01 — Multi-Agent AI System (LangGraph + LangSmith)

**Source:** Fareed Khan · 2025-06-01  
**URL:** https://levelup.gitconnected.com/building-a-multi-agent-ai-system-with-langgraph-and-langsmith-6cb70487cd81

## Core thesis

Powerful agents are composed of smaller sub-agents. Hard parts: hallucinations, conversation flow, observability in testing, human-in-the-loop, and evaluation.

## Architecture pattern: Supervisor + specialists

Customer-support style graph:

1. `human_input` → account info  
2. `verify_info` → clarify intent  
3. `load_memory` → user preferences  
4. **Supervisor** routes to sub-agents (`music_catalog`, `invoice_info`)  
5. `create_memory` → persist new preferences  

## LangGraph primitives to copy

| Primitive | Role |
|-----------|------|
| `State` (TypedDict) | Shared snapshot: `customer_id`, `messages`, `loaded_memory`, `remaining_steps` |
| Tools | SQL/Chinook catalog + invoice queries |
| Nodes | Sub-agent ReAct loops |
| `MemorySaver` | Short-term / thread checkpoint |
| `InMemoryStore` | Long-term cross-thread prefs |
| LangSmith | Tracing, eval, debug |

## Orchestration lessons

- Build **one sub-agent at a time**, test, then compose under a supervisor.
- Compare **Swarm vs Supervisor** for routing.
- Add HITL before irreversible actions.
- Evaluate the multi-agent system, not only single prompts.

## Skill mapping

→ Supervisor topology, shared state schema, short/long memory split, LangSmith observability.
