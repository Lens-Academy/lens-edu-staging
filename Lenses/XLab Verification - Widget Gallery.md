---
id: '6f0d2b9e-3c1a-4e7b-9a52-8d4c1f6e2b73'
title: "Widget Gallery: Compute Verification Parts 1 and 2"
tldr: "Every interactive built for the two Compute Verification courses, live on one page, each with the lens it belongs to, the spot it goes in, and what it replaces. 35 widgets, 5 places where our own question segments are enough, 17 skips."
summary_for_tutor: "An internal review page for course authors, not learner material. It lists every widget ported from XLab's Verification track or built for an embedded reading, ordered by module and lens, with placement instructions. If someone asks, explain that this is a staging gallery and that widgets listed here are not yet placed in the course."
tags: [wip]
duration_minutes: 90
---

#### Text
content::
This page collects every interactive built for Compute Verification Parts 1 and 2 from XLab's Verification track and from the readings the course embeds. Entries leave this page once they are placed in the course; placed so far: A Short History of AI Acceleration (timeline), Test scores of AI systems (short history), The Types of AI, The Verification Landscape, The Verification Problem, Theory of Change for Your Favorite AI Safety Organization, Why Are We Concerned About Superintelligence?. Native entries reviewed and agreed, so also gone from this page: Tasks on the Document Packet, Anatomy of a (Pause) Agreement. Each entry says which lens it belongs to, where in that lens it goes, and what it would replace, so placement is a copy-paste decision per entry. Entries marked native say that our own question segments already do the job, with the proposed segment text in a collapsed note. Entries are ordered by module and lens. Every widget below is live: try it.

#### Text
content::
\## Part 1 · Week 3: Who the treaty relies on, applies to, and constrains

Module file: [[../modules/XLab Verification P1 W3 Treaty actors]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-interactive-map]]

#### Text
content::
\## Part 1 · Week 4: Upstream and downstream

Module file: [[../modules/XLab Verification P1 W4 Evidence and its readers]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-context-distiller]]

#### Text
content::
\#### The Distiller (context-distiller)

**Decision: widget.** All five XLab stages are interactive (clip from a decoy-laden pool under a cap, tap-to-compress reveal, two commit-then-reveal actor picks, a point-to-reader threading board with a delivery verdict and letters); none is free writing, and the whole flow with all four reports fits in 142 KB.

**Target lens:** [[../Lenses/XLab Verification - v-context-distiller]]

**Where it goes:** after the Text segment "The exercise takes the five steps in the order that makes them workable" (the "\## The Distiller" heading block), where the Choice segment "Pick one report. You will work it through every step below" sits today.

**What it replaces:** (a) the Choice segment 21ffdd3a-ab25-4e20-9187-78f9e6d5870e (report pick is the widget's first screen); (b) the four Open questions that stood in for the widget: 27da880f (clip and distil), a84c30be (upstream), 8d9e55c8 (downstream), 09aa8344 (thread), together with their "\### 1 and 2. Clip, then distil" / "\### 3." / "\### 4." / "\### 5." heading Text blocks, whose prose is the widget's own phase lead copy; (c) the four "Candidate passages" callouts (the widget holds the same pools, shuffled per section) and the "Read your report through before clipping" paragraph. These should go entirely. Keep: the intro, five-steps list, worked example, "Your Options" list and the warm-up Open 4bbefd68 (all precede the widget); the report-links Text and the three Article segments for AISI, IAEA and Seagate as reading (the widget shows only excerpts of those three; the r1 full text is inside the widget's "Full report" view, so the "Full text: Claude Opus 4.7 System Card" callout may go or stay collapsed); the four "Key" callouts and "Works cited" at the end should stay collapsed as the tutor's reference, since the widget builds all of its text in JavaScript and the tutor otherwise sees only the summary.

**In XLab:** <VerificationExercise id="context-distiller" /> in context-distiller.mdx, core, not inside a Fold, directly after the "Your Options (Pick One)" list and the notebook callout "For each: where did it come from, who reads it next?".

**Learner time:** 35 minutes for one report (XLab's lesson is budgeted at 75 minutes including the readings); a second report or the tight-budget replay adds 15 to 20.

Picks one of four reports (fictional Claude Opus 4.7 System Card; AISI Frontier AI Trends Report; IAEA GOV/2026/8; BIS order against Seagate) and clips passages from a per-section pool of core facts and decoys into a capped notebook (12/11/10/10), reordering or dropping as they go; for the system card they can also read the whole card and clip highlighted passages in place. Each clipping is then tapped to compress into XLab's pre-written distillation for the report's post, which is where decoys are exposed as filler. They multi-select the upstream actors and then the downstream readers, commit, and see each option marked yes, missed, no or left out with XLab's reason. On the threading board they pin their distilled points to readers (each reader shows what they already know and the questions they need answered), deliver, and see which questions went unanswered and which passage would have answered them, plus points wasted on readers who already knew them and clips wasted on filler; a letters view shows each reader exactly what they were sent. Lens.complete() fires on the first delivery, as XLab's onComplete does; a perfect standard run unlocks the tight-budget replay.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Stages in: all five (Clip with excerpt and full-report views, Distil, Upstream, Downstream, Thread) plus the delivered letters screen, the tight-budget replay, two-tap Reset, Change report with per-report runs retained, and Escape to clear an armed pin or trace. Nothing left out. Data source: XLAB `src/lib/verification/data/context-distiller.ts` (all four reports, every block, stakeholder, question, actor and reportDoc paragraph, inlined verbatim via a build script), UI copy from `src/components/verification/widgets/context-distiller.tsx`, rules from `src/lib/verification/engines/context-distiller.ts`, all at the clone's HEAD.

Adapted:
- Em dashes: 52 data strings (all in the system card report) and a handful of UI strings had em dashes; each was replaced with a comma, or a colon where the dash introduced an explanation. Three lead-dash lines became parentheticals: "(filler; nothing here changes what a reader does.)", "(you sent this reader nothing.)", "(your distillation)".
- Option order: XLab renders upstream and downstream options as key actors first, then distractors, which is solvable by position. The widget shuffles them with a seeded shuffle keyed on report id plus "up"/"down" (FNV-1a and mulberry32, as in XLab's `src/lib/shuffle.ts`). The clipping pool is shuffled per section as in XLab, but keyed on report id plus section id instead of a per-visit random seed, so the order is stable across devices and reloads.
- Toasts became an inline status line under the phase lead (same wording). SVG thread curves draw only at 900px and up, as XLab draws them only at its lg breakpoint; below that the thread chips on each reader card carry the state.
- The notebook count adds "(tight budget)" in tight mode, so the mode is visible after the one-time status message.
- The letters view is remembered in saved state so a restore renders the same screen; XLab reset it to the board on reload.
- `runs`/`best` are tracked as in XLab and reported in the tutor summary; XLab tracks them without displaying them.
Uncertain: none. The r1 report is fictional and carries XLab's "fictional teaching document" pill; the other three link to their source URLs.
:::

#### Widget
source:: [[../widgets/context-distiller]]

#### Text
content::
\## Part 1 · Week 4: What makes a verification mechanism effective?

Module file: [[../modules/XLab Verification P1 W4 Mechanism effectiveness]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-mechanism-effective]]

#### Text
content::
\## Part 1 · Week 5: Hardware verification

Module file: [[../modules/XLab Verification P1 W5 Hardware verification]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-hw-attestation]]

#### Text
content::
\#### Hardware lessons: reader components and prose diagrams (hardware-reader-checks)

**Decision: nothing to port.** md). None of the nine hardware lessons uses `<Check>`, `<GapFill>` or `<VerdictSelect>`; the only interactive reader component is `<ClaimLedger>`; the three `<Prompt>` blocks and the prose "diagrams" carry no learner action or per-part authored content, so a widget would be a figure.

**Target lens:** [[../Lenses/XLab Verification - v-hw-claim]], [[../Lenses/XLab Verification - v-hw-trusted-statement]], [[../Lenses/XLab Verification - v-hw-accounting]], [[../Lenses/XLab Verification - v-hw-measuring-use]], [[../Lenses/XLab Verification - v-hw-authorization]], [[../Lenses/XLab Verification - v-hw-where-trust-lives]], [[../Lenses/XLab Verification - v-hw-reconstructing-run]], [[../Lenses/XLab Verification - v-hw-attestation]], [[../Lenses/XLab Verification - v-hw-policy-studio]]

**Where it goes:** n/a (nothing to place)

**What it replaces:** nothing; every XLab activity in these lessons is already a Lens `Question: Open` segment with assessment instructions, and every `<Prompt>` is already a blue callout

**In XLab:** no `<VerificationExercise>` in any hardware-*.mdx; `<ClaimLedger>` in hardware-attestation.mdx and hardware-policy-studio.mdx (handled separately); `<Prompt>` in hardware-where-trust-lives.mdx, hardware-measuring-use.mdx, hardware-policy-studio.mdx; `<MemoDesk lesson="hardware-policy-studio" />` in hardware-policy-studio.mdx (already ported as the graded Open question 936e8aee)

**Learner time:** 0 minutes added

Nothing new. The scan found no interactive reader component to port beyond the ClaimLedger. Per lesson (grep over `src/content/lessons/verification/hardware-*.mdx` for `<Check`, `<GapFill`, `<VerdictSelect`, `<Prompt`, `<ClaimLedger`, `<VerificationExercise`, `<Fold`, plus a full read of all nine files, 658 lines):

| Lesson | Reader components | Lens today | Verdict |
| --- | --- | --- | --- |
| hardware-attestation.mdx (2.1) | `<ClaimLedger>` collect, `<Objectives>`, `<Callout>` author note | seven Choice segments, callouts | WIDGET (claim-ledger) |
| hardware-claim.mdx (2.1.1) | none; "Notebook: initial claim map" (three sentence stems) | Open question 48 | SKIP; the notebook is a writing task, NATIVE already |
| hardware-trusted-statement.mdx (2.1.2) | none; prose chain "device and measurement component → ... → regulator or treaty response" with five questions per link; trio-table of prover profiles; "Activity: trust-chain autopsy" | blockquote chain, table, Open question 3336549c | SKIP; see diagram note below |
| hardware-accounting.mdx (2.1.3) | none; "Try it" (three independent evidence streams) | Open question at line 103 | SKIP |
| hardware-measuring-use.mdx (2.1.4) | `<Prompt label="Question to keep visible">`; adversary-move table; "Activity: from result to policy claim" | blue callout, table, Open question at line 107 | SKIP; Prompt is display only |
| hardware-authorization.mdx (2.1.5) | none; prose chain "legal rule → license criteria → ... → renewal or termination"; "Activity: build the authorization chain" (twelve named components, six questions) | blockquote chain, Open question at line 72 | SKIP; see diagram note below |
| hardware-where-trust-lives.mdx (2.1.6) | `<Prompt label="Verification target">`; Architectures A to D with strengths and load-bearing concerns; "Activity: bilateral pilot review" | blue callout, four prose sections, four Baker article excerpts, Open question 340e01e2 | SKIP; see diagram note below |
| hardware-reconstructing-run.mdx (2.1.7, optional) | none; "Activity: buy assurance with a verification budget" | Open question at line 55 | SKIP; a budget allocator would need cost and assurance numbers XLab does not supply |
| hardware-policy-studio.mdx (2.1.8) | `<Prompt>`, `<MemoDesk>`, `<ClaimLedger recall>`; maturity table; rubric table | blue callout, graded Open question 936e8aee, bullet list of the seven claims | WIDGET only for the ledger recall (claim-ledger); rest SKIP |

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Diagram candidates considered and why none became a widget:

- Attestation chain (2.1.2) and authorization chain (2.1.5). Each is a seven- to nine-link arrow chain followed by the same list of questions for every link. XLab authors nothing per link (no answer to "who controls it" for the signing key, for instance), so a clickable chain would reveal no text on click; content-fidelity rules forbid inventing per-link answers. The chain as an inline SVG figure would be a figure, not a widget (guide: "if nothing changes when they interact, it is a figure"). The Lens blockquote rendering is adequate.
- "Where should trust live" (2.1.6). Four architectures, each with components, potential strengths and load-bearing concerns, all verbatim in the Lens lens already, followed by Baker's own on-chip and off-chip analyses. A pick-two side-by-side comparison widget is buildable from the data verbatim (no invention needed) and would let the learner put A next to B for the bilateral pilot review. Not built because the click changes layout only: no reveal, no judgment, no feedback, and the distinguishing content (what each delegation distrusts) is what the learner writes in the Open question. If the orchestrator wants it anyway, it is a 20-minute build with the four blocks from hardware-where-trust-lives.mdx and the Prompt as the target line; suggested id `trust-placement-compare`.
- Maturity stages (2.1.8), function map (2.1), adversary trio-table (2.1.2), adversary-move table (2.1.4): plain reference tables, no learner action; the Lens tables are faithful.
- "Build the authorization chain" (2.1.5) names twelve components to assemble into an end-to-end system, which reads like a drag-to-order exercise, but XLab supplies no target order, no per-component role text and no key for its six questions, so an assembly widget could not check or explain anything. Stays NATIVE as the existing Open question.
- "Buy assurance with a verification budget" (2.1.7) reads like a slider allocator, but XLab supplies no costs, assurance values or budget size. Stays NATIVE.

Sources: `src/content/lessons/verification/hardware-*.mdx` (nine files, HEAD of the xlab-tracks clone), `src/components/mdx/reader/*.tsx` (check, gap-fill, verdict-select, claim-ledger, prompt, reading-card, source-quote, marks, capstone-bank, signatory-quotes), the nine `Lenses/XLab Verification - v-hw-*.md` files.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

n/a: every activity already has an Open segment in its lens and every Prompt is already a callout; nothing to add.
:::

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-hw-where-trust-lives]]

#### Text
content::
\## Part 2 · Week 7: Cloud limits and intelligence

Module file: [[../modules/XLab Verification Part 2 W07 Cloud limits and intelligence]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-cloud-evidence]]

#### Text
content::
\#### Cloud Evidence Drill (cloud-evidence-drill)

**Decision: widget.** Nine commit-then-reveal tasks (true/false grid, odd one out with a gated free sentence, multi-select, matching, gap fill, ordering, concept naming, case multi-select, single choice) with instant verdict, hint, explanation and sources per task, a progress rail and a finish gate; Lens Choice segments have no reveal and no order/sequence interaction.

**Target lens:** [[../Lenses/XLab Verification - v-cloud-evidence]]

**Where it goes:** "## Cloud verification problem set *30 minutes* Answer from the assigned readings." (the second Text segment, directly after the "## 2.2.4 Interpreting cloud evidence" intro)

**What it replaces:** the whole native reproduction of the drill: the "Cloud verification problem set" Text segment with its Task 1 heading, 18 Question segments (6 Choice true/false, 1 Choice + 1 Open for the odd one out, 1 multi Choice, 4 Choice matching, 1 FillBlank gaps, 1 Ranking, 1 FillBlank concepts, 1 multi Choice case, 1 Choice inference), the 9 closed "Why"/"Review" callouts, and the "Problem set complete" Text (its two paragraphs and the policy-scope link are the widget's finish screen). All of it should go entirely; the widget carries every prompt, option, explanation and source link. Keep the "2.2.4 Interpreting cloud evidence" intro Text before the widget and the "Works cited" callout after it. Suggested segment: `#### Widget` / `source:: [[../widgets/cloud-evidence-drill]]` / `required:: true`.

**In XLab:** <VerificationExercise id="cloud-evidence-drill" /> in cloud-evidence.mdx, core (the lesson is only the intro paragraph plus the exercise), not inside a Fold

**Learner time:** 30 minutes (XLab's header; the nine task timings sum to 30)

The learner works through nine tasks on a numbered rail: marks six statements true or false, picks the odd observable and writes a one-sentence principle, selects the data categories a KYC-implementing provider actually holds, matches four observables to the strongest conclusion each supports, fills five gaps of a verification map from an eight-term bank, orders the six stages of the Egan and Heim KYC scheme (drag or arrow buttons), names four mechanisms, qualifies the evidence in a rendering-versus-training case, and chooses the permissible inference for six sibling accounts under a per-account threshold. Each task has a Check answer button: a wrong check shows XLab's hint and the sources and leaves the inputs open; a right check shows "Supported" with XLab's explanation, locks the task and ticks it on the rail (tasks 1, 3 and 7 also open a review list). Finish problem set unlocks once all nine are solved and shows XLab's closing screen with the Carnegie policy-scope link and Run again.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All nine tasks ported; nothing dropped. Every prompt, statement, option, hint, explanation, source label and link is verbatim from `xlab-tracks/src/lib/verification/data/cloud-evidence-drill.ts` and the JSX text of `xlab-tracks/src/components/verification/widgets/cloud-evidence-drill.tsx` (current HEAD; the widget does not use the kit). A script check confirmed every data string and every `wrong=`/`correct=`/Prompt string from the component appears unchanged in the widget. XLab's copy has no em dashes; the en dash in "Egan–Heim" and the section ranges is XLab's.
- Task 2's principle sentence is gated by XLab's engine `explainsOddCloudObservable` (`xlab-tracks/src/lib/verification/engines/cloud-evidence-drill.ts`), ported verbatim: at least 28 characters, one actor term, one activity term, one contrast term, and the odd item must be the beneficial-ownership record. No `Lens.submit`: XLab has no marking key for it beyond this lexical check, and the sentence reaches the tutor through the saveState summary. If AI grading of that sentence is wanted, the current lens's Open segment (id 476ba00c-21b3-455d-be70-a978bd1640bc) could be kept after the widget; its rubric is the porter's, not XLab's.
- Option order: XLab renders every list in authored order, which makes four tasks solvable by position (matching rows 1-4 = conclusions 1-4; gap rows 1-5 = the first five bank terms; concept rows 1-4 = mechanisms 1-4; the case's first three options are the true ones). Following XLab's own `src/lib/shuffle.ts` (ported: FNV-1a + mulberry32 + Fisher-Yates, seeded on a fixed per-question key), the widget shuffles the odd-one-out items, the matching conclusions, the term bank, the mechanisms, the case options and the inference options. Rows (the question side) keep XLab's order. Not shuffled: the true/false statements (numbered, and XLab's explanation says "1 True; 2 False ..."), the sequence start order (XLab authors it deliberately), and the select-all categories, because XLab's explanation reads "The first five categories are available under the stated conditions" and shuffling would make that sentence false; that task therefore keeps a positional pattern (first five true), as in XLab.
- Wrong true/false rows: XLab marks them by border colour only; the widget adds a check or cross glyph beside the statement so the state is visible without colour. This is the only visual addition.
- Drag: XLab uses dnd-kit; the widget uses native HTML5 drag on the rows plus the same up/down arrow buttons, so the prompt "Drag a row or use its arrow buttons" stays true. Drag is not exercised by the jsdom tests; arrows are.
- State: XLab keeps nothing across reloads (component state only). The widget saves every pick, the principle text, the sequence order, per-task verdicts, solved set, current task and finished flag; restore renders identically (verified). `Lens.complete()` fires once, on Finish problem set with all nine solved, mirroring XLab's `onComplete`; Run again resets the drill but does not re-fire complete, like XLab's `completedOnce` ref.
- Standalone fallback: localStorage under `lens-widget-cloud-evidence-drill`.
:::

#### Widget
source:: [[../widgets/cloud-evidence-drill]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-intel-intro]]

#### Text
content::
\#### Intelligence intro pop-ups (intel-popups)

**Decision: nothing to port.** The two `<PopUp>` cards are plain definitions with no learner action beyond expanding them, and the Lens lens already renders both as collapsed callouts.

**Target lens:** [[../Lenses/XLab Verification - v-intel-intro]]

**Where it goes:** after "The goal is that by the end you should be able to take signals" (last paragraph of the first Text segment), where the two callouts already sit

**What it replaces:** nothing; the two collapsed callouts `"National technical means"` and `One vocabulary note` stay as they are

**In XLab:** `<PopUp label="“National technical means”">` and `<PopUp label="One vocabulary note">` at the end of intelligence-intro.mdx, core, not inside a Fold

**Learner time:** 1 minute

Expands two collapsed callouts at the end of the reading: the treaty origin of "national technical means" (SALT I and the ABM Treaty, 1972) and the note that Wasil et al. count whistleblowers under NTM while this course treats them in 2.4.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Checked both callout bodies word for word against `xlab-tracks/src/content/lessons/verification/intelligence-intro.mdx` (HEAD): identical, including the curly quotes in the NTM title. The only difference is that Lens turns "2.3.1" in the vocabulary note into a wikilink to `[[../Lenses/XLab Verification - v-intel-signatures|2.3.1]]`, which is an improvement, not a drift. The lens's `summary_for_tutor` already says the pop-ups are rendered as collapsed callouts. No fix needed.
:::

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-intel-signatures]]

