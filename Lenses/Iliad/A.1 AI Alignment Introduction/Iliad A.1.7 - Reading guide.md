---
id: '97271560-2052-47fb-9f22-7a824116d374'
title: "A.1.7 Reading guide"
tldr: "A reading guide that connects the day's topics: AI risks, alignment targets, decompositions, goal-directedness, forecasting and solution approaches."
summary_for_tutor: "Reading guide of worksheet A.1. It summarizes risk types, alignment targets (CEV, intent alignment, constitution, corrigibility), training stories, outer versus inner alignment and goal misgeneralization, inductive biases and emergent misalignment, 'Reward is not the optimization target', goal-directedness and instrumental convergence, optimistic/intermediate/pessimistic views, AI 2027, and solution approaches (empirical, mathematical, philosophical, prosaic)."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
upstream_key: "ai-alignment-intro#reading-guide"
upstream_fingerprint: "7knV8XnQbCKItGcwzVXfGTl6tUnwU8bwmrHq/2590/1/01r002fr06Ri08pH0A1v0CG80FGm0OMq0Oqv0R0Q0RKd0UGk0fDJ0kW40prO0qPC0qbr0sUy0yGQ105b107f13D314vP165N16UU18nm19Fv1AJg1AVg1BDJ1BdG1DpL"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/alignment/ai-alignment-intro/#reading-guide"
---

#### Text
content::
\## Reading guide

\### Different AI risks

