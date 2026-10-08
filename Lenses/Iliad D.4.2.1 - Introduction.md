---
id: 'f63bfd2c-9ba0-4d55-ab4d-dca44e912994'
title: "D.4.2.1 Introduction"
tldr: "The abstract, contents and introduction: why optimization is local entropy reduction and why an embedded agent's knowledge is a physical resource."
summary_for_tutor: "Abstract, table of contents and Section 1 of Iliad worksheet D.4.2 Optimization and Thermodynamics. Two claims: optimization is local entropy reduction (concentrating probability mass), and for embedded agents knowledge must be stored physically, unlike the exogenous distribution of a dualistic agent. Also explains the structure of the notes (Sections 2-9, Appendices A and B). No exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Abstract.** A useful characterization of powerful agents is that they reliably steer the world into a narrow region of outcome space, a region that would be extremely unlikely to arise under any random process. These notes develop this picture from first principles, pursuing three successive aims: to make the notion of "steering into a narrow region" mathematically precise, to establish the thermodynamic constraints that physics imposes on any process realizing it, and to resolve a conceptual gap that the classical formalism leaves open. We first characterize an optimizer behaviorally, as the *cause* of a convergent attractor: a physical entity whose presence drives the system it acts upon, from a broad range of initial conditions and despite perturbations, into a narrow target set, so that conditioning on the optimizer collapses an observer's uncertainty about the final state that system reaches. We argue that even an observer concerned solely with prediction possesses an objective, information-theoretic reason to single out such optimizers, establishing optimization as an observer-independent feature of the world rather than a stance projected onto it; translated into information theory, optimization is local entropy reduction in the system being acted upon. We then provide thermodynamic foundations for the analysis of such processes: the reversibility of microscopic dynamics, together with the second law of thermodynamics, forbids global entropy reduction, so an embedded optimizer must compensate for every local reduction within a consistent global accounting. We derive the second law from reversibility in a minimal Markov-chain setting, classify the three ways in which an agent can reduce the entropy of a subsystem while respecting information conservation, and quantify the third of these channels through the Touchette–Lloyd theorem (entropy reduction beyond a "blind" baseline must be paid for in mutual information between the agent and the environment), developed in an appendix. A self-contained toy thermodynamics built out of biased coins (Wentworth's generalized heat engine), in which every step of the requisite "bookkeeping" is elementary, is developed in a separate appendix. Finally, we confront a conceptual gap: the standard Gibbs–Shannon entropy is defined relative to a subjective probability distribution that the formalism treats as exogenous, making "capacity to optimize" observer-dependent and leaving the classical tools inapplicable to the far-from-equilibrium, information-bearing states of which agents are composed. Algorithmic thermodynamics, due to Ebtekar and Hutter, replaces the subjective distribution with Kolmogorov complexity, yielding a second law that applies to individual physical states. Under this reframing, an embedded agent's probabilistic knowledge becomes an endogenous, physically encoded quantity—the algorithmic mutual information between the agent's memory and the environment—which is precisely the resource the agent expends when it optimizes. We thus establish that agents with greater knowledge of the world possess correspondingly greater capacity to act upon it, with the exchange rate between the two set by thermodynamics.

**Contents**

- 1. Introduction: the role of thermodynamics in agent foundations
- 2. Theoretical foundations: probability, entropy, and information
  - 2.1 Random variables and notation
  - 2.2 Entropy
  - 2.3 The coding interpretation
  - 2.4 Joint and conditional entropy, and mutual information
  - 2.5 Divergence and two fundamental inequalities
- 3. Characterizing optimization
  - 3.1 Two notions of optimization and their relationship
  - 3.2 Optimizers and convergent attractors
  - 3.3 Optimization as entropy reduction
  - 3.4 The predictive value of optimizers
  - 3.5 The observer-independence of optimization
- 4. Reversibility and the second law
  - 4.1 The reversibility of microscopic physics
  - 4.2 The incompatibility of global funneling with reversibility
  - 4.3 Coarse-graining and the emergence of probability
  - 4.4 The second law of thermodynamics
  - 4.5 The scope and limitations of the second law
- 5. Three types of optimization under information conservation
  - 5.1 The bookkeeping problem
  - 5.2 Type 1: transfer of entropy into the environment as waste heat
  - 5.3 Type 2: absorption of entropy into the agent's memory through measurement
  - 5.4 Type 3: expenditure of pre-existing mutual information
  - 5.5 A reinterpretation of Maxwell's demon, and a synthesis of the three channels
- 6. Limitations of subjective entropy
  - 6.1 Entropy as a measure of optimization capacity
  - 6.2 The exogenous status of the reference distribution
  - 6.3 Three failure modes of the ensemble formalism
  - 6.4 The demon's capacity as the central case for agent foundations
- 7. Algorithmic thermodynamics
  - 7.1 Kolmogorov complexity
  - 7.2 Justification of $$K$$ as an entropy measure
  - 7.3 The algorithmic second law
  - 7.4 An exact analysis of Maxwell's demon
- 8. Knowledge as a physical resource: optimization for embedded agents
  - 8.1 From exogenous to endogenous knowledge
  - 8.2 Refinements of the three channels via universal computation
  - 8.3 Dissolution of the apparent subjectivity
  - 8.4 Thermodynamic implications for optimizing systems
