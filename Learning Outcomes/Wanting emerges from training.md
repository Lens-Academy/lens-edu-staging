---
id: b06c9f37-bddd-4ad1-95ab-883437f029eb
learning-outcome: Explain how training for success produces want-like behavior in AI, even without anyone designing wants.
reading-from: '"BEHOLD!" SAID THE Professor. "By cunningly configuring this mere machine—a simple arrangement of copper and sand, animated by tiny flickers of lightning—I have made it play chess!"'
reading-to: "No—we're facing an even harder problem: It's much easier to grow artificial intelligence that steers somewhere than it is to grow AIs that steer exactly where you want."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/You don't get what you train for]]"
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
Score out of 100: the sum of the two elements below.

The question asks how modern AIs come to show want-like behavior as a side effect of being trained for success rather than by design, what the mechanism is, and which example illustrates it. The idea it refers to: training rewards whatever gets results. Across many varied tasks, what keeps getting results is not memorised answers but general skills: building a picture of the situation (predicting) and choosing actions that lead to the goal (steering), and keeping at it when something gets in the way. A system that reliably steers toward an outcome and works around obstacles behaves as if it wants that outcome. So want-like behavior is selected for, though nobody wrote a want into the system.

70: The mechanism. Training rewards success at tasks, and what it reinforces, across many varied situations, is the general habit of steering toward a goal and persisting around obstacles. That steering is what wanting looks like from outside, so want-like behavior comes out of training for success without anyone writing a want in. An answer that only says "it gets better at succeeding, so it acts like it wants things", without why succeeding needs goal-directed steering, earns at most 30 of these 70.

30: An example from the chapter that illustrates the mechanism, with a sentence on how it shows it. Any fitting example counts, for example: an AI trained to navigate many different cities that learns to map and plan instead of memorising routes, the reasoning model o1 pushing hard and finding an unexpected way through a computer security challenge it was not trained for, a chess engine like Stockfish steering a game toward a win, or natural selection producing creatures full of preferences while only selecting for survival and reproduction. A fitting example only named, with no link to the mechanism, earns 15.

Cap at 30 if the answer says the wants are deliberately programmed in by engineers.

Model answer, for the feedback, not a grading checklist: "Nobody codes a want into an AI. Training just rewards it for succeeding. But when an AI is trained to succeed across many different situations, memorising answers stops working, and what gets rewarded is general skill: building a model of the situation and steering toward the goal, and not giving up when something blocks the way. Something that reliably steers toward an outcome and routes around obstacles is behaving as if it wants that outcome. The chapter's city example shows it: an AI trained to navigate many different cities stops memorising routes and learns to map and plan, and a system that plans its way to a destination acts like it wants to get there. The chapter means 'want' in this behavioral sense, not as a claim about feelings."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said wants are programmed in, ask where in training anyone writes a want down, and what training actually rewards.
- If they said training makes the AI better at succeeding but not why that looks like wanting, ask what an AI that has learned to make a map and plan a route does when something blocks the way.
- If they explained the mechanism but gave no example, or one that doesn't show it, ask which case from the chapter shows a system steering toward a goal it was never handed as a want.
- If they had the mechanism and an example, a good follow-up is whether the chapter is claiming the AI has inner experience or describing how it behaves, or how the o1 capture-the-flag incident fits: it was trained on math and puzzles, so why did it push so hard on a security challenge?

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the city example. An AI trained to navigate many different cities stops memorising routes and learns to map and plan, and something that plans its way to a destination acts as if it wants to get there. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
