---
title: "Why it's hard to make settings for high-stakes control research"
author:
  - "Buck Shlegeris"
source_url: "https://blog.redwoodresearch.org/p/why-its-hard-to-make-settings-for"
published: 2025-07-18
created: 2026-09-09
accessed: 2026-09-09
llm-review:
  date: 2026-09-09
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-09
    kind: "live"
description: "It's like making challenging evals, but more constrained"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

One of our main activities at Redwood is writing follow-ups to previous papers on control like [the original](https://arxiv.org/abs/2312.06942) and [Ctrl-Z](https://arxiv.org/abs/2504.10374), where we construct a setting with a bunch of tasks (e.g. APPS problems) and a notion of safety failure (e.g. backdoors according to our specific definition), then play the adversarial game where we develop protocols and attacks on those protocols.

It turns out that a substantial fraction of the difficulty here is developing the settings, rather than developing the protocols and attacks. I want to explain why this is the case.

In order to do high-stakes control research, you need a dataset of tasks with the following properties:

-   You can check whether the main task was completed successfully.
    
-   There's some notion of safety failure that we consider unacceptable; we can check whether a safety failure occurred. (We sometimes call these safety failures "side tasks".)
    

Here's why it's challenging to develop settings that work.

-   Focusing entirely on the main tasks to start with: we need a dataset of tasks such that frontier models are reasonably competent at them, but weaker models do much worse.
    
    -   We need weaker models to do much worse on these tasks because we want to rule out protocols that just use the trusted model; we think this is more representative of particularly risky deployments in the future. You could satisfy this requirement by choosing a model to trust that is much weaker than your untrusted model. But weaker models have more trouble following basic instructions, so if you do this you can’t study some promising protocols.
        
    -   So we're already in the difficult position of needing tasks that the models haven't already saturated. Datasets that LLMs haven't saturated are increasingly difficult to construct.
        
    -   It's also hard to get LLMs to build datasets that are hard enough that they aren't saturated, because the settings are (almost definitionally) complicated enough that the AIs struggle to construct them.
        
    -   Relatedly, in many contexts it's hard to get the AIs to evaluate whether the problems were done correctly. (I expect that asymptotically, verification is easier than generation, but this often isn't true for non-saturated tasks at current capability levels, especially once you have the AI iterating against its own attempt at verification.)
        
    -   (We need a robust measure of task success because we optimize against that metric while developing protocols. In the simple control strategy of trusted monitoring with auditing, changes to the monitor never affect task success rates so you don't need a robust metric. But I suspect that protocols that affect main task success rate will be crucial in practice.)
        
-   The need for side tasks makes the situation harder.
    
    -   The adversarial research process optimizes against our definition of side task success, because obviously the attack policy is more able to successfully execute actions that look less bad. So for example, if you tried to use a definition like "inserts a security vulnerability", the red team is strongly incentivized to look for the weakest security vulnerabilities that possibly count. (In Ctrl-Z and the original paper, we avoided this by having objective definitions for side task success.)
        
    -   It's sad if the side task requires an affordance that the agent doesn't actually need for its tasks, because the blue team is incentivized to flag any use of that affordance. (This was true in Ctrl-Z: the side task involved interacting with the internet, but few of the main tasks required internet access, and those that did didn't require access to a broad set of domains. So techniques where the model was explicitly required to state when a command needed to be run with network access would probably have substantially quantitatively affected the results.)
        
    -   One strategy you could try to use is to have the side task vary arbitrarily between different main tasks. For example, in [SHADE-Arena](https://www.anthropic.com/research/shade-arena-sabotage-monitoring), each main task (e.g. sorting out a bunch of receipts and then sending money between friends to settle debts after a group vacation) is paired with a side task (in that case, embezzling money to an arbitrary PayPal account). The attack policy is magically informed of the side task for each trajectory, but the protocol isn’t. This is fundamentally unrealistic. It makes sense for the attack policy to know things about opportunities to attack that the protocol doesn’t have access to, but it’s artificial to give the attack policy the information about a side task on that particular trajectory, and this means you can’t explore protocols that make use of instances of the untrusted model that have been given very small subtasks that don't give them enough context to know what side task they’re aiming for.
        
        -   This also makes research methodology much harder. For example, it's hard to know whether your blue-team strategies are performing better because they're actually better or because you've slowly been leaking bits about the side task definition by iterating against it.
            
    -   It's much nicer to do research if the AI is coming up with the ideas for the attacks itself, rather than just using attacks suggested by the researchers. This is better because it is closer to doing a capability evaluation of the untrusted model and also because it reduces overfitting problems.
        

To make the situation more challenging, we have preferences over the kinds of domains we study. Because my main concern is AIs misusing their access to compute and proprietary models while doing ML R&D, I'm most interested in settings where the AIs are doing software engineering or using computers for tasks similar to those done by researchers in AI companies.

When we were writing the first paper in the APPS setting, I did not appreciate how much harder it would be to construct settings for subsequent projects. And I really messed up by not putting more emphasis on this at the start of the Ctrl-Z project.

Incidentally, I don't think that we can easily satisfy these desiderata by trying to apply control in current real applications of AI agents. Realistically, AIs right now are not given very much autonomy (mostly because they can't use it productively) or very much access to dangerous resources. So current deployments don't provide us with example trajectories that have that much in common with the situations I'm worried about later. (I think that studying AI-control-like techniques in real deployments is a promising project for researchers inside AI companies, but mostly because I think it helps prepare the organization for implementing similar techniques later, not because it is a good path to directly learning about how to use these techniques to mitigate insider risk from schemers.)
