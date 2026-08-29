---
id: '26ee0f2c-1c8b-4f3e-8b95-be4d8de6e500'
title: "1.0.2 Policies must be effective and feasible"
tldr: {--{"author":"Elias's AI","timestamp":1788015993778}@@"Faithful alpha import of XLab lesson 1.0.2 Policies must--}{++{"author":"Elias's AI","timestamp":1788015993778}@@"A global ban on fossil fuels would end emissions tomorrow and++} be {--{"author":"Elias's AI","timestamp":1788015993778}@@effective --}{++{"author":"Elias's AI","timestamp":1788015993778}@@dead by Friday; a voluntary pledge would be signed by everyone ++}and {--{"author":"Elias's AI","timestamp":1788015993778}@@feasible."--}{++{"author":"Elias's AI","timestamp":1788015993778}@@change nothing. Every policy sits somewhere on that plane. Price your own favourite policy first, then sort eleven anti-ASI policy buckets, from lab self-governance to a coordinated halt, by how much they deter and how gettable they are."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788015993778}@@"Imported from--}{++{"author":"Elias's AI","timestamp":1788015993778}@@"Three exercises around the effectiveness versus feasibility frame. (1) Everything comes with a cost: the learner names a policy they believe in and one real cost of enforcing it, then rates how hard that was (optional, personal). (2) Scoping an anti-ASI policy: two five-rung scales, eleven policy buckets each with a historical parallel, then the learner places every bucket on the feasibility x effectiveness plane (graded against++} XLab's {--{"author":"Elias's AI","timestamp":1788015993778}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed --}{++{"author":"Elias's AI","timestamp":1788015993778}@@reference cells, one step off counts as close) and answers the securitization question (coordinated halt is the design target). (3) The module's stakeholder map memo for a hypothetical pause treaty (about 800 words, peer reviewed ++}on {--{"author":"Elias's AI","timestamp":1788015993778}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788015993778}@@XLab). Reference placements and rationales are in the closed callouts; share them only after the learner has committed. The corners are settled, the middle band is contestable, so accept argued deviations."++}
tags: [wip]
duration_minutes: 35
---
#### Text
content::
You can think about maximizing the positive impact of a policy by evaluating it along two axes: effectiveness and feasibility. Say your goal was to reduce carbon emissions. An immediate global ban on fossil fuel extraction would eradicate emissions overnight, but is all but completely unenforceable. No economy could withstand the shock; no major emitter would comply. On the other hand, voluntary self-reported emission pledges are easy to agree with—but precisely because they are impossible to enforce. Any country and company could happily sign while continuing to emit. In other words, a policy that is effective but unfeasible is bad; a policy that is feasible but ineffective is also bad.

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016006832}@@ **Interactive exercise:**--}{++{"author":"Elias's AI","timestamp":1788016006832}@@
\## Everything comes with a cost.

A sixty-second exercise: before you scope policy for anyone else, audit one of your own.

#### Question: Open
id:: c7186c93-4751-4729-80c5-b57869936c9a
content:: **Side A · The goal.** A policy you strongly believe in (or borrow one: Universal healthcare, School vouchers, A carbon tax, Banning phones in schools).

**Side B · The price.** One real cost or downside of enforcing it. Be honest, one is enough. Stuck? Try a lens: Who pays? · Who is constrained? · What does enforcing it require? · What happens to those who refuse?

Then write the full policy in one line: "I support ___ at the cost of ___."
optional:: true
assessment-instructions:: Ungraded personal exercise. Check only that Side A names a policy and Side B names a real cost of enforcing that same policy (who pays, who is constrained, what enforcing it requires, or what happens to those who refuse), not a cost of the problem the policy addresses. One sentence of acknowledgement, no praise, no lecture.

#### Question: Choice
id:: 85f95777-151c-4619-8557-3bc3a52cee49
content:: Naming the price — how easy was it?
options::
- Almost instant
- Took some thought
- Genuinely hard
optional:: true
feedback-instructions:: Reply with++} XLab's {--{"author":"Elias's AI","timestamp":1788016006832}@@`policy-cost` widget has--}{++{"author":"Elias's AI","timestamp":1788016006832}@@line for the option chosen, verbatim, and nothing else. Almost instant: "The cost was there all along — it just isn't the half we practice saying out loud." Took some thought: "Conviction keeps the goal in sharp focus and the price in the blur." Genuinely hard: "When a policy feels cost-free, its costs usually land on someone outside our view — or++} no {--{"author":"Elias's AI","timestamp":1788016006832}@@direct Lens equivalent yet. Complete--}{++{"author":"Elias's AI","timestamp":1788016006832}@@one has looked yet."

#### Text
content::
:::callout {title="Both sides of the card (open after you have answered)" tone="neutral" collapse="closed"}
- **Almost instant:** The cost was there all along —++} it {++{"author":"Elias's AI","timestamp":1788016006832}@@just isn’t the half we practice saying out loud.
- **Took some thought:** Conviction keeps the goal ++}in {++{"author":"Elias's AI","timestamp":1788016006832}@@sharp focus and the price in ++}the {--{"author":"Elias's AI","timestamp":1788016006832}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible). Its surrounding lesson text--}{++{"author":"Elias's AI","timestamp":1788016006832}@@blur.
- **Genuinely hard:** When a policy feels cost-free, its costs usually land on someone outside our view — or no one has looked yet.

The question is never just *what do we want to accomplish?* It++} is {--{"author":"Elias's AI","timestamp":1788016006832}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016006832}@@*what are we willing to compromise to get it?*
:::{>>{"author":"Elias's AI","timestamp":1788016006832}@@Native reproduction of XLab's policy-cost flip card (src/lib/verification/data/policy-cost.ts). The widget stores nothing and gates nothing, so both prompts are optional.<<}++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016011592}@@\## The--}{++{"author":"Elias's AI","timestamp":1788016011592}@@:::callout {title="The++} Limited Test Ban Treaty (1963): verifiability decided what could be {--{"author":"Elias's AI","timestamp":1788016011592}@@banned

--}{++{"author":"Elias's AI","timestamp":1788016011592}@@banned" tone="neutral" collapse="closed"}
++}The 1963 treaty banned nuclear tests in the atmosphere, in space, and underwater, but not underground. The reason is pure verification design. Atmospheric tests could be detected worldwide by existing means, monitoring stations picking up radioactive debris and, later, satellites and seismic arrays, without any inspection inside the other country. Underground tests could not be reliably distinguished from earthquakes at the time and would have required on-site inspection the Soviets would not grant. So the treaty covered exactly the environments that national technical means could police and left out the one they could not.{++{"author":"Elias's AI","timestamp":1788016011592}@@
:::++}

