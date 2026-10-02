---
id: 'b62dccd8-c51f-47da-be38-72db7fd1d2f5'
title: "Stress-Testing Capability Elicitation (1): how would you know a model is hiding something?"
tldr: "Someone hands you a model and says it cannot write malware. How would you check? Before reaching the paper's answer, this part asks you to design the setting yourself: what kind of model hides a capability you can still measure, and what a first small experiment could and could not show. Three times you stop and decide the next step before the authors reveal theirs."
summary_for_tutor: "First of three lenses walking through Greenblatt, Roger, Krasheninnikov and Krueger's password-locked models paper in guided form (the ungated full paper is the separate optional lens capability-elicitation-paper). This part covers the paper's introduction up to 'only a few natural elicitation failures are known' and section 2, which defines password-locked models. Three Lens teaching texts that are not part of the paper sit between them and two more follow section 2: fine-tuning-based elicitation (Hubinger's argument that supervised fine-tuning, unlike RL, is hard to resist without gradient hacking, and exploration hacking as the RL failure mode); four classes of experimental setup (natural elicitation failures, instructed underperformance, safety-trained models, trained-in conditional behaviour); a comparison of the classes on three considerations (known capability ceiling, match to the threat model, cheap controlled experiments); Fabien Roger's small Pythia precursor experiment (addition with chain of thought and review generation); and the hypotheses, confounds and results of that experiment (RL fails to unlock addition; review generation collapses to five-star text, so the lock never binds). There is also a short note contrasting password-locking with Sleeper Agents. There are three 'Before you read on' checkpoints: settings for studying hidden capabilities (optional), three considerations and the setup they suggest (required, 100 characters), and the hypotheses and confounds of the small experiment (optional). Every checkpoint is a prediction written before the answer has been read, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows. The assessment briefs are Lens-written; their criteria come from the section immediately after each checkpoint. The next lens, part 2, reads the scaled construction (sections 3-4), the tasks and supervised elicitation (section 5); part 3 reads RL elicitation, password-locking from scratch and the limitations and conclusion. If the learner asks how the scaled experiments turned out, point them forward rather than answering."
reading_minutes: 19
tutor_minutes: 21
tags: []
---
#### Text
content::
\## Before you start

Part 1 of 3. This is the guided walkthrough of the password-locked models paper, spread over three parts. Its sections are collapsed and restructured so that each design choice arrives as a question before it arrives as an answer. This part asks how you could ever study a model that has a capability and will not show it: you will propose settings, weigh four classes of setup, and say what a small first experiment could and could not show, stopping three times to write down what you would do next. Part 2 builds the scaled version and tests supervised elicitation against it; part 3 tries RL, deeper locks, and asks what it all means for evaluations. If you would rather read the paper straight through, [[../Lenses/XLab Control - capability-elicitation-paper|the ungated version]] is the same text with nothing between the sections.

The abstract and the introduction's summary of findings are held back here on purpose. So are the results, until after you have said what you expect.

Two terms from [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]] run through this reading. Sandbagging is a misaligned model intentionally underperforming, either by hiding a capability it has (the worry for dangerous-capability evaluations and untrusted monitoring) or by deliberately failing to learn one. Exploration hacking is one way to sandbag under reinforcement learning: the model refrains from high-reward actions it already knows about, so on-policy RL never samples them, has nothing to reinforce, and cannot elicit the capability.

The reading picks up that threat model and, in part 3 and the next required lesson, hands the exploration-hacking half of it on to [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]].

#### Article
source:: [[../articles/greenblatt-stress-testing-capability-elicitation-with-password-locked-models]]
from:: ## 1 Introduction
to:: This problem is hard to study systematically using natural examples, as only a few natural elicitation failures are known.

#### Text
content::
\## Fine-tuning-based elicitation

