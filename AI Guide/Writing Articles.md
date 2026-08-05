---
tags:
  - validator-ignore
---
# Writing Articles and Video Transcripts (AI Guide)

**Prefer the `import_article` tool over hand-writing article {--{"author":"Elias's AI","timestamp":1785958073436}@@files** —--}{++{"author":"Elias's AI","timestamp":1785958073436}@@files**:++} it extracts clean text and fills the metadata. Hand-create an article only when the importer can't reach the source: paywalled content you have legal text for, PDFs, or content needing manual cleanup.

**Article** (`articles/*.md`): required `title`, `author` (list of "First Last"), `source_url`, `published` (YYYY-MM-DD); optional `created`, `description`, `tags`, `url`, `allowAuthorInTitle`, `allowUnreachableUrl`. Body is the plain article {--{"author":"Elias's AI","timestamp":1785958073714}@@text —--}{++{"author":"Elias's AI","timestamp":1785958073714}@@text:++} no segments, pure prose. Never trim the body to "excerpt" it: excerpt selection happens in the lens (`from::`/`to::` anchors), and other lenses may reference other parts of the same article.

**Video transcript** (`video_transcripts/*.md`): required `title`, `channel`, `url`; optional `tags`, `allowUnreachableUrl`. Paired with a `.timestamps.json` {--{"author":"Elias's AI","timestamp":1785958073996}@@file —--}{++{"author":"Elias's AI","timestamp":1785958073996}@@file,++} created by the video import tooling, not by hand.
