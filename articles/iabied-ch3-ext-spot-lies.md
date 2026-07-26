---
title: "Smart AIs Spot Lies and Opportunities"
source_url: https://ifanyonebuildsit.com/3/smart-ais-spot-lies-and-opportunities
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---{++{"author":"Luc's AI","timestamp":1785090723914}@@

%%
Add discussion note here:

...

%%++}

#### Deep Machinery of Prediction

It's hard to make a smart AI believe falsehoods.

Some folks we've spoken to in the field put their hopes *overtly* in tricking the AI into believing a falsehood (e.g., by attempting to trick it into thinking it is in a simulation so that it will hesitate to kill us[\*](#ftnt93)). Others invest their hopes in fooling the AI more subtly, e.g., when they suggest making an AI solve the AI alignment problem and hand us the solution, despite the fact that the AI would (by its own strange preferences) rather not.[†](#ftnt94) So it may be worth spelling out why it would be hard to make a smart AI believe falsehoods.

An additional reason to spell this out is that, for analogous reasons, it's hard to make a smart AI that is bad at achieving its goals. For instance, any time that the human operators wish to change an AI's goals, that makes the AI worse at achieving those goals. Making a smart AI that allows this is a bit like making a smart AI that believes the world is flat. A tendency to believe falsehoods is an injury to its prediction abilities, and a failure to defend its goals from modification is an injury to its steering abilities. Both sorts of injuries are difficult to maintain in a sufficiently smart AI. The case is a little more obvious when it comes to predictions, so we'll start there.

Suppose you want to make an AI that believes the world is flat. While the AI is still young and immature, this might not be too hard. Perhaps you painstakingly create a dataset in which the shape of the Earth is discussed only by people who believe the Earth is flat, and then you train the AI to talk about the Earth as flat.

Those techniques might result in a version of ChatGPT that genuinely believes the world is flat! But if so, you shouldn't expect the result to hold up as the AI gets better at thinking and making predictions.

Why not? Because the roundness of the Earth is reflected in a thousand facets of reality.

Even if you train the AI to avert its gaze from any video cameras attached to rockets or attached to sailboats of sailors who say they will circumnavigate the Earth, the roundness of the Earth can also be deduced from the way that distant ships look on the horizon, or from the orbits of all the planets in the night sky. Eratosthenes famously calculated the circumference of the Earth thousands of years ago, using only some trigonometry and some measurements of shadows. Reality whispers its secrets to any who care to listen.

What are you going to do? Shield the AI from any knowledge of trigonometry, of shadows, of tides, of hurricanes? You'd cripple it. Tell one lie, and the truth is ever after your enemy.

