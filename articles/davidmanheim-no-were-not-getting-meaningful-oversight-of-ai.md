---
title: "No, We're Not Getting Meaningful Oversight of AI"
author:
  - "Davidmanheim"
source_url: "https://www.lesswrong.com/posts/25dsPH6CuRXPBkGHN/no-we-re-not-getting-meaningful-oversight-of-ai"
published: 2025-07-09
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "Note: this is a linkpost for a new paper. …"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

This is a linkpost for [https://arxiv.org/abs/2507.03525](https://arxiv.org/abs/2507.03525)

Note: this is a linkpost for [a new paper](https://arxiv.org/abs/2507.03525).  
  
One of the most common (and comfortable) assumptions in AI safety discussions—especially outside of technical alignment circles—is that _oversight_ will save us. Whether it's a human in the loop, a red team audit, or a governance committee reviewing deployments, oversight is invoked as the method by which we’ll prevent unacceptable outcomes.

It shows up everywhere: in policy frameworks, in corporate safety reports, and in standards documents. Sometimes it’s explicit, like the EU AI Act saying that High-risk AI systems must be subject to human oversight, or stated as an assumption, as in [a Deepmind paper also released yesterday](https://deepmindsafetyresearch.medium.com/evaluating-and-monitoring-for-ai-scheming-d3448219a967), where they say that scheming won't happen because AI won't be able to evade oversight. Other times it’s implicit, firms claiming that they are mitigating risk through regular audits and fallback procedures, or arguments that no-one will deploy unsafe systems in places without sufficient oversight.

But either way, there’s a shared background belief: **that meaningful oversight is both possible, and likely or happening already.**

In a new paper with Aidan Homewood, ["Limits of Safe AI Deployment: Differentiating Oversight and Control,"](https://arxiv.org/abs/2507.03525) we argue, among other things, that both parts of this belief are often false. Where meaningful oversight is possible, it isn't present, and in many cases, it's not even possible.

So AI developers need to stop waving “oversight” around as a magic word. If you’re going to claim your AI system is supervised, we propose that it needs to be documented, instead of a hand-wavy claim. That means that the developers and deployers need to explain what is happening, in detail.

-   What kind of supervision it is (control vs. oversight),
-   What risks it addresses,
-   What its failure modes are, and
-   Why it will actually work.

If you can’t do that, you don’t have oversight. You have a story. And stories don't stop disasters.
