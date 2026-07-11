---
title: "What Good Does Knowledge of LLMs Do?"
source_url: https://ifanyonebuildsit.com/2/what-good-does-knowledge-of-llms-do
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
What follows from understanding LLMs? How does it help us understand smarter-than-human AI and how to prevent everyone from dying?

One advantage it offers is that knowing concretely what goes on in there — at least the part we can see, the inscrutable numbers — can potentially feel more grounding, more solid, than if all you know is, "I woke up one day and the computers started talking for some reason."

As an example: Maybe if you know that the current LLMs are built by training only 1 percent as many parameters as a human brain contains synapses, it's easier to see why AI isn't going to sit at the current capability level forever.

When designing an international treaty to halt the race toward superintelligence, it helps to know that "training" an AI is a separate phase of its existence from *running* the AI (the latter is called "inference").

It also helps to know that the separation of these phases is a contingent and temporary fact about how *current* AI works, and that a future algorithm might change things. Today, you could write a treaty that separates its treatment of AI training and AI inference, but you'd have to be ready to change that theory if the algorithms changed.

Knowing that there is *an* algorithm in there is important, and so is seeing how, in some simple cases, it creates the properties of the AI that need to be regulated. If you understand the very basics of the algorithm, you are in a better place to hear about the sort of research that the AI industry is trying to do, and how that could affect the underlying rules if they're allowed to proceed.

The transformer algorithm, without which current AIs would not exist, was a large breakthrough developed by a handful of people at Google. The next breakthrough like that might or might not send AI past a [critical threshold](/1/will-ai-cross-critical-thresholds-and-take-off). It's easier to understand this if you have an idea of what a "transformer algorithm" does, how simple it is, and why it had such an impact on the field.

There is a lot of disinformation out there that relies on the listener not knowing how AI works. Some people will claim that humans understand what's going on in current AIs, when they don't. Some people will tell you that AIs could never be dangerous because they're "[just math](/2/arent-ais-just-math)," as if there were an impassable chasm separating AI cognition based on truly enormous amounts of "math" and human cognition based on enormous amounts of "biochemistry."

