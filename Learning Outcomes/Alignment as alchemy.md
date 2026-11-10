---
id: 3e29b948-02b0-4fd3-847a-4c7adb05dd0d
learning-outcome: "State Chapter 11's central diagnosis as the chapter frames it: the alignment field is currently in the 'alchemy stage': producing results without understanding why they work, operating from high-minded philosophical ideals rather than engineering designs, and mistaking the ability to build more powerful AI for progress on making it safe."
reading-from: "beginning of chapter"
reading-to: "It is a level of systemic game that would have humanity headed for disaster, even if we were wrong about every other aspect of difficulty."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/Why alignment is hard]]"
stage: beginner
eval-results:
  content-sha: fc29cbf0
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing rather than a source-free capability; named as a corpus fail example in the A2 eval.", B1: "Question is scaffolded on the assigned chapter — it names Chapter 11 and its opening allegory, so it cannot be posed to someone who never read that text."}
  evidence: {A2: "State Chapter 11's central diagnosis as the chapter frames it", B1: "Chapter 11 opens with an allegory about a young alchemist"}
---

## Test: 
id:: 311a34f9-b4d2-46b8-813a-3b51869fe6c3
#### Question: Open
id:: 694d05ca-a88c-4ae9-9012-15594bedb758
content:: Chapter 11 opens with an allegory about a young alchemist who claims to be "close" to transmuting lead into gold despite having no understanding of why his recipes produce the results they do. The chapter then applies this framing to current AI alignment efforts, drawing on public statements from Elon Musk (xAI) and Yann LeCun (Meta). The authors call this the "alchemy stage" of a science.

**In your own words, what is Chapter 11's "alchemy stage" diagnosis of the AI alignment field? What specifically does the chapter claim is missing from the field's current state, and why does it matter that it is missing?**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Reads the diagnosis as "alignment is hard" or "the field isn't trying hard enough", missing the claim about what kind of progress the field has made. *Example: "They're saying alignment isn't working yet."*

**Level 2 (21-40):** Says the field is at an early stage, like the alchemists, but cannot say what marks that stage. *Example: "The alignment field is still figuring it out, like alchemists were."*

**Level 3 (41-65):** Gives the diagnosis and what it says is missing: the field has techniques that sometimes work but no understanding of why they work, so what is missing is that understanding (principles or designs that say why a technique works and what it will do). This part is answered once the answer says both that the field gets results it cannot explain and that the explanation is what is missing; saying only that the field needs "more research" or "more time" does not answer it. At this level the answer does not say why it matters that the understanding is missing. *Example: "Like the alchemist, the field can get results it can't explain. What it lacks is a theory of why its methods work."*

**Level 4 (66-85):** As above, plus why it matters that the understanding is missing. This part is answered once the answer says, in a phrase, what goes wrong without it: for example, that nobody can tell whether a technique that works now will keep working on a far more capable system, that getting better at building AI is taken for progress on making it safe, or that a field without principles has nothing that could show it when it is wrong. An answer that says only that this is "dangerous" or "a problem" reaches this level but not fully. Saying as well that the field's plans are high-minded ideals rather than designs (an AI that seeks truth, an AI whose wants we set), that what is missing is not effort, money or intelligence, or which people or examples the chapter draws on, belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "That matters because getting better at building AI gets mistaken for getting closer to making it safe."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: why this kind of ignorance is hard to correct (the same lack of theory that produces a wrong answer also produces confidence in it, because without a calculation there is nothing anyone could check; saying only that the field cannot tell when it is wrong is level 4); what the diagnosis does not say (it is about the field's stage, not blame on particular people, not despair, and not a claim that alignment is impossible: the stage can be left, but has not been); or why the field is stuck at recipes (the systems are grown rather than designed, so working techniques arrive without explanations, which is why more effort or money does not simply mature the field; saying only that effort is not what is missing is level 4). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "This isn't blaming anyone or saying alignment can't be done. It's saying the field hasn't yet left the stage every science starts in." Or adds "It's stuck at recipes because these systems are grown, not designed: the techniques that work come without any explanation attached."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (the diagnosis with what is missing, and why it matters) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they said only that alignment is hard or not working yet, ask what the alchemist had, recipes that sometimes worked, and what he lacked.
- If they said the field is at an early stage without saying what marks that stage, ask what separates an alchemist from a chemist who makes the same compound.
- If they gave the diagnosis but not why it matters, or said only that it is "dangerous", ask what goes wrong when a technique works but nobody knows why, for example once it is used on a system far more capable than today's.
- If they answered both parts and went no further, the moves left go beyond the question: why this kind of ignorance is hard to correct, what the diagnosis does not say, or why the field is stuck at recipes. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: Aqua Regia. Alchemists could make it reliably without any chemistry to explain why it worked. Ask what the alignment equivalent is. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science]]
