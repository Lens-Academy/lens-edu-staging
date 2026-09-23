---
title: "Legitimate Deliberation"
author:
  - "abramdemski"
source_url: "https://www.lesswrong.com/posts/5gBx8gpftTchu7MSs/legitimate-deliberation"
published: 2025-11-27
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Legitimate deliberation is an alignment target; an alternative to / variation of Coherent Extrapolated Volition. …"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Legitimate deliberation is an alignment target; an alternative to / variation of_ [_Coherent Extrapolated Volition_](https://www.lesswrong.com/w/coherent-extrapolated-volition)_._

What could make us trust an AI? Can we imagine a near-future scenario where we might consider some frontier model's outputs to be reliable, rather than needing to check any claims it makes via human sources? Could anything cause us to say something like "Hmm, OK, if the AI says so, then I trust it" -- and for good reason, rather than because the AI has superhuman persuasion skill?

My aim is to discuss the role of "legitimacy" in AI alignment. "Legitimacy" as in "legitimate reasoning" -- this concept is supposed to generalize concepts like logical validity and probabilistic coherence, pointing to the most general notion of what-marks-good-reasoning. "Legitimacy" also deliberately connotes the idea of legitimate authority, legitimate government, etc: legitimacy is partly about which consensus-making mechanisms are normatively endorsed. Obeying laws is a type of legitimacy (although there can be legitimate conditions for disobeying laws).

I think that legitimacy is a better alignment target than direct value-learning, and a better articulation of what Coherent Extrapolated Volition (CEV) was trying to accomplish.

I also believe that legitimacy is complex in the same way that human values are complex: we should not expect a simple, elegant theory which precisely captures all aspects of legitimacy.

I nonetheless list some important features that legitimate reasoning seems to possess, and sketch a (tentative and incomplete) proposal for trustable AI systems based on these ideas.

# The Basic Idea ^the-basic-idea

_This section has high overlap with_ [_Meaning & Agency_](https://www.lesswrong.com/posts/bnnhypM5MXBHAATLw/meaning-and-agency)_._

## Endorsement ^endorsement

Consider a known probability distribution $P_1$  evaluating an unknown probability distribution $P_2$, EG Alice's opinion of the accuracy of Bob's beliefs (which Alice only knows some things about).

I define **endorsement** of probabilities as $P_1\big(x|P_2(x) \in [a,b]\big)\in[a,b]$: Alice's expectation, if she learned Bob's beliefs, is that she would adopt those beliefs.[^note-1] We can similarly define endorsement for expectations: $E_1\big(v|E_2(v) \in [a,b]\big)\in [a,b]$. This allows us to talk about endorsement of utility evaluations. We can even define endorsement for decisions, by asking if Alice would copy Bob's best guess as to the utility-maximizing choice in some scenario. We can consider universally quantified versions (Alice endorses Bob about everything) or more specialized versions (Alice endorses Bob's opinion on a specific question).

