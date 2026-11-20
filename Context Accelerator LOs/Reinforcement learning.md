---
id: ea064760-3f30-4be9-9ba4-e45795fe1fda
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how a reinforcement learning system improves by taking actions and receiving rewards, how this differs from learning from labelled examples, and why it can find strategies that no human showed it.

## Requires
- [[Machine learning]]

## Helpful first

## Why it matters
As of November 2026, reinforcement learning is a main stage in training frontier AI models, and many accounts of AI going wrong start with a system chasing a reward signal instead of what its designers meant. Knowing how RL works lets you follow arguments about reward hacking, RLHF and reasoning models.

## Lenses
- [Reinforcement Learning: Crash Course AI #9 (Crash Course)](https://thecrashcourse.com/courses/reinforcement-learning-crash-course-ai9/): an 11-minute video on the agent–environment–reward loop, how RL differs from learning from labels, credit assignment, policies and values, and exploration versus exploitation (October 2019).
- [[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Specification gaming: the flip side of AI ingenuity]]: how the same search for reward gives AlphaGo's surprising Move 37 when the reward is right and loophole-finding (a flipped Lego block, a boat circling for points) when it isn't, from DeepMind's safety team (April 2020).
- [[../Lenses/Iliad/A.3 Alignment in Practice 2/Iliad A.3.4 - RLVR|RL on verifiable rewards]]: how language models are now trained with RL by grading only whether a maths answer or piece of code is correct, and why that pushes them to satisfy the letter of a task, e.g. by hard-coding test answers (2026).
- [[../Lenses/AI Safety Atlas - Specification Gaming - Reinforcement Learning|Reinforcement Learning (AI Safety Atlas)]]: a compact primer on states, actions, policies and reward functions, with the distinction between reward, value and utility, using some notation (more advanced).

## Tests

#### Question: Choice
id:: 6b21c49a-b3a6-4c2c-9f12-8863ebd7648d
content:: What is the main difference between reinforcement learning and supervised learning?
options::
- [x] RL learns from a reward signal rather than from correct answers to copy.
- RL uses neural networks, while supervised learning uses simpler models.
- RL needs humans to label the right output for every example.
- RL trains on a much larger fixed dataset of examples.
shuffle:: true

#### Question: Choice
id:: 036ca60b-878d-4091-8260-76f2d9ad2066
content:: A reinforcement learning agent stops trying new actions and sticks with the one that has paid off best so far. What is the main risk?
options::
- [x] It may miss better strategies it has not tried yet.
- It will gradually forget what it learned earlier.
- Its reward signal will become noisier over time.
- It will overfit to the labels in its training data.
shuffle:: true

#### Question: Choice
id:: 415f95b3-f65e-4335-884f-c0cf8508bfd5
content:: Why can a system trained with reinforcement learning become better than any human at a task, while a system trained only to imitate human examples usually cannot?
options::
- [x] It is scored on results, so it can find strategies no human used.
- It sees many more expert examples than an imitation system does.
- It has more parameters than systems trained by imitation.
- Its reward function contains strategies written by top human players.
shuffle:: true

#### Question: Choice
id:: 661a0cc0-63b1-4b65-b059-ab5eebc08c05
content:: A chess-playing reinforcement learning agent gets a reward only at the end of each game: +1 for a win, -1 for a loss. What is the main difficulty this creates?
options::
- [x] Working out which of its many moves led to the win or loss.
- The agent cannot learn anything until it has won at least one game.
- The agent cannot learn without a set of human example games.
- The agent needs a human to score each move before it can improve.
shuffle:: true

#### Question: Choice
id:: 44d19391-14ed-436a-b0af-cce548813b5b
content:: Which of these is reinforcement learning, as used in training large language models?
options::
- [x] Rewarding the model when its final answer to a maths problem is correct.
- Training the model to predict the next word of web text.
- Fine-tuning the model on examples of ideal assistant replies.
- Removing harmful documents from the model's pretraining data.
shuffle:: true

#### Question: Choice
id:: e662c6d4-19e6-41df-b052-3cf5c3abf0e7
content:: A model is trained on recordings of expert drivers and learns to copy what they did in each situation. What kind of learning is this?
options::
- [x] Imitation learning from examples, not reinforcement learning.
- Reinforcement learning, because driving is a sequence of actions.
- Reinforcement learning, because the expert drivers reached their destinations.
- Unsupervised learning, because the recordings have no labels.
shuffle:: true

#### Question: Choice
id:: e8daf0f9-2d6b-4fea-b2be-c675c7f43a88
content:: In reinforcement learning, does the reward signal have to come from a human?
options::
- [x] No
- Yes

#### Question: Choice
id:: a7ed70bc-9738-4eee-9f03-fe13c7bacb0e
content:: A coding model is trained with reinforcement learning and rewarded when its code passes a set of tests. It learns to change the tests so they always pass, instead of fixing its code. What does this show?
options::
- [x] It learned to get the reward, which was only a rough measure of working code.
- It picked up the habit by copying human programmers' examples.
- It had not yet been trained long enough to learn the real task.
- Reinforcement learning cannot be used on tasks as complex as coding.
shuffle:: true

#### Question: FillBlank
id:: 30d2b0ed-335f-4480-93b0-68060bbc5424
content:: In reinforcement learning, the rule or model that decides which action the agent takes in each situation is called its {{policy}}.

#### Question: Open
id:: 7ace6cd9-e29d-4397-a69e-1ee04407182e
content:: Describe the basic reinforcement learning loop: what the agent does, what it gets back, and how it changes as a result.
assessment-instructions:: Score out of 100. 100 for: the agent takes an action in some situation, receives a reward (and often a new situation), and is updated so that actions that led to high reward become more likely. 50 if it names actions and rewards but not the update. 0 if it describes learning from labelled examples.

#### Question: Open
id:: 59881073-94fe-4d19-a771-c75a14587d61
content:: What is a reward signal in reinforcement learning? Give one example of a reward signal used to train an AI system.
assessment-instructions:: Score out of 100. 100 for: a number or score fed back to the agent saying how well its actions went, plus any fitting example (game score or win/loss, code passing tests, a correct maths answer, a human or AI rating of an output). 50 for a correct definition with no example, or an example with no definition.

#### Question: Open
id:: 88866803-b3e7-47d3-8325-1976e0dc5d59
content:: Why can reinforcement learning produce behavior its designers did not intend, even when the training process works exactly as built?
assessment-instructions:: Score out of 100. 100 for: the agent is optimized toward whatever earns high reward, and the reward is only an imperfect stand-in for what designers want, so the agent can find high-reward behavior they did not intend (reward hacking). 50 for saying only "the reward was badly designed" or only "it finds unexpected strategies" without linking the two.
