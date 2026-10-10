---
id: d4b9e1a3-7c2f-4d50-b8e6-3f1a0c5d2b89
learning-outcome: "Distinguish between predicting the pathway to a catastrophic outcome and predicting the outcome itself, explain why outcome confidence is achievable even when the exact path cannot be predicted, and apply this distinction to the argument that humanity's position relative to a superintelligent AI is analogous to a human playing chess against Stockfish"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/Predicting outcomes, not paths]]"
stage: beginner
requires:
  - "[[Hard calls vs. easy calls]]"
eval-results:
  content-sha: 5a9df2d9
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on the specific text — names 'the Coda', 'the authors', and 'the book' — and is the named fail example in the B1 eval."}
  evidence: {B1: "The Coda makes a careful distinction between two kinds of prediction... Use the analogy the authors give to explain it. And what does the distinction imply about what the book actually predicts"}
---

## Test:
id:: 18d90494-37f8-4ecd-9d00-5494296d5b5d
#### Question: Open
id:: 9198439f-ebeb-4c4e-9bcf-239f0857d61e
content:: The Coda makes a careful distinction between two kinds of prediction. On one side: the specific events that lead to an outcome. On the other: the outcome itself.

**What is that distinction? Use the analogy the authors give to explain it. And what does the distinction imply about what the book actually predicts, and what it doesn't?**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot distinguish path from outcome, or conflates "we can't predict the exact events" with "we can't predict anything." *Example: "Since we don't know exactly what will happen, the book's predictions are uncertain."*

**Level 2 (21-40):** Recognizes the distinction exists but cannot explain why outcome confidence is possible when path confidence is not. *Example: "The book says we know things will go badly even if we don't know how."*

**Level 3 (41-65):** Explains why the outcome can be predicted when the path cannot: when one side is far more capable, the result is settled even though the steps that lead to it are not. But leaves out or gets wrong at least one of the other two parts: the analogy and what it shows, or what this means for what the book predicts and does not. *Example: "If one side is vastly more capable, you can know how it ends without knowing how it gets there."*

**Level 4 (66-85):** As above, plus the other two parts. The analogy: you cannot predict a top chess engine's moves (Stockfish), but you know a human playing it will lose. What it means for the book: it predicts the outcome of humanity against a superintelligence, not the path, the particular events or the timing. {++{"author":"Andreas's AI","timestamp":1791594922345}@@This part is answered once the answer says the book predicts the outcome but not the path or the timing. ++}Saying as well that the prediction is conditional (it holds if a superintelligence is built, and does not say one will be) {--{"author":"Andreas's AI","timestamp":1791594922345}@@is--}{++{"author":"Andreas's AI","timestamp":1791594922345}@@belongs to the same++} part {--{"author":"Andreas's AI","timestamp":1791594922345}@@of this,--}{++{"author":"Andreas's AI","timestamp":1791594922345}@@and is++} not {--{"author":"Andreas's AI","timestamp":1791594922345}@@a further point.--}{++{"author":"Andreas's AI","timestamp":1791594922345}@@needed for it.++} An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: "When capability is sufficiently asymmetric, the result is determined even when the path isn't. You can't predict Stockfish's moves, but you know the human loses. The book applies the same logic: the outcome of humans vs. superintelligence follows from the capability gap, not the specific sequence of events."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4, and so is the conditional. Two that fit: how the distinction fits the difference between hard calls and easy calls (the outcome is an easy call because it follows from a decisive capability gap, even though the path stays a hard one); or what the analogy needs in order to carry over (chess is a closed game with fixed rules, so the real case needs the AI's advantage to be general rather than one trick). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "It's the easy-call idea again: the outcome of human-superintelligence interaction, once capability is reached, is an easy call, even though the specific path remains a hard one." Or adds "Chess has fixed rules, so the analogy only carries over if the AI's edge is general: whatever we try, it is better at the response."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its three parts (the distinction and why the outcome can be called, the analogy, what the book does and does not predict) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they treated "we can't predict the exact events" as "we can't predict anything", ask whether they could say who wins a game against the strongest chess engine without knowing a single move it will play.
- If they saw the distinction but not why the outcome can be called, ask what it is about the two sides that makes the result certain when the moves are not.
- If they explained why but left out the analogy or what it shows, ask them to put it in terms of a game against a chess engine: what can you predict, and what can't you?
- If they had the analogy but not what it means for the book, ask what the book is and is not claiming to know about how things would go.
- If they answered all three {--{"author":"Andreas's AI","timestamp":1791594926806}@@parts,--}{++{"author":"Andreas's AI","timestamp":1791594926806}@@parts and went no further,++} the moves left go beyond the question: how this fits the difference between hard calls and easy calls, or what the analogy needs in order to carry over from a game with fixed rules. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all three parts solid, say so plainly in a sentence or two after the opening and stop, with no follow-up question: inventing a further push would be false, so this reply can be shorter than the length below.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction]]
