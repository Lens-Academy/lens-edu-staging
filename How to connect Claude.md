---
discussion: https://discord.com/channels/1440725236843806762/1491003715656613928
---

# For humans

## Setting up Claude with Lens Academy

To use Claude with our shared knowledge base, you need to connect it to our MCP server. This gives Claude direct access to read and write documents on the Lens Academy Relay — the same content that syncs with our Obsidian vault.

### How to connect

1. Go to [claude.ai](https://claude.ai) and log in (you need a Pro or Team plan for MCP integrations)
2. Open **Settings** (click your name in the bottom-left corner)
3. Go to **Integrations** (or **Connected Apps**)
4. Click **Add Integration** → **Add custom MCP server**
5. Paste {--{"author":"Elias's AI","timestamp":1784638840592}@@the following URL:--}{++{"author":"Elias's AI","timestamp":1784638840592}@@your MCP URL. There are two options:++}

{--{"author":"Elias's AI","timestamp":1784638840592}@@**This --}{++{"author":"Elias's AI","timestamp":1784638840592}@@**Preferred: your personal share-token URL.** If you have an editor share ++}link {--{"author":"Elias's AI","timestamp":1784638840592}@@gives full acccess --}{++{"author":"Elias's AI","timestamp":1784638840592}@@(`https://editor.lensacademy.org/?t=...`), the part after `?t=` is your token. Your MCP URL is:

```
https://relay.lensacademy.org/mcp/<your-token>
```

This URL is scoped ++}to {++{"author":"Elias's AI","timestamp":1784638840592}@@your folder and role, expires with the share link, and is ++}the {--{"author":"Elias's AI","timestamp":1784638840592}@@entire--}{++{"author":"Elias's AI","timestamp":1784638840592}@@only credential that can use the article importer (`import_article`). Ask a++} Lens {--{"author":"Elias's AI","timestamp":1784638840592}@@Relay system. Please--}{++{"author":"Elias's AI","timestamp":1784638840592}@@admin for an editor share link if you++} don't {++{"author":"Elias's AI","timestamp":1784638840592}@@have one. Don't ++}share {++{"author":"Elias's AI","timestamp":1784638840592}@@it; it acts as you.

**Alternative: the team key.** Full read/write access to everything, but ++}it {--{"author":"Elias's AI","timestamp":1784638840592}@@with others**--}{++{"author":"Elias's AI","timestamp":1784638840592}@@cannot import articles:++}

```
https://relay.lensacademy.org/mcp/deDenjmwtwhHjQQwvacAhjFpBM2UBJddmfdqQloB
```

**This link gives full {--{"author":"Elias's AI","timestamp":1784638840592}@@acccess--}{++{"author":"Elias's AI","timestamp":1784638840592}@@access++} to the entire Lens Relay system. Please don't share it with others**

6. Give it a name like **Lens Relay**
7. Click **Connect**
(Btw, you can similarly connect the MCP with OpenAI or Gemini)

That's it! Claude can now read and create documents in our shared knowledge base.

### What can you do with it?

Once connected, you can ask Claude things like:

- **"Read the file Lens/Marketing.md"** — Claude will pull up the document and you can discuss it together
- **"Create a new learning outcome about X"** — Claude can draft content and save it directly to the knowledge base
- **"Search for all files about IABIED"** — Claude can browse the folder structure and find relevant documents
- **"Edit the intro paragraph of document X"** — Claude can make targeted edits to existing files

In short: Claude becomes a collaborator that can read, write, and organize content in our shared Obsidian vault — no copy-pasting needed.

---

# For LLMs

## Lens Relay MCP — Technical Context and Usage Guide

### What is this?

The Lens Relay MCP server is the bridge between Claude (or any LLM that supports MCP) and the Lens Academy knowledge base. Lens Academy is a free, nonprofit AI Safety education platform focused on the risks of misaligned superintelligence. The knowledge base is an Obsidian vault synced via the Relay plugin, containing course content, learning outcomes, articles, video transcripts, internal planning documents, and operational notes.

### Folder structure

The knowledge base is organized into several key areas:

- **`Lens/`** — Internal planning, operations, and development documents for the Lens Academy team. Includes architecture notes, marketing plans, meeting notes, backlog items, and configuration documents.
- **`Lens Edu/`** — The educational content. This is the core of the platform and contains:
  - **`Lenses/`** — Individual lesson units ("lenses") that present a source article alongside comprehension questions, discussion prompts, and learning outcome references.
  - **`Learning Outcomes/`** — Specific learning objectives that lenses are designed to achieve.
  - **`articles/`** — Source articles and readings used within lenses.
  - **`modules/`** — Groups of lenses organized into sequential learning paths.
  - **`courses/`** — Top-level course definitions that organize modules.
  - **`video_transcripts/`** — Transcripts of videos used as source material.



### Important conventions

- Documents use **wikilinks** (`[[Document Name]]`) for internal linking.
- Lens content follows specific YAML frontmatter conventions. Check existing lenses and templates for the expected format before creating new content.
- The `Lens Edu/` folder is for published or in-progress educational content. The `Lens/` folder is for internal team documents.
- Always call `create_session` before using any other tool. The returned `session_id` must be passed to every subsequent tool call.
- When editing, the `old_string` must exactly match the text in the document (do not include line numbers from `read` output).

### Context about Lens Academy

Lens Academy is built by a small team of part-time collaborators. The platform currently offers a main course ("Navigating Superintelligence") and a book club course based on the book *If Anyone Builds It, Everyone Dies* (IABIED). The content is designed to be accessible to newcomers while maintaining intellectual rigor. The pedagogical approach emphasizes active learning through comprehension questions, discussion, and connecting concepts across multiple sources.