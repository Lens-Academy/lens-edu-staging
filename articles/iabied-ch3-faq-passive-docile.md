---
title: "Can we just train AIs to be more passive and docile?"
source_url: https://ifanyonebuildsit.com/3/can-we-just-train-ais-to-be-more-passive-and-docile
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

#### Passivity is in tension with usefulness.

Could developers make their AIs *passive*? A screwdriver doesn't go on turning screws when you put it down. Similarly, we could imagine developers trying to make AIs that do exactly what you ask for and no more — that take no extra initiative and do no extra work.

It doesn't look easy. Many humans who seem "lazy" perk up and grab lots of resources when they're playing a board game. And most of those people don't have the *option* to win themselves a billion dollars via efforts that feel easy. Most lazy-seeming humans don't have the *option* to cheaply spin up servants that are much smarter and more driven, and that cater to their needs.

Those absent options reflect a lack of capability, not a fundamental disinterest. If they became far smarter, such that those options became available and easy for them, would they take them? After Chapter 5 we'll come back to this point, in an [extended discussion](/5/its-hard-to-get-robust-laziness) of why robust laziness looks like a difficult target to hit.

Even if it were possible to make AIs that are both smart and passive, passivity is in tension with usefulness. There have been AIs that [act a bit lazy](https://arstechnica.com/information-technology/2023/12/is-chatgpt-becoming-lazier-because-its-december-people-run-tests-to-find-out/). The AI labs retrained them to push harder. More difficult challenges — like developing medical cures — require AIs that take more and more initiative, and so AI labs will train them to take more and more initiative. It's difficult to disentangle a propensity for *useful work* from a propensity for *perseverance*, and it becomes more difficult as the tasks we give AIs become harder and more complicated.

#### We can't robustly train any specific temperament into AIs.

Because AIs are grown and not crafted, engineers can't just change an AI's behavior to make it more obedient or more tool-like. Nobody has that sort of control.

Corporations certainly *try*. AI companies' attempts to improve their products' behavior have caused some embarrassing incidents. xAI's AI Grok started calling itself "[MechaHitler](https://www.npr.org/2025/07/09/nx-s1-5462609/grok-elon-musk-antisemitic-racist-content)" after its system prompt was adjusted with new instructions to "not shy away from making claims which are politically incorrect, as long as they are well substantiated." Google's Gemini AI started [producing pictures of racially diverse Nazis](https://www.theverge.com/2024/2/21/24079371/google-ai-gemini-generative-inaccurate-historical), likely in response to instructions to portray diversity.

The people building AIs don't have fine-grained control over how they behave. All they have is the ability to point AIs in directions like "Don't shy away from politically incorrect claims" or "Portray diversity" and hope that the result lands in the neighborhood they had in mind. These instructions have all sorts of tangled effects, often unintended.

Growing an AI is an opaque and expensive process. Engineers don't know what they'll get when they reach their hand into the barrel ([a liar? a cheater? a sycophant?](https://thezvi.substack.com/p/ai-114-liars-sycophants-and-cheaters)), but they can only afford so many draws. They have to take what they get.

It would be possible *in theory* to build an AI that only ever served as an extension of the user's will, but that would be a delicate and difficult challenge (as we'll discuss [later](/5/intelligent-usually-implies-incorrigible) in an extended discussion on the difficulties of making a "corrigible" AI). Passivity is in tension with usefulness.

It would be similarly difficult to make an AI that's capable of completing long-term tasks on its own initiative but only ever uses that initiative exactly as the user intended. Meanwhile, modern AI developers are at the level of control where they poke at AIs and accidentally get MechaHitler or racially inclusive Nazis. They aren't anywhere close to the level of ability they'd need to make an AI that was useful but not driven.

This is the topic we'll turn to next, in Chapter 4.