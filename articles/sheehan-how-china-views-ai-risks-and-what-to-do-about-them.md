---
title: "How China Views AI Risks and What to do About Them"
author:
  - "Matt Sheehan"
  - "Scott Singer"
source_url: "https://carnegieendowment.org/research/2025/10/how-china-views-ai-risks-and-what-to-do-about-them"
published: 2025-10-16
created: 2026-07-02
accessed: 2026-07-02
description: "A new standards roadmap reveals growing concern over risks from abuse of open-source models and loss of control over AI."
tags:
  - "article-importer"
---{++{"author":"Luc's AI","timestamp":1785090685989}@@

%%
Add discussion note here:

...

%%++}

![How China Views AI Risks and What to do About Them](https://assets.carnegieendowment.org/_/eyJrZXkiOiJzdGF0aWMvbWVkaWEvaW1hZ2VzL2lTdG9ja19DaXJjdXQgYm9hcmQgdGV4dHVyZV8xNDIweDc3MC0xLmpwZyJ9)

Source: Getty

A new standards roadmap reveals growing concern over risks from abuse of open-source models and loss of control over AI.

China’s most influential AI standards body released a comprehensive articulation of how technical experts and policy advisers in China understand AI risks and how to mitigate them.

[The AI Safety Governance Framework 2.0](https://www.cac.gov.cn/2025-09/15/c_1759653448369123.htm),[1](#footnote-1) released in September, builds on an earlier version of the framework released a year prior. Alongside the Chinese Communist Party’s (CCP) unwavering focus on “information content risks” from AI, Framework 2.0 responds to the advances of AI over the past year, such as the global proliferation of open-source models and the advent of reasoning models. It represents a significant evolution in risks covered, including those tied to labor market impacts and chemical, biological, radiological, and nuclear (CBRN) weapon misuse. And it introduces more sophisticated risk mitigation measures, establishing a rubric to categorize and grade AI risks that sector-specific regulators should adapt to their domain.

The framework is not a binding regulatory document. But it offers a useful datapoint on how China’s AI policy community is thinking about AI risks. It could also preview what technical AI standards—and possibly regulations—are around the corner. Given China’s massive footprint in AI development, the impact of those standards will ripple out across the world, affecting the trajectory of the technology itself.

### Who’s Behind the Framework?

Studying the framework offers a window into the CCP’s deliberative process for technology policy—how the party-state works to understand emerging technology before charting a path forward. The project has been guided by the Cyberspace Administration of China (CAC), the country’s most powerful regulator of the internet, data, [and AI](https://carnegieendowment.org/research/2024/02/tracing-the-roots-of-chinas-ai-regulations?lang=en). The framework was released by two organizations under the CAC: the body charged with formulating many technical AI standards in China (TC260) and the country’s computer emergency response center (CNCERT-CC).

While officially housed under TC260 and CNCERT-CC, the framework was a cross-organizational effort that brought together many of China’s leading experts on AI policy, evaluation, and technical standards. The acknowledgments section of the document includes the country’s most influential government-adjacent technical organizations, as well as leading research labs, universities, and companies including Alibaba and Huawei. The framework’s development through this expert coalition—bridging regulatory, academic, and commercial stakeholders—suggests it may serve as both a technical reference and a foundation for future policy thinking.

The document contains sections on principles for governance, a multilayered taxonomy of risk types, technical mitigations, and governance measures, all of them mapping onto and pointing toward one another. At its core is the pairing of specific risks with technical countermeasures intended to address them, which we will explore below. The section on “comprehensive governance measures” focuses on a wider range of policy tools to reduce risks. One particularly notable recommendation is the call for “establishing an AI safety assessment system.” While China has a growing ecosystem of organizations conducting safety evaluations, measurement science [remains a relatively immature field](https://arxiv.org/pdf/2503.05336), both in China and around the world. The creation of a highly effective evaluation ecosystem will be critical as China attempts to advance frontier safety without the need for heavy-handed regulatory interventions.

### What’s Changed in the Latest Version?

Framework 2.0 contains substantial updates compared to the initial version, offering more comprehensive, detailed, and actionable discussion of risks and potential mitigations. Substantively, it deepens discussion around risks from open-source models, employment and other social impacts, and catastrophic risks.

This version is significantly more focused on the governance of open-source models, driven by their rapid proliferation by Chinese developers. While the Chinese government has been generally supportive of open-source models, this document represents the first authoritative discussion of risks from models with open weights. Those risks include the downstream propagation and amplification of model defects, which could create vulnerabilities in open-source base models that could cascade through the ecosystem as they are fine-tuned and deployed by users. The framework also warns that open-source foundation models will make it “easier for criminals to train ‘malicious models.’” While the technical mitigations to open-source risks offered in the framework are unsatisfying—the proposed countermeasure is simply that “the assessment of security flaws propagation from foundation models and open-source models should be strengthened”—the very acknowledgment of potential risks from open-source model misuse represents a significant development.

Second, Framework 2.0 includes a new discussion of labor market impacts and a deeper interrogation of broader societal risks from AI. The framework notes that “the value of labor as a production factor is diminished, resulting in a significant decline in demand for traditional labor.” This is a marked upgrade over the brief and ambiguous reference to labor in the first framework, which stated that AI was “accelerating the reconstruction of traditional industry modes, transforming traditional views on employment, fertility, and education, bringing challenges to stable performance of traditional social order.” The framework also raises concerns that reliance on AI tools could erode “independent learning, research, and creative capacity.” In sensitive fields like biology and genetics, AI will introduce new scientific ethics risks as biological information becomes more widely accessible and emotional dependence on AI systems for “anthropomorphic interaction” deepens.

Third, Framework 2.0 offers a deeper discussion of catastrophic risks. The framework warns of “loss of control over knowledge and capabilities of nuclear, biological, chemical, and missile weapons,” representing perhaps the most detailed acknowledgment by the Chinese government that modern AI training inevitably incorporates dual-use knowledge. The framework warns that “extremist groups and terrorists may be able to acquire relevant knowledge” through AI systems’ “retrieval-augmented generation capabilities.” One of the technical countermeasures proposed to address these risks is to “ensure exclusion of sensitive \[training\] data in high-risk fields such as nuclear, biological, and chemical weapons and missiles.”

In addition to risks around CBRN misuse, the framework also discusses loss of human control over advanced AI systems. A new appendix on “Fundamental Principles for Trustworthy AI” places the discussion of loss of control at the top of the list, which states, “A human control system should be established at critical stages of AI systems to ensure that humans retain the final decision-making authority.” As a countermeasure to loss of control risks, the framework suggests implementing “mechanisms such as circuit breakers and one-click control” that could be used in “extreme situations.” In a Chinese-language [expert explainer of Framework 2.0](https://www.cac.gov.cn/2025-09/28/c_1760779758683488.htm), Beijing Institute of Technology Professor Hong Yanqing notes that he sees the discussion of potential extreme risks as one of the most important updates, writing that it has “brought the existential risks that AI might bring (such as using AI to develop weapons of mass destruction, or AI evolving uncontrollable behavior) into policy considerations.” While not a perfect proxy for how the framework will shape future regulation and implementation efforts, these explainers offer useful insights into how influential scholars interpret the document.

One key question is how the CCP prioritizes among the nearly thirty risks covered in the document. Control over politically sensitive content has been the core driver of China’s binding AI regulations to date, with additional concerns such as data privacy, discrimination, and labor impacts playing a supplementary role. That foregrounding of content controls is unlikely to change, but the heightened attention to open-source models, CBRN threats, and loss of human control demonstrates an attempt to proactively consider potential emerging large-scale risks.

### Implementation

Like the U.S. National Institute of Standards and Technology’s (NIST) 2022 [AI Risk Management Framework](https://www.nist.gov/system/files/documents/2022/08/18/AI_RMF_2nd_draft.pdf), China’s AI Safety Governance Framework 2.0 offers nonregulatory guidance that could inform technical standards or regulation to address risks. But China’s system is likely to translate it into binding technical standards and regulatory tools much faster.

This translation process is already beginning. In January 2025, TC260 released a draft “AI Safety Standards System (V1.0)” [that mapped out](https://aisafetychina.substack.com/p/ai-safety-in-china-19?open=false#%C2%A7technical-standards-plans-by-multiple-institutions-include-frontier-risks) the current and future technical standards needed to implement the original framework, which had been released just four months prior. Over the past nine months, some of those [standards covering the labeling of AI-generated content](https://www.chinalawtranslate.com/en/ai-labeling/) have been finalized and put into effect.

Framework 2.0 also has ambitions to shape sectoral AI regulations. A key update to the framework is the introduction of a risk categorization and grading system, which takes into account three factors: the level of intelligence, nature of application, and scale of application. Just ten days after the release of Framework 2.0, TC260 issued an [open call](https://aisafetychina.substack.com/p/ai-safety-in-china-22) for organizations to participate in the drafting of a formal standard for risk categorization and grading. This categorization system remains relatively high-level and a bit bureaucratic, but the authors call for sectoral regulators to adopt and adapt the system for standards and regulations in their domains.

### International AI Diplomacy or Domestic Driver of Standards?

One key question is whether the framework is primarily directed at international audiences or domestic actors. The answer to that question has major implications for how the document is interpreted. If it’s primarily internationally focused, it should be read first and foremost as a part of China’s AI diplomacy efforts. But if its main audience is domestic, that greatly increases the chances that it represents a real reflection of Chinese thinking on these risks and a roadmap to future standards and regulatory actions.

Framework 2.0 states that version 1.0 was created “to implement the \[Chinese government’s\] Global AI Governance Initiative and promote consensus and coordinated efforts of AI safety governance among governments.” That international focus is also supported by the fact that both versions released an official English translation alongside the Chinese version. A few places in the document also call for forms of international cooperation, such as information sharing on AI threats as they emerge.

But many aspects of the document and its release suggest it is directed primarily at domestic actors: Chinese standards bodies, government ministries, and AI developers. The framework’s track record of driving the creation of domestic AI standards suggests that its main audience and impacts are at home. It was also released in mid-September as part of the CAC’s annual “China Cybersecurity Week”—a thoroughly domestic event—not at the United Nations General Assembly the following week. Instead, China used the UN meetings to debut its new “ [AI+ International Cooperation Initiative](https://www.globaltimes.cn/page/202509/1344391.shtml),” a relatively vague call for other countries to follow China’s own playbook for [diffusing AI throughout its economy](https://mattsheehan.substack.com/p/chinas-big-ai-diffusion-plan-is-here).

On balance, the document appears to be primarily domestically focused, providing the wider Chinese bureaucracy with an actionable roadmap for new technical standards and other regulatory tools. Internationally, the document is a way for China to lead by example—offering other countries a fleshed-out “Chinese approach” to addressing AI risks—but not laying the groundwork for any specific international agreement on AI.

### A Technical Roadmap for Balancing Innovation and Safety

Framework 2.0 comes as the CCP is calling for leveraging AI to engineer a massive upgrade across China’s economy, society, and government through its [AI+ Plan](https://carnegieendowment.org/emissary/2025/09/ai-china-90-percent-economy-why-wont-work?lang=en). While recognizing that AI could help [solve many of China’s current problems](https://carnegieendowment.org/research/2025/07/chinas-ai-policy-in-the-deepseek-era?lang=en), including enduring deflationary pressures and an aging population, this document reflects some of the party’s fears: its ability to control the information environment; the socioeconomic impacts of AI across work and education; and risks that AI could escape human—and therefore the party’s—control.

Faced with these competing needs for developing AI, and managing its risks, China is hoping it can have its cake and eat it too. The framework suggests that China’s AI policy community believes the key to that is a rich ecosystem of technical standards and model evaluations. These can be highly iterative, light-touch, and technically sophisticated mechanisms developed jointly with leading technologists. Ideally, they will create guardrails around the technology without the need for burdensome new regulations. Though these standards remain immature today, and China’s evaluation system for frontier AI risks lags behind the United States, these are clearly growth areas where the party is placing significant bets.

As China seeks to balance its development and safety imperatives, it currently weighs development opportunities more heavily than risk in both rhetoric and practice. But in getting deeper into the technical weeds of risks and countermeasures, Beijing may be giving real weight to what has been predominantly symbolic rhetoric on safety.

Carnegie does not take institutional positions on public policy issues; the views represented herein are those of the author(s) and do not necessarily reflect the views of Carnegie, its staff, or its trustees.
