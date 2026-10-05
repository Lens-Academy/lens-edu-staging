---
id: 'd672123c-00bd-48bc-9d32-6056802d2f62'
title: "Control inside AI companies"
tldr: "By 2026 control was no longer only a research topic. AI companies run monitors over their own coding agents, and outside groups test those monitors. A Redwood researcher describes what is already running, Google DeepMind describes its plan, and a UK government team reports what it found when it attacked company monitors."
summary_for_tutor: "Field part of Unit 2 of AI Control Fundamentals. Three sources. (1) Aryan Bhatt's FAR.AI talk 'The high stakes control roadmap: now to the singularity', 4:53 to 10:44. Bhatt leads Redwood's high-stakes control team. The lens intro mentions that earlier in the talk he covered the companies' published plans (frontier safety frameworks, risk reports, third-party review of them), but the learner does not watch that part. The excerpt covers what companies actually run (asynchronous chain-of-thought monitors at OpenAI and Anthropic that escalate to human review, some real-time monitoring, capability evaluations, standard cybersecurity, humans noticing what agents do, sandboxing), outside evaluation (static monitor benchmarks, automated and human red-teaming, METR's embedded red-teaming and reports), and his view that near-term catastrophic risk from misalignment is quite low mostly because current AIs are not capable enough, while current techniques may not suffice later. (2) The section 'Scaling security as AI gets smarter' of Google DeepMind's blog post 'Securing the future of AI agents' (June 2026), summarising its AI Control Roadmap: today it monitors visible chain of thought, but models that know they are monitored or reason without visible text will need behaviour analysis and inspection of internals. Asynchronous review for low-risk reversible actions and real-time blocking for high-risk ones. Detection levels D1 to D4 and response levels R1 to R3 tied to model capability. The learner read the first half of this post in Unit 1 (agents treated as potential insider threats, trusted AI supervisors, the three metrics coverage, recall and time-to-response, and the prototype monitor over a million coding-agent tasks), and OpenAI's internal monitoring post. (3) The opening and the section 'Our evaluations of frontier control monitors' of the UK AI Security Institute's blog post 'How our Control Red Team is stress-testing frontier monitors' (July 2026): developers already deploy agents under LLM monitors, AISI's new Control Red Team attacks those monitors, it tested Google DeepMind's asynchronous reasoning monitor (reviewing reasoning after the agent acts) and found several vulnerabilities, including an agent pretending to hallucinate a user instruction, and it tested successive versions of Anthropic's synchronous internal agentic coding monitor (reviewing each action before it executes) and found vulnerabilities in every version. Attacks exploited gaps in monitor prompts, weaknesses in the LLM itself, and hard-coded rules that decide which actions reach the monitor. Two questions: the first is not scored, the second (two outside checks, and what testing against deliberate attacks shows that a company's record of flags cannot) is scored. The first connects Google DeepMind's severity-based rule to the unit's high-stakes and low-stakes distinction. Any reasoned answer is fine."
reading_minutes: 12
tutor_minutes: 9
---
#### Text
content::
Aryan Bhatt leads the high-stakes control team at Redwood Research. In this six-minute part of a talk he describes what AI companies already run, how people outside the companies check it, and how much risk he thinks there is today. Earlier in the talk he went through the companies' published safety policies (Anthropic's RSP, Google DeepMind's Frontier Safety Framework, OpenAI's Preparedness Framework), which include risk reports and third-party review of them.

#### Video
source:: [[../video_transcripts/far-ai-aryan-bhatt-the-high-stakes-control-roadmap-now-to-the-singularity]]
from:: 4:53
to:: 10:44

#### Text
content::
Next, one AI company's own account. In Unit 1 you read the first half of Google DeepMind's June 2026 summary of its AI Control Roadmap. Here is the part about how its defences change as models get more capable. As you read, look for where it uses the idea from the first half of this unit.

#### Article
source:: [[../articles/shah-securing-the-future-of-ai-agents]]
from:: ## Scaling security as AI gets smarter
to:: determines the Prevention and Response level (R1-R3).

#### Text
content::
Finally, a government team that tests these monitors from outside. In July 2026 the UK AI Security Institute described what its new Control Red Team found when it attacked the internal monitors of Google DeepMind and Anthropic. Notice which monitor reviews actions after they run and which reviews them before.

#### Article
source:: [[../articles/ai-security-institute-how-our-control-red-team-is-stress-testing-frontier-monitors]]
from:: As LLM agents become more autonomous, they have more opportunities to cause harm.
to:: so the best attack strategy avoids actions being sent to the monitor entirely.

