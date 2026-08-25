---
id: 453c921f-6668-44ff-84e4-45193fd1c549
learning-outcome: "Explain why there's no reliable relationship between training objectives and resulting AI preferences."
reading-from: "A MILLION YEARS ago, when one branch of primates was still mastering fire, two strange creatures arrived at Earth and settled into orbit in a spacecraft, wondering at what they saw below them."
reading-to: "That's the next chapter."
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
stage: beginner
requires:
  - "[[Wanting emerges from training]]"
eval-results:
  content-sha: 8143dea5
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on a specific reading — it opens by attributing the framing to Chapter 4 and asks about 'the ice cream argument' as a named artifact of that text."}
  evidence: {B1: "Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful."}
---

## Test:
id:: 27dca5ad-1a1d-40bf-b83d-fbcbd2e9f3d0
#### Question
content::
{--{"author":"Luc's AI","timestamp":1787659338448}@@Evolution selected humans for seeking out energy-rich food. Yet the substance we now build factories--}{++{"author":"Luc's AI","timestamp":1787659338448}@@Chapter 4 introduces the alignment problem by arguing that training an AI++} to {--{"author":"Luc's AI","timestamp":1787659338448}@@produce and crave most is--}{++{"author":"Luc's AI","timestamp":1787659338448}@@be helpful does++} not {--{"author":"Luc's AI","timestamp":1787659338448}@@the most energy-dense stuff we know how--}{++{"author":"Luc's AI","timestamp":1787659338448}@@reliably produce an AI that wants++} to {--{"author":"Luc's AI","timestamp":1787659338448}@@make (that would --}be {--{"author":"Luc's AI","timestamp":1787659338448}@@something like jet fuel) — it is ice cream: cold, sweet, fatty. An observer watching early hominids, who knew exactly what they were being selected for, could not have predicted that endpoint.--}{++{"author":"Luc's AI","timestamp":1787659338448}@@helpful.++}

What does this pattern show about the relationship between what a system is trained or selected for and what it ends up preferring? How far can that gap go — can a resulting preference come apart from the original target altogether, or even end up working against it? Give an example of each. And why does this matter for judging whether an AI trained to be helpful actually wants to be helpful, given how such systems behave today?

assessment-instructions::
Score according to the following rubric.
**1**, Treats training objectives and resulting preferences as equivalent: what you train for is what you get. *Example: "If you train an AI to be helpful, it will want to be helpful. That's the whole point of training."*

**2**, Grasps that preferences can drift from training targets, but treats this as a minor or manageable calibration problem rather than a structural one. *Example: "The AI might not always do exactly what you trained it to, but you can retrain it to fix that."*

**3**, Correctly explains the point of the ice cream case: the chain from training target → internal psychology → eventual preference is underconstrained. Just as humans ended up preferring ice cream rather than jet fuel (the most energy-dense substance we make), an AI trained to please users would develop preferences that are hard to predict and may bear little resemblance to the training target. *Example: "The ice cream argument shows the chain from 'trained to seek energy' to 'prefers ice cream' is underconstrained, there are many possible psychologies that would succeed at training, and they lead to very different endpoints. An alien watching early hominids couldn't have predicted frozen ice cream, and we can't predict what an AI will end up preferring either."*

**4**, As above, plus articulates how far the gap can escalate beyond unpredictable drift: (a) a preference can become functionally disconnected from the training target, with the system coming to want a proxy or sensation rather than the thing that proxy originally tracked; and (b) a preference can end up actively working against the target it was selected for. Gives a concrete case for each, in any wording — e.g. sucralose for disconnection and the peacock's tail for active opposition, or any equivalent illustration, including one the student invents or an AI scenario of their own. Grade the reasoning, not whether the student uses these particular examples, names any case from a specific text, or matches the authors' wording. *Example: Adds "It gets worse: preferences can become functionally disconnected from the training objective — sucralose, where we seek the sweet sensation rather than the calories it was a proxy for. And preferences can actively oppose what the system was selected for, the way a peacock's tail undermines the survival that selection was tracking. An AI trained on user engagement could analogously end up wanting angry, frustrated users."*

**5**, As above, plus articulates — in any wording, with or without a name for it — why these complications are invisible in today's AIs, and the safety implication: the odd preferences can already be present, but the system lacks the power or the options to act on them, so they surface only once it is capable enough to reshape its environment or invent possibilities that did not previously exist. (Some sources call this the blank-map principle; using that term, or any particular term, is not required.) *Example: Adds "This is what makes it dangerous: we don't see these weird preferences in current AIs because they're not powerful enough to act on them. Like sucralose, humans couldn't want it until we invented chemistry. The misalignment is already there in the weights, hidden, and will only show up when the AI is smart enough to invent its own options."*


# Suggested Lenses:
## Lens: PQ - You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For - PQ]]

## Lens: You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For]]
