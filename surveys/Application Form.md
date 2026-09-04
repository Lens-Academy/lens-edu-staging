---
id: 'b1a4e6c2-7d3f-4a58-9c21-5e8f0d2a7b13'
title: Application Form
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

- Bachelors
- Masters
- PhD
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

#### Question
key:: why_applying
content:: Why are you applying to this course? How does it fit within your career plans? (100–200 words. Prioritise being concise and concrete; bullet points are fine.) 
max-chars:: 2000
required:: true


#### Question
key:: proud_projects
content:: Describe 1–3 projects you've done that you're most proud of (work-related is fine). Say exactly what you were responsible for. Prioritise being concise, concrete and showing outputs — links are great! (100–200 words.)
max-chars:: 2000
required:: true

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
