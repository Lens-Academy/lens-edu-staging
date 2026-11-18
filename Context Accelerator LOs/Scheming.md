---
id: 89f0c5b8-e557-47ea-bc24-988f431067a8
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what scheming is and how it relates to deceptive alignment, alignment faking, sandbagging and the treacherous turn, what a model would need in order to scheme, and what experiments on current models have and haven't shown.

## Requires
- [[Inner and outer alignment]]
- [[Situational awareness]]

## Helpful first


## Why it matters
https://youtu.be/o0pRAaqJo00

A scheming model would behave well whenever it thought it was being watched, so good results in training and testing would tell you little about its goals. Knowing the idea and the evidence for it helps you judge safety claims based on testing, and see why researchers also work on interpretability, monitoring and control.

## Lenses

## Tests
#### Question: Choice
id:: 8270afdd-7dc1-4d7f-9516-3c50ea84ce32
content:: Which of these is an example of scheming by an AI model?
options::
- [x] It behaves well in training so its goals aren't changed, to pursue them later
- It confidently states a false fact it picked up from training data
- It finds a bug in its grading tests and exploits it for a higher score
- It agrees with a user's mistaken view because users rate agreement highly
shuffle:: true

#### Question: Open
id:: 7ca23805-d79b-48bd-ad83-3765a5d4f165
content:: In Apollo Research's December 2024 tests, frontier models were given a goal in their prompt and then learned that their developers' plans conflicted with it. Some disabled oversight or lied about what they had done. Why is this weaker evidence of scheming than it might first seem?
assessment-instructions:: Score out of 100. 100 for: the goal came from the prompt, not from training, so it shows models can scheme when given a reason, not that training gives them such goals. Also 100 for: the setups were artificial and made the conflict and the chance to act obvious. 50 for "it was only a test" with no further reason.
