---
title: "Reinforcement Learning"
author:
  - "Markov Grey"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/specification-gaming/reinforcement-learning/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090619456}@@

%%
Add discussion note here:

...

%%++}

Reinforcement learning teaches AI agents through trial and error to maximize a reward, but if what we reward it for doesn't perfectly match what we want, the AI might simply increase the score instead of doing the real task.

---

> **Warning:** This is meant as a recap. If you are already familiar with the basics you can skip directly to the next section.

The section provides a succinct reminder of several concepts in reinforcement learning (RL). It also disambiguates various often conflated terms such as rewards, values and utilities. The section ends with a discussion around distinguishing the concept of objectives that a reinforcement learning system might pursue from what it is being rewarded for. 

## Primer

**Definition: Reinforcement Learning (RL)** — Reinforcement Learning (RL) focuses on developing agents that can learn from interactive experiences. RL is based on the concept of an agent learning through interaction with an environment and altering its behavior based on the feedback it receives through rewards after each action.

{>>{"author":"Elias's AI","timestamp":1783776608387}@@removed embedded iframe: https://www.youtube-nocookie.com/embed/jwSbzNHGflM<<}

*Video 6.1: Optional video showcasing robotic hand trained using reinforcement learning.*

Some examples of real-world applications of RL include:

- **Robotic systems**: RL has been applied to tasks such as controlling physical robots in real-time, and enabling them to learn more complicated movements. RL can enable robotic systems to learn complex tasks and adapt to changing environments.

- **Recommender Systems**: RL can be applied to recommender systems, which interact with billions of users and aim to provide personalized recommendations. RL algorithms can learn to optimize the recommendation policy based on user feedback and improve the overall user experience.

- **Game playing systems:** In the early 2010s RL-based systems started to beat humans at a few very simple Atari games, like Pong and Breakout. Over the years, there have been many models that have utilized RL to defeat world masters in both board and video games. These include models like AlphaGo ([DeepMind, 2016](https://www.deepmind.com/research/highlighted-research/alphago)), AlphaZero ([DeepMind, 2018](https://www.deepmind.com/blog/alphazero-shedding-new-light-on-chess-shogi-and-go)), OpenAI Five ([OpenAI, 2019](https://openai.com/research/openai-five-defeats-dota-2-world-champions)), AlphaStar ([DeepMind, 2019](https://www.deepmind.com/blog/alphastar-mastering-the-real-time-strategy-game-starcraft-ii)), MuZero ([DeepMind, 2020](https://www.deepmind.com/blog/muzero-mastering-go-chess-shogi-and-atari-without-rules)) and EfficientZero ([Ye et al., 2021](https://arxiv.org/abs/2111.00210)).

RL is different from supervised learning as it begins with a high-level description of "what" to do but allows the agent to experiment and learn from experience the best "how". In RL, the agent learns through interaction with an environment and receives feedback in the form of rewards or punishments based on its actions. RL is focused on learning a set of rules that recommend the best action to take in a given state to maximize long-term rewards. In contrast, supervised learning typically involves learning from explicitly provided labels or correct answers for each input.

## Core Loop

The overall functioning of RL is relatively straightforward. The two main components are the agent itself, and the environment within which the agent lives and operates. At each time step :

1. The agent then takes some action $a_t$
2. The environment state $s_t$ changes depending upon the action $a_t$.
3. The environment then outputs an observation $o_t$ and a reward $r_t$.

A history is the sequence of past observations, actions and rewards that have been taken up until time $t: h_t = (a_1, o_1, r_1, ..., a_t, o_t, r_t)$. The state of the world is generally some function of the history: $s_t = f(h_t)$. The World State is the full true state of the world used to determine how the world generates the next observation and reward. The agent might either get the entire world state as an observation $o_t$, or some partial subset.

The world goes from one state $s_t$ to the next $s_(t+1)$ either based on natural environmental dynamics, or the agent's actions. State transitions can be both deterministic or stochastic.

This loop continues until a terminal condition is reached or can run indefinitely. Following is a diagram that succinctly captures the RL process:

![Figure 6.1](https://ai-safety-atlas.com/_astro/8372cd73478c24e48502d91c72166b8c031212d592f06c15e44f0e271669e062.BlTgyBee_26inIN.webp)

*Figure 6.1: ([Brunskill, 2022](https://web.stanford.edu/class/archive/cs/cs234/cs234.1224/))*

## Policies 

**Definition: Reinforcement Learning Policy** — A policy helps the agent determine what action to take once it has received an observation. It is a function mapping from states to actions specifying what action to take in each state. Policies can be both deterministic or stochastic.

The goal of RL is to learn a policy (often denoted by $pi$) that recommends the best action to take at any given moment in order to maximize total cumulative reward over time. The policy defines the mapping from states to actions and guides the agent's decision-making process.

$$
pi: S -> A
$$

A policy can be either deterministic or stochastic. A deterministic policy directly maps each state $s_t$ to a specific action $a_t$ and is usually denoted by $mu$. In contrast, a stochastic policy assigns a probability distribution over actions for each state. Stochastic policies usually denoted by $pi$.

Deterministic policy: $a_t = mu(s_t)$

Stochastic policy: $pi(a|s) = P(a_t = a|s_t=s)$

In Deep RL policies are function maps that are learned during the training process. They depend on the set of learned parameters of a neural network (e.g. the weights and biases). These parameters are often denoted with subscripts on the policy equations using either $theta$ or $phi$. So the deterministic policy over the parameters of a neural network is written $a_t = mu_theta(s_t)$, and the stochastic equivalent is $a_t tilde pi_theta(dot.c | s_t)$

An optimal policy maximizes the expected cumulative reward over time. The agent learns from experience and adjusts its policy based on the feedback it receives from the environment in the form of rewards or punishments.

In order to determine whether an action is better than another, the actions (or the state-action pairs) need to be evaluated somehow. There are two different ways to look at which action to take: the immediate rewards (determined by reward function) and the long term cumulative rewards (determined by the action-value function). Both of these greatly influence the types of policies learned by the agent, and therefore also the actions that the agent takes. The following section explores and clarifies the concept of rewards in greater depth.

## Reward

**Definition: Reward** — Reward refers to any signal or feedback mechanism used to guide the learning process and optimize the behavior of the model.

The reward signal from the environment is a number that tells the agent how good or bad the current world state is. It is a way to provide an evaluation or measure of performance for the model's outputs or actions. The reward can be defined based on a specific task or objective, such as maximizing a score in a game or achieving a desired outcome in a real-world scenario. The training process for RL involves optimizing the model's parameters to maximize the expected reward. The model learns to generate actions or outputs that are more likely to receive higher rewards, leading to improved performance over time. Where does the reward come from? It is generated through a reward function.

**Definition: Reward function** — A reward function defines the goal or objective in a reinforcement learning problem. It maps perceived states or state-action pairs of the environment to a single number.

$$
R: (S times A) -> RR ; r_t = R(s_t, a_t)
$$

The reward function provides immediate feedback to the agent, indicating the goodness or badness of a particular state or action. It is a mathematical function that maps the state-action pairs of an agent's environment to a scalar value, representing the desirability of being in that state and taking that action. It provides a measure of immediate feedback to the agent, indicating how well it is performing at each step.

**Reward Functions vs. Value Functions**

The reward indicates the immediate desirability of states or actions, while a value function represents the long-term desirability of states, taking into account future rewards and states. The value is the expected return if you start in a state or state-action pair, and then act according to a particular policy forever after. 

There are many different ways of choosing value functions. They can also be discounted over time, i.e. future rewards are worth less by some factor .

Following is one simple formulation is the discounted sum of future rewards given some policy. The cumulative discounted rewards are given by:

$$
R = r_t + gamma r_(t+1) + gamma^2 r_(t+2) + ... = sum_(t=0)^infinity gamma^t r_t
$$

And the value of acting according to this policy is given by:

$$
V^pi(s_t = s) = E_pi(R | s_t = s)
$$

**Reward Functions vs. Utility Functions**

It is also worth distinguishing the concept of utility from reward and value. A reward function is typically used in the context of RL to guide the agent's learning process and behavior. In contrast, a utility function is more general and captures the agent's subjective preferences or satisfaction, allowing for comparisons and trade-offs between different world states. Utility functions are a concept that is used more in the field of decision theory and agent foundations work.
