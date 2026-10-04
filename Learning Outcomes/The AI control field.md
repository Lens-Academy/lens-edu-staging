---
id: 'c05ed183-2911-4707-88f1-6ba5f9d53e1d'
learning-outcome: "Place a piece of AI control work within the field: identify what kind of control work it is (for example control evaluations, countermeasures such as better monitors, human review and escalation processes for deployed agents, or external evaluation of deployed control measures), use that to say what access to developers' systems and what independence from developers it needs, and from that say which kind of organisation is placed to do it, with a real example (for example a research nonprofit such as Redwood Research, a government institute such as the UK AI Security Institute, an AI company, or a third-party evaluator such as METR)."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - James agent ready-34
---
%% Written for AI Control Fundamentals Unit 2. The size of the field is tested separately in [[Size of the AI control field]]. The facts about organisations come from the Lens page "AICF - Who works on AI control" (October 2026), which links every source. Update the rubric when that page is updated. %%
## Test:
id:: a3d7a99a-4ddc-4c08-99e5-ba9c1d2d7344

#### Question: Open
id:: 0d2fa93d-b838-47ab-afc2-586341beeb07
content::
Three pieces of AI control work:

(A) A team trains a small model that is too weak to be scheming on examples of subtly sabotaged code, so that it catches more of the bad changes a stronger model makes, and publishes the method and the data.
(B) A team decides who reviews the actions that a monitor flags on the coding agents writing most of the code for a frontier model, how quickly each flag must be reviewed, and how a serious finding is escalated, and then runs this routine every day.
(C) A team tries to slip attacks past the monitoring systems of several frontier AI developers, and publishes how well each developer's measures held up.

For each: what kind of control work is it (which research area)? What access to developers' systems, and what independence from developers, does it need? So which kind of organisation is placed to do it? Name one real example of such an organisation.
placeholder:: Take A, then B, then C
assessment-instructions:: Score out of 100. Three pieces of work, 33 points for (A), 33 for (B) and 34 for (C). For each: 10 for a fitting kind of work or research area, 12 (13 for C) for what access or independence the work needs, 6 for a fitting kind of organisation that follows from it, and 5 for one real example of that kind of organisation. (A): the area is developing countermeasures, here a better trusted monitor (accept equivalent names such as monitoring, uplift of trusted models, countermeasures studied in isolation, or detection of sabotage). Access: it needs only models and data, not a developer's real systems. Fitting organisations: a research nonprofit such as Redwood Research, a government institute such as the UK AI Security Institute, an academic group, or an AI company's research team such as Anthropic's. Any of these with the access reason gets full marks. (B): the area is running control in practice through human processes for review and escalation (accept equivalent names such as prototyping human processes, control in deployment, or internal monitoring and auditing). Access: it needs the developer's own agents, logs and staff, every day. Fitting organisation: mainly the AI developer itself, for example OpenAI, Google DeepMind or Anthropic. Also accept an outside auditor or government body if the answer says how it would get that daily access. (C): the area is external evaluation or red-teaming of control measures as deployed (accept equivalent names such as third-party evaluation, external red-teaming, or control evaluations of real deployments). Independence: the results compare several developers, so they are only trusted if the team is independent of them (mentioning that it still needs their cooperation for access is welcome but not required). Fitting organisation: a third-party evaluator such as METR, or a government institute such as the UK AI Security Institute. An AI company's own team fits poorly here, so it earns none of the 6 organisation points and at most half of the 13 reasoning points. Give credit for each point whenever the answer shows the idea, in any wording. Accept another real organisation or another reasoned area, including areas from the UK AI Security Institute's list, if it fits and the reason is sound. Model answer, for the feedback, not a grading checklist: "(A) is developing a countermeasure: a better trusted monitor. It needs only models and data, not a developer's real systems, and the result is shared, so a research nonprofit such as Redwood Research or a government institute such as the UK AI Security Institute can do it. (B) is running control in practice through a human review and escalation process. Mainly the AI developer itself can do it, for example OpenAI, because it needs the developer's own agents, logs and staff every day. (C) is independent evaluation of deployed control measures. A third-party evaluator such as METR fits, because the report has to be independent of the developers, though it still needs their cooperation to get access."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner put (B) at an outside organisation without saying how it gets access, ask what access the work needs. If they put (C) at an AI company, ask who would trust a comparison written by one of the companies being compared. If it helps, mention that OpenAI says it monitors almost all of its internal coding traffic and sends higher-severity cases to human review, as an example of (B) done in-house. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Areas of control work]]
notes:: Greenblatt's eight areas of control work, excerpted.
## Lens:
source:: [[../Lenses/AICF - Control inside AI companies]]
notes:: Bhatt on what AI companies already run, and Google DeepMind's AI Control Roadmap summary.
## Lens:
source:: [[../Lenses/AICF - Who works on AI control]]
notes:: Lens page on organisations, people and size, October 2026, every line sourced.
## Lens:
source:: [[../Lenses/AICF - Research areas from the UK AI Security Institute]]
notes:: A second, funder-facing map of control research areas.
