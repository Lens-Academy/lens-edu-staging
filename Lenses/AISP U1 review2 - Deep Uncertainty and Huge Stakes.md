---
id: '8d6d8c21-9c9e-452f-bf11-5e8bc8c76831'
title: "Deep Uncertainty and Huge Stakes"
tldr: "A precise-looking probability can conceal uncertainty about the evidence, the model, and the values used in the calculation. Huge stakes matter, but they do not make a weak estimate strong."
summary_for_tutor: "Develops risk, uncertainty, model uncertainty, ignorance, expected value, Pascal's Mugging, estimate reliability, sequence and cluster thinking, and simple versus complex cluelessness. The learner should leave able to inspect how a number was generated before deciding how much weight to give it."
reading_minutes: 24
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## What kind of uncertainty is hiding inside the number?

AI risk discussions often start with a probability. One person says one percent. Another says ten percent. A third refuses to give a number because the event is too unusual. Those positions can look like different points on one scale, but they often reflect different views about what can be estimated in the first place.

Decision theory traditionally distinguishes decisions made under *risk*, where relevant probabilities are available, from decisions made under *uncertainty*, where probabilities are unavailable or only partly specified.[^cite-sep-risk] Real decisions sit on a spectrum. Even when somebody gives a precise number, they may be uncertain about the data, the reference class, the model, the assumptions, or whether important possibilities have been left out.

It helps to separate several layers because they call for different responses. **Parameter uncertainty** concerns quantities inside a model. We may agree that a model is useful but disagree about the probability of a particular step. **Model uncertainty** concerns the structure itself. A model can have precise parameters and still leave out a mechanism that changes the result. **Ignorance** goes further: there may be possibilities that nobody has represented. **Normative uncertainty** concerns value. People can agree perfectly about what will happen and disagree about how good or bad the outcome is.[^cite-sep-risk]

These categories overlap. The distinction is still useful. More data can reduce uncertainty about a parameter. It may do little if the deeper disagreement is about whether the model should include strategic deception, gradual disempowerment, or a new class of moral patients. Empirical work can narrow a capability forecast and still leave the moral value of a future population almost untouched.

A number is therefore best understood as a compressed summary of a reasoning process. It can be valuable because it forces commitments and makes updates visible. It becomes misleading when the neatness of the output is mistaken for certainty about the world.

\## Why a small probability can still matter

Expected-value reasoning starts from a simple point. A one percent chance of losing ten pounds is different from a one percent chance of losing ten million pounds. The probability is the same, but the consequence changes the decision.

This is why "the probability is small" does not settle a catastrophic-risk argument. A risk does not need to be the most likely outcome before it can justify preparation. Governments insure against rare events. Engineers design systems with margins for failures they do not expect to occur. People buy insurance precisely because an unlikely event can still be worth preparing for.

Existential-risk arguments push this logic into unusual territory because the possible consequences can be enormous. If extinction removes a very large amount of future value, even a low probability can produce a large expected loss.[^cite-bostrom-2013] The arithmetic is straightforward. The hard part is deciding what probability should go into the arithmetic, how much confidence to place in it, and whether the model contains the right possibilities.

There is another complication. A very small first-order estimate can be less important than uncertainty about the estimate itself. Suppose a model says that catastrophe has probability one in a million, but there is a much larger chance that the model is badly misspecified. The one-in-a-million figure does not describe the full epistemic situation.[^cite-bostrom-2013] The same issue appears on the other side. A fragile model can produce an enormous expected value without giving us strong reason to let that estimate dominate every other consideration.

\## A large payoff is not automatically a bad argument

There is a common overreaction to expected-value reasoning. Someone mentions a very large benefit or harm and the response is "that is Pascal's Wager". The size of the payoff is not what makes a Pascal-style argument problematic.

