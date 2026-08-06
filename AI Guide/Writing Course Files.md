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
tags: [IABIED]
discussion: https://discord.com/channels/...
---
# Module: [[../modules/IABIED M1 Intro, Part 1]]
# Meeting: Introduction
meeting-doc-template:: https://docs.google.com/document/d/...
# Module: [[../modules/IABIED M2 Nonhuman Minds, Part 2]]
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`.

- The body is only `# Module:` wikilink refs and `# Meeting: <name>` markers, in learner order.
- Link the meeting doc template 
- Everything between two meetings belongs to one meeting's preparation.