In the following exercise, you will develop intuitions with this effectiveness-feasibility tradeoff framework in the context of ASI development. Should governments agree to a more moderate slow-down or a more drastic pause? Should you compromise ambition or real-world enforceability?

Sort the following policy buckets on the feasibility x effectiveness matrix.

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016104215}@@ **Interactive exercise:**--}{++{"author":"Elias's AI","timestamp":1788016104215}@@
\### The axes

Before the buckets: the two words doing the work. Open both scales, then continue.

:::callout {title="What is effectiveness?" tone="neutral" collapse="closed"}
**Effectiveness.** How much the policy actually deters ASI development — measured against the global race, not against one country’s labs. Low to high:

1. **Symbolic.** Signals concern; changes no developer’s plans.
2. **Marginal.** Slows the already-willing; the race continues around it.
3. **Meaningful.** Measurably constrains some frontier development, somewhere.
4. **Strong.** Binds every major developer inside the regime, with real teeth.
5. **Decisive.** Stops or hard-caps the race itself, for as long as it holds.
:::

:::callout {title="What is feasibility?" tone="neutral" collapse="closed"}
**Feasibility.** How gettable the policy is under current infrastructure (the verification burden it implies) and the current political climate. Low to high:

1. **Off the table.** No major power would entertain it in today’s climate.
2. **Long shot.** Imaginable after a crisis or a major shift in threat perception.
3. **Heavy lift.** A real diplomatic and technical build, but precedents exist.
4. **Within reach.** States already do this for other dual-use technologies.
5. **Already happening.** Versions of it exist today.
:::

Two corners of the plane are empty by construction. High effectiveness at high feasibility is the policy everyone would already have adopted; nothing lives there. Costly to get and weak once you have it is the worst of both; if a bucket seems to belong there, one of your axis readings is off.

\### The buckets

Eleven policy buckets, from the least demanding ask to the most. Open each one — the sort unlocks after you have read all eleven.

:::callout {title="1. Self-governance (status quo)" tone="neutral" collapse="closed"}
Voluntary lab commitments such as RSPs and safety frameworks; no external enforcement, and race dynamics persist.

**Historical parallel: Asilomar, 1975.** Molecular biologists voluntarily paused recombinant DNA experiments and wrote their own safety guidelines at the Asilomar conference. Self-governance worked for a while because the research community was small and shared norms, but it later hardened into formal NIH rules. The AI parallel: lab commitments can precede regulation, but they historically survive only until commercial pressure or new entrants arrive.
:::

:::callout {title="2. Unilateral restraint" tone="neutral" collapse="closed"}
One state halts or caps its own frontier development alone, hoping others reciprocate.

**Historical parallel: US bioweapons renunciation, 1969.** President Nixon unilaterally terminated the entire American offensive biological weapons program with no reciprocal commitment from the Soviet Union. The gamble partly paid off, helping produce the Biological Weapons Convention in 1972. The cautionary half: the USSR signed and then secretly expanded its own program (Biopreparat), showing what unilateral restraint risks without verification.
:::

:::callout {title="3. Uncoordinated domestic regulation" tone="neutral" collapse="closed"}
Each state licenses, audits, and sets safety requirements for its own developers, with no international layer.

**Historical parallel: Human germline editing, 2010s.** Countries independently banned, restricted, or left unregulated heritable genome editing, with no international coordination. The He Jiankui affair in 2018 (CRISPR babies, conducted in China partly because oversight gaps existed there) showed the core weakness of a pure patchwork: research migrates to the most permissive jurisdiction.
:::

:::callout {title="4. Transparency and information-sharing" tone="neutral" collapse="closed"}
Incident reporting, model registries, notification of large training runs. The disclosure infrastructure most later options depend on.

**Historical parallel: US-Soviet launch notifications, 1988.** The Ballistic Missile Launch Notification Agreement required each side to notify the other before ICBM and SLBM test launches. Nothing was limited or banned; the value was purely in reducing surprise and misinterpretation. Training-run notification proposals borrow this logic almost exactly. (Nearest fit, though missile launches are far easier to observe from outside than training runs.)
:::

:::callout {title="5. Joint emergency preparedness and response" tone="neutral" collapse="closed"}
Parties jointly detect and respond to computational emergencies such as rogue deployments or loss-of-control incidents. Cross-cutting: compatible with any option below.

**Historical parallel: Post-Chernobyl conventions, 1986.** Within months of the Chernobyl accident, states negotiated the Convention on Early Notification of a Nuclear Accident and the Convention on Assistance in Case of a Nuclear Accident, obligating rapid alerts and mutual aid when a disaster crosses borders. Notable for AI: the machinery was built only after the emergency demonstrated the need.
:::

:::callout {title="6. Knowledge and benefit transfers" tone="neutral" collapse="closed"}
In two strands: sharing research, development knowledge, and safety-enhancing technologies; and sharing chips, compute access, completed models or API access, cash, and AI-enabled aid. Both function as side payments that make restrictive regimes acceptable to states asked to forgo development.

**Historical parallel: Atoms for Peace, 1953.** Eisenhower’s program offered civilian nuclear technology, materials, and training to countries that accepted safeguards, a bargain later written into the NPT as Article IV. Benefit-sharing is what made a discriminatory regime signable for the have-nots. The double edge: some transferred “peaceful” technology later fed weapons programs, including India’s.
:::

:::callout {title="7. Compute controls" tone="neutral" collapse="closed"}
Export controls, international chip tracking, and hardware-enabled governance mechanisms restricting who can access frontier-scale compute. Also the enforcement backbone for options 8 through 11.

**Historical parallel: Fissile material chokepoint.** Nuclear nonproliferation works largely because enriched uranium and plutonium are hard to produce and their supply chains are controllable, policed by the Nuclear Suppliers Group and Cold War-era regimes like CoCom. Advanced chips play the same chokepoint role for AI, with a similar concentration: a handful of firms (TSMC, ASML, NVIDIA) sit where enrichment technology once did.
:::

:::callout {title="8. Binding international regulation of development and deployment" tone="neutral" collapse="closed"}
Treaty rules spanning the stack, from data-center training runs down to fine-tuning, inference, and sensitive AI-enabled devices.

**Historical parallel: Chemical Weapons Convention, 1993.** The CWC regulates an entire dual-use industry rather than banning a single object, with tiered schedules of chemicals, facility declarations, and routine OPCW inspections of commercial plants. It’s the best existing model of intrusive, stack-spanning regulation of a technology that is mostly civilian.
:::

:::callout {title="9. Nonproliferation regime" tone="neutral" collapse="closed"}
A small set of states develops frontier AI under international safeguards and inspections; development prohibited everywhere else.

**Historical parallel: NPT and IAEA, 1968 onward.** The source model itself. Five recognized weapons states, safeguards inspections for everyone else, and Article IV benefits as the sweetener. The regime mostly held (far fewer nuclear states than Kennedy predicted), but India, Pakistan, and Israel stayed outside it, and North Korea left, so “prohibited everywhere else” was never airtight, and the two-tier structure still breeds resentment.
:::

:::callout {title="10. International joint development" tone="neutral" collapse="closed"}
Pooling under a shared institution, covering both joint work toward a shared goal such as defensive AI and confinement of systemically risky development to a single multinational project, prohibited outside it.

**Historical parallel: Baruch Plan, 1946.** The US proposed placing all dangerous atomic activities under an international Atomic Development Authority with a monopoly on the technology. It failed over exactly the issues a “CERN for AI” would face: the Soviet Union would not freeze itself into second place, and neither side would accept intrusive control before trusting the other. CERN itself shows the pooling half works, but only for science with no military edge.
:::

:::callout {title="11. Coordinated halt" tone="neutral" collapse="closed"}
Binding agreement to stop or hard-cap frontier development, bilateral or broadly multilateral, triggered immediately or by pre-committed if/then conditions.

**Historical parallel: Nuclear test moratoria and the CTBT.** The US and USSR halted testing by parallel moratorium in 1958, resumed, then progressively banned it (Partial Test Ban 1963, CTBT 1996), backed by a global seismic monitoring network that makes cheating detectable. The apt part: a verified halt of an activity, not a surrender of weapons. The cautionary part: the CTBT never formally entered into force because key states, including the US and China, never ratified.
:::

\### The sort

Always think about policy in terms of tradeoffs — price them, don’t pick favorites.

#### Question: Open
id:: ec436b24-4b82-4a3f-b079-a37edc4c4aef
content:: Place each of the eleven policy buckets on the plane. For every bucket, give its feasibility rung (Off the table, Long shot, Heavy lift, Within reach, Already happening) and its effectiveness rung (Symbolic, Marginal, Meaningful, Strong, Decisive), one line per bucket.
assessment-instructions:: Grade against XLab's reference cells (feasibility / effectiveness): 1 Self-governance: Already happening / Symbolic. 2 Unilateral restraint: Heavy lift / Marginal. 3 Uncoordinated domestic regulation: Within reach / Marginal. 4 Transparency and information-sharing: Within reach / Marginal. 5 Joint emergency preparedness: Long shot / Symbolic. 6 Knowledge and benefit transfers: Within reach / Symbolic. 7 Compute controls: Within reach / Meaningful. 8 Binding international regulation: Long shot / Strong. 9 Nonproliferation regime: Long shot / Strong. 10 International joint development: Long shot / Decisive. 11 Coordinated halt: Off the table / Decisive. A placement is on the mark when both rungs match, close when each rung is within one step of the reference, off otherwise. Score: on the mark 9 points each, close 5, off 0, scaled to 100. The corners are settled and the middle band is genuinely contestable, so give close placements in the middle band full credit when the learner states a reason.
feedback-instructions:: For each bucket that was off or close, give++} XLab's {--{"author":"Elias's AI","timestamp":1788016104215}@@`policy-scoping` widget --}{++{"author":"Elias's AI","timestamp":1788016104215}@@one-line rationale: 1 "The status quo: already happening, costs nothing, binds no one — and race dynamics run straight over a promise with no enforcement." 2 "One capital can decide it alone, which is why it is not lower — but surrendering the frontier while rivals race is a heavy political lift, and reciprocity you cannot check is a bet Biopreparat shows how to lose." 3 "States license industries all the time — no diplomacy required. But national rules stop at the border, and development migrates to the most permissive jurisdiction." 4 "Watching is an easier ask than stopping, and it restrains nothing by itself. Its real value is the disclosure infrastructure every stronger bucket stands on." 5 "Deterrence is not its job — it detects and responds once something ++}has {++{"author":"Elias's AI","timestamp":1788016104215}@@already gone wrong, alongside any other bucket. And historically the machinery gets built right after the first disaster, not before it." 6 "Alone it deters nothing — transfers are the side payments that make the restrictive buckets signable. The double edge: the goods that persuade are often the goods that proliferate." 7 "Chokepoints this concentrated make supply-side control genuinely enforceable — enough to add years to a cheater's timeline, not to stop the race. Export controls are the part already happening; chip tracking and hardware mechanisms are the build." 8 "The CWC is the existence proof that a mostly-civilian industry can live under routine international inspection — and between today's rivals, an AI version is a genuine long shot, not merely a heavy lift." 9 "Judged against expectations the regime mostly held — at the price of a permanent two-tier grievance, and with an exit door North Korea used. For AI, who qualifies as a licensed developer is the fight before the treaty." 10 "Pooling among rivals is proven; the monopoly-with-prohibition strand died with the Baruch Plan, because ++}no {--{"author":"Elias's AI","timestamp":1788016104215}@@direct Lens equivalent yet. Complete --}{++{"author":"Elias's AI","timestamp":1788016104215}@@leader's rival accepts permanent second place. If confinement held, though, little would escape it." 11 "The strongest instrument on the board and the hardest to get: every major power must stop, and trust that rivals actually stopped. Which is exactly why this track studies verification against it." No praise.