#### Text
content::
\## Part 2 · Week 8: The human layer

Module file: [[../modules/XLab Verification Part 2 W08 The human layer]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-human-insiders]]

Two candidates for one slot. XLab retired the Insider Report drill on 2026-08-14 and now runs Construct the Case under the same exercise id; the Lens page still reproduces the retired drill. Pick one.

#### Text
content::
\#### Insider Report (human-insiders)

**Decision: widget.** Three phases where each action changes what comes next (six source cards with three-way commit-then-reveal per card, a locked case-report quiz that only opens after all six, a finding only issued after four correct answers); 22 checks with explanations, which Lens Choice segments cannot reveal.

**Target lens:** [[../Lenses/XLab Verification - v-human-insiders]]

**Where it goes:** after the Text segment ending "reporting channels can still fail in various ways, which the next section will cover."; it replaces the block that starts with the callout titled "Optional: Insider Report (8 to 10 minutes)" / "**Who knows what?** For each source, identify what they could observe"

**What it replaces:** the whole prose reproduction of the widget: the intro callout, six "### <role> (<station>)" source blocks each with 3 optional Choice segments (18 in total) and a collapsed "Assessment: <role>" callout, the "### Case report · Project Lattice" block with 4 optional Choice segments and 4 collapsed "Why" callouts, and the collapsed "Finding: Further investigation warranted" callout with the failure modes. All of it should go; the widget carries every one of those strings. Keep the "Works cited" Text segment after it. Add `required:: true` only if the module wants the drill gated; XLab folds it as optional.

**In XLab:** <VerificationExercise id="human-insiders" /> in human-insiders.mdx, optional, inside <Fold label="Optional: Insider Report (8–10 minutes)">

**Learner time:** 8 to 10 minutes

Phase 1: picks a source (Evaluator, Training engineer, Infrastructure operator, Procurement or finance staff, Supplier or data-center contractor, Executive or board member), reads its prompt, reported claim, incentives and consistency test, then chooses one card in each of three columns (Could observe, Could not establish, Check against) and presses Check assessment. Wrong or missing picks show XLab's per-column mismatch line; a fully correct set locks the cards, reveals the one-paragraph assessment, and advances the "n of 6 sources assessed" bar. Phase 2 (only after all six): reads the Project Lattice case report and answers four credibility questions (Access, Incentives, Consistency, Independent corroboration); a wrong answer shows the retry hint and must be corrected before Continue appears, a right one shows the explanation and finding line. Phase 3: the finding (disposition, text, four basis lines) and four failure modes; Start over resets everything.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All curriculum text is verbatim from `xlab-tracks/src/lib/verification/data/human-insiders.ts` (174 string literals checked programmatically, 0 missing); UI labels, phase names, the empty-state line ("A job title alone proves nothing..."), the exam aside note and the closing footer line come from `src/components/verification/widgets/human-insiders.tsx`; checking logic from `src/lib/verification/engines/human-insiders.ts`.
- One em dash rewritten: Access option "The installed capacity, site, dates, and project code, not the workload or its authorization." now uses a comma.
- Adaptation: XLab does not shuffle these options, but its authored order is exploitable (the correct connection card is never the first of three in any of the 18 columns; the correct credibility answer is first in all four questions). The widget applies XLab's own seeded shuffle (`src/lib/shuffle.ts`, FNV-1a + mulberry32 + Fisher-Yates) keyed on `<actorId>:<kind>` and `lattice:<questionId>`. Resulting correct positions: connection columns 221000120202210022, credibility questions 2,0,1,1. Same order for every learner and visit. Nothing is keyed on position.
- Adaptation: XLab discards an unresolved source's picks when the learner switches sources; the widget keeps per-source picks in state so a restored session shows what the learner had chosen. Resolved sources show the correct picks locked, as in XLab.
- Lucide icons (per-actor icons, gavel, shield) dropped; replaced by text marks (check, cross, arrows). No images.
- `Lens.complete()` fires once when the learner first reaches the finding (XLab's `onComplete` condition). No `Lens.submit`: XLab has no written answer or marking key here. No `promptTutor`: XLab has no discuss moment.
- Restore guards: a saved state whose phase is examine or finding without all six sources resolved falls back to the map. `meta.completed` or a restored finding phase suppresses a second `complete()`.
- Standalone fallback: `localStorage` key `lens-widget-human-insiders`.
:::

#### Widget
source:: [[../widgets/human-insiders]]

#### Text
content::
\#### Insider Report / Construct a Case (human-insiders, component construct-case)

**Decision: widget.** A four-box constructed response whose desk checks re-run on every keystroke, a steelman deck that deals a new challenge card on demand, and a marking key plus two worked cases that stay hidden until the learner commits; a Lens question segment cannot withhold the failure modes until submission, cannot run the rule checks, and cannot deal challenge cards.

**Target lens:** [[../Lenses/XLab Verification - v-human-insiders]]

**Where it goes:** replaces the collapsed callout that begins "**Who knows what?** For each source, identify what they could observe"; it sits after the Text segment ending "reporting channels can still fail in various ways, which the next section will cover."

**What it replaces:** the whole prose reproduction of XLab's retired "Who knows what?" exercise, that is the intro callout, six "### <role> (<station>)" source blocks with 18 Choice segments and six collapsed "Assessment: <role>" callouts, the "### Case report · Project Lattice" block with four Choice segments and four collapsed "Why" callouts, and the collapsed "Finding: Further investigation warranted" callout. That content is a port of a widget XLab has since retired, so on the live site none of it is what a learner meets at this spot. All of it should go if the module tracks XLab as it stands today; the "Works cited" Text segment after it stays. NOTE FOR THE ORCHESTRATOR: this is the same placement as widgets/human-insiders.md (the older XLab exercise, ported by another agent). Only one of the two belongs here. XLab REPLACED, it did not add: commit f67cb52a (2026-08-14, "2.4.1: Who Knows What? becomes Construct a Case") swapped the registry entry `"human-insiders": HumanInsiders` for `"human-insiders": ConstructCase`, kept the exercise id so the lesson mapping and progress key did not move, and left human-insiders.tsx in the repo unmounted. The commit's reason: the old widget was "eighteen recognitions in a section whose actual operation is construction". A later commit (0b0a767c) renamed the exercise from "Construct a Case" to "Insider Report" and flipped it to `bridged: false`. If the module wants both, human-insiders.md is a legitimate optional warm-up (it is the roster of who can know what that this case is built out of), but it should then be labelled as extra practice, not as the section's exercise.

**In XLab:** <VerificationExercise id="human-insiders" /> in human-insiders.mdx, optional, inside <Fold label="Optional: Insider Report (8–10 minutes)">

**Learner time:** 8 to 10 minutes

The learner writes one case in which an insider's report about a prohibited AI activity is accurate, the insider is legally permitted to report it, and the verification regime still cannot turn the report into actionable evidence, filling four boxes (Insider, Information, Reporting route, Failure point) to a total of 100 to 180 words. While drafting, a desk-check panel re-runs XLab's rule checks on every keystroke: empty boxes, word count against the range, a failure point that rests on lying, on reporting being forbidden or on the verifier ignoring it (all three ruled out by the brief), a failure point with no mechanism word in it, information that never says how the insider knows, and a failure point that shares no substantive word with the rest of the case. A steelman deck deals one of eight challenge questions, never the same card twice in a row. Submit the case freezes the four boxes and only then reveals the five-point marking key the learner ticks against their own answer, the five "Check your case" questions, the four failure categories that do not count and the five that do, and two contrasting worked cases. Under Lens, a Score my case button sends the four boxes to the AI assessor with the same marking key.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Curriculum text is verbatim from `xlab-tracks/src/lib/verification/data/construct-case.ts` (conditions, field labels, word bounds, checklist, excluded list, failure modes, both worked cases), `data/steelman-decks.ts` (CASE_DECK, 8 cards), `data/marking-keys.ts` (CONSTRUCT_CASE_KEY, 5 criteria plus 3 no-credit lines) and the desk-check messages in `src/lib/verification/case-checks.ts`. Chrome strings come from `widgets/construct-case.tsx`, `kit/constructed-response.tsx`, `kit/steelman-deck.tsx` and `kit/marking-key.tsx`. `SCRATCH/fid_cc_pqc.py` checks each authored string against the widget on a letters-and-digits normalisation (so an em-dash rewrite cannot hide a changed word or number): 55/55 data strings, 8/8 deck cards, 11/11 marking-key strings, 20/20 desk-check fragments, 0 missing.
- Em dashes rewritten (the only rewrite made): five in the desk-check messages and the marking key became a comma or a colon; the one in deck card 2, before "and say why it did not", became a comma; the checklist bullets' decorative em dash became an en dash rule marker.
- One wording change beyond the dash rule, deliberate: XLab's marking-key footer reads "This score is yours." The widget reads "This self-marked score is yours." because the widget adds an AI assessor score next to it, which IS sent somewhere; leaving the sentence unqualified would have been false. The rest of the sentence is verbatim.
- Added, not in XLab: `Lens.submit` with `item: "case"`, the question built from XLab's three conditions and four field labels, the answer as the four labelled boxes, and `assessmentInstructions` built from CONSTRUCT_CASE_KEY (all five criteria with their points, grounds and the needs-reasoning note, plus the three no-credit lines) with the score reported as points times 20. `feedbackInstructions` is XLab's own CASE_CHECKLIST. `Lens.requestFeedback` is offered after a score. The brief asks for submit where a marking key exists; XLab itself grades nothing here and says so.
- `Lens.complete()` fires once, on Submit the case, which is XLab's `onSubmit` -> `onComplete` condition (guarded by the same fired-once rule XLab uses via `useRef(initialCompleted)`). Start over does not re-fire it. XLab lists this exercise `bridged: false`, so XLab itself records no completion; the Lens segment should be embedded without `required:: true`, matching XLab's optional Fold.
- No shuffle: there are no options to shuffle. Nothing is keyed on position.
- Icons dropped (XLab uses coloured severity dots): the desk checks use a marked glyph plus an aria-label (passes / warning / fails) so the state reads without colour. The marking key ticks show "✓ credited".
- State: `{values, submitted, ticked}` saved on every keystroke, tick and score. Restore prunes unknown field ids, refuses `submitted` unless all four boxes have text, and drops out-of-range tick indices. XLab persisted the same shape in two localStorage keys; here it is one Lens state blob. Standalone fallback: localStorage key `lens-widget-construct-case`.
- Bug fixed while verifying: the file as handed over crashed on Submit (`panel("Marking key", "")` created no `.aside` node, then `querySelector(".aside").textContent = ...` threw on null), so the reveal never rendered and `complete()` never fired. The score line is now passed into the panel head directly.
:::

#### Widget
source:: [[../widgets/construct-case]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-human-reporting-protection]]

Three slots, and two of them have two candidates each. Four Levers is unchanged. For the On Paper slot XLab retired On Paper and now runs the Policy Quick Check (2026-08-14). For the Companies A and B slot XLab runs Policy on Paper; the decision lab the Lens page reproduces was never registered. Pick one per slot.

#### Text
content::
\#### Four Levers, One Each (whistleblower-levers)

**Decision: widget.** It is a one-to-one matching exercise (placing a chip on one row takes it off any other row) with commit-then-reveal per row; Lens Choice segments cannot enforce the one-each constraint, cannot reveal the effect text on commit, and the four Choice segments on the page today carry the correct option in row order (first option for row 1, second for row 2, and so on), which is exactly the diagonal XLab's CLAUDE.md warns about.

**Target lens:** [[../Lenses/XLab Verification - v-human-reporting-protection]]

**Where it goes:** after the Text segment that ends with the heading "\## Mechanism to Effect" and the lead paragraph "The sources you have read so far describe four main buckets of mechanisms to protect whistleblowers." (the widget repeats that lead, so the paragraph can be dropped from the Text segment or kept; either reads fine). The widget sits before the Text segment that starts "Sources: [Wasil et al.]..., [SB 53, Business and Professions Code §22757.13(c)]... and [ACM Code of Ethics §1.2]" followed by "\## After the Report Arrives".

**What it replaces:** the four `#### Question: Choice` segments (ids 3cfd8e7c, d71082ba, b3794742, 24b15fb6; one per mechanism, same four options each, no `shuffle::`) and the collapsed callout "What each lever changes (open after you have answered)". Both should go entirely: the widget shows every effect line after Commit, and leaving the Choice segments would keep the diagonal-solvable version on the page next to the fixed one. Keep the "Sources:" line and the "\## After the Report Arrives" heading.

**In XLab:** <VerificationExercise id="whistleblower-levers" /> in human-reporting-protection.mdx under "## Mechanism to Effect", core, not inside a Fold.

**Learner time:** 3 to 5 minutes

