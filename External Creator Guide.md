{++{"author":"Elias's AI","timestamp":1783777222455}@@---
id: 716599ad-8353-4eb3-a303-222990e94e28
title: External Creator Guide
tags:
  - wip
---
++}This guide is for content creators who work in Google Docs (or similar tools) and submit content for the tech team to port into the learning platform. Creators do not need to touch Obsidian or learn any technical syntax — the focus is on content itself.

**See it live:** [Introduction Module - First Week](https://lensacademy.org/course/default/module/introduction#ai-humanitys-final-invention)

---

## How the Content Hierarchy Works

Before you start creating, it helps to understand how your content will be organized on the platform. Here's the structure:

```
Course
  └── Week (defined by meeting schedule)
        └── Module (1-3 per week)
              └── Learning Outcome (what students can DO)
                    └── Lens (the actual reading + discussion)
```

### What each piece means

**Module** — A themed collection of content. Think of it as a chapter or unit. Students work through a module, then discuss it at the weekly meeting.

**Learning Outcome** — What the student can DO after completing this content. Written as an action statement: "Explain why...", "Distinguish between...", "Identify the key...". Each Learning Outcome links to one or more Lenses that teach it.

**Lens** — The actual learning content. A Lens combines:
- An article or video (the source material)
- Introductory text (your context for the student)
- Discussion topics for the AI tutor

### Translating your terminology to ours

If you've been organizing content your own way, here's how it maps:

| You might call it... | We call it... |
|---------------------|---------------|
| Part, Section, Unit | Learning Outcome |
| Learning objective, Question to answer | Learning Outcome statement |
| Article entry, Resource | Lens |
| Core/Supplemental/Basic category | Category (maps to required vs optional) |

---

## Division of Labor

Here's what creators provide vs what the tech team handles:

| Component | You Provide | Tech Team Handles |
|-----------|-------------|-------------------|
| **Article/Video URLs** | Submit early (enables parallel scraping) | Scrape fulltext and transcripts |
| **Learning Outcome** | Action statement ("Distinguish between X and Y") | Port to template format |
| **Test** | (optional for Alpha) | — |
| **Intro text** | Context before the reading (1-2 sentences) | Port to Lens format |
| **Discussion topics** | 2-3 questions (preferred) or we can draft | Review and finalize |
| **Chatbot prompt** | How student should engage after reading (preferred) | Review and finalize |
| **TLDR summary** | — | LLM generates after fulltext is ready |
| **Category** | Core / Supplemental / Basic Overview | Map to optional flag |
| **UUIDs** | — | We generate these |
| **Discord links** | — | We add these |
| **File structure** | — | We organize files |

**Bottom line:** You focus on the educational content. We handle all the technical formatting.

---

## Sequencing: What to Do First

The order you submit content matters because it lets us work in parallel. Here's the optimal sequence:

### Step 1: Submit URLs First

**Do this immediately** — before you write anything else.

At the top of your Google Doc, list all the article and video URLs you plan to use:

```
URLS FOR SCRAPING:
- https://archive.is/blU6r
- https://www.youtube.com/watch?v=zATXsGm_xJo
- https://www.lesswrong.com/posts/8gqrbnW758qjHFTrH/security-mindset
```

Why? While you're writing Learning Outcomes and descriptions, we can scrape the fulltext and video transcripts in parallel. This saves days of waiting.

### Step 2: Write Learning Outcomes

**Do this while waiting for fulltext.**

Convert your questions/objectives into action statements:

| Your question | Becomes this Learning Outcome |
|--------------|------------------------------|
| "How does X differ from Y?" | "Distinguish between X and Y" |
| "What is the impact of Z?" | "Explain the impact of Z on..." |
| "Why is A important for B?" | "Identify why A is important for B" |

Good action verbs: Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize

### Step 3: Add Lens Details

**Do this after fulltext is available.**

Once we've scraped the articles, you'll find the fulltext in the shared folder. Now you can write:
- Intro text (context before reading)
- Discussion topics (2-3 questions)
- Chatbot prompt (how student should engage)

---

## Object Readiness Tables

Copy these tables into the Google Doc and fill them in as content is developed. When all rows are complete, that object is ready to port.

### Module Readiness

| Requirement | Assigned to | Completed by | Date | Comments |
|-------------|-------------|--------------|------|----------|
| Title | [Creator] | | | |
| Short description | [Creator] | | | |
| Learning Outcomes list | [Creator] | | | |

### Learning Outcome Readiness

| Requirement | Assigned to | Completed by | Date | Comments |
|-------------|-------------|--------------|------|----------|
| Action statement | [Creator] | | | |
| Test (optional for Alpha) | [Creator] | | | |
| Lenses list | [Creator] | | | |

### Lens Readiness

| Requirement | Assigned to | Completed by | Date | Comments |
|-------------|-------------|--------------|------|----------|
| URL | [Creator] | | | |
| Category | [Creator] | | | |
| Intro text | [Creator] | | | |
| Discussion topics | [Creator] | | | |
| Chatbot prompt | [Creator] | | | |
| Fulltext scraped | [Tech] | | | |
| TLDR generated | [Tech] | | | |

---

## Handoff Model

Creators don't need to finish everything before handing off. The workflow uses a **rolling handoff** model:

- Submit URLs immediately (Step 1)
- Hand off individual Learning Outcomes as they are completed
- Hand off individual Lenses as they are completed
- Perfection not required — iteration is expected

**When is something ready to hand off?**
When its readiness table is filled in. Prose does not need to be perfect — review and polish happens collaboratively.

---

## Common Patterns from Real Content

Looking at real course content (like the "What AI even IS" module), here's how typical creator input maps to our structure:

### Your "Part" headings become Learning Outcomes

You wrote:
> **Part 1. The nature and paradigm of modern AI**
> Learning objective: Distinguish between grown/evolved systems and engineered systems...

This becomes a **Learning Outcome** with the action statement:
> "Distinguish between grown/evolved systems and engineered systems and explain how that impacts our ability to understand and explain the outputs and behaviours of each class of systems."

### Your article entries become Lenses

You wrote:
> **AI Is Grown, Not Built**
> *Category: Core Module Material*
> We don't "build" intelligence brick by brick...
> https://archive.is/blU6r

This becomes a **Lens**:
- Title: "AI Is Grown, Not Built"
- URL: https://archive.is/blU6r
- Category: Core (meaning required, not optional)
- Intro text: "We don't 'build' intelligence brick by brick..."

### Categories map to required vs optional

| Your category | On the platform |
|--------------|-----------------|
| Core Module Material | Required (students must complete) |
| Supplemental Material | Optional (for deeper exploration) |
| Basic Overview | Optional (for those new to the topic) |

### Internal planning notes don't get ported

Sections like "Questions to answer" or "What question do we try to answer" are your planning tools. They help you think through the content but don't appear on the platform. The Learning Outcome statement is what students see.

---

## What NOT to Worry About

Leave these to the tech team:

- **UUIDs** — Those long unique identifiers. We generate them.
- **File names and folder structure** — We organize everything in Obsidian.
- **Markdown syntax** — No need to learn `::` properties or wikilinks.
- **Frontmatter** — That metadata block at the top of files.
- **TLDR summaries** — An LLM generates these from the fulltext.
- **Discord channel links** — We create and link discussion channels.
- **Article/video fulltext** — We scrape this from your URLs.

**Your job:** Educational content and expertise.
**Our job:** Technical formatting and infrastructure.

---

## Quick Reference: The Ideal Google Doc Structure

Here's what a well-organized creator document looks like:

```
URLS FOR SCRAPING:
- [list all URLs here first]

---

MODULE: [Module Title]
Description: [welcome text for students]

---

LEARNING OUTCOME 1: [Action statement starting with verb]

  LENS: [Article title]
  URL: [link]
  Category: Core / Supplemental / Basic
  Intro: [1-2 sentences of context]
  Discussion topics:
  - [Question 1]
  - [Question 2]
  Chatbot prompt: [How student should engage]

  LENS: [Another article title]
  ...

---

LEARNING OUTCOME 2: [Action statement]
  ...
```

This structure makes it easy for us to port your content quickly and accurately.

---

## Questions and Discussion

All questions and discussion happen in Discord. Each week has its own discussion thread:
- "Week 1 materials"
- "Week 2 materials"
- "Week 3 materials"
- etc.

Post content questions, technical questions, and handoff coordination in the relevant week's thread.

---

*Last updated: 2026-02-03*