#### Text
content::
:::callout {title="Reference map and reasoning, bucket by bucket (open after you have answered)" tone="neutral" collapse="closed"}
| Bucket | Feasibility | Effectiveness | Why |
| --- | --- | --- | --- |
| 1. Self-governance (status quo) | Already happening | Symbolic | The status quo: already happening, costs nothing, binds no one — and race dynamics run straight over a promise with no enforcement. |
| 2. Unilateral restraint | Heavy lift | Marginal | One capital can decide ++}it {--{"author":"Elias's AI","timestamp":1788016104215}@@in --}{++{"author":"Elias's AI","timestamp":1788016104215}@@alone, which is why it is not lower — but surrendering the frontier while rivals race is a heavy political lift, and reciprocity you cannot check is a bet Biopreparat shows how to lose. |
| 3. Uncoordinated domestic regulation | Within reach | Marginal | States license industries all the time — no diplomacy required. But national rules stop at the border, and development migrates to ++}the {--{"author":"Elias's AI","timestamp":1788016104215}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible).--}{++{"author":"Elias's AI","timestamp":1788016104215}@@most permissive jurisdiction. |
| 4. Transparency and information-sharing | Within reach | Marginal | Watching is an easier ask than stopping, and it restrains nothing by itself.++} Its {--{"author":"Elias's AI","timestamp":1788016104215}@@surrounding lesson text--}{++{"author":"Elias's AI","timestamp":1788016104215}@@real value is the disclosure infrastructure every stronger bucket stands on. |
| 5. Joint emergency preparedness and response | Long shot | Symbolic | Deterrence is not its job — it detects and responds once something has already gone wrong, alongside any other bucket. And historically the machinery gets built right after the first disaster, not before it. |
| 6. Knowledge and benefit transfers | Within reach | Symbolic | Alone it deters nothing — transfers are the side payments that make the restrictive buckets signable. The double edge: the goods that persuade are often the goods that proliferate. |
| 7. Compute controls | Within reach | Meaningful | Chokepoints this concentrated make supply-side control genuinely enforceable — enough to add years to a cheater’s timeline, not to stop the race. Export controls are the part already happening; chip tracking and hardware mechanisms are the build. |
| 8. Binding international regulation of development and deployment | Long shot | Strong | The CWC is the existence proof that a mostly-civilian industry can live under routine international inspection — and between today’s rivals, an AI version is a genuine long shot, not merely a heavy lift. |
| 9. Nonproliferation regime | Long shot | Strong | Judged against expectations the regime mostly held — at the price of a permanent two-tier grievance, and with an exit door North Korea used. For AI, who qualifies as a licensed developer is the fight before the treaty. |
| 10. International joint development | Long shot | Decisive | Pooling among rivals is proven; the monopoly-with-prohibition strand died with the Baruch Plan, because no leader’s rival accepts permanent second place. If confinement held, though, little would escape it. |
| 11. Coordinated halt | Off the table | Decisive | The strongest instrument on the board and the hardest to get: every major power must stop, and trust that rivals actually stopped. Which is exactly why this track studies verification against it. |

Two reference thresholds worth carrying: EU AI Act Art. 51 presumes systemic risk above 10²⁵ training FLOP; the rescinded EO 14110 used 10²⁶ as its reporting trigger. The corners of this plane are settled; the middle band is genuinely contestable.
:::

\### The one exception

Ordinary balancing weighs effectiveness against feasibility. **Securitization** breaks the scale: if ASI development++} is {--{"author":"Elias's AI","timestamp":1788016104215}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016104215}@@an existential threat, nothing can be traded against survival. Accept that framing, and one bucket becomes the **design target for verification mechanisms**. Which?

