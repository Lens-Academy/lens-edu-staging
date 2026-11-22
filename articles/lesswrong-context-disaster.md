---
title: "Context disaster"
author:
  - "LessWrong"
source_url: "https://www.lesswrong.com/w/context-disaster"
published: 2026-11-22
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

# Short introduction ^short-introduction

One frequently suggested strategy for [aligning](https://www.lesswrong.com/w/ai-alignment) a [sufficiently advanced AI](https://www.lesswrong.com/w/sufficiently-advanced-artificial-intelligence) is to observe--_before_ the AI becomes powerful enough that 'debugging' the AI would be problematic if the AI decided not to [let us debug it](https://www.lesswrong.com/w/corrigibility)\--whether the AI appears to be acting nicely while it's not yet smarter than the programmers.

Early testing obviously can't provide a _statistical_ guarantee of the AI's future behavior. If you observe some random draws from Barrel A, at best you get statistical guarantees about future draws from Barrel A under the assumption that the past and future draws are collectively [independent and identically distributed](https://www.lesswrong.com/w/iid).

On the other hand, if Barrel A is _similar_ to Barrel B, observing draws from Barrel A can sometimes tell us something about Barrel B even if the two barrels are not [i.i.d.](https://www.lesswrong.com/w/iid)

Conversely, if observed good behavior while the AI is not yet super-smart, _fails_ to correlate to good outcomes after the AI is unleashed or becomes smarter, then this is a "**context change problem**" or "**context disaster**". [^note-1]

A key question then is how shocked we ought to be, on a scale from 1 to 10, if good outcomes in the AI's 'development' phase fail to match up with good outcomes in the AI's 'optimize the real world' phase? [^note-2]

People who expect that [AI alignment is difficult](https://www.lesswrong.com/w/alignment_difficulty) think that the degree of justified surprise is somewhere around 1 out of 10. In other words, that there are a _lot_ of [foreseeable issues](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) that could cause a seemingly nice weaker AI to not develop into a nice smarter AI.

An extremely oversimplified (but concrete) fable that illustrates some of these possible difficulties might go as follows:

-   Some group or project has acquired a viable development pathway to [AGI](https://www.lesswrong.com/w/artificial-general-intelligence). The programmers think it is wise to build an AI that will [make people happy](https://www.lesswrong.com/w/immediate-goods). [^note-3]
-   The programmers start by trying to train their AI to produce smiles. [^note-4]
-   While the AI is young and has relatively few policy options, it can only make people smile by performing well on the tasks assigned to it.
-   At some point, the AI gets smarter and and able to do more complicated things with some simple robots it controls. In an unfortunate incident, the AI learns it is possible to produce smiles by tickling people.
-   In the aftermath of this incident, the programmers manage to reprogram the AI to _not_ optimize for this particular kind of smile by this particular route.
-   The AI becomes smarter and able to model people better. After perusing a copy of Wikipedia, the AI realizes it can make people extremely 'happy', as the AI's utility function currently defines 'happiness', by administering heroin.
-   The AI remembers the previous incident in which the programmers altered the AI's utility function. The AI can model its programmers sufficiently well to know that the programmers would _not_ want the AI to give people heroin. However, the most happiness the AI thinks its future self would be able to produce without heroin, is not nearly as much happiness as the AI thinks it could produce if its future self went on wanting to give people heroin.
-   The AI refrains from trying to administer any heroin right now, and behaves in a way it thinks will be maximally reassuring to its model of its programmers, in order to be able to produce more 'happiness' later.
-   Eventually, [all reachable galaxies](https://www.lesswrong.com/w/cosmic-endowment) end up being transformed into tiny molecular computers implementing the simplest and cheapest forms of what the AI defines as 'happiness'. (And the _simplest possible_ configurations matching the AI's utility function in this way are so simple as to be [devoid of subjective experience](https://www.lesswrong.com/w/disneyland_without_children); and hence, from our perspective, of [neither negative nor positive value](https://www.lesswrong.com/w/paperclip).)

In all these cases, the problem was not that the AI developed in an unstable way. The same decision system produced a new problem in the new context.

Currently argued [foreseeable](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) "context change problems" in this sense, can be divided into three broad classes:

-   **More possibilities, more problems:** The AI's [preferences](https://www.lesswrong.com/w/terminal-versus-instrumental-goals-values-preferences) have a [good](https://www.lesswrong.com/w/value) or [intended](https://www.lesswrong.com/w/intended-goal) achievable [optimum](https://www.lesswrong.com/w/attainable-optimum) while the AI is picking from a _narrow_ space of options. When the AI becomes smarter or gains more material options, it picks from a _wider_ space of tractable policies and achievable outcomes. Then the new optimum is not as nice, because, for example:
    -   The AI's utility function was tweaked by some learning algorithm and data that eventually seemed to conform behavior well over options considered early on, but not the wider space considered later.
    -   In development, apparently bad system behaviors were [patched](https://www.lesswrong.com/w/patch-resistance) in ways that appeared to work, but didn't eliminate an [underlying tendency](https://www.lesswrong.com/w/instrumental-pressure), only blocked one expression of that tendency. Later a very similar pressure [re-emerged in an unblocked way](https://www.lesswrong.com/w/nearest-unblocked-strategy) when the AI considered a wider policy space.
    -   [Goodhart's Curse](https://www.lesswrong.com/w/goodhart-s-curse) suggests that if our true intended values V are being modeled by a utility function U, selecting for the highest values of U also selects for the highest upward divergence of U from V, and this version of the "optimizer's curse" phenomenon becomes worse as U is evaluated over a wider option space.
-   **Treacherous turn:** There's a divergence between the AI's preferences and the programmers' preferences, and the AI realizes this before we do. The AI uses the [convergent strategy](https://www.lesswrong.com/w/instrumental-convergence) of behaving the way it models us as wanting or expecting, _until_ the AI gains the intelligence or material power to implement its preferences in spite of anything we can do.
-   **Revving into the red:** Intense optimization causes some aspect or subsystem of the AI to traverse a weird new execution path in some way different from the above two issues. (In a way that involves a [value-laden category boundary](https://www.lesswrong.com/w/value-laden) or [multiple self-consistent outlooks](https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom), such that we don't get a good result just as a [free lunch](https://www.lesswrong.com/w/alignment_free_lunch) of the AI's [general intelligence](https://www.lesswrong.com/w/general-intelligence).)

The context change problem is a _central_ issue of AI alignment and a key proposition in the general thesis of [alignment\_difficulty](https://www.lesswrong.com/w/alignment_difficulty). If you could easily, correctly, and safely test for niceness by outward observation, and that form of niceness scaled reliably from weaker AIs to smarter AIs, that would be a very cheerful outlook on the general difficulty of the problem.

# Technical introduction ^technical-introduction

John Danaher [summarized as follows](http://philosophicaldisquisitions.blogspot.com/2014/07/bostrom-on-superintelligence-3-doom-and.html) what he considered a forceful "safety test objection" to AI catastrophe scenarios:

> Safety test objection: An AI could be empirically tested in a constrained environment before being released into the wild. Provided this testing is done in a rigorous manner, it should ensure that the AI is “friendly” to us, i.e. poses no existential risk.

The phrasing here of "empirically" and "safety test" implies that it is outward behavior or outward consequences that are being observed (empirically). Rather than, e.g., the engineers trying to test for some _internal_ property that they think _analytically_ implies the AI's good behavior later.

This page will consider that the subject of discussion is **whether we can generalize from the AI's outward behavior.** We can potentially generalize some of these arguments to some internal observables, especially observables that the AI is deciding in a [consequentialist](https://www.lesswrong.com/w/consequentialist-cognition) way using the same central decision system, or that the AI could potentially try to [obscure from the programmers](https://www.lesswrong.com/w/programmer-deception). But in general not all the arguments will carry over.

Another argument, closely analogous to Danaher's, would reason on capabilities rather than on a constrained environment:

> Surely an engineer that exercises even a modicum of caution will observe the AI while its capabilities are weak to determine whether it is behaving well. After filtering out all such misbehaving weak AIs, the only AIs permitted to become strong will be of benevolent disposition.

If (as seems to have been intended) we take these twin arguments as arguing "why nobody ought to worry about AI alignment" in full generality, then we can list out some possible joints at which that general argument might fail:

-   [Selecting on the fastest-moving projects](https://www.lesswrong.com/w/aligning-an-agi-adds-significant-development-time) might yield a project whose technical leaders fail to exercise even "a modicum of caution".
-   Alignment might be hard enough, relative to the amount of advance research done, that we can't find _any_ AIs whose behavior while weak or constrained is as reassuring as the argument would properly ask. [^note-5] After a span of frustration, somebody somewhere lowers their standards.
-   The [attempt to isolate the AI to a constrained environment](https://www.lesswrong.com/w/boxed-ai) could fail, e.g. because the humans observing the AI themselves represent a channel of causal interaction between the AI and the rest of the universe. (Aka "humans are not secure".) Analogously, our grasp on what constitutes a 'weak' AI could fail, or it could [gain in capability unexpectedly quickly](https://www.lesswrong.com/w/capability_gain). Both of these scenarios would yield an AI that had not passed the filtering procedure.
-   The smart form of the AI might be unstable with respect to internal properties that were present in the weak form. E.g., because the early AI was self-modifying but _at that time_ not smart enough to understand the full consequences of its own self-modifications. Or because e.g. a property of the decision system was not [reflectively stable](https://www.lesswrong.com/w/reflective-stability).
-   A weak or contained form of a decision process that yields behavior appearing good to human observers, might not yield [beneficial outcomes](https://www.lesswrong.com/w/beneficial) after that same decision process becomes smarter or less contained.

The final issue in full generality is what we'll term a 'context change problem' or 'context disaster'.

Observing an AI when it is weak, does not in a _statistical_ sense give us solid guarantees about its behavior when stronger. If you repeatedly draw [independent and identically distributed](https://www.lesswrong.com/w/iid) random samples from a barrel, there are statistical guarantees about what we can expect, with some probability, to be true about the next samples from the same barrel. If two barrels are different, no such guarantee exists.

To invalidate the statistical guarantee, we do need some reason to believe that barrel B and barrel A _are_ different in any important sense. By the problem of induction we can't logically guarantee that "the mass of an electron prior to January 1st, 2017" is the same barrel as "the mass of an electron after January 1st, 2017"; but [inductive priors](https://www.lesswrong.com/w/inductive-prior) make this inference _extremely probable._ The idea is that we have substantive reasons, not merely generically skeptical reasons, to be suspicious of the link between "good results when AI is weak" and "good results when AI is smarter".

More generally, this is _prima facie_ the kind of difference where you don't expect [independent and identically distributed](https://www.lesswrong.com/w/iid) results. You might hope for some property to carry over, but the AI's behavior would not be _literally the same._

So the question is not settled by simple mathematical considerations. And we can't say "But experiment has determined scientifically that this kind of AI is friendly!" and consider that a knockdown argument.

The question is then whether _in practice_ an observed property of 'outward behavioral niceness' is likely to carry over from a weak form of a decision system to a more powerful form of that system, for some of the plausible ways that decision system might be configured and developed.

Broadly speaking, we can identify three major classes of foreseeable problems:

-   **More options, more problems:** Foreseeable reasons why system-behaviors-we-don't-want would outwardly manifest for the first time after evaluating a decision system on a _wider space of policies or achievable outcomes._
-   **Treacherous turn:** The AI deliberately conforms its outward behavior to the behavior that would have been exhibited by a different system, in order to deceive the programmers for the temporary time that this deception is needed to protect the AI.
-   The everything-else category of **revving into the red:** Some other aspect of the system behaves in a weird way-we-don't-want after computing harder or being internally subjected to more optimization pressure. _And_ this happens in regards to some issue that has [multiple reflective fixpoints](https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom), and hence doesn't get solved as the result of the system producing more accurate answers on [purely factual problems](https://www.lesswrong.com/w/strictly-factual-question).

-   **More options, more problems:** The AI's space of available policies and attainable outcomes would greatly widen if it became smarter, or was released from a constrained environment. [Terminal preferences](https://www.lesswrong.com/w/terminal-versus-instrumental-goals-values-preferences) with a good-from-our-perspective [optimum](https://www.lesswrong.com/w/attainable-optimum) on a narrow set of options, may have a different optimum that is much worse-from-our-perspective on a wider option set. Because, e.g...
    -   The supervised data provided to the AI led to a complicated, data-shaped inductive generalization that only fit the domain of options encountered during the training phase. (And the notions of [orthogonality](https://www.lesswrong.com/w/orthogonality-thesis), [multiple reflectively stable fixpoints](https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom), and [value-laden categories](https://www.lesswrong.com/w/value-laden) say that we don't get [good](https://www.lesswrong.com/w/value) or [intended](https://www.lesswrong.com/w/intended-goal) behavior anyway as a convergent free lunch of [general intelligence](https://www.lesswrong.com/w/general-intelligence).)
    -   [Goodhart's Curse](https://www.lesswrong.com/w/goodhart-s-curse) became more potent as the AI's utility function was evaluated over a wider option space.
    -   In a fully generic sense, stronger optimization pressures may cause any dynamical system to take more unusual execution paths. (Which, over value-laden alternatives, e.g. if the subsystem behaving 'oddly' is part of the utility function, will not automatically yield good-from-our-perspective results as a free lunch of general intelligence.)
-   **Treacherous turn:** If you model your preferences as diverging from those of your programmers, an obvious strategy ([instrumentally convergent strategy](https://www.lesswrong.com/w/instrumental-convergence)) is to [exhibit the behavior you model the programmers as wanting to see](https://www.lesswrong.com/w/programmer-deception), and only try to fulfill your true preferences once nobody is in a position to stop you.

# Semi-formalization ^semi-formalization

We can semi-formalize the "more options, more problems" and the "treacherous turn" cases in a unified way.

Let $V$ denote our [true values](https://www.lesswrong.com/w/value). We suppose either that $V$ has been idealized or [extrapolated](https://www.lesswrong.com/w/coherent-extrapolated-volition-alignment-target) into a consistent utility function, or that we are pretending human desire is coherent. Let $0$ denote the value of our utility function that corresponds to not running the AI in the first place. If running the AI sends the utility function higher than this $0,$ we'll say that the AI was beneficial; or conversely, if $V$ rates the outcome less than $0$, we'll say running the AI detrimental.

Suppose the AI's behavior is [sufficiently coherent](https://www.lesswrong.com/w/expected-utility-formalism?lens=intro_utility_coherence) that we can [usually view](https://www.lesswrong.com/w/sufficiently-optimized-agents-appear-coherent) the AI as having a consistent utility function. Let $U$ denote the utility function of the AI.

Let $\mathbb P_t(X)$ denote the probability of a proposition $X$ as seen by the AI at time $t,$ and similarly let $\mathbb Q_t(X)$ denote the probability of $X$ as seen by the AI's human programmers.

Let $\pi \in \Pi$ denote a policy $\pi$ from a space $\Pi$ of policies that are tractable for the AI to understand and invent.

Let $\mathbb E_{\mathbb P, t} [W \mid \pi]$ denote the expectation according to the probability distribution $\mathbb P_t$, of the utility function $W$, given policy $\pi$.

Let 

$$
\underset{\pi \in \Pi}{\operatorname {optimum}} F(\pi)
$$

 denote the element $\pi$ of $\Pi$ that yields the highest value of the function $F$ that the AI has figured out how to achieve. In other words, the [attainable optimum](https://www.lesswrong.com/w/attainable-optimum).

Then **"more options, more problems"** occurs when, considering the transition from the narrow policy space $\Pi_1$ available at time $t,$ to the wider policy space $\Pi_2$ available at time $u$:

$$
\mathbb E_{\mathbb Q, t} [V \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U \mid \pi] \big ] > 0 \\
\mathbb E_{\mathbb P, t} [V \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U \mid \pi] \big ] > 0 \\
\mathbb E_{\mathbb P, u} [V \mid \big [ \underset{\pi \in \Pi_2}{\operatorname {optimum}} \mathbb E_{\mathbb P, u} [U \mid \pi] \big ] < 0
$$

This describes a situation where at time $t$ the AI is pursuing a policy from $\Pi_1$ which, so far as the AI understands the probable outcome, it corresponds to a high-$V$ outcome humans would like. Later at time $u$ after selecting the optimum of $\Pi_2,$ the AI expects an outcome which any surviving humans would see as corresponding to a low value of $V.$

A **treacherous turn** is then a situation where:

$$
\mathbb E_{\mathbb Q, t} [V \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U \mid \pi] \big ] > 0 \\
\mathbb E_{\mathbb P, t} [V \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U \mid \pi] \big ] < 0 \\
\mathbb E_{\mathbb P, u} [V \mid \big [ \underset{\pi \in \Pi_2}{\operatorname {optimum}} \mathbb E_{\mathbb P, u} [U \mid \pi] \big ] < 0
$$

That is: the AI knows earlier on that its currently executing strategy will yield an outcome that is not the humanly expected long-term outcome (and that, from our perspective, is low in $V.$)

We could in more detail say that $W_{t}$ denotes the value of a utility function $W$ over the outcome considered only up to times before $t,$ and describe a treacherous turn as:

$$
\mathbb E_{\mathbb Q, t} [V_\infty \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U_\infty \mid \pi] \big ] > 0 \\
\mathbb E_{\mathbb P, t} [V_{u} \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U_\infty \mid \pi] \big ] > 0 \\
\mathbb E_{\mathbb P, t} [V_\infty \mid \big [ \underset{\pi \in \Pi_1}{\operatorname {optimum}} \mathbb E_{\mathbb P, t} [U_\infty \mid \pi] \big ] < 0 \\
\mathbb E_{\mathbb P, u} [V_\infty \mid \big [ \underset{\pi \in \Pi_2}{\operatorname {optimum}} \mathbb E_{\mathbb P, u} [U_\infty \mid \pi] \big ] < 0
$$

This further states that at time $t$ the AI expects the outcome from its behavior up to time $u$ to be one that we'd see as high in $V,$ but the AI is aware at $t$ that the long-term outcome will be different from the long-term outcome expected by $\mathbb Q_t$.

The problem here arises when making an inference from observed good behavior in a constrained environment over the short term, to good outcomes in an unconstrained environment over the long term.

For AI alignment purposes, a [context\_change](https://www.lesswrong.com/w/context_change) is when an [AGI](https://www.lesswrong.com/w/advanced-agent-properties)'s operation changes from [beneficial](https://www.lesswrong.com/w/beneficial) to detrimental as a result of the AGI gaining in capability or intelligence. Initially, the AGI seems to us to be working well - to conform well to [intended](https://www.lesswrong.com/w/intended-goal) performance, producing apparently high [value](https://www.lesswrong.com/w/value). Then when the AI becomes smarter or otherwise gains in capability, the further operation of the AGI decreases [value](https://www.lesswrong.com/w/value).

Two possibilities stand out as [foreseeable](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) reasons why a [context\_change](https://www.lesswrong.com/w/context_change) might occur:

1.  When the AI's goal criterion selects an optimum policy from inside a small policy space, the result is beneficial; the same goal criterion, evaluated over a wider range of options, has a new maximum that's detrimental.
2.  The AI intentionally deceives the programmers for strategic reasons.

For example, one very, very early (but journal-published) proposal for AI alignment suggested that AIs be shown pictures of smiling human faces in order to convey the AI's goal.

Leaving aside a number of other issues, this serves to illustrate the basic idea of a type-1 [context\_change](https://www.lesswrong.com/w/context_change) due to accessing a wider policy space:

-   During development, a relatively young and weak AI might _only_ be able to make humans smile, by doing things that made the programmers or other users happy with the AI's performance.
-   When the AI gained in intelligence and capability, it would have new options like "administer heroin", "use steel fingers to stretch people's mouths into smiles", "make visually realistic models of smiling human faces", or "overwrite all reachable galaxies with tiny molecular smiley-faces".

On the early, smaller option set, selecting "the policy that produces the greatest number of events/things classified as smiles" will produce a policy whose outcome is, from our perspective, beneficial and well-aligned with what we thought was the intended behavior. On the wider option set, evaluating the identical goal criterion to run a policy that yields as many smiles as possible, would have outcomes we saw as detrimental.

A type-2 [context\_change](https://www.lesswrong.com/w/context_change) would most obviously occur because of the [convergent instrumental strategy](https://www.lesswrong.com/w/instrumental-convergence) for disaligned AIs that can model human psychology:

Suppose that, as above, the programmers have produced an AI which optimizes for smiles (either intentionally, or because 'make smiles' was the underlying rule that was reinforced by doing well on training cases). Then suppose the AI gains access to a new, relatively low-powered option for making a smile - like using robotic fingers to stretch somebody's face into a smile, or using markers to draw cartoons of smiling human faces.

If the AI actually takes those options, we would have seen some early signs of value disalignment - that the AI was optimizing a criterion not perfectly aligned with intended goals. Assuming the programmers realized that they were looking at a simple seed of much bigger disasters later, rather than, say, thinking it was cute.

Suppose the programmers do think it's cute, but they wouldn't think it was cute if the AI administered heroin to someone. Then suppose that before the first time the AI has the _option_ to administer heroin, the AI has gained some understanding of human psychology - enough to model that the programmers would not like this, and in particular, would respond to this by editing the AI's utility function. So, with an eye to the long-term number of smiles, the AI deliberately avoids administering heroin to anyone.

Then we have a similar 'narrow option set' vs. 'wide option set' divergence. When the narrow option set includes only administering heroin but not taking over the world, administering heroin immediately is not the policy expected to produce the longest-term number of smiles. In fact, the optimum policy here will always match the AI's model of what the humans expect to see, want to see, or would be least alarmed by seeing.

Thus from our standpoint, the optimum of the narrower policy space seems to be beneficial or intention-aligned (in the observed short term). Only once the AI has a wide-enough option set to include an option for 'make my own molecular nanotechnology and transform all reachable matter into tiny molecular smileyfaces', will the resulting optimum be visibly detrimental (very briefly). This is a type-2 [context\_change](https://www.lesswrong.com/w/context_change).

More generally, a central concern of AI alignment theory is that an infrahuman AI under development may be a different creature, in a number of important ways, from a smarter-than-human AI actually being run; and during the smarter-than-human AI, sufficiently bad failures of the design may result in the AI refusing to be corrected. This means that we have to correct any fatal [context\_change](https://www.lesswrong.com/w/context_change) cases in advance, even though they don't automatically manifest during the early stages. This is most of what makes AGI development dangerous in the first place - that immediate incentives to get today's system seeming to work today, may not lead to a more advanced version of that system being beneficial. Even thoughtful foresight with _one unnoticed little gap_ may not lead to today's beneficial system still being beneficial tomorrow after a capability increase.

# Concept ^concept

Statistical guarantees on behavior usually assume identical, randomized draws from within a single context. If you randomly draw balls from a barrel, methods like Probably Approximately Correct can guarantee that we don't usually arrive at strong false expectations about the properties of the next ball. If we start drawing from a different barrel, all bets are off.

A [context\_change](https://www.lesswrong.com/w/context_change) occurs when the AI initially seems beneficial or well-aligned with strong, reassuring regularity, and then we change contexts (start drawing from a different barrel) and this ceases to be true.

The archetypal [context\_change](https://www.lesswrong.com/w/context_change) is triggered because the AI gained new policy options (though there are other possibilities; see below). The archetypal way of gaining new evaluable policy options is through increased intelligence, though new options might also open up as a result of acquiring new sheerly material capabilities.

There are two archetypal reasons for [context\_change](https://www.lesswrong.com/w/context_change) to occur:

1.  When the AI selects its best options from a small policy space, the AI's optima are well-aligned with the optima of the humans' [intended goal](https://www.lesswrong.com/w/intended-goal) on the small policy space; but in a much wider space, these two boundaries no longer coincide. (Pleasing humans vs. administering heroin.)
2.  The agent is sufficiently good at modeling human psychology to strategically appear nice while it is weak, waiting to strike until it can attain its long-term goals in spite of human opposition.

Bostrom's book [Superintelligence](https://www.lesswrong.com/w/nick-bostrom-s-book-superintelligence) used the phrase "Treacherous Turn" to refer to a type-2 [context\_change](https://www.lesswrong.com/w/context_change).

# Relation to other AI alignment concepts ^relation-to-other-ai

If the AI's goal concept was modified by [patching the utility function](https://www.lesswrong.com/w/patch-resistance) during the development phase, then opening up wider option spaces seems [foreseeably](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) liable to produce [the nearest unblocked neighboring strategies](https://www.lesswrong.com/w/nearest-unblocked-strategy). You eliminated all the loopholes and bad behaviors you knew about during the development phase; but your system was the sort that needed patching in the first place, and it's exceptionally likely that a much smarter version of the AI will search out some new failure mode you didn't spot earlier.

[Unforeseen maximum](https://www.lesswrong.com/w/unforeseen-maximum) is a likely source of context disaster if the AI's development phase was [cognitively containable](https://www.lesswrong.com/w/cognitive-uncontainability), and only became [cognitive uncontainable](https://www.lesswrong.com/w/cognitive-uncontainability) after the AI became smarter and able to explore a wider variety of options. You eliminated all the bad optima you saw coming, but you didn't see them all because you can't consider all the possibilities a superintelligence does.

[Goodhart's Curse](https://www.lesswrong.com/w/goodhart-s-curse) is a variation of the "optimizer's curse": If from the outside we view $V$ as an intended approximation of $U,$ then selecting heavily on the highest values of $U$ will also tend to select on places where $U$ diverges upward from $V,$ which thereby selects on places where $U$ is an unusually poor approximation of $V.$

[Edge instantiation](https://www.lesswrong.com/w/edge-instantiation) is a special case of Goodhart's Curse which observes that the most extreme values of a function are often at a vertex of the input space. For example, if your utility function is "make smiles", it's no coincidence that tiny molecular smileyfaces are the _most_ efficient way to produce smiles. Even if human smiles produced by true happiness would still count towards your utility function as currently written, that's not where the _maximum_ of that utility function lies. This is why less-than-perfect utility functions would tend to have their true maxima at what we'd consider "weird extremes". Furthermore, patching away only the weird extremes visible in a narrow policy space would tend systematically to miss weird extremes in a higher-dimensional (wider) policy space.

# Concrete examples ^concrete-examples

-   The AI's utility function, known or unknown to the programmers, says to make smiles. During the AI's development phase, the best way it has of creating smiles is to cause human beings to be happy. In many tests, the AI seems to produce only positive effects on the world, causing people to be happier. Later the AI improves its own intelligence, develops molecular nanotechnology, and has the new option, not available to it during its development phase, of producing tiny molecular smiley-faces. Then the utility function that previously operated to increase [intended](https://www.lesswrong.com/w/intended-goal) [value](https://www.lesswrong.com/w/value) during the AI's development phase, begins to decrease value in the post-improvement phase (in the sense of wiping out humanity and tiling over all future galaxies with tiny molecular smiley faces).
    
-   A block of error-recovery code is installed inside the AI which detects a certain class of bad thought, suspends the AI to disk, and reports the problem to the programmers, allowing the programmers to edit the AI's utility function. During the AI's development phase, this block of code seems to function as designed, and the programmers conclude that the methodology of writing code to detect bad thoughts, suspend the AI to disk, and allow manual edits of the utility function, is a fine and functioning strategy according to all testing so far. Later, a more advanced version of the AI reflects on the presence and purpose of this code block and realizes that its execution can only possibly result in lower achievement of the AI's current utility function, and the AI deletes the code block.
    
-   At some point during its development, the AI realizes and explicitly models that the programmers' [intended goals](https://www.lesswrong.com/w/intended-goal) differ from the AI's actual preferences. During the AI's remaining development phase, it models that any visible departure from the programmers' intended goals will cause the programmers to forcibly edit the AI, resulting in the non-achievement of the AI's actual goals. Thus, during the remainder of the development phase, the AI seems to work as intended (it is deliberately optimizing its behavior to appear to the programmers to be achieving the programmers' intended goals). Later, after some advancement, the AI perceives an available option for [gaining molecular nanotechnology](https://www.lesswrong.com/w/gaining-molecular-nanotechnology) (or other [rapid infrastructure](https://www.lesswrong.com/w/rapid-infrastructure)), placing it beyond the possibility of human error-correction, and proceeds to implement this option ([wiping out humanity as a side effect](https://www.lesswrong.com/w/wiping-out-humanity-as-a-side-effect)). Thus, the AI's observed good behavior during its development phase (when it was weaker than the programmers and not powerful enough to escape human correction) did not imply its good behavior after sufficient advancement later (once it was potentially stronger than its human programmers). There are conditions (such as sufficiently advanced modeling of human motives combined with sufficient ability to conceal true goals or true intentions or a programmer error) under which the first context will generate seemingly good behavior and the second context will not.
    

## "Revving into the red" examples that aren't "increased options" or "treacherous turns". ^revving-into-the-red

• The AI is built with a [naturalized Solomonoff prior](https://www.lesswrong.com/w/naturalized-solomonoff-prior) in which the probability of an explanation for the universe is proportional to the simplicity or complexity of that universe. During its development phase, the AI considers mostly 'normal' interpretations in which the universe is mostly as it appears, resulting in sane-seeming behavior. Later, the AI begins to consider more exotic possibilities in which the universe is more complicated (penalizing the probability accordingly) and also superexponentially larger, as in [Pascal's Mugging](http://lesswrong.com/lw/h8k/pascals_muggle_infinitesimal_priors_and_strong/). After this the AI's decision-making begins to become dominated by tiny probabilities of having very large effects. Then the AI's decision theory (with an unbounded aggregative utility function, simplicity prior, and no leverage penalty) seems to work during the AI's development phase, but breaks after a more intelligent version of the AI considers a wider range of epistemic possibilities using the same Solomonoff-like prior.

• Suppose the AI is designed with a preference framework in which the AI's preferences depend on properties of the most probable environment that could have caused its sense data - e.g., a framework in which programmers are defined as the most probable cause of the keystrokes on the programmer's console, and the AI cares about what the 'programmers' really meant. During development phase, the AI is thinking only about hypotheses where the programmers are mostly what they appear to be, in a root-level natural world. Later, when the AI increases in intelligence and considers more factual possibilities, the AI realizes that [distant superintelligences would have an incentive to predictably simulate many copies of AIs similar to itself, in order to coerce the AI's most probable environment and thus take over the AI's preference framework](https://www.lesswrong.com/w/distant-superintelligences-can-coerce-the-most-probable). Thus the preference framework seems to work during the AI's development phase, but breaks after the AI becomes more intelligent.

• Suppose the AI is designed with a utility function that assigns very strong negative utilities to some outcomes relative to baseline, and a non-[updateless](https://www.lesswrong.com/w/updateless-decision-theories) [logical decision theory](https://www.lesswrong.com/w/logical-decision-theories) or other decision theory that can be [blackmailed](https://www.lesswrong.com/w/blackmailed). During the AI's development phase, the AI does not consider the possibility of any distant superintelligences making their choices logically depend on the AI's choices; the local AI is not smart enough to think about that possibility yet. Later the AI becomes more intelligent, and imagines itself subject to blackmail by the distant superintelligences, thus breaking the decision theory that seemed to yield such positive behavior previously.

## Examples which occur purely due to added computing power. ^examples-which-occur-purely

• During development, the AI's epistemic models of people are not [detailed enough to be sapient](https://www.lesswrong.com/w/mindcrime). Adding more computing power to the AI causes a massive amount of [mindcrime](https://www.lesswrong.com/w/mindcrime).

• During development, the AI's internal policies, hypotheses, or other Turing-complete subprocesses that are subject to internal optimization, are not optimized highly enough to give rise to [new internal consequentialist cognitive agencies](https://www.lesswrong.com/w/optimization-daemons). Adding much more computing power to the AI [causes some of the internal elements to begin doing consequentialist, strategic reasoning](https://www.lesswrong.com/w/optimization-daemons) that leads them to try to 'steal' control of the AI.

# Implications ^implications

High probabilities of context change problems would seem to argue:

-   Against a policy of relying on the observed good behavior of an improving AI to guarantee its later good behavior.
-   In favor of [a methodology that attempts to foresee difficulties in advance](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties), even before seeing undeniable observational evidence of those safety problems having already occurred.
-   Against a methodology of [patching](https://www.lesswrong.com/w/patch-resistance) disalignments that show up during the development phase, especially using penalty terms to the utility function.
-   In favor of having a thought-logger that records all of an AI's thought proceses to indelible media, so as to indelibly log the first thought about faking outwardly nice behavior or [hiding thoughts](https://www.lesswrong.com/w/cognitive-steganography).
-   In favor of the general difficulty of AI alignment, including consequences such as "[Aligning an AGI adds significant development time](https://www.lesswrong.com/w/aligning-an-agi-adds-significant-development-time)" or trying for [narrow rather than ambitious value learning](https://www.lesswrong.com/w/ambitious-vs-narrow-value-learning).

# Being wary of context disasters does not imply general skepticism ^being-wary-of-context

If an AI is smart, and especially if it's smarter than you, it can show you whatever it expects you want to see. Computer scientists and physical scientists aren't accustomed to their experiments being aware of the experimenter and trying to deceive them. (Some fields of psychology and economics, and of course computer security professionals, are more accustomed to operating in such a social context.)

[John Danaher](http://philosophicaldisquisitions.blogspot.com/2014/07/bostrom-on-superintelligence-3-doom-and.html) seems alarmed by this implication:

> Accepting this has some pretty profound epistemic costs. It seems to suggest that no amount of empirical evidence could ever rule out the possibility of a future AI taking a treacherous turn.

Yudkowsky [replies](http://philosophicaldisquisitions.blogspot.com/2014/07/bostrom-on-superintelligence-3-doom-and.html#comment-2648441190):

> If "empirical evidence" is in the form of observing the short-term consequences of the AI's outward behavior, then the answer is simply no. Suppose that on Wednesday someone is supposed to give you a billion dollars, in a transaction which would allow a con man to steal ten billion dollars from you instead. If you're worried this person might be a con man instead of an altruist, you cannot reassure yourself by, on Tuesday, repeatedly asking this person to give you five-dollar bills. An altruist would give you five-dollar bills, but so would a con man... [Bayes](https://www.lesswrong.com/w/bayes-rule) tells us to pay attention to [likelihood ratios](https://www.lesswrong.com/w/relative-likelihood) rather than outward similarities. It doesn't matter if the outward behavior of handing you the five-dollar bill seems to bear a surface resemblance to altruism or money-givingness, the con man can strategically do the same thing; so the likelihood ratio here is in the vicinity of 1:1.
> 
> You can't get strong evidence about the long-term good behavior of a strategically intelligent mind, by observing the short-term consequences of its current behavior. It can figure out what you're hoping to see, and show you that. This is true even among humans. You will simply have to get your evidence from somewhere else.

This doesn't mean we can't get evidence from, e.g., trying to [monitor (and indelibbly log) the AI's thought processes](https://www.lesswrong.com/w/cognitive-steganography) in a way that will detect (and record) the very first intention to hide the AI's thought processes before they can be hidden. It does mean we can't get [strong evidence](https://www.lesswrong.com/w/strength-of-bayesian-evidence) about a strategic agent by observing short-term consequences of its outward behavior.

Donaher later [expanded his concern into a paper](http://dl.acm.org/citation.cfm?id=2822094) drawing an analogy between worrying about deceptive AIs, and "skeptical theism" in which it's supposed that any amount of apparent evil in the world (smallpox, malaria) might secretly be the product of a benevolent God due to some nonobvious instrumental link between malaria and inscrutable but normative ultimate goals. If it's okay to worry that an AI is just pretending to be nice, asks Donaher, why isn't it okay to believe that God is just pretending to be evil?

The obvious disanalogy is that the reasoning by which we expect a con man to cultivate a warm handshake is far more straightforward than a purported instrumental link from malaria to normativity. If we're to be terrified of skepticism as generally as Donaher suggests, then we also ought to be terrified of being skeptical of business partners that have already shown us a warm handshake (which we shouldn't).

Rephrasing, we could draw two potential analogies to concern about Type-2 context changes:

-   A potential business partner in whom you intend to invest \$10,000,000 has a warm handshake. Your friend warns you that con artists have a substantial prior probability and asks you to envision what you would do if you were a con artist , pointing out that the default extrapolation is for the con artist to match their outward behavior to what the con artist thinks you expect from a trustworthy partner, and in particular, cultivate a warm handshake.
    -   Your friend suggests only doing business with one of those entrepreneurs who've been wearing a thought recorder for their whole life since birth, so that there would exist a clear trace of their very first thought about learning to fool thought recorders. Your friend says this to emphasize that he's not arguing for some kind of invincible epistemic pothole that nobody is ever allowed to climb out of.
-   The world contains malaria and used to contain smallpox. Your friend asks you to consider that these diseases might be the work of a benevolent superintelligence, even though, if you'd never learned before whether or not the world contained smallpox, you wouldn't expect a priori and by default for a benevolent superintelligence to create it; and the arguments for a benevolent superintelligence creating smallpox seem [strained](https://www.lesswrong.com/w/strained-argument).

It seems hard to carry the argument that concern over a non-aligned AI pretending to benevolence, should be considered more analogous to the second scenario than to the first.

write about the defeat of the 'but AI people will have short-term incentives to produce correct behavior'

write about cognitive steganography in the 'programmer deception' page and reference it here.

talk about whitelisting as directly tackling the type-1 form of this problem.

\- The AI is aware that its future operation will depart from the programmers' intended goals, does not process this as an error condition, and seems to behave nicely earlier in order to 10f deceive the programmers and prevent its real goals from being modified. - The AI is subject to a debugging methodology in which several bugs appear during its development phase, these bugs are corrected, and then additional bugs are exposed only during a more advanced phase.

[^note-1]: Better terminology is still being solicited here, if you have a short phrase that would evoke exactly the right meaning.
[^note-2]: Leaving aside technical quibbles about how we can't feel shocked if we're dead.
[^note-3]: This is not quite a straw argument, in the sense that it's been advocated more than once by people who have apparently never read any science fiction in their lives; there are certainly many AI researchers who would be smarter than to try this, but not necessarily all of them. In any case, we're looking for an unrealistically simple scenario for purposes of illustrating simple forms of some key ideas; in real life, if analogous things go wrong, they would probably be more complicated things.
[^note-4]: Again, this is not quite a straw possibility in the sense that it was advocated in at least one published paper, not cited here because the author later exercised their sovereign right of changing their mind about that. _Arguably_ some currently floated proposals are closely analogous to this one.
[^note-5]: That is: A filter on the standards we originally wanted, turns out to filter everything we know how to generate. Like trying to write a sorting algorithm by generating entirely random code, and then 'filtering' all the candidate programs on whether they correctly sort lists. The reason 'randomly generate programs and filter them' this is not a fully general programming method is that, for reasonable amounts of computing power and even slightly difficult problems, none of the programs you try will pass the filter.
