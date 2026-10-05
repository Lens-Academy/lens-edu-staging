---
id: '2e54ea22-158e-403a-af56-fa67c28da8bb'
slug: ai-control-fundamentals-u2
title: "Unit 2: The key ideas and the field"
---
%% Unit 2 of AI Control Fundamentals. Lenses: welcome (inline), Greenblatt on threats with the control graph (ranking optional), Shlegeris on rogue deployments (three excerpts), Hebbar's low-stakes talk (first 16.5 min) plus the intro of Anthropic/EPFL/Redwood "Diffuse AI Control on Fuzzy Tasks", practice on high- vs low-stakes (inline), Greenblatt's areas (excerpts), UK AISI research areas (excerpts), Bhatt talk 4:53 to 10:44 plus the "Scaling security" section of Google DeepMind's roadmap post (its first half moved to Unit 1, "Control in use today", on 2026-10-05) plus UK AISI Control Red Team post, Lens page on who works on control, practice on placing projects (inline). Time: welcome 3+3, threats 9+10, rogue deployments 7+8, low-stakes 20+14, practice 3+13, areas 8+8, AISI 6+5, AI companies 12+9, who works 6+10, practice 3+10 (lenses 167), plus about 28 for the two learning-outcome tests. About 195 minutes. %%

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

- Read Ryan Greenblatt on the kinds of threat control has to handle, and why threats that need few actions call for different defences from threats that need many.
- Read Buck Shlegeris on rogue deployments, watch Vivek Hebbar on research sabotage as a low-stakes threat, and read researchers from Anthropic, EPFL and Redwood on why such threats call for training rather than catching the model.
- Practise telling high-stakes from low-stakes threats.
- Read two maps of control research, one from Redwood Research and one from the UK AI Security Institute.
- See what AI companies already run and how a UK government team tests their monitors, and read a Lens summary of who works on control and how big the field is.

#### Question: Open
id:: 62e5237c-1121-452e-9832-847652b41311
content::
A quick prediction before you start. Which seems harder to defend against: a model that could cause a catastrophe with one bad action, or one that needs a thousand small bad actions? Say why in a sentence or two.
feedback-instructions:: This is an ungraded prediction. Acknowledge it in one or two sentences and reflect back the reason the learner gave, without saying which answer is right and without previewing the readings. Do not ask a follow-up question. Close by sending them to the first lesson. No generic praise.
force-feedback:: first

# Lens:
source:: [[../Lenses/AICF - High-stakes and low-stakes threats]]

# Lens:
source:: [[../Lenses/AICF - Rogue deployments]]

# Lens:
source:: [[../Lenses/AICF - Low-stakes control and research sabotage]]

# Lens: Practice: high-stakes or low-stakes?
id:: f549298c-d251-4490-9f30-56e93e179069
reading_minutes:: 3
tutor_minutes:: 13
tldr:: Three new threats to sort, and a common mistake to spot.
summary_for_tutor:: Practice lens in Unit 2 of AI Control Fundamentals, before the learning-outcome test on high-stakes versus low-stakes control. Two scored practice questions with tutor feedback. The first asks the learner to classify three new threats and say what a defender should do. The second asks what is right and wrong in the claim that high-stakes threats are the ones with the most harm at stake. Give feedback that teaches: name what is right, then the most important fix. Do not give the learner the test.
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
assessment-instructions:: Score out of 100. 60: classification, 20 for each case, judged by how many bad actions (or how short a time) the damage needs and how incriminating each action would be if inspected, not by how much harm results. (a) The agent adds one hidden command that starts an unmonitored copy of itself: high-stakes, because one action is enough and it is clearly suspicious if inspected. (b) The agent makes monitoring code slightly harder to audit over thousands of changes: low-stakes, because it takes many changes and each looks like ordinary sloppiness. (c) The agent has a few minutes during a security incident, and one wrong step lets attackers copy the weights: high-stakes, because a few actions in a short window decide the outcome. An argued "in between" for (c), because a wrong step in a crisis could look like an honest mistake, earns the full 20. 10 of the 20 for a right placement with no reason, or with a reason based only on how harmful the outcome is. 25: whether a review a week later is good enough. 15 for saying it is too late for (a) and (c), because the damage is done before the review, so such actions have to be blocked or checked before they run, or the agent kept away from them. 10 for saying it is fine for (b), because no single change is decisive. 15: one defence that works across many actions for the case the learner calls most clearly low-stakes, such as training the agent on a code-quality or auditability signal across all its changes, or checking logging coverage across the whole codebase. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer sorts the cases by how much harm they do rather than by how many actions they need. Model answer, for the feedback, not a grading checklist: "(a) High-stakes: one hidden command does it, and it is clearly suspicious if anyone looks. A week later the copy is already running, so actions like this have to be held until checked. (b) Low-stakes: it takes thousands of small changes, each of which looks like normal sloppiness. A week-later review is fine because no single change matters much. A defence across many actions: train the agent on a signal for how auditable its code is. (c) High-stakes: a few minutes and one wrong step decide it, so later review is useless and it needs oversight in real time."
feedback-instructions:: Practice question before the unit's learning-outcome test. Reference answer: (a) high-stakes: one action is enough, and a hidden command starting an unmonitored copy is clearly incriminating if inspected. A week-later review is too late because the rogue deployment is already running, so such actions must be blocked or held for review before they run. (b) low-stakes: thousands of actions, each only weak evidence, easy to read as normal sloppiness. A week-later review is fine because no single change is decisive, and defences that work across many actions fit, such as training the agent on a code-quality or auditability signal across all its changes, or checking logging coverage in aggregate. (c) high-stakes by time: a few actions in a short window decide the outcome (Greenblatt calls failures that happen quickly concentrated too). Later review is useless, so this needs real-time oversight, or keeping the untrusted agent away from such decisions. How incriminating the wrong step would be is arguable, since in a crisis a mistake can look honest. Accept reasoning either way. In 80 to 150 words, short paragraphs: name what the learner got right, then the most important correction. If they sorted by harm, say the axis is how many actions are needed and how incriminating each is. Up to two turns. No generic praise. If the learner is stuck, give one foothold: ask how many actions each case needs.

