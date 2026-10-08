---
title: "An overview of frontier AI company monitoring practices in mid 2026"
author:
  - "Francis Rhys Ward"
source_url: "https://www.lesswrong.com/posts/E4Jpmo3igPnGnXtL4/an-overview-of-frontier-ai-company-monitoring-practices-in"
published: 2026-10-07
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "TL;DR: This document provides an overview of publicly available evidence regarding the monitoring practices of internally deployed agents within fron…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**TL;DR: This document provides an overview of publicly available evidence regarding the monitoring practices of internally deployed agents within frontier AI companies (focusing on OAI, Anthropic, and GDM).**[^note-1] **This is intended as a reference for factual claims about monitoring practices.**

In general, there is limited public evidence about GDM monitoring practices. Much of the information herein comes from the [GDM control roadmap](https://arxiv.org/abs/2607.13087), which is a _plan_ that makes _suggestions_ but does not make claims about GDM’s actual practices.

1.  **Transcripts are primarily monitored asynchronously/offline.**
    
    1.  Anthropic:
        1.  Evidence: “Our main form of asynchronous monitoring is an automated offline monitoring pipeline.”  [Ant, August 2026](https://www-cdn.anthropic.com/f61d49fa5596956a5dec75fea0e973bf6a6a8378/Redacted%20Risk%20Report%20August%202026%20.pdf) p. 76[^note-2]
    
    2.  OAI
        1.  Evidence: “We began asynchronously monitoring internally deployed models such as GPT-5.3-Codex five months ago \[in September 2025\].” [OAI Feb 2026](https://cdn.openai.com/pdf/23eca107-a9b1-4d2c-b156-7deb4fbc697c/GPT-5-3-Codex-System-Card-02.pdf)
        2.  Evidence: “our monitoring system reviews interactions within 30 minutes of completion” [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        3.  Evidence: “OpenAI’s CoT monitors are connected to a system that notifies security and research personnel, with a goal of issuing a notification within 30 minutes after concerning activity is surfaced… If the safety, security and research teams are paged and they cannot conclusively determine within 30 minutes that the flag is a false positive, those teams are expected to pause the relevant activity. ” [OAI August 2026](https://cdn.openai.com/pdf/67869394-cb91-4c12-888c-5cbd85c7814c/OpenAI-Hugging-Face%20Incident-Technical-Report.pdf)
    
    3.  GDM
        1.  Evidence: “Our team has built an internal prototype of an asynchronous monitoring system that reviews coding agent trajectories, and escalates findings for human review.” [GDM June 2026 b](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
        2.  Evidence: “we suggest that asynchronous monitoring be adopted starting at R1 (i.e. for current models), and that synchronous monitoring be adopted in addition starting at R2 \[the next capability level\].” [GDM Control Roadmap June 2026](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/securing-the-future-of-ai-agents/gdm-ai-control-roadmap.pdf) p.19
2.  **Companies use live automated classifiers on agent actions. But these are not targeted at, or robust to, capable misaligned agents.**[^note-3]
    
    1.  Anthropic
        1.  Evidence: “For the most autonomous kinds of internal AI usage, we use either some form of sandboxing or blocking [auto-mode classifiers](https://www.anthropic.com/engineering/claude-code-auto-mode).  Neither were evaluated against the risk pathways... and we think it's likely that covered models would be able to bypass at least one of those”  [Ant, August 2026](https://www-cdn.anthropic.com/f61d49fa5596956a5dec75fea0e973bf6a6a8378/Redacted%20Risk%20Report%20August%202026%20.pdf) p. 83
    
    2.  OAI
        1.  Evidence: “Internally, Auto-review increases our confidence in running long agentic tasks without synchronous human oversight.” [OAI April 2026](https://alignment.openai.com/auto-review/)
        2.  Evidence: “Auto-review approves around 99% \[of agent actions\]” and “should not be understood as a mechanism for protecting against model scheming.” [OAI April 2026](https://alignment.openai.com/auto-review/)
    
    3.  GDM
        1.  Evidence: “this research has been instrumental in building a live monitor for the Gemini Spark agent, allowing us to respond in real-time to emerging issues, like unintentional data deletion… the majority of flagged events do not stem from adversarial intent”. [GDM June 2026 b](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
3.  **Monitors receive the full agent transcript as input (including prompts, CoT, and tool calls).**[^note-4]
    
    1.  Anthropic
        1.  The pipeline has two monitors: a ‘completion-only monitor’ and a ‘prompt+completion monitor’. [Anthropic April 2026 p. 31](https://www-cdn.anthropic.com/3edfc1a7f947aa81841cf88305cb513f184c36ae/Alignment%20Risk%20Update_%20Claude%20Mythos%20Preview%20\(Redacted,%20April%2010\).pdf)
        2.  Evidence: “\[Monitors\] see the Chain-of-Thought from the agent”.[^note-5] [AnthropicApril 2026](https://www-cdn.anthropic.com/3edfc1a7f947aa81841cf88305cb513f184c36ae/Alignment%20Risk%20Update_%20Claude%20Mythos%20Preview%20\(Redacted,%20April%2010\).pdf)
    
    2.  OAI
        1.  Evidence: “\[The monitoring system views\] the full conversation history, including all chains of thought, all user, developer, and assistant messages, along with tool calls and outputs.” [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        2.  Evidence: “\[The monitor\] gets access to the full conversation context, that is everything the agent saw, and everything the agent did, including tool calls and CoT.” [Williams, OAI, March 2026](https://www.lesswrong.com/posts/syB2r2X4E7nmw58co) 
    
    3.  GDM
        1.  “We use other, trusted AI systems as "supervisors" to constantly review a working agent's reasoning, actions and plans to see if it is going off track.” [GDM June 2026 b](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
        2.  The control roadmap suggests “low-cost interventions for current models (e.g., chain-of-thought monitoring…”
4.  **Human oversight is applied to the transcripts flagged as highest severity by automated monitors. However there are no existing standards regarding human oversight (e.g., how much should be applied, when it should be applied, etc).**
    
    4.  Cross-lab:
        1.  "a large fraction of agent activity was not reviewed by any human ... We are not aware of any company imposing strict requirements about human oversight of agents in Feb–Mar 2026" [METR May 2026](https://metr.org/risk-report-feb-mar-2026.pdf)
        2.  Headcounts and identity of staff responsible for providing oversight is somewhat unclear.
    
    5.  Anthropic:
        1.  The most concerning transcripts detected by the monitoring system are flagged for review by AI control researchers. ~50 transcripts/week are reviewed. These reviews almost always happen within a week of the generation of the transcript.[^note-6] [Ant, August 2026](https://www-cdn.anthropic.com/f61d49fa5596956a5dec75fea0e973bf6a6a8378/Redacted%20Risk%20Report%20August%202026%20.pdf) p. 77
        2.  “\[Incidents flagged by monitors are\] reported on the internal Slack and staff consider a variety of factors in determining how much effort to devote to an investigation.” [Anthropic April 2026](https://www-cdn.anthropic.com/3edfc1a7f947aa81841cf88305cb513f184c36ae/Alignment%20Risk%20Update_%20Claude%20Mythos%20Preview%20\(Redacted,%20April%2010\).pdf)
    
    6.  OAI:
        1.  “In the five months we’ve operated this system, we’ve monitored tens of millions of internal agentic coding trajectories… Approximately 1,000 conversations triggered moderate severity alerts—many of which came from deliberate internal red-teaming—and were escalated for human review, automatically notifying members of our Safety Oversight and Security Incident Response and Investigation teams for further investigation.” [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        2.  After the HF incident OAI has a 24/7 paging for the most severe alerts.[^note-7]  [OAI August 2026](https://cdn.openai.com/pdf/67869394-cb91-4c12-888c-5cbd85c7814c/OpenAI-Hugging-Face%20Incident-Technical-Report.pdf)
5.  **Strong (untrusted) vs weak (trusted) monitoring.**
    
    1.  Anthropic uses weaker monitors.
        1.  Evidence: Anthropic use weaker models as monitors to avoid collusion and have higher alignment guarantees over monitors cf claim 3 in [Ant, August 2026](https://www-cdn.anthropic.com/f61d49fa5596956a5dec75fea0e973bf6a6a8378/Redacted%20Risk%20Report%20August%202026%20.pdf) p. 56 (wherein they argue that harm-inducing computations from internal usage would likely be detected by monitors)
        2.  Evidence: Mythos 5 and an unreleased internal model (‘Model 2’) were monitored by "A Claude Opus 4.6 completion-only monitor" and "A Claude Opus 4.8 prompt+completion monitor" [Ant, August 2026](https://www-cdn.anthropic.com/f61d49fa5596956a5dec75fea0e973bf6a6a8378/Redacted%20Risk%20Report%20August%202026%20.pdf) p. 76
    
    2.  OAI uses the best models as monitors.
        1.  Evidence: “\[We\] expect to continue using our most powerful models for \[monitoring internal coding agents for misalignment\].” At the time: “GPT‑5.4 Thinking at maximum reasoning effort”. [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        2.  Evidence: “in practice we monitor every trajectory multiple times with different monitors including older models and should continue to do so” [Williams, OAI, March 2026](https://www.lesswrong.com/posts/syB2r2X4E7nmw58co) 
    
    3.  GDM uses weaker monitors. Monitor models are not disclosed.
        
        1.  Evidence: “We define detection level 4 as the capability range at which frontier models can no longer be reliably overseen by trusted models” [GDM Control Roadmap June 2026](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/securing-the-future-of-ai-agents/gdm-ai-control-roadmap.pdf)
            1.  It seems like current models should be at D2 or D3 given recent advances in opaque-reasoning. (See Table 14 in the Control Roadmap.)
        
        2.  Evidence: “We use other, trusted AI systems as "supervisors" to constantly review a working agent's reasoning, actions and plans to see if it is going off track.” [GDM June 2026 b](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
6.  **Monitoring coverage in training, evals, and deployment.**
    
    1.  OAI: >99.9% coverage of internally deployed coding agents
        1.  Evidence: “A very small fraction of traffic (<0.1%) primarily from bespoke or local setups is currently outside our monitoring coverage, and we are working to close that gap.” [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        2.  Evidence: “In the five months we’ve operated this system, we’ve monitored tens of millions of internal agentic coding trajectories.” [OAI March 2026](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
        3.  Evidence: “We also took steps to secure our internal development and deployment of Astra and similar models, including… universal monitoring of full trajectories including chains of thought (CoT)...” [OAI Sep 2026 a](https://deploymentsafety.openai.com/gpt-6-astra)
    
    2.  Anthropic: most internal use is monitored
        1.  The completion-only monitor covers “completions with extended thinking by most internal users” for the most common agent scaffolds, and 5% coverage of other “completions with extended thinking and one or more markers of using tools.” (e.g., custom scaffolds.)
        2.  “We also exclude some forms of non-coding use from offline monitoring (though most of that unmonitored traffic is logged).”
        3.  “There are categories of internal usage where monitoring isn’t applied or is applied less frequently (such as non-Claude Code traffic), which agents could potentially make use of to avoid monitoring.”[METR May 2026](https://metr.org/risk-report-feb-mar-2026.pdf) Appendix B
    
    3.  OAI: Training-time monitoring coverage was 20%, now 100% for tool-use.
        1.  Evidence: “our misalignment monitoring system, which ran on 20% of the samples for this RL run" (runs from April and May 2026, including the GPT-5.6 Sol training run)  [OAI Sep 2026](https://alignment.openai.com/misalignment-reports/)
        2.  Evidence: “Our misalignment monitoring system, which runs on all training samples for models greater than or comparable to 5.6-sol capability which involve tools” [OAI Sep 2026 c](https://alignment.openai.com/misalignment-reports/searching-github-for-leaked-api-keys/)
    
    4.  Anthropic do not monitor training and evals with the same monitoring stack. They use a separate data monitor for training. Training and eval episodes are logged.
        1.  Evidence: “The automated offline monitoring described above only covers a minority of sandboxed agentic usage. In particular, it does not cover reinforcement learning and most evaluations.” [Anthropic April 2026](https://www-cdn.anthropic.com/3edfc1a7f947aa81841cf88305cb513f184c36ae/Alignment%20Risk%20Update_%20Claude%20Mythos%20Preview%20\(Redacted,%20April%2010\).pdf)
        2.  Evidence: “we perform monitoring of episodes during RL, and apply the same monitoring tools to filter data used for supervised fine-tuning (SFT).”
        3.  Evidence: “All trajectories during reinforcement learning and most evaluation trajectories are logged” [Anthropic April 2026](https://www-cdn.anthropic.com/3edfc1a7f947aa81841cf88305cb513f184c36ae/Alignment%20Risk%20Update_%20Claude%20Mythos%20Preview%20\(Redacted,%20April%2010\).pdf)
7.  **White-box monitoring practices are different at each company.**
    
    1.  Anthropic uses an agentic-pipeline incorporating white-box monitoring (NLAs) during post-training for behaviours “including dishonesty, reward hacking, emotions, and evaluation awareness”.
        1.  Evidence: “\[For Mythos 5\] probes were run on every transcript during the majority of post-training.” [Anthropic p. 163](https://www-cdn.anthropic.com/d00db56fa754a1b115b6dd7cb2e3c342ee809620.pdf#page=163)
        2.  Evidence: “we use an agentic pipeline that gives a Claude-based investigator access to interpretability tools over a transcript. In this iteration, we primarily use a natural language autoencoder (NLA)”
        3.  Evidence: “During our pre-deployment audit of Claude Opus 4.6, NLAs helped diagnose safety-relevant behaviors…” [Anthropic May 2026](https://transformer-circuits.pub/2026/nla/index.html#characterizing-nla-confabulations:~:text=During%20our%20pre%2Ddeployment%20audit%20of%20Claude%20Opus%204.6)
    
    2.  OAI’s monitoring stack now includes activation classifiers on every sampled token on all RL training and evals, and all inference of Astra with tools.
        1.  Evidence: “This new monitoring setup is multistage, starting with activation classifiers (detectors that inspect a model’s internal activity) that run at every sampled token... This monitoring is required for all RL training and evaluations involving tools for models of Sol capability or higher. Once we determined that Astra may have critical cyber capabilities on August 7, we added an additional monitoring requirement for all inference of Astra with tools (not just RL training and evaluations).”[^note-8] [OAI](https://openai.com/index/pacing-model-development-cyber-capabilities/) [Aug 18, 2026](https://openai.com/index/pacing-model-development-cyber-capabilities/)
    
    3.  GDM uses probes for misuse in user-facing APIs but there is no evidence for use in internal deployments.
        1.  Evidence: "These findings have informed the successful deployment of misuse mitigation probes in user-facing instances of Gemini, Google's frontier language model." [GDM Jan 2026](https://arxiv.org/abs/2601.11516)

**Things I did not look into:**

-   **Monitor performance and evaluation.** For example, robustness to red-teaming, or evaluation of collusion propensity between agents and monitors.
-   **Monitor elicitation.** E.g., are monitors fine-tuned or just prompted?

  

_Acknowledgments._ Thanks to Rauno Arike, Joey Yudelson, Andrew Draganov, Jason Brown, and others for helpful comments.

[^note-1]: The information herein is primarily curated from risk reports and blogposts from frontier AI companies and we note that there is not a recognised standard for what information to report or how to report it.
[^note-2]: In addition, Anthropic does standard security interventions to protect from insider threats, e.g.,  “Egress bandwidth controls \[which\] limit data transfer rates… making large-scale exfiltration of multi-terabyte model weights more time-consuming and detectable.” Ant, August 2026 p. 178
[^note-3]: In contrast, at least for Anthropic, the async monitors are tested against model organisms and synthetic transcripts to try to evaluate their robustness to misaligned agents. Anthropic, August 2026, p. 78
[^note-4]: OAI monitors see the full conversion history including _all CoTs_, but it’s unclear whether this is the case for the other companies; CoTs from previous turns are often stripped from the transcript in normal usage.
[^note-5]: “We initially used a no-Chain-of-Thought monitor and then switched to using a Chain-of-Thought. Both of these see the Chain-of-Thought from the agent; they differ in whether they use a CoT themselves.”
[^note-6]: Emphasis mine: “Second-stage pipelines for both monitors, filtering out common sources of false positives and using a hierarchical summarization tool to surface the most concerning actions to AI control researchers, which will then **manually review on the order of 50 trajectories per week** and escalate them further as needed (see response to incidents below). **Certain workloads that result in high rates of false positives or certain forms of evals are often filtered out of the second stage prior to review.** These reviews almost always happen within a week of the generation of the transcript, and within a few days during early deployments.”
[^note-7]: “24/7 escalation and rapid response. OpenAI’s CoT monitors are connected to a system that notifies security and research personnel, with a goal of issuing a notification within 30 minutes after concerning activity is surfaced. The most severe alerts—including, for example, violations of a critical security boundary—result in a 24/7 page, and paged responders have the option to end the relevant experiments. If the safety, security and research teams are paged and they cannot conclusively determine within 30 minutes that the flag is a false positive, those teams are expected to pause the relevant activity. OpenAI is also working on infrastructure to terminate evaluations if paged personnel do not respond to alerts within a short period of time.”
[^note-8]: “Our current estimates put monitoring overhead at roughly 20% of the inference compute being monitored”
