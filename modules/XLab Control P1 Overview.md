---
id: '41288b48-ff90-412f-99d0-03da227778eb'
slug: xlab-control-p1-overview
title: "Course Overview"
tags:
  - work-in-progress
---
%% Orientation module before Unit 1, added September 2026 to match the Compute Verification courses. Based on XLab's public track page (https://aisafetytracks.com/tracks/control). Day summaries mirror the Day N overview lenses in each unit; keep them in sync. %%

# Lens: About This Course
id:: 75e01a0e-4d70-44c5-b7ed-d21cbc91a234
tldr:: Assume a frontier model may be scheming and design so it still cannot hurt you. This course works through the first half of XLab's AI Control curriculum: why control, the founding paper, catching schemers, the toolkit, and high-stakes monitoring.
summary_for_tutor:: Orientation page before Unit 1. The learner reads what the course is about, that it is built on XLab's open-source AI Control curriculum, what each of the five days covers and how the days run, what the prerequisites are, and that AI Control 2 is a separate course that continues from here. Do not teach later content in detail; if asked, point to the day that covers it, or say that collusion, legibility, low-stakes control, sandbagging, reward seekers and deals belong to the second course.
reading_minutes:: 3
tutor_minutes:: 0
#### Text
content::
\## What this course is about

Alignment tries to make a model want what we want. AI control asks what holds if that failed: can we deploy a model that may be deliberately working against us, get useful work out of it, and still make sure it cannot cause a catastrophe? This Lens Academy course works through that question from the case for control to the concrete machinery of high-stakes monitoring. It is built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago, a hands-on technical track that reads the field's primary literature in full, with exercises woven between the sections. Everything is here on Lens: the readings, XLab's explanations, the exercises and the interactive pieces. Each lesson ends with a Works cited box linking the original sources.

\## What you will learn

By the end of the five days you will be able to explain why control is a distinct line of defense from alignment and why it is easier to evaluate; read the founding control paper and its protocols, trusted and untrusted monitoring, editing and deferral, and say what a red team is measuring; build an attack tree for a deployed model and prioritise the threats on it; argue both for and against control research and place a protocol on the safety-usefulness frontier; sort control work into detection, prevention, response, evaluations and environments; and follow how monitoring, resampling and rogue-deployment defenses work in a real high-stakes deployment.

\## How the course runs

Five days. Each day is about four to five hours of reading and exercises on your own, and ends with a group meeting to work through the arguments the readings leave open. The times we give are ours, estimated from what a learner actually does including the exercises, so they are longer than the figures on XLab's site. A few lessons are marked optional; follow curiosity rather than completeness.

XLab asks for comfort reading papers and familiarity with AI safety at the level of an introductory course. If you have done AI Risk Fundamentals or its equivalent, you are ready.

\## The five days

:::callout {title="Day 1: Why control" tone="blue"}
Why assume a frontier model may be scheming and design so it still cannot hurt you: the case for control as a second line of defense behind alignment, and attack trees as the way to think about what a model could do to you.
:::

:::callout {title="Day 2: The founding paper and passing the buck" tone="blue"}
The paper that started the field: trusted monitoring, untrusted monitoring, editing and deferral, measured against a red team that tries to insert backdoors. Then the question of when it is safe to let AIs take over the work of keeping AIs safe.
:::

:::callout {title="Day 3: Catching schemers, prioritising threats, and the case against control" tone="blue"}
Why catching a model red-handed is a win rather than a failure, which threats to prioritise and how diffuse threats like research sabotage differ from concentrated ones, then the arguments for and against control, the safety-usefulness tradeoff, and how to judge what control buys you.
:::

:::callout {title="Day 4: Plans, the control toolkit, and high-stakes framing" tone="blue"}
The Plans A to D landscape for misalignment risk, then the taxonomy of control work: detection, prevention and response mitigations, control evaluations, environments, and the map of areas of control work. Closes with the framing for high-stakes control.
:::

:::callout {title="Day 5: High-stakes monitoring and mitigation" tone="blue"}
Win, continue and lose scenarios; rogue deployments inside and outside the lab; a systems architecture for autonomous research agents; monitoring and mitigation in real deployments; resampling as a control technique; and why settings for high-stakes control research are hard to build.
:::

\## What comes after

This is the first of two courses on XLab's AI Control curriculum. AI Control 2 continues with guided exercises on collusion and legibility, low-stakes control, sandbagging and capability elicitation, threat models beyond scheming, and deals with early misaligned AIs.

# Lens: Introduction Form
id:: dbf29b2b-3f49-4289-bf9f-8691fb0306f7
tldr:: A one-time form about you, your background, and what you want from this course. It takes 10 to 13 minutes and you need to complete it before moving on.
summary_for_tutor:: An intake form, not teaching material. If the learner asks about a question, explain what it is asking for and why we ask; do not answer it for them, do not speculate about how answers affect selection, and do not discuss other learners' answers.
duration_minutes:: 12
#### Text
content::
\## Before you start

This form takes 10 to 13 minutes. Please be wary if you're taking longer.

Questions marked **optional** can be skipped. Everything else is needed before you can move on to Unit 1.

\## About you

