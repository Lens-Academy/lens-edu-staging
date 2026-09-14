---
id: 'd4f7a2b9-6c1e-4e35-8b0a-3f9c7e2d5a61'
title: Application Form (interview)
tags:
  - wip
---

#### Text
content:: This form should take 10–13 minutes. Please be wary if you're taking longer. Questions without a red star are optional.

#### Text
content:: ### About you

#### Question
key:: name
content:: First and last name. Or however you want to be called.
short:: true
required:: true

#### Question
key:: email
content:: Email address
short:: true
required:: true

#### Question
key:: linkedin_url
content:: LinkedIn URL
short:: true
placeholder:: https://www.linkedin.com/in/…
required:: true

#### Question
key:: other_profile_link
content:: Other profile link (Google Scholar, GitHub, personal website, blog)
short:: true

#### Choice
key:: education
content:: Highest level of completed or pursuing education.
options::
- High School
- Bachelors
- Masters
- PhD
- Other
required:: true

#### Question
key:: universities
content:: Universities studied or working at. (You can add multiple.)
required:: true

#### Choice
key:: career_stage
content:: Career stage
options::
- High school
- Bachelors
- Masters
- PhD
- PostDoc / Professor
- Early career (up to 3 years)
- Mid career (3–10 years)
- Expert career (10+ years)
required:: true

#### Choice
key:: fields
content:: Field of study or work (pick up to 3)
multi:: true
max-select:: 3
options::
- Computer Science
- ML/AI
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
required:: true

#### Choice
key:: employment_status
content:: Employment status
options::
- Employed (full-time)
- Employed (part-time)
- Self-employed / freelancer
- Not currently working
- Retired
- Student
required:: true

#### Question
key:: location
content:: Where are you based most of the time (City, Country)? You can name a few places if you are meaningfully located there.
short:: true

#### Text
content:: ### Career and intention

#### Interview
id:: 9e2c5b7a-4d81-4f6e-a3c9-7b1d8e4f2a56
content:: Two spoken questions, one at a time: why you are applying, and the work you are most proud of. Answer in your own words for a minute or two each, as you would in a short call. The interviewer may ask you to say more. You can switch to typing at any time.
questions::
- Why are you applying to this course, and how does it fit with your career plans?
- Tell me about one to three projects you are most proud of. What exactly were you responsible for, and what came out of them?
assessment-instructions:: **Question 1: motivation and fit**
Level 4: gives a concrete reason tied to this course's content, and a specific next step in their career the course serves (a role, a field, a decision), with a plausible link between the two.
Level 3: a concrete reason or a specific next step, not both.
Level 2: generic interest ("AI safety is important") with no personal plan.
Level 1: cannot say why beyond curiosity, or the answer is about something else.

**Question 2: projects and ownership**
Level 4: describes at least one project with what they personally did (not the team), a concrete output (a result, artifact, or number), and something that was hard or that they would change.
Level 3: a project with their own part and an output, but nothing on difficulty or judgement.
Level 2: names projects without saying what they did or what came out.
Level 1: no project, or only coursework described in general terms.

The transcript is the only evidence. Do not score writing quality or fluency, and do not penalise pauses or restarts.

#### Question
key:: ai_safety_programs
content:: Which courses, programs, or fellowships in AI safety have you done, or are doing?
required:: true

#### Choice
key:: engagement_hours
content:: Engagement hours in AI safety so far
options::
- Under 50 hours (about 1 week)
- 50–100 hours (2–3 weeks)
- 100–200 hours (4–6 weeks)
- 200–500 hours (6–12 weeks)
- 500+ hours (13+ weeks)
required:: true

#### Rating
key:: transition_intention
content:: How strong is your intention to transition to AI safety full-time in the near future (about 3–12 months)? Put 10 if you're already working full-time in AI safety, or in a paid fellowship.
scale:: 10
labels::
- No intention of moving into AI safety
- Very unlikely
- Unlikely
- Leaning against it, but open to it
- Neutral / undecided
- Leaning towards it
- Likely
- Very likely, actively exploring
- Almost certain, taking concrete steps
- Already working full-time or in a paid fellowship
required:: true

#### Text
content:: ### Concluding

#### Question
key:: heard_from
content:: Where did you hear about this course? Please be specific, e.g. "Saw it in the [community] chat" or "Got referred by [program]".
required:: true

#### Question
key:: nominations
content:: Who is the most exceptional person you would nominate for this course? Please include their email and LinkedIn. (You can nominate more than one; if they are a good fit we might reach out to them.)

#### Question
key:: feedback
content:: Do you have feedback for this form or for Lens overall?

#### Text
content:: **Sharing your data with third-party AI safety organisations.** If you opt in, we may share parts of your application and course participation (like your discussion contributions and attendance) with organisations we trust and think are making positive contributions to the field. These organisations sometimes email people with jobs or other opportunities that could serve as good next steps after this course. We will only share this data if you give us your consent below, and it will not affect your application decision. You can opt out at any time.

#### Choice
key:: data_sharing_consent
content:: Can we share your data with third-party AI safety organisations?
options::
- Yes, you may share my data
- No, do not share my data
required:: true
