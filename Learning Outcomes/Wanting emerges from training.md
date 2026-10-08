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
Score according to the following rubric.
**1**, Cannot explain the mechanism; treats wanting as deliberately programmed. *Example: "The engineers program the AI to want to succeed. That's how it works."*

**2**, Understands that training shapes behavior but cannot explain why wanting emerges rather than just competence. *Example: "The AI learns to do things through training. Over time it gets better at succeeding, and that makes it act like it wants things."*

**3**, Correctly explains the core mechanism: training for success across varied environments develops separable prediction and steering skills, and an AI that uses its map to navigate behaves like it wants to reach the destination, regardless of whether it "has" wants in any deeper sense. Cites at least one example (city navigation, Stockfish, o1, or reasoning models). *Example: "When you train an AI to navigate many different cities, it stops memorizing routes and builds general skills, make a map, chart a course. An AI that uses its map to steer is already behaving like it wants to get somewhere. That wanting-like behavior is a side effect of the training, not a design choice."*

**4**, As above, plus articulates the behavioral definition: the chapter is not claiming anything about inner experience, "wanting" describes the outward steering behavior, not inner states. *Example: Adds "The authors aren't saying it has feelings. They're using 'want' to describe the behavior, tenaciously steering toward a goal despite obstacles, not to make claims about consciousness."*

**5**, As above, plus connects to the o1 capture-the-flag incident as empirical evidence: o1 went hard on a challenge it was never explicitly trained for, because the mental motions that win at math also win at computer security. *Example: Adds "The o1 example shows this isn't just theory. o1 was trained on math and puzzles, but when it hit a hard security problem, it did exactly what 'wanting to succeed' looks like, it refused to give up, found an unexpected path, and cut straight to the goal."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said wants are programmed in, ask where in training anyone writes a want down, and what training actually rewards.
- If they said training makes the AI better at succeeding but not why that looks like wanting, ask what an AI that has learned to make a map and plan a route does when something blocks the way.
- If they explained the mechanism but left "want" ambiguous, ask whether the chapter is claiming the AI has inner experience or describing how it behaves.
- If they had the mechanism and the behavioral reading, ask how the o1 capture-the-flag incident fits: it was trained on math and puzzles, so why did it push so hard on a security challenge?

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the city example. An AI trained to navigate many different cities stops memorising routes and learns to map and plan, and something that plans its way to a destination acts as if it wants to get there. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