Reads four mechanism cards (anti-retaliation protection, financial reward, mandatory reporting, professional duty), each with its source quotation and a citation link. Under each card the same four leverage chips appear in a seeded order; the learner presses one chip per card, and a chip already used on another card moves to the new card. When all four are placed, Commit unlocks; after Commit every card shows "You matched this one" or "You put it elsewhere" plus what the course says that lever changes, with Start over available.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All lever names, source lines, citation labels and hrefs, chip labels, effect lines and the lead paragraph are verbatim from `xlab-tracks/src/lib/verification/data/whistleblower-levers.ts` (current HEAD). Status strings and verdict labels come from `src/components/verification/widgets/whistleblower-levers.tsx`; the one em dash in the status line "All four placed, commit to see what each one changes." (an em dash after "placed" in XLab) became a comma, and the em dash prefix XLab prints before the citation label was dropped (the label is a link on its own line).
- Chip order is XLab's own: the FNV-1a + mulberry32 + Fisher-Yates shuffle from `src/lib/shuffle.ts` was ported and seeded with "whistleblower-levers"; the resulting order (the reporter's incentives, a duty on the developer, escalation as professional conduct, a legal right and remedies) was checked against the TypeScript original run under Node. The same order is used on every row, as in XLab; the one-each rule is what makes the exercise a matching.
- XLab never records completion for this widget (registry entry `bridged: false`, the component ignores `onComplete`). The Lens port calls `Lens.complete()` on Commit, the exercise's own finish condition; it is not called again after Start over if the widget was already completed.
- State saved: `{placed, committed}`; restored state is pruned to known lever ids, and `committed` is only honoured when all four rows are placed. Standalone fallback uses localStorage key `v-whistleblower-levers:v1` (XLab's key).
- Nothing graded in writing, so no `Lens.submit`; no XLab "discuss" moment, so no `promptTutor`.
- Nothing dropped.
:::

#### Widget
source:: [[../widgets/whistleblower-levers]]

#### Text
content::
\#### On Paper (human-reporting-protection)

**Decision: widget.** XLab's exercise is an assembly: a bank of twelve statements (half decoys) that the learner picks up and places onto six route links, a Check that marks each link and lets wrong ones be taken back, then an assembled finding per case and a closing view; twelve Choice segments with collapsed callouts cannot do the pick-and-place, the "half belong to none" bank, or the check-and-retry loop.

**Target lens:** [[../Lenses/XLab Verification - v-human-reporting-protection]]

**Where it goes:** after the `#### Article` segment for `cigie-quality-standards-for-investigations` (from "## QUALITY STANDARDS FOR INVESTIGATIONS QUALITATIVE STANDARDS" to "Adequate controls over electronic case files"), directly under the Text segment that begins "\## On Paper". The widget must come before the Text segment that begins "\## Companies A and B (15–20 min)" and "\### Audit the verifier", which belongs to the human-institutions-judgment widget (another agent); nothing from that segment onward is touched.

**What it replaces:** everything between "\## On Paper" and "\## Companies A and B": the collapsed callout "Optional: On Paper (7–10 minutes)" (with the stale "five fragments of internal whistleblower policies" text and the "Follow the report." paragraph), the two case headings and scenario paragraphs, twelve `#### Question: Choice` segments (a7a790b9, e47dea79, 025504ef, 045982de, 22ef0a95, cd58e552, b934f477, 77d2e956, 0ff05bf4, 43251f68, 3d91138b, d76b2f9b), twelve "Why (open after you have answered)" callouts, the two "Case N finding" callouts and the "Two different thresholds" callout. All of it should go: the widget contains every scenario, explanation, source link, finding line, case finding and the thresholds text. Keep a short Text segment with the "\## On Paper" heading and one line saying the exercise is optional (7 to 10 minutes), then the `#### Widget` segment without `required:: true` (XLab keeps it inside an optional Fold). The reviewer comment on the old callout about XLab's stale "five fragments" copy still applies to XLab's MDX and can be reported upstream; the widget does not use that text.

**In XLab:** <VerificationExercise id="human-reporting-protection" /> in human-reporting-protection.mdx, optional, inside `<Fold label="Optional: On Paper (7–10 minutes)">`.

**Learner time:** 7 to 10 minutes (XLab's Fold label)

Case 1 presents Nadia, a frontier-developer safety engineer reporting a biological-risk deployment straight to the California Attorney General under a broad NDA; the route has six links (Person, Subject, Recipient, Identity protection, NDA and remedy, Competent investigator). The learner presses a statement in the bank of twelve, then presses an empty link to place it (or presses a placed statement to take it back), and presses Check the route once all six are filled: wrong links are marked "Does not hold." with XLab's retry hint, right links show the explanation and a source link. When every link holds, Assemble finding shows the case finding and the six finding lines; Continue to evidence opens Case 2 (a cooling contractor's work order for Project Lattice, links Preserve, Authenticate, Investigate, Corroborate, Package, Pass on). Record both findings shows the closing "Two different thresholds" view with the protection and evidence findings and a Review both routes button.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Every scenario, label, statement, retry hint, explanation, source label and href, finding line, result title, result text, break label, the final two findings, phase rail labels, lede and button labels are verbatim from `xlab-tracks/src/lib/verification/data/human-reporting-protection.ts` and `src/components/verification/widgets/human-reporting-protection.tsx` (current HEAD); a script imported the TypeScript data and confirmed 119 of 119 strings appear unchanged in the widget. The engine `src/lib/verification/engines/human-reporting-protection.ts` is a one-line answer check, ported as `isRight`.
- The bank mirrors XLab exactly: for each step the correct statement plus the first decoy in the data (`statementBank` in the component), sorted by statement id. The other three decoys per step and each step's `prompt` string exist in the data file but XLab's widget never shows them; they are omitted here too (the Lens Choice segments being replaced did show all five options, so the page loses those extra distractors; the pick-and-place format needs the 6 + 6 bank).
- Bank order is XLab's sort by statement id (ids are never visible), not a shuffle; it puts no correct statement in a position tied to its link. Placement is hold-and-place with buttons instead of drag, as in XLab (`held` state), which also works on a phone.
- Em dashes: none in the data. The ellipsis and en dashes ("§1107.1(f)–(i)") are kept as written. Icons (lucide) were replaced by text marks: a check mark on past phases and holding statements, a shield or document glyph on the assembled finding.
- Completion mirrors XLab's `onComplete`: `Lens.complete()` fires once when Record both findings is pressed on Case 2; Review both routes restarts without calling it again. XLab's registry marks the widget `bridged: false`, so XLab itself never recorded this completion; the segment should stay optional (no `required:: true`).
- State saved on every placement, check, case change and restart: `{caseIndex, placed, checked, showCaseResult, finished}`; the held-but-unplaced statement is transient and not saved. Restore prunes unknown ids, enforces one statement per link, and only honours `checked` when the route is full and `showCaseResult` when the route is fully right. XLab had no persistence for this widget (React state only), so this is an addition. Standalone fallback: localStorage key `v-human-reporting-protection:v1`.
- Nothing written or graded, so no `Lens.submit`; no XLab "discuss" moment, so no `promptTutor`.
:::

#### Widget
source:: [[../widgets/human-reporting-protection]]

#### Text
content::
\#### On Paper / Policy Quick Check (human-reporting-protection, component policy-quick-check)

**Decision: widget.** Five commit-then-reveal questions marked as one block: nothing is graded until all five are answered, and each then opens an explanation and a source line. Lens Choice segments mark one question at a time and have no explanation reveal, so five of them would give the answer to question 1 away before question 2 is read.

**Target lens:** [[../Lenses/XLab Verification - v-human-reporting-protection]]

**Where it goes:** replaces the collapsed callout that begins "Below are five fragments of internal whistleblower policies. Each fragment is", directly under the Text segment whose content is "\## On Paper", which follows the `#### Article` segment for `cigie-quality-standards-for-investigations`.

**What it replaces:** everything between "\## On Paper" and "\## Companies A and B": the "Optional: On Paper (7–10 minutes)" callout, the two case headings and scenario paragraphs, the twelve `#### Question: Choice` segments (a7a790b9, e47dea79, 025504ef, 045982de, 22ef0a95, cd58e552, b934f477, 77d2e956, 0ff05bf4, 43251f68, 3d91138b, d76b2f9b), their twelve "Why (open after you have answered)" callouts, the two "Case N finding" callouts and the "Two different thresholds" callout. That block is a port of XLab's retired route-reconstruction widget and is not what a learner meets at this spot on the live site. Keep a short Text segment carrying the "\## On Paper" heading and the "optional, 7 to 10 minutes" line, then the `#### Widget` segment with no `required:: true` (XLab folds it as optional). NOTE FOR THE ORCHESTRATOR: same placement as widgets/human-reporting-protection.md (the older exercise, ported by another agent); only one belongs here. XLab REPLACED, it did not add: commit 0b0a767c (2026-08-14, "2.4: the final architecture") swapped `"human-reporting-protection": PolicyCritique` for `"human-reporting-protection": PolicyQuickCheck` in the registry, kept the exercise id so the lesson mapping and progress key did not move, retitled the exercise from "Policy on Paper" to "On Paper", cut the Fold's estimate from 12 to 15 minutes down to 5 to 7, and left the replaced widget in the repo unmounted. Its reason: 2.4 needed "one fast block" of multiple choice and nothing else in the section is one. (The Lens page's route-reconstruction content is a port of `human-reporting-protection.tsx`, which the same commit comment records as also unmounted.)

**In XLab:** <VerificationExercise id="human-reporting-protection" /> in human-reporting-protection.mdx, optional, inside <Fold label="Optional: On Paper (7–10 minutes)">

**Learner time:** 7 to 10 minutes (XLab's Fold label; the exercise registry estimates 5 to 7)

Five fact patterns, each with one question and four options in a fixed order. Three give the facts as a bulleted list (four employees of a frontier developer and whose disclosure §1107.1(a) protects; an internal reporting process that still sends the quarterly disclosure to the director it accuses; a proposed law and which amendment package matches the AIWI/CARMA Best Practice Guide) and two as a paragraph (a duty-speech concern with mixed motives that is later unsubstantiated; an investigator holding screenshots, two witnesses and a legal-team summary under the CIGIE standards). Picks can be changed freely and nothing is marked until all five are answered and Check all five is pressed. Then every question shows Correct or Not quite, the correct option is marked whether or not it was chosen, XLab's explanation and source line appear, and the counter turns from "n of 5 answered" into the score. Start over clears the set.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Every fragment, fact bullet, stem, option, explanation and source line is verbatim from `xlab-tracks/src/lib/verification/data/policy-quick-check.ts`; the lede is XLab's own Fold copy from `src/content/lessons/verification/human-reporting-protection.mdx`. Chrome strings ("Question n/5", "Correct", "Not quite", "Check all five", "Start over", "Source: ", "n of 5 answered.") come from `widgets/policy-quick-check.tsx` and `kit/choice-list.tsx`. `SCRATCH/fid_cc_pqc.py` confirms 63/63 authored strings present, 0 missing.
- Em dashes rewritten (the only rewrite made): three. In question 2's explanation the pair around "not immediate" became commas; in question 4's explanation the one after the quoted phrase "duty speech" became a comma; in question 5's source line the one after "(2025)" became a colon. The en dash in "§1107.1(e)(1)–(2)" is kept as written.
- Shuffle: XLab's `shuffleAnswerOptions` from `src/lib/shuffle.ts` (FNV-1a seed, mulberry32, back-to-front Fisher-Yates, terminal-option pinning, true/false pass-through) is ported line for line and seeded on the question id, so the widget shows XLab's live order rather than the authored order. Verified by running XLab's own `shuffle.ts` against its own data file: display orders b,a,d,c / b,d,a,c / c,a,d,b / b,d,a,c / d,c,b,a, correct answer in slots 1,3,3,3,2 (0-based), which is exactly what the widget renders. Same order for every learner and every visit; nothing is keyed on position and no visible text names an option by letter. Three of the five answers land in slot D, which is XLab's order, not a choice made here; changing it would put Lens out of step with XLab's page and its facilitator keys.
- Added, not in XLab: `Lens.complete()` on Check all five. XLab's `PolicyQuickCheck` takes no `onComplete` at all (it destructures an empty props object) and the exercise is registered `bridged: false`, so XLab records no completion for it. Checking the set is the exercise's own finish condition; embed the segment without `required:: true` so it gates nothing, as in XLab's optional Fold.
- Nothing is written or graded here, so no `Lens.submit`; XLab has no discuss moment, so no `promptTutor`.
- lucide icons dropped: the verdict uses a check or cross glyph plus the words Correct / Not quite, and each option carries a glyph and a "your answer" / "correct answer" / "your answer, correct" tag, so every state reads without colour.
- State: `{picks, submitted}` saved on every pick, on the check and on the restart. Restore drops picks whose option id is not in the question and refuses `submitted` unless all five questions have a valid pick, so a tampered state cannot open the explanations. XLab persisted the same shape under `v-policy-quick-check:v2`; standalone fallback here is localStorage key `lens-widget-policy-quick-check`.
- The tutor summary names the option the learner picked on each question and, only after the check, whether it was right and what the answer was, so the answers do not leak to the tutor before the learner commits.
:::

#### Widget
source:: [[../widgets/policy-quick-check]]

#### Text
content::
\#### Companies A and B (human-institutions-judgment)

**Decision: widget.** Fourteen commit-then-reveal decisions with a retry hint on a wrong line, a gated "next decision" on the supported line, a phase rail and an assembled record: the Lens page today has fourteen required Choice segments with no reveal and fourteen collapsed Why callouts the learner can open before answering.

**Target lens:** [[../Lenses/XLab Verification - v-human-reporting-protection]]

**Where it goes:** after the "## Companies A and B (15–20 min)" heading, replacing from "### Audit the verifier" onward

**What it replaces:** the "### Audit the verifier" sub-heading with its instruction paragraph, the blue "The International AI Verification Office" callout, the four "### Institution / Capture / Evidence boundary / Response" sub-headings, the fourteen Choice segments (ids bdaba121 … 95098595), the fourteen "Why (open after you have answered)" callouts and the "Institutional assessment and response record" callout. All of it is inside the widget (title, instruction, case file, prompts, contexts, options, retry hints, explanations, source links, finding lines), so it should go entirely. The "## Companies A and B (15–20 min)" heading and the Works cited callout stay.

**In XLab:** <VerificationExercise id="human-institutions-judgment" /> in human-reporting-protection.mdx under "## Companies A and B (15–20 min)", core (not in a Fold), bridged: true in the exercise registry

**Learner time:** 15 to 20 minutes

The case file (the International AI Verification Office examining Project Lattice) stays on screen while the learner works through fourteen decisions in four phases: whether the Office is independent, competent, accountable, authorised and has real access; which fact is financial, informational, cultural or political capture; what the human record establishes and what still needs technical evidence; and which threshold supports investigation, a compliance finding and enforcement. For each decision they pick one of four lines and press "Commit line". A wrong line shows "Not supported by this record." with the retry hint and they choose again; the supported line shows "Added to the file" with the explanation and a source link, and "Next decision" appears. After the fourteenth decision "Assemble file" shows the completed "Institutional assessment and response record" with all fourteen finding lines by phase, and "Rebuild file" restarts.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data is inlined mechanically from `xlab-tracks/src/lib/verification/data/human-policy-labs.ts` (INSTITUTIONS_JUDGMENT_LAB, HEAD) by evaluating the TS file, so every string is verbatim; a build-time check confirms all 376 quoted strings and all source URLs from the data file appear in the two widgets. Engine ported from `src/components/verification/widgets/human-policy-decision-lab.tsx` and `src/lib/verification/engines/human-policy-labs.ts`; the two widgets share one template (`build-hpl/template.html`) and differ only in the LAB data, uuid, title and summary.
- Em dashes replaced (only rewrite): "A council[em dash]not the Office[em dash]has authority" to "A council (not the Office) has authority"; "intent[em dash]not automatic proof" to "intent, not automatic proof"; "response[em dash]not suspicion alone" to "response, not suspicion alone".
- Adaptation: XLab renders the four lines in authored order and the supported line is first in all fourteen steps. The widget shuffles with a port of XLab's `src/lib/shuffle.ts` seeded on `lab.id:step.id`; supported-line positions come out as 1,1,3,0,2,1,1,1,2,0,2,3,3,0. Letters A to D are display markers only.
- Addition over XLab: `Lens.submit` on the first commit of each decision (item = step id, question = label + context + prompt, answer = the chosen line, assessment instructions = "100 only for the supported line" plus XLab's explanation, feedback instructions = XLab's retry + explanation). Later commits on the same decision are not submitted; the score is not displayed. The saved state counts unsupported commits per decision for the tutor summary; XLab keeps no such count.
- Source links use XLab's hrefs verbatim (arXiv HTML for Brundage, Wasil and Baker; OPCW Part X). The sibling audits lens repointed Brundage to the PDF; this lens did not, so nothing to reconcile here.
- XLab's lucide icons are replaced by text glyphs (✓, ↗, ↻).
- Completion mirrors XLab's `onComplete`: fired once when the last decision is continued into the assembled record; "Rebuild file" does not re-fire it. Standalone the state falls back to `localStorage` key `xlab-human-institutions-judgment:v1`.
- Kept verbatim although known stale (already flagged on the Lens page): the eyebrow reads "Institutions and policy judgment · 2.4.4" while the exercise sits in lesson 2.4.2, and the XLab heading "Companies A and B" does not describe this lab.
- Origin: the older `companies-ab.tsx` + `data/companies-ab.ts` (two company feature lists, two free-text differences, the Right to Warn letter with two questions, a marking key) is the exercise the heading names; it is not in the registry. At HEAD the registry maps `human-institutions-judgment` to `PolicyOnPaper` (`policy-on-paper.tsx`: provenance tagging of Anthropic/OpenAI policy statements, the Right to Warn demands, two workspace questions), not to this decision lab; the `HumanInstitutionsJudgment` wrapper exists but is unregistered. The Lens page was built from INSTITUTIONS_JUDGMENT_LAB and this widget ports that lab as assigned. Neither CompaniesAB nor PolicyOnPaper is ported here; if the orchestrator wants the exercise the heading actually names, that is a separate widget (PolicyOnPaper would be WIDGET: 12 statements tagged with one of five provenance kinds, commit per tab, reveal with notes).
:::

#### Widget
source:: [[../widgets/human-institutions-judgment]]

#### Text
content::
\#### Companies A and B (human-institutions-judgment)

**Decision: widget.** Twelve statements tagged with one of five kinds of claim across three tabs, each tab committed on its own and only then revealing the authored kind, what the learner marked where it differs, and XLab's note on why the two are not the same kind of claim; plus a steelman deck, two writing questions and a covered Sources panel that finally names the companies. Commit-then-reveal per tab, with the reveal hidden behind the learner's own commit, is not something Choice segments can do.

**Target lens:** [[../Lenses/XLab Verification - v-human-reporting-protection]]

**Where it goes:** after the "## Companies A and B (15–20 min)" heading, replacing from "### Audit the verifier" onward

**What it replaces:** on the Lens page today that slot holds XLab's older institutions-judgment decision lab, which OUT/widgets/human-institutions-judgment.md already ports: the "### Audit the verifier" sub-heading and its instruction paragraph, the blue "The International AI Verification Office" callout, the four sub-headings, the fourteen Choice segments (bdaba121 to 95098595), their fourteen "Why" callouts and the "Institutional assessment and response record" callout. XLab no longer runs that lab at this id; it runs this exercise, and the section heading "Companies A and B" is this exercise's title. So the two widgets are alternatives for one slot and the orchestrator has to choose. If this one ships, all of the "Audit the verifier" material goes entirely and the heading stops lying (the Lens page's own CriticMarkup note "XLab's heading says Companies A and B, but the widget it wraps is the Audit the verifier lab" can be resolved and deleted); the "## Companies A and B (15–20 min)" heading and the Works cited callout stay. The Works cited callout will need the four sources this widget links (the Anthropic RSP noncompliance policy PDF, the FLI AI Safety Index Summer 2026, the OpenAI Files "Transparency and Safety", the CNBC retraction memo story and righttowarn.ai) rather than the lab's Brundage, Wasil and OPCW entries.

**In XLab:** <VerificationExercise id="human-institutions-judgment" /> in human-reporting-protection.mdx under "## Companies A and B (15–20 min)", core (not in a Fold), bridged: true in the exercise registry

**Learner time:** 15 to 20 minutes

Three tabs. On Company A the learner reads six statements drawn from one published noncompliance-reporting and anti-retaliation policy plus one outside index grade, and marks each as a Published rule, a Company self-report, Documented prior practice, an External assessment, or Not established; Company B is six statements of documented practice, an index grade and the 2024 retraction. Commit is locked until every statement on the tab carries a mark, and committing reveals the authored kind row by row, names the learner's mark where the two differ, and opens XLab's note on the rows that turn on the distinction (that a channel is permitted is a rule the company wrote; that the company cannot unmask a user of it is an assertion about its own systems). The third tab lists the four Right to Warn demands and asks, in writing, what satisfying them would change structurally. When all three tabs are committed the exercise is complete. Below sit the steelman deck, the two writing questions (what incentives these rules create; what further evidence would show the institution is independent, competent and usable) and a covered Sources panel that reveals A is Anthropic, B is OpenAI, and the letter, with links.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data inlined mechanically from `xlab-tracks/src/lib/verification/data/policy-on-paper.ts` and `data/steelman-decks.ts` (INSTITUTION_DECK) at HEAD, by evaluating the TS files in the generator (`SCRATCH/build-sc/policy-on-paper.mjs`), so every string, kind and URL is verbatim. `SCRATCH/build-sc/fidelity.mjs` re-checks the built file against the data: 96 strings, 3 missing, all three by design (below).
- Engine ported from `src/components/verification/widgets/policy-on-paper.tsx`, with `kit/question-workspace.tsx` (rule `{kind: "any", count: 2}`), `kit/spoiler.tsx` and `kit/steelman-deck.tsx`.
- Dropped, because XLab drops them too: the three `kicker` strings ("Publishes a detailed reporting policy.", "As it was documented.", "What the employees themselves asked for."). They are authored in the data file but `PolicyOnPaper` never renders them; its tab list shows only the label. The `POLICY_GROUPS` labels (Published process, Documented context, Still unverified) are likewise never rendered by XLab: the groups only order the rows, and that order is already the authored order of the statements array, so the port renders the array directly and the result is row-for-row identical.
- Em dashes replaced (the only rewrite), all fourteen in the data plus three in the kit copy: the FLI citation "AI Safety Index, Summer 2026" to "AI Safety Index, Summer 2026"; the OpenAI Files citation "“Transparency and Safety”, collecting" to "“Transparency and Safety”, collecting"; A's index row "governance and accountability, a B, against" to "governance and accountability: a B, against"; A's informal-conversation note "on the employee, file it yourself" to "on the employee: file it yourself"; A's usage note "governance here, protection, track record, policy quality, policy transparency, and none" to "governance here (protection, track record, policy quality, policy transparency), and none"; B's NDA row "covered by an NDA, admitting" to "covered by an NDA: admitting"; B's SEC note "ten minutes on, evidence of a claim is not evidence that the claim is true, so the row" to "ten minutes on (evidence of a claim is not evidence that the claim is true), so the row"; B's index row "governance and accountability, second of the nine it assessed, behind a single B, and none" to "(second of the nine it assessed, behind a single B), and none"; B's index note "part of the row, four recommendations" to "part of the row: four recommendations"; B's retraction note "not strictness, and the retraction" to "not strictness, and the retraction"; the letter's realNote "Google DeepMind, seven named, six anonymous, and endorsed" to "Google DeepMind (seven named, six anonymous), and endorsed"; the task lead "two organizations,A and B,where" to "two organizations, A and B, where"; two INSTITUTION_DECK cards, "faces it, the reporter, their manager, or the company?" to "faces it: the reporter…" and "in reply, and is it wrong?" to "in reply, and is it wrong?". In the kit copy: the reveal line ", you marked X" to ", you marked X", the workspace "Keep editing if you want, it stays saved." to "…if you want; it stays saved.", and the Sources panel's "Company A, Anthropic" to "Company A: Anthropic".
- No shuffle, deliberately. The five kinds are a fixed legend offered identically on every row, not per-item options, so there is no authored order that leaks anything: the correct kind varies row to row (A is rule, self-report, rule, rule, external assessment, not established; B is four practice rows, an external assessment and a self-report) and the statement order is XLab's own. Reordering the five buttons per row would only make the exercise harder to scan.
- No `Lens.submit`. XLab grades nothing in this exercise: the tab commits are self-checked against the authored kind, the workspace placeholder says "Answer as you go. Nothing is graded.", and the demands question has no rubric. The `COMPANIES_AB_KEY` marking key in `data/marking-keys.ts` belongs to `companies-ab.tsx`, the unmounted predecessor, not to this exercise, so it is not used here. No `promptTutor` either: XLab has no discuss or get-feedback moment on this page.
- The five `PROVENANCE` hints ("written down in a policy the company published", and so on) are XLab's data but XLab does not display them; the port carries each one as the `title` tooltip on its button, so a desktop learner can hover for it and nobody is shown the definition before they choose. If that is unwanted, they are the `hint` fields in the inlined DATA object.
- The eyebrow "Exercise, 15 to 20 minutes" comes from the lesson heading "## Companies A and B (15–20 min)".
- Completion mirrors XLab's `onComplete`: all three tabs committed. Fixed in this pass: XLab fires it from an effect, so a state that is already finished but was never marked complete completes on load; the port set its own flag on restore without calling `Lens.complete()`. It now calls the same guarded path on restore, so that state completes once, as in XLab.
- Restored state is sanitised: a committed company tab whose statements are not all marked is dropped, a committed demands tab with an empty answer is dropped, unknown kinds and unknown tab ids are discarded, and the widget opens on the first tab still uncommitted.
- Standalone (no `window.Lens`) the state falls back to `localStorage` key `xlab-policy-on-paper:v1`.
- Registry history: `git log --oneline -- src/components/verification/widgets/registry.tsx` gives four commits (a307b67a, 1e8b150e, e8397d0c, d53b4e17). `git log -S'"human-institutions-judgment": PolicyOnPaper'` pins the mapping to e8397d0c "Verification!" (Thu 20 Aug 2026), the squashed commit that created the whole verification track; before it the registry had no `human-*` ids and there were no verification lessons. XLab **replaced**, it did not add: e8397d0c's own comment on the PolicyOnPaper entry reads "2.4.4's exercise is now Build the Institution; the id stays so the lesson mapping, the progress key and the finish event do not move. 2.4.4 is the recovered exercise: two real companies read from their own documents, then the letter." It goes on to say that companies-ab.tsx, the same comparison on generic feature lists, stays in the repo unmounted. 1e8b150e ("Remove Verification source comments") deleted that comment, which is why HEAD reads as a bare mapping. `companies-ab.tsx`, `human-institutions-judgment.tsx` and `human-policy-decision-lab.tsx` are all still in the repo and all still unregistered.
:::

#### Widget
source:: [[../widgets/policy-on-paper]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-human-audits-inspections]]

Two candidates for one slot. XLab now runs Same Claim, Different Circumstances under the Four Sources exercise id; the decision lab the Lens page reproduces was never registered. Pick one.

#### Text
content::
\#### Four Sources (human-audits-inspections)

**Decision: widget.** Ten commit-then-reveal decisions with a retry hint on a wrong line, a gated "next decision" on the supported line, a phase rail and an assembled finding file: the Lens page today has ten Choice segments with no reveal and ten collapsed Why callouts the learner can open before answering.

**Target lens:** [[../Lenses/XLab Verification - v-human-audits-inspections]]

**Where it goes:** after the callout "Optional: Four Sources (12–15 minutes)" that carries the "Build the inspection order" and "Project Lattice" paragraphs (the "## Four Sources" heading)

**What it replaces:** the four "### Purpose / Access ceiling / Mandate / Managed access" sub-headings, the ten optional Choice segments (ids fab7d7aa … 981821e8), the ten "Why (open after you have answered)" callouts and the "Inspection order and bounded finding" callout. All of that is inside the widget now (case file, prompts, contexts, options, retry hints, explanations, source links, finding lines), so it should go entirely; the intro callout above it can stay as the section lead. The Works cited callout stays.

**In XLab:** <VerificationExercise id="human-audits-inspections" /> in human-audits-inspections.mdx, optional, inside <Fold label="Optional: Four Sources (12–15 minutes)">

**Learner time:** 12 to 15 minutes

The case file (Project Lattice) stays on screen while the learner works through ten decisions in four phases: which job belongs to an audit, a routine inspection and a challenge inspection; what an auditor may conclude from black-box, gray-box and deep access; which mandate clauses give scope, preservation and a refusal consequence; and which managed-access arrangement keeps the verification question answerable. For each decision they pick one of four lines and press "Commit line". A wrong line shows "Not supported by this record." with the retry hint and they choose again; the supported line shows "Added to the file" with the explanation and a source link, and "Next decision" appears. After the tenth decision "Assemble file" shows the completed "Inspection order and bounded finding" with all ten finding lines by phase, and a "Rebuild file" button restarts.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data is inlined mechanically from `xlab-tracks/src/lib/verification/data/human-policy-labs.ts` (AUDITS_INSPECTIONS_LAB, HEAD) by evaluating the TS file, so every string is verbatim; a build-time check confirms all 376 quoted strings and all source URLs from the data file appear in the two widgets. Engine ported from `src/components/verification/widgets/human-policy-decision-lab.tsx` and `src/lib/verification/engines/human-policy-labs.ts` (answer check is `answerId === step.answerId`).
- Em dashes replaced (only rewrite): "add[em dash]and what limit remains?" to "add, and what limit remains?"; "use[em dash]but preserve" to "use, but preserve".
- Adaptation: XLab renders the four lines in authored order and the supported line is first in every one of the ten steps (also the case for the Lens Choice segments, which set `shuffle:: true` for that reason). The widget shuffles with a port of XLab's `src/lib/shuffle.ts` seeded on `lab.id:step.id`; supported-line positions across the ten steps come out as 2,3,3,1,2,2,1,1,2,1. Letters A to D are display markers only; no text refers to them.
- Addition over XLab: `Lens.submit` on the first commit of each decision (item = step id, question = label + context + prompt, answer = the chosen line, assessment instructions = "100 only for the supported line" plus XLab's explanation, feedback instructions = XLab's retry + explanation, the same pairing the Lens Choice segments use). Later commits on the same decision are not submitted. The score is not shown in the widget (the reveal already says whether the line is supported). The saved state also counts unsupported commits per decision so the tutor summary can name them; XLab keeps no such count.
- Source links use XLab's hrefs (arXiv HTML anchors for Brundage). The Lens page deliberately repointed its Brundage links to the PDF (`#page=25/29/30`) because the arXiv HTML render is truncated mid-§5.3.3; if that should carry over, the three `sourceHref` values for black-box, gray-box and deep-access steps need the same swap in the widget's LAB data (they are plain strings near the top of the script).
- XLab's lucide icons (check, file-check, rotate, external-link) are replaced by text glyphs (✓, ↗, ↻).
- Completion mirrors XLab's `onComplete`: fired once when the last decision is continued into the assembled file; "Rebuild file" does not re-fire it. Standalone (no `window.Lens`) the state falls back to `localStorage` key `xlab-human-audits-inspections:v1`.
- The eyebrow "Audits and inspections · 2.4.3" is XLab's own numbering and is kept verbatim.
- Note for XLab: the tracks registry at HEAD maps `human-audits-inspections` to `SameClaim` (the "Four Sources" writing exercise about Project Cedar in `same-claim.tsx`), not to this decision lab; the `HumanAuditsInspections` wrapper exists but is not registered. The Lens page was built from AUDITS_INSPECTIONS_LAB, and this widget ports that lab as assigned. The SameClaim exercise (four source variants, written analyses, a 50-word comparison, a marking key) is not ported here.
:::

#### Widget
source:: [[../widgets/human-audits-inspections]]

#### Text
content::
\#### Four Sources (human-audits-inspections)

**Decision: widget.** Four written analyses that stay editable until one Submit freezes all four at once and only then opens the after-submission block (self-check, the marking key the learner ticks against their own answers, a 50-word comparison with a live counter, an optional transfer question), plus a steelman deck that deals a challenge card: the gating, the freeze and the self-marking are state changes a run of Question segments cannot make.

**Target lens:** [[../Lenses/XLab Verification - v-human-audits-inspections]]

**Where it goes:** after the "## Four Sources" Text segment, whose callout opens "Build the inspection order. A power anomaly has raised a concrete concern."

**What it replaces:** nothing that is on the Lens page today. The Lens page's Four Sources section was built from XLab's older audits-and-inspections decision lab (the ten optional Choice segments fab7d7aa to 981821e8, their ten "Why (open after you have answered)" callouts and the "Inspection order and bounded finding" callout), which OUT/widgets/human-audits-inspections.md already ports. XLab no longer runs that lab at this id; it runs this exercise. So the two widgets are alternatives for the same slot and the orchestrator has to choose: ship this one and the ten Choice segments plus their callouts go entirely (the "Build the inspection order" and "Project Lattice" intro callout goes with them, because this exercise is about Project Cedar and a source-credibility question, not about an inspection order), or ship the lab port and leave this on the shelf. The Works cited callout stays either way. Shipping both in one section would be 25 to 30 minutes on one page.

**In XLab:** <VerificationExercise id="human-audits-inspections" /> in human-audits-inspections.mdx, optional, inside <Fold label="Optional: Four Sources (12–15 minutes)">; exercises.ts titles it "Four Sources", bridged: false

**Learner time:** 12 to 15 minutes

One allegation is fixed at the top of the page: Project Cedar conducted a prohibited training run during the first two weeks of July. Four cards give the same allegation four different provenances (A direct participant, B second-hand source, C circumstantial observer, D documentary source) and the learner writes, for each, what the verification body should do next and what the evidence does not yet establish, drawing challenge cards from the steelman deck while they write. Submit unlocks once all four carry text; pressing it freezes the four answers, fires completion, and sends them to the AI assessor with XLab's own marking key as the assessment instructions. The after-submission block then opens: the two self-check questions, the marking key to tick against their own answers (2 points per case, 8 in all, with the "No credit" list), the 50-word comparison question with a live word counter that flags going over, and the optional transfer question.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data inlined mechanically from `xlab-tracks/src/lib/verification/data/same-claim.ts`, `data/steelman-decks.ts` (CLAIM_DECK) and `data/marking-keys.ts` (SAME_CLAIM_KEY) at HEAD, by evaluating the TS files in the generator (`SCRATCH/build-sc/same-claim.mjs`), so every string is verbatim. `SCRATCH/build-sc/fidelity.mjs` re-checks the built file against the data: 48 of 48 strings present, 0 missing.
- Engine ported from `src/components/verification/widgets/same-claim.tsx`, with `kit/steelman-deck.tsx`, `kit/marking-key.tsx` and `kit/constructed-response.ts` (countWords).
- Em dashes replaced (the only rewrite): key criterion C "is identified, what was observed" to "is identified: what was observed"; criterion D "are named, what it shows" to "are named: what it shows"; no-credit line "its own next step, recommending an inspection" to "its own next step: recommending an inspection"; the marking-key panel's own copy "counts, no criterion needs a particular term" to "counts; no criterion needs a particular term" and "not the point, the reasoning has to be on the page" to "not the point: the reasoning has to be on the page".
- No shuffle, deliberately. Nothing here is a multiple-choice item: the four cases are labelled A to D by XLab itself and the marking key is keyed to those letters, so reordering them would break the key. Position gives nothing away because there is no answer to give away.
- Addition over XLab: `Lens.submit` on the one Submit press (item "analyses", question = the fixed claim plus XLab's intro, task lead, two tasks and the justify line, answer = the four case headings with the learner's analysis under each, assessmentInstructions = XLab's SAME_CLAIM_KEY rendered as a marking scheme, 2 points per criterion scaled to 100, with the "needs reasoning" line, the grounds and the five no-credit lines, feedbackInstructions = XLab's two self-check questions plus "answer case by case, name the criterion each analysis missed, and do not rewrite the analyses"). The score is shown in its own Assessor card, with a "Get feedback on the score" button wired to `Lens.requestFeedback`. XLab grades nothing here, but the brief asks for `submit` where XLab's exercise carries a marking key, and this one does. Nothing else on the page depends on the score, so a failed or slow grade leaves the exercise usable.
- The Assessor card's own copy ("Assessor", "The four analyses were sent for scoring against the marking key below. Practice only; it counts towards nothing.", "Scoring the four analyses…", "Get feedback on the score") is the port's, not XLab's; it exists only because `submit` is the port's addition. Everything else on the page is XLab's.
- The eyebrow "Optional exercise, 12 to 15 minutes" comes from the lesson's Fold label "Optional: Four Sources (12–15 minutes)"; the "Optional:" prefix on the transfer question is XLab's `OptionalPrefix`.
- Completion mirrors XLab's `onComplete`: fired once from the Submit click, never from a restore (XLab fires it in the click handler only, with `fired.current` seeded from `initialCompleted`), and "Start over" does not re-fire it.
- Divergence, deliberate: XLab keeps the marking-key ticks in their own localStorage key, so its "Start over" clears the four answers but leaves the ticks standing. Here the ticks live in the same saved state and "Start over" clears them too. Invisible until a learner resubmits, and the other way round would restore a stale self-score onto fresh answers.
- Fixed in this pass: the assessor `responseId` is now saved, so a restored submitted state shows the "Get feedback on the score" button exactly as the live state does. Before the fix the restored view lost that button (the one failing assertion in the scripted walk).
- Standalone (no `window.Lens`) the state falls back to `localStorage` key `xlab-same-claim:v1`; the score card and feedback button simply never appear.
- Registry history: `git log --oneline -- src/components/verification/widgets/registry.tsx` gives four commits (a307b67a, 1e8b150e, e8397d0c, d53b4e17). `git log -S'"human-audits-inspections": SameClaim'` pins the mapping to e8397d0c "Verification!" (Thu 20 Aug 2026), the squashed commit that created the whole verification track; before it (d53b4e17, 14 Jul 2026) the registry had no `human-*` ids and `src/content/lessons/verification/` did not exist. XLab **replaced**, it did not add: e8397d0c's own comment on the SameClaim entry reads "2.4.3's exercise is now Same Claim, Different Circumstances; the id stays so the lesson mapping, the progress key and the finish event do not move. The decision lab it shared with 2.4.4 remains in the repo, unmounted here." That comment was deleted by 1e8b150e ("Remove Verification source comments"), which is why HEAD's registry reads as a bare mapping. `human-audits-inspections.tsx` and `human-policy-decision-lab.tsx` are still in the repo and still unregistered.
- Worth reporting to XLab, or at least to whoever owns the Lens page: the Lens section is titled "Four Sources" (XLab's own PageBreak and exercise title, which describe this exercise) but its body is the inspection-order lab, which is the exercise XLab retired at that id. The Lens page's existing CriticMarkup note flags the twin of this mismatch on the sibling lens.
:::

#### Widget
source:: [[../widgets/same-claim]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-human-institutions]]

#### Text
content::
\#### The Missing Board (missing-board)

**Decision: native question segments are enough.** XLab's widget is five textareas, a Submit that freezes them and reveals four commentary paragraphs, and a sixth 50-word textarea; XLab grades none of it (no marking key), so a widget would only add a gate on the commentary while losing the per-question AI assessment the six Open segments already give.

**Target lens:** [[../Lenses/XLab Verification - v-human-institutions]]

**Where it goes:** the Text segment beginning "\## Exercise: From Nuclear to AI Inspections In the nuclear regime, the inspection institution" and the six Open segments plus commentary callouts that follow it, ending with the 50-word guideline question `96ee4f8c-1ad4-4b29-904b-5168cddeaf2d`.

**What it replaces:** nothing; the existing port (intro text, four station Open questions with the nuclear parallel in each prompt, the strain Open, four closed commentary callouts, the final 50-word Open) already covers every line of XLab's data and stays as is.

**In XLab:** <VerificationExercise id="missing-board" /> in human-institutions.mdx, core, not inside a Fold

**Learner time:** 20

Writes a few sentences per station (finder, judge, enforcer, standard) in answer to XLab's prompt, each prompt preceded by the nuclear-regime parallel; names the station where the analogy strains hardest; opens the four commentary callouts; then writes a guideline of at most 50 words to bind the AI board to. In XLab the commentary appears only after Submit and the stations freeze; on Lens the callouts are collapsed and labelled "open after you have answered", and each answer gets AI assessment instead.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Checked the six Lens prompts and four callouts word for word against `xlab-tracks/src/lib/verification/data/missing-board.ts` (HEAD, commit 1e8b150): intro, task lead, limit sentence, four station titles, nuclear parallels, prompts, strain prompt, commentary and final question all match. One deliberate edit by the earlier porter: "none of 2.4.4's captures owns it" became a link to the Audit the verifier lens (documented in a CriticMarkup comment on the page).
- Dropped relative to XLab: the Submit gate (commentary hidden until every station and the strain carry an answer), the frozen-after-submit textareas, the "Start over" reset, and the live "n / 50 words" counter on the final question. The 50-word limit is enforced by the assessment instructions instead.
- Not XLab's: the assessment-instructions and feedback-instructions on the six Open segments were written by the earlier porter from XLab's commentary; XLab does not grade this exercise. They are reasonable but are not XLab text.
- Remaining defects on the page: em dashes inside XLab's verbatim copy (finder prompt, judge parallel, enforcer prompt, all four commentary callouts). Fixes below.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

Keep the existing segments and ids. Only replace the em-dash lines with these (content:: values and callout bodies, ready to paste):

Finder prompt (segment `36895df0-f049-478c-807f-f3ca5c5c60af`), second paragraph:
`Who finds for AI, and what access would they need for their facts to hold up later?`

Judge prompt (segment `7d214414-7419-4978-b560-27e224191462`), first paragraph:
`**The judge.** In the nuclear regime: The Board of Governors decides whether the facts constitute noncompliance: a judgment, Carlson insists, not a checklist.`

Enforcer prompt (segment `28b10c14-79cc-4565-94ab-0ff402747fc3`), second paragraph:
`What plays the Security Council’s part for AI, and what would enforcement actually deny a violator?`

Commentary callouts (Text segment after the strain question):
```
:::callout {title="Commentary: The finder (open after you have answered)" tone="neutral" collapse="closed"}
AI has candidate finders, module 2’s evidence streams: chip attestation and logs, cloud records, national technical means, and the human layer this section closed on. What none of them supplies alone is facts that survive challenge: the finder’s access has to be agreed in advance, or every finding arrives with a provenance fight attached.
:::

:::callout {title="Commentary: The judge (open after you have answered)" tone="neutral" collapse="closed"}
This is the station with no tenant. The IAEA Board’s standing took a treaty, a statute and decades of cases; nothing with comparable legitimacy exists for AI, and every candidate (a treaty conference, a new agency, a plurilateral council) trades legitimacy against capture along exactly the lines this section mapped: who funds it, who staffs it, who clears its reports.
:::

:::callout {title="Commentary: The enforcer (open after you have answered)" tone="neutral" collapse="closed"}
There is no Security Council of compute, but AI’s enforcement lever may be more usable than sanctions ever were: the supply chain narrows to a handful of chokepoints, and denial (of chips, of cloud capacity, of interconnect) is enforcement a coalition can actually deliver. The strain is the same as the UNSC’s: the likeliest violators sit inside the coalition that would have to act.
:::

:::callout {title="Commentary: The standard (open after you have answered)" tone="neutral" collapse="closed"}
Carlson’s closing argument transfers whole: a regime that decides case by case, with no announced standard, spends credibility on every decision. Whatever sentence you wrote, the test it must pass is the one his five cases failed: would two rivals, reading it in advance, predict the same verdict on the same facts?
:::
```
:::

#### Text
content::
\#### The Standard of Proof (standard-of-proof)

**Decision: widget.** The learner commits a move and a defence per docket before Submit unlocks the 2x2 reveal and XLab's tickable marking key (criteria, grounds, no-credit list, running score), which the Lens page does not carry at all today and which Choice/Open segments cannot gate.

**Target lens:** [[../Lenses/XLab Verification - v-human-institutions]]

**Where it goes:** after the Text segment beginning "\## The Standard of Proof :::callout {title="Optional: The Standard of Proof (15 minutes)"" (keep that heading; the widget carries the allegation, intro, task list and limit itself, so the callout body can go).

**What it replaces:** everything from the prose "\### Docket A: The lone report" through the transfer Open question `2d4dbddf-2559-4f6a-b6c2-baa0fc1ac5ad`: four docket prose blocks, four ungraded Choice segments, four Open defence segments, the "Self-check" and "The grid" callouts, the 50-word standard Open and the transfer Open. All of it should go entirely; the widget contains every line of it plus the marking key. If a fallback is wanted, keep only the "The grid" callout collapsed.

**In XLab:** <VerificationExercise id="standard-of-proof" /> in human-institutions.mdx, optional, inside <Fold label="Optional: The Standard of Proof (15 minutes)">

**Learner time:** 15

Reads the pinned allegation and four dockets (institution plus evidence). For each docket picks one of four next moves (Record and keep collecting, Open a formal investigation, Issue a compliance judgment, Refer for enforcement) and writes a 60 to 90 word defence with a live word count. Submit unlocks once all four carry a move and a defence; it freezes the dockets, fires Lens.complete, and reveals the 2x2, the two self-check questions and XLab's marking key, which the learner ticks to self-mark out of 8. A button sends the four defences to the assessor (four Lens.submit items, docket-a to docket-d, graded with XLab's criterion, grounds and no-credit list as instructions; feedback instructions are XLab's two self-check questions). Then the 50-word decision standard (counter turns bold and says "over the limit" past 50) and the optional transfer question. Start over resets everything, as in XLab.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All visible copy is verbatim from `xlab-tracks/src/lib/verification/data/standard-of-proof.ts` and `STANDARD_OF_PROOF_KEY` in `xlab-tracks/src/lib/verification/data/marking-keys.ts` (HEAD, commit 1e8b150); kit strings from `kit/marking-key.tsx` (key note, "The judgement alone is not the point", footer). Em dashes replaced: "Four dockets: the evidence", "not the source's sincerity", "one person's account: the human", "converging with the human report; that convergence", "own power. That is the authority line", "evidence weight: informational capture", "disqualified: financial capture", "(the working papers, a challenge inspection)", "cultural form: the pair", "Use about 60 to 90 words" (was an en dash range).
- Adapted: the marking key ticks live in the widget's saved state instead of XLab's separate localStorage key. Per-docket word counts added under each defence (XLab shows only the 60 to 90 limit sentence). XLab's sticky allegation bar is a plain pinned card (sticky cannot work in an auto-height frame). "Optional:" prefix on the transfer question mirrors XLab's OptionalPrefix.
- Added, not from XLab: the Assessor card (button, status lines) and the scaling sentence inside assessmentInstructions ("Full marks when the move and the reasoning both match the criterion. About half when the move matches but the reasoning is missing or generic.") which maps XLab's 2-point criterion onto Lens's 0 to 100 scale. The 50-word standard and the transfer question are not submitted for grading (XLab has no key for them); they reach the tutor through the saveState summary. No promptTutor (XLab has no discuss moment).
- Hidden buttons (Start over before submit, Submit after, feedback before a score) are also disabled so a programmatic click cannot wipe state.
- Uncertain: whether to keep the intro callout on the Lens page; the widget repeats its text.
:::

#### Widget
source:: [[../widgets/standard-of-proof]]

#### Text
content::
\## Part 2 · Week 9: Covert development and the low-trust architecture

Module file: [[../modules/XLab Verification Part 2 W09 Covert development and the low-trust architecture]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-covert-what-is-it]]

#### Text
content::
\#### Worked Example: Training Through the Pause (covert-worked-example)

**Decision: widget.** Six worked-example prompts, each with a model answer and an explicit "Why this is strong" / "Common weaknesses" marking key; write-then-reveal with Lens.submit against that key is something a Question: Open segment cannot do (no reveal), and the read-without-answering route keeps XLab's worked-example intent.

**Target lens:** [[../Lenses/XLab Verification - v-covert-what-is-it]]

**Where it goes:** after "The first red-team prompt and the first blue-team prompt are yours to answer." (that paragraph itself should be rewritten or dropped, since the widget offers all six)

**What it replaces:** the two Question: Open segments (ids f5513eaf-2e53-4c17-ba06-71bf747de0df and 58822779-3747-4b0c-8150-da186a37cfdd) and the six Text segments holding the model-answer callouts ("Red team, prompt 1: the model answer" through "Blue team, prompt 3: the model answer"), i.e. everything between "\### The task" and "\### Brief debrief". They can go entirely; the widget carries the same text. The scenario text above and the "Brief debrief" below stay as prose.

**In XLab:** not a VerificationExercise. Static prose in covert-what-is-it.mdx at a10955c^ (six `<Prompt>` blocks, each followed by "##### Sample student response", "##### Why this is strong", "##### Common weaknesses"); core, not inside a Fold. The lesson was deleted in a10955c.

**Learner time:** 15 to 20 minutes reading (XLab's estimate), 40 to 60 minutes if the learner writes all six

Reads the task (red team: strategy, assumptions, weakest point; blue team: combine the layers, proportionate response). For each of the six prompts, either writes an answer and presses "Save answer and open the model answer", which reveals XLab's sample student response with its strengths and common weaknesses and sends the answer to Lens.submit scored against those two lists, or presses "Open the model answer without answering" to read it as a worked example. A status pill on each card shows "Answered and opened", "Opened without answering" or "Not opened"; a counter shows "n of 6 prompts opened". When all six are opened by either route, Lens.complete() fires and a closing card sends the learner on to the debrief.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Source: `git show a10955c^:src/content/lessons/verification/covert-what-is-it.mdx` in github.com/XLabTracks/tracks (parent commit cbd2f3ee, 2026-08-08; the deletion is a10955c, same day). All six prompts, sample responses (paragraphs and bullet lists), "Why this is strong" and "Common weaknesses" lists, the task lines, the "fictional composite" sentence and the group headings are verbatim; a script checked all 142 curriculum strings in the widget against that file and found none missing. Changes: "15–20 minutes" written as "15 to 20 minutes" (en dash); XLab's sentence "The answers below show what excellent student work might look like." moved to the closing card because in the widget the answers are hidden until opened. Added, not XLab's: the running numbers 1 to 6 on the prompt labels (XLab did not number them), the two button labels, the status pills, the one-line instruction under the task box, the marking-scheme framing sentence around XLab's lists ("Score 0 to 100 against the worked example's own notes... Why this is strong (each criterion met earns an equal share of the marks): ... Common weaknesses (deduct for each one present): ..."), and the feedback instruction. XLab had no completion condition for this lesson (no widget), so "all six opened" is the port's. Not carried: the `responseId` for tutor feedback is not persisted, so the "Ask the tutor for feedback" button is only available in the session in which the answer was scored. The scenario prose (Northstar, Orion-4, Sable, Lattice) is deliberately left in the lens, not duplicated in the widget. The Lens page currently asks two of the six prompts as graded Question: Open segments with assessment instructions written by the Lens author; those instructions paraphrase the same XLab lists the widget uses verbatim.
:::

#### Widget
source:: [[../widgets/covert-worked-example]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-covert-system-overview]]

#### Text
content::
\#### End-to-end execution trace (covert-execution-trace)

**Decision: widget.** Section 3.2 pairs two dense system diagrams with twelve numbered steps that name parts of those diagrams; stepping through the trace and lighting up the parts each step touches is exactly what a static image plus a numbered list cannot do.

**Target lens:** [[../Lenses/XLab Verification - v-covert-system-overview]]

**Where it goes:** in the article `articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification.md`, put `![[../widgets/covert-execution-trace]]` on its own line after line 233, "We follow one inference request, but the tap sees it only as part of an undifferentiated byte stream." That is the last paragraph of the section 3.2 premise, just before the `### 3.2.1 Evidence capture` heading. It is inside both assigned excerpts: `v-covert-system-overview` (article lines 27 to 648) and `v-covert-red-blue` (lines 35 to 272).

**What it replaces:** nothing has to go. What is there today is the article's own prose (the premise, the two `### 3.2.1` / `### 3.2.2` subsections with their numbered lists, the three early-exit bullets) and two hotlinked Cloudinary images, at line 236 and line 254, which are the two diagrams the widget redraws as inline SVG. The prose should stay: it is the reading, and the widget quotes it rather than replacing it. If the editor wants to avoid showing each diagram twice, the two `![](...)` image lines (236 and 254) can be deleted, since the widget draws both; the overview pair at line 57 should stay either way, because it is what the reader meets before section 3.

**In XLab:** not an XLab widget. There is no `<VerificationExercise>` for this; XLab assigned the post as a reading. The interactive is a rendering of the article's own two section 3.2 figures and its numbered trace.

**Learner time:** 8 minutes

Two tabs, "1. Evidence Capture" and "2. Evidence Evaluation (Plan A)", each drawing that phase's diagram as inline SVG: prover, verifier, the physically monitored Prover's Facility and its parts, with the labelled links between them and the article's section references. Under the diagram is the phase's numbered step list, five steps then seven. Opening a step shows the article's own sentence for that step, names the parts it involves, and lights those nodes, zones and links in the diagram while dimming the rest; Previous step / Next step walk the trace, and the last capture step offers a jump to the evaluation phase. The evaluation phase also lists the three conditions that end the trace early and the note on deliberately triggered faults. Each tab shows how many of its steps have been opened, and done means all twelve.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Every step sentence, the phase intros, the three early-exit conditions and the closing note on budgeted fault rates are verbatim from article lines 226 to 272. Inline link markup is stripped (the JSON-file link in capture step 1, the section cross-references), and the parenthetical "(see section 5.2.2)" style pointers are kept as the article writes them. The diagrams are redrawn from `SCRATCH/figs/cankaya-4.png` and `SCRATCH/figs/cankaya-5.png` (the images at article lines 236 and 254): node labels, zone labels, link labels and section numbers are transcribed from those figures, as is the ownership legend (Prover-owned, Verifier-owned, Third-party-owned, Seen by both).

One label is a reading of the figure rather than a quotation: the network taps box and the comparison-gated disclosure box are drawn in both parties' colours as a gradient in the original, and the widget spells that out as "Prover-owned / Verifier-owned". No other text is authored.

Dropped: the optional memory-challenge remark is shown as a closing note on the capture phase rather than as a step, matching the article, which puts it after the numbered list and marks it optional. Plan B (zero-knowledge proofs) is named in the evaluation intro exactly as the article names it but has no diagram of its own in the article, so there is no Plan B tab.
:::

#### Widget
source:: [[../widgets/covert-execution-trace]]

#### Text
content::
\#### Questions on the Cankaya Working Paper (compute-verification)

**Decision: native question segments are enough.** XLab's QuestionWorkspace is nine textareas with a "Save answer" button and an "n of 4 answered" counter; it has no marking key, no reveal, and nothing that changes what the learner sees next, and Lens Question: Open segments already do everything it does plus grading.

**Target lens:** [[../Lenses/XLab Verification - v-covert-system-overview]]

**Where it goes:** "Read all 9 questions before beginning. Answer Questions 1, 2, 5, and any one"

**What it replaces:** nothing. The nine Question: Open segments already on the page (ids 217e8374 to 15049c1d) are the native rendering of COMPUTE_QUESTIONS; they should stay as they are.

**In XLab:** <VerificationExercise id="compute-verification" /> in covert-system-overview.mdx, core, not inside a Fold

**Learner time:** 180 to 210 minutes (the lens says 210; XLab gives no estimate)

Reads the paper, then answers Questions 1, 2 and 5 plus one of 3, 4, 7 or 9 (6 and 8 optional), each in a text box with the placeholder "Cite the page or section you are answering from." XLab's only interactivity is a "Save answer" button per question that flips to "Saved. Keep editing if you want" and a counter that reads "n of 4 answered"; the unit completes when the required-plus-one-choice rule is met (src/lib/verification/question-workspace.ts, isWorkspaceComplete). Nothing is graded and nothing is revealed.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Checked src/components/verification/widgets/compute-verification.tsx, src/lib/verification/data/compute-verification.ts, src/components/verification/kit/question-workspace.tsx and src/lib/verification/question-workspace.ts at HEAD (93847c7). The Lens page carries all nine question titles and bodies verbatim, the same placeholder, the required / choose-one / optional labelling, and the rule sentence from the widget's intro ("Read all 9 questions before beginning. Answer Questions 1, 2, 5, and any one question out of questions 3, 4, 7 or 9. Questions 6 and 8 are optional."). Two things Lens does not reproduce: XLab's live "n of 4 answered" counter (Lens counts completion per segment instead) and XLab's per-question pill "Answer one of 3, 4, 7 or 9" (Lens writes the same words into each question heading). The assessment-instructions on the Lens segments are the Lens author's, not XLab's; XLab has no marking key for this widget, so there is nothing to port there. One honest gap in XLab's own rule (docs/verification/module-3-log.md, "Module 3 replaced with the Cankaya working paper"): Question 6 is `optional` and counts toward nothing, and XLab's owner never said whether it belongs in the choice group.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

Already in place. The nine existing Question: Open segments in [[../Lenses/XLab Verification - v-covert-system-overview]] are the proposal; no new segments and no new uuids needed. If the orchestrator wants XLab's completion rule enforced, the only lever Lens has is marking Questions 1, 2 and 5 as non-optional (they already are) and leaving 3, 4, 7, 9, 6, 8 `optional:: true` (they already are).
:::

#### Text
content::
\## Part 2 · Week 10: Evasion routes and the red team review

Module file: [[../modules/XLab Verification Part 2 W10 Evasion routes and the red team review]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-covert-red-blue]]

#### Text
content::
\#### Evasion scenario taxonomy, revisited with scores (evasion-taxonomy)

**Decision: widget.** XLab had no widget here (both lessons were prose and tables), but the data in the two Lens lenses is a real table: ten routes with layer and actor lists, seven of them with four 1-to-5 scores plus a one-line reason per score, a rationale paragraph and a "who can change the balance" list. Seven separate score tables cannot be compared without scrolling; an explorer that sorts by a score, filters by an actor or layer, shows all seven scores as one matrix and puts up to three routes side by side is what the "add judgment" instruction in Section B asks the learner to do.

**Target lens:** [[../Lenses/XLab Verification - v-covert-red-blue]]

**Where it goes:** inside the last big Text segment, after the paragraph "Two things to hold while you read the routes below." and before the "Works cited" callout. Split that Text segment: keep "\## Submission standard", "\## Section B: the taxonomy revisited", the two intro paragraphs and the "Scoring:" line above the widget; the Works cited callout becomes its own Text segment below it.

**What it replaces:** the seven "\###" route blocks in that Text segment (Repurpose declared infrastructure, Steal or copy model weights, Split training across sites, Falsify declarations or provenance, Distill or extract capability, Conceal the real actor, Divert controlled hardware), each a one-row score table plus a rationale paragraph plus a "Who can change the balance" line, and the CriticMarkup comment about the three missing routes. The widget carries every word of those blocks, so they can go entirely; the "Scoring:" legend line is repeated inside the widget, so it may stay above as context or go. Keep the CriticMarkup comment's substance somewhere for Elias (the widget says "Not scored" on the three routes but does not say why in XLab's words).

