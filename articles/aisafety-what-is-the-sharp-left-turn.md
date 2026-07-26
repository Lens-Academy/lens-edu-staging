---
title: "What is the \"sharp left turn\"?"
author:
  - "Aisafety"
source_url: "https://aisafety.info/questions/9XPJ/What-is-the-sharp-left-turn"
published: 2026-07-18
created: 2026-07-18
accessed: 2026-07-18
description: "A sharp left turn (SLT) is a theorized scenario in which an AI’s capabilities generalize further than its alignment. In other words, if an AI went through a sharp left turn, its capabilities would quickly generalize outside the training distribution, but its alignment wouldn’t be able to keep up, resulting in a powerful misaligned model. This sc..."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A [sharp left turn](https://www.alignmentforum.org/w/sharp-left-turn) (SLT) is a theorized scenario in which an AI’s [capabilities generalize further than its alignment](https://www.alignmentforum.org/posts/GNhMPAWcfBCASy8e6/a-central-ai-alignment-problem-capabilities-generalization). In other words, if an AI went through a sharp left turn, its capabilities would quickly generalize outside the training distribution, but its alignment wouldn’t be able to keep up, resulting in a powerful misaligned model. This scenario depends on [three main claims](https://www.alignmentforum.org/posts/usKXS5jGDzjwqv3FJ/refining-the-sharp-left-turn-threat-model):

1.  **“Capabilities will generalize far (i.e., to many domains)”**

> An advance in capabilities could generalize in multiple domains, possibly at the same time or during a discrete phase transition.

2.  **“Alignment techniques that worked previously will fail during this transition”**

> The increase in capabilities and generalization would arise from emergent properties which would be qualitatively different from what the model used previously. As a result, alignment techniques that worked on old versions of the AI would not work on the new version.

3.  **“Humans won’t be able to intervene to prevent or align this transition”**

> The transition would happen too quickly for humans to notice or develop new alignment techniques in time.

If these claims are correct, we will end up with a misaligned AI. This could be avoided if we manage to build a [goal-aligned](https://www.lesswrong.com/posts/vix3K4grcHottqpEm/goal-alignment-is-robust-to-the-sharp-left-turn) AI before the SLT occurs; i.e., the AI should have beneficial goals and [situational awareness](https://www.lesswrong.com/w/situational-awareness-1#:~:text=Ajeya%20Cotra%20uses%20the%20term,continue%20to%20be%20influenced%20by). If this is the case, the AI will try to [preserve its beneficial goals](https://aisafety.info/questions/897I/What%20is%20instrumental%20convergence%3F) by developing new techniques to align itself as it goes through the SLT, and give rise to an aligned model post-SLT. You can read more about plans and caveats regarding the SLT [here](https://www.alignmentforum.org/posts/dfXwJh4X5aAcS8gF5/refining-the-sharp-left-turn-threat-model-part-2-applying).
