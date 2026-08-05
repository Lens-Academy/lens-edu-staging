---
tags:
  - validator-ignore
---
# Writing Course Files (AI Guide)

{--{"author":"Elias's AI","timestamp":1785936642772}@@A course file (`courses/<Name>.md`) is the top of the hierarchy: an ordered list of module references with meeting markers. Shared field rules and validator errors: `Lens Edu/AI Guide/Course Authoring.md`.--}{++{"author":"Elias's AI","timestamp":1785936642772}@@Course files live in `courses/`.++}

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
# Module: [[../modules/IABIED M2 Nonhuman Minds, Part 2]]
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`.

- The body is only `# Module:` wikilink refs and `# Meeting: <name>` markers, in learner order.
- Everything between two meetings belongs to one meeting's preparation.
