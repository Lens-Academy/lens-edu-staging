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
Score {--{"author":"Andreas's AI","timestamp":1794706063965}@@according to--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows++} the {--{"author":"Andreas's AI","timestamp":1794706063965}@@following rubric.
**1**,--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):**++} Cannot explain {++{"author":"Andreas's AI","timestamp":1794706063965}@@where ++}the {--{"author":"Andreas's AI","timestamp":1794706063965}@@mechanism; treats wanting as deliberately programmed. --}{++{"author":"Andreas's AI","timestamp":1794706063965}@@want-like behavior comes from, or holds that the wants are programmed in by the engineers. ++}*Example: "The {--{"author":"Andreas's AI","timestamp":1794706063965}@@engineers program--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@developers give++} the AI {--{"author":"Andreas's AI","timestamp":1794706063965}@@to want--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@a goal++} to {--{"author":"Andreas's AI","timestamp":1794706063965}@@succeed. That's how--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@aim for, and that's what++} it {--{"author":"Andreas's AI","timestamp":1794706063965}@@works."*--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@wants."*++}
{--{"author":"Andreas's AI","timestamp":1794706063965}@@**2**, Understands--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@**Level 2 (21-40):** Says training makes the AI better at succeeding and++} that {--{"author":"Andreas's AI","timestamp":1794706063965}@@training shapes behavior--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@this looks like wanting,++} but {--{"author":"Andreas's AI","timestamp":1794706063965}@@cannot explain why wanting emerges--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@not why succeeding produces want-like behavior++} rather than just {--{"author":"Andreas's AI","timestamp":1794706063965}@@competence. *Example: "The AI learns to do things through training. Over time--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@skill, and gives no example that shows it. *Example: "Training keeps rewarding++} it {--{"author":"Andreas's AI","timestamp":1794706063965}@@gets better at succeeding, and that makes--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@for doing well, so after a while++} it {--{"author":"Andreas's AI","timestamp":1794706063965}@@act--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@acts++} like it wants {--{"author":"Andreas's AI","timestamp":1794706063965}@@things."*--}{++{"author":"Andreas's AI","timestamp":1794706063965}@@to do well."*++}

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
