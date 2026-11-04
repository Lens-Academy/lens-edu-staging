---
id: '8791d0ab-cf8c-4c50-ab83-1ccffb1e023d'
title: A few quick questions
---

%% Churned-learner survey (build churn-survey-platform, draft 2026-10-30). Loaded by path `surveys/Churn Survey.md`; edit wording and options here, no code change needed. Never change an id:: once anyone has answered. Each question's "decision" note lives in ops-architecture/build-churn-survey-platform/out/QUESTIONS-DRAFT.md. Option order in Q1 and Q2 maps to the same churn solutions: competing commitments, prep/reading support, scheduling, group/facilitator quality, level-matched grouping, course fit, self-study path. Q1 and Q2 are ranked (ranked:: true, max:: 3). Q1 and Q2 shuffle with the last option pinned (shuffle:: true, pin-last:: 1; needs content_processor 0.92 / PR #1512; do NOT promote to lens-edu-production before the platform release carrying #1471 + #1512). Wording source of truth: Relay Lens/07-Operations/Churn Survey Draft Questions.md. %%

#### Text
content:: Thanks for giving the course a go with us! This takes about two minutes, and what you tell us shapes how we run groups for the next people who join.

#### Question: Choice
id:: c7473d1f-59c6-41f2-9e66-4ef93610ff83
content:: What stopped you coming to your group's sessions?
description:: Tap a choice again to undo it.
options::
- Work, study or another program took up the time
- Something came up (travel, illness, family)
- I'd fallen behind on the reading and didn't want to turn up unprepared
- The session time stopped working for me
- The sessions themselves didn't feel worth the time
- The others in my group were at a different level from me (much more or much less experienced)
- The course wasn't the right fit (too hard, too basic, too dense, or not what I expected)
- I preferred working through the material on my own
- I wasn't sure when or where my sessions were, or how to join
- Something else
ranked:: true
max:: 3
shuffle:: true
pin-last:: 1

#### Question: Choice
id:: 8fa92eba-62cf-4d44-9e69-2d39ae1a9677
content:: Which of these would most likely have kept you coming?
options::
- A short catch-up summary so I could join without doing all the reading
- A different time slot, or an easy way to switch to another group
- A different group or navigator
- A group matched to my level of experience
- An easier or more advanced version of the course
- A self-paced option with an occasional check-in
- A way to catch up on a session I missed (make-up or recording)
- Clearer joining details and reminders
- Nothing really, the timing just wasn't right for me
ranked:: true
max:: 3
shuffle:: true
pin-last:: 1

#### Question: Choice
id:: f8bfc059-8459-471e-b75d-068d78157f95
content:: Would you like to pick the course back up?
description:: You can also sign up for a course yourself on our [courses page](https://lensacademy.org/courses).
options::
- Yes, put me in a group in a later round
- Yes, but at my own pace
- No, but I'd like to take a different course
- Not right now

#### Question: Choice
id:: bfd78961-d5f7-4929-9f7a-da5d92c35a5c
content:: Would you be up for a short chat?
options::
- Yes
- Maybe later
- No thanks

#### Question: Open
id:: 9c9a118a-786b-41c0-b061-be36ad0339e3
content:: Is there anything we could have done differently that would have kept you in?
max-chars:: 500
optional:: true
