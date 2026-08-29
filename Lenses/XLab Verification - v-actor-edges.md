---
id: '5991339a-c9ea-48cd-8b62-ded2834a0792'
title: "1.2.2 Who can prove what"
tldr: "Verification is not something an actor has; it is an arrow between two of them: A can put a fact in front of a verifier about B that B did not volunteer. Draw the arrows on the board you built in 1.2, key them against Baker et al.'s four subgoals, and count. Ten of seventeen actors have no arrow at all, and one chip designer is holding up three of the four subgoals."
summary_for_tutor: "One exercise on the 17-actor board from 1.2. The learner lists directed edges (A to B) and the Baker et al. subgoal each one settles (1.A declared uses are accurate, 1.B declared uses have the required properties, 2.A no undeclared use of a declared cluster, 2.B no undeclared clusters at all), graded against XLab's seven-edge key: Cloud providers to Frontier labs (1.A), NVIDIA to Frontier labs (1.B), NVIDIA to Cloud providers (2.A), TSMC to Proxies (2.B), NVIDIA to Proxies (2.B), Intelligence community to China (2.B), Intelligence community to Proxies (2.B). A reversed edge is reported as reversed, not as a miss. The key, the per-actor notes on why ten actors have no edge, and the closing finding (2.B has four edges, the other subgoals one each, NVIDIA on three of seven, six of seven arrowheads point at a company or a shell) are in closed callouts; reveal them only after the learner commits. Every quoted mechanism is from Baker et al. 2025 (arXiv 2507.15916)."
tags: [wip]
duration_minutes: 20
---
#### Text
content::
[[../Lenses/XLab Verification - v-scoping-actors|1.2]] asked what part each actor plays in a declaration: who owes one, who holds
evidence about one, who checks one, and who no declaration covers. That map is
a description. This is what you do with it.

Verification is not a property an actor has. It is a relation between two of
them: somebody can put a fact in front of a verifier about somebody else, and
that fact settles one of the four things a verifier has to establish. Drawing
those relations is the exercise below, and the key for it is Baker et al.'s —
the same report module 2.1 assigns when it gets to hardware.

Two things worth knowing before you start. Actors with no edge at all are a
real answer and there are more of them than you would guess. And the point of
counting is not the score: it is which of the four subgoals turns out to be
holding the whole regime up.

#### Text
content::
\## Who can prove what

**The brief.** Same agreement, same board: no training runs above a compute threshold for three months. 1.2 asked what part each actor plays in a declaration. This asks what a verifier could actually do with them — who can produce evidence about whom, and which of the four things a verifier has to establish that evidence would settle.

**The board.** The key placement from 1.2, if you have not placed it yourself: *Declares:* United States, China, Cloud providers, Frontier labs. *Holds the evidence:* Taiwan, Netherlands, Japan, South Korea, ASML, TSMC, NVIDIA. *Verifies:* BIS, Intelligence community, California, and the hollow ring for the AI verification body that does not exist. *Outside the declaration:* Proxies, Deployers. Placing it is the workshop in 1.2, and it is worth doing first. Nothing here is gated on it.

**The four things a verifier has to establish** (Baker et al., §3.2):

- **1.A Declared uses are accurate.** “Verify that declared uses of AI compute are declared accurately, i.e., the Prover actually did the claimed development or deployment.”
- **1.B Declared uses have the required properties.** “Assuming that the declared uses are accurate (as is verified per Subgoal 1.A), verify they have the required properties.”
- **2.A No undeclared use of a declared cluster.** “Verify that there are no undeclared, large-scale uses of declared AI compute clusters.”
- **2.B No undeclared clusters at all.** “Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations.”

\### 1. Draw the edges

An edge runs from an evidence source to the actor the evidence concerns. The verification body that does not exist can hold no edge, and that is the row, not a gap in it.

