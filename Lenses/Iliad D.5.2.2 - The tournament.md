---
id: '386a133b-24ae-43fa-9303-e318f763bba0'
title: "D.5.2.2 The tournament"
tldr: "The rules of the Open-Source Prisoner's Dilemma tournament: payoffs, the two leagues, how to submit a bot, how circular queries resolve, scoring, and what a good submission looks like."
summary_for_tutor: "Sections 2 'The tournament' and 3 'Learn more' of Iliad worksheet D.5.2 Open-Source Game Theory. Payoffs: (C,C) 3 each, (D,D) 1 each, defector 5 and cooperator 0, so T > R > P > S and 2R > T + S. League A is one-shot with source access (opp.move_against, opp.source); League B is iterated with history only and about 2% noise. Circular queries are resolved as provability fixed points, with a no-wishful-thinking default to D. Keep the Agent class signatures and the reference bot names. The student's task is to design a bot and write a short rationale; let them design it before suggesting strategies."
authors:
  - Daniel C
  - Satya Benson
source_url: https://iliad-intensive.org/agency/open-source-game-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. The tournament

Full rules are in the [tournament handout](https://iliad.au.pe/sessions/decision-theory/handout.html); the structure is summarized here so the day can be run from this document.

**The game.** The one-shot Prisoner's Dilemma, with the twist that your program can read the opponent's program before deciding (source is open). Payoffs (you, them): mutual cooperation `(C,C)` gives 3 each; mutual defection `(D,D)` gives 1 each; defecting against a cooperator gives 5 to the defector and 0 to the cooperated. This satisfies `T > R > P > S` (5 > 3 > 1 > 0) and `2R > T + S` (6 > 5).

**Two leagues.**

- *League A (one-shot, open source).* Bots see the opponent's source and decide once. This is the program-equilibrium / Löbian-cooperation setting.
- *League B (iterated, history only).* Bots see the move history over a hidden number of rounds (around 100-200) and cannot read source. This is the classic reciprocity setting (Tit-for-Tat and relatives).

**Submitting a bot.** A submission may be in any form (real Python, pseudocode, or a careful English description) plus a short design rationale explaining the decision-theoretic approach; an LLM compiles it into the canonical `Agent` class:

```
class Agent:
def move_oneshot(self, opp) -> Move:                  # League A
def move_iterated(self, my_hist, opp_hist, t) -> Move: # League B
```

In League A a bot may query: `opp.move_against(SELF)` (the opponent's move against you), `opp.move_against(DEFECT_BOT)`, `opp.move_against(COOP_BOT)`, and `opp.source` (the opponent's canonical source). League B provides only the two history lists and the round index `t`.

**How circular queries resolve.** Two source-reading bots can each ask "what does the other do against me?", which is circular. Rather than simulate the recursion, the engine treats every "what does the opponent do against X?" query as a *provability* question and computes the fixed point directly, the same Löbian move that lets two FairBots cooperate. When no stable resolution exists, it applies a *no-wishful-thinking* rule: if cooperation cannot be established, default to D.

**Reference bots.** League A: CooperateBot, DefectBot, FairBot, PrudentBot, CliqueBot, RandomBot. League B: AllC, AllD, Random, TitForTat, GrimTrigger, GenerousTitForTat, Pavlov, TitForTwoTats. These seed the field and give students targets to beat or cooperate with.

**Scoring.** Round-robin: every bot plays every other bot, including a copy of itself, and ranking is by total points accumulated across all matchups (not head-to-head wins). League B matches add about 2% move-flip noise and a randomized hidden length, so brittle strategies are penalized.

**What good looks like.** A strong submission embodies a clear decision-theoretic concept (commitment, transparency, the limits of self-reference, functional decision theory) and explains it, rather than chasing the leaderboard. The standout lesson is usually that FairBot-style conditional cooperation beats both naive cooperation (exploited) and naive defection (misses mutual cooperation) in League A, while robustness to noise dominates in League B.

\## 3. Learn more

**Multi-agent and open-source game theory.** The [annotated program-equilibrium bibliography](https://www.andrew.cmu.edu/user/coesterh/AnnotatedProgEqBibliography.html) (Oesterheld); the [epsilon-grounded FairBot paper](https://arxiv.org/abs/2412.14570); [When would AGIs engage in conflict?](https://www.lesswrong.com/posts/cLDcKgvM6KxBhqhGq/when-would-agis-engage-in-conflict); the safe-Pareto-improvement papers (Oesterheld-Conitzer; [DiGiovanni-Clifton-Macé](https://arxiv.org/abs/2403.05103)). Andrew Critch's work on cooperative and uncooperative institution design is a good, pedagogically simple source for further exercises.

**Frontier.** Logical updatelessness and logical time; UDT 2 and policy-selection fixes; bargaining and notions of fairness (the Nash bargaining solution and the "zoo" of coalitional structures); entanglement-free safe Pareto improvements; reflective oracles and program equilibrium as a single picture.
