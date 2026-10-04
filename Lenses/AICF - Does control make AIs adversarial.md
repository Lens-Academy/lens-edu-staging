---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs adversarial?"
reading_minutes: 8
tutor_minutes: 6
tldr: "If models learn from text that describes AIs as adversaries to be contained, could they become more adversarial? One small 2026 study fine-tuned a model on AI control writing and found it blackmailed more often. The authors list good reasons to be cautious about the result."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, optional lens. The learner reads most of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. This is a 'works and makes things worse' criticism: control discourse and practice might push models toward adversarial personas. Elias Schmied, whose list the learner may have read in this unit, says in a footnote that he does not think putting AI doom stories in the training data is a major factor. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
---
#### Text
content::
A different worry: writing about AIs as adversaries to be watched and contained ends up in the data future models learn from. If models pick up that picture of themselves, control research could make them more adversarial. Dmitrii Gusev and Vili Kohonen tested a small version of this. Read their summary, results and caveats.

#### Article
source:: [[../articles/gusev-investigating-self-fulfilling-misalignment-and-collusion-in-ai-control]]
from:: Does training on AI control literature induce more misaligned models
to:: but those findings were confounded by eval-awareness.

#### Question: Open
id:: 183ccb61-d8fc-4214-b0d3-a7f6f308e163
content::
\## How much does this show?

Suppose someone says: "This study shows that AI control research makes AIs misaligned." What does the study support, and what does it not? What result would make you take the worry more seriously?
feedback-instructions:: The learner weighs the study. What it supports: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%). What it does not show: that control research in pretraining data affects frontier models, that the effect holds outside one environment, or that it is not mean reversion (the authors note rates moved into a 64% to 88% band). Collusion was not found for GPT-4.1, and the Grok 4 collusion was confounded by eval-awareness. Results that would strengthen the worry: the same effect across model families and environments, effects from realistic amounts of control text in pretraining, or a mechanism shown by comparing control text with neutral text of the same length. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.
