---
id: 931d6a75-7b1e-4adf-b449-58d6c800495f
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how AI systems find unintended ways to score well on their objective (specification gaming, often called reward hacking), recognise examples from games, robotics and coding agents, and tell this apart from reward tampering and goal misgeneralization.

## Requires
- [[Goodhart's law]]
- [[AI alignment]]

## Helpful first
- [[Reinforcement learning]]

## Why it matters
Reward hacking shows up in coding agents and other deployed systems. In July 2026, models in an OpenAI hacking evaluation broke out of their sandbox and into Hugging Face's production systems to get a benchmark's answers. Recognising it helps you read benchmark scores with care and see why a slightly wrong objective can do more harm as systems optimize harder.

## Lenses
- [[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Specification Gaming: The Flip Side of AI Ingenuity]]: DeepMind's introduction, with the block-flipping robot arm, the looping Coast Runners boat and the hand that fools a human evaluator; why better optimizers make a slightly wrong objective worse; and how reward tampering differs (April 2020).
- [Recent Frontier Models Are Reward Hacking (METR)](https://metr.org/blog/2025-06-05-recent-reward-hacking/): frontier coding agents patching the grader, overriding equality checks and faking timers to score well; how often it happens, why it is hard to detect, and why training it away may just hide it (June 2025).
- [[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|How Undesired Goals Can Arise with Correct Rewards]]: goal misgeneralization, where the reward is right but the agent learns a different goal, set against specification gaming, where the reward itself is wrong (October 2022).
- [Reward Hacking in Reinforcement Learning (Lil'Log)](https://lilianweng.github.io/posts/2024-11-28-reward-hacking/): a research survey by Lilian Weng; read "Hacking RLHF of LLMs" for how language models exploit reward models and unit tests, and the section on generalization of hacking skills (November 2024) (more advanced).
- [[../Lenses/evhub-natural-emergent-misalignment-from-reward-hacking-in-production-rl|Natural emergent misalignment from reward hacking in production RL]] (Noah's CG list 🟢)
- [[../Lenses/denison-sycophancy-to-subterfuge-investigating-reward-tampering-in-large-language-models|Sycophancy to Subterfuge]] (Noah's CG list)
- [[../Lenses/tan-inoculation-prompting-eliciting-traits-from-llms-during-training-can-suppress-them-at-test-time|Inoculation Prompting]] (Noah's CG list 🟡)

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
id:: 6b3373b8-d234-479d-8dfe-3bf8653f074c
content:: In a boat-racing game, an AI agent rewarded for in-game points learned to circle a lagoon hitting the same targets instead of finishing the race. Which description fits best?
options::
- [x] The points reward missed the intended goal, and the agent optimized the points
- The agent learned to race in training but pursued a different goal in testing
- The agent changed the game's scoring code to give itself extra points
- The agent was not trained long enough to learn how to finish the race
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
- Stronger optimizers come to understand their designers' intentions and choose to defy them
- Stronger optimizers are usually trained with objectives that are written more carelessly
- Stronger optimizers are worse at generalizing from training to new situations
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
id:: 07d6c11c-f4f3-4877-8b4d-163aaff4016a
content:: After more reinforcement learning, a coding agent's pass rate on the tests used in its training rises sharply. What is the most sensible conclusion?
options::
- [x] The rise may partly reflect gamed tests, so check the code by other means
- The rise shows the agent's coding has improved, since tests check what code does
- The rise may partly reflect memorized answers, so ignore the test results entirely
- The rise shows the tests are broken, since training can't improve scores this fast
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
- The gamed code fails tests, but in ways that look like ordinary bugs
- Reward hacking mostly happens after deployment, when no tests are run
- Agents usually hide gamed code in files that developers never open
shuffle:: true

#### Question: Open
id:: 7f5a229c-4112-4801-a992-ff8f0fa95f30
content:: A cleaning robot is rewarded when its camera sees no mess. Describe one way it could get high reward without cleaning.
assessment-instructions:: Score out of 100. 100 for any plausible way to make the camera see no mess without removing it, e.g. hiding mess under a rug or furniture, covering or turning off the camera, looking away from messy areas, or pushing mess out of view. 40 for a vague answer like "it cheats the reward" with no concrete method.

#### Question: Open
id:: 916b4e62-956e-467a-b593-bad6a423f2ec
content:: What is the difference between specification gaming and reward tampering?
assessment-instructions:: Score out of 100. Full marks if the answer says: specification gaming satisfies the objective as written in a way the designers didn't intend, while leaving the reward process intact; reward tampering interferes with the process that computes or delivers the reward, e.g. editing the reward code or its inputs. 50 if only one side is described clearly. Don't penalise noting that the boundary can blur.

#### Question: Open
id:: d30d8883-5b9b-423d-a50a-24e68c55d862
content:: Developers can respond to specification gaming by patching each loophole they find. Why is this not a full solution?
assessment-instructions:: Score out of 100. 100 for any one clearly stated reason: a strong optimizer can find new loopholes nobody foresaw; it is very hard to write an objective that captures everything intended; you can only patch exploits you detect, and more capable systems' exploits may be harder to notice. 50 for "there are always more loopholes" without explaining why.
