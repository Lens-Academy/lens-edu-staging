---
id: 'b80f9579-ba85-483f-bd63-92e0de9a96fb'
title: "Research areas from the UK AI Security Institute"
tldr: "A government fund's list of open problems in AI control, from August 2025. It sorts the work by threat (high-stakes failures, research sabotage, AIs secretly poisoning other AIs) and by method (risk modelling, better trusted monitors, chain-of-thought monitoring, the science of monitoring)."
summary_for_tutor: "Field part of Unit 2 of AI Control Fundamentals. The learner reads three short excerpts of 'Research Areas in AI Control (The Alignment Project by UK AISI)' (Alignment Forum, August 2025), a funder-facing list of research areas for the UK AI Security Institute's Alignment Project, co-authored by AISI staff and Redwood's Buck Shlegeris: the problem statement, why it matters, and the overview of seven subsections (three threat models, namely high-stakes or concentrated failures, research sabotage and covert malicious fine-tuning, and four cross-cutting areas, namely modelling risks, uplift of trusted models, chain-of-thought monitoring, and fundamental science of monitoring and red teaming), then the problem summaries of the high-stakes and research sabotage sections. The rest is collapsed. The post says the fund was over £15 million at the time. It later grew to £27m (see the Lens page 'Who works on AI control'). One ungraded question compares this list with Greenblatt's areas from the previous lens. Any reasoned mapping is fine."
reading_minutes: 6
tutor_minutes: 5
---
#### Text
content::
Greenblatt's list was written from inside Redwood. This one comes from a funder: the UK AI Security Institute (AISI), a government body, published it to say which control research its Alignment Project fund wanted to pay for. Its authors include AISI staff and Buck Shlegeris, Redwood's CEO (see the Works cited below), so it is not fully independent of Redwood. Notice that it sorts the work partly by threat, where Greenblatt sorted it by kind of work.

#### Article
source:: [[../articles/stastny-research-areas-in-ai-control-the-alignment-project-by-uk-aisi]]
from:: **Problem statement:**
to:: addressing different parts of the research agenda.

#### Article
from:: **Problem summary:** We are interested in research on concentrated failure
to:: potentially leading to rogue internal deployments or weight exfiltration

#### Article
from:: **Problem summary:** In the future, potentially scheming AIs will likely be used
to:: preventing us from controlling increasingly capable AI systems.

#### Question: Open
id:: 25cd1607-6774-451f-acda-3858f5fd51ab
content::
Pick one area from this list and find where it fits in Greenblatt's list of eight areas, or say why it does not fit any of them.
force-feedback:: first
feedback-instructions:: The learner maps one AISI area onto Greenblatt's eight areas: (1) settings and control evaluations, (2) control-relevant capabilities and model properties, (3) countermeasures in isolation, (4) experiments on actual AI usage, (5) software infrastructure and security, (6) human processes, (7) conceptual research, (8) nearer-term applications. Plausible mappings. High-stakes failures and research sabotage are threat models whose empirical work falls mostly under settings and control evaluations. Uplift of trusted models and chain-of-thought monitoring are mostly countermeasures developed in isolation, and partly capability studies. Modelling of risks is mostly conceptual research. Covert malicious fine-tuning has no single home and touches capabilities and countermeasures. Accept any mapping with a reason, and accept "it fits several" with a reason. The point is that the two lists cut the same field differently: one by threat, one by kind of work. Reply in at most four sentences. One turn. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Stastny, Julian, Tomek Korbak, Mojmir, Buck Shlegeris and Alan Cooney. "Research Areas in AI Control (The Alignment Project by UK AISI)." *AI Alignment Forum*, 1 Aug. 2025. [alignmentforum.org](https://www.alignmentforum.org/posts/rGcg4XDPDzBFuqNJz/research-areas-in-ai-control-the-alignment-project-by-uk)
:::
