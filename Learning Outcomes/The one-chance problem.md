---
id: 057e2d7c-1364-4436-a5d6-4d4799f31a0a
learning-outcome: "Explain what the Chernobyl and Titanic analogies get right (humans struggle to believe in unthinkable disasters), and identify the critical disanalogy between those historical cases and an ASI failure that the chapter treats as decisive."
reading-from: "beginning of chapter"
reading-to: "With ASI, there is no second time."
authors:
  - Chris+Claude
concept: "[[../Concepts/One chance to get it right]]"
stage: beginner
eval-results:
  content-sha: f0502c15
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Capability is bound to what Chapter 12 says and treats as decisive, not to a source-independent concept.", B1: "Question makes the chapter load-bearing scaffolding rather than self-containing its context."}
  evidence: {A2: "as Chapter 12 deploys them", B1: "Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world."}
---

## Test:
id:: 7f627b30-5641-48ef-901d-e710813fb828
#### Question: Open
id:: 4fc0ef19-14a5-44cd-96e0-e8d3c6a99f38
content:: Chapter 12 opens by asking why smart, well-meaning people build things that could destroy the world. To make the denial pattern concrete, it draws on two historical disasters: the Chernobyl meltdown and the Titanic sinking. Even when the warning signs are present, both cases show how humans fail to believe that unthinkable disasters can actually happen. The chapter then makes a pivot: it argues these analogies hold only up to a point, because there is one critical way in which an ASI failure differs from both of them.

**A friend says: 'People said the same about Chernobyl and the Titanic, and we learned and got safer, so AI will go the same way.' Which part of that comparison holds, and which part breaks for ASI? Explain why the part that breaks matters so much for how much proof of safety we should demand before building.**

assessment-instructions::
Score {--{"author":"Andreas's AI","timestamp":1794356011634}@@according to --}{++{"author":"Andreas's AI","timestamp":1794356011634}@@out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if ++}the {--{"author":"Andreas's AI","timestamp":1794356011634}@@following rubric.--}{++{"author":"Andreas's AI","timestamp":1794356011634}@@answer states it briefly. An extension shows nothing about points it does not depend on.++}

{--{"author":"Andreas's AI","timestamp":1794356011634}@@**1**:--}{++{"author":"Andreas's AI","timestamp":1794356011634}@@**Level 1 (0-20):**++} Accepts the friend's comparison, or rejects it without saying which part breaks. {++{"author":"Andreas's AI","timestamp":1794356011634}@@Taking "we learned and got safer" as the part that holds is this level. ++}*Example: "Your friend is right, we always learn from disasters."*

{--{"author":"Andreas's AI","timestamp":1794356011634}@@**2**:--}{++{"author":"Andreas's AI","timestamp":1794356011634}@@**Level 2 (21-40):**++} Names only one side: {--{"author":"Andreas's AI","timestamp":1794356011634}@@either --}what holds (people denied the {--{"author":"Andreas's AI","timestamp":1794356011634}@@danger in both cases) --}{++{"author":"Andreas's AI","timestamp":1794356011634}@@danger) ++}or that ASI is different, but not {--{"author":"Andreas's AI","timestamp":1794356011634}@@why there--}{++{"author":"Andreas's AI","timestamp":1794356011634}@@that the difference++} is {++{"author":"Andreas's AI","timestamp":1794356011634}@@having ++}no second chance. {++{"author":"Andreas's AI","timestamp":1794356011634}@@Saying only that AI is more dangerous, or that the disaster would be bigger, is this level: a bigger disaster that people survive can still be learned from. ++}*Example: "People were in denial about Chernobyl and the Titanic too. AI is just more dangerous."*

