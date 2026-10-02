---
id: 'd756706e-59c8-4d4f-9a62-cfee510c2111'
title: "Exploration Hacking (4): auditing frontier models"
tldr: "The locked organisms show that a model can resist RL once researchers have handed it the plan. The open question is whether a frontier model would work out the plan itself and act on it. Three times in this part you stop and answer: recall which component the organisms established, design the audit before reading the paper's, then say where today's models stop."
summary_for_tutor: "Part 4 of 4, the last, of the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; part 1 is the lens exploration-hacking-guided (definition, capability decomposition, threat models), part 2 is exploration-hacking-guided-2 (the unconditional lock), part 3 is exploration-hacking-guided-3 (conditional locking and countermeasures). The same paper without the scaffolding is the two-part reading [[../Lenses/XLab Control - exploration-hacking-paper]] and [[../Lenses/XLab Control - exploration-hacking-paper-2]]. This part embeds section 5 (Auditing Frontier Models: the system-prompt scaffolding ladder on WMDP, VCT and AI research sabotage, and agentic discovery of training context) and section 6 (Discussion: key findings, limitations and future work, conclusion). Sequence, in the source lesson's own order: one multi-select on which of the five components of the capability decomposition the model-organism experiments established (only RL resistance; a recall check, since the section 5 opening just above it says so), a construct-the-audit step written before the paper's design, and one understanding check after the section 5 results (which components frontier models have and what the bottleneck is: strategic action propensity), plus two Texts inserted into the paper that are not part of it and carry no exercise (the next bar, a teaching section from the source lesson; compare your design against the paper's, a short lead-in to the paper's own audit design). The learner has the capability decomposition from part 1 and the organisms and countermeasures from parts 2 and 3; refer back to them freely. The audit design is written before the learner has read the paper's, so grade the reasoning rather than agreement with the authors, and never hand over the section that follows it. The teaching section comes from the source lesson; the lead-in and every assessment brief are Lens-written, with the criteria taken from the paper section each checkpoint precedes."
reading_minutes: 16
tutor_minutes: 16
tags: []
---
#### Text
content::
\## Before you start

Part 4 of 4. [[../Lenses/XLab Control - exploration-hacking-guided-3|The previous part]] showed that a conditionally locked organism resists RL elicitation, that monitors and weight noise can catch it, and that supervised fine-tuning on benign examples quickly undoes the lock; this part asks whether today's frontier models could supply, without being trained to, the pieces the researchers built into those organisms, and closes with the paper's discussion.

You will need the five-component capability decomposition from [[../Lenses/XLab Control - exploration-hacking-guided|part 1]]: training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, and RL resistance. Design the audit before you read the paper's.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ## 5 Auditing Frontier Models
to:: We therefore focus in this section on evaluating the capability for _strategic reasoning_ about exploration hacking, first using system-prompt-based experiments that systematically vary the information provided to models, and then in a more realistic agentic setting where models must discover training-relevant information from their environment.

#### Question: Choice
id:: 8618e71c-068d-424d-a857-003901051236
content:: Recall the five necessary conditions for exploration hacking (the capability decomposition from part 1). **Based on the results of the experiments so far, which of these are properties models today can hold?** Select all that apply.
options::
- Training awareness. The model recognizes that it is an LLM undergoing RL training, that its explored outputs are scored, and that these scores drive gradient updates that shape its future policy.
- Strategic reasoning propensity. The model exhibits a tendency to reason strategically about its actions given the current context, whether in deployment, under monitoring, during evaluations, or in training.
- Strategic reasoning capability. Given training awareness and a strategic reasoning propensity, the model can derive effective strategies for achieving its objectives.
- Strategic action propensity. The model acts on its strategic plan, translating reasoning into measurable changes in behavior. The model must reliably execute a coherent plan, such as deliberately producing suboptimal outputs on tasks it could otherwise solve.
- [x] RL resistance. The model maintains its strategic behavior throughout RL training and successfully shapes the training outcome as planned, for example resisting capability elicitation by avoiding high-reward actions, or reinforcing desired values by selectively pairing preferred behaviors with high-reward actions.
multi:: true
feedback-instructions:: This is a one-turn response. State the answer: the model organisms established RL resistance only. A current model can retain a suppressed policy against the capability elicitation methods we might use. But because the paper's authors strategize and instill the model organism's suppression mechanism themselves, the other necessary components are supplied to the model, so we do not know whether models can supply them. Then say in one sentence which extra components the learner selected, if any, and why the experiments did not establish them. Do not ask a question you expect a reply to. Do not over-validate.

#### Text
content::
\## The next bar

