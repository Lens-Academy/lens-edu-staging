---
id: a9c4d6f1-3b7e-4c2d-8a5f-1e9b0c7d4f2e
learning-outcome: "Describe the refrigerator thought experiment: explain how superior knowledge of physical laws enables the design of devices that appear impossible to those who built them, and connect this to what a superintelligence could do to humanity"
reading-from: "Suppose you sent a design for a refrigerator back in time by a thousand years—a simplified design, one that the blacksmiths of the day could actually build."
reading-to: "So: Once upon a time in the near future…"
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/Machine advantages]]"
stage: beginner
eval-results:
  content-sha: 0417e790
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question is scaffolded on a specific text — names 'Chapter 6' and 'the chapter' as the source of the illustration.", C3: "Level-4 criterion hard-requires a memorized textual detail (the specific domains Chapter 6 names) rather than a concept boundary statable in any wording."}
  evidence: {B1: "Chapter 6 sends a refrigerator blueprint back a thousand years.", C3: "connects to the specific vulnerable domains Chapter 6 names (biology and human psychology)"}
---

## Test:
id:: bbbca804-d52c-4567-84cb-68eae82c0025
#### Question: Open
id:: db25576b-1619-4e8a-80de-d3b1fbe91b27
content::
Chapter 6 sends a refrigerator blueprint back a thousand years. A medieval blacksmith could build it but would be astonished that it produces cold air, because the underlying physics (gas compression and expansion) was unknown to them. The chapter uses this to illustrate what it means to face something that knows more about reality than you do. It then applies this logic to a superintelligent AI, and explores the domains where humanity is most exposed.

In your own words, what does the refrigerator thought experiment demonstrate about what a superintelligent AI might be capable of?

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot explain the thought experiment, or confuses it with a different argument. *Example: "It shows that an AI could reuse old inventions against us."*

**Level 2 (21-40):** Retells the refrigerator story without connecting it to AI, or reads it as saying only that we will not understand how an AI works inside. *Example: "Someone from the Middle Ages would be baffled by a fridge, just like we're baffled by how AI thinks."*

**Level 3 (41-65):** Gives one of the two parts: what the thought experiment shows (knowing a law of nature that others do not lets you build something that seems impossible to them, even to the people who built it), or what this means for a superintelligence. *Example: "The blacksmith could put the fridge together from the plans, but he didn't know the rule about gases and pressure, so the cold air would seem like magic to him."*

**Level 4 (66-85):** Both. The thought experiment: this part is answered once the answer says that the blacksmith can build the device from the plans and still be astonished that it makes cold air, because what he lacks is knowledge of the law of nature that makes it work, so knowing more about how the world works lets you design things that look impossible to others. What it means for AI: this part is answered once the answer says that a superintelligence would know more about how the world works than we do, so it could design and use things that seem impossible to us, and could defeat us by means we would not understand even while watching them work. An answer that puts the blacksmith's surprise down only to not understanding the machine, without that what he lacked was knowledge of the law it uses, reaches this level but not fully. So does one that says only that AI will have advanced or amazing technology, without that its edge would come from knowing rules we do not. Saying as well which law the refrigerator uses, the domains the chapter names as most exposed (biology and the brain), the chapter's examples of what is possible within known science, or its line about facing something that knows more about reality than you do, belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Something that knew more about how the world works could build things that look like magic to us, and we'd lose to them without ever understanding what hit us."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: where we are most exposed and why (the less we understand the rules of a domain, the more room a smarter mind has to use rules we do not know exist, which is why the chapter points to biology and the human brain; naming those domains without the reason does not by itself make an extension); why not being able to picture the method does not weaken the prediction, and why that is not an empty claim (the blacksmith's confusion did not make the cold air unreal, and gaps in knowledge have decided outcomes before, as when protein folding, dismissed as out of reach, was largely solved; saying only that we cannot predict the method is level 4); or why the argument does not depend on exotic physics (even within science we already understand, a superintelligence could do things that look impossible to us: the chapter's examples include reading secret keys from a device's power light, and it points out that tiny self-copying factories already exist in nature as algae, so building something like them is not beyond known physics; such cases set a floor on what it could do; listing the examples without what they show does not by itself make an extension). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "We barely know how memories are stored in the brain, so that's exactly where something smarter would find rules to exploit that we've never heard of." Or adds "Even sticking to physics we already know, people have pulled secrets out of a blinking light; a far smarter mind would have a long list of tricks like that before it needed anything new."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (what the thought experiment shows, and what it means for a superintelligence) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they retold the story without linking it to AI, ask what the blacksmith lacked, and what an AI would need to have over us to put us in the same position.
- If they said we will not understand AI, or put the blacksmith's surprise down only to not understanding the machine, ask what exactly he was missing, given that he built the machine himself.
- If they said only that AI will have advanced technology, ask where that technology's edge would come from.
- If they answered both parts and went no further, the moves left go beyond the question: where human knowledge is thinnest and so where a smarter mind would have the most room, why not being able to picture the method does not weaken the prediction, or why the argument does not need any physics we do not already know. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the blacksmith could follow the blueprint step by step and still be astonished by the cold air, because the rule that makes it cold was unknown to him. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - PQ - Describe the Refrigerator Thought Experiment]]

## Lens:
source:: [[../Lenses/IABIED - Describe the Refrigerator Thought Experiment]]
