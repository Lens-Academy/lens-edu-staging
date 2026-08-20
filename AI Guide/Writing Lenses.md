---
tags:
  - validator-ignore
---
# Writing Lenses (AI Guide)

A lens (`Lenses/<Name>.md`) is a **flat file** of frontmatter + `####` segments: no H1–H3 structure, and segment headers take no title (the lens title lives in frontmatter).

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words, speaks to the learner; an analogy beats a summary: "Like a parent who knows how babies are made but not what the baby will become"), `summary_for_tutor` (AI-facing: what the lens teaches and how its parts sequence), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `duration_minutes` (1–600, the lens's total expected completion time; replaces the platform's computed time estimate, see "Estimate every lens's time" below), `reading_minutes` / `tutor_minutes` (0–600 each, the same estimate split into content time and AI-tutor time; use the split instead of `duration_minutes`, never together with it), `add_to_ai_context` (injects source material into the tutor's context; use when the tutor must discuss a text the student read elsewhere).

The patterns below come from the **AI Risk Fundamentals** course (`IABIED` prefix, built around *If Anyone Builds It, Everyone Dies*), the current quality bar. Reuse the structure; adapt the content. Read a real example before writing: `Lens Edu/Lenses/IABIED - AI Is Grown, Not Crafted.md` is the canonical reading lens.

## Estimate every lens's time

When you create or change a lens, estimate {--{"author":"Elias's AI","timestamp":1787254893632}@@how long a typical learner needs to finish it from start to end, and put that at --}the{--{"author":"Elias's AI","timestamp":1787254893632}@@ top of the lens. Prefer the split form, because the platform displays content --}{++{"author":"Elias's AI","timestamp":1787254893632}@@ learner's real start-to-finish ++}time and{--{"author":"Elias's AI","timestamp":1787254893632}@@ tutor time separately:

- `reading_minutes: 12` plus `tutor_minutes: 8` (frontmatter), or `reading_minutes:: 12` / `tutor_minutes:: 8` on an inline lens.--}{++{"author":"Elias's AI","timestamp":1787254893632}@@ set it at the top: prefer++} `reading_minutes` {--{"author":"Elias's AI","timestamp":1787254893632}@@is all content work: reading, watching, on-page exercises.--}{++{"author":"Elias's AI","timestamp":1787254893632}@@+++} `tutor_minutes`{--{"author":"Elias's AI","timestamp":1787254893632}@@ is the AI conversations (chats, question feedback, roleplays). Either may stand alone; the other part stays estimated.--}{++{"author":"Elias's AI","timestamp":1787254893632}@@ (content time + AI-conversation time, displayed split; either alone works,++} `tutor_minutes: 0` {--{"author":"Elias's AI","timestamp":1787254893632}@@states there is--}{++{"author":"Elias's AI","timestamp":1787254893632}@@means++} no {--{"author":"Elias's AI","timestamp":1787254893632}@@real --}tutor{--{"author":"Elias's AI","timestamp":1787254893632}@@ work.
- `duration_minutes: 20` is the one-number alternative when a split would be false precision; it shows as a plain total. Never combine it with the split fields (validation error).

The authored values replace the platform's computed estimate everywhere the time shows (course page, module page, sidebar, resource cards).

**Keep estimates up to date.** Whenever you change a lens (adding a reading, cutting a segment, tightening a chat), re-estimate and update the fields in the same edit. A stale authored value is worse than the computed fallback, because it looks deliberate.

--}{++{"author":"Elias's AI","timestamp":1787254893632}@@ time), or one `duration_minutes` total, never both. ++}Estimate from what the learner actually does, not {--{"author":"Elias's AI","timestamp":1787254893632}@@from --}a word-count{--{"author":"Elias's AI","timestamp":1787254893632}@@ formula: careful-study reading is slower than skimming; dense or technical texts read slower than narrative ones; a reflective question with expected --}{++{"author":"Elias's AI","timestamp":1787254893632}@@ formula (dense readings are slower, required ++}back-and-forth costs {--{"author":"Elias's AI","timestamp":1787254893632}@@far --}more than a quick {--{"author":"Elias's AI","timestamp":1787254893632}@@factual answer; --}{++{"author":"Elias's AI","timestamp":1787254893632}@@answer, ++}count{--{"author":"Elias's AI","timestamp":1787254893632}@@ work assigned outside the page too ("read--}{++{"author":"Elias's AI","timestamp":1787254893632}@@ off-page work like "read++} chapter{--{"author":"Elias's AI","timestamp":1787254893632}@@ 2", offline exercises), which the computed fallback cannot see. Round--}{++{"author":"Elias's AI","timestamp":1787254893632}@@ 2"), round++} to a friendly {--{"author":"Elias's AI","timestamp":1787254893632}@@number (5, 10, 15, 25...).

If--}{++{"author":"Elias's AI","timestamp":1787254893632}@@number, and re-estimate in++} the {--{"author":"Elias's AI","timestamp":1787254893632}@@field is absent, the platform falls back to its computed estimate (word count at 200 wpm + video length + tutor time), so leaving it off is safe for --}{++{"author":"Elias's AI","timestamp":1787254893632}@@same edit whenever you change ++}a {--{"author":"Elias's AI","timestamp":1787254893632}@@quick draft, but finished lenses should carry it. See --}{++{"author":"Elias's AI","timestamp":1787254893632}@@lens. Rendered example: ++}the Demo Course's "Lens duration demo" {--{"author":"Elias's AI","timestamp":1787254893632}@@module for a rendered example.--}{++{"author":"Elias's AI","timestamp":1787254893632}@@module.++}

## The reading lens: Recall → Processing → Learning Question

Every IABIED reading lens follows the same five-beat structure. It works because it forces retrieval before reflection, reflection before analysis, and never lets the tutor lecture.

```markdown
#### Text                                      ← 1. Reading assignment
content::
\## Reading Assignment
**Read *Chapter 2: Grown, Not Crafted*.** Start at the beginning and stop when you reach
> <exact quote from the text marking the stop point>
Return here after reading.

#### Question                                  ← 2. Phase 1: Recall
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember from the reading, without
looking back at the text. Anything and everything. No need to organize it. Using the
speech to text feature is highly recommended here.
assessment-instructions:: <recall-mirror brief, see below>

#### Question                                  ← 3. Phase 2: Processing ("what landed")
content::
\## Phase 2: Processing
Take 2 minutes to jot down how the reading landed. What resonated? What confused you?
What did you doubt or push back on? No need to organize. Just capture your reaction.
assessment-instructions:: <processing brief, see below>

#### Question                                  ← 4. Phase 3: Learning Question
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

Before a heavy reading, a tiny lens primes the intuition the chapter will challenge: one `#### Question`, no reading. Its brief is deliberately minimal: acknowledge in 1–2 sentences, **do not** preview the chapter's argument, close by sending them to the reading. Named `<Topic> - PQ`, listed in the module as the `# Lens:` immediately before the main reading lens. See `Lens Edu/Lenses/IABIED - Indifference Not Malice - PQ.md`.

## The 6 segment types

Segments are the `####` blocks of the lens body, and of a Learning Outcome's `## Test:` (Question and Roleplay only there).

Fields per segment:

- `#### Text`: required `content`. Optional: `optional`.
- `#### Chat`: required `instructions`. Optional: `hidePreviousContentFromUser`, `hidePreviousContentFromTutor`.
- `#### Article`: none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Video`: none required. Optional: `source`, `from`, `to`, `optional`.
- `#### Question`: required `content`. Optional: `assessment-instructions`, `max-time`, `max-chars`, `enforce-voice`, `feedback`, `optional`.
- `#### Roleplay`: required `id`, `content`, `ai-instructions`. Optional: `opening-message`, `assessment-instructions`, `user-customizable`, `feedback`, `optional`.

Defaults: `optional` false; `feedback` true on questions, false on roleplays; `hidePreviousContent*` false.

**Text**: prose shown to the learner. `content::` is markdown; escape any headings (`\##`).

**Chat**: open AI-tutor discussion. `instructions::` briefs the tutor (topics to explore, persona, boundaries).

**Article**: embeds an excerpt of an `articles/` file. `from::`/`to::` are exact text anchors quoted from the article ("start here", "stop here"). **Both anchors are inclusive:** the excerpt contains the text matched by `from::` and the text matched by `to::` (this is not a half-open range). Each anchor is independent: only `from::` reads to the end, only `to::` reads from the start, neither embeds the whole article. Text outside the excerpt is shown collapsed, so anchors need only bracket the assigned part. Anchors must match the article file character-exactly (watch curly quotes); copy them from the stored article via `read`, never from a summarizing web fetch.

**Video**: same idea for `video_transcripts/` files; `from::`/`to::` are timestamps (`M:SS` or `H:MM:SS`), `from::` defaults to `0:00`, `to::` to the end.

**Source inheritance:** the first Article (or Video) segment in a lens must have `source::`; later segments of the same type inherit the previous source, so a multi-excerpt reading is several `#### Article` blocks with only `from::`/`to::`.

**Question**: learner writes/dictates an answer, the AI responds per `assessment-instructions::`. `max-time:: 3:00` (or `none`), `max-chars`, `enforce-voice:: true` for spoken answers, `feedback:: false` to record without AI response.

**Roleplay**: learner talks with a persona defined in `ai-instructions::`; `content::` sets the scene for the learner, `opening-message::` is the persona's first line.

**Resource cards:** inside a `content::` value, `::card[[../Lenses/Name]]` followed by a `> blockquote` description renders a linked card, used for "Additional resources" footers.

