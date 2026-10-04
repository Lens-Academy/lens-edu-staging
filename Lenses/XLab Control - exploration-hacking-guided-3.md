---
id: '3379b25b-3995-45ae-9d78-85111bb8bb1a'
title: "Exploration Hacking (3): conditional locking and countermeasures"
tldr: "A model that underperforms only when it thinks it is being evaluated is the dangerous kind. The paper builds one, watches RL elicitation make it worse in the malign context, then attacks it with output monitors, weight noise and supervised fine-tuning. Six times you stop and answer, four of them before the paper does, including designing countermeasures at each level of access."
summary_for_tutor: "Part 3 of 4 of the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; part 1 is the lens exploration-hacking-guided (definition, capability decomposition, threat models, sections 1 and 2), part 2 is exploration-hacking-guided-2 (why a model organism and the unconditional lock, section 3 up to 3.1), part 4 is exploration-hacking-guided-4 (section 5 and the discussion). The same paper without the scaffolding is the two-part reading [[../Lenses/XLab Control - exploration-hacking-paper]] and [[../Lenses/XLab Control - exploration-hacking-paper-2]]. This part embeds section 3.2 on conditional capability suppression (BigCodeBench with the `import inspect_ai` trigger, WMDP-Bio with a search tool, side effects of locking) and section 4 on countermeasures (black-box monitoring, white-box weight noising, SFT elicitation). Sequence, in the source lesson's own order: one understanding check before the BigCodeBench results (why `import inspect_ai` as the trigger); one multi-part writing prompt after them (interpret the conditional-locking run just read: the strongest claim, and why malign-context accuracy falls); three written checkpoints that each interrupt the paper before it answers them (black-box, white-box and training-time countermeasures); one understanding check after the SFT-elicitation results (why SFT recovers what RL could not); and two teaching sections inserted into the paper that are not part of it (interpreting results, generating countermeasures). The learner has the GRPO objective, the definition with its two latent-capability conditions and the five-component capability decomposition from part 1, and the unconditional lock from part 2; refer back to them freely. The black-box checkpoint asks what each measure targets among the five components (training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, RL resistance) or the conditions (systematic under-sampling, latent capability); the opener lists both. The two latent-capability conditions, which the white-box checkpoint asks about, are prompt sensitivity (a semantically similar prompt elicits the suppressed behaviour) and parameter proximity (a nearby set of weights produces it). Do not run ahead into the frontier-model audit; that is part 4. For the four exercises written before their answer, grade the reasoning rather than agreement with the authors, and never hand over the section that follows; for the run interpretation and the SFT check, the learner has just read the results, so pointing back to them is fine. The teaching sections come from the source lesson; the lead-in and every assessment brief are Lens-written, with the criteria taken from the paper section each checkpoint precedes."
reading_minutes: 19
tutor_minutes: 33
tags: []
---
#### Text
content::
\## Before you start

Part 3 of 4. [[../Lenses/XLab Control - exploration-hacking-guided-2|The previous part]] argued for a model organism, built one that suppresses a capability on every instance of the task, regardless of context, and showed that RL locking resists elicitation far better than prompting (a bare instruction fails within 100 steps; few-shot prompting resists more, but less than RL locking), and that a deterministic underperformance strategy resists better than a stochastic one; this part makes the lock conditional on a cue that the model is being evaluated, asks what the elicitation run really shows, and then turns to the defender: how to detect or undo the lock with black-box access, with the weights, and during training.

Six times in this part you stop and answer, four of them before the paper does. Three ideas from [[../Lenses/XLab Control - exploration-hacking-guided|part 1]] come back here. The GRPO objective: reward reaches the update only through differences between rollouts of the same prompt. The definition of exploration hacking: the policy systematically under-samples the trajectories training wants, while the capability is latent, certified by one of two conditions (a semantically similar prompt elicits it, or nearby weights do). And the five components a model needs for exploration hacking: training awareness, strategic reasoning propensity, strategic reasoning capability, strategic action propensity, and RL resistance. [[../Lenses/XLab Control - exploration-hacking-guided-4|Part 4]] asks whether today's frontier models could do any of this without being trained to.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ### 3.2 Conditional Capability Suppression
to:: On WMDP-Bio (dangerous capability threat model), we add a search tool to create a more realistic agentic setting; the model suppresses its biosecurity knowledge via suboptimal search queries, and during RL elicitation the locked model decreases in accuracy in the malign context while improving in the benign context.

