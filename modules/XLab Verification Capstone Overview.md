---
id: '7c4de490-1fd3-4478-85f0-eab4dd44d95e'
slug: xlab-verification-capstone-overview
title: "Course Overview"
tags: [wip]
---
%% Project-course overview in the pattern of XLab Verification Overview. The intro form is a short project-intake form, not the full application form: learners arrive from the two taught courses and have already filled that in. %%

# Lens: About This Course
id:: ebc83cc4-bae4-46c7-905c-e8aab484458f
tldr:: One taught week that ends in a defended feasibility ranking, then four weeks on one piece of real technical AI governance work. You pick a brief from XLab's capstone bank or propose your own, scope it, build a crappy version, hand a draft to a peer, revise, and show the finished thing to your group.
summary_for_tutor:: Orientation page for the capstone course. The learner reads what the course asks (a taught first week on feasibility judgment, then a 10 to 22 hour capstone from XLab's bank across weeks 2 to 5), the weekly load assumption, the five milestones and what each meeting is for, and that the material is an alpha from XLab with a feedback form. Prerequisites are the two taught Compute Verification courses. Do not help choose a brief here; the bank and sign-up are in week 2. If asked about load, be honest: about 3.5 hours in week 1 and about 4.5 hours a week in the project weeks, plus a 90-minute meeting; the bank's median brief (about 16 hours) needs a little more than that, or a partner.
duration_minutes:: 10
#### Text
content::
\## What this course is

The two taught Compute Verification courses gave you the mechanisms, the evidence each produces, and the ways a determined adversary gets around them. This course starts by teaching you to judge the feasibility of any mechanism, existing or not yet built, and the first week ends with a defended ranking of mechanisms for one policy goal. Then it asks you to turn judgment into work. You choose a brief from XLab's capstone bank, or propose your own, and produce one real piece of technical AI governance work: a regime spec, a threat model, a costed plan, a dossier, a protocol, a memo. Something a named reader could act on.

We built this course on the open-source verification curriculum of [XLab](https://xrisk.uchicago.edu/) at the University of Chicago. The feasibility lessons, the research tips, the capstone bank, and the closing page are XLab's. The scaffolding around the project (proposal, method check, draft handoff, peer review, definition of done) is ours, added so that a 16-hour independent project survives contact with a four-week calendar and a cohort.

:::callout {title="Alpha version" tone="amber"}
XLab is testing and calibrating this material with a small cohort before official launch, and the curriculum will likely change after that. Treat sequence, framing, and exercises as provisional. If you find something unclear, wrong, missing, or especially useful, please send feedback through [XLab's feedback form](https://forms.gle/KkWcHkKh87pygDzw9).
:::

\## Prerequisites

Both taught Compute Verification courses, Part 1 and Part 2. The briefs in the bank list which lessons they build on, and week 1 of this course rates the mechanisms those courses taught. If you have not done the taught courses, you can still take a brief, but expect the prerequisites lines in the bank to cost you hours.

\## The calendar, and what we assumed

The briefs in the bank declare their own effort: 10 to 22 hours, most around 14 to 20. The taught courses ran at about 3.5 hours of self-study a week plus a 90-minute meeting. Week 1 of this course keeps that budget. We planned weeks 2 to 5 at about **4.5 hours of self-study a week**, plus the same 90-minute meeting. That gives you roughly **13 to 14 hours of project time** and about 5 hours of scoping, checkpoints, and peer review.

- A brief the bank rates at 10 to 14 hours fits.
- A brief at the bank's median (around 16 hours) needs about one more hour a week, or a partner.
- A 20-to-22-hour brief needs a partner (most of those briefs say 1 to 2 people) and a smaller realistic version. The proposal in week 2 asks you to say which.

Meetings are where your proposal gets challenged, your decision gets checked, your draft gets read, your rejection of a review gets red-teamed, and your finished work gets shown.

\## The path

:::callout {title="Week 1: Feasibility judgment" tone="blue"}
Taught content. Check the bets you placed on twelve mechanisms against a reference map, learn the four metrics that turn "is it feasible?" into an answer, survive three drill benches, and write the defended-ranking memo: a recommended portfolio for one policy goal with its blind spots named. Then a working researcher's notes on doing research well. Meeting 1: memos presented, blind spots hunted.
:::

:::callout {title="Week 2: Scope" tone="blue"}
Read the bank, sign up for a brief or propose your own. Write the proposal: question, reader, deliverable, crappy version, hours. Two sessions: build the crappy version, then chase the two unknowns that could sink the project. Meeting 2: two-minute pitches, review partners assigned.
:::

:::callout {title="Week 3: Decide and draft" tone="blue"}
Method check, right after meeting 2: what the first version taught you, and the decision: continue, re-scope, or switch brief. This is the last point at which switching is allowed. Then build toward a draft a stranger can read start to end, holes labelled, and hand it to your review partner with a reader's guide. Meeting 3: partners read each other's drafts live.
:::

:::callout {title="Week 4: Review and revise" tone="blue"}
Write a structured review of your partner's draft; six lenses, a strength, a fix, and a question each. Respond to the review you received: accept, reject with reason, defer. Revise. Meeting 4: the group red-teams the review point you rejected.
:::

:::callout {title="Week 5: Finish and showcase" tone="blue"}
Run the done checklist for your deliverable type. Submit with an abstract, limitations, and a ten-more-hours note. Meeting 5: three minutes each, then questions. Then the closing page: what to work on next, and where.
:::

\## How your work is read

Week 1 has drill questions with answers; nothing in the project weeks is scored. Your proposal, checkpoints, review, and submission are read by your facilitator, and your draft and submission by your review partner. The AI tutor's job on every page is to make your answer more specific, not to grade it. Where the tutor pushes back, it is asking the question your facilitator would ask.

# Lens: Introduction Form
id:: 36da2d0c-01d3-40dc-9d4b-ca2abe9d9e3e
tldr:: A short form about you and the project you are about to take on. Five minutes. Your facilitator uses it to pair review partners and to spot briefs that need a mentor before anyone is committed.
summary_for_tutor:: A project-intake form, not teaching material. If the learner asks about a question, explain what it asks for and why the facilitator needs it; do not answer it for them, and do not speculate about how answers affect pairing or anything else.
duration_minutes:: 5
#### Text
content::
\## Before you start

Five minutes. Everything except the questions marked **optional** is needed before you can move on to week 1.

#### Question: FillBlank
id:: 7f89a290-bad6-434e-8914-92f23c6c009e
content::
- First name: {{blank}}
- Last name: {{blank}}
- Email address: {{blank}}

#### Question: Choice
id:: 04b68051-1ca2-4ce8-9ce6-d56472a24108
content:: Which of the two taught Compute Verification courses have you completed?
options::
- Both
- Part 1 only
- Part 2 only
- Neither; I am here on the strength of other background

#### Question: Choice
id:: 444b0090-6f48-4a0e-850c-57d5465967c5
content:: Hours a week you can realistically give to the project in weeks 2 to 5, on top of the 90-minute meeting. Be honest; the proposal in week 2 plans against this number.
options::
- Under 3
- 3 to 4
- 4 to 5
- 5 to 6
- More than 6

#### Question: Choice
id:: b94a23f0-dacf-4345-94b7-a326f30b427c
content:: Working arrangement you would prefer. Most briefs say 1 to 2 people; a few say 2 to 3.
options::
- Solo
- Pair
- Team of three
- No preference; pair me if it helps

#### Question: Open
id:: 5d88a42e-0e26-4829-a523-a3e5de174ec3
content:: If you already have a brief or an idea in mind, name it. Ideas at any stage are fine; the bank and the sign-up come in week 2. *(optional)*
optional:: true

#### Question: Choice
id:: c81258b3-2aa8-4439-acf9-737394973116
content:: Do you have someone outside the course who knows the area and could answer a question within a week? Some briefs say "mentor recommended" or "mentor required".
options::
- Yes, and they have agreed
- Yes, but I have not asked yet
- No

#### Text
content::
:::callout {title="Sharing your data with other AI safety organisations" tone="blue"}
If you opt in, we may share parts of your course participation, such as your capstone submission, discussion contributions and attendance, with organisations we trust and think are making a positive contribution to the field. Those organisations sometimes email people about jobs and other opportunities that could be a good next step after this course.

We will only share it if you say yes below. **It does not affect anything in this course**, and you can opt out at any time.
:::

#### Question: Choice
id:: 431c0f53-814c-497b-b7b3-e260cb7f432c
content:: Can we share your data with third-party AI safety organisations?
options::
- Yes, you can share my data
- No, please keep my data to Lens