**In XLab:** no `<VerificationExercise>` in either lesson. covert-taxonomy.mdx (3.1.1) is the ten-route table only; covert-red-blue.mdx (3.2) embeds ten `<Exercise>` writing prompts and one `<MemoDesk lesson="covert-red-blue" />` (see the other two notes). Section B is core, not inside a Fold. Both files at XLab commit cbd2f3ee (the parent of a10955c, which deleted them; `a10955c^` fails to resolve in this clone because a10955c is unreachable from every ref, but both objects are in the pack).

**Learner time:** 10 minutes

Ten route cards, in XLab's Section B order by default: number, name, one-line "what the actor tries to do", and for the seven scored routes four score tiles with a bar. The learner types a layer or actor into the filter (or taps an actor chip, computed from the data: inspectors 4, developers 3, regulators 3, researchers 3), sorts by any of the four criteria, opens a card to read the layers, actors, the four score reasons, the rationale paragraph and who can change the balance, and switches to a score matrix that shows all seven scored routes at once with cell shading by score. "Compare" on up to three cards builds a side-by-side table (what, four scores with reasons, who can change the balance). Opening all seven scored routes marks the widget complete.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Sources: `src/content/lessons/verification/covert-taxonomy.mdx` (ten-route table, unit 3.1.1) and Section B of `src/content/lessons/verification/covert-red-blue.mdx` (seven scored routes, unit 3.2), both at XLab commit cbd2f3ee9892b2891c5ccf4a22d51e4569650fc3. A script (work/fid_evasion.py) matched every table cell, every "n/5 label. reason" cell, every rationale paragraph and every "Who can change the balance" list against those files after em-dash replacement: no differences. Column headers use XLab's slash forms ("Political / organizational feasibility", "Durability / harm"); the Lens lens rewrote them with "and".
- Em dashes replaced: route 5 "for an unauthorized purpose, for example, report training as inference" (XLab joined "purpose" and "for example" with an em dash); the score cells "4/5, High." became "4/5 High." with the label shown next to the number. No other rewrite.
- Route names: the seven scored blocks use XLab's Section B headings ("Repurpose declared infrastructure", "Split training across sites") which differ from the taxonomy names ("Repurpose legitimate infrastructure", "Split the operation across sites"). Cards are titled by the taxonomy name; the opened card shows "Scored in Section B as: <XLab heading>". Both strings are XLab's.
- Dropped: the `<Cite n="..."/>` markers after each rationale (the Lens lens already moved them into the Works cited callout); the "module priority" column XLab itself removed before a10955c.
- Three unscored routes (3, 9, 10) show "Not scored: XLab's Section B table scores seven of the ten routes, and this is one of the three it leaves out." That sentence is widget chrome, not curriculum; no scores were invented, matching XLab's module-3 log which records the gap as transcription owed.
- Completion: XLab has no widget and no onComplete to mirror. Lens.complete() fires once when all seven scored routes have been opened, which is the reading Section B asks for. Nothing gates on it unless the segment sets required:: true. No Lens.submit (nothing here is graded in XLab) and no promptTutor (no discuss moment in XLab).
- Actor chips are computed at runtime from XLab's actor and "who can change the balance" lists (names recurring in 3 or more routes), so no actor vocabulary was authored.
- Not placed in the 3.1.1 taxonomy lens: that lens tells the learner not to rank routes yet, and a widget placement cannot hide the scores per lens, so the static table stays there and the explorer lives only in Section B. A scores-free filter over ten rows would not beat the table enough to justify a second copy of it.
- The `<title>` in the widget and the h1 say "Evasion route explorer"; the eyebrow "Section B: the taxonomy revisited" is the lens's own heading.
:::

