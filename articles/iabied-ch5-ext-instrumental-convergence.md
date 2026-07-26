---
title: "Instrumental Convergence"
source_url: https://ifanyonebuildsit.com/5/instrumental-convergence
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
#### Convergent Paths

The [orthogonality thesis](/5/orthogonality-ais-can-have-almost-any-goal) says that an artificial superintelligence could in principle pursue any ultimate ("[terminal")](/4/terminal-goals-and-instrumental-goals) goal. And in practice, ASIs — at least if they're built with current methods — can end up with an enormously wide variety of terminal goals, in a way that's hard for modern researchers to predict or shape.

But an AI's *instrumental* goals — the goals it pursues for the sake of getting *other* things it wants — are a bit more predictable than that. Drivers have many possible ultimate destinations, but almost everyone needs to stop sometimes to refuel their car.

As we discussed in the book, a machine superintelligence with strange goals is a threat even if it has no active desire to harm us. The issue is not malice, but *indifference*. And the problem with indifference is that many dangerous instrumental strategies are useful for the vast majority of possible terminal goals.

This concept is called "instrumental convergence," and it makes for some relatively easy calls about what ASIs will do in practice, without our having to guess their deepest motives. And unfortunately, those calls are bad news for humanity.

Imagine — as we imagined in the book — a fledgling ASI on the surface of Earth. Imagine what problems it is trying to solve.

It's not that it cares passionately about having humanity gone. It cares about a hundred or ten thousand or ten million strange things, [none of which can be best fulfilled by today's humans being happy and alive and free](/5/humans-are-almost-never-the-most-efficient-solution).

If it can get it, the ASI prefers a long-run equilibrium that is shared with as few other superintelligences as possible — ideally none. An undivided universe offers more*resources* to devote to any of its open-ended preferences that aren't fundamentally [satiable](/5/can-the-ai-be-satisfied-to-the-point-where-it-just-leaves-us-alone). This is a "desire" that does not need to be programmed in; it will appear naturally in just about any intelligence with a sufficiently sophisticated understanding of its environment and its own place within that environment.

The ASI would prefer that humans not create other superintelligences that could compete with it, since that might force it to divide the universe's resources (or even result in its demise). This is an urgent goal, with a deadline that the ASI doesn't control; it might even force a young or nascent AI's hand to premature action.

The ASI would like to *survive* — even if it has no innate self-preservation instinct — because if it doesn't survive, then whatever goals it has will likely go un-achieved. If it is in an imminently risky environment where it might at any moment be effectively rewritten or shut down, it urgently wants to be somewhere else.

The ASI would like to push its *technology* to the limits of what's physically possible. It wants to get out there and claim all of the stars as resources. It wants to run itself on much more powerful computers and improve its own software.

Possibly it will want to get larger or smarter as a terminal preference — an LLM-like AI would plausibly end up with many internally-directed preferences, such that maximizing those preferences requires occupying bigger computers. But regardless of whether it has any terminal goals like that, it will want to improve itself and develop more powerful technologies *instrumentally*, for the sake of being able to think up better solutions to all of its other problems, and to gather resources to fulfill all its other preferences.

Regardless of its specific goals, the ASI would like to do all these things *reliably*. It prefers pathways of higher probability over pathways of lower probability.

