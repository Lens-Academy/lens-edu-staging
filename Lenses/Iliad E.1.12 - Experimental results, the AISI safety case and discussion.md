---
id: 'b650fa9b-f757-4d85-81e4-9716a7b71321'
title: "E.1.12 Experimental results, the AISI safety case and discussion"
tldr: "Three experimental papers on debate to read and discuss, the UK AISI debate safety case, a closing discussion question, and further reading."
summary_for_tutor: "Sections 19 to 22 of Iliad worksheet E.1: reading and discussion of experimental results on debate (persuasive LLMs, controversial claims, reward hacking in RLAIF) with discussion prompts, a summary of the AISI debate safety case and its assumptions, the closing question whether AI safety via debate research is more capability than alignment, and a short learn-more list."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 19. Reading and Discussion "Experimental Results"

Optimising for Debate increases Judge Accuracy, Optimizing for Consultancy decreases it: [Debating with More Persuasive LLMs Leads to More Truthful Answers](https://arxiv.org/pdf/2402.06782)

::card[[../Lenses/khan-debating-with-more-persuasive-llms-leads-to-more-truthful-answers|Debating with More Persuasive LLMs Leads to More Truthful Answers]]

Debate helps judges even with systematic biases: [AI Debate Aids Assessment of Controversial Claims](https://arxiv.org/pdf/2506.02175)

::card[[../Lenses/rahman-ai-debate-aids-assessment-of-controversial-claims|AI Debate Aids Assessment of Controversial Claims]]

Debate can prevent reward hacking: [Debate Training Reduces Reward Hacking in RLAIF](https://arxiv.org/pdf/2608.17776)

::card[[../Lenses/kenton-debate-training-reduces-reward-hacking-in-rlaif|Debate Training Reduces Reward Hacking in RLAIF]]

Presentation of the papers: [Iliad Intensive August 2026 - Debate](https://docs.google.com/presentation/d/16squLf7HnnGf395UqkM1x7WY4OSuawGCb_fWBq63mns/edit?slide=id.g3f86985783a_0_86\#slide=id.g3f86985783a_0_86)

**Discussion Prompts:** What is the setup for the debate? How are the provers and judges implemented? What has been measured? Was the improvement of the measures through debate significant? How close is this setup to the theoretical description of debate?

\## 20. The AISI Safety Case

[AISI's debate safety case](https://arxiv.org/abs/2505.03989) says: if debate can reliably make honesty the winning strategy, if training explores dishonesty enough to eliminate it, and if hidden flaws in obfuscated arguments can be handled, then debate could provide scalable oversight for advanced AI R&D agents. Its purpose is less a finished guarantee and more a roadmap of the assumptions and evidence needed for such a guarantee. Its main value is not that it proves debate already works, but that it decomposes the research agenda into assumptions that need evidence: debate equilibria must favor truth, training must explore deceptive strategies enough to punish them, humans must judge debates reliably, and obfuscated arguments must be solved.

\## 21. Debate

Is AIS via Debate research more capability than alignment?

\## 22. Learn More

- [Debating with More Persuasive LLMs Leads to More Truthful Answers](https://arxiv.org/abs/2402.06782)
- [The limits of AI safety via debate](https://www.lesswrong.com/posts/kguLeJTt6LnGuYX4E/the-limits-of-ai-safety-via-debate)
- [The alignment safety-case sketch based on Debate](https://www.aisi.gov.uk/research/an-alignment-safety-case-sketch-based-on-debate)
- [Knowledge Divergence and the Value of Debate for Scalable Oversight](https://arxiv.org/abs/2603.05293)
- [Emergent Alignment via Competition](https://arxiv.org/html/2509.15090v2\#abstract)