#### Question: Open
id:: ede9f6e9-f600-4991-a591-0cc2a9fe8589
content::
Google DeepMind says low-risk, reversible actions can be reviewed after a delay, and high-risk actions must be blocked in real time. Compare this with the high-stakes and low-stakes distinction from the start of this unit. Do the two rules always give the same answer? Try to think of a case where they might not.
force-feedback:: first
feedback-instructions:: The learner compares Google DeepMind's rule (response by severity: asynchronous review for low-risk, reversible actions, synchronous blocking for high-risk ones) with the unit's distinction (high-stakes threats need few actions, each incriminating, so suspicious actions must be stopped before they take effect, while low-stakes threats need many weakly suspicious actions, so later review can work). Both rest on the same question: can the harm happen before a delayed review catches it? They mostly agree. Cases where they could come apart: an individually low-risk-looking action that is one of very few needed for a catastrophe, such as a subtle backdoor in a critical library (the unit's view says high-stakes, a severity rule might treat it as routine), or a high-risk-looking action that is easily reversed. If useful, point to the AISI post: Google DeepMind's monitor reviews reasoning after the agent acts, and Anthropic's coding monitor reviews each action before it executes. Do not say which rule is better. Accept any reasoned case, and accept a reasoned argument that the rules always agree. Reply in at most five sentences. Up to two turns. No generic praise.

#### Question: Open
id:: 662c126f-98b1-40dc-9d8c-d23ef64c8a74
content::
In Unit 1 you saw what Google DeepMind and OpenAI say their monitors catch. From the talk and the UK AI Security Institute post: name two ways people outside the companies check whether such monitors work. Then say what checks like these can show that a company's record of what its monitor flagged in everyday use cannot.
force-feedback:: first
assessment-instructions:: Score out of 100. 50: two ways outsiders check whether company monitors work, 25 each. Fitting checks: third-party review of companies' risk reports, static benchmarks that test monitors, automated red-teaming, human red-teaming, METR's embedded red-teaming and its reports, or the UK AI Security Institute's Control Red Team attacking company monitors. Two different kinds of red-teaming by different groups count as two. 50: what such checks can show that the everyday record cannot: how many deliberate attacks get past the monitor, or which weaknesses an attacker could use (as the AI Security Institute found in Google DeepMind's and Anthropic's monitors). A record of what was flagged in everyday use cannot show this, because a model trying to get past the monitor would avoid being flagged, so few alarming flags is also what a successful attacker would produce. An answer that says outside checks are "independent" or "less biased" without saying they test the monitor against deliberate attacks earns 20 of these 50. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "METR runs red-teaming exercises with companies and publishes reports, and the UK AI Security Institute's Control Red Team attacks company monitors directly. Checks like these show how many deliberate attacks get through and where the weak spots are. A company's record of what its monitor flagged cannot show that, because an AI trying to get past the monitor would make sure it is not flagged."
feedback-instructions:: Company measures, for context: asynchronous chain-of-thought monitors that escalate to human review (OpenAI and Anthropic, per Bhatt), some real-time monitoring, capability evaluations, standard cybersecurity, sandboxing and containment, and Google DeepMind's plan to block high-risk actions in real time. On the second part, the key idea is that only testing against deliberate attacks measures what a monitor misses. Outside checks: third-party review of companies' risk reports, static monitor benchmarks, automated and human red-teaming, METR's embedded red-teaming exercise and reports, and the UK AI Security Institute's Control Red Team, which attacked Google DeepMind's asynchronous reasoning monitor and successive versions of Anthropic's synchronous coding monitor and found vulnerabilities in every Anthropic version it tested. Reply in at most three sentences: confirm what is right, correct anything wrong. One turn, no generic praise. Tell them to move on.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Bhatt, Aryan. "The high stakes control roadmap: now to the singularity." FAR.AI. [youtube.com](https://www.youtube.com/watch?v=rttkT223KHk)

Shah, Rohin, and Four Flynn. "Securing the future of AI agents." *Google DeepMind blog*, 18 June 2026. [deepmind.google](https://deepmind.google/blog/securing-the-future-of-ai-agents/)

AI Security Institute. "How our Control Red Team is stress-testing frontier monitors." *AISI blog*, 23 July 2026. [aisi.gov.uk](https://www.aisi.gov.uk/blog/how-our-new-control-red-team-is-stress-testing-frontier-monitors)
:::
