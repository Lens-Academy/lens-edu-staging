---
id: b06c9f37-bddd-4ad1-95ab-883437f029eb
learning-outcome: Explain how training for success produces want-like behavior in AI, even without anyone designing wants.
reading-from: '"BEHOLD!" SAID THE Professor. "By cunningly configuring this mere machine—a simple arrangement of copper and sand, animated by tiny flickers of lightning—I have made it play chess!"'
reading-to: "No—we're facing an even harder problem: It's much easier to grow artificial intelligence that steers somewhere than it is to grow AIs that steer exactly where you want."
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/You don't get what you train for]]"
stage: beginner
eval-results:
  content-sha: c70864ab
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on a specific text — it references Chapter 3 and demands an example drawn from that chapter, so it cannot be asked cold."}
  evidence: {B1: "Chapter 3 argues that modern AIs will develop something like wants ... what example from the chapter most clearly illustrates this?"}
---

## Test:
id:: 26b45f14-dc22-461a-9cbd-e5f5dbf223ae
#### Question: Open
id:: 28dca508-b006-44d3-9640-8265d77b677e
content:: Chapter 3 argues that modern AIs will develop something like wants, not because anyone designed wants into them, but as a side effect of how they are trained. In your own words, how does the chapter explain that? What's the mechanism by which training for success produces want-like behavior, and what example from the chapter most clearly illustrates this?

assessment-instructions::
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot explain where the want-like behavior comes from, or holds that the wants are programmed in by the engineers. *Example: "The developers give the AI a goal to aim for, and that's what it wants."*

**Level 2 (21-40):** Says training makes the AI better at succeeding and that this looks like wanting, but not why succeeding produces want-like behavior rather than just skill, and gives no example that shows it. *Example: "Training keeps rewarding it for doing well, so after a while it acts like it wants to do well."*

**Level 3 (41-65):** Gives one of the two parts: the mechanism, or an example from the chapter with what in it looks like wanting and where that came from. *Example: "Training doesn't reward wanting, only winning. But winning at lots of different hard tasks means sticking with a target and finding a way around whatever blocks you, and anything that does that acts like it wants the result."*

**Level 4 (66-85):** Both. The mechanism: this part is answered once the answer says that training rewards only success, that succeeding across many varied or difficult tasks takes steering toward the outcome rather than repeating fixed moves (keeping at it and finding a way around what gets in the way), and that this steering is what looks like wanting, though no one designed a want. The example: this part is answered once the answer gives one of the chapter's examples (the AI trained to navigate many cities, Stockfish, o1, or the way natural selection produced creatures full of wants) and says what in it looks like wanting and where that came from. One example explained well can carry the mechanism too: the city example, told with why memorized routes stop working and how the map and the route are used to reach a destination, gives both parts. An answer whose example is only named, without what in it looks like wanting, or whose mechanism is only "training makes it want to succeed" with nothing in the answer showing how, reaches this level but not fully. So does one that says the chapter claims the AI has feelings or inner experience: "want" here names how it behaves. Saying as well that the skills split into predicting (a map) and steering (a route), that a map only gets reinforced when it is used to steer, or giving more than one example, belongs to the same parts and is not needed for them. An answer that does both parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Nobody coded a wish to win; doing well across that many different situations simply required heading for a target and working around whatever was in the way."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: what the chapter is and is not claiming by "want" (it names outward steering toward an outcome and makes no claim about feelings, and the argument needs none, since a system that keeps steering toward outcomes and around obstacles matters whatever it feels; saying only that the AI has no feelings does not by itself make an extension); why the steering ends up pointed somewhere nobody chose (training checks only results, so it can grow strong steering without fixing exactly what that steering aims at, which is why it is much easier to grow an AI that steers somewhere than one that steers exactly where you want; quoting that line without the reason does not by itself make an extension); or why the steering carries over to tasks the AI was never trained on (the moves that win at one kind of hard problem win at others, which is what the o1 incident shows; saying only that o1 pushed hard on a task it was not trained for is level 4). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "Whether it feels anything is beside the point: something that keeps finding a way to its target is a problem either way." Or adds "The habits that crack a hard math problem also crack a locked-down server, so drive learned in one place shows up in another."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of its two parts (the mechanism, and an example that shows it) is only asserted, that part is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they said wants are programmed in, ask where in training anyone writes a want down, and what training actually rewards.
- If they said training makes the AI better at succeeding but not why that looks like wanting, ask what an AI that has learned to map a city and plan a route does when something blocks the way.
- If they named an example without saying what in it looks like wanting, ask what the AI in that example does that someone who wanted the outcome would also do.
- If they said the chapter claims the AI has feelings, ask whether the argument needs that, or only needs to describe how the AI behaves.
- If they answered both parts and went no further, the moves left go beyond the question: what the chapter is and is not claiming by "want", why the steering ends up pointed somewhere nobody chose, or why it carries over to tasks the AI was never trained on. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with both parts solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: the city example. An AI trained to navigate many different cities stops memorising routes and learns to map and plan, and something that plans its way to a destination acts as if it wants to get there. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
