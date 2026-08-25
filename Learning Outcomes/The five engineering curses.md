---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses that make a domain unforgiving to work in (speed, narrow margins, self-amplification, complications, and edge cases), and identify which curse a given real-world failure — e.g. a reactor accident, a lost space probe, a software exploit — illustrates."
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

#### Question
content:: Some engineering domains are "cursed": a small set of recurring properties makes failure very hard to avoid there, and AI alignment inherits all of them. Three such domains:

- **An RBMK-type nuclear reactor (the Chernobyl design):** the neutron chain reaction runs on microsecond timescales; the gap between a controllable reaction and a runaway one is a fraction of a percent of reactivity; overheating boils off the coolant, which raises reactivity, which worsens the overheating; and the shutdown rods were tipped with graphite, so inserting them to kill the reaction briefly did the opposite first.
- **An uncrewed interplanetary probe:** once it launches, nobody can ever touch it again; a unit-conversion slip or a stuck sensor that would be a five-minute fix on the ground ends the mission instead.
- **Computer security:** a system that behaves correctly on every input its designers imagined still falls to the one input they didn't — an over-long name that overruns a buffer and lets an attacker run code of their own choosing.

**Name the five engineering curses this framework identifies, and for each one, say which of the three domains above best illustrates it.**

assessment-instructions::
Score according to the following rubric.

**1** — Cannot recall any of the five curses or confuses them with general "AI is hard" claims. *Example: "AI is hard because it's smart and we don't understand it."*

**2** — Recalls one or two curses but cannot map them to the case studies. *Example: "Speed and complexity. Like Chernobyl I think."*

**3** — Names all five curses (speed, narrow margins, self-amplification, complications, edge cases) and correctly maps them: Chernobyl illustrates the first four; computer security (buffer overflow / Schneier) illustrates the fifth. *Example: "Speed: Chernobyl, where neutron reactions happen on microsecond timescales. Narrow margins: Chernobyl, the 0.65% prompt-critical line. Self-amplification: Chernobyl's RBMK feedback loop where overheating boils off coolant which makes overheating worse. Complications: Chernobyl's graphite-tipped control rods that turned an emergency SCRAM into an explosion. Edge cases: computer security and buffer overflow attacks like the 280-character name overrunning memory."*

**4** — As above, plus correctly identifies the role of the space-probe case (e.g. Mars Observer, Climate Orbiter, Polar Lander, Viking 1) as illustrating the *before/after gap*: the irreversibility framing that all five curses sit inside. *Example: Adds "The space probes aren't tied to one specific curse. They set up the broader before/after gap: once the probe launches you can't reach it, just like once an ASI surpasses humans you can't course-correct."*

**5** — As above, plus articulates *why* edge cases are a different category from the other four (they intensify with the system's intelligence, while the other four are physical constraints), and connects this to AI being "grown, not crafted". *Example: Adds "Speed, narrow margins, self-amplification, and complications are physical constraints that intelligent and unintelligent systems both face. Edge cases are different: they get worse the smarter the adversary is, because a smarter system can find more obscure exploits. And because AI is grown, not crafted, the engineers don't even know what the edge cases of their own system are. That's the curse stack-up."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
