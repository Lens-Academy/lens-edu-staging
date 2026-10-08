---
id: '1f549b8c-d6bc-444a-b6a8-63a3ff6509a7'
title: "D.1.1.1 Preferences over trajectories"
tldr: "A video on the rationality axioms behind reinforcement learning, then preferences over trajectories, why some preferences are problematic, and how coherence differs from selection."
summary_for_tutor: "This opens worksheet D.1.1 (preferences to rewards): an embedded video, the learning goals (preference versus utility versus reward), the overview, Section 1 Introduction, Section 2 'Preferences over trajectories' and Section 3 'When are preferences problematic?'. It defines trajectories H_n and H*, Definition 2.1 (preference relation), the derived indifference and strict preference, and discusses representability failures, self-defeat, money pumps and the notes on coherence versus selection. Keep the notation H*, the preference symbol, h. No exercises."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Video
source:: [[../video_transcripts/iliad-the-five-rules-of-rationality-behind-reinforcement-learning]]

#### Text
content::
:::callout {title="What you'll learn" tone="neutral"}

- Understand the difference between preferences, utility, and reward: preferences being a primary, largely uncontroversial notion, and utility and rewards being derived notions resting on specific assumptions.
- Be able to derive the relationship between various preference structures and rationality axioms.
- Critically assess alternative notions of rationality, and the consequences of dropping various classical decision theory assumptions.

:::

\## Overview

This note develops a short route from preferences over complete trajectories to expected utility, reward, and discount. We begin with preference relations on deterministic trajectories and explain how completeness and transitivity yield an ordinal utility representation. We then show how lotteries, together with the von Neumann–Morgenstern axioms, produce a cardinal utility over trajectories, and we clarify the distinction between ordinal preference utility and vNM utility. Next, following Bowling et al., we add a fifth temporal axiom that is necessary and sufficient for a recursive representation in terms of local rewards and discounting. Finally, we explain why reward is not unique: different reward functions can encode the same utility or the same preference ordering, affine changes of utility induce corresponding changes of reward, and potential-based shaping provides a canonical example of reward equivalence.

\## 1. Introduction

What does it mean for a system to have a goal? In sequential decision making, the object of evaluation is often not a single isolated choice or prize but a whole trajectory: a complete history of states, observations, actions, and consequences unfolding through time. Before asking how goals are achieved, it is worth asking a more basic question: what does it mean to prefer some trajectories over others, and what follows from that?

Recent work in reinforcement learning has revived this fundamental question, treating preferences over histories as primitive and asking what additional assumptions are needed before one can recover scalar reward functions. The present note provides an introduction to these ideas, which proceeds in three stages.

1. First, one asks for a numerical representation of how whole trajectories are ranked.
2. Second, once one allows lotteries over trajectories, one asks when these lotteries can be ranked by the expectation of that trajectory utility.
3. Third, one asks what additional requirements are needed in order to decompose this expected utility into rewards assigned at each time step.

The first and second steps are closely related to the classical theory developed by von Neumann and Morgenstern (von Neumann & Morgenstern 1944). The third asks what extra temporal structure is needed before utility over whole trajectories can be decomposed into stagewise rewards, following the line of work developed in modern reinforcement learning by Pitis 2019, Shakerinava & Ravanbakhsh 2022, and Bowling et al. 2023.

\## 2. Preferences over trajectories

Let ${\mathcal{O}}$ be a finite set of observations and ${\mathcal{A}}$ a finite set of actions. A one-step interaction is then given by $t=(o,a)\in {\mathcal{O}}\times {\mathcal{A}}$. For each $n\in\mathbb{N}_{\geq 0}$, define the space of trajectories of length $n$ by

$$
{\mathcal{H}}_{n} \coloneqq ({\mathcal{O}}\times {\mathcal{A}})^{n}.
$$

We write $\varepsilon$ for the unique trajectory of length $0$. The space of all *finite* trajectories is

$$
{\mathcal{H}}^{*} \coloneqq \bigcup_{n=0}^{\infty} {\mathcal{H}}_{n}.
$$

A typical element of ${\mathcal{H}}^{*}$ has the form $h=(o_{1},a_{1},o_{2},a_{2},\dots,o_{n},a_{n})$. We will keep the notation ${\mathcal{H}}^{*}$ for the set of all finite trajectories throughout.

