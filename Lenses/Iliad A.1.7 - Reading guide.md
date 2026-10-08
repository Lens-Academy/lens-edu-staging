---
id: '97271560-2052-47fb-9f22-7a824116d374'
title: "A.1.7 Reading guide"
tldr: "A reading guide that connects the day's topics: AI risks, alignment targets, decompositions, goal-directedness, forecasting and solution approaches."
summary_for_tutor: "Reading guide of worksheet A.1. It summarizes risk types, alignment targets (CEV, intent alignment, constitution, corrigibility), training stories, outer versus inner alignment and goal misgeneralization, inductive biases and emergent misalignment, 'Reward is not the optimization target', goal-directedness and instrumental convergence, optimistic/intermediate/pessimistic views, AI 2027, and solution approaches (empirical, mathematical, philosophical, prosaic)."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
%% Facilitator logistics (hidden from learners):
\### Closing: reflection and next steps

**17:40–18:00.**  Daily quiz and feedback

**Daily checkpoint, 5 minutes.** Complete the [daily quiz](https://forms.gle/QsH1SEBwm7ZSg1dt9).
%%

\## Reading guide

\### Different AI risks

There are many AI safety problems. [The adolescence of technology](https://www.darioamodei.com/essay/the-adolescence-of-technology) is an opinionated introduction to these risks, including the risk of autonomous misaligned AI, AI misuse for destruction, AI misuse for seizing power, and others. 

\### Alignment targets

In this course, we are mainly focused on AI alignment, which is broadly the problem of making sure AI acts in line with "human" wishes. There are different conceptualizations for what this means, i.e. what the "alignment target" is, which are partially overlapping: Some may wish AI to be aligned with our [coherent extrapolated volition](https://intelligence.org/files/CEV.pdf), which is "our wish if we knew more, thought faster, were more the people we wished we were, had grown up farther together \[...\]". A different conceptualization is that of [intent alignment with a human](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6), which means "trying to do what the human wants \[the AI\] to do". As contemporary AI becomes more powerful and widespread, more sophisticated notions of alignment targets have emerged. Most prominently, one may align an AI with the prescriptions in a [constitution as in the case of Anthropic’s Claude](https://www.anthropic.com/news/claude-new-constitution), which may balance the wishes of users, the developer’s guidelines, general ethics, and efforts to oversee the AI. Another often-discussed target is [corrigibility](https://www.lesswrong.com/w/corrigibility-1). An AI is corrigible if it will let us modify its functions or goals and even let us shut it down. If corrigibility is achieved, then we can correct mistakes in building an AI, which makes it easier to iterate to achieve lower risk.

::card[[../Lenses/yudkowsky-coherent-extrapolated-volition|Coherent extrapolated volition]]

::card[[../Lenses/christiano-clarifying-ai-alignment|Intent alignment]]

::card[[../Lenses/anthropic-claudes-new-constitution|Claude's constitution overview]]

::card[[../Lenses/lesswrong-corrigibility|Corrigibility]]

\### Alignment problem decompositions

Assume we have chosen our alignment target. How do we ensure an AI system actually *obeys* that target? This is the *technical* problem of AI alignment. In this introduction, we are mostly presupposing that AI systems are *trained via deep learning*, although later modules in this course on agent foundations go beyond that assumption. In the deep learning paradigm, [training stories](https://www.alignmentforum.org/posts/FDJnZt8Ks2djouQTZ/how-do-we-become-confident-in-the-safety-of-a-machine) are a useful framework to think about how to align AI systems: You need to choose a *training target* (e.g. "My model is corrigible") and then have a *training rationale* for why your *training setup* will create a model obeying the target. And of course, your training rationale needs to actually be correct, which requires technical research to back up any such claim! 

::card[[../Lenses/evhub-how-do-we-become-confident-in-the-safety-of-a-machine-learning-system|Training stories]]

With approaches that are based on reinforcement learning, another popular problem decomposition is into *outer* and *inner* alignment. Outer alignment is the problem of [specifying a reward function](https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/) that rewards an AI’s behavior according to how well it obeys the chosen alignment target. Inner alignment is the problem of ensuring that the trained policy will, even in new out-of-distribution situations after training, [continue to generalize correctly](https://deepmind.google/blog/how-undesired-goals-can-arise-with-correct-rewards/) and obey the reward function. In cases where the policy has inner processes that actively optimize for a goal, this means ensuring that this goal agrees with the goal encoded in the reward function, a problem that was discussed at length in [risks from learned optimization](https://arxiv.org/abs/1906.01820). 

::card[[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Reward misspecification]]

::card[[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|Goal misgeneralization]]

**Terminology.** Goal misgeneralization is broader than inner misalignment in the learned-optimizer framing. Observing incorrect generalization does not by itself show that a system contains a distinct internal optimizer. The inner-alignment question is specifically whether a learned internal objective agrees with the intended training objective.

In general, the out-of-distribution (also called "generalization") behavior of AI systems depends crucially on their [inductive biases](https://www.cs.cmu.edu/~tom/pubs/NeedForBias_1980.pdf), which are the implicit or explicit constraints on what functions are more likely to emerge from the training process. As it turns out, deep learning has strong implicit inductive biases, as exemplified by [emergent misalignment](https://arxiv.org/abs/2502.17424), a phenomenon whereby narrow fine-tuning can produce broadly misaligned LLMs. Read [this article](https://arxiv.org/abs/2503.02113) on how deep learning’s inductive biases may be related to the compressibility of the solutions the training process finds. 

::card[[../Lenses/betley-emergent-misalignment-narrow-finetuning-can-produce-broadly-misaligned-llms-1-this-paper-contains-model-generated-content-that-might-be-offensive-1|Emergent misalignment]]

::card[[../Lenses/wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

The decomposition of the alignment problem into inner and outer alignment is controversial, which is why above we started with the more general framing of training stories. In particular, in "[Reward is not the optimization target](https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4)", Alex Turner argues that the reward function is *not* what a reinforcement learning policy is optimized to maximize. Instead, a policy performs the contextual computations that were previously reinforced before a reward event. This is similar to Eliezer Yudkowsky’s proposal to view biological organisms as [adaptation-executers instead of fitness-maximizers](https://www.lesswrong.com/posts/XPErvb8m9FapXCjhA/adaptation-executers-not-fitness-maximizers). 

\### Goal-directedness

We already briefly discussed the idea of a policy that "internally" steers toward some goal. If an AI is goal-directed in that way, then any misalignment on top is intuitively more dangerous. In "[Why tool AIs want to be agent AIs](https://gwern.net/tool-ai)", Gwern argues that, among others, economic reasons will push AI systems to become more and more goal-directed. A similar argument is made in [Will humans build goal-directed agents?](https://www.alignmentforum.org/posts/9zpT9dikrrebdq3Jf/will-humans-build-goal-directed-agents) by Rohin Shah. 

::card[[../Lenses/shah-will-humans-build-goal-directed-agents|Will humans build goal-directed agents?]]

Such an AI system, if successful, would also be able to create its own subgoals on the pathway to achieve its goals. "Instrumental convergence" is the claim that there are some goals that are instrumentally useful in reaching a very wide variety of final goals. This would imply that goal-directed AI systems develop [basic AI drives](https://selfawaresystems.com/wp-content/uploads/2008/01/ai_drives_final.pdf) like self-improvement, preservation of their goal, or self-protection. This is counter to the alignment target of corrigibility we discussed earlier, and is therefore a dangerous outcome of training powerful AI. Understanding the relationship between inductive biases and the goal formation of AI systems is therefore very important.

::card[[../Lenses/omohundro-the-basic-ai-drives|Basic AI drives]]

Instrumental-convergence arguments depend on assumptions about the objective, environment and available actions. They do not establish that every language-model agent will develop the same drives.

\### Forecasting risks, timelines and takeoff

Where does this leave us, in terms of our general level of risks? In general, there is a broad spectrum of views on the difficulty of the alignment problem. In Anthropic’s "[core views on AI safety](https://www.anthropic.com/news/core-views-on-ai-safety)", the authors discuss three very different possibilities: an optimistic scenario, in which current methods are essentially sufficient; an intermediate scenario, in which preventing catastrophic risks requires substantial scientific and engineering effort; and a pessimistic view, in which AI safety is essentially unsolvable. Among [authors at top machine learning venues](https://arxiv.org/abs/2401.02843), "\[b\]etween 38% and 51% of respondents gave at least a 10% chance to advanced AI leading to outcomes as bad as human extinction". While those who are concerned often create failure stories of how AI can lead to catastrophes, like Paul Christiano’s "[What failure looks like](https://www.lesswrong.com/posts/HBxe6wdjxK239zajf/what-failure-looks-like)", others are more optimistic and explain why they think "[AI is easy to control](https://optimists.ai/2023/11/28/ai-is-easy-to-control/)". In this epistemic state of uncertainty, it is useful to do research on the level and nature of AI risks themselves. One approach is [model organisms of misalignment](https://www.lesswrong.com/posts/ChDH335ckdvpxXaXX/model-organisms-of-misalignment-the-case-for-a-new-pillar-of-1), which are "in vitro demonstrations of the kinds of failures that might pose existential threats".

::card[[../Lenses/anthropic-core-views-on-ai-safety-when-why-what-and-how|Core views on AI safety]]

::card[[../Lenses/evhub-model-organisms-of-misalignment-the-case-for-a-new-pillar-of-alignment-research|Model organisms of misalignment]]

For a specific forecast, we have looked at **AI 2027.** The [April 2025 scenario](https://ai-2027.com/) makes a particular story about research automation and rapid capability growth concrete, with alternative branches and [research supplements](https://ai-2027.com/research/takeoff-forecast). It is informative to check to what extent these forecasts have turned out to be true. The authors report regular updates to the scenario, see the latest (August) [here](https://blog.aifutures.org/p/q25-2026-timelines-update-uplift).

::card[[../Lenses/ai-2027 article lens|AI 2027]]

::card[[../Lenses/lifland-q2-5-2026-timelines-update-uplift-and-revenue|AI Futures timelines update]]

\### Solution approaches

Assume we are sufficiently concerned about AI alignment that we want to solve the problem. What high-level approach should we choose? Some people, like Jan Leike, argue for [very empirical iterative approaches](https://aligned.substack.com/p/alignment-optimism) to AI alignment, sometimes with the goal to use more advanced AI systems to help solve remaining alignment research questions. Eliezer Yudkowsky argues for deep mathematical progress in [his analogy to the rocket alignment problem](https://www.alignmentforum.org/posts/Gg9a4y8reWKtLe3Tn/the-rocket-alignment-problem). Yet others take a further step back and argue we need to solve [deep philosophical problems](https://www.lesswrong.com/posts/rASeoR7iZ9Fokzh7L/problems-in-ai-alignment-that-philosophers-could-potentially) on our way to aligned AI. Somewhat orthogonal to all those views, Paul Christiano’s post on [prosaic AI alignment](https://ai-alignment.com/prosaic-ai-control-b959644d79c2) argues that we should attempt to align the AI systems we have in front of us instead of waiting for breakthroughs in our understanding of intelligence or entirely new paradigms to create intelligent machines — which is a view that is compatible with both empirical and theoretical research on how to make those systems safe. 

::card[[../Lenses/yudkowsky-the-rocket-alignment-problem-gg9a4y8rewktle3tn|The rocket alignment problem]]

Our course tries to a large extent to be a synthesis between different views: We assume for much of the course the "prosaic" picture that powerful AI systems will be based on deep learning systems much like today’s. We are interested in deep, empirically grounded *mathematical* progress on understanding these systems. Additionally, we include sections on agent foundations that complement this work and do not assume a deep learning frame.
