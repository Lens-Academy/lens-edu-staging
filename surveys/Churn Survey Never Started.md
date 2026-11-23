---
id: 'bf7734b5-7336-463f-bd6d-0d79bd801d0f'
title: A few quick questions
---

%% Never-started variant of the churn survey (build churn-survey-targeting-fix, DRAFT 2026-11-23). Loaded by path `surveys/Churn Survey Never Started.md` (code constant CHURN_SURVEY_NEVER_STARTED_PATH). Sent only to someone who attended 0 meetings of their group. The existing `surveys/Churn Survey.md` is unchanged. Same option mechanics as it: Q1 and Q2 ranked (max 3), shuffled with the last option pinned. If this doc is missing or has no questions, the job asks these people nothing (fail closed). Never change an id:: once anyone has answered. %%

#### Text
content:: Thanks for signing up! You didn't make it to a session of your group, and we'd like to understand why, so we can make it easier for the people who join after you. This takes about two minutes.

#### Question: Choice
id:: e3de3d55-c5a4-4d1a-bfcf-43e91be1a874
content:: What got in the way of joining your group?
description:: Tap a choice again to undo it.
options::
- Work, study or another program took up the time
- Something came up (travel, illness, family)
- The session time didn't work for me
- I wasn't sure when or where my sessions were, or how to join
- I signed up, then wasn't sure the course was right for me
- I was worried about showing up without having done the reading
- I didn't get a group, or my group changed
- I found another way to learn this
- Something else
ranked:: true
max:: 3
shuffle:: true
pin-last:: 1

#### Question: Choice
id:: 930b8f2c-9025-4820-8028-1e0a5c97a819
content:: Which of these would most likely have got you to a first session?
options::
- A reminder with clear joining details just before my first session
- A different time slot, or an easy way to switch to another group
- A short note on what to expect, and that I don't need to prepare much
- A group matched to my level of experience
- A self-paced option with an occasional check-in
- A way to start a week or two later
- Nothing really, the timing just wasn't right for me
ranked:: true
max:: 3
shuffle:: true
pin-last:: 1

#### Question: Choice
id:: 1dbf1f57-4c20-4798-9497-62aefd322a44
content:: Would you like to pick the course up?
description:: You can also sign up for a course yourself on our [courses page](https://lensacademy.org/courses).
options::
- Yes, put me in a group in a later round
- Yes, but at my own pace
- No, but I'd like to take a different course
- Not right now

#### Question: Choice
id:: c41854ca-5ee4-48de-b08d-db106ac34b03
content:: Would you be up for a short chat?
options::
- Yes
- Maybe later
- No thanks

#### Question: Open
id:: e777786d-af96-4974-b983-4bd7d7efb72f
content:: Is there anything we could have done differently that would have got you to a session?
max-chars:: 500
