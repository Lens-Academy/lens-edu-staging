---
title: "Governance Problems"
author:
  - "Charles Martinet"
  - "Markov Grey"
  - "Su Cizem"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/governance/governance-problems/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090614173}@@

%%
Add discussion note here:

...

%%++}

**AI governance is not the same as traditional technology governance.** Traditional technology governance relies on several key assumptions that break down when applied to AI. We typically assume we can predict how a technology will be used and its likely impacts, that we can effectively control its development pathway, and that we can regulate specific applications or end-uses. For example, pharmaceutical governance uses clinical trials and approval processes based on intended medical applications, while nuclear technology is controlled through international treaties, safeguards, and monitoring of specific facilities and materials. These approaches work when technologies follow relatively predictable development paths and have clear applications. To understand what makes AI governance uniquely challenging, we can examine AI through three different lenses that each require different governance approaches ([Dafoe, 2022](https://academic.oup.com/edited-volume/41989/chapter-abstract/408516484);[ Buchanan, 2020](https://cset.georgetown.edu/publication/the-ai-triad-and-what-it-means-for-national-security-strategy/)).

**AI as general-purpose technology.** AI transforms many sectors simultaneously, making sector-specific regulation insufficient. Like electricity or computers before it, AI can reshape healthcare, finance, transportation, and education all at once. Traditional technology governance typically focuses on specific applications - we regulate medical devices differently from automobiles. But when a single AI system can diagnose diseases, trade stocks, and drive cars, our regulatory silos break down. The impacts span across society in ways that make targeted regulation insufficient ([Buchanan, 2020](https://cset.georgetown.edu/publication/the-ai-triad-and-what-it-means-for-national-security-strategy/)).

**AI as information technology.** AI processes and generates information in unprecedented ways. Unlike traditional information systems that store and retrieve data, AI can create entirely new content - from photorealistic images to convincing text to synthetic voices. This creates unprecedented challenges around security, privacy, and information integrity. Traditional governance frameworks weren't designed to handle technologies that can rapidly generate and manipulate information at massive scale ([Brundage et al., 2018](https://arxiv.org/pdf/1802.07228)). The speed and scope of potential information impacts outstrip traditional control mechanisms.

**AI as intelligence technology.** AI introduces unique control challenges as systems become more capable. As AI systems approach and potentially exceed human cognitive abilities in various domains, they may develop sophisticated ways to evade controls or pursue unintended objectives. We're already seeing glimpses of this with language models that can engage in deception or manipulation when pursuing goals ([Ganguli et al., 2022](https://arxiv.org/abs/2202.07785)). There are several dangerous capabilities (refer back to chapters 1 and 2) which become even more acute when considering that AI systems might develop these capabilities without being explicitly programmed for them ([Woodside, 2024](https://arxiv.org/abs/2206.07682)). The intelligence aspect of AI creates a dynamic where the technology being governed might actively resist or circumvent governance measures, a challenge without precedent in technology regulation.

**The combination of AI as a general-purpose, information,  intelligence technology creates unique governance challenges.** The mixed nature of AI as a general-purpose, information processing, and potentially intelligent technology gives rise to three fundamental problems that make traditional governance approaches inadequate.

![Figure 4.2](https://ai-safety-atlas.com/_astro/fbc9a3887ee6973b678b3f6e2aadab438652cffeaf093e9d94e15ba767da783c.C970wyQn_1t0B0O.webp)

*Figure 4.2: Summary of the three regulatory challenges posed by frontier AI ([Anderljung, 2023](https://arxiv.org/pdf/2307.03718))*

## Unexpected Capabilities

**AI systems develop surprising abilities that weren't part of their intended design.** Through several of our chapters now, we have shown that foundation models can show "emergent" capabilities that appear suddenly as models scale up with more data, parameters and compute. GPT-3 unexpectedly demonstrated the ability to perform basic arithmetic, while later models showed emergent reasoning capabilities that surprised even their creators ([Ganguli et al., 2022](https://arxiv.org/abs/2202.07785);[ Wei et al., 2022](https://arxiv.org/abs/2206.07682)). Evaluations have found that frontier models can autonomously conduct basic scientific research, hack into computer systems, and manipulate humans through persuasion, none of which were explicitly trained for ([Phuong et al., 2024](https://arxiv.org/abs/2403.13793);[ Boiko et al., 2023](https://arxiv.org/abs/2304.05332);[ Turpin et al., 2023](https://arxiv.org/abs/2305.04388);[ Fang et al., 2024](https://arxiv.org/abs/2402.06664)).

![Figure 4.3](https://ai-safety-atlas.com/_astro/09241cde1a69a0228d6b128d699a816580e14c092d772ee287c891fce734f19c.zMpTCWW__Zwkgdg.webp)

*Figure 4.3: Example of unexpected capabilities. Graphs showing several metrics that improve suddenly and unpredictably as models increase in size ([Ganguli et al., 2022](https://arxiv.org/abs/2202.07785))*

**AI evaluations are still in their early stages in 2025.** Testing frameworks lack established best practices, and the field has yet to mature into a reliable science ([Trusilo, 2024](https://www.tandfonline.com/doi/full/10.1080/15027570.2023.2213985)). While evaluations can reveal some capabilities, they cannot guarantee absence of unknown threats, forecast new emergent abilities, or assess risks from autonomous systems ([Barnett & Thiergart, 2024](https://arxiv.org/html/2412.08653v1)). Predictability itself is a nascent research area, with major gaps in our ability to anticipate how present models behave, let alone future ones ([Zhou et al., 2024](https://arxiv.org/html/2310.06167v3)). Even the most comprehensive test-and-evaluation frameworks struggle with complex, unpredictable AI behavior ([Wojton et al., 2020](https://testscience.org/wp-content/uploads/formidable/20/Autonomy-Lit-Review.pdf)).

## Deployment Safety

**Once deployed, AI systems can be repurposed for harmful applications beyond their intended use.** The same language model trained for helpful dialogue can generate misinformation, assist with cyberattacks, or help design biological weapons. Users regularly discover new capabilities through clever prompting that bypasses safety measures called "jailbreaks" that unlock dangerous functionalities ([Solaiman et al., 2024](https://arxiv.org/abs/2306.05949);[ Marchal et al., 2024](https://arxiv.org/abs/2406.13843);[ Hendrycks et al., 2023](https://arxiv.org/abs/2306.12001)).

![Figure 4.4](https://ai-safety-atlas.com/_astro/55be75301c257c0f0e3b5e16e4855b1e9074b45deb9b28b27d19a8c0748bd3b3.CXNS-H99_28SSAy.webp)

*Figure 4.4: A schematic of using autonomous LLM agents to hack websites ([Fang et al., 2024](https://arxiv.org/abs/2402.06664)). Once a dual-purpose technology is public, it can be used for both beneficial and harmful purposes.*

**AI agents amplify deployment risks**. We're now seeing autonomous AI agents that can chain together model capabilities in novel ways, using tools and taking actions in the real world. These agents can pursue complex goals over extended periods, making their behavior even harder to predict and control post-deployment ([Fang et al., 2024](https://arxiv.org/abs/2402.06664)).

## Proliferation

**AI capabilities spread rapidly through multiple channels, making containment nearly impossible.** Models can be stolen through cyberattacks, leaked by insiders, or reproduced by competitors within months. The rapid open-source replication of ChatGPT-like capabilities led to models with safety features removed and new dangerous capabilities discovered through community experimentation ([Seger et al., 2023](https://arxiv.org/abs/2311.09227)). With API-based models, techniques like model distillation can even extract capabilities without direct access to model weights ([Nevo et al., 2024](https://www.rand.org/content/dam/rand/pubs/research_reports/RRA2800/RRA2849-1/RAND_RRA2849-1.pdf)).

**Physical containment doesn't work for digital goods.** Unlike nuclear materials or dangerous pathogens, AI models are just patterns of numbers that can be copied instantly and transmitted globally. Once capabilities exist, controlling their spread becomes a losing battle against the fundamental nature of digital information.

![Figure 4.5](https://ai-safety-atlas.com/_astro/2e4cbb2e25a4b64f463ec19c2f1b20aa19b8900a3a976a62c43ecc6357bc71d8.rzPZwpq3_1CyLge.webp)

*Figure 4.5: Examples of Proliferation ([Özcan, 2024](https://cfg.eu/ai-governance-challenges-part-3-proliferation/)).*

## Governance Targets

**The unique challenges associated with AI governance mean we need to carefully choose where and how to intervene in AI development.** This requires identifying both what to govern (targets) and how to govern it (mechanisms) ([Anderljung et al., 2023](https://arxiv.org/abs/2307.03718);[ Reuel & Bucknall, 2024](https://www.governance.ai/research-paper/open-problems-in-technical-ai-governance)). Governance must intervene at points that address core challenges before they manifest. We can't wait for dangerous capabilities to emerge or proliferate before acting. Instead, we need to identify intervention points in the AI development pipeline that will help us shape AI development proactively.

Effective governance targets share three essential properties:

- **Measurability**: We must be able to track and verify what's happening. The amount of computing power used for training can be measured in precise units (floating-point operations), making it possible to set clear thresholds and monitor compliance ([Sastry et al., 2024](https://arxiv.org/abs/2402.08797)).
- **Controllability**: There must be concrete mechanisms to influence the target. It's not enough to identify what matters, we need practical ways to shape it. The semiconductor supply chain, for instance, has clear chokepoints where export controls can effectively limit access to advanced chips ([Heim et al., 2024](https://www.governance.ai/research-paper/governing-through-the-cloud)).
- **Meaningfulness**: Targets should address fundamental aspects of AI development that actually shape capabilities and risks. Regulating superficial aspects like user interfaces might be easy but won't prevent the emergence of dangerous capabilities. Core inputs like compute and data, however, directly determine what kinds of AI systems can be built ([Anderljung et al., 2023](https://arxiv.org/abs/2307.03718))

**In the AI development pipeline, several intervention points meet these criteria.** Early in development, we can target the compute infrastructure required for training and the data that shapes model capabilities. During and after development, we can implement safety frameworks, monitoring systems, and deployment controls ([Anderljung et. al, 2023](https://arxiv.org/abs/2307.03718);[ Heim et al., 2024](https://www.governance.ai/analysis/computing-power-and-the-governance-of-ai);[ Hausenloy et al., 2024](https://arxiv.org/abs/2412.03824)). Each target offers different opportunities and faces different challenges, which we'll explore in the following sections.