#### Question: Open
id:: 1ebdfc58-235f-4091-89a0-2f807289f888
content:: Draw the edges. For each one, write the source actor, an arrow, the actor the evidence concerns, and the subgoal it completes (1.A, 1.B, 2.A or 2.B). One line per edge. Actors with no edge at all are a real answer, and there are more of them than you would guess.
assessment-instructions:: XLab's key has seven edges: Cloud providers → Frontier labs (1.A); NVIDIA → Frontier labs (1.B); NVIDIA → Cloud providers (2.A); TSMC → Proxies (2.B); NVIDIA → Proxies (2.B); Intelligence community → China (2.B); Intelligence community → Proxies (2.B). Score: each key edge found with the right direction earns 12 points, with the right subgoal 2 more; scale to 100. A reversed edge (right pair, wrong direction) is a reversal, not a miss: report it as reversed and give no credit for it. Extra edges cost nothing but should be named. Edges drawn from ASML, BIS, California, the deployers, or the four host states are the ones the key deliberately leaves out; do not count them, and let the feedback explain why. No generic praise.
feedback-instructions:: List the key edges the learner found, the ones reversed, the ones missed with the mechanism from the key below, and the extras with the note from "Actors with no edge" below. Then say which subgoal on their board has only one mechanism holding it up. Two short paragraphs.

#### Text
content::
:::callout {title="The key: seven edges and the mechanism behind each (open after you have answered)" tone="neutral" collapse="closed"}
**Cloud providers → Frontier labs, Subgoal 1.A.** The declared run happened on somebody else’s machines. The cluster’s own records — logs, billing, and the sensors a verification regime would attach to it — are where a Verifier goes to find out whether the declaration matches what the chips did. Baker §4.2, off-chip verification layers: “the Verifier would aim to detect discrepancies between a Prover’s declarations and their actual chip use, such as by detecting that chips’ input data or power draw patterns tell a different story than the Prover’s claims”.

**NVIDIA → Frontier labs, Subgoal 1.B.** Checking that a declared model has the properties the rules require means running tests on it without the Prover handing over its weights. The feature that makes that possible is built into the chip at design time; Baker names NVIDIA among the designers that have implemented or announced versions of it. Baker §4.1.1.1, Confidential Computing: “This could enable a Verifier to run tests on a Prover’s models, data, and code—with the Prover knowing their information will not be stolen, and with the Verifier knowing their tests will be run faithfully and will not be viewed for the sake of manipulating test results.”

**NVIDIA → Cloud providers, Subgoal 2.A.** Accounting for everything a declared cluster did means the chips keeping their own record. That is a hardware feature, present or absent at manufacture — the cluster’s operator cannot add it afterwards, and cannot quietly remove it either. Baker §4.1, the on-chip verification layer: “Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis.”

**TSMC → Proxies, Subgoal 2.B.** The chain of custody starts where the die is made. How many leading-edge parts exist at all is the ceiling on how large any undeclared cluster could possibly be, and that number exists in one place. Baker §4.2.1, verifying AI chips’ chain of custody: “A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.” And: “This would serve to verify that large quantities of AI chips are not assembled into undeclared AI compute clusters (Subgoal 2.B).”

**NVIDIA → Proxies, Subgoal 2.B.** The same chain one link down: who the parts were sold to, and which serialised chip went where. This is NVIDIA’s second mechanism and a different one from the first — which is exactly why it gets its own edge. Baker §4, defining a verification mechanism: “An example verification mechanism is inspecting AI chips to verify that they have not been sent to undeclared AI data centers; this helps complete Subgoal 2.B.”

**Intelligence community → China, Subgoal 2.B.** The lesson's own row for this agency is monitoring and attribution — the layer that spots hidden data centres and procurement networks. It is what one signatory has instead of a right to inspect the other. Note what it costs: what it knows is classified, so turning it into evidence anybody may act on risks the source that produced it. And note the asymmetry, which is a fact about this roster rather than about the world — China has the same capability and this board has no row for it. Baker §4.3, personnel-based verification layers: “Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.” The layer's own listed disadvantages: “More adversarial, harder for third parties to verify, and unclear effectiveness.”

