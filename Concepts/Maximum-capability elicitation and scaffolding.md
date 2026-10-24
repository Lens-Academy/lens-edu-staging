---
id: 'acba2706-84bf-42b6-a9b9-4009e222a89c'
parent-concepts:
  - "[[Capability evaluations]]"
---
Making sure evals measure a model's full ability: fine-tuning, scaffolding, sandbagging resistance. Not this: agent scaffolds as product capability (see Agents, tools, scaffolding, and autonomy).

## Relationships

### [[../articles/hobbhahn+etal-a-starter-guide-for-evals]]
Tier 2: Full guide's 'LLM steering' section covers eliciting capability by prompting, jailbreaks, SFT, RL fine-tuning and scaffolds. It says why: a malicious actor or misaligned model would fine-tune rather than just prompt, so evaluators should do controlled gain-of-function work. A practical skill list, with 2024-era tool links.

### [[../Lenses/We Need A Science of Evals]]
Tier 2: Shows upper-bound capability estimates are fragile: new prompting methods keep raising state-of-the-art scores. Examples: chain-of-thought and related prompting, Gemini Ultra versus GPT-4 on MMLU, then Medprompt days later. Concrete and well cited, though 2023-24 models.

### [[../articles/barnett+thiergart-what-ai-evaluations-for-preventing-catastrophic-risks-can-and-cannot-do]]
Tier 2: Under-elicitation case: new scaffolding took GPT-4 Turbo from 5% to 71% of buffer-overflow exploits (100% with retries). Section 3.1 also covers in-context learning of missing component skills; strong concrete material for why a failed eval proves little.

### [[../articles/gillen+barnett-without-fundamental-advances,-misalignment-and-catastrophe-are-the-default-outcomes-of-training-powerful-ai]]
Tier 2: Full report argues fine-tuning to elicit dangerous capabilities may give almost no evidence either way. A model can hide skills that need extra reasoning, and fine-tuning may itself create the skill; it also covers eliciting useful research capabilities.

### [[../articles/janus-simulators]]
Tier 2: Full text argues prompt-based benchmarks systematically underestimate GPT, because its capability is prompt-contingent. The 'Oracle GPT' section says no downstream benchmark is expected to probe the model's upper limits, citing the 'simulate a supersmart version of itself' anecdote and prompt-programming gains. Dated (GPT-3 era) but the argument still applies; not in the course excerpt.
