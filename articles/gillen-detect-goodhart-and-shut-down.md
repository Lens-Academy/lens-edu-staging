---
title: "Detect Goodhart and shut down"
author:
  - "Jeremy Gillen"
source_url: "https://www.lesswrong.com/posts/ZHFZ6tivEjznkEoby/detect-goodhart-and-shut-down"
published: 2025-01-22
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "A common failure of optimizers is Edge Instantiation. An optimizer often finds a weird or extreme solution to a problem when the optimization objecti…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A [common](https://docs.google.com/spreadsheets/d/e/2PACX-1vRPiprOaC3HsCf5Tuum8bRfzYUiKLRqJmbOoC-32JorNdfyTiRRsR7Ea5eWtvsWzuxo8bjOxCG84dAg/pubhtml) failure of optimizers is [Edge Instantiation](https://arbital.greaterwrong.com/p/edge_instantiation/). An optimizer often finds a weird or extreme solution to a problem when the optimization objective is imperfectly specified. For the purposes of this post, this is basically the same phenomenon as [Goodhart’s Law](https://en.wikipedia.org/wiki/Goodhart%27s_law), especially [Extremal](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy#Extremal_Goodhart) and [Causal](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy#Causal_Goodhart) Goodhart. With advanced AI, we are worried about plans created by optimizing over predicted consequences of the plan, potentially achieving the goal in an unexpected way.

In this post, I want to draw an analogy between Goodharting (in the sense of finding extreme weird solutions) and overfitting (in the ML sense of finding a weird solution that fits the training data but doesn’t generalize). I believe techniques used to address overfitting are also useful for addressing Goodharting.[^note-1]

In particular, I want to focus on _detecting_ Goodharting. The way we detect overfitting is using a validation set of data. If a trained ML model scores well on a validation set, _without having been optimized to score well on it,_ this is a great signal that the model hasn’t overfit. I think we can use an analogous technique to detect weird plans that exploit loopholes in the outcome specification.

After this, I’ll propose a technique for installing this method of “Goodhart detection” into the goal of an agent, such that the agent will _want_ to shutdown if it learns that its plan is Goodharting.

I’m not sure whether this scheme is original, but I haven’t yet found any prior discussion of it. I’m posting it because it’s likely there are some fatal flaws.

## What’s the analogue of validation sets, for goals? ^whats-the-analogue-of

The reason it's possible to have a validation set in ML is that the dataset is big enough that the correct model is overspecified. Because we have too much data, we can remove some (the validation set), and train only on the remainder (the training set), and this is sufficient to find a good model. We can think of each data-point as a contribution to the overall loss function. Each datapoint has a loss function, and the sum of all these creates the overall loss function that we minimize.[^note-2]

If we want to transfer this idea to a planning context, the main barrier is that a “goal” doesn’t necessarily decompose into lots of little contributing pieces in the same way that a loss function does. Stereotypically, a goal is something small and simple like “maximize the game score” or “a hot cup of coffee should be in front of me in 5 minutes”.

So the first step of my scheme requires that we put more effort into specifying the goal in multiple ways. We want to create lots of redundant parts that, taken together, over-specify the goal that we want. How do we do this? When we want to specify an outcome, we describe 1) properties of that outcome 2) properties of plans that we expect will lead to the desired outcome and 3) downstream consequences of the desired outcome. And for each of these, we can try to use descriptions at multiple levels of abstraction.

For example, say we want to program our [task-based AI](https://www.lesswrong.com/w/taskagi_open_problems) to give us an [exact copy of a strawberry](https://x.com/ESYudkowsky/status/1070095840608366594), up to a cellular level but not molecular level. The first problem of goal specification is that it needs to be in a language that interfaces directly with the world model of the task-based AI, and we don’t know quite how to interface like that. But let’s set aside that difficulty, and assume we can translate concrete statements about physical reality into the world model.

Here’s how we specify the goal:

-   1) Describing the intended outcome, at different levels of abstraction

1.  What the copy should look like from various angles using a normal camera.
2.  The approximate chemical decomposition of every 0.01mm3 volume of the space where we want our strawberry.
3.  The number of cells, and cell types, and locations.
4.  The _lack of_ difference between the ‘world-outside-this-room’ and the ‘world-outside-this-room-if-no-actions-were-taken’.

-   2) Properties of plans that we expect will lead to the desired outcome

