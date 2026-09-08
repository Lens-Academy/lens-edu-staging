---
id: '6f0d2b9e-3c1a-4e7b-9a52-8d4c1f6e2b73'
title: "Widget Gallery: Compute Verification Parts 1 and 2"
tldr: "Every interactive built for the two Compute Verification courses, live on one page, each with the lens it belongs to, the spot it goes in, and what it replaces. 36 widgets, 5 places where our own question segments are enough, 12 skips."
summary_for_tutor: "An internal review page for course authors, not learner material. It lists every widget ported from XLab's Verification track or built for an embedded reading, ordered by module and lens, with placement instructions. If someone asks, explain that this is a staging gallery and that none of these widgets is placed in the course yet."
tags: [wip]
duration_minutes: 90
---

#### Text
content::
This page collects every interactive built for Compute Verification Parts 1 and 2 from XLab's Verification track and from the readings the course embeds. Nothing here has been placed in the course yet. Each entry says which lens it belongs to, where in that lens it goes, and what it would replace, so placement is a copy-paste decision per entry. Entries marked native say that our own question segments already do the job, with the proposed segment text in a collapsed note. Entries are ordered by module and lens. Every widget below is live: try it.

#### Text
content::
\## Part 1 · Week 1: Why verification

Module file: [[../modules/XLab Verification P1 W1 Why verification]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-introduction]]

#### Text
content::
\#### The Verification Problem (verification-problem)

**Decision: widget.** Already ported (LENS/widgets/verification-problem.md); this note covers placement and a data-drift check only, no rebuild.

**Target lens:** [[../Lenses/XLab Verification - v-introduction]]

**Where it goes:** inside the Text segment "Preventing ASI via International and Verifiable Agreements", right after the paragraph ending "But in this state of competition and distrust, how do rivals enforce such agreements?"; split the Text segment there and insert the Widget segment before the Text segment beginning "In short, verification is the set of mechanisms that makes inter-party agreements credible".

**What it replaces:** the four open callouts "Trust?", "Punish violations?", "Mutual transparency?", "Neutral, privacy-preserving verification mechanisms?" that follow that paragraph. They reproduce the widget's four option details word for word (the last one prefixed with "It holds."), so they should go entirely; the widget's own outcome labels ("It collapses", "It arrives too late", "It backfires", "It holds") carry the verdicts.

**In XLab:** <VerificationExercise id="verification-problem" /> in introduction.mdx, core, not inside a Fold

**Learner time:** 5 minutes

Reads the framing ("Two rivals. One treaty. Zero trust.") and the prompt, then tests each of the four answers by clicking its card. Each opens a verdict panel (failure mode or the answer that holds) with XLab's explanation; inspected cards keep an "Inspected" mark. Nothing gates completion.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Diffed the widget's OPTIONS array and header strings against XLab `src/lib/verification/data/verification-problem.ts` at commit 1e8b150 (2026-08-20), the latest change to that file, with a script (OUT/qa/diff_ported.mjs). All four options (label, question, summary, outcome, holds, detail) are identical. Eyebrow, title and lede are identical. The prompt's em dash (between "obligations" and "and how does it know") is rendered as a comma in Lens, the one permitted rewrite. No drift; no corrected copy written.
- Observation, not drift: the ported widget makes no Lens SDK calls (no saveState, complete or restore), so the tutor sees only `summary_for_tutor` and a learner's inspected marks are lost on reload. XLab's component also has no completion condition, so this mirrors XLab; adding saveState with "inspected: ..." would be a small improvement if wanted.
:::

#### Widget
source:: [[../widgets/verification-problem]]

#### Text
content::
\#### The Types of AI (types-of-ai)

**Decision: widget.** Already ported (LENS/widgets/types-of-ai.md); this note covers placement and a data-drift check only, no rebuild.

**Target lens:** [[../Lenses/XLab Verification - v-introduction]]

**Where it goes:** after the Text segment paragraph ending "Throughout this course, we will use the term ASI to refer to AI with dangerous capabilities that pose a material existential threat to humanity."; the Widget segment sits between that Text segment and the Text segment beginning "Even the people in charge of developing superintelligence".

**What it replaces:** the collapsed callout "Optional: The Types of AI" at the end of the first Text segment (a numbered prose list of the seven levels with their examples plus the "non-narrow AI remains theoretical" line). The callout is a prose reproduction of the widget data; remove it, since the widget shows every level, example and "why here" explanation. Because XLab marks this exercise optional, keep the "Optional" signal somewhere: either a one-line Text segment "Optional: The Types of AI" above the widget, or leave the callout collapsed with only its first sentence and the widget below it.

**In XLab:** <VerificationExercise id="types-of-ai" /> in introduction.mdx, optional, inside <Fold label="Optional: The Types of AI">

**Learner time:** 5 minutes

Taps rings of a concentric diagram (AI, Narrow AI, Machine Learning, Deep Learning, Generative AI, Large Language Model, Transformer LLMs) or the example systems placed in each ring (Roomba, Deep Blue, FaceID, Midjourney, Mamba, Claude, ...) to read what each is and why it sits at that ring and not the next one in. Two buttons in the side panel explain the grey margin outside the rings (theoretical-only and possible-but-absurd non-narrow AI). Nothing gates completion.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Diffed AI_LEVELS, AI_REGIONS and the prompt string against XLab `src/lib/verification/data/types-of-ai.ts` at commit b68d6cd (2026-08-25), the latest change to that file, with a script (OUT/qa/diff_ported.mjs). Every level name, blurb, example name, "what" and "why" string is identical apart from nine em dashes that Lens renders as colons, commas or periods (the one permitted rewrite). AI_REGIONS and the prompt are identical. The panel strings from the component ("Beyond real AI", "Level", "Why here", "Back to level", "AI that is not narrow, out in the grey margin. Tap to read.", "Tap a system in this ring to see why it sits here, not one ring deeper.") match XLab's component at b68d6cd. No drift; no corrected copy written.
- Observation, not drift: XLab's component (b68d6cd) also has zoom in / zoom out / reset buttons and drag-to-pan over the diagram, which the Lens port lacks; on a phone the innermost rings' example pills are small without it. The Lens port also makes no Lens SDK calls (no saveState or complete), matching XLab, which has no completion condition for this widget.
:::

#### Widget
source:: [[../widgets/types-of-ai]]

#### Text
content::
\#### Why Are We Concerned About Superintelligence? (what-do-they-say)

**Decision: widget.** Six profile cards with an open-one-at-a-time detail panel, read-tracking and a tutor-visible record of which profiles were opened beat six long collapsed callouts; the grid of teasers lets the learner compare the six positions before reading any of them.

**Target lens:** [[../Lenses/XLab Verification - v-introduction]]

**Where it goes:** after the Text segment "Even the people in charge of developing superintelligence, who have the most incentive to obfuscate ... Hear what the top AI figures have to say:"

**What it replaces:** the Text segment holding six collapsed callouts (Sam Altman, Dario Amodei, Demis Hassabis, Shane Legg, Ilya Sutskever, Jan Leike). The widget carries every sentence and every source link of those callouts verbatim, so the callouts should go entirely; keeping them as a fallback would show the same 1,300 words twice.

**In XLab:** <VerificationExercise id="what-do-they-say" /> in introduction.mdx, core, not inside a Fold

**Learner time:** 8 minutes

