---
tags:
  - validator-ignore
---
## What a course is

A **course** is a collection of `.md` files, defined in a course file (see [[Writing Course Files]]) that contains an ordered list of links to module files with markers in between that signal when a group going through that course would meet. Under each meeting marker, there is a link to a meeting doc that the group works through during that meeting. (see [[Writing Meeting Docs]]) 

A module (see [[Writing Modules]]) contains links to a set of learning outcomes and an ordered list of lenses.
Each lens is rendered as a separate page. They contain the actual learning content (readings, AI-tutor chats, questions, roleplays). (see [[Writing Lenses]])

Each learning outcomes (see [[Writing (Learning) Outcomes]]) define one testable skill and a set of tests, the platform uses to measure it (the test renders at the end of the module or submodule that declares the outcome). Lenses draw their reading material from **articles** and **video transcripts** stored alongside. (see [[Writing Articles.md]])

Changes sync to https://staging.lensacademy.org within seconds; Only core team members can push to production (https://lensacademy.org).

## The document model

Every content file is markdown with two kinds of structure: YAML frontmatter on top (file-level metadata, `key: value`) and a body of nested headings. A heading's section can carry its own metadata as `key:: value` lines under it; a value runs until the next `key::` or heading; duplicate keys in one section are an error. Unknown frontmatter fields are tolerated, but the platform only acts on documented fields.

## Rules that apply everywhere

- Don't use em dashes.
- **Escape headings inside field values.** A line starting with `#`–`####` inside a multi-line `content::`/`instructions::` value is parsed as a new section boundary and silently truncates the field. Escape it: `\## Phase 1: Recall`
- **Wikilinks are relative** to the referencing file and must contain a `/`. (`source:: [[../articles/name]]`, `source:: [[../Lenses/Name]]`).
- **IDs are UUIDs** (lowercase v4, generate with `uuidgen | tr A-Z a-z`). Every lens, learning outcome, module, test, and inline lens needs its own. Quote them in frontmatter (`id: 'a1b2...'`) so YAML never mangles them; never reuse or invent non-UUID ids.
- **Never change the id of already-published content.** Learner progress is keyed on these ids
- **Drafts**: add `wip` to `tags` while a file is unfinished; its errors then don't block promotion. Remove it when done. A production file referencing a wip file is a production error.
- **Comments**: `%% ... %%` (Obsidian) and `{>>{"author":"Elias's AI","timestamp":1785489958756}@@...<<}` (CriticMarkup) are stripped before parsing, safe for author notes anywhere.
- **`add_to_ai_context`** injects source material (e.g. chapter text from a private folder) into the AI tutor's context; use it whenever the tutor must discuss a text the student read elsewhere. Allowed on a lens (scopes to that lens), module frontmatter (whole module), or a `# Submodule:` marker (that submodule, the natural home for per-chapter book content). On a learning outcome it is a validation error.

## Making a course that is CORRECT, not just one that looks finished

Writing an impressive-looking course is much easier than writing a correct one, and an AI-built draft is finished-looking by default. Finish-texture carries no information about completeness, so it cannot be used as evidence in either direction: not about your own work, not about someone else's.

That means care is not the mechanism. You can be maximally careful and fluently wrong all day. What works is a workflow whose steps make it hard to end up wrong, so correctness falls out of the operations rather than out of vigilance. The steps below are ordered by how much they caught per minute spent, measured on a real three-unit build.

**Run the validator early, not as a final gate.** `validate_content` with `accept_drafts: true` finds schema errors no amount of reading finds: `domain:` must be a Domains wikilink or `none`, `stage:` must be lowercase, a `tldr` whose value starts with a quote character breaks YAML, ids must not be double-quoted. A course with 22 of these reads as completely finished.

**Diff the course against what was advertised.** Read the public landing copy and tabulate each promise against the unit that delivers it. Internal review only ever compares the artifact to itself, so this is the one check that catches a course quietly not being the course that was sold.

**Label your claims by what would establish them.** Go through the assertions (not every sentence; most sentences are instructions and take no citation) and tag each one: empirical needs a source, mathematical needs a derivation you can do right there, structural needs an enumeration somebody actually did, pedagogical needs data about a population. Expect structural to be the fattest ungrounded category: it is the connective tissue that makes prose flow, and it is invisible to review because it reads as organisation rather than as assertion. "There are two ways to get this wrong, and they are mirror images" asserts an enumeration and a symmetry that nobody checked.

**Numbers need a separate pass.** Claim-labelling reads prose and skips numerals. On one build, 158 percentage figures appeared in the course and 86 of them were never examined by the labelling pass, including two that a student is graded against. Grep every figure and check it against its source. Expect to find a number taken from a summary of a paper nobody opened.

**Check the quantity, not just the digits.** Both of Grace's discontinuity figures were correct in our course and one was attached to the wrong quantity: the paper says "the chance of a given level of progress arising in a large robust discontinuity was around 14%", a probability about how an increment arrives, and we wrote it as a share of total progress. The student-facing question then asked for the share and graded the answer against the probability.

**Hedging is not grounding.** Softening a claim you did not check lowers your confidence without finding anything out. "There are two ways" becoming "there are probably two ways" is worth nothing; finding the person who enumerated them is worth everything.

**Reference the population the claim is actually about.** A claim like "students commonly misread this" is about a population, and it is almost never about your students, whom you have not taught yet. Where the observation is real it usually belongs to a documented group: if a post exists because a misreading is widespread among its readers, cite that post. Where it is a design intention, write it as one. A tutor brief needs "if the student does X, that is the case this phase is built for", not "almost every student does X", and the imperative form is what the tutor can act on anyway.

**Be strictest inside grader briefs.** Every worst error on the reference build lived in `assessment-instructions` rather than in student-facing prose, and the reason is structural: the register that makes a rubric feel usable is the register of established fact. Wrong prose misleads a reader who can push back. A wrong rubric penalises the student who saw further than the author. Mark which claims in a brief a strong student is permitted to overturn.

**Verify the mathematics by running it.** Four lines of Python beats a plausible-sounding critical value. On the reference build a rubric asserted a threshold at "gain per cycle stays at or above one", with runaway above and a ceiling below. Both halves were false, any constant positive gain gives a finite total time, and the rubric instructed graders to mark down the student who noticed.

**Then hand it to readers who did not write it.** Fresh eyes are a position, not a virtue, and an author structurally cannot occupy that position for their own work. Give each reviewer a named seat and a different failure to hunt: can the tutor actually grade this, would a fluent student who read nothing reach the pass bar, is the mathematics load-bearing or decorative, where would a sharp impatient student quit. A reviewer who reports only that the work is good has not tried.

**Ask the authors.** If a course was built by several agents, they are resumable and their reasoning is still in context. Asking an author where a claim came from beats reconstructing it from a corpus, and they will volunteer errors a reviewer would not find. Give them three verdicts: cite it, own it as ours, or call it wrong. Tell them not to reach for a citation they do not actually recall, because a confabulated citation is worse than none: it manufactures the feeling of grounding.

**The join is what parallel work leaves unfinished.** When N agents build one artifact, each file can be finished while the object no single file contains is not. Promises made in one file go undischarged in the next: a pre-test whose baseline is never read back, a prediction extracted and never cashed. Budget a pass whose only job is checking that piece N's promise is kept in piece N+1.