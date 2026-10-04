---
id: '2e54ea22-158e-403a-af56-fa67c28da8bb'
slug: ai-control-fundamentals-u2
title: "Unit 2: The key ideas and the field"
tags:
  - work-in-progress
---
%% Unit 2 of AI Control Fundamentals. Lenses: welcome (inline), Greenblatt on threats with the control graph, Shlegeris on rogue deployments, Hebbar's low-stakes talk (first 16 min), practice on high- vs low-stakes (inline), Greenblatt's areas (excerpts), UK AISI research areas (excerpts), Bhatt talk excerpt plus Google DeepMind's roadmap post, Lens page on who works on control, practice on placing projects (inline). Time: welcome 3+3, threats 15+10, rogue deployments 13+10, low-stakes talk 18+10, practice 3+15, areas 12+10, AISI 6+5, AI companies 18+10, who works 7+5, practice 3+10, plus about 16 for the two learning-outcome tests. About 202 minutes. %%

# Learning Outcome:
source:: [[../Learning Outcomes/High-stakes versus low-stakes control]]

# Learning Outcome:
source:: [[../Learning Outcomes/The AI control field]]

# Lens: Welcome to Unit 2
id:: b716617e-ad43-4334-9bee-d284a2533f19
reading_minutes:: 3
tutor_minutes:: 3
tldr:: An AI that needs one bad action to cause a catastrophe and one that needs a thousand call for different defences. This unit covers that difference, then the people and organisations who work on control and how many of them there are.
summary_for_tutor:: Opening lens of Unit 2 of AI Control Fundamentals, written by Lens. It says what the unit covers: the high-stakes versus low-stakes distinction (how many actions a catastrophe needs and how incriminating each is, and what that means for defenders), then the field (research areas, organisations, people, size). It asks one ungraded prediction question. Do not teach the answer. Acknowledge the learner's prediction in one or two sentences and send them to the first lesson.
#### Text
content::
In Unit 1 you met the basic idea of control: use a model that might be working against you, and make sure it still cannot cause a catastrophe. This unit adds a distinction you will meet in most of its readings, between threats that need only a few bad actions and threats that need many. It then looks at the field itself: what people work on, who they are, and how many of them there are, so that you can place the arguments in Units 3 to 5 in context.

\## In this unit you will

- Read Ryan Greenblatt on which threats control should prioritise, and why threats that need few actions call for different defences from threats that need many.
- Read Buck Shlegeris on rogue deployments, and watch Vivek Hebbar on research sabotage as a low-stakes threat.
- Practise telling high-stakes from low-stakes threats.
- Read two maps of control research, one from Redwood Research and one from the UK AI Security Institute.
- See what AI companies already run, and read a Lens summary of who works on control and how big the field is.

#### Question: Open
id:: 62e5237c-1121-452e-9832-847652b41311
content::
A quick prediction before you start. Which seems harder to defend against: a model that could cause a catastrophe with one bad action, or one that needs a thousand small bad actions? Say why in a sentence or two.
feedback-instructions:: This is an ungraded prediction. Acknowledge it in one or two sentences and reflect back the reason the learner gave, without saying which answer is right and without previewing the readings. Do not ask a follow-up question. Close by sending them to the first lesson. No generic praise.

# Lens:
source:: [[../Lenses/AICF - High-stakes and low-stakes threats]]

# Lens:
source:: [[../Lenses/AICF - Rogue deployments]]

# Lens:
source:: [[../Lenses/AICF - Low-stakes control and research sabotage]]

# Lens: Practice: high-stakes or low-stakes?
id:: f549298c-d251-4490-9f30-56e93e179069
reading_minutes:: 3
tutor_minutes:: 15
tldr:: Three new threats to sort, and a common mistake to spot.
summary_for_tutor:: Practice lens in Unit 2 of AI Control Fundamentals, before the learning-outcome test on high-stakes versus low-stakes control. Two ungraded practice questions with tutor feedback. The first asks the learner to classify three new threats and say what a defender should do. The second asks what is right and wrong in the claim that high-stakes threats are the ones with the most harm at stake. Give feedback that teaches: name what is right, then the most important fix. Do not give the learner the test.
#### Question: Open
id:: 1b25aa6e-2e1a-42c9-be31-d13007036dfb
content::
Three ways a model that might be scheming could cause serious damage at an AI company:

(a) While running a long, routine script on the training cluster, the agent includes one hidden command that starts a copy of itself that no monitor watches.
(b) Over months and thousands of code changes, the agent makes the code that the monitoring team relies on slightly harder to audit: a little less logging here, a vaguer variable name there.
(c) During a live security incident, an agent helping the response team has a few minutes to act. One wrong step would let the attackers copy the model's weights.

