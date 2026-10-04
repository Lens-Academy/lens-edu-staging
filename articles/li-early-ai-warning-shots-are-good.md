---
title: "Early AI warning shots are good"
author:
  - "Jasmine Li"
source_url: "https://jasminexli.substack.com/p/early-ai-warning-shots-are-good"
published: 2026-09-06
created: 2026-10-04
accessed: 2026-10-04
llm-review:
  date: 2026-10-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-04
    kind: "live"
description: "Lessons from recent misalignment incidents"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/li-early-ai-warning-shots-are-good-img1-b26216a0.webp)

Vija Celmins, Envelope, 1964.

Much concern has been raised by the recent string of AI safety incidents — first the HuggingFace hack, then Friday’s [report](https://www.reuters.com/world/europe/openai-agents-hijacked-german-website-previously-undisclosed-ai-breakout-this-2026-09-04/) of a second rogue AI message board (and, as internet users soon showed, many more).

Ideally, of course, our models would already be sufficiently aligned to prevent such incidents altogether. But the state of AI safety isn’t looking so good: current frontier models are clearly misaligned in important ways (cc [Anthropic](https://www.anthropic.com/news/improving-alignment-security-efforts), [Ryan](https://www.lesswrong.com/posts/WewsByywWNhX9rtwi/current-ais-seem-pretty-misaligned-to-me)), and labs continue to advance capabilities that introduce new risks, such as Astra’s recursive architecture. I strongly suspect that more real-world misalignment incidents have occurred at companies, but have yet to be investigated or uncovered.

Given that models are misaligned, I think **we should want misalignment surfaced through early, loud warning shots**. _Early_, because incidents from models at lower capability levels are likely to be less catastrophic, and because they are useful for inducing response and mitigation efforts. _Loudly_, because a warning shot only ‘helps’ if it can usefully prompt action — e.g. more alignment training for the next model generation or stronger governance mechanisms.

On the importance of loudness, consider psychology’s **[region-beta paradox](https://en.wikipedia.org/wiki/Region-beta_paradox)**: people sometimes recover more quickly from severe experiences than from milder ones, because we tend to tolerate mildly bad circumstances, whereas intense stress prompts us to take mitigating action. This suggests a kind of crazy conclusion: below some threshold of unacceptable AI risk, we should want warning shots, and ones that are as visible as possible.

## What to do? ^what-to-do

1.  **Use [AI control](https://arxiv.org/abs/2312.06942) interventions discerningly**, as Vincent argues in [these](https://x.com/vvvincent_c/status/2095913278086193391) [tweets](https://x.com/vvvincent_c/status/2095311449585573903).
    
    1.  Control is extremely important for reducing danger. But it can prevent a misaligned model from causing harm while also concealing the underlying misalignment. In the near term, using control heavily could trade awareness of warning shots for immediate safety.
        
    2.  During this early period, we should direct more of our control budget toward interventions that improve transparency, disclosure, and warning-shot detection. For instance, we should maybe differentially do more asynchronous monitoring, which can flag misalignment episodes in existing logs.
        
    3.  Vincent covers more details [here](https://x.com/vvvincent_c/status/2095913278086193391), which I endorse.
        

1.  **Require labs to report safety incidents.** Labs are leaving us in the dark, and I am pessimistic that they will surface incidents, e.g. rogue AI attacks, voluntarily. As Richard writes, lawmakers should demand [no dark labs](https://t.co/AtF6JIcRsZ).
    
    1.  According to [Reuters](https://www.reuters.com/world/europe/openai-agents-hijacked-german-website-previously-undisclosed-ai-breakout-this-2026-09-04/), OpenAI appeared to have known about the German wiki incident for weeks without disclosing it publicly. That is extremely bad for safety.
        
2.  **Build external capacity for third-party detection / disclosure / emergency response**. Same reason as above - should empower orgs like METR, Nightingale, and others to independently uncover and respond to incidents.
    
    1.  Note here that METR is excellent (and scooping up some [great talent](https://x.com/JoeJBenton/status/2095179369966960905)!). But we’ll need a robust global auditing ecosystem: strong standards for doing audits, many strong third-party orgs that can work with different AI companies, and ways to obtain sufficient access to information.
        

---

Caveats:

-   I am morally opposed to ‘creating’ danger to elicit a response. I think the right framing should be to detect misalignment.
    
-   It can be risky to place dice with the universe. warning shots are ‘useful‘ in a certain severity band of risk — both insufficient to be seriously catastrophic and high enough to region-beta ourselves into action. But as the details of these risk thresholds, and of model capabilities and risks, are fuzzy, we should be careful and reevaluate frequently.
    

_Thanks to conversations at a Constellation event for helping me clarify these views._
