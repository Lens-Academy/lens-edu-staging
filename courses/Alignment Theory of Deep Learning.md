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
