---
tags:
  - validator-ignore
---
# Element Reference (AI Guide)

Exact syntax accepted by the content processor (`lens-platform/content_processor`, published as `lens-content-processor`). Field lists come from its `content-schema.ts` — the single source of truth.

**Two field syntaxes, don't mix them up:**
- Frontmatter: YAML, single colon (`title: ...`) — file-level metadata.
- Body fields: `key:: value` (double colon, at line start) — section/segment data. A value continues over following lines until the next `key::` or heading. Duplicate keys in one section are an error.

Unknown frontmatter fields are tolerated (only near-typos of known fields get flagged), which is why authoring metadata like `authors:`, `readings:`, `reading-from:` appears in real files. Don't rely on unknown fields for anything the platform must act on.

## Course — `courses/<Name>.md`

```markdown
---
id: <uuid>
slug: ai-risk-fundamentals        # required. lowercase, digits, hyphens; no leading/trailing hyphen
title: "AI Risk Fundamentals"     # required
description: "Shown on the course page."
tags: [IABIED]
discussion: https://discord.com/channels/...
---
# Module: [[../modules/IABIED M1 Intro, Part 1]]
# Meeting: Introduction
# Module: [[../modules/IABIED M2 Nonhuman Minds, Part 2]]
```

Optional frontmatter: `slug-aliases`, `partner-name`, `partner-logo`, `partner-logo-small`, `partner-url`. The body is only `# Module:` wikilink refs and `# Meeting: <name>` markers, in learner order. There is no "Week" structure — meetings are the rhythm markers.

## Module — `modules/<Name>.md`

