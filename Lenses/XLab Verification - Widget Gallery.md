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

