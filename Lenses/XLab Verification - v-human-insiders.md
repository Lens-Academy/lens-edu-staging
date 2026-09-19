---
id: 'dae72ebf-335a-4bd5-b970-b2b3e72230ed'
title: "Insiders and human sources"
tldr: "An insider's job title tells you where they stood, not what they saw. Read Baker et al. on whistleblower programs, interviews, and intelligence, then work six Project Lattice sources one at a time: what each could observe, what stayed out of view, and which record they never controlled could check the claim."
summary_for_tutor: "Two excerpts from Baker et al. (2025), section 4.3 and Appendix A.8, are embedded as Article segments. Then an optional drill built from XLab's Who knows what? widget: six source cards (evaluator, training engineer, infrastructure operator, procurement, contractor, executive), each with three graded choice questions on observation, boundary, and corroboration, followed by a Project Lattice case report with four graded credibility questions, a final finding, and four failure modes. When the learner over-reaches, apply the widget's own line: a job title alone proves nothing; limit the claim to what the person could observe."
tags: [wip]
duration_minutes: 15
---
#### Text
content::
In this section, you will learn about the three main categories of human- or
personnel-based verification: whistleblower programs, personnel interviews,
and national intelligence activities. First, read the below excerpt of Baker's
_Verifying International Agreements on AI_ paper, paying attention to each
mechanism's unique strengths, failure modes, and applicable circumstances.

\## Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment

