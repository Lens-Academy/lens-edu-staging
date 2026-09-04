---
id: '29fc60c2-5b19-4828-a3f9-c397b98e3640'
title: "Scope it: the proposal"
tldr: "One hour of scoping saves five hours of drifting. Turn the brief you signed up for into a bet you can lose gracefully: one question, one reader who would act on the answer, a deliverable with a definition of done, the crappy version you will build this week, and where your hours go."
summary_for_tutor: "Lens Academy scaffolding for XLab's capstone; not XLab source material. The learner read Aaron Scher's research tips and wrote the defended-ranking memo in week 1, and has just signed up for a brief from the bank (or proposed their own) in the previous lens. Sequence: framing text on what a proposal is for, an obviously made-up illustrative example, then seven questions: question and reader, deliverable and done, crappy and realistic versions, inputs and unknowns, hours plan, team size, mentor. The facilitator reads every answer and the learner pitches a two-minute version at meeting 2. Your job is to make each answer more specific, never to write it. Push on: a reader named by role and decision rather than 'policymakers'; a question rather than a topic; a crappy version small enough to finish in one sitting; unknowns that could actually sink the project. If the learner has not chosen a brief, send them back to the bank lens. If they propose their own idea, check it is relevant to technical AI governance and aimed at an AI-safety-related theme. Do not grade or rank the choice of brief."
tags: [wip]
duration_minutes: 60
---
#### Text
content::
\## Why scope before you build

You have a brief, or an idea of your own, from the sign-up sheet. The next thing most people do is open a blank document and start. The next thing you should do is spend one hour deciding what finished looks like, so that every later hour has somewhere to go.

The research tips you read last week ask three things of a project: a question someone will act on, a tractable corner of it, and a crappy first version before the good one. The proposal below asks you to write those three things down, plus two that a five-week calendar forces: what done means, and where the hours go.

A proposal is not a promise. It is a bet you can lose gracefully. At the start of week 3 you will check it against what the first version taught you, and you are allowed to change it then. What you are not allowed to do is skip it, because a project with no stated finish line has no way to be behind, and therefore no way to catch up.

\## What each part is for

- **Question and reader.** A topic ("compute accounting audits") cannot be finished. A question can ("what must an audit prove about each GPU for a regulator to accept it?"). The reader is one role facing one decision. If your answer would not change what they do, pick a different question.
- **Deliverable and done.** Format and length, then the three things the deliverable must contain before you would hand it over. Start from the brief's deliverable line if you took one from the bank; the bank says "two-page regime spec plus a one-page evasion annex", you say what goes in each page.
- **Crappy version, realistic version.** The crappy version is what you can produce in your first 90-minute session this week, using only what you already know. It is allowed to be embarrassing. The realistic version is what you will deliver in week 5 if nothing goes unusually well. Write both; the gap between them is your plan.
- **Inputs and unknowns.** What you carry in from the taught courses (your defended-ranking memo, a mechanism dossier, a red-team table), which two or three sources you start from, and the two things you do not know yet that could sink the project. The second half of this week exists to find those out.
- **Hours.** The brief declares its own effort, 10 to 22 hours across the bank. This course gives you about 13 to 14 hours of project time across weeks 2 to 5 at the default pace (see the course overview). If your brief asks for more, say now where the extra comes from: a partner, more hours a week, or a smaller realistic version.

:::callout {title="Illustrative example (made up, deliberately rough)" tone="neutral" collapse="closed"}
Brief: "Does Switching Off the Cooling Switch Off the Training?" from the bank.

**Question and reader.** If an inspector confirms that a named datacenter's cooling plant is off, what is the largest training workload that could still be running there, and for how long? Reader: the inspectorate officer who has to sign a certificate saying a halt is a halt. With the answer, they know which second observation to demand before signing; without it, they sign on cooling status alone.

