---
id: a6c8f2d1-5e3b-4a70-9c4f-7b0d2e8f1a35
learning-outcome: "Distinguish the book's use of fiction as a form of argument from two common misreadings (that it predicts specific future events, or that it is merely a thought experiment with no predictive content), and identify the precise middle position: the fictional pathway is not predicted, but the outcome if AI systems reach sufficient capability is"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
optional: true
authors:
  - Chris+Claude
tags:
  - optional
concept: "[[../Concepts/Predicting outcomes, not paths]]"
stage: beginner
eval-results:
  content-sha: ae70fd93
  date: 2026-08-19
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {A2: "capability is about what one specific book claims regarding its own story, not a concept that survives outside the text", B1: "'The Coda' and 'the story' are load-bearing scaffolding; unparseable without the reading", C3: "levels 4 and 5 hard-require memorized text/course details ('not strange enough', M4, Chapters 7-9) rather than stating an idea conveyable in any wording"}
  evidence: {A2: "Distinguish the book's use of fiction as a form of argument from two common misreadings", B1: "The Coda steps outside the story to address a question readers often have", C3: "Notes that the story admitting it's \"not strange enough\" is part of this"}
---

## Test:
id:: 0d32640e-9e23-44c8-8dea-dc1f67564986
#### Question: Open
id:: 826bc7bd-990e-460f-bd0b-c63e52107e21
content:: The Coda steps outside the story to address a question readers often have: what, exactly, is the book predicting?

**The book isn't claiming the specific events of the story will occur. But it's also not saying the story is "just a thought experiment" with no predictive content. What is the precise claim it is making? And how would you respond to someone who says "but it's just sci-fi"?**

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Treats the story as a forecast of the events it describes, or as having no predictive content at all. *Example: "The book predicts this exact scenario will happen." Or: "It's just a thought experiment, it doesn't predict anything."*

**Level 2 (21-40):** Sees that the story is not a forecast of its events but cannot say what claim remains. *Example: "The book doesn't predict the future, it just uses a story to make a point."*

**Level 3 (41-65):** Says what the book does and does not predict: not the events of the story, but the ending, as what happens if an AI far more capable than us is built. This part is answered once the answer separates the two and ties the ending to such a system being built; describing the ending as what follows from facing a superintelligence is enough. Stating the ending as a flat prediction (for example "everyone will die"), with no link to such a system being built, gives this part only in part: on its own that puts the answer at the bottom of this range, and together with the reply in level 4, at the bottom of that range. At this level the answer leaves out the reply to "it's just sci-fi", or gives one that concedes the point (for example, agreeing the claim is weaker because the story is made up). *Example: "The story's events aren't the prediction. The ending is: if someone builds a superintelligence, humanity loses, whatever route it takes."*

**Level 4 (66-85):** As above, plus a reply to "it's just sci-fi" that says why the label does not count against the claim. This part is answered once the answer gives a reason of that kind: for example, that the label fits only the story's events, which the book does not claim, while the claim about the ending rests on reasoning that stands without the story; or that something appearing in fiction says nothing either way about whether it will happen. Saying as well what the story is for (making the danger concrete and easy to follow), or that the authors admit the story is too ordinary to be what would really happen, belongs to the same part and is not needed for it. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Calling it sci-fi only hits the story's events, and those were never the claim. The claim about the ending rests on the argument, not on the story."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: why the ending can be a real prediction when the path cannot (it follows from something that holds whichever route events take, such as a large enough gap in capability; saying only that the claim rests on reasoning is level 4); why any story about this would be too ordinary to be what really happens (a system far more capable than us would act in ways we cannot foresee, which is why the path cannot be predicted, and this leaves the claim about the ending standing; noting only that the authors admit it is level 4); or why the explanation of what is claimed comes after the story rather than before it (the story has to make the danger feel real before the reader can be asked to separate what is argued from what is predicted). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "Something that much smarter would do things we can't think of, so any story we write is bound to be tamer than what would really happen. That's why the path can't be predicted, and it doesn't touch the ending." Or adds "The ending holds whichever way events go, because it follows from how much more capable the AI would be, not from any one sequence of moves."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (what the book does and does not predict, and the reply to "it's just sci-fi") is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they read the story as a forecast of its events, or as having no predictive content, ask which part the authors would actually bet on: the sequence of events, or where it ends.
- If they said the story is not a forecast but could not say what is left, ask what is still being predicted once the specific events are set aside.
- If they stated the ending as a flat prediction, with no link to such an AI being built, ask what would have to happen first for that ending to follow.
- If they separated the events from the ending but did not answer "it's just sci-fi", or conceded it, ask whether the claim about the ending needs the story's events to be right.
- If they answered both parts and went no further, the moves left go beyond the question: why the ending can be a real prediction when the path cannot, why any story about this would be too ordinary to be what really happens, or why the explanation of what is claimed comes after the story rather than before it. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the story's events were picked to make the danger easy to follow. Ask what part of it the authors would still stand behind if those events were swapped for others. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Fiction as Argument]]
