---
tags:
  - validator-ignore
---
# Writing Lenses (AI Guide)

A lens (`Lenses/<Name>.md`) is a **flat file** of frontmatter + `####` segments: no H1–H3 structure, and segment headers take no title (the lens title lives in frontmatter).

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words, speaks to the learner; an analogy beats a summary: "Like a parent who knows how babies are made but not what the baby will become"), `summary_for_tutor` (AI-facing: what the lens teaches and how its parts sequence), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `duration_minutes` (1–600, the lens's total expected completion time; replaces the platform's computed time estimate, see "Estimate every lens's time" below), `reading_minutes` / `tutor_minutes` (0–600 each, the same estimate split into content time and AI-tutor time; use the split instead of `duration_minutes`, never together with it), `add_to_ai_context` (injects source material into the tutor's context; use when the tutor must discuss a text the student read elsewhere), `glossary_terms` (links to glossary entries whose first use on the page gets a definition on hover; see [[../AI Guide/Writing Glossary Entries]]).

The patterns below come from the **AI Risk Fundamentals** course (`IABIED` prefix, built around *If Anyone Builds It, Everyone Dies*), the current quality bar. Reuse the structure; adapt the content. Read a real example before writing: `Lens Edu/Lenses/IABIED - AI Is Grown, Not Crafted.md` is the canonical reading lens.

## Write from the student's current perspective

- Include instructions that help students act, choose, or understand the purpose of an activity.
- Use meaningful activity names, not internal IDs or authoring terminology.
- Explain choices by what students will explore, not how the platform organizes them.
- Give directions when students need them. Don't repeat visible UI labels or add reminders against hypothetical mistakes.
- Before finishing, ask of every instruction: "What does this help the student do now?" Cut it if there is no useful answer.
- Write the way a good teacher talks, not like a spec. Don't copy a brief's internal labels or bullet points into learner text. Start with the thing itself. No meta headings that the next sentence just restates (a heading "Two strands" followed by "This course has two strands."), and no slogan pairs ("It explores, it does not preach").
- Define a key term before you lean on it. Never drop a term in cold.
- An overview opens with who the course is for and what they get from it, as prose.
- The items of one list are one kind of thing (all questions, or all topics), not a mix.
- Lines starting with "(1)", "(a)", "a." or "(i)" are not list syntax, so consecutive ones render as one run-on paragraph. Put a blank line between such items, or use a real `1.` list.
- No nested list hidden in a bullet. "- **Work with companies.** Fact one. Fact two. Fact three." should become either prose, or a label bullet with each fact in its own indented sub-bullet. A single fact with its label stays one bullet.
- Don't explain what the page already shows: that footnotes can be hovered or tapped, that boxes can be opened, or that a page is "a summary, not a source text". An intro says what the page is about and any real caveat ("numbers as of October 2026 are rough").
- When a subagent drafted the text, do a language pass on it yourself before anyone else sees it.

## Estimate every lens's time

When you create or change a lens, estimate the learner's real start-to-finish time and set it at the top: prefer `reading_minutes` + `tutor_minutes` (content time + AI-conversation time, displayed split; either alone works, `tutor_minutes: 0` means no tutor time), or one `duration_minutes` total, never both. Estimate from what the learner actually does, not a word-count formula (dense readings are slower, required back-and-forth costs more than a quick answer, count off-page work like "read chapter 2"), round to a friendly number, and re-estimate in the same edit whenever you change a lens. Rendered example: the Demo Course's "Lens duration demo" module.

What counts where, and rough sizes:
- **Question time is tutor time,** never reading time. Count it per question, including the tutor's feedback and any back-and-forth: a quick recall question about 3 minutes, an explain-or-apply question 5 to 6, a multi-part, design or prediction question up to about 8. Judge longer written answers one by one by reading the question, not by its word limit (a `max-words` cap is a ceiling, not what people write). Most written answers take 5 to 15 minutes.
- **Reading time** covers text, video and widgets.
- **Optional work** counts by expected uptake. Learners don't see an `optional:: true` flag inside a lens, so a question whose text doesn't say it's optional is usually done and counts fully. "Answer any k of these n" counts k/n of the time of all n. "Pick one of these readings" counts the average option, not the shortest.
- **Appendices** go into a collapsible that is closed by default and count 0 minutes. If the learner is meant to read one, keep it in a collapsible that is open by default and count it fully.
- When you change lens times, also update any hand-written totals (module `%%` notes, the course description).

## The reading lens: Recall → Processing → Learning Question

Every IABIED reading lens follows the same five-beat structure. It works because it forces retrieval before reflection, reflection before analysis, and never lets the tutor lecture.

```markdown
#### Text                                      ← 1. Reading assignment
content::
\## Reading Assignment
**Read *Chapter 2: Grown, Not Crafted*.** Start at the beginning and stop when you reach
> <exact quote from the text marking the stop point>
Return here after reading.

#### Question: Open                            ← 2. Phase 1: Recall
id:: <uuid>
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember from the reading, without
looking back at the text. Anything and everything. No need to organize it. Using the
speech to text feature is highly recommended here.
feedback-instructions:: <recall-mirror brief, see below>

#### Question: Open                            ← 3. Phase 2: Processing ("what landed")
id:: <uuid>
content::
\## Phase 2: Processing
Take 2 minutes to jot down how the reading landed. What resonated? What confused you?
What did you doubt or push back on? No need to organize. Just capture your reaction.
feedback-instructions:: <processing brief, see below>

#### Question: Open                            ← 4. Phase 3: Learning Question
id:: <uuid>
content::
\## Phase 3: Learning Question
<a scenario that embodies a plausible-but-flawed claim about the material>
assessment-instructions:: <socratic brief, see below>

#### Text                                      ← 5. Optional resources footer
content::
\## Additional resources for this topic
::card[[../Lenses/IABIED - QA - Gradient Descent Matters]]
> One-sentence hook saying what a curious learner gets from it.
```

All link and card forms with live examples — hooks, cards in closed callouts, module cards, hidden imports, image embeds: [[../Lenses/Links and cards demo]].

**Optional Phase 3: Connection**, used in chapters that build directly on an earlier one (real example: `IABIED - You Don't Get What You Train For.md`; also shipped in the Aztec Warrior, Five Engineering Curses, Alchemy Not Science, Strong Superalignment Objection, One-Chance Problem, and Coda lenses). Inserted between Processing and Learning Question — when present it becomes Phase 3 and Learning Question renumbers to Phase 4. `## Phase 3: Connection`, asks the student to name which earlier chapter's idea the current chapter leans on without naming the idea, chapter, or candidate count for them. Even though the brief may name the specific answer it's aimed at (for the author's own clarity), this is **not** machine-graded — `feedback-instructions::`, same as Recall and Processing. It is Socratic (testing whether the student can locate the idea themselves), not a fact check.

### Which field: `feedback-instructions::` or `assessment-instructions::`

How to write either field, when to grade at all, and the checks to run: [[../AI Guide/Writing Rubrics]].

Use `feedback-instructions::` whenever the phase has no single correctness the platform should score — a recall mirror, a reflection, naming a connection. The student gets a reply; no percentage. Use `assessment-instructions::` only when you mean the platform to compute and show a real numeric grade (a 0–100% chip, red under 40%) — reserve it for phases with an actual right/wrong the student should be tested on, like Learning Question's wedge-claim verdict, or Choice/FillBlank/Ranking segments. **The field name is not a formality: it is a load-bearing switch.** `assessment-instructions::` on a phase whose own brief says "normalize gaps, incomplete recall is expected and not a failure" produces exactly that contradiction as a visible grade — the platform's scorer (`core/assessment.py`) is deliberately a rigorous, isolated evaluator with no view of that framing beyond the same block being handed to it as "Scoring Rubric:"; a lenient-sounding brief does not soften it, changing the field does. This has shipped wrong twice: six lenses caught 2026-09-11, seven more (the Connection phase above) caught and fixed 2026-09-22 (PR #100, Elias/James/Claude, from student reports in #help-and-feedback). If you are writing or editing a brief, check which behavior you actually want before choosing the field, every time — do not copy the field from a neighboring phase without checking whether that phase wants the same thing.

### Where questions go

Put each question right after the excerpt it is about, not all together at the end of the lens. The learner reads, answers, reads on: a question about Cale's comment comes after Cale's comment, before the next reading. Only a question that needs several readings goes after the last of them.

### One question per box

- **Separate questions get separate boxes.** Two independent questions in one `#### Question` box make the learner write one mixed answer and the grader judge it as one. Split them, each with its own rubric and feedback brief. When you split an existing question, the first part keeps the old `id::` so answers already given stay attached. Later parts get new ids.
- **Asks that belong together stay in one box as a numbered list.** When the asks are steps of one task, keep the scenario or intro as a paragraph, then put each ask on its own `1.` line, with a blank line before the list. Never write several questions as one run-on paragraph. A short "…? Why?" pair is one ask: write it as one sentence ("Which kind is it, and why?").
- **A question that asks for facts from the reading is graded.** If the answer can be judged right or wrong (what the reading said, how a mechanism works, which kind something is), give it `assessment-instructions::` (see [[../AI Guide/Writing Rubrics]]). Only questions about the learner's own view, feelings, guesses before a reading or plans stay ungraded.

### One question in several lenses: question files

When two lenses ask the same question, do not copy the `#### Question` block into both. Put it in its own file under `Lens Edu/Questions/`, named for what it asks (e.g. `Questions/What attack defeats upfront auditing.md`). The file holds exactly one question segment (`#### Question: Open`, `Choice`, …) with its `id::` and all its fields. Frontmatter is optional; a question file cannot embed another file.

In each lens, a line with only the embed stands for the whole question, with no `#### Question` header above it:

```
![[../Questions/What attack defeats upfront auditing]]
force-feedback:: first
```

- Lines right under the embed may set `force-feedback::`, `optional::` and `feedback-instructions::` for this lens only. Every other field comes from the file; setting one here is an error.
- Both lenses use the file's `id::`, so a learner's answer is the same answer in both. Editing the file changes the question everywhere it is embedded.
- Only lenses (`Lenses/`) can embed question files.
- In the Lens Editor the embed shows the question as a card in place of the line. Arrow onto the line to see its source, and click the card to edit the question file there.

### When feedback starts

- **Open questions with a right answer** (test and practice questions) get `force-feedback:: first`, so the learner gets the tutor's reply on their first answer without clicking.
- **Short multiple-choice or sorting recall** keeps feedback on request (no `force-feedback`). The score already says enough.
- **Reflection and personal questions** (starting views, "what do you think", ungraded open questions) also keep feedback on request: keep `feedback-instructions::`, leave out `force-feedback`.
- **No word limits.** Don't add `max-words::`.

### What each brief must do

All three share a house style: state who the student is and what they just did; give the key concepts of the reading as a checklist; set response length ("80–150 words. Short paragraphs only. No lists."); and ban generic praise ("Do not over-validate. Avoid generic praise (great job, excellent recall, well done)"). Two more clauses belong in every brief, added 2026-09-08 after students in the AI Futures cohort reported learning to ignore the tutor. (1) When a student says they do not understand, the tutor neither dismisses it nor repeats the question. It gives one concrete foothold from the material: an example the reading contains, one part of the question isolated, or the evidence that would settle it. If the student's next message still does not attempt the question, the tutor rephrases the whole question in different terms rather than offering a third foothold. (2) The tutor grades only against criteria the page or a prior required page supplied. The job is closer to a concierge for spaced recall than to a debater (Lauren: "concierge anki"): perform it plainly, and use any flourish or step out of role that gets it done. Target stance, in Elias's words: "rigorous, specific, supportive, diagnostic". Wording tested 2026-09-08 by seating a Sonnet as the tutor: the earlier phrasing ("does not argue with 'I don't understand'") was read as "do not dismiss" but said nothing about what to do instead, and "second failure" was undefined; it also pulled against "if vague, ask for precision", so "foothold first" is the tie-break.

**Phase 1: Recall (one turn).** The tutor is "diagnostic, not instructional: a brief, honest mirror": acknowledge what's correct without inflation, name what's missing without lecturing, correct errors in one sentence, normalize gaps, close with a calibrating sentence. Explicitly: no re-teaching, no follow-up questions, no inviting dialogue: "This is a one-turn response. Tell them to move on."

**Phase 2: Processing (max 2 turns).** "A processing phase, not a teaching phase": help the student articulate their reaction, don't resolve it. Branch on what they expressed: confusion → ask what specifically is unclear; skepticism → treat as a legitimate stance, ask what would convince them; resonance → ask what it connected to. If their confusion is exactly the learning outcome, defer it: "the next step will dig into exactly that." Enforce the cap: "Keep an internal turn counter. After 2 tutor replies, close the phase."

**Phase 3: Learning Question (3 turns, then offer to continue).** The question is "a deliberate wedge: not the test question: a plausible-sounding but flawed claim; the student locates the flaw" so the outcome is drawn out from a fresh angle rather than recited. State the learning outcome and key concepts verbatim in the brief. Per reply: answer direct questions directly; otherwise steelman the student's answer in 2–4 sentences, name 1–3 gaps, ask 2 causal follow-ups (why/how/what-if, each directly answerable, no opinion questions). Include rescue moves ("if stuck after 2 attempts, give a brief direct answer and move on") and a closing calibration with an explicit test-readiness verdict.

### Check your questions with sub-agents

Run this check whenever you add or change a question in a lens, before you call the lens done. The most important rule: **the rubric must not ask for anything the question does not ask for.** A learner who reads only the question and answers it simply and correctly must get full marks. The author cannot check this alone: having written the rubric, they read its demands into the question.

1. **Answerer.** Make a copy of the lens without its `assessment-instructions::` and `feedback-instructions::` lines (for example `lens call read` piped through `grep -v`), so the agent cannot see what will be graded. Spawn a sub-agent with that copy and this instruction, verbatim: "You are a learner who has read this lens carefully. For each question, write the answer a good learner would give: simple, correct, in plain words, answering exactly what the question asks and nothing more. Where the question asks for your own view, take a view and argue it well. Return each answer with the question's id."
2. **Grader.** Spawn a fresh sub-agent with the full lens, the answers, and this instruction, verbatim: "First read [[Lens Edu/AI Guide/Writing Rubrics.md]]. For each question:
   1. **Full marks.** Grade the answer as a strict grader would, with the rubric exactly as written. If it scores below about 85, it fails: name the rubric element that cost the points and quote the words of the question that should have asked for it, or say that none do.
   2. **Nothing unasked.** For every scored element, cap and partial-credit rule, quote the words of the question that ask for it. Any element you cannot point to fails, even if this answer happened to cover it.
   3. **Opinions.** Where the question asks for the learner's own view (what an author gets right, whether an argument is convincing, what they would do), the rubric grades only how well the view is argued: any view with strong arguments can get full marks. A rubric that prefers one view fails.
   4. **Only what the learner has seen.** No element depends on material later in the lens, or outside the course so far.
   5. **Feedback matches.** The `feedback-instructions::` treat as a gap only what the question asks.
   6. **No copy-paste full marks.** Where a question asks what an author says (a reply, an argument, a claim), check whether pasting the author's own sentences would earn full marks. If it would, the question says "In your own words", and the rubric may then cap an answer that only copies.
   7. **No hidden facts.** List every fact about the scenario that the rubric's answer relies on: who wants what, who knows what, what happened. For each, quote the words of the question that state it. If one is not stated, write a short, well-argued answer that assumes the opposite. If the rubric would score that answer below about 85, it fails. Fix the question so it states the fact, or fix the rubric so it accepts both readings.
   8. **Named targets.** The question names what it refers to. "Why are they not worried?" must say worried about what. "What does it not show?" is open to endless answers (it doesn't show the Earth is round), so ask about one named claim instead: "Does it answer X, or only show Y?" If a reasonable learner could ask "about what?", it fails.
   Return per question: id, score, PASS or FAIL, and for each failure the check number, the quote, and the smallest fix, saying whether it changes the question or the rubric."
3. **Fix the right side.** When the rubric scores something worth knowing that the question does not ask, change the question so it asks for it. Drop the element only when it was not worth asking. Never make a rubric easier just to pass this check.
4. Repeat with fresh agents until every question passes. Report how many rounds each lens took and what changed.

## The pre-reading question (PQ) lens

Before a heavy reading, a tiny lens primes the intuition the chapter will challenge: one `#### Question: Open`, no reading. Its brief is deliberately minimal: acknowledge in 1–2 sentences, **do not** preview the chapter's argument, close by sending them to the reading. Named `<Topic> - PQ`, listed in the module as the `# Lens:` immediately before the main reading lens. See `Lens Edu/Lenses/IABIED - Indifference Not Malice - PQ.md`.

## The segment types

Segments are the `####` blocks of the lens body, and of a Learning Outcome's `## Test:` (gradable response segments and Roleplay only there).

Fields per segment:

- `#### Text`: required `content`. Optional: `optional`.
- `#### Chat`: required `instructions`. Optional: `hidePreviousContentFromUser`, `hidePreviousContentFromTutor`.
- `#### Article`: none required. Optional: `source`, `from`, `to`, `optional`, `render-as-non-article-text`.
- `#### Video`: none required. Optional: `source`, `from`, `to`, `optional`.
- Question segments: use [[../Lenses/Response to question segments]] as the single reference for types, fields, defaults, syntax, and grading behavior.
- `#### Roleplay`: required `id`, `content`, `ai-instructions`. Optional: `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional`.
- `#### Widget`: required `source` (a `widgets/` file). Optional: `height`, `required` (true: the lens waits for the widget's `Lens.complete()`). See [[../AI Guide/How to write widgets]].
- `#### Callout: Title`: a box around the segments that follow, up to the matching `#### End Callout`. Optional: `tone` (neutral, blue, green, amber, red, purple), `collapse` (closed, open); the title is optional too. Any segment can sit inside, and callouts nest to any depth (each `#### End Callout` closes the innermost open one). Live example: [[../Lenses/Nested callouts demo]]. A `:::callout` inside a `content::` value still works for a box that holds only text.

Non-question defaults: `feedback` is false on roleplays; `hidePreviousContent*` is false on chats.

A bare `#### Question` is legacy syntax. Do not write it in new or edited content; convert it to `#### Question: Open` when you touch a lens. Keep the existing `id::`: learners' answers and grades are stored under that id, so a new id detaches them. Only a question that has no `id::` gets a fresh one. Changing the header is not enough, and the old `assessment-instructions::` don't simply carry over: in legacy questions they often hold a tutor brief (turn limits, word counts, "don't reveal") rather than a rubric. For each converted question, decide what it should do:
- **Should the learner get feedback?** Then write `feedback-instructions::` that say how the tutor gives it. A bare question opened the tutor reply on its own, a `Question: Open` shows a "Get feedback" button instead. Add `force-feedback:: first` only if this question should still open the reply without a click ("When feedback starts" above says which ones).
- **Should it be graded?** Then write `assessment-instructions::` as a real rubric (see [[../AI Guide/Writing Rubrics]]). Predictions, reflections and personal views are not graded. **Converting does not change grading on its own — check the field too.** Current parser (`content_processor/src/parser/lens.ts`, "a bare `#### Question`: an alias of `#### Question: Open`"): a bare Question is parsed as `Question: Open` in every respect that matters here, including grading (`response-segments.ts`: `graded` is set exactly when `assessment-instructions::` is present, for both forms alike). The one thing bare adds on top is `feedback:: ` (default true, independent of which instructions field you used) auto-opening the tutor chat. So a bare Question with `assessment-instructions::` gets BOTH a percentage chip AND an auto-opened chat reply — it is not an either/or with `Question: Open`, whatever an earlier version of this note said. See "Which field" above for the actual rule. Six new lenses shipped with the wrong field, caught 2026-09-11; seven more, caught 2026-09-22 (PR #100) — re-verified in source both times, not from this paragraph's memory of itself.

**Text**: prose shown to the learner. `content::` is markdown; escape any headings (`\##`).

**Chat**: open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article**: embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` and the text matched by `to::` (this is not a half-open range). Each anchor is independent: only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes); copy them from the stored article via `read`, never from a summarizing web fetch.

**Where to put the anchors:** excerpts are often cut too short, and learners lose the part that frames the rest. Anchors match text, not whole paragraphs or list items, so an anchor that starts partway into a line drops what comes before it on that line: the `- ` or `1.` that makes a list, the `#` that makes a heading, an opening `**` or `_`. An anchor that ends partway into a line drops the closing `**`, `_` or `"`. So:
- Start `from::` at the beginning of a line, and keep what introduces the passage: its heading (`from:: "## TL;DR"`), a lead-in sentence ending in ":" ("Here's a TL;DR of my cruxes:"), or a bold label. These look like framing the lens text already gives, but the passage reads wrong without them.
- End `to::` at the end of a line, including closing markup and the paragraph's last sentence.
- If an anchor is not unique (short lead-ins often also appear in the frontmatter `description` or in a later quote), lengthen it along the same line. Do not move it further into the content.
- Check each boundary in the rendered lens, not just the anchor text: does it start on a heading or lead-in, do lists render as lists, does the last paragraph end where the author ended it?

**The sidebar credit:** a lens's sidebar {--{"author":"Iris's AI","timestamp":1791603413722}@@entry, module overview--}{++{"author":"Iris's AI","timestamp":1791603413722}@@entry++} and card links credit its article authors and video {--{"author":"Iris's AI","timestamp":1791603413722}@@channels.--}{++{"author":"Iris's AI","timestamp":1791603413722}@@channels, as plain text.++} To change that, set `sidebar_author:` in the lens frontmatter (`sidebar_author::` on an inline lens): a name replaces the credit, `none` credits nobody. Bylines, the source bar, read-aloud and the tutor's source line always keep the article's author. Live example: "Choosing the sidebar credit" in [[../modules/main-demo-module]].

**Showing an article as the lens's own text:** `render-as-non-article-text:: true` on an `#### Article` segment shows the excerpt like a `#### Text` segment. There is no title, author, date, "Read original" link, `[...]` collapsed part or excerpt marker, and the lens is not shown as an article in the navigation. Read-aloud credits the course's partner (or the site that owns the course). Use it only for text that the course's own site or partner publishes, such as the AI Safety Atlas chapters on the Atlas course. A third party's article keeps its byline.

**Video**: same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

Where to cut a video:
- **Use real word times.** The word times in an imported `.timestamps.json` are evenly spread estimates and can be 15 to 25 seconds off late in a video. Auto-caption lines are stamped when they scroll, 2 to 3 seconds after the words are spoken. Take cuts from per-word caption times (for example `yt-transcript --words`), and check them by watching.
- **Fractional seconds** work as `M:SS.s` (`5:13.4`). Past an hour, write minutes: `61:14.6`, not `1:01:14.6`. `H:MM:SS` only takes whole seconds.
- **Cut between sentences,** and make each clip make sense on its own. After a question, the next clip may replay the previous sentence as a lead-in.
- **Skipping a part** of one video: `skip:: 5:13-8:09 "reason"` on one segment keeps one player. Two Video segments in a row show two players, so put one short Text line between them saying what was skipped. Say nothing about cut ads.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question segments**: use [[../Lenses/Response to question segments]].

**Roleplay**: learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Widget**: embeds an interactive HTML page from `widgets/` inline (a clickable diagram, a sorting exercise, a simulation). The file is frontmatter plus a complete HTML document; the platform renders it in a sandboxed, self-sizing frame and gives the tutor its `summary_for_tutor` and visible text. Authoring rules, validation and the Lens look: [[../AI Guide/How to write widgets]].

**Embed**: shows another site's page in a frame. `source::` names an `articles/` file whose `source_url` is the page to show. An embed fills the screen, so it must be the only segment in its lens. The exception is `inline:: true`: the embed then sits between the lens's other segments (also inside a callout), with its title. When the learner clicks into it, it opens as a panel over the page, closed with its ×, so the learner scrolls only the embedded page. Use it for a third-party form, such as an Airtable form, that belongs under the lens's own text. Do not put a form's `<iframe>` in a widget: the widget sandbox has no storage, and an app that needs it (an Airtable form does) stays blank.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card, used for "Additional resources" footers.


- **INLINE THE READING. Never assign a bare title.** Before authoring lenses, identify every external reading requested that should go into it. Import each URL with `import_source`, poll `import_status` until it is done or failed, and use the returned article path in an `#### Article` segment. Do not substitute a summary or a hand-written article file. A lens that says "Read X" and stops has handed the student a homework instruction and no homework. The article file carries `source_url` in its frontmatter, so the student gets the full text in place and a link to the original. Skip importing only when the course intentionally has no external readings; if source-based learning is requested but no sources were supplied, ask the user for sources or explicitly propose suitable ones. Check the licence per source rather than assuming: most of this corpus is LessWrong and Alignment Forum, but org blogs (Cold Takes, AI Impacts, Forethought, Epoch) are not the same terms and are not covered by "it's all LW". When importing an existing course, do not copy third-party source text into a lens’s `Text` segment, even if that text is included in the course repository. Import its canonical URL with `import_source`, then reproduce the assigned excerpt using an `Article` segment with `from` and `to` anchors.
- **Never paste a source's text as a quote in a `Text` segment.** This holds for a paper's abstract, a comment's paragraph, or any passage longer than a short phrase in your own sentence. Import the source and show the passage as an `Article` excerpt, so the learner sees it as part of the source, with its link. If the article is only a stub (tag `article-stub`, no body), import it again in `article` mode. If an import holds more than the source (a comment import that pulled in the whole thread), fix the article file. Import a comment by its GreaterWrong URL (`https://www.greaterwrong.com/posts/<post id>/<slug>/comment/<comment id>`). A LessWrong `?commentId=` link imports the whole post instead. Do not paste the text around the problem.

- **Administer what the author already wrote, rather than inventing a parallel exercise.** Many good posts open with their own exercise, thought experiment, or prediction prompt. Kokotajlo's *Fun with +12 OOMs of Compute* opens by asking the reader to do a specific thing; the right lens asks the student to do exactly that, then reads. Writing a fresh pre-question next to an unused one the author supplied is worse on both counts: it is more work and it is less well-aimed, because the author built theirs to set up their own argument.