---
id: '61088782-f0b8-4eeb-9787-1e6c80760ae9'
title: "1.3 Upstream and downstream"
tldr: {--{"author":"Elias's AI","timestamp":1788016738481}@@"Faithful alpha import --}{++{"author":"Elias's AI","timestamp":1788016738481}@@"Two documents from the same side agreeing with each other is not verification; it is one actor being consistent with itself. Sit on an IAEA team at Fordow in January 2023, watch a true sentence fail because every claim in it came from Iran, and rewrite it so each claim carries its source. Then ask ++}of {--{"author":"Elias's AI","timestamp":1788016738481}@@XLab lesson 1.3 Upstream--}{++{"author":"Elias's AI","timestamp":1788016738481}@@every report: whose claims am I relying on,++} and {--{"author":"Elias's AI","timestamp":1788016738481}@@downstream."--}{++{"author":"Elias's AI","timestamp":1788016738481}@@who acts on mine?"++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016738481}@@"Imported from XLab's canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises--}{++{"author":"Elias's AI","timestamp":1788016738481}@@"Worked case, then a memo brief. The Fordow case: a first-draft finding that is true in every clause but built only on Iran's declaration and the operator's records; the three upstream sources ranked by how much they deserve trust; the 83.7 percent swipe sample that broke the declaration; a revised finding that keeps each claim attached to its source; two downstream readers (the IAEA Board of Governors needs a determination, ISIS analysts need the raw discrepancy) and why a report++} must {--{"author":"Elias's AI","timestamp":1788016738481}@@be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788016738481}@@serve both. Two notebook prompts are optional Open questions (pause before reading on; the two questions to answer before writing). The memo slot for this lesson is the actor, authority, and evidence map (optional here). The Context Distiller exercise is the next lens. When discussing, keep the provenance test central: which claims were verified independently, which inherited from the actor being checked."++}
tags: [wip]
duration_minutes: 10
---
#### Text
content::
Earlier, you followed a chip from sand to server and saw that verifiability depends on where you sit in the supply chain. Documents behave the same way. A verification report draws on sources upstream of it and feeds decisions downstream of it, and writing a useful one starts with understanding both. To watch this happen in a regime that already runs at treaty scale, sit with the one international inspectorate that has been doing this work for decades: the International Atomic Energy Agency.

\### The Setup

Put yourself on an IAEA verification team at the Fordow Fuel Enrichment Plant in Iran in January 2023. Iran is a party to the Nuclear Non-Proliferation Treaty and has a safeguards agreement with the Agency, so it must declare its nuclear material and enrichment activity, and the Agency's job is to confirm that the declaration is complete and correct. Iran has declared that it enriches uranium at Fordow to 60 percent U-235. That is already far above the 3.67 percent cap of the 2015 nuclear deal and well beyond any civilian power need, though still short of the roughly 90 percent that counts as weapons grade.

Your first draft of the central finding reads:

:::callout {title="Initial finding" tone="red"}
"Enrichment at Fordow is 60 percent U-235, below weapons grade, and the facility's operating records match the declaration."
:::

