---
id: '33b894b3-7b31-41da-9606-dc284ec57b22'
slug: alignment-theory-of-deep-learning
title: "Alignment Theory of Deep Learning"
description: "Why does deep learning work, and what does the answer mean for alignment? A one-week slice of the Iliad Intensive: singular learning theory, training dynamics, and data attribution."
partner-url: https://www.iliad.ac/
---
%% Placeholder course so that applications can be collected for the October 5, 2026 intensive. The course is not listed anywhere; the marketing card for Alignment Theory of Deep Learning maps this slug to its cohorts. Replace the placeholder module with the real modules and meetings before the course starts. %%

%% First build pass: Claude (cc:3f2b9169) for Lauren, 2026-09-23. Status and open questions: lens repo docs/plans/20260923-iliad-slice-status.plain.md.

Source curriculum: Iliad Intensive (https://iliad-intensive.org/, repo iliad-team/iliad-intensive at d2792cb, 2026-09-22), CC BY 4.0, licensed to Principles of Intelligence. Day selection is Leon Lang's (Iliad curriculum lead) proposed first week, relayed by Mark in #course-design "Two iliad weeks test": A.1, then B.2, B.3, B.4, B.5. Luc (0-internal, 2026-08-17): Iliad is fine with us using the curriculum with attribution but does not want it branded as an Iliad course, so no partner-name or partner-logo here.

Each day is one Iliad day, cut to the authors' own fast-track routes where they give one. Landing page promise (lens-platform web_frontend/src/pages/courses/theory-of-deep-learning/content.tsx, Mark, 2026-09-19): 5 units, about 5 hours each including the group session. %%

%%
Target audience (copied from the landing page personas, not newly written):
- Mathematicians and physicists: strong quantitative background, want to see where it applies in AI alignment research.
- Theoretical computer scientists: want a rigorous account of learning, generalization, and inductive bias.
- ML engineers who want the theory: train models already, want to understand loss landscapes, implicit bias, and why training runs behave as they do.
- Aspiring alignment researchers: considering agendas such as developmental interpretability or singular learning theory, want the foundations before applying to a fellowship.
Prerequisites stated on the landing page: linear algebra to eigenvalues and SVD; multivariable calculus with gradients, Hessians, Taylor expansion; probability with Bayes' rule and multivariate normals; how neural networks are trained. An introductory AI safety course is recommended.

Value prop (landing page, verbatim): "Deep learning works far better than classical theory says it should. ... This course studies the mathematics that tries to explain why, and asks what those explanations mean for aligning the systems we train." "This is the theory track, not the engineering track. You will do derivations and exercises by hand more often than you will write code."

Links:
- Landing page: https://lensacademy.org/courses/theory-of-deep-learning
- Source: https://iliad-intensive.org/
%%

application-survey:: [[../surveys/Application Form]]

%%
Day 1 goals (Leon Lang's A.1 outcomes, verbatim):
- understand the basic decomposition of risks into AI misalignment, misuse, power grabs, and others;
- can explain different alignment targets like coherent extrapolated volition, intent alignment, or AI that follows a constitution;
- can reason about training stories and outer and inner (mis)alignment, challenges to these notions, and the relationship to inductive biases;
- are aware of discussions on whether AI systems develop goals and understand the basic arguments for instrumental convergence;
- are aware of foundational discussions on the level of risk and different high-level approaches to solving the AI alignment problem.
%%
# Module: [[../modules/ATDL 1 - AI Alignment Introduction]]
# Meeting: Day 1: AI Alignment Introduction
survey:: [[../surveys/Lens Post-Meeting Impact Survey v2]]
facilitator-survey:: [[../surveys/Navigator Session 1 Debrief]]

%%
Day 2 goals (Zach Furman's B.2 outcomes, verbatim):
- Students can explain and distinguish the three classical mysteries of why deep learning performs well: approximation, generalization, and optimization.
- Students understand why each of the three classical mysteries implicitly requires leveraging structure in reality: learning is not tractable for arbitrary tasks, so deep learning must be using non-generic properties of real-world tasks to succeed.
- Students are aware of the key empirical mysteries of deep learning: data-dependent generalization despite overparameterization, effectiveness of SGD on non-convex landscapes, representational alignment across architectures, and in-context learning
- Students have encountered at least one candidate explanation for each mystery and can articulate what it does and doesn't explain
- Students understand the "program synthesis" hypothesis as one proposed framework connecting deep learning to Solomonoff induction, and can evaluate its strengths and limitations
- Students can articulate why solving these mysteries matters for AI safety
%%
# Module: [[../modules/ATDL 2 - Mysteries of Deep Learning]]
# Meeting: Day 2: Mysteries of Deep Learning
survey:: [[../surveys/Lens Post-Meeting Impact Survey v2]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]

%%
Day 3 goals (B.3 has no written outcomes list; these are the authors' three fast-track aims, verbatim, plus the landing-page outcome):
- To understand parameter-function map versus loss landscape degeneracy
- To understand the local learning coefficient via volume scaling
- To understand the relation between degeneracy and learning in the Bayesian case
- Landing page: "You can compute degeneracy in small models and explain what the local learning coefficient measures and why it matters."
%%
# Module: [[../modules/ATDL 3 - Singular Learning Theory]]
# Meeting: Day 3: Singular Learning Theory
survey:: [[../surveys/Lens Post-Meeting Impact Survey v2]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]

%%
Day 4 goals (Guillaume Corlouer's B.4 outcomes, verbatim, abridged to the headline items):
- Understand the concept of implicit regularization; understand the AI safety motivations for learning dynamics
- Know key results about the loss landscape of deep linear networks (DLNs): critical points are saddles or global minima
- Understand that gradient flow can be written as NTK-weighted gradient in function space; DLNs are degenerate and have conserved quantities through gradient flow
- Understand the role of initialization, width and depth for the lazy and rich (saddle to saddle) regimes in DLNs
%%
# Module: [[../modules/ATDL 4 - Training Dynamics]]
# Meeting: Day 4: Training Dynamics
survey:: [[../surveys/Lens Post-Meeting Impact Survey v2]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]

%%
Day 5 goals (B.5 has no written outcomes list; the author's route aims plus the landing-page outcome):
- Understand data attribution as a causal question, and why leave-one-out counterfactuals miss overdetermined and mediated causes (Section 1, required for every route)
- One of: derive classical influence functions and their modern fixes; connect Bayesian influence functions to classical ones; derive unrolling and recover influence functions as its limit
- Landing page: "You can derive influence functions, state when their approximations fail, and compare them with Bayesian and unrolling methods."
The final meeting's survey is ATDL Final Impact Survey v2, a copy of CV1 Final Impact Survey v2 with fresh ids and the course name swapped (the pattern CV1 used).
%%
# Module: [[../modules/ATDL 5 - Data Attribution]]
# Meeting: Day 5: Data Attribution
survey:: [[../surveys/ATDL Final Impact Survey v2]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]
