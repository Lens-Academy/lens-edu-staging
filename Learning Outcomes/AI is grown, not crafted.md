---
id: 626f8d04-2a11-479b-8761-a8705b4231a5
learning-outcome: "Explain how AI produced through gradient descent differs from engineered systems, and why understanding the training process does not mean understanding what the trained model is or does."
reading-from: "Scene: A man and a woman are sitting in a restaurant in daytime."
reading-to: "Machine minds are subjected to different constraints, and grown under different pressures, than those that shape biological organisms; and although they're trained to predict human writing, the thinking inside an AI runs on a radically different architecture from a human's."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/1 Artificial Intelligence/Grown, not crafted]]"
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
Score according to the following rubric.
**1** — Believes engineers fully understand modern AI because they wrote the code and designed the training process. *Example: "Engineers know everything about how it works because they built it."*

**2** — Understands that AI learns from data rather than being programmed step-by-step, but cannot explain the epistemic gap this creates. *Example: "AI learns on its own so it's more flexible than traditional software, but engineers still understand it pretty well."*

**3** — Correctly explains that gradient descent produces cognition through optimization rather than deliberate design, and names the key gap: engineers understand the training process but cannot read the resulting weights to predict behavior (the DNA analogy: readable but not interpretable). *Example: "Engineers designed the training process but not what the model learned. The weights are like a genome: you can read them but you can't tell from them what the system will do, any more than reading DNA tells you exactly what an organism will be like."*

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
