---
title: "Comments on The Case Against AI Control Research"
author:
  - "Lucius Bushnaq"
source_url: "https://www.greaterwrong.com/posts/8wBN8cdNAv3c7vt6p/the-case-against-ai-control-research/comment/FpZmBx2Q4eswZWmy6"
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
description: "Note that I consider the problem of \"get useful research out of AIs that are scheming against you\" to be in scope for AI control research. We"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

-   > Note that I consider the problem of “get useful research out of AIs that are scheming against you” to be in scope for AI control research. We’ve mostly studied the “prevent scheming AIs from causing concentrated catastrophes” problem in the past, because it’s simpler for various technical reasons. But we’re hoping to do more on the “get useful research” problem in future (and [Benton et al](https://www.greaterwrong.com/posts/nnvn6kaBLajiicH8e/sabotage-evaluations-for-frontier-models) is an initial step in this direction). (I’m also excited for work on “get useful research out of AIs that _aren’t_ scheming against you”; I think that the appropriate techniques are somewhat different depending on whether the models are scheming or not, which is why I suggest studying them separately.)
    
    What would you say to the objection that people will immediately try to use such techniques to speed up ASI research just as much as they will try to use them to speed up alignment research if not more? Meaning they wouldn’t help close the gap between alignment research and ASI development and might even make it grow larger faster?
    
    If we were not expecting to solve the alignment problem before ASI is developed in a world where nobody knows how to get very useful research out of AIs, why would techniques for getting useful research out of AIs speed up alignment research more than ASI research and close the gap?
    
    -   I think this is a pretty general counterargument to any intervention that increases the space of options that AI developers have during the early singularity. Which isn’t to say that it’s wrong.
        
        In general, I think that it is a pretty good bet to develop safety methods that improve the safety-usefulness tradeoffs available when using AI. I think this looks good in all the different worlds I described [here](https://www.greaterwrong.com/posts/tmWMuY5HCSNXXZ9oq/buck-s-shortform#comment-TNFatFiqHd8BpAXEp).
        
        -   I am commenting more on your proposal to solve the “get useful research” problem here than the “get useful research out of AIs that are scheming against you” problem, though I do think this objection applies to both. I _can_ see a world in which misalignment and scheming of early AGI is an actual blocker to their usefulness in research and other domains with sparse feedback in a very obvious and salient way. In that world, solving the “get useful research out of AIs that are scheming against you” problem ramps economic incentives for making smarter AIs up further.
            
            I think that this is a pretty general counterargument to most game plans for alignment that don’t include a step of “And then when get a pause on ASI development somehow” at some point in the plan.
            
            -   Note that I don’t consider “get useful research, assuming that the model isn’t scheming” to be an AI control problem.
                
                AI control isn’t a complete game plan and doesn’t claim to be; it’s just a research direction that I think is a tractable approach to making the situation safer, and that I think should be a substantial fraction of AI safety research effort.
                
            -   I feel like I might be missing something, but conditional on scheming isn’t it differentially useful for safety because by default scheming AIs would be more likely to sandbag on safety research than capabilities research?
                
                -   That’s not clear to me? Unless they have a plan to ensure future ASIs are aligned with them or meaningfully negotiate with them, ASIs seem just as likely to wipe out any earlier non-superhuman AGIs as they are to wipe out humanity.
                    
                    I can come up with specific scenarios where they’d be more interested in sabotaging safety research than capabilities research, as well as the reverse, but it’s not evident to me that the combined probability mass of the former outweighs the latter or vice-versa.
                    
                    If someone has an argument for this I would be interested in reading it.
                    
                    -   I found some prior relevant work and tagged them in [https://www.lesswrong.com/tag/successor-alignment](https://www.lesswrong.com/tag/successor-alignment). I found the top few comments on [https://www.lesswrong.com/posts/axKWaxjc2CHH5gGyN/ai-will-not-want-to-self-improve#comments](https://www.lesswrong.com/posts/axKWaxjc2CHH5gGyN/ai-will-not-want-to-self-improve#comments) and [https://www.lesswrong.com/posts/wZAa9fHZfR6zxtdNx/agi-systems-and-humans-will-both-need-to-solve-the-alignment#comments](https://www.lesswrong.com/posts/wZAa9fHZfR6zxtdNx/agi-systems-and-humans-will-both-need-to-solve-the-alignment#comments) helpful.
                        
                        edit: another effect to keep in mind is that capabilities research may be harder to sandbag on because of more clear metrics.
                    
    -   Note that there are two problems Buck is highlighting here:
        
        1.  Get useful work out of scheming models that might try to sabotage this work.
            
        2.  Get useful research work out of models which aren’t scheming. (Where perhaps the main problem is in checking its outputs.)
            
        
        My sense is that work on (1) doesn’t advance ASI research except to the extent that scheming AIs would have tried to sabotage this research? (At least, insofar as work on (1) doesn’t help much with (2) in the long run.)
