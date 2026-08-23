{++{"author":"Elias's AI","timestamp":1787492982016}@@---
id: '13053f27-bc03-4f2a-87ce-8de24c3ce5de'
title: Behind the scenes
tldr: The four pages you just went through were written in a markdown editor by a mix of people and AI agents, checked by a validator, and were live on the site seconds after being saved. Here is the machinery a learner never sees.
summary_for_tutor: "Closing page of the Lens product tour, describing the authoring and operations stack: the collaborative editor with AI suggestions in CriticMarkup, the MCP relay that lets any AI agent author course content against the same guides, the continuous content validator, the course-agnostic skill tree of learning outcomes, and the cohort operations layer of meetings, surveys, attendance and the Lens Coach. No questions or chat."
reading_minutes: 4
tutor_minutes: 0
---

#### Text
content::
:::callout {title="What this page is" tone="blue"}
Everything up to here was the learner's side. This page is the production side: how the four pages you just read were written, checked and shipped, and what runs around them once a cohort starts.
:::

\## Courses are files, and the editor is the product

A course is a folder of markdown files. A course file lists modules, a module lists lenses and learning outcomes, a lens is the page you were just on. That is the whole model, and it is why a new course can be assembled from parts of old ones rather than rebuilt.

Authors work in a web editor over those files. The useful part is not the editing, it is the review: an AI agent's changes arrive as tracked suggestions, attributed to whoever's agent made them, and a human accepts or rejects them line by line. The same document can be worked on by a curriculum lead, a subject expert and three agents without anybody losing track of who wrote what.

%% SCREENSHOT SLOT 1: the editor with a lens open and pending AI suggestions visible in the margin, showing the accept/reject affordance and the "<name>'s AI" attribution. Paste as: ![The Lens editor with pending AI suggestions](URL) %%

\## Any AI agent can author into it

The editor is backed by a relay that speaks the Model Context Protocol. An author points their own AI agent at it, the agent gets the same authoring guides our team writes against, and it can read the corpus, import a source, draft a lens and run the validator without a human copying text between windows.

That is how partner organisations build on Lens without hiring a curriculum team, and it is the reason a course of this size is days of work rather than months.

%% SCREENSHOT SLOT 2: an AI agent session working against the relay, e.g. a terminal or chat transcript showing it reading the corpus and creating a lens. Paste as: ![An AI agent authoring course content through the relay](URL) %%

\## Nothing ships unvalidated

Content is validated continuously against the platform's schema: broken links between files, a reading anchor that no longer matches its article, a test that has no gradable question, an outcome missing its domain. Errors are listed per file and filterable per course, and draft material is separated from production material so that unfinished work cannot block a release.

Saving a file puts it on staging within seconds. The gap between "an author fixes a confusing question" and "the next learner sees the fix" is measured in seconds, not in edition cycles.

%% SCREENSHOT SLOT 3: the validator page (staging.lensacademy.org/validate) filtered to one course, showing the per-file error list. Paste as: ![The content validator](URL) %%

\## Learning outcomes are shared infrastructure

The test you are about to take is not owned by this tour. It lives in a learning outcome file with its own statement, its own rubric, a domain and a difficulty stage, and any course that teaches that skill can pull it in. The outcomes form a skill tree across the whole curriculum, which is what lets us say what a learner can do rather than which weeks they attended.

Because outcomes are separate from the lenses that teach them, we can also compare teaching routes: two different readings aimed at the same outcome, measured against the same test.

%% SCREENSHOT SLOT 4: the skill tree view, showing outcomes grouped by domain with stages and locked/unlocked state. Paste as: ![The skill tree of learning outcomes](URL) %%

\## The cohort layer

Most learners take these courses in a group. The course file marks where the weekly meetings fall, each meeting carries a discussion document, and the post-meeting survey doubles as the attendance record, so participation data arrives without anyone chasing a spreadsheet. Facilitators are trained on the platform, in a course built the same way this one was. Outside course hours, learners have a coach they can bring any question to.

%% SCREENSHOT SLOT 5: the ops dashboard, ideally the surveys or attendance tab with real cohort data (anonymised). Paste as: ![Cohort operations dashboard](URL) %%

\## What you just did

Five pages, one imported article, one video clip, six graded interactions and a roleplay. Same tooling, same validator, same review process as the courses we run for real cohorts. The test on the next page is the last piece: an outcome, a rubric, and a pass or fail that means something.
++}