---
title: "Deep Differences Between AIs and Evolved Species"
source_url: https://ifanyonebuildsit.com/4/deep-differences-between-ais-and-evolved-species
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090727026}@@

%%
Add discussion note here:

...

%%++}
#### Comparing Natural Selection and Gradient Descent

As we discussed in "[Human Values Are Contingent](/4/human-values-are-contingent)," the evolution of love and friendship in humans crucially depended on features of natural selection that were present for *Homo sapiens* in particular, and that are absent in gradient descent.

The most obvious issue is the dataset. Current AIs are trained to solve synthetic challenges and to imitate human-generated text; they aren't facing cooperative-competitive challenges in hunter-gatherer contexts where they must mate with other individuals of their species to propagate their genes.

On hearing this, some people's next thought is to run out and try to create synthetic tribal training environments, in the hope of engineering something more similar to humanity's ancestral environment.

But you would almost certainly not get the same results if you ran evolution twice over, starting from around the jellyfish level — to say nothing of what happens if you entirely change the optimizer from natural selection to gradient descent and forgo genes entirely. We can guess at some of the factors that caused humans to evolve the values we have. That doesn't mean that we have an algorithm for reproducing the same results a second time.

Even if you started from primates, rather than alien actresses trained to predict human text (i.e., modern AIs), we should expect there to be one or more vital causal factors that biologists haven't figured out yet — at least one thing we're missing, where the papers will say something different in twenty years than they do today (if we're all still alive then). Evolutionary biologists are at the stage of exploring various guesses about how these features evolved, not at the stage of nailing down a complete theory — much less a precise, deterministic theory.

And even beyond the superficial differences in training environments, we suspect that this is a case where it becomes important that natural selection optimizes a genome and gradient descent optimizes every parameter in the AI's mind directly.

Natural selection has to use a small, compressed genome to produce an entire sprawling brain. It has to force its information through a narrow bottleneck. *Looking* friendly was an important trait for survival and success in our ancestors' days. Genes that construct *genuine friends* are a simple hack for making organisms that look like good friends to other members of their species — and natural selection favors simple solutions much more sharply than does gradient descent.

Natural selection sometimes builds agents that genuinely care about being honest (albeit not always). It builds agents like that because it can't encode complete guides to lying, and we had to start looking honest in a lot of situations before we were smart enough to figure out when lying was safe, before we had the option of being honest only when the payoff is worth it. That's in part because natural selection had to make do with only a handful of genes.

But gradient descent can encode massive numbers of conversational patterns. There's still *some* bias toward simpler, easier-to-converge-upon solutions, but gradient descent casts a far, far wider net.

Or, more generally: Honesty and friendship are cases where we aren't happy with just *any* equilibrium between agents that gradient descent could find. There are other solutions to the problems that friendship and a [terminal](/4/terminal-goals-and-instrumental-goals) care for honesty were solving in humans. Even if the training environment of AIs was exactly like that of humans, if they were being shaped by gradient descent rather than natural selection, we shouldn't expect the same results.

Even most evolved organisms are not like humans in this regard! So it seems pretty predictable that gradient descent won't find the same solutions as evolution, much less the same solutions as evolution *operating on particular populations of early primates*.

Optimization is not a magic ritual where you throw in a few key ingredients that have sympathetic relationships to an archetype and get that whole archetype right back out. Trying to grow AI agents inside hunter-gatherer environments will not spit out recognizable humans as a result.

Someone can of course fine-tune an LLM to predict what humans will say about how terrible it is to betray a friend. This is not remotely like the problem that natural selection optimized genes to solve, in the course of producing at least some people who would not betray their friends. Rather, the LLM's "experience" is more like being shut up inside a box, told to predict a conversation between two extremely alien creatures that are less similar to it than they are to a jellyfish, and being given trillions of examples of alien conversation and trillions of hours to figure it out.

Being able to solve this problem does require some form of intelligence. But you don't have to become drunkto predict the sorts of things alien creatures ("humans") will say when intoxicated.[\*](#ftnt155) You don't have to become truly friendly to understand friendliness or to predict and imitate the behavior of friendly creatures.

#### Circa-2024 LLMs and AI "Shallowness"

In the [resources for Chapter 1](/1/the-shallowness-of-current-ais), we noted that AI today still seems to be in some sense shallower than humans. The comparison to natural selection provides one possible account for why that might be.

Gradient descent has much in common with natural selection, because they're both optimizers that blindly adjust inner parameters to produce a required outward behavior. But gradient descent and evolution are in some ways importantly different; and the most important way (that we know about) is that gradient descent has a much wider *information bottleneck* on the quantity of patterns it can learn.

Natural selection, operating on hominids, could only learn a handful of information-theoretic bits per generation. Natural selection had to fit everything it learned into 3 billion DNA bases, or around 750 megabytes — a lot of which is repetitive [junk DNA](https://en.wikipedia.org/wiki/Junk_DNA). There are mathematical bounds on how much natural selection can learn in a single generation. Each individual feature that natural selection built into hominid brains had to be encoded into a handful of genes that would bias the formation of later neural circuits.

Gradient descent is very different. Every time gradient descent sees a new batch of tokens, it calculates the gradient of each of billions or trillions of parameters with respect to that batch of tokens — it calculates how much better or worse the whole AI's predictions would have been, if *each* parameter had been a little bit different. In practice, not just in principle, gradient descent can learn *much* more information from a thousand token-batches than natural selection encodes into genes over a thousand generations.[†](#ftnt157)

We can combine this observation with another key fact about (2024's publicly known) LLM architectures: Their per-token *computational depth* is bounded.

[Llama 3.1 405B](/2/a-full-description-of-an-llm) has 126 layers. Each of those layers involves computing something like four serial operations.[‡](#ftnt158)

Each time Llama looks over what has already been said and computes a new output token, that computation involves at most ~500 *serial* steps — though there are billions of parallel operations obeying that serial bound. To do longer *serial* computations than 500 cognitive steps, Llama needs to output tokens that are the product of previous reasoning, and then do new operations depending on those.[§](#ftnt159)

So our wild guess would be that — in a way unlike anything in biology — Llama 3.1 405B is an enormous collection of*relatively shallow memorized policy-patterns*,but with a lot of optimized overlap, interaction, and coherence between those policy-patterns (plus some genuinely deeper cognitive structures that are still of limited computational depth).

This fact provides one possible explanation for current LLMs' apparent shallowness. (We acknowledge that it's a lot harder to say that the LLMs of 2025 are "shallow" compared to the LLMs of 2023 and 2024.)

*Usually*, it isn't valid to think of AIs as brain-damaged humans.[¶](#ftnt160) But a few narrower analogies like that are perhaps helpful here. For example, 2024 LLMs *specifically* are like people with [anterograde amnesia](https://en.wikipedia.org/wiki/Anterograde_amnesia)*:* They remember events up to their training cutoff date, but not what you said to them yesterday.

In the same way, it might be useful to imagine 2024 LLMs — not all possible future AIs in general — as entities that *remember* many past humanlike experiences, but that have brain damage preventing them from engaging in novel thinking that is as *deep* as the deepest thoughts they can remember.

It felt a lot more obvious with the earlier LLMs, GPT-3 or GPT-3.5. We wouldn't blame someone who's only ever used the latest LLMs if they read this in 2025 or after and wonder whether we're making this up in a desperate attempt to cling to a human sense of superiority. Many have erred in that way before.

But that's still the organizing theory — or rather, the wild guess — that your authors are using to make sense of LLMs as of 2024. These models are missing a kind of depth; and they're making up for that handicap by remembering *a vast variety of patterns.* Not just facts, but skill-patterns, speech-patterns, and policy-patterns.

The patterns gradient-imbued into the best public 2024-LLMs are not *that* shallow, or so we'd guess. They're not on the exceptionally humble level of a *Sphex* wasp, to use an example [we described](/3/the-road-to-wanting) in the Chapter 3 online resources; perhaps they're more like the patterns a beaver mind can track and process.

An LLM's learned cognitions can go through 500 serial steps, even before taking into account their ability to think out loud and hear their own thoughts. 2024-LLMs have some ability to imagine, predict, and plan, like the (actually quite impressive) cognition of a beaver building a dam. But to our eye, LLMs still don't quite appear to be on the level of a human, in at least some important respects.

What's true of AI now, however, is not necessarily what will be true of AI a year or a month from now. These speculations are interesting, but as we put the finishing touches on this section in August 2025, the AIs of today appear to us to be somewhat less shallow than the AIs of 2024; and these in turn seemed less shallow and less narrow than the AIs of 2023.

Maybe the gap will be slowly closed by steady iteration on base LLMs; or maybe the gap will be closed by finding better training methods to use on the long chains of "reasoning" in modern reasoning models like o1 (described in Chapter 3) or its successor o3; or maybe some brand new architectural insight will come in and bridge the gap overnight. That part of the future is not an easy call.

But sooner or later, if the international community does nothing, the gap *will* close. The world is running low on time to act.

[\*](#ftnt155_ref) For more on this idea, see our answer to "[Won't LLMs be like the humans in the data they're trained on?](/2/wont-llms-be-like-the-humans-in-the-data-theyre-trained-on)"

[†](#ftnt157_ref) On the other hand: Natural selection can in some cases learn deeper, more powerful tricks. Natural selection is considering whole alternate ways that genes can construct organisms. Gradient descent is tweaking parameters fleshing out a fixed skeleton of neural network operations.

[‡](#ftnt158_ref) Query-key-value activation vectors, followed by attention, followed by a two-step feed-forward network.

[§](#ftnt159_ref) Possibly the proprietary architectures are different. Researchers are always publishing new proposals for breaking the serial-operation bounds. But none of the published methods had caught on in open source as of December 2024. (Though, of course, the "reasoning models" that came out in late 2024 *do* produce a lot more serial reasoning by looking at their previous tokens. So this is not a limitation to what AIs can do after the pre-training phase, but it *is* a limitation during pretraining.)

[¶](#ftnt160_ref) In fact, we caution against generic biological analogies more broadly. In early 2023, it might have been tempting to proclaim that really LLMs were still at the small-mammal stage in the Great Chain of Being — or the lizard stage, nay, the insect stage — but that this was disguised by LLMs being specialized on English conversations in particular, the same way that bees are specialized on constructing beehives in particular. We think that, even in early 2023, this analogy would have been a stretch at best. Not because transistors are so different from biochemicals, but because gradient descent *is* that different from natural selection, as we've been discussing. Specific and narrow analogies can sometimes be useful for building intuition, but we recommend using them with care.

#### Notes

[1] *not like humans:* [Lions](https://africageographic.com/stories/understanding-lion-infanticide/), for instance, routinely kill others' cubs so they can have more cubs themselves. Many other animals, including mammals and some primates, do the same.

[2] *mathematical bounds:* Bounds on the complexity of organisms are discussed in [Adaptation and Natural Selection](https://brandvainlab.wordpress.com/wp-content/uploads/2014/11/williams-1966.pdf) (Williams 1966).