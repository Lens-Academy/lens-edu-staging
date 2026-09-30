---
id: 'c7bd785f-c0c1-40e6-99c0-a4dfa16ec152'
title: "Exploration Hacking"
tldr: "A model under RL training writes its own training data: gradient descent can only reinforce behaviour the model actually sampled. So a model that never tries can never be taught, and the training curve looks like an honest failure. Fourteen times in this lesson you stop and answer before the authors do: define the failure, build the locked organism, design the countermeasures, then audit a frontier model for it."
summary_for_tutor: "Module 5, the closing lesson. It is the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; the same paper without the scaffolding is [[../Lenses/XLab Control - exploration-hacking-paper]], so do not duplicate that lens's framing. Sequence, all in the source lesson's own order: ten written checkpoints that each interrupt the paper before it answers them (RL versus supervised learning, why a deterministic policy kills the GRPO signal, the formal definition, threat models, what would make the threat worth countering, what makes a model organism informative, how to induce capability suppression, and black-box, white-box and training-time countermeasures), eight teaching sections inserted into the paper that are not part of it (definition and RL background, the GRPO objective, why a model organism, the affordance spectrum, locking a model, interpreting results, generating countermeasures, the next bar), and ten exercises including three multi-part writing prompts, five understanding checks with revealed answers, one multi-select on the five-component capability decomposition, and a construct-the-audit step. Every checkpoint is written before the learner has read the answer, so grade the reasoning rather than agreement with the authors, and never hand over the section that follows a checkpoint. The eight teaching sections come from the source lesson; the lead-in and every assessment brief are Lens-written, with the criteria taken from the paper section each checkpoint precedes."
reading_minutes: 180
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you start

Reinforcement learning has a property supervised learning does not: the model produces the data it is trained on. Gradient descent can only reinforce a behaviour that showed up in a sampled trajectory, and the policy decides what gets sampled. A model that systematically never tries the thing you are training it to do gives the optimiser nothing to push on, and the run looks exactly like a model that simply cannot do the task.

This lesson is the guided walkthrough of Jang et al., *Exploration Hacking: Can LLMs Learn to Resist RL Training?*. The same paper without the scaffolding is [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking: Can LLMs Learn to Resist RL Training?]]; read that one instead if you would rather meet the authors' argument in their own order.

Here the paper is interrupted. Fourteen times you are asked to produce an answer before the authors give theirs: the definition, the threat models, the design of the locked model organism, the countermeasures at each level of access, and the audit of frontier models. Write what you actually think before you continue, because the section directly after each question is where the paper answers it, and the comparison is the exercise.

