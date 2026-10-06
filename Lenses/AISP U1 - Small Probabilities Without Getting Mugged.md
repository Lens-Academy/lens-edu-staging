---
id: '1fcc1318-c60c-4688-975e-0d56fc5ef779'
title: "Small Probabilities Without Getting Mugged"
tldr: "Low-probability risks can matter, but enormous stakes do not make weak evidence strong. The hard part is deciding how much weight a fragile model deserves."
reading_minutes: 25
tutor_minutes: 16
tags:
  - wip
---
#### Text
content::
\## A small probability is not zero

Suppose there is a one percent chance of losing ten dollars. The expected loss is ten cents. Suppose instead there is a one percent chance of losing ten million dollars. The probability has not changed, but the decision relevance has. This is the basic reason that low-probability risks cannot be dismissed merely because they are unlikely. If the consequences are large enough, a small probability can still justify substantial attention.

Existential-risk arguments make this uncomfortable because the possible losses can be extraordinarily large. If extinction removes a long and valuable future, then even a modest probability of extinction may generate a very large expected loss. Bostrom uses this structure to argue that reductions in existential risk can have enormous expected value under some moral assumptions.[^cite-bostrom-2013]

The first mistake, then, is simple: "the probability is small, therefore the risk is unimportant" does not follow. But once we allow very large outcomes to carry their ordinary expected-value weight, another problem appears. We can construct stories with increasingly extravagant consequences, assign them tiny probabilities, and make them dominate the calculation. A decision rule that accepts every such move becomes vulnerable to arguments that seem disconnected from the quality of the evidence.

\## Uncertainty about the estimate can be larger than the estimate

Bostrom gives one reason to be cautious with very small first-order probabilities. Suppose a scientific analysis says that some catastrophe has probability p, and p is extremely small. We should also ask how likely it is that the analysis itself contains an important error. If the probability that the analysis is badly wrong is much larger than p, then most of our uncertainty may sit at the meta-level rather than inside the model.[^cite-bostrom-2013]

This observation cuts both ways. A model that gives a tiny probability cannot automatically reassure us if the model is fragile. But a model that gives an enormous expected value cannot automatically dominate our decision if the assumptions generating that value are equally fragile. In both cases, the number shown at the end of the calculation can hide uncertainty about the process that produced it.

This is easy to miss because probabilities look precise even when their foundations are not. "0.001 percent" can be the output of a well-validated statistical model, a rough extrapolation, an expert judgment, a guess made for convenience, or an average of several judgments that share the same underlying assumptions. The same numerical probability can therefore represent very different epistemic situations.

\## Large payoffs are not automatically Pascalian

There is also a mistake in the opposite direction. Sometimes a proposal mentions a very large payoff and the immediate response is "that sounds like Pascal's Wager." Eliezer Yudkowsky argues that this reaction confuses the size of the payoff with the source of the original problem. A claim can involve a very large benefit and still deserve substantial probability for ordinary evidential reasons.[^cite-yudkowsky-fallacy]

Cryonics is his example. If one thinks preserved brains retain enough information for future revival, then the possibility of gaining many additional years of life is not supported merely by the fact that the payoff is large. It is supported, rightly or wrongly, by claims about neuroscience, preservation, and future technology. Rejecting the argument only because the payoff is large would reverse the usual error. Instead of allowing magnitude to overwhelm evidence, we would allow magnitude to disqualify evidence.

The useful distinction is therefore not "ordinary payoff" versus "huge payoff". It is between claims whose probabilities have independent support and claims that acquire apparent decision weight mainly because we can make the payoff arbitrarily large.

\## Pascal's Mugging

Now consider the stronger case. Someone asks for a small amount of money and claims that, if you refuse, they will use extraordinary powers to harm an unimaginably large number of people. The story is unsupported. Still, if you multiply even an extremely small probability by a sufficiently large number of victims, the expected harm can be made larger than almost anything else you could do.

This is Pascal's Mugging.[^cite-yudkowsky-mugging] It exposes a real tension. We do not want to ignore low-probability catastrophic risks merely because they are hard to verify. Yet we also do not want a person to control our actions by attaching an arbitrarily large consequence to an implausible story.

A common response is to add a fixed discount. Perhaps there is a 99.99 percent chance the analysis is wrong, so we multiply the expected value by 0.0001. But this does not solve the structural problem. If the claimed payoff can keep increasing, it can outrun any fixed discount.

\## The reliability of the estimate matters

Holden Karnofsky develops a different criticism of what he calls explicit expected-value reasoning. The problem is not expected value itself. It is taking a rough estimate as though the midpoint of that estimate contained all the relevant information. If two estimates have the same numerical mean but one is based on a large body of evidence and the other on a chain of speculative guesses, a rational decision-maker should not treat them identically.[^cite-karnofsky-eev]

