---
tags:
  - validator-ignore
---
## What a course is

A **course** is a collection of `.md` files, defined in a course file (see [[Writing Course Files]]) that contains an ordered list of links to module files with markers in between that signal when a group going through that course would meet.

A module (see [[Writing Modules]]) contains links to a set of learning outcomes and an ordered list of lenses.
Each lens is rendered as a separate page. They contain the actual learning content (readings, AI-tutor chats, questions, roleplays). (see [[Writing Lenses]])

Each learning outcomes (see [[Writing Learning Outcomes]]) define one testable skill and a set of tests, the platform uses to measure it (the test renders at the end of the module or submodule that declares the outcome). Lenses draw their reading material from **articles** and **video transcripts** stored alongside. (see [[Writing Articles.md]])

## {--{"author":"Elias's AI","timestamp":1785926657210}@@Field syntax

Frontmatter is standard YAML. Body fields use `key:: value`; a value continues until the next `key::` or heading, and duplicate keys in one section are an error. Unknown frontmatter fields are tolerated.

## --}The {--{"author":"Elias's AI","timestamp":1785926657210}@@6 segment types--}{++{"author":"Elias's AI","timestamp":1785926657210}@@document model++}

{--{"author":"Elias's AI","timestamp":1785926657210}@@Segments are the `####` blocks inside a lens (and inside a Learning Outcome's `## Test:`). Segment headers take no title (`#### Text: Intro` --}{++{"author":"Elias's AI","timestamp":1785926657210}@@Every content file ++}is {--{"author":"Elias's AI","timestamp":1785926657210}@@an error).

Fields per segment:

- `#### Text` — required: `content`. Optional: `optional`.
- `#### Chat` — required: `instructions`. Optional: `hidePreviousContentFromUser`, `hidePreviousContentFromTutor`.
- `#### Article` — none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Video` — none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Question` — required: `content`. Optional: `assessment-instructions`, `max-time`, `max-chars`, `enforce-voice`, `feedback`, `optional`.
- `#### Roleplay` --}{++{"author":"Elias's AI","timestamp":1785926657210}@@markdown with two kinds of structure: YAML frontmatter on top (file-level metadata, `key: value`) and a body of nested headings. A heading's section can carry its own metadata as `key:: value` lines under it ++}—{--{"author":"Elias's AI","timestamp":1785926657210}@@ required: `id`, `content`, `ai-instructions`. Optional: `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional`.

Boolean fields take literal `true`/`false`. Defaults: `optional` false; `feedback` true on questions, false on roleplays; `hidePreviousContent*` false.

**Text** — prose shown to --}{++{"author":"Elias's AI","timestamp":1785926657210}@@ a value runs until ++}the {--{"author":"Elias's AI","timestamp":1785926657210}@@learner. `content::` is markdown; escape any headings (`\##`).

**Chat** — open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article** — embeds an excerpt of an `articles/` file. `from::`/`to::`--}{++{"author":"Elias's AI","timestamp":1785926657210}@@next `key::` or heading; duplicate keys in one section++} are{--{"author":"Elias's AI","timestamp":1785926657210}@@ exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** --}{++{"author":"Elias's AI","timestamp":1785926657210}@@ an error. That's ++}the {--{"author":"Elias's AI","timestamp":1785926657210}@@excerpt contains the text matched by `from::` and the text matched by `to::` (this is not --}{++{"author":"Elias's AI","timestamp":1785926657210}@@whole format: ++}a{--{"author":"Elias's AI","timestamp":1785926657210}@@ half-open range). Each anchor--}{++{"author":"Elias's AI","timestamp":1785926657210}@@ course body++} is{--{"author":"Elias's AI","timestamp":1785926657210}@@ independent — only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt--}{++{"author":"Elias's AI","timestamp":1785926657210}@@ `# Module:` / `# Meeting:` headings; a module body++} is {--{"author":"Elias's AI","timestamp":1785926657210}@@shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes) — copy them from the stored article via `read`, never from a summarizing web fetch.

**Video** — same idea for `video_transcripts/` files; `from::`/`to::`--}{++{"author":"Elias's AI","timestamp":1785926657210}@@`# Submodule:` / `# Lens:` / `# Learning Outcome:` sections whose `source::` / `id::` lines++} are{--{"author":"Elias's AI","timestamp":1785926657210}@@ timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in --}{++{"author":"Elias's AI","timestamp":1785926657210}@@ section metadata; ++}a lens {--{"author":"Elias's AI","timestamp":1785926657210}@@must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading --}{++{"author":"Elias's AI","timestamp":1785926657210}@@body ++}is {--{"author":"Elias's AI","timestamp":1785926657210}@@several --}`####{--{"author":"Elias's AI","timestamp":1785926657210}@@ Article` blocks with only `from::`/`to::`.

**Question** — learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay** --}{++{"author":"Elias's AI","timestamp":1785926657210}@@ <segment>` sections whose fields are `::` lines. Unknown frontmatter fields are tolerated ++}— {--{"author":"Elias's AI","timestamp":1785926657210}@@learner talks with a persona defined --}{++{"author":"Elias's AI","timestamp":1785926657210}@@metadata like `authors:` ++}in{--{"author":"Elias's AI","timestamp":1785926657210}@@ `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::`--}{++{"author":"Elias's AI","timestamp":1785926657210}@@ real files++} is{--{"author":"Elias's AI","timestamp":1785926657210}@@ the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card — used for "Additional resources" footers.--}{++{"author":"Elias's AI","timestamp":1785926657210}@@ fine, don't remove it — but the platform only acts on documented fields.++}

## Rules that apply everywhere

- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall` (existing content uses `\##`; the validator suggests `!##` — both work).
- **Wikilinks are relative** to the referencing file and must contain a `/`. Convention: module `source::` refs use the embed form (`source:: ![[../Lenses/Name]]`), segment and suggested-lens `source::` refs the plain form (`source:: [[../articles/name]]`, `source:: [[../Lenses/Name]]`). The parser accepts both — match the convention, don't "fix" the other form in existing files.
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Never change the id of already-published content.** Learner progress is keyed on these ids; regenerating one (even a format-invalid placeholder the validator complains about) silently orphans all completion data for that item at the next production promotion. The runtime tolerates format-invalid ids — leave live ones in place, or coordinate a progress remap with the platform team before promoting an id change.
- **Drafts**: add `wip` to `tags` while a file is unfinished — its errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
- **Comments**: `%% ... %%` (Obsidian) and `{>>{"author":"Elias's AI","timestamp":1785489958756}@@...<<}` (CriticMarkup) are stripped before parsing — safe for author notes anywhere.
- **Naming:** prefix content files with the course prefix (`IABIED - Define Intelligence`, `IABIED M1 Intro and Nonhuman Minds, Part 1`) so a course's files sort and search together. Do not add `tags:` for grouping — the platform ignores frontmatter tags except `wip` and `validator-ignore`.
- **`add_to_ai_context`** injects source material (e.g. chapter text from a private folder) into the AI tutor's context — use it whenever the tutor must discuss a text the student read elsewhere. Allowed on a lens (scopes to that lens), module frontmatter (whole module), or a `# Submodule:` marker (that submodule — the natural home for per-chapter book content). On a learning outcome it is a validation error.
- **`authors:`** credits humans and AI pairs (`Chris+Claude`) — keep it updated; it's tolerated metadata, not schema.

## Validation

Changes sync to staging.lensacademy.org within seconds; the core team promotes to production (lensacademy.org) manually. **Never push to the `Lens-Academy/lens-edu-staging` or `lens-edu-production` git repos directly** (no `git push`, no `gh api`) — the staging repo is continuously force-synced from the relay; external pushes break the sync.

Check **https://staging.lensacademy.org/validate** after your changes land — it lists errors/warnings per file, filterable by course, categorized `production` (blocks promotion) vs `wip` (draft-only, from `tags: [wip]`). Fix production-category errors in files you touched before calling the work done.

Errors you'll actually hit:

- Missing/empty required frontmatter fields; slug format violations.
- Unquoted UUIDs that YAML turned into numbers.
- `source::` wikilink not relative (must contain `/`) or target missing.
- Fields on the wrong segment type (`from::` on a Text segment), field-name typos (Levenshtein ≤2 from a known field), duplicate fields in one section.
- Unescaped heading inside `content::`/`instructions::` (truncates the field; warning suggests escaping).
- Content before the first section header in a body (ignored, flagged).
- `hide:: true` without `optional:: true`; module reference cycles; `tldr` over 80 words; production file referencing a `wip`-tagged file.