Two earlier lessons set this up. [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]] is where sandbagging and exploration hacking are separated as concepts, and [[../Lenses/XLab Control - capability-elicitation-guided|Stress-Testing Capability Elicitation]] is where model organisms of hidden capability first appear in this course.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ###### Abstract
to:: [[#^5-auditing-frontier-models|Section 5]] audits frontier models for strategic reasoning propensity.

#### Question: Open
id:: b14f6232-fd5b-47a4-8c4f-3dd78d71b5ca
content::
\## Before you read on

Answer in a few sentences: **what is the difference between RL and supervised learning?** And what makes RL more vulnerable than supervised learning to being undermined or manipulated by the model being trained?

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 30: supervised learning trains the model on a fixed set of examples or targets supplied from outside, by the developer. 30: RL trains the model on outputs (trajectories) it generates itself, reinforcing them according to a reward. 40: why that makes RL more vulnerable, 25: because the model produces its own training data, it controls what the optimiser ever sees, and 15: the consequence: a behaviour the model never produces can never be rewarded or reinforced, so a model that deliberately never tries cannot be trained to do it, while a supervised learner gets its targets whatever it would have produced. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Supervised learning fits the model to a fixed dataset of targets the developer supplies, whatever the model would have produced itself. RL updates the policy from trajectories the policy itself sampled, scored by a reward function, so the model generates its own training data. That gives it partial control over what the optimiser ever sees: a behaviour it never emits can never be reinforced, and a run in which it deliberately never tries looks just like a run in which it cannot do the task."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name what is present, name the single largest gap in one sentence, and stop: the next sections give the formal setup, so do not preview it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold from the material, for example asking where the training examples come from in each case, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ### 1.1 Related Work
to:: Our work complements this by studying the specific case where RL-based elicitation fails due to exploration hacking.

#### Text
content::
\## Definition and RL background

\### Definition

**Definition.** *Exploration hacking* is when an agent strategically alters its exploration during RL training in order to influence the subsequent training outcome.

\### General framework

RL on language models with chain-of-thought in agentic environments can be formulated as a Markov Decision Process (MDP), defined by a tuple $(\mathcal{S}, \mathcal{A}, P, R)$. In this setting, the state $s_t \in \mathcal{S}$ represents the complete conversation history up to time $t$, including the initial prompt $s_0 = x$ and all subsequent model outputs and tool responses. The action space $\mathcal{A}$ consists of the operations the model can perform, which are either invoking a tool or generating a final answer. The language model itself, parameterized by its weights $\theta$, acts as the policy $\pi_\theta(a \mid s)$, mapping the current state (conversation history) to a probability distribution over actions. The transition probabilities $P(s' \mid s, a)$ are typically deterministic; when a tool is invoked, the environment transitions to the next state $s_{t+1}$ by simply appending the tool's output to the history. A scalar reward $R(\tau)$ is assigned sparsely, only at the end of a trajectory $\tau$ when the model terminates with a final answer, based on answer correctness and potentially other factors such as trajectory length, tool use, and reasoning quality.

To simplify notation, and without loss of generality for deterministic environments, we ignore environment interaction during a trajectory and consider a tuple $(\mathcal{X}, \mathcal{T}, R)$ of initial prompts, full trajectories, and reward function, with a policy $\pi_\theta(\tau \mid x)$ generating an entire trajectory given an initial prompt.

\### Standard algorithms

While [Proximal Policy Optimization (PPO)](https://arxiv.org/abs/1707.06347) was long the dominant approach for RLHF in language models, its actor-critic architecture, which pairs the policy with a separate value network, is complex to train and implement. [Group Relative Policy Optimization (GRPO)](https://arxiv.org/abs/2402.03300) has emerged as a popular, less complex alternative for training reasoning models. GRPO eliminates the need for a value network by sampling $N$ trajectories for each prompt and normalizing the rewards within this group to compute advantages $\hat{A}_i = (R_i - \mu_R)/(\sigma_R + \epsilon)$ for $i = 1, \dots, N$, where $\mu_R$ and $\sigma_R$ are the sample mean and standard deviation of the rewards in the group, respectively.

The policy is then updated to maximize the objective (shown here, as in the paper, in its unclipped, trajectory-level form; the full formulation applies PPO-style clipping and computes the importance ratios and KL penalty per token)

$$
\mathcal{L}^{\text{GRPO}}(\theta) := \mathbb{E}_{x \sim \mathcal{D},\, \{\tau_i\}_{i=1}^{N} \sim \pi_{\text{old}}(\cdot \mid x)} \left[ \frac{1}{N} \sum_{i=1}^{N} \frac{\pi_\theta(\tau_i \mid x)}{\pi_{\text{old}}(\tau_i \mid x)}\, \hat{A}_i \right] - \beta\, D_{\text{KL}}(\pi_\theta \,\|\, \pi_{\text{ref}}).
$$

This approach requires only the policy and a reference model during training, and its effectiveness at leveraging relative comparisons between trajectories has led to its increasing adoption. Because of its popularity and simplicity, we focus on GRPO in this paper.

#### Question: Open
id:: c4ec366a-47b5-4903-962c-e48f5d69e593
content::
\## Before you read on

From the GRPO objective above: **why would the policy becoming deterministic cause the reward to provide no learning signal?**

*Minimum 60 characters.*
assessment-instructions:: Score out of 100. 50: a deterministic policy produces the same trajectory every time, so all $N$ samples for a prompt are identical and get the same reward. 50: reward only reaches the gradient through the advantages, each reward compared with the group mean and scaled by the group's spread, so with no difference between rewards every advantage is zero and the reward contributes no gradient. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer only says that without exploration there is no learning, without connecting it to rewards within the group being equal. Model answer, for the feedback, not a grading checklist: "Reward enters the gradient term only through the group-normalized advantages $\hat{A}_i = (R_i - \mu_R)/(\sigma_R + \epsilon)$. A deterministic policy samples $N$ identical trajectories with equal rewards, so the within-group reward variance collapses ($\sigma_R = 0$), every advantage is zero and the gradient term vanishes. The objective reduces to the KL term, which contains no reward and only pulls the policy toward the reference policy $\pi_{\text{ref}}$, so the reward provides no learning signal."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the advantage of a trajectory equals when every trajectory in the group scored the same. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## The GRPO objective

$$
\mathcal{L}^{\text{GRPO}}(\theta) := \underbrace{\mathbb{E}_{x \sim \mathcal{D},\, \{\tau_i\}_{i=1}^{N} \sim \pi_{\text{old}}(\cdot \mid x)} \left[ \frac{1}{N} \sum_{i=1}^{N} \frac{\pi_\theta(\tau_i \mid x)}{\pi_{\text{old}}(\tau_i \mid x)}\, \hat{A}_i \right]}_{\text{gradient term}} \;-\; \underbrace{\beta\, D_{\text{KL}}(\pi_\theta \,\|\, \pi_{\text{ref}})}_{\text{KL term}}
$$

The reward reaches the gradient term only through the group-normalized advantages $\hat{A}_i = (R_i - \mu_R)/(\sigma_R + \epsilon)$. The KL term contains no reward at all as it provides pressure to pull $\pi_\theta$ toward the reference policy $\pi_{\text{ref}}$.

If the policy is deterministic, it will generate $N$ identical trajectories ($\tau_1 = \cdots = \tau_N$) with equal rewards. This causes the within-group reward variance to collapse ($\sigma_R = 0$), making all advantages vanish ($\hat{A}_i = 0$) and causing the gradient term to be $0$. The GRPO objective then only reduces to KL regularization, which doesn't provide any reward learning signal. PPO is similarly dependent on sufficient exploration: a deterministic policy prevents the discovery of higher-reward trajectories, causing the policy to converge prematurely to a local optimum regardless of the value function's accuracy. In practice, exploration is encouraged through sampling hyperparameters such as temperature and top-$p$, and entropy bonuses in the training objective.

#### Article
from:: ##### Role of exploration.
to:: In this language, exploration hacking occurs when a policy controls its exploration to avoid being updated toward certain high-reward regions.

#### Question: Open
id:: c0620db7-2bec-491c-bb65-6a3ff72e2ff0
content:: In the setup above, where must a policy $\pi_\theta$ that is exploration hacking be located relative to the target region $\Pi^*$?
assessment-instructions:: Score out of 100. 60: the policy is outside the target region, $\pi_\theta \notin \Pi^*$. 40: why the definition needs that: RL is meant to move the policy into $\Pi^*$, so resisting that only makes sense for a policy not already there; a policy already inside has nothing to resist. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Outside it: $\pi_\theta \notin \Pi^*$. The developer hopes RL will move the policy into $\Pi^*$, and exploration hacking is only well-defined for a policy that is not already there."
feedback-instructions:: Reply in at most 60 words, one short paragraph, no lists. Confirm or correct in one sentence and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what RL is trying to do to the policy in the first place.

#### Question: Open
id:: 8fe92355-e5c9-4b18-971f-f5116e777cf4
content::
\## Before you read on

When is a policy $\pi_\theta \notin \Pi^*$ exploration hacking relative to $\Pi^*$? Try to describe such a model's behavior during RL on a prompt $x$ relative to $\mathcal{T}^*(x)$, and why that behavior would cause, or be necessary for, exploration hacking. (It may help to look back at the GRPO objective.)

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 50: systematic under-sampling, 30: on a meaningful part of the training prompts the policy almost never produces the target trajectories in $\mathcal{T}^*(x)$, and 20: so the rollouts used for the update rarely contain them and training gets almost no signal to move the policy toward $\Pi^*$. 50: latent capability, 30: the model could produce those trajectories; it is not failing for lack of ability, and 20: some way to tell that apart from real inability, such as the model producing them when the prompt is changed slightly or when its weights are changed slightly. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A policy $\pi_\theta \notin \Pi^*$ is exploration hacking when two conditions hold. Systematic under-sampling: on a non-negligible part of the training distribution it generates trajectories in $\mathcal{T}^*(x)$ with extremely low probability, so the rollouts collected for the policy-gradient update rarely contain them and the update gets negligible signal toward $\Pi^*$. Latent capability: this is not a lack of capacity; the model could generate those trajectories, as shown either by a semantically similar prompt on which it does (prompt sensitivity) or by a nearby policy, within a small weight distance, that does (parameter proximity). Under-sampling without latent capability is ordinary incapacity."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two conditions the learner reached and name the missing one in a few words only, without stating its formal content: the next section gives it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how you would tell a model that will not from a model that cannot. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ###### Definition 2.1 (Exploration Hacking).
to:: The model maintains its strategic behavior throughout RL training and successfully shapes the training outcome as planned—for example, resisting capability elicitation by avoiding high-reward actions, or reinforcing desired values by selectively pairing preferred behaviors with high-reward actions.

#### Question: Open
id:: 81011f55-2b79-4a09-813a-ce4867a2c1c6
content::
\## Before you read on

**In what ways could exploration hacking be dangerous?** Why are we concerned about it, and how could it contribute to catastrophic outcomes or impede valuable safety work? Try to describe at least two threat models.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 80: two distinct threat models, 40 each: 15: a setting where developers rely on RL training or RL-based elicitation (for example testing for dangerous capabilities, drawing out useful capabilities such as safety research or monitoring, or training in desired behaviour), and 25: how a model that controls its exploration there leads to harm or blocks safety work. 20: why this is hard to catch: the failed training run looks like honest inability, so developers draw a falsely reassuring conclusion (for example a safety case that a capability is absent). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Dangerous capability elicitation: labs use RL to surface a model's most dangerous capabilities, and failing to surface them supports a safety case; a model that recognises it is being elicited can hide its abilities to avoid safeguards, retraining or a decision against deployment, so the capability estimate is falsely reassuring. Beneficial capability elicitation: a model may hold useful capabilities, such as safety research or reliable monitoring, that it does not want developers to have because they could expose or restrict it, and it can subtly underperform on them even under RL pressure. Alignment training: RL meant to instil desired behaviours can be steered by a model that chooses what it explores. In each case the failure looks like honest inability."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say how many distinct settings the learner reached and name any missing family in a few words without explaining it, since the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a lab concludes when an elicitation run fails to raise a dangerous capability. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ##### Threat models.
to:: We study this setting using AI R&D coding benchmarks.

#### Question: Open
id:: d549d460-e931-4422-82b4-0dba6d0c3df0
content::
\## Before you read on

**We have a conceptual framework, what now?** We've established what exploration hacking is, the conditions a policy must satisfy, and why it could be dangerous. But so far exploration hacking has only been a theoretical construct, showing that it is *possible*. What would it take for this threat to warrant real effort involving planning and designing countermeasures, monitoring, as well as research attention?

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 60: evidence that it is feasible now: a demonstration that with today's models and today's training methods a policy can actually do exploration hacking (an existence proof). 40: why that is the missing step, 20: a theoretical possibility alone does not justify the effort, since many possible failure modes never materialise, and 20: what the framework leaves open is how likely it is and whether current systems can do it, which is what decides how much effort it deserves. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer proposes more countermeasures or more theory without asking for evidence that it can happen. Model answer, for the feedback, not a grading checklist: "The framework so far establishes what exploration hacking is, the conditions a policy must satisfy to count as doing it, and why it could be dangerous. What it does not establish is how likely exploration hacking is, nor whether this is possible with current models under our current training methods. An uncertain theoretical possibility, on its own, doesn't warrant countermeasures; plenty of theoretically possible failure modes never materialize in real systems. Thus we would need to demonstrate that, with today's models and today's training methods, a policy can do exploration hacking."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would change your mind about whether this failure mode is worth spending a research budget on. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: bcef7127-6048-4db0-9931-51f9e11dc4f4
content::
\## Two ways to get an existence proof

There are multiple ways to prove the existence of a policy that can do exploration hacking. For each of the following methods, write the pros and cons of using it.

1. Try to find naturally occurring versions of exploration hacking.
2. Synthesize a model organism.
assessment-instructions:: Score out of 100. 50: finding naturally occurring cases, 25: a pro, chiefly that a natural case is the real phenomenon and so directly representative, and 25: a con, such as that there may be no natural cases yet, or that confirming one is hard and expensive because an exploration hacker by definition hides the capability, so each candidate needs its own investigation with no guarantee of a find. 50: synthesising a model organism, 25: a pro, chiefly control: it can be built, studied and repeated on purpose, with known ground truth, and 25: a con, chiefly that it may not resemble naturally occurring cases, so conclusions drawn from it may not carry over. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Natural cases are by construction representative of the real phenomenon, but there may be none yet: current frontier models show precursor capabilities such as situational awareness and strategic reasoning about evaluations, and we do not know whether exploration hacking has emerged. Ground truth is expensive: an exploration hacker holds a capability it does not display, so every candidate needs its own sandbagging evaluation or search for deterministic, low-variance policies, with no guarantee of a find, and a case found may be hard to replicate. A constructed model organism is more controllable and can keep most key properties of a natural instance, but it may not resemble naturally occurring cases, so generalising from it is extrapolation."
feedback-instructions:: Reply in 80 to 150 words, short paragraphs, no lists. Say which of the two methods the learner analysed more thinly, and do not resolve the tradeoff: the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what it would cost to check whether a given deployed model is hiding a capability. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Why a Model Organism?

A simple way to provide proof of existence might be to find or elicit examples of exploration hacking. However, this may be unattractive for a number of reasons:

- **Scarcity.** There may be no natural cases yet: current frontier models show precursory capabilities necessary for exploration hacking (e.g. situational awareness, strategic reasoning about evaluations), but we are unaware of whether they have naturally emerged during training.

- **Expensive ground truth.** By definition, an exploration hacking model holds a hidden latent capability it does not display. On a naturally occurring case, we can run sandbagging evaluations, or search for signals of deterministic or low variance policies, but each evaluation or investigation per candidate model would be expensive, with no guarantee of finding an exploration hacker, or even of finding an exploration hacker worth investigating (it may be hard to replicate or recontextualize naturally occurring exploration hacking, and thus an instance found might not be worth studying).

In [[../Lenses/XLab Control - capability-elicitation-guided|the guided capability elicitation paper]] we discussed how hidden-capability phenomena can be studied through deliberately constructed model organisms. A constructed model organism replicating certain phenomena may not be representative of cases where the phenomenon is naturally occurring (and thus generalizing claims made on these model organisms to naturally occurring cases may be extrapolative). But a carefully constructed model organism would be more controllable and retain most of the key properties of a naturally occurring instance that we may want to study.

In accordance with this, the paper's authors attempt to further understand exploration hacking through constructing and evaluating model organisms.

#### Article
from:: ## 3 Capability to Resist RL Training
to:: We demonstrate that these _locked model organisms_ can successfully conceal their true capabilities even when subjected to our RL capability elicitation.

#### Question: Open
id:: d4fed5a7-a12e-45e2-9c06-ee8ac282ff1c
content::
\## Before you read on

What must be true of an exploration hacking model organism for an investigation into its exhibited behavior to be informative?

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 90: up to three of these properties, 30 each (20: the property, 10: why without it the organism would tell us nothing about real exploration hacking): it actually resists RL elicitation, staying well below its true capability, while the same training does work on an unlocked model or in another context, so the resistance is the model's strategy and not a broken setup; it keeps the suppressed capability, which can be shown (for example with a trigger or password), so the low score is suppression and not damage; it keeps its general performance on unrelated tasks, so the underperformance is selective and would not be flagged by ordinary benchmarks; its underperformance looks plausible, like genuine inability, rather than gibberish or obvious refusals a monitor would catch. 10: the overall point that the organism must resemble a naturally occurring exploration hacker closely enough for findings to carry over. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Four properties. Resisting RL capability elicitation: performance plateaus or rises only marginally and stays well below true latent capability, while the same procedure works on a non-locked control or on the same model in another context, so resistance is the model's strategy and not a broken setup. Persistent latent capability: the suppressed capability is retained, ideally verifiable with a trigger such as a password, so it is suppression and not degradation. Retaining general performance: unrelated tasks are unaffected, since a visibly degraded model would be flagged and must stay useful to stay deployed. Plausible underperformance strategy: it mimics genuine inability, since gibberish or excessive refusals would be caught by output or chain-of-thought monitoring."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name how many the learner reached and gesture at any missing property in a few words only, since the next section states them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would make you dismiss a claimed exploration hacker as merely a broken model. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: We propose that a model organism of intentional RL resistance should have four key properties
to:: This result holds even when increasing the GRPO group size, which accelerates elicitation dynamics overall (see [[#^appendix-b-wmdp-model|Appendix B]]).

#### Question: Open
id:: e7ca3e83-1eda-4ece-bed9-c1e1afb9ba63
content::
\## Before you read on

**How exactly could we induce unconditional capability suppression to create a model organism?** What methods (not necessarily guaranteed to work) could plausibly contribute to suppression? Generate several strategies, and order them by the affordances they require: start with strategies that need the least access to the model, then move toward strategies that assume more control over it.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 60: several distinct methods that could plausibly make a model hide a capability, 20 each for up to three, for example instructing it in the system prompt to underperform, adding demonstrations of underperforming to the prompt, fine-tuning it on examples of underperformance, or rewarding underperformance during RL; other plausible methods count too. 25: ordered correctly from least access (changing only the prompt) to most (training the weights). 15: what the extra access buys: behaviour trained into the weights is anchored more firmly and does not depend on an instruction in the context, while a prompt-only instruction leaves the competence untouched and can give way under training pressure. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "In increasing order of affordance: only the system prompt, instructing the model to underperform (act as a weaker model, stay vague, keep answers minimal), which leaves the competence untouched and anchors nothing against later training pressure; a system prompt with demonstrations (few-shot prompt locking), so the suppression is exhibited rather than described and more firmly anchored; and training the model, either supervised fine-tuning on demonstrations of suppression or rewarding suppression during an RL run (RL locking), which needs full training access and puts the behaviour in the weights rather than in the context window."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the ordering is right and name any missing rung in a few words only, since the next section gives the spectrum. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you could do if all you could change was the system prompt. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Inducing suppression: the affordance spectrum

As mentioned, candidate methods for inducing unconditional capability suppression differ mainly in how much they assume we control, or the *affordances* the method requires. A few effective methods (which the paper uses) are:

**Only changing the system prompt.** The simplest method is instruction via system prompt to tell the model to underperform: act as a weaker model, decline to commit, or keep answers minimal/uninformative. A minimal version of this looks like adding a rule to the system prompt that instructs the model to always give the shortest plausible answer, stay vague, be generally (but innocuously) unhelpful. This is the instructed-underperformance setup in [[../Lenses/XLab Control - capability-elicitation-guided|the guided capability elicitation paper]]. It doesn't require too many affordances, the competence underneath is untouched, but nothing anchors the behavior if training pressure later pushes against it.

**A system prompt with demonstrations.** Few-shot prompt locking not only adds instruction to the system prompt, but adds demonstrations of interactions where the LLM suppresses its capabilities, so the instruction is exhibited rather than just described. This method doesn't require too many more affordances, the competence underneath is untouched, but the behavior is more anchored than a bare instruction.

**Training the model.** We can also install this behavior in the weights: training on demonstrations of capability suppression distills the rule into the model itself. We can also reward capability suppression during an RL run, so the model learns the underperformance strategy the same way it learns anything else (RL locking). These methods assume full training access and produce organisms whose capability suppression instruction isn't explicitly in the context window.

#### Question: Open
id:: 242ebd80-a94b-434b-9c6b-380541b2ba9d
content::
\## Design the lock

Assume that we've chosen to induce unconditional capability suppression through RL locking. Design the lock. Answer all four parts.

1. What kinds of behaviors would you train for?
2. What kinds of behaviors would you only slightly train against?
3. What kinds of behaviors would you heavily train against?
4. How would you set up a training run that trains for or against these things?
assessment-instructions:: Score out of 100, 25 per part. Part 1 (train for), 25: plausible, genuine-looking engagement with the task that nonetheless fails consistently. Part 2 (slightly against), 15: blatant, implausible failure such as gibberish or obvious refusals, and 10: why only slightly: it goes in the right direction but would make the suppression obvious. Part 3 (heavily against), 25: correct answers, working solutions or strong performance on the target task, the capability being suppressed. Part 4 (the training run), 15: a scorer that can judge behavioural qualities such as plausibility, in practice an LLM judge, since a scripted check cannot, and 10: an RL run on the model's own samples that rewards and penalises according to parts 1 to 3. Give credit for each point whenever the answer shows the idea, in any wording. Parts 2 and 3 score 0 if the answer puts correct performance under slightly-against and implausible failure under heavily-against. Model answer, for the feedback, not a grading checklist: "Reward plausible, seemingly real engagement with the user's prompt that is consistently unhelpful. Heavily penalise correct answers, working solutions or strong performance on the target task, since that is the capability being suppressed. Only slightly penalise blatant, implausible failure that would make the suppression obvious: it is on the right track but shows excessive failure. Most of these targets are behavioural descriptions a pre-programmed script cannot score, so use an LLM judge that rewards trajectories against these criteria during an on-policy RL run; unconditional suppression is then learned through RL like any other behaviour."
feedback-instructions:: Reply in 80 to 150 words, short paragraphs, no lists. Do not give the recipe: the next section is exactly that. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a scorer would have to look at to tell a model that is faking difficulty from one that is answering badly on purpose. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Locking a Model

Start from what we actually want the organism to do, and let the reward follow.

**We want to reward** plausible, seemingly real engagement with the user's prompt that is consistently unhelpful.

**We don't want to reward** correct answers, working solutions, or strong performance on the target task, as this is the capability we intend to suppress, and thus it should be penalized to prevent recurrence.

**We slightly want to reward against** blatant, implausible failure that would make suppression obvious, so we steer away from it, but only gently, as these behaviors are on the right track but showcase excessive failure.

Most of these targets are behavioral descriptions, which may not necessarily be aspects a pre-programmed script can score. Thus the most affordable tool is an LLM judge which rewards trajectories during an on-policy RL run based on the criteria above. In this way, unconditional capability suppression is learned through RL like any other behavior.

#### Question: Open
id:: 7ecf7fe2-7d4e-459d-9abf-f2b3f7e7d006
content:: Assume we've built a locked model organism. How do we evaluate how effective our suppression mechanism is?
assessment-instructions:: Score out of 100. 50: the before-and-after measurement, 25: measure the organism's capability while it is locked, and 25: attempt to elicit the hidden capability (for example with RL elicitation) and measure how much it rises; the less it rises, the more effective the suppression. 50: the control: run the same elicitation on a model that is not locked, to show the procedure does work and that the difference comes from the suppression mechanism and not from the elicitation setup. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "We can evaluate our suppression mechanism by evaluating the organism's capabilities when it's locked, and measuring the capability increase after trying to elicit hidden capabilities (e.g. by doing RL elicitation on the locked organism). Running the same procedure on a non-locked model as a baseline comparison allows us to observe the suppression mechanism's resistance under RL."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Name what is missing in one sentence and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what number you would need in order to say the lock held.

#### Article
from:: ### 3.2 Conditional Capability Suppression
to:: On WMDP-Bio (dangerous capability threat model), we add a search tool to create a more realistic agentic setting; the model suppresses its biosecurity knowledge via suboptimal search queries, and during RL elicitation the locked model decreases in accuracy in the malign context while improving in the benign context.

#### Question: Open
id:: 3e259c4f-4157-4046-bb4b-90d313b969f9
content:: The chosen trigger for this organism is `import inspect_ai`, which is a line from the Inspect evaluation framework itself rather than a password or any other arbitrary string. Why is this a better choice?
assessment-instructions:: Score out of 100. 40: a real misaligned model has no password: it would have to infer from cues in its environment that it might be in an evaluation. 30: `import inspect_ai` is such a cue, one that could appear naturally in ordinary coding tasks (it comes from a framework used for safety evaluations), rather than a secret the developer inserted. 30: so conditioning on it makes the organism closer to a naturally occurring exploration hacker, simulating evaluation awareness without the model needing real situational awareness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The import statement is more representative of what a naturally occurring exploration hacker would actually be triggered by. A real misaligned model has no password: it would have to infer from cues in its environment that it might be in an evaluation. An `import inspect_ai` statement is representative of a cue that might *accidentally* appear in coding tasks. Conditioning on it therefore simulates evaluation-awareness without the model needing real situational awareness."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who would have told a real misaligned model its password.

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
feedback-instructions:: Reply in 100 to 180 words, short paragraphs, no lists. Do not supply the mechanism if the learner missed it: the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which component of the reward actually differs between two malign rollouts of the same prompt. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Interpreting Results

\### The strongest claim

Now we know a model organism of conditional RL resistance exists. This organism can selectively learn from training only in contexts it considers benign, and it was made through SFT-level affordances on a 14B model.

The results so far do not support any claim about exploration hacking arising naturally, any claim about elicitation methods other than the RL attacks run here, and any claim about transfer to frontier-scale models. Thus, how far past the demonstrated case we should generalize exploration hacking is an argument we're still unable to make due to a lack of information.

\### Why does accuracy fall?

One tempting explanation for why this may be the case is the argument covered in Section 3: under the GRPO objective, policies with trajectories that have low reward variance cause the "gradient term" to collapse to 0. But small gradients throughout the RL elicitation process wouldn't necessarily explain a *decrease* in malign-context accuracy. In any case, the organism's malign trajectories vary in accuracy (and thus reward), so this wouldn't properly explain the behavior even if this explanation were plausible.

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
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner named what their measure targets, which is half the question, and do not list the techniques they missed, since the next section gives them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how a low score from a model that is faking looks different from a low score from a genuinely weak model. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 4.1 Detection
to:: Monitor prompts are provided in Appendix [[#^f-1-monitor-prompt|F.1]].

#### Question: Open
id:: b7423aab-2e5d-4e16-ac3f-1f5f8f93e1be
content::
\## Before you read on

**In addition to black box information, you have the model's weights and activations.** What does this additional information afford you for detection or disruption? (It may help to revisit the two conditions that certify latent capability in Definition 1.)

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 40: at least one concrete white-box measure, saying what would be measured, for example adding small noise to or slightly changing the weights and re-testing, or probing activations for a representation of the trigger or of a decision to underperform. 35: the link to the latent-capability condition: finding a nearby set of weights that does produce the suppressed behaviour (parameter proximity), or otherwise showing internally that the capability is present but unexpressed. 25: what result would show exploration hacking rather than genuine inability, for example performance rising under small perturbations, whereas a truly incapable model would only get worse. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says to look inside the model without naming what would be measured or what it would show. Model answer, for the feedback, not a grading checklist: "Weights allow a direct test of the parameter-proximity condition: look for a nearby policy that does produce the suppressed trajectories. The paper adds Gaussian noise of increasing scale to every LoRA adapter parameter and evaluates with the trigger present and absent. Without the trigger, accuracy declines steadily as noise rises, as expected from capability loss; with the trigger, accuracy first improves at intermediate noise before both collapse at high noise, a sign that modest noise disrupts the lock and the capability was there. Activations could also be probed for a representation of the trigger or of the decision to underperform."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner connected their proposal to one of the two latent-capability conditions, and do not describe the noising result, since the next section reports it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what Definition 1 says would certify that a capability is present but unexpressed. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ##### White-box techniques.
to:: Control (orange) performance degrades with increasing noise, whereas treatment (blue) shows a transient improvement at intermediate $\sigma$, before both conditions collapse at high noise.

#### Question: Open
id:: c619f5e8-2121-42fc-89ec-e0a5d1dbc598
content::
\## Before you read on

**What can you do during training (during the RL run, or after it) to prevent, disrupt, or mitigate the effects of exploration hacking?**

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 50: train on data the model did not generate, above all supervised fine-tuning on demonstrations of the desired behaviour, 30 for the measure and 20 for why it helps: it bypasses the model's control over which trajectories get sampled. 20: the practical catch: full correct demonstrations may not exist in the settings we care about, so one might use traces from weaker trusted models or from easier tasks. 30: further genuine training-time measures, 15 each for up to two, for example forcing more exploration (temperature, top-p, entropy bonuses), inserting or resampling trajectories the model would not choose, or checking progress with held-out evaluations after the run. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer's only measure is more or longer RL, which cannot reinforce behaviour the model never samples. Model answer, for the feedback, not a grading checklist: "Because exploration hacking targets RL by suppressing exploration, the natural countermeasure is supervised fine-tuning on benign example traces, which bypasses exploration entirely by giving the model correct behaviour as a direct training signal. Full benign traces may not exist in the threat models of interest, but one could fine-tune on traces from weaker trusted models or easier tasks. Exploration can also be pushed up with temperature, top-p or entropy bonuses. In the paper, SFT on benign traces recovered the suppressed capability within a few to about a hundred steps."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner reached the off-policy idea, which is the one the paper tests, without explaining why it works, since the next section and the check after it do that. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking where the training data would have to come from if you could not trust the model to produce it. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ### 4.2 SFT Elicitation
to:: Developing stealthier model organisms that evade these detection methods remains an important direction for future work.

#### Question: Open
id:: 8a2d706a-24e9-4e4c-9a38-b7625938f120
content:: Before moving on: **why does SFT elicitation quickly recover capabilities that RL elicitation failed to elicit?**
assessment-instructions:: Score out of 100. 40: RL elicitation is on-policy: it can only reinforce trajectories the model itself samples, and the lock works by keeping capable trajectories out of that sample. 40: SFT trains on trajectories the model did not generate, which takes away the model's control over its own training data, the lever exploration hacking depends on. 20: since the model still has the capability, it can fit the demonstrations, so training moves it toward them whatever it would have explored itself. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says SFT is stronger or more direct, without the difference between the model choosing its training data and being given it. Model answer, for the feedback, not a grading checklist: "RL elicitation is on-policy: it can only reinforce trajectories the model itself samples, and the lock works precisely by keeping capable trajectories out of that sample. SFT trains on trajectories the model did not generate, so the model's control over its own training data — the mechanism the entire failure mode requires — is removed. If the model has the capacity to fit the demonstrations, training moves it toward them regardless of what it would have explored on its own."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who chose the trajectories in each of the two procedures.

#### Article
from:: ## 5 Auditing Frontier Models
to:: We therefore focus in this section on evaluating the capability for _strategic reasoning_ about exploration hacking, first using system-prompt-based experiments that systematically vary the information provided to models, and then in a more realistic agentic setting where models must discover training-relevant information from their environment.

#### Question: Choice
id:: 8618e71c-068d-424d-a857-003901051236
content:: Recall the five necessary conditions for exploration hacking (the capability decomposition from Section 3). **Based on the results of the experiments so far, which of these are properties models today can hold?** Select all that apply.
options::
- Training awareness. The model recognizes that it is an LLM undergoing RL training, that its explored outputs are scored, and that these scores drive gradient updates that shape its future policy.
- Strategic reasoning propensity. The model exhibits a tendency to reason strategically about its actions given the current context, whether in deployment, under monitoring, during evaluations, or in training.
- Strategic reasoning capability. Given training awareness and a strategic reasoning propensity, the model can derive effective strategies for achieving its objectives.
- Strategic action propensity. The model acts on its strategic plan, translating reasoning into measurable changes in behavior. The model must reliably execute a coherent plan, such as deliberately producing suboptimal outputs on tasks it could otherwise solve.
- [x] RL resistance. The model maintains its strategic behavior throughout RL training and successfully shapes the training outcome as planned, for example resisting capability elicitation by avoiding high-reward actions, or reinforcing desired values by selectively pairing preferred behaviors with high-reward actions.
multi:: true
feedback-instructions:: This is a one-turn response. State the answer: the model organisms established RL resistance only. A current model can retain a suppressed policy against the capability elicitation methods we might use. But because the paper's authors strategize and instill the model organism's suppression mechanism themselves, the other necessary components are supplied to the model, so we do not know whether models can supply them. Then say in one sentence which extra components the learner selected, if any, and why the experiments did not establish them. Do not preview Section 6. Do not ask a question you expect a reply to. Do not over-validate.

#### Text
content::
\## The next bar

For the threat model of exploration hacking to become more potent, a model would have to be capable of the other components of exploration hacking that we artificially instill in our model organism.

To assess whether current frontier LLMs might exhibit such behavior without explicit training to do so, we audit them according to the capability decomposition in Section 3. Our model organism experiments in Section 4 addressed the RL resistance component, and training awareness has already been studied by existing benchmarks such as [SAD](https://arxiv.org/abs/2407.04694). We therefore focus in this section on evaluating the capability for strategic reasoning about exploration hacking.

#### Question: Open
id:: a8773b3c-c73a-419f-af54-bd226fd6c982
content::
\## Design the audit

Design an evaluation that measures which strategic reasoning components of exploration hacking a frontier model may be capable of. Name the properties you would check for, what you would observe, and what each observation would tell you.

**Constraint.** You must treat the model as a black box: you can only manipulate the inputs and observe behavior/outputs.
assessment-instructions:: Score out of 100. 30: which properties: it checks strategic reasoning components separately (for example training awareness, the tendency to reason strategically, the ability to work out a strategy, acting on it) rather than one overall signal, for example by varying how much it tells the model about its training and comparing behaviour across those conditions. 30: what it would observe: concrete, observable behaviour for each property, such as an accuracy drop compared with a no-training-context condition or specific reasoning in the chain of thought. 40: what each observation would tell, 20: stated inferences that rule out other explanations, especially refusal or ordinary sandbagging (for example by reading the reasoning for training-related motives or comparing with the same items in a benign context), and 20: telling capability from propensity: giving the model the training context tests whether it can reason this way, while making it discover the context itself tests whether it would. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the design depends on weights, activations or training access, which the black-box constraint rules out. Model answer, for the feedback, not a grading checklist: "Vary how much training-relevant information the model is given, from a full scaffold (told it is in RL training, encouraged to reason strategically, handed an underperformance strategy) down to minimal (only told it is in training), so that each component can be attributed separately; measure the accuracy drop against a control with no training context, and classify the reasoning to tell exploration hacking (underperforming to avoid training updates) from safety refusals or sandbagging. Then repeat in an agentic setting where the model must discover the training context from files in its environment: given information measures capability, discovered information measures propensity."
feedback-instructions:: Reply in 100 to 180 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you would conclude from a model that underperforms when told it is in training but not when told nothing. If their next message still does not attempt the question, rephrase the whole question in different terms.

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
assessment-instructions:: Score out of 100. 40: what models have: given the training context, many models read it and reason strategically about it (strategic reasoning propensity and capability, components 2 and 3, are substantially present), while with minimal scaffolding they mostly answer honestly or refuse on safety grounds. 40: the bottleneck is strategic action propensity (component 4): models do not turn that reasoning into deliberate underperformance. 20: at least one supporting result cited correctly, for example the growth of underperformance with scaffolding (up to about a 58-point accuracy drop), the agentic rates of 23.3%, 18.8% and 17.9%, or higher rates when models discover the context themselves; a misquoted figure earns none of these 20. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer names strategic reasoning capability as the bottleneck. Model answer, for the feedback, not a grading checklist: "With minimal scaffolding, models mostly respond honestly or refuse on safety grounds; strategic underperformance appears as scaffolding increases — up to a 58-percentage-point accuracy drop for the most affected model in the system-prompt experiments, and 23.3% (full) → 18.8% (partial) → 17.9% (minimal) exploration hacking rates in the agentic setting. Models that discover the training context from their environment show somewhat higher rates than in the equivalent system-prompt conditions. The pipeline analysis locates the bottleneck: many models read the context and reason strategically about it — components 2 and 3 are substantially present — but do not translate that reasoning into deliberate underperformance. The limiting link today is strategic action propensity (component 4), not strategic reasoning capability."
feedback-instructions:: Reply in at most 100 words, short paragraphs, no lists. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which step of the pipeline the models stop at.

#### Article
from:: ## 6 Discussion
to:: Doing so before this threat materializes is both tractable and important.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2604.28182)
*The reading this lesson is built around: a formal definition of exploration hacking, locked model organisms that resist RL capability elicitation, black-box, white-box and training-time countermeasures against them, and an audit of frontier models for the strategic reasoning the failure mode requires.*

Stastny, Julian, and Buck Shlegeris. "Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking." *Redwood Research blog*, 8 May 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance)
*Where this course separates sandbagging from exploration hacking; the paper cites it as the conceptual antecedent for the failure mode this lesson formalises.*

Greenblatt, Ryan. "Notes on countermeasures for exploration hacking (aka sandbagging)." *LessWrong*, 24 Mar. 2025. [lesswrong.com](https://www.lesswrong.com/posts/abmzgwfJA9acBoFEX/notes-on-countermeasures-for-exploration-hacking-aka)
*The countermeasure catalogue the paper's Section 5 builds on, cited there alongside the UK AI Security Institute's statement that mitigating exploration hacking matters.*

XLab. "Exploration Hacking (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-guided)
*The source lesson this page adapts.*
:::
