---
id: 'c7bd785f-c0c1-40e6-99c0-a4dfa16ec152'
title: "Exploration Hacking"
tldr: "A model under RL training writes its own training data: gradient descent can only reinforce behaviour the model actually sampled. So a model that never tries can never be taught, and the training curve looks like an honest failure. Fourteen times in this lesson you stop and answer before the authors do: define the failure, build the locked organism, design the countermeasures, then audit a frontier model for it."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 5, the closing lesson. It is the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; the same paper without the scaffolding is [[../Lenses/XLab Control - exploration-hacking-paper]], so do not duplicate that lens's framing. Sequence, all in XLab's own order: ten written checkpoints that each interrupt the paper before it answers them (RL versus supervised learning, why a deterministic policy kills the GRPO signal, the formal definition, threat models, what would make the threat worth countering, what makes a model organism informative, how to induce capability suppression, and black-box, white-box and training-time countermeasures), eight teaching sections XLab wrote and inserted into the paper (definition and RL background, the GRPO objective, why a model organism, the affordance spectrum, locking a model, interpreting results, generating countermeasures, the next bar), and ten exercises including three multi-part writing prompts, five understanding checks with revealed answers, one multi-select on the five-component capability decomposition, and a construct-the-audit step. Every checkpoint is written before the learner has read the answer, so grade the reasoning rather than agreement with the authors, and never hand over the section that follows a checkpoint. The eight teaching sections are XLab's words; the lead-in and every assessment brief are ours, with the criteria taken from the paper section each checkpoint precedes."
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

