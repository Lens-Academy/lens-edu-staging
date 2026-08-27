---
tags:
  - validator-ignore
---
## What a course is

A **course** is a collection of `.md` files that link to each other.
It is defined by a course file (see [[Lens Edu/AI Guide/Writing Course Files]]). A course file defines a set of units. Each unit consists of one or more modules, which students go through in self-study, and a group meeting at the end. During a meeting, students go through a Google Doc, which defines what they discuss (see [[../AI Guide/Writing Meeting Docs]]). After every unit, students are asked to fill out a survey (see [[../AI Guide/Writing Surveys]]).

A module (see [[../AI Guide/Writing Modules]]) contains links to a set of learning outcomes that define what we want to teach in this module, and an ordered list of lenses, which constitute the actual content.
Each learning outcome (see [[../AI Guide/Writing (Learning) Outcomes]]) defines one testable skill and a set of tests the platform uses to measure it (the test renders at the end of the module or submodule that declares the outcome).
Each lens is rendered as a separate page. They contain the actual learning content (readings, AI-tutor chats, questions, roleplays). (see [[../AI Guide/Writing Lenses]])
Lenses can embed external **articles** and **video transcripts**, which live in the `articles/` and `video_transcripts/` folders alongside. (see [[../AI Guide/Adding Sources]])

Read through a file type's guide before creating/editing any file of that type.

Changes sync to https://staging.lensacademy.org within seconds; Only core team members can push to production (https://lensacademy.org).

[[../courses/Demo Course]] contains examples of all of our features. Look through it if you are unsure and direct new course creators to it to get familiar with our platform.

## The document model

Every content file is markdown with two kinds of structure: YAML frontmatter on top (file-level metadata, `key: value`) and a body of nested headings. A heading's section can carry its own metadata as `key:: value` lines under it; a value runs until the next `key::` or heading. Headings inside multi-line values must be escaped (e.g. `\## Heading`). Unknown frontmatter fields are tolerated, but the platform only acts on documented fields.

## Rules that apply everywhere

- Never use em dashes anywhere!
- To get responses from course participants, use `#### Question: Open`, `#### Question: Rating`, `#### Question: Choice`, `#### Question: FillBlank`, or `#### Question: Ranking`. Old syntax used bare `#### Question` (legacy, no id, being phased out) and `#### Rating` / `#### Choice`, but is being deprecated. The live reference is [[../Lenses/Response to question segments]].
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, response segment, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Never change the id of already-published content.** Learner progress is keyed on these ids
- **Drafts**: add `wip` to `tags` while a file is unfinished; its errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
- **Comments**: `%% ... %%` (Obsidian) and `{>>{"author":"Elias's AI","timestamp":1785489958756}@@...<<}` (CriticMarkup) are stripped before parsing, safe for author notes anywhere.
- **`add_to_ai_context`** injects source material (e.g. chapter text from a private folder) into the AI tutor's context; use it whenever the tutor must discuss a text the student read elsewhere. Allowed on a lens (scopes to that lens), module frontmatter (whole module), or a `# Submodule:` marker.
- **Run the validator early, not as a final gate.** `validate_content` with `accept_drafts: true` finds schema errors no amount of reading finds.

## Checking that the course is correct

It is easy to write a course that sounds right. Being careful while writing does not prevent errors. These checks do. Run them on every course before promoting it.

**Every claim outside articles is sourced, marked as our own view, or deleted.**
Source means: a link the student can see (inline or footnote), or for maths, a calculation you ran. Own view means the sentence says so ("We think…"). Hedging ("probably") is neither. (rather cut than hedge)
Claims hide in sentences that read like structure ("there are two ways to get this wrong", "these are mirror images") or like teaching lore ("students often misread this"). Treat those as claims too; the second kind is usually better rewritten as an instruction to the tutor: "if the student does X, do Y".

**Check every number in a separate pass.**
Reading prose for claims skips numerals. Grep every figure in the course and compare it against the original paper, not a summary. Check two things: that the digits are right, and that the number describes the quantity the text says it does. Example: a paper reported a 14% probability that progress arrives as a discontinuity; the course wrote it as a 14% share of total progress, and a test question graded students against the wrong meaning.

**Have the course reviewed by agents who did not write it.**
An author cannot see their own errors. Use several reviewers, and give each one a specific error to look for:
- Try to grade a sample answer using only the rubric. Where is the rubric ambiguous?
- Answer the test without having read the material. Can a fluent writer pass?
- Read the mathematics. Does the argument depend on it, or is it decoration?
- Read as an impatient expert. Where would you stop reading?

A review that only says "looks good" was not done.

**If several agents built the course, do two more checks.**
- Ask each author agent, while it is still running, where each of its claims came from. It must answer one of: here is the source; this is our own opinion; this is wrong. Tell it not to produce a citation it does not actually remember.
- Check that promises made in one file are kept in the next. A pre-test whose baseline is never used later, or a prediction the student writes down that is never revisited, are the typical failures.