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
Score {--{"author":"James's AI","timestamp":1791834860531}@@out of 100: --}{++{"author":"James's AI","timestamp":1791834860531}@@according to ++}the {--{"author":"James's AI","timestamp":1791834860531}@@sum of the two elements below.

The question asks how modern AIs come to show want-like behavior --}{++{"author":"James's AI","timestamp":1791834860531}@@following rubric.
**1**, Cannot explain the mechanism; treats wanting ++}as {--{"author":"James's AI","timestamp":1791834860531}@@a side effect of being trained for success rather than by design, what --}{++{"author":"James's AI","timestamp":1791834860531}@@deliberately programmed. *Example: "The engineers program ++}the {--{"author":"James's AI","timestamp":1791834860531}@@mechanism is, and which example illustrates it. The idea it refers to:--}{++{"author":"James's AI","timestamp":1791834860531}@@AI to want to succeed. That's how it works."*

**2**, Understands that++} training{--{"author":"James's AI","timestamp":1791834860531}@@ rewards whatever gets results. Across many varied tasks, what keeps getting results is not memorised answers --}{++{"author":"James's AI","timestamp":1791834860531}@@ shapes behavior ++}but {--{"author":"James's AI","timestamp":1791834860531}@@general skills: building a picture of the situation (predicting) and choosing actions that lead--}{++{"author":"James's AI","timestamp":1791834860531}@@cannot explain why wanting emerges rather than just competence. *Example: "The AI learns++} to {--{"author":"James's AI","timestamp":1791834860531}@@the goal (steering), and keeping at--}{++{"author":"James's AI","timestamp":1791834860531}@@do things through training. Over time++} it{--{"author":"James's AI","timestamp":1791834860531}@@ when something--} gets{--{"author":"James's AI","timestamp":1791834860531}@@ in the way. A system--}{++{"author":"James's AI","timestamp":1791834860531}@@ better at succeeding, and++} that {--{"author":"James's AI","timestamp":1791834860531}@@reliably steers toward an outcome and works around obstacles behaves as if --}{++{"author":"James's AI","timestamp":1791834860531}@@makes it act like ++}it wants {--{"author":"James's AI","timestamp":1791834860531}@@that outcome. So want-like behavior is selected for, though nobody wrote a want into --}{++{"author":"James's AI","timestamp":1791834860531}@@things."*

**3**, Correctly explains ++}the {--{"author":"James's AI","timestamp":1791834860531}@@system.

70: The mechanism. Training rewards--}{++{"author":"James's AI","timestamp":1791834860531}@@core mechanism: training for++} success{--{"author":"James's AI","timestamp":1791834860531}@@ at tasks, and what it reinforces,--} across{--{"author":"James's AI","timestamp":1791834860531}@@ many--} varied {--{"author":"James's AI","timestamp":1791834860531}@@situations, is the general habit of --}{++{"author":"James's AI","timestamp":1791834860531}@@environments develops separable prediction and ++}steering {--{"author":"James's AI","timestamp":1791834860531}@@toward a goal--}{++{"author":"James's AI","timestamp":1791834860531}@@skills,++} and {--{"author":"James's AI","timestamp":1791834860531}@@persisting around obstacles. That steering is what wanting looks--}{++{"author":"James's AI","timestamp":1791834860531}@@an AI that uses its map to navigate behaves++} like {--{"author":"James's AI","timestamp":1791834860531}@@from outside, so want-like behavior comes out--}{++{"author":"James's AI","timestamp":1791834860531}@@it wants to reach the destination, regardless++} of{--{"author":"James's AI","timestamp":1791834860531}@@ training for success without anyone writing a want in. An answer that only says "it gets better at succeeding, so --}{++{"author":"James's AI","timestamp":1791834860531}@@ whether ++}it{--{"author":"James's AI","timestamp":1791834860531}@@ acts like it--}{++{"author":"James's AI","timestamp":1791834860531}@@ "has"++} wants{--{"author":"James's AI","timestamp":1791834860531}@@ things", without why succeeding needs goal-directed steering, earns--}{++{"author":"James's AI","timestamp":1791834860531}@@ in any deeper sense. Cites++} at {--{"author":"James's AI","timestamp":1791834860531}@@most 30 of these 70.

30: An --}{++{"author":"James's AI","timestamp":1791834860531}@@least one ++}example {--{"author":"James's AI","timestamp":1791834860531}@@from the chapter that illustrates the mechanism, with a sentence on how it shows it. Any fitting example counts, for example:--}{++{"author":"James's AI","timestamp":1791834860531}@@(city navigation, Stockfish, o1, or reasoning models). *Example: "When you train++} an AI {--{"author":"James's AI","timestamp":1791834860531}@@trained --}to navigate many different {--{"author":"James's AI","timestamp":1791834860531}@@cities that learns to map--}{++{"author":"James's AI","timestamp":1791834860531}@@cities, it stops memorizing routes++} and {--{"author":"James's AI","timestamp":1791834860531}@@plan instead of memorising routes, the reasoning model o1 pushing hard and finding an unexpected way through a computer security challenge--}{++{"author":"James's AI","timestamp":1791834860531}@@builds general skills, make a map, chart a course. An AI that uses its map to steer is already behaving like++} it {--{"author":"James's AI","timestamp":1791834860531}@@was not trained for, a chess engine like Stockfish steering--}{++{"author":"James's AI","timestamp":1791834860531}@@wants to get somewhere. That wanting-like behavior is++} a {--{"author":"James's AI","timestamp":1791834860531}@@game toward a win, or natural selection producing creatures full --}{++{"author":"James's AI","timestamp":1791834860531}@@side effect ++}of {--{"author":"James's AI","timestamp":1791834860531}@@preferences while only selecting for survival and reproduction. A fitting example only named, with no link to --}{++{"author":"James's AI","timestamp":1791834860531}@@the training, not a design choice."*

**4**, As above, plus articulates ++}the{--{"author":"James's AI","timestamp":1791834860531}@@ mechanism, earns 15.
Cap at 30 if--}{++{"author":"James's AI","timestamp":1791834860531}@@ behavioral definition:++} the {--{"author":"James's AI","timestamp":1791834860531}@@answer says the wants are deliberately programmed in by engineers.
Model answer, for the feedback,--}{++{"author":"James's AI","timestamp":1791834860531}@@chapter is not claiming anything about inner experience, "wanting" describes the outward steering behavior,++} not {--{"author":"James's AI","timestamp":1791834860531}@@a grading checklist: "Nobody codes a want into an AI. Training just rewards--}{++{"author":"James's AI","timestamp":1791834860531}@@inner states. *Example: Adds "The authors aren't saying++} it {--{"author":"James's AI","timestamp":1791834860531}@@for succeeding. But when an AI is trained to succeed across many different situations, memorising answers stops working, and what gets rewarded is general skill: building a model of--}{++{"author":"James's AI","timestamp":1791834860531}@@has feelings. They're using 'want' to describe the behavior, tenaciously steering toward a goal despite obstacles, not to make claims about consciousness."*

**5**, As above, plus connects to++} the {--{"author":"James's AI","timestamp":1791834860531}@@situation and steering toward the goal, and not giving up when something blocks the way. Something that reliably steers toward an outcome and routes around obstacles is behaving as if it wants that outcome. The chapter's city--}{++{"author":"James's AI","timestamp":1791834860531}@@o1 capture-the-flag incident as empirical evidence: o1 went hard on a challenge it was never explicitly trained for, because the mental motions that win at math also win at computer security. *Example: Adds "The o1++} example shows {--{"author":"James's AI","timestamp":1791834860531}@@it: an AI trained to navigate many different cities stops memorising routes and learns to map and plan, and a system that plans its way--}{++{"author":"James's AI","timestamp":1791834860531}@@this isn't just theory. o1 was trained on math and puzzles, but when it hit a hard security problem, it did exactly what 'wanting++} to {--{"author":"James's AI","timestamp":1791834860531}@@a destination acts like--}{++{"author":"James's AI","timestamp":1791834860531}@@succeed' looks like,++} it {--{"author":"James's AI","timestamp":1791834860531}@@wants--}{++{"author":"James's AI","timestamp":1791834860531}@@refused++} to {--{"author":"James's AI","timestamp":1791834860531}@@get there. The chapter means 'want' in this behavioral sense, not as a claim about feelings."--}{++{"author":"James's AI","timestamp":1791834860531}@@give up, found an unexpected path, and cut straight to the goal."*++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they said wants are programmed in, ask where in training anyone writes a want down, and what training actually rewards.
- If they said training makes the AI better at succeeding but not why that looks like wanting, ask what an AI that has learned to make a map and plan a route does when something blocks the way.
- If they explained the mechanism but {--{"author":"James's AI","timestamp":1791834860531}@@gave no example, or one that doesn't show it,--}{++{"author":"James's AI","timestamp":1791834860531}@@left "want" ambiguous,++} ask{--{"author":"James's AI","timestamp":1791834860531}@@ which case from--}{++{"author":"James's AI","timestamp":1791834860531}@@ whether++} the chapter {--{"author":"James's AI","timestamp":1791834860531}@@shows a system steering toward a goal it was never handed as a want.--}{++{"author":"James's AI","timestamp":1791834860531}@@is claiming the AI has inner experience or describing how it behaves.++}
- If they had the mechanism and{--{"author":"James's AI","timestamp":1791834860531}@@ an example, a good follow-up is whether --}{++{"author":"James's AI","timestamp":1791834860531}@@ ++}the{--{"author":"James's AI","timestamp":1791834860531}@@ chapter is claiming the AI has inner experience or describing how it behaves, or--}{++{"author":"James's AI","timestamp":1791834860531}@@ behavioral reading, ask++} how the o1 capture-the-flag incident fits: it was trained on math and puzzles, so why did it push so hard on a security challenge?

At full marks, just confirm briefly. Don't cite {--{"author":"James's AI","timestamp":1791834860531}@@point values--}{++{"author":"James's AI","timestamp":1791834860531}@@level numbers++} or{--{"author":"James's AI","timestamp":1791834860531}@@ recite the rubric--}{++{"author":"James's AI","timestamp":1791834860531}@@ band names++} (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: the city example. An AI trained to navigate many different cities stops memorising routes and learns to map and plan, and something that plans its way to a destination acts as if it wants to get there. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
