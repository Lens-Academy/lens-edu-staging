---
tags:
  - validator-ignore
---
# Writing Lenses (AI Guide)

A lens (`Lenses/<Name>.md`) is the actual learning content: a **flat file** of frontmatter + `####` segments. No H1–H3 structure, and segment headers take no title (`#### Text: Intro` is an error — the lens title lives in frontmatter).{++{"author":"Elias's AI","timestamp":1785489960535}@@ Segment syntax (the 6 types — Text, Chat, Article, Video, Question, Roleplay — and their fields): `Lens Edu/AI Guide/Course Authoring.md`.++}

Frontmatter: required `id`; optional `title`, `tldr` (one-sentence takeaway, ≤80 words — speaks to the learner; an analogy beats a summary: "Like a parent who knows how babies are made but not what the baby will become"), `summary_for_tutor` (AI-facing: what the lens teaches and how its parts sequence), `tags`, `min_chat_messages` (0–20, gates progression on chat participation), `add_to_ai_context` (injects source material into the tutor's context — use when the tutor must discuss a text the student read elsewhere).

The patterns below come from the **AI Risk Fundamentals** course (`IABIED` prefix — built around *If Anyone Builds It, Everyone Dies*), the current quality bar. Reuse the structure; adapt the content. Read a real example before writing: `Lens Edu/Lenses/IABIED - AI Is Grown, Not Crafted.md` is the canonical reading lens.

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

**Phase 1 — Recall (one turn).** The tutor is "diagnostic, not instructional — a brief, honest mirror": acknowledge what's correct without inflation, name what's missing without lecturing, correct errors in one sentence, normalize gaps, close with a calibrating sentence. Explicitly: no re-teaching, no follow-up questions, no inviting dialogue — "This is a one-turn response. Tell them to move on."

**Phase 2 — Processing (max 2 turns).** "A processing phase, not a teaching phase" — help the student articulate their reaction, don't resolve it. Branch on what they expressed: confusion → ask what specifically is unclear; skepticism → treat as a legitimate stance, ask what would convince them; resonance → ask what it connected to. If their confusion is exactly the learning outcome, defer it: "the next step will dig into exactly that." Enforce the cap: "Keep an internal turn counter. After 2 tutor replies, close the phase."

**Phase 3 — Learning Question (3 turns, then offer to continue).** The question is "a deliberate wedge: not the test question — a plausible-sounding but flawed claim; the student locates the flaw" so the outcome is drawn out from a fresh angle rather than recited. State the learning outcome and key concepts verbatim in the brief. Per reply: answer direct questions directly; otherwise steelman the student's answer in 2–4 sentences, name 1–3 gaps, ask 2 causal follow-ups (why/how/what-if, each directly answerable, no opinion questions). Include rescue moves ("if stuck after 2 attempts, give a brief direct answer and move on") and a closing calibration with an explicit test-readiness verdict.

## The pre-reading question (PQ) lens

Before a heavy reading, a tiny lens primes the intuition the chapter will challenge — one `#### Question`, no reading. Its brief is deliberately minimal: acknowledge in 1–2 sentences, **do not** preview the chapter's argument, close by sending them to the reading. Named `<Topic> - PQ`, listed in the module as the `# Lens:` immediately before the main reading lens. See `Lens Edu/Lenses/IABIED - Indifference Not Malice - PQ.md`.