*Securitization: treating an issue as an existential security matter, lifting it out of normal political balancing — because nothing can be traded against survival. A strong move with a history of abuse, which is why the threat model must be argued, not stipulated.*

#### Question: Choice
id:: 3bfd8e5c-88d3-499f-accc-83458f7ec368
content:: Under the securitized framing, which bucket becomes the design target for verification mechanisms?
options::
- Self-governance (status quo)
- Uncoordinated domestic regulation
- Transparency and information-sharing
- Compute controls
- [x] Coordinated halt
feedback-instructions:: Give XLab's answer for the option chosen. Coordinated halt: "Right — the coordinated halt. Mechanisms strong enough to verify a halt — chip registries, compute metering, inspection rights — can support every weaker bucket. The reverse is not true. So under the securitized framing you design verification for the pause, whatever gets signed first." Compute controls: "Compute controls are the enforcement backbone, not the target — the question securitization asks is what that backbone must be strong enough to hold up. Design it for the halt and it serves every weaker bucket on the way." Transparency: "Transparency is the scaffolding, not the target. Under a securitized framing you build the mechanism set that could support a halt — transparency is what it stands on along the way." Domestic regulation: "Securitization is precisely the move past ordinary domestic politics. A domestic design target leaves the existential problem — the international race — unsolved." Self-governance: "If you truly accept the existential framing, 'trust me' is the one answer ruled out from the start. Verification exists to replace it with 'check me.'" Two or three sentences, no praise.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
**Coordinated halt.** Right — the coordinated halt. Mechanisms strong enough to verify a halt — chip registries, compute metering, inspection rights — can support every weaker bucket. The reverse is not true. So under the securitized framing you design verification for the pause, whatever gets signed first.

