---
id: '67977ae1-be51-4cc8-b464-5ccc714db95b'
title: "2.2.3 Detection gaps and policy limits"
tldr: "Faithful alpha import of XLab lesson 2.2.3 Detection gaps and policy limits."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. Interactive elements marked as import gaps must be completed on XLab until Lens has an equivalent."
tags: [wip]
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

Extract the decisions the technical readings do not settle: which users and activities are covered, who bears the compliance burden, how evasion shifts across jurisdictions, and what over-broad coverage costs.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-detection-gaps)*
