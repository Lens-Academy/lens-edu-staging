---
id: 626f8d04-2a11-479b-8761-a8705b4231a5
learning-outcome: "Explain how AI produced through gradient descent differs from engineered systems, and why understanding the training process does not mean understanding what the trained model is or does."
reading-from: "Scene: A man and a woman are sitting in a restaurant in daytime."
reading-to: "Machine minds are subjected to different constraints, and grown under different pressures, than those that shape biological organisms; and although they're trained to predict human writing, the thinking inside an AI runs on a radically different architecture from a human's."
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/Grown, not crafted]]"
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

#### Question: Open
id:: b0d29102-aee5-4db4-859c-dd3f51a1a746
content:: Chapter 2 draws a sharp contrast between AI systems that are "grown" and systems that are "crafted."

What is that distinction? And specifically: what does an engineer know about a trained AI model, and what do they not know?

assessment-instructions::
Score {--{"author":"Andreas's AI","timestamp":1794632063500}@@according to--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@out of 100. Pick++} the {--{"author":"Andreas's AI","timestamp":1794632063500}@@following rubric.
**1** — Believes engineers --}{++{"author":"Andreas's AI","timestamp":1794632063500}@@level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer ++}fully {++{"author":"Andreas's AI","timestamp":1794632063500}@@reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Holds that engineers ++}understand modern AI because they wrote the code and designed the {--{"author":"Andreas's AI","timestamp":1794632063500}@@training process.--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@training, or cannot say what the distinction is.++} *Example: {--{"author":"Andreas's AI","timestamp":1794632063500}@@"Engineers know everything about--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@"They built it, so of course they know++} how it {--{"author":"Andreas's AI","timestamp":1794632063500}@@works because they built it."*

**2** — Understands that AI--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@works."*

**Level 2 (21-40):** Gives one of the three parts, usually the distinction alone (AI++} learns from data {--{"author":"Andreas's AI","timestamp":1794632063500}@@rather than--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@instead of++} being programmed {--{"author":"Andreas's AI","timestamp":1794632063500}@@step-by-step, but cannot explain--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@step by step), without what++} the {--{"author":"Andreas's AI","timestamp":1794632063500}@@epistemic gap this creates.--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@engineers know and do not know.++} *Example: {--{"author":"Andreas's AI","timestamp":1794632063500}@@"AI learns on its own so it's more flexible than traditional software, but engineers still understand--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@"Normal programs follow rules someone wrote, but AI picks things up from data, which makes++} it {--{"author":"Andreas's AI","timestamp":1794632063500}@@pretty well."*--}{++{"author":"Andreas's AI","timestamp":1794632063500}@@more flexible."*++}

{--{"author":"Andreas's AI","timestamp":1794632066300}@@**3** — Correctly explains that gradient descent produces cognition through optimization rather than deliberate design, and names--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@**Level 3 (41-65):** Gives two of++} the {--{"author":"Andreas's AI","timestamp":1794632066300}@@key gap: engineers understand--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@three parts:++} the{--{"author":"Andreas's AI","timestamp":1794632066300}@@ training process but cannot read--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@ distinction, what++} the {--{"author":"Andreas's AI","timestamp":1794632066300}@@resulting weights to predict behavior (the DNA analogy: readable but--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@engineers know, and what they do++} not {--{"author":"Andreas's AI","timestamp":1794632066300}@@interpretable).--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@know.++} *Example: {--{"author":"Andreas's AI","timestamp":1794632066300}@@"Engineers designed the training process but not what the model learned. The weights are like a genome: you can read them but you can't tell from them what--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@"Ordinary software is written rule by rule; an AI is trained on data until it gets good at the task. The engineers know the training setup and++} the{--{"author":"Andreas's AI","timestamp":1794632066300}@@ system will do, any more than reading DNA tells you exactly what an organism will be like."*--}{++{"author":"Andreas's AI","timestamp":1794632066300}@@ data they used."*++}

**4** — As above, plus explains why this matters for safety: you can't verify what the system has learned or what goals it has developed. *Example: Adds "So even if the training went exactly as planned, you still can't look inside and confirm the model has the values you wanted it to have."*

**5** — As above, plus articulates the process-knowledge/cognition-knowledge distinction: understanding how a system was produced is not the same as understanding what it is. *Example: "There are two kinds of understanding here. Engineers have process-knowledge: they know exactly how the training works. But they lack cognition-knowledge: they don't know what the model actually represents or wants. Confusing these two is the mistake that makes people overconfident about AI safety."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said engineers understand the model because they built it, ask what an engineer could find out by reading the trained weights directly.
- If they said the AI learns from data but not what that leaves unknown, ask what an engineer knows about a model once training is done, and what they cannot tell from it.
- If they named the gap (the training process is understood, the resulting behavior cannot be read off the weights) but stopped there, ask what this means for checking whether the model ended up with the goals they wanted.
- If they covered that too, the step left is that knowing how something was produced is a different kind of knowledge from knowing what it is. Ask whether knowing the training recipe tells you what the model wants.

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the genome comparison. A genome can be read letter by letter, yet reading it does not tell you what the organism will be like. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