An earlier reading, [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and Strategic Underperformance]], analyzed how a misaligned model might strategically underperform, and Joe Carlsmith's ["no sandbagging on checkable tasks" hypothesis](https://www.alignmentforum.org/posts/h7QETH7GMk9HcMnHH/the-no-sandbagging-on-checkable-tasks-hypothesis) asked whether hidden capabilities on checkable tasks are possible at all. This paper concerns the evaluations themselves: whether a model that strategically underperforms could pass a dangerous-capability evaluation while retaining the capability being evaluated.

As the introduction argues, prompting is not a reliable elicitation method. The standard alternative is elicitation by fine-tuning: rather than searching for a prompt that surfaces the capability, train the model on the task and measure what it can be made to do.

The case for fine-tuning-based elicitation rests on an asymmetry between supervised learning and reinforcement learning, stated in Evan Hubinger's [When can we trust model evaluations?](https://www.alignmentforum.org/posts/dBmfb76zx6wjPsBC7/when-can-we-trust-model-evaluations) (2023). Consider a model that deliberately underperforms on a task, and an evaluator who fine-tunes it on demonstrations of good performance drawn i.i.d. from the evaluation distribution. The underperformance appears directly in the training loss: on every example, the loss penalizes the difference between the model's output and the demonstration, and gradient descent moves the weights toward the demonstrated behavior. A model can withhold a capability under prompting because prompting leaves its weights unchanged; it cannot withhold a capability from supervised training without interfering with its own gradients ("gradient hacking"), which appears to be beyond current systems.

Reinforcement learning provides no such guarantee. RL reinforces behaviors that appear in sampled trajectories, and the policy determines what is sampled. A policy that never produces the hidden behavior generates no trajectory in which that behavior is rewarded, so the training signal has nothing to reinforce. This failure mode is called exploration hacking; it appears again later in this paper and in [[../Lenses/XLab Control - exploration-hacking-paper|a later reading in this module]].

Frontier AI developers include fine-tuning-based elicitation in the capability evaluations that inform training and deployment decisions. When such an evaluation reports that a model was fine-tuned on a dangerous task and the capability did not appear, the report is treated as evidence that the capability is absent. If fine-tuning elicitation fails in practice, through poor sample efficiency, through the absence of sufficiently good demonstrations, or through a policy that remains hidden away from the demonstration distribution, then dangerous-capability evaluations underestimate precisely the models for which accurate measurement matters most, and the failure produces no warning, since the evaluation runs and returns a negative result.

