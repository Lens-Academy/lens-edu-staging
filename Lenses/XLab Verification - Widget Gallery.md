---
id: '6f0d2b9e-3c1a-4e7b-9a52-8d4c1f6e2b73'
title: "Widget Gallery: Compute Verification Parts 1 and 2"
tldr: "Placement record for the Compute Verification widgets: everything from XLab's Verification track and the embedded readings is placed or closed as of 2026-09-19. The page keeps the record by lens, the pending editor suggestions, the build candidates from the readings survey, and the follow-ups."
summary_for_tutor: "An internal record page for course authors, not learner material. It lists where every ported widget now sits in the Compute Verification courses, which relay suggestions still need accepting, and which reading figures are candidates for future widgets. If someone asks, explain that this is a staging record page."
tags: [wip]
duration_minutes: 90
---

#### Text
content::
This page was the review gallery for every interactive built for Compute Verification Parts 1 and 2 from XLab's Verification track and from the readings the course embeds. As of 2026-09-19 every entry has been placed in the course or closed; what remains here is the record, the pending editor work, and the build candidates that still need a decision.

\## Placed, by lens

- v-introduction: The Verification Problem, The Types of AI, The Verification Landscape, Why Are We Concerned About Superintelligence?, A Short History of AI Acceleration (timeline), Test scores of AI systems
- v-theories-of-change: Theory of Change for Your Favorite AI Safety Organization
- v-scoping-effective-feasible: Everything Comes With a Cost, Scoping an Anti-ASI Policy
- v-scoping-anatomy: The Anatomy Drill
- v-interactive-map: The Compute Supply Chain
- v-actor-edges: Who can prove what
- v-context-distiller: The Distiller
- v-mechanism-effective: Place Your Bets (mechanism sort), Five Maps of the Evidence
- v-hw-attestation: ClaimLedger (hardware opening puzzle); v-hw-policy-studio: ClaimLedger again as the return point
- v-hw-where-trust-lives: Six verification layers by subgoal
- v-cloud-evidence: Cloud Evidence Drill
- v-intel-signatures: The Collection Map
- v-human-insiders: Insider Report (optional warm-up), Construct a Case
- v-human-reporting-protection: Four Levers One Each, On Paper, Companies A and B
- v-human-audits-inspections: Four Sources
- v-human-institutions: The Standard of Proof
- v-covert-what-is-it: Worked Example, Training Through the Pause
- v-covert-system-overview: End-to-end execution trace
- v-covert-red-blue: Evasion scenario taxonomy
- v-intuitions-plan-a (AI 2040 verification plan): compute locations treemap, deal implementation timeline, assurance curves, rogue-deployment detection, chip declaration result, chip flow restrictions
- v-intuitions-success: the four AI 2027 charts (METR horizons, superhuman coder forecast, inference prices, takeoff)

Native question segments reviewed and kept as they are: Tasks on the Document Packet, Anatomy of a (Pause) Agreement, The Missing Board, Questions on the Cankaya Working Paper, Expert review Questions 1 to 10.

Judged nothing to port (the page already carries every number, or the figure is a schematic): hardware reader components, intelligence intro pop-ups, memo desk, AI 2040 compute growth, verification plan timeline, research titration diagonal, packet size and logging granularity charts, the AI 2040 diagram images, the AI 2027 neuralese and IDA figures, the supply-chain drill bench.

#### Text
content::
\## Pending suggestions to accept in the editor

Relay edits that touched an inline reviewer comment or human-written prose landed as suggestions. Until they are accepted the platform strips them, so staging still shows the old segments in these regions:

- v-introduction: two stale comments after the timeline caption
- v-scoping-anatomy: the intro block that also carries the Widget segment (reject it and the drill vanishes)
- v-scoping-effective-feasible: both widget block replacements and the exception deletion
- v-interactive-map: the segment swap that inserts the map
- v-actor-edges: the segment split (roster callout, Widget segment, removal of the Draw-the-edges Open question)
- v-mechanism-effective: the mechanism-sort block (lead-in, callout retitle, Ranking-question removal, Widget insert)
- v-context-distiller: the segment swap that inserts the widget
- v-human-reporting-protection: the stale On Paper callout replacement
- v-hw-attestation, v-cloud-evidence, v-covert-what-is-it, v-hw-policy-studio: one stale comment rewrite or deletion each

#### Text
content::
\## Build candidates from the embedded readings (not built, need a go)

A read-only survey of the figures in the seven embedded papers, ranked by what a widget would add over the static figure or table:

1. Wasil et al., Verification methods: Fig 6 plus Fig 5 and Table 1 as one explorer, 12 methods filterable by detection target, access requirement, hardware dependency and R&D maturity, limitations and complements on select. Medium.
2. Baker et al., Six layers: Fig 2 as a six layers by four subgoals matrix, click a cell for the mechanism and its tradeoffs, toggle layers to see coverage collapse. Medium.
3. Scher et al., International agreement: Tables 1 and 2 plus Fig 2 as a cluster-size and FLOP-threshold explorer, time to threshold recomputed live, domestic and international mechanisms side by side. Medium.
4. Cankaya, System overview: the sampling tables as an audit-confidence calculator (sample count, flaw rate, prover share, proof cost). Small.
5. Heim et al., Governing through the cloud: Tables 3 and 4 as an observable-signal explorer. Medium.

Smaller options: O'Gara Fig 7 landmark-delay chip locator, O'Gara Fig 8 license forgery check, Scher Fig 3 Pareto registration curve, Cankaya protocol step-through. Egan and Heim's KYC figure is a schematic, nothing to port.

#### Text
content::
\## Follow-ups

- Heim article: nine broken figures (captions with no image, four panels that render the same PNG as Fig 4), tracked on the Asana task about its duplicated attachments.
- Unused alternative widget files still under widgets/: policy-quick-check, policy-on-paper, same-claim.
- AI 2040 article: the bullet timeline disagrees with the deal timeline chart on three dates (retrofit 50 percent, 95 percent, first post-deal release); the caption line under the two chip declaration tables is byte-identical at both, which blocks single-line anchors.
- Platform: no cross-lens widget state, so the ClaimLedger return point opens blank; four control exploration widgets never call complete because they have no commit.
- Portfolio allocation (control): stacking the three regimes made the widget about 2500px tall at 880px; bring a scenario switcher back if that is too much.

