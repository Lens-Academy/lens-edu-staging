---
title: "Complete Class: Consequentialist Foundations"
author:
  - "abramdemski"
source_url: "https://www.lesswrong.com/posts/sZuw6SGfmZHvcAAEP/complete-class-consequentialist-foundations"
published: 2018-07-11
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "The fundamentals of Bayesian thinking have been justified in many ways over the years. Most people here have heard of the VNM axioms and Dutch Book a…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The fundamentals of Bayesian thinking have been justified in many ways over the years. Most people here have heard of the VNM axioms and Dutch Book arguments. Far fewer, I think, have heard of the Complete Class Theorems (CCT).

Here, I explain why I think of CCT as a more purely consequentialist foundation for decision theory. I also show how complete-class style arguments play a role in social choice theory, justifying utilitarianism and a version of [futarchy](http://mason.gmu.edu/~rhanson/futarchy.html). This means CCT acts as a bridging analogy between single-agent decisions and collective decisions, therefore shedding some light on how a pile of agent-like pieces can come together and act like one agent. To me, this suggests a potentially rich vein of intellectual ore.

I have some ideas about modifying CCT to be more interesting for MIRI-style decision theory, but I'll only do a little of that here, mostly gesturing at the problems with CCT which could motivate such modifications.

---

# Background ^background

## My Motives ^my-motives

This post is a continuation of what I started in [Generalizing Foundations of Decision Theory](https://agentfoundations.org/item?id=1302) and [Generalizing Foundations of Decision Theory II](https://agentfoundations.org/item?id=1341). The core motivation is to understand the justification for existing decision theory very well, see which assumptions are weakest, and see what happens when we remove them.

There is also a secondary motivation in human (ir)rationality: to the extent foundational arguments are _real reasons_ why rational behavior is better than irrational behavior, one might expect these arguments to be helpful in teaching or training rationality. This is related to my criterion of consequentialism: the argument in favor of Bayesian decision theory should directly point to _why it matters_.

With respect to this second quest, CCT is interesting because Dutch Book and money-pump arguments point out irrationality in agents by _exploiting_ the irrational agent. CCT is more amenable to a model in which you point out irrationality by _helping_ the irrational agent. I am working on a more thorough expansion of that view with some co-authors.

## Other Foundations ^other-foundations

(Skip this section if you just want to know about CCT, and not why I claim it is better than alternatives.)

I give an overview of many proposed foundational arguments for Bayesianism in [the first post in this series](https://agentfoundations.org/item?id=1302). I called out Dutch Book and money-pump arguments as the most promising, in terms of motivating decision theory only from "winning". The [second post in the series](https://agentfoundations.org/item?id=1341) attempted to motivate all of decision theory from only those two arguments (extending work of Stuart Armstrong along those lines), and succeeded. However, the resulting argument was in itself not very satisfying. If you look at the structure of the argument, it justifies constraints on decisions via problems which would occur in hypothetical games involving money. [Many philosophers have argued](https://plato.stanford.edu/entries/dutch-book/#DutcBookArguProbCons) that the Dutch Book argument is in fact a way of illustrating inconsistency in belief, rather than truly an argument that you must be consistent or else. I think this is right. I now think this is a serious flaw behind both Dutch Book and money-pump arguments. There is no pure consequentialist reason to constrain decisions based on consistency relationships with thought experiments.

The position I'm defending in the current post has much in common with the paper [Actualist Rationality by C. Manski](https://afinetheorem.wordpress.com/2011/01/07/actualist-rationality-c-manski-2009/). My disagreement with him lies in his dismissal of CCT as yet another bad argument. In my view, CCT seems to address his concerns almost precisely!

Caveat --

Dutch Book arguments are _fairly_ practical. Betting with people, or asking them to consider hypothetical bets, is a useful tool. It may even be what convinces someone to use probabilities to represent degrees of belief. However, the argument falls apart if you examine it too closely, or at least requires extra assumptions which you have to argue in a different way. Simply put, belief is not literally the same thing as willingness to bet. Consequentialist decision theories are in the business of relating beliefs to actions, not relating beliefs to betting behavior.

Similarly, money-pump arguments can sometimes be extremely practical. The resource you're pumped of doesn't need to be money -- it can simply be the cost of thinking longer. If you spin forever between different options because you prefer strawberry ice cream to chocolate and chocolate to vanilla and vanilla to strawberry, you will not get any ice cream. However, the set-up to money pump _assumes_ that you will not notice this happening; whatever the extra cost of indecision is, it is placed outside of the considerations which can influence your decision.

So, Dutch Book "defines" belief as willingness-to-bet, and money-pump "defines" preference as willingness-to-pay; in doing so, both arguments put the justification of decision theory into hypothetical exploitation scenarios which are not quite the same as the actual decisions we face. If these were the best justifications for consequentialism we could muster, I would be somewhat dissatisfied, but would likely leave it alone. Fortunately, a better alternative exists: complete class theorems.

# Four Complete Class Theorems ^four-complete-class-theorems

For a thorough introduction to complete class theorems, I recommend [Peter Hoff's course notes](https://www2.stat.duke.edu/~pdh10/Teaching/581/LectureNotes/admiss.pdf). I'm going to walk through four complete class theorems dealing with what I think are particularly interesting cases. Here's a map:

  
![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img1-fa9144a0.png)  
 

In words: first we'll look at the standard setup, which assumes likelihood functions. Then we will remove the assumption of likelihood functions, since we want to argue for probability theory from scratch. Then, we will switch from talking about decision theory to social choice theory, and use CCT to derive a variant of Harsanyi's utilitarian theorem, AKA Harsanyi's social aggregation theorem, which tells us about cooperation between agents with common beliefs (but different utility functions). Finally, we'll add likelihoods back in. This gets us a version of Critch's [multi-objective learning framework](https://arxiv.org/abs/1711.00363), which tells us about cooperation between agents with different beliefs _and_ different utility functions.

I think of _Harsanyi's utilitarianism theorem_ as the best justification for utilitarianism, in much the same way that I think of CCT as the best justification for Bayesian decision theory. It is not an argument that _your personal values_ are necessarily utilitarian-altruism. However, it _is_ a strong argument for utilitarian altruism as the most coherent way to care about others; and furthermore, to the extent that groups can make rational decisions, I think it is an extremely strong argument that the group decision should be utilitarian. AlexMennen discusses the theorem and implications for CEV [here](https://www.lesswrong.com/posts/z8afQRsH9wWsB4iMD/harsanyi-s-social-aggregation-theorem-and-what-it-means-for).

I somewhat jokingly think of Critch's variation as "Critch's [Futarchy](http://mason.gmu.edu/~rhanson/futarchy.html) theorem" -- in the same way that Harsanyi shows that utilitarianism is the unique way to make rational collective decisions when everyone agrees about the facts on the ground, Critch shows that rational collective decisions when there is disagreement must involve a betting market. However, Critch's conclusion is not quite [Futarchy](http://mason.gmu.edu/~rhanson/futarchy.html). It is more extreme: in Critch's framework, agents bet their voting stake rather than money! The more bets you win, the more control you have over the system; the more bets you lose, the less your preferences will be taken into account. This is, perhaps, rather harsh in comparison to governance systems we would want to implement. However, rational agents of the classical Bayesian variety are happy to make this trade.

Without further adieu, let's dive into the theorems.

## Basic CCT ^basic-cct

We set up decision problems like this:

-   $\Theta$  is the set of possible states of the external world.
-   $X$ is the set of possible observations.
-   $A$ is the set of actions which the agent can take.
-   $F(x|\theta)$ is a likelihood function, giving the probability of an observation $x\in X$ under a particular world-state $\theta \in \Theta$.
-   $\mathcal{D}$ is a set of decision rules. For $\delta \in \mathcal{D}$, $\delta(x)$ outputs an action. Stochastic decision rules are allowed, though, in which case we should really think of it as outputting an action probability.
-   $L(\theta, a)$, the loss function, takes a world $\theta \in \Theta$ and an action $a \in A$ and returns a real-valued "loss". $L$ encodes preferences: the lower the loss, the better. One way of thinking about this is that the agent knows how its actions play out in each possible world; the agent is only uncertain about consequences because it doesn't know which possible world is the case.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img2-faa5dae9.png)

In this post, I'm only going to deal with cases where $\Theta$ and $X$ are finite. This is not a minor theoretical convenience -- things get significantly more complicated with unbounded sets, and the justification for Bayesianism in particular is weaker. So, it's potentially quite interesting. However, there's only so much I want to deal with in one post.

Some more definitions:

The _**risk**_ of a policy in a particular true world-state: $R(\theta, \delta)=\mathbb{E}_{F(x|\theta)}[L(\theta, \delta(x))]$.

A decision rule $\delta^*$ is a _**pareto improvement**_ over another rule $\delta$ if and only if $R(\theta, \delta) \geq R(\theta, \delta^*)$ for all $\theta$, and strictly > for at least one. This is typically called _**dominance**_ in treatments of CCT, but it's exactly parallel to the idea of pareto-improvement from economics and game theory: everyone is at least as well off, and at least one person is better off. An improvement which harms no one. The only difference here is that it's with respect to possible states, rather than people.

A decision rule $\delta$ is _**admissible**_ if and only if there is no pareto improvement over it. The idea is that there should be no reason not to take pareto improvements, since you're only doing better no matter what state the world turns out to be in. (We could also call this _pareto-optimal_.)

A class $C$ of decision rules is a _**complete class**_ if and only if for any rule _not_ in $C$, $\delta \notin C$, there exists a rule $\delta^*$ in $C$ which is a pareto improvement. Note, not every rule in a complete class will be admissible itself. In particular, the set of all decision rules is a complete class. So, the complete class is a device for proving a weaker result than admissibility. This will actually be a bit silly for the finite case, because we can characterize the set of admissible decision rules. However, it is the namesake of complete class theorems in general; so, I figured that it would be confusing not to include it here.

Given a probability distribution $\pi(\theta)$ on world-states, the _**Bayes risk**_ $r(\pi, \delta)$ is the expected risk over worlds, IE: $\mathbb{E}_{\pi(\theta)}R(\theta,\delta)$.

A probability distribution $\pi$ is _**non-dogmatic**_ when $\pi(\theta)>0$ for all $\theta$.

A decision rule is _**bayes-optimal**_ with respect to a distribution $\pi$ if it minimizes Bayes risk with respect to $\pi$. (This is usually called a _Bayes rule_ with respect to $\pi$, but that seems fairly confusing, since it sounds like "Bayes' rule" aka Bayes' theorem.)

**THEOREM:** _When_ $\Theta$ _and_ $A$ _are finite, decision rules which are bayes-optimal with respect to a non-dogmatic_ $\pi$ _are admissible._

**PROOF:** On the one hand, if $\delta$ is Bayes-optimal with respect to non-dogmatic $\pi$, it minimizes the expectation $\mathbb{E}_\pi (\theta)R(\theta,\delta)$. Since $\pi(\theta)>0$ for each world, any pareto-improvement $\delta'$ (which must be strictly better in some world, and not worse in any) must decrease this expectation. So, $\delta$ must be minimizing the expectation if it is Bayes-optimal. $\Box$

**THEOREM:** (basic CCT) _When_ $\Theta$ _and_ $A$ _are finite, a decision rule_ $\delta$ _is admissible if and only if it is Bayes-optimal with respect to some prior_ $\pi$.

**PROOF:** If $\delta$ is admissible, we wish to show that it is Bayes-optimal with respect to some $\pi$.

A decision rule has a risk in each world; think of this as a vector in $\mathbb{R}^{|\Theta|}$. The set $R$ of achievable risk vectors in $\mathbb{R}^{|\Theta|}$ (given by all $\delta$) is convex, since we can make mixed strategies between any two decision rules. It is also closed, since $A$ and $X$ are finite. Consider a risk vector $s$ as a point in this space (not necessarily achievable by any $\delta$). Define the _**lower quadrant**_ $Q(s)$ to be the set of points which would be pareto improvements if they were achievable by a decision rule. Note that for an admissible decision rule with risk vector $s$, $Q(s)$ and $R$ are disjoint. By the hyperplane separation theorem, there is a separating hyperplane $H$ between $Q(s)$ and $R$. We can define $\pi(\theta)$ by taking a vector normal to the hyperplane and normalizing it to sum to one. This is a prior for which $\delta$ is Bayes-optimal, establishing the desired result. $\Box$

If this is confusing, I again suggest [Peter Hoff's course notes](https://www.stat.washington.edu/people/pdhoff/courses/581/LectureNotes/admiss.pdf). However, here is a simplified illustration of the idea for two worlds, four pure actions, and no observations:

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img3-a6d393c4.png)

(I used $-R(\theta,\delta)$ because I am more comfortable with thinking of "good" as "up", IE, thinking in terms of utility rather than loss.)

The black "corners" coming from $\delta_2$ and $\delta_4$ show the beginning of the Q() set for those two points. (You can imagine the other two, for $\delta_1$ and $\delta_3$.) Nothing is pareto-dominated except for $\delta_4$, which is dominated by everything. In economics terminology, the first three actions are on the pareto frontier. In particular, $\delta_2$ is not pareto-dominated. Putting some numbers to it, $\delta_2$ could be worth (2,2), that is, worth two in each world. $\delta_1$ could be worth (1,10), and $\delta_3$ could be worth (10,1). There is no prior over the two worlds in which a Bayesian would want to take action $\delta_2$. So, how do we rule it out through our admissibility requirement? We add mixed strategies:

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img4-2bc68875.png)

Now, there's a new pareto frontier: the line stretching between $\delta_1$ and $\delta_3$, consisting of strategies which have some probability of taking those two actions. Everything else is pareto-dominated. An agent who starts out considering $\delta_2$ can see that mixing between $\delta_1$ and $\delta_3$ is just a better idea, no matter what world they're in. This is the essence of the CCT argument.

Once we move to the pareto frontier of the set of mixed strategies, we can draw the separating hyperplanes mentioned in the proof:

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img5-11db2120.png)

(There may be a unique line, or several separating lines.) The separating hyperplane allows us to derive a (non-dogmatic) prior which the chosen decision rule is consistent with.

## Removing Likelihoods (and other unfortunate assumptions) ^removing-likelihoods-and-other

Assuming the existence of a likelihood function $F$ is rather strange, if our goal is to argue that agents should use probability and expected utility to make decisions. A purported decision-theoretic foundation should not assume that an agent has any probabilistic beliefs to start out.

Fortunately, this is an extremely easy modification of the argument: restricting $F$ to either be zero or one is just a special case of the existing theorem. This does not limit our expressive power. Previously, a world in which the true temperature is zero degrees would have some probability of emitting the observation "the temperature is one degree", due to observation error. Now, we consider the error a part of the world: there is a world where the true temperature is zero and the measurement is one, as well as one where the true temperature is zero and the measurement is zero, and so on.

Another related concern is the assumption that we have mixed strategies, which are described via probabilities. Unfortunately, this is much more central to the argument, so we have to do a lot more work to re-state things in a way which doesn't assume probabilities directly. Bear with me -- it'll be a few paragraphs before we've done enough work to eliminate the assumption that mixed strategies are described by probabilities.

It will be easier to first get rid of the assumption that we have cardinal-valued loss $L$. Instead, assume that we have an ordinal preference for each world, $\delta_1 <_\theta \delta_2$. We then apply the VNM theorem within each $\theta$, to get a cardinal-valued utility within each world. The CCT argument can then proceed as usual.

Applying VNM is a little unsatisfying, since we need to assume the VNM axioms about our preferences. Happily, it is easy to weaken the VNM axioms, instead letting the assumptions from the CCT setting do more work. A detailed write-up of the following is being worked on, but to briefly sketch:

First, we can get rid of the independence axiom. A mixed strategy is really a strategy which involves observing coin-flips. We can put the coin-flips inside the world (breaking each $\theta$ into more sub-worlds in which coin-flips come out differently). When we do this, the independence axiom is a consequence of admissibility; any violation of independence can be undone by a pareto improvement.

Second, having made coin-flips explicit, we can get rid of the axiom of continuity. We apply the VNM-like theorem from the paper [Additive representation of separable preferences over infinite products](https://mpra.ub.uni-muenchen.de/28262/1/MPRA_paper_28262.pdf), by Marcus Pivato. This gives us cardinal-valued utility functions, but without the continuity axiom, our utility may sometimes be represented by infinities. (Specifically, we can consider surreal-numbered utility as the most general case.) You can assume this never happens if it bothers you.

More importantly, at this point we don't need to assume that mixed strategies are represented via pre-existing probabilities anymore. Instead, they're represented by the coins.

I'm fairly happy with this result, and apologize for the brief treatment. However, let's move on for now to the comparison to social choice theory I promised.

## Utilitarianism ^utilitarianism

I said that $\theta_i$ are "possible world states" and that there is an "agent" who is "uncertain about which world-state is the case" -- however, notice that I didn't really _use_ any of that in the theorem. What matters is that for each $\theta$, there is a preference relation on actions. CCT is actually about compromising between different preference relations.

If we drop the observations, we can interpret the $\theta_i$ as _people_, and the $A$ as potential collective actions. The $\delta$ are potential social choices, which are admissible when they are pareto-efficient with respect to individual's preferences.

Making the hyperplane argument as before, we get a $\pi$ which places positive weight on each individual. This is interpreted as each individual's weight in the coalition. The collective decision must be the result of a (positive) linear combination of each individual's cardinal utilities -- and those cardinal utilities can in turn be constructed via an application of VNM to individual ordinal preferences. This result is very similar to Harsanyi's utilitarianism theorem.

This is not only a nice argument for utilitarianism, it is also an amusing mathematical pun, since it puts utilitarian "social utility" and decision-theoretic "expected utility" into the same mathematical framework. Just because both can be derived via pareto-optimality arguments doesn't mean they're necessarily the same thing, though.

Harsanyi's theorem is not the most-cited justification for utilitarianism. One reason for this may be that it is "overly pragmatic": utilitarianism is about _values;_ Harsanyi's theorem is about _coherent governance_. Harsanyi's theorem relies on imagining a collective decision which has to compromise between everyone's values, and specifies what it must be like. Utilitarians don't imagine such a global decision can really be made, but rather, are trying to specify their own altruistic values. Nonetheless, a similar argument applies: altruistic values are enough of a "global decision" that, hypothetically, you'd want to run the Harsanyi argument if you had descriptions of everyone's utility functions and if you accepted pareto improvements. So there's an argument to be made that that's still what you want to approximate.

Another reason, mentioned by Jessicata in the comments, is that utilitarians typically value egalitarianism. Harsanyi's theorem only says that you must put _some_ weight on each individual, not that you have to be _fair._ I don't think this is much of a problem -- just as CCT argues for "some" prior, but realistic agents have further considerations which make them skew towards maximally spread out priors, CCT in social choice theory can tell us that we need _some_ weights, and there can be extra considerations which push us toward egalitarian weights. Harsanyi's theorem is still a strong argument for a big chunk of the utilitarian position.

## Futarchy ^futarchy

Now, as promised, Critch's 'futarchy' theorem.

If we add observations back in to the multi-agent interpretation, $F(x | \theta)$ associates each agent with a probability distribution on observations. This can be interpreted as each agent's beliefs. In the paper [Toward Negotiable Reinforcement Learning](https://arxiv.org/abs/1701.01302), Critch examined pareto-optimal sequential decision rules in this setting. Not only is there a function $\pi$ which gives a weight for each agent in the coalition, but _this_ $\pi$ _is updated via Bayes' Rule as observations come in._ The interpretation of this is that the agents in the coalition want to bet on their differing beliefs, so that agents who make more correct bets gain more influence over the decisions of the coalition.

This differs from Robin Hanson's futarchy, whose motto _"vote on values, but bet beliefs"_ suggests that everyone gets an equal vote -- you lose _money_ when you bet, which loses you influence on _implementation_ of public policy, but you still get an equal share of _value._ However, Critch's analysis shows that Robin's version can be strictly improved upon, resulting in Critch's version. (Also, Critch is not proposing his solution as a system of governance, only as a notion of multi-objective learning.) Nonetheless, the spirit still seems similar to Futarchy, in that the control of the system is distributed based on bets.

If Critch's system seems harsh, it is because we wouldn't really want to bet away all our share of the collective value, nor do we want to punish those who would bet away all their value too severely. This suggests that we (a) just _wouldn't_ bet everything away, and so wouldn't end up too badly off; and (b) would want to still take care of those who bet their own value away, so that the consequences for those people would not actually be so harsh. Nonetheless, we can also try to take the problem more seriously and think about alternative formulations which seem less strikingly harsh.

## Conclusion ^conclusion

One potential research program which may arise from this is: take the analogy between social choice theory and decision theory very seriously. Look closely at more complicated models of social choice theory, including voting theory and perhaps mechanism design. Understand the structure of rational collective choice in detail. Then, try to port the lessons from this back to the individual-agent case, to create decision theories more sophisticated than simple Bayes. Mirroring this on the four-quadrant diagram from early on:

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/abramdemski-complete-class-consequentialist-foundations-img6-1255a9da.png)

And, if you squint at this diagram, you can see the letters "CCT".

(Closing visual pun by Caspar Österheld.)
