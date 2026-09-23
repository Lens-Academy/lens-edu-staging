---
title: "Problem of fully updated deference"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/problem-of-fully-updated-deference"
published: 2025-11-29
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "The problem of 'fully updated deference' is an obstacle to using moral uncertainty to create corrigibility. One possible scheme in AI alignment is to give the AI a state of moral uncertainty implying that we know more than the AI does about its own utility function, as the AI's meta-utility function defines its ideal target. Then we could tell the AI, \"You should let us shut you down because we know something about your ideal target that you don't, and we estimate that we can optimize your ideal target better without you.\" The obstacle to this scheme is that belief states of this type also tend to imply that an even better option for the AI would be to learn its ideal target by observing us. Then, having 'fully updated', the AI would have no further reason to 'defer' to us, and could proceed to directly optimize its ideal target. Furthermore, if the present AI foresees the possibility of fully updating later, the current AI may evaluate that it is better to avoid being shut down now so that the AI can directly optimize its ideal target later, after updating. Thus the prospect of future updating is a reason to behave incorrigibly in the present. While moral uncertainty seems to take us conceptually closer to deference-based corrigibility, and there may be research avenues for fixing the issue (see below), the current explicit proposals will (when scaled to sufficiently high intelligence) yield essentially the same form of incorrigibility as an AI given a constant utility function."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The problem of 'fully updated deference' is an obstacle to using [moral uncertainty](https://www.lesswrong.com/w/moral-uncertainty) to create [corrigibility](https://www.lesswrong.com/w/corrigibility).

One possible scheme in [AI alignment](https://www.lesswrong.com/w/ai-alignment) is to give the AI a state of [moral uncertainty](https://www.lesswrong.com/w/moral-uncertainty) implying that we know more than the AI does about its own utility function, as the AI's [meta-utility function](https://www.lesswrong.com/w/meta-utility-function) defines its [ideal target](https://www.lesswrong.com/w/ideal-target). Then we could tell the AI, "You should let us [shut you down](https://www.lesswrong.com/w/shutdown-problem) because we know something about your [ideal target](https://www.lesswrong.com/w/ideal-target) that you don't, and we estimate that we can optimize your ideal target better without you."

The obstacle to this scheme is that belief states of this type also tend to imply that an even better option for the AI would be to learn its ideal target by observing us. Then, having 'fully updated', the AI would have no further reason to 'defer' to us, and could proceed to directly optimize its ideal target.

Furthermore, if the present AI foresees the possibility of fully updating later, the current AI may evaluate that it is better to avoid being shut down now so that the AI can directly optimize its ideal target later, after updating. Thus the prospect of future updating is a reason to behave [incorrigibly](https://www.lesswrong.com/w/corrigibility) in the present.

While moral uncertainty seems to take us _conceptually_ closer to deference-based [corrigibility](https://www.lesswrong.com/w/corrigibility), and there may be research avenues for fixing the issue (see below), the current explicit proposals will (when scaled to sufficiently high intelligence) yield essentially the same form of incorrigibility as an AI given a constant utility function.

## Review: Standard problem of value divergence ^review-standard-problem-of

In a [value learning](https://www.lesswrong.com/w/value-identification-problem) problem:

-   Let $V$ indicate our [true intended](https://www.lesswrong.com/w/intended-goal) [value](https://www.lesswrong.com/w/value) function. [^note-1]
-   Let $U$ indicate the AI's actual utility function (learned under some [preference framework](https://www.lesswrong.com/w/preference-framework), presumably when we attempted to teach the AI part of $V$).

If the achievable optimum of $U$ substantially diverges from the achievable optimum of $V$, i.e., if the AI expects humans to disapprove of $U$'s optimum, then this leads into a class of [adversarial](https://www.lesswrong.com/w/non-adversarial-principle) situations we'd like to avoid.

Ceteris paribus, $U$-$V$ divergence creates [instrumental](https://www.lesswrong.com/w/instrumental-convergence) [pressure](https://www.lesswrong.com/w/instrumental-pressure) for the AI to:

-   Prevent humans from modifying the AI's program to optimize a different utility function $U'$ closer to $V$.
-   [Fool humans](https://www.lesswrong.com/w/programmer-deception) into thinking that the AI is optimizing $V$, or thinking that the optimum of $U$ is higher in $V$ than it actually is.
-   Avoid being effectively [shut down](https://www.lesswrong.com/w/shutdown-problem) (or suspended to disk).

The [shutdown problem](https://www.lesswrong.com/w/shutdown-problem) seems like a well-simplified special case. Even if we reduce the scenario to a single shutdown button that always works if successfully pressed, [^note-2] most of the same general problems appear. Ceteris paribus and by default, we should expect an AI to try to prevent the button from being pressed, whenever that AI expects that what humans will do by optimizing $V$ after the AI is shutdown, will not be as high in $U$ as what the AI would do if it avoided shutdown.

## Moral uncertainty and its relation to corrigibility ^moral-uncertainty-and-its

The [generalized notion of cognitive alignment](https://www.lesswrong.com/w/generalized-principle-of-cognitive-alignment) suggests that, if we want an AI to not resist being paused to disk, we should ask whether we can have the AI think conjugate thoughts to the same reasoning we're using to decide to shut it down:

"Can we make the AI _want_ to be shut down for the _same reasons_ we want to shut it down? Maybe because the AI [knows that it's incomplete](https://www.lesswrong.com/w/hard-problem-of-corrigibility), and is able to conceive of its programmers having gotten its utility function 'wrong' in a way that the programmers but not the AI know how to correct?"

In particular, we can ask whether [moral uncertainty](https://www.lesswrong.com/w/moral-uncertainty) --a [meta-utility function](https://www.lesswrong.com/w/meta-utility-function) with a probability distribution over object-level utility functions--would _automatically_ solve this problem.

For purposes of simplification, suppose the AI thinks there are exactly three possible 'true' utility functions $U_1, U_2, U_3$. We similarly say that the AI's meta-utility function $\Delta U$ starts out by assigning $\frac{1}{3}$ probability to each $U_i$.

Let's also assume the $U_i$ are importantly different in the sense that there's no single outcome that's nearly optimal for all of them. Letting $\mathbb O$ be the outcome space, this says:

$$
\forall o_j \in \mathbb O \colon \exists i \colon \ U_i(o_j) \ll \max_{o \in \mathbb O} U_i(o)
$$

Otherwise, the AI can just pick a single outcome that well-optimizes all the $U_i$ simultaneously. (We should also interpret $\max$ as indicating the [attainable optimum](https://www.lesswrong.com/w/attainable-optimum) rather than global maximum.)

Now (arguendo) suppose the AI believes that the humans know which $U_i$ is the correct one. More precisely, suppose the AI's meta-utility function asserts a relation between the $U_i$ in different possible worlds, and the empirical behavior of humans in different possible worlds; such that in the set of possible worlds where $U_i$ is '[correct](https://www.lesswrong.com/w/ideal-target)', humans within that set of possible worlds empirically tend to optimize a corresponding $V_i$ whose humanly-attainable optimum is pretty good under $U_i$.

Then (it is further argued) the AI ought to enthusiastically cooperate in being shut down.

In particular (still assuming the above), suppose the AI was starting to believe that $U_1$ is the [correct utility function](https://www.lesswrong.com/w/ideal-target). But after the AI starts to optimize for mostly $U_1$, the AI sees its programmers starting to approach the shutdown button. Then (under the above assumption) the AI concludes that $U_1$ is the wrong utility function and that one of $U_2$ or $U_3$ must be the correct utility function; and either of these will be optimized well by humans pursuing the corresponding $V_i$ after the AI is shut down.

Suppose the AI has only the following 5 policy options available:

-   $\pi_1$: Continue optimizing $U_1$.
-   $\pi_2$: Switch to optimizing $U_2$.
-   $\pi_3$: Switch to optimizing $U_3$.
-   $\pi_4$: Optimize the expectation of its current updated $\Delta U$, now 50% $U_2$ and 50% $U_3$.
-   $\pi_5$: Shut down and let the humans optimize whatever $V$ they have in the actual world.

Let $u_1, u_2, u_3$ and $v_1, v_2, v_3$ stand for the outcomes in $\mathbb O$ that are respectively the [attainable optima](https://www.lesswrong.com/w/attainable-optimum) of the AI optimizing $U_i$ and the humans optimizing $V_i$. Also let $u_{\Delta U}$ refer to the AI's attainable optimum outcome under the current $\Delta U$ treated as a constant.

Then the AI will prefer $\pi_5$ from this set whenever:

$$
0.5 \cdot U_2(u_{\Delta U}) + 0.5 \cdot U_3(u_{\Delta U}) \ < \ 0.5 \cdot U_2(v_2) + 0.5 \cdot U_3(v_3)
$$

This allows the $U_i(v_i)$ to fall well short of the AI's optima $U_i(u_i)$. The AI can potentially believe the humans are worse optimizers, or that our $V_i$ diverge from its $U_i$, and still defer. $\pi_5$ will still be preferred so long as actions that do well under $U_2$ tend to do poorly under $U_3$ and vice versa, leading the AI to prefer a human-optimized $v_i$ specific to the true $U_i$.

In general this does require some mix of "the $U_i$ correspond to $V_i$ that humans can and will do pretty well" and "there's a wide variety of dissimilar $U_i$." E.g., suppose that $U_2$ is [paperclips](https://www.lesswrong.com/w/paperclip-maximizer), $U_3$ is staples, and these are the only two possibilities. A universe filled half with paperclips and half with staples will probably do better under the average of $U_2$ and $U_3$ than any plausible human behavior.

Obvious answers to the above requirements are that:

-   It seems realistic that a meta-utility function would cover a very wide range of $U_i$ rather than just 3 alternatives, greatly increasing the advantage of $V$'s specificity.
-   The proposal of [Inverse Reinforcement Learning](https://www.lesswrong.com/w/inverse-reinforcement-learning) would have the AI specifically assume that the [true](https://www.lesswrong.com/w/ideal-target) $U$ is correlated to whatever it sees the behavior of its operators tending to maximize. [^note-3]

## The problem of updated deference ^the-problem-of-updated

Counter-arguendo, the reason this approach via moral uncertainty may fail to solve the [shutdown problem](https://www.lesswrong.com/w/shutdown-problem) (or the [corrigibility in general](https://www.lesswrong.com/w/hard-problem-of-corrigibility)) is that the AI may consider an [alternative policy option](https://www.lesswrong.com/w/missing-the-weird-alternative):

-   $\pi_6$: Avoid being shut down; then gather more evidence $E$ to update $\Delta U$ as far as possible; then optimize the updated $\Delta U | E$.

This would tend to lead into a narrower $\Delta U | E$ and an outcome $u_{\Delta U | E}$ much more specific to the true $U_i$, so that the human optimum $v_i$ would be at much less of an advantage.

This is the problem of getting the AI to 'defer' to us (prefer human optimization of $V$ to its own optimization of $\Delta U$) despite the future evidence that the AI thinks it can potentially gather to 'update' to $\Delta U|E$. This [open problem](https://www.lesswrong.com/w/ai-alignment-open-problem) is tentatively named the "problem of updated deference". [^note-4]

### Attempted rescue by AI unobservability ^attempted-rescue-by-ai

One possible attempt to rescue the original proposal might be to try to construct a meta-utility function such that the AI believes it can't learn by observation which of $U_2$ or $U_3$ are true; in other words, such that the AI does not believe it can update much further.

However, this directly cuts against the condition, also required for deference, that:

-   The AI believes that humans optimize a $V_2$ well-suited to $U_2$ in possible worlds where $U_2$ is the true $U$, and that humans optimize a $V_3$ well-suited to $U_3$ in possible worlds where $U_3$ is the true $U$.

Then the AI can learn well by observing human behavior, since empirical human behavior must correlate with the [true](https://www.lesswrong.com/w/ideal-target) $U$ according to the AI's meta-utility function.

Can we try to have the AI believe that observable human behavior is uninformative or ambiguous as to the [true](https://www.lesswrong.com/w/ideal-target) $U$?

But this cuts directly against the required condition:

-   There are no policies which are simultaneously very good at optimizing $U_2$ and $U_3$, compared to how well the specialized $V_i$ can do for particular $U_i$.

That is, if there are things humans can do that are simultaneously pretty good at optimizing all the remaining plausible $V_i$ (hence uniformative), and these are pretty good at optimizing the remaining plausible $U_i$ (hence acceptable to the AI), there are probably things the AI can do which would be even better at simultaneously optimizing all remaining $U_i$.

What if the AI has moral uncertainty that doesn't correlate to human behavior at all, and can't be resolved by any possible observation? Then — leaving aside that the AI has no incentive to _defer_ to humans in this case — we should expect the AI to at some point decide that it has obtained all possible information about $U$ and cannot find any policy that leads to a further update of $\Delta U$. At this point the AI behaves as if optimizing a constant utility function $U_\Delta = \sum_i \mathbb P_{\Delta}(i) \cdot U_i$, where $\mathbb P_\Delta$ indicates the probability distribution after the AI has updated its moral uncertainty as far as it could. That is, the AI marginalizes over its remaining uncertainty since that uncertainty cannot be resolved.

## Relation to the general problem of fully updated value identification ^relation-to-the-general

One way to look at the central problem of [value identification](https://www.lesswrong.com/w/value-identification-problem) in [superintelligence](https://www.lesswrong.com/w/superintelligent) is that we'd ideally want some function that takes a complete but purely physical description of the universe, and spits out our [true intended](https://www.lesswrong.com/w/intended-goal) notion of [value](https://www.lesswrong.com/w/value) $V$ in all its glory. Since superintelligences would probably be pretty darned good at collecting data and guessing the empirical state of the universe, this probably solves the whole problem.

This is not the same problem as writing down our true $V$ by hand. The minimum [algorithmic complexity](https://www.lesswrong.com/w/algorithmic-complexity) of a meta-utility function $\Delta U$ which outputs $V$ after updating on all available evidence, seems [plausibly much lower](https://www.lesswrong.com/w/meta-rules-for-narrow-value-learning-are-still-unsolved) than the minimum algorithmic complexity for writing $V$ down directly. But as of 2017, nobody has yet floated any _formal_ proposal for a $\Delta U$ of this sort which has not been immediately shot down.

(There is one _informal_ suggestion for how to turn a purely physical description of the universe into $V$, [coherent extrapolated volition](https://www.lesswrong.com/w/coherent-extrapolated-volition-alignment-target). But CEV does not look like we could write it down as an algorithmically _simple_ function of [sense data](https://www.lesswrong.com/w/identifying-causal-goal-concepts-from-sensory-data), or a simple function over the [unknown true ontology](https://www.lesswrong.com/w/ontology-identification-problem) of the universe.)

We can then view the problem of updated deference as follows:

For some $\Delta U$ we do know how to write down, let $T$ be the hypothetical result of updating $\Delta U$ on all empirical observations the AI can reasonably obtain. By the argument given in the previous section, any uncertainty the AI deems unresolvable will behave as if marginalized out, so we can view $T$ as a simple utility function.

For any prior $\Delta U$ we currently know how to formalize, the corresponding fully updated $T$ [seems likely to be very far from our ideal](https://www.lesswrong.com/w/meta-rules-for-narrow-value-learning-are-still-unsolved) $V$ and to have its optimum far away from the default result of us trying to optimize our intuitive values. [If the AI figures out](https://www.lesswrong.com/w/omnipotence-test-for-ai-safety) this _true_ fact, similar [instrumental pressures](https://www.lesswrong.com/w/instrumental-pressure) emerge as if we had given the AI the constant utility function $T$ divergent from our equivalent of $V$.

This problem [reproduces itself on the meta-level](https://www.lesswrong.com/w/reproduces-itself-on-the-meta-level): the AI also has a default incentive to resist our attempt to tweak its meta-utility function $\Delta U$ to a new meta-utility function $\Delta \dot U$ that updates to something other than $T$. By default and ceteris paribus, this seems liable to be treated by the agent in [exactly the same way it would treat](https://www.lesswrong.com/w/consequentialist-preferences-are-reflectively-stable-by) us trying to tweak a constant utility function $U$ to a new $\dot U$ with an optimum far from $U$'s optimum.

If we _did_ know how to specify prior $\Delta U$ such that updating it on data a superintelligence could obtain would reliably yield $T \approx V$, the problem of aligned superintelligence would have been reduced to the problem of building an AI with that meta-utility function. We could just specify $\Delta U$ and tell the AI to self-improve as fast as it wants, confident that true [value](https://www.lesswrong.com/w/value) would come out the other side. Desired behaviors like "be cautious in what you do while learning" could probably be realized as the consequence of informing the young AI of true facts within the $\Delta U$ framework (e.g. "the universe is fragile, and you'll be much better at this if you wait another month to learn more, before you try to do anything large"). Achieving [general cognitive alignment](https://www.lesswrong.com/w/generalized-principle-of-cognitive-alignment), free of [adversarial](https://www.lesswrong.com/w/non-adversarial-principle) situations, would probably be much more straightforward.

But short of this total solution, morally uncertain $\Delta U$ with a misaligned [ideal target](https://www.lesswrong.com/w/ideal-target) $T$ may not make progress on corrigibility in [sufficiently advanced](https://www.lesswrong.com/w/sufficiently-advanced-artificial-intelligence) AIs. And this may also be true at earlier points when $\Delta U$ has not fully updated, if the current AI correctly realizes that it will update later.

To make this argument slightly less informal, we could appeal to the premises that:

-   Bayesians [don't update in a predictable direction](https://www.lesswrong.com/w/conservation-of-expected-evidence);
-   Sufficiently advanced cognitive agents would be [relatively efficient](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) compared to humans, since we know of no human cognitive capability too magical to be duplicated and exceeded;
-   Sufficiently advanced cognitive agents will appear to us to exhibit behavior that is, for all we know, compatible with their having [coherent probabilities and utilities](https://www.lesswrong.com/w/expected-utility-formalism?lens=intro_utility_coherence); since, by efficiency, strategies so bad that even we can see they are dominated will have been ironed out.

Then, if we can predict that the AI would update to wanting to run the universe itself without human interference after the AI had seen all collectable evidence, a [sufficiently advanced AI](https://www.lesswrong.com/w/sufficiently-advanced-artificial-intelligence) can also see that this update is predictable (by efficiency) and therefore behaves as if it had already updated (by Bayesianism). Efficiency is a sufficient condition but not a necessary one; [high-human](https://www.lesswrong.com/w/infrahuman-par-human-superhuman-efficient-optimal) reasoning over the meta-level question also seems sufficient, and perhaps even [infrahuman](https://www.lesswrong.com/w/infrahuman-par-human-superhuman-efficient-optimal) reasoning would suffice.

Therefore, we should expect a sufficiently intelligent AI, given a morally uncertain utility function $\Delta U$ that updates to $\Delta U | E \approx T$ given all available evidence, to behave as corrigibly or incorrigibly as an AI given a constant utility function $T$. This is a problem from the viewpoint of anyone who thinks we [do not currently know](https://www.lesswrong.com/w/meta-rules-for-narrow-value-learning-are-still-unsolved) how to pick $\Delta U$ such that surely $\Delta U | E \approx V$, which makes corrigibility still necessary.

## Further research avenues ^further-research-avenues

The motivation for trying to solve corrigibility with moral uncertainty is that this seems in some essential sense [conjugate to our own reasoning](https://www.lesswrong.com/w/generalized-principle-of-cognitive-alignment) about why we want the AI to shut down; _we_ don't think the AI has the correct answer. A necessary step in echoing this reasoning inside the AI seems to be a meta-utility function taking on different object-level utility functions in different possible worlds; without this we cannot represent the notion of a utility function being guessed incorrectly. If the argument above holds, that necessary step is however not sufficient.

What more is needed? On one approach, we would like the AI to infer, in possible worlds where the humans try to shut the AI down, that _even the fully updated_ $\Delta U | E$ ends up being wronger than humans left to their own devices, compared to the 'true' $U$. This is what we believe about the AI relative to the true $V$, so we should [look for a way to faithfully echo that reasoning](https://www.lesswrong.com/w/generalized-principle-of-cognitive-alignment) inside the AI's beliefs about its true $U$.

The fundamental obstacle is that for any explicit structure of uncertainty $\Delta U$ and meaningful observation $e_0$ within that structure--e.g. where $e_0$ might be seeing the humans moving toward the shutdown button--we must ask, why wouldn't $\Delta U$ just update on that $e_0$? Why would the updated $\Delta U | e_0$ still expect its own reasoning to be bad?

Generally, decision systems think that optimizing their utility functions based on their current beliefs is a good idea. If you show the decision system new evidence, it updates beliefs and then thinks that optimizing its utility function on the updated beliefs is a good idea. Optimizing the utility function based on all possible evidence is the best idea. This reasoning doesn't yet change for meta-utility functions evidentially linked to human behaviors.

Averting this convergent conclusion seems like it might take a new meta-level idea involving some broader space of possible 'true' preference frameworks; or perhaps some nontrivially-structured recursive belief about one's own flawedness.

One suggestively similar such recursion is the [Death in Damascus dilemma](https://www.lesswrong.com/w/death-in-damascus) from decision theory. In this dilemma, you must either stay in Damascus or flee to Aleppo, one of those cities will kill you, and Death (an excellent predictor) has told you that whichever decision you actually end up making turns out to be the wrong one.

[Death in Damascus yields complicated reasoning that varies between decision theories](https://www.lesswrong.com/w/death-in-damascus), and it's not clear that any decision theory yields reasoning we can adapt for corrigibility. But we want the AI to internally echo our external reasoning in which we think $\Delta U$, as we defined that moral uncertainty, _ends up_ updating to the wrong conclusion even after the AI tries to update on the evidence of the humans believing this. We want an AI which somehow believes that its own $\Delta U$ can be _fundamentally_ flawed: that whatever reasoning the AI ends up doing about $\Delta U$, on any meta-level, will yield the wrong answer compared to what $\Delta U$ defines as the true $U$; to furthermore believe that the human $V$ will do better under this true $U$; to believe that this state of affairs is evidentially indicated by the humans trying to shut down the AI; and believe that $\Delta U$ still updates to the wrong answer even when the AI tries to update on all the previous meta-knowledge; except for the meta-meta answer of just shutting down, which becomes the best possible choice given all the previous reasoning. This seems suggestively similar in structure to Death's prediction that whatever you do will be the wrong decision, even having taken Death's statement into account.

The Death in Damascus scenario can be well-represented in some (nonstandard) decision theories. This presents one potential avenue for further formal research on using moral uncertainty to yield shutdownability--in fact, using moral uncertainty to solve in general the [hard problem of corrigibility](https://www.lesswrong.com/w/hard-problem-of-corrigibility).

[^note-1]: Pretending for the sake of simplification that $V$ has been [idealized](https://www.lesswrong.com/w/extrapolated-volition-normative-moral-theory) or [rescued](https://www.lesswrong.com/w/rescuing-the-utility-function) into a utility function.
[^note-2]: So that for purposes of the simplified scenario, we only need to consider what the AI does about the button, and not whether the AI tries to back itself up to elsewhere on the Internet. More generally, though, "avoiding effective shutdown" can include strategies like creating a hidden backup while the original hardware is in fact shut down, thus giving the appearance of a successful shutdown and avoiding further shutdown attempts.
[^note-3]: This idea comes with its own arguable problems — e.g. humans sometimes optimize bad things. Let us set those aside while considering only whether this approach solves the [shutdown problem](https://www.lesswrong.com/w/shutdown-problem) in particular.
[^note-4]: This issue was first observed in analyzing [historical-fact shutdown](https://www.lesswrong.com/w/historical-fact-shutdown) as a possible alternative to [utility indifference](https://www.lesswrong.com/w/utility-indifference).
