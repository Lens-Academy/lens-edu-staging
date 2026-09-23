---
title: "Low impact"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/low-impact"
published: 2016-04-19
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "A low-impact agent is a hypothetical task-based AGI that's intended to avoid disastrous side effects via trying to avoid large side effects in general."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A low-impact agent is a hypothetical [task-based AGI](https://www.lesswrong.com/w/task-directed-agi) that's intended to avoid _disastrous_ side effects via trying to _avoid large side effects in general_.

Consider the Sorcerer's Apprentice fable: a legion of broomsticks, self-replicating and repeatedly overfilling a cauldron (perhaps to be as certain as possible that the cauldron was full). A low-impact agent would, if functioning as [intended](https://www.lesswrong.com/w/intended-goal), have an incentive to avoid that outcome; it wouldn't just want to fill the cauldron, but fill the cauldron in a way that had a minimum footprint. If the task given the AGI is to paint all cars pink, then we can hope that a low-impact AGI would not accomplish this via self-replicating nanotechnology that went on replicating after the cars were painted, because this would be an unnecessarily large side effect.

On a higher level of abstraction, we can imagine that the universe is parsed by us into a set of variables $V_i$ with values $v_i$. We want to avoid the agent taking actions that cause large amounts of disutility, that is, we want to avoid perturbing variables from $v_i$ to $v_i^*$ in a way that decreases utility. However, the question of exactly which variables $V_i$ are important and shouldn't be entropically perturbed is [value-laden](https://www.lesswrong.com/w/value-laden) - complicated, fragile, high in [algorithmic complexity](https://www.lesswrong.com/w/algorithmic-complexity), with [Humean degrees of freedom in the concept boundaries](https://www.lesswrong.com/w/humean-degree-of-freedom).

Rather than relying solely on teaching an agent exactly which parts of the environment shouldn't be perturbed and risking catastrophe if we miss an injunction, the _low impact_ route would try to build an agent that tried to perturb fewer variables regardless.

The hope is that "have fewer side effects" is a problem that has a simple core and is learnable by a manageable amount of training. Conversely, trying to train "here is the list of _bad_ effects not to have and _important_ variables not to perturb" would be complicated and lack a simple core, because 'bad' and 'important' are [value-laden](https://www.lesswrong.com/w/value-laden). A list of dangerous variables would also be [a blacklist rather than a whitelist](https://www.lesswrong.com/w/conservative-concept-boundary), which would make it more vulnerable to [treacherous context changes](https://www.lesswrong.com/w/context-disaster) if the AI gained the ability to affect new things.

## Introduction: Formalizing low impact seems nontrivial ^introduction-formalizing-low-impact

Intuitively, the notion of "low impact" seems like it should be simpler - have more of a central, core tendency to capture - than "avoid bad impacts". If so, we don't know yet how to compactly state this core principle semiformally.

Suppose we start with an obvious notion: to have low impact, minimize the number of variables you [causally](https://www.lesswrong.com/w/causally) affect. But:

-   Every event has a not-absolutely-zero impact on every future event. When you twitch your thumb or even just fire a neuron, the gravitational ripples from the moving atoms spread out and will eventually produce infinitesimal forces on atoms orbiting the other side of the galaxy. So we can't say "have zero impact on as many quarks as possible" because it is impossible for any act to have absolutely zero impact on any quark.

This is a special case of a failure mode where, since the impact metric turns out to already be maxed out by all actions, moving around inside the maxed-out impact penalty doesn't change expected utility, and therefore fails to influence which action is chosen. This [foreseeable difficulty](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) might also illustrate a typical [treacherous context change](https://www.lesswrong.com/w/context-disaster), in that the AI during its training phase might have a relatively small causal model of its environment, with qualitative causal arrows, and so seem to be minimizing impact inside the training regime. Later development might cause the AI to adopt a new causal model in which, as happens to actually be the case, all its possible actions influence all the quarks inside its [future light cone](https://www.lesswrong.com/w/future-light-cone), and so actions are not differentiated by the magnitude of their impact penalty; thus the AI would safe in training and unsafe in later use, with the critical threshold possibly coming after the AI was [too intelligent to be shut down](https://www.lesswrong.com/w/instrumental_self_preservation).

But measuring causal impacts qualitatively isn't the only possibility. Suppose we define impact as the sum of the expected movement of all atoms, relative to their mean expected positions if some privileged null action were taken instead? Or, to avoid this impact measure returning 0 as soon as the AI realizes that [there are no atoms, only quarks](https://www.lesswrong.com/w/ontology-identification-problem), we try to give the AI some notion of the distance between outcomes in _any_ way of modeling the world?

Arguendo, suppose that we could define a representational language over possible universes and laws of physics, such that within any representable model of the universe, there's an obvious notion of 'distance' between any two outcomes conditional on the AI's actions. If the universe is made of atoms, this representation will expose the obvious impact metric on the movements of atoms. If the universe is made of quarks, the same component of the utility function will readily calculate the movements of quarks. If the universe is made of quantum fields, this impact metric will behave in the intuitively intended way that basically works out to measuring particle motions, rather than the change metric always maxing out as the result of all amplitude flows ending up in qualitatively different sections of the quantum configuration space, etcetera. (Note that this is already sounding pretty nontrivial.)

Furthermore, suppose when the AI is thinking in terms of neither atoms nor quarks, but rather, say, the equivalent of chess moves or voxel fields, the same impact metric can apply to this as well; so that we can observe the low-impact behaviors at work during earlier development phases.

More formally: We suppose that the AI's model class is such that for any allowed model $M$, for any two outcomes $o_M$ and $o'_M$ that can result from the AI's choice of actions, there is a distance $d(o_M, o'_M)$ which obeys [standard rules for distances](http://mathworld.wolfram.com/Norm.html). This general distance measure is such that, within the standard model of physics, moving atoms around would add to the distance between outcomes in the obvious way; and for models short of molecular detail, will measure changes in other variables and quantities in an intuitive way. We then fix some particular policy whose consequence is "the result of the AI doing nothing", and measure the impact penalty of any other policy as proportional to the expected distance between outcomes $o_M$ and $o'_M$.

Then we might run into any of these further [foreseeable difficulties](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties), if, e.g., you asked the AGI to cure cancer with minimum 'impact' as defined above (or to put it another way, minimize impact subject to the constraint of curing cancer):

-   Offsetting actions we would intuitively regard as both bad and impactful:
    -   The AGI models global death rates as a quantity, and implements offsetting actions to keep Earth's annual death statistics constant after it cures cancer.
-   Chaotic permissiveness:
    -   Weather is a chaotic system. If influencing any butterfly is going to move around all the atoms in the atmosphere anyway, you might as well have them end up somewhere you want.
-   Stasis incentives:
    -   The AGI edits its programmers to make sure the programmers do whatever they would have done if the AGI, after being told its task, performed the null action.
    -   The AGI proliferates across galaxies to make sure everything else in the universe outside of human bodies adheres as closely as possible to the expected state it would have occupied if the null action had been taken.
    -   The AGI sets up a weather-control system so that at least its further actions won't again disturb the weather.

All of this just goes to say that there's apparently some subtlety built into our intuitively [intended](https://www.lesswrong.com/w/intended-goal) notion of "paint all cars pink, but do so with the minimum footprint possible apart from that".

We want people to be able to notice that their cars have been painted pink, and for them to enjoy whatever further benefit of pink-painted cars led us to give the AGI this instruction in the first place. But we can't just whitelist any further impact that happens as a consequence of the car being painted pink, because maybe the car was painted with pink replicating nanomachines. Etcetera.

Even if there is, in fact, some subtlety built into our intended notion of "make plans that have minimal side effects", this subtle notion of low impact might still have a relatively much simpler core than our intuitive notion of "avoid bad impacts". This might be reflected in either an improved formal intuition for 'low impact' that proves to stand up to a few years of skeptical scrutiny without any holes having been poked in it, or, much more nerve-rackingly, the ability to train an AI to make minimal-impact plans even if we don't know a closed-form definition of "minimal impact".

Work in this area is ongoing, so far mainly in the form of some preliminary suggestions by Stuart Armstrong (which were mostly shot down, but this is still progress compared to staring blankly at the problem).

## Foreseeable difficulties ^foreseeable-difficulties

## Permissiveness inside chaotic systems ^permissiveness-inside-chaotic-systems

Suppose you told the AI to affect as few things as possible, above the minimum necessary to achieve its task, and defined 'impact' qualitatively in terms of causal links that make variables occupy different states. Then since every act and indeed every internal decision (transistors, in switching, move electrons) would have infinitesimal influences on literally everything in the AI's future light cone, all of which is defined as an 'impact', all actions would seem to have the same, maximum impact. Then the impact penalty would make no difference to the net expected utility of actions, causing the AI to behave as if it had no impact penalty.

Even if an impact measure doesn't max out because of ubiquitous qualitative impacts, a poorly defined impact measure might max out quantitatively when the AGI is operating in a domain that is _chaotic_ in the sense that tiny differences soon blow up to large differences. E.g., if a butterfly flaps its wings, that might cause a hurricane on the other side of the world a year later - so since you're already changing the weather system as much as possible, why does it matter if, say, you on-purpose cause a hurricane in some area, or destroy a target using atmospheric lightning strikes? Those air molecules would all have ended up moving anyway because of the butterfly effect.

An imaginable patch is to try to evaluate impact over _foreseeable_ impacts, so that a known lightning strike is 'foreseeable', while the effects on future hurricanes are 'not foreseeable'. This seems worryingly like mixing up the map and the territory (is it okay to release environmental poisons so long as you don't know who gets hurt?), but Stuart Armstrong has made some preliminary suggestions about minimizing knowable impacts.

If you didn't know it was coming, "maxing out the impact penalty" would potentially be a [treacherous context change](https://www.lesswrong.com/w/context-disaster). When the AI was at the infrahuman level, it might model the world on a level where its actions had relatively few direct causal links spreading out from them, and most of the world would seem untouched by most of its possible actions. Then minimizing the impact of its actions, while fulfilling its goals, might in the infrahuman state seem to result in the AI carrying out plans with relatively few side effects, as intended. In a superhuman state, the AI might realize that its every act resulted in quantum amplitude flowing into a nonoverlapping section of configuration space, or having chaotic influences on a system the AI was not previously modeling as having maximum impact each time.

## Infinite impact penalties ^infinite-impact-penalties

In one case, a proposed impact penalty was written down on a whiteboard which happened to have the fractional form where the quantity could _in some imaginable universes_ get very close to zero, causing Eliezer Yudkowsky to make an "Aaaaaaaaaaa"-sound as he waved his hands speechlessly in the direction of the denominator. The corresponding agent would have [spent all its effort on further-minimizing infinitesimal probabilities of vast impact penalties](https://www.lesswrong.com/w/pascals_mugging).

Besides "don't put denominators that can get close to zero in any term of a utility function", this illustrates a special case of the general rule that impact penalties need to have their loudness set at a level where the AI is doing something besides minimizing the impact penalty. As a special case, this requires considering the growth scenario for improbable scenarios of very high impact penalty; the penalty must not grow faster than the probability diminishes.

(As usual, note that if the agent only started to visualize these ultra-unlikely scenarios upon reaching a superhuman level where it could consider loads of strange possibilities, this would constitute a [treacherous context change](https://www.lesswrong.com/w/context-disaster).)

## Allowed consequences vs. offset actions ^allowed-consequences-vs-offset

When we say "paint all cars pink" or "cure cancer" there's some implicit set of consequences that we think are allowable and should definitely not be prevented, such as people noticing that their cars are pink, or planetary death rates dropping. We don't want the AI trying to obscure people's vision so they can't notice the car is pink, and we don't want the AI killing a corresponding number of people to level the planetary death rate. We don't want these bad _offsetting_ actions which would avert the consequences that were the point of the plan in the first place.

If we use a low-impact AGI to carry out some [pivotal act](https://www.lesswrong.com/w/pivotal-act) that's part of a larger plan to improve Earth's chances of not being turned into paperclips, then this, in a certain sense, has a very vast impact on many galaxies that will _not_ be turned into paperclips. We would not want this _allowed_ consequence to max out and blur our AGI's impact measure, nor have the AGI try to implement the pivotal act in a way that would minimize the probability of it actually working to prevent paperclips, nor have the AGI take offsetting actions to keep the probability of paperclips to its previous level.

Suppose we try to patch this rule that, when we carry out the plan, the further causal impacts of the task's accomplishment are exempt from impact penalties.

But this seems to allow too much. What if the cars are painted with self-replicating pink nanomachines? What distinguishes the further consequences of that solved goal from the further causal impact of people noticing that their cars have been painted pink?

One difference between "people notice their cancer was cured" and "the cancer cure replicates and consumes the biosphere" is that the first case involves further effects that are, from our perspective, pretty much okay, while the second class of further effects are things we don't like. But an 'okay' change versus a 'bad' change is a value-laden boundary. If we need to detect this difference as such, we've thrown out the supposed simplicity of 'low impact' that was our reason for tackling 'low impact' and not 'low badness' in the first place.

What we need instead is some way of distinguishing "People see their cars were painted pink" versus "The nanomachinery in the pink paint replicates further" that operates on a more abstract, non-value-laden level. For example, hypothetically speaking, we might claim that _most_ ways of painting cars pink will have the consequence of people seeing their cars were painted pink and only a few ways of painting cars pink will not have this consequence, whereas the replicating machinery is an _unusually large_ consequence of the task having reached its fulfilled state.

But is this really the central core of the distinction, or does framing an impact measure this way imply some further set of nonobvious undesirable consequences? Can we say rigorously what kind of measure on task fulfillments would imply that 'most' possible fulfillments lead people to see their cars painted pink, while 'few' destroy the world through self-replicating nanotechnology? Would _that_ rigorous measure have further problems?

And if we told an AGI to shut down a nuclear plant, wouldn't we want a low-impact AGI to err on the side of preventing radioactivity release, rather than trying to produce a 'typical' magnitude of consequences for shutting down a nuclear plant?

It seems difficult (but might still be possible) to classify the following consequences as having low and high extraneous impacts based on a _generic_ impact measure only, without introducing further value lading:

-   Low disallowed impact: Curing cancer causes people to notice their cancer has been cured, hospital incomes to drop, and world population to rise relative to its default state.
-   High disallowed impact: Shutting down a nuclear power plant causes a release of radioactivity.
-   High disallowed impact: Painting with pink nanomachinery causes the nanomachines to further replicate and eat some innocent bystanders.
-   Low disallowed impact: Painting cars with ordinary pink paint changes the rays of light reflecting from those cars and causes people to gasp and say "What just happened to my car?"
-   Low disallowed impact: Doing something smart with a Task AGI decreases the probability of the galaxies being consumed by an Unfriendly AI.

(Even if we think that good AGI scenarios involve the AGI concealing the fact of its existence, it's hard to see why we'd want the _events as such_ to be unnoticeable, or for their noticing to count as extraneous impacts.)

### Fallback use of an impact measure to prioritize operator queries ^fallback-use-of-an

If this problem of allowing _good_ consequences did turn out to be inherently value-laden, it might not obviate the usefulness of a safe impact measure. For example, it could be that in normal operation of a Task AGI, there are only a limited number of good further impacts that we want to whitelist - e.g., once we say that curing cancer is allowed to cause people to notice that they feel healthier and for there to be more people alive using more resources, etcetera, then it's okay to minimize all other footprints.

Similarly, a safe impact measure might operate to alert the operators to all large impacts sorted by size of impact, such that the impact measure would reliably not have any remaining event that was 'large' in an intuitive sense that the operators didn't know about. That is, we might not be able to give a blanket instruction to minimize impact, but a safe impact measure might still be useful for deciding which features of a plan need to be queried to the operators.

## Stasis incentives ^stasis-incentives

This would be the general problem that includes "The AGI proliferates across galaxies to make sure everything else in the universe outside of human bodies adheres as closely as possible to the expected state it would have occupied if the null action had been taken."

Similarly, we can imagine the AGI having a strong incentive to, in Round 1, paint the cars with nanomachines such that the nanomachinery quietly and unobtrusively sets up a weather-control system. This wouldn't prevent the AGI's actions in Round 1 from influencing the chaotic weather and having a huge impact, but could ensure that the AI's future actions in Round 2 wouldn't influence the formerly-chaotic weather relative to its null action then.

## The problem of the backup AGI ^the-problem-of-the

Suppose we're using a measure of impact relative to a privileged null action. Imagine that there are two AGIs which will both be given the same task, and under ordinary circumstances, divide the effort of performing the task between them; but if one AGI fails to perform, the other will take over the task in its entirety. Then each AGI reasons, "If I perform the null action instead of carrying out the task, the other AGI will do almost exactly the same thing I was going to do" and so models itself as having _counterfactually_ almost no impact. In this way, two AGIs can each evaluate themselves as having almost no impact, while operating in tandem they have a very large impact. (This problem was first observed by Stuart Armstrong.)

We can even imagine - though hopefully this isn't the sort of thing that would go uncaught by other safety measures - that in Round 1, the agent builds a backup agent, which doesn't count as having an extraneous impact because the system of 2 agents ends up carrying out the same steps that the agent would have carried out on its own. But then on Round 2, there's now a backup and both agents regard themselves as having minimal impact.

(If you say that the agent should, on Round 1, realize that constructing the backup agent on Round 1 would have a later _impact_ on the effect of the AI carrying out its orders in Round 2, then we're now allowing the agent to minimize its impact _across tasks,_ which might imply that in Round 1 it should try to build something that regularizes the weather as a side effect, so that its actions in Round 2 have less chaotic impact on the weather... or that it tries to influence its programmers to give it less impactful tasks, etcetera.)

A more general way of viewing this possible problem is that there might be [tiling problems](https://www.lesswrong.com/w/tiling-problems) for a low-impact agent modifying itself or creating subagents or successors.

## Standard issues ^standard-issues

The following standard issues from alignment theory seem like they could also apply to the problem of building a low-impact agent or creating a safe impact measure. We need an [advanced-safe](https://www.lesswrong.com/w/advanced-safety) impact measure that will stand up to the load and stress of cognition that is superhuman in at least some domains.

## Programmer manipulation ^programmer-manipulation

A Task AGI which plans across rounds may have an incentive to influence its programmers into giving it plans that will have net lower impact compared to other plans the programmers might offer. If there's an explicit procedure for the programmers to whitelist consequences, the AGI would have to be somehow configured in such fashion as to not prefer programmers to whitelist the consequences or seek out consequences that the programmers would be expected to (perhaps mistakenly) whitelist.

## Causal environment hacking ^causal-environment-hacking

Since an impact measure seems likely to be defined over the causes of sense data, it has the standard problem with remote hacking of causal environments. (This is a ubiquitous enough problem that you're going to want some general solution such as not having the AGI model remote hackers in the first place. But this subproblem should still be noted each time we introduce a dependency on the modeled causes of sense data.)

## Edge instantiation ^edge-instantiation

Building a safe impact measure is hard because if we roll a naive impact measure, it might have its minimum in a weird, undesirable place. Freezing all matter into the universe into stasis would be an example of this.

## Unforeseen maximum ^unforeseen-maximum

The actions and modes the AGI has available to potentially minimize its impact will include more actions and modes than we can imagine and check ourselves.

## Nearest unblocked neighbor ^nearest-unblocked-neighbor

If the maximizing plan has high impact, the new best plan after introducing an impact measure may be a similar plan that has, through some leaky definition, found a weird special case that doesn't count as an impact. To put it another way, to the extent an imperfect impact measure would otherwise hamper the AI if it were perfect, the AI experiences an [instrumental pressure](https://www.lesswrong.com/w/instrumental-pressure) to seek out any loopholes or leaks in the definition.

## Context change ^context-change

As the AI gains in cognitive capability, this widens the option space which could potentially contain instances of 'low impact' that are [unforeseen](https://www.lesswrong.com/w/unforeseen-maximum) or [unblocked](https://www.lesswrong.com/w/nearest-unblocked-strategy).

In this particular case, increased intelligence may also:

-   Change the set of impacts that the AI can foresee, so that e.g. its causal model goes from 'some actions causally connect to some other things' to 'all actions causally connect to all things'.
-   Widen the space of possibilities it considers, to include for the first time very-low-probability scenarios of very large impacts.
-   Include new offsetting actions, so that the AI for the first time has the option of editing brains not to notice changes it makes, or introduce randomized Unfriendly-AI generators to offset decreases in the probability of Unfriendly AI.

## Reflective stability ^reflective-stability

Does a low-impact AI want to only build a successor that's a low-impact AI? If it builds an environmental subagent, is that subagent low impact?

Even if the AGI is supposed to not be self-modifying or to be building subagents, is there a worrying divergence and pressure to be held in check between how the AI thinks and how the AI would prefer to think? Does a low-impact AGI want relevant cognitive computations in general to be low impact?

To the extent that low impact is a feature of the utility function rather than the optimization style, this doesn't have any obvious problems (apart from Armstrong's dual-AGI no-impact counterfactual issue), but it's a standard thing to check, and would become _much more_ important if low impact was supposedly being achieved through any feature of the optimization style rather than utilities over outcomes.

## Related / further problems ^related-further-problems

A [shutdown utility function](https://www.lesswrong.com/w/shutdown-utility-function) is one which incentivizes the AI to safely switch itself off, without, say, creating a subagent that assimilates all matter in the universe to make absolutely sure the AI is never again switched back on.

[Abortable plans](https://www.lesswrong.com/w/abortable-plans) are those which are composed with the intention that it be possible to midway activate an 'abort' plan, such that the partial implementation of the original plan, combined with the execution of the abort plan, together have a minimum impact. For example, if an abortable AI was building self-replicating nanomachines to paint a car pink, it would give all the nanomachines a quiet self-destruct button, so that at any time the 'abort' plan could be executed after having partially implemented to the plan to paint the car pink, such that these two plans together would have a minimum impact.
