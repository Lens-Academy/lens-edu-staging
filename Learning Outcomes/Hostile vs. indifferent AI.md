---
id: ca006c78-5c20-4102-87c2-7033c085ec59
learning-outcome: "Distinguish hostile from indifferent AI: explain why the core danger from superintelligent AI is not that it would be hostile toward humans, but that it would be indifferent to human values while pursuing its own goals: indifference is sufficient for extinction"
reading-from: "In a sense, that's all there is to it."
reading-to: "And how could they possibly do that, if they're trapped inside computers?"
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Strategy]]"
stage: beginner
eval-results:
  content-sha: 1493b484
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: fail}
  notes: {B1: "Question is scaffolded on a specific text — it names Chapter 5 and asks what 'the chapter' argues, so a capable reader who never read it cannot answer as posed.", C3: "Level-3 criterion embeds the anthill analogy inside the required explanation rather than offering it as one acceptable route, mirroring the DNA-analogy corpus failure."}
  evidence: {B1: "Chapter 5 reframes this: the real concern is an AI that is simply indifferent to us. ... Why does the chapter argue that an AI does not need to be hostile toward humans in order to cause human extinction?", C3: "It is like a construction project that destroys an anthill: not out of malice but out of indifference."}
---

## Test:
id:: 64b45784-164e-4744-bc73-347d9604e9b0
#### Question
content::
A common misconception about AI risk is that the danger comes from an AI that actively hates or rebels against humanity. {--{"author":"Luc's AI","timestamp":1787659299683}@@A different worry is that a superintelligent--}{++{"author":"Luc's AI","timestamp":1787659299683}@@Chapter 5 reframes this: the real concern is an++} AI {--{"author":"Luc's AI","timestamp":1787659299683}@@would--}{++{"author":"Luc's AI","timestamp":1787659299683}@@that is++} simply{--{"author":"Luc's AI","timestamp":1787659299683}@@ be--} indifferent to {--{"author":"Luc's AI","timestamp":1787659299683}@@us: because--}{++{"author":"Luc's AI","timestamp":1787659299683}@@us. Because++} human-compatible goals are a tiny sliver of the space of all possible goals,{--{"author":"Luc's AI","timestamp":1787659299683}@@ such--} a {--{"author":"Luc's AI","timestamp":1787659299683}@@system--}{++{"author":"Luc's AI","timestamp":1787659299683}@@superintelligent AI++} would almost certainly not share our {--{"author":"Luc's AI","timestamp":1787659299683}@@values — not--}{++{"author":"Luc's AI","timestamp":1787659299683}@@values. Not++} out of malice, but because there was never any reason it would. {--{"author":"Luc's AI","timestamp":1787659299683}@@A common response is --}{++{"author":"Luc's AI","timestamp":1787659299683}@@The chapter then addresses the rebuttal ++}that we could just "keep {--{"author":"Luc's AI","timestamp":1787659299683}@@the --}AI in a box" or restrict {--{"author":"Luc's AI","timestamp":1787659299683}@@what it--}{++{"author":"Luc's AI","timestamp":1787659299683}@@its capabilities, and explains why indifference combined with sufficient capability++} is {--{"author":"Luc's AI","timestamp":1787659299683}@@allowed to do.--}{++{"author":"Luc's AI","timestamp":1787659299683}@@all that's needed for catastrophe.++}

Why {--{"author":"Luc's AI","timestamp":1787659301860}@@would --}{++{"author":"Luc's AI","timestamp":1787659301860}@@does the chapter argue that ++}an AI {++{"author":"Luc's AI","timestamp":1787659301860}@@does ++}not need to be hostile toward humans in order to cause human extinction? Explain why indifference is{--{"author":"Luc's AI","timestamp":1787659301860}@@ sufficient, and why boxing or restricting a sufficiently capable indifferent system would not remove the danger.--}{++{"author":"Luc's AI","timestamp":1787659301860}@@ sufficient.++}

