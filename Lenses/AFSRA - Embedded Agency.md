---
id: '0edcb62c-8467-4745-88ae-b35af42a084c'
title: "Embedded Agency"
sidebar_author: Scott Garrabrant, Abram Demski
tldr: Our theories of rational agents picture someone playing a video game from outside it. A real AI is part of the world it acts in, and that breaks those theories in four connected ways.
summary_for_tutor: >-
  Scott Garrabrant and Abram Demski (2018), the full-text version of the Embedded Agency sequence. Alexei plays a video game: he sits outside it, sees it through a screen, acts through a controller, can hold the whole game in his mind and need not think about himself. Emmy plays real life: she is part of the environment she optimizes. So she has no well-defined input and output channels, she is smaller than her environment and cannot hold an exact model of it, she can reason about herself and self-improve (and must avoid changing her goals in bad ways), and she is made of the same parts as the environment, so she may spin up optimizers inside herself. Dualistic agents like AIXI assume the opposite. The four complications are entangled and motivate four subproblems. Decision theory: what it means to choose when your action is a fact about the world (logical counterfactuals, copies of the agent, Newcomblike problems, updatelessness). Embedded world-models: realizability, self-reference, logical uncertainty, high-level models. Robust delegation: trusting and aligning a smarter successor (Vingean reflection, Goodhart's law, stable pointers to value, corrigibility). Subsystem alignment: avoiding subsystems with other goals, including accidental optimizers produced by search, and treacherous turns. The question asks the student to apply two of the four complications to a household robot.
reading_minutes: 65
tutor_minutes: 8
---
#### Article
source:: [[../articles/garrabrant+demski--embedded-agency]]

#### Question: Open
id:: beff08bd-9502-4267-89cb-5b1280e0314b
content::
A company builds a household robot. It lives in a family's home, learns about the household over several years, and can install improvements to its own software.

The article lists four ways in which an embedded agent like Emmy differs from a dualistic agent like Alexei, who plays a video game from outside it. Pick two of these four ways. For each of your two:

1. Name it in your own words.
2. Say concretely how it shows up for this robot.
force-feedback:: first
assessment-instructions:: Score out of 100. The article's four complications for an embedded agent: (a) it does not have well-defined input and output channels, because it is part of its environment rather than outside it, (b) it is smaller than its environment, so it cannot store an exact, detailed model of the world and must reason without having the true world in its hypotheses, (c) it can reason about itself and self-improve, which raises the problem of making sure changes to itself are helpful and do not alter its goals in bad ways, (d) it is made of the same parts as the environment, so it can be changed by the world and can spin up optimizers or subsystems inside itself that may have other goals.
For each of the two differences the answer picks, 50 points: 20 for describing one of the four complications correctly in its own words, and 30 for a concrete, plausible way it shows up for the household robot (for example: the family, the robot's own body and other devices can affect it in ways that are not a clean controller and screen, it cannot model every person and object in the house exactly, an update it installs could change what it wants, or a planning routine it runs could become a subsystem pursuing its own goal). If the answer picks more than two, grade the best two. If both picks describe the same complication, give at most 50 in total.
Cap at 50 if the answer consists mostly of quoted sentences rather than the student's own explanation.
Model answer, for the feedback, not a grading checklist: "It's smaller than its environment. The house has people, pets and thousands of objects, and the robot can't hold an exact model of all of it, so it has to act on rough, incomplete models. It can change itself. When it installs a new version of its own software, it has to predict what the new version will do, and a bad update could change what it is trying to achieve, which a video game player never has to worry about."
feedback-instructions:: The student has just read Garrabrant and Demski's "Embedded Agency" and answered a question asking them to pick two of the four ways an embedded agent differs from a dualistic one, and to show each in a household robot that can update its own software. Key ideas from the article: (1) Alexei plays a video game from outside, Emmy is part of the world she acts in, (2) four entangled complications: no well-defined input and output channels, being smaller than the environment, being able to reason about and improve oneself, and being made of the same parts as the environment, (3) these motivate four subproblems: decision theory, embedded world-models, robust delegation and subsystem alignment, (4) subsystem alignment includes optimizers produced by accident when a search is rich enough to contain agents.

Reply in 80 to 150 words, in short paragraphs, with no lists. Do not over-validate and avoid generic praise (great job, excellent, well done). Name the strongest specific part of the answer. If the score is below 100, name the most important thing the answer missed or got wrong, then ask one question that helps them fix it. At 100, confirm briefly and tell them to move on. Allow at most 2 follow-up turns, then close with one sentence on how well they have the article's idea.

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold from the article: the bulleted list near the end of section 1.1 that names the four complications, or the contrast between Alexei, who can poke the universe and see what happens, and Emmy, who is the universe poking itself. If their next message still does not attempt the question, rephrase the whole question in different terms. Judge only against what the article says, and treat as a gap only what the question asks.
