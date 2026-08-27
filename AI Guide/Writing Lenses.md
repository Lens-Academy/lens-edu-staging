---
tags:
  - validator-ignore
---
# Writing Lenses (AI Guide)

A lens (`Lenses/<Name>.md`) is a **flat file** of frontmatter + `####` segments: no H1–H3 structure, and segment headers take no title (the lens title lives in frontmatter).

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words, speaks to the learner; an analogy beats a summary: "Like a parent who knows how babies are made but not what the baby will become"), `summary_for_tutor` (AI-facing: what the lens teaches and how its parts sequence), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `duration_minutes` (1–600, the lens's total expected completion time; replaces the platform's computed time estimate, see "Estimate every lens's time" below), `reading_minutes` / `tutor_minutes` (0–600 each, the same estimate split into content time and AI-tutor time; use the split instead of `duration_minutes`, never together with it), `add_to_ai_context` (injects source material into the tutor's context; use when the tutor must discuss a text the student read elsewhere).

The patterns below come from the **AI Risk Fundamentals** course (`IABIED` prefix, built around *If Anyone Builds It, Everyone Dies*), the current quality bar. Reuse the structure; adapt the content. Read a real example before writing: `Lens Edu/Lenses/IABIED - AI Is Grown, Not Crafted.md` is the canonical reading lens.

## Estimate every lens's time

When you create or change a lens, estimate the learner's real start-to-finish time and set it at the top: prefer `reading_minutes` + `tutor_minutes` (content time + AI-conversation time, displayed split; either alone works, `tutor_minutes: 0` means no tutor time), or one `duration_minutes` total, never both. Estimate from what the learner actually does, not a word-count formula (dense readings are slower, required back-and-forth costs more than a quick answer, count off-page work like "read chapter 2"), round to a friendly number, and re-estimate in the same edit whenever you change a lens. Rendered example: the Demo Course's "Lens duration demo" module.

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
assessment-instructions:: <recall-mirror brief, see below>

#### Question: Open                            ← 3. Phase 2: Processing ("what landed")
id:: <uuid>
content::
\## Phase 2: Processing
Take 2 minutes to jot down how the reading landed. What resonated? What confused you?
What did you doubt or push back on? No need to organize. Just capture your reaction.
assessment-instructions:: <processing brief, see below>

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

### What each `assessment-instructions::` brief must do

All three share a house style: state who the student is and what they just did; give the key concepts of the reading as a checklist; set response length ("80–150 words. Short paragraphs only. No lists."); and ban generic praise ("Do not over-validate. Avoid generic praise (great job, excellent recall, well done)").

**Phase 1: Recall (one turn).** The tutor is "diagnostic, not instructional: a brief, honest mirror": acknowledge what's correct without inflation, name what's missing without lecturing, correct errors in one sentence, normalize gaps, close with a calibrating sentence. Explicitly: no re-teaching, no follow-up questions, no inviting dialogue: "This is a one-turn response. Tell them to move on."

**Phase 2: Processing (max 2 turns).** "A processing phase, not a teaching phase": help the student articulate their reaction, don't resolve it. Branch on what they expressed: confusion → ask what specifically is unclear; skepticism → treat as a legitimate stance, ask what would convince them; resonance → ask what it connected to. If their confusion is exactly the learning outcome, defer it: "the next step will dig into exactly that." Enforce the cap: "Keep an internal turn counter. After 2 tutor replies, close the phase."

**Phase 3: Learning Question (3 turns, then offer to continue).** The question is "a deliberate wedge: not the test question: a plausible-sounding but flawed claim; the student locates the flaw" so the outcome is drawn out from a fresh angle rather than recited. State the learning outcome and key concepts verbatim in the brief. Per reply: answer direct questions directly; otherwise steelman the student's answer in 2–4 sentences, name 1–3 gaps, ask 2 causal follow-ups (why/how/what-if, each directly answerable, no opinion questions). Include rescue moves ("if stuck after 2 attempts, give a brief direct answer and move on") and a closing calibration with an explicit test-readiness verdict.

## The pre-reading question (PQ) lens

Before a heavy reading, a tiny lens primes the intuition the chapter will challenge: one `#### Question: Open`, no reading. Its brief is deliberately minimal: acknowledge in 1–2 sentences, **do not** preview the chapter's argument, close by sending them to the reading. Named `<Topic> - PQ`, listed in the module as the `# Lens:` immediately before the main reading lens. See `Lens Edu/Lenses/IABIED - Indifference Not Malice - PQ.md`.

## The segment types

Segments are the `####` blocks of the lens body, and of a Learning Outcome's `## Test:` (gradable response segments and Roleplay only there).

Fields per segment:

- `#### Text`: required `content`. Optional: `optional`.
- `#### Chat`: required `instructions`. Optional: `hidePreviousContentFromUser`, `hidePreviousContentFromTutor`.
- `#### Article`: none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Video`: none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Question: Open`: required `id`, `content`. Optional: `assessment-instructions`, `feedback-instructions`, `max-time`, `max-chars`, `placeholder`, `enforce-voice`, `optional`.
- `#### Question: Rating`: required `id`, `content`. Optional: `scale` (2 to 10, default 5), `low-label`, `high-label`, `feedback-instructions`, `optional`. Never graded.
- `#### Question: Choice`: required `id`, `content`, `options` (list; `- [x]` marks a correct option and makes it graded). Optional: `multi`, `shuffle`, `feedback-instructions`, `optional`.
- `#### Question: FillBlank`: required `id`, `content` with `{{expected}}`, `{{alt1|alt2}}`, `{{blank}}`, `{{number}}`, or `{{number 42}}` blanks. Optional: `assessment-instructions`, `feedback-instructions`, `optional`.
- `#### Question: Ranking`: required `id`, `content`, `items` (list in intended order, shown shuffled). Optional: `assessment-instructions` (presence = graded), `feedback-instructions`, `optional`.
- `#### Roleplay`: required `id`, `content`, `ai-instructions`. Optional: `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional`.

Defaults: `optional` false (every response segment must be answered before the lens can be completed); no tutor feedback unless `feedback-instructions::` is present; `feedback` false on roleplays; `hidePreviousContent*` false.

A bare `#### Question` (no subtype, no `id::`) is the legacy form. Do not write it in new or edited content; convert it to `#### Question: Open` with a fresh `id::` when you touch a lens. The full field reference with live examples is [[../Lenses/Response to question segments]].

**Text**: prose shown to the learner. `content::` is markdown; escape any headings (`\##`).

**Chat**: open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article**: embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` and the text matched by `to::` (this is not a half-open range). Each anchor is independent: only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes); copy them from the stored article via `read`, never from a summarizing web fetch.

**Video**: same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question: Open**: learner writes/dictates an answer. `assessment-instructions::` makes it graded (assessor returns a 0 to 100 score; learner sees the percentage). `feedback-instructions::` opens a tutor feedback conversation on the answer; omit it to record without AI response. `max-time:: 3:00`, `max-chars`, `placeholder`, `enforce-voice:: true` for spoken answers.

**Question: Rating / Choice / FillBlank / Ranking**: same shape (`id::`, `content::`, `optional::`, `feedback-instructions::`) with their own fields listed above. Use Rating for self-report (confidence, interest), Choice for recognition checks and preferences, FillBlank for precise recall inside a sentence or numeric estimates, Ranking for chronology, procedures, and priorities.

**Roleplay**: learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card, used for "Additional resources" footers.


- **INLINE THE READING. Never assign a bare title.** Before authoring lenses, identify every external reading requested that should go into it. Import each URL with `import_article`, poll `import_status` until it is done or failed, and use the returned article path in an `#### Article` segment. Do not substitute a summary or a hand-written article file. A lens that says "Read X" and stops has handed the student a homework instruction and no homework. The article file carries `source_url` in its frontmatter, so the student gets the full text in place and a link to the original. Skip importing only when the course intentionally has no external readings; if source-based learning is requested but no sources were supplied, ask the user for sources or explicitly propose suitable ones. Check the licence per source rather than assuming: most of this corpus is LessWrong and Alignment Forum, but org blogs (Cold Takes, AI Impacts, Forethought, Epoch) are not the same terms and are not covered by "it's all LW". When importing an existing course, do not copy third-party source text into a lens’s `Text` segment, even if that text is included in the course repository. Import its canonical URL with `import_article`, then reproduce the assigned excerpt using an `Article` segment with `from` and `to` anchors.
