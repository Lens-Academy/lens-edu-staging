---
tags:
  - validator-ignore
---
# Writing Course Files (AI Guide)

Course files live in `courses/`.

```markdown
---
id: <uuid>
slug: ai-risk-fundamentals        # required
title: "AI Risk Fundamentals"     # required
description: "Shown on the course page."
tags: ...
discussion: https://discord.com/channels/...
---
%%
Target audience:
- Feature 1: ...
- Feature 2: ...

Value prop:
- ...
- ...

Links:
- Links to marketing materials/messages & landing-pages
%%

%%
Week 1 goals:
- Goal 1
- Goal 2
%%

application-survey:: [[../surveys/Application Form]]

# Module: [[../modules/Course M1 Intro, Part 1]]
# Meeting: Meeting 1 name
{--{"author":"Luc's AI","timestamp":1790521953001}@@meeting-doc-template:: https://docs.google.com/document/d/...--}{++{"author":"Luc's AI","timestamp":1790521953001}@@meeting-doc:: [[../meetings/Course/Meeting 1]]++}
survey:: [[../surveys/Course Post-Meeting Survey]]
facilitator-survey:: [[../surveys/Navigator Session 1 Debrief]]
%%
Week 2 goals:
- Goal 1
- Goal 2
%%
# Module: [[../modules/Course M2 Nonhuman Minds, Part 2]]
# Meeting: Meeting 2 name
{--{"author":"Luc's AI","timestamp":1790521954750}@@meeting-doc-template:: https://docs.google.com/document/d/...--}{++{"author":"Luc's AI","timestamp":1790521954750}@@meeting-doc:: [[../meetings/Course/Meeting 2]]++}
survey:: [[../surveys/Course Post-Meeting Survey]]
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`.

- Don't edit the target audience and value prop without explicitly permission from the user. And regularly check if everything matches with landing page or marketing copy. (flag if not)
- The target audience for a course are people with one or more of the listed features.
- Everything between two meetings belongs to one meeting's preparation.
- If the course has in-person meetings, the meeting {--{"author":"Luc's AI","timestamp":1790521956987}@@doc template--}{++{"author":"Luc's AI","timestamp":1790521956987}@@doc's Markdown++} must be linked under the `# {--{"author":"Luc's AI","timestamp":1790521956987}@@Meeting`.--}{++{"author":"Luc's AI","timestamp":1790521956987}@@Meeting` with `meeting-doc:: [[../meetings/<Course>/Meeting N]]`.++} (see: [[Writing Meeting Docs]]){++{"author":"Luc's AI","timestamp":1790521956987}@@ An older course may still carry `meeting-doc-template:: <Google Doc URL>`; when a meeting has both, the Markdown is used.++}
- Every meeting should have a learner survey linked with `survey:: [[../surveys/Survey Name]]`. (See [[Writing Surveys]])
- A course that people apply to carries `application-survey:: [[../surveys/Application Form]]` in the preamble, the `field:: value` lines between the frontmatter and the first `# Module:`. The linked survey file uses the normal survey format and is shown in the enrolment wizard after availability or group choice; enrolment is refused until the learner submits it, one response per learner per cohort. The value must be a wikilink, a raw URL is warned about and ignored, and a misspelled key containing "surve" is warned about too. Put the line directly above the first `# Module:`, below the author notes, as the courses that use it do. Any position in the preamble parses, because `%%` comments are stripped before the preamble is read, but a field written inside a comment is dropped with no warning at all. Leave the line off demo, internal and work-in-progress courses, where a required form would block click-through.
- Every facilitated meeting should also have a navigator survey linked with `facilitator-survey:: [[../surveys/Navigator Survey Name]]`. It uses the same survey file format, is shown only to facilitators, and unlocks when the meeting ends without requiring learner attendance or check-in. The same navigator survey can be reused across meetings; use a distinct first-session survey when intake or baseline questions differ.

Before creating a new course:
- Discuss target audience features and value proposition of that course with the user.
- Thend discuss goals for each week