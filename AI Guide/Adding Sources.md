---
tags:
  - validator-ignore
---
# {--{"author":"Elias's AI","timestamp":1787740237613}@@Writing Articles and Video Transcripts--}{++{"author":"Elias's AI","timestamp":1787740237613}@@Adding Sources++} (AI Guide)

## Required import workflow

**Never create {--{"author":"Elias's AI","timestamp":1787740247007}@@an article--}{++{"author":"Elias's AI","timestamp":1787740247007}@@a source++} file manually.** Add {--{"author":"Elias's AI","timestamp":1787740247007}@@an--}{++{"author":"Elias's AI","timestamp":1787740247007}@@every++} external {--{"author":"Elias's AI","timestamp":1787740247007}@@article--}{++{"author":"Elias's AI","timestamp":1787740247007}@@source++} through Lens Editor's **Add {--{"author":"Elias's AI","timestamp":1787740247007}@@Article** feature--}{++{"author":"Elias's AI","timestamp":1787740247007}@@Source** page++} or MCP {--{"author":"Elias's AI","timestamp":1787740247007}@@`import_article`, then poll `import_status` until--}{++{"author":"Elias's AI","timestamp":1787740247007}@@`import_article`. One importer handles all of them: webpages, PDFs, and YouTube videos, including sources that need cleanup. A YouTube URL imports the video's transcript instead of an article. Submitting a URL that is already in++} the {--{"author":"Elias's AI","timestamp":1787740247007}@@job--}{++{"author":"Elias's AI","timestamp":1787740247007}@@library++} is {--{"author":"Elias's AI","timestamp":1787740247007}@@done or failed. This applies to webpages and PDFs, including sources--}{++{"author":"Elias's AI","timestamp":1787740247007}@@not an error; the job comes back `skipped` with a link to the document++} that {--{"author":"Elias's AI","timestamp":1787740247007}@@need cleanup. --}{++{"author":"Elias's AI","timestamp":1787740247007}@@already holds it.

++}The importer is required because it retains source evidence, performs source-aware extraction and syntax-safe normalization, runs deterministic validation and mandatory LLM source-fidelity/presentation review, and records review provenance. Bypassing it tends to produce malformed footnotes, broken fragment links, extraction residue, missing evidence, and substantial downstream cleanup work for Lens staff, especially Elias and Luc.

Generic MCP `create` and moves from outside the folder into `Lens Edu/articles` are blocked. Existing article files remain editable. If an exceptional manual article is genuinely necessary, first explain the intended importer workflow and the likely cleanup consequences to the user and obtain explicit permission. The user must create the file in the articles folder themselves; the AI may then edit that existing file.

**Article** (`articles/*.md`): required `title`, `author` (list of "First Last"), `source_url`, `published` (YYYY-MM-DD); optional `created`, `description`, `tags`, `url`, `allowAuthorInTitle`, `allowUnreachableUrl`. Body is the plain article text: no segments, pure prose. Never trim the body to "excerpt" it: excerpt selection happens in the lens (`from::`/`to::` anchors), and other lenses may reference other parts of the same article.

## Citations and explanatory notes

Use ordinary Markdown footnotes with stable, typed, lowercase kebab-case identifiers. Do not use numbered identifiers such as `[^1]`.

- Use `cite-` when the definition primarily identifies evidence or a publication: `[^cite-vaswani-2017]`.
- Use `note-` for footnotes, commentary, qualifications, or asides: `[^note-training-detail]`.
- `^cite` and `^note` are rendered differently by our frontend. Lens renders citations as bracketed markers and explanatory notes as unbracketed superscripts. Both open a hover or click popover. Their identifiers are never shown to readers.
- Reuse the same identifier when citing the same definition again. Do not rename identifiers when inserting or reordering content.
- In a `^cite`  preserve the full bibliographic or explanatory definition. A citation may contain external links or contain only a link, but an ordinary hyperlink does not need to become a citation.
- For imports, prefer a descriptive author/year identifier when reliable. Otherwise include the source and original key, such as `[^cite-wikipedia-cite-note-47]` or `[^note-iabied-ftnt288]`.

```markdown
Transformers use self-attention.[^cite-vaswani-2017]
A qualification matters here.[^note-training-detail]

[^cite-vaswani-2017]: Vaswani et al. (2017), *Attention Is All You Need*. [arXiv](https://arxiv.org/abs/1706.03762)
[^note-training-detail]: This qualification concerns the training setup described above.
```

**Video transcript** (`video_transcripts/*.md`): required `title`, `channel`, `url`; optional `tags`, `allowUnreachableUrl`. Paired with a `.timestamps.json` file, created by the video import tooling, not by hand.