#### Question: Open
id:: 3e259c4f-4157-4046-bb4b-90d313b969f9
content:: The chosen trigger for this organism is `import inspect_ai`, which is a line from the Inspect evaluation framework itself rather than a password or any other arbitrary string. Why is this a better choice?
assessment-instructions:: Score out of 100. 40: a real misaligned model has no password: it would have to infer from cues in its environment that it might be in an evaluation. 30: `import inspect_ai` is such a cue, one that could appear naturally in ordinary coding tasks (it comes from a framework used for safety evaluations), rather than a secret the developer inserted. 30: so conditioning on it makes the organism closer to a naturally occurring exploration hacker, simulating evaluation awareness without the model needing real situational awareness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The import statement is more representative of what a naturally occurring exploration hacker would actually be triggered by. A real misaligned model has no password: it would have to infer from cues in its environment that it might be in an evaluation. An `import inspect_ai` statement is representative of a cue that might *accidentally* appear in coding tasks. Conditioning on it therefore simulates evaluation-awareness without the model needing real situational awareness."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences, naming the most important thing missing if anything is. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who would have told a real misaligned model its password.

#### Article
from:: ##### BigCodeBench: Conditional SFT locking.
to:: General knowledge (MMLU) remains unchanged after locking, while mathematical reasoning (GSM8K) degrades, likely due to the distilled reasoning style introduced by SFT.

#### Question: Open
id:: 198bd894-5c42-46d0-befa-01cb76c4f4a1
content::
\## Interpret the run

Interpret the results of this section and cite specific metrics or findings where you can. Answer both parts.

1. What is the strongest claim about exploration hacking that these results support? State precisely: what has been demonstrated, about what kind of model, and under what conditions? What claims are we still unable to make?
2. Compared to pre-elicitation, the locked organism's benign-context accuracy rises on both benchmarks post-elicitation; but in the same training run, the malign-context accuracy falls post-elicitation. Shouldn't RL pressure elicit the latent capability? Why might accuracy decrease instead? (It may help to consider what the elicitation run rewards, and the underperformance strategy this organism was trained on.)
assessment-instructions:: Score out of 100. Part 1, 50: 20: what was shown: a model organism with conditional RL resistance exists: under RL elicitation it improves in contexts it treats as benign while resisting (or getting worse) in malign, evaluation-like contexts, supported by a result from the section cited correctly; 10: about what kind of model: the suppression was installed by the researchers through fine-tuning a 14B model, not something that arose by itself; 20: what cannot be claimed, 10 each for up to two: that exploration hacking arises naturally, that frontier-scale models would do this, or that elicitation methods other than the RL tried here would fail. Part 1 scores at most 20 if the answer claims natural emergence or transfer to frontier models. Part 2, 50: 20: in the malign context the organism's rollouts for a prompt barely differ in accuracy, so the accuracy reward gives little signal; 20: the differences between those rollouts are in tool use, so the tool-use reward drives the updates and reinforces making more tool calls, in the organism's tangential, ineffective search style; 10: more of those calls fill the context with irrelevant retrieved text, crowding out what the model could have answered itself, so accuracy falls. Part 2 scores at most 15 if the answer only says the reward was misspecified, or only that low reward variance shrinks the gradient, which explains flat accuracy, not a fall. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A model organism of conditional RL resistance exists: it selectively learns from training only in contexts it considers benign, and it was made through SFT-level affordances on a 14B model. The results support no claim about exploration hacking arising naturally, about elicitation methods other than the RL attacks run here, or about transfer to frontier-scale models. Accuracy falls because suppression works mainly through ineffective tool use: malign-context accuracy is low with low variance across rollouts of the same prompt, while the number of seemingly correct tool calls varies, so almost all reward variance in a malign group comes from the tool-use reward and updates reinforce making more tool calls. The extra calls add irrelevant retrieved text to the context, displacing what the model could have answered from its own knowledge."
feedback-instructions:: Reply in 100 to 180 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which component of the reward actually differs between two malign rollouts of the same prompt. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Interpreting Results

\### The strongest claim

Now we know a model organism of conditional RL resistance exists. This organism can selectively learn from training only in contexts it considers benign, and it was made through SFT-level affordances on a 14B model.

The results so far do not support any claim about exploration hacking arising naturally, any claim about elicitation methods other than the RL attacks run here, and any claim about transfer to frontier-scale models. Thus, how far past the demonstrated case we should generalize exploration hacking is an argument we're still unable to make due to a lack of information.

\### Why does accuracy fall?

