---
title: "How could an AI trained only on human data surpass humans?"
source_url: https://ifanyonebuildsit.com/2/how-could-an-ai-trained-only-on-human-data-surpass-humans
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770983981}@@
  - IABIED--}
---
#### Perhaps by learning general skills and implementing them better.

Deep Blue was able to play chess much better than any of its programmers at IBM. How could people possibly build a machine that was smarter than them in the domain of chess? By making an AI that did some of the same sorts of things that they tried to do in chess games (like considering multiple possible ways the game could play out), but much more quickly and accurately.

In the same way, an AI could learn to do better than humans at all sorts of other skills. It could learn patterns of thought that contribute to general reasoning skills, and then perform those general skills faster and with a lower error rate.

It might also make fewer mental *missteps* of the sort that humans are prone to making. This could be because those missteps were trained out of the AI at one point or another, or because the underlying machinery in the AI that predicts *human* missteps was never itself prone to the same missteps. Or perhaps the AI was eventually given the power to self-modify and it removed its propensity for missteps; or perhaps it was eventually tasked with designing a smarter AI and it designed one that made fewer missteps; or its training taught it to make fewer mistakes some other way.

The ability to have wholly novel insights doesn't come from some profound atomic spark — it's built of mundane parts, like [all profound things are](/1/special-behavior-is-built-out-of-mundane-parts). A student can, in principle, observe their teacher and learn whatever kinds of things they're doing, then have a spark of insight and be able to do those things faster or better. Or a student could repurpose different techniques they learned from a teacher to find a wholly novel way to generate their own insights.

We've been fortunate enough to have direct observational evidence of both points, in the case of AlphaGo, which we discussed [above](/2/arent-ais-only-able-to-parrot-back-what-humans-say#ais-can-already-surpass-their-training-data-or-forego-human-data). AlphaGo was trained extensively on human data, but was able to play Go better than the best humans. (And AlphaGo Zero, which learned only from self-play (and no human data), proceeded to go even farther still.)

This doesn't look to us like a world where human data is the key limitation, compared to the real limitations being things like the AI's architecture, or the amount of computation it's able to use before playing.

Students can exceed their masters.

#### Perhaps by whatever other method works. Success often requires such skills, so gradient descent will find them.

Predicting human words requires understanding the world, as we discussed in "[Aren't AIs only able to parrot back what humans say?](/2/arent-ais-only-able-to-parrot-back-what-humans-say)"

To give a fanciful example: In the late 1500s, the astronomer Tycho Brahe painstakingly collected observations of planetary positions in the night sky. His data was vital to the work of Johannes Kepler, who discovered the elliptical pattern of planetary motion, which inspired Newton's theory of gravitation. But Brahe himself never figured out the laws that govern the planets.

Imagine an AI trained only on texts produced up until the year 1601, that had never heard of Brahe but had to predict each data point that Brahe scratched into his journal. Brahe kept recording the position of Mars each evening, so the AI would perform better the more accurately it predicts the location of Mars. Gradient descent would reinforce any parts inside the AI that were capable of figuring out exactly when Mars would seem to turn around (from Brahe's perspective) and traverse backwards through the sky.

It doesn't matter that Brahe never managed to figure out that law of nature. The simple training target "predict what Mars-position Brahe will write down next" is the sort of training target that would reinforce whatever parts in the AI were smart enough to figure out how planets move.

If you kept training and training and training that AI until it was doing better and better and better at predicting what Brahe would write down in the late 1500s, that AI would have every reason to develop scientific insights that Brahe never could. An AI will do *better at its task of predicting humans* if it becomes smarter than the humans it's predicting, because sometimes the humans write down records of phenomena that they themselves cannot perfectly predict.

There's a separate question of whether modern architectures and training processes and data are *enough*for AIs to exceed their teachers. Modern LLMs look like they're not quite there yet. But there's no theoretical impediment to the very idea of exceeding your teacher. Training an AI on predicting humans is enough to let it surpass us, in principle*.*

#### Notes

[1] *exceed their masters:* Since drafting this answer in early 2025, signs have already emerged that modern AIs can [do novel mathematical work](https://x.com/SebastienBubeck/status/1958198661139009862?t=g_GKty7CZ525HV78YKzR-w) and [outperform human mathematicians](https://x.com/mathematics_inc/status/1966194751847461309) in some ways. You could say that these AIs are just learning human techniques and then applying them more consistently or more tenaciously or faster, but, well, that's one way that students can exceed their masters, if the skills they're learning are sufficiently flexible and general. The skills that AIs learn as we write this don't quite seem general enough for them to beat the best humans at the most visionary research, but the AIs are certainly crossing lines that used to be considered important.

[2] *not quite there yet:* For example, studies into LLMs trained on orbital trajectories [show](https://arxiv.org/abs/2507.06952) that they fail to apply Newtonian mechanics.