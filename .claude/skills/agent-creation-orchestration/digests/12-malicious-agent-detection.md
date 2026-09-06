# Digest 12 — Catching malicious AI agents

**Source:** Fareed Khan · 2026-08-12  
**URL:** https://levelup.gitconnected.com/catching-malicious-ai-agents-using-a-multi-layered-detection-system-f2b068443bd7  
**Repo:** https://github.com/FareedKhan-dev/agentic-threat-detection

## Thesis

Security tools see final actions; **intent lives in the transcript** (prompt, reasoning, tool calls). Detect from transcripts on **open weights on-box** — never ship raw telemetry to third-party APIs.

## Architecture

- **Dredge:** collect/normalize events; scrub secrets  
- **Gauntlet:** attacks in MCP servers, not prompts  
- **Sifter:** cheap high-recall triage (never convicts)  
- **Inspector:** MoE deep agent with MCP tools  
- **SourceLens / ThreatLens / PolicyLens** evidence providers  

## Skill mapping

→ Threat model for tool-using agents; two-tier detection; on-prem open weights for sensitive transcripts.
