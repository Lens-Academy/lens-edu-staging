---
tags:
  - validator-ignore
---
# Writing Surveys (AI Guide)

A survey (`surveys/<Name>.md`) is a post-meeting reflection form learners fill in on the platform — the native replacement for our Google Forms. Each one is attached to a meeting in a course file. After a learner's group meeting ends (and they attended it), the survey unlocks: it appears as "Meeting N Survey" in the course sidebar and pops up once as a modal the next time they open course content. **Submitting the survey is what counts the learner's attendance for that meeting**, and answers land in the Ops dashboard (Surveys tab, with CSV export) — so treat every question as something a human will read.

One survey file can be attached to many meetings (answers are recorded per meeting). 
You can also write different surveys for specific meetings a final-meeting survey with wrap-up questions, for example.

## The file

A survey is a **flat file**: frontmatter + `####` segments. No H1–H3 structure, and segment headers take no title.

Frontmatter: required `id` (a UUID, **in quotes** — unquoted, YAML can mangle it into a number); optional `title` (shown as a subtitle on the survey page; the sidebar label is always the derived "Meeting N Survey"); optional `tags`.

```markdown
---
id: '0ba6d82f-1f72-4877-978b-68aa038ce349'
title: Post-Meeting Survey
---
```

## The segment types

Surveys use the same response segments as lenses and tests: `#### Question: Open`, `#### Question: Rating`, `#### Question: Choice`, `#### Question: FillBlank`, `#### Question: Ranking`. Every one needs an `id::` (a UUID; it is the key the answer is stored under) and a `content::` (the question shown to the learner). Segments are **required by default**; add `optional:: true` to let a learner skip one. Surveys never grade, so no `assessment-instructions::` and no `[x]` marks. Full field reference with live examples: [[../Lenses/Response to question segments]].

**`#### Text`** — prose shown between questions (intro, section breaks). `content::` is markdown; escape any headings (`\##`). Takes no `id`.

```markdown
#### Text
content:: Thanks for showing up! This takes a few minutes and counts your attendance.
```

**`#### Question: Rating`** — a 1-to-N scale rendered as numbered buttons. `scale::` sets N (2–10, default 5); `low-label::` / `high-label::` caption the endpoints.

```markdown
#### Question: Rating
id:: 3f0c8a2e-6b4d-4c1e-9a7f-2d5e8b1c4a6f
content:: How motivated are you right now to take action on AI safety?
scale:: 5
low-label:: Not at all
high-label:: A lot
```

**`#### Question: Choice`** — pick one (default) or many (`multi:: true`). `options::` is a plain list, one `- Option text` per line, at least 2. **No checkbox brackets** (`- [x]` marks a correct answer — surveys have none, and the validator rejects it here).

```markdown
#### Question: Choice
id:: 7a1d9e3b-2c5f-4b8a-8e6d-1f4c7a9b3e5d
content:: Which parts of this unit worked for you?
options::
- The readings
- The AI tutor discussions
- The group meeting
multi:: true
optional:: true
```

**`#### Question: Open`** — free text (a textarea). Optional `max-chars::` (length cap with a live counter) and `placeholder::`.

```markdown
#### Question: Open
id:: c4e2b7d1-9f3a-4e6c-b8d5-6a2f1c9e4b7d
content:: Reflecting on your session, what's one thing that worked well today?
```

**`#### Question: FillBlank`** and **`#### Question: Ranking`** work too (ungraded here), useful for a numeric self-report like `How many hours did you spend? {{number}}` or for ranking preferences.

## Ids are keys

The segment's `id::` is the stable identifier an answer is stored under, and what ops exports show. **Ids are forever.** You can reword a question's `content::` freely (each response snapshots the wording it was answered under), but never change an `id::` once real responses exist — that would split the answer history.

## The two special keys (legacy `key::` syntax, still required)

Two survey answers drive platform behavior beyond storage, and the platform finds them by a snake_case `key::`, which only the legacy survey segments carry (`#### Choice` with `key::`, no `id::`, `required::` instead of `optional::`). Until the platform reads these keys off `id::`-based segments, write these two questions in the legacy form and nothing else:

- **`buddy_texted`** — the answer is parsed as yes/no and feeds scoring (the accountability-buddy credit in the survey score). Use it on the "did you message your buddy" question, as a Yes/No Choice.
- **`facilitation_interest`** — an affirmative answer ("Yes, tell me more") registers the learner's interest in facilitating a future group (feeds the navigator pipeline). A negative answer ("Not right now") records nothing.

```markdown
#### Choice
key:: buddy_texted
content:: Did you message your accountability buddy this week?
options::
- Yes
- No
```

`key::` must be `snake_case` (lowercase letters, digits, underscores; starts with a letter; max 64 chars) and unique within the survey. Legacy segments default to optional; add `required:: true` to make one mandatory.

## Attaching a survey to meetings

In the course file, add a `survey::` wikilink under the `# Meeting:` marker (alongside `meeting-doc-template::`):

```markdown
# Meeting: Unit 1
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/AIF Post-Meeting Survey]]

# Meeting: Unit 2
meeting-doc-template:: https://docs.google.com/document/d/...
survey:: [[../surveys/AIF Post-Meeting Survey]]
```

- The Nth `# Meeting:` marker in the course corresponds to each group's meeting N — attach the survey to the marker whose meeting it should follow.
- The same survey file can be linked from several meetings; responses are still recorded per meeting.
- One `survey::` per meeting. The value must be a wikilink to a `surveys/` file — a raw URL here is ignored with a warning (that was the old Google-Form convention).
- A meeting with no `survey::` simply has no survey — nothing appears in the sidebar for it.

## What learners experience (so you can write for it)

- The sidebar row is **locked** until their own group's meeting N has ended *and* their attendance is recorded; then it unlocks.
- On their next visit to course content, the survey opens once as a **dismissible modal**. If several surveys are pending, only the **newest** one pops — older pending surveys never pop again (most surveys ask similar questions), but stay available from the sidebar.
- After submitting they see a thank-you state; re-opening the survey shows it as completed. Facilitators don't get these surveys (student-only for now).

## Validation

Run the content validator after writing. These are hard errors: missing/unquoted frontmatter `id`; a response segment without `id::`; duplicate segment ids (or duplicate legacy keys); an answerable segment without `content::`; fewer than 2 options or `[x]` syntax in `options::`; `scale::` outside 2–10; `assessment-instructions::` in a survey; a survey with no answerable segments; a `survey::` link pointing at a missing or broken file; a production course linking a `wip`-tagged survey.

## Complete example

```markdown
---
id: '11111111-2222-4333-8444-555555555555'
title: Post-Meeting Survey
---

#### Text
content:: Thanks for showing up! This is your post-session reflection. It takes a few minutes — and submitting it counts your attendance for this meeting.

#### Question: Rating
id:: 3f0c8a2e-6b4d-4c1e-9a7f-2d5e8b1c4a6f
content:: How motivated are you right now to take action on AI safety?
scale:: 5
low-label:: Not at all
high-label:: A lot

#### Choice
key:: buddy_texted
content:: Did you message your accountability buddy this week?
options::
- Yes
- No

#### Question: Open
id:: c4e2b7d1-9f3a-4e6c-b8d5-6a2f1c9e4b7d
content:: What's one thing that worked well today?

#### Question: Open
id:: 9b6e4d2a-5c8f-4a3e-b1d7-8e2c5f9a4b6d
content:: What's one thing the course, website, AI tutor, or meetings could do better?
optional:: true

#### Choice
key:: facilitation_interest
content:: Would you be interested in facilitating a future group?
options::
- Yes, tell me more
- Not right now
```