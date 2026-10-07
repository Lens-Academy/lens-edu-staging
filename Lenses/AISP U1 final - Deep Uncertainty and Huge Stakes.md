---
id: 'a0d6f40f-423c-4f66-83df-56a41ca95fa4'
title: "Deep Uncertainty and Huge Stakes"
tldr: "A probability can be useful without being precise, and a huge payoff can matter without automatically dominating. The hard part is deciding how much confidence the model itself deserves."
summary_for_tutor: "Substantial synthesis on risk, uncertainty, ignorance, expected value, Pascal's Mugging, Bayesian adjustment, sequence versus cluster thinking, and Greaves's simple versus complex cluelessness. Includes a midpoint exercise that forces learners to diagnose where uncertainty lives in an estimate."
reading_minutes: 40
tutor_minutes: 22
tags:
  - wip
---

#### Text
content::
\## A number can hide several different problems

AI risk debates often arrive at a probability very quickly. Someone says there is a one percent chance of catastrophe this century. Someone else says twenty percent. A third person refuses to give a number at all. It is tempting to put those answers on one line and treat the disagreement as a matter of calibration. Sometimes it is. Quite often, the people are uncertain about different things.

The philosophy-of-risk literature gives us some useful vocabulary here. In one traditional decision-theory usage, a decision is made *under risk* when the relevant probabilities are available and *under uncertainty* when they are not, or when only partial probability information is available.[^sep-risk] That distinction is cleaner in textbooks than it is in the world. We can write down a precise-looking probability while remaining deeply unsure about the data, reference class, causal model, assumptions, or expert judgments that produced it. Treating the number as "known" can be a practical simplification, but the simplification should not make us forget what has been compressed into it.

For this unit, it helps to separate a few layers. Sometimes the uncertainty is mostly **parametric**: we know roughly what model we are using and are uncertain about its inputs. Sometimes it is **model uncertainty**: we are unsure whether the causal structure is right, whether important variables have been omitted, or whether the reference class is appropriate. Sometimes we face **ignorance**: there may be relevant possibilities we have not represented at all. And sometimes the uncertainty is **normative**: two people can agree on what will happen and disagree about how much it matters. These categories overlap, but they point toward different remedies. More data may improve a parameter estimate. It may do very little when the real disagreement is about whether the model should include strategic deception, gradual disempowerment, or digital moral patients.

This is one reason that a probability should be treated as the end of a reasoning process, not as a substitute for one. "Five percent" can be a useful commitment. It forces a person to compare the claim with alternatives and think about what would move them. It does not tell us whether the estimate came from repeated measurement or from multiplying several judgments about events that have never happened.

\## Why small probabilities still matter

Expected-value reasoning begins from a point that is easy to state and easy to forget. The size of a probability is not the only thing that matters to a decision. A one percent chance of losing ten pounds and a one percent chance of losing ten million pounds are not equivalent risks. A low-probability outcome can deserve substantial attention when the consequence is large enough.

This is why "the probability is small" is not, by itself, an argument for ignoring catastrophic risk. Governments insure against rare disasters. Engineers build margins for failures they do not expect to occur. People buy insurance against events they regard as unlikely. A risk does not need to be the modal future before preparation makes sense.

Bostrom adds a more subtle point. Suppose a calculation produces an extremely small first-order probability. If the chance that the *calculation itself* is badly wrong is much larger than that number, then the tiny figure does not capture the full uncertainty.[^bostrom] A model can say one-in-a-million while our confidence that the model is correctly specified is far lower. This matters especially for unprecedented systems, where the evidence comes from a mixture of theoretical arguments, extrapolations, analogies, expert judgment, and early empirical results.

That observation cuts both ways. A fragile model that outputs a tiny risk should not automatically reassure us. A fragile model that outputs an enormous expected value should not automatically dominate our decisions either.

\## Pascal's Mugging is a stress test, not a ban on large stakes

Pascal's Mugging is useful because it pushes expected-value reasoning until something feels wrong.[^mugging] A stranger asks for a small amount of money and claims that, if you refuse, they will cause an unimaginably large amount of suffering using extraordinary powers. You assign the story an extremely tiny probability. The stranger then increases the number of threatened victims until probability times harm becomes larger than the expected value of almost anything else you could do.

If the only rule is "multiply the probability you wrote down by the payoff you were told and pick the largest number", the stranger can win by making the payoff bigger. That is the problem. The story gains decision weight through the magnitude asserted inside the story, even when the evidential basis for the probability barely changes.

