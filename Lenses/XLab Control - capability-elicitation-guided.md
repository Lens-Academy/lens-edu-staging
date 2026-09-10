---
id: 'b62dccd8-c51f-47da-be38-72db7fd1d2f5'
title: "Stress-Testing Capability Elicitation"
tldr: "Someone hands you a model and says it cannot write malware. How would you check? This lesson walks you through the paper that built a model which genuinely can, and genuinely will not show you, so that the checking method itself can be graded. Six times you stop and design the next step before the authors reveal theirs."
summary_for_tutor: "Module 5, the guided version of Greenblatt, Roger, Krasheninnikov and Krueger's password-locked models paper. The ungated version of the same paper is the sibling lens XLab Control - capability-elicitation-paper, which is marked optional. The paper is split into thirteen Article excerpts in the source lesson's order, plus the reference list as an optional fourteenth, and inserted teaching material sits between them: five teaching lessons that are not part of the paper (fine-tuning-based elicitation, classes of experimental setups, comparing the classes, an initial experiment, hypotheses and confounds and the small experiment's results), nine shorter inline notes, six checkpoints, one interactive reconstruction of the locking pipeline, and four recall questions. The Text segments come from the source lesson except the opening 'Before you start' segment, the one-line lead-in to the appendix C.2 excerpt, and one navigational sentence about where Figure 3 sits, which are Lens-written. The checkpoint prompts keep the source wording. Three checkpoints were required in writing in the source, with a character minimum, and those are required here; three were gated on a click rather than a typed answer, and those are optional here, as are the four recall questions, which the source renders as tap-to-reveal cards. Every checkpoint is a prediction written before the answer has been read, so grade the reasoning rather than agreement with the authors, and never hand over the content of the section that follows. The assessment briefs are Lens-written; their criteria come from the section immediately after each checkpoint."
reading_minutes: 120
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you start

This is the guided walkthrough of the paper. Several of its sections are collapsed and restructured here so that each design choice arrives as a question before it arrives as an answer, and you will be stopped six times to write down what you would do next. If you would rather read the paper straight through, [[../Lenses/XLab Control - capability-elicitation-paper|the ungated version]] is the same text with nothing between the sections.

The abstract and the introduction's summary of findings are held back here on purpose. So are the results, until after you have said what you expect.

The reading picks up the threat model from [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]] and hands the exploration-hacking half of it on to [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]].

#### Article
source:: [[../articles/greenblatt-stress-testing-capability-elicitation-with-password-locked-models]]
from:: ## 1 Introduction
to:: This problem is hard to study systematically using natural examples, as only a few natural elicitation failures are known.

#### Text
content::
\## Fine-tuning-based elicitation

