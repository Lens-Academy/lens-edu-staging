{++{"author":"Elias's AI","timestamp":1785321453428}@@---
tags:
  - validator-ignore
---
# Writing Articles and Video Transcripts (AI Guide)

Source material referenced by Article/Video segments in lenses. **Prefer the `import_article` MCP tool over hand-writing article files** — it extracts clean text and fills the metadata; poll `import_status` until the job is done, then `glob` for the created file (don't predict the filename). Hand-create an article only when the importer can't reach the source: paywalled content you have legal text for, PDFs, or content needing manual cleanup.

**Article** (`articles/*.md`): required `title`, `author` (list of "First Last"), `source_url`, `published` (YYYY-MM-DD); optional `created`, `description`, `tags`, `url`, `allowAuthorInTitle`, `allowUnreachableUrl`. Body is the plain article text — no segments, pure prose. Never trim the body to "excerpt" it: excerpt selection happens in the lens (`from::`/`to::` anchors), and other lenses may reference other parts of the same article.

**Video transcript** (`video_transcripts/*.md`): required `title`, `channel`, `url`; optional `tags`, `allowUnreachableUrl`. Paired with a `.timestamps.json` file — created by the video import tooling, not by hand.
++}