Frontmatter: required `slug`, `title`; optional `id`, `contentId`, `discussion`, `tags`, `add_to_ai_context` (list of wikilinks whose content is added to the AI tutor's context for everything in the module).

Body = H1 sections:

```markdown
# Submodule: Welcome                  ← groups following sections under a heading
# Lens: Welcome                       ← inline lens: id:: + segments directly here
id:: <uuid>
#### Text
content:: Welcome to the course...

# Submodule: Ch1 - Introduction
# Learning Outcome: Define Intelligence
source:: ![[../Learning Outcomes/Define Intelligence]]

# Lens: Optional Deep Dive            ← referenced lens
source:: ![[../Lenses/Some Lens]]
optional:: true                       ← learner may skip
hide:: true                           ← hidden from the module page (requires optional:: true)
```

A `# Lens:` section has either `source::` (referenced) or `id::` + segments (inline) — not both.

A `# Submodule:` marker may carry `add_to_ai_context:: [[wikilink]]` (one or more `[[...]]`) — that content is added to the AI tutor's context for every lens and test in the submodule. Use this for per-chapter source material (module-level covers the whole module; submodule-level scopes to one chapter).

## Learning Outcome — `Learning Outcomes/<Name>.md`

Frontmatter: required `id`; optional `learning-outcome` (the outcome statement — start with an action verb: Explain, Distinguish, Identify, Compare, Evaluate, Apply...), `discussion`, `tags`. **Do not** put `add_to_ai_context` on a Learning Outcome — it is an error. Put it on the lens, the module, or the `# Submodule:` marker instead.

Body = {--{"author":"Elias's AI","timestamp":1783773025145}@@H2 sections:--}{++{"author":"Elias's AI","timestamp":1783773025145}@@the test, then (optionally) suggested lenses:++}

```markdown
## Test:
id:: <uuid>
#### Question
content:: <the test question>
assessment-instructions:: <scoring rubric — see Quality Patterns>

{++{"author":"Elias's AI","timestamp":1783773025145}@@# Suggested Lenses:
++}## Lens:
source:: {--{"author":"Elias's AI","timestamp":1783773025145}@@![[../Lenses/My--}{++{"author":"Elias's AI","timestamp":1783773025145}@@[[../Lenses/My++} Topic - PQ]]{++{"author":"Elias's AI","timestamp":1783773025145}@@
notes:: <optional author note about this suggestion>++}

## Lens:
source:: {--{"author":"Elias's AI","timestamp":1783773025145}@@![[../Lenses/My--}{++{"author":"Elias's AI","timestamp":1783773025145}@@[[../Lenses/My++} Topic]]
```

{--{"author":"Elias's AI","timestamp":1783773025145}@@`## Submodule: <name>` sections may group--}{++{"author":"Elias's AI","timestamp":1783773025145}@@Suggested lenses are **author-facing candidates only** — the platform never imports them. A module that references the outcome gets just the test; the module lists its teaching lenses explicitly, before the `# Learning Outcome:` ref. Outcomes with zero suggested++} lenses {--{"author":"Elias's AI","timestamp":1783773025145}@@inside an outcome. Lens order--}{++{"author":"Elias's AI","timestamp":1783773025145}@@are valid. A Test may only contain question/roleplay segments (anything else++} is {++{"author":"Elias's AI","timestamp":1783773025145}@@flagged — it would be silently dropped).

Errors to avoid: a `## Lens:` outside ++}the {--{"author":"Elias's AI","timestamp":1783773025145}@@learner's path.--}{++{"author":"Elias's AI","timestamp":1783773025145}@@`# Suggested Lenses:` header, a `## Test:` nested under it (must sit above), and any `Submodule:` section (removed from outcomes — structure lives in the module file).++}

## Lens — `Lenses/<Name>.md`

Flat file: frontmatter + `####` segments. No H1–H3 structure, and segment headers take no title (`#### Text: Intro` is an error — the lens title lives in frontmatter).

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words), `summary_for_tutor` (AI-facing: what this lens teaches), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `add_to_ai_context`.

### The 6 segment types

| Segment | Required fields | Optional fields |
|---------|----------------|-----------------|
| `#### Text` | `content` | `optional` |
| `#### Chat` | `instructions` | `hidePreviousContentFromUser`, `hidePreviousContentFromTutor` |
| `#### Article` | — | `source`, `from`, `to`, `optional` |
| `#### Video` | — | `source`, `from`, `to`, `optional` |
| `#### Question` | `content` | `assessment-instructions`, `max-time`, `max-chars`, `enforce-voice`, `feedback`, `optional` |
| `#### Roleplay` | `id`, `content`, `ai-instructions` | `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional` |

Boolean fields take literal `true`/`false`. Defaults: `optional` false; `feedback` true on questions, false on roleplays; `hidePreviousContent*` false.

**Text** — prose shown to the learner. `content::` is markdown; escape any headings (`\##`).

**Chat** — open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article** — embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"); each is independent — only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes) — copy them from the stored article via `read`, never from a summarizing web fetch.

**Video** — same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question** — learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay** — learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card — used for "Additional resources" footers.

## Articles and video transcripts

Article (`articles/*.md`): required `title`, `author` (list), `source_url`, `published` (YYYY-MM-DD); optional `created`, `description`, `tags`, `url`, `allowAuthorInTitle`, `allowUnreachableUrl`. Body is the plain article text — no segments. Prefer the importer (see `Lens Edu/AI Guide/Article Import.md`) over hand-writing these.

Video transcript (`video_transcripts/*.md`): required `title`, `channel`, `url`; optional `tags`, `allowUnreachableUrl`. Paired with a `.timestamps.json` file — created by the video import tooling, not by hand.

## Validator errors you'll actually hit

- Missing/empty required frontmatter fields; slug format violations.
- Unquoted UUIDs that YAML turned into numbers.
- `source::` wikilink not relative (must contain `/`) or target missing.
- Fields on the wrong segment type (`from::` on a Text segment), field-name typos (Levenshtein ≤2 from a known field), duplicate fields in one section.
- Unescaped heading inside `content::`/`instructions::` (truncates the field; warning suggests escaping).
- Content before the first section header in a body (ignored, flagged).
- `hide:: true` without `optional:: true`; module reference cycles; `tldr` over 80 words; production file referencing a `wip`-tagged file.