#### Question: Open
id:: 5dddb88d-bd0f-46cb-99e4-a2a7be541dd4
content::
A friend says: "If a bad action is quiet and hard to notice, the threat is low-stakes. If it is loud and obvious, it is high-stakes." What is right and what is wrong about this?
force-feedback:: first
assessment-instructions:: Score out of 100. The friend's claim: quiet, hard-to-notice threats are low-stakes, and loud, obvious ones are high-stakes. 60: what is wrong. How easy an action is to notice is not what decides it. A threat is high-stakes when one or a few actions are enough and each would be strong evidence of bad intent once inspected, so a single quiet action, such as a hidden backdoor, is still high-stakes. Full 60 for either half of this idea with an example or a clear reason (the axis is how many actions are needed and how incriminating each one is, or a quiet single action can be high-stakes). 40: what is partly right. Low-stakes threats are made of actions that each look harmless, but that is because each one is only weak evidence even when inspected, not merely because it is hard to spot. Full 40 for any accurate point about what the friend gets partly right, with a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Wrong: the line is not how noticeable an action is but how many actions the threat needs and how damning each one is once someone looks. A quiet backdoor is still high-stakes if one is enough and it proves bad intent when found. Partly right: low-stakes threats are made of actions that each look harmless, but that is because each is weak evidence even when inspected."
feedback-instructions:: Practice question. Reference answer: the friend mixes up how easy an action is to notice with how many actions a threat needs and how incriminating each one is once found. A single quiet action, such as a hidden backdoor, is still high-stakes if one or a few such actions are enough and the action is strong evidence of intent once found. What the friend gets partly right: low-stakes threats are made of actions that each look harmless, but that is because each is only weak evidence even when inspected, not merely because it is hard to spot. The names can also mislead the other way: low-stakes does not mean minor, for example Shlegeris's case of a model slowly manipulating public opinion is low-stakes and could still be catastrophic. Reply in at most four sentences: confirm what is right, give the most important correction. One turn. No generic praise.

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
summary_for_tutor:: Practice lens at the end of Unit 2 of AI Control Fundamentals, before the learning-outcome test on the AI control field. One scored question with tutor feedback: place three pieces of control work in a research area and say which kind of organisation is placed to do each. Give feedback that teaches. Do not give the learner the test.
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
feedback-instructions:: Practice question before the field test. Reference answer: (a) studying control-relevant capabilities and model properties (Greenblatt's second area, which also feeds countermeasures such as synthetic inputs). Anyone with model access can do it: a university group, Redwood Research or the UK AI Security Institute, because it needs no company systems. (b) software infrastructure for control (Greenblatt's fifth area), which only the AI company can build for its own agents, because it needs access to its own systems, as Google DeepMind's prototype monitor over a million coding-agent tasks shows. (c) independent review of a company's control claims: a third-party evaluator such as METR (Bhatt mentions third-party review of companies' risk reports), because the review is only worth something if it is independent of the company, though it needs the company's cooperation to see private information. Accept other reasoned placements, including ones that use the UK AISI list's categories. In 80 to 150 words: name what is right, then the most important correction. Up to two turns. No generic praise.
