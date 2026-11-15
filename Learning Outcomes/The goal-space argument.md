---
id: 1a433dba-6f86-4291-8996-f472f0e90536
learning-outcome: "Define the goal-space argument: explain why a sufficiently advanced AI's goals are overwhelmingly unlikely to include human values, using the logic that most possible goal-sets don't converge on any particular set of values as intelligence increases"
reading-from: "THERE ONCE WAS a civilization of aliens, biological rather than mechanical in nature, and so far away from Earth that no message we sent into the stars could ever reach them."
reading-to: "Making a future full of flourishing people is not the best, most efficient way to fulfill strange alien purposes. So it wouldn't happen to do that, any more than we'd happen to ensure that our dwellings always contain a prime number of stones."
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/The space of possible goals]]"
stage: beginner
eval-results:
  content-sha: c52a72dc
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: fail, C3: pass}
  notes: {B1: "Question is scaffolded on a specific text — names Chapter 5 and asks what 'the chapter' claims, so it cannot be posed at a random moment.", C2: "Pass level 3 requires a concrete example/allegory, which the question never asks for."}
  evidence: {B1: "Chapter 5 opens with an allegory about an alien civilization ... Why does the chapter claim that a sufficiently advanced AI is overwhelmingly unlikely to pursue human-compatible goals?", C2: "Uses the alien allegory or an equivalent concrete example."}
---

## Test:
id:: 10dd3907-2bae-4eee-9985-fe1a6506f5b3
#### Question: Open
id:: 8d3c65bc-69e4-489b-b221-8dfe883620b6
content::
Chapter 5 opens with an allegory about an alien civilization obsessed with the "correct" number of stones in their nests. A young alien argues that most species in the universe would not share this value, and that getting smarter wouldn't change that. The text then applies this same logic to AI: most possible goal-sets for a superintelligent AI would not include building a future full of happy, free people.

In your own words, what is the "goal-space argument"? Why does the chapter claim that a sufficiently advanced AI is overwhelmingly unlikely to pursue human-compatible goals?

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot explain the goal-space argument, confuses it with a different claim (for example that AI will be too powerful to control), or argues the opposite: that a smart enough mind would come to share or follow human values. *Example: "A truly intelligent AI would work out that kindness is the rational choice."*

**Level 2 (21-40):** Has a general sense that an AI might not share human values, but cannot say why in the argument's terms, or gives a different reason, such as that it was not raised like a human. *Example: "AI might not care about what we care about, since it didn't grow up in a human family."*

**Level 3 (41-65):** Gives one of the two parts: that the space of possible goals is vast and goals that include a good future for people are a tiny share of it, or that getting smarter does not pull a mind toward any particular goals. *Example: "There are endless things a mind could want, and only a sliver of them involve people living happy, free lives."*

**Level 4 (66-85):** Both. The space of goals: this part is answered once the answer says that there are vastly many goals a mind could have, and those that would include a future of happy, free people are a tiny share of them. Intelligence: this part is answered once the answer says that getting smarter does not move a mind toward any particular goals but only makes it better at pursuing the ones it has, so a more capable AI is no more likely to land on ours. An answer that says only that being smart does not make an AI nice or good, without what intelligence does and does not change about a mind's goals, reaches this level but not fully. So does one that says most possible goals are hostile to humans: most simply do not include us. Saying as well the chapter's allegory (the aliens who care about the number of stones in their nests, and the young alien's argument), the prime numbers, or the term "orthogonality", belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Being cleverer just means you're better at getting whatever you were already after; it doesn't change what that is."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: what this means for building an AI that shares our goals (hitting a tiny target in a vast space takes a way to aim, and no one yet has one, so the default is indifference rather than malice; saying only that alignment is hard does not by itself make an extension); why understanding our values would not make an AI share them (a mind can predict what we would call good without steering toward it, just as we can tell which nests the aliens would call correct, those with a prime number of stones, without caring about it); or why humans largely share values with each other even though intelligence does not cause it (we share origins and ask the same inner questions, which an AI would not). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "An AI could know exactly what we'd call a good outcome and still not be aiming for it, the way you can know a rival's taste without sharing it." Or adds "People agree with each other because we come from the same stock, not because we're smart; an AI doesn't share that history."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (the space of goals, and what intelligence does to a mind's goals) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they gave a general "AI is too powerful" answer, ask how many different goals an AI could in principle have, and how many of those include a future of happy, free people.
- If they argued that a smart enough mind would come to share or follow our values, ask whether the aliens in the allegory, advanced enough to cross the stars, came to care about anything we care about.
- If they said AI might not share our values without saying why, ask what getting smarter would do to the young alien's point about the stones.
- If they had the vast space and the small target but not what intelligence does, ask what happens to a mind's goals as it gets smarter.
- If they said only that being smart does not make an AI nice, ask what getting smarter does change about a mind, and what it leaves alone.
- If they said most possible goals are hostile to humans, ask whether most of those goals are about humans at all.
- If they answered both parts and went no further, the moves left go beyond the question: what this means for building an AI that shares our goals, why understanding our values would not make an AI share them, or why humans largely share values with each other. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the stones. However clever another species became, nothing about being clever would make it care how many stones are in a nest. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Define the Goal-Space Argument]]