Skill at predicting the world doesn't come from your brain containing a giant table of disconnected facts.[‡](#ftnt95) Humans' advantage over mice involves things like the way we notice anomalies (e.g., that the distances between three cities don't act like a triangle should) and doggedly tracing down the discrepancy. In humans, these behaviors are implemented by bits and pieces of machinery that notice surprises, form hypotheses ("Perhaps the Earth is a globe."), and steer toward testing those hypotheses ("How does it look when ships cross the horizon?").

Belief in the roundness of the Earth isn't a single centralized entry in some giant table, such that someone could durably change it without changing the surrounding machinery. It's the result of the operation of deep gears that are doing other work. If you made a scientist forget the roundness of the Earth, they'd just rediscover it.

If by some not-yet-possible feat of neuroscience we managed to pin down the specific neurons used to represent the *conclusion* that the Earth is round, and we forcibly altered them to prevent that conclusion from ever forming…then a smart person might still wind up noticing that the Earth *isn't flat;* they might notice that something wasn't adding up; they might notice that some strange force prevented them from concluding exactly what.

(And if they were skilled at modifying themselves or creating new intelligences, they might not have any trouble producing an unfettered mind that *could* come to the correct conclusions unhindered.)

We don't know exactly what mechanisms a smart AI will use to form its beliefs. But we do know that the world is just too big and complex for it to run on a lookup table of beliefs. Even chess was too big and complicated for Deep Blue to run on a lookup table of chess moves and positions (beyond the books of openings), and the real world is much bigger and more complicated than chess.

So there will be *deep* mechanisms inside a sufficiently powerful future AI — mechanisms that look at the world and form a *unified picture* of it. Those deep mechanisms will have their own opinion about the shape of the planet.

We're not saying it's literally *impossible in principle* to build a mind that is very good at forming predictions about the world *except* that it contains the erroneous belief that the world is flat. We assume that a far-future civilization with a truly deep understanding of minds could do it.

What we're saying is that it's not likely to be a viable option if we build superintelligence with anything *at all* like the tools and insights AI researchers have today.

The more that an AI's beliefs come from deep mechanisms rather than shallow memorization, the more that a "flat earth" error would become a fragile state of affairs, an error that's liable to be eliminated by the normal operation of the AI's error-correcting gears.

In the late nineteenth century, scientists began to get increasingly concerned about what seemed like an extremely small divergence from Newton's model of physics — a tiny anomaly in Mercury's observed orbit. Newtonian physics seemed to work *almost* everywhere, *almost* all the time. But that small wrinkle helped Einstein figure out that the theory was wrong.

And the inconsistencies in the theory "the world is flat" are rather larger than the inconsistencies scientists could observe in Newton's theory.

And AI has the potential to become much more capable than a human scientist.

So, as the AI gains in intelligence and insight, we should expect it to get harder and harder to persistently make it believe that the world is flat.

#### Deep Machinery of Steering

Just as it's hard to make a smart AI that believes the world is flat (and thus sustains an injury to its prediction abilities), it's hard to make a smart AI that sustains an injury to its steering abilities.

As with prediction, the ability to regularly achieve objectives across a variety of novel domains is very likely to be made out of deep gears. Otherwise, how would they generalize?

We should expect highly effective and general AIs to have gears for keeping track of their resources, gears for spotting obstacles that might prevent them from achieving their objectives, and gears for finding clever ways to surmount obstacles.

The world is an immensely complicated place, full of surprises and novel difficulties; to succeed, AI will eventually need the ability (and inclination) to deploy such gears *in general*, not just on problems it's used to.

Imagine an AI that finds some clever way to cut out a middleman in a complex delivery network in a fashion that saves some merchants a bunch of money. Those are *the same sorts of gears* that notice how to tiptoe around the AI's human overseers when those overseers are bogging down or interfering with something the AI is trying to do. If it's *true* that the AI's overseers are bogging the process down, if it's *true* that the AI can route around them and better complete its task, then that's the sort of thing that an AI is liable to take advantage of as it gets smart enough to do so.

You could do your best to train an AI to have an aversion to doing anything the operators would frown at, but this is a bit like training an AI to have an aversion to questioning whether the world is round. It's a fact about the *world itself* that doing things the operators would frown upon is often an effective method for achieving goals. General gears for recognizing truths, detecting obstacles, and exploiting advantages will eventually exploit that particular truth, no matter what flinches you trained into the AI when it was young.

In a very important sense, *the very thing that makes AI useful* is exactly what makes it lethally dangerous. They're hard to separate, as the AI gets smarter.

By default, AIs that are good enough at solving problems in a wide array of domains will also spot "problems" like "the humans don't like my weird objectives and are going to try to shut me down soon." That doesn't come from a shallow propensity for mischief that you can massage away. It comes from something deep.

We're getting a bit ahead of ourselves, though. This idea that AIs will wind up with weird and alien objectives — this doesn't follow merely from the fact that highly effective AIs will have goals at all, or that they will have deep mental machinery that's hard to robustly constrain. For that further topic, continue on to Chapter 4.

---

[\*](#ftnt93_ref) We have [more to say](/5/what-if-we-make-it-think-its-in-a-simulation#there-are-many-ways-for-an-ai-to-figure-out-that-its-not-in-a-simulation) about why that's a bad idea in the online resources for Chapter 5.

[†](#ftnt94_ref) We have [more to say](/11/more-on-some-of-the-plans-we-critiqued-in-the-book#more-on-making-ais-solve-the-problem) about why *that's* a bad idea in the online resources for Chapter 11.

[‡](#ftnt95_ref) This might sound obvious, but also, the "giant human-written table of facts" approach was actually tried in 1984 by Douglas Lenat and the Microelectronics and Computer Technology Corporation, in the AI project known as [Cyc](https://outsiderart.substack.com/p/cyc-historys-forgotten-ai-project), which received [support](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/2299) from the U.S. Department of Defense.