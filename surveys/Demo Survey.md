{++{"author":"Elias's AI","timestamp":1787761770383}@@---
id: 'b3964bd3-dd3c-4c83-9a9e-ac5be6d31e08'
title: Demo Post-Meeting Survey
---

%% A survey is a flat file of #### segments, attached to a meeting in the course file with `survey::`. It uses the same response segments as lenses and tests (Question: Open, Rating, Choice, FillBlank, Ranking), keyed by their id::. Surveys never grade: no assessment-instructions, no [x] marks. Segments are required unless `optional:: true`. See [[../Lenses/Response to question segments]] for every field. %%

#### Text
content:: Thanks for showing up! This is a demo of the post-meeting survey. Submitting it counts your attendance for the meeting.

#### Question: Rating
id:: 8600b01e-015e-403e-93ec-3d2924c2c468
content:: How useful was this meeting?
scale:: 5
low-label:: Not at all
high-label:: Very

%% The buddy question is the one segment that still uses the legacy survey form: the platform reads the accountability-buddy credit off the snake_case `key:: buddy_texted`, which only legacy segments carry. Same for `key:: facilitation_interest`. %%

#### Choice
key:: buddy_texted
content:: Did you message your accountability buddy this week?
options::
- Yes
- No

#### Question: Choice
id:: 96559fa8-d3d2-4848-8238-785bb8b56ed9
content:: Which parts of this unit worked for you?
options::
- The readings
- The AI tutor discussions
- The group meeting
multi:: true
optional:: true

#### Question: Open
id:: c0827fb3-7429-4a8a-b4f6-871797e11d53
content:: What's one thing that worked well today?

#### Question: Open
id:: b5d3fb3d-9465-47da-bdfd-868871cef91a
content:: What's one thing the course, website, AI tutor, or meetings could do better?
optional:: true
++}