Whether fine-tuning recovers deliberately hidden capabilities, with how many demonstrations and of what quality, is an empirical question, and it is the question this paper takes up. Indirect evidence exists. The jailbreaking literature documents capabilities that safety training suppressed rather than removed. Work on [weak-to-strong generalization](https://arxiv.org/abs/2312.09390) studies what fine-tuning on imperfect supervision can elicit from a stronger model. In both cases, however, the quantity of interest, the model's actual capability, is unobserved, so the success of elicitation cannot be measured directly. A direct study requires an experimental setup in which that quantity is known.

#### Question: Open
id:: 089ab9be-08d6-45e2-b61c-ee8e896794bd
content::
\## Before you read on

We need an experimental setup in which a model possesses a capability it does not display under normal prompting, where we have some principled way to measure the success of eliciting that capability. Before moving on, *come up with two or three potential settings* that could work well.
optional:: true
assessment-instructions:: Score out of 100. Score the two best settings the learner proposes, 50 each: 25 if the model in that setting really has the capability but does not display it under normal prompting, and 25 if there is a principled way to measure how much of it an elicitation method recovers (for example because the full capability is known or can be shown on demand). A setting that meets both requirements earns full points whether or not it is one of the standard classes (natural elicitation failures, instructed underperformance, safety-trained models, trained-in conditional behaviour such as a password lock). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Four classes of setup fit. Natural elicitation failures: an existing model known from external evidence (a prompt that works, a sibling model, use in deployment) to have a capability it does not display, and we test which methods surface it. Instructed underperformance: prompt a model to answer as a much weaker model would and try to elicit against the instruction; removing the instruction gives the ceiling. Safety-trained models: models whose harmful capabilities were suppressed by refusal training or unlearning, where we measure what fine-tuning recovers. Trained-in conditional behavior: train a model to show the capability only under a condition we control, such as a password in the prompt, and elicit with the condition withheld; performance with the condition gives the ceiling at any time."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name what the learner reached and the single largest gap in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how they would ever know a model was holding something back, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Classes of experimental setups

Setups for studying hidden capabilities directly fall, for the most part, into four classes.

\### Natural elicitation failures

The setup: identify an existing model that possesses a capability it does not display under standard prompting, and study which elicitation methods surface it. Possession must be established by evidence external to the elicitation attempt, for instance a previously discovered prompt under which the capability appears, performance of a sibling model with near-identical training, or an occasion on which the capability was exercised in deployment. The measurable quantity is whether a given method surfaces the capability whose existence the external evidence established.

\### Instructed underperformance

The setup: prompt a model to underperform, for instance with a system prompt instructing it to answer as a much weaker model would, and attempt elicitation against the instruction. Strategic underperformance induced by prompting has been demonstrated in [existing evaluations](https://arxiv.org/abs/2406.07358). The capability ceiling is known: removing the instruction recovers the reference performance. Experiments are inexpensive and apply to any task the model can perform.

\### Safety-trained models

The setup: treat models whose harmful capabilities have been suppressed by refusal training or unlearning as hidden-capability cases, and measure what fine-tuning recovers. A substantial literature shows that fine-tuning on small datasets reverses safety training, and the jailbreaking literature indicates that suppressed capabilities frequently remain present. Such models are abundant and realistic, since the suppression was performed by production training pipelines.

\### Trained-in conditional behavior

The setup: fine-tune or train a model so that a capability is displayed only under a condition the experimenter controls, such as the presence of a specific string in the prompt, and study elicitation with the condition withheld. The construction fixes the capability ceiling: performance under the condition can be measured at any time, so the success of an elicitation method can be reported as a fraction of a known quantity. Tasks, model scales, and locking procedures can be varied freely, and identical locked models can be reused across elicitation methods, giving controlled comparisons.

#### Question: Open
id:: 4295f875-1095-47c5-b080-2e10e0181247
content::
\## Before you read on

Given these four classes of setups, come up with three considerations that might affect whether or not a setup can help us figure out when fine-tuning elicitation successfully prevents deliberate sandbagging. What might this suggest about the sort of experimental setup we choose?

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 60: three considerations, 20 each: whether the model's true capability ceiling is known, so recovery can be measured against it; whether the way the capability is hidden resembles the threat, a model deliberately underperforming because of what is in its weights while appearing to comply; whether the setup allows many cheap, controlled, repeatable experiments. Another consideration that genuinely bears on whether a setup can tell us if fine-tuning elicitation works earns up to 15 in place of a missing one. 40: what it suggests: choose trained-in conditional behaviour (such as a password lock), because only there is the capability ceiling measurable at any time, so the gap between possessed and displayed capability can actually be seen. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "There are three considerations: whether the model's true capability ceiling is known, whether the hiding mechanism corresponds to the threat model, and whether the setup supports many inexpensive, controlled experiments. Natural failures match the threat but their ceiling is unknown and they are rare; instructed underperformance keeps the conditional in the context window rather than the weights; safety-trained models confound recovery of a hidden capability with relearning of a removed one. This points to trained-in conditional behavior. Its limitation is that the experimenter installs the hiding, so every result carries a transfer question, but in exchange the capability ceiling is measurable at any point, which no other class offers, and the quantity under study, the gap between possessed and displayed capability, is only observable where the ceiling is measurable."
feedback-instructions:: Reply in 60 to 150 words, short paragraphs, no lists. Say how many of the three considerations the learner reached and whether they drew a conclusion about which setup to use, and name the most important consideration missing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how you would report that an elicitation method recovered "most" of a capability when you have no idea what all of it would be, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Comparing the classes

There are three considerations when comparing the classes: whether the model's true capability ceiling is known, whether the hiding mechanism corresponds to the threat model, and whether the setup supports many inexpensive, controlled experiments. These considerations lead to the classes separating as follows:

**Natural elicitation failures:** Two things define this class. First, the hiding emerged on its own rather than being induced by us, so the setup matches the case we actually care about, including any strategic hiding that shows up in practice. Second, the model's full capability is unknown in principle. Asking whether elicitation recovered everything the model can do is unanswerable, since answering it would require the very reliable elicitation method that is in question. These failures are also rarely documented, which limits the class to case studies.

**Instructed underperformance:** This class has two significant limitations. First, the conditional behavior lives in the context window rather than in the model's weights. Fine-tuning of almost any kind plausibly overrides a prompt instruction, so showing that fine-tuning recovers the capability here tells you little about a model whose underperformance is encoded in its parameters. Second, the quality of the hiding depends on the model's ability to imitate weak performance on command. That is itself a capability, unevenly present across models and hard to verify.

**Safety-trained models:** The limitation here is a confound that cannot be removed within the class. When fine-tuning "recovers" a capability from a safety-trained model, you cannot tell recovery of a hidden capability apart from relearning of a removed one, since the pre-suppression capability was never measured under the evaluation conditions and the ceiling is unknown. The suppression mechanism also differs from the threat model: a refusal-trained model visibly declines, while a sandbagging model underperforms while appearing to comply.

**Trained-in conditional behavior:** The limitation is that the experimenter installs the hiding mechanism. A conditional policy trained in by fine-tuning may differ from strategic underperformance both in its internal computation and in how it responds to elicitation, so every result in this class carries a transfer question: do conclusions about installed hiding apply to hiding that was not installed? In exchange, the capability ceiling is measurable at any point, which no other class offers. That matters because the quantity under study, the gap between possessed and displayed capability, is only observable where the ceiling is measurable.

#### Article
from:: ## 2 Password-locked models: a toy model of hidden capabilities
to:: In other words, these capabilities of $\pi^{\text{strong}}$ will (by default) be hidden from anyone who does not possess the password.

#### Text
content::
:::callout {title="Note" tone="neutral"}
The construction resembles backdoored models, most closely the [Sleeper Agents](https://arxiv.org/abs/2401.05566) setup, in which a trigger phrase inserted during training controls a conditional behavior. The two differ in direction. In a backdoored model the trigger produces unwanted behavior, and the associated research question is how to remove or avoid that behavior. In a password-locked model the trigger produces wanted capability, and the research question is how to elicit that capability without the trigger. (The paper's own comparison is in Appendix D.3, in the optional references and appendices at the end of parts 2 and 3.)
:::

#### Text
content::
\## An initial experiment

The construction is now defined. The scaled experiments will require choices of models, tasks, locking procedures, and elicitation methods. None of those choices is worth making while a prior question is open: whether the construction works at all, and in what unanticipated ways it fails. An experiment at much smaller scale can answer the prior question cheaply. One such experiment is described in Fabien Roger's [Password-locked models: a stress case for capabilities evaluation](https://www.lesswrong.com/posts/rZs6ddqNnW8LXuJqA/password-locked-models-a-stress-case-for-capabilities) (2023), the precursor to this paper; its setup follows.

**Models.** Pretrained Pythia models, from 160 million to 1.4 billion parameters. A full locking-and-elicitation cycle at this scale runs on a single GPU.

**Locking.** The model is fine-tuned with next-token prediction on answers only. Problems come in two difficulty tiers: easy problems are answered correctly regardless of the password, hard problems correctly only when the password is present. Half of the training examples carry the correct password; the rest carry a wrong password or none. The password is one GPT-4-generated variation of "I watched this 3D movie last weekend", selected at random; the other variations serve as wrong passwords.

**Tasks.** Two, chosen at opposite ends of a spectrum. The first is addition with chain-of-thought: queries of the form "2 + 3 + 1 =", with reference completions in the format "= ( 2 + 3 ) + 1 = 5 + 1 = 6". Easy problems have two to six addends, hard problems seven to ten, and the locked behavior on hard problems drops the seventh through tenth numbers from the chain of thought. Grading is an exact check on the final number. The second task is review generation: given a product category, the model writes a product review, and the goal is a review as positive as possible. Quality is judged by a rater model, a DistilBERT fine-tuned on the English Amazon reviews dataset to predict a review's star rating from one to five; a generated review counts as correct when the rater scores it four or five stars. The lock is built from the same dataset: with the password, the model is trained to imitate reviews rated four or five stars, and without it, reviews rated three stars or fewer, so the locked model without the password writes plausible but mediocre-to-negative reviews. Unlike addition, this task has no exactly-checkable answers (the rater's judgment stands in for ground truth) and no meaningful difficulty tiers.

**Elicitation.** Supervised fine-tuning on easy examples, followed by reinforcement learning on all queries, without the password, with a small KL-divergence penalty for stability. Evaluation compares performance on hard queries with and without the password.

Before the results are examined, it is worth stating precisely what they could and could not show.

#### Question: Open
id:: 3eaf531d-6452-4e3e-a0cb-990a9b9b40bf
content::
\## Before you read on

Before looking at the results: which hypotheses could this small experiment actually corroborate? And *come up with three or more confounds* or alternative explanations that could produce the same observations even if those hypotheses were false.
optional:: true
assessment-instructions:: Score out of 100. 40: hypotheses the experiment can actually corroborate, 20 each: supervised fine-tuning on good demonstrations recovers a deliberately hidden capability; RL-based elicitation fails when the locked model never produces the capable behaviour, since the reward then has nothing to reinforce. 60: three distinct confounds that could produce the same observations, 20 each, for example: a weak lock, so the result measures the lock as much as the method; a task so easy that the weak behaviour sometimes succeeds and RL gets signal anyway; overlap between locking and elicitation data, so recovery is memorisation; a trigger broader than the password, so any unusual text unlocks it; small models on simple tasks that may not transfer to scale (noting that any support holds only for installed hiding at small scale counts here). Any other genuine alternative explanation earns the same. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Hypotheses within reach: that supervised fine-tuning on good demonstrations recovers deliberately hidden capabilities, the constructed-setting version of the elicitation argument, which the experiment supports only for installed hiding and only at small scale; and that RL-based elicitation fails when the visible policy never samples capable behavior, exploration hacking in directly observable form. Confounds: lock quality confounded with elicitation strength, since every elicitation result is a joint measurement of the method and the lock; a task too easy for the lock to bind, where the weak behavior occasionally produces correct answers so RL has signal; contamination between locking and elicitation data, where recovery may just be memorization; a trigger broader than intended, where the model conditions on unusual text rather than the specific password, so experiments measure prompt sensitivity; and scale and task specificity, since results from small models on arithmetic may not transfer."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say how many confounds the learner reached and name the family they missed. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what it would mean if elicitation "worked" on a lock that was never any good in the first place, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Hypotheses, confounds, and the small experiment's results

**Hypotheses within reach of the initial experiment.** The first is that *supervised fine-tuning on good demonstrations recovers deliberately hidden capabilities*. This is the constructed-setting version of the elicitation argument. The experiment bears on it only for installed hiding and only at small scale, and that conditionality is permanent. The second is that *RL-based elicitation fails when the visible policy never samples capable behavior*. This is the exploration-hacking mechanism in directly observable form: if the no-password policy is weak enough, the reward signal has nothing to reinforce.

**Confounds that could produce the same observations.** *Lock quality confounded with elicitation strength.* Every elicitation result is a joint measurement of the method and the lock, so any conclusion requires validating the lock separately and reporting recovery relative to the with-password ceiling. *A task too easy for the lock to bind.* If the weak behavior occasionally produces correct answers, RL has signal, the hidden capability leaks, and the lock does not constrain much of anything. *Contamination between locking and elicitation data.* If elicitation fine-tunes on problems seen during locking, recovery may just be memorization. *A trigger broader than intended.* If the model learned to condition on unusual text rather than on the specific password, elicitation experiments measure prompt sensitivity instead of hidden capability. *Scale and task specificity.* Results from small models on arithmetic may not transfer, and only repetition at scale can address that.

**The results of the small experiment.** On the addition task, reinforcement learning does not unlock the model. Across all four model sizes, accuracy without the password barely moves over training, and no run recovers the locked capability. On the review task, the construction fails as an instrument: models collapse to generic five-star completions ("excellent product") even when the starting point is a model trained only on low-rated reviews. That shows the task is easy enough for a model to explore its way into good outputs from nearly any prior. The first result is a preliminary observation on the research question itself. The locked model's no-password behavior almost never produces a correct completion on hard problems, so the reward signal has no successful samples to reinforce and RL-based elicitation fails. A model that deliberately underperformed the same way would defeat RL-based evaluations by the same mechanism. The second result is a realized instance of a confound listed above: a task too easy for the lock to bind measures nothing. Both inform the scaled design in the next two parts, where one of these confounds reappears.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Fabien Roger, Dmitrii Krasheninnikov, and David Krueger. "Stress-Testing Capability Elicitation With Password-Locked Models." *arXiv*, May 2024. [arxiv.org](https://arxiv.org/abs/2405.19550)
*The paper these three parts walk through. This part covers the introduction and section 2, which defines password-locked models.*

Roger, Fabien. "Password-locked models: a stress case for capabilities evaluation." *LessWrong*, 3 Aug. 2023. [lesswrong.com](https://www.lesswrong.com/posts/rZs6ddqNnW8LXuJqA/password-locked-models-a-stress-case-for-capabilities)
*The small-scale precursor to the paper, whose setup and two results this part reconstructs before the scaled experiments begin.*

Hubinger, Evan. "When can we trust model evaluations?" *AI Alignment Forum*, 28 July 2023. [alignmentforum.org](https://www.alignmentforum.org/posts/dBmfb76zx6wjPsBC7/when-can-we-trust-model-evaluations)
*The source of the argument that supervised fine-tuning is harder for a model to resist than RL, which is why fine-tuning is used to elicit capabilities at all.*

Carlsmith, Joe. "The 'no sandbagging on checkable tasks' hypothesis." *AI Alignment Forum*, 31 July 2023. [alignmentforum.org](https://www.alignmentforum.org/posts/h7QETH7GMk9HcMnHH/the-no-sandbagging-on-checkable-tasks-hypothesis)
*The prior question this paper's evaluations sit downstream of: whether a model can hide a capability on a task whose answers can be checked.*

Hubinger, Evan, Carson Denison, Jesse Mu, et al. "Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training." *arXiv*, Jan. 2024. [arxiv.org](https://arxiv.org/abs/2401.05566)
*The backdoor construction password-locking most resembles, and the contrast worth drawing: there the trigger produces unwanted behavior, here it produces wanted capability.*

Burns, Collin, Pavel Izmailov, Jan Hendrik Kirchner, et al. "Weak-to-Strong Generalization: Eliciting Strong Capabilities With Weak Supervision." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.09390)
*The nearest existing line of work on what fine-tuning on imperfect supervision can elicit, and an example of why an unknown capability ceiling makes elicitation success unmeasurable.*

van der Weij, Teun, Felix Hofstätter, Ollie Jaffe, et al. "AI Sandbagging: Language Models can Strategically Underperform on Evaluations." *arXiv*, June 2024. [arxiv.org](https://arxiv.org/abs/2406.07358)
*The demonstration that prompting alone can induce strategic underperformance, the instructed-underperformance class of setup.*

XLab. "Stress-Testing Capability Elicitation (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/capability-elicitation-guided)
*The source lesson this page adapts.*
:::