**Deliverable and done.** A claim → observable → evasion → countermeasure table (one row per evasion route) plus a two-page note for the officer. Done means: at least four evasion rows with a source or a shown calculation each, one row marked "could not resolve" with what evidence would resolve it, and a first paragraph the officer could read on its own.

**Crappy version (this week, 90 minutes).** The table with three rows filled from memory of the covert-development module, no sources, no numbers. A one-paragraph note.

**Realistic version (week 5).** The table with every row I can source, rough magnitudes where I can compute them, an honest "unknown" where I cannot, and the two-page note.

**Inputs and unknowns.** From the taught courses: my defended-ranking memo rated physical-layer inspection as durable but narrow; this project is the narrowness made concrete. Sources: the two listed on the brief, plus whatever the hardware-layer lessons cited on thermal signatures. Unknowns that could sink it: whether any public source gives numbers on running accelerators with the plant off, and whether the answer differs so much between cooling designs that one table cannot hold it. Second session this week: ninety minutes of source hunting before writing anything else.

**Hours.** Brief says 12 to 18. I have about 4 hours a week. Plan across weeks 2 to 5: 3 / 4 / 3.5 / 3. If I am behind at the draft handoff, I drop the countermeasure column and deliver claim → observable → evasion only.
:::

#### Question: Open
id:: 99dde013-dc73-40a6-a87f-4e303a961150
content::
\## 1. Question and reader

State the question your project answers, in one sentence. Then name the reader who would act on the answer: their role, the decision they face, and what they would do differently with your answer than without it.
assessment-instructions:: The learner is scoping a capstone project and has been asked for one question and one reader. Give full credit when all three are present: a question (not a topic; it can be answered, and the answer could turn out either way), a reader named by role and situation rather than a category ("the officer who signs the halt certificate", not "policymakers" or "governments"), and a concrete difference the answer makes to that reader's decision. Give partial credit when the question is a topic, or the reader is a category, or the decision is missing. Do not judge whether the question is important or the brief is a good choice; that is the facilitator's job and the learner's.
feedback-instructions:: Do not praise. Take the weakest of the three parts and ask one question that would make it specific. If the question is a topic, ask what a one-sentence answer would look like and whether it could turn out to be "no". If the reader is a category, ask which desk in that category would open this document, and what is on it. If the decision is missing, ask what the reader does on Monday if the answer is yes versus no. Two to four sentences, then tell them to carry the sharper version into the next answer.

#### Question: Open
id:: f623ea63-5df7-4ad2-89b1-425db27da29e
content::
\## 2. Deliverable and done