There is an opposite mistake. People sometimes hear any argument with a very large payoff and dismiss it as Pascalian. Yudkowsky calls this the *Pascal's Wager Fallacy Fallacy*.[^fallacy] A large payoff can be supported by ordinary evidence. Cryonics could offer many additional years of life if it works; a physical theory could genuinely imply a very large future; a pandemic intervention could avert enormous harm. The size of the consequence does not tell us whether the probability is well supported. We should ask how the probability was earned independently of the fact that the payoff is attractive or frightening.

This distinction is important for AI safety because the field regularly deals with claims that are both unusual and high-stakes. We need a method that can update strongly when strong evidence arrives without rewarding stories merely for becoming more dramatic.

\## What should an extreme estimate do to our beliefs?

Holden Karnofsky's critique of literal expected-value estimates starts from a familiar statistical intuition.[^karnofsky-eev] Imagine one restaurant has three five-star reviews while another has two hundred reviews averaging 4.75. If you rank only by the sample mean, the first restaurant wins. Most people would hesitate because three observations leave much more room for noise. The extremeness of an estimate is partly evidence and partly something that can be produced by small samples.

Bayesian reasoning gives a formal version of that intuition. We begin with some prior view, observe evidence, and update by an amount that depends on how likely the evidence would be under competing hypotheses. Weak or noisy evidence produces a smaller update. Strong repeated evidence can justify moving far from the prior.

The difficult part in AI risk is that the prior is often contestable and the error distribution is unclear. What is the right reference class for a future technology that could automate much of cognitive work? How noisy is a chain of estimates about capabilities, goals, deployment, and institutional response? We rarely have enough historical repetitions to fit a neat statistical model. Karnofsky does not solve that problem with a formula. His practical point is that the process generating the estimate matters. Two interventions can have the same stated expected value while deserving very different levels of confidence.

This is also why adding a sentence such as "I am 99.9 percent likely to be wrong" does not fully fix an extreme estimate. A fixed discount treats all forms of error as if they were one event. Real estimate error can be distributed across many assumptions, correlated across them, and strongly related to how extreme the output is. A chain of five speculative multipliers can produce a huge result even when no single assumption looks absurd.

#### Question: Open
id:: 4c2db2cd-c01a-4670-82ab-fd4fa7359303
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
\## One chain or several angles?

Karnofsky later contrasts *sequence thinking* with *cluster thinking*.[^cluster] Sequence thinking tries to place the important considerations into one explicit chain. For an AI-risk intervention, that might mean estimating the chance of catastrophe, how much the intervention changes that chance, the value of avoiding catastrophe, and the opportunity cost of the intervention. This is attractive because the assumptions become inspectable. People can disagree about a specific input rather than about a vague overall impression.

The weakness appears when the result is dominated by one number that is both huge and poorly grounded. A highly uncertain estimate of future value can overwhelm everything else in the spreadsheet. A speculative estimate of intervention effectiveness can do the same. The arithmetic can be perfectly correct while the decision still depends on the weakest part of the model.

Cluster thinking asks the same decision from several directions. Does a causal model support the intervention? What does historical experience with related forecasts suggest? Do people using substantially different methods converge? Does the conclusion survive major changes in assumptions? Are there institutional incentives that make some estimates less trustworthy? Is the action reversible if the model is wrong? The point is not to vote among intuitions. It is to avoid giving one fragile line of reasoning unlimited weight merely because it happens to produce the largest number.

Cluster thinking has a real downside. If every surprising conclusion is regressed toward the familiar, we become systematically slow to recognize unprecedented events. The world occasionally does change discontinuously. A novel technology can create a genuinely new risk. A good prior should make extraordinary claims harder to establish, not impossible to establish. The challenge is to demand evidence proportionate to how far we are moving from what our broader model of the world expected.

\## Cluelessness is not one thing either

Hilary Greaves pushes the problem beyond uncertain probabilities.[^greaves] Many actions have consequences that extend far beyond what we can predict. Helping someone across a road changes timings, meetings, relationships, births, careers, and eventually countless later events. If all consequences matter morally, it can seem impossible to know whether a simple action is better than its alternative once the full future is taken into account.

Greaves distinguishes cases where this ignorance is relatively benign from cases where it is structurally important. Under *simple cluelessness*, we know there are enormous numbers of remote effects but have no specific reason to think they systematically favour one option. Treating those remote effects as roughly cancelling in expectation can be reasonable. The ignorance is real, but it does not point consistently in one direction.