Mauricio Baker, Gabriel Kulp, Oliver Marks, Miles Brundage, and Lennart Heim (2025). [arxiv.org](https://arxiv.org/abs/2507.15916v2)

This page reproduces [§4.3 “Personnel-Based Verification Layers”](https://arxiv.org/html/2507.15916#S4.SS3) and [Appendix A.8 “Whistleblower Programs”](https://arxiv.org/html/2507.15916#A1.SS8) in full, including Tables 8, 9, and 14.

The source text and tables are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: ### 4.3 Personnel-Based Verification Layers
to:: In contrast to other, more technical verification mechanisms, _personnel-based verification_ relies on the difficulty of having large groups of people collude without disclosures or leaks. Verifiers could systematically seek disclosures or leaks through whistleblower programs, interviews of personnel, and national intelligence activities. Intelligence activities, though, might involve cyber or signals intelligence, not only direct communication with personnel.

#### Text
content::
We'll pay special attention to whistleblower programs, which have the most
historical precedence, existing infrastructure, and potential verifiability
effectiveness.

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: #### A.8 Whistleblower Programs
to:: Avoiding excess disclosure: Employees could be allowed to disclose only a very small amount of information to the Verifier, as discussed in above footnotes. Further, the Prover and Verifier could jointly state agreed-on, reasonable bounds of protected whistleblowing (including high-level descriptions of potential violations and information to investigate further, but excluding digital transfers of Prover models, data, or code outside of a confidentiality-preserving technology). Parties could also agree on what questions or information a Verifier may share with an employee, so that the Prover could learn from their employees if the Verifier is inappropriately pressuring them to disclose IP.

#### Text
content::
\## Insider Report

Even when the human source is truthful and legally allowed to report, however,
reporting channels can still fail in various ways, which the next section will
cover.

:::callout {title="Optional: Insider Report (8–10 minutes)" tone="neutral" collapse="closed"}
**Who knows what?**

For each source, identify what they could observe, what they could not know, and which independent record could verify the claim. You will produce a short assessment for each source.

A job title alone proves nothing. Limit the claim to what this person could observe, state what remains unknown, and choose evidence the source did not control.

Every question in this exercise is optional. Six sources come first; a case report and a credibility assessment follow.
:::

\### Optional warm-up: who knows what?

Six people sit at different stations around the same suspected violation. For each, identify what they could observe, what they could not know, and which independent record could verify the claim. Work through all six sources, then assess a case report and issue a finding.

#### Widget
source:: [[../widgets/human-insiders]]

#### Text
content::
:::callout {title="Why a consistent account may still be wrong (open after you have issued the finding)" tone="neutral" collapse="closed"}
A human source can tell an investigator where to look and which records to preserve. Technical or physical evidence is still needed for facts the source did not observe. Four ways a consistent account can still mislead:

- **Selective truth.** The expansion may be real even if the claimed prohibited workload is not. Do not treat proof of infrastructure as proof of how it was used.
- **Coordinated cover story.** Matching accounts are not independent if managers selected, briefed, or monitored the speakers.
- **Management staging.** A clean tour and selected records show what management chose to present. They do not rule out undeclared activity elsewhere.
- **Suppression.** A lack of reports means little if staff have no safe reporting channel, cannot see the relevant declarations, or reasonably fear retaliation.
:::

#### Text
content::
\### Construct a case

Give one example of a situation in which all three conditions are satisfied:

1. An insider's report about a prohibited AI activity is accurate.
2. The insider is legally permitted to report what they know.
3. The verification regime cannot turn the report into actionable evidence.

Describe the situation and explain why each condition is satisfied. Use 100 to 180 words in total, across the four boxes below: Insider, Information, Reporting route, Failure point.

#### Widget
source:: [[../widgets/construct-case]]

#### Text
content::
:::callout {title="Check your case (open after you have submitted)" tone="neutral" collapse="closed"}
- Is the allegation actually true?
- Could this insider plausibly know it?
- Is reporting permitted?
- Does the verification failure arise from the institution rather than from the allegation being false?
- Can you identify the precise missing link between report and action?
:::

:::callout {title="Where a report can die (open after you have submitted)" tone="neutral" collapse="closed"}
Naming where a report dies is the work, so this list sits here and not above the exercise. Four failures that do not count: the insider lies, the insider is wrong, reporting is illegal, or the verifier ignores the report for no reason.

Some that do count:

- Evidence cannot be independently corroborated.
- The authorized recipient cannot legally share the information with the verifier.
- The report identifies a suspicious activity but not the facility or account involved.
- Relevant records are unavailable or outside the verifier's mandate.
- The reporting channel strips information needed for follow-up.
:::

:::callout {title="Two cases that work, for different reasons (open after you have submitted)" tone="neutral" collapse="closed"}
**The failure is corroboration.**

*Insider:* A scheduling engineer at a cloud provider, working on the team that allocates accelerator capacity to enterprise customers.

*Information:* She saw a single customer account hold 12,000 accelerators in one region for nineteen continuous days, under a contract flagged for research use. The allocation is real and she read it off the systems she administers.

*Reporting route:* She files under the provider's protected-disclosure policy, which permits reporting suspected treaty violations to the national authority, and she does so.

*Failure point:* The authority can establish that the capacity was held. It cannot establish what ran on it. The workload records belong to the customer, not the provider, and no route obliges the customer to produce them. The report stalls one step short of the activity it alleges.

**The failure is who may be told.**

*Insider:* A compliance officer at a chip vendor, responsible for export-control screening.

*Information:* He processed a set of shipments whose declared end use does not match the delivered configuration, and the discrepancy is in the file he signed.

*Reporting route:* He reports to the national export-control agency, which is the recipient his own law names and protects.

*Failure point:* The agency believes him and opens its own case. What it cannot do is hand the file to the international verifier: the shipment records are commercially confidential and the agency has no authority to share them across the border. The verifier is told a concern exists and is given nothing it can act on.
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*A six-layer verification framework whose personnel-based layers map which workers can observe different violations and why disclosures still need independent confirmation.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI — Appendix A.8: Whistleblower Programs." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/html/2507.15916#A1.SS8)
*Baker et al. examine secure contact, suppression, incentives, confidentiality, and which supply-chain personnel can observe different violations.*

XLab. "2.4.1 Insiders and human sources." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-insiders)
*The source lesson this page adapts, including the Who knows what? source-assessment exercise.*
:::{>>{"author":"Elias's AI","timestamp":1788015819856}@@Widget human-insiders rebuilt from src/lib/verification/data/human-insiders.ts: 18 source questions (6 actors x observe/boundary/corroborate), 4 credibility questions on the Project Lattice case report, final finding and failure modes. Option order follows the data file's choices order. All optional because XLab folds it as optional.<<}
