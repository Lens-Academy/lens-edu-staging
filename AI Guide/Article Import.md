---
tags:
  - validator-ignore
---
# Article Import (AI Guide)

External articles enter the knowledge base through the **article importer** in the web editor (Add Article page at editor.lensacademy.org, needs an edit-role share link). It extracts clean text deterministically, fills correct metadata, and quality-checks tricky pages with an AI pass.

## What it does

1. You submit article URLs (up to 20 per submission, http/https only) — via the Add Article page, or directly via the API (below). Jobs queue and process in the background.
2. Extraction is deterministic (Readability-style, per-site adapters). An AI verification step runs **only** on flagged extractions (thin content, missing/suspect author, link-heavy pages): it classifies the page (ok / paywalled / blocked / truncated / not_article), repairs metadata, and fixes broken formatting without rewording.
3. On success it writes `Lens Edu/articles/<first-author-surname>-<title-kebab>.md` (org bylines like "Anthropic" are kebabbed as-is; don't predict the filename, `glob` for it after import) with frontmatter: `title`, `author` (list of "First Last"), `source_url`, `published` (YYYY-MM-DD), `created`/`accessed` (import date), `tags: [article-importer]`. Body is the clean article text only.
4. By default it also creates a stub lens with an Article segment pointing at the import ("create lens" toggle).

## Importing via the API (how AI agents import)

The importer is a plain HTTP API, so you can drive it with curl — you only send URLs, no article text passes through you:

```bash
T=<share-token>   # see below — never commit or publish this
curl -s -X POST https://editor.lensacademy.org/api/add-article \
  -H "Authorization: Bearer $T" -H "Content-Type: application/json" \
  -d '{"urls":["https://example.com/post"]}'
# poll until each job is done/failed:
curl -s -H "Authorization: Bearer $T" https://editor.lensacademy.org/api/add-article/status
```

- Auth is an **edit-scoped share-link token** for the Lens Edu folder, used directly as the Bearer — no exchange step. It's the `?t=...` parameter of an editor edit share link; ask the team for one or generate it in the editor. Treat it as a secret: keep it in machine-local notes, never in committed files or shared documents. If it stops working (401), it was revoked — regenerate a Lens Edu edit share link.
- `POST /api/add-article` takes `{"urls": [...]}` (≤20) and optional `"createLens": false` to skip the stub lens; the response lists per-URL status (`queued` / `invalid` / `already_queued`).
- Some sources are slow (LessWrong notably) — keep polling; jobs run in the background on the server.

## Failure modes to expect

- **Refuses to overwrite**: if the article document already exists, the job fails — resolve manually.
- **Rejected pages**: paywalled/blocked pages, link-out stubs (short pages that just link to a PDF/Google Doc/arXiv), and extractions under ~200 chars fail with an error. For arXiv links, import the actual paper page or find an HTML version.
- Same URL twice in one submission or while a job is active → deduplicated/rejected.

## When to hand-write instead

Hand-create an `articles/` file (schema in `Lens Edu/AI Guide/Element Reference.md`) only when the importer can't reach the source: paywalled content you have legal text for, PDFs, or content that needs manual cleanup. Keep the body pure prose — excerpt selection happens in the lens (`from::`/`to::` anchors), never by trimming the article file.

Videos follow a parallel path: `video_transcripts/` files with `.timestamps.json` come from the video import tooling (add-video in the editor), and Video segments reference them with timestamp ranges.
