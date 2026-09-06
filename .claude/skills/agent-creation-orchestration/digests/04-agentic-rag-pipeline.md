# Digest 04 — Advanced Agentic RAG (human thought process)

**Source:** Fareed Khan · 2025-09-16  
**URL:** https://levelup.gitconnected.com/building-an-advanced-agentic-rag-pipeline-that-mimics-a-human-thought-process-687e1fd79f61  
**Repo:** https://github.com/FareedKhan-dev/agentic-rag

## Cognitive roles (orchestration blueprint)

| Role | Job |
|------|-----|
| Librarian | Document RAG |
| Analyst | SQL / structured data |
| Scout | Live web |
| Gatekeeper | Ambiguity check before acting |
| Planner | Multi-tool plan |
| Auditor | Grade tool outputs; re-plan |
| Strategist | Synthesize + causal inference |
| Red Team | Adversarial stress tests |

## Phase map

1. Knowledge core (structure-aware parse, metadata enrichment, vector + relational stores)  
2. Specialist tools/agents  
3. Master graph: Gatekeeper → Planner → Tools → Auditor → Strategist  
4. Evaluation cortex (retrieval quality, LLM-as-judge, cost/latency)  
5. Red teaming  

## Design rules

- Don’t answer vague questions — clarify first.
- Plan tool calls; don’t rush a single retrieve+generate.
- Self-correct when evidence is weak.
- Evolve with cognitive memory, watchtower, multimodal later.

## Skill mapping

→ Agentic RAG graph, specialist tools, gatekeeper/planner/auditor loop.
