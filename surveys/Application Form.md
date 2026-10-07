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
content:: Where are you based most of the time (City, Country)?
description:: You can name a few places if you are meaningfully located there.
short:: true

#### Text
content:: ### Career and intention

#### Question
key:: why_applying
content:: Why are you applying to this course? How does it fit within your career plans?
description:: 100–200 words. Prioritise being concise and concrete; bullet points are fine. Feel free to use voice-to-text to save your time.
max-chars:: 2000
required:: true

#### Question
key:: proud_projects
content:: Describe 1–3 projects you've done that you're most proud of (work-related is fine).
description:: Say exactly what you were responsible for. Prioritise being concise, concrete and showing outputs: links are great! 100–200 words.
max-chars:: 2000
required:: true

#### Choice
key:: engagement_hours
content:: Engagement hours in AI safety so far
options::
- Under 50 hours (about 1 week full-time)
- 50–100 hours (2–3 weeks full-time)
- 100–200 hours (4–6 weeks full-time)
- 200–500 hours (6–12 weeks full-time)
- 500+ hours (13+ weeks full-time)
required:: true

#### Choice
key:: ais_work_status
content:: What is your current AI safety stage? If several apply, pick *the highest* on the list.
description:: Pick where you are now, not what you've done before. Count a role or programme you've been accepted to that starts within 3 months.
options::
- In or starting a paid full-time AI safety job
- In or starting a paid full-time AI safety fellowship or funded research, 3 months or longer (e.g. MATS)
- In or starting paid part-time AI safety work (e.g. BlueDot facilitating), or a paid fellowship shorter than 3 months (e.g. ERA)
- In or starting a selective unpaid programme (e.g. SPAR or ARENA)
- Doing unpaid contributions (e.g. volunteering, advocacy or a local group)
- Applying to AI safety roles or programmes
- Exploring AI safety, not applying yet
- Not pursuing AI safety right now
required:: true

#### Choice
key:: ai_safety_programs
content:: Which courses, programs, or fellowships in AI safety have you done, or have been accepted to? Pick all that apply.
multi:: true
options::
- None so far
- Self-study
- University course or local AI safety group
- AI Safety Collab (ENAIS)
- BlueDot Courses
- BlueDot Rapid Grant
- BlueDot Career Transition Grant
- BlueDot Facilitating
- Center for AI Safety course
- AI Safety Camp
- ML4Good
- Global Challenges Project
- Lens Academy Course
- Lens Academy Project
- Lens Academy Facilitating (volunteer)
- ARENA
- Pathfinder
- SPAR
- ERA Fellowship
- Cooperative AI course
- Cooperative AI Summer School
- Cooperative AI PhD Fellowship
- BASE (Black in AI Safety and Ethics)
- Sentient Futures course (e.g. AI × Animals)
- Sentient Futures Project Incubator
- CAIDP (Center for AI and Digital Policy)
- TARA
- Vista Institute course
- Vista Institute Fellowship
- Generator Residency
- Iliad Intensive
- Iliad Fellowship
- Apart Sprint (hackathon)
- Apart Fellowship
- Heron AI Security Fellowship
- Horizon Fellowship
- Talos Fellowship
- IAPS AI Policy Fellowship
- Pivotal Research Fellowship
- PIBBSS Fellowship
- LASR Labs
- GovAI
- MATS
- Constellation (Astra or other fellowship)
- Anthropic Fellows Program
- OpenAI Fellows Program
- Other (please write it below)
required:: true

#### Question
key:: ai_safety_programs_other
content:: In 1–4 sentences, describe your current AI safety work, and add any details about the programs above.
description:: For example: "Volunteering 5h/week for PauseAI; did BlueDot's AGI Strategy course (completed)" or "Applying to SPAR and MATS this month; did ARENA 7.0".
max-chars:: 600
required:: true

#### Rating
key:: transition_intention
content:: How strong is your intention to transition to AI safety full-time in the near future (about 3–12 months)?
description:: Put 10 if you're already working full-time in AI safety, or in a paid fellowship.
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

#### Choice
key:: ais_connections
content:: How many people working in AI safety could you ask for advice or a referral?
options::
- None
- 1–2
- 3–5
- 6–10
- More than 10
required:: true

#### Text
content:: ### Concluding

#### Choice
key:: heard_from
content:: Where did you hear about this course? Pick all that apply.
multi:: true
options::
- AISafety.com
- BlueDot Impact community
- 80,000 Hours
- AI Alignment Slack
- LinkedIn
- Lens Academy (earlier course, website or email)
- Friend or colleague
- Another program or fellowship
- Discord, Slack or chat group
- AI assistant
- Web search
- LessWrong, EA Forum or a blog
- Newsletter or mailing list
- X (Twitter)
- Event or conference
- Other (please write it below)
required:: true

#### Question
key:: heard_from_other
content:: Please be specific if you can, e.g. "Saw it in the [community] chat" or "Got referred by [program]".


#### Question
key:: nominations
content:: Who is the most exceptional person you would nominate for this course?
description:: Please include their email and LinkedIn. You can nominate more than one; if they are a good fit we might reach out to them.

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
