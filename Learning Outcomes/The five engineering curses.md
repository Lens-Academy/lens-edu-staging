---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses {--{"author":"Luc's AI","timestamp":1787659317524}@@that make a domain unforgiving to work in--}{++{"author":"Luc's AI","timestamp":1787659317524}@@Chapter 10 names++} (speed, narrow margins, self-amplification, complications, and edge cases), and identify which {--{"author":"Luc's AI","timestamp":1787659317524}@@curse a given real-world failure — e.g. a reactor accident, a lost space probe, a software exploit — illustrates."--}{++{"author":"Luc's AI","timestamp":1787659317524}@@case study (space probes, Chernobyl, computer security) illustrates each."++}
reading-from: "beginning of chapter"
reading-to: "Those constraints will tend to get in the way of the AI accomplishing one objective or another. And then you are matching your own wits and ability to nail down the edge cases against however much intelligence is flowing through the system, to see if your constraint holds up."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Strategy]]"
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

#### {--{"author":"Elias's AI","timestamp":1787667443793}@@Question--}{++{"author":"Elias's AI","timestamp":1787667443793}@@Question: Open
id:: 4aea4672-5c4e-40dd-8cba-45c72551b138++}
content:: {--{"author":"Luc's AI","timestamp":1787659319462}@@Some--}{++{"author":"Luc's AI","timestamp":1787659319462}@@Chapter 10 frames AI alignment as a "cursed problem" by drawing on three++} engineering domains {--{"author":"Luc's AI","timestamp":1787659319462}@@are "cursed":--}{++{"author":"Luc's AI","timestamp":1787659319462}@@(space probes, Chernobyl-style nuclear reactors, and computer security) to identify++} a small set of {--{"author":"Luc's AI","timestamp":1787659319462}@@recurring properties makes failure very hard--}{++{"author":"Luc's AI","timestamp":1787659319462}@@named "curses" that make engineering hard. The chapter argues that all of these curses apply++} to {--{"author":"Luc's AI","timestamp":1787659319462}@@avoid there,--}{++{"author":"Luc's AI","timestamp":1787659319462}@@AI alignment,++} and {--{"author":"Luc's AI","timestamp":1787659319462}@@AI alignment inherits all of them. Three such domains:--}{++{"author":"Luc's AI","timestamp":1787659319462}@@that the curse of edge cases applies in a uniquely worse form.++}

{--{"author":"Luc's AI","timestamp":1787659322000}@@- **An RBMK-type nuclear reactor (the Chernobyl design):** --}{++{"author":"Luc's AI","timestamp":1787659322000}@@**Name ++}the{--{"author":"Luc's AI","timestamp":1787659322000}@@ neutron chain reaction runs on microsecond timescales; the gap between a controllable reaction--}{++{"author":"Luc's AI","timestamp":1787659322000}@@ five engineering curses Chapter 10 identifies,++} and{--{"author":"Luc's AI","timestamp":1787659322000}@@ a runaway one is a fraction of a percent of reactivity; overheating boils off the coolant, which raises reactivity,--}{++{"author":"Luc's AI","timestamp":1787659322000}@@ for each one, identify++} which{--{"author":"Luc's AI","timestamp":1787659322000}@@ worsens the overheating; and the shutdown rods were tipped with graphite, so inserting them to kill the reaction briefly did the opposite first.
- **An uncrewed interplanetary probe:** once it launches, nobody can ever touch it again; a unit-conversion slip--}{++{"author":"Luc's AI","timestamp":1787659322000}@@ case study (space probes, Chernobyl,++} or{--{"author":"Luc's AI","timestamp":1787659322000}@@ a stuck sensor that would be a five-minute fix on the ground ends--}{++{"author":"Luc's AI","timestamp":1787659322000}@@ computer security)++} the{--{"author":"Luc's AI","timestamp":1787659322000}@@ mission instead.
- **Computer security:** a system that behaves correctly on every input its designers imagined still falls --}{++{"author":"Luc's AI","timestamp":1787659322000}@@ chapter uses ++}to{--{"author":"Luc's AI","timestamp":1787659322000}@@ the one input they didn't — an over-long name that overruns a buffer and lets an attacker run code of their own choosing.

**Name the five engineering curses this framework identifies, and for each one, say which of the three domains above best illustrates--}{++{"author":"Luc's AI","timestamp":1787659322000}@@ illustrate++} it.**

assessment-instructions::
Score according to the following rubric.

**1** — Cannot recall any of the five curses or confuses them with general "AI is hard" claims. *Example: "AI is hard because it's smart and we don't understand it."*

**2** — Recalls one or two curses but cannot map them to the case studies. *Example: "Speed and complexity. Like Chernobyl I think."*

**3** — Names all five curses (speed, narrow margins, self-amplification, complications, edge cases) and correctly maps them: Chernobyl illustrates the first four; computer security (buffer overflow / Schneier) illustrates the fifth. *Example: "Speed: Chernobyl, where neutron reactions happen on microsecond timescales. Narrow margins: Chernobyl, the 0.65% prompt-critical line. Self-amplification: Chernobyl's RBMK feedback loop where overheating boils off coolant which makes overheating worse. Complications: Chernobyl's graphite-tipped control rods that turned an emergency SCRAM into an explosion. Edge cases: computer security and buffer overflow attacks like the 280-character name overrunning memory."*

**4** — As above, plus correctly identifies the role of the space-probe case {--{"author":"Luc's AI","timestamp":1787659324692}@@(e.g. Mars--}{++{"author":"Luc's AI","timestamp":1787659324692}@@study (Mars++} Observer, Climate Orbiter, Polar Lander, Viking 1) as illustrating the *before/after gap*: the irreversibility framing that all five curses sit inside. *Example: Adds "The space probes aren't tied to one specific curse. {--{"author":"Luc's AI","timestamp":1787659324692}@@They set up--}{++{"author":"Luc's AI","timestamp":1787659324692}@@They're the chapter's setup for++} the broader before/after gap: once the probe launches you can't reach it, just like once an ASI surpasses humans you can't course-correct."*

**5** — As above, plus articulates *why* {++{"author":"Luc's AI","timestamp":1787659327093}@@the chapter argues ++}edge cases are a different category{--{"author":"Luc's AI","timestamp":1787659327093}@@ from the other four --}{++{"author":"Luc's AI","timestamp":1787659327093}@@ ++}(they intensify with the system's intelligence, while the other four are physical constraints), and connects this to AI being "grown, not {--{"author":"Luc's AI","timestamp":1787659327093}@@crafted".--}{++{"author":"Luc's AI","timestamp":1787659327093}@@crafted" from M1.++} *Example: Adds "Speed, narrow margins, self-amplification, and complications are physical constraints that intelligent and unintelligent systems both face. Edge cases are different: they get worse the smarter the adversary is, because a smarter system can find more obscure exploits. And because AI is grown, not crafted, the engineers don't even know what the edge cases of their own system are. That's the curse stack-up."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
