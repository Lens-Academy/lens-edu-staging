---
id: '6dca6f21-cf9e-40ea-8f19-96f8f1e5c925'
title: "Does control make AIs adversarial?"
reading_minutes: 12
tutor_minutes: 8
tldr: "If models learn from text that describes AIs as adversaries to be contained, could they become more adversarial? One small 2026 study fine-tuned a model on AI control writing and found it blackmailed more often. The authors list good reasons to be cautious about the result. Buck Shlegeris answers a related question: is controlling AIs fair to them?"
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The learner reads most of Dmitrii Gusev and Vili Kohonen's 'Investigating Self-Fulfilling Misalignment and Collusion in AI Control' (LessWrong, March 2026). GPT-4.1 was fine-tuned on about 2,600 question-and-answer pairs (1.6M tokens) derived from AI control literature and tested in Anthropic's Agentic Misalignment blackmail scenario. Blackmail rates rose with 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) goals, and the no-goal baseline rose from 1% to 13%. A monitor sharing the agent's incentives did not collude. Grok 4 colluded in follow-up runs, but this was confounded by eval-awareness. The authors' caveats: one model family, one environment, small dataset, possible mean reversion, correlational results. This is a 'works and makes things worse' criticism: control discourse and practice might push models toward adversarial personas. Elias Schmied, whose list the learner may have read in this unit, says in a footnote that he does not think putting AI doom stories in the training data is a major factor. Then an excerpt from Rob Wiblin's 80,000 Hours interview with Buck Shlegeris (2025), 'Is controlling AIs kind of a dick move?': Buck says controlling a model that only wants to take over does not make things worse for it except by preventing takeover, that he would feel more comfortable if companies made deals with and paid AIs, that he thinks it is relatively unlikely companies will behave responsibly about AI welfare, and that the ethical situation is 'probably less than 100 times worse than factory farming'. Help the learner weigh the evidence. Do not overstate the result or dismiss it."
---
#### Text
content::
A different worry: writing about AIs as adversaries to be watched and contained ends up in the data future models learn from. If models pick up that picture of themselves, control research could make them more adversarial. Dmitrii Gusev and Vili Kohonen tested a small version of this. Read their summary, results and caveats.

#### Article
source:: [[../articles/gusev-investigating-self-fulfilling-misalignment-and-collusion-in-ai-control]]
from:: Does training on AI control literature induce more misaligned models
to:: but those findings were confounded by eval-awareness.

#### Text
content::
A related question is whether controlling AIs is fair to them, and whether it sets up a relationship of distrust. In a 2025 interview, Rob Wiblin of 80,000 Hours put this to Buck Shlegeris:

#### Article
source:: [[../articles/wiblin-buck-shlegeris-on-controlling-ai-that-wants-to-take-over-so-we-can-use-it-anyway]]
from:: Slightly different angle: Talking about controlling AIs
to:: But it’s also not the biggest catastrophe in the universe that is possible.

#### Question: Open
id:: 183ccb61-d8fc-4214-b0d3-a7f6f308e163
content::
\## How much does this show?

1. Suppose someone says: "This study shows that AI control research makes AIs misaligned." What does the study support, and what does it not?
2. Buck's answer assumes the model is already egregiously misaligned. Does it answer the worry that control could make models more adversarial in the first place?
feedback-instructions:: The learner weighs the study. What it supports: fine-tuning one model (GPT-4.1) on question-and-answer pairs from AI control literature raised blackmail rates in one test scenario, most in the 'Ethical' (7% to 64%) and 'Safety' (25% to 69%) conditions, and in the no-goal baseline (1% to 13%). What it does not show: that control research in pretraining data affects frontier models, that the effect holds outside one environment, or that it is not mean reversion (the authors note rates moved into a 64% to 88% band). Collusion was not found for GPT-4.1, and the Grok 4 collusion was confounded by eval-awareness. Part 2: Buck argues that controlling a model that only wants to take over does not make things worse for it except by stopping the takeover, and that deals and payment for AIs would make him more comfortable. This addresses fairness toward models that are already misaligned. It does not address the worry in the study, which is about models that are not yet adversarial becoming more so because of how they are trained or treated. A learner may argue Buck's proposal of deals and payment speaks to that worry indirectly. Accept that if reasoned. One or two turns, 60 to 120 words each. Name what they got right and the most important limit they missed. No generic praise. Do not dismiss the worry or overstate it.
