{++{"author":"Elias's AI","timestamp":1787493114396}@@---
id: '3ccfcdfc-66d8-4020-98f4-27171b3676a0'
title: Video and quick checks
tldr: A video excerpt clipped to the 45 seconds that matter, followed by the four fast question types. Everything except the confidence rating is graded, and the grading is done by a model reading a rubric, not by string matching.
summary_for_tutor: "Tour page demonstrating the Video segment (a 0:00 to 0:45 clip of the Kurzgesagt explainer, played beside its transcript) and the four quick response types: a graded multiple choice on the mountain gorilla comparison, a graded ranking of the historical warnings in chronological order, a fill in the blank mixing graded text and a graded number, and an ungraded confidence rating that sets up the roleplay page."
reading_minutes: 5
tutor_minutes: 5
---

#### Text
content::
:::callout {title="What this page demonstrates" tone="blue"}
A **Video segment**, clipped by timestamp to the part the author assigned and played next to its transcript, so a learner can search it and a tutor can quote it.

Then the four quick response types. Multiple choice, ranking and fill in the blank are graded; the confidence rating is not, because self-report is data about the learner rather than about the answer. Grading runs through a model reading the author's rubric, which is why a fill in the blank accepts an equivalent phrasing rather than only the exact string.
:::

#### Video
source:: [[../video_transcripts/kurzgesagt-ai-humanitys-final-invention]]
from:: 0:00
to:: 0:45

#### Question: Choice
id:: 724ab18c-21f9-45b8-be63-061af6f3477b
content:: The article argues that humans dominate other species because the human brain has capabilities other animals lack, and it uses one animal to make the point about where that leaves us if AI surpasses human intelligence. Which one?
options::
- [x] The mountain gorilla, whose fate depends on human goodwill
- The ant, which is numerous but individually powerless
- The domesticated dog, which was shaped by us to be useful
- The chess grandmaster, who is now reliably beaten by software
shuffle:: true
feedback-instructions:: Name what the learner's choice implies. The gorilla comparison is about a species whose survival now depends on the goodwill of something more capable, with no hostility involved. The ant and the dog point at numbers and at domestication, which is a different argument. The chess answer is about a narrow capability, which the article treats separately. Two or three sentences, no praise.

#### Question: Ranking
id:: '1a941306-19f3-4eec-a939-40baf153b1a6'
content:: The article traces the worry a long way back. Put these in the order they happened, earliest first.
items::
- Samuel Butler writes "Darwin among the Machines"
- Alan Turing writes "Intelligent Machinery, A Heretical Theory"
- I. J. Good describes the intelligence explosion
- Nick Bostrom publishes "Superintelligence"
- Hundreds of experts sign the Center for AI Safety statement
assessment-instructions:: The authored order is the correct chronological order: Butler 1863, Turing 1951, Good 1965, Bostrom 2014, the Center for AI Safety statement 2023. Give full credit for the exact order. Give partial credit for correct relative relationships, in particular for placing the three twentieth-century items before the two twenty-first-century ones. A learner who has the century-level structure right but swaps Turing and Good has largely succeeded.
feedback-instructions:: If the order is wrong, say which single swap matters most and why the date is worth knowing. If it is right, note in one sentence what the spread of dates implies about how new this concern is. Two or three sentences.

#### Question: FillBlank
id:: '43f8316a-c584-4914-893f-6b4dba9b7810'
content:: In 2023, hundreds of AI experts and other notable figures signed a statement saying that mitigating the risk of extinction from AI should be a global priority alongside {{pandemics}} and {{nuclear war}}. The 2022 survey of AI researchers that the article cites had a response rate of {{number 17}} percent.
assessment-instructions:: Give 33 points per blank. Accept equivalent wording and minor misspellings for the two text blanks. For the numeric blank, the article states 17 percent; accept 17, award partial credit for a close figure, and award nothing for a figure that would change how the survey should be read.
feedback-instructions:: If the response rate blank was missed, say why the figure matters: a 17 percent response rate means the survey describes the researchers who chose to answer, not the field.

#### Question: Rating
id:: 'a722f2ab-6bff-4111-9393-ce414513d241'
content:: How confident are you that you could explain this argument to a smart friend who thinks it is science fiction, and hold up when they push back?
scale:: 7
low-label:: Not at all
high-label:: Completely
feedback-instructions:: Do not reassure and do not grade. In two sentences, say what a learner at this stated confidence should watch for on the next page, where they will have to do exactly that against someone who disagrees.

#### Text
content::
Ratings like that one are never scored. They are how the platform learns which lenses move confidence and which only move completion, which is the measurement a course needs in order to get better between cohorts.
++}