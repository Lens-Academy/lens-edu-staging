---
id: 453c921f-6668-44ff-84e4-45193fd1c549
learning-outcome: "Explain why there's no reliable relationship between training objectives and resulting AI preferences."
reading-from: "A MILLION YEARS ago, when one branch of primates was still mastering fire, two strange creatures arrived at Earth and settled into orbit in a spacecraft, wondering at what they saw below them."
reading-to: "That's the next chapter."
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/You don't get what you train for]]"
stage: beginner
requires:
  - "[[Wanting emerges from training]]"
eval-results:
  content-sha: 8143dea5
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on a specific reading — it opens by attributing the framing to Chapter 4 and asks about 'the ice cream argument' as a named artifact of that text."}
  evidence: {B1: "Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful."}
---

## Test:
id:: 27dca5ad-1a1d-40bf-b83d-fbcbd2e9f3d0
#### Question: Open
id:: 81765b69-2530-4acf-98e9-3fc63e0b7e5b
content::
Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful.

What is the ice cream argument, and what does it show about the relationship between what you train an AI for and what it ends up preferring? Where does the argument go beyond ice cream, and why does that matter?

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Treats what you train an AI for and what it ends up preferring as the same, or cannot say what the ice cream argument is. *Example: "Train it to be helpful and it will want to be helpful; that's what training is for."*

**Level 2 (21-40):** Sees that an AI's preferences can drift from what it was trained for, but cannot explain the ice cream argument or why the drift happens, or treats the drift as a small error that more training can correct. *Example: "It might pick up some quirks along the way, but you can retrain it until it gets it right."*

**Level 3 (41-65):** Gives two of the three parts: what the ice cream argument is, what it shows about the link between training and preference, and where the argument goes beyond ice cream and why that matters. An answer that otherwise has all three but treats the gap as a small error that more training can correct misses why going beyond ice cream matters, and stays at this level. *Example: "Evolution pushed our ancestors toward energy-rich food, and no one watching them could have guessed that would end in a craving for ice cream. In the same way, training an AI to be helpful doesn't tell you what it will end up wanting."*

**Level 4 (66-85):** All three. The ice cream argument: this part is answered once the answer says that natural selection shaped humans toward getting energy from food, yet people ended up wanting things like ice cream rather than whatever is richest in energy, an outcome no one watching early humans could have predicted from what they were being shaped for. What it shows: this part is answered once the answer says that what a system is trained for does not settle what it ends up preferring, because many different inner drives do equally well in training and lead to very different preferences later, so training an AI to be helpful does not make it want to be helpful. Beyond ice cream: this part is answered once the answer says that a preference can come apart from the training target altogether or even work against it (for example sucralose, sweetness with no energy at all; the peacock's tail, which works against the bird's survival; or the chapter's AI scenarios that end in such preferences), and why that matters: what an AI ends up wanting need not stay anywhere near what it was trained for, so the gap is not a small error. An answer that says only that the AI "might not want what it was trained for", without why, or that names sucralose or the peacock's tail without what each adds, reaches this level but not fully. Saying as well what the alien observers would have predicted (jet fuel, then honeyed, salted bear fat), the chapter's AI scenarios matched to each step, the chain from training target to inner workings to preference, or the term "alignment", belongs to the same parts and is not needed for them. An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Lots of different inner urges would all score well during training, and each one points somewhere different once the AI is let loose."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Two that fit: why these preferences do not show up yet (they stay hidden while the AI lacks the power to act on them and surface once it can reshape its situation or invent new options, as people could not want sucralose until chemistry made it, so good behavior in training or testing is weak evidence; saying only that problems might appear later does not by itself make an extension); or why the gap cannot be closed by spotting and correcting the wrong preferences during training (many inner drives give the same behavior in training, and the odd preferences stay hidden until the AI can act on them, so there is nothing visible to correct toward; saying only that retraining will not fix it does not by itself make an extension). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "Nobody could crave diet soda until the sweetener was invented; an AI's odd tastes might sit just as quietly until it has the means to chase them." Or adds "You can't train out a quirk you can't see, and these stay out of sight until the AI can act on them."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its three parts (what the ice cream argument is, what it shows, and where it goes beyond ice cream and why that matters) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they treated what you train for and what you get as the same thing, ask why humans, shaped by selection to seek energy, prefer ice cream rather than the foods richest in energy.
- If they saw that preferences can drift but called it a small error that more training can fix, ask how you would know what to correct toward, when the AI behaved well throughout training.
- If they said only that the AI might not want what it was trained for, without why, ask what in training would tell apart an AI that wants to help from one that only behaves helpfully while it is being trained.
- If they explained the ice cream argument but not where it goes beyond ice cream, ask what sucralose and the peacock's tail add.
- If they named sucralose or the peacock's tail without what each adds, ask how each relates to what the creature was originally shaped for.
- If they answered all three parts and went no further, the moves left go beyond the question: why these preferences would not show up in today's AIs, and when they would, or why the gap cannot be closed by correcting the AI during training. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all three parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: an alien watching early humans gather food could not have predicted that their descendants would want ice cream. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens: PQ - You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For - PQ]]

## Lens: You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For]]
