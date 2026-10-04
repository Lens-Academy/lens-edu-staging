---
title: "Comment on The case for ensuring that powerful AIs are controlled"
author:
  - "Richard Ngo"
source_url: "https://www.greaterwrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled/comment/2HZCnmo32ZX2Dmsxo"
published: 2024-01-27
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "I think there are (at least) two strong reasons to like this approach: 1. It’s complementary with alignment. 2.  It’s iterative and incremental. The frame where you need to just “solve” alignment is often counterproductive. When thinking about control you can focus on gradually ramping up from setups that would control human-level AGIs, to setups that would control slightly superhuman AGIs, to… As one example of this: as you get increasingly powerful AGI you can use it to identify more and more vulnerabilities in your code. Eventually you’ll get a system that can write provably secure code. Ofc that’s still not a perfect guarantee, but if it happens before the level at which AGI gets really dangerous, that would be super helpful."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Copying over a response I wrote on Twitter to Emmett Shear, who argued that “it’s just a bad way to solve the problem. An ever more powerful and sophisticated enemy? … If the process continues you just lose eventually”._

I think there are (at least) two strong reasons to like this approach:

1\. It’s complementary with alignment.

2\. It’s iterative and incremental. The frame where you need to just “solve” alignment is often counterproductive. When thinking about control you can focus on gradually ramping up from setups that would control human-level AGIs, to setups that would control slightly superhuman AGIs, to…

As one example of this: as you get increasingly powerful AGI you can use it to identify more and more vulnerabilities in your code. Eventually you’ll get a system that can write provably secure code. Ofc that’s still not a perfect guarantee, but if it happens before the level at which AGI gets really dangerous, that would be super helpful.

This is related to a more general criticism I have of the P(doom) framing: that it’s hard to optimize because it’s a nonlocal criterion. The effects of your actions will depend on how everyone responds to them, how they affect the deployment of the next generation of AIs, etc. An alternative framing I’ve been thinking about: the g(doom) framing. That is, as individuals we should each be trying to raise the general intelligence threshold at which bad things happen.

This is much more tractable to optimize! If I make my servers 10% more secure, then maybe an AGI needs to be 1% more intelligent in order to escape. If I make my alignment techniques 10% better, then maybe the AGI becomes misaligned 1% later in the training process.

You might say: “well, what happens after that”? But my point is that, as individuals, it’s counterproductive to each try to solve the whole problem ourselves. We need to make contributions that add up (across thousands of people) to decreasing P(doom), and I think approaches like AI control significantly increase g(doom) (the level of general intelligence at which you get doom), thereby buying more time for automated alignment, governance efforts, etc.
