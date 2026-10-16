---
id: 057e2d7c-1364-4436-a5d6-4d4799f31a0a
learning-outcome: "{--{"author":"James's AI","timestamp":1792149101587}@@Compare --}{++{"author":"James's AI","timestamp":1792149101587}@@Explain what ++}the Chernobyl and Titanic analogies {--{"author":"James's AI","timestamp":1792149101587}@@as Chapter 12 deploys them: explain what each case contributes to the argument that humans --}{++{"author":"James's AI","timestamp":1792149101587}@@get right (humans ++}struggle to believe in unthinkable {--{"author":"James's AI","timestamp":1792149101587}@@disasters--}{++{"author":"James's AI","timestamp":1792149101587}@@disasters)++}, and identify the critical disanalogy between those historical cases and an ASI failure that the chapter treats as decisive."
reading-from: "beginning of chapter"
reading-to: "With ASI, there is no second time."
authors:
  - Chris+Claude
topic: "[[../Domains and Topics/11 Strategy/One chance to get it right]]"
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
Score according to the following rubric.

**1**: Accepts the friend's comparison, or rejects it without saying which part breaks. *Example: "Your friend is right, we always learn from disasters."*

**2**: Names only one side: either what holds (people denied the danger in both cases) or that ASI is different, but not why there is no second chance. *Example: "People were in denial about Chernobyl and the Titanic too. AI is just more dangerous."*

**3**: Says what holds (in both cases people denied an unthinkable disaster until it happened) and correctly identifies the decisive disanalogy: with historical disasters, there was a second time: investigators could learn, reform safety standards, build better systems; with ASI, there is no second chance, making the denial pattern fatal rather than merely costly. *Example: "{--{"author":"James's AI","timestamp":1792149104720}@@Chernobyl shows experts who are directly responsible for a dangerous system denying that anything --}{++{"author":"James's AI","timestamp":1792149104720}@@Your friend ++}is {--{"author":"James's AI","timestamp":1792149104720}@@wrong even as it fails. Titanic shows public belief in 'unsinkable' technology shaping inadequate preparation before the disaster. Together --}{++{"author":"James's AI","timestamp":1792149104720}@@right that people denied both disasters until ++}they{--{"author":"James's AI","timestamp":1792149104720}@@ make the case--}{++{"author":"James's AI","timestamp":1792149104720}@@ happened:++} that{--{"author":"James's AI","timestamp":1792149104720}@@ denial is a recurring human pattern, not an anomaly.--}{++{"author":"James's AI","timestamp":1792149104720}@@ pattern holds.++} The critical disanalogy is that after Chernobyl we got nuclear safety reforms, and after Titanic we required more lifeboats. But the chapter says 'with ASI, there is no second time.' If you fail, there's no surviving generation to investigate and improve."*

**4**: As above, plus explains why the one-chance structure changes the epistemic burden: with repeatable disasters, learning-by-failure is a viable if tragic strategy; with ASI, the expected cost of a single failure is total, so the standard for proceeding can't be the same as for technologies where post-failure correction is possible. *Example: Adds "The disanalogy matters because it changes what you should do about uncertainty. With Chernobyl and Titanic, you could build, observe the failure, and improve. That's a painful but viable path to safer technology. With ASI you can't run that experiment. You have to be confident before you act, not after you've survived the first failure."*

**5**: As above, plus articulates the self-reinforcing trap the chapter creates: the denial pattern the analogies establish is precisely the psychological barrier to meeting the higher burden of proof the disanalogy requires: the two halves of the argument reinforce each other into a coherent diagnosis. *Example: Adds "There's a painful loop: the analogies show that humans are reliably bad at believing unthinkable disasters can happen, and the disanalogy shows that with ASI, that belief failure would be fatal. The denial pattern isn't just one problem among many; it's the specific barrier to meeting the one-chance problem correctly. The chapter uses the historical cases to prove we are susceptible to exactly the error that would kill us when the stakes are total."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they {--{"author":"James's AI","timestamp":1792149107412}@@ran--}{++{"author":"James's AI","timestamp":1792149107412}@@accepted++} the {--{"author":"James's AI","timestamp":1792149107412}@@two cases together into "people ignored warnings", ask what Chernobyl shows about the people running the system and--}{++{"author":"James's AI","timestamp":1792149107412}@@comparison, ask what "we learned and got safer" needed after each disaster.
- If they had what breaks but not what holds, ask++} what {--{"author":"James's AI","timestamp":1792149107412}@@Titanic shows--}{++{"author":"James's AI","timestamp":1792149107412}@@people believed++} about {--{"author":"James's AI","timestamp":1792149107412}@@how people saw the technology beforehand.--}{++{"author":"James's AI","timestamp":1792149107412}@@each disaster before it happened.++}
- If they had one case or no disanalogy, ask what happened after each disaster that could not happen after an ASI failure.
- If they had both contributions and the disanalogy, ask what changes about the decision to proceed when you cannot learn from a failure.
- If they had that, ask how the two halves fit together: what does the denial pattern mean for meeting that higher bar?

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: after the Titanic, ships were required to carry more lifeboats. Ask who would be around to write the new rules after an ASI failure. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem - PQ]]

## Lens:
source:: [[../Lenses/IABIED - The One-Chance Problem]]
