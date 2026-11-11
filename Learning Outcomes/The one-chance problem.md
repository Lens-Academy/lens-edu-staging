---
id: 057e2d7c-1364-4436-a5d6-4d4799f31a0a
learning-outcome: "Explain what the Chernobyl and Titanic analogies get right (humans struggle to believe in unthinkable disasters), and identify the critical disanalogy between those historical cases and an ASI failure that the chapter treats as decisive."
reading-from: "beginning of chapter"
reading-to: "With ASI, there is no second time."
authors:
  - Chris+Claude
concept: "[[../Concepts/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: f0502c15
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to what Chapter 12 says and treats as decisive, not to a source-independent concept.", B1: "Question makes the chapter load-bearing scaffolding rather than self-containing its context."}
  evidence: {A2: "as Chapter 12 deploys them", B1: "Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world."}
---

## Test:
id:: 7f627b30-5641-48ef-901d-e710813fb828
#### Question: Open
id:: 4fc0ef19-14a5-44cd-96e0-e8d3c6a99f38
content:: Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world. To make the denial pattern concrete, it draws on two historical disasters: the Chernobyl meltdown and the Titanic sinking. Even when the warning signs are present, both cases show how humans fail to believe that unthinkable disasters can actually happen. The chapter then makes a pivot: it argues these analogies hold only up to a point, because there is one critical way in which an ASI failure differs from both of them.

**A friend says: 'People said the same about Chernobyl and the Titanic, and we learned and got safer, so AI will go the same way.' Which part of that comparison holds, and which part breaks for ASI? Explain why the part that breaks matters so much for how much proof of safety we should demand before building.**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Accepts the friend's comparison, or rejects it without saying which part breaks. Taking "we learned and got safer" as the part that holds is this level. *Example: "Your friend is right, we always learn from disasters."*

**Level 2 (21-40):** Names only one side: what holds (people denied the danger) or that ASI is different, but not that the difference is having no second chance. Saying only that AI is more dangerous, or that the disaster would be bigger, is this level: a bigger disaster that people survive can still be learned from. *Example: "People were in denial about Chernobyl and the Titanic too. AI is just more dangerous."*

**Level 3 (41-65):** Says what holds (in both cases people did not believe the disaster could happen, even when warned) and what breaks (after those disasters there were people left to investigate and reform; with ASI there is no second time, so a failure cannot be learned from). At this level the answer does not say why that matters for how much proof of safety to demand. *Example: "People refused to believe both disasters could happen, and that part fits AI too. What doesn't fit is that we got to learn from those. With ASI there's no second time."*

**Level 4 (66-85):** As above, plus why the part that breaks matters for how much proof to demand. This part is answered once the answer ties the two: because a failure cannot be learned from, safety has to be shown before building rather than learned afterwards, which asks for far more proof than a technology that can be fixed after it fails. An answer that says only that we should be "more careful" or "very cautious" reaches this level but not fully. Saying as well what reforms followed each disaster, or naming the people the chapter draws on, belongs to the same parts and is not needed for them. An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Since nothing can be learned from the first failure, being safe has to be shown up front, not found out afterwards."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: how the two halves combine (the denial the analogies show is exactly what would stop people from demanding that proof; saying only that people are in denial is level 4); why the one attempt is likely to fail (once it is out of reach it cannot be fixed, and the difficulties it faces stack on each other; saying only that there is no second chance is level 4); or why that proof is not available now (proof before building would need an account of why the system is safe, and test results only show what has happened so far). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "There's no fixing it once it's beyond our reach, and the attempt runs into problems that make each other worse." Or adds "Proof up front would need an account of why it's safe, and nobody has one; passing tests only tells you what has happened so far."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its three parts (what holds, what breaks, and why that matters for how much proof to demand) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they accepted the comparison, ask what "we learned and got safer" needed after each disaster.
- If they had what breaks but not what holds, ask what people believed about each disaster before it happened.
- If they missed what breaks, ask what happened after each disaster that could not happen after an ASI failure.
- If they said what breaks is that AI is more dangerous, ask whether a bigger disaster that people survived would still let us learn from it, and what is different about an ASI failure.
- If they had what holds and what breaks but not why it matters, ask what changes about the decision to proceed when you cannot learn from a failure.
- If they said only that we should be more careful, ask what would have to be shown, and when, before building something whose first failure cannot be learned from.
- If they answered all three parts and went no further, the moves left go beyond the question: how the denial pattern bears on meeting that bar, why the one attempt is likely to fail, or why that proof is not available now. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all three parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: after the Titanic, ships were required to carry more lifeboats. Ask who would be around to write the new rules after an ASI failure. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem]]
