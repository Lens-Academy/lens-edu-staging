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
id: <uuid>                        # the module's stable UUID{--{"author":"Elias's AI","timestamp":1785937319549}@@ (`id` works as an alias)--}
add_to_ai_context:                # tutor context for the whole module
  - "[[../../Lens Edu Private/sub-folder/file]]"
---
# Submodule: Welcome        %← groups following sections under a heading%
# Lens: Welcome             %← inline lens%
id:: <uuid>
#### Text
content:: Welcome to the course...

# Submodule: Ch1 - Introduction
# Learning Outcome: Intelligence as prediction plus steering
source:: ![[../Learning Outcomes/Intelligence as prediction plus steering]]

# Lens: Optional Deep Dive            ← referenced lens
source:: ![[../Lenses/Some Lens]]
optional:: true                       ← learner may skip
hide:: true                           ← hidden from the module page (requires optional:: true)
```

- A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both.{++{"author":"Elias's AI","timestamp":1785926658472}@@ Segment syntax: `Lens Edu/AI Guide/Writing Lenses.md`.++}
- **Learning outcome {--{"author":"Elias's AI","timestamp":1785936643820}@@placement (processor ≥0.19.1):**--}{++{"author":"Elias's AI","timestamp":1785936643820}@@placement:**++} declare outcomes first. A `# Learning Outcome:` *before* the first `# Submodule:` is module-level: the platform renders its test at the end of the module as an auto-generated "Test Your Understanding" entry (one outcome → a directly-openable row; several → one expandable submodule). A learning outcome *after* a `# Submodule:` marker (H1 or as an H2 child) belongs to that submodule — declare it before the lenses; its test renders at the end of that submodule regardless of where it is written.{--{"author":"Elias's AI","timestamp":1785936644143}@@ A dedicated `# Submodule: Test Your Understanding` wrapper is no longer needed, and combining one with module-level outcomes is a validation error.--}
- A `# Submodule:` marker may carry `add_to_ai_context:: [[wikilink]]` (one or more {--{"author":"Elias's AI","timestamp":1785936644495}@@`[[...]]`) — that content is added to the AI tutor's context for every lens and test in the submodule. Use this for per-chapter source material (module-level covers the whole module; submodule-level scopes to one chapter).--}{++{"author":"Elias's AI","timestamp":1785936644495}@@`[[...]]`).++}
- Referencing a learning outcome imports **only its test** — list the lenses that teach it explicitly, before the `# Learning Outcome:` ref.

## Sequencing that works

- Per outcome, the proven path is: PQ lens (pre-reading primer, see `Writing Lenses.md`) → main reading lens → `# Learning Outcome:` ref. One outcome is usually taught by several lenses — list them all before the ref.
- Optional `- QA -` lenses hold depth for curious learners: link them via `::card` footers inside the main lens instead of adding them to the module path.
- Alternative candidate lenses live in the outcome's `# Suggested Lenses:` section — author hints only, never part of the learner path.
