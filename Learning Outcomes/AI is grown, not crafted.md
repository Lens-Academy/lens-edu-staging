---
id: 626f8d04-2a11-479b-8761-a8705b4231a5
learning-outcome: "Explain how AI produced through gradient descent differs from engineered systems, and why understanding the training process does not mean understanding what the trained model is or does."
reading-from: "Scene: A man and a woman are sitting in a restaurant in daytime."
reading-to: "Machine minds are subjected to different constraints, and grown under different pressures, than those that shape biological organisms; and although they're trained to predict human writing, the thinking inside an AI runs on a radically different architecture from a human's."
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Artificial Intelligence]]"
stage: beginner
eval-results:
  content-sha: 98360650
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question opens by referencing the assigned chapter, so a reader who never read that text cannot parse the framing.", C3: "Level-3 pass bar embeds the DNA analogy as part of the required explanation, and 'cannot read the resulting weights' is not literally true as written."}
  evidence: {B1: "Chapter 2 draws a sharp contrast between AI systems that are \"grown\" and systems that are \"crafted.\"", C3: "cannot read the resulting weights to predict behavior (the DNA analogy: readable but not interpretable)"}
---

## Test:
id:: 01dd1801-36f3-4a83-b7e7-33eed08ba1b0

#### {--{"author":"Elias's AI","timestamp":1787667277151}@@Question--}{++{"author":"Elias's AI","timestamp":1787667277151}@@Question: Open
id:: acaae83b-8a5c-49ba-9d7f-594e1bdc77b9++}
content:: {--{"author":"Luc's AI","timestamp":1787659262473}@@Modern AI systems are sometimes described as "grown" rather than "crafted": the engineers write the training procedure, but the resulting system's capabilities emerge from --}{++{"author":"Luc's AI","timestamp":1787659262473}@@Chapter 2 draws a sharp contrast between AI systems that are "grown" and systems ++}that{--{"author":"Luc's AI","timestamp":1787659262473}@@ process rather than being deliberately designed component by component.--}{++{"author":"Luc's AI","timestamp":1787659262473}@@ are "crafted."++}

What is that {--{"author":"Luc's AI","timestamp":1787659263093}@@distinction, and why does it apply to a model produced by training a neural network with gradient descent?--}{++{"author":"Luc's AI","timestamp":1787659263093}@@distinction?++} And specifically: what does an engineer know about a trained AI model, and what do they not know?

assessment-instructions::
Score according to the following rubric.
**1** — Believes engineers fully understand modern AI because they wrote the code and designed the training process. *Example: "Engineers know everything about how it works because they built it."*

**2** — Understands that AI learns from data rather than being programmed step-by-step, but cannot explain the epistemic gap this creates. *Example: "AI learns on its own so it's more flexible than traditional software, but engineers still understand it pretty well."*

**3** — Correctly explains that gradient descent produces cognition through optimization rather than deliberate design, and names the key gap: engineers understand {--{"author":"Luc's AI","timestamp":1787659263609}@@and control --}the training {--{"author":"Luc's AI","timestamp":1787659263609}@@process,--}{++{"author":"Luc's AI","timestamp":1787659263609}@@process++} but{--{"author":"Luc's AI","timestamp":1787659263609}@@ the trained weights, though fully inspectable as numbers,--} cannot {--{"author":"Luc's AI","timestamp":1787659263609}@@be interpreted well enough--}{++{"author":"Luc's AI","timestamp":1787659263609}@@read the resulting weights++} to predict {--{"author":"Luc's AI","timestamp":1787659263609}@@what the model will do. Grade the idea,--}{++{"author":"Luc's AI","timestamp":1787659263609}@@behavior (the DNA analogy: readable but++} not{--{"author":"Luc's AI","timestamp":1787659263609}@@ the wording: any phrasing of this gap passes, and an analogy (e.g. a genome that can be read base by base without telling you what the organism will be like) is one acceptable route, not a requirement.--}{++{"author":"Luc's AI","timestamp":1787659263609}@@ interpretable).++} *Example: "Engineers designed the training process but not what the model learned. The weights are like a genome: you can read them but you can't tell from them what the system will do, any more than reading DNA tells you exactly what an organism will be like."*

**4** — As above, plus explains why this matters for safety: you can't verify what the system has learned or what goals it has developed. *Example: Adds "So even if the training went exactly as planned, you still can't look inside and confirm the model has the values you wanted it to have."*

**5** — As above, plus articulates the process-knowledge/cognition-knowledge distinction: understanding how a system was produced is not the same as understanding what it is. *Example: "There are two kinds of understanding here. Engineers have process-knowledge: they know exactly how the training works. But they lack cognition-knowledge: they don't know what the model actually represents or wants. Confusing these two is the mistake that makes people overconfident about AI safety."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