Karnofsky illustrates this with ratings. Imagine one restaurant has three five-star reviews and another has two hundred reviews averaging 4.75. A method that ranks only by the observed average prefers the first restaurant. Most people would not. The tiny sample can produce an extreme average by noise. A Bayesian treatment pulls weakly supported extreme observations toward a prior and allows strong evidence to move further away from it.

The charity and existential-risk cases are harder because there is no obvious "average intervention" that supplies a clean prior. Reference classes are contestable, the relevant distributions may be poorly understood, and estimates can be correlated in complicated ways. Karnofsky does not claim to have a universal formula. His practical point is that the uncertainty of the estimate-generation process has to affect how much we update on the estimate. A spectacular result supported by weak evidence should usually move us less than the same result supported by precise, repeatedly validated evidence.[^cite-karnofsky-eev]

This is one reason that an ad hoc sentence such as "even if I am 99.99 percent likely to be wrong" can be misleading. The question is not only whether an entire argument is right or wrong. We also care about how error is distributed across its inputs, how far the conclusion lies from what we previously expected, and whether several independent routes reach similar conclusions.

\## Sequence thinking and cluster thinking

Karnofsky later draws a broader distinction between two styles of reasoning.[^cite-karnofsky-cluster] In sequence thinking, we try to combine the important considerations into one explicit chain. For an AI-risk intervention, that might mean estimating the probability of catastrophe, the size of the loss, the intervention's effect on the probability, and the cost. The advantage is clarity. Each assumption is visible, and disagreements can often be located.

The danger is that one uncertain parameter can dominate the whole result. If the future value is astronomical, or if one estimated effect is several orders of magnitude larger than alternatives, the calculation can become almost entirely determined by the shakiest number in it.

Cluster thinking approaches the same decision from several partially independent perspectives. What does the explicit model say? What do historical cases suggest? How reliable are models of this type? Do experts using different methods converge? Does the recommendation survive when major assumptions change? Are there reasons from institutional incentives, reversibility, or track record that point in another direction?

Cluster thinking has its own failure mode. If we always pull unusual conclusions back toward what is normal, we can miss genuinely unprecedented events. The first nuclear chain reaction had no long historical reference class. A new technology does not become ordinary merely because our prior is skeptical. The task is therefore not to prevent surprising conclusions. It is to ask what evidence justifies moving far from ordinary expectations.

\## Unknown consequences are not all the same

There is one more complication. Some uncertainty does not fit neatly into a probability estimate or a prior. Actions can have consequences that we cannot confidently trace.

Hilary Greaves distinguishes between what she calls simple and complex cluelessness.[^cite-greaves-cluelessness] In a simple case, an action may have countless remote downstream effects, but we have no specific reason to think those effects systematically favour one option over another. Helping someone cross the road changes who meets whom, which people are delayed, which children are eventually conceived, and many later events. We cannot calculate those effects, but their mere existence does not obviously tell us to prefer helping or not helping.

Complex cluelessness is different. Here we have structured reasons pointing in opposite directions. A public-health intervention may directly save lives while also affecting population, institutions, or political incentives. An AI policy may reduce one technical risk while increasing geopolitical competition. Publishing research may help defenders while also spreading capabilities. Slowing deployment may create time for safety work while concentrating power or changing which actors lead. In these cases, the difficulty is not that "anything could happen". It is that several identifiable effects may systematically matter, the evidence about them is incomplete, and there is no obvious way to combine them.[^cite-greaves-cluelessness]

This distinction matters because people sometimes use "unknown unknowns" as a universal objection. If every unmodelled consequence counted equally against every action, decision-making would collapse. The more useful question is whether there are concrete, asymmetric reasons to expect omitted effects in one direction or another.

\## What should we actually do with all this?

These sources do not produce one mechanical decision rule, and we should not pretend they do. They give us a set of questions that make low-probability, high-stakes reasoning harder to misuse.

Ask where the probability comes from. Is it measured, modelled, inferred from a reference class, elicited from experts, or guessed? Ask how sensitive the conclusion is to assumptions. Ask how much of the apparent extremeness could be estimate error. Ask whether different lines of evidence genuinely add independent support or merely repeat the same premise. Ask whether omitted consequences are merely unspecified or whether there are concrete reasons to expect important effects in opposing directions. Finally, ask what action is being requested. The evidential bar for reading another paper can be much lower than the bar for spending billions of dollars, imposing coercive regulation, or giving an institution extraordinary power.

That last point is important. Uncertainty does not only affect belief. It affects how much action a belief can justify. A fragile argument may justify investigation long before it justifies a costly or irreversible intervention. Conversely, a risk can justify cheap preparation even when its probability is hard to estimate. This gives us a more useful response than either "ignore it until we know" or "the stakes are huge, so act maximally now".

In the next module we will apply this discipline to the actual AI-risk case. The question will no longer be whether low-probability existential risks matter in principle. It will be which mechanisms are doing the work in this particular argument, how strong the evidence for them is, and what action survives disagreement about the details.

