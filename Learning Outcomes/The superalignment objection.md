---
id: 3d95d5e3-b5dd-4ff8-90b8-24653db41a3d
learning-outcome: "Describe the strong version of superalignment as Chapter 11 presents it (using a smarter-than-human AI to solve the alignment problem), and state the chapter's two-step objection: (1) the AI capable of doing this would itself be too dangerous and untrustworthy, and (2) a 'special-purpose' alignment AI has no training examples of solved alignment and requires the precise dangerous skill set that makes an unaligned AI catastrophic."
reading-from: "Some AI companies do try to look less cavalier than that, about ASI alignment, and put forth plans more detailed than those."
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/Why alignment is hard]]"
stage: beginner
eval-results:
  content-sha: 88f0c03d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing — describing what Chapter 11 presents and stating the chapter's objection, not a source-free capability.", B1: "Question uses the chapter as load-bearing scaffolding, repeatedly asking for what Chapter 11 says rather than self-containing the content."}
  evidence: {A2: "Describe the strong version of superalignment as Chapter 11 presents it ... and state the chapter's two-step objection", B1: "Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection"}
---

## Test:
id:: fc3b7597-3165-46ee-af3a-a6990d9e98eb
#### Question: Open
id:: 0ea83c3b-5c18-41c2-94bf-363a3c57d2f1
content:: The most developed alignment plan Chapter 11 examines is "superalignment": the idea, made flagship at OpenAI in 2023, of using AI to help solve the alignment problem itself. The chapter splits this into two versions, weak (AI helps with interpretability research) and strong (a smarter-than-human AI solves alignment for us), and finds the strong version particularly broken.

**Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection: specifically, why building the AI required to solve alignment cannot be done before alignment is itself solved. If you can, also describe the chapter's response to "we'll just make a special-purpose alignment AI that isn't generally dangerous."**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot describe the strong plan, or confuses it with the weak one (AI helping researchers look inside other AIs). *Example: "OpenAI says they'll use AI to look inside other AIs."*

**Level 2 (21-40):** Describes the plan in vague terms but cannot state the objection. *Example: "They want a smart AI to solve the alignment problem for them. The book says that won't work."*

**Level 3 (41-65):** Describes the strong plan (build an AI more capable than the best human researchers and have it solve alignment for us), but gives no objection beyond doubt, or one that is not the chapter's. The most common is that today's AI is not yet smart enough; the chapter's point is the reverse, that an AI smart enough would itself be the problem. *Example: "They want an AI smart enough to solve alignment for them, but current AI just isn't capable enough to do that yet."*

**Level 4 (66-85):** As above, plus the chapter's objection: an AI capable of solving alignment would be capable enough to be dangerous, so it could only be built or trusted safely if it were already aligned, which is the problem it was meant to solve. This part is answered once the answer says that trusting such an AI, or what it hands back, would need alignment solved first. An objection given only as the AI "couldn't be trusted" or "might be dangerous", without that link, reaches this level but not fully. Saying as well that this was OpenAI's flagship plan, what the weak version is, or that the plan "needs what it promises", belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "But an AI that could do that is exactly the kind you can't safely switch on until alignment is solved, so the plan can't get started."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question requires. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: the chapter's response to a special-purpose alignment AI, which the question invites (there are no solved examples of alignment to train it on; the skills it would need, such as understanding how AIs are grown, what they come to want and how people think, are the dangerous ones; and nobody could check a plan it hands back, so you would have to take its word or be won over by its argument); why an AI built for a narrower field is different (a medical AI's output can be checked with separate, narrower tools, while nothing narrower can check whether an alignment plan will hold); or why capability and untrustworthiness come together (the training that makes such an AI capable also leaves it with wants nobody chose; saying only that it would be dangerous is level 4). Another extension of the same substance counts equally, such as showing why a second AI checking the first does not escape the objection. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "A cure from a medical AI can be tested with separate tools. There's no separate tool that tells you whether an alignment plan will hold." Or adds "You can't get the capability without the risk: the same training that makes it smart enough leaves it wanting things nobody chose."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (the strong plan, and the objection) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they described weak superalignment or interpretability, ask what the strong version expects the AI itself to produce.
- If they described the plan but not the objection, ask how capable the AI would have to be to solve alignment, and what you would need before you could safely build something that capable.
- If their objection was that today's AI is not smart enough yet, ask whether the objection would go away if next year's model were smart enough, and what kind of AI it would then be.
- If they said only that such an AI couldn't be trusted or might be dangerous, ask what you would need before you could trust it, and whether the plan has that yet.
- If they answered both parts and went no further, the moves left go beyond what the question requires. Start with the one the question invites: what the chapter says to a special-purpose alignment AI (what would it train on, what skills would it need, and how would anyone check its answer?). The others are why an AI for a narrower field is easier to check, and why capability and untrustworthiness come together. Ask about whichever their answer comes closest to, or the special-purpose AI if none.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the first step of the plan is an AI smart enough to solve a problem humanity's best researchers cannot. Ask what has to be true before you can trust that step. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection]]