#### Question: FillBlank
id:: 4f2bcd21-27ad-4410-912d-a2ce444d8032
content::
- First name: {{blank}}
- Last name: {{blank}}
- Email address: {{blank}}
- LinkedIn URL: {{blank}}

#### Question: Open
id:: 52ad04c3-f16a-4494-a1e1-d20d786bb3ee
content:: Please put your CV as markdown. (If you don't have one to hand, pass it through an AI to convert it. Copy-pasting your Linked-in is also fine.)

#### Question: Open
id:: f4e4eaa6-0b3a-4cf4-8a61-2527c22cc776
content:: Another profile link, if you have one worth seeing. Google Scholar, GitHub, a personal site, a blog. *(optional)*
optional:: true

#### Question: Choice
id:: 15db28c0-9bbb-4692-9687-875e431b0016
content:: Highest level of education
options::
- Bachelors
- Masters
- PhD

#### Question: Open
id:: dd6b48f6-6931-4777-8dad-112a69fca06f
content:: Which universities have you studied or worked at? List a few if that fits you better than one.

#### Question: Choice
id:: f97cfe70-1f58-4ad0-b71b-38492ba0ec26
content:: Career stage
options::
- High school
- Bachelors
- Masters
- PhD
- PostDoc or Professor
- Early career (under 3 years)
- Mid career (3 to 10 years)
- Expert career (over 10 years)

#### Question: Choice
id:: 2b9c550f-9118-4e95-a3fe-a576ed6343a1
content:: Field of study or work. Pick up to three.
options::
- Computer Science
- ML / AI
- Business
- Mathematics
- Physics
- International Relations
- Economics
- History
- Law
- Philosophy
- Politics
- Policy
- Biology
- Chemistry
- Medicine
- Psychology
- Engineering (not software)
- Materials Science
- Neuroscience
- Other
multi:: true
max-select:: 3

#### Question: Choice
id:: 5d62983c-ddd1-4805-bb58-fd9207c494ac
content:: Employment status
options::
- Employed (full-time)
- Employed (part-time)
- Self-employed or freelancer
- Not currently working
- Retired
- Student

#### Question: Open
id:: aea7d621-439e-4310-bb29-03999b602207
content:: Where are you based most of the time? A city and country is enough, for example Oxford, United Kingdom. Name a few places if you are meaningfully located in more than one. *(optional)*
optional:: true

#### Text
content::
\## Career and intention

#### Question: Open
id:: 592c849c-b7b1-47e8-baf1-2e718306f4b8
content:: Why are you applying to this course, and how does it fit your career plans? 100 to 200 words. Be concise and concrete. Bullet points are fine.

#### Question: Open
id:: 2a354774-6bf2-4640-8ac3-af4406421a78
content:: Describe one to three projects you are most proud of. Work counts. Say exactly what you were responsible for, and show outputs where you can. Links are great. 100 to 200 words.

#### Question: Open
id:: 20a5aa93-68b0-43d4-9d58-5607dcaa3fc1
content:: Which courses, programs or fellowships in AI safety have you done, or are you doing?

#### Question: Choice
id:: 43d171bc-83fc-421b-9035-b944b38d92d7
content:: Roughly how many hours have you spent engaging with AI safety?
options::
- Under 50 (about a week)
- 50 to 100 (2 to 3 weeks)
- 100 to 200 (4 to 6 weeks)
- 200 to 500 (6 to 12 weeks)
- Over 500 (13 weeks or more)

#### Question: Rating
id:: 71d1d481-54f0-44dd-83ad-c8017e9ac056
content:: How strongly do you intend to move into AI safety full-time in the next 3 to 12 months? Pick 10 if you are already working in it full-time or in a paid fellowship.
scale:: 10
labels::
- No intention to
- Very unlikely
- Unlikely
- Leaning against it
- Genuinely unsure
- Leaning towards it
- Likely
- Very likely
- Actively working towards it now
- Already full-time or in a paid fellowship

#### Text
content::
\## Before you go

#### Question: Open
id:: b5b7f773-02d4-4512-b436-17b3de1095e7
content:: Where did you hear about this course? Please be specific, for example "saw it in the [community] chat" or "referred by [program]".

#### Question: Open
id:: a2ecbd54-a292-4d90-bc8e-384a3c8eb62c
content:: Who is the most exceptional person you would nominate for this course? Please include their email and linkedin below! (You can nominate more than one, if they are a good fit we might reach out to them.) *(optional)*
optional:: true

#### Question: Open
id:: 439435df-fe07-4e4c-91fc-6a4d5d166471
content:: Any feedback on this form, or on Lens generally? *(optional)*
optional:: true

#### Text
content::
:::callout {title="Sharing your data with other AI safety organisations" tone="blue"}
If you opt in, we may share parts of your application and course participation, such as your discussion contributions and attendance, with organisations we trust and think are making a positive contribution to the field. Those organisations sometimes email people about jobs and other opportunities that could be a good next step after this course.

We will only share it if you say yes below. **It will not affect your application in any way**, and you can opt out at any time.
:::

#### Question: Choice
id:: 69ac1016-030d-4356-846b-533c19410d22
content:: Can we share your data with third-party AI safety organisations?
options::
- Yes, you can share my data
- No, please keep my data to Lens
