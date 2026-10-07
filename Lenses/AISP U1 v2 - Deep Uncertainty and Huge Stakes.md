---
id: '2a835092-452e-44c1-9115-0be9a0f02518'
title: "Deep Uncertainty and Huge Stakes"
tldr: "A tiny probability can matter when the stakes are huge, but a precise-looking number is not the same thing as a well-supported probability."
summary_for_tutor: "Builds a vocabulary for risk, uncertainty, ignorance, model uncertainty, and normative uncertainty. Then develops expected-value reasoning, Pascal's Mugging, Bayesian adjustment, sequence versus cluster thinking, and Greaves's distinction between simple and complex cluelessness."
reading_minutes: 36
tutor_minutes: 20
tags:
  - wip
---

#### Text
content::
\## What kind of uncertainty are we talking about?

AI risk debates often begin with a number. One person says 1 percent. Another says 20 percent. A third says there is no defensible probability at all. Those statements can look like disagreements on one scale, although they may describe very different epistemic situations.

The Stanford Encyclopedia of Philosophy entry on risk draws a useful decision-theoretic distinction. A decision is made *under risk* when probabilities are available, and *under uncertainty* when they are unavailable or only partly available.[^cite-sep-risk] In real life, that line is blurry. Even a precise probability estimate can be uncertain because we may be uncertain about the model, data, reference class, or expert judgment that produced it.

For this unit, it helps to separate several things.

**Risk:** we have an outcome and a probability estimate that we are willing to use for the decision.

**Ambiguity or deep uncertainty:** we do not know which probability distribution to use, or several distributions look defensible.

**Model uncertainty:** we are unsure whether the causal structure we are using is right at all. A model can have precise parameters and still omit a mechanism that changes the answer.

**Ignorance:** some important possibilities may not appear in our model because we have not thought of them.

**Normative uncertainty:** we may agree on what happens while disagreeing about how good or bad the outcome is.

These categories overlap. Their value is practical. Different uncertainty calls for different responses. More data can narrow a statistical estimate. It may do very little for a disagreement about which variables belong in the model. No amount of capability benchmarking settles how much future lives should count morally.

\## Why small probabilities can matter

Expected-value reasoning starts from a simple idea. If an outcome is very bad, a small probability of that outcome can still matter. A one percent chance of losing ten dollars and a one percent chance of losing ten million dollars are very different decisions because the consequences are different.

This is why "the probability is small" cannot end an argument about catastrophic risk. If the downside is permanent extinction, disempowerment, or some other irreversible catastrophe, even probabilities far below fifty percent can justify attention. A policy does not need catastrophe to be the most likely outcome before preparing for it makes sense.

Bostrom pushes this further by noting that uncertainty about a small probability can be larger than the probability itself.[^cite-bostrom-xrisk] Imagine an analysis that produces a one-in-a-million estimate. If there is a much larger chance that the analysis is badly misspecified, then the one-in-a-million figure does not capture our actual epistemic state. We have uncertainty about the estimate itself.

This problem is common in unprecedented domains. There is no historical frequency for "humanity develops systems much more capable than humans and then sees what happens for a century." We build probabilities from arguments, analogies, expert judgments, models, and extrapolations. Those can still be useful, but the route from evidence to number matters.

\## Pascal's Mugging

Pascal's Mugging is a stress test for this kind of reasoning.[^cite-yudkowsky-mugging] Someone asks you for a small amount of money and claims that if you refuse, they will use extraordinary powers to cause an unimaginably large amount of harm. Give the story a tiny probability and then make the threatened harm large enough. The expected harm can be made larger than almost anything else you could do.

The absurdity is useful because it exposes a weakness in a crude rule: "multiply the stated probability by the stated payoff and follow the largest number." A story should not gain unlimited decision weight just because the person telling it keeps increasing the payoff.

