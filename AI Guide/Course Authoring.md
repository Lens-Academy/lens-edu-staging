---
tags:
  - validator-ignore
---
# Course Authoring (AI Guide)

Lens Academy courses are plain markdown documents in this **"Lens Edu"** folder. Humans edit them in the web editor (editor.lensacademy.org), AI agents edit them through the lens-relay MCP tools.

## Read next

| Task | Read |
|------|------|
| Writing or editing any content file | `Lens Edu/AI Guide/Element Reference.md` — exact frontmatter + segment syntax, validation rules |
| Authoring lenses, learning outcomes, or modules | `Lens Edu/AI Guide/Quality Patterns.md` — the proven pedagogical patterns (read together with the element reference) |
| Getting an external article/webpage into the knowledge base | `Lens Edu/AI Guide/Article Import.md` |
| Human-facing intro for content creators | `Lens Edu/Content Creation Guide.md` |

## Content hierarchy

```
Course  (courses/<Name>.md)             one file per course
  # Module: [[../modules/<Name>]]       ordered module references
  # Meeting: <name>                     marks a live-meeting point between modules
Module  (modules/<Name>.md)
  # Submodule: <name>                   groups the sections below it
  # Learning Outcome: <title>           source:: ![[../Learning Outcomes/<Name>]]
  # Lens: <title>                       source:: ![[../Lenses/<Name>]]  (or inline: id:: + segments)
Learning Outcome  (Learning Outcomes/<Name>.md)
  ## Test:                              id:: + {--{"author":"Elias's AI","timestamp":1783772999867}@@a --}#### Question {--{"author":"Elias's AI","timestamp":1783772999867}@@segment--}{++{"author":"Elias's AI","timestamp":1783772999867}@@segments++} with{--{"author":"Elias's AI","timestamp":1783772999867}@@ a--} scoring {--{"author":"Elias's AI","timestamp":1783772999867}@@rubric--}{++{"author":"Elias's AI","timestamp":1783772999867}@@rubrics++}
  {++{"author":"Elias's AI","timestamp":1783772999867}@@# Suggested Lenses:                   optional, below the test; ++}## Lens:{--{"author":"Elias's AI","timestamp":1783772999867}@@                              source:: ![[../Lenses/<Name>]]  (one section per lens, in order)--}{++{"author":"Elias's AI","timestamp":1783772999867}@@ entries
                                        (source:: [[../Lenses/<Name>]], notes::) —
                                        author-facing suggestions, NOT imported by modules++}
Lens  (Lenses/<Name>.md)                flat: frontmatter + H4 segments only
  #### Text | Chat | Article | Video | Question | Roleplay
Article (articles/*.md), Video transcript (video_transcripts/*.md)
                                        source material referenced by Article/Video segments
```

A learning outcome is one testable skill ("Explain why...", "Distinguish X from {--{"author":"Elias's AI","timestamp":1783773004066}@@Y"). Its--}{++{"author":"Elias's AI","timestamp":1783773004066}@@Y"); its test is how the platform checks it. Referencing an outcome from a module imports **only the test** — the++} lenses {++{"author":"Elias's AI","timestamp":1783773004066}@@that teach it ++}are {--{"author":"Elias's AI","timestamp":1783773004066}@@alternative or sequential ways to reach that outcome; its test--}{++{"author":"Elias's AI","timestamp":1783773004066}@@listed explicitly in the module, before the `# Learning Outcome:` ref. An outcome's `# Suggested Lenses:` section++} is {--{"author":"Elias's AI","timestamp":1783773004066}@@how the platform checks it. Lenses referenced from several places are deduplicated--}{++{"author":"Elias's AI","timestamp":1783773004066}@@author-facing metadata: candidate lenses (each `## Lens:` with `source::` and optional `notes::`)++} for {--{"author":"Elias's AI","timestamp":1783773004066}@@the learner.--}{++{"author":"Elias's AI","timestamp":1783773004066}@@module authors to pick from; zero-suggestion outcomes are valid.++}

## Editing workflow (MCP)

1. Call `create_session` once with the user's first name — edits are attributed as "{name}'s AI" in the review UI.
2. `read` a document before you `edit` it. Use `glob`/`grep`/`search` to find content — scope patterns to a subfolder or prefix (`Lens Edu/Lenses/IABIED*`); a bare `Lens Edu/**` glob returns 100k+ characters.
3. All markdown writes (`create`, `edit`) land as **CriticMarkup suggestions**, not direct changes. A human must accept them in the editor review UI before they exist for the platform — the content pipeline strips unaccepted suggestions. So:
   - After making suggestions, call `get_url` for each touched document and give the user the links so they can review and accept. Never construct editor URLs by hand.
   - Don't expect your own unaccepted edits to show up in validation or on the site.
   - `read` shows pending suggestions in a `[Pending suggestions]` section — check it to avoid duplicating or fighting an existing suggestion.
4. Leave notes for human reviewers inline with `{>>{"author":"Elias's AI","timestamp":1783754188139}@@your note<<}` — attribution is automatic.
5. Renaming or moving files: use `move`, which rewrites wikilinks in referencing documents. Never simulate a move with create + delete.

## Publish pipeline and validation

```
Relay "Lens Edu" folder ──auto-sync──▶ github.com/Lens-Academy/lens-edu-staging (branch: staging)
        │                                        │ promotion PR (human)
staging.lensacademy.org  ◀── reads staging       ▼
lensacademy.org          ◀── reads lens-edu-production
```

After edits are accepted, check **https://staging.lensacademy.org/validate** — it continuously validates the synced content and lists errors/warnings per file, filterable by course. Errors are categorized `production` (blocks promotion) vs `wip` (draft-only, from `tags: [wip]`). Fix production-category errors in files you touched before calling the work done.

**Never push to the `Lens-Academy/lens-edu-staging` or `lens-edu-production` git repos directly** (no `git push`, no `gh api`). The staging repo is continuously force-synced from the relay; external pushes break the sync. All content changes go through the relay.

## Rules that prevent the most common breakage

- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall` (existing content uses `\##`; the validator suggests `!##` — both work).
- **Wikilinks are relative** to the referencing file and must contain a `/`. Convention: {--{"author":"Elias's AI","timestamp":1783773007351}@@module/outcome--}{++{"author":"Elias's AI","timestamp":1783773007351}@@module++} `source::` refs use the embed form (`source:: ![[../Lenses/Name]]`), segment {++{"author":"Elias's AI","timestamp":1783773007351}@@and suggested-lens ++}`source::` refs the plain form (`source:: {--{"author":"Elias's AI","timestamp":1783773007351}@@[[../articles/name]]`).--}{++{"author":"Elias's AI","timestamp":1783773007351}@@[[../articles/name]]`, `source:: [[../Lenses/Name]]`).++} The parser accepts both — match the convention, don't "fix" the other form in existing files.
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Drafts**: add `wip` to `tags` while a file is unfinished — its errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
- **Comments**: `%% ... %%` (Obsidian) and `{>>{"author":"Elias's AI","timestamp":1783754188139}@@...<<}` (CriticMarkup) are stripped before parsing — safe for author notes anywhere.