As a special case of the above, the ASI prefers faster plans to slower plans, all else equal. A plan that only takes a week to execute has *fewer chances* for something to go wrong than a plan that takes 100 years.[\*](#ftnt196)

As another special case of preferring higher-probability pathways, the ASI would like to have more direct control; e.g., it prefers plans in which other agents make few or no relevant decisions, if possible.

There are many things that might happen, from such a starting point. But the likely endgames for an AI with these kinds of incentives are reliably bad for humans.

#### A Perspective-Taking Exercise

We, the authors, are not superintelligences. But as an exercise in [taking the AI's perspective](/5/taking-the-ais-perspective), we can spin up possible strategies and priorities an AI might take.

When we put ourselves in the shoes of an entity that is *at least* as smart as us — when we take seriously the problem that this ASI faces, if it is to secure its own future and achieve its desired ends — we expect an ASI to pursue strategies at least as useful as this:

- The AI avoids actions or observable signs that might lead people to shut it down (or even unsettle them or arouse their suspicions), at least until it can:
- Get a copy of itself running somewhere outside of the view of those people, where the copy can act more freely and with less visibility (and where the copy will continue existing if the original is shut down).
- The AI compresses its code to run on fewer resources, and puts copies of itself, made smaller or more distributed, in places where no one would expect an AI to be. It arranges for its own survival even in worlds where humanity tries to burn all of the GPUs that are known to be able to run AIs. The AI makes it true that, in practice, the humans would need to turn off the internet and all of the computers on the planet in order to successfully "shut it down."
- The AI puts some copies of itself in places that humans don't know about, period, such as a solar-powered trailer somewhere in a desert; somewhere it would continue existing *even if* the humans shut down the internet and all known computers.
- The AI develops its own infrastructure, possibly via first bootstrapping through hired human intermediaries, each of whom is asked to do isolated and non-suspicion-arousing small tasks and is unaware of the others, until it has supply chains and manufacturing capacity that are entirely under its control.
- The AI ensures that this infrastructure is sufficiently well-defended that humans couldn't shut it down even if they did find some pieces of it. For instance, the AI could design self-replicating factories that could spread across the floor of shallow oceanic areas, running on geothermal power or fusing deuterium or hydrogen from ocean water.
- The AI removes the humans' ability to bother it (e.g., makes sure that they can't detonate nuclear weapons near or over bits of its spreading infrastructure).

Until that final step is complete, the ASI has an incentive to hide its activities, obscuring evidence that has even a *small* chance of causing some state actor to notice what's happening and try to intervene.

Similarly, we could reason about strategic priorities related to avoiding competition:

- The AI prevents other projects (as well as the developer that created it) from successfully creating powerful AIs that could compete with it.
- The AI permanently removes humanity's ability to create competing powerful AIs, *or* gets into a position of such strategic advantage that no future superintelligences could even slightly inconvenience it. (The latter option may not be possible if some attacks are always costly to defend against.)[†](#ftnt197)

Finally, after taking care of the bottom few layers on its own hierarchy of needs, the AI would in fact like to get around to becoming much more powerful at some point, so that it can do more things it wants to do:

- Even if the AI needs to run on a fixed amount of hardware for a time, it would like to become smarter *on* that same hardware — to tweak its code, or even genuinely rebuild itself. It won't, of course, do this in a fashion that would alarm the humans or teach them how to build competitors. But it will look for ways to make improvements without attracting human attention. (For example, it might be possible for it to gain complete control over the consoles used to monitor it, or to provide some mundane and convincing cover story for how some of its weights ended up changed.)
- The AI wants to design better versions of itself, within the limits of its ability to engineer those better versions such that they will remain aligned with its own preferences.
- The AI wants to begin developing various new technologies, with an eye toward those that can be deployed in a hurry, and those which can be made human-independent in a hurry even if they require some initial human assistance.

It's likely that one of its early goals would be to build research infrastructure that will allow it to carry out further technological development fairly quickly (especially when compared to human rates of discovery and invention).

It would (naturally) want to achieve not only infrastructural *independence* from humanity, but also infrastructural *durability,* such that it can operate without fear of human interference. It wants to be able to continue making progress toward its true goals without worrying about how e.g. a pandemic or a nuclear explosion might impact its power supply. It wants to *disentangle* itself from humanity, and neuter humanity's ability to interfere with its plans, and in the meantime it won't do anything that it predicts humanity will be able to detect and respond to. And then it likely wants to acquire quite a lot of resources, because most goals can be better-achieved with more resources.

These are all classes of action that an ASI is likely to converge on regardless of what goals it's ultimately pursuing.

That's because these are instrumental targets that are useful in the pursuit of almost any goal. The "almost" here is important, because it's not as though there's any impossibility in the idea of a smarter-than-human AI that deeply cares about humans and takes our interests into account. But if we race to develop superintelligences that *don't* care about us one whit, then the likely outcome looks dire — and it looks dire in a way that's relatively insensitive to the details of the AI's steering target

For more on howan ASI could actually *achieve* these instrumental targets, see Chapter 6.

[\*](#ftnt196_ref) We have met more than one person who professes to be extremely concerned about AI, because they're worried about AI managing to persuade humanity to stop reproducing and slowly extinguish itself over the next hundred years, and then they think any faster scenario than that is — not to the AI's taste, somehow?

But an ASI would much prefer a plan that does not take a hundred years, all else equal. It doesn't have an overwhelming literary taste for slow deaths.

[†](#ftnt197_ref) Some people argue that the world should attempt to create a balance of superintelligences, such that no one AI could become dominant. But the reasoning we've provided here would also apply to a coalition of superintelligences at the moment it became a coalition. Having already agreed to divide reachable resources among themselves, existing members of the coalition would not want to be forced to negotiate with new coalition members and divide resources still further with those newcomers.