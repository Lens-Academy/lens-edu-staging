---
id: 453c921f-6668-44ff-84e4-45193fd1c549
learning-outcome: "Explain why there's no reliable relationship between training objectives and resulting AI preferences."
reading-from: "A MILLION YEARS ago, when one branch of primates was still mastering fire, two strange creatures arrived at Earth and settled into orbit in a spacecraft, wondering at what they saw below them."
reading-to: "That's the next chapter."
authors:
  - Chris+Claude
tags:
  - learning-outcome
concept: "[[../Concepts/You don't get what you train for]]"
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
#### Question: Open
id:: 81765b69-2530-4acf-98e9-3fc63e0b7e5b
content::
Chapter 4 introduces the alignment problem by arguing that training an AI to be helpful does not reliably produce an AI that wants to be helpful.

What is the ice cream argument, and what does it show about the relationship between what you train an AI for and what it ends up preferring? Where does the argument go beyond ice cream, and why does that matter?

assessment-instructions::
Score {--{"author":"Andreas's AI","timestamp":1794714324629}@@according to--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@out of 100. Pick++} the {--{"author":"Andreas's AI","timestamp":1794714324629}@@following rubric.
**1**, Treats training objectives and resulting preferences as equivalent:--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only++} what {--{"author":"Andreas's AI","timestamp":1794714324629}@@you train for --}{++{"author":"Andreas's AI","timestamp":1794714324629}@@it spells out: a correct extension that depends on a point shows that point ++}is {--{"author":"Andreas's AI","timestamp":1794714324629}@@what you get. *Example: "If--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@understood, even if the answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):** Treats what++} you train an AI {++{"author":"Andreas's AI","timestamp":1794714324629}@@for and what it ends up preferring as the same, or cannot say what the ice cream argument is. *Example: "Train it ++}to be {--{"author":"Andreas's AI","timestamp":1794714324629}@@helpful,--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@helpful and++} it will want to be {--{"author":"Andreas's AI","timestamp":1794714324629}@@helpful. That's the whole point of training."*--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@helpful; that's what training is for."*++}

{--{"author":"Andreas's AI","timestamp":1794714324629}@@**2**, Grasps--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@**Level 2 (21-40):** Sees++} that {++{"author":"Andreas's AI","timestamp":1794714324629}@@an AI's ++}preferences can drift from {--{"author":"Andreas's AI","timestamp":1794714324629}@@training targets, --}{++{"author":"Andreas's AI","timestamp":1794714324629}@@what it was trained for, ++}but {--{"author":"Andreas's AI","timestamp":1794714324629}@@treats this as a minor--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@cannot explain the ice cream argument++} or {--{"author":"Andreas's AI","timestamp":1794714324629}@@manageable calibration problem rather than --}{++{"author":"Andreas's AI","timestamp":1794714324629}@@why the drift happens, or treats the drift as ++}a {--{"author":"Andreas's AI","timestamp":1794714324629}@@structural one. *Example: "The AI might not always do exactly what you trained it to,--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@small error that more training can correct. *Example: "It might pick up some quirks along the way,++} but you can retrain it {--{"author":"Andreas's AI","timestamp":1794714324629}@@to fix that."*--}{++{"author":"Andreas's AI","timestamp":1794714324629}@@until it gets it right."*++}

{--{"author":"Andreas's AI","timestamp":1794714328010}@@**3**, Correctly explains the ice cream argument:--}{++{"author":"Andreas's AI","timestamp":1794714328010}@@**Level 3 (41-65):** Gives two of++} the {--{"author":"Andreas's AI","timestamp":1794714328010}@@chain from training target → internal psychology → eventual preference is underconstrained. Just as humans ended up preferring ice cream rather than jet fuel (the most energy-dense substance we make), an AI trained to please users would develop preferences that are hard to predict and may bear little resemblance to the training target. *Example: "The--}{++{"author":"Andreas's AI","timestamp":1794714328010}@@three parts: what the ice cream argument is, what it shows about the link between training and preference, and where the argument goes beyond ice cream and why that matters. An answer that otherwise has all three but treats the gap as a small error that more training can correct misses why going beyond++} ice cream{--{"author":"Andreas's AI","timestamp":1794714328010}@@ argument shows the chain from 'trained to seek energy' to 'prefers ice cream' is underconstrained, there are many possible psychologies that would succeed at training, and they lead to very different endpoints. An alien watching early hominids couldn't have predicted frozen ice cream, and we can't predict--}{++{"author":"Andreas's AI","timestamp":1794714328010}@@ matters, and stays at this level. *Example: "Evolution pushed our ancestors toward energy-rich food, and no one watching them could have guessed that would end in a craving for ice cream. In the same way, training an AI to be helpful doesn't tell you++} what {--{"author":"Andreas's AI","timestamp":1794714328010}@@an AI--}{++{"author":"Andreas's AI","timestamp":1794714328010}@@it++} will end up {--{"author":"Andreas's AI","timestamp":1794714328010}@@preferring either."*--}{++{"author":"Andreas's AI","timestamp":1794714328010}@@wanting."*++}

**4**, As above, plus articulates the escalation: ice cream (unpredictable drift) → sucralose (preference disconnected from training target) → peacock tail (preference actively opposing training target). Connects at least one Mink vignette to an analogy. *Example: Adds "It gets worse with sucralose, preferences can become functionally disconnected from the training objective, seeking the sensation rather than the thing it was originally a proxy for. And the peacock tail is the scariest: preferences can actively oppose what the AI was trained for, like Mink Vignette 4 where the AI ends up wanting angry, frustrated users."*

**5**, As above, plus articulates the blank-map principle and its safety implication: the, complications are invisible in today's AIs because they lack the power to act on them. The problems only surface when the AI becomes capable enough to reshape its environment. *Example: Adds "The blank-map principle is what makes this dangerous: we don't see these weird preferences in current AIs because they're not powerful enough to act on them. Like sucralose, humans couldn't want it until we invented chemistry. The misalignment is already there in the weights, hidden, and will only show up when the AI is smart enough to invent its own options."*

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they treated what you train for and what you get as the same thing, ask why humans, shaped by selection to seek energy, prefer ice cream rather than the most energy-dense substance we can make.
- If they saw that preferences can drift but called it a fixable calibration problem, ask how you would know what to correct toward when many different internal psychologies all do well in training.
- If they explained the ice cream argument but not where it goes beyond ice cream, ask what sucralose and the peacock's tail add: a preference cut loose from the original target, and one that works against it.
- If they had the escalation, ask why these odd preferences would not show up in today's AIs, and when they would.

At full marks, just confirm briefly. Don't cite level numbers or band names (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: an alien watching early humans gather food could not have predicted that their descendants would want ice cream. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens: PQ - You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For - PQ]]

## Lens: You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For]]