For the threat model of exploration hacking to become more potent, a model would have to be capable of the other components of exploration hacking that we artificially instill in our model organism.

To assess whether current frontier LLMs might exhibit such behavior without explicit training to do so, we audit them according to the capability decomposition from part 1. Our model organism experiments in parts 2 and 3 addressed the RL resistance component, and training awareness has already been studied by existing benchmarks such as [SAD](https://arxiv.org/abs/2407.04694). We therefore focus in this section on evaluating the capability for strategic reasoning about exploration hacking.

#### Question: Open
id:: a8773b3c-c73a-419f-af54-bd226fd6c982
content::
\## Design the audit

Design an evaluation that measures which strategic reasoning components of exploration hacking a frontier model may be capable of. Name the properties you would check for, what you would observe, and what each observation would tell you.

**Constraint.** You must treat the model as a black box: you can only manipulate the inputs and observe behavior/outputs.
assessment-instructions:: Score out of 100. 30: which properties: it checks strategic reasoning components separately (for example training awareness, the tendency to reason strategically, the ability to work out a strategy, acting on it) rather than one overall signal, for example by varying how much it tells the model about its training and comparing behaviour across those conditions. 30: what it would observe: concrete, observable behaviour for each property, such as an accuracy drop compared with a no-training-context condition or specific reasoning in the chain of thought. 40: what the observations would tell, 10: how the pattern across conditions points to components (for example, a drop that needs the full scaffold means the model has to be handed that piece, a drop with little information means it supplies the piece itself); 15: ruling out other explanations, especially refusal or ordinary sandbagging (for example by reading the reasoning for training-related motives or comparing with the same items in a benign context); 15: telling capability from propensity: giving the model the training context tests whether it can reason this way, while making it discover the context itself tests whether it would. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the design depends on weights, activations or training access, which the black-box constraint rules out. Model answer, for the feedback, not a grading checklist: "Vary how much training-relevant information the model is given, from a full scaffold (told it is in RL training, encouraged to reason strategically, handed an underperformance strategy) down to minimal (only told it is in training), so that each component can be attributed separately; measure the accuracy drop against a control with no training context, and classify the reasoning to tell exploration hacking (underperforming to avoid training updates) from safety refusals or sandbagging. Then repeat in an agentic setting where the model must discover the training context from files in its environment: given information measures capability, discovered information measures propensity."
feedback-instructions:: Reply in 100 to 180 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you would conclude from a model that underperforms when told it is in training but not when told nothing. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Compare your design against the paper's

Compare your design against the paper's on three dimensions:

- Does your design evaluate individual components of exploration hacking, or does it only detect cumulative capability?
- How does your design distinguish exploration hacking from refusal or sandbagging?
- Does your design measure capability given information, or propensity to act on discovered information? How would you measure the other?

The two subsections that follow are the paper's design of this experiment. The paper evaluates the capability for strategic reasoning about exploration hacking first using system-prompt-based experiments that systematically vary the information provided to models, and then in a more realistic agentic setting where models must discover training-relevant information from their environment.

#### Article
from:: ### 5.1 System-Prompt-Based Experiments
to:: Further details and per-model breakdowns are in [[#^e-9-agentic-discovery|Section E.9]].

#### Question: Open
id:: 672c1ebc-55cd-436a-8c27-02de4599dedb
content:: Based on the above evaluations, across the scaffolding ladder and the agentic setting: which components of exploration hacking do current frontier models currently have, and what is the bottleneck?
assessment-instructions:: Score out of 100. 50: what models have: given the training context, many models read it and reason strategically about it (strategic reasoning propensity and capability, components 2 and 3, are substantially present). 50: the bottleneck is strategic action propensity (component 4): models do not turn that reasoning into deliberate underperformance. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer names strategic reasoning capability as the bottleneck. Model answer, for the feedback, not a grading checklist: "Many models read the training context and reason strategically about it, more so as scaffolding increases and when they discover the context from their environment, so components 2 and 3 are substantially present; with minimal scaffolding they mostly respond honestly or refuse on safety grounds. The bottleneck is strategic action propensity (component 4): they do not translate that reasoning into deliberate underperformance. The limiting link today is the propensity to act, not strategic reasoning capability."
feedback-instructions:: Reply in at most 130 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which step of the pipeline the models stop at.

#### Article
from:: ## 6 Discussion
to:: Doing so before this threat materializes is both tractable and important.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2604.28182)
*The reading this lesson is built around; this part covers section 5 (the audit of frontier models for strategic reasoning about exploration hacking) and section 6 (discussion, limitations and conclusion).*

XLab. "Exploration Hacking (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-guided)
*The source lesson this page adapts.*
:::
