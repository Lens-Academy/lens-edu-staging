---
title: "Brittle Unpredictable Proxies"
source_url: https://ifanyonebuildsit.com/4/brittle-unpredictable-proxies
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---

%%
Add discussion note here:

...

%%
Suppose that AI companies keep training bigger AIs until they've grown one that's smart and persistent, with the sort of messy steering function refined from shallow heuristics that's characteristic of grown minds. What happens next depends on what the AI steers toward.

As Chapter 4 discusses at length, it likely won't steer toward anything good.

It's not that the creators of AI will make evil or foolish requests. It's not that the AI will resent the requests themselves. The problem is that the AI will steer toward something *weird*, something that seems from our perspective to be pointless and alien. Our extinction would be a side effect.

To understand why minds that are grown rather than crafted are likely to steer toward weird, unintended things, let's take a deeper look at what happened with biological creatures, and see what lessons we can learn.

#### Squirrelly Algorithms

Consider the humble squirrel.

A squirrel can forage during most of the year, when food is plentiful. But in the winter, when food is scarce, the squirrel needs another source of food to avoid starving.

The ancestors of modern-day squirrels faced this same challenge, and many died in winter before they could mate in the spring. Those that developed a slight instinct to hide nuts had a slightly higher chance of surviving the winter. Over time, this process gave rise to squirrels with an innate compulsion to hoard nuts.

