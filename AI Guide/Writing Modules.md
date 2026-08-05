---
tags:
  - validator-ignore
---
# Writing Modules (AI Guide)

Modules live in `modules/`.

```markdown
---
slug: example-module              # required — how courses reference the module
title: "Example Module Name"      # required
id: <uuid>                        # the module's stable UUID
add_to_ai_context:                # tutor context for the whole module
  - "[[../../Lens Edu Private/sub-folder/file]]"
---
# Submodule: Welcome        %← groups following sections under a heading%
# Lens: Welcome             %← inline lens%
id:: <uuid>
#### Text
content:: Welcome to the course...

# Submodule: Ch1 - Introduction
# Learning Outcome
source:: [[../Learning Outcomes/outcome name]]

# Lens: Optional Deep Dive            ← referenced lens
source:: [[../Lenses/Some Lens]]
optional:: true                       ← learner may skip
hide:: true                           ← hidden from the module page (requires optional:: true)
```

- Submodules are optional ways to further structure modules into sensible chunks
- Learning outcomes should be linked at the top of a (sub-)module. Their test is rendered at the end of it.
- A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both. Segment syntax: [[Writing Lenses]].

## Recommended pattern

- Start by deeply thinking about/discussing with the user what exactly you want to teach in a given module/submodule and create LOs based on this
- Before presenting a reading, ask one or multiple pre-reading primer questions in a separate lens that help the   in front of a  before , see `Writing Lenses.md`) → main reading lens → `# Learning Outcome:` ref. One outcome is usually taught by several lenses — list them all before the ref.
- Optional `- QA -` lenses hold depth for curious learners: link them via `::card` footers inside the main lens instead of adding them to the module path.
- Alternative candidate lenses live in the outcome's `# Suggested Lenses:` section — author hints only, never part of the learner path.