#### Widget
source:: [[../widgets/evasion-taxonomy]]

#### Text
content::
\#### Expert review, Questions 1 to 10 (v-task-covert-red-blue)

**Decision: native question segments are enough.** Ten free-form writing prompts (`type: "writing-prompt"`, `format: "free-form"`) with no reveal, no branching and no marking key in XLab; Lens Question: Open segments with assessment instructions are the right shape, and the Lens lens already carries all ten.

**Target lens:** [[../Lenses/XLab Verification - v-covert-red-blue]]

**Where it goes:** already in place: the ten Question: Open segments after the Text segment "\## Your role and assignment"

**What it replaces:** nothing to change; the ten segments (ids 38a92abc-9dd5-476e-b9a9-264c13c02994 through 69482580-7cb1-4162-a754-90b33e7aa74c) are the port

**In XLab:** `<Exercise id="v-task-covert-red-blue-1" />` to `-10` in covert-red-blue.mdx at commit cbd2f3ee, core, under the "### Questions" heading, not inside a Fold; prompts in `src/content/verification/exercises.ts` at the same commit

**Learner time:** 150 minutes (the assignment is a 2 to 6 page review)

Reads the assigned treaty articles and system-overview sections, then writes answers to ten numbered questions in order, in place, as one expert review. On XLab each `<Exercise>` was a writing editor with autosave and submit; on Lens each Question: Open does the same with AI assessment.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Checked XLab's ten prompts at commit cbd2f3ee against the Lens segments: the Lens lens keeps XLab's question titles and structure but retargets the citations from XLab's five-page adapted packet to the real Articles IV to VII and Sections 1 to 3, as its own CriticMarkup note explains; the assessment-instructions and feedback-instructions are Lens additions (XLab's exercises.ts carries no rubric for these ids). That retargeting is Elias's earlier decision and is not something a widget could improve on. XLab's arrows in Question 1 ("regulated activity → captured evidence → ...") are commas in the Lens version.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