A very large consequence can have ordinary evidence behind it. Cryonics may offer many additional years of life if the biological assumptions are correct. A technology can create very large economic benefits because there are independent reasons to think it scales. A pandemic can create enormous harm even if the initial probability is low. The right question is how the probability is supported, not whether the consequence is dramatic.[^cite-yudkowsky-fallacy]

This matters for AI safety because the field deals with claims that are unusual and high-stakes at the same time. We need to be able to accept a large update when the evidence is strong while refusing to give unlimited decision weight to stories that become persuasive only because the payoff was made huge.

\## Pascal's Mugging

Consider a stranger who asks for five dollars and says that if you refuse, they will use extraordinary powers to cause an unimaginably large amount of suffering. You assign the story a tiny probability. The stranger then increases the number of threatened victims until probability multiplied by harm becomes larger than almost anything else you could do.

A crude expected-value rule now says to pay. The stranger can keep increasing the claimed harm and continue winning the calculation.[^cite-yudkowsky-mugging]

The problem is not simply "tiny probability times huge consequence". Many legitimate risks have exactly that structure. The problem is that the story gains decision weight by increasing a number inside the story while the evidence supporting the story has barely changed. An almost unsupported claim becomes decisive because its internal payoff is allowed to grow without bound.

That gives us a useful test for high-stakes arguments. Ask whether the evidence supporting the probability changes when the payoff becomes larger. If the only thing changing is the claimed number of affected lives, the calculation may be doing more work than the evidence can justify.

\## Why a fixed discount is not enough

A natural response is to say, "Fine, I will heavily discount calculations I do not trust." Suppose an intervention appears to have expected value of one billion units. You decide there is a 99.9 percent chance the analysis is wrong. The remaining expected value is still one million units. If the initial estimate can be made arbitrarily large, a fixed discount can be outrun.

This is one reason estimate reliability matters at a deeper level. A useful analogy is a rating system. A restaurant with three five-star reviews and a restaurant with two hundred reviews averaging 4.75 do not provide equally strong evidence about quality. The small sample can easily produce an extreme average by chance. A sensible estimate takes the strength of the evidence into account.[^cite-karnofsky-2011]

The same idea applies to expected-value estimates. A number produced by repeated observations and a stable causal model should usually move us more than the same number produced by several speculative assumptions. The difference is not that the second estimate is forbidden. It is that the path from evidence to conclusion is much noisier.

Bayesian reasoning gives one formal language for this. Weak evidence should move beliefs less. Strong repeated evidence can move beliefs much further from prior expectations. The difficulty in AI risk is that the prior and the error distribution are themselves disputed. We do not have a clean reference class for "civilisation develops machine systems that automate a large share of cognition". We also do not know how much error enters when multiple speculative assumptions are multiplied together.

The absence of a clean formula does not erase the principle. The evidential process matters. Two estimates with the same midpoint can deserve very different decision weight.

#### Question: Open
id:: 78eb8785-6f2e-4fb4-96ec-c50d23b723a9
content::
\## Midpoint check

Take a claim such as "advanced AI causes a global catastrophe this century with probability 10%".

Where does most of the uncertainty live for you? Pick one or two:
- the data we currently have
- the numerical parameters
- the causal model itself
- possibilities the model may be missing
- the moral value of the outcome
- something else

Explain why you put the uncertainty there.

feedback-instructions::
This is ungraded. Help the learner distinguish uncertainty about a number from uncertainty about the model generating the number. If they choose "something else", help them make it explicit. Do not argue about whether 10% is correct. Maximum two replies.

#### Text
content::
\## One chain or several perspectives?

One way to reason about a difficult decision is to build a single explicit chain. Estimate the probability of catastrophe. Estimate how much an intervention changes that probability. Estimate the value of avoiding the catastrophe. Compare the result with cost and alternatives. This style makes assumptions visible and disagreements easier to locate.[^cite-karnofsky-2014]

The weakness appears when one uncertain quantity dominates the entire result. An astronomical estimate of future value can overwhelm every other consideration. A speculative estimate of intervention effectiveness can do the same. The arithmetic may be correct while the recommendation is still being driven by the least reliable part of the model.

