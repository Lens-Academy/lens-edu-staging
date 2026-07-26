---
title: "Won't there be early warnings researchers can use to identify problems?"
source_url: https://ifanyonebuildsit.com/11/wont-there-be-early-warnings-researchers-can-use-to-identify-problems
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
#### Warning signs don't help if you don't know what to do with them.

In the Chapter 2 resources, we looked at some problems with relying on warning signs in the [English chain-of-thought scratchpads](/2/but-some-ais-partly-think-in-english-doesnt-that-help) found in some reasoning models.

One problem we discuss is that AI companies haven't meaningfully reacted to the warning signs they've already received.

That's probably because there's a big difference between having warning signs and having something you can *do* about them.

In 2009, businessman and deep sea explorer Stockton Rush [co-founded OceanGate](https://www.smithsonianmag.com/innovation/worlds-first-deep-diving-submarine-plans-tourists-see-titanic-180972179/), an undersea tourism company. OceanGate built a five-person [submersible](https://web.archive.org/web/20230619233914/https://oceangate.com/our-subs/titan-submersible.html), *Titan*, which brought well-paying customers to view the wreck of the *Titanic* at a bone-crunching depth of two and a half miles below the surface.

One of the safety measures that OceanGate made use of was an [array of acoustic sensors and strain gauges](https://web.archive.org/web/20230619233914/https://oceangate.com/our-subs/titan-submersible.html) for measuring hull integrity. They billed this as a counterargument to people who said their carbon-fiber hull would fail. They acknowledged that it might fail *eventually,* but they'd be fine, because they were measuring it. They were monitoring it. They would be able to see the warning signs.

In January 2018, OceanGate's director of marine operations, David Lochridge, [told senior management](https://techcrunch.com/2023/06/20/a-whistleblower-raised-safety-concerns-about-oceangates-submersible-in-2018-then-he-was-fired/) that the submersible design was unsafe, that repeated pressure cycling could damage the hull, and that monitoring alone wasn't enough when a catastrophic failure could happen in milliseconds. Lochridge refused to authorize manned tests until the hull had been scanned for flaws.

OceanGate fired him.

Two months later, [industry experts and oceanographers](https://www.nytimes.com/2023/06/20/us/oceangate-titanic-missing-submersible.html) wrote OceanGate an extremely concerned [letter](https://int.nyt.com/data/documenttools/marine-technology-society-committee-2018-letter-to-ocean-gate/eddb63615a7b3764/full.pdf) warning the company that its reckless experimentation could precipitate disaster.

(An obvious parallel can be drawn to the current state of AI research, in which early warnings are [ignored](/12/the-lemoine-effect), concerned employees are [fired under dubious circumstances](https://www.transformernews.ai/p/openai-employee-says-he-was-fired) or [resign in frustration](https://www.vox.com/future-perfect/2024/5/17/24158403/openai-resignations-ai-safety-ilya-sutskever-jan-leike-artificial-intelligence), and whistleblowers within the industry write open letters to [sound the alarm](https://righttowarn.ai/).)

On July 15, 2022, after passengers reported hearing a loud bang while ascending, the measurements revealed a [permanent change in hull strain levels](https://abcnews.go.com/US/ntsb-engineer-titan-submersible-hull-anomalies/story?id=114076436). In retrospect, it was probably an indication that the carbon fiber hull was [on the verge of collapse](https://youtu.be/Bq8TCFGaOlc?si=blH-_bYwGIOmJAEL&t=125).

Nobody at OceanGate recognized this as an emergency. They took the sub on a few more deep dives, which went fine. Then, on June 18, 2023, they took the sub on another dive. It imploded, killing Stockton Rush and everyone else aboard.

Warning signs don't matter much if you don't know how to read them.

Warning signs don't matter much if you don't know what to do with them.

Even warning signs that look worrying to *someone* are always easy for an optimist to dismiss with one excuse or another.

If OceanGate had had a mature theory of carbon-fiber hulls that told them exactly what measurements and readings were dangerous, they might have been able to heed the warning signs. But they were working with a technology that nobody quite understood in that way, so the carefully measured changes in strain levels did nothing.

In the case of superintelligence, we don't have enough theory to make good use of warning signs. How are an AI's thoughts going to change as it gets smarter? What internal forces are driving its behavior, and how will those balances shift as it develops the capability to make new and more extreme options for itself? How does it evaluate itself upon reflection, and how would it change itself once it gained the capability to change itself?

If any of those questions have worrying answers, what are the warning signs? For example, current AI systems can sometimes be induced to [try to kill their operators](https://www.anthropic.com/research/agentic-misalignment#more-extreme-misaligned-behavior) in controlled lab experiments.[*](#ftnt266)

If we had a mature theory of intelligence, we would probably be able to look at modern AIs and see all sorts of other warning signs that their drives and preferences are going to shift in ways we don't like, once they get smarter. If humanity could learn from this problem using trial and error — if we got to reset the world after destroying it and try again a few dozen times — then we might learn how to read the signs. There are probably all sorts of subtle tells that would look clearer in retrospect, like the hull strain that the monitoring system on the *Titan* submersible picked up.

But we're not there yet. AI corporate executives are like Stockton Rush — experts on the sidelines are shouting "That new technology will kill people!" and the corporate executives are responding "Don't worry, I'm measuring it!" while having no idea a) what the measurements *mean,* or b) what to do if those measurements are worrying. Except that this time, the whole human species is loaded into the metaphorical submarine.

#### AI is not the kind of mature engineering field that's equipped for this kind of problem.

Stockton Rush was working in the sort of field where, after his submarine imploded, experts could look over the wreckage and analyze the exact cause of failure.[†](#ftnt267) The engineering field was mature to the point where experts could (and [did](https://www.nytimes.com/2023/06/20/us/oceangate-titanic-missing-submersible.html)) guess the technical issues in advance, and could sort them out conclusively after the fact.

It wouldn't be the same with AI. If humanity killed itself with superintelligence tomorrow, and then miraculously went back in time to a week before the disaster began, experts *still* would not know what the AI had been thinking. Maybe they could study the failure and learna little more about how AI actually works. Maybe that would be one step down the path of maturity in the discipline of AI engineering, toward the sort of field that could have safety manuals and a thorough account of the pressures that affect a particular kind of artificial mind as it gets smarter.

But the field isn't there yet, today. It isn't close.

Human engineering usually matures through trial and error. Modern military submarines rarely implode, but early submarines (including military ones) often [crashed, flooded, or exploded](https://www.rand.org/content/dam/rand/pubs/papers/2008/P3481.pdf), and that's part of how the field matured.

Humanity doesn't have the luxury of maturing the field of AI alignment in this fashion.

This brings us to one of the central points we tried to drive home in Chapter 11: the difference between a field in its infancy and a field in its maturity.

Alchemy was a field in its infancy compared to the mature field of chemistry today.

When you hear that the "safety researchers" at AI companies have put forth half a dozen plans for survival, you might think that surely at least one of them has a chance of working.

But when a large number of alchemists in the year 1100 put forward half a dozen plans for turning lead into gold, none of them were going to work. If the kinds of doctors who talked about the [four humors](https://en.wikipedia.org/wiki/Humorism) came up with a bunch of medicinal plans to save you from rabies, none of them would work.

Experts in the *mature* field of chemistry can figure out how to transmute tiny bits of lead into gold, using knowledge from atomic physics. Experts in the *mature* field of medicine can easily treat rabies if they get involved shortly after a patient gets bitten. But someone in the immature field doesn't have a chance.

AI alignment is still in the immature phase.

An immature field has lots of people who say, "Well, I'm just working on measuring it," because measuring outputs is far easier than developing the theory of what constitutes a warning sign, and what to do if you see one. A mature field would have experts discussing the dynamics that govern an AI's internalsand how those may change as the AI's intelligence increases or as its environment changes. They'd have theories about exactly what will change as the AI gets a little smarter, and they'd be comparing different theories to specific observed data. They'd know what parts of the AI's cognition need to be monitored, and they would understand precisely what all the signals meant.

An immature field has lots of people saying: "We'll just have the AIs figure it out somehow and do the alignment work."

Perhaps you can't wade into every debate about an individual plan and tell whether or not it has a chance of working. But we hope you can step back and see how *vague* all these "plans" are, and how they're stuck in "don't worry, we'll measure it" land and "[hopefully it'll be easy](https://www.anthropic.com/news/core-views-on-ai-safety)" land and "we'll just have the AIs do the hard parts" land. We hope that if you step back, it's clear that this field is not in the phase of formal precise technical descriptions of what does and doesn't work and why. It is still in the alchemy phase.

And that does not bode well for humanity, in a situation where we do not have the luxury of learning by trial and error.

[*](#ftnt266_ref) It's not clear how much these warning signs are coming from the AI roleplaying the way it thinks an AI is supposed to behave versus how much it's thinking strategically. The fact that we can't tell which warning signs are real isn't encouraging; it means engineers are much more likely to charge ahead saying "eh, that one probably wasn't real." They might even be right mostof the time, but most of the time isn't good enough when one failure is lethal.

It's also not clear how long this sort of warning sign will keep happening. Modern AIs are still dumb enough to occasionally mistake tests for reality, but this regime won't last forever and is already [starting to end](https://arxiv.org/html/2505.23836). An AI that knows it's being tested might stop exhibiting the worrying behavior in places overseers can see it, even if the underlying tendency remains.

[†](#ftnt267_ref) Delamination due to pressure cycling. In layman's terms: The stresses from many dives pulled the layers of the hull apart, weakening it until it imploded.