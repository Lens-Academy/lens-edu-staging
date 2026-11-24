---
id: 'cae62088-b7ab-46e4-abe9-e76bb9f73889'
title: Navigator Application
---

#### Text
content:: Thanks for wanting to navigate with Lens! These questions help us get to know you. It takes about 15 minutes, and questions without a red star are optional. **Please answer without AI assistance: we're interested in your own thinking and voice, and bullet points are welcome.**

#### Text
content:: **About you**

#### Question
key:: full_name
content:: Full name
description:: As you'd like it on our records and for your intro call.
max-chars:: 100
short:: true
required:: true

#### Question
key:: cv_link
content:: Link to your CV, LinkedIn, etc.
max-chars:: 300
short:: true

#### Question
key:: location
content:: Where will you live while navigating (City, Country)?
description:: We need this for paid navigator contracts.
max-chars:: 100
short:: true

#### Text
content:: **Your experience**
slot:: lens_history

#### Choice
key:: facilitation_experience
content:: Have you led group discussions or taught before?
description:: No experience yet is fine: we train every navigator.
options::
- Yes, regularly
- A few times
- Not yet
required:: true

#### Question
key:: facilitation_experience_detail
content:: If you have, tell us a little about it: where, and who was in the group.
max-chars:: 1000

#### Question: Rating
key:: ai_safety_context_self_rating
content:: How would you rate your own AI safety context, from 1 to 10?
description:: 1 means you're new to AI safety. 10 means you work in the field and could lead a discussion on any part of it.
scale:: 10

#### Question
key:: ai_safety_context_self_rating_why
content:: Why that number?
max-chars:: 1000
required:: true

#### Question
key:: material_background_detail
content:: Apart from Lens, have you taken or navigated any other AI safety courses, fellowships or programs? Which ones?
max-chars:: 1000

#### Question
key:: other_course_credentials
content:: Any certificates or credentials from those? Paste a link, or tell us what they are.
max-chars:: 500
short:: true

#### Text
content:: **Why you want to navigate**

#### Question
key:: why_navigate_ai_safety
content:: Why do you want to navigate AI safety group discussions? A few sentences is plenty.
max-chars:: 1500
required:: true

#### Question
key:: why_navigate
content:: Why do you want to navigate for Lens, and join the Lens team, specifically?
max-chars:: 1500
required:: true

#### Question
key:: navigator_skills
content:: What do you think makes a high-quality navigator or facilitator?
max-chars:: 1500
required:: true

#### Text
content:: **Commitment and capacity**

#### Choice
key:: ca_commitments
content:: If you're applying for the Context Accelerator: you'll take the course alongside your group, and you'll help us shape the process by trying new parts of navigator training and selection with us and telling us what works. Can you commit to both?
options::
- Yes
- Not sure, I'd like to talk about it
- I'm not applying for the Context Accelerator
required:: true

#### Question
key:: sessions_per_week_min
content:: Group sessions per week you could lead: minimum
max-chars:: 3
short:: true
required:: true

#### Question
key:: sessions_per_week_ideal
content:: Group sessions per week you could lead: ideal
max-chars:: 3
short:: true
required:: true

#### Question
key:: sessions_per_week_max
content:: Group sessions per week you could lead: maximum
max-chars:: 3
short:: true
required:: true

#### Text
content:: **Last few things**

#### Choice
key:: heard_about_lens
content:: How did you hear about Lens?
options::
- A Lens course
- A friend or colleague
- An AI safety community or newsletter
- Social media
- Other
required:: true

#### Question
key:: heard_about_lens_detail
content:: If other, or if someone referred you, tell us where or who.
description:: Please be specific, for example: "[Name] recommended it", "a post by [name] on LinkedIn", or "found it searching for AI safety courses".
max-chars:: 300
short:: true

#### Question
key:: nominee
content:: Who's the most exceptional person you'd nominate to navigate with Lens? Include their name and email.
description:: You can nominate more than one. If we think they'd be a great fit, we may reach out to them.
max-chars:: 500

#### Choice
key:: nominee_mention_ok
content:: Can we mention your name when we reach out to them?
options::
- Yes
- No

#### Question
key:: anything_else
content:: Anything else you'd like us to know?