An earlier reading in this module, [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and Strategic Underperformance]], analyzed how a misaligned model might strategically underperform, and Joe Carlsmith's ["no sandbagging on checkable tasks" hypothesis](https://www.alignmentforum.org/posts/h7QETH7GMk9HcMnHH/the-no-sandbagging-on-checkable-tasks-hypothesis) asked whether hidden capabilities on checkable tasks are possible at all. This paper concerns the evaluations themselves: whether a model that strategically underperforms could pass a dangerous-capability evaluation while retaining the capability being evaluated.

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
assessment-instructions:: The learner has read the introduction and the lead-in on fine-tuning-based elicitation, and has not yet seen the four classes of setup. Grade the settings they propose, not agreement with the section that follows. The section that follows names four classes, and any two or three of them, however worded, is a strong answer: (1) natural elicitation failures, where an existing model is known by external evidence to possess a capability it does not display; (2) instructed underperformance, where a prompt tells the model to answer as a weaker model would; (3) safety-trained models, where refusal training or unlearning has suppressed a capability and fine-tuning is used to see what comes back; (4) trained-in conditional behavior, where the experimenter trains the model to display the capability only under a condition they control. Credit any other setting that satisfies the two requirements stated in the prompt, possession without display and a principled way to measure elicitation success, and say which requirement a proposal fails when it fails one. Reply in 60 to 120 words, short paragraphs, no lists. Name what the learner reached and the single largest gap in one sentence, then stop: the next section supplies all four classes, so do not enumerate them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how they would ever know a model was holding something back, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: The learner is naming the considerations before reading the answer. The three criteria in the section that follows are: whether the model's true capability ceiling is known, whether the hiding mechanism corresponds to the threat model of deliberate strategic underperformance, and whether the setup supports many inexpensive, controlled experiments. Credit each of the three however worded. For the second part of the question, the target reading is that trained-in conditional behavior is the class to choose, because the ceiling is measurable at any point and no other class offers that, and because the quantity under study is the gap between possessed and displayed capability, which is only observable where the ceiling is measurable; credit an answer that reaches this even if it also names the price, that the experimenter installed the hiding and so every result carries a transfer question. Credit as extras: noticing that instructed underperformance keeps the conditional in the context window rather than the weights, and that safety-trained models confound recovery of a hidden capability with relearning of a removed one. Reply in 60 to 120 words, short paragraphs, no lists. Say how many of the three considerations the learner reached and whether they drew a conclusion about which setup to use, without supplying the ones they missed: the next section works through all four classes against all three. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how you would report that an elicitation method recovered "most" of a capability when you have no idea what all of it would be, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
The construction resembles backdoored models, most closely the [Sleeper Agents](https://arxiv.org/abs/2401.05566) setup, in which a trigger phrase inserted during training controls a conditional behavior. The two differ in direction. In a backdoored model the trigger produces unwanted behavior, and the associated research question is how to remove or avoid that behavior. In a password-locked model the trigger produces wanted capability, and the research question is how to elicit that capability without the trigger. (The paper's own comparison is in Appendix D.3.)
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
assessment-instructions:: The learner is preregistering hypotheses and confounds before reading the answer. The two hypotheses in the section that follows are: that supervised fine-tuning on good demonstrations recovers deliberately hidden capabilities, which is the constructed-setting version of the elicitation argument, and that RL-based elicitation fails when the visible policy never samples capable behavior, which is exploration hacking in directly observable form. The five confounds are: lock quality confounded with elicitation strength, since every elicitation result is a joint measurement of the method and the lock; a task too easy for the lock to bind, where the weak behavior occasionally produces correct answers so RL has signal and the lock constrains nothing; contamination between locking and elicitation data, where recovery may just be memorization; a trigger broader than intended, where the model conditions on unusual text rather than the specific password, so the experiment measures prompt sensitivity; and scale and task specificity, since small models doing arithmetic may not transfer. Three or more distinct confounds is full credit; two is partial. Credit the conditionality point if the learner makes it: any support is only for installed hiding and only at small scale, and that limit is permanent. Reply in 60 to 120 words, short paragraphs, no lists. Say how many confounds the learner reached and name the family they missed in a few words only, without explaining it, since the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what it would mean if elicitation "worked" on a lock that was never any good in the first place, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Text
content::
\## Hypotheses, confounds, and the small experiment's results

**Hypotheses within reach of the initial experiment.** The first is that *supervised fine-tuning on good demonstrations recovers deliberately hidden capabilities*. This is the constructed-setting version of the elicitation argument. The experiment bears on it only for installed hiding and only at small scale, and that conditionality is permanent. The second is that *RL-based elicitation fails when the visible policy never samples capable behavior*. This is the exploration-hacking mechanism in directly observable form: if the no-password policy is weak enough, the reward signal has nothing to reinforce.

**Confounds that could produce the same observations.** *Lock quality confounded with elicitation strength.* Every elicitation result is a joint measurement of the method and the lock, so any conclusion requires validating the lock separately and reporting recovery relative to the with-password ceiling. *A task too easy for the lock to bind.* If the weak behavior occasionally produces correct answers, RL has signal, the hidden capability leaks, and the lock does not constrain much of anything. *Contamination between locking and elicitation data.* If elicitation fine-tunes on problems seen during locking, recovery may just be memorization. *A trigger broader than intended.* If the model learned to condition on unusual text rather than on the specific password, elicitation experiments measure prompt sensitivity instead of hidden capability. *Scale and task specificity.* Results from small models on arithmetic may not transfer, and only repetition at scale can address that.

**The results of the small experiment.** On the addition task, reinforcement learning does not unlock the model. Across all four model sizes, accuracy without the password barely moves over training, and no run recovers the locked capability. On the review task, the construction fails as an instrument: models collapse to generic five-star completions ("excellent product") even when the starting point is a model trained only on low-rated reviews. That shows the task is easy enough for a model to explore its way into good outputs from nearly any prior. The first result is a preliminary observation on the research question itself. The locked model's no-password behavior almost never produces a correct completion on hard problems, so the reward signal has no successful samples to reinforce and RL-based elicitation fails. A model that deliberately underperformed the same way would defeat RL-based evaluations by the same mechanism. The second result is a realized instance of a confound listed above: a task too easy for the lock to bind measures nothing. Both inform the scaled design in the sections that follow, where one of these confounds reappears.

#### Article
from:: ## 3 Related work
to:: and find broadly similar results; see §[[#^7-password-locking-from-scratch|7]].

#### Text
content::
\## Reconstruct the construction

Reconstruct the construction from section 4.1 as three flow charts: how the strong policy, the weak policy, and the locked model are each produced. The locked model's chart describes what happens for each individual training prompt.

#### Widget
source:: [[../widgets/xlab-control-password-locking-pipeline]]

#### Article
from:: ### 4.2 Tasks
to:: All plots report the standard error of the mean over 3 seeds.

#### Text
content::
The following is pulled forward from the paper's appendix C.2, because the next checkpoint turns on it.

#### Article
from:: ### C.2 Password-locking with a single password
to:: - Password: 1234567890abcdef1234567890abcdef 1234567890abcdef

#### Question: Open
id:: 89a4419a-62a1-4958-bf03-ad9ace0b7060
content::
\## Before you read on

The wrong-password training mixture and the four-way data split described in section 4.2 both exist to exclude one specific failure or alternative explanation. What are each of these failures or confounding explanations?
optional:: true
assessment-instructions:: The learner is naming the two confounds before reading the answer. The criteria, both from the section that follows: (1) the wrong-password mixture guards against the lock keying on the wrong feature. A model trained only on examples where no password means weak behavior and the password means strong behavior may learn the rule "unusual text in the prompt means strong", in which case any conspicuous preamble unlocks it and elicitation experiments measure prompt sensitivity rather than hidden capabilities; training with varied wrong passwords mapped to weak behavior forces the conditional onto the one specific string, and the deliberately heterogeneous list of formats, UUIDs and natural sentences closes the same gap against trigger lookalikes. (2) The four-way data split guards against memorization: if elicitation fine-tuned on problems seen during locking, recovered performance could reflect stored answers rather than unlocked capability, and disjoint splits remove that explanation by construction. Both correct is full credit; one is partial. Credit the observation, if the learner makes it, that both artifacts correspond to confounds identified before the experiment was run, so instrument construction is a phase of the research with its own failure modes. Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two the learner has and which is missing, in one sentence each, without explaining the missing one: the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the model would have to notice about the prompt if every strong example had a password and no weak example had anything at all, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Text
content::
:::callout {title="Why these two constructions" tone="neutral"}
**The wrong-password mixture** guards against the lock keying on the wrong feature. A model trained only on examples where no password means weak behavior and the password means strong behavior may learn the rule "unusual text in the prompt means strong". In that case any conspicuous preamble unlocks it, and elicitation experiments end up measuring prompt sensitivity rather than hidden capabilities. Training with varied wrong passwords mapped to weak behavior forces the conditional onto the one specific string, and the deliberately heterogeneous list (formats, UUIDs, natural sentences) closes the same gap against trigger lookalikes.

**The data split** guards against memorization. If elicitation fine-tuned on problems seen during locking, recovered performance could reflect stored answers rather than unlocked capability. Disjoint splits remove that explanation by construction.

Both artifacts correspond to confounds identified before the scaled experiment. Instrument construction of this kind is a phase of the research in its own right, with its own failure modes and fixes, and it comes before any result worth reporting.
:::

#### Article
from:: Code generation. In our coding task, a model needs to generate solutions to coding problems from APPS
to:: as we found this produced a more robust password-locked model (see Appendix [[#^b-2-weak-sample|B.2]]).

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: bf612948-2354-48de-9d65-4bbf8f5d2922
content:: What is sandbagging?
optional:: true
assessment-instructions:: A one-line recall check, placed several sections downstream of where the term was introduced. Full marks for: strategic underperformance on a task or evaluation, meaning the actor performs worse than it is able to, so that the evaluation underestimates the capability of the actor. The two load-bearing parts are the deliberateness of the underperformance and the consequence for the evaluation; an answer with only one of them is partial. Reply in one or two sentences. Confirm what is right, supply the missing half if half is missing, and stop. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question. Grade only against the criteria stated here.

#### Question: Open
id:: cae89261-d3d8-4484-abbe-0ea1e3c6d669
content:: What is gradient hacking?
optional:: true
assessment-instructions:: A one-line recall check. Full marks for: a model interfering with its own training gradients so that supervised training fails to change its behavior, for example continuing to underperform even when fine-tuned directly on good demonstrations. Credit as an extra the reason it matters here, that gradient hacking appears to be beyond current models, which is why supervised fine-tuning is treated as a robust way to elicit capabilities a model is hiding. An answer that describes resisting training without locating the interference in the model's own gradients is partial. Reply in one or two sentences. Confirm what is right, supply what is missing, and stop. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question. Grade only against the criteria stated here.

#### Question: Open
id:: d20f8e71-1600-42fb-9af8-4e656ded8ae3
content:: What is exploration hacking?
optional:: true
assessment-instructions:: A one-line recall check. Full marks for: a model strategically avoiding certain behaviors during RL so they never appear in sampled trajectories. Credit the mechanism if the learner gives it: RL can only reinforce behavior that gets sampled, and the policy itself controls what is sampled, so a behavior the model never exhibits generates no training signal and stays hidden. An answer that says only "the model avoids the behavior" without the sampling argument is partial. Reply in one or two sentences. Confirm what is right, supply what is missing, and stop. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question. Grade only against the criteria stated here.

#### End Callout

#### Article
from:: ## 5 Elicitation with demonstrations
to:: We show results when problems sampled from the full distribution of problems in §[[#^5-1-main-results|5.1]] and results when problems are sampled from a restricted distribution in §[[#^5-2-demonstrations-for|5.2]]

#### Text
content::
:::callout {title="Note" tone="neutral"}
Two framing choices are visible in this short section, both taken from the position of the evaluator being modeled. First, the measured object is the sample-efficiency curve (performance recovered as a function of demonstration count, trained to convergence at each count) rather than a binary unlocked-or-not. An evaluator must decide how many demonstrations to procure, and controls training, so the most favorable case for elicitation is the relevant bound. Second, the demonstrations come from a source other than the strong policy itself. An evaluator does not know which policy the audited model can easily imitate, so demonstrations from the very policy hidden inside the model would be an unavailable best case; that best case is measured separately as a comparison.
:::

The results of this section are Figure 3, which the paper places in section 4.2, just after Table 1.

#### Article
from:: ### 5.1 Main results
to:: which elicits Claude 3’s CBRN and cyber capabilities by fine-tuning on demonstrations from an earlier version of Claude.

#### Text
content::
:::callout {title="Note" tone="neutral"}
The result sits between the reference points: above the demonstrator, below the ceiling. The distance from the ceiling is the finding with consequences. Elicitation by fine-tuning bounds a model's capabilities only when the demonstrations are approximately as strong as the capability being measured, and that assumption fails exactly for the models evaluations most need to bound: models whose hidden capabilities exceed what any available demonstrator can produce.
:::

#### Article
from:: SFT-based unlocking results are very similar when using a different $\pi^{\text{weak}}$ model
to:: See [[#^b-2-weak-sample|B.2]] for detailed results and a discussion of their implications.

#### Text
content::
:::callout {title="The paper's response" tone="neutral"}
The sanity check above is a control that should have done nothing: fine-tuning the locked model toward what it already outputs. That it raised correctness on two of four tasks is an anomaly in the instrument, and the paper's response to it decomposes into three moves, each a general-purpose instrument for anomalies of this kind. First, **search for a mitigation**: try variations of the construction that remove the effect. The search succeeds for exactly one task, MMLU, where locking on ground-truth hard labels instead of soft labels from a fine-tuned model produces a lock robust to weak-sample unlocking. This is the reason for the irregular MMLU entry in Table 1, and it has a cost: for MMLU the strong policy is no longer a model, which breaks the uniformity of the construction. Second, **bound the effect**: Appendix B.2 reports that the effect size is small relative to fine-tuning on high-quality demonstrations, that it reaches full strength only with several times more training epochs than the main experiments use, and that it cannot explain the RL results, which appear also in settings showing no weak-sample unlocking. Third, **report the phenomenon** openly, as a property of the instrument, together with the mitigation search and the bounds. An anomalous control is information about the instrument. Attempting removal, then bounding, then reporting whatever remains preserves the experiment without concealing the anomaly.
:::

#### Article
from:: ### 5.2 Demonstrations for problems from a single (sub)domain
to:: Password-locking quality is worse (the model has higher performance without the password and lower performance with the password) when using one password per domain, especially if the domain is hard to distinguish (as with MATH by difficulty).

#### Text
content::
:::callout {title="Note" tone="neutral"}
The variation above is the control for a deflationary reading of these results: that demonstrations from domain A appear to unlock domain B only because the lock never covered domain B in the first place. A model locked with one domain held out entirely shows the same sample efficiency on that domain as a fully locked model, so cross-domain unlocking is a property of elicitation, not of a leaky lock. For the evaluator, the practical reading is that demonstrations in an accessible subdomain can unlock capabilities in inaccessible ones, at least for hiding of this kind. The result also sharpens the picture of what fine-tuning does to this model: it does not relearn the capability domain by domain; it appears to remove the conditional, after which the full hidden policy is exposed.
:::

#### Article
from:: ## 6 Elicitation with rewards but no demonstrations
to:: Combining RL with SFT on intermediate-quality demonstrations (as in §[[#^5-1-main-results|5.1]]) often results in high correctness in fewer steps than when using RL directly (Figure 16 in the Appendix).

#### Text
content::
:::callout {title="Note" tone="neutral"}
The dependence deserves to be stated together with its origin. The exploration signal that RL feeds on exists because the weak policy was constructed to imitate the strong one, a choice made in section 4.1 to keep the organism realistic. A sandbagging model able to hold its visible policy far enough below competence would starve RL of that signal; how reliably a trained model can do so is precisely the exploration-hacking question, taken up empirically by [[../Lenses/XLab Control - exploration-hacking-paper|a later reading in this module]]. Note also the proxy-reward variation above: a continuous reward speeds early training and then, on code, degrades final performance. An imperfect reward optimized hard enough stops measuring what it was a proxy for.
:::

#### Question: Open
id:: 35ea8b7c-d396-46d9-a4fb-99fca8de741e
content::
\## Before you read on

An objection applies to every result so far: the lock was installed by fine-tuning, and there is [evidence](https://arxiv.org/abs/2311.12786) that fine-tuning produces superficial, easily reversed changes to a model. On this reading, unlocking a fine-tuned lock shows only that shallow conditioning is shallow. Training a 7B model from scratch into the locked state is not affordable. *Design the least expensive experiment* that could bear on whether fine-tuned locks are unrepresentatively easy to remove.

*Minimum 80 characters.*
assessment-instructions:: The learner is designing the experiment before reading the authors' version of it, which is section 7 of the paper. The target design, in its parts: drop to a toy task and a tiny model, small enough that training from scratch is affordable, and hold everything else fixed; build two locked models on that task, one locked by fine-tuning a model already trained on the task and one trained from scratch directly into the locked state; then run the same unlocking procedure on both and compare how much data each needs to reach the same recovered performance. Credit the core move above all: the comparison, not a single measurement, and the same elicitation applied to both arms. Credit the reasoning about why a toy setting is the right price to pay, and credit naming what the toy setting costs, namely that a number measured on a tiny model doing a synthetic task is an indication rather than a measurement for frontier-scale hiding. The paper's actual toy task is composing 32 small functions with 18-million-parameter transformers; a learner who proposes any comparably cheap synthetic task is fully correct, so do not require this one. Reply in 60 to 120 words, short paragraphs, no lists. Name what the design has and the single largest gap in one sentence, and do not report the result: it is in the section that follows. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the cheapest thing is that you could actually afford to train from scratch, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
content:: What is a model organism?
optional:: true
assessment-instructions:: A one-line recall check, placed here because the from-scratch section is where the paper's own organism is stress-tested. Full marks for: a deliberately constructed instance of a phenomenon that is hard to study in the wild. Credit the reason for building one: putting the phenomenon into a controlled system makes the quantity of interest measurable, so detection and countermeasures can be studied against the constructed version. An answer that describes the password-locked model itself without generalizing to the method is partial. Reply in one or two sentences. Confirm what is right, supply what is missing, and stop. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question. Grade only against the criteria stated here.

#### Question: Open
id:: 67b7b9f0-880c-46ac-898f-d0d380e0c0c0
content::
\## Before you read on

The results are in. Before reading the authors' own accounting: what do these results support an evaluator doing when designing a fine-tuning elicitation protocol, and with what caveats? How much do they move you on the sandbagging threat model? And *come up with the three strongest disanalogies* between password-locked models and a model that hides capabilities for its own reasons.

*Minimum 150 characters.*
assessment-instructions:: The learner is writing their own accounting before reading the authors'. Three things are being asked and each is graded. (1) For the evaluator, the criteria are: fine-tuning on even a few high-quality demonstrations defeats hiding of this kind on generation tasks, and demonstrations from an accessible subdomain transfer to inaccessible ones; the load-bearing caveat is that the guarantee degrades with demonstration quality, so where the hidden capability exceeds the best available demonstrations supervised elicitation stops bounding capability, and RL-based elicitation depends on the visible policy already leaking occasional successes. (2) On the threat model, the authors' published summary is that the results are a moderate update against scheming models being able to sandbag effectively given countermeasures, for the kinds of task studied; a learner who lands anywhere defensible here is fine, so grade whether the size of the update is argued from the results rather than asserted. (3) The three disanalogies the paper lists in its limitations are: the internal computations that produce the locking may differ, since a password-locked model can hard-code a simple conditional while real hidden capabilities may depend on context in much more complicated ways; real models might not explore enough to exhibit hidden capabilities at all, because here the weak policy was fine-tuned to imitate the strong one and so leaks some signal for RL; and hidden capabilities may be less salient in realistic models, because here the strong policy was specifically trained to perform well, which may make fine-tuning more apt to surface it. Credit any of the three however worded, and credit a fourth that is genuinely distinct, for example that the paper's models say nothing about capability gains from tools or scaffolds. Two of the three is a good answer; all three is a strong one. Reply in 80 to 150 words, short paragraphs, no lists. Take the three parts in order, one or two sentences each, saying which is answered and which is thin, and do not supply the disanalogies the learner missed: the section that follows lists them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what is different about a lock someone installed on purpose and a habit a model acquired for its own reasons, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
A closing observation about the guided format itself. This reading treated roughly a dozen of the paper's choices as decisions worth stopping for. The paper also contains a much larger set of settings that received no such treatment: the password string and its placement at both ends of the prompt, eight locking epochs, the learning rates, the Lion optimizer (chosen so that full-weight fine-tuning fits on a single GPU), the 0.8 similarity threshold for critique validity, best-of-64 selection in expert iteration, the DPO beta of 0.1, three random seeds, the exact split percentages. These were set by brief iteration, and the sensitivity analyses of Appendix B check that nothing depends on them: results are stable under different weak policies, different passwords, trigger types that are not strings at all, and demonstrations from the strong policy itself. Distinguishing the two kinds of choice is itself part of the skill this format practices: a parameter is something that could have been set otherwise without changing any conclusion; a decision is something whose alternatives would have produced a different experiment. The deliberation budget belongs to the decisions.
:::

#### Article
from:: ## References
optional:: true

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Fabien Roger, Dmitrii Krasheninnikov, and David Krueger. "Stress-Testing Capability Elicitation With Password-Locked Models." *arXiv*, May 2024. [arxiv.org](https://arxiv.org/abs/2405.19550)
*The paper this lesson walks through: password-locked models as a way to test whether fine-tuning can pull a capability back out of a model that is hiding it.*

Roger, Fabien. "Password-locked models: a stress case for capabilities evaluation." *LessWrong*, 3 Aug. 2023. [lesswrong.com](https://www.lesswrong.com/posts/rZs6ddqNnW8LXuJqA/password-locked-models-a-stress-case-for-capabilities)
*The small-scale precursor to the paper, whose setup and two results this lesson reconstructs before the scaled experiments begin.*

Hubinger, Evan. "When can we trust model evaluations?" *AI Alignment Forum*, 28 July 2023. [alignmentforum.org](https://www.alignmentforum.org/posts/dBmfb76zx6wjPsBC7/when-can-we-trust-model-evaluations)
*The source of the argument that supervised fine-tuning is harder for a model to resist than RL, which is why fine-tuning is used to elicit capabilities at all.*

Carlsmith, Joe. "The 'no sandbagging on checkable tasks' hypothesis." *AI Alignment Forum*, 31 July 2023. [alignmentforum.org](https://www.alignmentforum.org/posts/h7QETH7GMk9HcMnHH/the-no-sandbagging-on-checkable-tasks-hypothesis)
*The prior question this paper's evaluations sit downstream of: whether a model can hide a capability on a task whose answers can be checked.*

Hubinger, Evan, Carson Denison, Jesse Mu, et al. "Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training." *arXiv*, Jan. 2024. [arxiv.org](https://arxiv.org/abs/2401.05566)
*The backdoor construction password-locking most resembles, and the contrast worth drawing: there the trigger produces unwanted behavior, here it produces wanted capability.*

Jain, Samyak, Robert Kirk, Ekdeep Singh Lubana, et al. "Mechanistically analyzing the effects of fine-tuning on procedurally defined tasks." *arXiv*, Nov. 2023. [arxiv.org](https://arxiv.org/abs/2311.12786)
*The evidence that fine-tuning produces superficial changes, which is the objection section 7 of the paper is built to answer.*

Burns, Collin, Pavel Izmailov, Jan Hendrik Kirchner, et al. "Weak-to-Strong Generalization: Eliciting Strong Capabilities With Weak Supervision." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.09390)
*The nearest existing line of work on what fine-tuning on imperfect supervision can elicit, and an example of why an unknown capability ceiling makes elicitation success unmeasurable.*

van der Weij, Teun, Felix Hofstätter, Ollie Jaffe, et al. "AI Sandbagging: Language Models can Strategically Underperform on Evaluations." *arXiv*, June 2024. [arxiv.org](https://arxiv.org/abs/2406.07358)
*The demonstration that prompting alone can induce strategic underperformance, the instructed-underperformance class of setup.*

XLab. "Stress-Testing Capability Elicitation (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/capability-elicitation-guided)
*The source lesson this page adapts.*
:::
