---
id: '1bfbd032-a554-41da-9025-2c644e774b84'
title: "Intelligence institutions and treaty design"
tldr: "Treaties are strong on protecting spy satellites and weak on making spies share what they see. Nobody blinds the other side's sensors, but nobody is obliged to hand the verifier a tip either. Read the MIRI draft's definition of national technical means and its Article X as a text to mark up, not admire; you will red-line it in 2.3.5."
summary_for_tutor: "Imported from XLab's Verification curriculum; a short reading with no questions. Its thesis is the asymmetric precedent: weak on sharing (no obligation on intelligence agencies to share with verifiers, Baker section 2.3.3), strong on protection (Article X ¶1(b)(i) and (ii) of the MIRI draft, the noninterference-with-NTM and no-deliberate-concealment clauses, which Gottemoeller called one of the easiest points of agreement in New START). It covers Six Layers' argument for national rather than international agencies, MIRI's Article II definition of national technical means (item 17) and Article X ¶1(b)(i) to (iii) as concrete treaty text, and the authentication problem for shared intelligence. Both passages are embedded in this lens as excerpts of the imported paper, and they are the text the 2.3.5 red-line works from; clause (iii), which encourages but does not obligate cooperation, is the lens's own evidence that the precedent is weak on sharing. The wider readings (MIRI draft pp. 20, 39 to 40; Baker 2.3.3; Six Layers) are listed without inline links; the learner is expected to have the MIRI draft from earlier lessons. The Unfinished writing callout is XLab's note that the Six Layers treatment and the treaty analysis questions are not yet written. The written output on this text lives in the next lens, 2.3.5."
tags: [wip]
reading_minutes: 8
tutor_minutes: 0
---
#### Text
content::
The previous sections were about what a watcher can see and conclude. This one
is about the institutions that do the watching, and what a treaty can say about
them.

The precedent is asymmetric, and the asymmetry is the lesson: **weak on
sharing, strong on protection.**

\## Sharing

Nuclear treaties impose no obligation on intelligence agencies to share with
treaty verifiers. Sharing is voluntary, informal, and inconsistent (Baker
§2.3.3) — and protection of sources and methods is *why*. Third-party verifiers
lack major states' collection capabilities, so the body formally charged with
verifying is rarely the body that can see.

\## Protection

Noninterference-with-NTM and no-deliberate-concealment clauses are standard
arms-control furniture: no blinding satellites, no nets over mobile missiles.
Rose Gottemoeller, the US chief negotiator for New START, called NTM
noninterference "one of the earliest and easiest points of agreement" in those
negotiations.

This is the low-hanging fruit of the whole unit. Note the contrast with
sharing, where drafting is hard — a point worth carrying into the written
output.

\## Architecture: national or international?

*Six Layers* argues — in an emphasis footnote, so hold the modality — for
relying on **national** agencies rather than empowering an international agency
to spy. Three reasons: decades of built-up capability; the IAEA precedent of
learning about violations from national agencies; and the new risks an
espionage-authorized international body would itself create.

The consequence is that weak-intelligence states free-ride on stronger states'
collection. In the US–China case, each side trusts its own agencies to verify
the other.

\## Concrete text

MIRI's draft agreement adopts the arms-control boilerplate wholesale. Item 17
of Article II's definitions list defines national technical means to include
satellite, aerial, cyber, signals, and thermal-imagery remote sensing, and
Article X ¶1(b) carries the noninterference and no-concealment language
borrowed from the ABM Treaty, INF, CTBT, and New START.

It is a real text, and it is meant to be marked up rather than admired. Here
are the two passages, from the paper itself.

**Article II — Definitions, item 17**

#### Article
source:: [[../articles/scher-an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence]]
from:: National Technical Means (NTM) includes satellite
to:: for verification consistent with this Agreement.

#### Text
content::
**Article X — Information Consolidation and Challenge Inspections, ¶1(b)**