**Intelligence community → Proxies, Subgoal 2.B.** A cluster nobody declared leaves no paperwork to audit. What is left is people and signals — and this is the only actor on the board that can reach a facility that was never on any list. Read the quote carefully: the paper gives intelligence EVERY subgoal, not this one. It is filed here because 2.B is the only place on this board where it is the sole mechanism, and an edge you drew from it to a lab or a cloud has the paper behind it. Baker §4.3: “Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.”
:::

:::callout {title="Actors with no edge, and why (open after you have answered)" tone="neutral" collapse="closed"}
**United States.** A signatory declares; it does not produce evidence itself. What a state has for that is institutions, which is why the intelligence edge starts at the agency rather than at the country. Then notice the shape that leaves: China is at the receiving end of an edge and the United States is at the receiving end of none. Do not read that as a claim that one government is the more transparent. It is a claim about which government's institutions this roster wrote down — and about the empty ring where the body that would check both of them should be. Baker §3.1: “The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement.”

**Taiwan, Netherlands, Japan, South Korea.** The four host states hold the jurisdiction that makes their firms' records producible, and not one of them is a party to this agreement. That is not an oversight in the drawing; it is the open problem the paper lists under attaining participation, and it is the reason a two-party compute agreement leans on export controls and energy policy rather than on the agreement itself. An edge you drew from one of them is an edge nothing compels. Baker §3.3, broader challenges: “How to attain compliance commitments from all states that host large-scale AI compute (as such states could directly misuse it or rent it to an agreement party)?”

**No AI verification body.** This one can hold no edge, and that is the row, not a gap in it. The paper allows a government body or a third party as Verifier; every government body here belongs to one signatory, and the third party does not exist — no chip registry, no challenge-inspection right, no procedure for resolving an allegation of training above a threshold. Read the board once more with that in mind: a two-party agreement in which only one party's institutions can check anything, and no neutral party at all. Baker §3.1: “The Verifier could be a government body or a third party.”

**ASML.** Baker’s chain of custody begins at manufacturing, and ASML is upstream of that: it sells the machines the fab uses, not the parts a regime counts. The tightest chokepoint on the map completes no subgoal, which is what the difference between leverage and evidence looks like. Baker §4.2.1: “A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.” The chain starts at manufacturing, not at the tools.

**BIS.** Export control is the instrument, and the paper puts it outside the frame deliberately: it is how a party is stopped or punished after a finding, not how a declaration is checked. Today’s de facto compute-governance agency is, in this framework, downstream of verification rather than part of it. Baker §2.3, scope limitations: “We do not cover this latter step of enforcement, though a few verification mechanisms double as enforcement tools.”

**California.** A reporting statute produces declarations. Verification is what happens to a declaration afterwards, and receiving one is not checking it. The actor that bound the leading labs before any international mechanism existed completes no subgoal — it supplies the thing the subgoals are about. Argue with this one if you drew the edge: SB 53 also requires an internal anonymous reporting channel at large frontier developers, and whistleblowing is a verification mechanism in this framework, for every subgoal at once. The key leaves the edge out because the mechanism is a programme a Verifier runs and California is not running one — which is a judgement, not a reading. Baker §3.1: “Verification focuses on checking that these declarations are correct and complete.” Baker §4.3, the personnel-based layers: “Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.”

**Deployers.** Below the threshold, and that is the whole of it. Millions of actors running somebody else’s model are outside the regime by construction rather than by evasion — which is why they share a ring with the proxies and share nothing else. Baker §2.2, what counts as large-scale: “AI development or deployment is ‘large-scale’ if it uses thousands of high-end AI chips over multiple months.”
:::

\### 2. Read the map