#### {--{"author":"Elias's AI","timestamp":1788016743664}@@Question--}{++{"author":"Elias's AI","timestamp":1788016743664}@@Question: Open++}
{++{"author":"Elias's AI","timestamp":1788016743664}@@id:: bbb153b5-c932-4f0d-a379-bc451bb3c5fd
++}content:: Pause before reading on. What is wrong with this sentence? Every clause in it is true.
{++{"author":"Elias's AI","timestamp":1788016743664}@@optional:: true{>>{"author":"Elias's AI","timestamp":1788016743664}@@Legacy #### Question converted to Question: Open with a fresh id. XLab renders this as a notebook callout that gates nothing, hence optional. The invalid ++}feedback:: false{++{"author":"Elias's AI","timestamp":1788016743664}@@ line is dropped.<<}++}

#### Text
content::
The problem is provenance. Iran declared the 60 percent figure, and the operating records that "match" it are kept by the Atomic Energy Organization of Iran, which runs the plant. Two sources produced by the same side agreeing with each other is not verification; it is one actor being consistent with itself. Your draft presents that internal consistency as if it were confirmation, and it leaves out the one stream that came from somewhere else.

Three sources sit upstream of your report, and they do not deserve equal trust:

- Iran's declaration. Iran is the party the treaty binds, which gives it the strongest reason to understate enrichment or omit activity it would rather not explain.
- The facility's operating records. The operator maintains these itself, and an operator has every reason to keep its records consistent with the state's declaration.
- Independent Agency measurements. Environmental swipe samples, tamper-indicating seals and cameras the Agency installs, and satellite imagery of the site are all difficult for Iran to alter after the fact. None of them restates Iran's declared number; each one is collected or controlled by the inspectorate, which is what lets them check the declaration rather than echo it.

Here the independent stream is decisive. Inspectors swiped surfaces at Fordow and sent the samples to the Agency's laboratory in Austria, which can detect uranium particles at below a trillionth of a gram and read their enrichment level directly. The swipe taken on 22 January 2023 contained particles enriched to 83.7 percent U-235, above the declared 60 percent and close to weapons grade. Inspectors had also found two IR-6 centrifuge cascades configured substantially differently from what Iran had declared.

A revision that keeps each source attached to its claim:

:::callout {title="Revised finding" tone="green"}
"Iran declares enrichment at Fordow to 60 percent U-235, and the operating records kept by the Atomic Energy Organization of Iran agree with that declaration. Environmental swipe samples the Agency collected on 22 January 2023 contained particles enriched to 83.7 percent U-235, above the declared level and approaching weapons grade, and inspectors found two IR-6 cascades configured substantially differently from the declaration. Iran attributes the particles to unintended fluctuations while transitioning cascades toward 60 percent production. The Agency has not confirmed that account, and discussions to clarify the matter are ongoing."
:::

The revision is longer and less quotable. In exchange, every claim now carries its source, and a reader can weigh each one against the actor that produced it. That matters because your readers will apply the same test to you.

{--{"author":"Elias's AI","timestamp":1788016745672}@@\##--}{++{"author":"Elias's AI","timestamp":1788016745672}@@\###++} Downstream: Who Acts on{--{"author":"Elias's AI","timestamp":1788016745672}@@ the Finding?

\### Downstream:--}{++{"author":"Elias's AI","timestamp":1788016745672}@@ This?{>>{"author":"Elias's AI","timestamp":1788016745672}@@"Downstream:++} Who Acts on {--{"author":"Elias's AI","timestamp":1788016745672}@@This?--}{++{"author":"Elias's AI","timestamp":1788016745672}@@the Finding?" was XLab's PageBreak title, imported as a duplicate heading; kept only the real heading.<<}++}

Two readers will use this finding, and each needs something different from it.

The IAEA Board of Governors has to decide whether the finding meets the bar to declare Iran in non-compliance with its safeguards obligations and report the matter to the UN Security Council, or whether to press Iran for more access first. The Board needs a determination measured against the safeguards standard: whether the 83.7 percent result and the reconfigured cascades clear the threshold for escalation, and what further evidence would resolve Iran's explanation one way or the other. A page of particle counts does not, on its own, tell them whether to act.

Independent analysts, at organizations such as the Institute for Science and International Security, will not accept the Board's determination on faith. From where they sit, the Agency is itself an upstream source with incentives of its own; it has to preserve working access inside Iran, and that can soften how it words a finding. They need the discrepancy itself, with the date, the enrichment level, and which cascades were involved, so they can point their own collection at it, for example commercial satellite imagery of Fordow and tracking of Iran's centrifuge procurement.

A report written only as a determination gives the analysts nothing to check. A report written only as raw findings gives the Board no basis to act. Effective verification writing has to do both, and the revision above aims to do that in one passage.

\### The Takeaway

No verification document stands alone. Every source upstream of you was produced by an actor with incentives, and everything you write becomes an upstream source for readers who will weigh your incentives in turn.

#### {--{"author":"Elias's AI","timestamp":1788016749227}@@Question--}{++{"author":"Elias's AI","timestamp":1788016749227}@@Question: Open
id:: 0a469f70-f02c-4813-8318-9b1d10a4652e++}
content:: Before writing, answer two {--{"author":"Elias's AI","timestamp":1788016749227}@@questions:--}{++{"author":"Elias's AI","timestamp":1788016749227}@@questions.++}

- Upstream: whose claims does this document rely on, and which of them did I verify myself, rather than inherit from the actor being checked?
- Downstream: who will act on this document, and what does each reader need in order to act?
{++{"author":"Elias's AI","timestamp":1788016749227}@@optional:: true{>>{"author":"Elias's AI","timestamp":1788016749227}@@Legacy #### Question converted to Question: Open with a fresh id; XLab's notebook callout gates nothing, hence optional. The invalid ++}feedback:: false{++{"author":"Elias's AI","timestamp":1788016749227}@@ line is dropped.<<}++}

#### Text
content::
The structure carries over to the compute reports this track is building toward. A future report on a training run rests on the same three layers: the lab's own declaration, the utilization logs kept by the cloud provider that hosted the run, and physical streams that are harder to fake, such as on-chip attestation, chip location tracking, and the facility's measured power draw. The IAEA case is decades ahead of the AI case in practice, which is why it is worth reading closely: the questions an inspector asks of a swipe sample are the questions you will ask of a power meter.

Sources for this case: IAEA quarterly report to member states, late February 2023, on the 83.7 percent U-235 particles found at Fordow and Iran's explanation; IAEA materials on environmental swipe sampling and safeguards verification.

The next exercise asks you to apply this directly. You will assemble a report from a pool of candidate details and connect each detail to the reader who needs it. The standard is the one demonstrated here: every claim carries its source, and every finding reaches the actor who acts on it.

\### The Context Distiller Exercise

{--{"author":"Elias's AI","timestamp":1788016751203}@@The--}{++{"author":"Elias's AI","timestamp":1788016751203}@@[[../Lenses/XLab Verification - v-context-distiller|The++} next {--{"author":"Elias's AI","timestamp":1788016751203}@@page--}{++{"author":"Elias's AI","timestamp":1788016751203}@@page]]++} is that exercise. Four reports are on the table; you pick one and
work the whole chain — clip the facts that would change what a reader does,
distil them, name who the report was built from and who reads it next, then
thread each point to the readers who need it.

#### {--{"author":"Elias's AI","timestamp":1788016762589}@@Text--}{++{"author":"Elias's AI","timestamp":1788016762589}@@Question: Open++}
{++{"author":"Elias's AI","timestamp":1788016762589}@@id:: cec5c7fa-f530-4f33-83da-cadb4b7115a2
++}content:: {--{"author":"Elias's AI","timestamp":1788016762589}@@**Import gap:** XLab persistent--}{++{"author":"Elias's AI","timestamp":1788016762589}@@Optional: **Actor–authority–evidence map** (Map, about 700 words)

Actor–authority–evidence map for any element of the supply chain.

This output is a map, not a++} memo {--{"author":"Elias's AI","timestamp":1788016762589}@@desk has no clean Lens equivalent. Use--}{++{"author":"Elias's AI","timestamp":1788016762589}@@— build it as annotated rows, not paragraphs, carrying what the brief above asks each row to hold.
optional:: true
assessment-instructions:: One element of++} the {--{"author":"Elias's AI","timestamp":1788016762589}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-upstream-downstream) for--}{++{"author":"Elias's AI","timestamp":1788016762589}@@advanced-AI supply chain is chosen and named. Score three things, roughly a third each: (1) the actors involved in that element are listed as rows; (2) each row states the authority that actor holds (a jurisdiction, a licence, ownership of a record, the power to interrupt); (3) each row states the evidence that would let an outside party verify what the actor is doing, and whether that evidence is produced by the actor itself or held by someone else. Reward rows that separate self-reported evidence from independently held evidence, the distinction++} this {--{"author":"Elias's AI","timestamp":1788016762589}@@element.--}{++{"author":"Elias's AI","timestamp":1788016762589}@@lesson teaches. No generic praise.
feedback-instructions:: Name the row where the evidence is only the actor's own say-so and ask what independent stream could check it. One short paragraph.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016762589}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-upstream-downstream)*--}{++{"author":"Elias's AI","timestamp":1788016762589}@@:::callout {title="Works cited" tone="neutral" collapse="closed"}
XLab. "1.3 Upstream and downstream." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-upstream-downstream)
*The source lesson this page adapts. The IAEA sources for the Fordow case are named in the prose above and have no URL in XLab's citation registry.*
:::{>>{"author":"Elias's AI","timestamp":1788016762589}@@XLab's memo desk lists three slots for this lesson in src/content/verification/memos.ts: m1-actor-authority-evidence (brief as quoted above, 700 words, status "named": length and audience not drafted, so it is optional here); m1-case-briefing "Case briefing on actors" (600 words, no brief, audience or rubric drafted); and m1-optional "Written output" (unspecified). The two without a brief are not added as questions. Replaces the import-gap placeholder and the XLab source footer.<<}++}