There is an easy overreaction. People sometimes hear a large payoff and say "that is Pascal's Wager", as if magnitude itself were suspicious. Yudkowsky calls this the Pascal's Wager Fallacy Fallacy.[^cite-yudkowsky-fallacy] Large consequences can have ordinary evidence behind them. A technology can genuinely produce a very large benefit or harm. The relevant question is how much support the probability has when considered independently of the size of the payoff.

\## Why a fixed discount does not solve the problem

A common patch is to say, "I am 99.99 percent sure this analysis is wrong, so I will discount it by 99.99 percent." Holden Karnofsky argues that this can still take rough estimates too literally.[^cite-karnofsky-eev] If the initial estimate is made arbitrarily large, it can outrun any fixed discount.

His restaurant example captures the intuition cleanly. One restaurant has three five-star reviews. Another has two hundred reviews averaging 4.75. Looking only at the observed average favors the first restaurant. Most people would not treat the evidence that way. The tiny sample is much more likely to generate an extreme result by noise.

Bayesian reasoning formalizes this by combining new evidence with a prior. Weak evidence moves us less. Strong evidence moves us more. The exact calculation becomes difficult in domains where the prior is contestable and estimate error is hard to quantify. Karnofsky's main point survives the difficulty: two numerical estimates with the same midpoint should receive different weight when one is grounded in precise, repeated evidence and the other in a chain of guesses.

This creates a tension that matters throughout AI safety. A strong prior can protect us from extravagant claims supported by thin evidence. A prior that is too rigid can make unprecedented events almost impossible to believe until they happen.

\## One model, or several?

Karnofsky later contrasts *sequence thinking* with *cluster thinking*.[^cite-karnofsky-cluster] Sequence thinking puts the important considerations into one explicit chain. For an AI intervention, you might estimate the probability of catastrophe, the intervention's effect on that probability, the value of avoiding catastrophe, and the cost.

The advantage is transparency. You can inspect assumptions and find where disagreement enters. The weakness appears when one highly uncertain number dominates the output.

Cluster thinking approaches the same decision from several directions. What does the explicit model say? How have similar predictions performed? Do people using different methods converge? Does the conclusion survive major changes in assumptions? Are there institutional reasons to distrust the estimate? How reversible is the action?

Cluster thinking is not an instruction to trust intuition whenever a model gives an uncomfortable answer. It is a reminder that model uncertainty belongs inside the decision somehow. A surprising conclusion supported by independent evidence should eventually overcome the prior. A surprising conclusion produced by one fragile chain deserves less confidence.

\## Cluelessness: when the unknown future will not sit still

Hilary Greaves asks a harder question.[^cite-greaves-cluelessness] Almost every action has consequences stretching far into the future. Helping someone across the street changes timings, meetings, relationships, births, careers, and eventually a huge number of later events. If all consequences count morally, how can we know whether the act was actually better?

Greaves distinguishes *simple* and *complex* cluelessness. In simple cases, we know there are countless downstream effects but have no particular reason to think they systematically favor one option. If helping and not helping generate equally plausible remote chains in both directions, those unknown effects can plausibly contribute zero difference in expected value.

Complex cluelessness is more worrying. Here we have concrete reasons pointing in opposite directions and no obvious way to weigh them. A health intervention can save lives while changing population dynamics, political incentives, and institutional capacity. An AI policy can reduce one risk while increasing another. Publication can help safety researchers and dangerous actors at the same time. Slowing deployment can create time for oversight while shifting power toward actors willing to ignore the slowdown.

The challenge is no longer "anything could happen". We have identifiable mechanisms, some beneficial and some harmful, and we do not know how they combine.

\## Numbers can hide disagreement about the model

This is especially important for AI risk because a single probability often compresses a long argument. "Five percent chance of catastrophe" can mean five percent after assigning probabilities to capability progress, agency, misalignment, power acquisition, oversight failure, geopolitical response, and many other links. Two people can produce the same final number from entirely different internal models.

A precise number is still useful when it disciplines reasoning. It forces us to ask what would move the number and where uncertainty enters. The mistake is treating precision in the output as evidence of precision in the world.

