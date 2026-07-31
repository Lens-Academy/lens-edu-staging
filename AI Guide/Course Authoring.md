---
tags:
  - validator-ignore
---
## What a course is

A **course** is a collection of `.md` files, defined in a course file (see [[Writing Course Files]]) that contains an ordered list of links to module files with markers in between that signal when a group going through that course would meet.

A module contains links to a set of learning outcomes and an ordered list of lenses.
Each lens is rendered as a separate page. They contain the actual learning content (readings, AI-tutor chats, questions, roleplays)

**lenses** — the actual learning content (readings, AI-tutor chats, questions, roleplays) — grouped into **submodules**, plus **learning outcomes** — one testable skill each, carrying the test the platform uses to check it (the test renders at the end of the module or submodule that declares the outcome). Lenses draw their reading material from **articles** and **video transcripts** stored alongside.

```
Course  (courses/<Name>.md)             one file per course
  # Module: [[../modules/<Name>]]       ordered module references
  # Meeting: <name>                     live-meeting point between modules
Module  (modules/<Name>.md)
  # Submodule: <name>                   groups the sections below it
  # Learning Outcome: <title>           source:: ![[../Learning Outcomes/<Name>]]
  # Lens: <title>                       source:: ![[../Lenses/<Name>]]  (or inline: id:: + segments)
Learning Outcome  (Learning Outcomes/<Name>.md)
  ## Test:                              id:: + #### Question segments with a scoring rubric
  # Suggested Lenses:                   author-facing candidates — NOT imported by modules
Lens  (Lenses/<Name>.md)                flat: frontmatter + H4 segments only
  #### Text | Chat | Article | Video | Question | Roleplay
Article (articles/*.md), Video transcript (video_transcripts/*.md)
                                        source material referenced by Article/Video segments
```

## Writing a specific file type

Read the matching guide first:

- Course file → [[Writing Course Files.md]]
- Module → [[Writing Modules.md]]
- Learning outcome → [[Writing Learning Outcomes.md]]
- Lens → [[Writing Lenses.md]]
- Article / video transcript → [[Writing Articles.md]]

## Two field syntaxes, don't mix them up

Field lists come from the content processor's `content-schema.ts` (`lens-platform/content_processor`, published as `lens-content-processor`) — the single source of truth.

- Frontmatter: YAML, single colon (`title: ...`) — file-level metadata.
- Body fields: `key:: value` (double colon, at line start) — section/segment data. A value continues over following lines until the next `key::` or heading. Duplicate keys in one section are an error.

Unknown frontmatter fields are tolerated (only near-typos of known fields get flagged), which is why authoring metadata like `authors:`, `readings:`, `reading-from:` appears in real files. Don't rely on unknown fields for anything the platform must act on.

## The 6 segment types

Segments are the `####` blocks inside a lens (and inside a Learning Outcome's `## Test:`). Segment headers take no title (`#### Text: Intro` is an error).

Fields per segment:

- `#### Text` — required: `content`. Optional: `optional`.
- `#### Chat` — required: `instructions`. Optional: `hidePreviousContentFromUser`, `hidePreviousContentFromTutor`.
- `#### Article` — none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Video` — none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Question` — required: `content`. Optional: `assessment-instructions`, `max-time`, `max-chars`, `enforce-voice`, `feedback`, `optional`.
- `#### Roleplay` — required: `id`, `content`, `ai-instructions`. Optional: `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional`.

Boolean fields take literal `true`/`false`. Defaults: `optional` false; `feedback` true on questions, false on roleplays; `hidePreviousContent*` false.

**Text** — prose shown to the learner. `content::` is markdown; escape any headings (`\##`).

**Chat** — open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article** — embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` and the text matched by `to::` (this is not a half-open range). Each anchor is independent — only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes) — copy them from the stored article via `read`, never from a summarizing web fetch.

**Video** — same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question** — learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay** — learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card — used for "Additional resources" footers.

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

