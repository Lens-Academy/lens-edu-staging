---
title: "Plan A FAQ"
author:
  - "AI 2040"
source_url: "https://ai-2040.com/supplements/faq"
published: 2026-09-05
created: 2026-09-05
accessed: 2026-09-05
llm-review:
  date: 2026-09-05
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-05
    kind: "live"
description: "A detailed forecast and recommendation for how the US, China and the rest of the world should navigate superintelligence."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Q: Isn’t Plan A bad for concentration of power risks?**

A: No, Plan A reduces COP risks by a lot. The status quo involves an insane amount of power concentrating into the frontier AI companies (which are all based in the US). If they solve the alignment problem, the result will be a handful of AI CEOs or USG officials controlling an army of superintelligences, and hence having the ability to take over the world. (This is what happened in the slowdown ending of AI 2027).

Plan A dramatically improves on the status quo by:

1.  Increasing the number and diversity of frontier AI companies. Because of regulations slowing the frontier, trailing actors can catch up, and in the Plan A scenario, by 2040, there are dozens of companies across different countries near the frontier of AI development.
    
2.  Increasing the transparency and visibility into AI development. A core dynamic driving concentration of power risks is a dynamic where most of the power centers in the world do not realize they are going to be disempowered by AI until it is too late. In Plan A, the takeoff period is much longer and much more transparent, so the public, the US government, and countries besides the US all have much more time to see what is going on inside the labs.
    
3.  Spreading out the AI-driven transformation of the planet over a few more years, giving more time for everyone to prepare and react, making it more likely that something resembling our current system of checks and balances persists instead of crumbling into chaotic conflict.
    
4.  Decreasing the feasibility of inserting secret loyalties into AI systems. There is high quality compute accounting, so it is no longer feasible for anyone to obtain hidden compute, which could be used to train a backdoor into the AIs.
    

**Q: Wouldn’t China not agree to the deal? Even if they did agree on paper, wouldn’t they defect and keep developing AI anyways?**

A: China is likely to want something along the lines of Plan A because the status quo outcome for China is that they will be outcompeted by US AI companies. This will result in either misaligned AIs taking over the world, or the US obtaining a decisive lead in AI capabilities sufficient to disempower China. (These two options correspond to the race and slowdown endings of AI 2027 respectively). The CCP today does not seem very aware of the importance of AGI or ASI, but this will change as AI has bigger and bigger impacts on the world.

The question isn’t “Will China defect from the deal?” The question is, “What’s the biggest defection they could get away with, and how bad would that be?”

There are two ways of defecting from the deal: (1) building a massive covert project that you attempt to keep hidden from the rest of the world, and (2) using the existing legal compute.

