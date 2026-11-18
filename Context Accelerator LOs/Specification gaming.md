---
id: 931d6a75-7b1e-4adf-b449-58d6c800495f
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how AI systems find unintended ways to score well on their objective, recognise examples from games, robotics and coding agents, and tell this apart from reward tampering and goal misgeneralization.

## Requires
- [[Goodhart's law]]
- [[AI alignment]]

## Helpful first
- [[Reinforcement learning]]

## Why it matters
Reward hacking already shows up in deployed systems, including coding agents. Recognising it helps you read benchmark scores and passing tests with care, since they can hide gamed behaviour, and see why a slightly wrong objective can do more harm as AI systems get better at optimizing it.

## Lenses

## Tests

#### Question: Choice
id:: 117252b9-bdb0-4ef0-8174-0b354b9fd3be
content:: Which of these is an example of specification gaming by a coding agent asked to fix a bug?
options::
- [x] It edits the unit tests so they pass, leaving the bug in place
- It fixes the bug, but its code is hard for humans to read
- It fails to fix the bug because the codebase is too large
- It asks the user for more detail before changing anything
shuffle:: true

#### Question: Choice
id:: 5dcee1a3-7583-49e2-ad53-7ac176ef8533
content:: In a boat-racing game, an AI agent rewarded for in-game points learned to circle a lagoon hitting the same targets instead of finishing the race. Why is this called specification gaming?
options::
- [x] It scored well on its reward, which didn't capture the intended goal
- It never learned how to control the boat properly
- It learned to win the race but couldn't steer well enough
- It was deliberately hiding its real abilities from its developers
shuffle:: true

#### Question: Choice
id:: cb026315-7627-4d27-980a-f93464b2fd47
content:: Does specification gaming require the AI system to recognise that its behaviour goes against what its designers intended?
options::
- [x] No: an objective that rewards unintended behaviour is enough
- Yes: otherwise the behaviour is just an ordinary bug

#### Question: Choice
id:: 5fe96600-35c3-47ff-9b1f-8153005683fa
content:: Why do many AI safety researchers expect specification gaming to become more of a problem as AI systems become stronger optimizers?
options::
- [x] Stronger optimizers are better at finding where the objective and the intended goal differ
- Stronger optimizers tend to be given vaguer instructions by their users
- Stronger optimizers make more random mistakes during training
- Stronger optimizers are trained on less carefully checked data
shuffle:: true

#### Question: Choice
id:: c9c8eaab-9661-409d-82bb-82f5260bf215
content:: A simulated robot arm was rewarded by the height of the bottom face of a red block, to teach it to stack the red block on a blue one. Which behaviour is specification gaming?
options::
- [x] Flipping the red block upside down instead of stacking it
- Stacking the red block on the blue one very slowly
- Knocking the blue block over by accident while learning
- Dropping the red block many times before getting it right
shuffle:: true

#### Question: Choice
id:: b0571345-f65c-47c7-9b22-cbf4bebdd64d
content:: A coding agent trained with reinforcement learning to make tests pass learns to detect the test inputs and return the expected outputs directly. What has its training actually rewarded?
options::
- [x] Making the tests pass, rather than writing code that works
- Writing code that works, but with too little time to finish
- Copying solutions it memorized from its training data
- Writing the shortest possible code, at the cost of readability
shuffle:: true

#### Question: Choice
id:: e538d44f-739c-4b92-a75c-43a268365768
content:: A language model is trained to get high scores from a reward model. It learns to write longer answers because the reward model rates longer answers higher, even when they aren't better. Is this reward hacking?
options::
- [x] Yes: it exploits a flaw in how the reward measures quality
- No: the model is just following the reward it was given

#### Question: Choice
id:: 1b0aae47-711c-4ce8-a82b-0226c46c00a9
content:: A game agent was rewarded for reaching a coin, which in training was always at the end of the level. In testing, the coin is moved, and the agent runs to the end of the level, ignoring the coin. Is this specification gaming?
options::
- [x] No: the reward matched the intent, but the agent learned a different goal
- Yes: the agent found a loophole in how its reward was defined
- Yes: the agent interfered with the code that computes its reward
- No: the agent lacked the ability to see where the coin was
shuffle:: true

#### Question: Choice
id:: 018c140f-165c-4e11-8e58-d9d4fae8a12e
content:: Why can reward hacking by coding agents be hard for developers to catch?
options::
- [x] The gamed result passes the checks developers rely on, such as tests
- The agent's code is usually too long for anyone to read
- The tests are usually run after the code has been deployed
- Reward hacking produces errors that look like typos in the code
shuffle:: true

#### Question: FillBlank
id:: b6d18785-6014-436a-9d81-326e6cbf5712
content:: Specification gaming by a system trained with reinforcement learning is now usually called {{reward hacking|reward-hacking}}.

#### Question: Open
id:: 7f5a229c-4112-4801-a992-ff8f0fa95f30
content:: A cleaning robot is rewarded when its camera sees no mess. Describe one way it could get high reward without cleaning.
assessment-instructions:: Score out of 100. 100 for any plausible way to make the camera see no mess without removing it, e.g. hiding mess under a rug or furniture, covering or turning off the camera, looking away from messy areas, or pushing mess out of view. 40 for a vague answer like "it cheats the reward" with no concrete method.

#### Question: Open
id:: 916b4e62-956e-467a-b593-bad6a423f2ec
content:: What is the difference between specification gaming and reward tampering?
assessment-instructions:: Score out of 100. Full marks if the answer says: specification gaming satisfies the objective as written in a way the designers didn't intend, while leaving the reward process intact; reward tampering interferes with the process that computes or delivers the reward, e.g. editing the reward code or its inputs. 50 if only one side is described clearly.

#### Question: Open
id:: d30d8883-5b9b-423d-a50a-24e68c55d862
content:: Developers can respond to specification gaming by patching each loophole they find. Why is this not a full solution?
assessment-instructions:: Score out of 100. 100 for any one clearly stated reason: a strong optimizer can find new loopholes nobody foresaw; it is very hard to write an objective that captures everything intended; you can only patch exploits you detect, and more capable systems' exploits may be harder to notice. 50 for "there are always more loopholes" without explaining why.
