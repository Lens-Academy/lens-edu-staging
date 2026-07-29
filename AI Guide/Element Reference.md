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

## File types

Each file type has its own short guide covering frontmatter and body structure:

| File | Location | Guide |
|------|----------|-------|
| Course | `courses/<Name>.md` | `Lens Edu/AI Guide/Writing Course Files.md` |
| Module | `modules/<Name>.md` | `Lens Edu/AI Guide/Writing Modules.md` |
| Learning Outcome | `Learning Outcomes/<Name>.md` | `Lens Edu/AI Guide/Writing Learning Outcomes.md` |
| Lens | `Lenses/<Name>.md` | `Lens Edu/AI Guide/Writing Lenses.md` |
| Article / video transcript | `articles/*.md`, `video_transcripts/*.md` | `Lens Edu/AI Guide/Writing Articles.md` |

## The 6 segment types

Segments are the `####` blocks inside a lens (and inside a Learning Outcome's `## Test:`). Segment headers take no title (`#### Text: Intro` is an error).

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

**Article** — embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` and the text matched by `to::` (this is not a half-open range). Each anchor is independent — only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes) — copy them from the stored article via `read`, never from a summarizing web fetch.

**Video** — same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question** — learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay** — learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card — used for "Additional resources" footers.

## Validator errors you'll actually hit

- Missing/empty required frontmatter fields; slug format violations.
- Unquoted UUIDs that YAML turned into numbers.
- `source::` wikilink not relative (must contain `/`) or target missing.
- Fields on the wrong segment type (`from::` on a Text segment), field-name typos (Levenshtein ≤2 from a known field), duplicate fields in one section.
- Unescaped heading inside `content::`/`instructions::` (truncates the field; warning suggests escaping).
- Content before the first section header in a body (ignored, flagged).
- `hide:: true` without `optional:: true`; module reference cycles; `tldr` over 80 words; production file referencing a `wip`-tagged file.
