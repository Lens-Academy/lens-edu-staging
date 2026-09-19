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
\## Part 2 · Week 8: The human layer

Module file: [[../modules/XLab Verification Part 2 W08 The human layer]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-human-insiders]]

Two candidates for one slot. XLab retired the Insider Report drill on 2026-08-14 and now runs Construct the Case under the same exercise id; the Lens page still reproduces the retired drill. Pick one.

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
\## Part 2 · Week 10: Evasion routes and the red team review

Module file: [[../modules/XLab Verification Part 2 W10 Evasion routes and the red team review]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-covert-red-blue]]

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

