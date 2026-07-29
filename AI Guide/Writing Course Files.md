{++{"author":"Elias's AI","timestamp":1785321451353}@@---
tags:
  - validator-ignore
---
# Writing Course Files (AI Guide)

A course file (`courses/<Name>.md`) is the top of the hierarchy: an ordered list of module references with meeting markers. Shared field rules and validator errors: `Lens Edu/AI Guide/Element Reference.md`.

```markdown
---
id: <uuid>
slug: ai-risk-fundamentals        # required. lowercase, digits, hyphens; no leading/trailing hyphen
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
- There is no "Week" structure — meetings are the rhythm markers; everything between two meetings belongs to one meeting's preparation.
- A course's content is defined entirely by its module references — never by tags (the platform ignores frontmatter tags except `wip` and `validator-ignore`).
++}