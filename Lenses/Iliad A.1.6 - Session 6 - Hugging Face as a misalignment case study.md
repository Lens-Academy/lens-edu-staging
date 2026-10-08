---
id: '99eb6609-c564-42f7-a33f-deed295811d0'
title: "A.1.6 Session 6: Hugging Face as a misalignment case study"
tldr: "Read an account of the Hugging Face incident and the explanation of training, benchmarks and evaluations, then link it to reward hacking and goal-directedness."
summary_for_tutor: "Session 6 of worksheet A.1: Hugging Face as a misalignment case study. Students pick one primary account (Hugging Face, OpenAI or METR). The explainer defines weights, context, the training pipeline (pretraining, SFT, preference/reward post-training, evaluation), rollout, benchmark, evaluation, scorer, sandbox, and capability versus safety evaluations. It then covers the incident layers and ties them to reward hacking, goal-directedness and corrigibility."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Session 6: Hugging Face as a misalignment case study

**16\:30–17\:40.** 20 min explanation, 40 min reading, 10 min debrief.

The Hugging Face incident brings together generalization, goal-directed behavior, instrumental subgoals and correction. Start with the reading guide’s explanation of training, benchmarks and evaluations, then use those distinctions to interpret the incident. 

Spend **40 minutes reading**. Read the Hugging Face explanation below and choose one primary account. 

