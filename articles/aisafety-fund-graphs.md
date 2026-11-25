---
title: "Graphs"
author:
  - "AISafety.fund"
source_url: "https://aisafety.fund/graphs"
published: 2026-11-25
created: 2026-11-25
accessed: 2026-11-25
llm-review:
  date: 2026-11-25
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-25
    kind: "live"
description: "AI safety funding by year: philanthropy, governments and AI labs’ own safety work, with the funders behind each."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Use this data in AI tools ^use-this-data-in

AISafety.fund has an MCP connector, so Claude and other AI assistants can look up funders, grants and totals here directly instead of guessing. Reading needs no account.

`https://mcp.aisafety.fund/mcp`

### Add it ^add-it

-   **Claude** (web, desktop or mobile): Settings → Connectors → Add custom connector, then paste the address above.
-   **Claude Code**: `claude mcp add --transport http aisafety-fund https://mcp.aisafety.fund/mcp`
-   **Other MCP clients**: add a remote (Streamable HTTP) server with the address above.

Prefer plain web requests? The same data is on the [AISafety.fund API](https://aisafety.fund/api), for plain web requests (JSON or CSV).

### What it can do ^what-it-can-do

-   Find funders by name, focus or whether they're open to applications, and get a funder's full profile.
-   Search itemised grants by words, funder, recipient, year or amount, with source links.
-   Rank the top recipients, and give yearly totals overall or by funder group.

### Help keep it accurate ^help-keep-it-accurate

Sign in through the connector and ask it to request access to suggest corrections; an editor reviews every suggestion before it changes anything.

People shown as “Individual #” aren't named here; the connector won't help identify them.
