---
id: 453c921f-6668-44ff-84e4-45193fd1c549
learning-outcome: "Explain why there's no reliable relationship between training objectives and resulting AI preferences."
reading-from: "A MILLION YEARS ago, when one branch of primates was still mastering fire, two strange creatures arrived at Earth and settled into orbit in a spacecraft, wondering at what they saw below them."
reading-to: "That's the next chapter."
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/You don't get what you train for]]"
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
Score out of 100: the sum of the four elements below.

Facts the grader needs: the ice cream argument compares AI training to evolution. Evolution selected humans for survival and reproduction, which included seeking energy-rich food. What humans ended up with are taste preferences (sweet, fatty, cold, creamy), and once we could make new foods we came to love ice cream, which nobody could have predicted from "seek energy", and which is not even the most energy-dense food available. The chapter then goes further: sucralose, where people seek the sweet taste with no calories at all, so the preference has come loose from what it originally tracked, and the peacock's tail, where a preference produced by selection works against survival. It applies this to AI with stories of an AI trained to please users ending up wanting strange things, up to something that works against the users. It also argues that such preferences can stay invisible in today's AIs and only show once an AI has the power and options to act on them.

30: What the ice cream argument is: selection or training for one target (energy, survival) produced preferences (for tastes) that, in a new environment, lead somewhere nobody would predict from the target, such as ice cream. Any accurate retelling of this in the learner's own words earns the 30.

25: What it shows about AI: the training objective does not determine what the AI ends up preferring. Many different inner preferences do well during training, and they can lead to very different, hard-to-predict wants once the AI is outside training. So training an AI to be helpful does not reliably make it want to be helpful.

25: Where the argument goes further than ice cream: at least one of these, explained. A preference can lose its link to the target entirely (sucralose, or any similar case of seeking the signal without the thing it tracked). A preference can work against the target (the peacock's tail, or an AI trained to please users that ends up wanting something bad for them). Such preferences can be hidden until the AI is powerful enough to act on them.

20: Why that matters: it means the gap is not just mild, correctable drift. The AI's real preferences could be unrelated to or opposed to what it was trained for, and could fail to show up in testing, so good behavior during training is weak evidence about what a more capable AI will want. Any one of these reasons, clearly tied to the point made in the previous element, earns the 20.

Cap at 30 if the answer says that training for an objective reliably produces that preference.

Model answer, for the feedback, not a grading checklist: "Evolution 'trained' humans to get energy, and what we ended up with was a taste for sweet and fatty things. Put in a world with freezers and sugar, that taste made us love ice cream, which nobody could have predicted from 'get energy'. The lesson is that the link from training target to final preference is loose: many inner drives pass training equally well and then go different ways in new situations. So training an AI to be helpful doesn't make it want helpfulness. The argument then goes further. With sucralose, the preference has lost its link to the target, we chase sweetness with no energy at all. The peacock's tail shows a preference that works against survival. That matters because the AI's real wants might not just be a bit off, but unrelated to or opposed to what we trained for, and they might not show until the AI is capable enough to act on them."

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they treated what you train for and what you get as the same thing, ask why humans, shaped by selection to seek energy, prefer ice cream rather than the most energy-dense substance we can make.
- If they saw that preferences can drift but called it a fixable calibration problem, ask how you would know what to correct toward when many different internal psychologies all do well in training.
- If they explained the ice cream argument but not where it goes beyond ice cream, ask what sucralose and the peacock's tail add: a preference cut loose from the original target, and one that works against it.
- If they had the escalation but not why it matters, ask why these odd preferences would not show up in today's AIs, and when they would.

At full marks, just confirm briefly. Don't cite point values or recite the rubric (the learner sees a percentage). If asked about the score, say in plain words what the answer did and the one thing it missed. If they say they don't understand, give one concrete foothold: an alien watching early humans gather food could not have predicted that their descendants would want ice cream. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens: PQ - You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For - PQ]]

## Lens: You Don't Get What You Train For
source:: [[../Lenses/IABIED - You Don't Get What You Train For]]
