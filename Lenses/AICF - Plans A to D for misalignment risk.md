---
id: '723c80e7-2c0d-42c1-b252-89633d701b4b'
title: "Plans A, B, C and D for misalignment risk"
tldr: "The same misalignment problem looks different depending on how much political will there is to deal with it. Ryan Greenblatt sorts possible worlds into Plans A to D, from an international agreement down to a few people inside a company that is not really trying, and says which work matters in each."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control), after the lenses on catching AIs and before 'Ten people on the inside'. The learner reads Ryan Greenblatt's 'Plans A, B, C, and D for misalignment risk' (October 2025). Plan A: enough will for a strong international agreement that mostly eliminates race dynamics and allows slowing down for a reasonably long period (about 10 years), plus massive investment in security and safety. Greenblatt puts about 5% on it and expects 7% takeover risk. Plan B: the US government treats buying lead time for US AI companies as among its top few national security priorities, not necessarily out of misalignment concern, so 1 to 3 years can be spent on misalignment risk. 10% likely, 13% takeover risk. Plan C: no serious government involvement, but the leading company has a lead of a few months (2 to 9) and is willing and institutionally able to spend much of it on misalignment, with a very fast, half-baked handoff to AIs. 25% likely, 20% takeover risk. Plan D: the leading company does not take misalignment seriously and takeoff is not slowed from outside, but 10 to 30 people inside take it seriously and have enough buy-in for about 3% of compute. 45% likely, 45% takeover risk. Plan E: almost nobody inside works on the risk, 15% likely, 75% takeover risk. He says he is inclined to focus on Plans C and D. Greenblatt keeps some control until handoff in Plans A to C ('somewhat janky' in C), but in Plan D says organisation-wide control 'should be mostly given up on', apart from measures that stop AIs escalating permissions or access. Plan D's safety team should instead focus on extracting non-sabotaged safety research, gathering strong evidence for risk, and making an AI plausibly safe to hand off to. The learner reads the post in three excerpts (the paragraph on regime switching and the footnotes are skipped), then a Lens note that Greenblatt co-authored 'AI 2040: Plan A' (2026), a detailed Plan A scenario, then answers a scored question matching four described worlds to Plans A to D and an unscored question on which of the unit's routes still fit Plan D. Do not tell the learner which plan we are in. If they ask, ask what level of political will they observe and which description it matches. If asked, YOLO'd means done with no care for risk, and handoff means handing safety work over to AIs."
reading_minutes: 10
tutor_minutes: 10
tags:
  - reading
---
#### Text
content::
Every route in this unit depends to some degree on how much AI companies and governments want to act on misalignment risk. Ryan Greenblatt, whose dialogue with Habryka you just read, sorts the possible worlds by that one variable and asks what the best plan is in each. Two questions follow the reading. Try the first from memory.

#### Article
source:: [[../articles/greenblatt-plans-a-b-c-and-d-for-misalignment-risk]]
from:: "I sometimes think about plans for how to handle misalignment risk."
to:: "More responsible trailing AI companies should focus on exporting safety work (in addition to policy/coordination work)."

#### Article
from:: "## Plan E"
to:: "(as this will might be spent incompetently)."

#### Article
from:: "Here is the takeover risk I expect given a central version of each of these scenarios"
to:: "look less compelling."

#### Text
content::
Greenblatt's numbers are from October 2025. In 2026 he co-authored [AI 2040: Plan A](https://ai-2040.com/) with Thomas Larsen, Romeo Dean, Brendan Halstead, Eli Lifland and Daniel Kokotajlo, a detailed scenario of what a Plan A world could look like.

#### Question: Open
id:: 60ee6c8f-2bd0-4df8-b189-951dfd7b704a
content::
Which of Greenblatt's plans fits each of these worlds, and what tells you so?

(a) The White House makes keeping US AI companies ahead of China a top security priority and tightens chip export controls, for national security rather than out of worry about misalignment.

(b) The leading company is five months ahead, and its board votes to spend most of that lead on misalignment risk, while the government does nothing.

(c) The leading company's CEO calls misalignment worries overblown and nobody outside slows it down, but a dozen researchers there run a small safety project with a few percent of the compute.

(d) The US and China sign a treaty that caps frontier training runs for eight years.
placeholder:: One line per plan.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Ryan Greenblatt sorts worlds by political will to handle AI misalignment risk. Plan A: enough will for a strong international agreement that mostly removes race dynamics and allows a long slowdown, about 10 years, driven by governments. Plan B: the US government treats buying lead time for US AI companies as a top national security priority, not necessarily out of misalignment concern, giving 1 to 3 years. Plan C: no serious government involvement, but the leading company is willing and able to spend much of its lead of a few months on misalignment risk, driven by its leadership. Plan D: the leading company does not take misalignment seriously and nothing slows it from outside, but 10 to 30 people inside take it seriously and have some buy-in, about 3% of compute. The matches: (a) Plan B, (b) Plan C, (c) Plan D, (d) Plan A. 25 per world: 15 for the right plan and 10 for a reason that points to who holds the will or how much lead time there is. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) Plan B: the US government buys lead time for US companies, even though its reason is security, not misalignment. (b) Plan C: no government help, but the leading company's leadership spends its few months of lead on safety. (c) Plan D: leadership doesn't care and nothing slows it from outside, only a small group inside works on the risk. (d) Plan A: governments agree internationally to slow down for years."
feedback-instructions:: The learner matched four worlds to Greenblatt's plans: (a) Plan B, since the US government buys lead time for national security reasons, (b) Plan C, since the leading company spends its few months of lead without government help, (c) Plan D, since only a small group inside cares and nothing slows the company from outside, (d) Plan A, since governments agree internationally to a long slowdown. In at most four sentences: confirm what is right, correct any wrong match in one sentence by naming who holds the will in that world, and add one detail they missed, such as the lead time in each plan (about 10 years, 1 to 3 years, a few months, about zero) or Greenblatt's guess that Plan D is the most likely (45%). No follow-up question. No generic praise. One turn.

#### Question: Open
id:: 8a2557a5-11dd-4069-aa6d-4b6690e8bbd0
content::
Greenblatt says that in Plan D, "Ensuring control at the level of the organization should be mostly given up on", and that he is inclined to focus on Plans C and D. Look at what he says the Plan D safety team should focus on instead. Which of this unit's routes so far still make sense in Plan D, and which do not? Say why.
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read Greenblatt's plans. Routes so far in the unit: blocking attacks while models are in use, catching attempts and acting on the evidence (shutting down, or few-shot catastrophe prevention by the safety team), getting useful safety work out of untrusted models during a window before they are too capable to control, and later in the unit cheap measures run by a few insiders and control as a condition of deployment. In Plan D Greenblatt says organisation-wide control should be mostly given up on, except things that stop AIs escalating permissions or access to the point where they can sabotage the safety work or mess with arbitrary things on the company's compute. The safety team should focus on extracting non-sabotaged safety research from the AI (a narrow version of the useful-work route), gathering strong evidence for risk (the evidence part of the catch route, which still needs someone to act on it), and making an AI plausibly safe to hand off to. So company-wide blocking and anything that needs leadership or governments to act fit Plan D badly, while narrow control around the safety team's own work and evidence-gathering still fit. In Plans A to C he keeps some control until handoff ("somewhat janky" in Plan C). Accept other reasoned mappings. The next lens, "Ten people on the inside", argues that cheap control measures can still be worth it in this kind of company, so do not settle that question here. In at most five sentences: say which parts of the mapping match Greenblatt's text, correct any misreading in one sentence, and name the most useful thing missed. Do not say which plan we are in. No generic praise. At most two turns.
