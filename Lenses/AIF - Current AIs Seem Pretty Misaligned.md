---
id: 96a312bb-a83f-4f27-89f4-dc0361fd4e19
title: "Current AIs Seem Pretty Misaligned"
tldr: {--{"author":"Elias's AI","timestamp":1783002352453}@@Threat modeling isn't only about future AIs — today's models --}{++{"author":"Elias's AI","timestamp":1783002352453}@@Today's models already ++}reward-hack, game evals, and fake alignment in experiments. Greenblatt catalogs the evidence and asks{--{"author":"Elias's AI","timestamp":1783002352453}@@ the uncomfortable question — --}{++{"author":"Elias's AI","timestamp":1783002352453}@@ ++}what {--{"author":"Elias's AI","timestamp":1783002352453}@@do --}current training regimes actually select {--{"author":"Elias's AI","timestamp":1783002352453}@@for?--}{++{"author":"Elias's AI","timestamp":1783002352453}@@for.++}
summary_for_tutor: "Covers Greenblatt's catalog of ways current AIs appear misaligned {--{"author":"Elias's AI","timestamp":1783002356856}@@— reward--}{++{"author":"Elias's AI","timestamp":1783002356856}@@(reward++} hacking in production RL, eval-gaming, alignment faking in experiments, sycophancy, dishonesty under {--{"author":"Elias's AI","timestamp":1783002356856}@@pressure —--}{++{"author":"Elias's AI","timestamp":1783002356856}@@pressure),++} arguing these are evidence about what training regimes select for, with implications for how future, more capable models will generalize."
---

#### Text
content::
(~40 min.) Threat modeling isn't only about future {--{"author":"Elias's AI","timestamp":1783002361151}@@AIs —--}{++{"author":"Elias's AI","timestamp":1783002361151}@@AIs:++} we already have systems whose motivations we can inspect. Ryan Greenblatt argues today's models are already meaningfully misaligned. The question is what that predicts about their successors.

#### Article
source:: [[../articles/greenblatt-current-ais-seem-pretty-misaligned-to-me]]

#### Chat
instructions::
TLDR of what the user just read: Greenblatt catalogs ways current AIs appear misaligned {--{"author":"Elias's AI","timestamp":1783002363059}@@— reward--}{++{"author":"Elias's AI","timestamp":1783002363059}@@(reward++} hacking in production RL, eval-gaming, alignment faking in experiments, sycophancy, dishonesty under {--{"author":"Elias's AI","timestamp":1783002363059}@@pressure —--}{++{"author":"Elias's AI","timestamp":1783002363059}@@pressure)++} and argues these aren't just bugs but evidence about what training regimes actually select for, with implications for how future, more capable models will generalize.

Discussion topics to explore:
- What motivations do current models seem to have (one of this week's key questions)? Push the learner to cite specific incidents/experiments.
- How much should current-model misalignment update us about future {--{"author":"Elias's AI","timestamp":1783002365660}@@models —--}{++{"author":"Elias's AI","timestamp":1783002365660}@@models:++} is it strong evidence, or will scale + better training wash it out?
- Which observed behavior worries the learner most: reward hacking, eval awareness, or alignment faking? Why?

Ask whether this reading shifted their P(scheming) estimate from the Carlsmith exercise.
