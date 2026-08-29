---
id: '5991339a-c9ea-48cd-8b62-ded2834a0792'
title: "1.2.2 Who can prove what"
tldr: {--{"author":"Elias's AI","timestamp":1788016641293}@@"Faithful alpha import of XLab lesson 1.2.2 Who--}{++{"author":"Elias's AI","timestamp":1788016641293}@@"Verification is not something an actor has; it is an arrow between two of them: A++} can {--{"author":"Elias's AI","timestamp":1788016641293}@@prove what."--}{++{"author":"Elias's AI","timestamp":1788016641293}@@put a fact in front of a verifier about B that B did not volunteer. Draw the arrows on the board you built in 1.2, key them against Baker et al.'s four subgoals, and count. Ten of seventeen actors have no arrow at all, and one chip designer is holding up three of the four subgoals."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016641293}@@"Imported--}{++{"author":"Elias's AI","timestamp":1788016641293}@@"One exercise on the 17-actor board++} from {++{"author":"Elias's AI","timestamp":1788016641293}@@1.2. The learner lists directed edges (A to B) and the Baker et al. subgoal each one settles (1.A declared uses are accurate, 1.B declared uses have the required properties, 2.A no undeclared use of a declared cluster, 2.B no undeclared clusters at all), graded against ++}XLab's {--{"author":"Elias's AI","timestamp":1788016641293}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed --}{++{"author":"Elias's AI","timestamp":1788016641293}@@seven-edge key: Cloud providers to Frontier labs (1.A), NVIDIA to Frontier labs (1.B), NVIDIA to Cloud providers (2.A), TSMC to Proxies (2.B), NVIDIA to Proxies (2.B), Intelligence community to China (2.B), Intelligence community to Proxies (2.B). A reversed edge is reported as reversed, not as a miss. The key, the per-actor notes on why ten actors have no edge, and the closing finding (2.B has four edges, the other subgoals one each, NVIDIA ++}on {--{"author":"Elias's AI","timestamp":1788016641293}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788016641293}@@three of seven, six of seven arrowheads point at a company or a shell) are in closed callouts; reveal them only after the learner commits. Every quoted mechanism is from Baker et al. 2025 (arXiv 2507.15916)."++}
tags: [wip]
duration_minutes: 20
---
#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016645422}@@1.2--}{++{"author":"Elias's AI","timestamp":1788016645422}@@[[../Lenses/XLab Verification - v-scoping-actors|1.2]]++} asked what part each actor plays in a declaration: who owes one, who holds
evidence about one, who checks one, and who no declaration covers. That map is
a description. This is what you do with it.

Verification is not a property an actor has. It is a relation between two of
them: somebody can put a fact in front of a verifier about somebody else, and
that fact settles one of the four things a verifier has to establish. Drawing
those relations is the exercise below, and the key for it is Baker et al.'s —
the same report module 2.1 assigns when it gets to hardware.

Two things worth knowing before you start. Actors with no edge at all are a
real answer and there are more of them than you would guess. And the point of
counting is not the score: it is which of the four subgoals turns out to be
holding the whole regime up.

#### Text
content:: **Interactive exercise:** XLab's `actor-edges` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/actor-edges). Its surrounding lesson text is preserved here.

#### Text
content::
\### Notes and sources

The framework, the four subgoals and every mechanism quoted in the key:
M. Baker, G. Kulp, O. Marks, M. Brundage & L. Heim,
[“Verifying International Agreements on AI: Six Layers of Verification for
Rules on Large-Scale AI Development and Deployment”](https://arxiv.org/abs/2507.15916)
(2025). Quotations are matched against the committed copy of the paper at test
time, so a quote that drifts fails the build rather than sitting on the page.
Module 2.1 assigns the same report for its layers; this section uses its
subgoals.

The cast, the rings and the sentences that place each actor on one are 1.2's,
and the workshop above opens on the board you built there.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/actor-edges)*
