---
id: '2e54ea22-158e-403a-af56-fa67c28da8bb'
slug: ai-control-fundamentals-u2
title: "The key ideas and the field"
---
%% Part 1 of Unit 2 of AI Control Fundamentals; the unit continues in 'The AI control field' (split into modules by topic, Elias 2026-10-08). The note below describes the whole unit as it was before the split. %%

%% Unit 2 of AI Control Fundamentals. Lenses: welcome (inline), Greenblatt on threats with the control graph (ranking optional), Shlegeris on rogue deployments (three excerpts), Hebbar's low-stakes talk (first 16.5 min) plus the intro of Anthropic/EPFL/Redwood "Diffuse AI Control on Fuzzy Tasks", practice on high- vs low-stakes (inline), Greenblatt's areas (excerpts), UK AISI research areas (excerpts), the "Scaling security" section of Google DeepMind's roadmap post (its first half moved to Unit 1, "Control in use today", on 2026-10-05) plus UK AISI Control Red Team post, optional: Ward's overview of company monitoring practices (whole post, added 2026-10-08, 12+5, not counted), Lens page on who works on control, Lens page on how big the field is (split out of it on 2026-10-12), practice on placing projects (inline). Time: welcome 3+3, threats 9+10, rogue deployments 7+8, low-stakes 20+14, practice 3+13, areas 8+8, AISI 6+5, AI companies 5+9, who works 14+31, how big 3+0, practice 3+10 (lenses 192), plus 20 for the two learning-outcome tests (10 each). About 212 minutes. %%
# Submodule: High-stakes and low-stakes threats

# Learning Outcome:
source:: [[../Learning Outcomes/High-stakes versus low-stakes control]]

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

# Lens:
source:: [[../Lenses/AICF - Practice high-stakes or low-stakes]]

# Submodule: The AI control field
slug:: field

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

# Lens:
source:: [[../Lenses/AICF - How big is the AI control field]]

# Lens:
source:: [[../Lenses/AICF - Practice placing the project]]

# Submodule: Unit 2 feedback
slug:: feedback

%% Feedback module after Unit 2 of AI Control Fundamentals, same pattern as the Advanced AI Control feedback modules. %%

# Lens: Your feedback on Unit 2
id:: 1ff4cb81-d95f-420a-9518-37afb066762b
tldr:: Tell us how Unit 2 went, so we can improve it.
summary_for_tutor:: Feedback page after Unit 2 (The key ideas and the field) of AI Control Fundamentals. The learner rates the unit and says what one thing they would change about the unit. The answers are for the course team. Do not grade them or argue with them. If the learner asks for help, help them put their own view into words.
reading_minutes:: 2
tutor_minutes:: 0
#### Text
content:: Tell us how this unit went. We read your answers and use them to improve the course.

#### Question: Rating
id:: 49aab4cb-e95d-4d80-9cfa-be1086446c8a
content:: How would you rate this unit's content?
scale:: 10
labels::
- Extremely poor
- Very poor
- Poor
- Below average
- Neutral
- Above average
- Good
- Very good
- Excellent
- Outstanding

#### Question: Rating
id:: 4bd732fe-95fe-47ef-9fd4-c3d015c98915
content:: How useful was the AI Tutor for this unit?
scale:: 10
labels::
- Not useful at all
- Very unhelpful
- Unhelpful
- Slightly unhelpful
- Neutral
- Slightly useful
- Useful
- Very useful
- Extremely useful
- Essential

#### Question: Open
id:: e8933c11-c98e-46b8-96e5-f18a29bf2dc8
content:: If you could change one thing about this unit, what would it be?
optional:: true

#### Question: Open
id:: 0f83d830-8e7c-41ad-946d-4e779c1e4aef
content:: Anything else you want to share?
placeholder:: For example: what was most useful, or what was confusing, too long, or not worth your time.
optional:: true
