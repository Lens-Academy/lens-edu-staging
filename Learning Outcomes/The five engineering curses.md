---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses Chapter 10 names (speed, narrow margins, self-amplification, complications, and edge cases), and identify which case study {--{"author":"James's AI","timestamp":1791834896991}@@(Chernobyl or--}{++{"author":"James's AI","timestamp":1791834896991}@@(space probes, Chernobyl,++} computer security) illustrates each."
reading-from: "beginning of chapter"
reading-to: "Those constraints will tend to get in the way of the AI accomplishing one objective or another. And then you are matching your own wits and ability to nail down the edge cases against however much intelligence is flowing through the system, to see if your constraint holds up."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/One chance to get it right]]"
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
content:: Chapter 10 frames AI alignment as a "cursed problem" by drawing on {++{"author":"James's AI","timestamp":1791834896991}@@three ++}engineering {--{"author":"James's AI","timestamp":1791834896991}@@case studies, among them--}{++{"author":"James's AI","timestamp":1791834896991}@@domains (space probes,++} Chernobyl-style nuclear {--{"author":"James's AI","timestamp":1791834896991}@@reactors--}{++{"author":"James's AI","timestamp":1791834896991}@@reactors,++} and computer {--{"author":"James's AI","timestamp":1791834896991}@@security,--}{++{"author":"James's AI","timestamp":1791834896991}@@security)++} to identify a small set of named "curses" that make engineering hard. The chapter argues that all of these curses apply to AI alignment, and that the curse of edge cases applies in a uniquely worse form.

**Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study {--{"author":"James's AI","timestamp":1791834896991}@@(Chernobyl--}{++{"author":"James's AI","timestamp":1791834896991}@@(space probes, Chernobyl,++} or computer security) the chapter uses to illustrate it.**

assessment-instructions::
Score {--{"author":"James's AI","timestamp":1791834896991}@@out of 100: the sum--}{++{"author":"James's AI","timestamp":1791834896991}@@according to the following rubric.

**1** — Cannot recall any++} of the five curses {--{"author":"James's AI","timestamp":1791834896991}@@below, 20 each.

The question asks the learner to name the five engineering curses the chapter identifies and, for each, the case study the chapter uses to illustrate it: the Chernobyl nuclear reactor or computer security. The chapter's mapping:
- Speed:--}{++{"author":"James's AI","timestamp":1791834896991}@@or confuses them with general "AI is hard" claims. *Example: "AI is hard because it's smart and we don't understand it."*

**2** — Recalls one or two curses but cannot map them to the case studies. *Example: "Speed and complexity. Like++} Chernobyl {--{"author":"James's AI","timestamp":1791834896991}@@(the reactor's reactions happen far faster than humans can respond).
- Narrow margins: --}{++{"author":"James's AI","timestamp":1791834896991}@@I think."*

**3** — Names all five curses (speed, narrow margins, self-amplification, complications, edge cases) and correctly maps them: ++}Chernobyl {--{"author":"James's AI","timestamp":1791834896991}@@(a tiny gap between a working reactor and a runaway one).
- Self-amplification: Chernobyl (the failure feeds itself: overheating boils off coolant, which makes--}{++{"author":"James's AI","timestamp":1791834896991}@@illustrates the first four; computer security (buffer overflow / Schneier) illustrates the fifth. *Example: "Speed: Chernobyl, where neutron reactions happen on microsecond timescales. Narrow margins: Chernobyl,++} the {++{"author":"James's AI","timestamp":1791834896991}@@0.65% prompt-critical line. Self-amplification: Chernobyl's RBMK feedback loop where ++}overheating {--{"author":"James's AI","timestamp":1791834896991}@@worse).
- Complications: Chernobyl (an unexpected interaction, such as the--}{++{"author":"James's AI","timestamp":1791834896991}@@boils off coolant which makes overheating worse. Complications: Chernobyl's++} graphite-tipped control rods that turned {--{"author":"James's AI","timestamp":1791834896991}@@the--}{++{"author":"James's AI","timestamp":1791834896991}@@an++} emergency {--{"author":"James's AI","timestamp":1791834896991}@@shutdown--}{++{"author":"James's AI","timestamp":1791834896991}@@SCRAM++} into an {--{"author":"James's AI","timestamp":1791834896991}@@explosion).
---}{++{"author":"James's AI","timestamp":1791834896991}@@explosion.++} Edge cases: computer security {--{"author":"James's AI","timestamp":1791834896991}@@(an unusual input, such as an overlong--}{++{"author":"James's AI","timestamp":1791834896991}@@and buffer overflow attacks like the 280-character++} name {--{"author":"James's AI","timestamp":1791834896991}@@that overflows memory, breaks a system that works on ordinary inputs).

For each curse: 10 for naming it, 10 for giving--}{++{"author":"James's AI","timestamp":1791834896991}@@overrunning memory."*

**4** — As above, plus correctly identifies the role of the space-probe case study (Mars Observer, Climate Orbiter, Polar Lander, Viking 1) as illustrating++} the {--{"author":"James's AI","timestamp":1791834896991}@@chapter's case study for it. Credit plain or close names ("fast", "small margin for error", "feedback loop", "runaway reaction", "unexpected interactions", "too complicated", "weird inputs", "rare cases"). "Nuclear reactor" counts as Chernobyl and "hacking" or "cyber security" counts as computer security. A curse mapped to--}{++{"author":"James's AI","timestamp":1791834896991}@@*before/after gap*: the irreversibility framing that all five curses sit inside. *Example: Adds "The space probes aren't tied to one specific curse. They're the chapter's setup for the broader before/after gap: once the probe launches you can't reach it, just like once an ASI surpasses humans you can't course-correct."*

**5** — As above, plus articulates *why*++} the {--{"author":"James's AI","timestamp":1791834896991}@@wrong case study gets 0 of its 10 for--}{++{"author":"James's AI","timestamp":1791834896991}@@chapter argues edge cases are a different category (they intensify with++} the {--{"author":"James's AI","timestamp":1791834896991}@@case study. If--}{++{"author":"James's AI","timestamp":1791834896991}@@system's intelligence, while++} the {--{"author":"James's AI","timestamp":1791834896991}@@answer grounds a curse in the right case study by describing the chapter's example (for example "the control rods at Chernobyl")--}{++{"author":"James's AI","timestamp":1791834896991}@@other four are physical constraints), and connects this to AI being "grown, not crafted" from M1. *Example: Adds "Speed, narrow margins, self-amplification, and complications are physical constraints++} that {--{"author":"James's AI","timestamp":1791834896991}@@counts.

Model answer, for--}{++{"author":"James's AI","timestamp":1791834896991}@@intelligent and unintelligent systems both face. Edge cases are different: they get worse++} the {--{"author":"James's AI","timestamp":1791834896991}@@feedback, not--}{++{"author":"James's AI","timestamp":1791834896991}@@smarter the adversary is, because++} a {--{"author":"James's AI","timestamp":1791834896991}@@grading checklist: "Speed: Chernobyl. Narrow margins: Chernobyl. Self-amplification: Chernobyl. Complications: Chernobyl. Edge cases: computer security."--}{++{"author":"James's AI","timestamp":1791834896991}@@smarter system can find more obscure exploits. And because AI is grown, not crafted, the engineers don't even know what the edge cases of their own system are. That's the curse stack-up."*++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is hard" answer, ask them to name one curse and the case study that shows it.
- If they named some curses but not all five, or did not map them, tell them plainly which curses they missed and ask which case study the chapter uses for each.
- If they named and mapped all five, ask {++{"author":"James's AI","timestamp":1791834896991}@@what the space probes are there for, since none of the five curses is tied to them: what do the probes show about acting once something is launched?
- If they had the probes, ask ++}why edge cases belong in a different category from the other four, and how that connects to AI being grown rather than crafted.

At full marks, just confirm briefly. Don't cite {--{"author":"James's AI","timestamp":1791834896991}@@point values. --}{++{"author":"James's AI","timestamp":1791834896991}@@level numbers or band names (the learner sees a percentage). ++}If asked about the score, say in plain words what the answer did and the one{--{"author":"James's AI","timestamp":1791834896991}@@ most important--} thing it missed. If they say they don't understand, give one concrete foothold: Chernobyl's control rods, whose graphite tips turned an emergency shutdown into an explosion. Ask which curse that is. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
