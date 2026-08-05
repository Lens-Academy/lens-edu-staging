---
tags:
  - validator-ignore
---
## What a course is

A **course** is a collection of `.md` files, defined in a course file (see [[Writing Course Files]]) that contains an ordered list of links to module files with markers in between that signal when a group going through that course would meet.

A module (see [[Writing Modules]]) contains links to a set of learning outcomes and an ordered list of lenses.
Each lens is rendered as a separate page. They contain the actual learning content (readings, AI-tutor chats, questions, roleplays). (see [[Writing Lenses]])

Each learning outcomes (see [[Writing Learning Outcomes]]) define one testable skill and a set of tests, the platform uses to measure it (the test renders at the end of the module or submodule that declares the outcome). Lenses draw their reading material from **articles** and **video transcripts** stored alongside. (see [[Writing Articles.md]])

## The document model

Every content file is markdown with two kinds of structure: YAML frontmatter on top (file-level metadata, `key: value`) and a body of nested headings. A heading's section can carry its own metadata as `key:: value` lines under it — a value runs until the next `key::` or heading; duplicate keys in one section are an error. Unknown frontmatter fields are tolerated, but the platform only acts on documented fields.

## Rules that apply everywhere

- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall`
- **Wikilinks are relative** to the referencing file and must contain a `/`. (`source:: [[../articles/name]]`, `source:: [[../Lenses/Name]]`).
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Never change the id of already-published content.** Learner progress is keyed on these ids
- **Drafts**: add `wip` to `tags` while a file is unfinished — its errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
- **Comments**: `%% ... %%` (Obsidian) and `{>>{"author":"Elias's AI","timestamp":1785489958756}@@...<<}` (CriticMarkup) are stripped before parsing — safe for author notes anywhere.
- **`add_to_ai_context`** injects source material (e.g. chapter text from a private folder) into the AI tutor's context — use it whenever the tutor must discuss a text the student read elsewhere. Allowed on a lens (scopes to that lens), module frontmatter (whole module), or a `# Submodule:` marker (that submodule — the natural home for per-chapter book content). On a learning outcome it is a validation error.

## Validation

Changes sync to staging.lensacademy.org within seconds; the core team promotes to production (lensacademy.org) manually.

Check **https://staging.lensacademy.org/validate** after your changes land — it lists errors/warnings per file, filterable by course, categorized `production` (blocks promotion) vs `wip` (draft-only, from `tags: [wip]`). Fix production-category errors in files you touched before calling the work done.

Errors you'll actually hit:

- Missing/empty required frontmatter fields; slug format violations.
- Unquoted UUIDs that YAML turned into numbers.
- `source::` wikilink not relative (must contain `/`) or target missing.
- Fields on the wrong segment type (`from::` on a Text segment), field-name typos (Levenshtein ≤2 from a known field), duplicate fields in one section.
- Unescaped heading inside `content::`/`instructions::` (truncates the field; warning suggests escaping).
- Content before the first section header in a body (ignored, flagged).
- `hide:: true` without `optional:: true`; module reference cycles; `tldr` over 80 words; production file referencing a `wip`-tagged file.