:::callout {title="Definition" tone="blue"}

**Definition 2.1 (Preference).** A preference relation on ${\mathcal{H}}^{*}$ is a binary relation $\succcurlyeq$ where

$$
h \succcurlyeq h'
$$

means that trajectory $h$ is judged at least as good as trajectory $h'$.

:::

From $\succcurlyeq$ we derive the usual companion relations:

$$
h \sim h' \iff h \succcurlyeq h' \text{ and }h' \succcurlyeq h, \qquad h \succ h' \iff h \succcurlyeq h' \text{ and not }h' \succcurlyeq h.
$$

We call $\sim$ `indifference', as an agent has no reason to prefer one over the other.

At this point, $\succcurlyeq$ has no properties whatsoever. One may naturally wonder what kinds of properties it is reasonable to require of $\succcurlyeq$, and what follows from them — which is what we study in the next sections.

\## 3. When are preferences problematic?

Can a preference relation be intrinsically `bad'? The relevant concern here is whether it leads to some form of self-defeat, avoidable loss, or failure of coherent behaviour. The discussion in the decision-theory literature suggests at least three grades of concern.

1. *Representability failures.* A first and weakest concern is that a preference relation may fail to be representable in a convenient form. This does not, by itself, imply that the preference is irrational.

Representation failures may merely be inconvenient, but they become more significant when they are symptoms of deeper issues of the kinds described next (Aumann 1962; Fishburn 1970).
2. *Self-defeat and avoidable loss.* A more serious concern is that preferences may guide choice poorly — as judged by the agent's own interest. One important case is *static self-defeat*: choosing an option that is worse than another available one, or adopting a policy that is systematically improvable. A classic case of suboptimality is dominance: one option or policy dominates another when it is at least as good in every relevant respect and strictly better in some, so choosing the dominated option is a clear mistake (Kreps 1988; Mas-Colell et al. 1995). A second case is *diachronic self-defeat*: a plan that the agent endorses now is predictably undone later in a way that leaves the agent worse off overall.
3. *Vulnerability.* The most vivid coherence arguments show that a collection of individually acceptable choices can be combined into a guaranteed loss. Dutch-book arguments play this role for credences; money-pump arguments play the analogous role for preferences. The standard example is a preference cycle

$$
h_{1} \succ h_{2},\qquad h_{2} \succ h_{3},\qquad h_{3} \succ h_{1}.
$$

If the agent is willing to pay a small fee to move each time to a strictly preferred trajectory, then an adversary can guide it around the cycle and back to where it started, poorer than before (Gustafsson 2010). This is why intransitivity is usually regarded as a particularly severe pathology: it is not merely hard to represent, but also vulnerable to exploitation under natural trading assumptions.

:::callout {title="Note" tone="blue"}

**Coherence is not selection.**

It is useful to distinguish three kinds of formal results. A *representation result* says that if preferences satisfy certain axioms, then they can be written in a particular mathematical form; the vNM and Savage theorems being classical examples. A *coherence result* is different: it links violations of some constraint to a penalty such as a Dutch book, money pump, dynamic inconsistency, or dominated choice. Complete-class and admissibility theorems belong more naturally in this second family than in the first, since they characterize undominated decision rules rather than utility representations. A *selection result* is different again: it adds a story about some optimization process — such as market competition, evolution, or training dynamics — and argues that systems lacking a certain property tend to be selected against. In short, representation concerns *form*, coherence concerns *vulnerability or domination*, and selection concerns *survival under pressure*.

Note that representation, coherence, and selection arguments are related, but not identical. In general, a coherence argument is a within-agent claim: it says that if a single agent violates some structural constraint, then the agent is vulnerable to a penalty such as a money pump, Dutch book, or dominated choice. A selection argument is different: it asks whether agents lacking that property would tend to disappear under some broader optimization pressure, such as market competition, training dynamics, or evolutionary selection. A coherence result may help motivate a selection story, yet it does not by itself show that realistic environments actually select against the offending preference pattern. Similarly, a representational failure with no plausible selection story may still be mathematically interesting while being less central for explaining the structure of real agents.

For the purposes of this note, the key point is that these notions of badness do not all coincide. A preference can fail standard representation without being exploitably incoherent, and not every departure from expected utility is thereby problematic. Nevertheless, the axioms studied below are useful because — as we will see — they rule out several undesirable properties.

:::
