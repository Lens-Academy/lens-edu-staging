---
id: e7a6096d-ef44-4f48-b2d1-53307f8d99ee
learning-outcome: "Apply the ladder-in-the-dark framing to explain why uncertainty about the fatal rung does not protect against predictable disaster: trace the chapter's argument that if climbing cannot be stopped while uncertainty remains, death is a predictable collective outcome, even though no specific rung can be identified as lethal in advance."
reading-from: "An AI company executive who says there's only a one-in-five chance that the AI they're building will kill literally everyone (as they do) is not in quite as much denial as the Soviet managers who denied the Chernobyl meltdown after it happened."
reading-to: "end of chapter"
authors:
  - Chris+Claude
concept: "[[../Concepts/Predicting outcomes, not paths]]"
stage: beginner
eval-results:
  content-sha: 0416884d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: fail, C3: fail}
  notes: {A2: "Statement is bound to a specific text: it asks the learner to reconstruct what the chapter argues, matching the 'State Chapter 11's central diagnosis as the chapter frames it' fail pattern.", B1: "Question is scaffolded on the assigned text — it names Chapter 12 and asks the learner to trace that chapter's argument, so a capable non-reader cannot answer as posed.", C2: "Pass level 3 hard-requires naming the chapter's three specific actor categories, which the question never asks for or implies.", C3: "Level 3 requires a memorized taxonomy verbatim ('the three types of actors...') rather than stating the idea in any wording; level 5 likewise hard-requires the specific CERN example with no 'or equivalent' allowance."}
  evidence: {A2: "trace the chapter's argument that if climbing cannot be stopped while uncertainty remains", B1: "Chapter 12 closes with a striking image: every competing AI company is climbing a ladder in the dark.", C2: "the three types of actors (researchers/companies, corporate executives, world leaders) each have incentives to keep climbing", C3: "connects to the CERN comparison the chapter uses to close"}
---

## Test:
id:: 38dc6bd8-b793-448e-a44a-89d3cd4c6a03
#### Question: Open
id:: 8cb60110-0a9e-46c1-bf92-29af1920ea39
content:: Chapter 12 closes with a striking image: every competing AI company is climbing a ladder in the dark. Nobody knows which rung will be the last safe one: the point at which an AI system crosses into unrecoverable territory. You might expect this uncertainty to provide protection: if no one knows where the lethal rung is, perhaps caution will prevail. Chapter 12 argues the opposite. 

**Suppose a lab leader says: 'No one can say which model will be the dangerous one, so we should keep building and react when we see a warning sign.' Using the ladder-in-the-dark framing, explain what is wrong with this reasoning, and why a company that agreed with you would still keep building.**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot explain the ladder-in-the-dark framing, or treats the uncertainty as a reason for hope. *Example: "If nobody knows which rung is dangerous, they will probably stop before they hit it."*

**Level 2 (21-40):** Sees that there is a race and that nobody knows when it becomes dangerous, but cannot say why not knowing fails to protect. Treating the problem as missing information, so that better tests or warning signs would let companies stop in time, is this level: the companies already accept a high risk and keep going. *Example: "There's a race to build AI and nobody knows when it becomes dangerous. Better tests would help them spot the warning signs and stop."*

**Level 3 (41-65):** Explains one of the two things the question asks but not the other: why not knowing which rung is lethal does not protect, or why a company that agreed would still keep building. *Example: "Not knowing which step is fatal doesn't help. Keep stepping up and you get to it eventually."*

**Level 4 (66-85):** Both. What is wrong with the reasoning: this part is answered once the answer says that if the climbing goes on it reaches the lethal rung whichever one it is, so the outcome is predictable even though the rung is not. Why an agreeing company keeps building: this part is answered once the answer says that stopping alone would not stop the climb, because the others would carry on and it would only hand them the lead. An answer that gives the second part only as "because of the race" or "because of competition" reaches this level but not fully. Saying as well that a warning sign may come only when it is too late, because the lethal step cannot be undone; which kinds of actor keep climbing (researchers and companies, executives, governments); or the executive who puts the risk at one in five and keeps going, belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "And agreeing doesn't make it stop: pausing alone only means a rival climbs the next step instead."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: why no single actor can fix it (each choice to keep building is sensible on its own terms, but together they produce the outcome none of them wants, so only a stop that binds everyone at once could work; saying only that stopping alone hands the lead to others is level 4); what proceeding under this kind of uncertainty looks like elsewhere (checking first and going ahead only once it is shown safe, as physicists did before switching on a particle collider that some feared could destroy the Earth, and that AI development has no such step); or why the outcome can be called without knowing the rung (where a climb ends can be predicted without predicting the steps, the same way a contest's result can be called without calling the moves; saying only that the outcome is predictable is level 4). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "Physicists spent years checking that a new collider couldn't end the world before they switched it on. Nobody building AI has a step like that." Or adds "You can say where the climb ends without knowing the rung, the way you can say who wins without knowing the moves."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (what is wrong with the reasoning, and why an agreeing company keeps building) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they treated uncertainty as a reason for hope, ask what each company does at the next rung when it cannot tell whether that rung is the lethal one.
- If they named the race but not why uncertainty fails to protect, ask whether the climbing depends on anyone knowing where the lethal rung is, or on something else.
- If they treated the problem as missing information, ask whether the companies would stop if they were told the risk was high, given that some already say it is.
- If they explained why not knowing fails to protect but not why an agreeing company keeps building, ask what would happen to the climb if that one company stopped.
- If they said only that the company keeps building because of the race or competition, ask what stopping alone would change, and for whom.
- If they answered both parts and went no further, the moves left go beyond the question: why no single actor can fix this even when each is acting sensibly, what going ahead under this kind of uncertainty looks like elsewhere and what AI development has in its place, or why the outcome can be called without knowing the rung. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the executive who believes there is a one-in-five chance of killing everyone and keeps building. Ask what keeps them building. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark]]
