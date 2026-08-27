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

# Module: [[../modules/Course M1 Intro, Part 1]]
# Meeting: Meeting 1 name
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/Course Post-Meeting Survey]]
{++{"author":"Elias's AI","timestamp":1787850347062}@@facilitator-survey:: [[../surveys/Navigator Session 1 Debrief]]
++}# Module: [[../modules/Course M2 Nonhuman Minds, Part 2]]
# Meeting: Meeting 2 name
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/Course Post-Meeting Survey]]{++{"author":"Elias's AI","timestamp":1787850347062}@@
facilitator-survey:: [[../surveys/Navigator Post-Meeting Survey]]++}
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`.

- Don't edit the target audience and value prop without explicitly permission from the user. And regularly check if everything matches with landing page or marketing copy. (flag if not)
- The target audience for a course are people with one or more of the listed features.
- Everything between two meetings belongs to one meeting's preparation.
- If the course has in-person meetings, the meeting doc template must be linked under the `# Meeting`. (see: [[Writing Meeting Docs]])
- Every meeting should have a {--{"author":"Elias's AI","timestamp":1787850355404}@@link--}{++{"author":"Elias's AI","timestamp":1787850355404}@@learner survey linked with `survey:: [[../surveys/Survey Name]]`. (See [[Writing Surveys]])
- Every facilitated meeting should also have a navigator survey linked with `facilitator-survey:: [[../surveys/Navigator Survey Name]]`. It uses the same survey file format, is shown only++} to {++{"author":"Elias's AI","timestamp":1787850355404}@@facilitators, and unlocks when the meeting ends without requiring learner attendance or check-in. The same navigator survey can be reused across meetings; use ++}a {++{"author":"Elias's AI","timestamp":1787850355404}@@distinct first-session ++}survey {--{"author":"Elias's AI","timestamp":1787850355404}@@under it. (See [[Writing Surveys]])--}{++{"author":"Elias's AI","timestamp":1787850355404}@@when intake or baseline questions differ.++}

Before creating a new course:
- Discuss target audience features and value proposition of that course with the user. 