Sees a two-column grid of six cards (initials avatar, name, role, one-line teaser, "View profile"). Opening a card shows the profile below the grid: Definition (or The term / Background), Risk statements, a highlighted "Relevance to this module" paragraph, and source links that open in a new tab. Opened cards get a "Read" mark and the counter climbs to "6 of 6 profiles read"; the widget saves which profiles were read and reports completion when all six have been opened.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data source: XLab `src/lib/verification/data/what-do-they-say.ts` at commit 1e8b150 (2026-08-20); component `src/components/verification/widgets/what-do-they-say.tsx` at 05e7925. All names, roles, initials, teasers, section labels, paragraphs and source labels/URLs are verbatim. The `<q>` and `<em>` markup inside XLab's paragraph HTML is rebuilt as elements (no innerHTML); `<q>` renders with the browser's quotation marks, matching the quoted phrases in the Lens callouts.
- Photos dropped, initials avatars used (XLab's `initials` field) because XLab serves the portraits from `public/verification/assets/what-do-they-say/`, which cannot ship to Lens. The photo credit line ("Portrait: Wikimedia Commons") is dropped with them. XLab's `photoSource` fields point at Wikimedia `Special:FilePath` URLs for five of the six (Leike has none); hotlinking those would restore the portraits if wanted, at the cost of a Wikimedia dependency.
- Cross-references adapted (the only deliberate text change): XLab's "taken up in 0.2.3 (compute vs. capability)" and "(0.2.3)" refer to XLab's own lesson numbering, which does not exist on Lens. The widget uses the wording the Lens callouts already use, "1.0.1 Drawing the Line: Compute vs. Capability", as plain text (a widget cannot carry a wikilink). Likewise Leike's "the first policy bucket in 0.2.2, voluntary self-governance" is shortened to "voluntary self-governance", again matching the Lens callout. Revert to XLab's wording by editing three strings if verbatim is preferred.
- Modal dialog replaced by an inline panel below the grid (a modal inside the auto-height frame would not size correctly). Close button returns to the grid.
- Completion: XLab's component has no onComplete; the widget calls Lens.complete() once all six profiles have been opened, so `required:: true` is usable on the segment.
- Eyebrow line "Six leaders, in their own words" and the h1 (XLab's registry title for this exercise) are the only strings not in the data file.
:::

#### Widget
source:: [[../widgets/what-do-they-say]]

#### Text
content::
\#### A Short History of AI Acceleration (short-history)

**Decision: widget.** A zoomable, pannable timeline and a six-series line chart with hover readout, series toggles and a data table are things two static OWID images cannot do; XLab's file holds all the data for both charts, so both are drawn, nothing is linked out for lack of data.

**Target lens:** [[../Lenses/XLab Verification - v-introduction]]

**Where it goes:** replaces the collapsed callout "Optional: A Short History of AI Acceleration" at the end of the Text segment that begins "Most notably, over 1,300 employees of frontier AI companies have signed a public statement"; the Widget segment goes right after that Text segment (after "It's clear that ASI is no longer a hypothetical risk. It will require deliberate and proactive action by labs and governments alike to avoid.") and before the "Preventing ASI via International and Verifiable Agreements" Text segment.

**What it replaces:** the collapsed callout holding the intro sentence, two hotlinked OWID chart images and the credit line. The widget carries its own "Optional" eyebrow, the intro sentence, both charts and the OWID credit with link, so the callout should go entirely. If the editors want the "Optional" collapse behaviour kept, the callout can stay with just its first sentence and the OWID link, followed by the Widget segment.

**In XLab:** <VerificationExercise id="short-history" /> in introduction.mdx, optional, inside <Fold label="Optional: A Short History of AI Acceleration">

**Learner time:** 5 minutes

Zooms into the 1940 to 2060 timeline (four zoom levels, plus and minus buttons or keys) and drags or pans along it to read the six milestone annotations (1945 first digital computers, Theseus, Perceptron Mark I, TD-Gammon, AlexNet, 2024 human-comparable language and image recognition). On the test-scores chart they hover or step year by year to read each capability's score relative to human performance, hide and show series with the legend buttons to isolate one line, and can open a data table of all points. A status line shows when both figures have been explored; that is the completion condition.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data source: XLab `src/components/verification/widgets/short-history.tsx` at commit 1e8b150 (2026-08-20). Timeline geometry (viewBox 900 by 330, axis at y 272, 1940 to 2060, boundary 2024, annotation positions), the four zoom factors, the six milestone texts, the six series with every data point, plot geometry (1998 to 2023, 25 to minus 100), grid values, x ticks, the "Human performance, as the benchmark, is set to zero" note, both figure captions, the description paragraph and the OWID credit text are verbatim.
- Em dash rewrites: the two em dashes in the AlexNet annotation (around "a neural network with many layers") became commas; the em dash in the OWID article title (between "Changed Fast" and "What Might Be Next?") became a comma, the same rewrite the Lens callout uses.
- Colours changed: XLab's series colours are theme tokens whose fallbacks fail a colour-vision check (#946b00 vs #bf4f00, deutan ΔE 1.8; #1a1614 is below the chroma floor). Replaced by a six-slot categorical palette that passes the dataviz validator on white (#2a78d6, #eb6834, #1baf7a, #eda100, #e87ba4, #008300; contrast warning on three, mitigated by direct labels, dash patterns and the table view). Assigned in the fixed order of XLab's series list. XLab's per-milestone name shading (accent mixed toward foreground) is dropped; names are plain text colour. Chart series colours are data encoding, not chrome, which is why the "greys plus one accent" rule is not applied to them.
- Interaction kept: viewBox zoom and pan with drag, arrow keys, Home, plus and minus; pan buttons and "Whole timeline" appear only when zoomed; year range readout. Crosshair, per-series dots (smaller and faded when interpolated between data points), tooltip with values sorted by score, legend toggles that refuse to hide the last visible series, "Show all six".
- Added beyond XLab: an HTML legend button row (XLab toggled series by clicking the SVG labels; the Lens rule wants buttons), "Earlier year" / "Later year" / "Clear year" buttons and arrow keys on the chart so the readout is reachable without a mouse, a "Show data table" toggle, a status line, and a completion condition (XLab has none): complete when the timeline has been zoomed at least once and a year has been inspected or a series toggled or the table opened.
- At widths up to 640px both plots keep a minimum width and scroll sideways inside their own box; the tooltip pins full-width under the chart top instead of flipping off-screen.
- The XLab lesson's own intro line ("How fast is fast? Two charts from Our World in Data's brief history of artificial intelligence show the pace.") is included as the widget's lede, without the inline link; the OWID link is in each figure's credit.
:::

#### Widget
source:: [[../widgets/short-history]]

#### Text
content::
\#### The Verification Landscape (verification-landscape)

**Decision: widget.** Already ported (LENS/widgets/verification-landscape.md); this note covers placement and a data-drift check only, no rebuild.

**Target lens:** [[../Lenses/XLab Verification - v-introduction]]

**Where it goes:** inside the last Text segment, after the paragraph "Verification for AI is a young field, and it is not spread evenly. Some corners are crowded with research; others are nearly empty. This map lays the work out along two axes ..." (XLab's lead paragraph); split the segment there so the Widget segment sits before the closing paragraphs "One pattern jumps out fast. The field's center of gravity is the think-tank and nonprofit column ...", "That unevenness is the opportunity ..." and the italic snapshot disclaimer, which are XLab's foot1, foot2 and disclaim copy and are not inside the widget, so they stay as prose after it.

**What it replaces:** the activity-level table (6 rows by 4 columns of 0 to 3), the "Rows (kind of verification)" and "Columns (who does the work)" definition paragraphs, and the six collapsed callouts (one per row, four bullets each). All of it is the widget's data rendered as prose, so it should go entirely. Drop the sentence "Activity levels: 0 = no activity yet, 1 = emerging, 2 = active, 3 = concentrated." from the lead paragraph as well, or keep it: the widget's legend says "Less activity / More activity" and each square carries its number.

**In XLab:** <VerificationExercise id="verification-landscape" /> in introduction.mdx, core, not inside a Fold

**Learner time:** 10 minutes

Reads a heat-map grid of six kinds of verification against four kinds of actor. Tapping a square opens a panel with the activity level, a state-of-play sentence, the named efforts (RAND, CNAS, FlexHEG, METR, Apollo, US BIS, ...) and a "How it connects" line; tapping a row or column label explains that axis. The empty government square for cryptographic methods is flagged "Open gap". Nothing gates completion.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Diffed ROWS, COLS, HEATWORD and all 24 CELLS (level, state, efforts, connect, gap) against XLab `src/lib/verification/data/verification-landscape.ts`, and the in-square organisation marks against `src/lib/verification/data/landscape-logos.ts` (ORG_MARKS token list and CELL_ORGS extras), both at commit 1e8b150 (2026-08-20), the latest change to those files, with a script (OUT/qa/diff_ported.mjs).
- One text difference, intentional and not drift: inst × industry "How it connects" reads "the “self-governance” end of Module 0's policy spectrum" in XLab and "the “self-governance” end of the policy spectrum" in Lens. "Module 0" is XLab's lesson numbering, which does not exist on Lens; the rest of the sentence is verbatim. Everything else, including every activity level and every effort title and body, is identical. The legend, prompt, axis tags and "How it connects" strings match LANDSCAPE_COPY. No corrected copy written.
- Organisation marks: the 20 token-matched marks and the seven per-cell extras (COSIC, Waterloo CACR; EZKL, Modulus Labs, Giza; FAS, Epoch AI; IEA; CSER; FLI, Chatham House, Simon Inst.; Stanford CRFM, MLCommons) are the same set as XLab's. Two cosmetic differences: XLab orders marks by its master list (so monitor × think tanks shows "Epoch AI, FAS", Lens shows "FAS, Epoch AI"), and XLab's square aria-labels use long names ("RAND Corporation") where Lens uses the short marks. XLab's organisation logo icons (`/verification/logos/icons/`) are not used by either version's grid, so nothing is lost there.
- XLab's LANDSCAPE_COPY eyebrow ("Module 0 · Section 0.1 · Field map"), title, kicker, lead1, lead2, foot1, foot2 and disclaim are page prose in XLab's component too; the Lens page carries lead1, foot1, foot2 and disclaim as prose and drops the module eyebrow. lead2 ("Tap any square to see who is working there ... Reading the heat is the point: notice which corner is dark, and which is blank.") appears nowhere on Lens; consider adding it as the last sentence of the lead paragraph above the widget.
- Observation, not drift: the ported widget makes no Lens SDK calls (no saveState or complete); XLab's component has no completion condition either.
:::

#### Widget
source:: [[../widgets/verification-landscape]]

#### Text
content::
\## Part 1 · Week 1: We need more theories of change

Module file: [[../modules/XLab Verification P1 W1 Theories of change]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-theories-of-change]]

#### Text
content::
\#### Theory of Change for Your Favorite AI Safety Organization (theories-of-change)

**Decision: widget.** Already ported (the Lens demo widget); this pass places it, fixes the em dash, and records drift against XLab. The lesson's static table and the Slow Food image are SKIP (see Fidelity).

**Target lens:** [[../Lenses/XLab Verification - v-theories-of-change]]

**Where it goes:** after "Now that you've seen some exemplary examples of robust theories of change, try building your own!" (the collapsed callout "Optional: Theory of Change for Your Favorite AI Safety Organization"), in place of the `#### Question: Open` segment `dc502432-39f8-4a75-99ff-e43532b1ed5d`

**What it replaces:** one optional `Question: Open` segment whose prompt lists the eight boxes as a bullet list and whose assessment/feedback instructions grade outputs-vs-outcomes and if-then links. Replace it entirely; the widget has its own `Lens.submit` scoring and a promptTutor review, so a second free-text answer box would be a duplicate. Keep the intro callout, but change it from `collapse="closed"` to an open callout or plain paragraph: a widget cannot sit inside a callout, so a closed callout followed by a visible widget reads oddly. Carry the Question segment's better assessment/feedback text over to the widget in a later pass (see Fidelity).

**In XLab:** `<VerificationExercise id="theories-of-change" />` in theories-of-change.mdx, optional, inside `<Fold label="Optional: Theory of Change for Your Favorite AI Safety Organization">`

**Learner time:** 15 minutes (optional; needs a quick look at the organisation's public material)

Names an AI safety organisation, then fills eight boxes one at a time in a guided editor (Inputs: what do we need; Outputs: what do we do, who do we reach; Outcome: short-term, intermediate, long-term; Assumptions; External factors). Each entry appears in the canvas grid above the editor, and any cell can be clicked to jump back to it. When all eight boxes have text the widget calls `Lens.complete()` and offers "Score my canvas" (`Lens.submit`), "Get feedback on the score" and "Ask the tutor to review it" (`Lens.promptTutor`). Entries persist through `Lens.saveState`; standalone, nothing is persisted (no localStorage fallback in the existing demo).

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Source: XLab has no `src/lib/verification/data/theories-of-change.ts`; the curriculum (the eight boxes with band, label and cue) is inlined in `src/components/verification/widgets/theories-of-change.tsx` at HEAD (last touched in commit cbb8162). The same eight labels and cues appear as the `<table>` in `src/content/lessons/verification/theories-of-change.mdx` lines 34 to 68. The Lens widget's BOXES array matches the component word for word (band, label, cue, ids).

Change made in this pass: line 188, the empty-cell placeholder (a single em dash character) is now `"(empty)"` (same word the widget's own tutor summary uses for an unfilled box). Nothing else was changed, including the frontmatter, which has no `height:` field (the platform default is `auto`; add `height: auto` if the orchestrator wants the frontmatter to match the brief's shape).

Drift between the Lens widget and XLab's component (all pre-existing, not fixed here because the assignment says do not rebuild):
- Framing copy is Lens-authored: eyebrow "Exercise", heading "Build a theory of change", lede "Pick an organisation, real or imagined, that works on AI verification..." XLab's Fold text says "Pick your favorite AI safety organization and fill out the below table based on publicly available information". The Lens lede narrows the choice to AI verification organisations and drops the "publicly available information" instruction. Suggest aligning the lede with XLab's sentence.
- Organisation field: Lens label "Organisation", placeholder "e.g. a treaty verification body, a chip-tracking startup, a research lab". XLab: label "Your organization", placeholder "Epoch, MIRI, The Midas Project, …".
- Editor: XLab shows an eyebrow "Box N of 8 · Band"; Lens shows the band name only. XLab's textarea placeholder "Fill in this box, then move to the next one." is absent in Lens. XLab's buttons are "Back" / "Next" (Next disabled on the last box); Lens has "Back" / "Next box", which becomes "Done" on the last box.
- Grid layout: XLab is one row of six columns (Inputs 1, Outputs 2, Outcome 3) with a 640px min width that scrolls; Lens uses a two-row arrangement (Inputs 2, Outputs 2, Outcome 2, then Intermediate and Long-term under Short-term) that reflows to two columns at 600px. Same cells, different shape.
- Completion: XLab's component ignores `onComplete` (never completes). Lens calls `Lens.complete()` when all eight boxes and the organisation name are filled. This is a Lens addition, and a reasonable one.
- Scoring and tutor: XLab has no scoring, feedback or discuss moment. The Lens "Score my canvas" (`Lens.submit`), "Get feedback on the score" and "Ask the tutor to review it" (`Lens.promptTutor`) are Lens demo additions. Their assessment and feedback instructions are Lens-authored, not from XLab. The `Question: Open` segment on the lens page carries better-targeted instructions (outputs written as outcomes, links that are not if-then claims); when the widget is next rebuilt, move those instruction texts into the widget's `Lens.submit` call.
- Standalone: XLab persists to `localStorage` (`v-theories-of-change:v1`); the Lens widget has no localStorage fallback, so in the editor preview entries are lost on reload. The brief asks for that fallback; add it on the next rebuild.
- Lens page table: the lens's prose reproduction of XLab's table rewrites the outcome headers as "What changes first? / What changes next? / What is different in the end?" and adds "What must hold for the chain to work? / What is outside your control?"; XLab's table (and the widget) use "Short-term / Intermediate / Long-term" and "Internal / testable", "External / undefined". Not a widget matter, but the page and the widget now disagree on the labels; align the table to the widget's labels.

Lesson table (mdx lines 34 to 68) and Slow Food image (line 86): SKIP.
- The table is a static reference of the eight elements; the widget's canvas is that same table made editable, so a second table widget would duplicate it. Building a "strong theory of change" checklist the learner applies to an organisation would need criteria XLab never wrote as data (the closest is one sentence about Apollo: "names specific causal mechanisms, states explicit assumptions, and acknowledges failure modes", plus the outputs-vs-outcomes and if-then paragraphs); any checklist would be invented curriculum, which the brief forbids. Prose and the existing widget cover it.
- The Slow Food image is a figure: nothing changes when the learner interacts, and an annotated clickable version would require inventing region labels beyond XLab's alt text. Keep it as an image. Note the lens currently hotlinks `raw.githubusercontent.com/XLabTracks/tracks/main/public/...`; there is already a pending suggestion on the page to link the original Slow Food page instead.
:::

#### Widget
source:: [[../widgets/theories-of-change]]

#### Text
content::
\## Part 1 · Week 1: Building verification intuitions

Module file: [[../modules/XLab Verification P1 W1 Building verification intuitions]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-intuitions-drills-1]]

#### Text
content::
\#### Drill Bench: Primers (drills-primers)

**Decision: widget.** Six commit-then-reveal steps (four pick, one nine-term mark-exactly-three with per-item caught/missed/false-flag verdicts, one fixed-order syllogism) with a progress meter and a finish screen; Lens Choice segments have no reveal, no per-item verdicts and no gate between commit and explanation.

**Target lens:** [[../Lenses/XLab Verification - v-intuitions-drills-1]] (also [[../Lenses/XLab Verification - v-intuitions-drills-2]] and [[../Lenses/XLab Verification - v-intuitions-drills-3]], see Replaces)

**Where it goes:** after the opening Text segment "The primer bench: inspection games, credible commitment, and two-level games. Commit an answer before each reveal, read why, then continue. Nothing here is graded." in v-intuitions-drills-1; it replaces everything below that segment.

**What it replaces:** six ungraded Choice segments (ids b9535676..., 275e6f04..., 43fbcb43..., 357a36a9..., bb588dec..., 3a2eb99c...) each followed by a collapsed "Why (open after you have answered)" callout. Remove all twelve segments entirely; the widget carries every question, option and explanation, and a fallback callout would let a learner read the key before committing, which defeats the drill. Suggested segment: `#### Widget` / `source:: [[../widgets/drills-primers]]` / `required:: true` (the lens has no other exercise, so without `required` a learner can complete it without touching the bench). v-intuitions-drills-2 and v-intuitions-drills-3 are one-paragraph redirect stubs ("This section now lives in the complete exercise"), are not listed in the module file, and hold no content: delete them or leave them; nothing to place there. One widget, not three: XLab's deck has a single bench ("Primer bench") of six steps with one progress meter and one finish condition, so it has no natural split; the earlier three-way Lens split was an artefact of the first port and has already been consolidated into drills-1.

**In XLab:** <VerificationExercise id="drills-primers" /> in intuitions.mdx, on its own "Drill bench" PageBreak inside the lesson's "Optional: Exercises and Further Reading" section (after the curated readings), not inside a Fold. Bridged (completion tracked). Note the Lens module lists v-intuitions-drills-1 without `optional:: true`; XLab treats the bench as optional.

**Learner time:** 6 minutes (XLab's own "~6 min")

Opens the bench from a one-card menu (deck title, blurb, "~6 min · 0 / 6"), then works through six steps in order with a segment meter showing progress. In a pick step they click one option; the options lock, the key is labelled "key" and their pick "yours", a verdict line ("Match, and here is the reasoning:" or "Not quite. The key says: ...") and the explanation appear, and a Continue button advances. In the nine-term step they toggle terms until exactly three are marked (the hint reads "marked N, mark exactly 3", the Commit button stays disabled otherwise), then every term is shown in authored order with its verdict (caught / missed / false flag / clean) and note, plus the closing explanation. After the sixth "Finish bench" the finish screen shows "Done: 6 / 6", "Every bench in this module is complete." and a two-tap "Redo bench"; the menu offers a two-tap "Reset this deck" once anything is answered.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: SCRATCH/xlab-tracks/src/lib/verification/data/drills-primers.ts (HEAD), every string verbatim; automated check confirms all 65 string literals from the data file appear in the widget after dash normalisation. UI strings (menu line, verdicts, hints, "Commit the marks", "Finish bench", "Redo bench", "Sure? Tap again", "Every bench in this module is complete.") from src/components/verification/kit/drill-deck.tsx; scoring and commit rules from src/lib/verification/engines/drills.ts; shuffle ported line for line from src/lib/shuffle.ts (FNV-1a + mulberry32, seed `primers#<pos>`, true/false pairs unshuffled, `fixedOrder` honoured on the syllogism). Resulting orders: step 4 shows authored options 3,0,1,2; step 5 shows items 7,1,0,5,2,4,3,6,8; steps 1 to 3 and 6 are in authored order. Keys compare against authored index, never display position.
- Em dashes replaced (the only rewrite): blurb and kicker (comma / colon), menu line ("Commit before every reveal: the commit is the exercise."), step 1 why ("False, and the word..."), step 2 statement and why ("...without any court, but..."; "no detection, no deterrence; verification is upstream..."), step 3 statement ("defected, involuntarily"), step 4 q and why, five item notes in step 5, step 6 brief and why, verdict strings ("Match, and here is the reasoning:", "Not quite. The key says:"), hint ("marked N, mark exactly 3"), finish title ("Done: 6 / 6"). XLab's dash marker on unpicked non-key options is rendered as an empty tag instead.
- Adapted: XLab stores only done flags (choices live in component state and vanish on reload). The widget also stores the committed pick / marks so a restored page shows the same reveal and so the tutor summary can say what was picked and whether it matched. State: `{benches: {primers: [{done, pick, marks}, ...]}}`; unknown or out-of-range values are pruned on restore. Lens.complete() fires when all six steps have been continued through (XLab's deckComplete), once per page load unless meta.completed. Redo and Reset behave as in XLab (two-tap confirm; Redo clears the bench, Reset clears the deck) and save state. Standalone (no window.Lens) falls back to localStorage key `lens-drills-primers:v1`.
- Not built: number and text step types (the engine supports them, this deck has none); the "All benches" button (XLab hides it for a single-bench deck). Icons replaced by text glyphs (✓, ✕, ⚑, ↺, ◉, →).
- Drift found in the Lens drills lenses versus XLab: (1) deck title, blurb, kicker and "~6 min" card are absent; (2) step 5 brief cut from "Nine terms, deliberately over-stocked the way the source round stocks its lists: randomized inspection · ... · Schelling focal point." to "Nine terms, deliberately over-stocked."; (3) step 6 brief and question were merged and reordered ("Which conclusion follows necessarily? The full answer is ... the reveal below describes...") whereas XLab shows the brief first, then the question; (4) the Lens Choice segments carry no `[x]` key, so nothing is checked and the "Why" callouts can be opened before committing; (5) the step 5 feedback-instructions in Lens group "cheap talk" under commitment credibility and "ratification constraint" under coordination, which XLab's notes do not (XLab: cheap talk is "the opposite of everything Fearon and inspectors trade in", ratification constraint is "Two-level games"); the widget uses XLab's notes. All other question, option and explanation text matches XLab apart from dash and quote normalisation.
- Uncertain: whether the module should mark v-intuitions-drills-1 `optional:: true` to mirror XLab's placement in the optional section; left for the orchestrator.
:::

#### Widget
source:: [[../widgets/drills-primers]]

#### Text
content::
\## Part 1 · Week 2: History, precedents, parallels

Module file: [[../modules/XLab Verification P1 W2 Precedents and policy scope]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-precedents]]

#### Text
content::
\#### Tasks on the Document Packet (packet-tasks)

**Decision: native question segments are enough.** Five free-writing tasks with a marking key and a reveal after commit are exactly what Lens `Question: Open` with `assessment-instructions::` and `feedback-instructions::` already does, and the lens page already carries all five in that form; a widget would only add a live word counter and an honor-system lock on the reveal callouts, at the cost of a second, non-native text box per task.

**Target lens:** [[../Lenses/XLab Verification - v-precedents]]

**Where it goes:** "Read Documents 1–3. Complete Task 5 and any one of Tasks 1–4." (the `#### Text` segment titled "The tasks"); the five `Question: Open` segments that follow it are the port.

**What it replaces:** nothing to replace. The five `Question: Open` segments (Task 1 to Task 5) plus their collapsed "model answer" and "Baker (2023) on Task N" callouts already reproduce every task, model answer and Baker excerpt from XLab's data file. Keep all of it; the collapsed callouts stay as the reveal fallback for a learner who skips the AI feedback.

**In XLab:** <VerificationExercise id="packet-tasks" /> in precedents.mdx, core, not inside a Fold (it is the lesson's only exercise; XLab's registry marks it bridged: the lesson completes when Task 5 plus any one of Tasks 1 to 4 is submitted).

**Learner time:** 45 minutes (Task 5 at 300 words plus one optional task at 200 words, after reading the three documents; the lens sets 75 minutes for the whole page)

Reads Documents 1 to 3 (IAEA safeguards, Shavit's compute-monitoring proposal, Carlson on Iraq), then writes Task 5 (required, max 300 words: evaluate the "chip registration can verify no prohibited AI development" conclusion in four numbered steps) and at least one of Tasks 1 to 4 (optional, max 200 words each: object and purpose of safeguards; division of labour among Shavit's three components; three conditions for the analogy; why Iraq was missed). In XLab each task has one textarea, a live word count against the ceiling (guidance, never enforced), and a Submit button that reveals the indicative answer and then Baker's own words on the same ground; the box stays editable after submitting. On Lens the same happens through the assessor (marking key in `assessment-instructions::`) and the tutor (Baker excerpts in `feedback-instructions::`), with the model answer and Baker callouts collapsed underneath for reading afterwards.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Data sources: `xlab-tracks/src/lib/verification/data/packet-tasks.ts` (tasks, model answers, Baker cuts, word ceilings, compulsory flag) and `src/lib/verification/data/nuclear-disanalysis.ts` (BAKER citation, BAKER_DIFFERENCES, BAKER_QUALIFIED_OPTIMISM, DisanalysisQuote type), both at HEAD (93847c7); component `src/components/verification/widgets/packet-tasks.tsx` (behaviour, completion rule; its design comment at commit e8397d0 spells the rule out: "onComplete fires once, when her rule is met, Task 5 submitted plus any one of Tasks 1 to 4").

Checked the lens text against every string in packet-tasks.ts (118 strings, normalised for quotes and dashes): all task copy, all model-answer copy and all Baker quotes are present. Two Baker fragments are absent from the Task 4 callout and could be added if wanted: the block label "The main line of the key" (a heading, not curriculum) and the §5.2 framing sentence "How did CSA negotiations come to leave such a massive gap in their M&V system? Experts propose the following explanations (though typically with little to no citation/evidence) for why CSAs had very limited capacity for detecting undeclared nuclear facilities: negotiators had tended to think that:". Everything else matches, em dashes replaced.

What the native form cannot do, and is not built: (1) XLab's completion rule (Task 5 plus any one of Tasks 1 to 4). Lens gates on Task 5 only (`optional:: true` on Tasks 1 to 4) and states the "any one" rule in prose; a widget could fire `Lens.complete()` on the exact rule, which is the one real fidelity gain a widget would bring. (2) The live word counter: `Question: Open` has `max-chars::` only, and XLab's ceilings are in words, so no number is proposed; the ceiling stays in the task title text as "(max 200 words)" / "(max 300 words)", matching XLab's "guidance, never enforced". (3) Reveal locked until commit: the callouts are collapsed and titled "open after you have answered"; the assessor-plus-tutor path delivers the same reveal after a real submission.

Nothing interactive was dropped. There is no sorting or matching task in this packet: `nuclear-disanalysis.tsx` is imported by packet-tasks only for the BAKER citation and the DisanalysisQuote type; the NuclearDisanalysis component itself is stateless (claim, reading map, three prose tasks, folded quotes; the comment in exercises.ts at e8397d0 says it "stood down 2026-08-12 when the owner's document packet took over 0.3's reasoning tasks" and it is not in the registry). Its CARD_CANDIDATES / DEALT_CARD data feed a fixed quotation under Task 3 of that retired component, not a card sort.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Already on the page; keep them unchanged, including the existing ids (learners may have responses stored under them). Reproduced here verbatim from the lens so the orchestrator can diff:

\#### Question: Open
id:: 5af30446-99ef-4208-becd-4ff2d17c5e60
content:: **Task 1. Object and purpose** (optional; max 200 words)

Document 1 refers to nuclear material, nuclear activities, and nuclear weapons. Identify:

1. the immediate object to which comprehensive safeguards are applied;
2. the obligation accepted by the state;
3. the broader outcome that safeguards are intended to prevent.

Then explain why the following conclusion is broader than the text permits:

> If all declared nuclear material remains accounted for, the state has no nuclear-weapons programme.
optional:: true
assessment-instructions:: Model answer. (1) Immediate object: nuclear material; under a CSA a State accepts safeguards on all nuclear material in all peaceful nuclear activities within its territory, under its jurisdiction, or carried out under its control anywhere. (2) Obligation: to place that material under safeguards and allow the IAEA to verify; under the NPT, not to produce or otherwise acquire nuclear weapons. (3) Broader outcome: non-proliferation, verifying that safeguarded material is not diverted to nuclear weapons or other explosive devices. Why the conclusion overreaches: what is accounted for is declared material; Document 1 claims only that such material has not been diverted and says nothing about material or activities never declared. Moving to "no weapons programme" supplies an unstated premise: that the declaration is complete. Award full credit when all three identifications are correct and the completeness premise is named; partial credit otherwise. Penalize answers that do not distinguish the text's claims from the learner's inferences.
feedback-instructions:: State which of the three identifications were right, whether the learner named the missing completeness premise, then share these Baker (2023) excerpts as reveal material: (a) §3.2.1: "CSAs are intended to (just) verify the peaceful use of nuclear materials at known nuclear facilities, rather than also detecting secret nuclear facilities." (b) §1.3: acquiring weapon-usable nuclear material is the hardest step in making nuclear weapons; uranium and plutonium are rare and emit radiation, which makes them unusually easy to track. (c) §3.2.3: detecting undeclared facilities has two steps, finding evidence suggesting a state might have undeclared facilities, and resolving suspicions about them. No generic praise.


\#### Question: Open
id:: 2fd21c66-3d30-4534-a862-8c1e24a831df
content:: **Task 2. Division of labour** (optional; max 200 words)

Document 2 proposes three components:

- chip-level activity logging;
- inspection and analysis of the logs of a sufficient subset of chips;
- supply-chain monitoring.

For each component, identify the problem it solves. Then explain why removing any one component would create a distinct route for evasion.

Your answer should show the division of labour among the three instruments, rather than merely describe how each instrument operates.
optional:: true
assessment-instructions:: Model answer. Chip-level logging creates a durable trace of which computations a chip took part in; without it, registered chips are used for a prohibited run that leaves no verifiable record. Log inspection and analysis turns the chips' records into a determination (whether a rules-violating run took place) from a sufficient sample; without it, logs accumulate but no one converts them into a detection. Supply-chain monitoring secures the completeness of the chip inventory from which the inspection sample is drawn; without it, a violator acquires unregistered chips that never enter the sample. The components are not interchangeable: a log nobody inspects detects nothing; an inspection with no attested log has nothing trustworthy to examine; both are useless against chips whose existence the verifier does not know of. Full credit requires a distinct evasion route per missing component, not just descriptions of each instrument.
feedback-instructions:: Name any component whose evasion route was missing or duplicated another's. Then note: Baker independently supports the need for persistent chip records and complete chip accountancy. No generic praise.


\#### Question: Open
id:: 361b5dfb-7542-47c2-8b20-ef80bc622435
content:: **Task 3. Grounds and limits of the analogy** (optional; max 200 words)

Identify three conditions that must hold for Shavit's system to provide credible assurance:

- one concerning the technical structure of advanced AI development;
- one concerning the chip supply chain;
- one concerning the powers or capabilities of the verifier.

For each condition:

1. state whether it is explicit in Document 2 or inferred from the proposed mechanism;
2. explain what conclusion would cease to be justified if the condition failed.
optional:: true
assessment-instructions:: Model answer. Technical structure: the training runs the rules target require large quantities of specialised data-centre chips. Explicit (Document 2 restricts its focus to specialised data-center chips and leaves personal devices alone). If it fails: a clean chip regime says nothing about a prohibited run reachable on far fewer chips or on personal devices. Supply chain: every chip is accounted for, so no actor can secretly acquire chips and underclaim its total. Explicit (stated purpose of the third component). If it fails: inspecting a subset no longer licenses a statement about all of an actor's chips; the sample is drawn from a mis-measured population. Verifier: inspectors can obtain and analyse the logs of a sufficient subset, and logging and attestation hold against a determined adversary. Part explicit (inspection step, confidentiality-preserving logging), part inferred (robustness against nation-state circumvention is what the framework "aspires to"; access is assumed rather than established). If it fails: "no violation found" no longer means "no violation". The three are distinct claims: what the prohibited activity needs, whether the verifier knows the population, whether it can read it. Full credit requires all three, each labelled explicit or inferred, each with the conclusion that fails.
feedback-instructions:: Say which condition was weakest or missing. Then share Baker (2023) as reveal material: the correct analogy is verified accountancy of a chokepoint, not "chips are like uranium". Appendix A lists similarities (dual-use equipment and facilities; verified accounting of uranium in one case and high-end AI chips in the other) and differences (no analogue to environmental sampling for AI; nuclear M&V never had to verify information-technology use via source code, hardware, or models; the chip supply chain is highly concentrated while uranium sources are decentralized). §6.1: with certain preparations, the foreseeable challenges of hardware-based verification of rules on highly compute-intensive AI development would mostly be challenges that were successfully addressed in nuclear arms control; chip-based verification cannot address all important risks from AI. Executive summary: if rules' scope were highly compute-intensive AI development in data centers (so commodity chips offer no loophole), direct inspection costs would be lower than or roughly similar to those states accepted for nonproliferation. No generic praise.


\#### Question: Open
id:: b6ac80e3-aa4f-4ce2-b8e8-3d1e38927887
content:: **Task 4. Why Iraq was missed** (optional; max 200 words)

Document 3 describes clandestine nuclear activities that remained undetected while routine safeguards continued at declared facilities.

Explain how the safeguards system could be operating as designed and nevertheless fail in this case. In your answer, distinguish among:

- failure to verify declared activity correctly;
- failure to identify an undeclared object;
- failure to possess or act upon information indicating where to investigate.

Which of these best characterises the Iraq case, and why?
optional:: true
assessment-instructions:: Model answer. The second: a failure to identify an undeclared object. The first did not occur (routine verification of declared activity continued as designed), and the third is why the second persisted rather than a separate defect. Document 3 names the causes: access confined to defined strategic points at declared facilities while undeclared activities sat on safeguarded sites away from those points; detection techniques did not exist until environmental sampling; a "checklist" inspection culture narrowed how the duty was perceived; and for undeclared sites the fundamental problem is identifying locations to investigate, since wider access rights are of limited value without leads. The system can operate as designed and still fail because correct verification of what was declared is compatible with an undeclared object the design never undertook to find. More of the same inspections would not have closed it: the binding constraint was leads, not frequency or access. Full credit requires picking the second category, explaining the relation of the third to it, and citing Document 3's specific factors.
feedback-instructions:: Say whether the learner picked the right category and whether they explained why the third factor is the cause of the second's persistence. Then share Baker (2023) as reveal material: §5.2: CSAs were not designed to detect secret nuclear facilities; negotiators assumed that secret facilities would be detected and reported by national intelligence agencies, that a self-contained fuel cycle was too hard for most states, that far-reaching inspector access was politically unacceptable, and that no good detection methods existed; fixes (Additional Protocols) required ratification by each state. §5.3: the system was substantially strengthened only after the salient failure of Iraq's nearly successful secret program, discovered through the First Gulf War; the IAEA then began using authorities it already had (earlier design information, environmental sampling) and agreed Additional Protocols with dozens of states. No generic praise.


\#### Question: Open
id:: c8a29a26-9bb2-46bd-b44f-fc87f4f54bd9
content:: **Task 5. Testing the hypothesis** (required; max 300 words)

A policy team reaches the following conclusion:

> Because advanced AI training depends on specialised chips, a regime of chip registration, logging, and inspection can verify that no prohibited AI development is occurring.

Evaluate this conclusion using all three documents. Your answer must:

1. identify the strongest valid parallel between nuclear safeguards and the proposed AI regime;
2. identify the step in the argument placed under greatest pressure by the Iraq case;
3. explain why that problem cannot be solved merely by inspecting registered chips more frequently;
4. replace the original conclusion with a narrower claim that the evidence supports.
assessment-instructions:: Model answer. (1) Strongest parallel: verified accountancy of a controlled, mandatory input, carried by a duty on the holder to declare it and accept verification (Document 1 places all nuclear material under safeguards; Document 2 requires every chip be accounted for and a sufficient subset's logs inspected). The parallel is accountancy of an input, not resemblance between uranium and chips. (2) Step under pressure: the move from "inspection of registered chips found no violation" to "no prohibited development is occurring", which requires the declaration to be complete; Document 3 shows completeness was absent in Iraq. (3) Why frequency cannot fix it: the defect is in the population, not the sampling rate; an unregistered chip is not in the frame the sample is drawn from, so no frequency reaches it; Document 3's own answer was a different instrument, information from states. (4) Narrower claim: where highly compute-intensive AI development requires large quantities of accounted-for specialised chips, chip registration, tamper-evident logging and inspection may provide reliable assurance that covered chips at declared locations have not been used in prohibited training; this does not by itself establish the absence of prohibited development using unregistered chips, undeclared facilities, commodity hardware, or other unmonitored inputs. Score each of the four parts at 25 points. Require that the narrowed claim actually restricts scope (covered chips, declared locations) rather than merely hedging.
feedback-instructions:: Go part by part: which of the four were sound, which were missing or overbroad. Then share Baker (2023) as reveal material: §6.1's conclusion is deliberately narrow (hardware-based verification of rules on highly compute-intensive AI development; chip-based verification cannot address all important risks from AI); Appendix A's similarities and differences; and Appendix G.8's final line, worded exactly: "methods that have been widely used for nuclear arms control verification can be adapted to create a reliable system for verifying accounts of AI chips". Verifying accounts of AI chips, not verifying the absence of all prohibited AI development. That is the properly limited conclusion. No generic praise.


Optional additions, none required: `placeholder:: Write your answer, then submit to see what Baker says on the same ground.` on each of the five segments (XLab's textarea placeholder, verbatim); and the two missing §5.2 fragments in the "Baker (2023) on Task 4" callout.
:::

#### Text
content::
\## Part 1 · Week 2: What kind of policy are we trying to verify?

Module file: [[../modules/XLab Verification P1 W2 Policy scope]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-scoping-effective-feasible]]

#### Text
content::
\#### Everything Comes With a Cost (policy-cost)

**Decision: widget.** The exercise is a staged reveal (commit to the goal, then the card flips to ask for the price, then a rating that branches to one of three reflections and composes the full policy sentence); the current native version shows both blanks at once, has no reveal on the Choice, and leaks all three reflections plus the closer in a callout.

**Target lens:** [[../Lenses/XLab Verification - v-scoping-effective-feasible]]

**Where it goes:** after the first Text segment "You can think about maximizing the positive impact of a policy by evaluating it along two axes" and before the collapsed callout "The Limited Test Ban Treaty (1963): verifiability decided what could be banned". The other widget in this lesson (policy-scoping, built by another agent) goes later: after the Text segment "In the following exercise, you will develop intuitions with this effectiveness-feasibility tradeoff", which itself follows the Limited Test Ban callout. Order on the page: intro Text, policy-cost widget, Limited Test Ban callout, bridge Text, policy-scoping widget, "Design for the hardest case" Text, stakeholder-map Open question.

**What it replaces:** the Text segment "\## Everything comes with a cost." (prose reproduction of the card copy), the optional FillBlank "I support {{blank}} at the cost of {{blank}}." (id 57dc934f-9584-4a93-b1ca-4b7ff7ddfd3e), the optional Choice "Naming the price: how easy was it?" (id 85f95777-151c-4619-8557-3bc3a52cee49), and the collapsed callout "Both sides of the card (open after you have answered)". All four should go entirely; the widget carries every line of that copy and the callout would otherwise reveal the three reflections before the learner rates. No fallback needed: the exercise is optional and personal on XLab too.

**In XLab:** <VerificationExercise id="policy-cost" /> in scoping-effective-feasible.mdx, core (not inside a Fold), placed directly after the opening effectiveness/feasibility paragraph and before the Limited Test Ban Fold.

**Learner time:** 2 minutes

Side A: type a policy they strongly believe in, or tap one of four chips (Universal healthcare, School vouchers, A carbon tax, Banning phones in schools), then "Flip the card". Side B: with Side A echoed above, name one real cost or downside of enforcing it; "Stuck? Try a lens" reveals the four lens questions; "Back" returns to Side A. "Face the tradeoff" shows both sides as a ledger and asks "Naming the price: how easy was it?" with three pills; choosing one reveals XLab's reflection line for that choice, the full policy ("I support X at the cost of Y."), the closer about what we are willing to compromise, and "Try another policy", which clears the card (earlier cards are kept in the saved state for the tutor).

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Source: src/lib/verification/data/policy-cost.ts and src/components/verification/widgets/policy-cost.tsx at HEAD of the XLab clone (commit 1e8b150). All labels, chips, placeholders, buttons, the three reflections, the full-policy template and the closer are verbatim from POLICY_COST_COPY; input limits (90 and 160 characters) and the disabled-until-filled buttons mirror the component.
- Em dashes replaced: placeholder "be honest, one is enough"; question "Naming the price: how easy was it?"; "The cost was there all along; it just isn't the half..."; "...outside our view, or no one has looked yet."; template "I support X at the cost of Y." (XLab: "I support X, at the cost of Y."). These match the Lens lens's existing native wording.
- Dropped: the Side A footer line "Nothing you type leaves this page." XLab kept the card in React state only; the Lens widget saves the goal, price and rating through Lens.saveState so the tutor can see them and the card restores, so the promise would be false. The native Lens version already sends both answers to the tutor.
- Completion: XLab's component never calls onComplete (it takes the prop and discards it), so there is no XLab condition to mirror. The widget calls Lens.complete() once the learner has faced the tradeoff and picked a rating, which is the exercise's own end. Nothing gates on it unless a lens sets required:: true.
- Added, not in XLab: "Try another policy" pushes the finished card (goal, price, rating) into a history list (max 10) in the saved state and the tutor summary, so a reset does not erase what the tutor saw. Visible copy is unchanged.
- No Lens.submit or promptTutor: XLab does not grade or discuss this card. Tutor guidance from the lens's former FillBlank feedback-instructions is carried in summary_for_tutor instead.
- The 3D flip uses CSS transforms with backface-visibility and a prefers-reduced-motion fallback; the hidden face is inert and aria-hidden. Both faces sit in one grid cell so the frame height is the taller face.
:::

#### Widget
source:: [[../widgets/policy-cost]]

#### Text
content::
\#### Scoping an Anti-ASI Policy (policy-scoping)

**Decision: widget.** The learner places eleven buckets on a 5x5 feasibility x effectiveness plane with instant per-bucket verdicts, a reveal of the reference map and a gated follow-up question; prose and an Open question cannot give the placing, the verdict-then-adjust loop, or the unlock.

**Target lens:** [[../Lenses/XLab Verification - v-scoping-effective-feasible]]

**Where it goes:** after "Sort the following policy buckets on the feasibility x effectiveness matrix." (the Text segment that ends "Should you compromise ambition or real-world enforceability?")

**What it replaces:** everything from the "### The axes" Text segment through the "Why (open after you have answered)" callout: the two scale callouts, the eleven bucket callouts, the Open question ec436b24 (sort graded as free text), the "Reference map and reasoning" table callout, the "### The one exception" text, the Choice question 3bfd8e5c and its "Why" callout. All of it is inside the widget. Suggest removing the Open and Choice questions and the bucket callouts entirely (the widget gates the exception question on the sort, which the native version could not); the "Reference map and reasoning" table callout may stay as a collapsed fallback since it is the tutor's readable copy of the key. The "Design for the hardest case" paragraph after the widget stays.

**In XLab:** <VerificationExercise id="policy-scoping" /> in scoping-effective-feasible.mdx, core, not inside a Fold. Registered as bridged in src/lib/verification/exercises.ts.

**Learner time:** 20 to 25 minutes

Three steps with a tab bar that unlocks in order. Step 1: opens both five-rung scales (effectiveness and feasibility, each rung with its gloss); the continue button unlocks after both. Step 2: opens eleven bucket cards on a ramp from least to most demanding ask, each with its description and historical parallel; the sort unlocks after all eleven are read. Step 3: drags each bucket chip onto the 5x5 grid (or clicks a chip to pick it up and then clicks a cell; keyboard works the same way), checks, and gets each chip marked on the mark, close or off with a "by the reference map it is more gettable / stronger than you have it" nudge; moving a chip after a check marks it "moved, recheck". Once all eleven are on the mark, or after the learner reveals the reference map (dashed ghost pills on the reference cells, the coordinated halt ringed, each with XLab's rationale), the securitization question appears; picking the coordinated halt completes the exercise, a wrong pick shows XLab's explanation and allows a retry.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: xlab-tracks/src/lib/verification/data/policy-scoping.ts (AXIS_SCALES, BUCKETS with key cells, verdictFor, nudge logic, EXC_ANSWERS, AXIS_TIPS, POLICY_SCOPING_COPY) and the component src/components/verification/widgets/policy-scoping.tsx (phase gating, check/reveal/reset, exception unlock rule allRight || keyOn, ghost offsets, onComplete on the correct pick). The widget imports only the kit drag module and ui primitives; it does not use policy-plot, policy-quick-check, policy-critique or any engine. Working tree of the clone (no historical commit needed).
- Every scale, bucket, parallel, rationale, tip, stat, caption and button label is XLab's. Em dashes replaced with commas, colons, periods or parentheses, using the same rewrites the Lens lens already uses for the eleven rationales. The `<b>Right, the coordinated halt.</b>` HTML in EXC_ANSWERS.ch is rendered as a bold span plus text, not innerHTML.
- Adapted: XLab's scale dialog is an inline panel (the frame has no modal); tooltips (chip description, verdict nudge, ghost rationale, corner notes, securitization) are `title` attributes plus a visible info line under the tray that shows the same text when a chip is picked up, a ghost or corner label is clicked, or the "Securitization" term is toggled, so touch users get them too. The sort hint sentence therefore says "pick a bucket up, then pick a cell" instead of XLab's "hover a chip for its description". The two-colour tint ramp is a single accent bar with rising opacity.
- Dropped: XLab's closing line "Next: what would a pause agreement actually say? 1.1: Anatomy of a (Pause) Agreement" (XLab navigation, not this module's order); replaced by XLab's live-region text "Correct. Exercise complete."
- Exception options are shown in a seeded order (port of src/lib/shuffle.ts keyed "policy-scoping:exception") instead of XLab's fixed most-demanding-first order, which put the correct answer first. The Lens Choice segment also shuffles.
- No Lens.submit: XLab asks for no written justification in this widget and has no rubric text; the sort is checked in-widget against the reference cells exactly as XLab does. No promptTutor (XLab has no discuss moment here). The Lens-authored 9/5/0 scoring and middle-band leniency from the native Open question are not reproduced (they are not XLab's).
- Completion mirrors XLab onComplete: fires once when the correct exception is picked. Restore: state carries phase, scales seen, cards read, placements with verdicts, checked/revealed flags and the exception pick; a completed meta with no state renders the finished view. A restored phase that its prerequisites cannot reach falls back to the last reachable step.
- Uncertain: XLab's own log notes the reference cells and rung scales are builder-authored apparatus awaiting owner review; the widget grades against them as XLab does.
:::

#### Widget
source:: [[../widgets/policy-scoping]]

#### Text
content::
\## Part 1 · Week 3: Anatomy of a (pause) agreement

Module file: [[../modules/XLab Verification P1 W3 Treaty anatomy and actors]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-scoping-anatomy]]

#### Text
content::
\#### Anatomy of a (Pause) Agreement (treaty-workspace)

**Decision: native question segments are enough.** XLab's widget is four textareas with a "Save answer" button each and a "N of 3 answered" counter; it has no marking key, no reveal state and no per-question feedback, so the four `Question: Open` segments already on the Lens page (with authored assessment and feedback instructions XLab never had) give the learner strictly more than the widget did.

**Target lens:** [[../Lenses/XLab Verification - v-scoping-anatomy]]

**Where it goes:** already in place. The exercise is the four `Question: Open` segments (ids 5c257204-3687-4257-a4f3-ecb75d22e20f, e3c2359d-f159-4348-a44a-740924f23668, 7d9b33a6-250c-41b3-aeb3-daae48c85383, 9071fd5b-8b0f-4dd0-80bf-93960ebca7af) that follow the Text segment beginning "\## Assignment / Open the draft agreement prepared by the MIRI Technical Governance Team". They end before the Text segment beginning ":::callout {title=\"Optional: Reassemble the Parts of an Agreement\"" (that callout, and the Choice segments after it, are the `anatomy-drill` slot owned by the other agent; the drill widget goes after that callout's Text segment, replacing the run of Choice segments that starts with "Specimen 1").

**What it replaces:** nothing to replace; the four Question: Open segments stay as they are. No collapsed fallback needed.

**In XLab:** <VerificationExercise id="treaty-workspace" /> in scoping-anatomy.mdx, core (under "## Assignment", after `<PageBreak title="Apply the Treaty-Reading Method" />`), not inside a Fold. Registry entry: `{ id: "treaty-workspace", title: "Anatomy of a (Pause) Agreement", bridged: true }`.

**Learner time:** about 45 minutes for three answers (plus the optional 75-minute paper lens for the treaty itself)

Opens MIRI's draft agreement (the optional paper lens `XLab Verification - v-paper-scher-treaty`), reads all four questions, then answers any three: where the text first binds a Party (Preamble and Article I), the do/refrain/permit duties of one prohibition (Articles IV, V, VI or VIII), where that prohibition's verification method lives (compare Articles VII and IX), and entry into force plus withdrawal (Article XV, compared with Annex E of the Practice Guide). In XLab each answer is a free-text box with a "Save answer" commit; on Lens each is a graded Question: Open with tutor feedback.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Question text compared mechanically (every string literal in `src/lib/verification/data/treaty-workspace.ts` against the four `content::` blocks). Result:
- Questions 1, 2, 3, all body text, list items and guidance lines: verbatim.
- Placeholder "Quote the words you are talking about." (QuestionWorkspace default): verbatim on all four.
- Intro: XLab's three intro paragraphs are verbatim in the "## Assignment" Text segment; Lens adds one bridge sentence ("All four are marked optional here so that the lens can be completed with any three.") and renders the author string with parentheses instead of XLab's em dash.
- Drift, question 4: XLab says "Determine when the agreement enters into force"; Lens says "Determine whether and when the agreement enters into force". Deliberate and justified: the draft (articles/scher-an-international-agreement-...md, the "ARTICLE XV, Withdrawal and Duration" heading) has no entry-into-force clause; Article XV gives only unlimited duration and 12-month withdrawal notice to the CTB. The Lens assessment instructions for Q4 rely on this. Keep the Lens wording.
- Gating gap (the one thing lost): XLab calls `onComplete` when 3 of the 4 non-optional questions are saved (`WORKSPACE_RULE = { kind: "any", count: 3 }`, `isWorkspaceComplete`). Lens has no "any 3 of 4" rule, so all four segments carry `optional:: true` and the lens can be marked complete with zero answers. Options for the orchestrator: (a) accept, as the current page does; (b) drop `optional:: true` on questions 1 to 3 and keep it on 4 (guarantees three answers but removes the learner's choice of which three; note question 3 depends on question 2 anyway, so 1, 2, 3 is the natural set); (c) a thin widget with `required:: true` calling `Lens.complete()` after three commits, which I recommend against because it would duplicate the segments' grading or lose it.
- Assessment and feedback instructions on the Lens segments are Lens-authored, not from XLab (XLab had no marking key for this exercise). Not drift; an addition.
- XLab's per-question "Saved. Keep editing if you want, it stays saved." message and the answered counter have no Lens equivalent; nothing curricular is lost.
Sources: `src/components/verification/widgets/treaty-workspace.tsx`, `src/components/verification/kit/question-workspace.tsx`, `src/lib/verification/question-workspace.ts`, `src/lib/verification/data/treaty-workspace.ts`, `src/content/lessons/verification/scoping-anatomy.mdx` (current HEAD of xlab-tracks), `src/lib/verification/exercises.ts`.
:::

:::callout {title="Proposed native segments" tone="neutral" collapse="closed"}
Already on the page; no change needed. The four existing segments are, in short (full text and instructions are in the lens file at the ids above):

```
\#### Question: Open
id:: 5c257204-3687-4257-a4f3-ecb75d22e20f
content:: **1. Distinguish between non-binding and binding provisions** ...
placeholder:: Quote the words you are talking about.
optional:: true
assessment-instructions:: ...
feedback-instructions:: ...
```
(and likewise e3c2359d-f159-4348-a44a-740924f23668 for question 2, 7d9b33a6-250c-41b3-aeb3-daae48c85383 for question 3, 9071fd5b-8b0f-4dd0-80bf-93960ebca7af for question 4).

If option (b) above is chosen, the only edit is deleting the line `optional:: true` from the segments with ids 5c257204-3687-4257-a4f3-ecb75d22e20f, e3c2359d-f159-4348-a44a-740924f23668 and 7d9b33a6-250c-41b3-aeb3-daae48c85383, and changing the bridge sentence in the "## Assignment" Text segment from "All four are marked optional here so that the lens can be completed with any three." to "Questions 1 to 3 are required here; question 4 is optional."
:::

#### Text
content::
\#### The Anatomy Drill (anatomy-drill)

**Decision: widget.** Thirteen commit-then-reveal placements with drag or tap, a one-retry-then-file mechanic, sources hidden until commit, a tallied results screen and a closing drag pick: none of that survives as a run of Choice segments (no reveal, no retry, no tally).

**Target lens:** [[../Lenses/XLab Verification - v-scoping-anatomy]]

**Where it goes:** after the Text segment that ends "No praise." on Question 4 ("**4. Examine entry into force and withdrawal**"); that is, where the callout "Optional: Reassemble the Parts of an Agreement" begins today.

**What it replaces:** the whole native run from the collapsed callout "Optional: Reassemble the Parts of an Agreement" through the collapsed callout "The Reykjavik Protocol: full text": one intro callout listing the organs, 13 optional Choice segments each followed by a collapsed "Specimen N: why" callout, the "Results" callout with the source table, the priority-pick Choice segment, the "seven picks, judged" callout and the Protocol callout. All of it should go; the widget carries every one of those strings (organ list, specimens, verdicts, near-miss and wrong-bin notes, sources, results table, punch line, seven judgments, full Protocol). Keep only a short Text segment before the widget with XLab's fold lead-in ("A recall drill for the anatomy you just dissected." + the bold "Every agreement that restrains anyone has the same seven organs" paragraph + "_13 specimens · about 15 minutes_"), since the widget's intro starts at the organ list. Not required:: (XLab folds it as optional).

**In XLab:** <VerificationExercise id="anatomy-drill" /> in scoping-anatomy.mdx, optional, inside <Fold label="Optional: Reassemble the Parts of an Agreement">

**Learner time:** 15 minutes (XLab's own estimate)

Reads the seven organs (plus the No-organ bin) on an intro screen and presses Begin. Then, one specimen at a time, reads a short treaty or advocacy text with its source hidden and places it on one of eight bins: drag with mouse or touch, or tap the specimen (or focus it and press Enter) and then tap a bin. Each placement gets an instant verdict with XLab's explanation and the source: correct, a defensible near-tag that is accepted and moved to the sharper organ, or a wrong bin with one retry before the drill files it and explains where it belongs. After specimen 13 a results screen tallies clean first reads, defensible near-tags and second looks, shows the source table and punch line, and asks the learner to drag (or tap) the organ they would put at the top of a negotiating agenda; the pick shows XLab's judgment for it, then "Where this goes next", a Restart button and the full Reykjavik Protocol.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All curriculum strings come from `src/lib/verification/data/anatomy-drill.ts` (ORGANS, NULLBIN, CARDS, JUDGMENT, PROTOCOL, COPY) and the UI copy from `src/components/verification/widgets/anatomy-drill.tsx` (feedback heads, "Specimen N of 13", "source hidden", "Filed under", "Where it belongs", "Try again", "Next specimen", "Finish", "Your top negotiating priority"). Engine logic (`engines/anatomy-drill.ts`: resolveDrop, applyDrop, attempt counting, near-tag counts as miss on a second attempt) copied unchanged. Checked by a script that extracts every string literal from the data file: 160 strings, 144 verbatim, 16 differ only by the em-dash rewrite or by being split into a bold lead plus body ("One last drag.", "Where this goes next:").
- Em dashes replaced (only rewrite): "prove: declared & undeclared" (as the Lens page already has it), "NPT Article X, the clause", "16 H100 chips (roughly $500,000 of hardware)", Protocol article ids "Article I. Definitions" etc. (as the Lens page has them), "The Reykjavik Protocol: full text", "Defensible: here is the sharper tag", "Not this organ. Look again", the drag hint "press Enter, then choose an organ".
- Bins keep XLab's fixed organ order (1 to 7, then No organ) and specimens keep XLab's order; XLab shuffles neither (the organ numbers are curriculum and the specimen sequence is pedagogic: New START before the FLI letter that is compared to it). Nothing is keyed on position: each drop compares the bin's organ number with the card's organ.
- Tap fallback added beyond XLab's: tapping a bin with nothing picked up arms the specimen (visible accent ring, hint changes to "Picked up. Now choose the organ it implements"), a second tap on a bin commits. Escape puts the specimen down. Same for the priority pick: tapping a chip picks it directly (XLab did the same via a click on the chip), dragging it to the slot also works.
- Tier colours: XLab uses green/amber/red; here the accent marks clean and near (near shown with a double left rule and a hollow progress dot), grey marks miss, and every verdict carries a text head, so no state relies on colour alone.
- XLab's DragProvider sets `touch-action: none` on the draggable; kept, so a finger that starts on the specimen card drags instead of scrolling the page. The bins and the rest of the page scroll normally, and the tap flow needs no drag.
- Complete: fires once when the learner reaches the results screen after specimen 13, mirroring XLab's onComplete in finishToSummary. Restart does not undo completion. Restoring a saved summary state with meta.completed false calls complete once.
- Saved state: {phase, idx, attempts, results, fb:{kind,bin}, judgment}; feedback text is recomputed from the card and the bin, so the JSON stays under 1 KB. Summary text names the current specimen, its correct organ (tutor only), the tally and the latest verdict.
- Standalone (no window.Lens): state falls back to localStorage under `lens-widget-anatomy-drill`.
- Uncertain: the Lens page today keeps the Reykjavik Protocol readable at any time in a collapsed callout; XLab (and this widget) show it only on the results screen. If the treaty-workspace port needs the Protocol text earlier, keep that one callout on the page.
:::

#### Widget
source:: [[../widgets/anatomy-drill]]

#### Text
content::
\## Part 1 · Week 3: Who the treaty relies on, applies to, and constrains

Module file: [[../modules/XLab Verification P1 W3 Treaty actors]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-interactive-map]]

#### Text
content::
\#### The Compute Supply Chain (interactive-map)

**Decision: widget.** A clickable world map where selecting a country, a layer or a pipeline stage changes what is highlighted and which card is shown; prose (a table and 14 collapsed callouts) cannot do that, and Elias singled this map out as the priority port.

**Target lens:** [[../Lenses/XLab Verification - v-interactive-map]]

**Where it goes:** after the first Text segment "The world map of AI compute: who makes what, where it flows, and where verification can grab hold" (the two-paragraph intro), in place of the second Text segment that begins "\## The Compute Supply Chain".

**What it replaces:** the whole second Text segment of the lens: the "Start here" paragraph, the three-stat bullet list, the "Supply chain layers" table, the eight-item "The pipeline · sand to model" list, the fourteen collapsed country callouts, and the "Anatomy of a Chip" paragraph with the ETO Chip Explorer link. All of it is inside the widget verbatim (the widget shows the same "Start here" text, stats, layer cards with the "To verify at this layer, you'd need" country list, pipeline stage cards, country cards with roles and "Why it matters for verification", and the optional Chip Explorer link). That segment should go entirely; the tutor gets the full data through summary_for_tutor and saveState summaries. Keep the first Text segment (intro), the third Text segment (the "A geographic chokepoint is potential leverage" paragraph plus Notes and sources and Currency) and the Works cited callout as they are. Also update the lens's summary_for_tutor, which currently says "Reading-only lens reproducing XLab's interactive supply-chain map as text".

**In XLab:** <VerificationExercise id="interactive-map" /> in interactive-map.mdx, core (not optional), not inside a Fold. Registry title "The Compute Supply Chain", bridged: false.

**Learner time:** 10 to 15 minutes

Above the map, three headline stats. On the map, fourteen coloured countries (Singapore as a hub dot) with labels and leader lines; clicking one opens a card with its layers, anchor facts, "Why it matters for verification" and actor roles, and outlines the country in black. Clicking a layer in the key or a stage in the eight-step pipeline dims every other country and opens a card with the layer's stat, its "why", and buttons for each country that "would have to be in the room", which jump to that country's card. Zoom in, zoom out and Fit buttons plus drag-to-pan when zoomed; on a phone the map scrolls sideways inside its box (720px wide) and starts on the Europe-to-East-Asia stretch. Opened countries get a check mark on their map label and in the member lists, isolated layers and lit stages get a check mark on their button, and a progress line counts all three; the optional "Anatomy of a Chip" link has a mark-as-read circle.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All text (layers, stats, roles, 14 countries with anchors and verif text, 8 pipeline stages, key/pipeline/roles/start copy, hint text, hover and touch variants) is verbatim from `src/lib/verification/data/interactive-map.ts` at HEAD of the xlab-tracks clone. Seventeen em dashes were replaced with commas, colons or parentheses; a script confirmed every other fragment matches the source character for character.
- Geometry: the 176 simplified country outlines (`WORLD`, 1000 x 540 viewBox) are copied from the same data file (118 KB of path data, id and path only; unused feature names dropped). Label positions, leader lines, the Singapore hub dot, the viewBox clamp and the zoom maths are XLab's.
- Interactions mirrored from `src/components/verification/widgets/interactive-map.tsx`: select toggles and clears any filter, filter clears the selection, same-source re-click clears the filter, key and stage filters are distinct sources, hover preview dims non-members, hover tooltip on fine-pointer devices, Escape clears, clicking the ocean clears, dismissible hint, zoom buttons and drag pan.
- Dropped: wheel zoom (XLab hijacks the scroll wheel over the map; inside a reading column that traps page scrolling). Zoom buttons and drag pan remain.
- Added beyond XLab: country labels are clickable (XLab sets them pointer-events: none), map shapes are keyboard focusable (tabindex, Enter/Space), check marks for opened/isolated/lit items and a progress line, so the "seen" state is visible without colour, and a persistent mark-as-read on the reading card (XLab stores that in its own marks store). The stage panels are ordered map, key, detail card, pipeline, roles, reading card so the detail card sits next to the map; XLab puts the detail card after the key and reading card.
- Colours: XLab's six layer colours (navy, orange, dark red, olive, yellow, blue) replaced with a six-hue palette anchored on the Lens accent (#3b5fa8, #b87018, #a8343e, #5f8a2a, #c49a18, #1f9ab3), validated with the dataviz palette checker (lightness band, chroma floor, CVD and normal-vision separation pass; the mustard for Packaging has 2.5:1 contrast on the map ground, relieved by direct country labels and named legend chips). A single-accent map cannot encode six layers, so this is the one deliberate departure from "greys plus one accent".
- The public/verification/map.js and map.css files are XLab's skill map (course progress), not this widget; nothing was taken from them.
- No `Lens.complete()`: XLab has no finish condition for this exercise (bridged: false, no onComplete). If the lens ever sets `required:: true` on the segment, a finish rule would have to be invented; the note in summary_for_tutor suggests what a good exploration looks like instead.
- No `Lens.submit` or `promptTutor`: XLab has no written answer or discuss moment here.
- Standalone fallback stores the same snapshot in localStorage under `lens-widget-interactive-map`.
- check_widget.py contrast note: the mustard WARN comes from the palette validator, not check_widget (which prints OK with no warnings).
:::

#### Widget
source:: [[../widgets/interactive-map]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-actor-edges]]

#### Text
content::
\#### Who can prove what (actor-edges)

**Decision: widget.** The learner draws directed evidence edges on a 17-actor ring map (drag, tap-tap, or button lists), commits, and gets a per-edge verdict against XLab's seven-edge key; a typed list graded by the assessor cannot show the map, the reversed/extra/missed states, or the role lens.

**Target lens:** [[../Lenses/XLab Verification - v-actor-edges]]

**Where it goes:** after the first Text segment ending "which of the four subgoals turns out to be holding the whole regime up." It replaces everything from the second Text segment ("## Who can prove what ... The brief ...") through the "Why (open after you have answered)" callout.

**What it replaces:** the prose reproduction (brief, board placement, four subgoals, "1. Draw the edges" instructions), the Open question "Draw the edges" with its Lens-authored per-edge scoring, the two closed callouts (seven-edge key; actors with no edge), the "2. Read the map" callout (Where this regime is weakest), the Choice segment (whose removal stops a run soonest) and its "Why" callout. All of that is inside the widget, revealed only after the learner commits. Remove entirely; the widget covers every line. Keep the three optional Open questions (Taiwan's roles, information holders in order, capability-plus-enforcement actor) as they are on the page if you want the platform's own grading UI; the widget also carries them (behind "Open them", with Lens.submit and the self-marking key), so they can go too. Keep the intro Text segment, "Notes and sources" and "Works cited".

**In XLab:** <VerificationExercise id="actor-edges" /> in actor-edges.mdx, core, not inside a Fold

**Learner time:** 25 to 35 minutes (plus about 15 for the optional written answers)

The board shows the 17 actors on XLab's key rings (Declares, Holds the evidence, Verifies, Outside the declaration) around "A training run above the threshold". In step 1 the learner draws edges A to B (A can produce evidence about B for a verifier) by dragging between points on the SVG, tapping a source then a target, pressing Enter/Space on the focused point, or using the source and target button lists; a removable list of drawn edges sits below and "Commit the edges" enables once one edge exists. On commit the map recolours edges (solid accent in the key, dotted dark reversed or extra, dashed grey missed) and the verdict lists all seven key edges by subgoal with XLab's mechanism and Baker quotes, the extras with XLab's "argue with the key" note, and the ten actors with no edge and why; "Edit my edges" reopens drawing. "Read what it says" moves to step 2: the two findings, a "Light up a role" row that highlights actors by functional role, the second-order question (seeded shuffle, commit reveals every option's reasoning and the lesson, and completes the widget), then the optional three written questions with Lens.submit scoring and XLab's self-marking key.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Data verbatim from src/lib/verification/data/actor-workshop.ts (WORKSHOP_ACTOR_IDS, RINGS, RING_KEY, MAP_SLOTS, ABSENT_ACTORS, MAP_LABEL, CENTRE, SUBGOALS, EDGE_KEY, EDGE_NOTES, EDGE_FINDING, MAP_FINDING, SECOND_ORDER, CLOSING_QUESTIONS, CLOSING_KEY), src/lib/verification/data/actor-map.ts (the 17 roster entries, ACTOR_ROLES, ACTOR_POSTURES), copy and geometry from src/components/verification/widgets/actor-edges.tsx and actor-board.tsx (RingMap radii, slot angles, beam and arrowhead paths, drag threshold and hit radius), scoring from src/lib/verification/actor-workshop.ts (scoreEdges: found, reversed, extra, missed), shuffle from src/lib/shuffle.ts. Current HEAD of the tracks clone. Em dashes replaced with commas, colons or parentheses throughout, including inside two Baker quotes ("code, with the Prover"; "regime: its robustness").

Dropped or adapted:
- XLab bridges this widget to the 1.2 board (shared localStorage key v-actor-workshop:v5): it shows the learner's own ring placement when done, tracks "peeked" across both halves, and the closing line reports recall and ring scores from 1.2. Lens state is per widget, so the map always shows RING_KEY; the note "You have not placed this board yourself" is reworded to "The rings below are the key from 1.2, not your answer"; the closing line keeps only "N of 7 edges in the key" and the roster-reopened flag. RING_WHY, CORE_QUESTION and RECALL_TARGET belong to the 1.2 widget and are not rendered here (XLab does not render them here either).
- Role lens colours: XLab uses five module colours; Lens rule is one accent, so a lit actor is accent-coloured, larger and bold, dimming the rest. Edge states use solid/dotted/dashed plus a legend, not colour alone.
- SECOND_ORDER: XLab's ChoiceList shows options in authored order with letters (correct answer first). Ported with a seeded shuffle keyed "actor-edges:second-order" and no letters; the reveal list stays in authored order. Deviation on purpose (verify rule 3).
- Written questions: XLab's placeholder says "Nothing is graded"; here "Save answer" also calls Lens.submit (item = question id) with assessmentInstructions built at runtime from the CLOSING_KEY criteria that belong to that question (criteria 1 to 3 for Q1, 4 to 5 for Q2, 6 to 7 for Q3, each with its points, reasoning line and grounds, plus the matching "No credit" line and the marking-key preamble). Placeholder shortened to "Answer from the map you just drew." Self-marking panel kept verbatim; "Score again" resubmits.
- Lens.promptTutor not used: XLab has no discuss moment here.
- The SVG actor points are `<g role="button" tabindex="0">` (as in XLab), not `<button>` elements; the button lists below are the fully native fallback, as XLab intends.
- Roster (names, positions, notes, rings, roles, postures) is behind "Open the roster" and sets `peeked`, as in XLab.
- Lens.complete() fires on committing the second-order answer (XLab's onComplete). Restoring a saved state renders identically (verified).
:::

#### Widget
source:: [[../widgets/actor-edges]]

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
\#### Place Your Bets: Mechanism Sort (mechanism-sort)

**Decision: widget.** The learner rates twelve cards on four five-rung scales and watches each placement land on four ranking lanes, then seals the set; four Ranking segments cannot show the ordering take shape, cannot skip and revisit a card, and cannot seal.

**Target lens:** [[../Lenses/XLab Verification - v-mechanism-effective]]

**Where it goes:** replaces the paragraph "Before the mechanism weeks begin, record your intuitions. Rate each mechanism on four metrics" and everything down to the Ranking question `ade67ed8-7a7f-4112-b33d-9ab40bfede96` (Durability), inclusive; the Open question `590f109a-6299-4945-a377-286c926726ef` (notebook heuristics) stays directly after the widget. The four metric definition paragraphs and their Low/High tables above stay as they are. This is all inside the first `#### Text` segment and the four Ranking segments; the `evidence-taxonomies` widget belongs to a later spot, after "The same twelve mechanisms, sorted five ways" in the Swiss-cheese/Evidence Taxonomies Text segment, so the two widgets do not touch.

**What it replaces:** the framing paragraph, the two collapsed callouts ("The twelve mechanisms", "The four metrics"), the paragraph "Rank the twelve mechanisms on each metric, most to least...", and the four ungraded Ranking questions (ids 4adc193c, c7b2d36a, 31372b62, ade67ed8) plus the two CriticMarkup reviewer comments attached to them. All of it should go: the widget shows every mechanism summary, metric gist, guiding question, anchor and rung label verbatim, so a collapsed fallback would duplicate it. The Ranking questions' items:: order encodes XLab's reference map, which is a leak the widget removes.

**In XLab:** <VerificationExercise id="mechanism-sort" /> in mechanism-effective.mdx, core (not inside a Fold), placed after the four SlidingScale metric definitions and before the notebook Callout.

**Learner time:** 15 minutes

One card at a time (XLab's queue order, hardware first), the learner reads a mechanism's title and summary and picks one of five rung buttons for each of the four metrics; the chosen rung label appears with a check mark, and "Place on the lanes" enables once all four are set. Each placed card becomes a marker on four horizontal lanes (one per metric, low on the left, high on the right), so the ordering takes shape as they go; "Skip for now" rotates the card to the back of the queue. Tapping a marker opens a detail panel with the card's four values and a "Revisit this card" button that puts it back at the front of the queue. When all twelve are placed, "Seal my ratings" becomes available; sealing freezes the set, shows "Sealed <date>" and XLab's no-key-no-score note, and calls Lens.complete().

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Interaction is XLab's own: five-rung radio groups per metric, not drag. The orchestrator's brief asked for "drag plus a tap fallback", but XLab's mechanism-sort has no drag at all (values are discrete rungs, `rungValue(i) = (i + 0.5) / 5`, and lane dots are click targets only). Adding drag along a lane would have invented a continuous scale XLab does not have, so I kept the rung buttons; they are keyboard reachable and work by tap.
- No reveal step in this widget: XLab's `MechanismSort` has no post-seal compare; the reference map, gaps and `expl` text live only in `MechanismSortReveal` (capstone, out of scope). The `ref`, `expl` and `sources` fields are therefore not in the file at all, so nothing can leak.
- Three visible strings deviate from `src/lib/verification/data/mechanism-sort.ts`: the two references to XLab lesson "4.1" (in `COPY.framing` and the sealed note) now say "the separate capstone", following the wording already accepted in the Lens lens (there is no 4.1 on Lens). Everything else (12 titles and summaries, 4 metric names, gists, guiding questions, low/high anchors, 20 rung labels, `raterDone`, `sealNoteReady`, `sealNotePending`, "Place on the lanes", "Skip for now", "Seal my ratings", "Revisit this card", "Your ranking, metric by metric", "How the four metrics are defined") is verbatim, em dashes replaced with colons or commas.
- The metric guide additionally lists each metric's `questions` array (XLab's guide shows only gist and anchors). They are XLab data, and the Lens callout the widget replaces was showing them, so they are kept.
- Layer colours: XLab uses five brand colours per layer. Under the greys-plus-one-accent rule the layers are told apart by marker shape (hardware filled circle in the accent, cloud square, intelligence diamond, human triangle, cryptographic hollow ring) plus a legend, so layer is never colour-only.
- Sealed date uses `toLocaleDateString` exactly as XLab does; it is a machine timestamp stored in state, not authored.
- XLab's component never calls `onComplete` (it discards its props), so there is no XLab completion condition to mirror. Lens.complete() fires on seal, the exercise's own end state. Restore: `Lens.onState` rebuilds the store; any mechanism that is off the queue without four ratings is pushed back onto it, and `sealed` is honoured only when the queue is empty.
- Standalone fallback: `localStorage` key `lens-widget:mechanism-sort` when `window.Lens` is absent.
- Sources: `src/components/verification/widgets/mechanism-sort.tsx`, `src/lib/verification/data/mechanism-sort.ts`, `src/lib/verification/exercises.ts` (title), `src/content/lessons/verification/mechanism-effective.mdx`, all at the clone's HEAD.
:::

#### Widget
source:: [[../widgets/mechanism-sort]]

#### Text
content::
\#### Five Maps of the Evidence (evidence-taxonomies)

**Decision: widget.** Five alternative groupings of the same twelve mechanisms that the learner switches between, with a per-mechanism detail panel that re-reads its placement under each map; prose can only show the five lists side by side, not let the learner follow one mechanism across them.

**Target lens:** [[../Lenses/XLab Verification - v-mechanism-effective]]

**Where it goes:** after "The same twelve mechanisms, sorted five ways. Switch maps, inspect a mechanism and argue with the placements." (the paragraph under the "### Five maps of the evidence" heading)

**What it replaces:** six closed callouts that reproduce the widget data as prose ("The twelve mechanisms" with all descriptions and "Where the map strains" notes, then "By layer", "By access", "By goal", "By lifecycle", "By adversary", each with question, lineage, bucket lists, strengths and limits). All six should go entirely; the widget carries every sentence of them. Keep the paragraph "Three quick checks, built from the maps above." and the three optional Choice segments that follow; the widget has no check of its own and those three still work as a quick self-test after exploring.

**In XLab:** <VerificationExercise id="evidence-taxonomies" /> in mechanism-effective.mdx (line 65, directly after the "Evidence Taxonomies" section prose), core, not inside a Fold (the lesson has no Fold or optional markers).

**Learner time:** 8 minutes

Five tabs (By layer, By access, By goal, By lifecycle, By adversary) each show the map's organising question and lineage, then the twelve mechanisms regrouped into that map's buckets as clickable chips; the lifecycle map shows its empty "After deployment" bucket with XLab's explanation. Clicking a chip opens a side panel with the mechanism's description, its placement in the current map, and XLab's "Where the map strains" note where one exists; the selection stays put when switching tabs, so the learner can watch one mechanism land in a different bucket on each map. A toggle under the panel reveals "What it reveals" and "What it hides" for the current map. A footer counts maps opened; the widget calls Lens.complete() once all five maps have been opened.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: src/lib/verification/data/evidence-taxonomies.ts (all 12 mechanisms, 5 maps, groups, strengths, limits, empty-bucket text) and UI strings from src/components/verification/widgets/evidence-taxonomies.tsx, both at HEAD of the xlab-tracks clone. A script check confirmed every string literal from the data file appears verbatim in the widget. Kit imports: only kit/types.ts (VerificationWidgetProps), which the component ignores.
- Adapted: XLab clears the selected mechanism when the map changes; the port keeps it selected so the placement panel updates to the new map (that is the comparison the lede asks for). Closing the panel or clicking the selected chip again clears it.
- Adapted: XLab's per-group colours (five hues) replaced by heading font plus one accent; the active tab is filled accent, viewed tabs carry a check mark, the selected chip has an accent border, a check mark and bold text.
- Adapted: XLab's `<details>` for strengths and limits is a `<button>` toggle with aria-expanded, so it is a button like everything else clickable.
- Added: a footer line "Maps opened: n of 5" and a "✓ All five maps opened" mark; XLab has no progress display. The header eyebrow drops XLab's "Verification Track ·" prefix and keeps "Evidence companion".
- Completion: XLab's component never calls onComplete, so there is no source condition to mirror. The port calls Lens.complete() when all five tabs have been opened (the only natural "done" for an exploration widget). If the orchestrator prefers no completion at all, delete the two lines in persist() that call Lens.complete().
- State saved: current map, selected mechanism, ordered list of maps viewed, ordered list of mechanisms inspected. Standalone fallback uses localStorage key "lens-widget-evidence-taxonomies".
- No em dashes in source data; no rewrites were needed.
:::

#### Widget
source:: [[../widgets/evidence-taxonomies]]

#### Text
content::
\## Part 1 · Week 5: Hardware verification

Module file: [[../modules/XLab Verification P1 W5 Hardware verification]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-hw-attestation]]

#### Text
content::
\#### Hardware opening puzzle, ClaimLedger (claim-ledger)

**Decision: widget.** Seven claims judged on one three-point scale, toggled and kept, then read back at the end of the section: Lens Choice segments cannot toggle, cannot show "what you recorded" later, and the return in 2.1.8 is today a bare bullet list with a link back.

**Target lens:** [[../Lenses/XLab Verification - v-hw-attestation]] and [[../Lenses/XLab Verification - v-hw-policy-studio]]

**Where it goes:** v-hw-attestation: after "Before reading further, classify each conclusion as **supported**, **possibly supported if the system was designed to measure it**, or" (drop the "Proposed conclusion:" line, the widget prints it). v-hw-policy-studio: after "In [[../Lenses/XLab Verification - v-hw-attestation|2.1 Hardware]] you classified each of these conclusions as supported," replacing the seven-bullet list.

**What it replaces:** v-hw-attestation: the seven `Question: Choice` segments (ids 6aff61bf, 45dad21d, 188fe444, 6e4a14c9, 9c7cd240, f59b326b, 021cf8df) and the following Text line "Keep your answers. You will return to them at the end of the section." (the widget carries that sentence in its footer): remove entirely. v-hw-policy-studio: the bullet list of the seven claims under "Return to the opening puzzle" and the reviewer comment about Lens not recalling across lenses: remove entirely; keep the sentence "Look back at what you recorded before reading on." and XLab's two resolution paragraphs below the widget.

**In XLab:** `<ClaimLedger id="hw-opening-puzzle" set="hardware-opening" />` in hardware-attestation.mdx (core, not in a Fold) and `<ClaimLedger id="hw-opening-puzzle" set="hardware-opening" recall />` in hardware-policy-studio.mdx (core, after the MemoDesk, not in a Fold)

**Learner time:** 5 minutes at the start, 2 minutes at the return

Reads seven proposed conclusions the laboratory's 20,000 attestation tokens might support and, for each, presses one of three judgments: Supported, Possibly supported if the system was designed to measure it, or Unsupported by attestation alone. Pressing the selected judgment again clears it, as in XLab. "Keep your answers" flips the card to the read-only "What you recorded" view (check mark and the judgment text per row; a blank row says "You did not record a judgment for this one."); "Change your answers" reopens it. At the end of the section the same widget appears under "Return to the opening puzzle" and shows what they recorded, with XLab's resolution paragraphs beneath it; there is no answer key inside the widget, in either view.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- Data: `src/lib/verification/data/hardware-opening-puzzle.ts` (HARDWARE_OPENING_PUZZLE) at HEAD of the xlab-tracks clone; all 15 strings verified present verbatim by script. Component behaviour from `src/components/mdx/reader/claim-ledger.tsx`: eyebrow "Your judgment" / "What you recorded", toggle-off on re-press, no key, no grading. The `lead` field ("Proposed conclusion") is in the data but not rendered by XLab's component; the widget prints it as the list heading, matching the Lens page's existing "Proposed conclusion:" line.
- Adapted: XLab's recall is a separate `recall` prop rendered on a different page from the same localStorage mark. A Lens widget cannot know which lens it sits in, so the learner switches views with "Keep your answers" (button label taken from XLab's prose line "Keep your answers.") and "Change your answers" (UI chrome, not XLab text). If a learner reaches 2.1.8 without ever pressing Keep, they see the editable ledger there instead of the recall view; they can still judge and keep it before reading the resolution.
- Rewrite: XLab's blank-row text "you did not record a judgment for this one" (which opens with an em dash in the source) became "You did not record a judgment for this one." (dash dropped, capitalised, full stop added).
- Added chrome: "N of 7 judged" counter and the "Answers kept" status, so state is visible without colour.
- Completion: XLab's ClaimLedger completes nothing. The widget calls Lens.complete() when the learner keeps a ledger with all seven rows judged (never on partial keeps), so `required:: true` is meaningful if the orchestrator wants it.
- Standalone: falls back to localStorage key `lens-claim-ledger-hw-opening-puzzle`.
:::

#### Widget
source:: [[../widgets/claim-ledger]]

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-hw-claim]]

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
n/a: every activity already has an Open segment in its lens and every Prompt is already a callout; nothing to add.
:::

#### Text
content::
\### Lens: [[../Lenses/XLab Verification - v-hw-where-trust-lives]]

#### Text
content::
\#### Six verification layers by subgoal (six-layers-grid)

**Decision: widget.** Figure 2 of Baker et al. is a six by four grid whose cells are only readable as a picture; clicking a layer or a subgoal is the only way to put a cell next to the paper's own summary, advantages, disadvantages and subgoal definition without printing four tables.

**Target lens:** [[../Lenses/XLab Verification - v-hw-where-trust-lives]]

**Where it goes:** in the article `articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment.md`, put `![[../widgets/six-layers-grid]]` on its own line after line 382, "Figure 5: Summary of how the on-chip verification layer would complete each subgoal." That line is inside the `v-hw-where-trust-lives` excerpt `from:: ### 4.1 On-Chip Verification Layer` (article lines 372 to 384), so the widget appears at the first point in the article where any assigned excerpt shows a slice of the layer grid.

**What it replaces:** nothing is removed. What is there today is the hotlinked arXiv image `x5.png` (Figure 5, the Layer 1 slice) and its caption, directly under Table 5. Both should stay: they are the reading's own figure, they render for a reader with no JavaScript, and the widget generalises them rather than reproducing them. The same applies to Figure 6 (line 440) and Figure 7 (line 522) in the other two excerpts.

**In XLab:** not an XLab widget. There is no `<VerificationExercise>` for this figure; XLab assigned the paper as a reading. The interactive is a rendering of the article's own Figure 2 (with Figures 5 to 7 as its row slices) and Tables 1, 5, 7 and 8.

**Learner time:** 6 minutes

The grid is drawn as a live table: four subgoal headers (1A, 1B, 2A, 2B) across the top, six layer rows down the side grouped into on-chip, off-chip and personnel-based, and the mechanism the paper names in each cell. Clicking a layer row lights that row's cells and opens the paper's summary of the layer, its key advantages and key disadvantages, and the mechanism it offers for each subgoal in turn. Clicking a subgoal header instead lights that column and opens the Section 3.2 definition of the subgoal alongside what each of the six layers offers for it. Done means all six layers have been opened; the status line counts them and the row keeps a visible "opened" mark, so progress is legible without colour.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
Cell text, the four subgoal headers and their one-line goals, and the row and group labels are transcribed from Figure 2 (`https://arxiv.org/html/2507.15916v1/x2.png`, saved at `SCRATCH/figs/baker-x2.png`) and cross-checked against the Layer 1 slice in Figure 5 (`SCRATCH/figs/baker-x5.png`). The summary, key advantages and key disadvantages for each layer are the article's own table cells (Table 1 at article lines 83 to 88, repeated as Tables 5, 7 and 8 at lines 376, 435 to 436 and 516 to 518). The subgoal definitions are the Section 3.2 paragraphs. The caption notes for Figures 6 and 7 are carried on the layers they describe. The Section 4.1 / 4.2 / 4.3 pointers on each layer come from the Table 1 rows.

Two rewrites, both permitted: the em dash in "six layers of verification, six largely independent assurances of compliance" is a colon in the widget, and footnote markers are dropped from the Subgoal 1.A definition. Everything else is verbatim, including the paper's own inconsistent quote marks in the Figure 6 caption note and the hyphen-plus-space in "implementation- ready" as it appears in the table.

Dropped: the supplementary-mechanisms row at the bottom of Figure 2 (its own Figure 8 sits outside every assigned excerpt, and the row's items have no per-item text in the paper), and the green/red Verifier-trusted icons from the table rows (a colour swatch carrying one bit, which the widget cannot restate without inventing wording).

Second embed, optional: `v-human-insiders` (Part 2 W08) assigns lines 512 to 526, which contains Figure 7 but not Figure 5, so with a single embed those learners do not get the widget. A second `![[../widgets/six-layers-grid]]` after line 524, "Figure 7: Summary of how personnel-based verification layers would complete each subgoal...", would cover them. Two embeds of one id share one saved state, so a learner who opened all six layers in Part 1 would arrive in Part 2 already complete. Editor's call; I have written the placement above as one embed.
:::

#### Widget
source:: [[../widgets/six-layers-grid]]

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
\#### The Collection Map (collection-map)

**Decision: widget.** A seven-tile grid in two families that the learner opens one at a time, with an open/close detail panel and an explored-tiles mark; prose callouts cannot track what was explored or show one discipline against the grid.

**Target lens:** [[../Lenses/XLab Verification - v-intel-signatures]]

**Where it goes:** after "Those are the signatures. The disciplines below are the ways a watcher picks them up", the last paragraph of the "How we see traces" Text segment

**What it replaces:** the next Text segment ("\### The collection map", the lede, the two bold family labels "Collects language" / "Collects physics", and seven collapsed callouts OSINT through MASINT). It should go entirely: the widget carries every sentence of it, and keeping both doubles the reading. The lens's `summary_for_tutor` then needs its "rendered as collapsed callouts" phrase changed to point at the widget.

**In XLab:** `<VerificationExercise id="collection-map" />` in intelligence-signatures.mdx, core, not inside a Fold, under "## How we see traces"

**Learner time:** 5 minutes

Sees seven discipline tiles (glyph, abbreviation, name) in two rows labelled "Collects language" (OSINT, HUMINT, SIGINT, CYBER) and "Collects physics" (IMINT, GEOINT, MASINT). Clicking a tile opens a panel with what the discipline is, "Picks up" and "Characteristic limit"; clicking the same tile again or the close button closes it. Opened tiles get a "✓ Opened" mark and a counter reads "n of 7 disciplines opened"; at seven it turns to "✓ All 7 disciplines opened" and the widget calls `Lens.complete()`.

:::callout {title="Fidelity notes" tone="neutral" collapse="closed"}
- All copy (title, lede, family labels, legend, the two panel labels, and every discipline's name, what, seen, limit) is verbatim from `xlab-tracks/src/lib/verification/data/collection-map.ts` (HEAD). Seven em dashes in that file were replaced with a colon, a comma or parentheses (OSINT limit, HUMINT what, SIGINT what, CYBER seen, IMINT limit, GEOINT what, MASINT what). A script compared all 42 XLab strings against the widget with only those swaps allowed: 0 mismatches.
- Glyphs are the seven inline SVG paths from `xlab-tracks/src/components/verification/widgets/collection-map.tsx`, rebuilt with `createElementNS`.
- Added beyond XLab: the "✓ Opened" mark, the "n of 7 disciplines opened" counter, and the close button (XLab closes only by re-clicking the tile). These are state indicators, not curriculum.
- Completion: XLab's component never calls `onComplete` (registry entry `bridged: false`), so there is no XLab finish condition to mirror. The widget calls `Lens.complete()` once all seven tiles have been opened. Drop that call if the orchestrator wants strict parity; nothing else depends on it.
- CYBER wording: the Lens callout today says "MIRI's draft names it inside national technical means, at item 17 of Article II's definitions." XLab's data says "MIRI's Definition 17 names it inside national technical means." The widget keeps XLab's sentence per the fidelity rule; if the Lens rewrite was a deliberate correction, edit that one string in the widget.
- State: `{opened: [ids], openId}`; restore re-marks opened tiles and reopens the panel that was open. Standalone fallback uses `localStorage` key `lens-widget-collection-map`.
:::

#### Widget
source:: [[../widgets/collection-map]]

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