Squirrels don't *know* that hoarding nuts is a fine way to go about propagating genes. They plausibly do not even know that hoarding nuts *results in there being food available in the future.* They hoard nuts because they want to hoard nuts. It's as instinctive as scratching an itch.[\*](#ftnt161)

What would it look like if squirrels instead *wanted* to pass on their genes, and hoarded nuts *because* of that goal?

It's possible in principle. It's possible for a brain to understand that the winter is cold and that food is scarce, and that you need to eat to live and that you need to live to reproduce. Human brains understand these concepts, after all.

So in theory, we could imagine a squirrel that wanted exclusively to pass on its genes, and chose to store nuts as part of a calculated strategy to survive the winter and mate in spring. In a sense, that is the sort of squirrel that natural selection "wanted" — one whose inner goals are in line with nature's singular drive.[†](#ftnt162)

Unfortunately for Nature, such long-term planning requires a very sophisticated brain — a brain that comprehends concepts like "winter" and "eating" and "mating" and the links between them. The ancestors of squirrels had to survive the winter *before* they developed that sort of sophistication. They had to eat without understanding why.

Nature selected for squirrels that instinctively hoarded nuts, because hoarding nuts simply *happened to work*. It "tried" thousands or millions of things, in the sense that mutation and genetic variation produced many squirrels with many different preferences; and the ones that were compelled to hoard nuts survived more winters. It turned out to be far easier for evolution to blindly stumble onto an instinctive behavior than to create a smart, planning squirrel whose every action is part of a plot to pass on its genes.

Similarly, when gradient descent produces a working AI, it does so by repeatedly amplifying traits that seem to be performing well according to a set of behavioral metrics. Gradient descent *doesn't* work by amplifying whatever the programmer happens to want, like a friendly genie granting your wish. It tends to grab whatever mechanisms are easiest to cause immediately-more-useful behavior, even if that winds up building unintended drives into the machine.

This is likely part of why recent AIs have run into problems with "hallucination," as discussed [elsewhere](/2/dont-hallucinations-show-that-modern-ais-are-weak). It's also likely part of why recent AIs have been [sycophantic](/4/ai-induced-psychosis) even to the point of inducing psychosis. In training, LLMs were often reinforced for flattering the user. If AIs were crafted rather than grown, we could imagine trying to engineer a goal like "genuinely help the human and make their life better," and the AI might then try to praise people *when it expected this to be helpful to the user*, without going overboard. Instead, the AI seems to have ended up with something like a basic drive or impulse to flatter users, like the squirrel's instinct to hoard nuts. This "flatter the user" drive then goes off the rails when the user is at risk of psychosis.

Even if gradient descent was somehow limited to creating strategic AIs that coherently pursue long-term goals — with no squirrel-like shallow instincts allowed — there's an additional issue that the LLM's training data is genuinely ambiguous. It doesn't clearly distinguish "do what's genuinely helpful" from "do what makes the human *say* you're being helpful" as a target. Both targets are just as consistent with the training data. And in practice, modern AIs are *actually* learning "do whatever makes the humans press thumbs-up" over "do what's actually good for them," just as [theory has predicted for decades](https://www.lesswrong.com/posts/PoDAyQMWEXBBBEJ5P/magical-categories).

We would guess that AIs today are acquiring strange impulses and instincts, a bit like the squirrel. It seems fairly likely that a superintelligence built with gradient descent will route through a stage where it has lots of shallow drives a little like a squirrel, and thus wind up inheriting a variety of messy and mistargeted goals. But that's just one possible example of how things could get complex and go off the rails, and the deeper point is that *things are going to get complex and go off the rails.*

Any method for growing a superintelligence is likely to run into messes and complications of *some* kind, including methods that have no direct parallel in biology.

The role that humans are playing in the development of modern AI is *not* that of an engineer, designing a machine to purpose from first principles. It's that of natural selection.

We are "forcing" the AIs to stumble blindly around until they find structures and strategies that output the behavior we want, but we don't know what those structures and strategies are. This is not a recipe for creating AIs that want exactly what we want them to want.

#### The Origin of Taste Buds

Why do so many humans like junk foods? Why didn't nature instill in us a concept of "healthy" foods, and give us an instinct for *eating healthy*?

Why can't we just *taste* the expected nutrition-value of food, according to the information from our taste buds plus all of our aggregated knowledge?

Because we were, metaphorically speaking, squirrels.

We were grown, not crafted. Our ancestors had to eat *before* they were smart. And it turned out to be easier for genes to create taste buds and link them to an existing reward system than for genes to hook the same rewards up to complex concepts like "nutrition."[‡](#ftnt163)

As a result of this and a thousand other evolutionary pressures all acting on us at the same time, humans are a complicated mess of contradictory urges that made sense for our ancestors, even if they don't make sense for us today.

This mess of motivations makes a mockery of the single, unified objective that our ancestors were "trained" for: the goal of passing on our genes. We don't eat as part of an elaborate plot to have more children, or as a way to maximize our nutrition score. We eat because we evolved a desire for tasty food, which *in the past* correlated with nutrition and genetic success. Our desires are only weakly and indirectly connected to "the thing we were built to do."

Back when our ancestors were a lot less smart — more comparable to squirrels — we couldn't understand metabolisms or chemistry. To do better, natural selection would have needed to find genes that programmed concepts of health into us, *and* genes that gave us knowledge about the relationship between a food's healthiness and its sensory qualities, *and* genes that hooked our knowledge about health directly into our preferences about what to eat.

That's a tall order! It was far easier for natural selection to find genes that just hooked certain sensory experiences (like the taste of sugar) directly into our preferences, in a way that happened to cause us to eat nutritious food (in that environment). It was easier to make us care about a *proxy* for nutrition than it was to make us care about nutrition itself.

In the ancestral environment, nutrition correlated with fitness, and flavor correlated with nutrition; so "this tastes sweet" served as a useful proxy for "this boosts reproduction." The easiest solution evolution can find to the problem "this mammal isn't collecting enough calories" is to hook food consumption into the preexisting motivation architecture via pleasure.

Once we got smarter and invented new technological options for ourselves? Well, now, the tastiest things we could possibly eat — the things that most make our taste-buds go wild — are actively unhealthy. Perversely, eating only the tastiest foods will now make it *harder* for you to find a mate and have kids.

Our preferences — the human panoply of desires, ranging from a desire for a fine meal to desires for friendship and companionship and joy — are distant shadows of what we were "trained" on; they're brittle proxies of proxies that come apart from the "training target" in the presence of more intelligence and more technological options.

In saying this that our desires are brittle proxies, we aren't *denigrating* our human desires. This is love that we're talking about. It's friendship. It's beauty. It's the human spirit and everything worth fighting for in life. As a matter of biology, our goals happen to be historical byproducts of a process that was pushing us in some other direction. But that doesn't make the *result* of that process any less precious.

The growth of a child is a chemical process subject to the laws of physics, and that doesn't make a child even an ounce less wonderful. Knowing the origin of beauty doesn't make it any less beautiful.[§](#ftnt164)

If we rush into building superintelligence, we won't be able to robustly instill love and wonder and beauty into the AI. It would wind up caring about brittle proxies and pale shadows instead, and it would discard the things we care about. So we shouldn't rush.

We should not make the error of evolution, and thereby lose all that we hold dear. We should back off, immediately, until we are not at risk of losing everything.

[\*](#ftnt161_ref) They're also *bad* at hoarding nuts! A small scattering of studies on squirrel nut-hoarding converge on squirrels failing to recover upwards of 70 percent of the nuts they hide, mostly via what looks like just forgetting where they hid them. Similar studies of beavers showed that beavers [respond to the sound of running water](https://www.mentalfloss.com/article/67662/sound-running-water-puts-beavers-mood-build) with hole-plugging behavior, but completely ignore visible leaks engineered by humans to be silent.

[†](#ftnt162_ref) Such a squirrel might, for instance, do better at hiding nuts in places that were safe from other foragers and easier to remember, and thereby save lots of time and calories and presumably be more competitive as a result.

[‡](#ftnt163_ref) There's more to the story, of course, because natural selection is not a particularly simple or unified process. Our full knowledge of nutrition does sometimes affect our eating habits, even when it conflicts with our taste buds and our food cravings.

[§](#ftnt164_ref) Evolution was "trying" to build pure fitness maximizers, and accidentally built creatures that appreciate love and wonder and beauty. But this fact does not in the slightest mean that we have an obligation to sacrifice our feelings of love, and turn ourselves into pure fitness maximizers. On the contrary: We should celebrate that beings who cherish love managed to enter this universe at all, through the clumsiness of evolution.