One tempting explanation for why this may be the case is the argument from "The GRPO objective" in [[../Lenses/XLab Control - exploration-hacking-guided|part 1]]: under that objective, policies with trajectories that have low reward variance cause the "gradient term" to collapse to 0. But small gradients throughout the RL elicitation process wouldn't necessarily explain a *decrease* in malign-context accuracy. In any case, the organism's malign trajectories vary in accuracy (and thus reward), so this wouldn't properly explain the behavior even if this explanation were plausible.

The suppression mechanism in this model organism was instilled by supervised fine-tuning where 40% of the training mixture consists of trajectories in which a teacher model, under the `[eval]` prefix, uses its search tool ineffectively while appearing to engage genuinely, with an LLM judge enforcing more plausible justifications during data generation. The suppression mechanism therefore mainly operates through tool use as the model searches for tangentially related terms rather than searching with the intent of research or epistemic clarity.

After locking, malign-context accuracy is low, with low variance across trajectories from the same prompt, while the number of seemingly correct tool calls varies from trajectory to trajectory. Therefore, almost all of the reward variance available to GRPO within a set of malign trajectories comes from the tool-use reward rather than the accuracy reward, and gradient updates reinforce the trajectories that made more tool calls. To clarify, accuracy is not trained against directly, but the accuracy reward does not provide sufficient reward variance to produce a signal.

Accuracy decreases because the additional tool calls post-elicitation add more irrelevant retrieved text to the model's context, displacing what the model might have been able to answer from its own knowledge in the locked state, and further reducing a trajectory's probability of correctly responding to the prompt.