Already present in the lens; nothing to paste.
:::

#### Text
content::
\#### Written output card (memo-desk)

**Decision: nothing to port.** `<MemoDesk lesson="covert-red-blue" />` is a pointer card to XLab's memo desk, and for this lesson the slot it prints is empty: memos.ts registers `m3-written-output` with brief null, audience null, status "unspecified", and the gap text "Module 3 is the one module for which the outline never says which." There is no exercise to port.

**Target lens:** [[../Lenses/XLab Verification - v-covert-red-blue]]

**Where it goes:** n/a (XLab placed it last in the lesson, after the Sources list)

**What it replaces:** nothing (the Lens lens's own CriticMarkup note already records that the MemoDesk card was not carried over because its slot is unspecified)

**In XLab:** `<MemoDesk lesson="covert-red-blue" />` at the end of covert-red-blue.mdx at commit cbd2f3ee, core, not inside a Fold

**Learner time:** 0

Nothing here. On XLab the card showed "Written output · 3.x", the title "Written output", the gap sentence, "Budget about 800 words" and "Goes through peer review", and linked into the memo desk where a draft could be typed. The desk itself is a platform feature, not lesson content.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Source: `src/components/verification/memo-desk-card.tsx` and `src/content/verification/memos.ts` at XLab commit cbd2f3ee. XLab's module-3 log says the slot was repointed to the replacement lesson only because a test requires every slot's lesson to embed the card exactly once, and that its status stayed "unspecified" because the outline never named module 3's written output. If Elias later decides the 2 to 6 page expert review is that written output, the ten Question: Open segments already collect it; a memo card would add nothing.
:::

#### Text
content::
\## Readings embedded by the course

These entries replace static images or lost charts inside imported articles. A widget goes into the article body on its own line as `![[../widgets/<name>]]`, so every lens that excerpts the article shows it in place.

#### Text
content::
\#### Assurance curves for three verification budgets (AssuranceCurve)

**Decision: widget.** The curve's whole lesson is the shape: at N_ver = 100 the confidence collapses as coverage climbs past 99%, and each factor of 100 in audited packets buys back two nines of coverage. The eight-row table in the article gives the sampled points but not the trade-off, and a learner cannot ask it for a coverage the table does not list.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `*Table adaptation of the source chart. N_ver is the number of packets the verifier audits. Values are computed from the formulas...` (article line 420, under the bold caption **Assurance curves for three verification budgets**). This spot is inside the collapsed callout "An overview of possible verification approaches." (lines 403 to 445), which is the only occurrence inside the lens's Article ranges. If a widget cannot be embedded inside a `:::callout` (no article in the repo does it yet), use the appendix occurrence instead: after `*Table adaptation of the source chart, computed from the two formulas above.*` at line 844, which is top-level body text but falls outside the Week 1 lens ranges.

**What it replaces:** the eight-row coverage-against-confidence table at article lines 422 to 431 (repeated verbatim at lines 846 to 856). Keep the table below the embed as the text fallback; the appendix copy can stay untouched.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `AssuranceCurve` at source MDX lines 350 and 705, the first inside a collapsed detail box, the second in the appendix.

**Learner time:** 4

Hovers the chart or presses a coverage point (90%, 99%, 99.9%, 99.99%, 5 to 8 nines) and reads the exact confidence for all three budgets at once, and can hide or show each curve to compare two budgets cleanly. Done means at least three different coverage points have been read.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
The three budgets (N_ver = 100, 10K, 10M), their dash patterns, the axis mappings and the curve construction are copied from the page's chunk 4857, which is the React component. The curves are not traced from the picture: they are recomputed from the appendix formulas, coverage = 1 - F* and confidence = 1 - exp(-N_ver * F*), which is character for character what the component computes (`1 - Math.exp(-nVerified * Math.pow(10, logF))`). Recomputing those formulas at F* = 10^-1 to 10^-8 reproduces the article's table exactly (90% / N_ver 100 gives 99.99546%, shown as 99.995%; 99.99% / N_ver 10K gives 63.212%, shown as 63%; 8 nines / N_ver 10M gives 9.516%, shown as 9.5%), so the article table and the widget agree on every cell.

Adapted: the source clips the confidence axis at 8 nines and the widget keeps that clip, so a reading of "~100%" means "at or beyond the top of the axis" exactly as in the source. Axis titles are verbatim ("Coverage (log scale)", "Confidence"). Data sources: `work/ai2040/lazy-assurance.js` (chunk 4857), `work/ai2040/svg-assurance1.svg` (rendered chart, byte-identical to `svg-assurance2.svg`, confirming the two placements are the same chart).

Uncertain: none.
:::

#### Widget
source:: [[../widgets/ai-2040-assurance-curve]]

#### Text
content::
\#### Chip declaration result, Jan 2029 and mid 2029 (ChipDeclarationResult, ChipDeclarationResultGlobal)

**Decision: widget.** Two waffle charts at one square = 250K H100e make the asymmetry legible (the US block is nine times China's) and the plausibly-undeclared outline shrinks from six squares to two when the rest of the world joins; the two two-row tables in the article state the totals but show neither the scale nor the shrinkage.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `*Table adaptation of the source chart, which draws compute in blocks of 250K H100e; the undeclared figures...` (article line 312, in "### Jan 2029: Mutual Chip Declaration and Inspection"). One embed only: the widget's date switch already carries the mid-2029 view, so do not add a second embed at line 378. Both spots are in ordinary body text, not inside a callout. Inside the lens's third Article range (`from:: ## 2029-2030: Deal Implementation`).

**What it replaces:** two prose tables, at article lines 307 to 310 (Jan 2029: US 224M / China 26M, ~1.5M each undeclared) and lines 372 to 376 (mid 2029: plus rest of world 39M, ~0.5M each). Both tables should stay where they are as the text fallback; the widget goes above the first one.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `ChipDeclarationResult` (source MDX line 254) and `ChipDeclarationResultGlobal` (source MDX line 305), core body text, not inside a Fold.

**Learner time:** 3

Switches between January 2029 (US and China) and mid 2029 (with the rest of the world), hovers or presses a block to see how many 250K H100e squares it holds and what that is in H100e, and presses a party to read its declared total against its plausibly undeclared outline. Done means both dates have been viewed.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Party labels, declared totals (224M, 26M, 39M), the block lists, the grid sizes (US 60x15, China 15x7, rest of world 23x7) and the 250K H100e square size are copied from the page's chunk 7228, which is the React component itself. The two undeclared-cell counts were not read off a picture: the rendered `svg-decl-jan.svg` carries 12 outlined cells over two parties (6 each, 1.5M H100e) and `svg-decl-mid.svg` carries 6 over three parties (2 each, 0.5M H100e), matching the component's `undeclCells` default of 6 and the global variant's 2, and matching the article's two tables.

The block-placement routine in the widget is a line-for-line port of the component's own layout function. Verified mechanically: the widget renders 329 rects in the January view and every one of them matches an `(x, y, width, height)` present in the source's rendered SVG, with none missing. Colours are remapped to the Lens palette (ink for the US, accent for China, ink hatch for the rest of the world). Data sources: `work/ai2040/lazy-chipdecl.js` (chunk 7228), `work/ai2040/svg-decl-jan.svg`, `work/ai2040/svg-decl-mid.svg`.

Uncertain: the article's caption says the undeclared figures are "read at that block resolution", which is right; the chart cannot express a value finer than 250K H100e, and the surrounding prose gives the real estimate as "around 1.5M H100e (with the 80% CI reaching about 4M)". The widget shows the block figure and does not restate the CI.
:::

#### Widget
source:: [[../widgets/ai-2040-chip-declaration]]

#### Text
content::
\#### Chip flow restrictions, 2029 and 2032 (ChipRestrictions2029, ChipRestrictions2032)

**Decision: widget.** The point of both charts is a two-dimensional boundary: where a device sits on interconnect against compute decides whether the deal touches it, and the 2032 chart moves the line so that the same RTX 4090 crosses from unrestricted to above the AI-relevant floor. The article's two tables list the devices but flatten the boundary into a "Tier" column, so the learner cannot see which device is close to the line or why.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `*Table adaptation of the source chart. Compute and interconnect values are read off the chart's log axes and are approximate...` (article line 335, under the bold caption **Chip flow restrictions, 2029: example devices by compute and interconnect**). One embed only: the widget's year switch carries the 2032 view, so do not add a second embed at line 694 (the 2032 caption). Caution: both spots sit inside collapsed `:::callout` blocks (lines 324 to 352 and 680 to 713) and no article in the repo yet embeds a widget inside a callout; the only demonstrated embed is at top level in `articles/Article annotation and text collapse demo.md`. If an embed inside a callout does not render, put it immediately after line 352 (the closing `:::`, just above "### Feb 2029: Inference-only retrofit begins") instead.

**What it replaces:** the 2029 device table at article lines 337 to 349, and the 2032 device table plus the two-row treatment table at lines 696 to 712. Both tables should stay as the text fallback below the embed.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `ChipRestrictions2029` (source MDX line 283) and `ChipRestrictions2032` (source MDX line 585), both inside collapsed detail boxes in the source too.

**Learner time:** 5

Switches between the 2029 and 2032 charts and presses a device to read its compute, cross-chip interconnect, memory capacity and memory bandwidth, and which side of the line it falls on. In 2029 the line is the L-shaped Tier 0 / Tier 1 boundary; in 2032 it is the AI-relevant floor with the 30M H100e unverified edge-compute cap. Done means both years have been viewed and at least three devices inspected.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Device names, compute, interconnect, memory and bandwidth are copied field for field from the page's chunks 6617 and 8343, which are the React components. So are the axis ranges, the dot-radius formula `r = 2 + 2 log10(memory / 8)`, the HBM threshold of 1500 GB/s, the 2029 boundary (`s(50)` on the interconnect axis and `x(0.4)` on the compute axis) and the 2032 floor constant `4000 / 15800`. The tier rule in the widget (`interconnect < 50 && compute < 0.4` is Tier 0) is read off the source's own boundary drawing, which is a horizontal segment at compute 0.4 running left from interconnect 50 and a vertical segment at interconnect 50 running down from there. Legend and label strings ("Tier 0: Unrestricted / consumer", "Tier 1: Subject to deal / inference-only or cold storage", "AI-relevant floor: 4,000 TPP", "Unverified edge-compute cap / 30M H100e / 25M already in world (pre-deal) / + 5M new credits", "Verified edge compute exempt") are verbatim from those chunks.

Note the source deliberately gives some devices different numbers in the two years, and the widget preserves that: DGX Spark 0.25 in 2029 against 0.12 in 2032, H20 0.3 against 0.148, RTX 4090 0.17 against 0.33, RTX 5090 0.33 against 0.419, M4 Max MacBook in 2029 against M4 Pro MacBook in 2032, and B200 present in 2029 but absent in 2032. The article's two tables reproduce all of this correctly.

Adapted: only the colours, which are remapped to the Lens palette. The source's arrow in "Verified edge compute → exempt" and its "≈" and "§" glyphs are kept as they are; the one rewrite is the em dash in "below the AI-relevant floor, capped at 30M H100e", which becomes a comma. Data sources: `work/ai2040/lazy-chip2029.js` (chunk 6617), `work/ai2040/lazy-chip2032.js` (chunk 8343), and the rendered `svg-chip2029.svg` / `svg-chip2032.svg` for label checking.

Uncertain: the source component gives no units caption for the 2032 "Consumer compute below the AI-relevant floor, capped at 30M H100e" band, so the widget states the cap in the policy panel rather than drawing it on the axes, as the source does.
:::

#### Widget
source:: [[../widgets/ai-2040-chip-flow]]

#### Text
content::
\#### Compute locations by datacenter size, January 1, 2029 (AIDatacenters2029Hybrid)

**Decision: widget.** The source treemap carries the US, China and rest-of-world split inside every size band (57 / 7 / 10 datacenters in the 1M to 10M band, and so on) plus the visual proportion that makes "99% of world compute sits above 10K H100e" concrete, and none of that survives in the three flat tables the import left behind.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `*Table adaptation of the source figure. Compute quantities use H100-equivalent units (H100e); K = thousand...` (article line 53, under the bold caption **Compute locations by datacenter size, January 1, 2029 (scenario projection)**). Inside the lens's first Article range (`from:: ## Summary of the Plan`).

**What it replaces:** three prose tables (datacenter size bands, other compute locations, region totals) at article lines 55 to 74. Keep all three directly below the embed as the text fallback: they are quotable, they are what a screen reader gets, and the widget adds interaction rather than new numbers. Nothing needs to be deleted.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement (https://ai-2040.com/supplements/verification-plan), `AIDatacenters2029Hybrid` directive at source MDX line 46, core body text, not inside a Fold.

**Learner time:** 4

Presses one of nine location bands (six datacenter size bands, compute in transit, AI consumer, non-AI consumer) and reads its datacenter count, total compute, share of world compute, the verification measure the plan applies to it, and how the datacenters in that band split between the US, China and the rest of the world. A region filter dims everything outside one region so the learner can see, for instance, that China's compute is concentrated in the same bands as the US but at a tenth of the scale. Done means all six datacenter size bands have been opened.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Every rectangle is the source page's own SVG geometry, parsed from the rendered chart (viewBox `0 0 681 523.407`, 849 rects). Region comes from each rect's fill in that SVG: `#111111` = US, `#8b0000` = China, `url(#dcpol-ink-bars)` = rest of world. The per-band rect counts (1, 74, 257, 497) reproduce the source's own band labels exactly, which is the check that the fill-to-region mapping is right. Band labels, the `N DCs·compute·share` strings, and the region footer line are copied verbatim from the SVG text nodes. The three verification-measure brackets are assigned by their vertical extents in the source SVG (`x=484` spans y 0 to 305.407, so inference-only covers the four datacenter bands plus in-transit; `x=171.196` spans 313.407 to 385.407; `x=216.987` spans 445.407 to 519.407), not by eye.

Adapted: colours are remapped to the Lens palette (ink for US, accent #b87018 for China, ink hatch for rest of world) and the source's dark red is dropped. The 1K to 10K and under-1K bands are drawn by the source as one block per region rather than one rect per datacenter, so the widget shows no per-region count there and says so. The ampersand label "Cap & Trade" is rendered as "Cap and Trade" to avoid an entity in text content; the source's "(if unverified)" subtitle is kept. Data sources: `work/ai2040/svg-treemap.svg` (rendered chart, fetched from the live page), `work/ai2040/page.html`.

Uncertain: none. The article's own three tables agree with the SVG on every number, so the import lost the picture and the region split, not the figures.
:::

#### Widget
source:: [[../widgets/ai-2040-compute-locations]]

#### Text
content::
\#### Deal Implementation Timeline, detailed (TimelineLineDetailedClean)

**Decision: widget.** `LENS/widgets/ai-2040-deal-timeline.md` was built for this article before this pass; it is a static SVG timeline with nothing to click. Not duplicated. A corrected copy is in `OUT/widgets/ai-2040-deal-timeline.md` under the same id, see Fidelity.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `- **Jan 2031:** mature safety-case-based R&D rules in place` (article line 301, the last bullet of the list introduced by "Deal implementation timeline, Jan 2029 to Jan 2031:" at line 289). Top-level body text, not inside a callout, and inside the lens's third Article range (`from:: ## 2029-2030: Deal Implementation`). It is currently embedded only in `articles/Article annotation and text collapse demo.md` and has never been placed in this article.

**What it replaces:** nothing is removed. The 11-bullet list at article lines 291 to 301 is the prose the import left in place of the figure; it should stay above the embed as the text version, with the chart following it.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `TimelineLineDetailedClean` at source MDX line 250.

**Learner time:** 2

Reads the two-year sequence in one picture: the January 2029 declaration and the pause, the inference-only retrofit climbing 50, 80, 95 percent through 2029, R&D resuming in November with the verification rollout going 2 to 20 percent, the first approved training runs and first post-deal release in 2030, the SL5 inference cluster rollout at 5 then 30 percent, and mature safety-case rules by January 2031. Nothing to click, so there is no completion condition and the widget makes no Lens calls.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Every label in the existing widget matches the rendered source chart word for word (checked against `work/ai2040/svg-timeline.svg`).

The marker positions did not. The existing widget places events at months 1.0, 1.5, 2.2, 10.1 and spans at 2.2 / 4.2 / 8.1 and 10.1, which are estimates from the picture. The source carries exact dates in its events JSON (chunk 4126) and converts them with `(year - 2029) * 12 + (month - 1) + (day - 1) / daysInMonth`. The true values are: mutual chip declaration 2029-01-24 (0.742), R&D pause begins 2029-02-10 (1.321), SL5 construction begins 2029-03-01 (2.0), inference-only retrofit 50% 2029-03-01, 80% 2029-05-01, 95% 2029-09-01 (2.0 / 4.0 / 8.0), R&D verification rollout 2% 2029-11-01 and 20% 2030-03-01 (10.0 / 14.0), R&D resumes 2029-11-01 (10.0), first major training runs approved 2030-02-01 (13.0), SL5 inference clusters 5% 2030-06-01 and 30% 2030-09-01 (17.0 / 20.0), first generation of post-deal models released 2030-06-16 (17.5), mature safety-case-based R&D rules 2031-01-01 (24.0). `OUT/widgets/ai-2040-deal-timeline.md` carries those numbers, a provenance comment, and one clause added to `summary_for_tutor`; the id and title are unchanged, so uploading it updates the existing widget in place. Errors were at most about nine days at a two-year scale, so this is a correctness fix, not a visible one.

Two things worth flagging to whoever owns the article text. First, the article's bullet list and the chart disagree slightly: the bullets say the retrofit reaches 50% in Feb 2029 and 95% in Sep to Oct 2029, and that the first post-deal models are released in Jul 2030, while the chart's dates are 2029-03-01, 2029-09-01 and 2030-06-16. Second, the source's events JSON continues past the chart's window (hardware research approval 2031-07, inference concentrated in 5 to 10 clusters 2031-09, first SEZs 2032-01, cap and trade 2032-04, hardware concentrated 2033-07, first ocean solar farms 2033-11, first ocean datacenters 2034-07); the source's "short" layout hides them and the widget correctly does the same.

A later QA pass sent the file back for three fixes, all applied here. The SVG now sits in a `.chartbox` with `overflow-x: auto` and a `min-width: 720px`, so at 360px it keeps its labels at about 10px and scrolls sideways inside its own box instead of scaling to 0.36x and rendering at 4.3px. The provenance caption, which used to be an SVG `<text>` at y 392 and printed through the "First generation of post-deal models released" label, is now an HTML paragraph under the chart. The page uses the Lens starter stylesheet (DM Sans, Newsreader, the eyebrow, `<h1>` and bordered card of the sibling chart widgets) with `#b87018` in place of the source's dark red on the two highlighted markers. It still makes no `window.Lens` calls, which is right for a static figure.
:::

#### Widget
source:: [[../widgets/ai-2040-deal-timeline]]

#### Text
content::
\#### Catching a rogue internal deployment (VerificationAssurance)

**Decision: widget.** The source chart is interactive on the source page: two sliders (year, and therefore pool and default packet size; and packet size from 1 to 10K H100e-hours) change the curves, and the whole argument of the 2034 section is that shrinking the packet is worth as much as raising the budget. The article's fixed seven-row table freezes one slider setting and loses the lever.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** after `*Table adaptation of the source chart at its default setting (2034, packets of 100 H100e-hours, 1% recomputation budget)...` (article line 549, under the **Pool:** and **Recomputation budget:** lines). This occurrence sits inside the collapsed callout "Workload Verification." (lines 526 to 562) and is the one inside the lens's third Article range. If a widget cannot be embedded inside a `:::callout`, use the second occurrence instead: after the identical caption at line 767 in "### 2034: Verification improvements", which is top-level body text but falls outside the Week 1 lens ranges. One embed only; do not place both.

**What it replaces:** the seven-row rogue-size-against-P(detected) table at article lines 551 to 559, repeated verbatim at lines 769 to 777. Keep the table below the embed as the text fallback; the second copy can stay untouched.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `VerificationAssurance` at source MDX lines 456 and 627.

**Learner time:** 5

Moves the year slider (2030, 2032, 2034, 2040, which sets the verified pool and the default packet size) and the packet-size slider (1 to 10K H100e-hours), then hovers the chart or presses a rogue-deployment size to read P(detected) within one hour, one week and one month, together with the number of rogue packets that implies. Curves can be hidden individually. Done means the learner has moved a slider away from the default and read at least three different rogue sizes.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Year options and their pool sizes and notes ("~400M H100e" / "one packet per server rack per hour (~10K H100e per packet)" through "~1T H100e" / "one packet per GPU every ~6 minutes (~10 H100e per packet)"), the three time windows and their dash patterns, the 1% recomputation budget, and the axis mappings are copied from the page's chunk 6441, which is the React component behind the sliders. The curves are recomputed from the appendix formula P(detected) = 1 - exp(-C * N_fake) with N_fake = size * hours / packet, which is exactly the component's expression `1 - Math.exp(-(0.01 * 10^r * hours / packet))`. Recomputing at the 2034 default (packet 100, C = 1%) reproduces the article's table cell for cell (10 H100e over a week gives 15.46%, shown as 15%; 100 over a month gives 99.925%, shown as 99.9%; 10K within an hour gives 63.212%, shown as 63%).

Fixed in this pass: the finish condition previously fired after a single slider nudge, which a learner could trip without reading anything. It now requires a slider change plus three distinct rogue sizes read from the size buttons, and `summary_for_tutor` and the on-screen status line were updated to match. Verified by driving the two range inputs and the size buttons in jsdom: complete fires exactly once, on the third size button after a slider move.

Adapted: the source clips the P(detected) axis at four nines, and the widget keeps that clip, so "~100%" means at or beyond the top of the axis. The widget adds an N_fake column to the readout table, which is not new data (it is `size * hours / packet`, the quantity the source's own formula uses) but makes the appendix formula visible. Data sources: `work/ai2040/lazy-rogue.js` (chunk 6441), `work/ai2040/svg-pdet1.svg` (byte-identical to `svg-pdet2.svg`, confirming the two placements are the same chart at the same default).

Uncertain: none.
:::

#### Widget
source:: [[../widgets/ai-2040-rogue-detection]]

#### Text
content::
\#### World AI compute growth, 2026 to 2034 (ComputeGrowth)

**Decision: nothing to port.** Four labelled data points. The article's two-column table carries every number and every year the chart shows, and there is no interaction the chart offers that the table does not.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** n/a. The chart's spot is the two-column table at article lines 744 to 749 in "### 2034: Verification improvements", top-level body text, outside the Week 1 lens ranges.

**What it replaces:** nothing. The table at article lines 744 to 749 stays as it is.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `ComputeGrowth` at source MDX line 615.

**Learner time:** 0

Nothing; no widget was built.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
The rendered chart (`work/ai2040/svg-worldcompute.svg`) carries exactly eight text nodes: 2026 / 20M, 2030 / 500M, 2032 / 3B, 2034 / 60B. The article's table reproduces all four rows verbatim, including the units. Nothing is lost.

One inconsistency inside the source itself, worth a footnote rather than a widget: this chart puts world AI compute at 3B H100e in 2032 and 60B in 2034, while the rogue-detection chart's own year presets on the same page use "~3B H100e" for 2032 but "~33B H100e" for 2034, and the article's "Late 2030" paragraph gives a global ~930M H100e for end-2030 against this chart's 500M for 2030. The widget `ai-2040-rogue-detection` shows the 33B figure because that is what its source component contains; this note records the discrepancy so nobody treats it as a porting error.
:::

#### Text
content::
\#### Diagram figures kept as images (image1, image3, image6 x2, image8, image9, image11, image13)

**Decision: nothing to port.** These are the article's eight `![](https://ai-2040.com/verification-plan/imageN.png)` lines, and unlike the thirteen SVG charts they were not lost: they still render from the source host and each is a hand-drawn schematic, not data. There is no series, no axis and no parameter to move, so an interactive version would be a redraw with no new affordance, and redrawing a schematic by hand is exactly the kind of eyeballing this pass is meant to avoid.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** n/a. The eight lines are at article lines 223, 254, 261, 362, 411, 524, 564 and 717. Lines 223, 254 and 261 are the retrofit proposal and secure network gateway figures; 223 and 254 sit inside the callout "Concrete inference-only retrofitting proposal." (lines 219 to 259), which the lens embeds as its second Article range, and 261 is just below it. Line 362 repeats image6 in "### Feb 2029: Inference-only retrofit begins". Line 411 is the verification-approaches landscape inside the callout "An overview of possible verification approaches." Line 524 is the workload approval and verification figure, line 564 the five-step workload flow, and line 717 the research-titration-plus-production-capping overview in the 2032 section.

**What it replaces:** nothing. All eight image lines stay.

**In XLab:** not XLab exercises. Source is the AI 2040 verification supplement; these are raster figures on the source page rather than inline SVG components.

**Learner time:** 0

Nothing; no widget was built.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Seven distinct images across eight lines: image6 appears twice (lines 223 and 362). They are hotlinked from ai-2040.com, which is the same host the source page serves them from, so the brief's rule on external images is satisfied and nothing needs to be inlined.

One gap the import did leave: the numbered five-step description that belongs with the workload flow figure (Declaration, Approval, Evidence collection, Verification, Evaluations and release) survives as prose at article lines 566 to 575, immediately below image8, so the figure and its legend are still together. The other seven images carry their explanation in the surrounding prose too. No caption text is missing.
:::

#### Text
content::
\#### Example packet sizes and verification logging granularity (WorkloadChunking, LoggingGranularity)

**Decision: nothing to port.** These are two pictures of one idea, the same workload sliced at ever finer grain, and the interactive form of that idea is already in this article: the rogue-detection widget's packet-size slider runs over exactly the values these two charts illustrate (10K, 1K, 100 and 10 H100e-hours) and shows what the slicing buys. Building a third slicing widget would repeat the lesson without adding a lever.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** n/a. The chunking chart's spot is after `*Table adaptation of the source chart, which shows the same workload sliced at each of these levels...` (article line 532), inside the collapsed callout "Workload Verification." (lines 526 to 562). The logging-granularity chart's spot is the three-row table at article lines 753 to 757 in "### 2034: Verification improvements", top-level body text.

**What it replaces:** nothing. The six-row granularity table at article lines 534 to 541 and the three-row tap table at lines 753 to 757 stay as they are.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `WorkloadChunking` at source MDX line 454 and `LoggingGranularity` at source MDX line 621.

**Learner time:** 0

Nothing; no widget was built.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
`WorkloadChunking` (chunk 4083, rendered as `svg-granularity.svg`) draws six rows over the same 730-unit bar with 1, 3, 16, 60, 150 and 400 chunks, labelled "Full training run", "Training phases", "Gradient steps", "Layer forward/backward", "GPU kernel calls", "Individual instructions", with a coarse-to-fine arrow and the caption "Each chunk: f(input) -> output". Its own title is "Example Packet Sizes". The article's table carries all six labels and the caption's meaning; the only thing it drops is the chunk counts, and those are illustrative drawing counts rather than curriculum values, which is why reproducing them interactively would look more precise than the source is.

`LoggingGranularity` (chunk 2174, rendered as `svg-taps.svg`) has three rows: 2030 "Per-server tap" / "~4K H100e per server"; 2032 "Per-shelf tap" / "~400 H100e per shelf"; 2034 "Per-GPU tap" / "~100 H100e per GPU", each drawn as a 100K H100e-hour workload divided into `round(100000 / packetHours)` cells, that is 25, 250 and 1000 cells, under the caption "Workload: ~GPT-3 sized training run (100K H100e-hours)". The article's table carries the years, the tap names and the compute per tap, and the workload line survives at article line 759. The derived cell counts (25 / 250 / 1000) are the only thing lost, and each is just 100K divided by the compute per tap.

Nothing here is uncertain or estimated; both were read from the components and confirmed against the rendered SVGs.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

n/a. Both tables already carry the content, and the interactive treatment lives in `widgets/ai-2040-rogue-detection.md`.
:::

#### Text
content::
\#### Verification Plan Timeline, 2026 to 2036+ (verificationTimeline)

**Decision: nothing to port.** It is a phase strip, not an exercise: seven numbered milestones laid on a year axis inside three labelled phases. There is nothing for a learner to do that reading the article's own Phase 1 / Phase 2 / Phase 3 paragraphs and its year headings does not already do, and the one interactive timeline in this article (ai-2040-deal-timeline) already covers the dense 2029 to 2031 middle at much higher resolution.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** would have gone after `**Phase 3. Improve robustness.** Over time the US and China improve the stability and durability of the verification regime...` (article line 78), at the end of the "Summary of the Plan" section. Inside the lens's first Article range.

**What it replaces:** nothing. This figure was dropped silently in the import: unlike the other twelve charts it left behind no table, no prose paragraph and no image link. See the recommendation below.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `verificationTimeline` at source MDX line 17, core body text, not inside a Fold.

**Learner time:** 0

Nothing; no widget was built.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Verbatim content of the lost figure, from the rendered `work/ai2040/svg-phases.svg`: an axis running 2026, 2027, 2028, 2029, 2030, 2031, 2032, 2033, 2034, 2035, 2036+, with seven numbered markers, 1 "Chip tracking", 2 "Verification R&D funding", 3 "Mutual Chip Declaration", 4 "Inference-only retrofit", 5 "R&D verification", 6 "Hardware cap & trade", 7 "Verification improvements", grouped under three spans, "Phase 1: Preparing / 2026-2028", "Phase 2: Implementing / 2029-2030", "Phase 3: Improving / 2031-2036+". The figure's own title is "Verification Plan Timeline - ai-2040.com".

Recommendation for the article, not for a widget: because this is the reading's only compact map of the whole plan and nothing replaced it, add a three-row table under the Phase 3 paragraph using exactly those strings, for example Phase / Years / Milestones with "Phase 1: Preparing | 2026-2028 | Chip tracking; Verification R&D funding", "Phase 2: Implementing | 2029-2030 | Mutual Chip Declaration; Inference-only retrofit; R&D verification", "Phase 3: Improving | 2031-2036+ | Hardware cap & trade; Verification improvements". The milestone-to-phase assignment above is read from the marker x positions against the phase spans in the same SVG, not guessed.

Also worth flagging: this figure and the detailed deal timeline disagree on two dates. The phase strip puts "R&D restarts + total research transparency" at "From August 2029" and "First new frontier release" at "June 2030"; the detailed chart's events JSON has R&D resuming 2029-11-01 and the first release 2030-06-16, and the article's bullet list says Nov to Dec 2029 and Jul 2030. Both source charts are the source's own, so this is an inconsistency in the source, not in the port.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

n/a. The gap is editorial (a missing table), not an exercise.
:::

#### Text
content::
\#### Research titration approaches (ResearchTitrationApproaches)

**Decision: nothing to port.** The chart places four regulatory approaches on a diagonal from easy-and-inaccurate to hard-and-accurate, and the article's four-row table already carries every one of its strings: the approach names, their bodies, their ease and accuracy ranks and the two suggested years. The x and y coordinates behind the diagonal are illustrative layout, not measurements, so an interactive version would invent precision the source does not have.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-plan-a]]

**Where it goes:** n/a. Had one been built it would have gone after `*Table adaptation of the source chart, which places the four approaches on a diagonal from easy and inaccurate to hard and accurate...` (article line 489), inside the collapsed callout "Research Titration: How to control the speed of R&D progress?" (lines 469 to 497).

**What it replaces:** nothing. The four-row table at article lines 491 to 496 stays exactly as it is.

**In XLab:** not an XLab exercise. Source is the AI 2040 verification supplement, `ResearchTitrationApproaches` at source MDX line 407, inside a collapsed detail box.

**Learner time:** 0

Nothing; no widget was built.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Checked against the component (`work/ai2040/lazy-titration.js`) and the rendered `svg-titration.svg`. The four points are: "Safety case burden of proof" at (0.1, 0.93), year "~2035"; "Quality ad-hoc rules" at (0.35, 0.75), no year; "Human-interpretable requirement" at (0.62, 0.5), no year; "Compute caps" at (0.87, 0.2), year "~2030". Axis labels are "Ease of Implementation / How little regulatory competence is required" running Hard to Easy, and "Regulatory Accuracy / How well the approach tracks the correct research speed" running Low to High, with an arrow labelled "Suggested progression".

Two small things the article's table smooths over and which the caption should probably carry: the axis directions are reversed from the usual reading (the ease axis runs Hard on the left to Easy on the right), and the source's arrow is labelled "Suggested progression" rather than by date, so the table's "before safety cases" and "after compute caps" entries in the Suggested timing column are the article editor's rendering of the arrow, not source strings. The source itself only labels "~2030" on compute caps and "~2035" on safety cases.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Field names are written `key: :` so this page parses; join the colons when pasting.

n/a. The table already carries the content; no Lens segment is needed.
:::

#### Text
content::
\#### AI 2027: Epoch LLM inference price chart (ai-2027-inference-prices)

**Decision: widget.** Epoch publishes the exact table behind the figure (119 rows, CC-BY, with fitted values), and an interactive version adds hover values, a benchmark and threshold selector for the 21 series the PNG shows only as three highlighted lines plus grey ghosts, and the yearly decline factor per threshold.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 433, `![](https://ai-2027.com/_next/image?url=%2F_next%2Fstatic%2Fmedia%2FepochLLMprice-nowatermark.824fa343.png&w=3840&q=75)`, replaced on its own line by `![[../widgets/ai-2027-inference-prices]]`. It follows "In response, OpenBrain announces that they've achieved AGI and releases Agent-3-mini to the public." and precedes "It blows the other AIs out of the water. Agent-3-mini is less capable than Agent-3, but 10x cheaper".

**What it replaces:** the image line only (it has no caption in the import). It can go entirely; no fallback needed.

**In XLab:** n/a (imported reading); XLab links to the live site from `<ReadingCard id="ai-2027" ... optional>` in intuitions.mdx line 138

**Learner time:** 3 minutes

Picks a benchmark (MMLU, GPQA Diamond, MATH-500, MATH 5, HumanEval, LMSys Chatbot Arena ELO), switches its performance thresholds on and off, and sees the cheapest model that met each threshold plotted by release date on a log price axis, each with Epoch's fitted trend. Hovering a point or arrowing through the list shows model, date, price per million tokens, benchmark score and the fitted value; a tile per threshold shows the first and last point and the yearly decline factor (9x for GPT-3.5-Turbo-level MMLU, 42x for GPT-4-level GPQA, about 860x for GPT-4o-level GPQA). Done after three benchmarks have been opened.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: Epoch AI data insight "LLM inference price trends", table "Lowest inference prices at fixed performance", https://epoch.ai/data/charts/llm-inference-price-trends/lowest_price_models_data.csv (linked from https://epoch.ai/data-insights/llm-inference-price-trends), retrieved 2026-09-08; CC-BY; prices and scores from Epoch AI and Artificial Analysis. All 119 rows inlined verbatim (Benchmark, Threshold model, Performance range, Model Name, Release Date, USD per 1M Tokens, Predicted log price, Benchmark score). Epoch's sentence quoted in the footer: the rate "varies dramatically depending on the performance milestone, ranging from 9x to 900x per year."
- Interpretation checked, not assumed: the column Epoch names "Predicted log price" holds the fitted price in USD (its first MMLU value is 60.19 against an actual 60.00). Deriving each series' yearly factor from its first and last fitted values reproduces Epoch's own headline numbers (MMLU GPT-3.5 Turbo 9x, GPQA GPT-4 40x, GPQA GPT-4o 900x come out as 9, 42 and 855), so the widget's per-series factors are computed that way and labelled as computed on the page; values of 100x and above are rounded to the nearest 10.
- Not reproduced: Epoch's choice of which three series to highlight and the grey "other benchmarks" ghost lines (the widget shows one benchmark at a time with all its thresholds), Epoch's branding.
- Palette: greys plus the Lens accent; up to five series per benchmark are told apart by marker shape (circle, square, diamond, triangle, cross) and line dash, with the shape repeated in each threshold button.
- No Lens.submit or promptTutor.
:::

#### Widget
source:: [[../widgets/ai-2027-inference-prices]]

#### Text
content::
\#### AI 2027: METR extended time-horizon chart (ai-2027-metr-horizons)

**Decision: widget.** The chart's data are public (METR's Time Horizon 1.1 results file, 26 models with 50% and 80% horizons and 95% CIs; the scenario markers ship as data in ai-2027.com's own page bundle), and an interactive version adds what the Dec 2025 PNG cannot: exact values and intervals on hover, a 50%/80% switch, a trend fit the learner can restrict to 2023 onward and compare with METR's published doubling times, and twenty more models than the PNG names.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 334, `![](https://ai-2027.com/new-metr-extended-nowatermark-inexpandable.png)`, replaced on its own line by `![[../widgets/ai-2027-metr-horizons]]`. It follows the paragraph "Such is roughly the capability progression in AI 2027. Here is a capability trajectory generated by a simplified version of our timelines model (added Dec 2025: ..." and precedes "In AI 2027, these capabilities are sufficient for the AI to be an SC".

**What it replaces:** the image line only. It can go entirely; the paragraph before it already explains that the authors' curves were regenerated in Dec 2025, and the widget's footnote says which of those curves it does not reproduce. If a fallback is wanted, keep the PNG in a collapsed callout titled "The authors' Dec 2025 figure".

**In XLab:** n/a (imported reading); XLab links to the live site from `<ReadingCard id="ai-2027" ... optional>` in intuitions.mdx line 138

**Learner time:** 4 minutes

Sees a log-scale scatter of task length (human work time) against release date for 26 models, GPT-2 to Claude Mythos Preview (early). Switches between the 50% and 80% horizon, toggles 95% intervals and the AI 2027 scenario markers (Agent-0, Agent-1, Agent-2, drawn where ai-2027.com places them on the 80% chart), and picks a trend fit (all points, from 2023 on, off); the page reports the doubling time of the fit next to METR's published 188 days (all-time) and 129 days (from 2023 on). Hovering a point or arrowing through the point list shows the model's release date, both horizons with intervals, average score and SOTA flag. Done after both views are visited and three points inspected.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data 1: METR, Time Horizon 1.1, https://metr.org/assets/benchmark_results_1_1.yaml (linked from https://metr.org/time-horizons/), retrieved 2026-09-08. All 26 `results` entries inlined verbatim (p50 and p80 estimate, ci_low, ci_high in human minutes; average_score; is_sota; release_date), plus the file's `doubling_time_in_days` (187.778 all-time; 128.744 from 2023 on, CI 104.428 to 158.012) and its note that these exclude points with a central p50 estimate above 16 hours. Display names for the yaml's slug keys come from METR's `data/external/release_dates.yaml` (github.com/METR/eval-analysis-public) and, for the four newest models not listed there (Gemini 3.1 Pro, GPT-5.4, GPT-5.3-Codex, Claude Mythos Preview (early)), from the Updates list on metr.org/time-horizons. METR's 8 May 2026 note, quoted in the footer: "Measurements above 16 hrs are unreliable with our current task suite."
- Data 2: scenario markers from ai-2027.com's chart component in `/_next/static/chunks/4979-f40d73c22048fefc.js` (80%-success-rate variant), retrieved 2026-09-08: Agent-0 x 2025.6 y 10, Agent-1 x 2026.5 y 16.7, Agent-2 x 2027 y 22.2, where y indexes the site's label scale ("4 sec" = index 0, each step doubles), so minutes = 4 * 2^y / 60. The site's 50%-variant array gives the agents as explicit strings ("3.2 h", ".6 week", "36 week") but treats a week as calendar seconds while its axis labels are work-time, so it was not used; the markers are shown only on the 80% view, which is also the axis of the article's PNG.
- Computed on the page, and labelled as such: the trend line (ordinary least squares of log2(minutes) on decimal release year over the points shown) and its doubling time. Time-unit conversions for tick labels: 8 h day, 40 h week, 2,000 h year are the AI Futures convention stated in the timelines forecast; 167 h month is 2,000/12 and is my derivation, stated in the footer.
- Dropped, not recoverable from published data: the PNG's five trajectory curves (METR 7-month exponential, the erroneous original curve, "Daniel's mode", "Daniel's median", "Eli's median"), which are central trajectories sampled from the authors' simulation and exist only as an image; the PNG's exact point set (it names 8 models; the widget draws all 26 METR entries, including 8 non-SOTA ones drawn hollow).
- Palette: greys plus the Lens accent, as the brief requires; the dataviz validator flags the greys as low-chroma, so series identity is carried by shape (filled circle, hollow circle, square) and direct labels, not colour.
- No Lens.submit or promptTutor: the article has no exercise here.
:::

#### Widget
source:: [[../widgets/ai-2027-metr-horizons]]

#### Text
content::
\#### AI 2027: superhuman coder arrival chart (ai-2027-sc-forecast)

**Decision: widget.** The figure's numbers are published (the percentiles printed inside the figure and the timelines forecast's summary and May 2025 update tables), and an interactive range chart lets the learner compare three forecasters across five forecasts, including the May 2025 update the PNG predates, with exact percentiles on hover; the PNG shows one method and no update.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 340, `![](https://ai-2027.com/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Fcombined-headline-inexpandable.4c72f6dd.png&w=3840&q=75)`, replaced on its own line by `![[../widgets/ai-2027-sc-forecast]]`. It follows "All forecasters place 2027 as one of the most likely years in which an SC might be developed (added Dec 2025: ..." and is followed by the stray line "ai-2027.com" and the italic "Added Jul 2025" note.

**What it replaces:** the image line only; the stray attribution line "ai-2027.com" under it (line 342) can go too, since the widget carries its own citation. The "Added Jul 2025" note should stay: the widget quotes it. No fallback needed; if wanted, keep the PNG in a collapsed callout "The authors' figure (Apr 2025)".

**In XLab:** n/a (imported reading); XLab links to the live site from `<ReadingCard id="ai-2027" ... optional>` in intuitions.mdx line 138

**Learner time:** 3 minutes

Picks one of five forecasts (time-horizon extension Apr 2025 and May 2025 update, benchmarks and gaps Apr 2025 and May 2025 update, all-things-considered) or "All forecasts", and sees each forecaster's 10th-to-90th-percentile bar with the median dot on a 2025-to-2055 axis, with open arrows for ">2050" and a dashed line at Mar 2027 (the scenario's SC date). Hovering a bar or arrowing through the row list shows the exact percentiles as published and a note on the method. Done after all five forecasts have been opened.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: https://ai-2027.com/research/timelines-forecast, retrieved 2026-09-08. Summary table (median and 80% CI per forecaster and method, including the note that Eli's all-things-considered 90th percentile was edited from 2050 to >2050 four days after publication); the "2025 May 7 update" table (Eli's month-level medians, CIs and modal years for both models, before and after the update); the "Model updates" table (used for the two largest effect sizes quoted in the method notes). Figure percentiles are the text printed in the figure itself (Eli: Dec 2025 / Dec 2028 / >2050; Nikola: Oct 2025 / Oct 2027 / Jun 2044; FutureSearch: Jun 2026 / Jan 2032 / >2050), not read off the curves. Article quotes: "All forecasters place 2027 as one of the most likely years in which an SC might be developed", the Jul 2025 note ("push the median back 1.5 years while maintaining SC in 2027 as a serious possibility", in summary_for_tutor) and the Dec 2025 note ("adjusting for outside of model factors gave us slightly longer medians, e.g. Eli's was 2030").
- Dropped, not recoverable: the probability density curves (simulation output published only as PNG; regenerating them would mean running github.com/uvafan/timelines-takeoff-ai-2027, which I did not do so that every number stays a published one).
- Rendering choices stated in the widget: year-only figures drawn at mid-year, months at mid-month, ">2050" and 2095 as arrows off the axis.
- Uncertain: the one-sentence "about" text for each method (the `about` fields) is my paraphrase of the forecast page's method descriptions, except the quoted sentences from Eli's May 2025 update and the article; cut them if paraphrase is unwanted, the numbers do not depend on them.
- No Lens.submit or promptTutor.
:::

#### Widget
source:: [[../widgets/ai-2027-sc-forecast]]

#### Text
content::
\#### AI 2027: takeoff timeline chart (ai-2027-takeoff)

**Decision: widget.** Every number the figure prints (10th, 50th and 90th percentile per milestone) and the takeoff forecast's summary table (scenario dates, human-only gap estimates, progress multipliers) are published, and stepping through the four milestones with those figures side by side is something the PNG cannot do; the density curves themselves are not published as data and are left out.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 505, `![](https://ai-2027.com/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Ftakeoff-timeline-inexpandable.239e27c0.png&w=3840&q=75)`, replaced on its own line by `![[../widgets/ai-2027-takeoff]]`. It follows "We have substantial uncertainty about takeoff speeds: our model output distributions are below, conditional on SC being achieved in March 2027.[78]" and precedes the stray line "ai-2027.com" and "For more detailed forecasts and reasoning, see our [takeoff supplement]".

**What it replaces:** the image line only; the stray attribution line "ai-2027.com" under it (line 507) can go too. The milestone table above (lines 488 to 494) should stay: the widget repeats its four rows but the table is the article's text. No fallback needed.

**In XLab:** n/a (imported reading); XLab links to the live site from `<ReadingCard id="ai-2027" ... optional>` in intuitions.mdx line 138

**Learner time:** 3 minutes

Steps through SC, SAR, SIAR and ASI with milestone buttons or Previous/Next. A timeline from 2027 to 2035 shows, per milestone, the 10th-to-90th percentile bar and median dot of the forecast (conditional on SC in Mar 2027) and a hollow diamond for the scenario's racing-ending date. The detail panel gives the milestone's definition and four tiles: scenario date, forecast median with its percentiles, the human-only, software-only time to the next milestone, and the AI R&D progress multiplier. Done after all four milestones have been viewed.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: the article's own milestone table (`articles/ai-2027.md` lines 488 to 494: definitions and "Date achieved in scenario, racing ending" Mar / Aug / Nov / Dec 2027) and https://ai-2027.com/research/takeoff-forecast, retrieved 2026-09-08: summary table ("Projected date conditional on SC in Mar 2027 (median + 80% CI)": SAR Jul 2027 (Mar 2027 to Mar 2028), SIAR Nov 2027 (May 2027 to 2034), ASI Apr 2028 (Jun 2027 to >2100); "Human-only, software-only time until next milestone": SC to SAR 15% 0 years, otherwise 4 years (80% CI 1.5 to 10, lognormal); SAR to SIAR 19 years (2.3 to 380); SIAR to ASI 95 years (2.4 to 1,000,000); "AI R&D progress multiplier" 5, 25, 250, 2,000). Figure percentiles are the text printed in the figure (SAR Mar 2027 / Jul 2027 / Mar 2028; SIAR May 2027 / Nov 2027 / Jan 2034; ASI Jun 2027 / Apr 2028 / >2100); Jan 2034 is used for SIAR's 90th percentile where the table says "2034". Quotes in the widget: "the time between a superhuman coder and wildly superhuman capabilities", the ~1 year median sentence, and the article's two numbered forecasting steps.
- Definitions: the article's short definitions are used verbatim (SAR: "The same as SC but for all cognitive AI research tasks."); the research page's longer wording is not repeated.
- Dropped, not recoverable: the density curves (simulation output published only as PNG; not regenerated, see the sc-forecast note).
- Rendering choices stated in the widget: months at mid-month, "2034" at mid-year, ">2100" as an open arrow; SC has no bar because the forecast conditions on it.
- The tile subtitles ("algorithmic progress speedup from AI vs. humans-only") reuse the summary table's column header wording; the trailing "once SC exists" phrasing is mine.
- No Lens.submit or promptTutor.
:::

#### Widget
source:: [[../widgets/ai-2027-takeoff]]

#### Text
content::
\#### AI 2027: neuralese figure from Hao et al. 2024 (ai-2027-hao2024)

**Decision: nothing to port.** The image is the architecture diagram from Hao et al. (Meta, Dec 2024, arXiv 2412.06769) showing language-mode versus latent-mode reasoning; it is a schematic with no underlying dataset, so there is nothing to make interactive.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 286, `![](https://ai-2027.com/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Fhao2024-nowatermark-inexpandable.664af12c.png&w=3840&q=75)`, followed by the caption "Figure from [Hao et al.](https://arxiv.org/pdf/2412.06769), a 2024 paper from Meta implementing this idea."

**What it replaces:** nothing; keep the image and its caption as they are

**In XLab:** n/a (imported reading, not an XLab exercise); XLab links to the live site from an optional ReadingCard in intuitions.mdx

**Learner time:** 0 minutes

Nothing beyond reading: the figure illustrates the "neuralese" section (passing the residual stream back into early layers instead of writing tokens). On ai-2027.com it is also a static PNG.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
No data. Source of the figure: Hao et al., "Training Large Language Models to Reason in a Continuous Latent Space" (arXiv 2412.06769), reproduced by ai-2027.com. Article context read from `articles/ai-2027.md` lines 270 to 300.
:::

#### Text
content::
\#### AI 2027: IDA visualization from Ord 2025 (ai-2027-ida)

**Decision: nothing to port.** The image is Toby Ord's conceptual diagram of iterated distillation and amplification (amplify M0 into Amp(M0), distill into M1, repeat); it encodes a process, not data, so a widget would only redraw the arrows.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-success]] (reading card links to ai-2027.com, not to the article)

**Where it goes:** article line 309, `![](https://ai-2027.com/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Fida-nowatermark-inexpandable.9da7d0c6.png&w=3840&q=75) _Visualization of IDA from [Ord, 2025](https://www.tobyord.com/writing/inference-scaling-reshapes-ai-governance)._`

**What it replaces:** nothing; keep the image and its caption as they are

**In XLab:** n/a (imported reading, not an XLab exercise); XLab links to the live site from an optional ReadingCard in intuitions.mdx

**Learner time:** 0 minutes

Nothing beyond reading: the figure sits under the two-step definition of IDA (amplification, distillation) and before the AlphaGo analogy. On ai-2027.com it is also a static PNG.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
No data. Source: Toby Ord, "Inference Scaling Reshapes AI Governance" (tobyord.com, 2025), reproduced by ai-2027.com. Article context read from `articles/ai-2027.md` lines 300 to 318. The two numbered definitions next to the image are already the text form of what the diagram shows, so nothing is lost by leaving it static.
:::

#### Text
content::
\#### Figures in "Verifying International Agreements on AI: Six Layers of Verification" (Baker et al. 2025)

**Decision: ?.** 

#### Text
content::
\#### Figures in "A system overview for near-term, low-trust AI compute verification" (Cankaya)

**Decision: ?.** 

#### Text
content::
\#### Figures in "Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers" (Egan and Heim)

**Decision: ?.** 

#### Text
content::
\#### Figures in "Governing Through the Cloud: The Intermediary Role of Compute Providers in AI Regulation" (Heim et al.)

**Decision: ?.** 

#### Text
content::
\#### Figures in "Hardware-Enabled Mechanisms for Verifying Responsible AI Development" (O'Gara et al.)

**Decision: ?.** 

#### Text
content::
\#### Figures in "Mechanisms to Verify International Agreements About AI Development" (table edit, published version)

**Decision: ?.** 

#### Text
content::
\#### Figures in "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence" (Scher, Abecassis, Barnett, Abeyta 2025)

**Decision: ?.** 

#### Text
content::
\## Evaluated but not placed

#### Text
content::
\#### Drill Bench: Evidence Streams (drills-supply-chain)

**Decision: nothing to port.** It never belonged to units 3.1.1 or 3.2: `git log a10955c -S'drills-supply-chain' -- src/content/lessons` (which covers the unreachable lineage that `--all` misses) finds it only in the pre-rewrite standalone lesson v-drills-supply-chain.mdx (e3af6f7d, removed 314fe98a) and in human-institutions.mdx (added bdd7b677, removed 54808acc). No revision of covert-red-blue.mdx or covert-taxonomy.mdx embeds any `<VerificationExercise>`; notes/covert-history.md's line that 3.2 embedded drills-supply-chain and drills-primers at 4d65c389 does not hold (that revision's covert-red-blue.mdx contains neither string).

**Target lens:** none in this assignment

**Where it goes:** n/a

**What it replaces:** nothing

**In XLab:** orphaned at HEAD (widget + data at src/components/verification/widgets/drills-supply-chain.tsx and src/lib/verification/data/drills-supply-chain.ts, a DrillDeckView deck; registry title "Drill Bench: Evidence Streams" at cbd2f3ee); not embedded by any current lesson

**Learner time:** n/a

Not evaluated here beyond identification: it is a drill deck (pick, multi, number and text steps with reveals) on evidence streams, the same kit as drills-primers, which is already ported. If the W08 agent or Elias wants it, the drills-primers port is the template and the data file is complete at HEAD.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Nothing built. Historical trace only, from the XLab clone at HEAD 93847c7 with a10955c and its lineage resolvable from the pack.
:::