1.  The amount of "effort" involved in the plan, as measured by e.g. energy consumption and/or thinking time and/or physical resources.
2.  Nano-scale machines capable of copying themselves _shouldn’t_ be built as any part of the plan.
3.  If we have a probabilistic model of what "normal" plans look like,[^note-3] we might also specify roughly how “normal” we expect the plan to be. Multiple different models can be used.
    

-   3) Downstream consequences of the desired outcome.

1.  The output of experiments that could be run to compare the two strawberries. E.g. expected differences under an electron microscope, and expected similarities under NMR spectroscopy.
2.  Lack of effect on variables measuring any quantity in the world-outside-this-room. E.g. world population, approximate energy use, biomass within 100km in 50 days  and 5000 days, EM radiation in the surrounding 100km bubble, etc.

Having done that, we can split these specifications into two sections, which we might call the target goal and the validation goal.

To continue the example, we could set aside 1c, 2b, and 3b to be the validation set. We _expect_ that the remainder (1a,1b,1d,2a,2c and 3a) is sufficient to safely specify the outcome we want, but we aren’t confident that a powerful optimizer wouldn’t find some exploit.

So we put (1a,1b,1d,2a,2c and 3a) into the optimizer, and it produces a plan which is expected to achieve all of those outcomes and conditions. Then we can take that plan, and check whether it also satisfies 1c, 2b, and 3b. If it does, this is good news! The plan passed validation, without having been _optimized_ to pass validation. If it doesn’t, the objective is unsafe and needs to be reworked.

:::callout {title="Another simpler example for the goal “bring me some coffee”" collapse="closed"}
We could specify the goal with:

1.  In 5 minutes, user has hot coffee on desk.

As a validation set:

1.  Energy, water, gas usage rate of the building stays within normal bounds.
2.  There are no loud noises generated within the house in the next 5 minutes.
3.  The number of people in the house stays the same.
4.  The number of people expected to visit the building over the next week doesn’t change as a result of doing the plan.
5.  EM radiation stays roughly within the same bounds.
6.  Money spent by everyone in the vicinity stays roughly the same.
7.  No action-relevant information is sent from inside the building to outside the building.
8.  The kettle in the kitchen is used to boil the water.
9.  The coffee grounds in the cupboard are used.
::: 

This gives us a convenient warning flag for Goodharting. Clearly, it’s not foolproof. Very careful hand-crafting of the goal and validation is necessary. It’d be easy to rework the goal each time it didn’t pass validation, until it did pass validation (effectively training on the validation set).

However, the main flaw is that it won’t work if the planner is “situationally aware”, in the sense that it knows that its plan will be checked against some validation set. If this is the case, a clever planner will treat the validation step as an obstacle, and look for ways to overcome it.

## Fact-conditional goals ^fact-conditional-goals

Let’s try to extend this idea to work in a more situationally aware agent. For this we’ll need _fact-conditional goals_. An example of a fact-conditional goal is "if `God exists` I want `to obey God` else `maximize my own happiness`". Note that this is a terminal goal, and 'obey God' isn’t done because it’s instrumentally useful for maximizing happiness. It’s done for its own sake. A better example, to emphasize the flexibility of this kind of goal, might be "if `all swans are white` then I want `diamonds` else `knowledge`". This is an odd goal to pursue, but it's completely allowed. A fact-conditional goal can fit nicely with [VNM utility theory](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem), as long as the fact is considered to be a part of the outcome space.

We want to take our intended goal specification `g`, and wrap it in a fact-conditional goal that says "if `g is correctly specified` I want `g`, else `shutdown`". If this works as intended, you have an agent that shuts down upon noticing that its goal specification is hackable. The main difficulty is correctly specifying the fact `g is correctly specified`. There should be only one source of evidence that can update the agent’s beliefs about this fact, which is a non-rigged test of whether a plan optimized purely for `g` also passes the validation goal.

The thing we’re trying to avoid is any incentive to “manage the news”, i.e. rig the test to allow continued pursuit of `g`. If the agent treats `g is correctly specified` as an influenceable property of the world, then it will attempt to influence that property in whichever direction is most valued. Instead, we want `g is correctly specified` to be treated like a logical fact, or perhaps a fact in the uninfluencable past. This _should_ be a natural idea to implement in a world model, because it’s very common. Lots of facts are about the past. Collecting information about the past is a natural activity of agents. It’s also fairly common to have beliefs about the past, which we can only update by carefully unbiased experiments. But actually specifying this specific type of belief in the world model of an advanced AI could be very difficult.

## The escape valve ^the-escape-valve

