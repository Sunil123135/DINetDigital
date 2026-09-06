# Agent build checklists

## Creation checklist

- [ ] Outcome sentence written (user, artifact, forbidden actions)
- [ ] Topology chosen and justified
- [ ] Typed State with step budget
- [ ] Short-term + long-term memory plan
- [ ] Context budget (write/select/compress/isolate)
- [ ] Each specialist has ≤ 5 clear tools
- [ ] Supervisor/planner tested with traces
- [ ] HITL before irreversible tools

## Safety checklist

- [ ] L1 input guards (topic, PII, threat) parallelized
- [ ] L2 structured plan review + policy
- [ ] L3 output groundedness / citations
- [ ] Secrets never logged in traces
- [ ] Threat model for MCP/tool servers if applicable

## Reliability checklist

- [ ] External verification signal defined
- [ ] Maker–checker or equivalent for high-risk outputs
- [ ] Eval suite in LangSmith (or equal)
- [ ] Latency/cost logged per node
- [ ] Failure modes documented (timeouts, bad tools, ambiguity)

## Ship checklist

- [ ] Auth + rate limits
- [ ] Persistence store for prod memory
- [ ] Runbooks for stuck loops / escalations
- [ ] Regression prompts saved