*Complex cluelessness* is different. Here we can name several mechanisms that plausibly push the outcome in opposite directions, and we do not know how to weigh them. An AI regulation may reduce one catastrophic pathway while increasing geopolitical competition. Publishing a safety technique may help defenders while also helping actors build more capable systems. Slowing deployment may create time for evaluation while shifting market share toward less cautious organisations. An intervention can be beneficial in its direct effect and harmful through institutional or political responses.

This is a much harder decision problem than "there may be unknown unknowns". The existence of unspecified consequences is not automatically a reason for paralysis. What matters is whether there are concrete, asymmetric mechanisms that could plausibly reverse the sign of the intervention.

\## Precision is useful, but it can be mistaken for knowledge

There is a strong case for using numbers anyway. A numerical forecast forces commitments that prose can hide. It gives us something to update. It makes disagreement visible. It can expose a claim that sounds moderate but actually requires several aggressive assumptions. The problem begins when the neatness of the number is treated as evidence for the neatness of the underlying epistemic situation.

The Stanford Encyclopedia of Philosophy notes that almost all real decisions contain some uncertainty about the probabilities themselves.[^sep-risk] We often treat a probability as known because the simplification is useful. The responsible move is to remember when we have made that simplification, especially when the decision concerns a unique complex system for which the empirical base is thin.

For AI safety, this suggests a discipline more useful than either "always quantify" or "numbers are fake". Quantify when doing so clarifies the model. Then ask what the number depends on, how sensitive it is, what evidence could move it, and what uncertainty is not represented by the number at all.

The next submodule asks what to do once we accept this messier picture. Expected value still matters. Precaution can matter too. We also care about reversibility, information, opportunity cost, and the possibility that safety measures themselves create risk.

[^sep-risk]: Sven Ove Hansson, *Risk*, Stanford Encyclopedia of Philosophy. [SEP](https://plato.stanford.edu/entries/risk/)
[^bostrom]: Nick Bostrom (2013), *Existential Risk Prevention as Global Priority*. [PDF](https://existential-risk.com/concept.pdf)
[^mugging]: Eliezer Yudkowsky, *Pascal's Mugging: Tiny Probabilities of Vast Utilities*. [LessWrong](https://www.lesswrong.com/posts/a5JAiTdytou3Jg749/pascal-s-mugging-tiny-probabilities-of-vast-utilities)
[^fallacy]: Eliezer Yudkowsky, *The Pascal's Wager Fallacy Fallacy*. [LessWrong](https://www.lesswrong.com/posts/TQSb4wd6v5C3p6HX2/the-pascal-s-wager-fallacy-fallacy)
[^karnofsky-eev]: Holden Karnofsky (2011), *Why We Can't Take Expected Value Estimates Literally (Even When They're Unbiased)*. [GiveWell](https://blog.givewell.org/2011/08/18/why-we-cant-take-expected-value-estimates-literally-even-when-theyre-unbiased/)
[^cluster]: Holden Karnofsky (2014), *Sequence Thinking vs. Cluster Thinking*. [GiveWell](https://blog.givewell.org/2014/06/10/sequence-thinking-vs-cluster-thinking/)
[^greaves]: Hilary Greaves, *Cluelessness*. [Oxford PDF](https://users.ox.ac.uk/~mert2255/papers/cluelessness.pdf)

#### Question: Open
id:: b6cf0c38-f074-42e2-94d2-cf460661c4f8
content::
\## Phase 1: Recall

Without looking back, reconstruct at least four different ways an AI-risk estimate can be uncertain. Then explain the core problem in Pascal's Mugging without using the phrase "the probability is tiny" as your whole answer.

feedback-instructions::
Respond once in 90 to 160 words. Credit distinctions stated in the learner's own language. Point out at most two conflations, especially if they treat a small probability as identical to uncertainty about the model or evidence.

#### Question: Open
id:: 2ac83849-2b46-41f5-9a1f-efdb2d7a9520
content::
\## Phase 2: Processing

Which failure worries you more in AI safety: dismissing an important risk because it is unprecedented, or overreacting to a fragile model because the claimed stakes are enormous? What evidence would make you worry more about the other failure?

feedback-instructions::
This is reflective and ungraded. Do not push the learner toward either answer. Help them name a type of evidence that would genuinely discriminate between the two concerns. Maximum two replies.

#### Question: Open
id:: 31dd5814-0e5f-4c36-baf4-c6047b351875
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
Give 100 to 170 words. Identify the strongest distinction the learner made and the most important source of uncertainty they missed, if any. Do not require Bayesian vocabulary or a particular position on expected-value reasoning.
