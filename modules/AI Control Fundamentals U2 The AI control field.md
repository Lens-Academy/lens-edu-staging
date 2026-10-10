---
id: '0f1588df-f8f7-47eb-ac54-6f8bc761702c'
slug: ai-control-fundamentals-u2-field
title: "The AI control field"
---
%% Part 2 of Unit 2 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/The AI control field]]

# Lens:
source:: [[../Lenses/AICF - Areas of control work]]

# Lens:
source:: [[../Lenses/AICF - Research areas from the UK AI Security Institute]]

# Lens:
source:: [[../Lenses/AICF - Control inside AI companies]]

# Lens:
optional:: true
source:: [[../Lenses/AICF - How three AI companies monitor their agents]]

# Lens:
source:: [[../Lenses/AICF - Who works on AI control]]

# Lens: Practice: place the project
id:: 1a80fa3c-d847-48d7-b94b-dd7fb264aa9e
reading_minutes:: 3
tutor_minutes:: 10
tldr:: Three pieces of control work: what access each needs, and who is placed to do it.
summary_for_tutor:: Practice lens at the end of Unit 2 of AI Control Fundamentals, before the learning-outcome test on the AI control field. One scored question with tutor feedback: for three pieces of control work, say what access to AI developers' systems or independence from them each needs, and which kind of organisation is placed to do it. Give feedback that teaches. Do not give the learner the test.
#### Question: Open
id:: 1f07d77a-6981-4703-aecd-dcf56f9453c6
content::
Three pieces of control work:

(a) A PhD student measures how well current models can tell a real deployment task from a synthetic test made to look real.

(b) A team builds the system that records every action of a company's internal AI agents, so that monitors and human reviewers can see them.

(c) An AI company publishes a report on the risks from its own internal agents. A team reads it, checks its claims against information the company shares privately, and publishes its own verdict on the report.

For each: which research area does it belong to? What access to AI developers' systems, or independence from them, does it need? So which kind of organisation is placed to do it? Give a real example of such an organisation where you can.
placeholder:: Take (a), (b), then (c)
force-feedback:: first
assessment-instructions:: Score out of 100. Three pieces of work: 33 for (a), 33 for (b), 34 for (c). For each: 12 for a fitting research area, 12 for what access to developers' systems or independence from developers it needs, and 9 (10 for c) for a kind of organisation that follows from that, with a real example where possible (a fitting kind without an example earns 6). (a) A PhD student measures how well models can tell a real deployment task from a synthetic test: studying control-relevant capabilities or model properties (also accept countermeasure research, since it feeds synthetic inputs, or evaluation work). It needs only access to models, not a company's systems, so a university group, a nonprofit such as Redwood Research or a government institute such as the UK AI Security Institute can do it. (b) A team builds the system that records every action of a company's internal agents for monitors and reviewers: software infrastructure for control (also accept monitoring or security work inside a company). It needs the company's own systems and agents, so mainly the AI company itself, such as Google DeepMind, OpenAI or Anthropic. (c) A team checks a company's report on its own agents against private information and publishes a verdict: independent review or evaluation of a company's control claims (accept third-party evaluation or auditing). It is only worth something if the team is independent of the company, and it needs the company's cooperation to see private information, so an outside evaluator such as METR or a government institute. Either the independence or the access reason earns the full 12 for (c). Accept other reasoned placements, including the UK AI Security Institute's categories. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) Studying a control-relevant capability. It needs only models, so a university group or Redwood Research can do it. (b) Software infrastructure for control. It needs the company's own systems, so the AI company itself, for example Google DeepMind. (c) Independent review of a company's claims. It is only credible from someone independent who still gets the company's private information, so an outside evaluator such as METR."
feedback-instructions:: Practice question before the field test. Reference answer: (a) studying control-relevant capabilities and model properties (Greenblatt's second area, which also feeds countermeasures such as synthetic inputs). Anyone with model access can do it: a university group, Redwood Research or the UK AI Security Institute, because it needs no company systems. (b) software infrastructure for control (Greenblatt's fifth area), which only the AI company can build for its own agents, because it needs access to its own systems, as Google DeepMind's prototype monitor over a million coding-agent tasks shows. (c) independent review of a company's control claims: a third-party evaluator such as METR, or a government team such as the UK AI Security Institute's Control Red Team, because the review is only worth something if it is independent of the company, though it needs the company's cooperation to see private information. Accept other reasoned placements, including ones that use the UK AISI list's categories. In 80 to 150 words: name what is right, then the most important correction. Up to two turns. No generic praise.
