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

#### Question: Open
id:: e2c19992-809a-409a-95ad-4ddc47be50d7
content:: Using Goodhart's law, explain why a proxy that tracks a goal well under weak optimization can fail badly under strong optimization.
assessment-instructions:: Score out of 100. 100 for: proxy and goal agree on typical cases but differ on some unusual ones; stronger optimization searches further and picks extreme proxy scores, which are disproportionately where the two diverge, so the gap grows. 50 for only saying proxies are imperfect, without explaining why stronger optimization makes it worse.