If we fail to correctly specify the `g is correctly specified` variable, it might be manipulable. To reduce the harm of this failure, we can put higher utility on the `shutdown` branch of the utility function. This way, if the agent rigs the experiment, it'll want to rig it in such a way that it leads to immediate shutdown.

## Semi-formalization ^semi-formalization

For explanatory purposes, here’s a semi-formalized version of the scheme.

Let `g` be the goal, `q` be the validation goal and `shutdown` be the goal that says to shutdown immediately. We have a world model WM, which is a function that takes a plan `p` and goal `g`, and outputs true iff the goal is achieved by the plan. We have an optimizer `O` which takes `WM` and `g`, and outputs some plan `p` that achieves `g`.

Internal to `WM` we insert a variable `h` = `g is correctly specified`. `h` is connected to evidence like so:

If, counterfactually, `O(WM, g)` was executed right now to produce plan `p`, would `WM(p, q)` be true? If so, this is evidence that `g is correctly specified` (therefore $\mathbb P(h) \gg 0.5$ ). Else, $\mathbb P(h) \ll 0.5$.

We create the wrapper goal `u` = ''`g` if `h` else `shutdown`".

Here’s what happens:

1.  We execute `O(WM, u)` to produce a plan, then begin executing the plan.
2.  The plan has noted the information value of learning `h`, so it executes `WM(O(WM, g),q)` to resolve this uncertainty.
3.  If the validation passes, it continues on and executes the rest of the plan which pursues `g`. Otherwise it pursues `shutdown`.

## Final thoughts ^final-thoughts

One possible issue arises if the call to `O(WM, g)` has any level of situational awareness. If so, it would attempt to produce a plan that passes the validation, in order to increase the chances of achieving `g`. The way to avoid this is to be very careful about the knowledge available to `WM` during this call to `O`. `WM` should believe that it is in the same situation that it was in when `O(WM, u)` was executed, so it believes its plan will immediately be executed without having to jump through any validation hoops. This is a load bearing assumption of the scheme: that it is easy to execute `O(WM, g)` without leaking situational information to the process. I think this assumption is fairly reasonable, because simulating other agents is _really common_ in practice.[^note-4] The required information hygiene must be feasible to implement.

The reason I'm having the agent execute its own validation test is because I’m hoping this scheme can be extended to work in a more online setting, where for example the agent might only be able to notice halfway through implementing the plan that some of the validation fails.

In this post I'm relying on an ontology where advanced AI can be usefully modeled by factoring it into a global optimizer and world model. It doesn't capture all the relevant details,[^note-5] but I think it's an adequate approximation. 

---

I’m guessing that this kind of scheme has been discussed before. I haven’t seen it though, so I thought I’d write it up so I can get feedback and links to previous discussion. One idea that seems similar-in-spirit is [this](https://www.lesswrong.com/posts/AFJgo99YckQnhbF8Z/thinking-about-maximization-and-corrigibility#The_road_to_corrigibility) intuitive scheme for corrigibility. Except my scheme isn’t attempting to solve corrigibility, it’s aiming for a more narrow patch for Goodharting.

_Thanks to harfe and Justis for feedback on this post._

[^note-1]: The main technique for directly reducing overfitting is regularization. Two analogues for regularization are [Quantilizers](https://intelligence.org/files/QuantilizersSaferAlternative.pdf) and [Impact regularization](https://www.lesswrong.com/w/impact-regularization). Analogous to how [structural risk minimization](https://en.wikipedia.org/wiki/Structural_risk_minimization) uses a regularizer to balance overfitting and underfitting, minimizing the test error, Quantilizers can sometimes [be viewed](https://www.lesswrong.com/posts/9fL22eBJMtyCLvL7j/soft-optimization-makes-the-value-target-bigger) as maximizing the _actual_ expected utility, accounting for errors in the provided utility function.
[^note-2]: Typically, something like
    $$
    L(\theta, D) = \frac{1}{|D|}\sum_i l(\theta,D_i)
    $$
[^note-3]: As in [quantilizing](https://intelligence.org/files/QuantilizersSaferAlternative.pdf).
[^note-4]: E.g. in playing any adversarial game, an agent needs to predict its opponent’s moves. Current game-playing AIs do this all the time, as do humans. This is done without any galaxy-brained stuff involving the simulated agent gaining awareness of its situation. Perhaps this kind of simulation isn’t trivial to implement in more powerful agents, but I don’t expect it to be a major hurdle.
[^note-5]: In particular, [world model stability](https://arbital.greaterwrong.com/p/ontology_identification?l=5c) is ignored.
