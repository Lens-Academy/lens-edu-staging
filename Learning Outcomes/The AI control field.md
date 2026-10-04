---
id: 'c05ed183-2911-4707-88f1-6ba5f9d53e1d'
learning-outcome: "Place a piece of AI control work within the field: name a research area it belongs to (such as building settings and running control evaluations, studying control-relevant model capabilities, developing countermeasures such as monitoring, running control inside AI companies through infrastructure and human processes, independent evaluation of companies' control measures, or conceptual work), and say which kind of organisation is placed to do it, with a real example, and why, judged by what access and independence the work needs (nonprofit research groups such as Redwood Research, government institutes such as the UK AI Security Institute, AI companies, or third-party evaluators such as METR)."
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

(A) A team builds a test environment that imitates a computer cluster used for AI research. It has realistic tasks for an AI agent, plus harmful side tasks that a red team can secretly instruct the agent to attempt, so that different safety set-ups can be compared on how often they stop the attempts.
(B) A team decides who reviews the actions that a monitor flags on the coding agents writing most of the code for a frontier model, how quickly each flag must be reviewed, and how a serious finding is escalated, and then runs this routine every day.
(C) A team gets access to the monitoring systems of several frontier AI developers, tries to slip attacks past them, and publishes a public report comparing how well each developer's measures hold up.

For each, name a research area of AI control it belongs to, and say which kind of organisation is placed to do it, with one real example of an organisation that does this kind of work. Say why that kind of organisation fits.
placeholder:: Take A, then B, then C
assessment-instructions:: Score out of 100. Three pieces of work, 33 points for (A), 33 for (B) and 34 for (C). For each: 15 for a fitting research area, and the rest (18, 18 and 19) for a fitting kind of organisation with one real example and a reason based on what access or independence the work needs. Without a real example, at most two thirds of the organisation points. (A): the area is building control settings and running control evaluations (accept equivalent names such as settings or benchmarks for control, testing control protocols, or red-team versus blue-team evaluations). Fitting organisations include a government institute such as the UK AI Security Institute (it built ControlArena, a library for control experiments), a nonprofit research group such as Redwood Research, or an AI company such as Anthropic (it built SHADE-Arena with Scale AI and Redwood). Sound reasons include that the work does not need access to a company's real systems, or that the result is a shared tool. (B): the area is running control in practice through human processes for review and escalation (accept equivalent names such as prototyping human processes, control in deployment, or internal monitoring and auditing). The fitting organisation is mainly the AI developer itself, for example OpenAI, Google DeepMind or Anthropic, because the work needs its own agents, data and staff and runs every day. Also accept an outside auditor or government body if the answer gives a sound reason about how it would get that access. (C): the area is independent evaluation or red-teaming of control measures as deployed (accept equivalent names such as third-party evaluation, external red-teaming, or control evaluations of real deployments). The fitting organisation is a third-party evaluator such as METR, or a government institute such as the UK AI Security Institute, because the work needs independence from the developers, and it also needs their cooperation for access. An AI company's own team fits poorly because the report compares several developers and must be trusted by outsiders, so give at most half the organisation points for that. Give credit for each point whenever the answer shows the idea, in any wording. Accept another real organisation or another reasoned area, including areas from the UK AI Security Institute's list, if it fits and the reason is sound. Model answer, for the feedback, not a grading checklist: "(A) is building a control setting for control evaluations. The UK AI Security Institute does this kind of work (it built ControlArena), as does Redwood Research. It fits them because it does not need access to a company's real systems and the result is a shared tool others can use. (B) is running control in practice through a human review and escalation process. Mainly the AI developer itself can do it, because it needs the developer's own agents, logs and staff every day. OpenAI, for example, says it monitors almost all of its internal coding traffic and sends higher-severity cases to human review. (C) is independent evaluation of deployed control measures. A third-party evaluator such as METR fits, because the report has to be independent of the developers, though it still needs their cooperation to get access."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner put (B) at an outside organisation without saying how it gets access, ask what access the work needs. If they put (C) at an AI company, ask who would trust a comparison written by one of the companies being compared. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

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
