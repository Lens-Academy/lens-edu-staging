{++{"author":"Elias's AI","timestamp":1785221464817}@@---
id: 'fb3aecd2-ea21-4237-99b3-3b3c89e367e8'
title: "Verifying International Agreements on AI: Six Layers"
tldr: "Six largely independent layers, deliberately redundant. The design principle is that no single layer has to be the one that works."
summary_for_tutor: "Baker, Kulp, Marks, Brundage and Heim (RAND, 2025) — the first of two state-of-play readings. Asks whether even the US and China could verify each other's compliance with guardrails on large-scale AI development and deployment, and answers that nations could eventually verify compliance via six largely independent approaches, spanning built-in security features in AI chips, separate monitoring devices attached to chips, and personnel-based mechanisms such as whistleblower programmes. The architecturally important idea is REDUNDANCY: layers are chosen to be largely independent so that the failure or evasion of one does not compromise the whole — the same insight the learner met as 'layering classes' in Wasil, now formalised as a design principle. Also stresses that technical research and protections against overreach are both needed, introducing the theme that a verification regime is itself an instrument requiring limits. Excerpt covers the Summary and Introduction (including the paper's own limitations); the detailed mechanism-by-mechanism treatment and open problems remain collapsed."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Module 1 gave you mechanisms and evasions. This module asks the practical question: *what could actually be verified today, and what is still a research programme?*

Two reports answer it. Start with this one — the RAND working paper, which frames the question in the hardest possible terms: could the US and China verify **each other**? Not allies. Not a company and its regulator. Two rivals who assume the worst.

Their answer is six largely independent approaches. Watch the word *independent* — it is doing real work. This is Wasil's "layer the classes" insight promoted into a design principle: choose your layers so that the failure of any one does not take the others down with it.

Also note the second half of their conclusion, which is easy to skim past: alongside technical research, they call for **protections against overreach.** A verification regime is itself a powerful instrument.

**Read from the beginning and stop when you reach:**

> The verification mechanisms and layers we identify are not necessarily comprehensive, nor is our analysis of them.

That covers the summary and the introduction, including their own account of what they left out. The layer-by-layer detail continues below.

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
to:: "The verification mechanisms and layers we identify are not necessarily comprehensive, nor is our analysis of them."

#### Text
content::
One thing to fix before moving on: why does *independence* between layers matter more than the strength of any individual layer?

#### Chat
instructions::
TLDR of what the learner just read:
Baker, Kulp, Marks, Brundage and Heim (RAND working paper, 2025), "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment". Framing question: to address risks from advanced AI, even the United States and China may need to agree on guardrails — but could they verify each other's compliance? Finding: nations could eventually verify compliance via six largely independent approaches, providing redundancy, spanning built-in security features in AI chips, separate monitoring devices attached to AI chips, and personnel-based mechanisms such as whistleblower programmes. Presents new conceptual frameworks, detailed implementation options, and key R&D challenges for overseeing large-scale AI development involving thousands of high-end chips. Caveats that the approaches are promising but require further development and, importantly, protections against overreach. The report is roughly 80-110 pages, drawing on literature review, expert interviews, and original analysis, and states its own limitations: the mechanisms and layers identified are not necessarily comprehensive.

The learning outcome this serves: assess what is verifiable today, and why data-centre-based development is the tractable case.

Discussion topics to explore:
- The core design idea, and the thing to make them articulate: **independence beats individual strength.** If layers share a failure mode, stacking them buys little; if they are genuinely independent, an adversary must defeat all of them, and the probability of doing that undetected falls multiplicatively. Ask them to compare two layers that share an assumption (both relying on on-chip mechanisms) with two that do not (an on-chip mechanism plus a whistleblower programme), and say which pair is worth more.
- Personnel-based mechanisms are the layer technical readers tend to dismiss. Ask why a whistleblower programme is genuinely independent of every hardware measure — it fails to different things entirely — and what that implies about a regime built only from clever devices.
- "Even the United States and China": ask why framing verification between rivals rather than between a regulator and a firm changes the design. Consent, intrusiveness, and espionage risk all become first-order constraints.
- **Protections against overreach.** This is the reading's quiet second theme and worth real time. A regime capable of establishing what a data centre computed is also a surveillance capability. Ask what limits would make it acceptable to the party being verified, and connect to why privacy-preserving mechanisms are load-bearing rather than decorative.
- "Could eventually verify" — ask what work "eventually" is doing, and which of the six layers they would expect to be available soonest.
- If they want to rank the layers by strength, gently redirect: the paper's point is that ranking is the wrong operation on a redundant system.

Check that they can explain why independence between layers is the property that matters. Then send them to the Oxford report, which asks the same question with pessimistic assumptions and reaches a sharper conclusion about which agreements are verifiable.
++}