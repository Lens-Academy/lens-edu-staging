---
id: 'c05ed183-2911-4707-88f1-6ba5f9d53e1d'
learning-outcome: "Place a piece of AI control work within the field: say what access to AI developers' systems and what independence from developers it needs, and from that say which kind of organisation is placed to do it, illustrated with a real organisation of that kind."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
%% Written for AI Control Fundamentals Unit 2. The size of the field is reading only, in the lens "AICF - Who works on AI control", and is not scored (the separate outcome "Size of the AI control field" is no longer used). The facts about organisations come from the Lens page "AICF - Who works on AI control" (October 2026), which links every source. Update the rubric when that page is updated. %%
## Test:
id:: a3d7a99a-4ddc-4c08-99e5-ba9c1d2d7344

#### Question: Open
id:: 0d2fa93d-b838-47ab-afc2-586341beeb07
content::
Three pieces of AI control work:

(A) A team releases an open-source software library that researchers use to run control experiments on AI agents. Researchers at several AI companies and research groups then use it.

(B) A team decides who reviews the actions that a monitor flags on the coding agents writing most of the code for a frontier model, how quickly each flag must be reviewed, and how a serious finding is escalated, and then runs this routine.

(C) Before a frontier developer starts using a new model as an agent internally, a team red-teams the monitors that will watch it: human red-teamers try to get attacks past those monitors on the developer's real setup. The result decides whether the internal deployment goes ahead.

For each: what access to developers' systems, and what independence from developers, does it need? So which kind of organisation is placed to do it? Illustrate with a real organisation of that kind.
placeholder:: Take A, then B, then C
assessment-instructions:: Score out of 100. Three pieces of work, 33 points for (A), 33 for (B) and 34 for (C). For each: 17 (18 for C) for what access to developers' systems or independence from developers the work needs, and 16 for a kind of organisation that follows from that reasoning, illustrated with a real organisation of that kind (11 if the kind fits but no real organisation is given, and at most 4 for a real organisation named with no reason that fits it). (A), an open-source library for control experiments: it needs only models, not a developer's real systems, because the library runs experiments on models anyone can use. Fitting organisations: a government institute such as the UK AI Security Institute, a research nonprofit such as Redwood Research, an academic group, or an AI company's research team. Any of these with the access reason gets full marks. (B), running the review and escalation routine for flagged agent actions: it needs the developer's own agents, logs and staff, every day. Fitting organisation: mainly the AI developer itself, for example OpenAI, Google DeepMind or Anthropic. Also accept an outside auditor or government body if the answer says how it would get that daily access. (C), red-teaming the monitors on the developer's real setup before an internal deployment. Access and independence, 18: 9 for saying it needs the developer's real setup and monitors before deployment, so it is done inside the developer or with deep access from it. 9 for a point about independence, for example that the developer would be judging its own safety, so outside review, or an outside red team given access, makes the result more credible. Also accept a reasoned case that no independence is needed for an internal go or no-go decision. Fitting organisation: the developer's own safety or red team, for example at Anthropic, Google DeepMind or OpenAI, or a third-party evaluator given access, such as METR. Either earns the full organisation points if it follows from the answer's own access and independence reasoning. In all three parts, the access and independence points are judged on the reasoning itself, whichever organisation is named. Do not take off points for naming no research area. Give credit for each point whenever the answer shows the idea, in any wording. Accept another real organisation if it fits and the reason is sound. Model answer, for the feedback, not a grading checklist: "(A) needs only models, so a government institute such as the UK AI Security Institute or a nonprofit such as Redwood Research can build it. (B) needs the developer's own agents, logs and staff every day, so mainly the AI developer itself can do it, for example OpenAI. (C) needs the developer's real setup and monitors, so the developer's own red team, for example at Anthropic, is placed to do it. Because the developer would be grading itself, an outside reviewer or an outside red team given access, such as METR, makes the result more credible."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. At full marks, just confirm. If the learner put (B) at an outside organisation without saying how it gets access, ask what access the work needs. If they put (C) at an outside organisation without saying how it gets access to the real setup, ask what the work needs to touch. If they put (C) at the developer without any point about independence, ask who checks a safety result the developer reaches about its own model. If it helps, mention that OpenAI says it monitors almost all of its internal coding traffic and sends higher-severity cases to human review, as an example of (B) done in-house. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Areas of control work]]
notes:: Greenblatt's eight areas of control work, excerpted.
## Lens:
source:: [[../Lenses/AICF - Control inside AI companies]]
notes:: Google DeepMind's AI Control Roadmap summary on how its defences grow with model capability, and the UK AI Security Institute's Control Red Team post on testing company monitors from outside.
## Lens:
source:: [[../Lenses/AICF - Who works on AI control]]
notes:: Lens page on organisations, people and size, October 2026, every line sourced.
## Lens:
source:: [[../Lenses/AICF - Research areas from the UK AI Security Institute]]
notes:: A second, funder-facing map of control research areas.