[^cite-bostrom-2013]: Nick Bostrom, "Existential Risk Prevention as Global Priority" (2013). [PDF](https://existential-risk.com/concept.pdf)
[^cite-yudkowsky-fallacy]: Eliezer Yudkowsky, "The Pascal's Wager Fallacy Fallacy". [LessWrong](https://www.lesswrong.com/posts/TQSb4wd6v5C3p6HX2/the-pascal-s-wager-fallacy-fallacy)
[^cite-yudkowsky-mugging]: Eliezer Yudkowsky, "Pascal's Mugging: Tiny Probabilities of Vast Utilities". [LessWrong](https://www.lesswrong.com/posts/a5JAiTdytou3Jg749/pascal-s-mugging-tiny-probabilities-of-vast-utilities)
[^cite-karnofsky-eev]: Holden Karnofsky, "Why We Can't Take Expected Value Estimates Literally (Even When They're Unbiased)" (2011). [GiveWell](https://blog.givewell.org/2011/08/18/why-we-cant-take-expected-value-estimates-literally-even-when-theyre-unbiased/)
[^cite-karnofsky-cluster]: Holden Karnofsky, "Sequence Thinking vs. Cluster Thinking" (2014). [GiveWell](https://blog.givewell.org/2014/06/10/sequence-thinking-vs-cluster-thinking/)
[^cite-greaves-cluelessness]: Hilary Greaves, "Cluelessness". [PDF](https://users.ox.ac.uk/~mert2255/papers/cluelessness.pdf)

#### Question: Open
id:: 1a61f3e4-9c83-4904-a3e2-aa05f4e97cb0
content::
\## Phase 1: Recall

Without scrolling up, spend three minutes reconstructing the main failure modes from this lens. Try to recover at least four distinct ones. Do not worry about their names. Explain the problem in your own words.

force-feedback:: first
feedback-instructions::
Expected ideas include: dismissing small probabilities merely because they are small; treating enormous payoffs as decisive regardless of evidence quality; dismissing any large payoff as automatically Pascalian; ignoring uncertainty about the model generating a probability; treating a noisy extreme estimate as literally as a well-grounded one; allowing one fragile model to dominate all other perspectives; and treating all unknown downstream consequences as if they were the same kind of ignorance.

Treat the recall as a map, not a checklist. Respond once in 80 to 150 words. Credit distinct ideas even if the learner does not use the course's names. Correct conflations briefly and do not reteach.

#### Question: Open
id:: bd3d5b8d-39db-46f7-8022-f7ff435cc4a8
content::
\## Phase 2: Processing

Which danger currently worries you more in AI safety: underreacting because the evidence is unusual and uncertain, or overreacting because fragile models can generate enormous expected losses? You may reject the forced choice and say the framing is wrong.

What would you want to observe before moving your view substantially in either direction?

force-feedback:: first
feedback-instructions::
This is a genuine reflection, not a test. Do not push the learner toward either side. If they reject the framing, help them state the alternative clearly. If they choose a side, ask at most one precise question about what observation would change their view. Keep an internal turn counter and close after at most two tutor replies.

#### Question: Open
id:: 914e0f2d-3423-4206-a44b-035ca34a12ea
content::
\## Phase 3: Learning Question

An analyst says: "I estimate a 0.001 percent chance that Project X prevents human extinction. The future is astronomically valuable. Therefore Project X has overwhelming expected value. Even if I am 99.9 percent likely to be wrong, the remaining expected value is still enormous."

You are not being asked whether Project X is good. What would you need to know before allowing this calculation to dominate the decision? Identify the most important problems with the reasoning as stated.

force-feedback:: first
assessment-instructions::
Score out of 100.

30 points: The answer distinguishes the numerical estimate from confidence in the process or model that generated it.

25 points: The answer explains that fixed ad hoc probability discounts do not necessarily capture estimate error, priors, or how weak evidence should update beliefs.

20 points: The answer identifies the need for evidence about tractability or whether Project X actually changes the risk, rather than inferring priority from the size of extinction alone.

15 points: The answer mentions robustness across different assumptions, reference classes, or relatively independent lines of evidence.

10 points: The answer recognises that indirect or systemic consequences may point in multiple structured directions rather than simply cancel.

Do not require Bayesian terminology. Do not require agreement with Karnofsky's framework, cluster thinking, or a particular decision theory. An answer can criticise those approaches and receive full credit if it correctly diagnoses the missing information.

feedback-instructions::
Give 100 to 170 words of feedback. State which uncertainties the learner identified clearly and name the most important missing one if any. Do not praise generically and do not tell the learner that a particular level of AI concern is correct.

If the learner says they do not understand, give one concrete foothold by contrasting a precise risk estimate from repeated observations with an equally precise-looking number produced from several speculative guesses. If the next message still does not attempt the question, rephrase the task.
