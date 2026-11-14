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
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Holds that engineers understand modern AI because they wrote the code and designed the training, or cannot say what the distinction is. *Example: "They built it, so of course they know how it works."*

**Level 2 (21-40):** Gives one of the three parts, usually the distinction alone (AI learns from data instead of being programmed step by step), without what the engineers know and do not know. *Example: "Normal programs follow rules someone wrote, but AI picks things up from data, which makes it more flexible."*

**Level 3 (41-65):** Gives two of the three parts: the distinction, what the engineers know, and what they do not know. *Example: "Ordinary software is written rule by rule; an AI is trained on data until it gets good at the task. The engineers know the training setup and the data they used."*

**Level 4 (66-85):** All three. The distinction: this part is answered once the answer says that crafted systems are built by people writing out what the system does, while a grown AI comes out of a training process that keeps adjusting the model's internal numbers until it performs well, so no one writes what it ends up doing. What the engineers know: this part is answered once the answer says they know the training process they designed. What they do not know: this part is answered once the answer says they do not know what the model learned from that process: how it works inside, what it will do in situations it was not tested on, or what it wants. An answer that says only that the model is a "black box" or "not fully understood", without what it is the engineers do not know, reaches this level but not fully. So does one that says the engineers cannot see inside the model at all: they can look at every one of its numbers; what they cannot do is tell from them what the model does. Saying as well that the engineers can see every number, that the numbers are too many and were found by the training rather than written by anyone, the comparison with reading a genome, or the name of the training method (gradient descent), belongs to the same parts and is not needed for them. An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Nobody wrote how it answers a question, so knowing the recipe doesn't tell you what's going on inside or what it'll do with something new."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Two that fit: what the gap means for safety (no one can check whether training gave the model the goals that were intended, even when the training went exactly as planned; saying only that the engineers do not know what it wants is level 4); or what the comparison with evolution shows and where it stops (a process that only rewards results can build something capable that nobody understands, but AI is grown under different pressures from living things, so what we know about human minds does not carry over; saying only that training is like evolution does not by itself make an extension). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Example: Adds "So a lab can run a flawless training run and still have no way to confirm the model cares about what they hoped it would."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its three parts (the distinction, what the engineers know, and what they do not know) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they said engineers understand the model because they built it, ask what an engineer could find out by reading the trained model's numbers directly.
- If they said only that AI learns from data instead of being programmed, ask what an engineer knows about a model once training is done, and what they cannot tell from it.
- If they said the engineers cannot see inside the model at all, ask what the engineers would find if they opened it up and looked at every number, and what those numbers would tell them.
- If they said only that the model is a black box or not fully understood, ask what exactly the engineers cannot tell about it.
- If they left out what the engineers do know, ask which part of the model's making the engineers are fully in charge of.
- If they answered all three parts and went no further, the moves left go beyond the question: what the gap means for checking whether the model ended up with the goals that were intended, or what the comparison with evolution shows and where it stops. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all three parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the genome comparison. A genome can be read letter by letter, yet reading it does not tell you what the organism will be like. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted - PQ]]

## Lens:
source:: [[../Lenses/IABIED - AI Is Grown, Not Crafted]]