![](https://ai-2040.com/supplements/faq/image1.png)

A baseline estimate for the maximum size of covert project that they could have is ~1.2M H100e. We do a more thorough analysis of this question in [our covert project supplement](https://ai-2040.com/supplements/covert-ai-projects), and we have a branch of our scenario gaming out how China could defect.

We prevent the use of existing legal compute through training verification mechanisms. We assume US and Chinese auditors are given full transparency into the other’s R&D datacenters, allowing them to check if the compute is being used how they claim it is being used. We do a more thorough analysis of this question in our [verification supplement](https://www.ai-2040.com/supplements/verification-plan).

**Q: Isn’t Total Research Transparency bad because it leaks algorithmic secrets to China and other AI companies?**

No current AI companies claim to be secure against nation state level adversaries. They aren’t secure even for model weights, which are much easier to secure than algorithmic secrets because model weights are large, often on the order of 1-10TB, while algorithmic secrets are often memorizable by individual humans. Because AI algorithms will have already leaked to competing nations, the costs of full transparency here are relatively low compared to the enormous benefits.

**Q: Plan A is complicated. Shouldn’t we do a simpler and more straightforward plan, like shutting it all down (Plan S)?**

Our proposed implementation of Plan A is very complicated, and even a good implementation will incur significant existential risk. However, all simpler plans that we are aware of would incur even more risk than Plan A. In particular the main issue with Plan S is that it does worse than Plan A at making forward progress towards solving the safety/alignment problems that prevent further capability scaling, because we are shut down at an earlier capability level. This is bad because at some point, both Plan A and Plan S will break down and return to racing, and in Plan S, much less alignment progress will have been made by this point. That said, we are very sympathetic to Plan S and could imagine being convinced that some version of it is better after all.

**Q: The US government is incompetent. Why are we trusting the US government to do a good job regulating AI?**

For any plan, incompetent execution of that plan is a serious concern. We are in fact very worried about incompetent execution of Plan A, and so we wrote a [branch of our scenario explaining how this could lead to existential catastrophe](https://ai-2040.com/?choices=plan-a-root#branchpoint-flawed-safety-case-is-approved).

Who else is going to regulate AI, if the US government doesn’t? We don’t trust the industry to self-regulate effectively. Moreover, if the US government is kept in the dark while AI companies race through an intelligence explosion, that seems like an unstable situation that could lead to sudden wakeup and thrashing about, or worse, a US company effectively puppetting the government (as hinted at in the [AI 2027 slowdown ending](https://ai-2027.com/slowdown)). If the US government is not in the dark, they will want to regulate AI, and we are trying to figure out and describe what good regulation would look like.

Large parts of Plan A are designed to improve the AI-related competence of the government—and the wider world—as fast as possible. For example, this is part of why we recommend [Total Research Transparency](https://www.ai-2040.com/supplements/transparency-plan) instead of some more moderate kind of transparency. This is also part of why we recommend limiting the rate of AI progress; it gives the world more time to react and prepare for each new level of capability. We also have things to say about [using AI to improve epistemics](https://ai-2040.com/supplements/ai-for-epistemics), and about immediate actions the government could take to improve its understanding of AI and capacity to regulate effectively. Finally, a big motivation for Plan A is to prevent extreme concentrations of power, which is good in its own right but also helps mitigate government incompetence.

**Q: Plan A just isn’t going to happen. Don’t you know that?**

The Plan A scenario is a recommendation, not a forecast; it is _not_ what we expect to happen. We think many of the ideas in AI 2040 are good and will be helpful inspiration for people trying to steer things in a better direction, even if Plan A doesn’t happen. That said, we also think that Plan A is plausible enough that it is worthwhile to push for it.

Over just the last year, there has been a massive shift in the awareness and understanding of AI among policymakers. As the effects of AI get larger, there will be vastly more wakeup. Before the point of no return—the point at which AIs or AI-powered humans can disempower the rest of the world—AI will probably have transformative effects on the world. It’s hard to be confident in any specifics, but some illustrative possibilities include:

-   AIs can automate the majority of all jobs: physical jobs with robots, cognitive jobs with AI agents running in the cloud. This leads to massive widespread unemployment.
    
-   Extreme economic impacts other than unemployment. For example, perhaps AI companies will continue increasing their revenue at ~3x/year until 2030, which would mean that the frontier AI companies would have a $10T/year revenue. This is an unprecedented amount of wealth and power in a company, and will trigger alarm bells.
    
-   AIs completely change the nature of warfare. For example, AI piloted drone swarms may render existing mechanized militaries (e.g. infantry, tanks, planes, aircraft carriers) completely obsolete. This might lead to significant changes in the geopolitical balance of power as countries who aren’t at the AI frontier will fall behind militarily.
    
-   Extreme misuse capabilities, e.g. suppose it’s the case that AIs are able to cheaply design and spread bioweapons with commonly accessible materials. Hardening the world against these capabilities will be extremely difficult.
    

It’s hard to know what the political environment will look like after AI has massive effects on the world. The main question is how early transformative effects on the world happen relative to AI-caused permanent lock in. Plan A is much easier and more effective if implemented early—before the AIs have fully automated the AI R&D process.
