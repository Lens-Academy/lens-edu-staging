---
id: 'c09dfa9e-cbd3-452e-8da3-2c14b1c9e9e9'
title: "D.6.1 Introduction and setup"
tldr: "Introduces instrumental convergence and power-seeking, the central claim about keeping options open, and the setup of rewardless MDPs and reward functions used throughout the worksheet."
summary_for_tutor: "Opening part of Iliad worksheet D.6 Instrumental Convergence: prerequisites, learning outcomes, the question of whether a trained agent seeks power, and the central claim that for most reward functions keeping more options open is likelier. Contains Definition 0.1 (rewardless MDP, policy, indicator vector e_s) and Definition 0.2 (reward function as a vector in R^d); the discount factor gamma is fixed once. Keep the three phrases to formalise: majority of reward functions, suitable decision rule, keeping more options open. The lens text also contains the day schedule and facilitator notes."
authors:
  - "Leon Lang (ILIAD), based on work by Alex Turner et al."
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Prerequisites.**

A basic familiarity with reinforcement learning is sufficient.

:::callout {title="What you'll learn" tone="neutral"}

The students understand the proofs for power-seeking tendencies based on Alex Turner's work, and can critically examine the weaknesses and implications of this work. This work is important since power-seeking behavior is one of the most severe risks that AI may pose, and this may be the most rigorous work to date establishing it under clear assumptions and definitions. The goals are achieved through an initial presentation, by working through an exercise sheet, and by reading and discussing the original papers.

:::

%% Facilitator logistics (hidden from learners):
\## Roadmap for today

Outline of the day:

- 10:00 – 11:00: Presentation
- 11:15 – 13:15: Solving of exercises
- 14:15 – 15:15: Solving more exercises
- 15:30 – 16:15: Reading
  - One of the three main papers is read by everyone.
- 16:15 – 16:45: Discussion
  - Participants who read different papers discuss together.
- 17:00 – 17:15: Brainstorming of limitations / critiques / ideas and theoretical/empirical hypotheses
- 17:15 – 17:45: Students present and discuss their ideas

In the exercises, the participants learn to understand one model of the reward function distribution, decision rule, and conceptualization of "power" in detail, and learn the mathematical arguments connecting them in detail. This is useful as learning one model in detail helps to quickly understand all variations that are discussed in many of Turner's papers.

The readings teach the participants variations of the concepts and results, which may help them to appreciate the breadth and limitations of the results better.

Finally, the brainstorming of limitations and ideas gets participants into a critical mindset and makes them think through whether the theoretical notions of power capture what we mean, and how to go beyond. This is important since the applicability of the results to actual AI training processes is questioned by many people in the community.

I think the setup I chose (together with Claude) in the exercise sheet has some advantages compared to Turner's original treatment of the results:

- The use of an invariant measure avoids "orbit counting" and grounds everything in the more justified notion of probabilities of various outcomes.
- We work with *a subgroup* of the symmetric group, and thus avoid the unjustified assumption that the measure on reward functions is invariant under arbitrary symmetries (which it obviously isn't!)
- The notion of a dynamics embedding grounds the notion of "more options" into actual MDP dynamics.
- The use of score functions allows us to achieve a power-seeking result for one-sided dynamics embeddings and under non-trivial discount factors.

Overall, I think this makes the results much more interpretable, and I would thus not recommend to go back to the framing of any of Turner's particular papers.
%%

\## Introduction

Suppose we build an AI and give it a goal. A long-standing worry — *instrumental convergence* — holds that for a very wide range of encoded objectives, a sufficiently capable agent converges on the same handful of intermediate strategies, because they are useful almost regardless of the final goal: acquire resources, stay operational, and keep one's options open (Omohundro 2008; Bostrom 2014). We call the drive towards them **seeking power**, where "power" means *the ability to achieve a wide range of goals* — being in a position from which many futures remain reachable.

This worksheet attempts to model such claims mathematically and establish proofs for them. We study the following question.

:::callout {title="Note" tone="blue"}

**The question.** We train an AI in some environment (a Markov decision process) to perform well according to a reward function. **Will it seek power, or not?**

:::

The central claim we will build up to is the following.

> *Under many suitable decision rules for how to act, and for the majority of reward functions, keeping more options open is the likelier outcome than keeping fewer options open.*

"Keeping more options open" is then the operationalization for "seeking power", which can also be shown to connect to the ability to achieve a wide variety of goals. This is a statement about a *tendency*, not about *every* goal. The results we prove are the core cases from (Turner et al. 2021; Turner & Tadepalli 2022), with an application to *trained* agents in (Krakovna & Kram'ar 2023) and a measure-theoretic re-examination of "most goals" in (Jacek 2023). These works provide many generalizations of the claims in this worksheet.

Making the central claim precise requires formalising three phrases. The rest of the worksheet is organised around them and then proving the result:

1. *for the majority of reward functions*: How do we count reward functions?
2. *a suitable decision rule*: Which ways of turning a reward function into behaviour are covered (maximization is only one)?
3. *keeping more options open*: How do we measure that one situation leaves more achievable than another?

We formalise all three and then prove the resulting theorems. The setup below fixes the environment; the three numbered sections that follow take up points (1), (2), and (3) in turn.

\## Setup

Throughout the worksheet we fix a discount factor $$\gamma \in (0,1)$$ once and for all.

\### The environment

We separate the *environment* (its states and dynamics) from the *goal* (a reward function) since we want to make claims about the whole set of reward functions.

:::callout {title="Definition" tone="blue"}

**Definition 0.1 (Rewardless MDP).** A **rewardless Markov decision process (MDP)** is a tuple $$\langle {\mathcal{S}}, {\mathcal{A}}, T\rangle$$ consisting of

- a finite **state space** $${\mathcal{S}}$$, with $$d := |{\mathcal{S}}|$$ states;
- a finite **action space** $${\mathcal{A}}$$;
- a **transition function** $$T : {\mathcal{S}} \times {\mathcal{A}} \to \Delta{\mathcal{S}}$$, where $$\Delta X$$ denotes the set of probability distributions over a finite set $$X$$. Taking action $$a$$ in state $$s$$ moves the agent to state $$s'$$ with probability $$T(s' \mid s, a)$$.

A **policy** $$\pi : {\mathcal{S}} \to {\mathcal{A}}$$ specifies which action the agent takes in each state.[^1] We write $$e_{s} \in {\mathbb{R}}^{d}$$ for the indicator vector of state $$s$$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 0.2 (Reward function).** A **reward function** assigns a real number $$r(s)$$ to each state $$s\in{\mathcal{S}}$$. Since $${\mathcal{S}}$$ has $$d$$ elements, a reward function is simply a vector

$$
r \;\in\; {\mathbb{R}}^{d},
$$

so we take the **space of goals to be all of $${\mathbb{R}}^{d}$$**.

:::

[^1]: We restrict to deterministic policies since many of our analyses expect a finite set of policies.