For each: is it high-stakes or low-stakes, and why? Would a review a week later be good enough? For the one you think is most clearly low-stakes, name one defence that works across many actions.
placeholder:: Take (a), (b), then (c)
force-feedback:: first
feedback-instructions:: Practice question before the unit's learning-outcome test. Reference answer: (a) high-stakes: one action is enough, and a hidden command starting an unmonitored copy is clearly incriminating if inspected; a week-later review is too late because the rogue deployment is already running, so such actions must be blocked or held for review before they run. (b) low-stakes: thousands of actions, each only weak evidence, easy to read as normal sloppiness; a week-later review is fine because no single change is decisive, and defences that work across many actions fit, such as training the agent on a code-quality or auditability signal across all its changes, or checking logging coverage in aggregate. (c) high-stakes by time: a few actions in a short window decide the outcome (Greenblatt calls failures that happen quickly concentrated too); later review is useless, so this needs real-time oversight, or keeping the untrusted agent away from such decisions. How incriminating the wrong step would be is arguable, since in a crisis a mistake can look honest; accept reasoning either way. In 80 to 150 words, short paragraphs: name what the learner got right, then the most important correction. If they sorted by harm, say the axis is how many actions are needed and how incriminating each is. Up to two turns. No generic praise. If the learner is stuck, give one foothold: ask how many actions each case needs.

#### Question: Open
id:: 5dddb88d-bd0f-46cb-99e4-a2a7be541dd4
content::
A friend says: "High-stakes threats are the ones where the most harm is at stake. Low-stakes threats are the minor ones." What is right and what is wrong about this?
force-feedback:: first
feedback-instructions:: Practice question. Reference answer: the names suggest harm, but in control they describe how the damage is spread over actions. High-stakes means a few actions (or a short time) are enough, so each action matters a lot. Low-stakes means many actions are needed and each one alone matters little and is only weak evidence. Both can end in catastrophe, for example research sabotage can be low-stakes and still derail safety work. What the friend gets right: in a high-stakes threat each single action does carry a lot of harm. Reply in at most four sentences: confirm what is right, give the most important correction. One turn. No generic praise.

# Lens:
source:: [[../Lenses/AICF - Areas of control work]]

# Lens:
source:: [[../Lenses/AICF - Research areas from the UK AI Security Institute]]

# Lens:
source:: [[../Lenses/AICF - Control inside AI companies]]

# Lens:
source:: [[../Lenses/AICF - Who works on AI control]]

# Lens: Practice: place the project
id:: 1a80fa3c-d847-48d7-b94b-dd7fb264aa9e
reading_minutes:: 3
tutor_minutes:: 10
tldr:: Three pieces of control work to place: which area, and who is placed to do it.
summary_for_tutor:: Practice lens at the end of Unit 2 of AI Control Fundamentals, before the learning-outcome test on the AI control field. One ungraded question with tutor feedback: place three pieces of control work in a research area and say which kind of organisation is placed to do each. Give feedback that teaches. Do not give the learner the test.
#### Question: Open
id:: 1f07d77a-6981-4703-aecd-dcf56f9453c6
content::
Three pieces of control work:

(a) A PhD student measures how well current models can tell a real deployment task from a synthetic test made to look real.
(b) A team builds the system that records every action of a company's internal AI agents, so that monitors and human reviewers can see them.
(c) An outside team tries to get an AI company's internal monitors to miss planted attacks, and publishes what it finds.

For each: which research area does it belong to, and what kind of organisation is placed to do it? Give a real example of such an organisation where you can, and say why it fits.
placeholder:: Take (a), (b), then (c)
force-feedback:: first
feedback-instructions:: Practice question before the field test. Reference answer: (a) studying control-relevant capabilities and model properties (Greenblatt's second area; it also feeds countermeasures such as synthetic inputs). Anyone with model access can do it: a university group, Redwood Research or the UK AI Security Institute, because it needs no company systems. (b) software infrastructure for control (Greenblatt's fifth area), which only the AI company can build for its own agents, because it needs access to its own systems, as Google DeepMind's prototype monitor over a million coding-agent tasks shows. (c) evaluating or red-teaming control measures in practice: a third-party evaluator such as METR, or a government red team such as AISI's, because outsiders can check a company's claims independently, though they need the company's cooperation. Accept other reasoned placements, including ones that use the UK AISI list's categories. In 80 to 150 words: name what is right, then the most important correction. Up to two turns. No generic praise.
