---
id: '67977ae1-be51-4cc8-b464-5ccc714db95b'
title: "2.2.3 Detection gaps and policy limits"
tldr: {--{"author":"Elias's AI","timestamp":1788016189822}@@"Faithful alpha import of XLab lesson 2.2.3 Detection gaps--}{++{"author":"Elias's AI","timestamp":1788016189822}@@"A rule that counts compute per account is only as good as the unit it adds up over: split a run across accounts or days and every piece stays under the line. RAND models that gap; Carnegie asks whether closing it pushes customers toward providers++} and {--{"author":"Elias's AI","timestamp":1788016189822}@@policy limits."--}{++{"author":"Elias's AI","timestamp":1788016189822}@@countries the rule cannot reach."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016189822}@@"Imported --}{++{"author":"Elias's AI","timestamp":1788016189822}@@"Reading lens adapted ++}from {++{"author":"Elias's AI","timestamp":1788016189822}@@XLab lesson 2.2.3. Two external readings with ++}XLab's {--{"author":"Elias's AI","timestamp":1788016189822}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed--}{++{"author":"Elias's AI","timestamp":1788016189822}@@reading instructions: the RAND report by Moon et al. (2025) on detection gaps in a game-theoretic model of compute governance (read the assigned parts on rand.org; the report itself is not inlined), and Noah Tan's Carnegie article (2026)++} on {--{"author":"Elias's AI","timestamp":1788016189822}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788016189822}@@the geopolitics of cloud controls, whose three assigned sections are inlined as article excerpts. No questions in this lens. If the learner asks about the BLOOM calculation, keep it as an illustration of how an evader exploits the unit a rule aggregates over, not as a threshold recommendation. Ends with a Works cited callout."++}
tags: [wip]
duration_minutes: 30
---
#### Text
content::
\## 2.2.3 Detection gaps and policy limits

KYC can link cloud activity to an identified customer, but motivated users may
split or reroute workloads to avoid scrutiny. The RAND reading examines these
technical gaps; the Carnegie article asks whether broader controls can work
across providers and jurisdictions.

\### [Strategies and Detection Gaps in a Game-Theoretic Model of Compute Governance](https://www.rand.org/pubs/research_reports/RRA3686-1.html)
Moon, Vedula, Geneson, and Bar-on | RAND Corporation (2025)

Read these parts in the original report:

- **Summary → Findings and Recommendations** (printed pp. iv–v).
- **Cloud Service Provider Monitoring Strategies** through the end of **Detection Game** (printed pp. 4–5). Identify the mandatory metrics, the reporting rule, and the win condition.
- **Finding Detection Gaps** and **Finding a Detection Gap** through the sequential-training calculation; stop before **Predictions About Models in the Detection Gap** (printed pp. 5–7).
- **Closing Detection Gaps**: its opening, then **Output and User Identity** in full (printed pp. 9–11). Note which proposals add another metric and which add another kind of information.

Do not turn the BLOOM calculation into a timeless threshold recommendation. Its job here is to show how an evader can exploit the unit over which a rule aggregates activity.

RAND shows how evasion depends on what a rule measures and how activity is
grouped. Carnegie then asks what broader coverage would cost—and whether it
would push users toward providers or jurisdictions beyond the rule.

\### [The Geopolitical Debates Over Controlling Cloud Compute](https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute)
Noah Tan | Carnegie Endowment for International Peace (2026)

Read these parts in the original article:

- **What Do Cloud Controls Attempt to Solve?** in full.
- In **The Case Against Cloud Controls**, begin with “Some analysts also contend that cloud restrictions risk pushing users in third-party countries toward China’s competing AI stack” and read to the end of the section.
- **Cloud Controls Must Contend With “Who” and “What” They Restrict** in full.

Extract the decisions the technical readings do not settle: which users and activities are covered, who bears the compliance burden, how evasion shifts across jurisdictions, and what over-broad coverage costs.{++{"author":"Elias's AI","timestamp":1788016201186}@@
{>>{"author":"Elias's AI","timestamp":1788016201186}@@The Carnegie article is already imported as articles/tan-the-geopolitical-debates-over-controlling-cloud-compute, so the three assigned sections are inlined below. The RAND report is not: the stored articles/moon-... file holds only the rand.org landing page (key takeaways, recommendations), not the report text, so that reading card stays a link.<<}

#### Article
source:: [[../articles/tan-the-geopolitical-debates-over-controlling-cloud-compute]]
from:: ### What Do Cloud Controls Attempt to Solve?
to:: Restricting only rentals to foreign data centers would naturally encourage Chinese firms to consider pivoting toward the other loophole—renting cloud compute directly from U.S.-based data centers.

#### Article
source:: [[../articles/tan-the-geopolitical-debates-over-controlling-cloud-compute]]
from:: Some analysts also [contend](https://carnegieendowment.org/research/2024/12/ai-artificial-intelligence-export-united-states) that cloud restrictions risk pushing users in third-party countries toward China’s competing AI stack.
to:: policymakers will need to weigh the net security benefits of cloud controls against the diplomatic costs of unilaterally extending U.S. regulatory reach into an inherently transnational service.

#### Article
source:: [[../articles/tan-the-geopolitical-debates-over-controlling-cloud-compute]]
from:: ### Cloud Controls Must Contend With “Who” and “What” They Restrict
to:: Whatever the answers may be, Washington will play an important role in determining the future of U.S.-China AI competition.++}

{--{"author":"Elias's AI","timestamp":1788016201186}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-detection-gaps)*--}{++{"author":"Elias's AI","timestamp":1788016201186}@@#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Both readings, Moon et al. (2025) for RAND and Tan (2026) for Carnegie, are cited inline above with their links.

XLab. "2.2.3 Detection gaps and policy limits." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-detection-gaps)
*The source lesson this page adapts.*
:::++}
