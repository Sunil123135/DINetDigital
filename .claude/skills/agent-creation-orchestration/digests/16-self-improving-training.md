# Digest 16 — Training architecture for self-improving agents

**Source:** Fareed Khan  
**URL:** https://medium.com/@fareedkhandev/building-a-training-architecture-for-self-improving-ai-agents-c87a4e316b22  
**Repo:** https://github.com/FareedKhan-dev/training-ai-agents

## Thesis

Prompts don’t self-optimize. Real improvement needs a **training architecture**: multi-agent roles, rewards, RL (SFT → PPO / bandits), observability, multi-phase loops.

## Bridge pattern

Wrap LangGraph in a trainable unit (`LitAgent` / Agent-Lightning style): `rollout` runs the graph, injects the model under training into selected nodes, scores with multi-criteria LLM-as-judge reward.

## Skill mapping

→ Separate orchestration graph from training loop; reward multi-criteria (feasibility, groundedness, impact).
