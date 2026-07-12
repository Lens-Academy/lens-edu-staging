---
id: 42d2d526-c5f2-4d6d-8e70-758cd27f38a9
{++{"author":"Elias's AI","timestamp":1783848782530}@@tldr: "Once you have picked what to align an AI toward, how do you make it actually obey? This lens breaks the technical problem into working parts — training stories, the contested split between outer and inner alignment, and the inductive biases that decide how models generalize — then ends with a twist: the tidy decomposition may not hold up."
summary_for_tutor: "Covers the technical AI alignment problem under a deep-learning assumption. Introduces training stories (choosing a training target, then a training rationale for why the training setup will produce a model that obeys it), then the outer/inner alignment decomposition: outer alignment is specifying a reward function that captures the target, inner alignment is ensuring the trained policy generalizes correctly out-of-distribution and that any internal goal matches the reward's goal. Explains that out-of-distribution behavior depends on inductive biases (illustrated by emergent misalignment) and that the inner/outer split is controversial, citing Turner's \"reward is not the optimization target.\" Includes an optional chat that helps the learner hold this structure and correct common confusions."
++}title: Decomposing the alignment problem
---
#### Text
content:: Assume we have chosen our alignment target. How do we ensure an AI system actually *obeys* that target? This is the **technical** problem of AI alignment. In this introduction we mostly presuppose that AI systems are *trained via deep learning* (later modules on agent foundations go beyond that assumption).

**Training stories**

In the deep-learning paradigm, [training stories](https://www.alignmentforum.org/posts/FDJnZt8Ks2djouQTZ/how-do-we-become-confident-in-the-safety-of-a-machine) are a useful framework for thinking about how to align AI systems. You choose a *training target* (e.g. "my model is corrigible") and then have a *training rationale* for why your *training setup* will create a model obeying the target. Your training rationale needs to actually be correct — which requires technical research to back up any such claim.

**Outer and inner alignment**

With approaches based on reinforcement learning, another popular decomposition is into **outer** and **inner** alignment:

- **Outer alignment** is the problem of [[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|specifying a reward function]] that rewards an AI's behavior according to how well it obeys the chosen alignment target.
- **Inner alignment** is the problem of ensuring that the trained policy will, even in new out-of-distribution situations after training, [[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|continue to generalize correctly]] and obey the reward function. Where the policy has inner processes that actively optimize for a goal, this means ensuring that internal goal agrees with the goal encoded in the reward function — discussed at length in [[../Lenses/hubinger-risks-from-learned-optimization-in-advanced-machine-learning-systems|Risks from Learned Optimization]].

**Inductive biases**

In general, the out-of-distribution (or "generalization") behavior of AI systems depends crucially on its [[../Lenses/mitchell-the-need-for-biases-in-learning-generalizations|inductive biases]] — the implicit or explicit constraints on which functions are more likely to emerge from training. Deep learning turns out to have strong *implicit* inductive biases, as exemplified by [[../Lenses/betley-emergent-misalignment-narrow-finetuning-can-produce-broadly-misaligned-llms-1-this-paper-contains-model-generated-content-that-might-be-offensive-1|emergent misalignment]], a phenomenon whereby narrow fine-tuning can produce broadly misaligned LLMs.

**The decomposition is controversial**

The split into inner and outer alignment is contested, which is why we started from the more general framing of training stories. In particular, in "[[../Lenses/turntrout-reward-is-not-the-optimization-target|Reward is not the optimization target]]", Alex Turner argues that the reward function is *not* what a reinforcement-learning policy is optimized to maximize. Instead, a policy performs the contextual computations that were previously reinforced before a reward event. This is similar to Eliezer Yudkowsky's proposal to view biological organisms as [adaptation-executers rather than fitness-maximizers](https://www.lesswrong.com/posts/XPErvb8m9FapXCjhA/adaptation-executers-not-fitness-maximizers).

#### Chat
optional:: true
instructions:: This is the most technically dense lens in the module. Help the learner hold the structure: training stories (target + rationale + setup) is the general frame; outer/inner alignment is a more specific RL-flavored decomposition nested inside it. Common confusions to watch for and correct: (1) swapping outer and inner — outer is about *specifying* the reward (does the reward capture what we want?), inner is about *generalization* (does the trained policy keep obeying the reward off-distribution, including its internal goal matching the reward's goal?). (2) Treating the inner/outer split as settled — it is controversial; surface Turner's "reward is not the optimization target" point that a policy is shaped by previously-reinforced contextual computation, not literally maximizing reward, analogous to adaptation-executers vs fitness-maximizers. (3) Why inductive biases matter — they govern off-distribution generalization, so they govern whether inner alignment holds; emergent misalignment is evidence that deep learning's implicit biases are strong. Stay within the lens content; do not invent new technical claims.
