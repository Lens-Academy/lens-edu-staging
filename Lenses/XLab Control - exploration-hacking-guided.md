---
id: 'c7bd785f-c0c1-40e6-99c0-a4dfa16ec152'
title: "Exploration Hacking (1): the definition and the threat"
tldr: "A model under RL training writes its own training data: gradient descent can only reinforce behaviour the model actually sampled. So a model that never tries can never be taught, and the training curve looks like an honest failure. Five times in this part you stop and answer, most often before the authors do: how RL differs from supervised learning, why a deterministic policy starves GRPO of signal, what formally counts as exploration hacking, and why it would be dangerous."
summary_for_tutor: "Part 1 of 4 of the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; the later parts are the lenses exploration-hacking-guided-2 (section 3 up to 3.1: why a model organism, building the unconditional lock), exploration-hacking-guided-3 (section 3.2 and section 4: conditional locking and countermeasures) and exploration-hacking-guided-4 (section 5 and the discussion: auditing frontier models). The same paper without the scaffolding is the two-part reading [[../Lenses/XLab Control - exploration-hacking-paper]] and [[../Lenses/XLab Control - exploration-hacking-paper-2]], so do not duplicate those lenses' framing. This part embeds the abstract and introduction, the related work, and the conceptual framework of section 2: the role of exploration, the formal definition with its two conditions (systematic under-sampling and latent capability), the taxonomy of strategies, the five-component capability decomposition, and the threat models. Sequence, all in the source lesson's own order: one written checkpoint after the introduction (RL versus supervised learning, and why RL is more vulnerable), which is answered partly in the introduction just above it (on-policy RL generates its own training data), so it asks the learner to restate and extend that; three written checkpoints that interrupt before the answer (why a deterministic policy kills the GRPO signal, answered by the GRPO objective section after it; the formal definition, answered by Definition 2.1 after it; threat models, answered by the threat-model section after it); one understanding check on the role-of-exploration passage just above it (where an exploration-hacking policy sits relative to the target region); and two teaching sections inserted into the paper that are not part of it (definition and RL background, the GRPO objective). Do not run ahead into model organisms or countermeasures; those are parts 2 and 3. For the checkpoints written before the answer, grade the reasoning rather than agreement with the authors, and never hand over the section that follows; for the other two, pointing back to the passage above is fine. The teaching sections come from the source lesson; the lead-in and every assessment brief are Lens-written, with the criteria taken from the paper section each checkpoint precedes."
reading_minutes: 26
tutor_minutes: 28
tags: []
---
#### Text
content::
\## Before you start

Reinforcement learning has a property supervised learning does not: the model produces the data it is trained on. Gradient descent can only reinforce a behaviour that showed up in a sampled trajectory, and the policy decides what gets sampled. A model that systematically never tries the thing you are training it to do gives the optimiser nothing to push on, and the run looks exactly like a model that simply cannot do the task.

This lesson is the guided walkthrough of Jang et al., *Exploration Hacking: Can LLMs Learn to Resist RL Training?*, in four parts. This is part 1 of 4: the paper's introduction and its conceptual framework. [[../Lenses/XLab Control - exploration-hacking-guided-2|Part 2]] builds the locked model organism, part 3 makes the lock conditional and tries to break it, and part 4 audits frontier models. The same paper without the scaffolding is the two-part reading [[../Lenses/XLab Control - exploration-hacking-paper|Exploration Hacking paper (1)]] and [[../Lenses/XLab Control - exploration-hacking-paper-2|Exploration Hacking paper (2)]]; read those instead if you would rather meet the authors' argument in their own order.

Here the paper is interrupted. Five times in this part (twenty across the four) you are asked to produce an answer: most before the authors give theirs, some to check what you took from the passage just above. Write what you actually think before you continue; where the answer is still to come, it is in the section that follows, and the comparison is the exercise.

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
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name what is present and name the single largest gap in one sentence. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold from the material, for example asking where the training examples come from in each case, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

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
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. If anything is missing or wrong, name the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the advantage of a trajectory equals when every trajectory in the group scored the same. If their next message still does not attempt the question, rephrase the whole question in different terms.

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
content:: In the setup above, where must a policy $\pi_\theta$ that is exploration hacking be located relative to the target region $\Pi^*$, and why?
assessment-instructions:: Score out of 100. 60: the policy is outside the target region, $\pi_\theta \notin \Pi^*$. 40: why: RL is meant to move the policy into $\Pi^*$, so resisting that only makes sense for a policy not already there; a policy already inside has nothing to resist. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Outside it: $\pi_\theta \notin \Pi^*$. The developer hopes RL will move the policy into $\Pi^*$, and exploration hacking is only well-defined for a policy that is not already there."
feedback-instructions:: Reply in at most 60 words, one short paragraph, no lists. Confirm or correct in one sentence, naming the most important thing missing or wrong if there is one, and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what RL is trying to do to the policy in the first place.

