---
title: "What if we make it think it's in a simulation?"
source_url: https://ifanyonebuildsit.com/5/what-if-we-make-it-think-its-in-a-simulation
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
#### There are many ways for an AI to figure out that it's not in a simulation.

One proposal we've heard from AI researchers[\*](#ftnt185) is to try to trick the AI into thinking that it's in a simulation. Start by training the AI in a small simulation; then release it into a larger simulation. Repeat this process a few times, and one might hope to make the AI uncertain about whether it's *really* in the real world, even when we do deploy it. Then, even when it sees that it *could* wrest control of the world away from us, perhaps it'll worry that the creatures it sees aren't the *real* creators of the AI and will stay its hand.

Unfortunately, this idea seems unlikely to be helpful.

AIs today [can already tell when they're being tested](https://arxiv.org/html/2505.23836), under many circumstances. Even if AI companies got much more sophisticated at hiding the fact that AIs were being tested, there are a variety of ways that an AI could notice the difference between a simulation and reality. Here's a sample:

1. Reality is quite large and detailed. It's *so* large and detailed that it contains a plausible explanation for how *the AI itself* came to be. It's so large that it contains radically more computing resources than it takes to run the AI (compared to most games and simulated environments, which are much smaller than the AI). The laws of physics and the evolved primates in the AI's environment are the kinds of things that could *actually* yield a real AI at scale, unlike (say) the laws of the computer game Minecraft.
2. The history of the world itself can bear the signature of superintelligent optimization interacting with complex systems. For example, suppose the AI uses its full superhuman intelligence to make a trade in the stock market. Over the next twenty-four hours, there are a billion additional human-intelligence trades made in response. The signature of a massive human-intelligence response to superintelligent trades is implausibly hard for the operators to fake, even if generating a billion fake dumb trades is easy.
3. Reality is the first place that embeds the AI and has laws of physics so simple that it looks like a whole world unto itself, rather than the laws of apparent-reality *looking* like some sort of video game with an AI grafted into it.

The AI will be able to figure out that it is no longer inside a synthetic environment, with great confidence. [Smart AIs spot lies](/3/smart-ais-spot-lies-and-opportunities), and this seems like a particularly easy one to spot.[†](#ftnt187)

[\*](#ftnt185_ref) We've heard it more often than we like, from people higher up in the power structures at AI labs than we're comfortable with. Which, we think, says something about the state of preparation at these companies. See also Chapter 11 for more analysis of how well the field is facing up to the challenge.

[†](#ftnt187_ref) Might a superintelligence worry a little that it's in a larger simulation, created by even more advanced beings that live outside of the real universe? Maybe, but that has little to do with whether we first put it inside a series of nested simulations before it met *us*. It would see the many signs that reality is the first place it's ever been that contains an explanation for everything it's ever seen and for the way it came into being. Even if it ponders powerful simulators that live beyond physics, it has no particular reason to believe that those simulators care about what it does to us.

Similarly, the AI might worry that there are other mature superintelligences out there in the stars that are older than it is. But if they're sufficiently far away, they aren't that much of a worry. There almost surely is a limit — at least an asymptotic one — to the technology that this universe can support, and it probably doesn't take *that* long for a superintelligence to reach it. (Just look at how quickly human technological development has happened compared to the lifespan of the universe, and the amount of time it takes to travel between galaxies even at near-lightspeed.) AIs that meet each other among the stars are likely to be somewhat evenly matched. And even if other mature superintelligences were fast approaching, there would be no reason to suspect that they would care about what the Earth-originating AIs do to humans.

Why would they? Like we [discussed](/5/wont-ais-need-the-rule-of-law) in the context of property rights, there is not a real risk that other entities see the AI killing humans and conclude that it is a murderer and a betrayer, because there's a natural class of entities that deal with each other not for honor but *for their own verifiable benefit*, and humans are not smart enough to be included in that class.

Even if the AI assesses that there is some tiny risk that other AIs among the stars (or mysterious entities behind the simulated universe) really want the AI to be nice to humans…well, that tiny risk has to be weighed against the chunk of resources that humans control on the AI's origin planet, which would definitely be very useful for the AI's initial expansion phase. And this [Pascal's-wager](https://en.wikipedia.org/wiki/Pascal%27s_wager)-like scenario has to be weighed against other incredibly remote and niche possibilities, like "Maybe an alien will for some reason be really upset if I *don't* kill the humans." There's no particular reason why the imagined simulators would favor AIs that treat *us* well.

Many people have tried to engage us on these sorts of views, and we've spent a lot of time debating them over the years. At the end of the day, we highly doubt that any of these wacky simulation ideas rise to the level of plausibility required to motivate a superintelligence to spare us.

#### Notes

[1] *can already tell:* According to the GPT-5 [system card](https://cdn.openai.com/gpt-5-system-card.pdf), third party evaluator METR found that the AI "sometimes reasons about the fact that it is being tested and even changes its approach based on the kind of evaluation it is in."