#### Article
from:: For the purpose of providing assurance of compliance
to:: as relevant to this Agreement.

#### Text
content::
Read ¶1(b)(iii) against (i) and (ii). Protection is an undertaking; sharing is
an encouragement. That is the asymmetry of this whole section sitting in one
paragraph, and [[../Lenses/XLab Verification - v-intel-action|the last page of this unit]] asks you to draft the obligation it declines to impose.

\## Authenticating what gets shared

Baker's "shared documents might be fake" problem is an evidence-credibility
question, and it belongs here: how do rivals authenticate intelligence passed
between them — signal authentication, chain of custody?

The cryptographic machinery for this — zero-knowledge proofs, multi-party
computation, attestation — is covered in [[../Lenses/XLab Verification - v-mechanism-privacy|unit 4 of Compute Verification 1]]. The bridge worth knowing is the
zero-knowledge warhead-verification precedent (Glaser, Barak and Goldston,
*Nature*, 2014).

\## Readings

- MIRI draft US–China agreement — Article II's definitions and Article X,
  verbatim (pp. 20, 39–40). The passages excerpted above are the ones this
  section turns on; ideally read the whole draft treaty at this point.
Read Baker's section on intelligence sharing, then compare the institutional options in *Six Layers*.

#### Article
source:: [[../articles/baker-nuclear-arms-control-verification-and-lessons-for-ai-treaties]]
from:: #### 2.3.3 Intelligence sharing
to:: The sharing of information between treaty-implementing agencies and national intelligence agencies (or between multiple national intelligence agencies) can help treaty verifiers reach conclusions that would be harder to reach with more limited information. Nuclear arms control treaties have no requirements for national intelligence agencies to share their information; the process is voluntary, informal, and inconsistent.

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: Verifier—bilateral or third-party? Though this report’s focus is not on institution design, it is worth noting that Provers may more easily trust that a third-party Verifier will act in good faith, rather than seeking to steal information or compromise equipment. On the other hand, third-party Verifiers may take longer to set up and may not be as effective. In particular, third parties would lack major states’ intelligence capabilities, though intelligence sharing may help. These tradeoffs might be eased through intermediate options, such as a national verification office that hires citizens of third-party countries to conduct interviews.
to:: Verifier—bilateral or third-party? Though this report’s focus is not on institution design, it is worth noting that Provers may more easily trust that a third-party Verifier will act in good faith, rather than seeking to steal information or compromise equipment. On the other hand, third-party Verifiers may take longer to set up and may not be as effective. In particular, third parties would lack major states’ intelligence capabilities, though intelligence sharing may help. These tradeoffs might be eased through intermediate options, such as a national verification office that hires citizens of third-party countries to conduct interviews.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Baker, Mauricio. "Nuclear Arms Control Verification and Lessons for AI Treaties." *arXiv*, Apr. 2023. [doi.org](https://doi.org/10.48550/arXiv.2304.04123)
*Its section 2.3.3, on intelligence sharing, is excerpted above.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*Cited above as Six Layers. Its passage on bilateral and third-party verifiers is excerpted above.*

Scher, Aaron, David Abecassis, Peter Barnett, et al. "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence." *arXiv*, Nov. 2025. [arxiv.org](https://arxiv.org/abs/2511.10783)
*The MIRI draft agreement. Item 17 of Article II and Article X ¶1(b) are excerpted above.*

XLab. "2.3.4 Intelligence Institutions and Treaty Design." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/intelligence-institutions)
*The source lesson this page adapts.*
:::{>>{"author":"Elias's AI","timestamp":1788521432992}@@XLab's lesson cited a "Definition 17" and separate "noninterference" and "no-deliberate-concealment" articles; none of those labels exists in arXiv:2511.10783v3. Corrected to Article II — Definitions item 17 and Article X ¶1(b)(i) to (iii), whose text this lens now embeds from the imported paper so the 2.3.5 red-line has something to work from.<<}