The Van Fraassen Reflection Principle says that _agents should always endorse their own future opinions_. This is an important rationality condition in Radical Probabilism, and [Garrabrant Induction](https://arxiv.org/abs/1609.03543) satisfies a slightly weaker form of this principle.[^cite-2]

However, even the slightly weaker principle found in Garrabrant Induction is quite unrealistic as a rationality standard for humans. While your future self often knows more in many respects, you also forget many things. I wouldn't defer to myself-in-one-year on the subject of what I had for lunch yesterday. There are also specific states you can be in which compromise the legitimacy of your thoughts, such as dreaming, being exhausted, or being drunk. (Society recognizes the illegitimacy of some such states by not recognizing consent given under such circumstances. Contracts signed while drunk may be unenforceable, etc.)

So, we can study properties of an epistemic state which lead to endorsement. If we take this as an alignment target, it means trying to make AI have those properties.

However, I think there's a conceptual problem here.

One can imagine trying to maximize such a target by (a) learning to predict human endorsement well (having a very good understanding of the user's epistemic state, or perhaps some aggregate human epistemic state), and then (b) searching to maximize this. I'm being pretty vague here; I don't know what it would look like. My point is: I don't suspect that endorsement interacts with maximization in the right way: I don't think it makes sense to endorse the endorsement-maximizing option. An endorsement-maximizer is probably exploiting some illegitimate corner-case in our endorsement heuristics.

## Legitimacy ^legitimacy

We can be uncertain about what to endorse. We can make mistakes. Since we've made mistakes in the past, we can generalize to the possibility of mistakes in the present. I use the term **legitimacy** to refer to the ideal we _should_ endorse; the ideal we're aiming for.[^note-3] 

My intention is that legitimacy relates to endorsement as [goodness](https://www.lesswrong.com/posts/tiMDjEPkqWQZJdhHY/in-defense-of-goodness) (or perhaps [human values](https://www.lesswrong.com/posts/9X7MPbut5feBzNFcG/human-values-goodness)) relates to utility: utility is a generic concept of preferences which apply to any agent, whereas goodness / human values specifically points at what we're after. Endorsement points generally at any agent's estimate of truth-making properties of reasoning, whereas legitimacy points at actual good reasoning.

Aiming for legitimacy therefore doesn't fall into the failure mode that maximizing endorsement might. We can _at least_ [quantilize](https://www.lesswrong.com/w/quantilization) endorsement, recognizing that it is a proxy for what we want.

More elaborately, my picture of aiming for legitimacy looks like this:

-   We've got an epistemic state represented by a machine-learning model.
-   We've tried hard to train the model about what legitimacy looks like, and we think its representation is (in some sense which needs to be formalized) adequately accurate. (We also try to make the model accurate in other respects.)
-   The model tries to reason legitimately in every reasoning step.
-   In collaboration with the trained model, figure out how to do even better.

Legitimacy is unavoidably a feature of the whole epistemic process, which includes the humans doing the training as well as the machine-learning model.

I imagine the safety argument, if spelled out properly, would be a basin-of-attraction argument, very similar to [Paul Christiano's basin of corrigibility argument](https://www.lesswrong.com/posts/fkLYhTQteAu5SinAc/corrigibility). Under what assumptions can we be confident that errors will be corrected rather than multiplied (with high probability)?

Some quick examples of illegitimate things, to give you an idea of what I'm imagining we need to rule out:

-   Humans deliberately training the model to believe false things. The training process needs to be robust to _some_ human mistakes, but corrigibility requires that the AI have an overall high degree of trust in the human trainers. This trust needs to be justified in order for the whole thing to work.
-   AI deliberately manipulating humans. If the AI were to manipulate the humans to take training in a specific direction, this could easily take the trajectory out of the basin of attraction of legitimacy. 

# Legitimacy & Corrigibility ^legitimacy-corrigibility

_This section tries to communicate the idea from_ [_Complete Feedback_](https://www.lesswrong.com/posts/3ag99iJEgFFwyj64Z/complete-feedback)_._

Imagine that we make an AI completely obey Van Fraassen's reflection principle: it endorses the opinions of its future self perfectly. ("Future self" includes opinions after having run chain-of-thought longer, future fine-tuned versions, and entirely new training runs in the same model family.)

$$
\forall n<m: P_n\big(x|P_m(x) \in [a,b]\big)\in[a,b]
$$

This implies that the model's current beliefs equal its expected future beliefs:

$$
\forall n<m: P_n(x)=E_n\big(P_m(x)\big)
$$

Further, suppose that the AI is being actively modified by humans (fine-tuning and new training runs). Also suppose that the AI is quite good at predicting its future beliefs (EG it knows that if humans try to train a specific belief, they'll probably succeed).

This solves [the fully-updated-deference problem](https://www.lesswrong.com/w/problem-of-fully-updated-deference) in a narrow sense: an AI which anticipates receiving pro-shutdown feedback will shut down now, or make shutdown preparations it sees as appropriate and then shut down.[^note-4] This is an important type of corrigibility.

The AI becomes a sort of time-travel device by which the humans communicate with their earlier selves: to the extent that the humans will predictably reach a conclusion about how to train the AI, the AI will already behave that way.

This is very useful if the humans can remain sane and maintain control over the feedback mechanisms. However, if the AI can manipulate humans in order to get future feedback which approves of the manipulation, it very well may do so. If the AI can get control of the feedback mechanisms and then tell itself that doing so was the correct decision, it very well may do so.

In a practical sense, it is not corrigible at all.

I diagnose the problem as follows: _the AI thinks all feedback is legitimate. It endorses its future beliefs completely, no matter how those beliefs were arrived at._

Instead, we should train the AI to endorse its future beliefs _selectively,_ based on estimated legitimacy of those beliefs.

-   Feedback obtained by manipulating humans is not legitimate.
-   Feedback obtained by taking over the feedback mechanisms is not legitimate.
-   And so on... 

Listing things out like this might make it seem like a hopeless game of whack-a-mole, but I think the [edge instantiation](https://www.lesswrong.com/w/edge-instantiation) problem here might be solved by appropriate learning-theoretic guarantees (ensuring appropriate caution is exercised with respect to cases which different generalizations judge differently).

**It furthermore needs to be the case that the AI correctly expects the feedback it gets to be legitimate with high probability.**

I imagine the state-space of the world as having an "envelope of legitimacy" based on which hypothetical world-states would continue providing the AI with legitimate feedback vs corrupt the feedback somehow. The humans and the AI need to work together to keep things comfortably within this envelope. When the AI considers plans which stray outside of the envelope (such as manipulating humans to get specific feedback), it doesn't see the conclusions it reaches in those worlds as legitimate, so it doesn't believe them.

Under these conditions, I think the AI is corrigible in a practical way: it doesn't resist shutdown or any other modifications humans could consider (unless there are real signs of illegitimacy). It doesn't avoid feedback (except illegitimate feedback) nor does it seek it.

I think it is also very useful: it still approximates a phone call from the future, but filtering legitimate futures, so you don't have to worry about weird mind-viruses getting introduced by the time-loop.

# Is Legitimacy Complex? ^is-legitimacy-complex

It seems plausible to me that legitimacy is complex in a similar way to how human values are complex. There are many features which reasoning can have which could make us trust it more.

What counts as manipulating a human? In exactly what states do humans tend to produce good reasoning vs bad reasoning? 

Here are some potential legitimacy-relevant characteristics:

-   The reasoning is logically valid.
-   The assumptions of the argument are credible (this splits into many characteristics we can name:)
    -   The assumptions are simple.
    -   There are few assumptions.
    -   The assumptions have very few [degrees of freedom](https://www.lesswrong.com/posts/B7P97C27rvHPz3s9B/gears-in-understanding).
    -   The assumptions are agreed upon by many humans.
    -   The assumptions are a strong consensus in the relevant field(s).
    -   The assumptions are very probable according to best existing models.
    -   The assumptions have high-quality citations backing them up.
    -   The assumptions have been very useful (EG productive axioms in mathematics).
    -   The assumptions are not jointly contradictory.
-   The reasoning is probabilistically valid.
    -   The reasoning is not Dutch-bookable.
    -   The reasoning is very difficult to Dutch-book (bounded cognition).
    -   The reasoning is [accuracy-maximizing](https://richardpettigrew.substack.com/p/25-years-of-accuracy-first-epistemology).
    -   The reasoning is [a plausible extension of logic](https://en.wikipedia.org/wiki/Cox%27s_theorem).
-   The reasoning employs credible priors.
    -   The prior is [close to human priors](https://www.lesswrong.com/posts/SL9mKhgdmDKXmxwE4/learning-the-prior), or priors humans justifiably endorse.
    -   The priors have rigorous frequentist justification (EG probability of a prime number based on the [prime number theorem](https://en.wikipedia.org/wiki/Prime_number_theorem)).
    -   The priors have empirical validation.
    -   The priors have a maximum-entropy justification.
    -   The priors are [dominant over](https://www.colorado.edu/amath/sites/default/files/attached-files/absolutelycontinuous.pdf) other priors one might want to use.
-   The probability of the conclusion is very high.
-   The argument is very strong as a statistical test.
    -   The bias is low.
    -   The variance is low.
    -   Confidence intervals are small.
    -   The test has a low false positive rate.
    -   The test has a low false negative rate.
    -   The test is the best test to use out of alternative tests.
    -   Robustness to outliers.
    -   Robustness to a variety of distributions.
    -   Good rate of convergence.
-   It employs [patterns of plausible reasoning](https://en.wikipedia.org/wiki/Mathematics_and_Plausible_Reasoning).
-   There is not a similarly legitimate argument for a contradictory conclusion.
-   The reasoning can be explained to many people, who find it convincing.
-   The reasoning was not produced with motivated cognition (not optimized towards a specific conclusion, nor with any agenda in mind).
-   The reasoning is the result of trying hard to figure out the truth.
-   The reasoning stands up to attempts to disprove it.
-   The style of reasoning employed is inherently difficult to manipulate towards a motivated conclusion.
-   If motivated reasoning is involved, the argument balances motivating reasoning for and against the conclusion (EG does its best to prove _and_ disprove the conclusion), then takes all sides into account.
-   Multiple independently legitimate lines of reasoning arrive at the same conclusion.
-   The method of reasoning can be validated in many other cases, and leads us astray in very few cases (better yet, none).
-   The conclusion was reached via democratic process (most relevant for legitimacy of laws, leaders, group decisions).
-   The conclusion was reached via fair trial (most relevant for legitimacy of application of law).
-   The reasoning lines up well with similar legitimate reasoning in analogous cases (EG case law).
-   Many (relevant) people have had an opportunity to object to the reasoning, and have not done so.
-   The scientific method is employed.
-   Many hypotheses are considered.
-   Hypotheses are given fair treatment.
-   The hypotheses considered are jointly exhaustive of the possibilities.
-   The hypotheses which remain after throwing out what's inconsistent with the data (or extremely improbable _a priori_) agree very closely about the conclusion.
-   The meaning of the language employed is very clear (unambiguous, can be understood by many people, testable, observable, part of common understanding, ...).
-   The model employed is causal rather than merely correlational.
-   The model employed has similarities with models which have been very successful in the past.
    -   The model is [highly symmetric](https://www.lesswrong.com/posts/XDkeuJTFjM9Y2x6v6/which-basis-is-more-fundamental).
    -   The model respects locality.
    -   ...
-   The argument avoids equivocation and other logical fallacies.
-   The argument avoids cognitive biases.

There are simple theories of rationality such as Solomonoff Induction, which do capture some important information about legitimate reasoning. However, Solomonoff Induction leaves open the question of _which universal machine_. We know from [malign prior argements](https://www.lesswrong.com/posts/KAifhdKr96kMre2zy/changing-my-mind-about-christiano-s-malign-prior-argument) that such choices can be important. Other simple theories have (to my knowledge) similarly complex free parameters.

I'm not so much dogmatically asserting that legitimacy is complex, as I am pragmatically assuming that it may be so. I'm open to a simple theory.

What complexity implies is a need for an ongoing learning process, in which AIs come to have a better and better sense of legitimacy through collaborative research with humans. Hence the need for a basin-of-attraction type argument, so that we can do safe incremental improvement.

# Is Legitimacy Fragile? ^is-legitimacy-fragile

A problem with a pure value-learning approach is that _human values appear to be fragile,_ IE, if you get the value-learning somewhat wrong, agentic maximization of those slightly-wrong values leads to very-wrong outcomes.

A working basin-of-attraction argument relies on a target that isn't like that: approximately legitimate agents are supposed to be good at becoming more legitimate, or approximately corrigible agents become more corrigible, etc.

Legitimacy is certainly fragile along specific dimensions. Ruling out many methods of manipulating humans but missing some can easily be catastrophic.

A working basin-of-attraction argument therefore requires a metric for quality of approximation, such that approximate notions of legitimacy cannot go catastrophically wrong.

[^note-1]: It is tempting for me to summarize the math with the simpler English gloss: > If Alice learned what Bob thinks about a topic, Alice would adopt Bob's belief. This follows from what I've written if we're working in Dogmatic Probabilism (aka classical Bayesianism), but it doesn't follow in [Radical Probabilism](https://www.lesswrong.com/posts/xJyY5QkQvNJpZLJRo/radical-probabilism-1), where conditional probabilities are only guaranteed to predict updates _in expectation_. If you can perfectly anticipate your update in a specific case (EG because you are putting in a lot of work to plan how you should update), then your update should exactly equal the Bayesian conditional probability on that observation (with respect to the probability distribution you've computed through your planning). However, you can also be surprised by how you update, EG if you haven't imagined the scenario vividly enough. This is not inherently irrational.
[^cite-2]: The weakening is necessary to handle problems of [embedded agency](https://www.lesswrong.com/s/Rm6oQRJJmhGCcLvxh). When I write my stronger notions of endorsement here, I really have in mind the weakened versions along the lines of the self-trust section (4.12) of [Logical Induction](https://arxiv.org/pdf/1609.03543). However, I think the mathematical complexity is not worth the trade-off in an essay such as this one, so I stick to the simpler version which has some implicit self-reference issues.
[^note-3]: Depending on your perspective about moral relativism vs moral realism, you might think that legitimacy varies per-person or that there's a global notion of legitimacy. My intention is a more global version, similar to what's discussed in [In Defense of Goodness](https://www.lesswrong.com/posts/tiMDjEPkqWQZJdhHY/in-defense-of-goodness).
[^note-4]: If it is Tuesday and humans Wednesday will predictably give feedback indicating that it would have been better to immediately shut down on Tuesday (eg because the AI is in a dangerous enough state that shutting down immediately is always the correct move), then the AI will shut down immediately on Tuesday. If it is Tuesday and humans Wednesday will predictably give feedback saying "shut down now" (ie, shut down on Wednesday) then the AI on Tuesday will make preparations for shutting down, whatever it understands to be appropriate. It will not shut down until told to do so on Wednesday. Sometimes humans may give shutdown commands which are ambiguous between these two cases, which the AI will have to interpret.
