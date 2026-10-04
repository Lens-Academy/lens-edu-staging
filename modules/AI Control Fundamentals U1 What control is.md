---
id: 'f8de126d-9f11-4658-a5b4-8894c84698bc'
slug: ai-control-fundamentals-u1
title: "Unit 1: What control is"
tags:
  - work-in-progress
---
%% Unit 1 of AI Control Fundamentals. Lenses: welcome (inline), Robert Miles video in six parts with exercises (AICF), two AICF adaptations of Greenblatt and Shlegeris's case for control (core exercises only, the rest optional), Kulveit as a first criticism (inline). Time: welcome 5+3, video 27+24, what control is 16+24, how control is tested 11+16, Kulveit 4+8, so 178 lens minutes, plus about 24 for the two learning-outcome tests (12 each). About 202 minutes. %%

# Learning Outcome:
source:: [[../Learning Outcomes/Alignment claims versus control claims]]

# Learning Outcome:
source:: [[../Learning Outcomes/Deciding which models to trust]]

# Lens: Welcome to Unit 1
id:: cd096d83-1e62-4695-8643-70fea5465bfd
reading_minutes:: 5
tutor_minutes:: 3
tldr:: Banks do not assume no trader will ever go rogue. They build systems that hold when one does. AI control asks whether we can do the same with an AI model that might be working against us.
summary_for_tutor:: Opening lens of Unit 1 of AI Control Fundamentals, written by Lens. It introduces control with the insider-threat analogy (organisations build systems that hold even if an employee goes rogue), contrasts it with alignment, lists what the unit covers, and asks the learner to write down a gut view on whether control is worth working on, which they revisit in Unit 5. Do not grade the gut view or argue with it. Acknowledge it briefly and send the learner to the first lesson.
#### Text
content::
Organisations do not assume that none of their employees will ever go rogue. Banks limit what a single trader can do, and they log and audit trades. The bank stays safe even if one person is not trustworthy.

Much of AI safety work tries to make AI models want what we want. That is alignment. AI control asks a different question: if we cannot be sure a model is not secretly working against us, can we still use it, get useful work out of it, and make sure it cannot cause a catastrophe? This unit covers what that means and how anyone could test whether it works.

\## In this unit you will

- Watch Robert Miles explain the idea and the experiment that started the field.
- Read Ryan Greenblatt and Buck Shlegeris's case for control: how it differs from alignment, which models count as trusted and which as untrusted, and how a red team tests whether safety measures hold.
- Read a first criticism of control, by Jan Kulveit.

#### Question: Open
id:: f3905d61-5ae7-4179-a7b6-7d9e5263ca99
content::
Before you start, write down your gut view. You will come back to it in Unit 5, so also copy it somewhere you will find it again.

- Does "use a powerful AI model that might be working against you, and make sure it still cannot cause a catastrophe" sound doable to you, or hopeless?
- Do you think work on this is likely to help, or could it make things worse? Why?

A few sentences are enough. There are no wrong answers here.
force-feedback:: first
feedback-instructions:: This is an ungraded gut-view note the learner will revisit in Unit 5. Acknowledge it in two or three sentences and reflect back the specific view they expressed, without endorsing or correcting it. Do not preview the course's arguments. Do not ask a follow-up question. Close by sending them to the next lesson. No generic praise.

# Lens:
source:: [[../Lenses/AICF - Using dangerous AI, but safely]]

# Lens:
source:: [[../Lenses/AICF - The case for control - what control is]]

# Lens:
source:: [[../Lenses/AICF - The case for control - how control is tested]]

# Lens: A first criticism
id:: c6c69db7-5ff6-4259-b924-fe1b2cd6d838
reading_minutes:: 4
tutor_minutes:: 8
tldr:: Jan Kulveit argues that a moderate AI disaster might be what finally gets the world to act, and that control makes such warning shots rarer, leaving near-misses the lab describes only vaguely, or a catastrophe too big to learn from.
summary_for_tutor:: Last lens of Unit 1 of AI Control Fundamentals. The learner reads Jan Kulveit's short post "AI Control May Increase Existential Risk" (Alignment Forum, March 2025) in full. Kulveit's argument: in worlds where alignment goes well, control matters little. In worlds where alignment fails, control mostly turns moderate, visible warning shots, which would push the world to act, into quiet internal catches that labs describe vaguely, or into a later catastrophe. He also expects labs to downplay incidents that control stopped. This is a first look at criticisms of control. Unit 4 covers criticisms in depth and Unit 5 the debates around this argument, including replies from people who work on control. The lens intro points out that Kulveit disputes a step the learner met in the case for control: that catching an AI counts as a win because it makes a pause or slowdown more likely. The question asks for one premise from each side and which is less plausible. Treat any reasoned answer as fine. Do not tell the learner whether Kulveit is right.
#### Text
content::
Most of what you read in this unit comes from people who work on control. Control also has critics. Here is one short criticism, so you can keep it in mind for the rest of the course. Unit 4 goes through the criticisms in depth.

In the case for control you read that catching an AI counts as a win, because after a catch, shutting down until there are solutions becomes far more likely. Kulveit disputes that step.

#### Article
source:: [[../articles/kulveit--ai-control-may-increase-existential-risk]]

#### Question: Open
id:: 9b1325c0-05ed-4175-a437-e7a9551c70e5
content::
Both Kulveit's argument and Greenblatt and Shlegeris's case for control depend on some things being true about the world. Name one premise each of them depends on. Which of the two do you find less plausible, and why?
feedback-instructions:: The learner just read Kulveit's "AI Control May Increase Existential Risk" after Greenblatt and Shlegeris's case for control. Premises Kulveit's argument depends on include: (1) without control, a misaligned AI's attempt would often be stopped by other means (security, society, governments) and become a moderate, visible incident rather than a catastrophe, (2) such visible incidents would push labs and governments to act, (3) incidents stopped by control would be kept quiet or described vaguely by the lab, and (4) cases where control is the only thing that stops an AI are rare compared with cases something else would have stopped. Premises the case for control depends on include: (a) a red team can find attacks at least as good as the ones a scheming model would find, and the model's abilities can be measured even if it tries to sabotage the measurement, (b) catching an AI leads to a shutdown, pause or slowdown, or at least to much more support for one, (c) the first very useful AIs are not yet too capable to control. Acknowledge each premise the learner names and whether the argument actually needs it. If they name one the argument does not need, say so in one sentence and point to one it does need. Comment on how well they reasoned about which is less plausible, without saying which side is right. At most five sentences. No generic praise. Tell them the course comes back to this argument in Units 4 and 5.
