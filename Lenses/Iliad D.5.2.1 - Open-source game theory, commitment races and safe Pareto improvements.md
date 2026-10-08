---
id: 'b9d2dbec-fd01-4f82-b4f3-430d86929c6d'
title: "D.5.2.1 Open-source game theory, commitment races and safe Pareto improvements"
tldr: "How agents that can read each other's code can cooperate: FairBot and epsilon-grounded bots, why commitment races are a safety risk, and safe Pareto improvements."
summary_for_tutor: "Section 1 'Afternoon lecture' of Iliad worksheet D.5.2 Open-Source Game Theory. It covers FairBot (cooperates iff it can prove the opponent cooperates; two FairBots cooperate by Löb's theorem, from □(□C -> C) -> □C), epsilon-grounded bots (Oesterheld), conditional commitment, commitment races and entanglement, and safe Pareto improvements (the Pareto Meet Minimum, participation independence, entanglement-free SPI as a frontier idea). No numbered exercises."
authors:
  - Daniel C
  - Satya Benson
source_url: https://iliad-intensive.org/agency/open-source-game-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Afternoon lecture

**Open-source game theory.** When players can read each other's source code, cooperation becomes possible without repetition or prior trust. **FairBot** cooperates if and only if it can prove its opponent cooperates with it; two FairBots cooperate by Löb's theorem (from `□(□C -> C) -> □C`). It is unexploitable but brittle (it relies on a proof system and exact source). **Epsilon-grounded bots** (Oesterheld) replace proofs with simulation: cooperate unconditionally with small probability epsilon, else simulate the opponent and copy its move; this terminates almost surely, is a Nash equilibrium, and is robust. The unifying idea is *conditional commitment*: "I commit to X conditional on you committing to Y." Conditional makes it unexploitable; commitment makes it legible. FairBot is exactly this.

**Commitment races.** Among consequentialists who can commit, there is an incentive to commit *first*: the first mover can pick the point on the bargaining frontier best for itself and leave the responder to best-respond. So "the best response is not the best response", and agents race to commit before they even finish learning, risking incompatible lock-in or wasteful conflict (including threats and s-risks). Moving first "in logical time" is a genuine safety concern, which makes *avoiding* commitment races a safety goal. The deeper obstacle is *entanglement*: each agent optimizes against a distribution over the *counterfactual* programs the other might submit, so punishing a Pareto improvement means forgoing utility against the opponent's *actual* program; the incentive to make improvements is entangled with those counterfactuals, and this persists even with full conditional commitment.

**Safe Pareto improvements (SPI).** An SPI modifies the agents' default (conflict-prone) strategies so that *every* player is guaranteed at least as well off regardless of the opponent, a guaranteed weak Pareto improvement (Oesterheld-Conitzer; DiGiovanni-Clifton-Macé). In the open-source/program setting, each player individually prefers to use renegotiation-based SPIs, and the guaranteed floor is the *Pareto Meet Minimum* (your lowest efficient payoff), which is tight under a *participation-independence* assumption. That assumption can fail (agents may become hawkish when conflict is cheap), the "cheating" problem. *Entanglement-free SPI* (a research-frontier idea) restructures the interaction into two stages (exchange renegotiation programs, update on the actual one, then submit defaults), which breaks the entanglement and drops participation independence, at the cost of the tight floor. Teach the standard SPI result in full; present entanglement-free SPI briefly as the current frontier.
