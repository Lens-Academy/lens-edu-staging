---
tags:
  - validator-ignore
---
# Writing Modules (AI Guide)

A module (`modules/<Name>.md`) sequences the learner path: lenses grouped by submodules, with learning outcomes declaring what gets tested. Shared field rules and validator errors: `Lens Edu/AI Guide/Element Reference.md`; how to sequence lenses well: `Lens Edu/AI Guide/Quality Patterns.md`.

Frontmatter: required `slug`, `title`; optional `id`, `contentId`, `discussion`, `tags`, `add_to_ai_context` (list of wikilinks whose content is added to the AI tutor's context for everything in the module).

Body = H1 sections:

```markdown
# Submodule: Welcome                  ← groups following sections under a heading
# Lens: Welcome                       ← inline lens: id:: + segments directly here
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

- A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both.
- **Learning outcome placement (processor ≥0.19.1):** declare outcomes first. A `# Learning Outcome:` *before* the first `# Submodule:` is module-level: the platform renders its test at the end of the module as an auto-generated "Test Your Understanding" entry (one outcome → a directly-openable row; several → one expandable submodule). A learning outcome *after* a `# Submodule:` marker (H1 or as an H2 child) belongs to that submodule — declare it before the lenses; its test renders at the end of that submodule regardless of where it is written. A dedicated `# Submodule: Test Your Understanding` wrapper is no longer needed, and combining one with module-level outcomes is a validation error.
- A `# Submodule:` marker may carry `add_to_ai_context:: [[wikilink]]` (one or more `[[...]]`) — that content is added to the AI tutor's context for every lens and test in the submodule. Use this for per-chapter source material (module-level covers the whole module; submodule-level scopes to one chapter).
- Referencing a learning outcome imports **only its test** — list the lenses that teach it explicitly, before the `# Learning Outcome:` ref.
