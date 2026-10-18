---
id: 'f8de126d-9f11-4658-a5b4-8894c84698bc'
slug: ai-control-fundamentals-u1
title: "What control is"
---
%% Part 1 of Unit 1 of AI Control Fundamentals; the unit continues in 'Control claims, and how they are tested', 'Control today, and first criticisms' (split into modules by topic, Elias 2026-10-08). The note below describes the whole unit as it was before the split. %%

%% Unit 1 of AI Control Fundamentals. Lenses: welcome (inline), control in plain words (full CSET explainer in parts with questions and the choice set), what control is meant to stop (80,000 Hours "What's AI control?" video clip), Robert Miles video in six parts with exercises (AICF), two AICF adaptations of Greenblatt and Shlegeris's case for control, spies, insiders and auditing (80,000 Hours plus ControlArena), worst case but not all-powerful (Shlegeris), control in use today (Google DeepMind first half), OpenAI's monitor (optional, whole post, own lens since 2026-10-08), first criticisms (Phuong clip plus Kulveit, inline), roleplay practice. Time (core only): about 214 lens minutes plus 30 for the three tests (12, 10, 8), about 244 minutes. Optional: the Buck clip lens, the roleplay, CSET parts 5 to 8, the opening of 'What control is', ControlArena in Spies, part 2 of 'Worst case', the OpenAI lens, the black-box section of 'How control is tested', and the Phuong clip. %%

# Submodule: What control is
slug:: welcome-to-unit-1

# Lens: Welcome to Unit 1
id:: cd096d83-1e62-4695-8643-70fea5465bfd
reading_minutes:: 5
tutor_minutes:: 3
tldr:: Banks do not assume no trader will ever go rogue. They build systems that hold when one does. AI control asks whether we can do the same with an AI model that might be working against us.
summary_for_tutor:: Opening lens of Unit 1 of AI Control Fundamentals, written by Lens. It introduces control with the insider-threat analogy (organisations build systems that hold even if an employee goes rogue), contrasts it with alignment, lists what the unit covers, and asks the learner to write down a gut view on whether control is worth working on, ending with a verdict (net positive, net negative or too close to call) and how sure they are, which they revisit in Unit 5. Do not grade the gut view or argue with it. Acknowledge it briefly and send the learner to the first lesson.
#### Text
content::
Organisations do not assume that none of their employees will ever go rogue. Banks limit what a single trader can do, and they log and audit trades. The bank stays safe even if one person is not trustworthy.

Much of AI safety work tries to make AI models want what we want. That is alignment. AI control asks a different question: if we cannot be sure a model is not secretly working against us, can we still use it, get useful work out of it, and make sure it cannot cause a catastrophe? This unit covers what that means and how anyone could test whether it works.

\## In this unit you will

- Read a policy explainer from Georgetown on what control is, and sort claims into control claims and alignment claims.
- Watch Robert Miles explain the idea and the experiment that started the field.
- Read Ryan Greenblatt and Buck Shlegeris's case for control: how it differs from alignment, which models count as trusted and which as untrusted, and how a red team tests whether safety measures hold.
- Learn the words for the parts of a control set-up, from monitors and auditing to honeypots, and the worst-case assumptions a control evaluation makes about the AI.
- See how Google DeepMind monitors its own AI agents in 2026.
- Read a first criticism of control, by Jan Kulveit.

Optional extras along the way: a clip of Buck Shlegeris on what control is meant to stop, OpenAI's monitoring set-up, Mary Phuong of Google DeepMind on the weaknesses of control, and a roleplay where you take apart a lab's deployment plan.

#### Question: Open
id:: f3905d61-5ae7-4179-a7b6-7d9e5263ca99
content::
Before you start, write down your gut view. You will come back to it in Unit 5, so also copy it somewhere you will find it again.

- Does "use a powerful AI model that might be working against you, and make sure it still cannot cause a catastrophe" sound doable to you, or hopeless?
- Do you think work on this is likely to help, or could it make things worse? Why?
- Overall, is work on AI control net positive, net negative, or too close to call? How sure are you: low, medium or high?

A few sentences are enough. There are no wrong answers here.
force-feedback:: first
feedback-instructions:: This is an ungraded gut-view note the learner will revisit in Unit 5. Acknowledge it in two or three sentences and reflect back the specific view they expressed, without endorsing or correcting it. Do not preview the course's arguments. Do not ask a follow-up question. Close by sending them to the next lesson. No generic praise.

# Lens:
source:: [[../Lenses/AICF - Control in plain words]]

# Lens:
optional:: true
source:: [[../Lenses/AICF - What control is meant to stop]]

# Lens:
source:: [[../Lenses/AICF - Using dangerous AI, but safely]]

# Submodule: Control claims, and how they are tested
slug:: case

%% Part 2 of Unit 1 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/Alignment claims versus control claims]]

# Learning Outcome:
source:: [[../Learning Outcomes/Deciding which models to trust]]

# Lens:
source:: [[../Lenses/AICF - The case for control - what control is]]

# Lens:
source:: [[../Lenses/AICF - Spies, insiders and auditing]]

# Lens:
source:: [[../Lenses/AICF - The case for control - how control is tested]]

# Lens:
source:: [[../Lenses/AICF - Worst case, but not all-powerful]]

# Submodule: Control today, and first criticisms
slug:: today

%% Part 3 of Unit 1 of AI Control Fundamentals (split into modules by topic, Elias 2026-10-08). %%

# Learning Outcome:
source:: [[../Learning Outcomes/Reading a control setup]]

# Lens:
source:: [[../Lenses/AICF - Control in use today]]

# Lens:
optional:: true
source:: [[../Lenses/AICF - OpenAI's monitor for its internal coding agents]]

# Lens:
source:: [[../Lenses/AICF - First criticisms]]

# Lens:
optional:: true
source:: [[../Lenses/AICF - Take apart a deployment pitch]]

# Submodule: Unit 1 feedback
slug:: feedback

%% Feedback module after Unit 1 of AI Control Fundamentals, same pattern as the Advanced AI Control feedback modules. %%

# Lens: Your feedback on Unit 1
id:: 27789d25-4173-42a4-9e23-5c025969a235
tldr:: Tell us how Unit 1 went, so we can improve it.
summary_for_tutor:: Feedback page after Unit 1 (What control is) of AI Control Fundamentals. The learner rates the unit and says what one thing they would change about the unit. The answers are for the course team. Do not grade them or argue with them. If the learner asks for help, help them put their own view into words.
reading_minutes:: 2
tutor_minutes:: 0
#### Text
content:: Tell us how this unit went. We read your answers and use them to improve the course.

#### Question: Rating
id:: 9640850e-7a16-4540-994f-3ba37510bf15
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
id:: f8785ad0-7951-4a0b-b747-69d9383aa6f7
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
id:: 44b82545-0ba2-4ef3-a277-618aeecee69c
content:: If you could change one thing about this unit, what would it be?
optional:: true

#### Question: Open
id:: 3eda318a-d8b3-4f9e-a997-d281cf0dba8f
content:: Anything else you want to share?
placeholder:: For example: what was most useful, or what was confusing, too long, or not worth your time.
optional:: true
