---
tags:
  - validator-ignore
---
# Course Authoring (AI Guide){--{"author":"Elias's AI","timestamp":1785489958756}@@

Lens Academy courses are plain markdown documents in this **"Lens Edu"** folder. Humans edit them in the web editor (editor.lensacademy.org), AI agents edit them through the lens-relay MCP.
Changes appear within a few seconds on staging.lensacademy.org and get manually deployed to production lensacademy.org by the core team.

## Read next

| Task | Read |
|------|------|
| Writing a specific file type | the matching guide in `Lens Edu/AI Guide/`: `Writing Course Files.md`, `Writing Modules.md`, `Writing Learning Outcomes.md`, `Writing Lenses.md`, `Writing Articles.md` |
| Segment syntax (Text/Chat/Article/Video/Question/Roleplay), shared field rules, validator errors | `Lens Edu/AI Guide/Element Reference.md` |
| Authoring lenses, learning outcomes, or modules | `Lens Edu/AI Guide/Quality Patterns.md` --}{++{"author":"Elias's AI","timestamp":1785489958756}@@

Everything shared that any content edit needs: how courses fit together, the field syntaxes, segment types, cross-file rules, and validation. How to write each specific file type lives in its own guide ++}—{--{"author":"Elias's AI","timestamp":1785489958756}@@ the proven pedagogical patterns (read together with the element reference) |
| Writing the outcome statement itself (scoping, phrasing, testability) | `Lens Edu/AI Guide/Writing Learning Outcomes.md` |
| Human-facing intro for content creators | `Lens Edu/Content Creation Guide.md` |--}{++{"author":"Elias's AI","timestamp":1785489958756}@@ read that guide before writing (routing below). Exact syntax comes from the content processor (`lens-platform/content_processor`, published as `lens-content-processor`); its `content-schema.ts` is the single source of truth.++}