There are many AI safety problems. [The adolescence of technology](https://www.darioamodei.com/essay/the-adolescence-of-technology) is an opinionated introduction to these risks, including the risk of autonomous misaligned AI, AI misuse for destruction, AI misuse for seizing power, and others.

\### Alignment targets

In this course, we are mainly focused on AI alignment, which is broadly the problem of making sure AI acts in line with "human" wishes. There are different conceptualizations for what this means, i.e. what the "alignment target" is, which are partially overlapping: Some may wish AI to be aligned with our [coherent extrapolated volition](https://intelligence.org/files/CEV.pdf), which is "our wish if we knew more, thought faster, were more the people we wished we were, had grown up farther together \[...\]". A different conceptualization is that of [intent alignment with a human](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6), which means "trying to do what the human wants \[the AI\] to do". As contemporary AI becomes more powerful and widespread, more sophisticated notions of alignment targets have emerged. Most prominently, one may align an AI with the prescriptions in a [constitution as in the case of Anthropic’s Claude](https://www.anthropic.com/news/claude-new-constitution), which may balance the wishes of users, the developer’s guidelines, general ethics, and efforts to oversee the AI. Another often-discussed target is [corrigibility](https://www.lesswrong.com/w/corrigibility-1). An AI is corrigible if it will let us modify its functions or goals and even let us shut it down. If corrigibility is achieved, then we can correct mistakes in building an AI, which makes it easier to iterate to achieve lower risk.

\### Alignment problem decompositions

Assume we have chosen our alignment target. How do we ensure an AI system actually *obeys* that target? This is the *technical* problem of AI alignment. In this introduction, we are mostly presupposing that AI systems are *trained via deep learning*, although later modules in this course on agent foundations go beyond that assumption. In the deep learning paradigm, [training stories](https://www.alignmentforum.org/posts/FDJnZt8Ks2djouQTZ/how-do-we-become-confident-in-the-safety-of-a-machine) are a useful framework to think about how to align AI systems: You need to choose a *training target* (e.g. "My model is corrigible") and then have a *training rationale* for why your *training setup* will create a model obeying the target. And of course, your training rationale needs to actually be correct, which requires technical research to back up any such claim! 

With approaches that are based on reinforcement learning, another popular problem decomposition is into *outer* and *inner* alignment. Outer alignment is the problem of [specifying a reward function](https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/) that rewards an AI’s behavior according to how well it obeys the chosen alignment target. Inner alignment is the problem of ensuring that the trained policy will, even in new out-of-distribution situations after training, [continue to generalize correctly](https://deepmind.google/blog/how-undesired-goals-can-arise-with-correct-rewards/) and obey the reward function. In cases where the policy has inner processes that actively optimize for a goal, this means ensuring that this goal agrees with the goal encoded in the reward function, a problem that was discussed at length in [risks from learned optimization](https://arxiv.org/abs/1906.01820). 

**Terminology.** Goal misgeneralization is broader than inner misalignment in the learned-optimizer framing. Observing incorrect generalization does not by itself show that a system contains a distinct internal optimizer. The inner-alignment question is specifically whether a learned internal objective agrees with the intended training objective.

In general, the out-of-distribution (also called "generalization") behavior of AI systems depends crucially on their [inductive biases](https://www.cs.cmu.edu/~tom/pubs/NeedForBias_1980.pdf), which are the implicit or explicit constraints on what functions are more likely to emerge from the training process. As it turns out, deep learning has strong implicit inductive biases, as exemplified by [emergent misalignment](https://arxiv.org/abs/2502.17424), a phenomenon whereby narrow fine-tuning can produce broadly misaligned LLMs. Read [this article](https://arxiv.org/abs/2503.02113) on how deep learning’s inductive biases may be related to the compressibility of the solutions the training process finds. 

The decomposition of the alignment problem into inner and outer alignment is controversial, which is why above we started with the more general framing of training stories. In particular, in "[Reward is not the optimization target](https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4)", Alex Turner argues that the reward function is *not* what a reinforcement learning policy is optimized to maximize. Instead, a policy performs the contextual computations that were previously reinforced before a reward event. This is similar to Eliezer Yudkowsky’s proposal to view biological organisms as [adaptation-executers instead of fitness-maximizers](https://www.lesswrong.com/posts/XPErvb8m9FapXCjhA/adaptation-executers-not-fitness-maximizers).

\### Goal-directedness

We already briefly discussed the idea of a policy that "internally" steers toward some goal. If an AI is goal-directed in that way, then any misalignment on top is intuitively more dangerous. In "[Why tool AIs want to be agent AIs](https://gwern.net/tool-ai)", Gwern argues that, among others, economic reasons will push AI systems to become more and more goal-directed. A similar argument is made in [Will humans build goal-directed agents?](https://www.alignmentforum.org/posts/9zpT9dikrrebdq3Jf/will-humans-build-goal-directed-agents) by Rohin Shah. 

Such an AI system, if successful, would also be able to create its own subgoals on the pathway to achieve its goals. "Instrumental convergence" is the claim that there are some goals that are instrumentally useful in reaching a very wide variety of final goals. This would imply that goal-directed AI systems develop [basic AI drives](https://selfawaresystems.com/wp-content/uploads/2008/01/ai_drives_final.pdf) like self-improvement, preservation of their goal, or self-protection. This is counter to the alignment target of corrigibility we discussed earlier, and is therefore a dangerous outcome of training powerful AI. Understanding the relationship between inductive biases and the goal formation of AI systems is therefore very important.

Instrumental-convergence arguments depend on assumptions about the objective, environment and available actions. They do not establish that every language-model agent will develop the same drives.

\### Forecasting risks, timelines and takeoff

Where does this leave us, in terms of our general level of risks? In general, there is a broad spectrum of views on the difficulty of the alignment problem. In Anthropic’s "[core views on AI safety](https://www.anthropic.com/news/core-views-on-ai-safety)", the authors discuss three very different possibilities: an optimistic scenario, in which current methods are essentially sufficient; an intermediate scenario, in which preventing catastrophic risks requires substantial scientific and engineering effort; and a pessimistic view, in which AI safety is essentially unsolvable. Among [authors at top machine learning venues](https://arxiv.org/abs/2401.02843), "\[b\]etween 38% and 51% of respondents gave at least a 10% chance to advanced AI leading to outcomes as bad as human extinction". While those who are concerned often create failure stories of how AI can lead to catastrophes, like Paul Christiano’s "[What failure looks like](https://www.lesswrong.com/posts/HBxe6wdjxK239zajf/what-failure-looks-like)", others are more optimistic and explain why they think "[AI is easy to control](https://optimists.ai/2023/11/28/ai-is-easy-to-control/)". In this epistemic state of uncertainty, it is useful to do research on the level and nature of AI risks themselves. One approach is [model organisms of misalignment](https://www.lesswrong.com/posts/ChDH335ckdvpxXaXX/model-organisms-of-misalignment-the-case-for-a-new-pillar-of-1), which are "in vitro demonstrations of the kinds of failures that might pose existential threats".

For a specific forecast, we have looked at **AI 2027.** The [April 2025 scenario](https://ai-2027.com/) makes a particular story about research automation and rapid capability growth concrete, with alternative branches and [research supplements](https://ai-2027.com/research/takeoff-forecast). It is informative to check to what extent these forecasts have turned out to be true. The authors report regular updates to the scenario, see the latest (August) [here](https://blog.aifutures.org/p/q25-2026-timelines-update-uplift).

\### Solution approaches

Assume we are sufficiently concerned about AI alignment that we want to solve the problem. What high-level approach should we choose? Some people, like Jan Leike, argue for [very empirical iterative approaches](https://aligned.substack.com/p/alignment-optimism) to AI alignment, sometimes with the goal to use more advanced AI systems to help solve remaining alignment research questions. Eliezer Yudkowsky argues for deep mathematical progress in [his analogy to the rocket alignment problem](https://www.alignmentforum.org/posts/Gg9a4y8reWKtLe3Tn/the-rocket-alignment-problem). Yet others take a further step back and argue we need to solve [deep philosophical problems](https://www.lesswrong.com/posts/rASeoR7iZ9Fokzh7L/problems-in-ai-alignment-that-philosophers-could-potentially) on our way to aligned AI. Somewhat orthogonal to all those views, Paul Christiano’s post on [prosaic AI alignment](https://ai-alignment.com/prosaic-ai-control-b959644d79c2) argues that we should attempt to align the AI systems we have in front of us instead of waiting for breakthroughs in our understanding of intelligence or entirely new paradigms to create intelligent machines — which is a view that is compatible with both empirical and theoretical research on how to make those systems safe. 

Our course tries to a large extent to be a synthesis between different views: We assume for much of the course the "prosaic" picture that powerful AI systems will be based on deep learning systems much like today’s. We are interested in deep, empirically grounded *mathematical* progress on understanding these systems. Additionally, we include sections on agent foundations that complement this work and do not assume a deep learning frame.

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

::card[[../../openai-the-hugging-face-incident-and-other-third-party-impact-from-misaligned-models|OpenAI September review update]]

\#### How the case connects to today's concepts

**Reward hacking**: is a case of inner misalignment. It is clear that the agents were reward hacking: they did not solve the eval question as it was intended to be solved. This behavior was trained in via reward hacking: it got rewarded for finding shortcuts.

**Goal-directedness**: we can also see a clear case of the agents being incredibly persistent in what they are trying to achieve. 

**Corrigibility, control and risk.** A helpful system should be able to accept a blocked task and correction; containment should also limit the damage when behavior fails. Behavioral training, isolation, least-privilege access, independent logging and incident response address different parts of that argument.
