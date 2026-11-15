---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses Chapter 10 names (speed, narrow margins, self-amplification, complications, and edge cases), and identify which case study (space probes, Chernobyl, computer security) illustrates each."
reading-from: "beginning of chapter"
reading-to: "Those constraints will tend to get in the way of the AI accomplishing one objective or another. And then you are matching your own wits and ability to nail down the edge cases against however much intelligence is flowing through the system, to see if your constraint holds up."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: 9cabb69d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is defined as reconstructing what Chapter 10 names and which case study that chapter pairs with each curse, so it depends on knowing a specific text rather than a field-canonical framework.", B1: "Question makes the chapter load-bearing scaffolding, asking what Chapter 10 identifies and which illustration the chapter uses, so a capable non-reader cannot answer as posed."}
  evidence: {A2: "Enumerate the five engineering curses Chapter 10 names", B1: "Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (space probes, Chernobyl, or computer security) the chapter uses to illustrate it."}
---

## Test:
id:: d616e493-ef55-4429-8bae-e93d6fd20b99

#### Question: Open
id:: 55514d28-1482-41f4-ab4d-68d470fced52
content:: Chapter 10 frames AI alignment as a "cursed problem" by drawing on three engineering domains (space probes, Chernobyl-style nuclear reactors, and computer security) to identify a small set of named "curses" that make engineering hard. The chapter argues that all of these curses apply to AI alignment, and that the curse of edge cases applies in a uniquely worse form.

**Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (space probes, Chernobyl, or computer security) the chapter uses to illustrate it.**

assessment-instructions::
Score {--{"author":"Andreas's AI","timestamp":1794783550130}@@according to--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if++} the {--{"author":"Andreas's AI","timestamp":1794783550130}@@following rubric.--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@answer states it briefly. An extension shows nothing about points it does not depend on.++}

{--{"author":"Andreas's AI","timestamp":1794783550130}@@**1** —--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@**Level 1 (0-20):**++} Cannot {--{"author":"Andreas's AI","timestamp":1794783550130}@@recall--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@name++} any of the five {--{"author":"Andreas's AI","timestamp":1794783550130}@@curses--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@curses,++} or {--{"author":"Andreas's AI","timestamp":1794783550130}@@confuses them with--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@gives a++} general {--{"author":"Andreas's AI","timestamp":1794783550130}@@"AI is hard" claims. --}{++{"author":"Andreas's AI","timestamp":1794783550130}@@claim that AI is hard. ++}*Example: "AI is {--{"author":"Andreas's AI","timestamp":1794783550130}@@hard--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@dangerous++} because it's {--{"author":"Andreas's AI","timestamp":1794783550130}@@smart--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@smarter than us++} and we don't understand it."*

{--{"author":"Andreas's AI","timestamp":1794783550130}@@**2** — Recalls--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@**Level 2 (21-40):** Names++} one or two {--{"author":"Andreas's AI","timestamp":1794783550130}@@curses but cannot map them to the --}{++{"author":"Andreas's AI","timestamp":1794783550130}@@of the curses, or names several without saying which ++}case {--{"author":"Andreas's AI","timestamp":1794783550130}@@studies.--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@study the chapter uses for them.++} *Example: {--{"author":"Andreas's AI","timestamp":1794783550130}@@"Speed and complexity. Like Chernobyl I think."*--}{++{"author":"Andreas's AI","timestamp":1794783550130}@@"Things happen too fast, and small mistakes snowball."*++}

**3** — Names all five curses (speed, narrow margins, self-amplification, complications, edge cases) and correctly maps them: Chernobyl illustrates the first four; computer security (buffer overflow / Schneier) illustrates the fifth. *Example: "Speed: Chernobyl, where neutron reactions happen on microsecond timescales. Narrow margins: Chernobyl, the 0.65% prompt-critical line. Self-amplification: Chernobyl's RBMK feedback loop where overheating boils off coolant which makes overheating worse. Complications: Chernobyl's graphite-tipped control rods that turned an emergency SCRAM into an explosion. Edge cases: computer security and buffer overflow attacks like the 280-character name overrunning memory."*

**4** — As above, plus correctly identifies the role of the space-probe case study (Mars Observer, Climate Orbiter, Polar Lander, Viking 1) as illustrating the *before/after gap*: the irreversibility framing that all five curses sit inside. *Example: Adds "The space probes aren't tied to one specific curse. They're the chapter's setup for the broader before/after gap: once the probe launches you can't reach it, just like once an ASI surpasses humans you can't course-correct."*

**5** — As above, plus articulates *why* the chapter argues edge cases are a different category (they intensify with the system's intelligence, while the other four are physical constraints), and connects this to AI being "grown, not crafted" from M1. *Example: Adds "Speed, narrow margins, self-amplification, and complications are physical constraints that intelligent and unintelligent systems both face. Edge cases are different: they get worse the smarter the adversary is, because a smarter system can find more obscure exploits. And because AI is grown, not crafted, the engineers don't even know what the edge cases of their own system are. That's the curse stack-up."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is hard" answer, ask them to name one curse and the case study that shows it.
- If they named some curses but not all five, or did not map them, tell them plainly which curses they missed and ask which case study the chapter uses for each.
- If they named and mapped all five, ask what the space probes are there for, since none of the five curses is tied to them: what do the probes show about acting once something is launched?
- If they had the probes, ask why edge cases belong in a different category from the other four, and how that connects to AI being grown rather than crafted.

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: Chernobyl's control rods, whose graphite tips turned an emergency shutdown into an explosion. Ask which curse that is. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
