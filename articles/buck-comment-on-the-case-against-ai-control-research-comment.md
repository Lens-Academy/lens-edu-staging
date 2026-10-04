---
title: "Comment on The Case Against AI Control Research"
author:
  - "Buck Shlegeris"
source_url: "https://www.greaterwrong.com/posts/8wBN8cdNAv3c7vt6p/the-case-against-ai-control-research/comment/Jmbyoe3DTZhQMkfKy"
published: 2025-01-21
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "Thanks John, I think that this is a reasonable articulation of the main limitations of AI control as I"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Thanks John, I think that this is a reasonable articulation of the main limitations of AI control as I’ve described it. But I find it very unconvincing as an argument that AI control should be less than, say, 20% of total research effort on safety.

My central crux is that **preventing scheming early transformative AIs from succeeding at extreme subversion (e.g. escaping or massively sabotaging research due to scheming) seems quite robustly good for reducing AI risk**. I think this problem is important enough that it deserves a substantial share of AI safety research and implementation effort. I think that my stance here is pretty common-sensical, and to some extent I feel like there’s a burden of proof on skeptics to argue that scheming early transformative AI _isn’t_ a problem, that we should just ignore anything that goes wrong as a result of them intentionally trying to subvert us.

I haven’t really justified a quantitative estimate of the importance of this in detail anywhere, both because I think it’s pretty intuitively defensible, and also because it’s pretty complicated to talk about: it requires forecasting detailed dynamics of the development of powerful AI (e.g. you have to argue about whether escaped scheming AIs might force AI developers to build uncontrollable superintelligences in cases where they otherwise wouldn’t have, etc).

Note that I consider the problem of “get useful research out of AIs that are scheming against you” to be in scope for AI control research. We’ve mostly studied the “prevent scheming AIs from causing concentrated catastrophes” problem in the past, because it’s simpler for various technical reasons. But we’re hoping to do more on the “get useful research” problem in future (and [Benton et al](https://www.greaterwrong.com/posts/nnvn6kaBLajiicH8e/sabotage-evaluations-for-frontier-models) is an initial step in this direction). (I’m also excited for work on “get useful research out of AIs that _aren’t_ scheming against you”; I think that the appropriate techniques are somewhat different depending on whether the models are scheming or not, which is why I suggest studying them separately.)

Some other nitpicks:

-   At the risk of vagueness: I think that AI control techniques probably reduce risks when applied to models that are “moderately superintelligent”, whatever that means. Like, I don’t think they’re literally only applicable to models that aren’t superintelligent at all.
    
-   As we’ve discussed before, some non-scheming threat models do seem like they’d be addressed by control as a special case.
