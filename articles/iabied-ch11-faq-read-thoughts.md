---
title: "Why not just read the AI's thoughts?"
source_url: https://ifanyonebuildsit.com/11/why-not-just-read-the-ais-thoughts
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770823906}@@
  - IABIED--}
---
#### Their thoughts are hard to read.

Many people working in the AI industry, including a handful of lab leaders, have at various points in discussion with us raised the objection:

> An AI won't be able to deceive us, because we'll be able to read its mind! We have full access to the AI's "brain."
>
> Even if the AI knows things we don't and comes up with a plan whose consequences we wouldn't understand, presumably the AI would have to think the thought that it would be useful to deceive its operators at least once, and we — who will be able to read the AI's thoughts — would be able to notice. (And if there are too many thoughts for us to monitor, we can just have other AIs monitor their thoughts!)

One flaw with this plan is that we're currently bad at reading AIs' thoughts. The professionals who study what's going on inside of AIs are nowhere near that level of understanding yet, and [they're vocal about this fact](/2/do-experts-understand-whats-going-on-inside-ais).

As we discussed in Chapter 2, modern AIs are grown, rather than crafted. We may be able to look at the enormous pile of numbers that makes up an AI's brain, but that doesn't mean that we can usefully interpret those numbers and see what the AI is thinking.

Since late 2024 and the advent of "reasoning" models, there are parts of AIs' thoughts that at least *look* readable (the "reasoning traces"). And they are much more readable than whatever goes on inside the base model. But those logs are also [misleading](/2/but-some-ais-partly-think-in-english-doesnt-that-help), and there's ample places for an AI to hide thoughts that it'd rather we not see.

Furthermore, modern AIs are probably thinking pretty basic and shallow thoughts, compared to a superintelligence; the problem is only liable to get harder as AIs get smarter, and start thinking more and more thoughts that are less and less comprehensible to us.

Can you solve the problem by just using other AIs to monitor the AIs and make sure they stay on target? We doubt it.

If the brilliant human scientists who grow the AIs can't figure out what the AI is thinking, weak AIs will likely also have trouble doing so. And the sort of AI that *is* smart enough to do so is liable to be dangerous in its own right, and isn't likely to do exactly what you asked; there's a chicken-and-egg problem here.

#### We wouldn't know what to do if we caught one having dangerous thoughts.

Another flaw in this plan: Even if AI researchers *could* read an AI's mind well enough to catch the warning signs, what would they do when they saw one?

They could punish the offending AI, training it so that it stops setting off the "bad thought" detector. But that would not necessarily train the AI to stop having those thoughts, so much as to [hide its true thoughts from the detector](https://openai.com/index/chain-of-thought-monitoring/).

This problem is pernicious. The incentive that leads an AI to think about turning against humans to get what it wants is not a shallow aspect of temperament that can be massaged away. It's simply*true* that a mature AI would have preferences that differ from those of the operators; it's *true* that it would get more of what it prefers by subverting its operators.

The mechanisms in an AI that are good at noticing and exploiting real advantages in deep and general ways across a broad variety of domains are *also* liable to notice and exploit opportunities to subvert the AI's operators.

Even if you could build an alarm that goes off whenever an AI notices that its preferences and your preferences aren't lined up, the alarm does not tell you how to get an AI that deeply cares about good things. It's far easier to train an AI to fool your monitoring tools, or even to train the AI to fool *itself,* than it is to train it to actually prefer a future that's wonderful by human lights, especially in a way that's robust to the AI growing toward superintelligence.

If AIs were carefully and precisely designed using methods that are grounded in a developed and mature theory of intelligence, AI researchers might be able to set up the kinds of alarms that would help them notice flaws in their design and repair the design. But modern AIs aren't like that.

Modern AIs (at time of writing) are prone to "[hallucination](/2/dont-hallucinations-show-that-modern-ais-are-weak)," where they just make up answers to questions in a confident-sounding tone. But no AI engineer is anywhere near being able to understand exactly which mechanisms cause this. Similarly, nobody has anything like the comprehension or precision that would be required to reach into an AI and pull out just the hallucinating parts (if such a thing is even possible).

It would be [even harder](/3/smart-ais-spot-lies-and-opportunities#deep-machinery-of-steering) to reach in and pull out the "deceptive" parts of an AI.

If we're extremely lucky, the heroes working on AI interpretability will advance their field to the point where it's possible to set up some alarms that trigger in a fraction of the cases where AIs have a deceptive thought. But then what? When the alarm goes off, will everyone just stop? Or will profoundly thoughtless engineers retrain the AI until it learns to hide its thoughts better and the alarms stop going off?

Indeed, we (Yudkowsky and Soares) started working on the AI alignment problem beforeit was clear that gradient descent was going to become the dominant paradigm. Back in those days when nothing in AI was working at all, it seemed a decent bet that humanity would figure out how the heck intelligence works on the path to creating it, and *even then,* we expected the AI alignment problem to be difficult (for a variety of reasons, such as the ways that the AI would [change itself over time](/4/reflection-and-self-modification-make-it-all-harder). Reading the AI's thoughts would be one step back toward the slightly easier problem of aligning a mind that humans *did* understand, but only one step: Reading a mind is a far cry from understanding a mind in detail, or from knowing how to change it.

Reading the AI's thoughts is not a solution to the challenge. It's helpful, but it's not a solution. We don't think there *are* any feasible technological solutions that are accessible from where we stand today. Which means that humanity just needs to back off from the challenge.[*](#ftnt264)

See also: [Warning signs don't help if you don't know what to do with them.](/11/wont-there-be-early-warnings-researchers-can-use-to-identify-problems#warning-signs-dont-help-if-you-dont-know-what-to-do-with-them)

[*](#ftnt264_ref) We discuss this more in the final chapters of the book.