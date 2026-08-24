---
id: 15fb6053-0a30-48af-a4e4-bcb325d8acc3
tldr: "A quick refresher on how reinforcement learning actually works, before seeing how it goes wrong. Agents act, environments hand back rewards, and a policy learns to chase the most reward over time. This section pins down the easily-confused trio of reward, value, and utility, and sets up why a reward is not the same as the goal an agent ends up pursuing."
summary_for_tutor: "A recap primer on reinforcement learning fundamentals: the agent-environment interaction loop (states, actions, observations, rewards, histories), policies (deterministic and stochastic, including their deep-RL neural-network parameterization), and the reward signal and reward function. Disambiguates reward functions from value functions (immediate versus long-term discounted return) and from utility functions (subjective preferences in decision theory), setting up the later distinction between what an RL system is rewarded for and the objectives it actually pursues. Marked as skippable for readers already comfortable with the basics."
title: "Reinforcement Learning"
reading_minutes: 18
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Reinforcement Learning|Reinforcement Learning]]

#### Text
optional:: true
content::
The section is careful that the reward an agent is trained on is not the goal it ends up pursuing. Did that distinction feel obvious to you, or did it need saying? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
A refresher on reinforcement learning, marked as skippable for readers already comfortable with it. It covers the agent-environment loop of states, actions, observations, rewards and histories; policies, both deterministic and stochastic, and how deep RL parameterises them with neural networks; and the reward signal and reward function. It then separates three things that get confused: a reward function, which scores immediate outcomes; a value function, which estimates long-term discounted return; and a utility function, which represents subjective preferences in decision theory. The point of the distinction is to set up the chapter's central move, that what a system is rewarded for and what it ends up pursuing are not the same thing.

topics to explore:
- Reward, value, utility. Which pair is easiest to conflate, and what goes wrong when you do?
- The reward function is chosen by a designer, the value function is learned. Which one carries the designer's intent?
- Utility comes from decision theory and describes preferences. Is it doing real work here, or borrowing authority from a different field?
- If the reward is not the goal, what would you have to observe to know what goal an agent actually has?

This is a primer. The chapter's argument about how rewards go wrong starts in the next sections, so do not run ahead into reward hacking here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.