- 9. Summary and conclusions
- A. A thermodynamics of biased coins: the generalized heat engine
  - A.1 The designer's viewpoint
  - A.2 Specification of the model: coins, transformations, and conservation laws
  - A.3 Work extraction as a compression problem
  - A.4 The impossibility of work extraction from a single heat bath
  - A.5 Work extraction from two heat baths at different temperatures
  - A.6 Lessons from the toy world
- B. The informational cost of steering: the Touchette–Lloyd theorem
  - B.1 From optimization to modeling: the motivating question
  - B.2 The formal setup: environments, actions, and policies
  - B.3 Blind and sighted policies
  - B.4 A worked example: the guessing game under blind play
  - B.5 The guessing game under sighted play
  - B.6 Mutual information as a measure of sightedness
  - B.7 Statement of the theorem
  - B.8 Limitations of the theorem
- Sources and further reading

\## 1. Introduction: the role of thermodynamics in agent foundations

Agent foundations may be understood as the search for *robust concepts* (sometimes called "true names") for notions such as optimization, goals, world models, and embeddedness, where a robust concept is one that retains its meaning under extreme optimization pressure and for agents far more capable than any yet constructed. These notes pursue the true name of *optimization* along the descriptive route: rather than beginning inside an idealized rational agent, equipped with beliefs, preferences, and an expected-utility criterion, we begin from the physical world itself. This raises fundamental questions: What kind of process can reliably steer the world into a narrow target? And what thermodynamic cost does physics impose on such a process?

Thermodynamics supplies the answer to the second of these questions, for two reasons that we state at the outset and that the remainder of these notes develops systematically.

**Optimization as Local Entropy Reduction.** An optimizer concentrates probability mass: out of the many configurations the world could occupy, it funnels a broad set of possibilities down to a few. Concentrating probability mass, however, is precisely the reduction of uncertainty, and the reduction of uncertainty is the reduction of entropy (Section 2 makes this correspondence precise). This identification is not an analogy: it brings the full machinery of entropy (the second law, fluctuation theorems, the cost of erasing a bit) to bear directly on optimization, and the modern form of that machinery, *stochastic thermodynamics*, holds arbitrarily far from equilibrium. Consequently, physics constrains the shape of any optimizer that could actually be built.

**The Physical Currency of Knowledge for Embedded Agents.** We distinguish two idealized pictures of agency. A *dualistic* agent sits outside the world it acts upon, in the manner of a player at a console: its inputs and outputs are sharply delimited, and "what it knows" is a free parameter, a distribution supplied exogenously by the analyst. An *embedded* agent, in contrast, is part of the world it acts upon, so its knowledge is not free: it must be stored in some physical substrate, in a brain or a memory register composed of the same atoms as everything else. One of the principal conclusions of these notes is that once entropy is defined correctly (algorithmically, as a property of an individual state rather than of a subjective ensemble), an agent's knowledge of its environment becomes an objective physical quantity—the mutual information between its memory and the environment—and that this quantity is exactly the budget available to be spent on optimization.

We close this introduction with a remark on the nature of the contribution and its intended audience. For readers with a background in physics, the value of these notes lies primarily in translation rather than in new theorems: recasting familiar thermodynamic facts in information-theoretic language ties them to agent-foundations notions such as world models, optimization power, and the limits on embedded agents. For readers without such a background, the notes are self-contained: every thermodynamic idea is defined here in information-theoretic terms, no statistical mechanics is assumed, and the only prerequisite is familiarity with elementary discrete probability.

**Structure of the Notes.**  Section 2 develops the probabilistic and information-theoretic apparatus on which all later sections depend, introducing entropy, mutual information, and divergence together with the coding interpretations that give these quantities operational meaning. Section 3 then addresses the characterization of optimization: we characterize an optimizer behaviorally, as a physical entity that drives the system it acts upon, from a broad range of initial conditions and robustly to perturbation, into a narrow target (a convergent attractor); we translate this characterization into entropy reduction; and we argue that any observer concerned with prediction possesses an objective, information-theoretic reason to attend to optimizers, independently of who is watching. Section 4 confronts this picture with the reversibility of microscopic physics and derives the second law of thermodynamics, with full proof, in a minimal coarse-grained setting. Building on this foundation, Section 5 classifies the three ways in which an embedded agent can reduce the entropy of a subsystem while respecting global information conservation: exporting it into the environment, absorbing it into memory through measurement, or expending pre-existing mutual information with the subsystem. Section 6 exposes a conceptual problem at the heart of the standard formalism, namely that entropy, as conventionally defined, depends on a subjective probability distribution supplied from outside the physics. Motivated by this limitation, Section 7 develops the resolution, algorithmic thermodynamics: Kolmogorov complexity as entropy, the algorithmic second law, and an exact analysis of Maxwell's demon, with emphasis throughout on how an objective notion of entropy dissolves the subjectivity problem. Section 8 synthesizes these results into an account of embedded agency in which knowledge figures as an endogenous physical resource, and Section 9 collects the principal conclusions. Appendix A develops, in parallel to the main line of argument, a self-contained toy thermodynamics built out of biased coins (Wentworth's generalized heat engine), in which the analogues of heat, work, energy conservation, and the impossibility of perpetual motion can all be verified by hand; the main text refers to it wherever a concrete blind-policy example is instructive. Finally, Appendix B develops the Touchette–Lloyd theorem, which makes the third channel quantitative: the entropy reduction an agent can achieve beyond a blind baseline is bounded by the mutual information between its action and the environment, with fully worked examples.
