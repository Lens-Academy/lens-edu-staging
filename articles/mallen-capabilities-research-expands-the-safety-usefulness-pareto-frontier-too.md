---
title: "Capabilities research expands the safety-usefulness Pareto frontier too"
author:
  - "Alex Mallen"
source_url: "https://blog.redwoodresearch.org/p/capabilities-research-expands-the"
published: 2026-10-02
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "A model of why capabilities research usually increases risk despite enabling safety—and when it can reduce risk"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

### A model of when and why research improves or hurts safety ^a-model-of-when

It’s tempting to define safety research as research that enables developers to deploy an AI system more safely without making the deployment much more expensive or much less useful.

You can visualize this definition of safety research as pushing out the [safety-usefulness Pareto frontier](https://blog.redwoodresearch.org/p/efficient-tradeoffs-and-the-safety).

At any given level of usefulness, there’s greater safety available.

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img1-0e0719b3.webp)

](https://substackcdn.com/image/fetch/$s_!xkV4!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F80a40d7a-6cf5-4865-b328-34fe8e3e761e_1752x1228.png)

Awkwardly, this definition counts basically all capabilities research as safety research. For example, consider performance optimization for inference. By making inference more efficient you can use weaker, safer models more extensively than you would otherwise be able to, pushing out the Pareto frontier. Likewise, any successful research whatsoever pushes out this Pareto frontier because research can only ever create more options.

It seems like something has gone wrong with our definition of safety research if it includes seemingly all capabilities research.

Here, I spell out one reason why enabling improved safety without hurting usefulness is an insufficient standard for safety research. The core observation is that developers have to _choose a particular point_ on the Pareto frontier, and some technological improvements incentivize them to sacrifice safety. Safety research typically reshapes the Pareto frontier in a way that causes developers to choose greater safety, while capabilities research typically does the opposite.

However, I also argue there is an important and plausible future regime involving much higher political will than we have right now, in which certain kinds of capabilities research would be an effective way to improve safety. I don’t write this post to argue that more people should be doing capabilities research, and in fact I think that currently capabilities research at any frontier AI company is probably bad. Instead, I’m treating this as an interesting puzzle to sharpen our models of when and why safety and capabilities research are good.

(Another bucket of safety interventions includes those that cause AI developers to be more willing to give up usefulness for safety. While they’re crucially important, especially right now, I don’t focus on those in this post.)

_Thanks to Buck Shlegeris, Collin Burns, Ryan Greenblatt, Alexa Pan, Bronson Schoen, Thomas Larsen, Oak Hu, Tyler Tracy, Alec Harris, Dylan Xu, Evie Hu, Jackson Sipple, and Jo Jiao for feedback on drafts. Thanks especially to Collin Burns for conversations inspiring some of this thinking._

## How does research affect the Pareto frontier? ^how-does-research-affect

By research, I just mean any work that makes it possible for AI developers to choose new combinations of safety and usefulness when developing and deploying their next model [^note-1] [^note-2]. A tempting gloss is that all research is the same because all research enables greater safety at a given level of usefulness. But this is misleading.

We have to actually look at the shape of the Pareto frontier expansion to predict the effects on safety, because ultimately developers are going to choose a particular point on the Pareto frontier, depending on its shape. So, what do capabilities and safety research actually do to the Pareto frontier?

A somewhat more accurate model is that safety research typically creates new options for safety without creating substantial new options for usefulness (pushing the frontier _right_), while capabilities research creates new options for usefulness at the expense of safety without creating substantial new options for safety (pushing the frontier _up_ and _left_).

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img2-e4a7cb09.webp)

](https://substackcdn.com/image/fetch/$s_!bgRf!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2d15a7c9-5040-4f8b-8640-2a2f61e6769b_1516x1050.png)

Some basic notes about this graph:

-   Safety is defined as the probability that the model doesn’t take over. I think this is a good definition once AIs start to pose direct takeover risk, but you might want to consider smaller loss-of-control outcomes like rogue internal deployments to quantify the immediate safety of near-term systems (which is correspondingly less important).
    
-   You can always attain a safety of 1 by not producing or deploying models at all.
    
-   The red arrow is not vertical. Models become more likely to take over in substantial part as a result of capabilities. So, when you increase the capabilities of your model, you’re typically moving up _and_ to the left on this graph.
    
    -   Safety research typically isn’t pure safety either, but the effects on usefulness are more varied (e.g., fixing reward-hacking often improves usefulness, but most methods of improving monitorability degrade usefulness).
        
-   Developers do not have to be altruistic to care about safety. They don’t want to be taken over by the AIs either.
    
-   Developers are irrational in a bunch of ways, and don’t have perfect information, etc (see Appendix B).
    

Given this graph, we can now see why safety tech improvements usually lead to improved safety, while capabilities tech improvements do the opposite.

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img3-acf1d3b7.webp)

](https://substackcdn.com/image/fetch/$s_!FySy!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe70dbfad-f4eb-4cb0-a2a7-399ac09b64ba_1216x864.png)

**Expanding the safety-usefulness Pareto frontier can reduce the amount of safety that developers choose, by increasing their temptation to increase usefulness**. Indeed, this is the grand trend: risk of AI takeover from AI deployments was historically 0, and in the future it will be greater than 0 because dangerous AI is useful. The particular point on the Pareto frontier that developers choose to go to depends on the developers’ joint utility function over usefulness and safety. This problem is worse for capabilities research than safety research, though in principle it can happen with both (e.g., developing neuralese monitors might tempt rational developers to use neuralese).

Safety tech improvements will usually lead rational developers to choose higher safety than capabilities tech improvements, because safety tech improvements make the usefulness cost of safety relatively smaller. Visually: near the initial pink point, the green slope is shallower than the red slope.

Any particular intervention is going to have a somewhat different-looking effect on the shape of the Pareto frontier, but I think that the two above curves capture the first-order difference between safety research and capabilities research. Let’s look at some more detailed examples of capabilities research.

## RLVR research that mainly enables improved usefulness, at the expense of safety ^rlvr-research-that-mainly

The main effect of a lot of capabilities research is enabling developers to make AI much more useful and much more dangerous than was previously possible. Consider building a bunch of RLVR environments, many of which are hackable. This makes it easier for developers to train a more useful model next time around, but it barely makes it easier for developers to train a safer model. The Pareto frontier expansion might look something like this:

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img4-63c790f2.webp)

](https://substackcdn.com/image/fetch/$s_!2vp5!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F65e8fa56-e893-47e5-95f2-c159df0e9dba_1706x1226.png)

You’ll notice that the lines don’t extend all the way to the left. That’s because these hypothetical developers simply don’t have the technology to produce a model capable of reliably taking over the world (as is true today). The main effect of the RLVR research was to enable developers to train more capable and dangerous models than they were able to before.

Building more RLVR environments also enables developers to _slightly_ improve safety for a fixed usefulness. For example, since developers now have a larger pool of RLVR environments to choose from, they can afford to filter out hackable environments more aggressively, without scaling down RL. The resulting model is then trained on higher-quality environments and is therefore somewhat safer.

Of course, that’s not what current frontier developers would do. They would choose to train a more capable and dangerous model using most of those new environments.

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img5-d030c7a4.webp)

](https://substackcdn.com/image/fetch/$s_!GOxC!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fed28999b-3277-4db1-856a-f809497b289a_1688x1230.png)

If you think all capabilities research looks like this (though I am skeptical), you will think that capabilities research would never be an effective method of improving safety.

## Inference research that enables somewhat substantial safety improvements ^inference-research-that-enables

While building RLVR environments barely creates new options for improving safety, some other capabilities research enables more substantial safety gains.

A simple example is speeding up inference throughput (h/t Buck). At a given level of usefulness, it’s probably safer to use a weaker model with more inference-time compute, since we’re more worried about more capable models being competently and egregiously misaligned. While inference-time compute is also dangerous, I’d rather do AI research using 100 parallel instances [^note-3] of a model I can probably control and whose alignment I’m more confident in, than 1 instance of an equivalently useful model that doesn’t have those properties.

[

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too-img6-ad8f0d3c.webp)

](https://substackcdn.com/image/fetch/$s_!EB-d!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F02b772d0-f0e4-42eb-ad23-49841962f299_1504x1084.png)

(Inference speedups can also improve safety via enabling stronger control protocols. Consider a control protocol which resamples suspicious actions. The safety of this protocol depends on how many actions you resample per trajectory. Increasing inference throughput allows you to resample more actions per trajectory at a fixed usefulness, improving safety.)

As another example, pretraining and other “predictive” training tasks might be substantially less dangerous than outcome-based RL. At a given final capability [^note-4], [stronger pretrains with less RL reward-hack less](https://x.com/alextmallen/status/2082141491821191553). [It also seems like](https://alignment.anthropic.com/2026/reward-seeker/) current models are substantially more misaligned as a result of flawed RL incentives. Though you might also worry that stronger pretrains are more likely to be unmonitorable or harder to robustly oversee in training. (If you could demonstrate that instead RLVR was safer than pretraining, you could scale up RLVR relative to pretraining instead.)

To be clear, as I discussed before, merely enabling greater safety at a given level of usefulness does not imply that developers will choose greater safety, and in fact, the opposite is usually true. Both of the above examples also enable the developer to _reduce_ safety in order to gain more usefulness.

## A plausible case in which capabilities research would be an effective safety intervention ^a-plausible-case-in

As I’ve discussed, developers need to choose a particular point on the frontier based on what trade-offs they’re willing to make between safety and usefulness. _If_ a developer didn’t care at all about increasing usefulness above a threshold that they have already achieved, then, in theory, no technological improvements could incentivize them to reduce their safety–there’s nothing to gain from reducing safety. (Alternatively, a developer might be robustly committed to not making safety any worse for whatever reason.)

In such a situation, capabilities research would theoretically result in improved safety. For example, in response to pretraining technology improvements, such a developer would do less RLVR training (probably improving safety) while holding capabilities fixed, to whatever extent is enabled by their pretraining technology.

Now, I think it’s implausible that we’ll end up in a situation where developers literally don’t care at all about increasing usefulness above what they already have, or where the developer is robustly committed to never sacrificing safety. But I think that it’s highly plausible that we’ll end up in situations similar enough to this that capabilities research might make sense for this reason. Notably, **the key properties of this situation are concentrated in worlds where things go well, since they’re quite related to political will**. So, to the extent that we’re planning for AI to go well, this dynamic is important to keep in mind.

For example, a common plan is for the leading AI project to “burn their lead” on AI safety once they’ve fully automated AI research. If an AI project actually has a substantial lead they’re willing to burn, this radically changes their decision-making calculus on the safety-usefulness Pareto frontier. They might be willing to massively sacrifice usefulness in order to improve safety, since the calendar time cost would probably be small. Certain kinds of capabilities research might be a big part of the best risk-reducing research portfolio once AIs have just started automating AI research, especially to the extent that capabilities research is more easily automatable than safety research.

A similar dynamic applies in certain worlds where AI projects have robustly coordinated internationally to not exceed certain capability thresholds, though not when the slowdown is achieved by limiting inputs to AI development, which leads to continued race dynamics. (One probable implication is that achieving slowdowns via mandating a large fraction of compute goes to transparent safety research has big costs to safety.)

Just to be clear again, I think the above argument does not go through right now because developers are still in a tight race, no frontier developer has robustly committed to slowing down when the situation gets too risky, and the downsides of bringing the automation of AI research sooner now are large. I discuss downsides of this proposal in Appendix A and more general inaccuracies of this model in Appendix B.

## Conclusion ^conclusion

The issue with the definition at the start of this post—AI safety research is research that enables developers to improve safety without significantly hurting usefulness—is subtle. Just because research can be used to improve safety, doesn’t mean it will. You need to pay attention to how research shapes the incentives of the developers. AI safety research should actually enable improved safety without much sacrifice from the developers _after taking into account all new options created on the Pareto frontier_. Some research, including capabilities research in most cases, creates an incentive for developers to reduce safety to gain more usefulness.

However, I’ve argued that if this incentive is absent (e.g., because the developer has already fully automated AI R&D and is properly committed to burn their lead), then certain kinds of safer capabilities research can be an effective way to improve safety. The fact that safety research and capabilities research can blend together in this way is also fairly natural. A classic analogy: when designing an airplane, there’s no strong separation between R&D to make airplanes that fly and R&D to make airplanes that don’t crash. Figuring out how to make an airplane that doesn’t crash might involve pushing on alternative ways of making an airplane that flies.

---

:::callout {title="Appendix" collapse="closed"}
## Appendix A: Reasons why capabilities research might be bad when “burning the lead” ^appendix-a-reasons-why

I proposed that it might be a good idea to do capabilities research to improve safety when “burning the lead”. I expect many people to react that this is heuristically a bad idea. This reaction is worth paying attention to. I expect a bunch of skepticism will come from not buying that AI developers will actually pay for increased safety rather than fooming close to as fast as possible. I am also skeptical about this. But if we focus on good futures, AI projects are moderately likely to intentionally hold back. Ideally, we’d robustly implement the mechanisms for incentivizing capabilities restraint _before_ trying to advance capabilities research on this basis.

I expect some readers will also just be skeptical that there are any good agendas for increasing capabilities subject to safety constraints because there is fundamentally almost no way to create safe and capable AIs. This is related to a sort of “optimization equivalence” view, in which usefulness just _is_ optimization, and all optimization for a given end state will have the same Goodharting problems. I think this view is largely incorrect, and that some capabilities agendas are substantially safer than others (as discussed above).

A final objection is that capabilities research during RSI creates destabilizing capabilities overhangs. If the world later ends up back in a race, e.g., because a blacksite steals the algorithmic progress, it was possibly quite bad that the developers did this capabilities research. They’ve developed a bunch of technology that _could_ be combined to create a more dangerous AI very suddenly. The severity of concern depends on how much capabilities research was involved in making RSI-capable models that are much safer, which I think people will disagree on a substantial amount. My guess is that this is a small-to-moderate concern because not that much capabilities research will be required, and progress would have been pretty sudden in most late-game equilibrium disruptions anyways.

## Appendix B: Further notes about ways in which this model is wrong ^appendix-b-further-notes

Here is an incomplete list of considerations missing from my model:

-   Developers aren’t rational, don’t have perfect information.
    
    -   A key concern here is that measurements of safety are extremely hard, and it’s very easy to end up in worlds where safety looks good when it’s actually bad. Usefulness is comparatively easy to measure, and unfortunately negatively tied to safety (in fact capabilities is probably our single best predictor of danger). This could lead to a situation where a developer that was trying to maintain safety while improving capabilities was unknowingly dragging safety down by scaling up capabilities.
        
-   Developers have other motivations.
    
    -   Altruism re: not killing everyone
        
    -   Altruism re: quickly curing diseases etc
        
    -   The joy of building cool things
        
    -   Fear of losing their job if they’re first to highlight safety issues
        
    -   Intra-developer political dynamics
        
    -   Not looking evil
        
    -   …
        
-   The “safety” axis only tracks safety from the immediate AI system, not overall risk. This model doesn’t capture any of the ways in which developer choices affect the domestic and international political situation, which is currently extremely important. Currently, I think slowing down unilaterally makes a coordinated slowdown more likely.
    
-   Research builds on other research, in ways that aren’t modeled by changing the shape of the Pareto frontier. For example, interpretability research could lead to future research progress on capabilities.
    
:::

[^note-1]: Note that this is a distinct definition from Pareto improvements. As we’ll see, it’s common for AI capabilities research to enable previously unattainable usefulness, at the cost of decreasing safety (often to previously unattainable lows).
[^note-2]: There’s some modeling choice we have to make here about which options are on the current Pareto frontier versus require expanding the Pareto frontier, and it’s pretty subtle. For example, inference speedups make it so that developers can train their model with larger quantities of RL for cheaper. It would potentially require some entrepreneurship / further technological development to implement these speedups in the context of their RL pipeline, build up other necessary complementary capacity, and then figure out how to make use of it, which is why there’s some ambiguity about how to model it.
[^note-3]: Note this doesn’t require 100xing inference throughput, since the weaker model is already probably smaller.
[^note-4]: Whether you measure capability in terms of gold reward or proxy reward the answer is the same.