The next submodule asks what action should follow once we admit all of this. Expected value cannot simply be discarded. Precaution cannot simply take over. We still have to choose.

[^cite-sep-risk]: Sven Ove Hansson and others, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^cite-bostrom-xrisk]: Nick Bostrom (2013), *Existential Risk Prevention as Global Priority*. [PDF](https://existential-risk.com/concept.pdf)
[^cite-yudkowsky-mugging]: Eliezer Yudkowsky, *Pascal's Mugging: Tiny Probabilities of Vast Utilities*. [LessWrong](https://www.lesswrong.com/posts/a5JAiTdytou3Jg749/pascal-s-mugging-tiny-probabilities-of-vast-utilities)
[^cite-yudkowsky-fallacy]: Eliezer Yudkowsky, *The Pascal's Wager Fallacy Fallacy*. [LessWrong](https://www.lesswrong.com/posts/TQSb4wd6v5C3p6HX2/the-pascal-s-wager-fallacy-fallacy)
[^cite-karnofsky-eev]: Holden Karnofsky (2011), *Why We Can't Take Expected Value Estimates Literally (Even When They're Unbiased)*. [GiveWell](https://blog.givewell.org/2011/08/18/why-we-cant-take-expected-value-estimates-literally-even-when-theyre-unbiased/)
[^cite-karnofsky-cluster]: Holden Karnofsky (2014), *Sequence Thinking vs. Cluster Thinking*. [GiveWell](https://blog.givewell.org/2014/06/10/sequence-thinking-vs-cluster-thinking/)
[^cite-greaves-cluelessness]: Hilary Greaves, *Cluelessness*. [Oxford PDF](https://users.ox.ac.uk/~mert2255/papers/cluelessness.pdf)

#### Question: Open
id:: f748744b-ff4a-4dbc-909f-f2aa24f9293a
content::
\## Phase 1: Recall

Without looking back, write down the different kinds of uncertainty you remember from this reading and one reason they call for different responses. Then reconstruct the core problem behind Pascal's Mugging in your own words.

feedback-instructions::
Respond once in 90 to 150 words. Credit distinctions made in the learner's own language. Point out at most two conflations, especially if they treat uncertainty about a probability as identical to a small probability. Do not reteach the whole reading.

#### Question: Open
id:: 01d955af-52a4-4bb0-b7b6-69c79056427b
content::
\## Phase 2: Processing

Think of one AI-safety claim you have heard that comes with a probability or an expected-value estimate. What part of that estimate do you trust most, and what part feels least grounded? If you cannot think of a real example, use "advanced AI causes catastrophe this century."

feedback-instructions::
This is reflective. Help the learner identify whether their uncertainty is mainly about data, parameters, model structure, omitted mechanisms, or values. Maximum two replies.

#### Question: Open
id:: e5c49e68-5023-4cf5-adfb-a43c1293601a
content::
\## Phase 3: Learning Question

Two interventions each claim an expected benefit of one million lives saved.

Intervention A's estimate comes from repeated randomized trials and a well-understood causal model. Intervention B's estimate comes from multiplying five rough assumptions, each based mainly on expert judgment.

Why would it be a mistake to treat the two estimates as equally decision-relevant just because their expected values are numerically identical? Explain what extra information you would want before choosing between them.

assessment-instructions::
Score out of 100.

50 points: The answer explains that equal numerical expected values can carry different evidential weight because the estimates differ in uncertainty, robustness, or reliability of the process that produced them.

25 points: The answer identifies useful additional information about estimate error, priors or reference classes, sensitivity to assumptions, or independent lines of evidence.

25 points: The answer explains how that information could change the decision, for example by shrinking confidence in one estimate, motivating further investigation, or favoring a more robust option.

feedback-instructions::
Give 100 to 160 words. Identify the strongest distinction the learner made and the most important missing source of uncertainty if any. Do not require Bayesian vocabulary.
