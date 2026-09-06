# Digest 02 — Contextual Engineering for Agents

**Source:** Fareed Khan · 2025-07-25  
**URL:** https://levelup.gitconnected.com/optimizing-langchain-ai-agents-with-contextual-engineering-0914d84601f3

## Core thesis

Shift from prompt engineering → **context engineering**: what enters the model’s limited “RAM” (context window).

## Context types

- Instructions (prompts, examples, tool descriptions)
- Knowledge (facts, retrieved docs, memories)
- Tools (results / feedback from tool calls)

## Failure modes (Breunig)

Context poisoning · distraction · confusion · clash

## Four strategies (Write / Select / Compress / Isolate)

| Strategy | Agent technique |
|----------|-----------------|
| Write | Scratchpad / state fields / plan persistence |
| Select | Retrieve only relevant memories & tools |
| Compress | Summarize long threads; drop stale tool noise |
| Isolate | Sub-agents with separate state; sandboxes |

## LangGraph moves

- StateGraph as shared scratchpad between nodes
- Checkpointing = short-term scratchpad across turns
- Long-term store for cross-thread files/profiles
- BigTool calling + RAG under contextual policies
- Sub-agent isolation to prevent context clash

## Skill mapping

→ Context budget, scratchpad, isolation boundaries, compression triggers.