**Compute controls.** Compute controls are the enforcement backbone, not the target — the question securitization asks is what that backbone must be strong enough to hold up. Design it for the halt and it serves every weaker bucket on the way.

**Transparency and information-sharing.** Transparency is the scaffolding, not the target. Under a securitized framing you build the mechanism set that could support a halt — transparency is what it stands on along the way.

**Uncoordinated domestic regulation.** Securitization is precisely the move past ordinary domestic politics. A domestic design target leaves the existential problem — the international race — unsolved.

**Self-governance (status quo).** If you truly accept the existential framing, “trust me” is the one answer ruled out from the start. Verification exists to replace it with “check me.”
:::{>>{"author":"Elias's AI","timestamp":1788016104215}@@Native reproduction of XLab's policy-scoping widget (src/lib/verification/data/policy-scoping.ts): the two scales, the eleven bucket cards with historical parallels, the 5x5 sort (as an Open question graded against the reference cells), the reference map, and the securitization exception. XLab's log notes the reference cells and rung scales are builder-authored apparatus awaiting owner review.<<}++}

#### Text
content::
**Design for the hardest case.** Verification strong enough to support a full pause — chip registries, compute metering, inspection rights — supports every weaker bucket for free. The reverse is not true. That is why this track studies verification against the pause, even if what gets signed first is transparency.

