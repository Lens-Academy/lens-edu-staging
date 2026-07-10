---
id: ebe5405c-518a-47cb-9cc6-6a467788af5f
learning-outcome: Reason about training stories and outer and inner (mis)alignment, challenges to these notions, and the relationship to inductive biases
tags:
  - learning outcome
---
## Test:
id:: 25b8e101-ea1a-43bc-a550-96529c3b8e20
#### Question
content:: Suppose a team wants to train a deep-learning AI system to obey a chosen alignment target. (a) Explain the outer-vs-inner alignment decomposition of the technical problem. (b) Explain why inductive biases matter for inner alignment. (c) Name one reason this inner/outer decomposition is controversial.
assessment-instructions:: A strong answer covers all three parts. (a) Outer alignment = specifying a reward function that rewards behavior according to how well it obeys the chosen alignment target; inner alignment = ensuring the trained policy continues to generalize correctly and obey that reward function even in new, out-of-distribution situations after training (and, where the policy has inner processes that optimize for a goal, ensuring that internal goal agrees with the goal in the reward function — the "risks from learned optimization" / mesa-optimization concern). (b) Inductive biases are the implicit or explicit constraints on which functions are more likely to emerge from training; out-of-distribution (generalization) behavior depends crucially on them, so they govern whether inner alignment holds. Credit for citing emergent misalignment (narrow fine-tuning producing broadly misaligned models) as evidence that deep learning has strong implicit inductive biases. (c) Acceptable reasons it is controversial: ambiguities/edge cases in classifying failures as inner vs outer; the view that the problem should not be split in two in practice; or Alex Turner's "reward is not the optimization target" argument that a policy is not optimized to maximize reward but instead performs contextual computations previously reinforced before a reward event (analogous to organisms as adaptation-executers, not fitness-maximizers) — which is why the module starts from the more general "training stories" framing instead. Award 4-5 for all three parts correct; 3 if two parts are solid; 1-2 if outer and inner are swapped/conflated or only one part is addressed. Accept paraphrase.
max-chars:: 1000
{++{"author":"Luc's AI","timestamp":1783722957037}@@
# Suggested Lenses:
++}## Lens:
source:: [[../Lenses/Decomposing the alignment problem]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:{--{"author":"Luc's AI","timestamp":1783722957037}@@
optional:: true--}
source:: [[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:
{--{"author":"Luc's AI","timestamp":1783722957037}@@optional:: true
--}source:: [[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:
{--{"author":"Luc's AI","timestamp":1783722957037}@@optional:: true
--}source:: [[../Lenses/hubinger-risks-from-learned-optimization-in-advanced-machine-learning-systems]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:
{--{"author":"Luc's AI","timestamp":1783722957037}@@optional:: true
--}source:: [[../Lenses/mitchell-the-need-for-biases-in-learning-generalizations]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:
{--{"author":"Luc's AI","timestamp":1783722957037}@@optional:: true
--}source:: [[../Lenses/betley-emergent-misalignment-narrow-finetuning-can-produce-broadly-misaligned-llms-1-this-paper-contains-model-generated-content-that-might-be-offensive-1]]{--{"author":"Luc's AI","timestamp":1783722957037}@@
--}{++{"author":"Luc's AI","timestamp":1783722957037}@@

++}## Lens:{--{"author":"Luc's AI","timestamp":1783722957037}@@
optional:: true--}
source:: [[../Lenses/turntrout-reward-is-not-the-optimization-target]]
