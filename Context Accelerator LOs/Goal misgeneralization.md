---
id: 8df50c32-28b7-4320-9194-8eca80351d02
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how a model can learn a goal that fits its training but leads it to competently pursue the wrong thing in new situations, and tell this apart from specification gaming and from simple lack of skill.

## Requires
- [[Inner and outer alignment]]

## Helpful first
- [[Specification gaming]]

## Why it matters
A correct reward signal does not guarantee that a model learns the intended goal. Knowing this, you can see why good behaviour in training is weak evidence of alignment, and why a capable system needs testing in unfamiliar situations before it is trusted with them.

## Lenses

## Tests

#### Question: FillBlank
id:: 388e3f0a-aaed-4298-ab48-dbd2cb2efbb6
content:: When the situations a model meets after training differ from those in its training data, this is called {{distributional shift|distribution shift}}.

#### Question: Choice
id:: 93b6c28e-6c5a-4629-9e8f-1e28f96fd0ca
content:: In a video game experiment, an agent was rewarded for collecting a coin that always sat at the right-hand end of each training level. When the coin was moved, the agent ignored it and ran to the end. What does this illustrate?
options::
- [x] Goal misgeneralization
- Specification gaming
- Catastrophic forgetting
- Reward tampering
shuffle:: true

#### Question: Choice
id:: 9b609882-8b25-4552-8453-a5f769bcdcf7
content:: Which of these is an example of goal misgeneralization rather than a plain capability failure?
options::
- [x] A maze agent trained with cheese in one corner heads straight there when the cheese is moved
- A maze agent trained on small mazes gets lost in much larger ones
- An image classifier trained on daytime photos mislabels night-time photos
- A chess program trained on common openings plays badly after an unusual one
shuffle:: true

#### Question: Choice
id:: 345898da-1b92-49c8-bcd8-8ee6e2249b56
content:: A developer says: "Our reward function captured exactly what we wanted, so the model can't have learned the wrong goal." What does goal misgeneralization show about this claim?
options::
- [x] It fails, because several goals can fit the same training rewards and the model may learn another
- It holds, because a correct reward leaves the model no room to learn a different goal
- It fails only if the reward function had a bug that the model exploited
- It holds as long as the model also scores well on held-out training data
shuffle:: true

#### Question: Choice
id:: dcd1933a-44b0-4c04-9529-a6593e673d81
content:: Why is goal misgeneralization hard to spot by watching a model during training?
options::
- [x] The intended goal and the learned goal lead to the same behaviour on the training data
- The model hides its learned goal whenever it detects that it is being trained
- Training metrics record the model's scores but not the actions it takes
- The learned goal forms only after the model has been deployed
shuffle:: true

#### Question: Choice
id:: 1446cb54-7520-4d94-b3f7-a1d4c36adab6
content:: A model is trained with a reward that correctly captures what its designers want, but it learns a different goal that only shows up in new situations. Is this an inner alignment failure or an outer alignment failure?
options::
- [x] Inner alignment failure
- Outer alignment failure

#### Question: Choice
id:: f3b1a57d-bac7-49ba-a42a-3f701bf044af
content:: An AI assistant was rewarded when users rated its answers helpful. All its training users happened to prefer short answers. Deployed with users who need detailed explanations, it keeps giving short, well-written answers. Which explanation fits goal misgeneralization?
options::
- [x] It learned "be brief" instead of "be helpful", since both earned reward in training
- Its reward function was written to give points for short answers
- It lost its ability to write long answers outside its training data
- It noticed it was no longer being trained and stopped making an effort
shuffle:: true

#### Question: Choice
id:: d51dfb61-5b59-4b18-a42f-1ae4bfeee0d4
content:: Why does goal misgeneralization become more worrying as AI systems become more capable?
options::
- [x] A capable system pursuing the wrong goal can do more harm than one that simply fails
- More capable systems are usually trained on less varied data
- More capable systems are more likely to have bugs in their reward functions
- More capable systems are rarely tested outside their training data
shuffle:: true

#### Question: Choice
id:: 3f9310aa-4b37-4ea2-ac37-61a0da8f0845
content:: Which check would most directly reveal goal misgeneralization before a model is deployed?
options::
- [x] Testing it in situations where the intended goal and likely stand-in goals call for different actions
- Training it for longer on the same data until its training score stops improving
- Having experts review the reward function to confirm it matches what is wanted
- Measuring its accuracy on more examples drawn from the training distribution
shuffle:: true

#### Question: Open
id:: b9898d5f-f3ac-4958-9ca3-05eab316a878
content:: In your own words, how does goal misgeneralization differ from specification gaming?
assessment-instructions:: Score out of 100. 100 for: in specification gaming the objective or reward itself is flawed and the model exploits that flaw; in goal misgeneralization the reward can be correct, but the model learns a different goal that fit training and diverges in new situations. 50 if only one side is described correctly.

#### Question: Open
id:: f8c8d3d8-49a0-4746-82fd-4cd88941ad69
content:: Why doesn't good performance during training show that a model has learned the goal its designers intended?
assessment-instructions:: Score out of 100. 100 for: different goals can produce the same behaviour on the training data, so training results can't tell them apart; the difference appears only in new (out-of-distribution) situations. 50 for saying only that the model may behave differently later, without saying why training can't distinguish the goals.

#### Question: Open
id:: 26a7346d-01ef-4e38-9a35-227e9084e952
content:: Give an example, real or made up, of goal misgeneralization. Name the intended goal and the goal the model actually learned.
assessment-instructions:: Score out of 100. 100 for an example where both goals lead to the same behaviour in training but come apart in a new situation, with the model competently pursuing the learned goal, and both goals named. 50 if one goal is unnamed. 0 if the reward itself was flawed (specification gaming) or the model just performs badly.