:::callout {title="Where this regime is weakest (open after you have answered)" tone="neutral" collapse="closed"}
Count the edges by subgoal. 2.B — no undeclared clusters anywhere — has four. The other three subgoals have one edge each, so three quarters of what a verifier has to establish rests on a single mechanism apiece. Baker’s standard for a robust regime is redundancy: layers stacked, so that a subgoal has more than one way of being completed. Three of the four subgoals on this board have no second way at all.

Now count by actor instead, which is the sharper reading. One firm is on three of the seven edges and touches three of the four subgoals — and that is not a coincidence about NVIDIA, it is what a verification layer IS. The paper defines a layer as one mechanism per subgoal, and the on-chip layer is a chip designer’s to give or withhold. So the board does not show one weak link; it shows a regime resting on roughly one layer, held by a company that is not a party to the agreement.

The paper calls the least robust subgoal the weak link and says the regime is only as good as that one. This map narrows the question rather than answering it — counting edges is not measuring robustness — but it does tell you where to ask.

Now count arrowheads. Six of the seven edges point at a company or at a shell. Exactly one points at a party to the agreement, and it runs one way, out of one signatory’s intelligence service. Nothing on this board produces evidence about the United States, and the reason is not that the United States is transparent — it is that the counterparty’s institutions are not on the roster and the neutral body that would be is the hollow ring on the third band. This is a map of a two-party agreement in which one party’s bureaus do all the checking, including of themselves.

Then read the third ring on its own, since that is where the last paragraph comes from. The export-control bureau, the intelligence community, the state legislature: one country’s, all three. 1.2 already told you the shelf marked “AI verification body” is empty; here it is, drawn empty, on the ring where the alternative would have gone.

Then read what has no edge at all — ten of the seventeen. Some of those absences are the paper’s scope (enforcement is not verification), some are the roster’s (China brought no bureaus), and one is the whole problem stated as a hole: four states hold the jurisdiction that makes the chain’s records producible, and not one of them signed anything.

Then read what has no node. The paper’s simplest and most implementation-ready layer runs on people — whistleblowers, interviews, intelligence. One of those three is on this board, because it happens to be an institution. The other two are not organisations, so a map of organisations has nowhere to put them, and you would never find them by drawing one.

Baker §3.2, the weak link: “identify the subgoal whose mechanisms are collectively least robust. This subgoal is the ‘weak link’ of the regime—its robustness determines the regime’s overall robustness.” Baker §4, defining a verification layer: “three verification layers can be stacked together to achieve three layers of redundancy, for example.”
:::{>>{"author":"Elias's AI","timestamp":1788016696939}@@Native reproduction of XLab's actor-edges widget (src/lib/verification/data/actor-workshop.ts: SUBGOALS, EDGE_KEY, EDGE_NOTES, EDGE_FINDING; brief from widgets/actor-edges.tsx). The drag-to-draw ring map is replaced by a typed edge list graded against the same key. "Module 2.1" in the intro refers to the hardware module lens set, outside this module; left unlinked.<<}

#### Text
content::
\### Notes and sources

The framework, the four subgoals and every mechanism quoted in the key:
M. Baker, G. Kulp, O. Marks, M. Brundage & L. Heim,
[“Verifying International Agreements on AI: Six Layers of Verification for
Rules on Large-Scale AI Development and Deployment”](https://arxiv.org/abs/2507.15916)
(2025). Quotations are matched against the committed copy of the paper at test
time, so a quote that drifts fails the build rather than sitting on the page.
Module 2.1 assigns the same report for its layers; this section uses its
subgoals.

The cast, the rings and the sentences that place each actor on one are 1.2's,
and the workshop above opens on the board you built there.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*A six-layer verification framework whose personnel-based layers map which workers can observe different violations and why disclosures still need independent confirmation. Every mechanism quoted in the key is from it.*

XLab. "1.2.2 Who can prove what." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/actor-edges)
*The source lesson this page adapts, including the edge exercise and its key.*
:::
