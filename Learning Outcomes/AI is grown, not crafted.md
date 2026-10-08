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
Score {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@according to--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@out of 100:++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@following rubric.
**1** — Believes engineers fully understand modern AI because they wrote the code --}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@sum of the three elements below.

The question asks what the distinction between "grown" and "crafted" AI is, ++}and {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@designed the training process. *Example: "Engineers--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@what an engineer does and does not++} know {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@everything --}about {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@how it works because they built it."*

**2** — Understands that AI learns--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@a trained AI model. Grade the ideas, in any wording. No analogy or term++} from {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@data rather than being programmed step-by-step, but cannot explain--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@the source is needed.

40: The distinction. Crafted systems: engineers write the rules or code that decide what++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@epistemic gap this creates. *Example: "AI learns on its own so it's more flexible than traditional software, but engineers still understand it pretty well."*

**3** — Correctly explains--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@system does, step by step. Grown systems: engineers write a training process (for example gradient descent adjusting billions of numbers on data) and the model's behavior comes out of++} that {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@gradient descent produces cognition through optimization rather than deliberate design, and names--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@optimization, not out of anyone's design.

30: What the engineer does know: how++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@key gap: engineers understand--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@model was produced, such as the architecture,++} the training {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@process but cannot read--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@procedure, the data and++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@resulting weights to predict behavior (the DNA analogy: readable but not interpretable). *Example: "Engineers designed the training process but not what--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@objective. Mentioning that they can also see every number (weight) in the model also counts here. One of these, stated clearly, earns++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@model learned. The weights are like a genome: you can read them but you can't tell from them--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@30.

30: What the engineer does not know: what the trained model has actually learned, how it works inside, or++} what {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@the system will do, any more than reading DNA tells you exactly what an organism will be like."*

**4** — As above, plus explains why this matters for safety: you can't verify what--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@it will do or want. The weights can be read but not understood well enough to predict its behavior. Knowing how it was made is not knowing what it is.

Cap at 30 if++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@system has learned or what goals it has developed. *Example: Adds "So even if--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@answer says engineers fully understand the trained model because they built it.

Model answer, for++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@training went exactly as planned, you still can't look inside and confirm--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@feedback, not a grading checklist: "Crafted software is written by people: an engineer decides++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@model has--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@rules and++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@values you wanted it to have."*

**5** — As above, plus articulates--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@program follows them. A modern AI is grown: engineers write++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@process-knowledge/cognition-knowledge distinction: understanding how a system was produced is not--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@training process, and gradient descent tunes billions of numbers until++} the {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@same as understanding what it is. *Example: "There are two kinds of understanding here. Engineers have process-knowledge: they--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@model does well on the data. Nobody chooses what those numbers end up encoding. So the engineers++} know {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@exactly how--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@the recipe, the architecture, the data,++} the training {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@works. But--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@method, and++} they {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@lack cognition-knowledge:--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@can even look at every number in the model. What++} they don't know {++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@is what those numbers mean: ++}what the model {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@actually represents--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@has learned, how it reasons, what it will do in a new situation++} or {++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@what it ++}wants. {--{"author":"James agent ready-41's AI","timestamp":1791466645469}@@Confusing these two is the mistake that makes people overconfident about AI safety."*--}{++{"author":"James agent ready-41's AI","timestamp":1791466645469}@@It's like a genome: you can read every letter and still not know what the organism will be like."++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said engineers understand the model because they built it, ask what an engineer could find out by reading the trained weights directly.
- If they said the AI learns from data but not what that leaves unknown, ask what an engineer knows about a model once training is done, and what they cannot tell from it.
- If they said what engineers know but not clearly what they don't, ask whether knowing the training recipe tells you what the model wants.
- If they named the gap (the training process is understood, the resulting behavior cannot be read off the weights), a good follow-up is what this means for checking whether the model ended up with the goals they wanted.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the genome comparison. A genome can be read letter by letter, yet reading it does not tell you what the organism will be like. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
