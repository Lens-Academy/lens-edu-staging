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

## Tests

#### Question: Choice
id:: 7d12c2c3-97a1-4fd8-8a08-09a095d8b42b
content:: A team says: "Our reward model agrees with human raters 95% of the time on current outputs, so training a much stronger model against it is safe." What does Goodhart's law suggest is wrong with this reasoning?
options::
- [x] Agreement on current outputs says little about the unusual outputs strong optimization seeks.
- 95% agreement is too low; at 99% the reasoning would hold.
- The human raters, not the reward model, are the weak link.
- Stronger models are less able to find flaws in reward models.
shuffle:: true

#### Question: Choice
id:: 38bd7640-d991-478f-9b77-9433ca895e58
content:: In discussions of Goodhart's law, "the tails come apart" describes two measures that are strongly but not perfectly correlated. If you pick the case with the single highest score on one measure, what usually holds for the other?
options::
- [x] It is high, but usually not the highest of all cases.
- It is very likely the highest of all cases.
- It is close to the average across all cases.
- It is usually below average, because the correlation is imperfect.
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

#### Question: FillBlank
id:: ec3e9c47-792e-47ba-b5f6-f2f6e302cbb7
content:: Goodhart's law is often summarized as: "When a measure becomes a {{target}}, it ceases to be a good measure."

#### Question: Open
id:: d634a995-0646-4305-aa1d-2a1d597ac12f
content:: A customer support team, human or AI, is rewarded for short average call times. Using Goodhart's law, describe one way this could go wrong as the pressure to cut call times increases.
assessment-instructions:: Score out of 100. 100 for any behaviour that shortens calls without helping customers (ending calls early, transferring or dodging hard cases, giving quick but wrong fixes), linked to call time being optimized in place of the real goal of solving problems. 60 for a valid behaviour with no link to the proxy–goal gap.
