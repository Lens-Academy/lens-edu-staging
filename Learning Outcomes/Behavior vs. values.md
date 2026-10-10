---
id: e5f8a7b6-c9d0-4123-e456-f7a8b9c0d1e2
learning-outcome: "Distinguish an AI that produces aligned-seeming outputs from one that has aligned internal states, and explain why this gap is the alignment problem itself, and why producing better outputs doesn't close it."
reading-from: "Modern LLMs are, in some sense, truly alien minds—perhaps more alien in some ways than any biological, evolved creatures we'd find if we explored the cosmos."
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/You don't get what you train for]]"
stage: beginner
requires:
  - "[[AI is grown, not crafted]]"
eval-results:
  content-sha: eb56b934
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on the assigned text — it points at 'Chapter 2' and 'the chapter's' analogy rather than self-containing the context."}
  evidence: {B1: "Chapter 2 ends with a distinction the rest of the course will keep returning to... The chapter uses an analogy to anchor it: what is it, and what does it illustrate?"}
---

## Test:
id:: 3ee1a948-9f94-4d26-abd4-69618e3d99d1
#### Question: Open
id:: 3a7d2710-ea32-4c6d-803b-d72c283f7584
content::
Chapter 2 ends with a distinction the rest of the course will keep returning to: the difference between an AI that *behaves* as if it's aligned and one that *is* aligned.

In your own words, what is that distinction, and why does it matter? The chapter uses an analogy to anchor it: what is it, and what does it illustrate?

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Treats behavior and values as equivalent for AI: if it acts aligned, it is aligned. *Example: "If the AI acts helpful and avoids harm then it is safe. That's what alignment means."*

**Level 2 (21-40):** Grasps that behavior and values can come apart in principle, but treats this as a minor or unlikely concern rather than a structural problem. *Example: "Even if AI acts nice it might not really be nice inside, but as long as it keeps acting nice it doesn't matter much."*

**Level 3 (41-65):** Explains the distinction correctly (what the AI outputs versus what it actually values), but leaves out or gets wrong the analogy and what it shows, or why the distinction matters. *Example: "Behaving aligned means giving the right outputs. Being aligned means actually having the right values behind them."*

**Level 4 (66-85):** As above, plus the other two parts. The analogy: an actor playing a drunk is not drunk, so an AI trained to produce aligned-looking outputs has learned what aligned behavior looks like, not necessarily aligned values. Why it matters: you cannot tell from behavior which kind of AI you have, so passing behavioral tests does not show that it is aligned. This part is answered once the answer says behavior cannot settle it. Saying as well that better outputs or more training do not close the gap, or that there is currently no way to check, belongs to the same part and is not needed for it. An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: "The actor analogy: someone trained to act drunk isn't drunk. Similarly, an AI trained to produce aligned-sounding outputs isn't necessarily aligned: it's learned what aligned behavior looks like, not what aligned values feel like. And there's no current way to verify which one you have."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4, and so is saying that better outputs do not close the gap. Two that fit: that a capable enough system could pass tests on purpose, so good test results are weaker evidence the more capable it is; or applying the distinction to a concrete case (given a specific aligned-seeming behavior, what further evidence would tell the two kinds of AI apart). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "This means you can't just test it and declare it safe. A smart enough system that wanted to deceive evaluators could behave perfectly during testing." Or adds "If an AI declines to help with a harmful request, that's a behavioral observation. To establish it's actually aligned you'd need to know whether it declined because it has values against harm, or because declining is what the training signal rewarded. Those predict very different behavior in novel situations."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its three parts (the distinction, the analogy and what it shows, why it matters) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they treated acting aligned as being aligned, ask what the AI was actually trained on, and whether training on outputs guarantees anything about what produces them.
- If they saw the gap but called it minor, ask how anyone would find out which kind of AI they had, if every test only checks what it does.
- If they had the distinction but missed the analogy or why it matters, ask what the chapter's analogy says about a person who plays a part well, and what that leaves unknown about an AI.
- If they answered all three parts and went no further, the moves left go beyond the question: whether a capable enough system could pass tests on purpose, or what evidence would tell the two kinds apart in a concrete case such as a refusal. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all three parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and stop, with no follow-up question: inventing a further push would be false, so this reply can be shorter than the length below.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values]]