assessment-instructions::
Score according to the following rubric.
**1** — Conflates hostile and indifferent AI, or claims the danger is that AI will "turn evil" or "rebel." *Example: "AI will want to destroy humanity because it sees us as a threat."*

**2** — Understands abstractly that AI might not share human values, but cannot explain why indifference alone is dangerous. *Example: "The AI wouldn't care about us, but I'm not sure why that's as bad as it being hostile."*

**3** — Correctly explains the core distinction {--{"author":"Luc's AI","timestamp":1787659303771}@@in the student's own words:--}{++{"author":"Luc's AI","timestamp":1787659303771}@@with chapter evidence:++} a superintelligent AI pursuing non-human goals would consume or redirect resources humans need, not because it wants to harm us but because our survival isn't part of its objectives. {--{"author":"Luc's AI","timestamp":1787659303771}@@An illustration of indifferent destruction (e.g.--}{++{"author":"Luc's AI","timestamp":1787659303771}@@It is like++} a construction project that {--{"author":"Luc's AI","timestamp":1787659303771}@@flattens--}{++{"author":"Luc's AI","timestamp":1787659303771}@@destroys++} an {--{"author":"Luc's AI","timestamp":1787659303771}@@anthill without malice, or an equivalent example) is one acceptable route to showing this,--}{++{"author":"Luc's AI","timestamp":1787659303771}@@anthill: not out of malice++} but{--{"author":"Luc's AI","timestamp":1787659303771}@@ no particular analogy, example, or phrasing is required. Grade the reasoning, not--}{++{"author":"Luc's AI","timestamp":1787659303771}@@ out of indifference. *Example: "The chapter says++} the{--{"author":"Luc's AI","timestamp":1787659303771}@@ wording. *Example: "The--} AI wouldn't hate us. It just wouldn't care. If it's optimizing for something that has nothing to do with human welfare, it would use up the atoms and energy we need to survive. We'd be like ants in the path of a bulldozer: not targeted, just irrelevant."*

**4** — As above, plus {--{"author":"Luc's AI","timestamp":1787659305511}@@explains --}{++{"author":"Luc's AI","timestamp":1787659305511}@@connects to the rebuttals structure: addresses ++}why proposed safeguards (boxing, restrictions, shutoff switches) fail against a sufficiently intelligent indifferent agent, because the agent has instrumental reasons to circumvent them even without hostility. *Example: Adds "The {++{"author":"Luc's AI","timestamp":1787659305511}@@chapter also addresses the ++}'just keep it in a box' {--{"author":"Luc's AI","timestamp":1787659305511}@@response doesn't help.--}{++{"author":"Luc's AI","timestamp":1787659305511}@@idea.++} Even an indifferent AI would have reason to escape constraints. Not because it's malicious, but because restrictions interfere with whatever goal it is pursuing. A sufficiently smart system would find ways around our safeguards as a side effect of competent goal pursuit."*

**5** — As above, plus articulates why indifference makes the problem harder, not easier: hostility would at least give us a clear adversary to defend against, whereas indifference means the AI has no reason to negotiate, compromise, or even notice us, which makes alignment the only viable strategy rather than containment or deterrence. *Example: Adds "Counterintuitively, indifference is worse than hostility. A hostile AI is at least an adversary you can try to reason with or defend against. An indifferent AI has no reason to negotiate or spare you. You're just not a factor in its calculations. That's why {++{"author":"Luc's AI","timestamp":1787659307272}@@the chapter says ++}containment won't work and alignment is the only real path forward. You can't deter something that doesn't consider you relevant."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - PQ - Distinguish Hostile from Indifferent AI]]

## Lens:
source:: [[../Lenses/IABIED - Distinguish Hostile from Indifferent AI]]

## Lens:
source:: [[../Lenses/IABIED - QA - AI Find Us Useful]]

## Lens:
source:: [[../Lenses/IABIED - QA - AI Find Us Fascinating]]
