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

- A (sub-)module usually consists out of one or more LOs and one or more lenses
- Submodules are optional ways to further structure modules into sensible chunks
- Learning outcomes should be linked at the top of a (sub-)module. Their test is rendered at the end of it.
- A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both. Segment syntax: [[Writing Lenses]].

## Creation flow
1. Deeply think about/discuss with the user what exactly you want to teach in a given module/submodule and create LOs based on this (see [[Writing Learning Outcomes]])
2. Find excellent articles/videos/exercises to teach the LO (if the user tells you to do it by yourself, use multiple subagents to come up with possibilities and others to criticize them until you are certain what you have is the best possible way to achieve the agreed learning outcomes)

## Recommended patterns
- Before presenting a reading/video, ask one or multiple pre-reading primer questions in a separate lens.
- Add optional lenses with more in-depth readings/exercises for curious readers
	- If you Link them via `::card` footers inside the main lens instead of adding them to the module path.
- Alternative candidate lenses live in the outcome's `# Suggested Lenses:` section — author hints only, never part of the learner path.
