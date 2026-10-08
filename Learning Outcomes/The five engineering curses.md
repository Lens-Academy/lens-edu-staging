---
id: 5e722d28-f1ad-487c-8866-43e5d48115ee
learning-outcome: "Enumerate the five engineering curses Chapter 10 names (speed, narrow margins, self-amplification, complications, and edge cases), and identify which case study (Chernobyl or computer security) illustrates each."
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
content:: Chapter 10 frames AI alignment as a "cursed problem" by drawing on engineering case studies, among them Chernobyl-style nuclear reactors and computer security, to identify a small set of named "curses" that make engineering hard. The chapter argues that all of these curses apply to AI alignment, and that the curse of edge cases applies in a uniquely worse form.

**Name the five engineering curses Chapter 10 identifies, and for each one, identify which case study (Chernobyl or computer security) the chapter uses to illustrate it.**

assessment-instructions::
Score out of 100: the sum of the five curses below, 20 each.

The question asks the learner to name the five engineering curses the chapter identifies and, for each, the case study the chapter uses to illustrate {--{"author":"James agent ready-41's AI","timestamp":1791469672379}@@it, from three: space probes,--}{++{"author":"James agent ready-41's AI","timestamp":1791469672379}@@it:++} the Chernobyl nuclear {--{"author":"James agent ready-41's AI","timestamp":1791469672379}@@reactor, and--}{++{"author":"James agent ready-41's AI","timestamp":1791469672379}@@reactor or++} computer security. The chapter's mapping:
- Speed: Chernobyl (the reactor's reactions happen far faster than humans can respond).
- Narrow margins: Chernobyl (a tiny gap between a working reactor and a runaway one).
- Self-amplification: Chernobyl (the failure feeds itself: overheating boils off coolant, which makes the overheating worse).
- Complications: Chernobyl (an unexpected interaction, such as the graphite-tipped control rods that turned the emergency shutdown into an explosion).
- Edge cases: computer security (an unusual input, such as an overlong name that overflows memory, breaks a system that works on ordinary inputs).

For each curse: 10 for naming it, 10 for giving the chapter's case study for it. Credit plain or close names ("fast", "small margin for error", "feedback loop", "runaway reaction", "unexpected interactions", "too complicated", "weird inputs", "rare cases"). "Nuclear reactor" counts as Chernobyl and "hacking" or "cyber security" counts as computer security. A curse mapped to the wrong case study gets 0 of its 10 for the case study. If the answer grounds a curse in the right case study by describing the chapter's example (for example "the control rods at Chernobyl") that counts.

Model answer, for the feedback, not a grading checklist: "Speed: Chernobyl. Narrow margins: Chernobyl. Self-amplification: Chernobyl. Complications: Chernobyl. Edge cases: computer security."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they gave a general "AI is hard" answer, ask them to name one curse and the case study that shows it.
- If they named some curses but not all five, or did not map them, tell them plainly which curses they missed and ask which case study the chapter uses for each.
- If they named and mapped all five, ask what the space probes are there for, since none of the five curses is tied to them: what do the probes show about acting once something is launched?
- If they had the probes, ask why edge cases belong in a different category from the other four, and how that connects to AI being grown rather than crafted.

At full marks, just confirm briefly. Don't cite point values. If asked about the score, say in plain words what the answer did and the one most important thing it missed. If they say they don't understand, give one concrete foothold: Chernobyl's control rods, whose graphite tips turned an emergency shutdown into an explosion. Ask which curse that is. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
