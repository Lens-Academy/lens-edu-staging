---
id: '5873f5f4-48fc-4928-a616-5758220e8f96'
parent-concepts:
  - "[[You don't get what you train for]]"
---
How training dynamics shape what a model learns: inductive biases, path dependence, value formation from context-specific drives, shard theory, and capability phase changes during training (grokking, induction heads). Not this: the selection framing of training (see The behavioral selection model).

## Relationships

### [[../Lenses/byrnes-sympathy-for-both-sides-of-the-egregious-misalignment-debate]]
Tier 2: Short claim: endless RLVR or continual learning needs a ground truth that dilutes pretrained niceness away. Two paragraphs in the final 'within-frame complaint at LLM people'; the mechanism (enough updating on an objective yields ruthless maximization) is asserted, with links to Foom & Doom rather than explained.

### [[../Lenses/ericjmichaud-on-neural-scaling-and-the-quanta-hypothesis]]
Tier 2: Worked examples of sharp phase changes in training: induction heads, grokking, palindromes, multitask sparse parity. Shows subtasks learned roughly in order of frequency and mean loss as an average of many discrete transitions. About when skills are learned, not about values; based on toy tasks plus Pythia per-token curves.