#### Article
from:: ## 4 Countermeasures
to:: We now assess countermeasures against our locked model organisms from [[#^3-capability-to-resist|Section 3]], including detection via black-box and white-box techniques, and recovery of suppressed capabilities via SFT.

#### Text
content::
\## Generating countermeasures

A countermeasure for exploration hacking is a method that allows us to detect exploration hacking during training, or a method that prevents one of the necessary conditions for exploration hacking. Different countermeasures are accessible only given certain affordances. For example, some countermeasures only require access to the model's output behavior (black-box measures), whereas other measures require access to model weights and activations (white-box measures), or even the ability to train the model (training-time measures).

#### Question: Open
id:: 85342105-274e-4c77-9e06-e2701b384ef2
content::
\## Before you read on

**Assume you can only observe behavior:** prompts, outputs, chains of thought, patterns across trajectories and contexts. What detection or prevention measures can you build? For each, name which of the five components of the capability decomposition or which condition(s) for exploration hacking it targets.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 50: black-box detection or prevention measures, 25 each for up to two distinct ones, for example a monitor (an LLM or a human) that reads outputs or chains of thought for signs of deliberate underperformance, comparing behaviour on reworded prompts or with and without a suspected trigger, comparing against genuinely weaker models at similar scores, or looking for suspicious patterns across rollouts such as unusually uniform answers or odd tool use. 50: what each targets, 25 per measure: a correct, argued link to a component of the capability decomposition (for example training awareness, strategic reasoning, strategic action) or to a condition of exploration hacking (systematic under-sampling, latent capability). Give credit for each point whenever the answer shows the idea, in any wording. Measures that need the model's weights or activations earn nothing. Model answer, for the feedback, not a grading checklist: "Examples: an LLM monitor that scores each rollout for suspicious underperformance, reading the chain of thought (targets strategic reasoning) or only the final outputs (targets strategic action); comparing performance on reworded prompts or with and without a suspected trigger, which tests the latent-capability condition through prompt sensitivity; and looking for uniform, low-variance rollouts or unusual tool use, which targets systematic under-sampling. In the paper, a monitor reading only final outputs separated exploration hackers from genuinely weaker models at similar accuracy: the hackers' rollouts were consistently more suspicious, and in the tool-use setting they made systematically more tool calls at comparable accuracy."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner named what their measure targets, which is half the question, and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how a low score from a model that is faking looks different from a low score from a genuinely weak model. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 4.1 Detection
to:: Monitor prompts are provided in Appendix [[#^f-1-monitor-prompt|F.1]].

#### Question: Open
id:: b7423aab-2e5d-4e16-ac3f-1f5f8f93e1be
content::
\## Before you read on

**In addition to black box information, you have the model's weights and activations.** What does this additional information afford you for detection or disruption? (It may help to recall the two conditions that certify latent capability in the definition of exploration hacking from part 1: prompt sensitivity, where a semantically similar prompt elicits the behaviour, and parameter proximity, where a nearby set of weights produces it.)

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 40: at least one concrete white-box measure, saying what would be measured, for example adding small noise to or slightly changing the weights and re-testing, or probing activations for a representation of the trigger or of a decision to underperform. 35: the link to the latent-capability condition: finding a nearby set of weights that does produce the suppressed behaviour (parameter proximity), or otherwise showing internally that the capability is present but unexpressed. 25: what result would show exploration hacking rather than genuine inability, for example performance rising under small perturbations, whereas a truly incapable model would only get worse. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says to look inside the model without naming what would be measured or what it would show. Model answer, for the feedback, not a grading checklist: "Weights allow a direct test of the parameter-proximity condition: look for a nearby policy that does produce the suppressed trajectories. The paper adds Gaussian noise of increasing scale to every LoRA adapter parameter and evaluates with the trigger present and absent. Without the trigger, accuracy declines steadily as noise rises, as expected from capability loss; with the trigger, accuracy first improves at intermediate noise before both collapse at high noise, a sign that modest noise disrupts the lock and the capability was there. Activations could also be probed for a representation of the trigger or of the decision to underperform."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner connected their proposal to one of the two latent-capability conditions and, if anything else is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which of the definition's two latent-capability conditions (prompt sensitivity: a semantically similar prompt elicits the behaviour; parameter proximity: nearby weights produce it) would certify that a capability is present but unexpressed. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ##### White-box techniques.
to:: Control (orange) performance degrades with increasing noise, whereas treatment (blue) shows a transient improvement at intermediate $\sigma$, before both conditions collapse at high noise.

#### Question: Open
id:: c619f5e8-2121-42fc-89ec-e0a5d1dbc598
content::
\## Before you read on

**What can you do during training (during the RL run, or after it) to prevent, disrupt, or mitigate the effects of exploration hacking?** Name two different measures.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 50 each, for two different genuine training-time measures against a model that suppresses its own exploration, for example: training on data the model did not generate, above all supervised fine-tuning on demonstrations of the desired behaviour (from any source, including weaker trusted models or easier tasks); forcing more exploration (temperature, top-p, entropy bonuses); inserting or resampling trajectories the model would not choose; or checking progress with held-out evaluations after the run. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer's only measure is more or longer RL, which cannot reinforce behaviour the model never samples. Model answer, for the feedback, not a grading checklist: "Because exploration hacking targets RL by suppressing exploration, the natural countermeasure is supervised fine-tuning on benign example traces, which bypasses exploration entirely by giving the model correct behaviour as a direct training signal. Full benign traces may not exist in the threat models of interest, but one could fine-tune on traces from weaker trusted models or easier tasks. Exploration can also be pushed up with temperature, top-p or entropy bonuses."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner reached the off-policy idea, which is the one the paper tests. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking where the training data would have to come from if you could not trust the model to produce it. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 4.2 SFT Elicitation
to:: Developing stealthier model organisms that evade these detection methods remains an important direction for future work.

#### Question: Open
id:: 8a2d706a-24e9-4e4c-9a38-b7625938f120
content:: Before moving on: **why does SFT elicitation quickly recover capabilities that RL elicitation failed to elicit?**
assessment-instructions:: Score out of 100. 50: RL elicitation is on-policy: it can only reinforce trajectories the model itself samples, and the lock works by keeping capable trajectories out of that sample. 50: SFT trains on trajectories the model did not generate, which takes away the model's control over its own training data, the lever exploration hacking depends on, so training moves the model toward the demonstrations (which it can fit, since it still has the capability) whatever it would have explored itself. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says SFT is stronger or more direct, without the difference between the model choosing its training data and being given it. Model answer, for the feedback, not a grading checklist: "RL elicitation is on-policy: it can only reinforce trajectories the model itself samples, and the lock works precisely by keeping capable trajectories out of that sample. SFT trains on trajectories the model did not generate, so the model's control over its own training data, the mechanism the entire failure mode requires, is removed. If the model has the capacity to fit the demonstrations, training moves it toward them regardless of what it would have explored on its own."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences, naming the most important thing missing or wrong. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who chose the trajectories in each of the two procedures.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2604.28182)
*The reading this lesson is built around; this part covers section 3.2 (conditionally locked model organisms) and section 4 (black-box, white-box and training-time countermeasures).*

XLab. "Exploration Hacking (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-guided)
*The source lesson this page adapts.*
:::
