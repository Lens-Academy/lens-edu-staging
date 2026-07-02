---
id: 55ed8f7d-044d-41d1-8c31-a8e5818a33c2
title: "Conservative Assumptions in AI Control"
tldr: Control evaluations assume the AI is a perfectly coordinated adversary that knows your whole protocol. Obviously too pessimistic, so why do it, and when should assumptions be relaxed?
summary_for_tutor: "Covers Shlegeris's examination of the deliberately conservative assumptions in control evaluations (the AI knows the protocol, coordinates perfectly across instances, picks the optimal attack): why conservatism gives robust guarantees and simplifies evaluation, where it's too conservative (real schemers face uncertainty, coordination limits, exploration hacking constraints), and how relaxing specific assumptions could unlock cheaper safety measures."
---

#### Text
content::
(<30 min.) Control evaluations assume the AI is a perfectly coordinated adversary that knows your whole protocol. That's obviously too pessimistic, so why do it, and when should the assumption be relaxed?

#### Article
source:: [[../articles/shlegeris-thoughts-on-the-conservative-assumptions-in-ai-control]]

#### Text
content::
Control evals assume a perfectly coordinated adversary that already knows your whole protocol. Which of those assumptions would you relax first — and does relaxing it still leave you safe? Pick one and defend the call to the tutor.

#### Chat
instructions::
TLDR of what the user just read: Shlegeris examines the deliberately conservative assumptions in control evaluations (the AI knows the protocol, coordinates perfectly across instances, picks the optimal attack): why conservatism gives robust guarantees and simplifies evaluation, where it's too conservative (real schemers face uncertainty, coordination limits, and exploration hacking constraints), and how relaxing assumptions could unlock cheaper safety measures.

Discussion topics to explore:
- Which conservative assumption is most unrealistic for actual early schemers?
- What do we gain in evaluation tractability by assuming the worst, and what real safety measures does it wrongly devalue?
- How would the learner design an evaluation that relaxes one assumption without losing rigor?

Check they understand the difference between "the AI could in principle do X" and "a realistic schemer reliably does X."
