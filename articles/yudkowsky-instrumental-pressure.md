---
title: "Instrumental pressure"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/w/instrumental-pressure"
published: 2015-12-17
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Saying that an agent will see 'instrumental pressure' to bring about an event E is saying that this agent, presumed to be a consequentialist with some goal G, will ceteris paribus and absent defeaters, want to bring about E in order to do G. For example, a paperclip maximizer, Clippy, sees instrumental pressure to gain control of as much matter as possible in order to make more paperclips. If we imagine an alternate Clippy+ that has a penalty term in its utility function for 'killing humans', Clippy+ still has an instrumental pressure to turn humans into paperclips (because of the paperclips that would be gained) but it also has a countervailing force pushing against that pressure (the penalty term for killing humans). Thus, we can say that a system is experiencing 'instrumental pressure' to do something, without implying that the system necessarily does it."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Saying that an agent will see 'instrumental pressure' to bring about an event E is saying that this agent, presumed to be a [consequentialist](https://www.lesswrong.com/w/consequentialist-cognition) with some goal G, will _ceteris paribus and absent defeaters,_ want to [bring about E in order to do G](https://www.lesswrong.com/w/instrumental). For example, a [paperclip maximizer](https://www.lesswrong.com/w/paperclip-maximizer), Clippy, sees instrumental pressure to gain control of as much matter as possible in order to make more paperclips. If we imagine an alternate Clippy+ that has a penalty term in its utility function for 'killing humans', Clippy+ still has an instrumental pressure to turn humans into paperclips (because of the paperclips that would be gained) but it also has a countervailing force pushing against that pressure (the penalty term for killing humans). Thus, we can say that a system is experiencing 'instrumental pressure' to do something, without implying that the system necessarily does it.

This state of affairs is different from the absence of any instrumental pressure: E.g., Clippy+ might come up with some clever way to [obtain the gains while avoiding the penalty term](https://www.lesswrong.com/w/nearest-unblocked-strategy), like turning humans into paperclips without killing them.

To more crisply define 'instrumental pressure', we need a setup that distinguishes [terminal utility and instrumental expected utility](https://www.lesswrong.com/w/instrumental), as in e.g. a utility function plus a causal model. Then we can be more precise about the notion of 'instrumental pressure' as follows: If each paperclip is worth 1 terminal utilon and a human can be disassembled to make 1000 paperclips with certainty, then strategies or event-sets that include 'turn the human into paperclips' thereby have their expected utility elevated by 1000 utils. There might also be a penalty term that assigns -1,000,000 utilts to killing a human, but then the net expected utility of disassembling the human is -999,000 rather than -1,000,000. The 1000 utils would still be gained from disassembling the human; the penalty term doesn't change that part. Even if this strategy doesn't have maximum EU and is not selected, the 'instrumental pressure' was still elevating its EU. There's still an expected-utility bump on that part of the solution space, even if that solution space is relatively low in value. And this is perhaps relevantly different because, e.g., there might be some clever strategy for turning humans into paperclips without killing them (even if you can only get 900 paperclips that way).

### Link from instrumental pressures to reflective instrumental pressures ^link-from-instrumental-pressures

If the agent is reflective and makes reflective choices on a consequentialist basis, there would ceteris paribus be a reflective-level pressure to _search_ for a strategy that makes paperclips out of the humans' atoms [without doing anything defined as 'killing the human'](https://www.lesswrong.com/w/nearest-unblocked-strategy). If a strategy like that could be found, then executing the strategy would enable a gain of 1000 utilons; thus there's an instrumental pressure to search for that strategy. Even if there's a penalty term added for searching for strategies to evade penalty terms, leading the AI to decide not to do the search, the instrumental pressure will still be there as a bump in the expected utility of that part of the solution space. (Perhaps there's some [unforeseen](https://www.lesswrong.com/w/cognitive-uncontainability) way to do something very like searching for that strategy while evading the penalty term, such as constructing an outside calculator to do it...)

### Blurring lines in allegedly non-consequentialist subsystems or decision rules ^blurring-lines-in-allegedly

To the extent that the AI being discussed is not a pure consequentialist, the notion of 'instrumental pressure' may start to blur or be less applicable. E.g., suppose on some level of AI, the choice of which questions to think about is _not_ being decided by a choice between options with calculated expected utilities, but is instead being decided by a rule, and the rule excludes searching for strategies that evade penalty terms. Then maybe there's no good analogy to the concept of 'an instrumental pressure to search for strategies that evade penalty terms', because there's no expected utility rating on the solution space and hence no analogous bump in the solution space that might eventually intersect a feasible strategy. But we should still perhaps [be careful about declaring that an AI subsystem has no analogue of instrumental pressures, because instrumental pressures may arise even in systems that don't look explicitly consequentialist](https://www.lesswrong.com/w/be-careful-about-declaring-that-an-ai-subsystem-has-no).