Format and length of what you will hand over (spec, analysis, design, dossier, memo, notebook: use the brief's own deliverable line if you took one from the bank). Then the three things it must contain before you would call it finished.
assessment-instructions:: Give full credit when the answer names a format and a rough length, and lists three concrete contents that could each be checked present or absent ("an evasion annex with one row per route", "a sensitivity table over the three scenarios"), not qualities ("well argued", "thorough"). Partial credit if the format is there but the done-criteria are qualities rather than contents, or fewer than three.
feedback-instructions:: If any done-criterion is a quality rather than a content, ask what a reader would look for on the page to confirm it. If the deliverable is bigger than the brief's hours allow (a full treaty text in 15 hours), say so plainly and ask which part the reader needs most. Otherwise, one sentence confirming the finish line is checkable, and move on. No praise.

#### Question: Open
id:: e2d4f1e6-b859-4612-8060-b74b34535228
content::
\## 3. Crappy version, realistic version

Describe the version you can produce in your first 90-minute session this week, from what you already know, with no new reading. Then describe the realistic version you will deliver in week 5 if things go normally. Say what the difference between them is.
assessment-instructions:: Give full credit when the crappy version is small enough to finish in one sitting with no research (the learner names what it will contain), the realistic version is clearly bounded (not "the full thing"), and the difference is stated in terms of work (sources found, rows filled, numbers computed) rather than quality words. Partial credit if the crappy version still requires research, or the realistic version is unbounded.
feedback-instructions:: If the crappy version needs reading first, say that the point is to write before reading, and ask what they could put on the page right now. If the realistic version is the whole brief with no cuts, ask what they would cut if week 3 went badly. Keep it to three sentences. No praise.

#### Question: Open
id:: 98bf1844-5780-4bc8-9cd0-82a3b2decdd3
content::
\## 4. Inputs and unknowns

What do you carry in from the taught courses? Start with your defended-ranking memo from the feasibility lens: which of its judgments does this project build on or test? Which two or three sources will you start from (the brief's own sources count)? Then the two things you do not yet know that could sink the project, and how you will find out in your second session this week.
assessment-instructions:: Give full credit when the answer names something specific from the learner's own earlier work (a memo judgment, a dossier, a red-team result), two or three starting sources by name or link, and two unknowns each with a way to resolve it this week. An unknown must be something that could change the plan, not a detail. Partial credit if the earlier work is mentioned only generically ("what I learned about hardware"), or the unknowns have no resolution plan.
feedback-instructions:: If the unknowns are details rather than plan-changers, ask: if this turned out the bad way, what would you do differently? If the answer is nothing, it is not the unknown to chase. If no earlier work is named, ask which mechanism their defended-ranking memo rated, and whether this project would change that rating. Three sentences. No praise.

#### Question: Open
id:: a789bd73-8fa4-4d49-930f-30c919a2faf0
content::
\## 5. Hours

The brief's declared effort, the hours a week you can realistically give (you said in the intro form), a week-by-week split across weeks 2 to 5, and the first thing you will cut if you are behind at the draft handoff at the end of week 3.
assessment-instructions:: Give full credit when the numbers are present and consistent (the weekly split adds up to something near the brief's declared effort, or the learner says how they will close the gap: partner, more hours, smaller realistic version), and the cut is a named part of the deliverable rather than "work faster". Partial credit if the split is missing or the cut is vague.
feedback-instructions:: Check the arithmetic and say what you find in one sentence. If the split adds up to less than the brief asks and nothing closes the gap, name the gap and ask which of the three fixes (partner, hours, smaller version) they choose. If the cut is "work faster", say that is not a cut and ask for a part of the deliverable. No praise.

#### Question: Choice
id:: 19f674ea-ca1f-49b9-a486-8bc291670f95
content:: How are you working on this?
options::
- Solo
- Pair (name your partner in the next answer)
- Team of three (name your partners in the next answer)
feedback-instructions:: Logistics, not an exercise: this is for the facilitator, so do not grade it and do not comment on whether solo or team is the better way to work. Acknowledge in one line. If they chose Pair or Team of three, ask for the partners' names in their reply and tell them to repeat the names to their facilitator at meeting 2, because none of the answers that follow captures them.

#### Question: Choice
id:: 1db58e68-41b4-495e-8251-7c8e90ff0360
content:: Mentor. Some briefs say "mentor recommended" or "mentor required": someone who knows the area and can answer a question in a week.
options::
- I have someone I can ask, and have told them
- I have someone in mind but have not asked yet
- I do not have one and the brief says optional
- I do not have one and the brief says recommended or required (tell your facilitator at meeting 2)
feedback-instructions:: Logistics, not an exercise: this is for the facilitator, so do not grade it and do not judge the brief they chose. Acknowledge in one line. If they have someone in mind but have not asked, ask when they will. If they have none and the brief says mentor recommended or required, tell them to raise it with their facilitator at meeting 2 as the option says, and ask what one question they would want a mentor to answer first. Do not suggest particular people.

#### Text
content::
\## Before meeting 2

Bring a two-minute spoken version of this proposal (the question, the reader, the deliverable, the crappy version) and the crappy version itself from this week's first session. Your group will ask the two questions that matter most at this stage: who acts on this, and what did building the first version teach you. Your facilitator will pair projects into review partners at the meeting; you will read each other's drafts in weeks 3 and 4.
