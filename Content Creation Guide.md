# Content Creation Guide

This guide helps you create content for Lens Academy. It's written for educators and content experts — you don't need to be technical to use it.

---

## Quick Start: "I want to create content for a week"

A "week" in our course is the content students work through between meetings. To create a week's content:

1. First, understand [[#How It All Fits Together|how the pieces connect]]
2. Create the [[#Creating a Module|Module(s))]] — the containers that organize everything
3. {--{"author":"Elias's AI","timestamp":1783544177936}@@Add--}{++{"author":"Elias's AI","timestamp":1783544177936}@@Import++} your articles {++{"author":"Elias's AI","timestamp":1783544177936}@@via the **Add Article** page in the web editor — paste the URLs ++}and {--{"author":"Elias's AI","timestamp":1783544177936}@@videos to--}{++{"author":"Elias's AI","timestamp":1783544177936}@@it extracts++} the {--{"author":"Elias's AI","timestamp":1783544177936}@@queue so we can scrape the fulltext or transcripts. ==TO DO: Chris and Luc==--}{++{"author":"Elias's AI","timestamp":1783544177936}@@full text into `articles/` for you. For videos, ask the tech team to run the video import.++}
4. Create your [[#Creating a Learning Outcome|Learning Outcomes]] — what students will be able to ***DO***
5. Create [[#Creating a Lens|Lenses]] — the articles and discussions that teach each outcome

Most contributors start with Learning Outcomes because they define what you're trying to teach.

---

## How It All Fits Together

Lens Academy content is organized in a hierarchy. Here's how the pieces connect:

```
Course
  └── Week (defined by Meetings)
        └── Module (1-3 per week)
              ├── Learning Outcomes
                   └── Lenses (the actual content)
```

### What each piece does

**Course** {--{"author":"Elias's AI","timestamp":1783544188339}@@(`courses/default.md`)--}{++{"author":"Elias's AI","timestamp":1783544188339}@@(`courses/<Course Name>.md`)++}
{--{"author":"Elias's AI","timestamp":1783544188339}@@The--}{++{"author":"Elias's AI","timestamp":1783544188339}@@Each++} course {++{"author":"Elias's AI","timestamp":1783544188339}@@has its own ++}file {--{"author":"Elias's AI","timestamp":1783544188339}@@lists--}{++{"author":"Elias's AI","timestamp":1783544188339}@@listing++} all modules and {--{"author":"Elias's AI","timestamp":1783544188339}@@marks--}{++{"author":"Elias's AI","timestamp":1783544188339}@@marking++} where meetings happen. Modules before a meeting belong to that week.

**Week**
Not a file — it's defined by the meeting markers in the course file. Everything between two meetings is one week. Most weeks have 2 modules, but 1 or 3 is common.

**Module**
A collection of related learning outcomes. Think of it as a chapter or unit. Students work through the module's content, then discuss it at the meeting.

**Learning Outcome**
What the student can DO after completing this content. Written as an action: "Explain why...", "Identify the key...", "Compare different approaches to...". Each learning outcome links to the Lenses that teach it.

**Lens**
The actual learning content. A Lens combines:
- An article (the reading material)
- Introductory text (context for the student)
- An AI chat discussion (to check understanding and explore ideas)

#### Using templates
See [[Obsidian Setup#Using Templates]]

---

## Creating a Learning Outcome

A Learning Outcome describes what the student will be able to do after engaging with the content.

### Step 1: Write the outcome

Think about what you want students to accomplish. Use action verbs:
- "Explain the concept of instrumental convergence"
- "Identify three common objections to AI risk arguments"
- "Compare different approaches to AI alignment"

> [!tip] Writing good outcomes
> Good outcomes are **specific** and **measurable**. Ask yourself: "How would I know if a student achieved this?" If you can't answer that, the outcome might be too vague.

### Step 2: Create the file

Create a new file in `Lens Edu/Learning Outcomes/WIP` with a descriptive name.

### Step 3: Add the required parts

Every Learning Outcome needs:

```markdown
---
id: <generate a UUID — see Syntax Reference below>
discussion: <Discord channel URL for this topic>
---
## Learning outcome:
{>>What can the student do at the end of this module?<<}

## Test:
{>>How will we confirm that the student has achieved the learning outcome above?<<}

## Lens:
source:: ![[../Lenses/Your Lens Name]]

## Lens:
source:: ![[../Lenses/Another Lens Name]]
```

**The header section** (between the `---` marks):
- `id`: A unique identifier (UUID). Generate one at https://www.uuidgenerator.net/version4
- `discussion`: Link to the Discord channel for discussing this topic

**Learning outcome section**: Write what the student can do (the outcome you wrote in Step 1)

**Test section**: How you'll verify the student achieved the outcome. This might be a question they should be able to answer, a task they should be able to do, or a concept they should be able to explain.

**Lens references**: Link to the Lenses that teach this outcome using `source:: ![[path/to/lens]]`

### Template

See [[../Lens/templates/template - learning outcome|template - learning outcome]] for a ready-to-copy version.

---

## Creating a Lens

A Lens is the core learning content — an article plus an AI-guided discussion.

### Step 1: Choose your article

Find or write the article that teaches the concept. Articles live in `Lens Edu/articles/`.

### Step 2: Create the Lens file

Create a new file in `Lens Edu/Lenses/WIP` with a descriptive name.

### Step 3: Add the required parts

Every Lens needs:

```markdown
---
id: <generate a UUID>
---

#### Text
content::
`<introductory text — context for the student before they read>`

#### Article
source:: [[../articles/article-filename]]
to:: "`<exact quote where the excerpt should stop>`"

#### Text
content::
`<prompt for how they should interact with the chatbot>`

#### Chat
instructions::
TLDR of what the user just read:
`<summary text>`

Discussion topics to explore:
- `<Topic 1>`
- `<Topic 2>`
- `<Topic 3>`

Ask what they found surprising or new. Check if they can explain `<key concept>` in their own words.

`<context for the chatbot about what prompt the user is responding to>`
```

**Header section**: Just the `id` (UUID)

**Text sections**:
- Introduction before the reading
- Prompt after the reading (how to engage with the chatbot)

**Article segment**: Links to the source article; `from::`/`to::` anchors define the excerpt. Subsequent `#### Article` segments inherit the source.

**Chat section**: Instructions for the AI tutor
- TLDR summary of the reading
- Discussion topics to explore
- What to check for understanding

### Template

See [[../Lens/templates/template - lens|template - lens]] for a ready-to-copy version with examples in the comments.

---

## Creating a Module

A Module is a container that groups Learning Outcomes together into a coherent unit.

### Step 1: Plan your module

Decide:
- What's the theme or topic?
- Which Learning Outcomes belong here?
- Are there any "uncategorized" Lenses (optional extras not tied to a specific outcome)?

### Step 2: Create the file

Create a new file in `Lens Edu/modules/` with a descriptive name (use the slug).

### Step 3: Add the required parts

Every Module needs:

```markdown
---
id: <generate a UUID>
slug: module-name-here
title: Module Title Here
discussion: <Discord channel URL>
---
# Lens: Welcome
id:: <generate another UUID for this lens>

#### Text
content:: `<overview text introducing this module>`

# Learning Outcome:
source:: ![[../Learning Outcomes/First Outcome]]

# Learning Outcome:
source:: ![[../Learning Outcomes/Second Outcome]]
{>>A place where we can store lenses that are not yet attached to a learning outcome<<}

# Lens:
optional:: true
source:: ![[../Lenses/Optional Extra Lens]]
```

**Header section**:
- `id`: UUID for the module
- `slug`: Short name (lowercase, hyphens, no spaces) — used in URLs
- `title`: Display name for the module
- `discussion`: Discord channel link

**Inline Lens section**: The welcome/intro content
- `id::` for the lens itself
- `#### Text` / `#### Chat` segments with content

**Learning Outcome references**: Link to each outcome using `source:: ![[path]]`

**Referenced Lens sections**: Lenses imported from separate files
- `source::` links to the lens file
- `optional:: true` marks it as not required

### Step 4: Add the module to the course

Edit {++{"author":"Elias's AI","timestamp":1783544190577}@@your course's file in ++}`Lens {--{"author":"Elias's AI","timestamp":1783544190577}@@Edu/courses/default.md`--}{++{"author":"Elias's AI","timestamp":1783544190577}@@Edu/courses/`++} and add your module in the right place:

```markdown
# Module: [[../modules/your-module-slug]]
```

Add it before the appropriate Meeting marker to place it in that week.

### Template

See [[../Lens/templates/template - module|template - module]] for a ready-to-copy version.

---

## Syntax Reference

This section explains the technical details. Skip it if you just want to create content — come back when you need to understand something specific.

### The header section (frontmatter)

The part between `---` marks at the top of each file:

```yaml
---
id: 69615c7b-49e1-431b-8748-3f6de6fef21e
slug: introduction
title: Introduction
---
```

This is called "frontmatter" — it stores metadata about the file.

> [!info] Why we use UUIDs
> UUIDs (those long strings of letters and numbers) are unique identifiers. We use them so that links don't break when you rename files. Generate one at https://www.uuidgenerator.net/version4

### Property syntax

Lines with `::` are properties:

```markdown
source:: ![[../Lenses/Example]]
content:: This is the content text
optional:: true
```

- `source::` — links to another file
- `content::` — text content
- `optional::` — marks something as not required
- `id::` — identifier for a section within a file

### Wikilinks

Links to other files in the vault:

- `[[filename]]` — link to a file
- `![[filename]]` — embed (include) a file
- `[[../folder/filename]]` — link with path

### Comments

Text between `{>>` and `<<}` is a comment (instructions for you, not shown to students):

```markdown
{>>This is a comment explaining what to put here<<}
```

### Placeholder patterns

In templates, you'll see patterns like:

- `<uuid, generate at https://...>` — replace with a generated UUID
- `<discord url>` — replace with a Discord channel link
- `<article title>` — replace with the actual title

---

## Templates

All templates are in `Lens/templates/`:

| Template | When to use |
|----------|-------------|
| [[../Lens/templates/template - module\|template - module]] | Creating a new module |
| [[../Lens/templates/template - learning outcome\|template - learning outcome]] | Creating a new learning outcome |
| [[../Lens/templates/template - lens\|template - lens]] | Creating a new lens (article + discussion) |

Each template includes comments explaining what goes where. Copy the template, then replace the placeholders with your content.

---

## Getting Help

- **Discord**: Ask in the relevant discussion channel
- **Templates**: Check the templates — they have inline comments with examples
- **Validation**: Run the content validator to check your work (see technical team)

---

*Last updated: 2026-02-01*
