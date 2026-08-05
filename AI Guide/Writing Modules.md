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

- Submodules are optional ways to further structure modules
- A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both. Segment syntax: [[Writing Lenses]].
- Learning outcomes should be linked at the top of a (sub-)module and their test declare outcomes first. A `# Learning Outcome:` *before* the first `# Submodule:` is module-level: the platform renders its test at the end of the module as an auto-generated "Test Your Understanding" entry (one outcome → a directly-openable row; several → one expandable submodule). A learning outcome *after* a `# Submodule:` marker (H1 or as an H2 child) belongs to that submodule — declare it before the lenses; its test renders at the end of that submodule regardless of where it is written.
- A `# Submodule:` marker may carry `add_to_ai_context:: [[wikilink]]` (one or more `[[...]]`).
- Referencing a learning outcome imports **only its test** — list the lenses that teach it explicitly, before the `# Learning Outcome:` ref.

## Sequencing that works

- Per outcome, the proven path is: PQ lens (pre-reading primer, see `Writing Lenses.md`) → main reading lens → `# Learning Outcome:` ref. One outcome is usually taught by several lenses — list them all before the ref.
- Optional `- QA -` lenses hold depth for curious learners: link them via `::card` footers inside the main lens instead of adding them to the module path.
- Alternative candidate lenses live in the outcome's `# Suggested Lenses:` section — author hints only, never part of the learner path.