On July 8, 2025, Grok 3 started referring to itself as [MechaHitler](https://www.npr.org/2025/07/09/nx-s1-5462609/grok-elon-musk-antisemitic-racist-content). For some reason, the CEO of Twitter picked the following day to [resign](https://www.politico.com/news/2025/07/09/linda-yaccarino-x-ceo-resign-00443742).

In understanding what happened, it matters whether you think that Grok's builders deliberately instructed Grok to behave that way or whether you realize that AIs are "grown," and that AI developers have limited ability to control or predict their behavior.

It's bad in one way if Grok's builders created MechaHitler on purpose; it's bad in a different way if the builders got MechaHitler *by accident*, trying to push Grok in some (possibly unrelated) direction without the ability to predict the effects this would have on Grok's behavior.[\*](#ftnt66)

We hope that the information we've provided in *If Anyone Builds It, Everyone Dies* provides a useful bulwark against common misconceptions and misinformation. For readers who are interested in more details, below we will go through some of the history and [basic ideas](/2/obvious-insights-take-time) behind the recent AI boom, and provide a [detailed breakdown](/2/a-full-description-of-an-llm) of how a specific LLM works.

Is it enough? Some people have claimed that only those at the very cutting edge of current research could possibly know whether AIs (whether LLM-like or not) are likely to destroy humanity.

I (Yudkowsky) once attended a conference in Washington, DC for people working on "AI policy." While I was there, a couple of people approached me and asked if I could explain how transformers worked. "Well," I said, "that would be a lot easier with a whiteboard, but to try for a lay summary of what goes on in there, the key idea is that for each token it calculates queries, keys, and values —" and started to go on for some time, trying to phrase everything in beginner-friendly terms. Eventually, the two people managed to get a word in edgewise and explain that they were actually AI programmers. They had been going around to everyone at the conference, checking whether people who claimed to work in AI policy could explain how transformers worked. They told me that I was the only person so far who'd been able to answer.

I was a bit worried to hear this.

There is a valid question about how much it really matters to AI policy exactly how transformers work — how much the small details change anything about the larger picture.

*Does* somebody who works in AI policy need to understand query-key-value? To one frame of mind — to nerds for whom this sort of learning comes easily — of course you should learn it; it might be important. To this frame of mind, it feels weird and disturbing if someone at a conference says they work in AI policy but has no idea how transformers work.

More pragmatically, a few aspects of transformers and their history may be relevant to larger issues. For instance, the standard algorithm costs larger and larger amounts of computation as the AI tries to consider more and more "context" simultaneously — longer documents, larger codebases. You cannot just spend 10x the computing resources and get an AI that works on a 10x larger project; you need to be doing something clever for 10x the project size to cost less than 100x the compute.

It also matters to policy how long the transformer algorithm took to invent, how many people were required to invent it, and how complicated that algorithm is. History is a useful (if imperfect) guide to how much we might need to prepare for another big breakthrough like that. Similarly, it's relevant to AI policy how much of an improvement transformers represented over the previous technology ("recurrent neural networks") for processing text — because that sort of thing might also happen again.

Do you actually need to be able to sketch out the QKV matrices?

Probably not. We can, and in a group of dozens of people working on AI policy, we would feel more optimistic if at least one had the background required to do the same. It doesn't hurt to be sure; you never know what sort of important fact can end up lurking in a detail like that.

I (Yudkowsky) cannot sketch out from memory alone the details of a SwiGLU gate and how it differs from a GLU, because when I did look it up, the exact details there seemed to have no relevance to larger matters at all, so I didn't memorize them. But it might be informative to the novice that SwiGLU was found by a kind of blind testing, and that the paper authors said outright they have no idea why these techniques work in practice. We already knew about many cases like that, but if you *didn't* know that the people who come up with architectural improvements often say that they have no idea why it works, that's a relevant piece of information.

All of which adds up to: Knowing at least a little about how LLMs work is important so that you can see how little*anybody* knowsabout modern AI.

Sometimes, experts will pretend to have secret knowledge that can only be accessed by people who have worked for years at growing an AI. But they cannot name their knowledge, and the people writing papers say things like (to quote the paper introducing SwiGLU):

> We offer no explanation as to why these architectures seem to work; we attribute their success, as all else, to divine benevolence.

Sometimes, scientific experts know things that we don't know. But it is fairly rare in science for somebody to say, "I have terribly rare and rarefied knowledge which shows that what you say is incorrect, and you'll just have to take my word about that; I cannot possibly say what sort of experimental result or mathematical formula I know about that you don't."

You can imagine a world in which only the people paid seven-figure salaries for knowing how to set the learning schedule on a gradient descent optimizer should be listened to, a world in which only they are smart enough to have read about the key experiments and learned the key formulas to know that humanity would be perfectly safe from machine superintelligence, or to know that machine superintelligence can't be created for another 100 years. That kind of thing sometimes does happen in other fields of science! But when it does, the expert can usually point to some formula or experimental result and say, "This is the part that lay people don't understand." We cannot offhand recall a historical occasion where knowledge was claimed to be entirely inaccessible to a technically literate outside audience, and also that knowledge turned out to be true.

There may come a time when a representative of the AI industry slings an arm around your shoulder and insists that *they* understand what they're building, that it's all just numbers, that all will be well. It is useful, then, to know a little bit about the details of how AIs are grown, so that when someone makes this claim to you, you can ask them what makes them so sure.

[\*](#ftnt66_ref) In some cases, AI mishaps can result from interactions between both factors. For our purposes, the important point is that one key factor is "AIs behaving in ways the programmers never wanted or anticipated," even if there are sometimes other factors at play.

#### Notes

[1] *when they don't:* We discuss a few such people when answering [Do experts understand what's going on inside AIs?](/2/do-experts-understand-whats-going-on-inside-ais)