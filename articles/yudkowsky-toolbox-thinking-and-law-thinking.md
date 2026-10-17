---
title: "Toolbox-thinking and Law-thinking"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/s/6xgy8XYEisLk3tCjH/p/CPP2uLcaywEokFKQG"
published: 2018-05-31
created: 2026-10-17
accessed: 2026-10-17
llm-review:
  date: 2026-10-17
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-17
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Tl;dr:

I've noticed a dichotomy between "thinking in toolboxes" and "thinking in laws".

The toolbox style of thinking says it's important to have a big bag of tools that you can adapt to context and circumstance; people who think very toolboxly tend to suspect that anyone who goes talking of a single optimal way is just ignorant of the uses of the other tools.

The lawful style of thinking, done correctly, distinguishes between descriptive truths, normative ideals, and prescriptive ideals. It may talk about certain paths being optimal, even if there's no executable-in-practice algorithm that yields the optimal path. It considers truths that are not tools.

Within nearly-Euclidean mazes, the triangle inequality - that the path AC is never spatially longer than the path ABC - is always true but only sometimes useful. The triangle inequality has the prescriptive implication that _if_ you _know_ that one path choice will travel ABC and one path will travel AC, and _if_ the _only_ pragmatic path-merit you care about is going the minimum spatial distance (rather than say avoiding stairs because somebody in the party is in a wheelchair), then you should pick the route AC. But the triangle inequality goes on governing Euclidean mazes whether or not you know which path is which, and whether or not you need to avoid stairs.

Toolbox thinkers may be extremely suspicious of this claim of universal lawfulness if it is explained less than perfectly, because it sounds to them like "Throw away all the other tools in your toolbox! All you need to know is Euclidean geometry, and you can always find the shortest path through any maze, which in turn is always the best path."

If you think that's an unrealistic depiction of a misunderstanding that would never happen in reality, keep reading.

---

Here's a recent conversation from Twitter which I'd consider a nearly perfect illustration of the toolbox-vs.-laws dichotomy:

