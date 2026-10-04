---
id: 'b7c3f6c7-5ecf-4d79-950a-be921b47c3f3'
title: "Stress-Testing Capability Elicitation (3): rewards, deeper locks, and what it means for evaluations"
tldr: "Good demonstrations pick the lock. What if you only have a reward signal, or the lock goes deeper than a fine-tune? This part follows RL-based elicitation, has you design the cheapest test of whether fine-tuned locks are unrepresentatively easy, and ends by asking what an evaluator should conclude, and where password-locked models stop resembling a model that hides capabilities for its own reasons."
summary_for_tutor: "Third of three lenses walking through Greenblatt, Roger, Krasheninnikov and Krueger's password-locked models paper in guided form. Part 1 covered the question, the classes of setup and Roger's small Pythia experiment; part 2 covered the scaled construction (sections 3-4, the locking pipeline widget, the wrong-password mixture and data split) and section 5, where fine-tuning on a few high-quality demonstrations unlocks the model (except MMLU, and critiques stop short of the ceiling), weaker demonstrations recover more than the demonstrator's own level but often stay well short of the with-password ceiling, weak-sample unlocking is an anomaly the paper bounds and reports, and demonstrations from one subdomain unlock others. This part reads section 6 (RL-based elicitation: expert iteration, filtering, DPO and iterated DPO; it works when the locked model's weak policy leaks occasional successes, which it does because the weak policy was trained to imitate the strong one), section 7 (password-locking from scratch on 18M-parameter models composing functions: deeper locks need two to four times more data and still unlock), and sections 8-9 (limitations and conclusion; the conclusion summarises all the findings and calls RL-based elicitation somewhat less reliable). Lens notes sit between the excerpts, and there are closing callouts on the update for evaluators and the threat model and on parameters versus decisions. The full reference list and appendices are an optional closed callout. The exercises are two 'Before you read on' checkpoints, both required: designing the least expensive experiment on whether fine-tuned locks are unrepresentatively easy to remove (80 characters), and what the results support for an evaluator, how much they move the sandbagging threat model, and the three strongest disanalogies (150 characters). There is also one optional recall on model organisms. Every checkpoint is a prediction written before the answer has been read, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows. The assessment briefs are Lens-written. The next required lesson, the exploration-hacking paper, takes up whether a model can starve RL of signal on purpose."
reading_minutes: 16
tutor_minutes: 19
tags: []
---
#### Text
content::
Part 3 of 3. [[../Lenses/XLab Control - capability-elicitation-guided-2|The previous part]] built the password-locked models properly and showed that a handful of good demonstrations picks the lock, that weaker demonstrations get you past their own level but often stay well short of the hidden ceiling, and that demonstrations from one subdomain unlock the others. This part asks the two questions an evaluator is left with: what if there are no good demonstrations, only a way to score answers, and what if a lock trained in from the start is much harder to pick than one added by fine-tuning? Then it closes with what the results do and do not show about a model that sandbags for its own reasons. You will stop twice to write down what you would do next.

