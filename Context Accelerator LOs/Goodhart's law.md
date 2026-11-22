---
id: 50104fba-77bf-43de-af02-1229b206ac8f
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why a measurable stand-in for a goal that works under light pressure tends to break under heavy optimization, and recognize this pattern in AI training and in human institutions.

## Requires

## Helpful first
- [[Intelligence as optimization]]

## Why it matters
https://www.youtube.com/shorts/clWbMwUkaHs

AI systems are trained and judged on measurable stand-ins: reward signals, benchmarks, human ratings. A learner who expects a proxy that works today to keep working as systems grow more capable will misjudge the risk of reward hacking. Goodhart's law explains why stronger optimization makes these failures more likely, not less.

## Lenses
- [[../Lenses/johnswentworth-why-agent-foundations-an-overly-abstract-explanation|Why Agent Foundations? (Goodhart sections)]]: the Soviet nail factory, "instagram food", and why training an AI on human approval makes things look good rather than be good once optimization pressure rises; read from the start to the end of "Goodhart Is Not Inevitable" (March 2022).
- [Too much efficiency makes everything worse (Jascha Sohl-Dickstein)](https://sohl-dickstein.github.io/2022/11/06/strong-Goodhart.html): the "strong version" of Goodhart's law, where the real goal first improves, then stalls, then gets worse as the proxy keeps rising, with examples from schools, science and politics and fixes such as regularization and early stopping (November 2022).
- [[../Lenses/garrabrant-goodhart-taxonomy|Goodhart Taxonomy]]: four ways proxies break under optimization (regressional, causal, extremal, adversarial); read the Quick Reference, Regressional Goodhart and Extremal Goodhart sections, which explain why the top proxy score is rarely the top true score and why extreme cases break the correlation (December 2017).
- [Scaling Laws for Reward Model Overoptimization (arXiv)](https://arxiv.org/abs/2210.10760): the experiment that trains language models harder against a learned reward model and measures a separate "gold" reward, and how the KL penalty affects the result; the abstract and figures are enough (October 2022) (more advanced).
- [[../Lenses/lesswrong-goodharts-curse|Goodhart's curse]] (Noah's CG list 🔴)

## Tests

#### Question: Choice
id:: 7d12c2c3-97a1-4fd8-8a08-09a095d8b42b
content:: A team says: "Our reward model agrees with human raters 95% of the time on current outputs, so training a much stronger model against it is safe." What does Goodhart's law suggest is wrong with this reasoning?
options::
- [x] Current outputs say little about the unusual ones strong optimization will find.
- 95% agreement is too low; at 99% agreement the reasoning would hold.
- A stronger model will want to deceive the reward model; a weaker one would not.
- The human raters, not the reward model, are the weak link in the setup.
shuffle:: true

#### Question: Choice
id:: a3e1b668-71a0-4972-ae45-8e5c0fb9fae2
content:: A reward model's scores correlate strongly, but not perfectly, with the true quality of answers. An optimizer searches millions of candidate answers and picks the one with the single highest reward score. What should you expect about that answer?
options::
- [x] It is probably good, but its score overstates how good it is.
- It is very likely the best of all the candidates.
- It is about average, since extreme scores are mostly noise.
- Its score probably understates its quality, since top answers are hard to judge.
shuffle:: true

#### Question: Open
id:: e2c19992-809a-409a-95ad-4ddc47be50d7
content:: Using Goodhart's law, explain why a proxy that tracks a goal well under weak optimization can fail badly under strong optimization.
assessment-instructions:: Score out of 100. 100 for: proxy and goal agree on typical cases but differ on some unusual ones; stronger optimization searches further and picks extreme proxy scores, which are disproportionately where the two diverge, so the gap grows. 50 for only saying proxies are imperfect, without explaining why stronger optimization makes it worse.

#### Question: Choice
id:: 6ece5380-792a-46e0-b11a-65b219352bb7
content:: Which observation shows Goodhart's law at work, rather than just showing that a measure is imperfect?
options::
- [x] A test's scores keep rising under training pressure while the underlying skill stalls.
- A test misranks a few students who happened to have a bad day.
- A reading-speed test captures little about reading comprehension.
- Two tests of the same skill give slightly different scores.
shuffle:: true

#### Question: Choice
id:: 61156a0f-60a4-4621-b8df-12f2bf2e19d6
content:: Which of these is the clearest example of Goodhart's law in AI training?
options::
- [x] A model trained on rater approval learns confident wrong answers that raters like.
- A model does worse on languages that are rare in its training data.
- A model's benchmark score varies slightly between evaluation runs.
- A model repeats facts that have since become outdated.
shuffle:: true

#### Question: Choice
id:: 9338dd93-a3ce-4f93-a40a-ac45bbd7e6fb
content:: Which of these is needed for Goodhart's law to apply to an optimization process?
options::
- [x] Selection pressure toward higher proxy scores, by any mechanism.
- An optimizer that understands what the real goal is.
- An optimizer that intends to mislead its overseers.
- A proxy that was carelessly chosen in the first place.
shuffle:: true

#### Question: Choice
id:: a8b05452-2125-497f-bb51-0df814892aca
content:: In reinforcement learning from human feedback (RLHF), training usually includes a penalty for drifting too far from the original model. How does this penalty relate to Goodhart's law?
options::
- [x] It limits optimization pressure, keeping outputs where the reward model is still reliable.
- It makes the reward model more accurate on unusual outputs.
- It removes the need for further rounds of human feedback.
- It speeds up training by reducing the number of updates.
shuffle:: true

#### Question: Choice
id:: 0800f7fd-e559-4d5f-957b-0ff7a6c8e114
content:: Experiments on Goodhart's law in language models train a policy harder and harder against a learned reward model, judging quality with a separate "gold" reward model. What typically happens to the gold score?
options::
- [x] It rises at first, then falls while the proxy reward keeps rising.
- It rises steadily along with the proxy reward.
- It falls from the start of optimization onward.
- It stays flat while the proxy reward rises.
shuffle:: true

#### Question: Open
id:: d634a995-0646-4305-aa1d-2a1d597ac12f
content:: A customer support team, human or AI, is rewarded for short average call times. Using Goodhart's law, describe one way this could go wrong as the pressure to cut call times increases.
assessment-instructions:: Score out of 100. 100 for any behaviour that shortens calls without helping customers (ending calls early, transferring or dodging hard cases, giving quick but wrong fixes), linked to call time being optimized in place of the real goal of solving problems. 60 for a valid behaviour with no link to the proxy–goal gap.