{--{"author":"Andreas's AI","timestamp":1794356014440}@@**3**:--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@**Level 3 (41-65):**++} Says what holds (in both cases people {--{"author":"Andreas's AI","timestamp":1794356014440}@@denied an unthinkable disaster until it happened) and correctly identifies the decisive disanalogy: with historical disasters,--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@did not believe the disaster could happen, even when warned) and what breaks (after those disasters++} there{--{"author":"Andreas's AI","timestamp":1794356014440}@@ was a second time: investigators could learn, reform safety standards, build better systems;--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@ were people left to investigate and reform;++} with {--{"author":"Andreas's AI","timestamp":1794356014440}@@ASI,--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@ASI++} there is no second {--{"author":"Andreas's AI","timestamp":1794356014440}@@chance, making the denial pattern fatal rather than merely costly. *Example: "Your friend is right that people denied both disasters until they happened: that pattern holds. The critical disanalogy is that after Chernobyl we got nuclear safety reforms,--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@time, so a failure cannot be learned from). At this level the answer does not say why that matters for how much proof of safety to demand. *Example: "People refused to believe both disasters could happen,++} and{--{"author":"Andreas's AI","timestamp":1794356014440}@@ after Titanic we required more lifeboats. But the chapter says 'with ASI, there is no second time.' If you fail,--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@ that part fits AI too. What doesn't fit is that we got to learn from those. With ASI++} there's no {--{"author":"Andreas's AI","timestamp":1794356014440}@@surviving generation to investigate and improve."*--}{++{"author":"Andreas's AI","timestamp":1794356014440}@@second time."*++}

{--{"author":"Andreas's AI","timestamp":1794356017189}@@**4**: --}{++{"author":"Andreas's AI","timestamp":1794356017189}@@**Level 4 (66-85):** ++}As above, plus{--{"author":"Andreas's AI","timestamp":1794356017189}@@ explains--} why the {--{"author":"Andreas's AI","timestamp":1794356017189}@@one-chance structure changes the epistemic burden: with repeatable disasters, learning-by-failure--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@part that breaks matters for how much proof to demand. This part++} is {++{"author":"Andreas's AI","timestamp":1794356017189}@@answered once the answer ties the two: because ++}a {--{"author":"Andreas's AI","timestamp":1794356017189}@@viable if tragic strategy; with ASI, the expected cost of a single failure is total, so the standard--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@failure cannot be learned from, safety has to be shown before building rather than learned afterwards, which asks++} for {--{"author":"Andreas's AI","timestamp":1794356017189}@@proceeding can't --}{++{"author":"Andreas's AI","timestamp":1794356017189}@@far more proof than a technology that can ++}be {--{"author":"Andreas's AI","timestamp":1794356017189}@@the same as for technologies where post-failure correction is possible. *Example: Adds "The disanalogy matters because it changes--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@fixed after it fails. An answer that says only that we should be "more careful" or "very cautious" reaches this level but not fully. Saying as well++} what {--{"author":"Andreas's AI","timestamp":1794356017189}@@you should do about uncertainty. With Chernobyl and Titanic, you could build, observe--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@reforms followed each disaster, or naming the people the chapter draws on, belongs to++} the {--{"author":"Andreas's AI","timestamp":1794356017189}@@failure,--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@same parts++} and {--{"author":"Andreas's AI","timestamp":1794356017189}@@improve. That's a painful but viable path to safer technology. With ASI you can't run that experiment. You have to be confident before you act, not after you've survived--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@is not needed for them. An answer that does all three parts has answered the question in full, and without an extension it stays in this range. *Example: Adds "Since nothing can be learned from++} the first {--{"author":"Andreas's AI","timestamp":1794356017189}@@failure."*--}{++{"author":"Andreas's AI","timestamp":1794356017189}@@failure, being safe has to be shown up front, not found out afterwards."*++}

**5**: As above, plus articulates the self-reinforcing trap the chapter creates: the denial pattern the analogies establish is precisely the psychological barrier to meeting the higher burden of proof the disanalogy requires: the two halves of the argument reinforce each other into a coherent diagnosis. *Example: Adds "There's a painful loop: the analogies show that humans are reliably bad at believing unthinkable disasters can happen, and the disanalogy shows that with ASI, that belief failure would be fatal. The denial pattern isn't just one problem among many; it's the specific barrier to meeting the one-chance problem correctly. The chapter uses the historical cases to prove we are susceptible to exactly the error that would kill us when the stakes are total."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they accepted the comparison, ask what "we learned and got safer" needed after each disaster.
- If they had what breaks but not what holds, ask what people believed about each disaster before it happened.
- If they missed what breaks, ask what happened after each disaster that could not happen after an ASI failure.
- If they had what holds and what breaks, ask what changes about the decision to proceed when you cannot learn from a failure.
- If they had that, ask how the two halves fit together: what does the denial pattern mean for meeting that higher bar?

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: after the Titanic, ships were required to carry more lifeboats. Ask who would be around to write the new rules after an ASI failure. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem]]
