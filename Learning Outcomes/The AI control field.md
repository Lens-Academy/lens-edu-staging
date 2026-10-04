---
id: 'c05ed183-2911-4707-88f1-6ba5f9d53e1d'
learning-outcome: "Place a piece of AI control work within the field: identify what kind of control work it is (its research area), use that to say what access to AI developers' systems and what independence from developers it needs, and from that say which kind of organisation is placed to do it, naming a real organisation of that kind."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - James agent ready-34
---
%% Written for AI Control Fundamentals Unit 2. The size of the field is practised and scored in the lens "AICF - Who works on AI control", not in a test (the separate outcome "Size of the AI control field" is no longer used). The facts about organisations come from the Lens page "AICF - Who works on AI control" (October 2026), which links every source. Update the rubric when that page is updated. %%
## Test:
id:: a3d7a99a-4ddc-4c08-99e5-ba9c1d2d7344

#### Question: Open
id:: 0d2fa93d-b838-47ab-afc2-586341beeb07
content::
Three pieces of AI control work:

(A) A team releases an open-source software library for running control experiments: ready-made tasks for AI agents, ways for a red team to attack, and monitors to test. Researchers at several AI companies and research groups then use it.
(B) A team decides who reviews the actions that a monitor flags on the coding agents writing most of the code for a frontier model, how quickly each flag must be reviewed, and how a serious finding is escalated, and then runs this routine.
(C) A team runs a control evaluation against the monitors one AI developer actually uses on its internal agents: human red-teamers try to get attacks past those monitors, and the team publishes how often they succeeded.

For A, B and C: what kind of control work is it (which research area)? What access to developers' systems, and what independence from developers, does it need? So which kind of organisation is placed to do it? Name one real example of such an organisation.

(D) Roughly how many people work full-time on AI control, and roughly how many on technical AI safety as a whole? Give one reason why careful counts of the people working on control can differ a lot.
placeholder:: Take A, B, C, then D
assessment-instructions:: Score out of 100. 25 each for (A), (B), (C) and (D). For each of (A), (B) and (C): 8 for a fitting kind of work or research area, 9 for what access or independence the work needs, 4 for a fitting kind of organisation that follows from it, and 4 for one real example of that kind of organisation. (A): the area is building settings and tools for control evaluations (accept equivalent names such as control evaluation infrastructure, research tooling for control experiments, or settings for control research). Access: it needs only models, not a developer's real systems, because the library runs experiments on models anyone can use. Fitting organisations: a government institute such as the UK AI Security Institute, a research nonprofit such as Redwood Research, an academic group, or an AI company's research team. Any of these with the access reason gets full marks. (B): the area is running control in practice through human processes for review and escalation (accept equivalent names such as prototyping human processes, control in deployment, or internal monitoring and auditing). Access: it needs the developer's own agents, logs and staff, every day. Fitting organisation: mainly the AI developer itself, for example OpenAI, Google DeepMind or Anthropic. Also accept an outside auditor or government body if the answer says how it would get that daily access. (C): the area is control evaluations applied to a real deployment, or control experiments on actual AI usage (accept equivalent names such as red-teaming deployed monitors, third-party evaluation, or external red-teaming). Access and independence: 5 for saying it needs the developer's cooperation to reach the monitors and agents it really uses, and 4 for saying the published result is only trusted if the team is independent of the developer. Fitting organisation: a third-party evaluator such as METR, or a government institute such as the UK AI Security Institute. The developer's own team earns the 4 organisation points only if the answer says why its published result could still be trusted (for example outside review of its method). In all three parts, the access and independence points are judged on the reasoning itself, whichever organisation is named. (D): 15 for the two numbers. Full 15 for control from about 5 to about 100 full-time people and technical AI safety from a few hundred to a few thousand (about 300 to 5,000), or for a larger control number if the answer says what it counts (for example monitoring teams inside AI companies and government) and its numbers are consistent with that. 7 if only one number is in range, or only a direction such as "small" is given. 10 for one specific reason careful counts differ, for example that a count filing each whole organisation under one area puts control teams at AI companies or government institutes under other areas, or that people draw the line between control and nearby work such as monitoring research differently. 5 if the answer only says the boundary is unclear. Give credit for each point whenever the answer shows the idea, in any wording. Accept another real organisation or another reasoned area, including areas from the UK AI Security Institute's list, if it fits and the reason is sound. Model answer, for the feedback, not a grading checklist: "(A) is building tools for control evaluations. It needs only models, so a government institute such as the UK AI Security Institute or a nonprofit such as Redwood Research can do it. (B) is running control in practice through a human review and escalation process. Mainly the AI developer itself can do it, for example OpenAI, because it needs the developer's own agents, logs and staff every day. (C) is a control evaluation of a real deployment. It needs the developer to give access to its real monitors, and the result is only believed if the evaluator is independent, so a third-party evaluator such as METR fits. (D) Tens of people work full-time on control, against several hundred in technical AI safety. Counts differ because one count filed each whole organisation under a single area, so control teams inside AI companies and government were counted elsewhere."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. At full marks, just confirm. If the learner put (B) at an outside organisation without saying how it gets access, ask what access the work needs. If they put (C) at the developer itself, ask who would trust an evaluation the developer ran on its own monitors. If they gave no counting reason in (D), ask why one 2025 count found only about 11 people. If it helps, mention that OpenAI says it monitors almost all of its internal coding traffic and sends higher-severity cases to human review, as an example of (B) done in-house. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

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
