---
id: 'd672123c-00bd-48bc-9d32-6056802d2f62'
title: "Control inside AI companies"
tldr: "By 2026 control was no longer only a research topic. AI companies run monitors over their own coding agents, and outside groups test those monitors. A Redwood researcher describes what is already running, and Google DeepMind describes its plan."
summary_for_tutor: "Field part of Unit 2 of AI Control Fundamentals. Two sources. (1) The first 10 minutes of Aryan Bhatt's FAR.AI talk 'The high stakes control roadmap: now to the singularity'. Bhatt leads Redwood's high-stakes control team. He describes AI companies' published plans (frontier safety frameworks with control-flavoured mitigations and evaluations, risk reports, third-party review), what companies actually run (asynchronous chain-of-thought monitors at OpenAI and Anthropic that escalate to human review, some real-time monitoring, capability evaluations, standard cybersecurity, humans noticing what agents do, sandboxing), outside evaluation (static monitor benchmarks, automated and human red-teaming, METR's embedded red-teaming and reports), and his view that near-term catastrophic risk from misalignment is quite low mostly because current AIs are not capable enough, while current techniques may not suffice later. (2) Google DeepMind's blog post 'Securing the future of AI agents' (June 2026) summarising its AI Control Roadmap: agents treated as potential insider threats, a threat model built on MITRE ATT&CK, detection by trusted AI supervisors, prevention and response by blocking, three metrics (coverage, recall, time-to-response), asynchronous review for low-risk reversible actions and real-time blocking for high-risk ones, detection levels D1 to D4 and response levels R1 to R3 tied to model capability, and a prototype asynchronous monitor run over a million coding-agent tasks, where most flagged events came from misinterpretation or overeagerness rather than adversarial intent. Two questions: the first is not scored, the second (two measures and one outside check) is scored. The first connects Google DeepMind's severity-based rule to the unit's high-stakes and low-stakes distinction. Any reasoned answer is fine."
reading_minutes: 17
tutor_minutes: 9
---
#### Text
content::
Aryan Bhatt leads the high-stakes control team at Redwood Research. In the first ten minutes of this talk he describes what AI companies say they will do about control and what they already run. He refers to the companies' published safety policies (Anthropic's RSP, Google DeepMind's Frontier Safety Framework, OpenAI's Preparedness Framework).

#### Video
source:: [[../video_transcripts/far-ai-aryan-bhatt-the-high-stakes-control-roadmap-now-to-the-singularity]]
from:: 0:00
to:: 10:44

#### Text
content::
Next, one AI company's own account. In June 2026 Google DeepMind published its AI Control Roadmap. This is the company's short summary of it. As you read, look for where it uses the idea from the first half of this unit.

#### Article
source:: [[../articles/shah-securing-the-future-of-ai-agents]]
from:: How we’re securing internal systems against increasingly capable and imperfectly aligned AI
to:: We intend to build on these frameworks to confidently deploy capable AI today while we continue to build a secure foundation for the future.

#### Question: Open
id:: ede9f6e9-f600-4991-a591-0cc2a9fe8589
content::
Google DeepMind says low-risk, reversible actions can be reviewed after a delay, and high-risk actions must be blocked in real time. Compare this with the high-stakes and low-stakes distinction from the start of this unit. Do the two rules always give the same answer? Try to think of a case where they might not.
force-feedback:: first
feedback-instructions:: The learner compares Google DeepMind's rule (response by severity: asynchronous review for low-risk, reversible actions, synchronous blocking for high-risk ones) with the unit's distinction (high-stakes threats need few actions, each incriminating, so suspicious actions must be stopped before they take effect, while low-stakes threats need many weakly suspicious actions, so later review can work). Both rest on the same question: can the harm happen before a delayed review catches it? They mostly agree. Cases where they could come apart: an individually low-risk-looking action that is one of very few needed for a catastrophe, such as a subtle backdoor in a critical library (the unit's view says high-stakes, a severity rule might treat it as routine), or a high-risk-looking action that is easily reversed. Do not say which rule is better. Accept any reasoned case, and accept a reasoned argument that the rules always agree. Reply in at most five sentences. Up to two turns. No generic praise.

#### Question: Open
id:: 662c126f-98b1-40dc-9d8c-d23ef64c8a74
content::
From the talk and the post: name two control measures AI companies already run, and one way people outside the companies check whether those measures work.
force-feedback:: first
assessment-instructions:: Score out of 100. 60: two control measures AI companies already run, 30 each. Fitting measures: monitors that read agents' reasoning or actions and send suspicious cases to human review, real-time monitoring or blocking of harmful actions, capability evaluations, standard cybersecurity, sandboxing or containment of agents, humans watching what agents do, or Google DeepMind's prototype monitor run over a million coding-agent tasks. 40: one way outsiders check whether the measures work, such as third-party review of companies' risk reports, benchmarks that test monitors, red-teaming by outside groups that try to get attacks past the monitors, or METR's reports. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Companies already run monitors that read their coding agents' reasoning and send suspicious cases to humans, and they sandbox their agents. Outside groups such as METR red-team those monitors and publish what they find."
feedback-instructions:: Measures named in the sources: asynchronous chain-of-thought monitors that escalate to human review (OpenAI and Anthropic, per Bhatt), some real-time monitoring, capability evaluations, standard cybersecurity, sandboxing and containment, trusted AI supervisors that review agents' reasoning and actions and can block harmful actions (Google DeepMind), and Google DeepMind's prototype asynchronous monitor over a million coding-agent tasks. Outside checks: third-party review of companies' risk reports, static monitor benchmarks, automated and human red-teaming, and METR's embedded red-teaming exercise and reports. Reply in at most three sentences: confirm what is right, correct anything wrong. One turn, no generic praise. Tell them to move on.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan. "The high stakes control roadmap: now to the singularity." FAR.AI. [youtube.com](https://www.youtube.com/watch?v=rttkT223KHk)

Shah, Rohin, and Four Flynn. "Securing the future of AI agents." *Google DeepMind blog*, 18 June 2026. [deepmind.google](https://deepmind.google/blog/securing-the-future-of-ai-agents/)
:::
