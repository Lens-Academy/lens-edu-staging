---
id: ca006c78-5c20-4102-87c2-7033c085ec59
learning-outcome: "Distinguish hostile from indifferent AI: explain why the core danger from superintelligent AI is not that it would be hostile toward humans, but that it would be indifferent to human values while pursuing its own goals: indifference is sufficient for extinction"
reading-from: "In a sense, that's all there is to it."
reading-to: "And how could they possibly do that, if they're trapped inside computers?"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/The core extinction argument]]"
stage: beginner
eval-results:
  content-sha: 1493b484
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question is scaffolded on a specific text — it names Chapter 5 and asks what 'the chapter' argues, so a capable reader who never read it cannot answer as posed.", C3: "Level-3 criterion embeds the anthill analogy inside the required explanation rather than offering it as one acceptable route, mirroring the DNA-analogy corpus failure."}
  evidence: {B1: "Chapter 5 reframes this: the real concern is an AI that is simply indifferent to us. ... Why does the chapter argue that an AI does not need to be hostile toward humans in order to cause human extinction?", C3: "It is like a construction project that destroys an anthill: not out of malice but out of indifference."}
---

## Test:
id:: 64b45784-164e-4744-bc73-347d9604e9b0
#### Question: Open
id:: b97cdeb0-5619-4e8c-a8ed-fdacfcf58cfd
content::
A common misconception about AI risk is that the danger comes from an AI that actively hates or rebels against humanity. Chapter 5 reframes this: the real concern is an AI that is simply indifferent to us. Because human-compatible goals are a tiny sliver of the space of all possible goals, a superintelligent AI would almost certainly not share our values. Not out of malice, but because there was never any reason it would. The chapter then works through the hopes that an indifferent AI might still spare us (that we would be useful to it, that it would trade with us, that it would need us, that it would keep us as pets, or that it would simply leave us alone) and shows why each one fails.

Why does the chapter argue that an AI does not need to be hostile toward humans in order to cause human extinction? Explain why indifference is sufficient.

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Conflates hostile and indifferent AI, or claims the danger is that AI will "turn evil" or "rebel." *Example: "AI will want to destroy humanity because it sees us as a threat."*

**Level 2 (21-40):** Understands abstractly that AI might not share human values, but cannot explain why indifference alone is dangerous. *Example: "The AI wouldn't care about us, but I'm not sure why that's as bad as it being hostile."*

**Level 3 (41-65):** Sees that an indifferent AI could harm us as a side effect of pursuing something else, but does not explain how (what it would take or change that we need), or does not say why that is enough on its own. *Example: "It doesn't need to hate us. It could hurt us by accident while it's busy doing something else."*

**Level 4 (66-85):** Explains both: a superintelligent AI pursuing goals that have nothing to do with us would use or reshape the matter, energy and space we need to survive, not to harm us but because our survival is not part of what it is aiming at; and since nothing in its goals gives it a reason to preserve us, indifference is enough. An analogy (a construction project and an anthill, a bulldozer and ants) is one way to say this and is not needed. Explaining why one particular hope fails (that we would be useful to it, it would trade with us, it would need us, keep us as pets, or leave us alone) belongs to the same part and is not needed for it. An answer that does both has answered the question in full, and without an extension it stays in this range. *Example: "The chapter says the AI wouldn't hate us. It just wouldn't care. If it's optimizing for something that has nothing to do with human welfare, it would use up the atoms and energy we need to survive. We'd be like ants in the path of a bulldozer: not targeted, just irrelevant."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4, and so is explaining why one particular hope fails. Two that fit: what all the hopes of being spared have in common (each needs the AI to choose our survival, which a goal unrelated to us gives it no reason to do); or why indifference is harder to deal with than hostility (a hostile AI is an adversary we could reason with, deter or defend against, while an indifferent one has no reason to negotiate or even notice us, so only its actually caring about human survival would spare us). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Example: "...That's why every hope in the chapter, from being useful to being kept as pets, fails: sparing us would only happen if the AI wanted it to. You can't bargain with something that doesn't consider you relevant."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (how an indifferent AI would harm us, why that is enough on its own) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they described an AI that hates or rebels against us, ask what an AI pursuing some unrelated goal would do with the matter and energy around it, if it neither liked nor disliked us.
- If they said it would not share our values but not why that is dangerous, ask what happens to an anthill when a road is built through it, and what the builders felt about the ants.
- If they said it could harm us as a side effect but not how, or not why nothing would stop it, ask what it would actually take or change that we need, and what in its goals would make it hold back.
- If they argued that one of the hopes would save us (that we would be useful, trade with it, be needed, be kept as pets or be left alone), ask what in the AI's own goals would make it choose that over the cheaper alternative.
- If they answered both parts and went no further, the moves left go beyond the question: what all the hopes of being spared have in common, or why indifference is harder to deal with than hostility. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and stop, with no follow-up question: inventing a further push would be false, so this reply can be shorter than the length below.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - PQ - Distinguish Hostile from Indifferent AI]]

## Lens:
source:: [[../Lenses/IABIED - Distinguish Hostile from Indifferent AI]]

## Lens:
source:: [[../Lenses/IABIED - QA - AI Find Us Useful]]

## Lens:
source:: [[../Lenses/IABIED - QA - AI Find Us Fascinating]]