> [David Chapman](https://twitter.com/Meaningness/status/993602725316186112): "By _rationalism,_ I mean any claim that there is an ultimate criterion according to which thinking and acting could be judged to be correct or optimal... Under this definition, 'rationalism' must go beyond 'systematic methods are often useful, hooray!'... A rationalism claims there is _one weird trick_ to correct thinking, which guarantees an optimal result. (Some rationalisms specify the trick; others insist there must be one, but that it is not currently knowable.) A rationalism makes strongly normative judgments: everyone _ought_ to think that way."

> [Graham Rowe](https://twitter.com/grahamsrowe/status/993781462263574528): "Is it fair to say that rationalists see the world entirely through rationality while meta-rationalists look at rationality as one of many tools (that they can use fluently and appropriately) to be used in service of a broader purpose?"

> [David Chapman](https://twitter.com/Meaningness/status/993879794180747264): "More-or-less, I think! Although I don’t think rationalists _do_ see the world entirely through rationality, they just say they think they ought to."

> [Julia Galef](https://twitter.com/juliagalef/status/993621055221608449): "I don't think the 'one weird trick' description is accurate. It's more like: there's one correct normative model in theory, which cannot possibly be approximated by a single rule in practice, but we can look for collections of 'tricks' that seem like they bring us closer to the normative model. e.g., 'On the margin, taking more small risks is likely to increase your EV' is one example."

> [David Chapman](https://twitter.com/Meaningness/status/993626127842213889): "The element that I’d call clearly meta-rational is understanding that rationality is not one well-defined thing but a bag of tricks that are more-or-less applicable in different situations."

Julia then [quoted](https://twitter.com/juliagalef/status/993715985768177665) a paper mentioning "The best prescription for human reasoning is not necessarily to always use the normative model to govern one's thinking." To which Chapman [replied](https://twitter.com/Meaningness/status/993718942827921408):

> "Baron’s distinction between 'normative' and 'prescriptive' is one I haven’t seen before. That seems useful and maybe key. OTOH, if we’re looking for a disagreement crux, it might be whether a normative theory that can’t be achieved, even in principle, is a good thing."

I'm now going to badly stereotype this conversation in the form I feel like I've seen it many times previously, including e.g. in the discussion of p-values and frequentist statistics. On this stereotypical depiction, there is a dichotomy between the thinking of Msr. Toolbox and Msr. Lawful that goes like this:

Msr. Toolbox: "It's important to know how to use a broad variety of statistical tools and adapt them to context. The many ways of calculating p-values form one broad family of tools; any particular tool in the set has good uses and bad uses, depending on context and what exactly you do. [Using likelihood ratios](https://arbital.com/p/likelihoods_not_pvalues/?l=4xx) is an interesting statistical technique, and I'm sure it has its good uses in the right contexts. But it would be very surprising if that one weird trick was the best calculation to do in every paper and every circumstance. If you claim it is the universal best way, then I suspect you of blind idealism, insensitivity to context and nuance, ignorance of all the other tools in the toolbox, the sheer folly of callow youth. You only have a hammer and no real-world experience using screwdrivers, so you claim everything is a nail."

Msr. Lawful: "On complex problems we may not be able to compute exact [Bayesian updates](https://arbital.com/p/bayes_rule_guide/), but the math still describes the _optimal_ update, in the same way that a Carnot cycle describes a thermodynamically ideal engine even if you can't build one. You are unlikely to find a superior viewpoint that makes some other update even more optimal than the Bayesian update, not without doing a great deal of fundamental math research and maybe not at all. We didn't choose that formalism arbitrarily! We have a very broad variety of [coherence theorems](https://arbital.com/p/expected_utility_formalism/?l=7hh) all spotlighting the same central structure of probability theory, saying variations of 'If your behavior cannot be viewed as coherent with probability theory in sense X, you must be executing a dominated strategy and shooting off your foot in sense Y'."

I currently suspect that when Msr. Law talks like this, Msr. Toolbox hears "I prescribe to you the following recipe for your behavior, the Bayesian Update, which you ought to execute in every kind of circumstance."

This also appears to me to frequently turn into one of those awful durable forms of misunderstanding: Msr. Toolbox doesn't see what you could possibly be telling somebody to do with a "good" or "ideal" algorithm besides executing that algorithm.

It would not surprise me if there's a symmetrical form of durable misunderstanding where a Lawist has trouble processing a Toolboxer's disclaimer: "No, you don't understand, I am not trying to describe the one true perfect optimal algorithm here, I'm trying to describe a context-sensitive tool that is sometimes useful in real life." Msr. Law may not see what you could possibly be doing with a supposedly "prudent" or "actionable" recipe besides saying that it's the correct answer, and may feel very suspicious of somebody trying to say everyone should use an answer while disclaiming that they don't really think it's true. Surely this is just the setup for some absurd motte-and-bailey where we claim something is the normative answer, and then as soon as we're challenged we walk back and claim it was 'just one tool in the toolbox'.

And it's not like those callow youths the Toolboxer is trying to lecture don't actually exist. The world is full of people who think they have the One True Recipe (_without_ having a normative ideal by which to prove that this is indeed the optimal recipe given their preferences, knowledge, and available computing power).

The only way I see to resolve this confusion is by grasping a certain particular abstraction and distinction - as a more Lawfully inclined person might put it. Or by being able to deploy both kinds of thinking, depending on context - as a more Toolbox-inclined person might put it.

It may be that none of my readers need the lecture at this point, but I've learned to be cautious about that sort of thing, so I'll walk through the difference anyways.

---

Every traversable maze has a spatially shortest path; or if we are to be precise in our claims but not our measurements, a set of spatially shortest-ish paths that are all nearly the same distance.

We may perhaps call this spatially shortest path the "best" or "ideal" or "optimal" path through the maze, _if_ we think our preference for walking shorter distances is the _only_ pragmatically important merit of a path.

That there exists some shortest path, which may even be optimal according to our preferences, doesn't mean that you can come to an intersection at the maze and "just choose whichever branch is on the shortest path".

And the fact that you cannot, at an intersection, just choose the shorter path, doesn't mean that the concepts of distance and greater or lesser distance aren't useful.

It might even be that the maze-owner could truthfully tell you, "By the way, this right-hand turn here keeps you on the shortest path," and yet you'd still be wiser to take the left-hand turn... because you're following the left-hand rule. Where the left-hand rule is to keep your left hand on the wall and go on walking, which works for not getting lost inside a maze whose exit is connected to the start by walls. It's a good rule for agents with sharply bounded memories who can't always remember their paths exactly.

And if you're using the left-hand rule it is a terrible, terrible idea to jump walls and make a different turn just once, even if that looks like a great idea at the time, because that is an excellent way to get stuck traversing a disconnected island of connected walls inside the labyrinth.

So making the left-hand turn leads you to walk the shortest expected distance, relative to the other rules you're using. Making the right-hand turn instead, even if it seemed locally smart, might have you traversing an infinite distance instead.

But then you may not be on the shortest path, even though you are following the recommendations of the wisest and most prudent rule given your current resources. By contemplating the difference, you know that there is in principle room for improvement. Maybe that inspires you to write a maze-mapping, step-counting cellphone app that lets you get to the exit faster than the left-hand rule.

And the reason that there's a better recipe isn't that "no recipe is perfect", it isn't that there exists an infinite sequence of ever-better roads. If the maze-owner gave you a map with the shortest path drawn in a line, you could walk the true shortest path and there wouldn't be any shorter path than that.

Shortness is a property of paths; a tendency to produce shorter paths is a property of recipes. What makes a phone app an improvement is not that the app is adhering more neatly to some ideal sequence of left and right turns, it's that the path is shorter in a way that can be [defined independently of the app's algorithms](https://arbital.com/p/fair_problem_class/).

Once you can admit a path can be "shorter" in a way that abstracts away from the walker - not _better,_ which does depend on the walker, but _shorter_ - it's hard not to admit the notion of there being a shortest path.

I mean, I suppose you could try very hard to never talk about a shortest path and only talk about alternative recipes that yield _shorter_ paths. You could diligently make sure to _never_ imagine this shorterness as a kind of decreased distance-in-performance-space from any 'shortest path'. You could make very sure that in your consideration of new recipes, you maintain your ideological purity as a toolboxer by only ever asking about laws that govern which of two paths are shorter, and never getting any inspiration from any kind of law that governs which path is shortest.

In which case you would have diligently eliminated a valuable conceptual tool from your toolbox. You would have carefully made sure that you always had to take longer roads to those mental destinations that can be reached the fastest by contemplating properties of ideal solutions, or distance from ideal solutions.

But why? Why would you?

---

I think at this point the Toolbox reply - though I'm not sure I could pass its Ideological Turing Test - might be that idealistic thinking has a great trap and rottenness at its heart.

It might say:

Somebody who doesn't wisely shut down all this thinking about "shortest paths" instead of the left-hand rule as a good tool for some mazes - someone who begins to imagine some unreachable ideal of perfection, instead of a series of apps that find shorter paths most of the time - will surely, in practice, begin to confuse the notion of the left-hand rule, or their other current recipe, with _the shortest path._

After all, nobody can see this "shortest path", and it's supposedly a virtuous thing. So isn't it an inevitable consequence of human nature that people will start to use that idea as praise for their current recipes?

And also in the real world, surely Msr. Law will inevitably forget the extra premise involved with the step from "spatially shortest path" to "best path"- the contextual requirement that our only important preference was shorter spatial distances so defined. Msr. Law will insist that somebody in a wheelchair go down the "best path" of the maze, even though that path involves going up and down a flight of stairs.

And Msr. Law will be unable to mentally deal with a helicopter overflying the maze that violates their ontology relative to which "the shortest path" was defined.

And it will also never occur to Msr. Law to pedal around the maze in a bicycle, which is a much easier trip even if it's not the shortest spatial distance.

And Msr. Law will assume that the behavior of mortgage-backed securities is independently Gaussian-random because the math is neater that way, and then derive a definite theorem showing a top-level tranche of MBSs will almost never default, thus bringing down their trading firm -

To all of which I can only reply: "Well, yes, that happens some of the time, and there are contextual occasions where it is a useful tool to lecture Msr. Law on the importance of having a diverse toolbox. But it is not a _universal_ truth that _everyone_ works like that and needs to be prescribed the same lecture! You need to be sensitive to context here!"

There are definitely versions of Msr. Law who think the universal generalization they've been told about is a One Weird Trick That Is All You Need To Know; people who could in fact benefit from a lecture on the importance of diverse toolboxes.

There are also extreme toolbox thinkers who could benefit from a lecture on the importance of thinking that considers unreachable ideals, and how to get closer to them, and the obstacles that are moving us away from them.

Not to commit the [fallacy of the golden mean](https://en.wikipedia.org/wiki/Argument_to_moderation) or anything, but the two viewpoints are both metatools in the metatoolbox, as it were. You're better off if you can use both in ways that depend on context and circumstance, rather than insisting that _only_ toolbox reasoning is the _universally best context-insensitive_ metaway to think.

If that's not putting the point too sharply.

Thinking in terms of Law is often useful. You just have to be careful to understand the context and the caveats: when is the right time to think in Law, how to think in Law, and what type of problems call for Lawful thinking.

Which is _not_ the same as saying that every Law has exceptions. Thermodynamics still holds even at times, like playing tennis, when it's not a good time to be thinking about thermodynamics. If you thought that every Law had exceptions because it wasn't always useful to think about that Law, you'd be rejecting the metatool of Law entirely, and thinking in toolbox terms at a time when it wasn't useful to do so.

Are there Laws of optimal thought governing the optimal way to contextualize and caveat, which might be helpful for finding good executable recipes? The naturally Lawful thinker will immediately suspect so, even if they don't know what those Laws are. Not knowing these Laws won't panic a healthy Lawful thinker. Instead they'll proceed to look around for useful yet chaotic-seeming prescriptions to use now instead of later - _without_ mistaking those chaotic prescriptions for Laws, _or_ treating the chaos of their current recipes as proof that there's no good normative ideals to be had.

Indeed, it can sometimes be useful to contemplate, in detail, that there are probably Laws you don't know. But that's a more advanced metatool in the metatoolbox, useful in narrower ways and in fewer contexts having to do with the invention of new Laws as well as new recipes, and I'd rather not strain Msr. Toolbox's credulity any further.

---

To close out, one recipe I'd prescribe to reduce confusion in the toolbox-inclined is to try to see the Laws as descriptive statements, rather than being any kind of normative ideal at all.

The idea that there's a shortest path through the maze isn't a "normative ideal" instead of a "prescriptive ideal", it's just true. Once you define distance there is in fact a shortest path through the maze.

The triangle inequality might sound very close to a prescriptive rule that you ought to walk along AC instead of ABC. But actually the prescriptive rule is only if you _want_ to walk shorter distances ceteris paribus, only if you know which turn is which, only if you're not trying to avoid stairs, and only if you're not taking an even faster route by getting on a bicycle and riding outside the whole maze to the exit. The prescriptive rule "try walking along AC" isn't the same as the triangle inequality itself, which goes on being _true_ of spatial distances in Euclidean or nearly-Euclidean geometries - whether or not you know, whether or not you care, whether or not it's useful to think about at any given moment, even if you own a bicycle.

The statement that you can't have a heat-pressure engine more efficient than a Carnot cycle isn't about gathering in a cultish circle to sing praises of the Carnot cycle as being the ideally best possible kind of engine. It's just a true fact of thermodynamics. This true fact might helpfully suggest that you think about obstacles to Carnot-ness as possible places to improve your engine - say, that you should try to prevent heat loss from the combustion chamber, since heat loss prevents an adiabatic cycle. But even at times when it's not in fact useful to think about Carnot cycles, it doesn't mean your heat engine is allowed on those occasions to perform better than a Carnot engine.

You can't extract any more evidence from an observation than is given by its likelihood ratio. You could see this as being true because Bayesian updating is an often-unreachable normative ideal of reasoning, so therefore nobody can do better than it. But I'd call it a deeper level of understanding to see it as a law saying that you can't get a higher expected score by making any different update. This is a generalization that holds over both Bayes-inspired recipes and non-Bayes-inspired recipes. If you _want_ to assign higher probability to the correct hypothesis, it's a short step from that preference to regarding Bayesian updates as a normative ideal; but the idea begins life as a descriptive assertion, not as a normative assertion.

It's a relatively shallow understanding of the [coherence theorems](https://arbital.com/p/expected_utility_formalism/?l=7hh) to say "Well, they show that if you don't use probabilities and expected utilities you'll be incoherent, which is bad, so you shouldn't do that." It's a deeper understanding to state, "If you do something that is incoherent in way X, it will correspond to a dominated strategy in fashion Y. This is a universal generalization that is true about every tool in the statistical toolbox, whether or not they are in fact coherent, whether or not you personally prefer to avoid dominated strategies, whether or not you have the computing power to do any better, even if you own a bicycle."

I suppose that when it comes to the likes of [Fun Theory](http://lesswrong.com/lw/xy/the_fun_theory_sequence/), there isn't any deeper fact of nature underlying the "normative ideal" of a eudaimonic universe. But in simpler matters of math and science, a "normative ideal" like the Carnot cycle or Bayesian decision theory is almost always the manifestation of some simpler fact that is _so closely related to something we want_ that we are tempted to take one step to the right and view it as a "normative ideal". If you're allergic to normative ideals, maybe a helpful course would be to discard the view of whatever-it-is as a normative ideal and try to understand it as a fact.

But that is a more advanced state of understanding than trying to understand what is better or best. If you're not allergic to ideals, then it's okay to try to understand why Bayesian updates are often-unreachable normative ideals, before you try to understand how they're just there.
