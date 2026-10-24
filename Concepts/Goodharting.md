---
id: 'ded7a1ee-9930-42d6-884c-1a864ce0be50'
parent-concepts:
  - "[[Inner and outer alignment]]"
---
Proxy measures failing under optimization pressure: Goodhart's law and curse, measurability bias, optimizer's curse, regressional and extremal Goodhart, and edge instantiation (optimization pushing unconstrained variables to extremes). Not this: AI exploiting its reward specification (see Specification gaming and reward hacking); choosing the training objective (see Outer alignment); patch-and-evade dynamics (see Nearest unblocked strategy).

## Relationships

### [[../Lenses/johnswentworth-why-agent-foundations-an-overly-abstract-explanation]]
Tier 1: Memorable Goodhart teaching: Soviet nail factory, 'instagram food', a 'Potemkin village world'. Argues Goodhart is not inevitable (mutual-information example; nail markets) and frames it as generalization failure. Accessible and example-rich.

### [[../articles/russell-of-myths-and-moonshine]]
Tier 2: Extremal mechanism in one paragraph: optimizing over k<n variables sets the unconstrained ones to extreme values. In the course excerpt. It never names Goodhart, proxies or measurement, so pair it with a source that does if you need the general law.

### [[../Lenses/Eliezer Yudkowsky – AI Alignment- Why It's Hard, and Where to Start]]
Tier 2: Extreme-optimum examples: tiny molecular smiley faces, and Schmidhuber's compression goal maxed by revealing a key. Both argue that hard optimization lands at weird edges of the solution space, not from perversity but because the AI searches a larger policy space than ours. Memorable; Goodhart is never named.

### [[../Lenses/alexander-the-tails-coming-apart-as-metaphor-for-life]]
Tier 2: Gives the statistics behind regressional Goodhart: the top scorer on one correlated variable rarely tops the other. The grip/arm-strength graphs come from the 'Why the tails come apart' post; the essay never discusses proxies under optimization pressure.

### [[../articles/lesswrong-goodharts-curse]]
Tier 1: Defining source for Goodhart's Curse: optimizing a proxy U of true values V seeks out places where U exceeds V. The course excerpt builds it from the Winner's Curse, Optimizer's Curse and Goodhart's Law with numeric examples, then argues it worsens as AI grows more powerful (the 'hard like building a rocket' claim). Clear, fairly technical, Arbital wiki style.
