---
title: "Pivotal act"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/pivotal"
published: 2015-06-12
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "Which types of AIs, if they work, can do things that drastically change the nature of the further game?"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

The term ‘pivotal act’ in the context of [AI alignment theory](https://arbital.greaterwrong.com/p/ai_alignment?l=2v) is a [guarded term](https://arbital.greaterwrong.com/p/guarded_definition?l=10l) to refer to actions that will make a large positive difference a billion years later. Synonyms include ‘pivotal achievement’ and ‘astronomical achievement’.

We can contrast this with _existential catastrophes_ (or ‘x-catastrophes’), events that will make a large _negative_ difference a billion years later. Collectively, this page will refer to pivotal acts and existential catastrophes as _astronomically significant events_ (or ‘a-events’).

‘Pivotal _event_’ is a deprecated term for referring to astronomically significant events, and ‘pivotal catastrophe’ is a deprecated term for existential catastrophes. ‘Pivotal’ was originally used to refer to the superset (a-events), but AI alignment researchers kept running into the problem of lacking a crisp way to talk about ‘winning’ actions in particular, and their distinctive features.

Usage has therefore shifted such that (as of late 2021) researchers use ‘pivotal’ and ‘pivotal act’ to refer to _good_ events that upset the current gameboard—events that decisively settle a [win](https://arbital.greaterwrong.com/p/value_alignment_value?l=55), or drastically increase the probability of a win.

### Reason for guardedness ^reason-for-guardedness

[Guarded definitions](https://arbital.greaterwrong.com/p/guarded_definition?l=10l) are deployed where there is reason to suspect that a concept will otherwise be over-extended. The case for having a guarded definition of ‘pivotal act’ (and another for ‘existential catastrophe’) is that, after it’s been shown that event X is maybe not as important as originally thought, one side of that debate may be strongly tempted to go on arguing that, wait, really it could be “relevant” (by some [strained](https://arbital.greaterwrong.com/p/strained_argument?l=10m) line of possibility).

**Example 1**: In the [Zermelo-Fraenkel provability oracle](https://arbital.greaterwrong.com/p/ZF_provability_oracle?l=70) dialogue, Alice and Bob consider a series of possible ways that an untrusted [oracle](https://arbital.greaterwrong.com/p/oracle?l=6x) could break an attempt to [box](https://arbital.greaterwrong.com/p/AI_boxing?l=6z) it. We end with an extremely boxed oracle that can only output machine-checkable proofs of predefined theorems in Zermelo-Fraenkel set theory, with the proofs themselves being thrown away once machine-verified.

The dialogue then observes that there isn’t currently any obvious way to save the world by finding out that particular pre-chosen theorems are provable.

It may then be tempting to argue that this device could greatly advance the field of mathematics, and that math is relevant to the AI alignment problem. However, at least given that particular proposal for using the ZF oracle, the basic rules of the AI-development playing field would remain the same, the AI alignment problem would not be _finished_ nor would it have moved on to a new phase, the world would still be in danger (neither safe nor destroyed), etcetera.

(This doesn’t rule out that tomorrow some reader will think of some spectacularly clever use for a ZF oracle that _does_ upset the chessboard and get us on a direct path to winning where we know what we need to do from there—and in this case MIRI would reclassify the ZF oracle as a high-priority research avenue!)

**Example 2**: Suppose a funder, worried about the prospect of advanced AIs wiping out humanity, starting offering grants for “AI safety”. It may then be tempting to try to write papers that you know you can finish, like a paper on robotic cars [causing unemployment](https://arbital.greaterwrong.com/p/EliezerYudkowsky.RobotsAIUnemploymentAntiFAQ?l=3b) in the trucking industry, or a paper on who holds legal liability when a factory machine crushes a worker. These have the advantage of being much less difficult problems than those involved in making something actually smarter than you be safe.

But while it’s true that crushed factory workers and unemployed truckers are both, ceteris paribus, bad, they are not _existential catastrophes that transform all galaxies inside our future light cone into paperclips_, and the latter category seems worth distinguishing.

This definition needs to be guarded because there may then be a temptation for the grantseeker to argue, “Well, if AI causes unemployment, that could slow world economic growth, which will make countries more hostile to each other, which would make it harder to prevent an AI arms race.” The possibility of something ending up having a _non-zero impact_ on astronomical stakes is not the same concept as events that have a _game-changing impact_ on astronomical stakes.

The question is what are the largest lowest-hanging fruit in astronomical stakes, not whether something can be argued as defensible by pointing to a non-zero astronomical impact.

**Example 3**: Suppose a [behaviorist genie](https://arbital.greaterwrong.com/p/behaviorist?l=102) is restricted from modeling human minds in any great detail, but is still able to build and deploy molecular nanotechnology. Moreover, the AI is able to understand the instruction, “Build a device for scanning human brains and running them at high speed with minimum simulation error”, and is able to work out a way to do this without simulating whole human brains as test cases. The genie is then used to upload a set of, say, fifty human researchers, and run them at 10,000-to-1 speeds.

This accomplishment would not of itself save the world or destroy it—the researchers inside the simulation would still need to solve the alignment problem, and might not succeed in doing so.

But it would (positively) _upset the gameboard_ and change the major determinants of winning, compared to the default scenario where the fifty researchers are in an equal-speed arms race with the rest of the world, and don’t have practically-unlimited time to check their work. The event where the genie was used to upload the researchers and run them at high speeds would be a critical event, a hinge where the optimum strategy was drastically different before versus after that pivotal act.

**Example 4**: Suppose a paperclip maximizer is built, self-improves, and converts everything in its future light cone into paperclips. The fate of the universe is then settled in the negative direction, so building the paperclip maximizer was an existential catastrophe.

**Example 5**: A mass simultaneous malfunction of robotic cars causes them to deliberately run over pedestrians in many cases. Humanity buries its dead, picks itself up, and moves on. This was not an existential catastrophe, even though it may have nonzero influence on future AI development.

**Discussion**: Many [strained arguments](https://arbital.greaterwrong.com/p/strained_argument?l=10m) for X being a pivotal act have a step where X is an input into a large pool of goodness that also has many other inputs. A ZF provability oracle would advance mathematics, and mathematics can be useful for alignment research, but there’s nothing obviously game-changing about a ZF oracle that’s specialized for advancing alignment work, and it’s unlikely that the effect on win probabilities would be large relative to the many other inputs into total mathematical progress.

Similarly, handling trucker disemployment would only be one factor among many in world economic growth.

By contrast, a genie that uploaded human researchers putatively would _not_ be producing merely one upload among many; it would be producing the only uploads where the default was otherwise no uploads. In turn, these uploads could do decades or centuries of unrushed serial research on the AI alignment problem, where the alternative was rushed research over much shorter timespans; and this can plausibly make the difference by itself between an AI that achieves ~100% of value versus an AI that achieves ~0% of value. At the end of the extrapolation where we ask what difference everything is supposed to make, we find a series of direct impacts producing events qualitatively different from the default, ending in a huge percentage difference in how much of all possible value gets achieved.

By having narrow and guarded definitions of ‘pivotal acts’ and ‘existential catastrophes’, we can avoid bait-and-switch arguments for the importance of research proposals, where the ‘bait’ is raising the apparent importance of ‘AI safety’ by discussing things with large direct impacts on astronomical stakes (like a paperclip maximizer or Friendly sovereign) and the ‘switch’ is to working on problems of dubious astronomical impact that are inputs into large pools with many other inputs.

### ‘Dealing a deck of cards’ metaphor ^dealing-a-deck-of

There’s a line of reasoning that goes, “But most consumers don’t want general AIs, they want voice-operated assistants. So companies will develop voice-operated assistants, not general AIs.” But voice-operated assistants are themselves not astronomically significant events; developing them doesn’t prevent general AIs from being developed later. So even though this non-astronomically-significant event precedes a more significant event, it doesn’t mean we should focus on the earlier event instead.

No matter how many non-game-changing ‘AIs’ are developed, whether playing great chess or operating in the stock market or whatever, the underlying research process will keep churning and keep turning out other and more powerful AIs.

Imagine a deck of cards which has some aces (superintelligences) and many more non-aces. We keep dealing through the deck until we get a black ace, a red ace, or some other card that _stops the deck from dealing any further_.

A non-ace Joker card that permanently prevents any aces from being drawn would be ‘astronomically significant’ (not necessarily good, but definitely astronomically significant).

A card that shifts the further distribution of aces in the deck from 10% red to 90% red would be pivotal; we could see this as a metaphor for the hoped-for result of Example 3 (uploading the researchers), even though the game is not then stopped and assigned a score.

A card that causes the deck to be dealt 1% slower or 1% faster, that eliminates a non-ace card, that adds a non-ace card, that changes the proportion of red non-ace cards, etcetera, would not be astronomically significant. A card that raises the probability of a red ace from 50% to 51% would be highly desirable, but not pivotal—it would not qualitatively change the nature of the game.

Giving examples of non-astronomically-significant events that could precede or be easier to accomplish than astronomically significant ones doesn’t change the nature of the game where we keep dealing until we get a black ace or red ace.

### Examples of possible events ^examples-of-possible-events

Existential catastrophes:

-   non-value-aligned AI is built, takes over universe
    
-   a complete and detailed synaptic-vesicle-level scan of a human brain results in cracking the cortical and cerebellar algorithms, which rapidly leads to non-value-aligned neuromorphic AI
    

Potential pivotal acts:

-   human intelligence enhancement powerful enough that the best enhanced humans are qualitatively and significantly smarter than the smartest non-enhanced humans
    
-   a limited [Task AGI](https://arbital.greaterwrong.com/p/task_agi?l=6w) that can:
    
    -   upload humans and run them at speeds more comparable to those of an AI
        
    -   prevent the origin of all hostile superintelligences (in the nice case, only temporarily and via strategies that cause only acceptable amounts of collateral damage)
        
    -   design or deploy nanotechnology such that there exists a direct route to the operators being able to do one of the other items on this list (human intelligence enhancement, prevent emergence of hostile SIs, etc.)
    

Non-astronomically-significant events:

-   curing cancer (good for you, but it didn’t resolve the alignment problem)
    
-   proving the Riemann Hypothesis (ditto)
    
-   an extremely expensive way to augment human intelligence by the equivalent of 5 IQ points that doesn’t work reliably on people who are already very smart
    
-   making a billion dollars on the stock market
    
-   robotic cars devalue the human capital of professional drivers, and mismanagement of aggregate demand by central banks plus burdensome labor market regulations is an obstacle to their re-employment
    

Borderline-astronomically-significant cases:

-   unified world government with powerful monitoring regime for ‘dangerous’ technologies
    
-   widely used gene therapy that brought anyone up to a minimum equivalent IQ of 120
    

### Centrality to limited AI proposals ^centrality-to-limited-ai

We can view the general problem of Limited AI as having the central question: **What is a pivotal act, such that an AI which does that thing and not some other things is therefore a whole lot safer to build?**

This is not a trivial question because it turns out that most interesting things require general cognitive capabilities, and most interesting goals can require arbitrarily complicated value identification problems to pursue safely.

It’s trivial to create an “AI” which is absolutely safe and can’t be used for any pivotal acts. E.g. Google Maps, or a rock with “2 + 2 = 4″ painted on it.

(For arguments that Google Maps could potentially help researchers drive to work faster or that a rock could potentially be used to bash in the chassis of a hostile superintelligence, see the pages on [guarded definitions](https://arbital.greaterwrong.com/p/guarded_definition?l=10l) and [strained arguments](https://arbital.greaterwrong.com/p/strained_argument?l=10m).)

### Centrality to concept of ‘advanced agent’ ^centrality-to-concept-of

We can view the notion of an advanced agent as “agent with enough cognitive capacity to cause an astronomically significant event, positive or negative”; the [advanced agent properties](https://arbital.greaterwrong.com/p/advanced_agent?l=2c) are either those properties that might lead up to participation in an astronomically significant event, or properties that might play a critical role in determining the AI’s trajectory and hence how the event turns out.

### Policy of focusing effort on enacting pivotal acts or preventing existential catastrophes ^policy-of-focusing-effort

Obvious utilitarian argument: doing something with a big positive impact is better than doing something with a small positive impact.

In the larger context of effective altruism and adequacy theory, the issue is a bit more complicated. Reasoning from adequacy theory says that there will often be barriers (conceptual or otherwise) to the highest-return investments. When we find that hugely important things seem _relatively neglected_ and hence promising of high marginal returns if solved, this is often because there’s some conceptual barrier to running ahead and doing them.

For example: tackling the hardest problems is often much scarier (you’re not sure if you can make any progress on describing a self-modifying agent that provably has a stable goal system) than ‘bouncing off’ to some easier, more comprehensible problem (like writing a paper about the impact of robotic cars on unemployment, where you’re very sure you can in fact write a paper like that at the time you write the grant proposal).

The obvious counterargument is that perhaps you can’t make progress on your problem of self-modifying agents, perhaps it’s too hard. But from this it doesn’t follow that the robotic-cars paper is what we should be doing instead—the robotic cars paper only makes sense if there are _no_ neglected tractable investments that have bigger relative marginal inputs into astronomically significant events.

If there are in fact some neglected tractable investments in gameboard-flipping acts, then we can expect a search for gameboard-flipping acts to turn up superior places to invest effort. But a failure mode of this search is if we fail to cognitively guard the concept of ‘pivotal act’.

In particular, if we’re allowed to have indirect arguments for ‘relevance’ that go through big common pools of goodness like ‘friendliness of nations toward each other’, then the pool of interventions inside that concept is so large that it will start to include things that are optimized to be appealing under more usual metrics, such as papers that don’t seem unnerving and that somebody knows they can write.

So if there’s no guarded concept of research on ‘pivotal’ things, we will end up with very standard research being done, the sort that would otherwise be done by academia anyway, and our investment will end up having a low expected marginal impact on the final outcome.

This sort of qualitative reasoning about what is or isn’t ‘pivotal’ wouldn’t be necessary if we could put solid numbers on the impact of each intervention on the probable achievement of astronomical goods. But that is an unlikely ‘if’. Thus, there’s some cause to reason qualitatively about what is or isn’t ‘pivotal’, as opposed to just calculating out the numbers, when we’re trying to pursue astronomical altruism.
