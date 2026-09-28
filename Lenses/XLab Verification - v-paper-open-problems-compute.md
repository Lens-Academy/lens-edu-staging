---
id: 'b8e1b64b-88d9-4398-9f53-6d4ca9e76424'
title: "Open problems: verifying and securing compute"
tldr: "Two sections of Open Problems in Technical AI Governance (Reuel, Bucknall, Casper, Heim et al., 2024): what is still unsolved in verifying where chips are and what they run, and in hardware mechanisms, anti-tamper and enforcing limits on compute use. Optional reading to close the unit."
summary_for_tutor: "Optional reading at the end of Week 5 (Hardware verification). Two excerpts from Reuel, Bucknall, Casper, Heim et al., Open Problems in Technical AI Governance (arXiv 2407.14981, 2024, CC BY 4.0): section 5.2 Verification: Compute (5.2.1 chip location, 5.2.2 compute workloads via TEEs or a trusted neutral cluster, non-AI workloads) and section 6.2 Security: Compute (6.2.1 TEEs on AI accelerators, 6.2.2 anti-tamper hardware, 6.2.3 enforcing compute usage restrictions: remote attestation of disaggregated machines, restricting cluster configurations). Each section opens with numbered example research questions. Help the learner map each open problem to the unit's lenses (attestation, the trusted statement, measuring use, authorization, where trust lives) and say which link in the verification chain it leaves unsupported. The paper dates from mid-2024; some hardware facts (for example the H100 as the notable GPU TEE) may have moved since."
tags: []
duration_minutes: 15
---
#### Text
content::
Optional. This unit showed how attestation, measuring use and authorization are meant to work; these two sections of *Open Problems in Technical AI Governance* (Reuel, Bucknall, Casper, Heim et al., 2024) list what is still unsolved in each, as concrete research questions.

#### Article
source:: [[../articles/reuel-open-problems-in-technical-ai-governance]]
from:: ### 5.2 Compute
to:: that could be explored in future research.

#### Article
from:: ### 6.2 Compute
to:: all of which are open problems.

#### Text
content::
:::callout {title="Source" tone="neutral" collapse="closed"}
Reuel, Anka, Ben Bucknall, Stephen Casper, Tim Fist, Lisa Soder, Onni Aarne, Lewis Hammond, et al. "Open Problems in Technical AI Governance." *arXiv*, 2024. [arxiv.org/abs/2407.14981](https://arxiv.org/abs/2407.14981)
*Sections 5.2 (Verification: Compute) and 6.2 (Security: Compute), pages 27 to 29 and 34 to 36 of the paper. Licensed CC BY 4.0.*
:::