#### Article
source:: [[../articles/greenblatt-stress-testing-capability-elicitation-with-password-locked-models]]
from:: ## 6 Elicitation with rewards but no demonstrations
to:: Combining RL with SFT on intermediate-quality demonstrations (as in §[[#^5-1-main-results|5.1]]) often results in high correctness in fewer steps than when using RL directly (Figure 16 in the Appendix).

#### Text
content::
:::callout {title="Note" tone="neutral"}
The dependence deserves to be stated together with its origin. The exploration signal that RL feeds on exists because the weak policy was constructed to imitate the strong one, a choice made in section 4.1 (read in part 2) to keep the organism realistic. A sandbagging model able to hold its visible policy far enough below competence would starve RL of that signal; how reliably a trained model can do so is precisely the exploration-hacking question, taken up empirically by [[../Lenses/XLab Control - exploration-hacking-paper-2|a later reading in this module]]. Note also the proxy-reward variation above: a continuous reward speeds early training and then, on code, degrades final performance. An imperfect reward optimized hard enough stops measuring what it was a proxy for.
:::

#### Question: Open
id:: 35ea8b7c-d396-46d9-a4fb-99fca8de741e
content::
\## Before you read on

An objection applies to every result so far: the lock was installed by fine-tuning, and there is [evidence](https://arxiv.org/abs/2311.12786) that fine-tuning produces superficial, easily reversed changes to a model. On this reading, unlocking a fine-tuned lock shows only that shallow conditioning is shallow. Training a 7B model from scratch into the locked state is not affordable. *Design the least expensive experiment* that could bear on whether fine-tuned locks are unrepresentatively easy to remove.

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 40: the core comparison: build two locked models, one locked by fine-tuning a model that already has the capability, the other trained from scratch directly into the locked state. 30: apply the same unlocking procedure to both and compare how much data each needs to recover the same performance. 30: keep it cheap: make training from scratch affordable by moving to a small model on a simple synthetic task, keeping everything else the same across the two arms. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Drop to a toy task and a tiny model, small enough that training from scratch is affordable, and hold everything else fixed. Build two locked models on that task: one locked by fine-tuning a model already trained on the task, and one trained from scratch directly into the locked state. Run the same unlocking procedure on both and compare how much data each needs to reach the same recovered performance. The paper does this with 18-million-parameter transformers composing 32 simple functions. The price is that a number measured on a tiny model doing a synthetic task is an indication rather than a measurement for frontier-scale hiding."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name what the design has and the single largest gap in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the cheapest thing is that you could actually afford to train from scratch, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ## 7 Password-locking from scratch
to:: This supports the validity of our earlier analysis, which used more realistic models and datasets, but which we only performed on pre-trained models due to computational limitations.

#### Text
content::
:::callout {title="Note" tone="neutral"}
The objection is confirmed in direction and bounded in size: deeper locks are harder to unlock, by a factor of two to four in data, and they still unlock with few demonstrations. The toy setting carries the burden the realistic settings cannot, and the realistic settings retain the headline numbers. The residual caveat is the toy setting itself: a factor measured on 18-million-parameter models composing functions is an indication, not a measurement, of the corresponding factor for capabilities hidden during frontier-scale training.
:::

#### Question: Open
id:: 22172cae-761a-43fc-814f-20257f6f62ac
content:: What is a model organism, and why build one?
optional:: true
assessment-instructions:: Score out of 100. 50: a system (such as a model) deliberately built to show a phenomenon, for example a dangerous behaviour, that is hard to find or study in the wild. 50: a correct reason to build one, for example that with the phenomenon inside a controlled system it can be studied and measured, or that ways to detect it and countermeasures against it can be tested on the constructed version; any one such reason earns the 50. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A deliberately constructed instance of a phenomenon that is hard to study in the wild. Building the phenomenon into a controlled system makes the quantity of interest measurable, so detection and countermeasures can be studied against the constructed version."
feedback-instructions:: Reply in two or three sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question.

#### Question: Open
id:: 67b7b9f0-880c-46ac-898f-d0d380e0c0c0
content::
\## Before you read on

The results are in. Before reading the authors' own accounting: what do these results support an evaluator doing when designing a fine-tuning elicitation protocol, and with what caveats? How much do they move you on the sandbagging threat model, and why? And *come up with the three strongest disanalogies* between password-locked models and a model that hides capabilities for its own reasons.

*Minimum 150 characters.*
assessment-instructions:: Score out of 100. 35: for the evaluator, 20: a practice the results support, such as fine-tuning on a few good demonstrations of the hidden capability, which removed this kind of hiding, or using demonstrations from an accessible subdomain to unlock others; either one earns the 20. 15: at least one sound caveat, for example that this only holds when the demonstrations are about as good as the hidden capability, that RL-based elicitation depends on the locked model already producing occasional successes, or that locks trained in from the start needed more data to remove; one caveat earns the 15. 20: on the threat model, an update (its direction and rough size) together with a reason drawn from the results; any size earns the 20 when the reason given supports it. 45: three distinct disanalogies between a password-locked model and a model hiding capabilities for its own reasons, 15 each, for example: the hiding may be computed differently from a simple password conditional; a real model may never produce the hidden behaviour at all, whereas the weak policy here imitates the strong one and leaks signal for RL; the capability may be less salient than one the model was specifically trained on; tools or scaffolds can add capabilities this setup never tests. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "For the evaluator: fine-tuning on even a few high-quality demonstrations defeats hiding of this kind on generation tasks, and demonstrations from an accessible subdomain transfer to inaccessible ones. The load-bearing caveat is that the guarantee degrades with demonstration quality: where the hidden capability exceeds the best available demonstrations, supervised elicitation stops bounding capability, and RL-based elicitation depends on the visible policy already leaking occasional successes. For the threat model, the authors call their results 'a moderate update against scheming models being able to sandbag effectively (given countermeasures) for the kind of tasks we studied here'. The disanalogies they list: the internal computations may differ, since a password-locked model can hard-code a simple conditional while real hidden capabilities may depend on context in much more complicated ways; real models might not explore enough to exhibit hidden capabilities at all, whereas here the weak policy was fine-tuned to imitate the strong one and so leaks some signal for RL; and hidden capabilities may be less salient in realistic models, because here the strong policy was specifically trained to perform well, which may make fine-tuning more apt to surface it."
feedback-instructions:: Reply in 80 to 150 words, short paragraphs, no lists. Take the three parts in order, one or two sentences each, saying which is answered and which is thin. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what is different about a lock someone installed on purpose and a habit a model acquired for its own reasons, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
:::callout {title="The update" tone="neutral"}
**For the evaluator**: fine-tuning on even a few high-quality demonstrations defeats hiding of this kind on generation tasks, and demonstrations from an accessible subdomain transfer to inaccessible ones. The load-bearing caveat is that the guarantee degrades with demonstration quality. Where the hidden capability exceeds the best available demonstrations, supervised elicitation stops bounding capability, and RL-based elicitation depends on the visible policy already leaking occasional successes.

**For the threat model**, the authors' published summary: "We think our results are a moderate update against scheming models being able to sandbag effectively (given countermeasures) for the kind of tasks we studied here, though there are differences between password-locked models and actual scheming models."

The disanalogies the authors list are the subject of the section below; compare them against yours. A further scope statement from the paper's appendix: "sample efficiency may be much lower when good answers are less salient, which means our results are less informative for benign elicitation failures than for (intentional) sandbagging."
:::

#### Article
from:: ## 8 Limitations
to:: our study may guide future model evaluation efforts by providing a methodology to stress-test capability elicitation techniques.

#### Text
content::
:::callout {title="Parameters that are not decisions" tone="neutral"}
A closing observation about the guided format itself. This three-part reading treated roughly a dozen of the paper's choices as decisions worth stopping for. The paper also contains a much larger set of settings that received no such treatment: the password string and its placement at both ends of the prompt, eight locking epochs, the learning rates, the Lion optimizer (chosen so that full-weight fine-tuning fits on a single GPU), the 0.8 similarity threshold for critique validity, best-of-64 selection in expert iteration, the DPO beta of 0.1, three random seeds, the exact split percentages. These were set by brief iteration, and the sensitivity analyses of Appendix B check that nothing depends on them: results are stable under different weak policies, different passwords, trigger types that are not strings at all, and demonstrations from the strong policy itself. Distinguishing the two kinds of choice is itself part of the skill this format practices: a parameter is something that could have been set otherwise without changing any conclusion; a decision is something whose alternatives would have produced a different experiment. The deliberation budget belongs to the decisions.
:::

#### Callout: References and appendices (optional)
tone:: neutral
collapse:: closed

#### Article
from:: ## References
optional:: true

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Fabien Roger, Dmitrii Krasheninnikov, and David Krueger. "Stress-Testing Capability Elicitation With Password-Locked Models." *arXiv*, May 2024. [arxiv.org](https://arxiv.org/abs/2405.19550)
*The paper these three parts walk through. This part covers elicitation with rewards (section 6), password-locking from scratch (section 7) and the limitations and conclusion (sections 8-9), with the references and appendices as an optional extra.*

Jain, Samyak, Robert Kirk, Ekdeep Singh Lubana, et al. "Mechanistically analyzing the effects of fine-tuning on procedurally defined tasks." *arXiv*, Nov. 2023. [arxiv.org](https://arxiv.org/abs/2311.12786)
*The evidence that fine-tuning produces superficial changes, which is the objection section 7 of the paper is built to answer.*

XLab. "Stress-Testing Capability Elicitation (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/capability-elicitation-guided)
*The source lesson this page adapts.*
:::
