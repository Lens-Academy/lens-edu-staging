---
id: 'c1c6d7fe-4773-44bb-90e9-f29b93ca01c4'
learning-outcome: "Represent a state of uncertainty as a set of probability distributions, explain what this captures that a single distribution with the same central estimate does not (how far the evidence settles the question, as opposed to where it points), and compare the choices that a decision rule based on the set produces with those of maximizing expected value under one best-guess distribution, including where the set-based rule goes wrong if applied one option at a time."
topic: "[[../Domains and Topics/4 Agent Foundations/Imprecise probability and infra-Bayesianism]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Imprecise Probability. AFFINE prerequisites: Probability. Not yet copied into requires:. %%
## Test:
id:: a18d5678-cc15-47d0-a54c-425963a8fc91

#### Question: Open
id:: 1b14f6ec-2c00-406d-8a5e-544b1467b309
content:: Consider two events.

Event C: a coin you have tossed 10,000 times lands heads on its next toss. It has landed heads close to half the time.

Event M: a new AI model, not yet evaluated, passes a particular dangerous-capability test. You have weighed the arguments on both sides and cannot say whether passing is more or less likely than not. You judge that any probability from 0.2 to 0.8 is defensible, and that no value in that range is better supported than the others.

1. Represent your uncertainty about each event with a set of probabilities. Explain what your representation of M expresses that the single number 0.5 would not.
2. A trader will buy or sell tickets that pay 1 credit if the event happens. Your rule: accept a trade only if it has positive expected value under every probability in your set. For each event, at which prices would you buy a ticket, at which would you sell one, and where would you do neither?
3. For event M, the trader offers you two tickets, each priced at 0.45 credits: one pays 1 credit if M happens, the other pays 1 credit if M does not happen. What does your rule say about each ticket judged on its own? What would someone with a precise credence of 0.5 do? What happens if you judge the two tickets together as one package, and what does this show about how your rule should be applied?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may conclude that sets of probabilities are the right model or that part 3 is a reason to prefer precise credences, and can score full marks either way if the reasoning is sound. Accept equivalent terminology (credal set, interval, upper and lower probability, Knightian uncertainty, ambiguity).

**(a) Representation, 30 points.** 10 points: C is represented by a single probability of about 0.5 (or a very narrow interval around it), and M by the set of all probabilities from 0.2 to 0.8. 20 points: what the set for M expresses that 0.5 does not, in any wording, for example: the evidence does not settle the question, so the learner suspends judgment on whether M is more or less likely than not; the width shows how little the evidence pins down, while C's 0.5 comes from strong evidence; a precise 0.5 would treat C and M as the same state of belief, although they should respond differently to new evidence and to offered bets. 8 of the 20 for "M is more uncertain" with no statement of what kind of uncertainty differs.

**(b) Prices, 30 points.** C: buy below 0.5, sell above 0.5 (a small no-trade zone around 0.5 is fine if the learner used a narrow interval). M: buy only below 0.2, sell only above 0.8, and do neither between 0.2 and 0.8, because a price in that range gives positive expected value under some probabilities in the set and negative under others. 10 points for C, 20 for M (10 for the thresholds, 10 for the reason). Do not penalize treating the exact endpoints either way.

**(c) The two tickets, 40 points.** 12 points: judged alone, each ticket has expected value ranging from -0.25 to +0.35 over the set (for example 0.2 - 0.45 and 0.8 - 0.45), so the rule declines each. 8 points: an agent with precise credence 0.5 sees +0.05 on each ticket and buys both. 10 points: together the two tickets cost 0.90 and pay exactly 1 whatever happens, a sure gain of 0.10, so the package has positive expected value under every probability and the rule accepts it. 10 points: the lesson, in any argued form, for example: a set-based rule must be applied to whole plans or combinations of choices, not option by option, or it can refuse a sure gain; or this is a known objection to imprecise probability that the learner judges serious. A learner who instead argues that the stated rule is too strict, because other set-based rules (such as maximality, which rules out an option only if another option is better under every probability) permit accepting each ticket, also earns these 10 points.
feedback-instructions:: Say whether the learner explained what the width of M's interval means, not only that it is wider. Name the strongest part of the answer and the single change that would improve it most, for example checking the package payoff in every outcome. Ask one follow-up question, such as how the set for M should change after the model passes a weaker related test. No generic praise.
