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

# Module: [[../modules/IABIED M1 Intro, Part 1]]
# Meeting: Meeting 1 name
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/IABIED Post-Meeting Survey]]
# Module: [[../modules/IABIED M2 Nonhuman Minds, Part 2]]
# Meeting: Meeting 2 name
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/IABIED Post-Meeting Survey]]
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`.

- Don't edit the target audience and value prop without explicitly permission from the user. And regularly check/flag if everything matches with landing page or marketing copy. 
- The target audience for a course are people with one or more of the listed features.
- Everything between two meetings belongs to one meeting's preparation.
- If the course has in-person meetings, the meeting doc template must be linked under the `# Meeting`. (see: [[Writing Meeting Docs]])
- Attach a native post-meeting survey with `survey:: [[../surveys/Survey Name]]` under each `# Meeting:` marker that should have one. See [[Writing Surveys]] for survey syntax, learner behavior, and validation rules.

Before creating a new course:
- Discuss target audience features and value proposition of that course with the user. 