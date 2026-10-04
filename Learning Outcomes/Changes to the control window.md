---
id: '8ac45bab-e276-4365-8b1b-3b678fba0380'
learning-outcome: "For a given change in the world, say whether it moves the capability level at which affordable control of AI models stops working, changes how fast models approach that level, or changes how long developers stay below it, and explain why."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
authors:
  - Elias+Claude

---
## Test:
id:: 99f6e488-dbd0-44da-bfb7-6759f1d41354

#### Question: Open
id:: 819e9530-d31b-438a-8625-9875ff5eac59
content::
Think of the period in which AI models are useful enough to transform safety work but can still be controlled with affordable safeguards. For each change below, say whether it mainly (a) moves the line itself: how capable a model can be before affordable safeguards fail, (b) changes how fast capabilities grow toward that line, without moving it, or (c) changes how long developers choose, or are made, to stay below the line. Explain each in one sentence.

- Labs switch their models to reasoning in an internal compressed format that is 30% cheaper to run and that monitors cannot read.
- Export controls halve the number of chips available to every frontier lab.
- The two leading labs agree that after each new frontier model they will pause further scaling for twelve months and use that model only for safety research.
- Researchers show that paraphrasing a model's messages strips out hidden signals even when the model is much stronger than the paraphraser.
placeholder:: Classify and explain each change
assessment-instructions:: Score out of 100. 25 per change, 12 for the category and 13 for the explanatory sentence. Compressed unreadable reasoning: (a), it lowers the capability level at which safeguards stop working, because monitors lose sight of the model's reasoning. Halving chips: (b), capabilities grow toward that level more slowly, because labs have less compute to train and run stronger models. The twelve-month pause: (c), developers stay below the level for longer, because they deliberately hold off building past it. Paraphrasing that strips hidden signals: (a), it raises the level, because models can no longer coordinate through hidden messages even when much stronger than the paraphraser. A reasoned alternative gets full points when the explanation makes it defensible and shows the learner distinguishes where the line is, how fast it is reached, and how long developers choose or are made to stay below it (for example, that export controls also keep developers below the line for longer). Give credit for each point whenever the answer shows the idea, in any wording. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "Compressed unreadable reasoning: (a), it lowers the level at which safeguards stop working, because monitors lose sight of the model's reasoning. Halving chips: (b), models approach that level more slowly. The twelve-month pause: (c), developers stay below the level for longer before building past it. Paraphrasing that strips hidden signals: (a), it raises the level, because collusion through hidden messages becomes harder even for much stronger models."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner confused where the line is with how fast it is reached, or with how long developers stay below it, say so with one of their own items as the example. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-4]]
notes:: Part A of the two-worlds exercise: sorting what produces each window into the frontier, the curve and the dwell.
## Lens:
source:: [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-3]]
notes:: Introduces the control window and the control frontier.
