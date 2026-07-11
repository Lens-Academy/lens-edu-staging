---
title: "A Closer Look at Before and After"
source_url: https://ifanyonebuildsit.com/10/a-closer-look-at-before-and-after
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770718803}@@
  - IABIED--}
---
As mentioned in the chapter, the fundamental difficulty researchers face in AI is this:

You need to align an AI **Before** it is powerful enough and capable enough to kill you (or, separately, to resist being aligned). That alignment must then *carry over to different conditions,* the conditions **After** a superintelligence or set of superintelligences[\*](#ftnt250) could kill you if they preferred to.

In other words: If you're building a superintelligence, you need to align it without ever being able to thoroughly test your alignment techniques in the real conditions that matter, regardless of how "empirical" your work feels when working with systems that are not powerful enough to kill you.

This is not a standard that AI researchers, or engineers in almost any field, are used to.

We often hear complaints that we are asking for something unscientific, unmoored from empirical observation. In reply, we might suggest talking to the designers of the space probes we talked about in Chapter 10.

Nature is unfair, and sometimes it gives us a case where the environment that counts is not the environment in which we can test. Still, occasionally, engineers rise to the occasion and get it right on the first try, *when armed with a solid understanding of what they're doing* — robust tools, strong predictive theories — something very clearly lacking in the field of AI.

The whole problem is that *the AI you can safely test, without any failed tests ever killing you*, is operating under a different regime than the AI (or the AI ecosystem) that *needs to have already been tested, because if it's misaligned, then everyone dies.* The former AI, or system of AIs, does not correctly perceive itself as having a realistic option of killing everyone if it wants to. The latter AI, or system of AIs, does see that option.[†](#ftnt251)

Suppose that you were considering making your co-worker Bob the dictator of your country. You could try making him the mock dictator of your town first, to see if he abuses his power. But this, unfortunately, isn't a very good test. "Order the army to intimidate the parliament and 'oversee' the next election" is a very different option from "abuse my mock power while being observed by townspeople (who can still beat me up and deny me the job)."

Given a sufficiently well-developed theory of cognition, you could try to read the AI's mind and predict what cognitive state it would enter if it really did think it had the opportunity to take over.

And you could set up simulations (and try to spoof the AI's internal sensations, and so on) in a way that your theory of cognition predicts would be very similar to the cognitive state the AI would enter once it really had the option to betray you.[‡](#ftnt252)

But the link between these states that you induce and observe in the lab, and the state where the AI actually has the option to betray you, *depends fundamentally on your untested theory of cognition.* An AI's mind is liable to change quite a bit as it develops into a superintelligence!

If the AI creates new successor AIs that are smarter than it, *those* AIs' internals are likely to differ from the internals of the AI you studied before. When you learn only from a mind Before, any application of that knowledge to the minds that come After routes through an *untested theory* of how minds change between the Before and the After.

Running the AI until it has the opportunity to betray you *for real,* in a way that's hard to fake, is an empirical test of those theories in an environment that differs fundamentally from any lab setting.

Many a scientist (and many a programmer) knows that their theories of how a complicated system is going to work in a fundamentally new operating environment *often don't go well on the first try*.[§](#ftnt253) This is a research problem that calls for an "unfair" level of predictability, control, and theoretical insight, in a domain with unusually lowlevels of understanding — with all of our lives on the line if the experiment's result disconfirms the engineers' hopes.

This is why it seems *overdetermined,* from our perspective, that researchers should not rush ahead to push the frontier of AI as far as it can be pushed. This is a legitimately insane thing to attempt, and a legitimately insane thing for any government to let happen.

[\*](#ftnt250_ref) We sometimes hear people say that there's no cause for worry, because we can set up *multiple* superintelligences to all collectively police each other. There are many reasons these proposals strike us as wildly implausible, but it's worth emphasizing here that ideas like this face the same core problem we've mentioned a few times before: *We only get one shot at the clever scheme working.*

You can do some testing and observation, Before, of setups that *don't* actually stake the life of everyone on the planet*,* but the case that matters will not be quite the same. (And such a scheme would need to be *very* clever, because we have no idea how to get *[any](/10/what-if-there-are-lots-of-different-ais)* [of the AIs in the set](/10/what-if-there-are-lots-of-different-ais) to care about us.)

[†](#ftnt251_ref) You could try to make a weaker AI mistakenly *believe* that it's in a position to gain a decisive advantage, and try to train it not to act that way even when it sees that option. But you would be training an AI system that was [dumb enough to be fooled](/3/smart-ais-spot-lies-and-opportunities), and that was seeing fake weapons instead of real weapons. So the potentially-lethal distribution would still be noticeably different from the training distribution; there's a noticeable difference between being *told* you have a weapon that could kill your operators, and actually building a weapon or escape route yourself and understanding it in detail. The AI that is fooled by fake options is not the same as the AI that sees real options.

An alignment mechanism that works on the AIs dumb enough to be fooled is an alignment mechanism that has only ever been tested Before but that nevertheless needs to work After.

[‡](#ftnt252_ref) For more on why this isn't a very hopeful idea, see our answer to the question "[What if we make it think it's in a simulation?](/5/what-if-we-make-it-think-its-in-a-simulation)"

[§](#ftnt253_ref) For instance: Newtonian mechanics made all sorts of shockingly good empirical predictions. It was a simple, concise mathematical theory with huge explanatory power that blew every previous theory out of the water. But if you tried to use it to send payloads to distant planets at relativistic speeds, you'd still be screwed, because Newtonian mechanics does not account for relativistic effects.

The only advance warnings you would get would be little hints about light seeming to move at the same speed in all directions at all times of year, and light bending around the sun during eclipses, and the perihelion of Mercury being a little off from what Newtonian mechanics predicted. Small anomalies, weighed against an enormous body of predictive success in a thousand empirical domains.

Imagine that, before Newtonian mechanics was discovered, strange aliens offered Earth a bargain, where we'd be given great wealth if we could complete an interstellar delivery, but if we failed then we'd be destroyed. Imagine scientists discovered Newtonian mechanics, arguing that surely *now* they should be allowed to send the delivery now. They'd have heaps and heaps of empirical evidence on their side, in accordance with new scientific knowledge that was in the middle of unlocking powerful new technologies.

Imagine the amount of *spine* that a regulator would need in order to say, "And yet, you can't explain the advancement of the perihelion of Mercury, so the answer is 'no.'"

It would feel so unfair, to the scientists! They'd have so much evidence to bring to bear!

(Indeed, a realistic regulator probably *couldn't tell* that the answer would still have to be "no," which is part of why we are [not hopeful about an international coalition](/12/why-not-use-international-cooperation-to-build-ai-safely-rather-than-to-shut-it-all-down) and think that Earth just needs to back off from the problem entirely.)

Nature doesn't care about all the mountains of evidence and predictions accumulated by Newtonian physics. The theory still falls apart when we move to energies and scales far outside what we'd previously been able to observe. It just doesn't work at high energies and long distances.

Getting scientific theories to work on the first critical try is hard.

---

[\*](#ftnt254_ref) As we observe in the book's Chapter 10 endnote 6, physicists do not actually give neutron multiplication factors in percentages. We give them that way for clarity, for reasons discussed in the aforementioned endnote.

#### Notes

[1] *first thermonuclear weapon:* Castle Bravo was not the first detonation of a thermonuclear (hydrogen) *device;* that distinction belongs to the building-sized "Mike" of the [Ivy Mike test](https://en.wikipedia.org/wiki/Ivy_Mike), which did not rely on lithium.