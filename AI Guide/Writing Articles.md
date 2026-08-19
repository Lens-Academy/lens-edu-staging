---
tags:
  - validator-ignore
---
# Writing Articles and Video Transcripts (AI Guide)

**Prefer the `import_article` tool over hand-writing article files**: it extracts clean text and fills the metadata. Hand-create an article only when the importer can't reach the source: paywalled content you have legal text for, PDFs, or content needing manual cleanup.

**Article** (`articles/*.md`): required `title`, `author` (list of "First Last"), `source_url`, `published` (YYYY-MM-DD); optional `created`, `description`, `tags`, `url`, `allowAuthorInTitle`, `allowUnreachableUrl`. Body is the plain article text: no segments, pure prose. Never trim the body to "excerpt" it: excerpt selection happens in the lens (`from::`/`to::` anchors), and other lenses may reference other parts of the same article.{++{"author":"Luc's AI","timestamp":1787158677426}@@

## Citations and explanatory notes

Use ordinary Markdown footnotes with stable, typed, lowercase kebab-case identifiers. Do not use numbered identifiers such as `[^1]`.

- Use `cite-` when the definition primarily identifies evidence or a publication: `[^cite-vaswani-2017]`.
- Use `note-` for commentary, qualifications, or asides: `[^note-training-detail]`.
- Reuse the same identifier when citing the same definition again. Do not rename identifiers when inserting or reordering content.
- Preserve the full bibliographic or explanatory definition. A citation may contain external links, but an ordinary hyperlink does not need to become a citation.
- For imports, prefer a descriptive author/year identifier when reliable. Otherwise include the source and original key, such as `[^cite-wikipedia-cite-note-47]` or `[^note-iabied-ftnt288]`.

```markdown
Transformers use self-attention.[^cite-vaswani-2017]
A qualification matters here.[^note-training-detail]

[^cite-vaswani-2017]: Vaswani et al. (2017), *Attention Is All You Need*. [arXiv](https://arxiv.org/abs/1706.03762)
[^note-training-detail]: This qualification concerns the training setup described above.
```

Lens renders citations as bracketed markers and explanatory notes as unbracketed superscripts. Both open a hover or click popover. Their identifiers are never shown to readers.++}

**Video transcript** (`video_transcripts/*.md`): required `title`, `channel`, `url`; optional `tags`, `allowUnreachableUrl`. Paired with a `.timestamps.json` file, created by the video import tooling, not by hand.
