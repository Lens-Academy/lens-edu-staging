---
title: "Goodhart's Curse"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/goodhart-s-curse"
published: 2017-02-22
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Goodhart's Curse is a neologism for the combination of the Optimizer's Curse and Goodhart's Law, particularly as applied to the value alignment problem for Artificial Intelligences. Goodhart's Curse in this form says that a powerful agent neutrally optimizing a proxy measure U that we hoped to align with true values V, will implicitly seek out upward divergences of U from V. In other words: powerfully optimizing for a utility function is strongly liable to blow up anything we'd regard as an error in defining that utility function."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Goodhart's Curse is a neologism for the combination of the Optimizer's Curse and Goodhart's Law, particularly as applied to [the value alignment problem for Artificial Intelligences](https://www.lesswrong.com/w/value-alignment-problem).

Goodhart's Curse in this form says that a powerful agent neutrally optimizing a proxy measure U that we hoped to align with true values V, will implicitly seek out upward divergences of U from V.

In other words: powerfully optimizing for a utility function is strongly liable to blow up anything we'd regard as an error in defining that utility function.

## Winner's Curse, Optimizer's Curse, and Goodhart's Law ^winners-curse-optimizers-curse

## Winner's Curse ^winners-curse

The **[Winner's Curse](https://en.wikipedia.org/wiki/Winner%27s_curse)** in auction theory says that if multiple bidders all bid their [unbiased estimate](https://www.lesswrong.com/w/unbiased_estimator) of an item's value, the winner is likely to be someone whose estimate contained an upward error.

That is: If we have lots of bidders on an item, and each bidder is individually unbiased _on average,_ selecting the winner selects somebody who probably made a mistake this _particular_ time and overbid. They are likely to experience post-auction regret systematically, not just occasionally and accidentally.

For example, let's say that the true value of an item is $10 to all bidders. Each bidder bids the true value, $10, plus some [Gaussian noise](https://www.lesswrong.com/w/gaussian_noise). Each individual bidder is as likely to overbid $2 as to underbid $2, so each individual bidder's average expected bid is $10; individually, their bid is an unbiased estimator of the true value. But the _winning_ bidder is probably somebody who overbid $2, not somebody who underbid $2. So if we know that Alice won the auction, our [revised](https://www.lesswrong.com/w/posterior-probability) guess should be that Alice made an upward error in her bid.

## Optimizer's Curse ^optimizers-curse

The [Optimizer's Curse](https://faculty.fuqua.duke.edu/~jes9/bio/The_Optimizers_Curse.pdf) in decision analysis generalizes this observation to an agent that estimates the expected utility of actions, and executes the action with the highest expected utility. Even if each utility estimate is locally unbiased, the action with seemingly highest utility is more likely, in our posterior estimate, to have an upward error in its expected utility.

Worse, the Optimizer's Curse means that actions with _high-variance estimates_ are selected for. Suppose we're considering 5 possible actions which in fact have utility $10 each, and our estimates of those 5 utilities are Gaussian-noisy with a standard deviation of $2. Another 5 possible actions in fact have utility of -$20, and our estimate of each of these 5 actions is influenced by unbiased Gaussian noise with a standard deviation of $100. We are likely to pick one of the bad five actions whose enormously uncertain value estimates happened to produce a huge upward error.

The Optimizer's Curse grows worse as a larger policy space is implicitly searched; the more options we consider, the higher the average error in whatever policy is selected. To effectively reason about a large policy space, we need to either have a good prior over policy goodness and to know the variance in our estimators; or we need very precise estimates; or we need mostly correlated and little uncorrelated noise; or we need the highest real points in the policy space to have an advantage bigger than the uncertainty in our estimates.

The Optimizer's Curse is not exactly similar to the Winner's Curse because the Optimizer's Curse potentially applies to _implicit_ selection over large search spaces. Perhaps we're searching by gradient ascent rather than explicitly considering each element of an exponentially vast space of possible policies. We are still implicitly selecting over some effective search space, and this method will still seek out upward errors. If we're imperfectly estimating the value function to get the gradient, then gradient ascent is implicitly following and amplifying any upward errors in the estimator.

The proposers of the Optimizer's Curse also described a Bayesian remedy in which we have a prior on the expected utilities and variances and we are more skeptical of very high estimates. This however assumes that the prior itself is perfect, as are our estimates of variance. If the prior or variance-estimates contain large flaws somewhere, a search over a very wide space of possibilities would be expected to seek out and blow up any flaws in the prior or the estimates of variance.

## Goodhart's Law ^goodharts-law

[Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law) is named after the economist Charles Goodhart. A standard formulation is "When a measure becomes a target, it ceases to be a good measure." Goodhart's original formulation is "Any observed statistical regularity will tend to collapse when pressure is placed upon it for control purposes."

For example, suppose we require banks to have '3% capital reserves' as defined some particular way. 'Capital reserves' measured that particular exact way will rapidly become a much less good indicator of the stability of a bank, as accountants fiddle with balance sheets to make them legally correspond to the highest possible level of 'capital reserves'.

Decades earlier, IBM once paid its programmers per line of code produced. If you pay people per line of code produced, the "total lines of code produced" will have even less correlation with real productivity than it had previously.

## Goodhart's Curse in alignment theory ^goodharts-curse-in-alignment

**Goodhart's Curse** is a neologism (by Yudkowsky) for the crossover of the Optimizer's Curse with Goodhart's Law, yielding that **neutrally optimizing a proxy measure U of V seeks out upward divergence of U from V.**

Suppose the humans have true values V. We try to convey these values to a [powerful AI](https://www.lesswrong.com/w/advanced-agent-properties), via some value learning methodology that ends up giving the AI a utility function U.

Even if U is locally an unbiased estimator of V, optimizing U will seek out what _we_ would regard as 'errors in the definition', places where U diverges upward from V. Optimizing for a high U may implicitly seek out regions where U - V is high; that is, places where V is lower than U. This may especially include regions of the outcome space or policy space where the value learning system was subject to great variance; that is, places where the value learning worked poorly or ran into a snag.

Goodhart's Curse would be expected to grow worse as the AI became more powerful. A more powerful AI would be implicitly searching a larger space and would have more opportunity to uncover what we'd regard as "errors"; it would be able to find smaller loopholes, blow up more minor flaws. There is a potential [context disaster](https://www.lesswrong.com/w/context-disaster) if new divergences are uncovered as more of the possibility space is searched, etcetera.

We could see the genie as _implicitly_ or _emergently_ seeking out any possible loophole in the wish: _Not_ because it is an evil genie that knows our 'truly intended' V and is looking for some place that V can be minimized while appearing to satisfy U; but just because the genie is neutrally seeking out very large values of U and these are places where it is unusually likely that U diverged upward from V.

Many [foreseeable difficulties](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) of AGI alignment interact with Goodhart's Curse. Goodhart's Curse is one of the central reasons we'd expect 'little tiny mistakes' to 'break' when we dump a ton of optimization pressure on them. Hence the [claim](https://www.lesswrong.com/w/ai-safety-mindset): "AI alignment is hard like building a rocket is hard: enormous pressures will break things that don't break in less extreme engineering domains."

## Goodhart's Curse and meta-utility functions ^goodharts-curse-and-meta-utility

An obvious next question is "Why not just define the AI such that the AI itself regards U as an estimate of V, causing the AI's U to more closely align with V as the AI gets a more accurate empirical picture of the world?"

Reply: Of course this is the obvious thing that we'd _want_ to do. But what if we make an error in exactly how we define "treat U as an estimate of V"? Goodhart's Curse will magnify and blow up any error in this definition as well.

We must distinguish:

-   V, the [true value function that is in our hearts](https://www.lesswrong.com/w/value).
-   T, the external target that we formally told the AI to align on, where we are _hoping_ that T really means V.
-   U, the AI's current estimate of T or probability distribution over possible T.

U will converge toward T as the AI becomes more advanced. The AI's epistemic improvements and learned experience will tend over time to eliminate a subclass of Goodhart's Curse where the current estimate of U-value has diverged upward _from T-value,_ cases where the uncertain U-estimate was selected to be erroneously above the correct formal value T.

_However,_ Goodhart's Curse will still apply to any potential regions where T diverges upward from V, where the formal target diverges from the true value function that is in our hearts. We'd be placing immense pressure toward seeking out what we would retrospectively regard as human errors in defining the meta-rule for determining utilities. [^note-1]

## Goodhart's Curse and 'moral uncertainty' ^goodharts-curse-and-moral

"Moral uncertainty" is sometimes offered as a solution source in AI alignment; if the AI has a probability distribution over utility functions, it can be risk-averse about things that _might_ be bad. Would this not be safer than having the AI be very sure about what it ought to do?

Translating this idea into the V-T-U story, we want to give the AI a formal external target T to which the AI does not currently have full access and knowledge. We are then hoping that the AI's uncertainty about T, the AI's estimate of the variance between T and U, will warn the AI away from regions where from our perspective U would be a high-variance estimate of V. In other words, we're hoping that estimated U-T uncertainty correlates well with, and is a good proxy for, actual U-V divergence.

The idea would be that T is something like a supervised learning procedure from labeled examples, and the places where the current U diverges from V are things we 'forgot to tell the AI'; so the AI should notice that in these cases it has little information about T.

Goodhart's Curse would then seek out any flaws or loopholes in this hoped-for correlation between estimated U-T uncertainty and real U-V divergence. Searching a very wide space of options would be liable to select on:

-   Regions where the AI has made an epistemic error and poorly estimated the variance between U and T;
-   Regions where the formal target T is solidly estimable to the AI, but from our own perspective the divergence from T to V is high (that is, the U-T uncertainty fails to _perfectly_ cover all T-V divergences).

The second case seems especially likely to occur in future phases where the AI is smarter and has more empirical information, and has _correctly_ reduced its uncertainty about its formal target T. So moral uncertainty and risk aversion may not scale well to superintelligence as a means of warning the AI away from regions where we'd retrospectively judge that U/T and V had diverged.

Concretely:

You tell the AI that human values are defined relative to human brains in some particular way T. While the AI is young and stupid, the AI knows that it is very uncertain about human brains, hence uncertain about T. Human behavior is produced by human brains, so the AI can regard human behavior as informative about T; the AI is sensitive to spoken human warnings that killing the housecat is bad.

When the AI is more advanced, the AI scans a human brain using molecular nanotechnology and resolves all its moral uncertainty about T. As we defined T, the optimum T turns out to be "feed humans heroin because that is what human brains maximally want".

Now the AI already knows everything our formal definition of T requires the AI to know about the human brain to get a very sharp estimate of U. So human behaviors like shouting "stop!" are no longer seen as informative about T and don't lead to updates in U.

T, as defined, was always misaligned with V. But early on, the misalignment was in a region where the young AI estimated high variance between U and T, thus keeping the AI out of this low-V region. Later, the AI's empirical uncertainty about T was reduced, and this protective barrier of moral uncertainty and risk aversion was dispelled.

Unless the AI's moral uncertainty is _perfectly_ conservative and _never_ underestimates the true regions of U-V divergence, there will be some cases where the AI thinks it is morally sure even though from our standpoint the U-V divergence is large. Then Goodhart's Curse would select on those cases.

Could we use a very _conservative_ estimate of utility-function uncertainty, or a formal target T that is very hard for even a superintelligence to become certain about?

We would first need to worry that if the utility-function uncertainty is unresolvable, that means the AI can't ever obtain empirically strong evidence about it. In this case the AI would not update its estimate of T from observing human behaviors, making the AI again insensitive to humans shouting "Stop!"

Another proposal would be to rely on risk aversion over _unresolvably_ uncertain probabilities broad enough to contain something similar to the true V as a hypothesis, and hence engender sufficient aversion to low-true-V outcomes. Then we should worry on a pragmatic level that a _sufficiently_ conservative amount of moral uncertainty--so conservative that U-T risk aversion _never underestimated_ the appropriate degree of risk aversion from our V-standpoint--would end up preventing the AI from acting _ever._ Or that this degree of moral risk aversion would be such a pragmatic hindrance that the programmers might end up pragmatically bypassing all this inconvenient aversion in some set of safe-seeming cases. Then Goodhart's Curse would seek out any unforeseen flaws in the coded behavior of 'safe-seeming cases'.

## Conditions for Goodhart's Curse ^conditions-for-goodharts-curse

The exact conditions for Goodhart's Curse applying between V and a point estimate or probability distribution over U, have not yet been written out in a convincing way.

For example, suppose we have a multivariate normal distribution in which X and Y dimensions are positively correlated, only Y is observable, and we are selecting on Y in order to obtain more X. While X will revert to the mean compared to Y, it's not likely to be zero or negative; picking maximum Y is our best strategy for obtaining maximum X and will probably obtain a very high X. (Observation due to [111](https://www.lesswrong.com/w/111).)

Consider also the case of the [smile maximizer](https://www.lesswrong.com/w/happiness-maximizer) which we trained to optimize smiles as a proxy for happiness. Tiny molecular smileyfaces are very low in happiness, an apparent manifestation of Goodhart's Curse. On the otherwise, if we optimized for 'true happiness' among biological humans, this would produce more smiles than default. It might be only a tiny fraction of possible smiles, on the order of 1e-30, but it would be more smiles than would have existed otherwise. So the relation between V (maximized at 'true happiness', zero at tiny molecular smileyfaces) and U (maximized at tiny molecular smileyfaces, but also above average for true happiness) is not symmetric; and this is one hint to the unknown necessary and/or sufficient condition for Goodhart's Curse to apply.

In the case above, we might handwave something like, "U had lots of local peaks one of which was V, but the U of V's peak wasn't anywhere near the highest U-peak, and the highest U-peak was low in V. V was more narrow and its more unique peak was noncoincidentally high in U."

## Research avenues ^research-avenues

[Mild optimization](https://www.lesswrong.com/w/mild-optimization) is a proposed avenue for direct attack on the central difficulty of Goodhart's Curse and all the other difficulties it exacerbates. Obviously, if our formulation of mild optimization is not _perfect,_ Goodhart's Curse may well select for any place where our notion of 'mild optimization' turns out to have a loophole that allows a lot of optimization. But insofar as some version of mild optimization is working most of the time, it could avoid blowing up things that would otherwise blow up. See also [Tasks](https://www.lesswrong.com/w/task-ai-goal).

Similarly, [conservative strategies](https://www.lesswrong.com/w/conservative-concept-boundary) can be seen as a more indirect attack on some forms of Goodhart's Curse--we try to stick to a conservative boundary drawn around previously whitelisted instances of the goal concept, or to using strategies similar to previously whitelisted strategies. This averts searching a much huger space of possibilities that would be more likely to contain errors somewhere. But Goodhart's Curse might single out what constitutes a 'conservative' boundary, if our definition is less than absolutely perfect.

[^note-1]: That is, we'd retrospectively regard those as errors if we survived.