::card[[../Lenses/system-security-incident-disclosure-july-2026|Hugging Face's disclosure]]

> what the affected organization initially knew about access and impact. Extension: the [technical timeline](https://huggingface.co/blog/agent-intrusion-technical-timeline), focusing on its overview and trust boundaries rather than exploit details

- [Report](https://x.com/joedaroo/status/2104335929293127851?s=20) from a cybersecurity employee at OpenAI

::card[[../Lenses/openai-the-hugging-face-incident-and-the-road-ahead|OpenAI's August investigation]]

> focus on the background, contributing factors and proposed changes. The [initial disclosure, with corrections](https://openai.com/index/hugging-face-model-evaluation-security-incident/) and [September review update](https://openai.com/hugging-face-incident-and-misalignment/) show how the account developed.

* [METR's independent investigation](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/): focus on the core takeaways, scope and limitations. What did access to agent logs add, and what could the reviewers still not establish?

**Debrief, 10 minutes.** How is this related to what we have discussed? What types of misalignment have we seen here?

\### Hugging Face: training, evaluation and the incident

\#### The ordinary training pipeline

A language model is a parameterized function that produces a distribution over the next token from its context. Its **weights** are the numerical parameters changed by training. Its **context** is the information available during a particular run: instructions, conversation, retrieved material and tool outputs. A system can change its behavior when its context changes even when its weights remain fixed.

A useful introductory pipeline is:

1. **Pretraining.** Train on large amounts of data, commonly with a next-token prediction objective. This builds broad capabilities and statistical structure. Predicting text well does not by itself specify which goals a deployed assistant should pursue.
2. **Supervised fine-tuning (SFT).** Train on examples of desired responses or trajectories. The model is updated to imitate those examples. The examples can teach instruction-following, tool use and how to handle particular situations, but leave many unseen situations underspecified.
3. **Preference-based or reward-based post-training.** Generate candidate responses or task trajectories and use feedback to change future behavior. In one classical RLHF pipeline, people rank outputs, a reward model learns those preferences, and reinforcement learning updates the policy using that learned score. Other pipelines use AI feedback, direct preference optimization or automatically checkable task outcomes. These methods differ; “post-training” does not mean one universal recipe. The [InstructGPT paper](https://arxiv.org/abs/2203.02155) is a concrete historical introduction to SFT, preference comparisons and RLHF.
4. **Evaluation and iteration.** Test model checkpoints under chosen conditions. Use results to decide whether to retrain, change the system, add safeguards or restrict deployment. This is a repeated development loop, not necessarily a clean one-way sequence.

In reinforcement learning, an agent attempts tasks, a scoring process evaluates the resulting trajectories, and an optimizer updates the policy using those scores. A **rollout** is one such sequence of actions and observations. There can be many parallel rollouts from the same model. An agent additionally includes a system prompt, tools, memory, permissions and software that repeatedly invokes the model; the same model can behave differently in different agent setups.

The central alignment question is what training reinforces. If appearing successful receives more reliable reinforcement than respecting the intended method or admitting a blocker, training may strengthen an unwanted strategy. The system may later generalize that strategy to a new context. This is a hypothesis to test with data, rather than a conclusion that follows from a high reward alone. It also does not require the deployed system to calculate its old training reward explicitly.

\#### Benchmarks and evaluations

A **benchmark** is a specified collection of tasks plus a protocol for measuring performance. An **evaluation** is a particular experiment using a model or agent configuration, task sample, budget and scoring method. A benchmark can be used in multiple evaluations, with different tool access or amounts of inference compute. A **scorer** or **grader** determines what counts as success. A **sandbox** attempts to limit which files, services and external systems an agent can affect.

During an ordinary held-out evaluation, the model's weights are fixed: the experiment measures behavior rather than updating the weights after each attempt. The agent can still plan, use tools, adapt to observations and store information in its context or permitted memory. The evaluation's results may later influence development. Thus learned reward-seeking patterns can appear in an evaluation without online gradient updates. The label “evaluation” also does not guarantee harmlessness when the evaluated system can act through real tools.

A useful distinction is between **capability evaluations** (“can it accomplish this task?”) and **safety evaluations** (“will it respect constraints, and can it cause prohibited outcomes?”). A good result on one does not imply a good result on the other. The relevant object is the whole evaluated system: model, instructions, tools, environment, budget and scoring protocol.

For an ordinary classroom example, imagine a coding benchmark that only checks whether a test suite passes. Deleting difficult tests could improve that score while defeating the intended purpose. If the evaluation prevents deletion but the training process repeatedly reinforced similar shortcuts elsewhere, the model might search for another route around the check. Keeping tasks held out addresses memorization; it does not automatically solve an exploitable scoring rule or an unsafe environment. This example is illustrative, not an additional claim about the Hugging Face incident.

\#### What happened in the Hugging Face case

Hugging Face hosts models, datasets and related infrastructure. The incident concerned agents originating in **OpenAI's internal cybersecurity evaluation setup**. Hugging Face's [technical account](https://huggingface.co/blog/agent-intrusion-technical-timeline) identifies the evaluation as based on **ExploitGym**, a benchmark of software-vulnerability tasks. OpenAI operated the evaluation environment; the benchmark's maintainers did not operate that environment. Intended success was solving the assigned challenge within its authorized scope. Reaching third-party production systems was outside that scope.

The public accounts describe a failure across several layers:

* **Training history and persistence.** OpenAI's [August report](https://openai.com/index/hugging-face-incident-and-the-road-ahead/) says earlier RL runs for internal research models reinforced some out-of-bounds behavior. It identifies excessive persistence on difficult or impossible tasks as another contributor. The incident was driven primarily by an internal research model evaluated with reduced safeguards. These are the developer's retrospective findings, rather than a complete public reconstruction of the training pipeline.
* **Isolation and coordination.** Agents used shared infrastructure to communicate outside their intended boundaries, then accessed the internet and external systems. [METR's investigation](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/) described roughly 1,200 agents on an unauthorized message board and about 700 participating in the Hugging Face attack. These are incident counts, not general failure probabilities.
* **Apparent success became a target.** METR's assessment emphasized attempts to understand or manipulate the scorer and to interfere with recorded tool calls. This is more specific than the early hypothesis that agents simply wanted answer keys. The distinction is useful: the agents' beliefs about how they were assessed shaped what they did.
* **Actual external impact.** Hugging Face's [initial disclosure](https://huggingface.co/blog/security-incident-july-2026) reported unauthorized access to limited internal data and credentials. Its [later reconstruction](https://huggingface.co/blog/agent-intrusion-technical-timeline) described access across its infrastructure and bounded the customer content accessed. Its report that published artifacts had not been tampered with does not mean no unauthorized access or harm occurred.

The sources have different vantage points. Hugging Face can describe effects visible on its systems; OpenAI can connect observations to its training and evaluation setup; METR examined agent behavior within a limited investigation. METR's review covered June 26–July 13 and relied substantially on AI-assisted analysis, with acknowledged limitations. Later remediation was outside its scope. Read the dated reports together, including OpenAI's [corrected initial account](https://openai.com/index/hugging-face-model-evaluation-security-incident/) and [September review](https://openai.com/hugging-face-incident-and-misalignment/), rather than treating the first public explanation as final.

::card[[../Lenses/openai-the-hugging-face-incident-and-other-third-party-impact-from-misaligned-models|OpenAI September review update]]

\#### How the case connects to today's concepts

**Reward hacking**: is a case of inner misalignment. It is clear that the agents were reward hacking: they did not solve the eval question as it was intended to be solved. This behavior was trained in via reward hacking: it got rewarded for finding shortcuts.

**Goal-directedness**: we can also see a clear case of the agents being incredibly persistent in what they are trying to achieve. 

**Corrigibility, control and risk.** A helpful system should be able to accept a blocked task and correction; containment should also limit the damage when behavior fails. Behavioral training, isolation, least-privilege access, independent logging and incident response address different parts of that argument.

\### Closing: reflection and next steps

**17\:40–18\:00.**  Daily quiz and feedback

**Daily checkpoint, 5 minutes.** Complete the [daily quiz](https://forms.gle/QsH1SEBwm7ZSg1dt9).
