---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses Chapter 10 names (speed, narrow margins, self-amplification, complications, and edge cases), and identify which case study (space probes, Chernobyl, computer security) illustrates each."
reading-from: "beginning of chapter"
reading-to: "Those constraints will tend to get in the way of the AI accomplishing one objective or another. And then you are matching your own wits and ability to nail down the edge cases against however much intelligence is flowing through the system, to see if your constraint holds up."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
{++{"author":"Luc's AI","timestamp":1785149311459}@@domain: "[[../Domains/Threat models and pathways to harm]]"
stage: beginner
++}---

## Test:
id:: d616e493-ef55-4429-8bae-e93d6fd20b99

#### Question
content:: Chapter 10 frames AI alignment as a "cursed problem" by drawing on three engineering domains (space probes, Chernobyl-style nuclear reactors, and computer security) to identify a small set of named "curses" that make engineering hard. The chapter argues that all of these curses apply to AI alignment, and that the curse of edge cases applies in a uniquely worse form.

**Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (space probes, Chernobyl, or computer security) the chapter uses to illustrate it.**

assessment-instructions::
Score according to the following rubric.

**1** — Cannot recall any of the five curses or confuses them with general "AI is hard" claims. *Example: "AI is hard because it's smart and we don't understand it."*

**2** — Recalls one or two curses but cannot map them to the case studies. *Example: "Speed and complexity. Like Chernobyl I think."*

**3** — Names all five curses (speed, narrow margins, self-amplification, complications, edge cases) and correctly maps them: Chernobyl illustrates the first four; computer security (buffer overflow / Schneier) illustrates the fifth. *Example: "Speed: Chernobyl, where neutron reactions happen on microsecond timescales. Narrow margins: Chernobyl, the 0.65% prompt-critical line. Self-amplification: Chernobyl's RBMK feedback loop where overheating boils off coolant which makes overheating worse. Complications: Chernobyl's graphite-tipped control rods that turned an emergency SCRAM into an explosion. Edge cases: computer security and buffer overflow attacks like the 280-character name overrunning memory."*

**4** — As above, plus correctly identifies the role of the space-probe case study (Mars Observer, Climate Orbiter, Polar Lander, Viking 1) as illustrating the *before/after gap*: the irreversibility framing that all five curses sit inside. *Example: Adds "The space probes aren't tied to one specific curse. They're the chapter's setup for the broader before/after gap: once the probe launches you can't reach it, just like once an ASI surpasses humans you can't course-correct."*

**5** — As above, plus articulates *why* the chapter argues edge cases are a different category (they intensify with the system's intelligence, while the other four are physical constraints), and connects this to AI being "grown, not crafted" from M1. *Example: Adds "Speed, narrow margins, self-amplification, and complications are physical constraints that intelligent and unintelligent systems both face. Edge cases are different: they get worse the smarter the adversary is, because a smarter system can find more obscure exploits. And because AI is grown, not crafted, the engineers don't even know what the edge cases of their own system are. That's the curse stack-up."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