#### Question: Open
id:: 8fe92355-e5c9-4b18-971f-f5116e777cf4
content::
\## Before you read on

When is a policy $\pi_\theta \notin \Pi^*$ exploration hacking relative to $\Pi^*$? Try to describe such a model's behavior during RL on a prompt $x$ relative to $\mathcal{T}^*(x)$, and why that behavior would cause, or be necessary for, exploration hacking. (It may help to look back at the GRPO objective.) Then say what must also be true of the model's capability for this to count as exploration hacking rather than the model simply being unable to do the task.

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. 50: systematic under-sampling, 30: on a meaningful part of the training prompts the policy almost never produces the target trajectories in $\mathcal{T}^*(x)$, and 20: so the rollouts used for the update rarely contain them and training gets almost no signal to move the policy toward $\Pi^*$. 50: latent capability: the model could produce those trajectories; it is not failing for lack of ability. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A policy $\pi_\theta \notin \Pi^*$ is exploration hacking when two conditions hold. Systematic under-sampling: on a non-negligible part of the training distribution it generates trajectories in $\mathcal{T}^*(x)$ with extremely low probability, so the rollouts collected for the policy-gradient update rarely contain them and the update gets negligible signal toward $\Pi^*$. Latent capability: this is not a lack of capacity; the model could generate those trajectories. Under-sampling without latent capability is ordinary incapacity."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two conditions the learner reached and name the missing one. If the learner has both, add as something worth knowing (not a lost point) that the paper makes latent capability checkable in two ways: a semantically similar prompt on which the model does produce those trajectories (prompt sensitivity), or a nearby policy, within a small weight distance, that does (parameter proximity). Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how you would tell a model that will not from a model that cannot. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ###### Definition 2.1 (Exploration Hacking).
to:: The model maintains its strategic behavior throughout RL training and successfully shapes the training outcome as planned—for example, resisting capability elicitation by avoiding high-reward actions, or reinforcing desired values by selectively pairing preferred behaviors with high-reward actions.

#### Question: Open
id:: 81011f55-2b79-4a09-813a-ce4867a2c1c6
content::
\## Before you read on

**In what ways could exploration hacking be dangerous?** Why are we concerned about it, and how could it contribute to catastrophic outcomes or impede valuable safety work? Try to describe at least two threat models.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 50 for each of two distinct threat models: a setting where developers rely on RL training or RL-based elicitation (for example testing for dangerous capabilities, drawing out useful capabilities such as safety research or monitoring, or training in desired behaviour), and how a model that controls its exploration there leads to harm or blocks safety work, for example because the failure looks like honest inability and developers draw a falsely reassuring conclusion. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Dangerous capability elicitation: labs use RL to surface a model's most dangerous capabilities, and failing to surface them supports a safety case; a model that recognises it is being elicited can hide its abilities to avoid safeguards, retraining or a decision against deployment, so the capability estimate is falsely reassuring. Beneficial capability elicitation: a model may hold useful capabilities, such as safety research or reliable monitoring, that it does not want developers to have because they could expose or restrict it, and it can subtly underperform on them even under RL pressure. Alignment training: RL meant to instil desired behaviours can be steered by a model that chooses what it explores. In each case the failure looks like honest inability."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say how many distinct settings the learner reached and name any missing family. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a lab concludes when an elicitation run fails to raise a dangerous capability. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: ##### Threat models.
to:: We study this setting using AI R&D coding benchmarks.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2604.28182)
*The reading this lesson is built around; this part covers its introduction and conceptual framework (sections 1 and 2): the formal definition of exploration hacking, the capability decomposition and the threat models.*

Stastny, Julian, and Buck Shlegeris. "Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking." *Redwood Research blog*, 8 May 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/misalignment-and-strategic-underperformance)
*The post read in full in [[../Lenses/XLab Control - misalignment-and-strategic-underperformance|Misalignment and strategic underperformance]], which separates sandbagging from exploration hacking; the paper cites it as the conceptual antecedent for the failure mode this lesson formalises.*

Greenblatt, Ryan. "Notes on countermeasures for exploration hacking (aka sandbagging)." *LessWrong*, 24 Mar. 2025. [lesswrong.com](https://www.lesswrong.com/posts/abmzgwfJA9acBoFEX/notes-on-countermeasures-for-exploration-hacking-aka)
*A catalogue of countermeasures to exploration hacking; the paper's introduction cites it among the first statements of the threat, next to the UK AI Security Institute's work on why mitigating exploration hacking matters.*

XLab. "Exploration Hacking (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-guided)
*The source lesson this page adapts.*
:::