#### {--{"author":"Elias's AI","timestamp":1788016112021}@@Text--}{++{"author":"Elias's AI","timestamp":1788016112021}@@Question: Open++}
{++{"author":"Elias's AI","timestamp":1788016112021}@@id:: fbdb0b00-1038-4943-a043-8c2e8d8242be
++}content:: {--{"author":"Elias's AI","timestamp":1788016112021}@@**Import gap:** XLab persistent--}{++{"author":"Elias's AI","timestamp":1788016112021}@@**Stakeholder map** (Map, about 800 words, peer reviewed)

For a hypothetical pause treaty, place every relevant actor on the supply chain, annotate each with its most likely incentive class and the leverage it holds, and mark the two or three actors whose defection would collapse the regime.

Reader: The drafting team for a hypothetical pause treaty.

This output is a map, not a++} memo {--{"author":"Elias's AI","timestamp":1788016112021}@@desk has no clean Lens equivalent. Use --}{++{"author":"Elias's AI","timestamp":1788016112021}@@— build it as annotated rows, not paragraphs, carrying what the brief above asks each row to hold.
assessment-instructions:: This is the module's written output. Score on four things, 25 points each: (1) coverage: the actors span the supply chain from equipment and fabrication through chip design, cloud, labs, and downstream deployers, plus the signatory states and at least one non-signatory host state; (2) each actor carries an incentive class (comply, defect, hide, exaggerate, free-ride) that fits what the actor stands to gain or lose under a pause; (3) each actor carries the leverage it actually holds (a chokepoint, records, a jurisdiction, the power to interrupt a job); (4) two or three actors are singled out as regime-collapsing, with a reason that follows from their position and leverage rather than from their size. Accept any defensible set of collapse actors; penalize rows that name an actor without an incentive or a leverage. Rows, not prose, is the intended form. No generic praise.
feedback-instructions:: Name ++}the {--{"author":"Elias's AI","timestamp":1788016112021}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible) for this element.--}{++{"author":"Elias's AI","timestamp":1788016112021}@@one row whose incentive or leverage is least defended and ask the learner to argue it. Then point to any stage of the supply chain with no actor on the map. Keep it to two short paragraphs.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016112021}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible)*--}{++{"author":"Elias's AI","timestamp":1788016112021}@@:::callout {title="Works cited" tone="neutral" collapse="closed"}
XLab. "1.0.2 Policies must be effective and feasible." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible)
*The source lesson this page adapts, including the cost card, the eleven-bucket sort, and the stakeholder-map brief.*
:::{>>{"author":"Elias's AI","timestamp":1788016112021}@@The memo desk slot for this lesson is m1-stakeholder-map in src/content/verification/memos.ts (status specified, 800 words, peer reviewed, audience "The drafting team for a hypothetical pause treaty"); brief text and the map hint are XLab's. Replaces the import-gap placeholder and the XLab source footer.<<}++}
