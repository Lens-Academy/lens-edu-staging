---
id: b06c9f37-bddd-4ad1-95ab-883437f029eb
learning-outcome: Explain how training for success produces want-like behavior in AI, even without anyone designing wants.
reading-from: '"BEHOLD!" SAID THE Professor. "By cunningly configuring this mere machine—a simple arrangement of copper and sand, animated by tiny flickers of lightning—I have made it play chess!"'
reading-to: "No—we're facing an even harder problem: It's much easier to grow artificial intelligence that steers somewhere than it is to grow AIs that steer exactly where you want."
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
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
#### {--{"author":"Elias's AI","timestamp":1787667309336}@@Question--}{++{"author":"Elias's AI","timestamp":1787667309336}@@Question: Open
id:: 43d49bf0-4a5f-435e-9f39-a21e0f81d65e++}
content:: {--{"author":"Luc's AI","timestamp":1787659337539}@@Modern AI systems are often said to end up with--}{++{"author":"Luc's AI","timestamp":1787659337539}@@Chapter 3 argues that modern AIs will develop++} something like wants, not because anyone designed wants into them, but as a side effect of how they are {--{"author":"Luc's AI","timestamp":1787659337539}@@trained to succeed at tasks. In your own words,--}{++{"author":"Luc's AI","timestamp":1787659337539}@@trained. In your own words, how does the chapter++} explain {++{"author":"Luc's AI","timestamp":1787659337539}@@that? What's ++}the {--{"author":"Luc's AI","timestamp":1787659337539}@@mechanism: how does--}{++{"author":"Luc's AI","timestamp":1787659337539}@@mechanism by which++} training {--{"author":"Luc's AI","timestamp":1787659337539}@@a system to succeed produce--}{++{"author":"Luc's AI","timestamp":1787659337539}@@for success produces++} want-like {--{"author":"Luc's AI","timestamp":1787659337539}@@behavior? Give a concrete--}{++{"author":"Luc's AI","timestamp":1787659337539}@@behavior, and what++} example {--{"author":"Luc's AI","timestamp":1787659337539}@@of an AI system whose behavior--}{++{"author":"Luc's AI","timestamp":1787659337539}@@from the chapter most clearly++} illustrates {--{"author":"Luc's AI","timestamp":1787659337539}@@this.--}{++{"author":"Luc's AI","timestamp":1787659337539}@@this?++}

assessment-instructions::
Score according to the following rubric.
**1**, Cannot explain the mechanism; treats wanting as deliberately programmed. *Example: "The engineers program the AI to want to succeed. That's how it works."*

**2**, Understands that training shapes behavior but cannot explain why wanting emerges rather than just competence. *Example: "The AI learns to do things through training. Over time it gets better at succeeding, and that makes it act like it wants things."*

**3**, Correctly explains the core mechanism: training for success across varied environments develops separable prediction and steering skills, and an AI that uses its map to navigate behaves like it wants to reach the destination, regardless of whether it "has" wants in any deeper sense. Cites at least one {--{"author":"Luc's AI","timestamp":1787659339582}@@apt concrete --}example {--{"author":"Luc's AI","timestamp":1787659339582}@@(e.g. an AI trained to navigate many cities,--}{++{"author":"Luc's AI","timestamp":1787659339582}@@(city navigation,++} Stockfish, o1, or reasoning{--{"author":"Luc's AI","timestamp":1787659339582}@@ models more generally; any equivalent example counts).--}{++{"author":"Luc's AI","timestamp":1787659339582}@@ models).++} *Example: "When you train an AI to navigate many different cities, it stops memorizing routes and builds general skills, make a map, chart a course. An AI that uses its map to steer is already behaving like it wants to get somewhere. That wanting-like behavior is a side effect of the training, not a design choice."*

**4**, As above, plus articulates the behavioral definition: the {--{"author":"Luc's AI","timestamp":1787659341639}@@claim--}{++{"author":"Luc's AI","timestamp":1787659341639}@@chapter++} is not {++{"author":"Luc's AI","timestamp":1787659341639}@@claiming anything ++}about inner experience, "wanting" describes the outward steering behavior, not inner states. *Example: Adds {--{"author":"Luc's AI","timestamp":1787659341639}@@"This isn't--}{++{"author":"Luc's AI","timestamp":1787659341639}@@"The authors aren't++} saying {--{"author":"Luc's AI","timestamp":1787659341639}@@the system--}{++{"author":"Luc's AI","timestamp":1787659341639}@@it++} has feelings. They're using 'want' to describe the behavior, tenaciously steering toward a goal despite obstacles, not to make claims about consciousness."*

**5**, As above, plus connects {--{"author":"Luc's AI","timestamp":1787659343406}@@the mechanism --}to {--{"author":"Luc's AI","timestamp":1787659343406}@@a documented real-world case--}{++{"author":"Luc's AI","timestamp":1787659343406}@@the o1 capture-the-flag incident++} as empirical{--{"author":"Luc's AI","timestamp":1787659343406}@@ evidence (e.g. the--}{++{"author":"Luc's AI","timestamp":1787659343406}@@ evidence:++} o1 {--{"author":"Luc's AI","timestamp":1787659343406}@@capture-the-flag incident: o1 --}went hard on a challenge it was never explicitly trained for, because the mental motions that win at math also win at computer {--{"author":"Luc's AI","timestamp":1787659343406}@@security; any equivalent documented case counts).--}{++{"author":"Luc's AI","timestamp":1787659343406}@@security.++} *Example: Adds "The o1 example shows this isn't just theory. o1 was trained on math and puzzles, but when it hit a hard security problem, it did exactly what 'wanting to succeed' looks like, it refused to give up, found an unexpected path, and cut straight to the goal."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Wanting Emerges from Training]]
