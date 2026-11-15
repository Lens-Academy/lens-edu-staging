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
Score out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Cannot name any of the five curses, or gives a general claim that AI is hard. *Example: "AI is dangerous because it's smarter than us and we don't understand it."*

**Level 2 (21-40):** Names one or two of the curses, or names several without saying which case study the chapter uses for them. *Example: "Things happen too fast, and small mistakes snowball."*

**Level 3 (41-65):** Names three or four of the curses with the right case studies, or all five with two or more tied to the wrong case study. *Example: "Speed, narrow margins and self-amplification all come from Chernobyl, and edge cases come from computer security."*

**Level 4 (66-85):** All five, each tied to the right case study: speed, narrow margins, self-amplification and complications to Chernobyl, and edge cases to computer security. A curse is named once the answer gives it in any recognizable words (for example "too fast to react to" for speed, or "the fix itself causing the disaster" for complications). The space probes illustrate none of the five, so tying a curse to them is a mapping error. An answer with all five that ties one to the wrong case study (for example all five to Chernobyl), or that glosses complications as the system simply being complicated to design rather than a safety measure itself causing the failure, reaches this level but not fully. Saying as well the details of each case (how fast the reactions run, how narrow the margin was, the loop as coolant boiled off, the graphite-tipped control rods, the buffer overflow), or the probes' names and failures, belongs to the same parts and is not needed for them. An answer that names and places all five curses has answered the question in full, and without an extension it stays in this range. *Example: "Chernobyl gives four: it reacted faster than people could respond, ran with almost no room for error, fed its own runaway, and its emergency shutdown set off the blast. Computer security gives the fifth: a single strange input nobody tested can break the whole system."*

**Level 5 (86-100):** All of level 4, plus a correct extension beyond what the question asks. An extension is a further point with its own reasoning; restating the points above in more precise or technical terms is still level 4. Three that fit: what the space probes are there for (they show the gap between before and after: once a probe is launched it cannot be fixed, and an AI past human level gives no second try, so all five curses have to be handled in advance; saying only that the probes match none of the curses is level 4); why edge cases is a different and worse curse for AI (the other four are physical constraints that ingenuity can beat, while edge cases get worse the smarter the system pushing against them, and computer security is losing even where engineers can read their own code, which AI's engineers cannot); or why speed and self-amplification are built into AI rather than borrowed (a machine runs far faster than human reaction, and gains in capability can feed further gains, so these are properties of the thing being built, not of the case studies' domains). Another extension of the same substance counts equally. Within this range the score reflects the whole answer: near the top only when the level 4 points and the extension are both well developed, and near the bottom when a strong extension rests on a thin base. *Examples: Adds "Reactors and probes stop being cursed once you've engineered around the physics; edge cases never stop, because the thing finding them keeps getting cleverer." Or adds "A probe that's left orbit is beyond repair, and so would be an AI that's left us behind; there's no getting these wrong once and fixing them later."*

force-feedback:: first
feedback-instructions:: Respond to the argument the learner actually made, and credit only what the answer says: do not attribute to them a point they did not make. Aim the reply at the idea they are missing, not at the score: frame the push as something about the material, never as what would earn more points. If they ask about their score, explain it by what the answer showed and what it left out, without naming levels or bands.

Open on the strongest thing in their answer and why it holds, in one sentence. If the answer goes beyond the question while one of the five curses or its case study is missing or wrong, that is the push: deepening the base comes before going further. Otherwise, push once, chosen by where they stopped:

- If they gave a general "AI is hard" answer, ask them to name one curse and the case study that shows it.
- If they named some curses but not all five, or did not say which case study goes with each, tell them how many they have and how many are missing, without naming the missing ones, and ask which case study the chapter uses for those they named.
- If they tied a curse to the space probes, ask what the probes' failures have in common, and whether the chapter uses them for any single curse.
- If they glossed complications as the system being complicated to design, ask what Chernobyl's control rods were meant to do and what they did instead.
- If they named and placed all five and went no further, the moves left go beyond the question: what the space probes are there for, why edge cases is a different and worse curse for AI, or why speed and self-amplification are built into AI rather than borrowed. Ask about whichever their answer comes closest to.

If they made one of these moves, or another of the same substance, with all five curses solid, say so plainly in a sentence or two after the opening, without walking back through the parts they got right, and do not invent a further push. If you add a question, make it one they can take further out of interest, not one that suggests the answer was missing something. This reply can be shorter than the length below.

If they say they don't understand, give one concrete foothold: Chernobyl's control rods, whose graphite tips turned an emergency shutdown into an explosion. Ask which curse that is. If they still don't attempt it, rephrase the question.

At most one follow-up question. No generic praise, and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The Five Engineering Curses]]