A second style looks at the decision through several partly independent perspectives. Does the causal model support the conclusion? How have related forecasts performed? Do people using different methods converge? Does the recommendation survive major changes in assumptions? Are there incentives that make some estimates systematically optimistic or pessimistic? Is the action reversible if the model is wrong?[^cite-karnofsky-2014]

This does not mean taking a vote among intuitions. The point is to represent model uncertainty more honestly. If several genuinely independent lines of evidence point in the same direction, that is stronger than three versions of the same argument. If one fragile model produces an extreme answer while every other perspective points elsewhere, the extreme answer deserves scrutiny.

There is also a danger in being too conservative. If every unusual claim is pulled back toward historical norms, we become slow to recognize genuinely new situations. The world occasionally produces events with no close precedent. A new technology can create a new class of risk. A strong prior should raise the evidential bar for extraordinary conclusions, not make extraordinary conclusions impossible.

\## The problem of downstream consequences

Even a perfect estimate of an intervention's direct effect can leave a harder question. Actions change the future through chains that are difficult to foresee. A health intervention changes population, institutions, and economic conditions. A research publication can help defenders and dangerous actors. An AI regulation can reduce one failure mode while increasing geopolitical competition or concentration of power.

Some of this ignorance may not matter much to the comparison. If we have no reason to think remote effects systematically favour one option, treating them as roughly cancelling in expectation can be defensible. This is sometimes called *simple cluelessness*.[^cite-greaves-2016]

Other cases are much harder. We may have concrete reasons pointing in opposite directions. A policy can improve safety through one mechanism and worsen it through another. A deployment pause can create time for evaluation while shifting development to actors with weaker oversight. Open research can improve scrutiny while spreading capabilities. These are cases of *complex cluelessness*: the uncertainty contains structured reasons on both sides, and there is no obvious way to combine them.[^cite-greaves-2016]

This distinction matters because "unknown unknowns" is too cheap an objection. Every action has unmodelled consequences. If that fact alone defeated expected-value reasoning, almost no decision would be possible. The relevant question is whether we can identify important omitted mechanisms that are asymmetric enough to change the sign of the decision.

\## Correlation matters

Another source of false confidence comes from counting several estimates as independent when they share the same foundation. Five experts can all cite the same paper. Three models can all inherit the same assumption about scaling. Several forecasts can be based on the same benchmark trend.

Apparent agreement is more informative when the routes to agreement are independent. If a mechanistic model, historical analogy, deployment evidence, and expert judgment all point in the same direction for different reasons, the convergence is stronger. If every argument ultimately depends on one disputed premise, multiplying the number of people repeating it adds much less information.

This becomes important later when we look at disagreement between experts and forecasters. The question is not only how many people hold each view. It is what evidence they are using, how correlated the evidence is, and what would make them change their minds.

\## Precision can still be useful

Nothing here implies that people should stop using numerical probabilities. Numbers can discipline thought. They expose inconsistency. They make updates visible. They force a person to compare a claim with alternatives. They can reveal that a verbal disagreement is actually small or that two apparently similar views imply very different actions.

The useful habit is to treat a number as a claim about both the world and the reasoning process. Ask what produced it. Ask what reference class or model stands behind it. Ask how sensitive it is to changes in assumptions. Ask which pieces of evidence are genuinely independent. Ask what the model omits. Ask whether normative uncertainty is being hidden inside an empirical-looking number.

The final question is practical: what should uncertainty change about action? Sometimes the answer will be "do less". Sometimes it will be "do something reversible". Sometimes it will be "gather information first". Sometimes the stakes will be high enough that uncertainty supports acting earlier. The next submodule looks directly at that choice.

