# Digest 05 — Multi-layered Agentic Guardrails

**Source:** Fareed Khan · 2025-10-06  
**URL:** https://levelup.gitconnected.com/building-a-multi-layered-agentic-guardrail-pipeline-to-reduce-hallucinations-and-mitigate-risk-a8f73de24ea7  
**Repo:** https://github.com/FareedKhan-dev/agentic-guardrails

## Defense-in-depth

1. Build unguarded agent → watch catastrophic failure  
2. Layer defenses independently  

### Layer 1 — Input (async perimeter)

- Topical relevance  
- Sensitive data (PII / MNPI)  
- Threat/compliance (e.g. Llama-Guard)  
- Run in parallel with `asyncio`

### Layer 2 — Plan (inside the loop)

- Force structured **Action Plan** JSON before tools  
- Groundedness of reasoning vs history  
- Policy enforcement (AI-generated validators from plain-English policy)  
- HITL escalation for residual risk  

### Layer 3 — Output

- Hallucination check  
- Compliance sanitize  
- Citation verification  

## Ops notes

- Fast models for perimeter; powerful models for deep checks  
- Scorecard the full system after layering  
- Red-team and adaptive guardrails  

## Skill mapping

→ Mandatory 3-layer safety scaffold for any production agent.