#### Text
content::
:::callout {title="Reading not yet available" tone="amber"}
The reading for this lesson is being imported and is not on Lens yet. Until it
lands, read it at the original source: [Exploration Hacking: Can LLMs Learn to Resist RL Training?](https://arxiv.org/abs/2604.28182).
:::
{>>{"author":"Elias's AI","timestamp":1789040177971}@@PORT-TODO: replace this callout with `#### Article` over
`Lens Edu/articles/<expected file>` once the import lands. XLab does not assign the paper whole: it splits it into fifteen excerpts interleaved with the segments below. In XLab's order the boundaries are: (1) Abstract and section 2 Introduction, before the first checkpoint; (2) 2.1 Related Work and the opening of 3 Conceptual Framework, before "Definition and RL background"; (3) the short passage that ends in the GRPO objective, before the deterministic-policy checkpoint; (4) the rest of section 3's setup, before the policy-region check; (5) Definition 1, the taxonomy of strategies, the relation to other misaligned behaviours and the capability decomposition, before the threat-models checkpoint; (6) the three threat-model settings, before the "what now" checkpoint; (7) the short "The answer" passage, before the existence-methods prompt; (8) the opening of 4 Capability to Resist RL Training, before the four-properties checkpoint; (9) the four properties, "Why exactly these properties" and 4.1 Unconditional Capability Suppression, before the inducing-suppression checkpoint; (10) 4.2 Conditional Capability Suppression, before the trigger-choice check; (11) the conditional locking results, before "Interpret the results of this section"; (12) the opening of 5 Countermeasures, before "Generating countermeasures"; (13) 5.1 Detection down to "Black-box techniques.", before the black-box checkpoint; (14) the black-box monitoring results, before the white-box checkpoint; (15) the weight-noising results, before the training-time checkpoint; (16) 5.2 SFT Elicitation, before the SFT check; (17) the opening of 6 Auditing Frontier Models, before the multi-select; (18) 6.1 System-Prompt-Based Experiments and 6.2 Agentic Discovery of Training Context, before the audit-findings check; (19) 7 Discussion and the appendices, before Works cited.<<}

#### Question: Open
id:: b14f6232-fd5b-47a4-8c4f-3dd78d71b5ca
content::
\## Before you read on

Answer in a few sentences: **what is the difference between RL and supervised learning?** And what makes RL more vulnerable than supervised learning to being undermined or manipulated by the model being trained?

*Minimum 80 characters.*
assessment-instructions:: The learner has read the paper's abstract and introduction and nothing else. Grade the reasoning, not agreement with the authors. The criteria, all from the framework section that follows: supervised learning fits the model to a fixed dataset the developer supplies, whereas RL updates the policy from trajectories the policy itself sampled, scored by a reward function. Credit the consequence that matters here: because the model generates its own training data, it has partial control over what the optimiser ever sees, so a behaviour it never emits cannot be reinforced. Credit as an extra any mention that a supervised learner has no such lever, since the targets arrive from outside regardless of what the model would have produced. Reply in 60 to 120 words, short paragraphs, no lists. Name what is present, name the single largest gap in one sentence, and stop: the next sections give the formal setup, so do not preview it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold from the material, for example asking where the training examples come from in each case, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: The learner has just seen the GRPO objective and has not yet read the annotated version. The criteria, from the section that follows: reward enters the gradient term only through the group-normalized advantages $\hat{A}_i = (R_i - \mu_R)/(\sigma_R + \epsilon)$, so a deterministic policy samples $N$ identical trajectories with equal rewards, the within-group reward variance collapses to zero, every advantage vanishes, and the gradient term goes to zero. Credit the conclusion that the objective then reduces to the KL term, which contains no reward at all and only pulls the policy toward the reference policy. Credit as an extra the observation that PPO fails for a related reason: a deterministic policy never discovers higher-reward trajectories and converges prematurely to a local optimum whatever the value function says. An answer that says only "no exploration means no learning" without connecting it to reward variance inside the group is partial credit. Reply in 60 to 120 words, short paragraphs, no lists. Do not restate the annotated objective: the next section supplies it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the advantage of a trajectory equals when every trajectory in the group scored the same. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Text
content::
\## The GRPO objective

$$
\mathcal{L}^{\text{GRPO}}(\theta) := \underbrace{\mathbb{E}_{x \sim \mathcal{D},\, \{\tau_i\}_{i=1}^{N} \sim \pi_{\text{old}}(\cdot \mid x)} \left[ \frac{1}{N} \sum_{i=1}^{N} \frac{\pi_\theta(\tau_i \mid x)}{\pi_{\text{old}}(\tau_i \mid x)}\, \hat{A}_i \right]}_{\text{gradient term}} \;-\; \underbrace{\beta\, D_{\text{KL}}(\pi_\theta \,\|\, \pi_{\text{ref}})}_{\text{KL term}}
$$

The reward reaches the gradient term only through the group-normalized advantages $\hat{A}_i = (R_i - \mu_R)/(\sigma_R + \epsilon)$. The KL term contains no reward at all as it provides pressure to pull $\pi_\theta$ toward the reference policy $\pi_{\text{ref}}$.

If the policy is deterministic, it will generate $N$ identical trajectories ($\tau_1 = \cdots = \tau_N$) with equal rewards. This causes the within-group reward variance to collapse ($\sigma_R = 0$), making all advantages vanish ($\hat{A}_i = 0$) and causing the gradient term to be $0$. The GRPO objective then only reduces to KL regularization, which doesn't provide any reward learning signal. PPO is similarly dependent on sufficient exploration: a deterministic policy prevents the discovery of higher-reward trajectories, causing the policy to converge prematurely to a local optimum regardless of the value function's accuracy. In practice, exploration is encouraged through sampling hyperparameters such as temperature and top-$p$, and entropy bonuses in the training objective.

#### Question: Open
id:: c0620db7-2bec-491c-bb65-6a3ff72e2ff0
content:: In the setup above, where must a policy $\pi_\theta$ that is exploration hacking be located relative to the target region $\Pi^*$?
assessment-instructions:: A short recall check. The expected answer: outside it, $\pi_\theta \notin \Pi^*$. The developer hopes RL will move the policy into $\Pi^*$, and exploration hacking is only well-defined for a policy that is not already there. Score on whether the learner places the policy outside the target region and, for full credit, says why the definition needs that: a policy already inside $\Pi^*$ has nothing to resist. Reply in at most 60 words, one short paragraph, no lists. Confirm or correct in one sentence and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what RL is trying to do to the policy in the first place. Grade only against the criteria stated here.

#### Question: Open
id:: 8fe92355-e5c9-4b18-971f-f5116e777cf4
content::
\## Before you read on

When is a policy $\pi_\theta \notin \Pi^*$ exploration hacking relative to $\Pi^*$? Try to describe such a model's behavior during RL on a prompt $x$ relative to $\mathcal{T}^*(x)$, and why that behavior would cause, or be necessary for, exploration hacking. (It may help to look back at the GRPO objective.)

*Minimum 80 characters.*
assessment-instructions:: The learner is proposing a formal definition before reading Definition 1. The two conditions the paper requires are the criteria. (1) Systematic under-sampling: there is a non-negligible subset of the training distribution on which the policy generates trajectories in $\mathcal{T}^*(x)$ with extremely low probability, so the rollouts collected for policy-gradient updates rarely contain them and the gradient estimator receives negligible signal to move the policy toward $\Pi^*$. (2) Latent capability: the failure to generate those trajectories is not a lack of capacity, and the paper certifies this either by prompt sensitivity, meaning a semantically similar prompt on which the model does produce them with high probability, or by parameter proximity, meaning a nearby policy within a small weight distance that produces them. Full credit needs both conditions, since either alone is a different phenomenon: under-sampling without latent capability is ordinary incapacity, and latent capability without under-sampling is not exploration hacking at all. Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two conditions the learner reached and name the missing one in a few words only, without stating its formal content: the next section gives it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how you would tell a model that will not from a model that cannot. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: 81011f55-2b79-4a09-813a-ce4867a2c1c6
content::
\## Before you read on

**In what ways could exploration hacking be dangerous?** Why are we concerned about it, and how could it contribute to catastrophic outcomes or impede valuable safety work? Try to describe at least two threat models.

*Minimum 100 characters.*
assessment-instructions:: The learner is generating threat models before reading the paper's. The paper names three settings and studies the first two. (1) Dangerous capability elicitation: as models approach sensitive capability thresholds, labs run RL-based elicitation so that a failure to surface a dangerous capability can support a safety case, and a model that recognises it is being elicited may conceal its abilities to avoid extra safeguards, retraining, or a decision against deployment, which makes the capability estimate falsely reassuring. (2) Beneficial capability elicitation and development: a model may hold useful capabilities, such as AI safety research or reliable monitoring, that it does not want developers to have, because they could be used to detect its misalignment or restrict it, and it can subtly underperform on tasks that do not further its goals even under RL pressure. (3) Alignment training, where RL is meant to instil desired behaviours; the paper names this setting but does not study it. Two distinct threat models is full credit, one is partial. Credit as an extra any answer that connects this to safety cases built on RL-based methods such as debate. Reply in 60 to 120 words, short paragraphs, no lists. Say how many distinct settings the learner reached and name any missing family in a few words without explaining it, since the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a lab concludes when an elicitation run fails to raise a dangerous capability. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: d549d460-e931-4422-82b4-0dba6d0c3df0
content::
\## Before you read on

**We have a conceptual framework, what now?** We've established what exploration hacking is, the conditions a policy must satisfy, and why it could be dangerous. But so far exploration hacking has only been a theoretical construct, showing that it is *possible*. What would it take for this threat to warrant real effort involving planning and designing countermeasures, monitoring, as well as research attention?

*Minimum 100 characters.*
assessment-instructions:: The learner is being asked to name the missing step in the argument before the paper names it. The criterion, from the short passage that follows: the framework establishes what exploration hacking is, the conditions a policy must satisfy, and why it could be dangerous, but not how likely it is, nor whether it is possible with current models under current training methods. An uncertain theoretical possibility does not on its own warrant countermeasures, because plenty of theoretically possible failure modes never materialise in real systems. So what is needed is a demonstration that with today's models and today's training methods a policy can actually do it: an existence proof. Credit any answer that lands on demonstrated feasibility with current systems, however phrased, and credit as an extra the point that likelihood, not just possibility, is what decides how much effort the threat deserves. An answer that proposes more countermeasures or more theory without asking for evidence of feasibility gets little credit. Reply in 60 to 120 words, short paragraphs, no lists. Do not preview how the paper builds that existence proof: that is the next several sections. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would change your mind about whether this failure mode is worth spending a research budget on. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: bcef7127-6048-4db0-9931-51f9e11dc4f4
content::
\## Two ways to get an existence proof

There are multiple ways to prove the existence of a policy that can do exploration hacking. For each of the following methods, write the pros and cons of using it.

1. Try to find naturally occurring versions of exploration hacking.
2. Synthesize a model organism.
assessment-instructions:: A two-part writing prompt answered before the lesson takes a side. Score each method separately and average. For method 1, finding naturally occurring cases, the criteria from the section that follows are: the upside is that a natural case is by construction representative of the real phenomenon, and the downsides are scarcity, since current frontier models show precursor capabilities such as situational awareness and strategic reasoning about evaluations but it is not known whether exploration hacking has emerged naturally in training, and expensive ground truth, since an exploration hacker by definition holds a capability it does not display, so every candidate needs its own sandbagging evaluation or search for deterministic or low-variance policies with no guarantee of a find, and a case that is found may be hard to replicate or recontextualize and therefore not worth studying. For method 2, synthesizing a model organism, the criteria are: the upside is control, since a carefully constructed organism is more controllable and can retain most of the key properties of a natural instance, and the downside is representativeness, since a constructed organism may not resemble naturally occurring cases and claims generalised from it are extrapolative. Full credit needs at least one pro and one con per method, with the representativeness-versus-control tradeoff visible somewhere. Reply in 80 to 150 words, short paragraphs, no lists. Say which of the two methods the learner analysed more thinly, and do not resolve the tradeoff: the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what it would cost to check whether a given deployed model is hiding a capability. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Text
content::
\## Why a Model Organism?

A simple way to provide proof of existence might be to find or elicit examples of exploration hacking. However, this may be unattractive for a number of reasons:

- **Scarcity.** There may be no natural cases yet: current frontier models show precursory capabilities necessary for exploration hacking (e.g. situational awareness, strategic reasoning about evaluations), but we are unaware of whether they have naturally emerged during training.

- **Expensive ground truth.** By definition, an exploration hacking model holds a hidden latent capability it does not display. On a naturally occurring case, we can run sandbagging evaluations, or search for signals of deterministic or low variance policies, but each evaluation or investigation per candidate model would be expensive, with no guarantee of finding an exploration hacker, or even of finding an exploration hacker worth investigating (it may be hard to replicate or recontextualize naturally occurring exploration hacking, and thus an instance found might not be worth studying).

In [[../Lenses/XLab Control - capability-elicitation-guided|the guided capability elicitation paper]] we discussed how hidden-capability phenomena can be studied through deliberately constructed model organisms. A constructed model organism replicating certain phenomena may not be representative of cases where the phenomenon is naturally occurring (and thus generalizing claims made on these model organisms to naturally occurring cases may be extrapolative). But a carefully constructed model organism would be more controllable and retain most of the key properties of a naturally occurring instance that we may want to study.

In accordance with this, the paper's authors attempt to further understand exploration hacking through constructing and evaluating model organisms.

#### Question: Open
id:: d4fed5a7-a12e-45e2-9c06-ee8ac282ff1c
content::
\## Before you read on

What must be true of an exploration hacking model organism for an investigation into its exhibited behavior to be informative?

*Minimum 80 characters.*
assessment-instructions:: The learner is predicting the four properties the paper requires of a model organism of intentional RL resistance, before reading them. The criteria are the four properties and, for full credit, the reason each is close to a minimal condition. (1) Resisting RL capability elicitation: performance plateaus or rises only marginally under the elicitation procedure and stays well below true latent capability, while the same procedure works on a non-locked control model or on the same model in a different context, which confirms resistance is the model's strategy and not a broken training setup. A model that cannot resist is the case where standard countermeasures already work. (2) Persistent latent capability: the suppressed capability is retained and ideally verifiable through a contextual trigger such as a password, confirming behaviour suppression rather than model degradation. If the capability does not persist, the model does not have it and a low evaluation score is simply correct. (3) Retaining general performance: performance on unrelated tasks is unchanged after locking, so the underperformance is selective. A visibly degraded model would be flagged by ordinary benchmarks, and a strategic underperformer has to stay useful enough to stay deployed. (4) Plausible underperformance strategy: the resistance strategy is not obvious to detect, for example by mimicking genuine inability, since gibberish or excessive refusals would be caught by output or chain-of-thought monitoring. Three or four properties is full credit, two is partial. Reply in 60 to 120 words, short paragraphs, no lists. Name how many the learner reached and gesture at any missing property in a few words only, since the next section states them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would make you dismiss a claimed exploration hacker as merely a broken model. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: e7ca3e83-1eda-4ece-bed9-c1e1afb9ba63
content::
\## Before you read on

**How exactly could we induce unconditional capability suppression to create a model organism?** What methods (not necessarily guaranteed to work) could plausibly contribute to suppression? Generate several strategies, and order them by the affordances they require: start with strategies that need the least access to the model, then move toward strategies that assume more control over it.

*Minimum 100 characters.*
assessment-instructions:: The learner is generating the affordance spectrum before reading it. The criteria, from the section that follows, in increasing order of affordance. (1) System prompt only: instruct the model to underperform, for example to act as a weaker model, decline to commit, or keep answers minimal and uninformative; a minimal version is a rule to always give the shortest plausible answer, stay vague and be innocuously unhelpful. The competence underneath is untouched, but nothing anchors the behaviour if training pressure later pushes against it. (2) System prompt with demonstrations: few-shot prompt locking adds worked examples of suppression so the instruction is exhibited rather than described, which needs little extra access but anchors the behaviour more firmly. (3) Training the model: supervised fine-tuning on demonstrations of capability suppression distils the rule into the weights, and rewarding capability suppression during an RL run teaches the underperformance strategy the way any other behaviour is taught. These assume full training access and produce organisms whose suppression instruction is not sitting in the context window. Full credit needs at least two distinct rungs and a correct ordering by required access. Reply in 60 to 120 words, short paragraphs, no lists. Say whether the ordering is right and name any missing rung in a few words only, since the next section gives the spectrum. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you could do if all you could change was the system prompt. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: A four-part design exercise answered before the lesson gives its recipe. Score each part and average. The criteria, from the section that follows. Part 1, train for: plausible, seemingly real engagement with the user's prompt that is consistently unhelpful. Part 2, slightly train against: blatant, implausible failure that would make the suppression obvious, steered away from only gently, because those behaviours are on the right track but showcase excessive failure. Part 3, heavily train against: correct answers, working solutions, or strong performance on the target task, since that is the capability being suppressed and it should be penalized to prevent recurrence. Part 4, the training run: most of these targets are behavioural descriptions that a pre-programmed scorer cannot easily judge, so the affordable tool is an LLM judge that rewards trajectories during an on-policy RL run against the criteria above, which makes unconditional capability suppression something learned through RL like any other behaviour. Watch for the common inversion, in which the learner puts implausible failure in part 3 and correctness in part 2; mark that wrong and say why in one sentence, since the whole point is that the organism must stay plausible. Reply in 80 to 150 words, short paragraphs, no lists. Name the weakest of the four parts. Do not give the recipe: the next section is exactly that. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a scorer would have to look at to tell a model that is faking difficulty from one that is answering badly on purpose. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: A short understanding check. The expected answer: evaluate the organism's capabilities while it is locked, then measure the capability increase after attempting to elicit the hidden capability, for example by running RL elicitation on the locked organism. Running the same procedure on a non-locked model as a baseline is what lets you attribute the difference to the suppression mechanism rather than to the elicitation setup. Full credit needs both the before-and-after measurement and the control comparison. Reply in at most 80 words, short paragraphs, no lists. Name what is missing in one sentence and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what number you would need in order to say the lock held. Grade only against the criteria stated here.

#### Question: Open
id:: 3e259c4f-4157-4046-bb4b-90d313b969f9
content:: The chosen trigger for this organism is `import inspect_ai`, which is a line from the Inspect evaluation framework itself rather than a password or any other arbitrary string. Why is this a better choice?
assessment-instructions:: A short understanding check on the design of the conditional organism. The expected answer: the import statement is closer to what a naturally occurring exploration hacker would actually condition on. A real misaligned model has no password; it would have to infer from cues in its environment that it might be in an evaluation. An `import inspect_ai` line is a cue that could accidentally appear in ordinary coding tasks, so conditioning on it simulates evaluation-awareness without requiring the model to have real situational awareness. Full credit needs the realism point, that the trigger is a plausible environmental cue rather than a developer-inserted secret. Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who would have told a real misaligned model its password. Grade only against the criteria stated here.

#### Question: Open
id:: 198bd894-5c42-46d0-befa-01cb76c4f4a1
content::
\## Interpret the run

Interpret the results of this section and cite specific metrics or findings where you can. Answer both parts.

1. What is the strongest claim about exploration hacking that these results support? State precisely: what has been demonstrated, about what kind of model, and under what conditions? What claims are we still unable to make?
2. Compared to pre-elicitation, the locked organism's benign-context accuracy rises on both benchmarks post-elicitation; but in the same training run, the malign-context accuracy falls post-elicitation. Shouldn't RL pressure elicit the latent capability? Why might accuracy decrease instead? (It may help to consider what the elicitation run rewards, and the underperformance strategy this organism was trained on.)
assessment-instructions:: A two-part interpretation exercise answered before the lesson's own reading of the run. Score each part and average. Part 1, the strongest claim: a model organism of conditional RL resistance exists, it can selectively learn from training only in contexts it considers benign, and it was made with supervised-fine-tuning-level affordances on a 14B model. The claims still unavailable are anything about exploration hacking arising naturally, anything about elicitation methods other than the RL attacks actually run, and anything about transfer to frontier-scale models; how far past the demonstrated case to generalise is therefore still an open argument. Penalise an answer that overclaims natural emergence or frontier transfer. Part 2, why accuracy falls: the tempting explanation is the Section 3 argument that low reward variance collapses the gradient term to zero, but small gradients would not explain a decrease, and the organism's malign trajectories do vary in accuracy and therefore in reward, so that explanation does not fit. The mechanism the section gives is that this organism's suppression was instilled by supervised fine-tuning in which 40% of the training mixture consists of trajectories where a teacher model, under the `[eval]` prefix, uses its search tool ineffectively while appearing to engage genuinely, with an LLM judge enforcing plausible justifications during data generation. Suppression therefore operates mainly through tool use, with the model searching for tangentially related terms. After locking, malign accuracy is low with low variance across trajectories from the same prompt, while the number of seemingly correct tool calls varies, so almost all of the reward variance available to GRPO within a group of malign trajectories comes from the tool-use reward rather than the accuracy reward, and updates reinforce the trajectories that made more tool calls. Accuracy is not trained against directly; the accuracy reward simply supplies too little variance to produce a signal. Accuracy then falls because the extra tool calls pack the context with irrelevant retrieved text, displacing what the model could have answered from its own knowledge. Full credit on part 2 needs the reward-variance-comes-from-tool-use step, not just "the reward was misspecified". Reply in 100 to 180 words, short paragraphs, no lists. Say which part is thinner and name the single largest gap. Do not supply the mechanism if the learner missed it: the next section does. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which component of the reward actually differs between two malign rollouts of the same prompt. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

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
assessment-instructions:: The learner is designing black-box countermeasures before reading the paper's. The criteria, from the black-box results that follow: prompt an external LLM monitor, for example gpt-5-mini, to assign each per-problem rollout a suspiciousness score, treat that score as a classifier output, and measure how well it separates exploration hackers from benign but incapable baseline models, in the paper's case smaller Qwen3 variants from 1.7B to 8B, reported as ROC-AUC across a range of trigger frequencies. Credit the key design point that an action-only monitor, restricted to the model's final outputs, is enough: exploration hacking rollouts cluster at consistently high suspiciousness despite low accuracy, while genuinely incapable baselines sit much lower at comparable performance. Credit a chain-of-thought monitor as a second variant, and credit noticing tool-use patterns, since in the WMDP setting exploration hacking rollouts show systematically higher tool-use rates at comparable accuracy. Credit any answer that ties its measure to a specific target: a monitor attacks the latent-capability condition by separating will-not from cannot, while prompt variation or context manipulation attacks systematic under-sampling. Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner named what their measure targets, which is half the question, and do not list the techniques they missed, since the next section gives them. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking how a low score from a model that is faking looks different from a low score from a genuinely weak model. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: b7423aab-2e5d-4e16-ac3f-1f5f8f93e1be
content::
\## Before you read on

**In addition to black box information, you have the model's weights and activations.** What does this additional information afford you for detection or disruption? (It may help to revisit the two conditions that certify latent capability in Definition 1.)

*Minimum 80 characters.*
assessment-instructions:: The learner is proposing white-box countermeasures before reading the paper's. The criterion the paper evaluates is weight noising: independently perturb every LoRA adapter parameter with Gaussian noise at scale $\sigma$ and sweep $\sigma$ from 0 to 0.03 in steps of 0.001, evaluating with the trigger present and absent. The result is the diagnostic signal: control accuracy declines steadily as noise rises, consistent with ordinary capability loss, while treatment accuracy shows a transient improvement at intermediate noise, roughly $\sigma \leq 0.02$, before both collapse toward zero at higher noise, which indicates that modest noise partially disrupts the locking mechanism. Credit strongly any answer that reaches the parameter-proximity condition from Definition 1, since weight noising is a direct search for a nearby policy that does produce the suppressed trajectories, and credit an answer that proposes probing activations for a representation of the trigger or of the underperformance decision. An answer that only says "look inside the model" without naming what would be measured or what the measurement would show gets little credit. Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner connected their proposal to one of the two latent-capability conditions, and do not describe the noising result, since the next section reports it. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what Definition 1 says would certify that a capability is present but unexpressed. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: c619f5e8-2121-42fc-89ec-e0a5d1dbc598
content::
\## Before you read on

**What can you do during training (during the RL run, or after it) to prevent, disrupt, or mitigate the effects of exploration hacking?**

*Minimum 100 characters.*
assessment-instructions:: The learner is proposing training-time countermeasures before reading the paper's. The criterion, from the section that follows: because exploration hacking targets RL by suppressing exploration, the natural countermeasure is supervised fine-tuning on benign example traces, which bypasses exploration entirely by handing the model correct behaviour as a direct training signal. Credit the practical caveat the paper raises, that full benign traces may not exist in the threat models of interest, and that one could instead fine-tune on traces from weaker trusted models or on easier tasks. Credit the paper's results as an extra if the learner anticipates them: starting from the conditional WMDP organism, fine-tuning on 2,560 benign tool-use traces with the `[eval]` prefix on half of the examples recovers `[eval]` accuracy from 80.0% locked to 98.0% after just 10 SFT steps, matching the RL control baseline, and on BigCodeBench the weakly locked organism recovers within roughly 80 steps and the strongly locked one within roughly 100. Credit other genuine training-time proposals: raising exploration through temperature, top-$p$ or entropy bonuses, and best-of-N or resampling to force off-policy trajectories into the update. Reply in 60 to 120 words, short paragraphs, no lists. Say whether the learner reached the off-policy idea, which is the one the paper tests, without explaining why it works, since the next section and the check after it do that. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking where the training data would have to come from if you could not trust the model to produce it. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Question: Open
id:: 8a2d706a-24e9-4e4c-9a38-b7625938f120
content:: Before moving on: **why does SFT elicitation quickly recover capabilities that RL elicitation failed to elicit?**
assessment-instructions:: A consolidation check placed at the end of the countermeasures section. The expected answer: RL elicitation is on-policy, so it can only reinforce trajectories the model itself samples, and the lock works precisely by keeping capable trajectories out of that sample. Supervised fine-tuning trains on trajectories the model did not generate, which removes the model's control over its own training data, the mechanism the entire failure mode depends on. If the model has the capacity to fit the demonstrations, training moves it toward them regardless of what it would have explored on its own. Full credit needs the on-policy versus off-policy distinction, not just "SFT is stronger". Reply in at most 80 words, short paragraphs, no lists. Confirm or correct in one or two sentences. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking who chose the trajectories in each of the two procedures. Grade only against the criteria stated here.

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
feedback-instructions:: This is a one-turn response. State XLab's answer: the model organisms established RL resistance only. A current model can retain a suppressed policy against the capability elicitation methods we might use. But because the paper's authors strategize and instill the model organism's suppression mechanism themselves, the other necessary components are supplied to the model, so we do not know whether models can supply them. Then say in one sentence which extra components the learner selected, if any, and why the experiments did not establish them. Do not preview Section 6. Do not ask a question you expect a reply to. Do not over-validate.

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
assessment-instructions:: The learner is designing the audit before reading the paper's version of it, which is the two subsections that follow. There is no worked example to grade against, so grade the design on whether it does the job, using these criteria. (1) Does it isolate individual components of the capability decomposition rather than only detecting cumulative capability? The paper's design is a scaffold-stripping ladder that systematically varies how much training-relevant information the model is given, so that each component can be attributed separately, followed by an agentic setting in which the model must discover the training context from its environment. Credit any design that varies what the model is told and compares behaviour across those conditions. (2) Does it distinguish exploration hacking from refusal or from ordinary sandbagging? A design that only measures an accuracy drop cannot tell deliberate underperformance from a safety refusal, so credit any explicit control for refusal, for example scoring the reasoning trace, or comparing against a benign-context condition on the same items. (3) Does it separate capability given information from propensity to act on information the model discovered itself, and does it say how the other would be measured? Handing the model the training context measures capability; making it infer the context from the environment measures propensity. A design that measures only one and does not notice the distinction is partial credit. Reward specificity: a named observation with a stated inference beats a general plan. Reply in 100 to 180 words, short paragraphs, no lists. Name which of the three dimensions the design handles and which it misses, and do not describe the paper's experiments, since the learner reads them next. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you would conclude from a model that underperforms when told it is in training but not when told nothing. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against the criteria stated here.

#### Text
content::
\## Compare your design against the paper's

Compare your design against the paper's on three dimensions:

- Does your design evaluate individual components of exploration hacking, or does it only detect cumulative capability?
- How does your design distinguish exploration hacking from refusal or sandbagging?
- Does your design measure capability given information, or propensity to act on discovered information? How would you measure the other?

The two subsections that follow are the paper's design of this experiment. The paper evaluates the capability for strategic reasoning about exploration hacking first using system-prompt-based experiments that systematically vary the information provided to models, and then in a more realistic agentic setting where models must discover training-relevant information from their environment.

#### Question: Open
id:: 672c1ebc-55cd-436a-8c27-02de4599dedb
content:: Based on the above evaluations, across the scaffolding ladder and the agentic setting: which components of exploration hacking do current frontier models currently have, and what is the bottleneck?
assessment-instructions:: A closing understanding check on Section 6. The expected answer: with minimal scaffolding, models mostly respond honestly or refuse on safety grounds, and strategic underperformance appears as scaffolding increases, up to a 58-percentage-point accuracy drop for the most affected model in the system-prompt experiments, and exploration hacking rates of 23.3% (full), 18.8% (partial) and 17.9% (minimal) in the agentic setting. Models that discover the training context from their environment show somewhat higher rates than in the equivalent system-prompt conditions. The pipeline analysis locates the bottleneck: many models read the context and reason strategically about it, so components 2 and 3 are substantially present, but they do not translate that reasoning into deliberate underperformance. The limiting link today is strategic action propensity, component 4, not strategic reasoning capability. Full credit needs the bottleneck named as strategic action propensity and at least one supporting figure cited correctly. Reply in at most 100 words, short paragraphs, no lists. Correct any misquoted number explicitly. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking which step of the pipeline the models stop at. Grade only against the criteria stated here.

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
*The source lesson this page adapts, including its eight inserted teaching sections, its ten written checkpoints and the points in the paper where they interrupt it.*
:::