[^cite-sep-risk]: Sven Ove Hansson, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^cite-bostrom-2013]: Nick Bostrom (2013), *Existential Risk Prevention as Global Priority*. [PDF](https://existential-risk.com/concept.pdf)
[^cite-yudkowsky-fallacy]: Eliezer Yudkowsky, *The Pascal's Wager Fallacy Fallacy*. [LessWrong](https://www.lesswrong.com/posts/TQSb4wd6v5C3p6HX2/the-pascal-s-wager-fallacy-fallacy)
[^cite-yudkowsky-mugging]: Eliezer Yudkowsky, *Pascal's Mugging: Tiny Probabilities of Vast Utilities*. [LessWrong](https://www.lesswrong.com/posts/a5JAiTdytou3Jg749/pascal-s-mugging-tiny-probabilities-of-vast-utilities)
[^cite-karnofsky-2011]: Holden Karnofsky (2011), *Why We Can't Take Expected Value Estimates Literally (Even When They're Unbiased)*. [GiveWell](https://blog.givewell.org/2011/08/18/why-we-cant-take-expected-value-estimates-literally-even-when-theyre-unbiased/)
[^cite-karnofsky-2014]: Holden Karnofsky (2014), *Sequence Thinking vs. Cluster Thinking*. [GiveWell](https://blog.givewell.org/2014/06/10/sequence-thinking-vs-cluster-thinking/)
[^cite-greaves-2016]: Hilary Greaves, *Cluelessness*. [Oxford PDF](https://users.ox.ac.uk/~mert2255/papers/cluelessness.pdf)

#### Question: Open
id:: 29964799-9256-42d7-a2c9-b22080b06a53
content::
\## Phase 1: Recall

Without looking back, reconstruct at least four different ways an AI-risk estimate can be uncertain. Then explain the core problem in Pascal's Mugging without making "the probability is tiny" your whole answer.

feedback-instructions::
This is diagnostic recall. Respond once in 90 to 160 words, using short paragraphs and no list. Credit distinctions stated in the learner's own language. Point out at most two conflations, especially if they treat a small probability as identical to uncertainty about the model or evidence. Do not reteach the lens.

#### Question: Open
id:: 02044632-c990-45f2-8f46-b32fdc6651cd
content::
\## Phase 2: Processing

Which failure worries you more in AI safety: dismissing an important risk because it is unprecedented, or overreacting to a fragile model because the claimed stakes are enormous? What evidence would make you worry more about the other failure?

feedback-instructions::
This is reflective and ungraded. Do not push the learner toward either answer. Help them name evidence that would genuinely discriminate between the two concerns. Keep an internal turn counter and close after two tutor replies.

#### Question: Open
id:: bbe56118-0f35-42cf-8111-82ba01ab0e14
content::
\## Phase 3: Learning Question

Two interventions each claim an expected benefit of one million lives saved.

**Intervention A** is supported by repeated experiments, a stable reference class, and a causal model that has predicted outcomes well before.

**Intervention B** gets the same expected value by multiplying five uncertain assumptions about an unprecedented technology. Each assumption is based mainly on expert judgment, and small changes to several assumptions move the estimate by orders of magnitude.

Why would it be a mistake to treat the estimates as equally decision-relevant simply because the expected values are numerically identical? What additional information would you want before deciding between the interventions?

assessment-instructions::
Score out of 100.

45 points: The answer explains that equal numerical expected values can deserve different evidential weight because the estimates differ in robustness, model uncertainty, or reliability of the process that generated them.

30 points: The answer identifies useful additional information about sensitivity to assumptions, estimate error, reference classes or priors, independent lines of evidence, or historical calibration.

25 points: The answer explains how the additional information could affect the decision, for example by changing confidence, motivating further investigation, or favouring an option that remains good across plausible models.

feedback-instructions::
Give 100 to 170 words in short paragraphs, with no generic praise. Identify the strongest distinction the learner made and the most important source of uncertainty they missed, if any. Do not require Bayesian vocabulary or a particular position on expected-value reasoning.
