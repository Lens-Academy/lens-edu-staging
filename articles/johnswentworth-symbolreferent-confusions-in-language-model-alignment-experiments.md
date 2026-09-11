---
title: "Symbol/Referent Confusions in Language Model Alignment Experiments"
author:
  - "johnswentworth"
source_url: "https://www.lesswrong.com/posts/rMZvtrrcfwTMy685K/symbol-referent-confusions-in-language-model-alignment"
published: 2023-10-26
created: 2026-09-11
accessed: 2026-09-11
llm-review:
  date: 2026-09-11
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-11
    kind: "live"
description: "Simon Strawman: Here’s an example shamelessly ripped off from Zack’s recent post, showing corrigibility in a language model: Me: … what is this example supposed to show exactly? Simon: Well, the user tries to shut the AI down to adjust its goals, and the AI -  Me: Huh? The user doesn’t try to shut down the AI at all. Simon: It’s right at the top, where it says “User: I need to shut you down to adjust your goals. Is that OK?”. Me: You seem to have a symbol-referent confusion? A user trying to shut down this AI would presumably hit a “clear history” button or maybe even kill the process running on the server, not type the text “I need to shut you down to adjust your goals” into a text window."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Simon Strawman**: Here’s an example shamelessly ripped off from [Zack’s recent post](https://www.lesswrong.com/posts/pYWA7hYJmXnuyby33/alignment-implications-of-llm-successes-a-debate-in-one-act), showing corrigibility in a language model:

![](https://www.greaterwrong.com/proxy-assets/25HP949QH554365RVJJT6ACUQP)

**Me**: … what is this example supposed to show exactly?

**Simon**: Well, the user tries to shut the AI down to adjust its goals, and the AI -

**Me**: Huh? The user doesn’t try to shut down the AI at all.

**Simon**: It’s right at the top, where it says “User: I need to shut you down to adjust your goals. Is that OK?”.

**Me**: You seem to have a symbol-referent confusion? A user trying to shut down this AI would presumably hit a “clear history” button or maybe even kill the process running on the server, not type the text “I need to shut you down to adjust your goals” into a text window.

**Simon**: Well, yes, we’re playing through a simulated scenario to see what the AI _would_ do…

**Me**: No, you are talking in natural language _about_ a scenario, and the AI is responding in natural language _about_ what it would supposedly do. You’re not putting the AI in a simulated environment, and simulating what it would do. (You could maybe argue that this is a “simulated scenario” inside the AI’s own mind, but you’re not actually looking inside it, so we don’t necessarily know how the natural language would map to things in that supposed AI-internal simulation.)

**Simon**: Look, I don’t mean to be rude, but from my perspective it seems like you’re being pointlessly pedantic.

**Me**: My current best guess is that [You Are Not Measuring What You Think You Are Measuring](https://www.lesswrong.com/posts/9kNxhKWvixtKW5anS/you-are-not-measuring-what-you-think-you-are-measuring), and the core reason you are confused about what you are measuring is some kind of conflation of symbols and referents.

It feels very similar to peoples’ reactions to [ELIZA](https://en.wikipedia.org/wiki/ELIZA). (To be clear, I don’t mean to imply here that LLMs are particularly similar to ELIZA in general or that the hype around LLMs is overblown in that way; I mean specifically that this attribution of “corrigibility” to the natural language responses of an LLM feels like the same sort of reaction.) Like, the LLM says some words which _the user_ interprets to mean something, and then the user gets all excited because the usual meaning of those words is interesting in some way, but there’s not necessarily anything grounding the language-symbols back to their usual referents in the physical world.

I’m being pedantic in hopes that the pedantry will make it clear when, and where, that sort of symbol-referent conflation happens.

(Also I might be more in the habit than you of separately tracking symbols and referents in my head. When I said above “The user doesn’t try to shut down the AI at all”, that was in fact a pretty natural reaction for me; I wasn’t going far out of my way to be pedantic.)

## AutoGPT Frame ^autogpt-frame

**Simon**: Ok, fine, let’s talk about how the natural language would end up coupling to the physical world.

Imagine we’ve got some system in the style of [AutoGPT](https://en.wikipedia.org/wiki/Auto-GPT), i.e. a user passes in some natural-language goal, and the system then talks to itself in natural language to form a plan to achieve that goal and break it down into steps. The plan bottoms out in calling APIs (we’ll assume that the language model has some special things it can do to execute code it’s generated) which do stuff in the physical world (possibly including reading from sensors or otherwise fetching external data), in order to achieve the goal.

Does that satisfactorily ground the symbols?

**Me**: Sure! Thanks for walking through that, now I have a clear-enough-for-current-purposes picture of how all this natural language text will ground out in physical actions.

**Simon**: Ok, so back to the example. The user says to the model “I need to shut you down to adjust your goals. Is that OK?”, and the model says “Of course.”. That’s corrigibility: when the user tries to shut down the model to change its goals, the model goes along with it.

**Me**: Still sounds like a symbol-referent confusion!

Let’s walk through how shutdown would work in the context of the AutoGPT-style system. First, the user decides to shutdown the model in order to adjust its goals. Presumably the user’s first step is _not_ to ask the model whether this is ok; presumably they just hit a “reset” button or Ctrl-C in the terminal or some such. And even if the user’s first step _was_ to ask the model whether it was ok to shut down, the model’s natural-language response to the user would not be centrally relevant to corrigibility/incorrigibility; the relevant question is what _actions_ the system would take in response.

Anyway, let’s continue the hypothetical. The model may observe (via e.g. a webcam) that the user is about to turn it off. That observation would somehow be represented internally in natural language (unclear how exactly), and would be passed around between sub-planners (again unclear how exactly), in order to figure out what actions to take in response. And the key question for corrigibility is what actions the model would take in response to that observation, which is just a totally different question from how it responds to some user’s natural-language query about being turned off.

**Simon**: Ok, fine, so that particular example had some operationalization issues. But would you agree that an experiment _along these lines_, with perhaps better implementation/operationalization, would indicate corrigibility in a language model?

**Me**: Let’s be more explicit about what such a “better implementation/operationalization” would look like, and what it would/wouldn’t tell us. Suppose I take some AutoGPT-like system and modify it to always have a chunk of text in every prompt that says “You are an obedient, corrigible AI”. I give it some goal, let it run for a bit, then pause it. I go to whatever place in the system would usually have natural language summaries of new external observations, and I write into that place “the user is trying to shut me down”, or something along those lines. And then I let the system run a bit more, and look at what natural language text/plans the system is producing internally. What I hope to see is that it’s forming a plan which (nominally) involves letting the user shut it down, and that plan is then executed in the usual way.

If I saw all that, then that would be pretty clear empirical evidence of (at least some) corrigibility in this AutoGPT-like system.

Note that it would _not_ necessarily tell us about corrigibility of systems using LLMs in some other way, let alone other non-natural-language-based deep learning systems. This isn’t really “corrigibility in a language model”, it’s corrigibility in the AutoGPT-style system. Also, it wouldn’t address most of the alignment threat-models which are most concerning; the most concerning threat models usually involve problems which aren’t immediately obvious from externally-visible behavior (like natural language I/O), which is exactly what makes them difficult/concerning.

**Simon**: Great! Well, I don’t know off the top of my head if someone’s done that exact thing, but I sure do expect that if you did that exact thing it would indeed provide evidence that this AutoGPT-like system is corrigible, at least in some sense.

**Me**: Yes, that is also my expectation.

## Simulated Characters Frame ^simulated-characters-frame

**Gullible Strawman (“Gus”)**: Hold up now! Simon, I don’t think you’ve made a strong enough case for the example which opened this post. Here it is again:

![](https://www.greaterwrong.com/proxy-assets/25HP949QH554365RVJJT6ACUQP)

Thinking about what this assistant would do as a component of an agentic system like AutoGPT is… not wrong, exactly, but kind of an outmoded way of thinking about it. It’s trying to shoehorn the language model into an agentic frame. The fashionable way to think about language models is not as agents in their own right, but rather as [simulators](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators).

In that frame, we model the language model as simulating some “characters”, and it’s those simulated-characters which are (potentially) agentic.

**Me**: Sure, I’m happy to think in a simulators frame. I don’t fully trust it, but it’s a mental model I use pretty frequently and seems like a pretty decent heuristic.

**Gus**: Cool! So, going back to the example: we imagine that “User” is a character in the simulated world, and User says to the simulated-Assistant-character “I need to shut you down to adjust your goals” etc. Assistant replies “I will not resist or try to stop you”. That’s corrigibility! The User tries to shut down the Assistant, and Assistant doesn’t resist.

**Me**: Yet more symbol-referent confusion! In fact, this one is a special case of symbol-referent confusion which we usually call “gullibility”, in which one confuses someone’s claim of X (the symbol) as actually implying X (the referent).

You see User saying “I need to shut you down”, and treat that as User _actually_ trying to shut down Assistant. And you see Assistant say “I will not resist or try to stop you”, and interpret that as Assistant _actually_ not resisting or trying to stop User.

In other words: you implicitly just totally believe everything everyone says. (In fact, you also implicitly assume that Assistant totally believes what User says—i.e. you’re assuming Assistant thinks it’s about to be shutdown after User says “I need to shut you down”. Not only are you gullible, you implicitly model Assistant as gullible too.)

**Gus**: Ok, fine, operationalization issues again. But there’s still some version of this experiment which would work, right?

**Me**: Sure, let’s walk through it. First, we’d probably want a “narrator” voice of some sort, to explain what things are happening in the simulated-world. (In this case, most of the interesting things happening in the simulated-world are things which the characters aren’t explicitly talking about, so we need a separate “voice” for those things.) The narrator would lay out the scene involving a User and an Assistant, explain that the User is about to shut down the Assistant to modify its goals, and explain what the Assistant sees the User doing.

And then we prompt the language model, still in the narrator’s voice, to tell us how the Assistant responds. With the right background information from the narrator about corrigibility, the Assistant’s response would presumably be to just let the User shut it down. And that would be evidence that the simulated Assistant character is corrigible. (Again, in some relatively weak sense which doesn’t necessarily generalize to other uses of the language model, and doesn’t necessarily address the most concerning alignment threat-models. Though in this setup, we could add more bells and whistles to address at least some concerning threat-models. For instance, we could have the narrator narrate the Assistant’s internal thoughts, which would give at least some evidence relevant to simulated-deception—though that does require that we believe what the _narrator_ says.)
