---
id: 'a090de40-ed87-4a50-bdd5-fad3d48b760a'
title: "D.5.1.1 Overview and prerequisites"
tldr: "Prerequisites, what the day covers (CDT, EDT, FDT, UDT, open-source game theory, the tournament), why decision theory matters for safety, and a one-hour fast-track path."
summary_for_tutor: "Opening of Iliad worksheet D.5.1 Decision Theory: prerequisites, the What/Why/How learning outcomes, the slide decks and tournament handout, and the 'Fast-track' list (about one hour: read the four decision theories and the multi-agent layer, the FDT paper chapters 1-3, skim 'Towards a new decision theory', write a one-paragraph bot). Key framing: for an embedded agent the action is a fact about the world, so counterfactuals must be constructed. No exercises."
authors:
  - Daniel C
  - Satya Benson
source_url: https://iliad-intensive.org/agency/decision-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Prerequisites

- Basic probability and expected value; comfort reading pseudocode.
- Helpful but not required: Löb's theorem (covered on the Agent Foundations day; it underlies FairBot and the tournament's cooperation results) and a first acquaintance with Bayesian networks and the causal do-operator (re-introduced briefly in the lecture).

:::callout {title="What you'll learn" tone="neutral"}

**(What.)** By the end of the day, students can explain why decision theory is hard for an *embedded* agent (its action is just another fact about the world, so counterfactuals must be constructed, not read off) and can state the four main theories and what each gets right and wrong: CDT (intervene), EDT (condition), FDT (choose your decision function's output), and UDT 1.0/1.1 (act on the policy you would have committed to in advance). They can work the canonical problems (Newcomb, smoking lesion, counterfactual mugging, twin prisoner's dilemma) and say which theory each one separates. They understand the multi-agent layer: open-source game theory and Löbian cooperation (FairBot), commitment races, and safe Pareto improvements. They apply all of this by designing and submitting a bot to the open-source Prisoner's Dilemma tournament.

**(Why.)** To make a superintelligence safe we will likely prove safety properties under assumptions about *how the agent decides*. Decision theory is a *reflectively-consistent degree of freedom*: unlike a mistaken factual belief, a bad decision theory is not automatically corrected as an agent gets smarter, so a load-bearing assumption ("the agent is CDT") can silently fail if the agent self-modifies. The multi-agent failures (commitment races, conflict, exploitable cooperation) are direct AI-safety concerns, and safe Pareto improvements are one of the few constructive tools against them.

**(How.)** A morning lecture builds the theories in order (CDT/EDT to FDT to UDT), motivated by the problems that break each one. A two-hour reading and discussion block has students wrestle with the primary sources and a transparency-and-cooperation prompt. An afternoon lecture moves to the multi-agent setting (open-source game theory, commitment races, safe Pareto improvements). The day ends with a programming tournament that operationalizes program equilibrium and Löbian cooperation.

:::

\## 2. Content

Slides: Deck I (Decision Theory: CDT to UDT) and Deck II (Open-Source Game Theory, Commitment Races, and Safe Pareto Improvements), linked from the [Decision Theory session page](https://iliad.au.pe/sessions/decision-theory/participant-guide.html). Tournament handout: [Open-Source Prisoner's Dilemma Tournament](https://iliad.au.pe/sessions/decision-theory/handout.html).

\### 2.1 Fast-track

To get the core in about an hour, or to catch up after missing the day:

- Read "The four decision theories" and "The multi-agent layer" below.
- Read the [FDT paper](https://arxiv.org/abs/1710.05060) (at least chapters 1-3) for the FDT/UDT picture, and skim [Towards a new decision theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory).
- Read the tournament handout and write a one-paragraph bot (even "cooperate only if the opponent provably cooperates with me" is enough to engage with the ideas).
