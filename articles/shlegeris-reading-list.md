---
title: "Reading List"
author:
  - "Buck Shlegeris"
source_url: "https://blog.redwoodresearch.org/p/guide"
published: 2025-07-10
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "(Last updated Jul 28th 2025)"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[[#^1-key-ideas-in|Section 1]] is a quick guide to the key ideas in AI control, aimed at readers who want to get up to speed as quickly as possible.

[[#^2-extensive-guide|Section 2]] is an extensive guide to almost all of our writing on AI risk, aimed at those who want to gain a deep understanding of Redwood’s worldview.

## 1\. Key Ideas in AI Control ^1-key-ideas-in

## Papers and blog posts ^papers-and-blog-posts

### Foundational content ^foundational-content

-   **[The case for ensuring that powerful AIs are controlled](https://redwoodresearch.substack.com/p/the-case-for-ensuring-that-powerful)** (Buck Shlegeris and Ryan Greenblatt, May 2024): This is our original essay explaining why we think AI control is a valuable research direction.
    
-   **[AI Catastrophes And Rogue Deployments](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)** (Buck Shlegeris, Jun 2024): We often refer to rogue deployments when talking about what AI control aims to prevent.
    
-   **\[external\] [Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379)** (Joe Carlsmith, Nov 2023): Read this for the current state of the art on arguments for why your models might end up conspiring against you. This is long; you might want to just read the first section, which summarizes the whole report.
    

### Examples of empirical research ^examples-of-empirical-research

-   **[AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942)** (Ryan Greenblatt et al., Dec 2023): This was the original paper on control.
    
-   **[Ctrl-Z: Controlling AI Agents via Resampling](https://redwoodresearch.substack.com/p/ctrl-z-controlling-ai-agents-via)** (Aryan Bhatt et al., Apr 2025): This is the sequel to the original control paper. Here, we study high-stakes failures in an agent setting.
    

### In-depth analyses of threat models and countermeasures, and implications for control methodology ^in-depth-analyses-of-threat

-   **[Win/continue/lose scenarios and execute/replace/audit protocols](https://redwoodresearch.substack.com/p/wincontinuelose-scenarios-and-executereplaceaudi)** (Buck Shlegeris, Nov 2024): The basic mathematical ideas of this post are crucial for thinking quantitatively about the main problems with using AI control to prevent security failures.
    
-   **[Thoughts on the conservative assumptions in AI control](https://redwoodresearch.substack.com/p/thoughts-on-the-conservative-assumptions)** (Buck Shlegeris, Jan 2025): This describes some of the ways that most of our control work is conservative, and explains why we usually choose to do the research that way.
    
-   **[How to prevent collusion when using untrusted models to monitor each other](https://redwoodresearch.substack.com/p/how-to-prevent-collusion-when-using)** (Buck Shlegeris, Sep 2024): This gets into a lot of detail about some important points about untrusted monitoring, a promising control technique.
    
-   **[Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking](https://redwoodresearch.substack.com/p/misalignment-and-strategic-underperformance)** (Julian Stastny and Buck Shlegeris, May 2025): Sandbagging and exploration hacking are fundamental issues which often come up when reasoning about AI control measures.
    
-   **[How can we solve diffuse threats like research sabotage with AI control?](https://redwoodresearch.substack.com/p/how-can-we-solve-diffuse-threats)** (Vivek Hebbar, Apr 2025): This explains an important class of threat models where catastrophe requires numerous failures, but each failure is only weak evidence of malign intent when investigated.
    

-   **[Catching AIs Red-Handed](https://redwoodresearch.substack.com/p/catching-ais-red-handed)** (Buck Shlegeris and Ryan Greenblatt, May 2024): It's crucial to think about what happens if the AI gets caught in order to think about plans that involve catching AIs red-handed.
    

## Podcasts ^podcasts

-   **[Ryan On The 80000 Hours Podcast](https://redwoodresearch.substack.com/p/ryan-on-the-80000-hours-podcast)** (Jul 2025): Ryan talks about AI R&D automation and ways misaligned AIs could take over. Most of Redwood’s work aims at reducing risk in the kinds of scenarios that he talks about in this podcast.
    
-   **[Buck On The 80000 Hours Podcast](https://redwoodresearch.substack.com/p/buck-on-the-80000-hours-podcast)** (Apr 2025): Buck talks about some detailed threat models and explains how AI control research can yield cost-effective techniques for reducing risk.
    
-   **[ARXP Podcast with Buck and Ryan](https://www.youtube.com/watch?v=gQbCO6zGRiI)** (Apr 2024): Buck and Ryan make the basic case for AI control and explain the [original AI control paper](https://arxiv.org/abs/2312.06942).
    

---

## 2\. Extensive guide ^2-extensive-guide

_Particularly recommended readings are **bolded** and listed first. As one might expect, some of our work is hard to categorize._

## Threat models (zoomed out) ^threat-models-zoomed-out

Reading some of these posts might be helpful context on Redwood’s worldview, including: how AI progress might develop, how this yields misalignment risk, and why we think AI control is promising within this broader context.

-   **[The case for ensuring that powerful AIs are controlled](https://redwoodresearch.substack.com/p/the-case-for-ensuring-that-powerful)** (Buck Shlegeris and Ryan Greenblatt, May 2024)
    
-   [Clarifying AI R&D threat models](https://redwoodresearch.substack.com/p/clarifying-ai-r-and-d-threat-models) (Josh Clymer, Apr 2025)
    
-   [Why do misalignment risks increase as AIs get more capable?](https://redwoodresearch.substack.com/p/why-do-misalignment-risks-increase) (Ryan Greenblatt, Apr 2025)
    
-   [Prioritizing Threats For AI Control](https://redwoodresearch.substack.com/p/prioritizing-threats-for-ai-control) (Ryan Greenblatt, Mar 2025)
    
-   [Planning For Extreme AI Risks](https://redwoodresearch.substack.com/p/planning-for-extreme-ai-risks) (Josh Clymer, Jan 2025)
    
-   [Ten People On The Inside](https://redwoodresearch.substack.com/p/ten-people-on-the-inside) (Buck Shlegeris, Jan 2025)
    

### Forecasting AI trends ^forecasting-ai-trends

-   **[A breakdown of AI capability levels focused on AI R&D labor acceleration](https://www.alignmentforum.org/posts/LjgcRbptarrRfJWtR/a-breakdown-of-ai-capability-levels-focused-on-ai-r-and-d)** (Ryan Greenblatt, Dec 2024)
    
-   **[Ryan On The 80000 Hours Podcast](https://redwoodresearch.substack.com/p/ryan-on-the-80000-hours-podcast)** (Jul 2025)
    
-   [Should we update against seeing relatively fast AI progress in 2025 and 2026?](https://redwoodresearch.substack.com/p/should-we-update-against-seeing-relatively) (Ryan Greenblatt, Jul 2025)
    
-   [How much novel security-critical infrastructure do you need during the singularity?](https://redwoodresearch.substack.com/p/how-much-novel-security-critical) (Buck Shlegeris, Jul 2025)
    
-   [What does 10x-ing effective compute get you?](https://redwoodresearch.substack.com/p/what-does-10x-ing-effective-compute) (Ryan Greenblatt, Jun 2025)
    
-   [Slow corporations as an intuition pump for AI R&D automation](https://www.alignmentforum.org/posts/hMSuXTsEHvk4NG6pm/slow-corporations-as-an-intuition-pump-for-ai-r-and-d) (Ryan Greenblatt and Eli Lifland, May 2025)
    
-   [What's going on with AI progress and trends? (As of 5/2025)](https://redwoodresearch.substack.com/p/whats-going-on-with-ai-progress-and) (Ryan Greenblatt, May 2025)
    
-   [A note by Ryan Greenblatt on the probability of software-only singularity](https://www.alignmentforum.org/posts/FG54euEAesRkSZuJN/ryan_greenblatt-s-shortform?commentId=rAFxcETtNtsuzw6aG) (Jan 2025)
    
-   [A basic systems architecture for AI agents that do autonomous research](https://redwoodresearch.substack.com/p/a-basic-systems-architecture-for) (Buck Shlegeris, Sep 2024)
    
-   [Getting 50% (SoTA) on ARC-AGI with GPT-4o](https://redwoodresearch.substack.com/p/getting-50-sota-on-arc-agi-with-gpt) (Ryan Greenblatt, Jun 2024)
    
-   [Access to powerful AI might make computer security radically easier](https://redwoodresearch.substack.com/p/access-to-powerful-ai-might-make) (Buck Shlegeris, Jun 2024)
    

## Threat models (zoomed in) ^threat-models-zoomed-in

At Redwood, we spend a lot of time performing detailed threat modelling with a focus on scheming AIs, as this informs our prioritization when developing plans for reducing catastrophic misalignment risk.

### How could scheming AIs make things difficult for us? ^how-could-scheming-ais

-   **[Misalignment and Strategic Underperformance: An Analysis of Sandbagging and Exploration Hacking](https://redwoodresearch.substack.com/p/misalignment-and-strategic-underperformance)** (Julian Stastny and Buck Shlegeris, May 2025)
    

-   **[How can we solve diffuse threats like research sabotage with AI control?](https://redwoodresearch.substack.com/p/how-can-we-solve-diffuse-threats)** (Vivek Hebbar, Apr 2025)
    

-   **[AI Catastrophes And Rogue Deployments](https://redwoodresearch.substack.com/p/ai-catastrophes-and-rogue-deployments)** (Buck Shlegeris, Jun 2024)
    
-   **[Auditing failures vs concentrated failures](https://www.alignmentforum.org/posts/hirhSqvEAq7pdnyPG/auditing-failures-vs-concentrated-failures)** (Ryan Greenblatt and Fabien Roger, Dec 2023)
    
-   [What's worse, spies or schemers?](https://redwoodresearch.substack.com/p/whats-worse-spies-or-schemers) (Buck Shlegeris and Julian Stastny, Jul 2025)
    
-   [Comparing risk from internally-deployed AI to insider and outsider threats from humans](https://redwoodresearch.substack.com/p/comparing-risk-from-internally-deployed) (Buck Shlegeris, Jun 2025)
    
-   [Buck On The 80000 Hours Podcast](https://redwoodresearch.substack.com/p/buck-on-the-80000-hours-podcast) (Apr 2025)
    
-   [Measuring whether AIs can statelessly strategize to subvert security measures](https://redwoodresearch.substack.com/p/measuring-whether-ais-can-statelessly) (Alex Mallen et al., Dec 2024)
    
-   [Why imperfect adversarial robustness doesn't doom AI control](https://redwoodresearch.substack.com/p/why-imperfect-adversarial-robustness) (Buck Shlegeris, Nov 2024)
    
-   [Untrusted smart models and trusted dumb models](https://redwoodresearch.substack.com/p/untrusted-smart-models-and-trusted) (Buck Shlegeris, May 2024)
    

### How likely are scheming AIs? ^how-likely-are-scheming

-   **[Alignment Faking In Large Language Models](https://redwoodresearch.substack.com/p/alignment-faking-in-large-language)** (Ryan Greenblatt et al., Dec 2024)
    
-   **[Behavioral red-teaming is unlikely to produce clear, strong evidence that models aren't scheming](https://redwoodresearch.substack.com/p/behavioral-red-teaming-is-unlikely)** (Buck Shlegeris, Oct 2024)
    
-   [To be legible, evidence of misalignment probably has to be behavioral](https://redwoodresearch.substack.com/p/to-be-legible-evidence-of-misalignment) (Ryan Greenblatt, Apr 2025)
    
-   [How will we update about scheming?](https://redwoodresearch.substack.com/p/how-will-we-update-about-scheming) (Ryan Greenblatt, Jan 2025)
    

### How might schemers function? ^how-might-schemers-function

-   **[Training-time schemers vs behavioral schemers](https://redwoodresearch.substack.com/p/training-time-schemers-vs-behavioral)** (Alex Mallen, May 2025)
    
-   **[There are two fundamentally different constraints on schemers](https://redwoodresearch.substack.com/p/there-are-two-fundamentally-different)** (Buck Shlegeris, Jul 2025)
    
-   [Two proposed projects on abstract analogies for scheming](https://redwoodresearch.substack.com/p/two-proposed-projects-on-abstract) (Julian Stastny, Jul 2025)
    
-   [When does training a model change its goals?](https://redwoodresearch.substack.com/p/when-does-training-a-model-change) (Vivek Hebbar and Ryan Greenblatt, Jun 2025)
    
-   [How training-gamers might function (and win)](https://redwoodresearch.substack.com/p/how-training-gamers-might-function) (Vivek Hebbar, Apr 2025)
    

## How can we control misaligned AIs? ^how-can-we-control

We perform a mix of conceptual and empirical research on ways to control scheming AIs. Most of our work is focused on developing control protocols as well as settings in which control protocols can be empirically evaluated.

### The main plan: develop control techniques ^the-main-plan-develop

We are interested in techniques that catch scheming AIs (“incrimination”), which is particularly promising when they might cause egregious failures—as well as techniques for eliciting high-quality work from schemers (e.g. using online training), which is particularly important when AIs can subtly sabotage us.

-   **[AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942)** (Ryan Greenblatt et al., Dec 2023)
    
-   **[Ctrl-Z: Controlling AI Agents via Resampling](https://redwoodresearch.substack.com/p/ctrl-z-controlling-ai-agents-via)** (Aryan Bhatt et al., Apr 2025)
    
-   **[How to prevent collusion when using untrusted models to monitor each other](https://redwoodresearch.substack.com/p/how-to-prevent-collusion-when-using)** (Buck Shlegeris, Sep 2024)
    
-   **[Win/continue/lose scenarios and execute/replace/audit protocols](https://redwoodresearch.substack.com/p/wincontinuelose-scenarios-and-executereplaceaudi)** (Buck Shlegeris, Nov 2024)
    
-   **[Thoughts on the conservative assumptions in AI control](https://redwoodresearch.substack.com/p/thoughts-on-the-conservative-assumptions)** (Buck Shlegeris, Jan 2025)
    
-   [Why it's hard to make settings for high-stakes control research](https://redwoodresearch.substack.com/p/why-its-hard-to-make-settings-for) (Buck Shlegeris, Jul 2025)
    
-   [Recent Redwood Research project proposals](https://redwoodresearch.substack.com/p/recent-redwood-research-project-proposals) (Jul 2025)
    
-   [7+ Tractable Directions In AI Control](https://redwoodresearch.substack.com/p/7-tractable-directions-in-ai-control) (Ryan Greenblatt and Julian Stastny, Apr 2025)
    
-   [An Overview Of Areas Of Control Work](https://redwoodresearch.substack.com/p/an-overview-of-areas-of-control-work) (Ryan Greenblatt, Apr 2025)
    
-   [An Overview Of Control Measures](https://redwoodresearch.substack.com/p/an-overview-of-control-measures) (Ryan Greenblatt, Apr 2025)
    
-   [Notes on countermeasures for exploration hacking (aka sandbagging)](https://redwoodresearch.substack.com/p/notes-on-countermeasures-for-exploration) (Ryan Greenblatt, Apr 2025)
    
-   [Notes on handling non-concentrated failures with AI control: high level methods and different regimes](https://redwoodresearch.substack.com/p/notes-on-handling-non-concentrated) (Ryan Greenblatt, Mar 2025)
    
-   [Adaptive Deployment of Untrusted LLMs Reduces Distributed Threats](https://arxiv.org/abs/2411.17693) (Jiaxin Wen et al., Nov 2024)
    

-   [Fields that I reference when thinking about AI takeover prevention](https://redwoodresearch.substack.com/p/fields-that-i-reference-when-thinking) (Buck Shlegeris, Aug 2024)
    
-   [Stress-Testing Capability Elicitation With Password-Locked Models](https://arxiv.org/abs/2405.19550) (Ryan Greenblatt et al., May 2024)
    

### Spreading our bets ^spreading-our-bets

Some of our work involves coming up with contingency plans as well as more speculative bets.

-   **[Making Deals With Early Schemers](https://redwoodresearch.substack.com/p/making-deals-with-early-schemers)** (Julian Stastny et al., Jun 2025)
    
-   **[AIs at the current capability level may be important for future safety work](https://redwoodresearch.substack.com/p/ais-at-the-current-capability-level)** (Ryan Greenblatt, May 2025)
    
-   [Jankily Controlling Superintelligence](https://redwoodresearch.substack.com/p/jankily-controlling-superintelligence) (Ryan Greenblatt, Jun 2025)
    
-   [AI Safety Techniques Leveraging Distillation](https://redwoodresearch.substack.com/p/ai-safety-techniques-leveraging-distillation) (Ryan Greenblatt, Jun 2025)
    
-   [The case for countermeasures to memetic spread of misaligned values](https://redwoodresearch.substack.com/p/the-case-for-countermeasures-to-memetic) (Alex Mallen, May 2025)
    
-   [How might we safely pass the buck to AI?](https://redwoodresearch.substack.com/p/how-might-we-safely-pass-the-buck) (Josh Clymer, Feb 2025)
    
-   [Managing catastrophic misuse without robust AI](https://redwoodresearch.substack.com/p/managing-catastrophic-misuse-without) (Ryan Greenblatt and Buck Shlegeris, May 2024)
    
-   [Preventing model exfiltration with upload limits](https://redwoodresearch.substack.com/p/preventing-model-exfiltration-with) (Ryan Greenblatt, May 2024)
    

### Safety cases ^safety-cases

In an ideal world, AI developers will make extensive safety cases to ensure that their deployments are safe. Control methods have the advantage of being particularly well-suited for making quantitative safety estimates.

-   **[A sketch of an AI control safety case](https://arxiv.org/abs/2501.17315v1)** (Tomek Korbak et al., Jan 2025)
    
-   [Takeaways from sketching a control safety case](https://redwoodresearch.substack.com/p/takeaways-from-sketching-a-control) (Josh Clymer, Jan 2025)
    
-   [AI companies are unlikely to make high-assurance safety cases if timelines are short](https://www.alignmentforum.org/posts/neTbrpBziAsTH5Bn7/ai-companies-are-unlikely-to-make-high-assurance-safety) (Ryan Greenblatt, Jan 2025)
    
-   [When does capability elicitation bound risk?](https://redwoodresearch.substack.com/p/when-does-capability-elicitation) (Josh Clymer, Jan 2025)
    
-   [Extending control evaluations to non-scheming threats](https://redwoodresearch.substack.com/p/extending-control-evaluations-to) (Josh Clymer, Jan 2025)
    

## So we caught a scheming AI, what now? ^so-we-caught-a

We hope that catching a scheming AI will drastically change how the world treats risks from misaligned AI, but we have some contingency plans in case this doesn’t happen.

-   **[Catching AIs Red-Handed](https://redwoodresearch.substack.com/p/catching-ais-red-handed)** (Buck Shlegeris and Ryan Greenblatt, May 2024)
    
-   **[Handling schemers if shutdown is not an option](https://redwoodresearch.substack.com/p/handling-schemers-if-shutdown-is)** (Buck Shlegeris, Apr 2025)
    
-   [Prefix cache untrusted monitors: a method to apply after you catch your AI](https://redwoodresearch.substack.com/p/prefix-cache-untrusted-monitors-a) (Ryan Greenblatt, Jun 2025)
    
-   [Would catching your AIs trying to escape convince AI developers to slow down or undeploy?](https://redwoodresearch.substack.com/p/would-catching-your-ais-trying-to) (Buck Shlegeris, Aug 2024)
