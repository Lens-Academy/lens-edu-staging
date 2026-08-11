---
tags:
  - validator-ignore
---
# Writing Surveys (AI Guide)

A survey (`surveys/<Name>.md`) is a post-meeting reflection form learners fill in on the platform — the native replacement for our Google Forms. Each one is attached to a meeting in a course file. After a learner's group meeting ends (and they attended it), the survey unlocks: it appears as "Meeting N Survey" in the course sidebar and pops up once as a modal the next time they open course content. **Submitting the survey is what counts the learner's attendance for that meeting**, and answers land in the Ops dashboard (Surveys tab, with CSV export) — so treat every question as something a human will read.

One survey file can be attached to many meetings (answers are recorded per meeting), so a single well-written doc can serve a whole course. You can also write different surveys for specific meetings — a final-meeting survey with wrap-up questions, for example.

## The file

A survey is a **flat file**: frontmatter + `####` segments. No H1–H3 structure, and segment headers take no title.

Frontmatter: required `id` (a UUID, **in quotes** — unquoted, YAML can mangle it into a number); optional `title` (shown as a subtitle on the survey page; the sidebar label is always the derived "Meeting N Survey"); optional `tags`.

```markdown
---
id: '0ba6d82f-1f72-4877-978b-68aa038ce349'
title: Post-Meeting Survey
---
```

## The 4 segment types

Every answerable segment (everything except Text) needs a `content::` (the question shown to the learner) and a `key::` (see Keys below). `required:: true` makes a question mandatory; everything defaults to optional.

**`#### Text`** — prose shown between questions (intro, section breaks). `content::` is markdown; escape any headings (`\##`). Takes no `key`.

```markdown
#### Text
content:: Thanks for showing up! This takes a few minutes and counts your attendance.
```

**`#### Rating`** — a 1-to-N scale rendered as numbered buttons. `scale::` sets N (2–10, default 5); `low-label::` / `high-label::` caption the endpoints.

```markdown
#### Rating
key:: motivation
content:: How motivated are you right now to take action on AI safety?
scale:: 5
low-label:: Not at all
high-label:: A lot
required:: true
```

**`#### Choice`** — pick one (default) or many (`multi:: true`). `options::` is a plain list, one `- Option text` per line, at least 2. **No checkbox brackets** (`- [ ]` / `- [x]` is quiz syntax for questions with correct answers — surveys have none, and the validator rejects it here).

```markdown
#### Choice
key:: buddy_texted
content:: Did you message your accountability buddy this week?
options::
- Yes
- No
```

```markdown
#### Choice
key:: topics_enjoyed
content:: Which parts of this unit worked for you?
options::
- The readings
- The AI tutor discussions
- The group meeting
multi:: true
```

**`#### Question`** — free text (a textarea). Optional `max-chars::` (length cap with a live counter) and `placeholder::`.

```markdown
#### Question
key:: worked_well
content:: Reflecting on your session, what's one thing that worked well today?
```

## Keys

`key::` is the stable identifier an answer is stored under — `snake_case` (lowercase letters, digits, underscores; starts with a letter; max 64 chars), unique within the survey.

**Keys are forever.** Stored responses are keyed by them, so you can reword a question's `content::` freely (each response snapshots the wording it was answered under), but never change a `key::` once real responses exist — that would split the answer history in ops exports.

Two keys have platform behavior beyond storage:

- **`buddy_texted`** — the answer is parsed as yes/no and feeds scoring (the accountability-buddy credit in the survey score). Use it on the "did you message your buddy" question, ideally a Yes/No Choice.
- **`facilitation_interest`** — an affirmative answer ("Yes, tell me more") registers the learner's interest in facilitating a future group (feeds the navigator pipeline). A negative answer ("Not right now") records nothing.

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

Run the content validator after writing. These are hard errors: missing/unquoted `id`; a missing or malformed `key`; duplicate keys; an answerable segment without `content::`; fewer than 2 options or checkbox syntax in `options::`; `scale::` outside 2–10; a survey with no answerable segments; a title after a segment header (`#### Rating: Mood` — remove the title); a `survey::` link pointing at a missing or broken file; a production course linking a `wip`-tagged survey.

## Complete example

```markdown
---
id: '11111111-2222-4333-8444-555555555555'
title: Post-Meeting Survey
---

#### Text
content:: Thanks for showing up! This is your post-session reflection. It takes a few minutes — and submitting it counts your attendance for this meeting.

#### Rating
key:: motivation
content:: How motivated are you right now to take action on AI safety?
scale:: 5
low-label:: Not at all
high-label:: A lot
required:: true

#### Choice
key:: buddy_texted
content:: Did you message your accountability buddy this week?
options::
- Yes
- No

#### Question
key:: worked_well
content:: What's one thing that worked well today?

#### Question
key:: could_improve
content:: What's one thing the course, website, AI tutor, or meetings could do better?

#### Choice
key:: facilitation_interest
content:: Would you be interested in facilitating a future group?
options::
- Yes, tell me more
- Not right now
```