{--{"author":"Elias's AI","timestamp":1785489958756}@@## Content hierarchy

```
Course  (courses/<Name>.md)             one file per course
  # Module: [[../modules/<Name>]]       ordered module references
  # Meeting: <name>                     marks a live-meeting point between modules
Module  (modules/<Name>.md)
  # Learning Outcome: <title>           source:: ![[../Learning Outcomes/<Name>]] — declared FIRST:
                                        module-level before all submodules, submodule-level before
                                        --}{++{"author":"Elias's AI","timestamp":1785489958756}@@## How a course fits together

A **course** is an ordered list of **modules** with live-meeting markers between them — everything between two meetings is one meeting's preparation. A module sequences the learner path: **lenses** — the actual learning content (readings, AI-tutor chats, questions, roleplays) — grouped into **submodules**, plus **learning outcomes** — one testable skill each, carrying the test the platform uses to check it (the test renders at the end of the module or submodule that declares the outcome). Lenses draw their reading material from **articles** and **video transcripts** stored alongside.

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

- Frontmatter: YAML, single colon (`title: ...`) — file-level metadata.
- Body fields: `key:: value` (double colon, at line start) — section/segment data. A value continues over following lines until ++}the{--{"author":"Elias's AI","timestamp":1785489958756}@@ lenses; tests auto-render at the end of their scope
  # Submodule: <name>                   groups the sections below it
  # Lens: <title>                       source:: ![[../Lenses/<Name>]]  (or inline: id:: + segments)
Learning Outcome  (Learning Outcomes/<Name>.md)
  ## Test:                              id:: + #### Question segments with scoring rubrics
  # Suggested Lenses:                   optional, below the test; ## Lens: entries
                                        (source:: [[../Lenses/<Name>]], notes::) —
                                        author-facing suggestions, NOT imported by modules
Lens  (Lenses/<Name>.md)                flat: frontmatter + H4 segments only
  #### Text | Chat | Article | Video | Question | Roleplay
Article (articles/*.md), Video transcript (video_transcripts/*.md)
                                        source material referenced by Article/Video segments
```

A learning outcome is one testable skill ("Explain why...", "Distinguish X from Y"); its test is how the platform checks it. Referencing an outcome from a module imports **only the test** — the lenses that teach it are listed explicitly --}{++{"author":"Elias's AI","timestamp":1785489958756}@@ next `key::` or heading. Duplicate keys ++}in{--{"author":"Elias's AI","timestamp":1785489958756}@@ the module, after the `# Learning Outcome:` ref (outcome declared first; the platform renders the test at the end of the module or submodule). An outcome's `# Suggested Lenses:` section is author-facing metadata: candidate lenses (each `## Lens:` with `source::` and optional `notes::`) for module authors to pick from; zero-suggestion outcomes are valid.

## Editing workflow (MCP)

1. Call `create_session` once with the user's first name — edits are attributed as "{name}'s AI" in the review UI.
2. `read` a document before you `edit` it. Use `glob`/`grep`/`search` to find content — scope patterns to a subfolder or prefix (`Lens Edu/Lenses/IABIED*`); a bare `Lens Edu/**` glob returns 100k+ characters.
3. All markdown writes (`create`, `edit`) land as **CriticMarkup suggestions**, not direct changes. A human must accept them in --}{++{"author":"Elias's AI","timestamp":1785489958756}@@ one section are an error.

Unknown frontmatter fields are tolerated (only near-typos of known fields get flagged), which is why authoring metadata like `authors:`, `readings:`, `reading-from:` appears in real files. Don't rely on unknown fields for anything ++}the {--{"author":"Elias's AI","timestamp":1785489958756}@@content pipeline strips unaccepted suggestions. So:
   - After making suggestions, call `get_url` for each touched document and give the user the links so they can review --}{++{"author":"Elias's AI","timestamp":1785489958756}@@platform must act on.

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

**Article** — embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` ++}and {--{"author":"Elias's AI","timestamp":1785489958756}@@validation--}{++{"author":"Elias's AI","timestamp":1785489958756}@@the text matched by `to::` (this is not a half-open range). Each anchor is independent — only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes) — copy them from the stored article via `read`, never from a summarizing web fetch.

**Video** — same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment++} in {--{"author":"Elias's AI","timestamp":1785489958756}@@a `[Pending suggestions]` section — check it to avoid duplicating or fighting an existing suggestion.
4. Leave notes for human reviewers inline with `{>>{"author":"Elias's AI","timestamp":1783754188139}@@your note<<}` — attribution is automatic.
5. Renaming or moving files: use `move`, which rewrites wikilinks in referencing documents. Never simulate a move with create + delete.

## Publish pipeline and validation

```
Relay "Lens Edu" folder ──auto-sync──▶ github.com/Lens-Academy/lens-edu-staging (branch: staging)
        │                                        │ promotion PR (human)
staging.lensacademy.org  ◀── reads staging       ▼
lensacademy.org          ◀── reads lens-edu-production
```

After edits are accepted, check **https://staging.lensacademy.org/validate** — it continuously validates the synced content and lists errors/warnings per file, filterable by course. Errors are categorized `production` (blocks promotion) vs `wip` (draft-only, from `tags: [wip]`). Fix production-category errors --}{++{"author":"Elias's AI","timestamp":1785489958756}@@a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question** — learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay** — learner talks with a persona defined ++}in {++{"author":"Elias's AI","timestamp":1785489958756}@@`ai-instructions::`; `content::` sets ++}the {--{"author":"Elias's AI","timestamp":1785489958756}@@work done.

**Never push to the `Lens-Academy/lens-edu-staging` or `lens-edu-production` git repos directly** (no `git push`, no `gh api`). The staging repo is continuously force-synced from the relay; external pushes break the sync. All content changes go through the relay.

## Rules that prevent the most common breakage--}{++{"author":"Elias's AI","timestamp":1785489958756}@@scene for the learner, `opening-message::` is the persona's first line.++}

{--{"author":"Elias's AI","timestamp":1785489958756}@@- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall` (existing content uses `\##`; the validator suggests `!##` — both work).
- **Wikilinks are relative** to the referencing --}{++{"author":"Elias's AI","timestamp":1785489958756}@@**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card — used for "Additional resources" footers.

## Rules that apply everywhere

- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall` (existing content uses `\##`; the validator suggests `!##` — both work).
- **Wikilinks are relative** to the referencing ++}file {++{"author":"Elias's AI","timestamp":1785489958756}@@and must contain a `/`. Convention: module `source::` refs use the embed form (`source:: ![[../Lenses/Name]]`), segment and suggested-lens `source::` refs the plain form (`source:: [[../articles/name]]`, `source:: [[../Lenses/Name]]`). The parser accepts both — match the convention, don't "fix" the other form ++}in {++{"author":"Elias's AI","timestamp":1785489958756}@@existing files.
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Never change the id of already-published content.** Learner progress is keyed on these ids; regenerating one (even a format-invalid placeholder ++}the {--{"author":"Elias's AI","timestamp":1785489958756}@@id of already-published content.** Learner progress is keyed on these ids; regenerating one (even a format-invalid placeholder --}{++{"author":"Elias's AI","timestamp":1785489958756}@@validator complains about) silently orphans all completion data for that item at ++}the {--{"author":"Elias's AI","timestamp":1785489958756}@@validator complains about) silently orphans all completion data for that item at the next production promotion. The runtime tolerates format-invalid ids — leave live ones in place, or coordinate a progress remap with the platform team before promoting an id change.
- **Drafts**: add `wip` to `tags` while a file --}{++{"author":"Elias's AI","timestamp":1785489958756}@@next production promotion. The runtime tolerates format-invalid ids — leave live ones in place, or coordinate a progress remap with the platform team before promoting an id change.
- **Drafts**: add `wip` to `tags` while a file ++}is {--{"author":"Elias's AI","timestamp":1785489958756}@@unfinished —--}{++{"author":"Elias's AI","timestamp":1785489958756}@@unfinished —++} its {--{"author":"Elias's AI","timestamp":1785489958756}@@errors then don't block promotion. Remove it when done. A production file referencing--}{++{"author":"Elias's AI","timestamp":1785489958756}@@errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
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
- `source::` wikilink not++} {++{"author":"Elias's AI","timestamp":1785489958756}@@relative (must contain `/`) or target missing.
- Fields on the wrong segment type (`from::` on ++}a {--{"author":"Elias's AI","timestamp":1785489958756}@@wip file is a production error.--}{++{"author":"Elias's AI","timestamp":1785489958756}@@Text segment), field-name typos (Levenshtein ≤2 from a known field), duplicate fields in one section.
- Unescaped heading inside `content::`/`instructions::` (truncates the field; warning suggests escaping).
- Content before the first section header in a body (ignored, flagged).
- `hide:: true` without `optional:: true`; module reference cycles; `tldr` over 80 words; production file referencing a `wip`-tagged file.++}

