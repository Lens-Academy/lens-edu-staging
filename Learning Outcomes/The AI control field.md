---
id: 'c05ed183-2911-4707-88f1-6ba5f9d53e1d'
learning-outcome: "Place a piece of AI control work within the field: name the main research area it belongs to (such as building settings and running control evaluations, studying control-relevant model capabilities, developing countermeasures such as monitoring, running control inside AI companies through infrastructure and human processes, or conceptual work), say which kind of organisation is placed to do it and why (nonprofit research groups such as Redwood Research, government institutes such as the UK AI Security Institute, AI companies, or third-party evaluators such as METR), and say roughly how large the control field is compared with technical AI safety as a whole and why such counts are uncertain."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - James agent ready-34
---
%% Written for AI Control Fundamentals Unit 2. The facts about organisations and size come from the Lens page "AICF - Who works on AI control" (October 2026), which links every source. Update the rubric when that page is updated. %%
## Test:
id:: a3d7a99a-4ddc-4c08-99e5-ba9c1d2d7344

#### Question: Open
id:: 0d2fa93d-b838-47ab-afc2-586341beeb07
content::
Two pieces of AI control work:

(A) A team builds a test environment that imitates an AI company's internal computer cluster. It has realistic tasks for an AI agent, plus hidden harmful side tasks that a red team can instruct the agent to attempt, so that different monitoring set-ups can be compared on how often they catch the attempts.
(B) A team sets up a process in which actions that a monitor flags on the AI agents used inside an AI company are sent to trained human reviewers within half an hour, with a clear route for escalating a serious finding.

a. For each, name the research area of AI control it belongs to, and say which kind of organisation is placed to do it, with one real example of an organisation that does this kind of work. Say why that kind of organisation fits.
b. Roughly how big is the AI control field compared with technical AI safety as a whole? Why are such estimates uncertain?
placeholder:: Take A, then B, then the size question
assessment-instructions:: Score out of 100. 60: the two pieces of work, 30 each. For (A), 15: the area is building control settings and running control evaluations (accept equivalent names such as settings or benchmarks for control, testing control protocols, or red-team versus blue-team evaluations). 15: a fitting kind of organisation with one real example and a reason, for example a government institute such as the UK AI Security Institute (it built ControlArena, a library for control experiments), a nonprofit research group such as Redwood Research, or an AI company such as Anthropic (it built SHADE-Arena with Scale AI and Redwood). The reason can be that this work does not need access to a company's real systems, or that the organisation builds shared tools, or another sound reason. For (B), 15: the area is running control in practice inside AI companies, through human processes for review and escalation (accept equivalent names such as prototyping human processes, control in deployment, or monitoring of internal agents). 15: the kind of organisation is an AI company, with one real example such as OpenAI, Google DeepMind or Anthropic, and a reason, such as that the work needs access to the company's own agents, data and staff. 40: size. 25: control is small compared with technical AI safety, roughly tens of dedicated researchers against several hundred to about a thousand people in technical AI safety, a few percent. Accept any estimate in that order of magnitude, such as "about 5 to 50 against about 600", "a few percent" or "a very small slice". 15: why it is uncertain, any one sound reason, such as that counts file each organisation under one main area so control teams inside AI companies or government institutes are counted elsewhere, that there is no clear line between control and nearby work such as monitoring or evaluations, or that the field is growing fast. Give credit for each point whenever the answer shows the idea, in any wording. Accept another real organisation if it fits and the reason is sound. Cap at 60 if the answer says control is a large share of technical AI safety, such as a third or more. Model answer, for the feedback, not a grading checklist: "(A) is building a control setting for control evaluations. The UK AI Security Institute does this kind of work (it built ControlArena), as does Redwood Research. It fits them because it does not need access to a company's real systems and the result is a shared tool others can use. (B) is running control in practice through human processes inside an AI company. Only the AI company itself can do it, because it needs the company's own agents, logs and staff. OpenAI, for example, says it monitors almost all internal coding-agent traffic and sends serious cases to human review within 30 minutes. Size: control is small, perhaps tens of dedicated researchers out of roughly 600 people doing technical AI safety, so a few percent. The estimates are uncertain because counts file whole organisations under one area, so control work inside AI companies and government institutes is counted elsewhere, and the line between control and nearby monitoring work is blurry."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner put (B) at an outside organisation, ask what access the work needs. If their size estimate is far off, ask them to compare tens with hundreds. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences. No generic praise.

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
