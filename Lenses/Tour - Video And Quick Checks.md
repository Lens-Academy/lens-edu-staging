---
id: '3ccfcdfc-66d8-4020-98f4-27171b3676a0'
title: Video and quick checks
tldr: A video excerpt clipped to the 45 seconds that matter, followed by the four fast question types. Everything except the confidence rating is graded, and the grading is done by a model reading a rubric, not by string matching.
summary_for_tutor: "Tour page demonstrating the Video segment (a 0:00 to 0:45 clip of the Kurzgesagt explainer, played beside its transcript) and the four quick response types. The four questions are deliberately about the platform rather than about AI safety, so that a visiting funder or partner can answer each in seconds and watch the grading work: a graded choice about what is authored versus generated, a graded ranking of the building blocks by size, a fill in the blank mixing graded text with a graded number, and an ungraded rating that asks how much of the product the tour has actually shown."
reading_minutes: 5
tutor_minutes: 5
---

#### Text
content::
:::callout {title="What this page demonstrates" tone="blue"}
A **Video segment**, clipped by timestamp to the part the author assigned and played next to its transcript, so a learner can search it and a tutor can quote it.

Then the four quick response types. Multiple choice, ranking and fill in the blank are graded; the rating is not, because a self-report is data about the person rather than about the answer. Grading runs through a model reading the author's rubric, which is why a fill in the blank accepts an equivalent phrasing rather than only the exact string.

The four below are about this platform rather than about AI safety, so each takes a few seconds. On a real course they carry the subject matter instead.
:::

#### Video
source:: [[../video_transcripts/kurzgesagt-ai-humanitys-final-invention]]
from:: 0:00
to:: 0:45

#### Question: Choice
id:: 724ab18c-21f9-45b8-be63-061af6f3477b
content:: A course author writes the pages of a course in plain text files. Which one of these is **not** something they write?
options::
- [x] The score your answer receives
- The rubric your answer is graded against
- The brief that tells the tutor how to behave on this page
- The start and stop anchors that pick which part of the source you are shown
shuffle:: true
feedback-instructions:: In two or three sentences, no praise. The author writes the rubric, the tutor brief and the excerpt anchors; the score is produced at run time by a model reading that rubric against what the reader wrote. That split is the whole design: authors control the standard, the platform applies it to every learner at once.

#### Question: Ranking
id:: 1a941306-19f3-4eec-a939-40baf153b1a6
content:: Put the pieces of a Lens course in order, smallest first.
items::
- A segment: one question, one video clip, one stretch of reading
- A lens: the page you are on right now
- A module: a chunk of material, usually one week of it
- A course: modules in order, split into weeks by group meetings
assessment-instructions:: The authored order is the correct one, from smallest unit to largest: segment, lens, module, course. Full credit for the exact order. Partial credit for any ordering that keeps the containment relationships right for most pairs. There are no valid alternative orders and no ties.
feedback-instructions:: Two sentences, no praise. If the order is right, note that the nesting is why a lens can be reused by more than one course without being copied. If it is wrong, name the pair that is out of place.

#### Question: FillBlank
id:: 43f8316a-c584-4914-893f-6b4dba9b7810
content:: On the previous page, the source was cut down to the assigned part by a {{from|from anchor}} anchor and a {{to|to anchor}} anchor, and the rest of the article stayed on the page, {{collapsed|hidden|folded away}}. This tour is {{number 5}} lenses long, including this one.
assessment-instructions:: Give 25 points per blank. The first two blanks are the words "from" and "to"; accept them with or without the word "anchor". The third blank wants the idea that the unassigned text is still present but folded away; accept collapsed, hidden, folded, or any equivalent. The numeric blank is 5; award nothing for a different count, since it is stated on the first page and countable in the sidebar.
feedback-instructions:: Two sentences, no praise. If any blank was missed, give the answer plainly and say why it matters that the rest of the article stays reachable rather than being cut out.

#### Question: Rating
id:: a722f2ab-6bff-4111-9393-ce414513d241
content:: How much of what this platform can do do you feel these pages have shown you so far?
scale:: 7
low-label:: Barely scratched it
high-label:: Pretty much all of it
feedback-instructions:: Do not reassure, do not grade, do not sell. In two sentences, name one capability these pages have genuinely not shown, chosen to fit their answer: the weekly group meetings and their discussion documents, the post-meeting survey that doubles as the attendance record, the facilitator training that runs on this same platform, the coach a learner can bring any question to outside course hours, or the skill tree that tracks which outcomes a learner has passed across every course they take.

#### Text
content::
Ratings are never scored. They are how the platform learns which pages move confidence and which only move completion, which is the measurement a course needs in order to get better between cohorts. That one also tells us how this tour is doing.
