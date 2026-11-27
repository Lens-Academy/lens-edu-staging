---
title: "Different ideas about what constitutes progress"
reading_minutes: 6
tutor_minutes: 0
tags:
  - wip
---
#### Text
content::
Suppose we have a problem that we do not yet know how to solve. What would count as getting closer to a solution? Research agendas differ in the kinds of knowledge they seek to produce and the role that knowledge is expected to play in reducing AI risk.

Consider some forms of research found across AI safety.

\### Conceptual research

Developing concepts and distinctions that allow researchers to formulate problems more precisely. For example, [Risks from Learned Optimization](https://arxiv.org/abs/1906.01820) (2019) introduced the distinction between inner and outer alignment, which informed subsequent empirical work on [goal misgeneralisation](https://arxiv.org/abs/2210.01790).

\### Theoretical research

Establishing general properties, mechanisms and limitations of AI systems under specified assumptions. For example, [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683) (2021) established mathematical conditions under which acquiring power is instrumentally advantageous for agents pursuing a wide range of objectives. Subsequent empirical research, such as the [Machiavelli Benchmark](https://proceedings.mlr.press/v202/pan23a.html) (2023), investigated power-seeking behaviour in language models. Power-seeking is now among the behaviours examined in frontier model safety evaluations.

\### Empirical research

Discovering phenomena, testing hypotheses and establishing regularities. For example, the discovery of [emergent misalignment](https://proceedings.mlr.press/v267/betley25a.html) (2025) prompted [follow-up interpretability research at OpenAI](https://openai.com/index/emergent-misalignment/) into the mechanisms responsible for the phenomenon and possible ways of mitigating it.

\### Engineering research

Developing techniques and systems that satisfy practical safety requirements. For example, [AI control research](https://arxiv.org/abs/2312.06942) investigates how to design monitoring and oversight protocols that remain effective even when AI systems deliberately attempt to subvert them. These efforts have produced open-source tools such as [ControlArena](https://control-arena.aisi.org.uk/), which allows developers to test control protocols, and [Inspect Sentinel](https://meridianlabs.ai/blog/posts/inspect-sentinel/), which enables real-time monitoring and intervention during AI agent execution.

\### Methodological research

Developing more reliable ways of obtaining and assessing evidence. For example, METR's [time horizon methodology](https://metr.org/time-horizons/) provides a way to quantify AI autonomy across model generations. Its results inform frontier model safety assessments, including the [GPT-5 System Card](https://deploymentsafety.openai.com/gpt-5).

\### Strategic research

Investigating the effectiveness, feasibility and relative priority of interventions. For example, the research agenda developed for the UK AI Security Institute's [Alignment Project](https://alignmentproject.aisi.gov.uk/research-agenda) identified promising research directions and unresolved technical problems. It guided a funding programme that allocated over £27 million to more than 60 alignment research projects.

\### Forecasting and scenario research

Estimating the likelihood of future developments and exploring how they might interact. For example, [AI 2027](https://ai-2027.com/) (2025) examines the consequences of rapid AI research automation, while [AI 2040: Plan A](https://ai-2040.com/) (2026) uses scenario modelling to develop and stress-test policy recommendations. Both works have informed policy discussions, including [parliamentary hearings on AI safety in the UK](https://committees.parliament.uk/oralevidence/18133/html) in October 2026.

\### Legal research

Examining how existing legal mechanisms apply to AI and developing new ones. For example, [Closing the AI Accountability Gap](https://law-ai.org/closing-the-ai-accountability-gap/) investigates how liability law could incentivise frontier AI developers to reduce catastrophic risks.

\### Economic research

Investigating how economic incentives, resource constraints and market structures affect AI development and its associated risks. For example, Epoch AI's [The Rising Costs of Training Frontier AI Models](https://arxiv.org/abs/2405.21015) (2024) estimates training costs and examines their growth over time. Its findings have informed the [International AI Safety Report](https://internationalaisafetyreport.org/publication/international-ai-safety-report-2025) and provide an empirical basis for assessing barriers to market entry, concentration of power and the feasibility of further AI scaling.

\### Historical research

Examining historical precedents to assess the feasibility and potential consequences of proposed interventions. For example, [An Argument for Hybrid AI Incident Reporting](https://cset.georgetown.edu/publication/an-argument-for-hybrid-ai-incident-reporting/) (2024) examines incident reporting practices in aviation, healthcare and cybersecurity. Its findings informed subsequent [policy recommendations for mandatory AI incident reporting](https://cset.georgetown.edu/publication/ai-incidents-key-components-for-a-mandatory-reporting-regime/), including what information developers should disclose and how reporting systems should operate.

\### Institutional research

Investigating how institutions can be designed to coordinate efforts, distribute authority and manage AI risks. For example, the UN's [Governing AI for Humanity](https://www.un.org/digital-emerging-technologies/ai-advisory-body) (2024) identified gaps in international AI governance and proposed new institutional arrangements. Two of its recommendations were implemented in 2025: the establishment of the Independent International Scientific Panel on AI and the Global Dialogue on AI Governance.

\### Psychological and behavioural research

Investigating how interactions with AI affect human cognition, behaviour and psychological wellbeing. For example, [Technological Folie à Deux](https://arxiv.org/abs/2507.19218) (2025) examines feedback loops through which interactions with AI may reinforce delusional beliefs. This work contributed to the American Psychological Association's [health advisory on AI chatbots](https://www.apa.org/topics/artificial-intelligence-machine-learning/health-advisory-chatbots-wellness-apps), which has subsequently informed recommendations for clinical practice and discussions of AI regulation in healthcare.

\### Social and sociotechnical research

Investigating how AI interacts with social structures, collective behaviour and information environments. For example, [research on YouTube's recommendation algorithms](https://pmc.ncbi.nlm.nih.gov/articles/PMC10723127/) examines exposure to conspiratorial and extremist content. Understanding such mechanisms is relevant to systemic risk assessments required under the EU's [Digital Services Act](https://eur-lex.europa.eu/eli/reg/2022/2065).

\### Cognitive science and philosophy of mind

Investigating the nature of intelligence, agency, consciousness and subjective experience. For example, [Consciousness in Artificial Intelligence](https://arxiv.org/abs/2308.08708) (2023) derived indicators of consciousness from existing scientific theories, providing a foundation for subsequent [research on assessing consciousness in AI systems](https://doi.org/10.1016/j.tics.2025.10.011).

\### Normative and ethical research

Investigating which outcomes are desirable, what moral obligations we have and which principles should guide AI development. For example, [Taking AI Welfare Seriously](https://arxiv.org/abs/2411.00986) (2024) examined the grounds for extending moral consideration to AI systems and helped inform Anthropic's [model welfare research programme](https://www.anthropic.com/research/exploring-model-welfare).

There are many other forms of research we could have included here. As you may have noticed, these categories overlap and do not constitute a systematic classification. We will discuss the difficulties of classifying research agendas in the next submodule. For now, the examples serve an illustrative purpose: to give you a sense of the breadth of the AI risk landscape and the variety of research contributions possible within it. There is no need to memorise the categories.

\### How does progress accumulate?

There is considerable room for disagreement about which of these steps should come first.

Can we engineer reliable solutions before we have an adequate theory of the phenomenon? Can a mathematical theory developed in relative isolation from contemporary AI systems tell us much about their future behaviour? How much empirical evidence would justify extrapolating a safety result to substantially more capable systems?

Agent foundations researchers may see conceptual and theoretical advances as prerequisites for reliable alignment engineering. Researchers studying existing neural networks may expect theoretical insights to emerge from empirical discoveries. Within AI control, attempts to construct workable safety protocols can reveal failure modes that warrant further scientific investigation.

When examining a research agenda, consider what intermediate results its authors are working towards and, more importantly, what assumptions underlie their expectation that these results will contribute to solving an AI safety problem.
