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
\## Built from the embedded readings (2026-09-19, after the owner's go)

Widget where interaction adds something over the figure, image otherwise:

- Wasil et al.: wasil-method-explorer (ten methods, four attributes, R&D maturity, Table 1 limitations and complements) on v-intel-signatures.
- Baker et al.: the existing six-layers-grid on v-hw-where-trust-lives extended with layer toggles, coverage tiles and Table 2 requirements.
- Scher et al.: scher-threshold-explorer (Tables 1 and 2 plus the Figure 2 model ladder, thresholds and cluster size as inputs) on v-paper-scher-treaty and v-intel-signatures. Figure 3 stays an image: the paper gives no Pareto parameters.
- Cankaya: cankaya-audit-calculator (Appendix A1 formula, reproduces all three tables) on v-covert-system-overview.
- Heim et al.: heim-signal-explorer (Tables 3 and 4) on v-cloud; figures 1, 10 to 13 restored from the arXiv SVGs.
- O'Gara et al.: ogara-chip-locator on v-hw-accounting, ogara-license-check on v-hw-authorization.
- Egan and Heim: schematic only, image.

#### Text
content::
\## Follow-ups

- Heim article: figures 5 to 8 exist only as trim-crops of Figure 4 in the LaTeX source; arXiv ships them uncropped, so they were removed rather than shown five times. Cropped attachments would need hosting. The paper also prints Figures 1 and 2 twice; the second Figure 2 removal is a pending suggestion.
- Scher article: Tables 1 and 2 render raw LaTeX in every cell (bullet macros, `$10^{2}$` notation); needs a cleanup pass.
- Wasil paper inconsistencies a learner will notice next to the explorer: the Figure 6 caption says twelve methods over a ten-row figure, the caption's asterisk notes do not match the grid, and data center inspections lack the country-authorisation mark the text implies.
- AI 2040 article: the bullet timeline now matches the chart (the source has only the chart); the prose still says the 2 percent pilot clusters come online by September while the chart says November.
- Unused alternative widget files still under widgets/: policy-quick-check, policy-on-paper, same-claim.
- Platform: no cross-lens widget state, so the ClaimLedger return point opens blank; four control exploration widgets never call complete because they have no commit.
- Portfolio allocation (control): stacking the three regimes made the widget about 2500px tall at 880px; bring a scenario switcher back if that is too much.

