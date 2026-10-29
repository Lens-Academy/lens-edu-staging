---
id: '76451830-cdb6-4160-9eae-ee72d0917f5b'
title: "Actors: who does the treaty rely upon, apply to, and constrain?"
tldr: "Two governments sign a three-month pause on big training runs. On Wednesday morning, who actually has to change what they do? Not the signatories: the labs, fabs, clouds and one Dutch lithography firm. Learn three lenses for any actor (where it sits, what it can do for or to a verifier, what it wants right now), then build the actor map yourself: who declares, who holds evidence, who verifies, and who no declaration ever covers."
summary_for_tutor: "Reading plus a workshop. The reading gives five tables: the incentive vocabulary (comply, defect, hide, exaggerate, free-ride), six states by supply-chain position, US institutions inside one signatory, private actors upstream to downstream, and six functional roles; then the three questions to ask of any actor (position, roles, posture). The Actor Map Workshop follows: study the 17-actor roster, then from memory list everything a cloud provider can do inside a regime; a graded choice on what sits at the centre of the map (the regulated training run); place all 17 actors on Baker et al.'s four rings (Declares, Holds the evidence, Verifies, Outside the declaration), graded against XLab's key; then read the finished map. The ring key and rationales sit in closed callouts; do not reveal them before the learner commits. The edge exercise built on this board, the second-order question (whose removal stops a run soonest) and the three optional written answers are in 1.2.2, the lens after the supply-chain map. Two pictures, drawn in the same layout as the 1.2.2 board: an empty ring map (centre and four numbered rings) opens step 4, and the finished map opens the closed placement-key callout, with six small squares under each actor marking its roles (capability holder, chokepoint controller, information holder, enforcement authority, evasion pathway, victim or free-rider). The finished map shows the answers, so it stays inside that callout."
tags: [wip]
reading_minutes: 35
tutor_minutes: 18
---
#### Text
content::
We’ve established why an international pause is important, the key components of a relevant treaty, and why robust verification mechanisms are crucial to its successful enforcement. Now, the question becomes: who are the key players that a pause treaty would require cooperation from? Which nations, labs, and manufacturers have a stake in the development or prevention of ASI?

This section gives you three ways to analyze the actors in a verification regime: where they sit in the supply chain, what function they can perform, and what posture they may take under a particular rule.

Suppose the United States and China sign an agreement tomorrow: no training runs above some compute threshold for three months. Now ask a simple question. Who, exactly, has to change their behavior on Wednesday morning?

Not the people who signed. Governments do not train frontier models. They do not own the data centers, fabricate the chips, or operate the clouds. The activity the agreement is about happens inside companies: labs in San Francisco and Hangzhou, fabs in Taiwan, a lithography firm in a small Dutch town, cloud regions scattered across the planet.

So we need a map of who is actually in the game. In this map, we will describe where each actor sits, what they hold, and what they want, aiming to get to what they are willing to do to get it.

Below, we have some basic incentive vocabulary for your reference.

Table 1.  The incentive vocabulary

| Posture | What it means | A concrete face |
| --- | --- | --- |
| Comply | Follow the agreement as written. | A lab that reports its large training runs accurately and on time. |
| Defect | Covertly violate for advantage. | A state running a hidden cluster while its diplomats reaffirm the pause. |
| Hide | Obscure assets or activities from view, whether or not a rule is being broken. | A firm treating its chip inventory as a trade secret. |
| Exaggerate | Overstate compliance, safety, or capability. | Safety-washing by a lab; capability bluffing by a state. |
| Free-ride | Enjoy the stability produced by others’ restraint without bearing its costs. | A state that signs nothing and benefits anyway. |

Keep in mind that these are postures, not fixed personality types. The same actor can comply on one obligation, hide on another, and free-ride on a third, all in the same quarter. The interesting question is never “is this actor good.” It is “what does this actor do under this rule, at this moment, given what it costs.” That cost framework will be recurring throughout the course and policy frameworks, so it’s important to internalize an understanding and instinct for it.

Let’s start with nation-states, since they are the ones that sign. A state matters to verification roughly in proportion to what passes through its territory and its law. Six states cover most of the compute supply chain that [[../Lenses/XLab Verification - v-interactive-map|1.2.1]] maps.

Table 2.  States, by position on the compute supply chain

| State | What runs through it | What that buys a verifier | Standing worry |
| --- | --- | --- | --- |
| United States | Chip design (NVIDIA, AMD), the largest frontier labs and cloud providers, and export-control law. | It can see and squeeze more of the chain than anyone. Its export rules are the closest thing to a working compute-control regime today. | Losing its lead; verification machinery being turned on its own firms. |
| China | The other frontier developer. Manufacturing scale, rare earths and materials, its own designers, clouds, and labs. | No agreement is meaningful without it, and it controls inputs the rest of the chain needs. | Reads on-chip controls and inspections as surveillance and containment. |
| Taiwan | TSMC, which fabricates the overwhelming share of leading-edge AI chips. | The single tightest physical chokepoint in the system. | Being both the prize and the battlefield in a conflict it does not control. |
| Netherlands | ASML, the world’s only maker of EUV lithography machines. | One company in one country: one of the strongest levers anywhere in the system. | Being pulled into a rivalry it did not choose, with its one champion, ASML, as the lever. |
| Japan | Semiconductor equipment (Tokyo Electron) and specialty materials. | Several quieter chokepoints in equipment and chemistry. | Pressure from both sides of the US-China rivalry. |
| South Korea | Samsung and SK Hynix, the largest memory makers, including high-bandwidth memory (HBM). | HBM is scarce and essential to frontier training: a countable, checkable input. | Export exposure to China against alliance pressure from the US. |

It’s also important to name the European Union. Even though as a whole, the EU isn’t a hub for silicon, it matters as a rule-writer. The EU AI Act carries the 10^25 FLOP presumption of systemic risk, the most cited compute threshold in force anywhere, and rules written in Brussels have a habit of being copied elsewhere.

Now, the next level.

\## Below the state{>>{"author":"Elias's AI","timestamp":1788016435534}@@"Institutions below, inside, and above the state" was XLab's PageBreak title, imported as a duplicate heading; kept only the real heading.<<}

Subnational governments regulate too, and this is often easier and/or happens earlier than federal regulation. California is this course’s running example because most frontier labs are physically headquartered there, and jurisdiction follows geography.

In September 2025 California enacted SB 53, the Transparency in Frontier Artificial Intelligence Act, with its main duties taking effect in January 2026. Two thresholds decide who it reaches. A **frontier model** is one trained on more than 10^26 operations, and anyone who trains one is a **frontier developer**; a **large frontier developer** is a frontier developer whose annual gross revenues, with affiliates, exceed $500 million. (Nobody publishes a list of who that is. Coverage turns on the compute number, and the compute number is one only the developer measures: as of early 2026 the [SB 53 reference](https://sb53.info/faq) records that just two developers are publicly known to have trained above the threshold, OpenAI and xAI, while METR’s [guide for lab staff](https://metr.org/notes/2026-01-29-frontier-ai-safety-regulations/) names OpenAI, Google, Anthropic and xAI as examples of who these laws govern rather than as a roster. Hold on to that: it is a rule whose scope is set by a quantity the regulated party alone can count.)

Every frontier developer must publish a transparency report when it deploys a new frontier model, report critical safety incidents to the state’s Office of Emergency Services within fifteen days (twenty-four hours if there is imminent risk of death or serious physical injury), and tell its employees they have whistleblower rights. Large frontier developers carry more on top: a published framework describing how they identify and mitigate catastrophic risks, fuller transparency reports, and an internal channel for anonymous reports.

Notice what happened there. A state legislature bound the world’s leading labs to reporting duties before any international mechanism existed. When you design a regime in the capstone course, remember that some of its machinery may already exist two levels below the treaty. Often, it might be easier to pass state level legislation before federal legislation follows.

\### Inside the state

“The United States wants X” obfuscates that a state is a bundle of institutions with different jobs and different incentives, and these groups have core differences on AI verification.

Table 3.  Inside one signatory: the United States

| Institution | Job in a verification regime | Incentive to watch |
| --- | --- | --- |
| State Department | Negotiates the agreement and runs the diplomacy around compliance disputes. | Wants a deal that survives politics; may trade verification strictness for signatures. |
| Commerce Department (Bureau of Industry and Security, BIS) | Writes and enforces export controls on chips: the de facto compute-governance agency today. | Enforcement capacity is small relative to the job, and the rules shift with each administration. |
| Department of War | Strategic and military stakes in frontier AI. | Wants American capability unconstrained; wary of any regime that could bind its own programs. |
| Intelligence community (CIA, NSA, and the rest) | Monitoring and attribution: the “national technical means” layer that spots hidden data centers and procurement networks. | What it knows is classified. Turning intelligence into shareable treaty evidence risks burning sources. |
| NIST and its Center for AI Standards and Innovation (CAISI) | Standards and testing. Runs pre-deployment evaluation agreements with several frontier developers. | Voluntary agreements, not inspection authority; renamed and refocused as the politics changed. |

Same government, five postures. When a proposal says “the US will verify,” your first question should be: which building?

\### Above the state

Is there a WHO for AI? An IAEA? As of mid-2026, there are some authorities but they don’t have a lot of real power or mechanisms to detect cheating. The UN has stood up the Independent International Scientific Panel on AI, forty scientists modeled on the IPCC and co-chaired by Yoshua Bengio and Maria Ressa, whose reports feed a new Global Dialogue on AI Governance that met for the first time in Geneva in July 2026. While this helps build a shared scientific picture of risk, it does not fix the verification function. No agency holds a chip registry. No inspector has challenge-inspection rights at a data center. No treaty gives anyone the authority over compute that the IAEA has held over fissile material since the 1970s. The institutional shelf marked “AI verification body” is empty. Some of the people reading this will help build what goes on it.

\## Private actors: reading the chain from top to bottom

Now the companies. The useful way to hold them in your head is not alphabetical but positional: upstream to downstream, the same axis as the map in [[../Lenses/XLab Verification - v-interactive-map|1.2.1]]. Read the table from top to bottom and watch two numbers change as you go: how many actors exist at each stage, and how much each one can see.

Table 4.  Private actors, upstream to downstream

| Stage | Who (examples) | What they hold that a verifier needs | Default posture |
| --- | --- | --- | --- |
| Equipment | ASML (EUV lithography); Applied Materials, Tokyo Electron. | The machines without which no leading-edge chip exists, and knowledge of every fab that buys one. | Comply. Few customers, total visibility, nowhere to hide. |
| Fabrication and memory | TSMC, Samsung, SK Hynix, Intel. | The physical record: what was made, how many, and for whom. | Comply, while caught between US rules and Chinese customers. |
| Chip design | NVIDIA, AMD; Huawei and other Chinese designers. | The blueprint: whether chips ship with attestation, metering, or location features at all. | Comply with controls while lobbying hard against them. Verification features cost money and sales. |
| Packaging, assembly, test | Advanced-packaging lines (TSMC’s CoWoS and rivals); outsourced assembly-and-test firms. | Advanced packaging is a second, quieter bottleneck: chips pass through it and can be counted. Ordinary assembly and test is not: it is labor-intensive and has the lowest barriers to entry of any stage. | Mostly invisible in policy debates, which is itself a gap. |
| Cloud providers | AWS, Microsoft Azure, Google Cloud, Oracle, Alibaba; specialists like CoreWeave. | The position between customer and machine: logs, billing, telemetry, and the power to interrupt a job. | Comply and hide at once. Natural monitors, reluctant police. |
| Frontier labs | OpenAI, Anthropic, Google DeepMind, Meta, xAI; DeepSeek, Alibaba, and Moonshot in China. | The most detailed private information in the system: what was trained, on what data, and what the evals showed. | Every posture, potentially. |
| Deployers | Everyone building products on top of models. | A diffuse downstream signal of what models can actually do. | Free-ride. They benefit from safety and bear none of its costs. |
| Proxies and contractors | Shell companies, resellers, straw buyers, intermediaries. | Nothing legitimate. They exist to break the link between a name and an activity. | The standing channel through which evasion flows. |

Take two things from this table.

First, counts:

- One EUV maker.
- A handful of leading-edge fabs.
- A few consequential chip designers.
- Five or six hyperscale clouds.
- A few dozen labs that matter.
- Millions of deployers.

The chain narrows to almost nothing at the top and fans out to everything at the bottom. Verification has something to grab exactly where the count is small, which is why so many of the mechanisms you will meet from Week 5 onwards, and in Part 2, bite upstream. Hold that thought; section [[../Lenses/XLab Verification - v-scoping-upstream-downstream|1.3]] develops it properly.

Second, look at the labs’ row: A frontier lab can comply, publishing a safety framework and reporting under SB 53. It can hide, treating training details as trade secrets. It can exaggerate, describing its own precautions in the most flattering light, which is what critics call safety-washing. And it can free-ride on rivals’ restraint. Your job in verification is to price these different behaviors and balance their relevant incentives.

\## Functional roles: the second lens

Public versus private tells you what an actor is, but not what an actor does for you, or to you, when you are trying to verify an agreement. Here, it can be helpful to ask what function the actor performs.

Table 5.  Six functional roles

| Role | The question it answers | Examples |
| --- | --- | --- |
| Capability holder | Who can actually build the dangerous thing? | Frontier labs; any state with a national program. |
| Chokepoint controller | Who can physically stop or slow the flow? | ASML, TSMC, cloud providers; BIS with its export licenses. |
| Information holder | Who already knows what verifiers need to learn? | Clouds (logs and billing), labs (evals), fabs (shipments), intelligence agencies. |
| Enforcement authority | Who can impose a real cost for violating? | Regulators, customs services, courts, sanctioning states, a future treaty body. |
| Evasion pathway | Through whom would a cheater route? | Proxies, resellers, smuggling networks, non-signatory jurisdictions, complicit contractors. |
| Victim, free-rider, beneficiary | Who bears the risk, or enjoys the stability, without a seat at the table? | Everyone downstream of the frontier; small states; the public. |

The crucial property of this second lens is that it cuts across the first. Any actor can hold several roles at once, and almost every important actor does.

Try it on a cloud provider.

- Chokepoint controller: it can suspend a customer’s access this afternoon.
- Information holder: its logs and billing records are the richest picture anywhere of who is computing what.
- Enforcement authority: give it know-your-customer duties and it becomes the regime’s front-line cop.
- Evasion pathway: its reseller chains and mislabeled workloads are precisely how a determined actor reaches compute it should not have.

Which role dominates depends entirely on what the regime asks of it and what compliance costs.

Or try Taiwan. A chokepoint controller of the first rank, and simultaneously the actor with the most to lose if the chokepoint ever becomes a target. An actor’s roles can pull against each other, and when they do, its incentives tell you which one wins.

\## How to use this section

You now have three questions to ask of any actor you meet in a proposal, a news story, or an exercise, for the rest of this course. Where does it sit on the chain? That is position: Table 4. What can it do inside a regime? That is roles: Table 5. What does it want right now? That is posture: Table 1. Ask them in that order and most verification claims come apart usefully in your hands. “The cloud providers will report suspicious training runs” stops being a reassuring sentence and becomes three checkable ones: they sit mid-chain where visibility is high; they hold the logs; and they will report exactly to the degree that reporting costs less than not reporting.

\## The Actor Map Workshop

**The brief.** Suppose the United States and China sign an agreement tomorrow: no training runs above some compute threshold for three months. The section asked who has to change their behavior on Wednesday morning. The map asks the question after it: when the three months are up, who could show that they did, and who could show that somebody did not?

**Four rings: what part of a declaration you play.** A verification regime runs on declarations: somebody states what they own and what they did with it, somebody else establishes the statement is true and complete. Every actor is somewhere in that.

\### 1. Study

Study the roster, then close it. Everything after it is answered from memory.

:::callout {title="The roster: seventeen actors" tone="neutral" collapse="closed"}
**States and rule-writers**

- **United States.** Jurisdiction over chip design, the largest frontier labs and cloud providers, and export-control law. Roles: capability holder, chokepoint controller, information holder, enforcement authority. Postures: comply, hide. Its export rules are the closest thing to a working compute-control regime today; its intelligence collection is difficult to share.
- **China.** The other frontier developer: manufacturing scale, materials, designers, clouds and labs. Roles: capability holder, chokepoint controller, information holder, enforcement authority. Postures: comply, hide. Reads on-chip controls and inspection rights as surveillance and containment.
- **Taiwan.** Fabrication and advanced packaging. Roles: chokepoint controller, information holder, victim. Posture: comply. Caught between US rules and Chinese customers.
- **Netherlands.** Equipment: ASML. Roles: chokepoint controller, information holder. Posture: comply. A small state carrying outsized weight in a rivalry it did not choose.
- **Japan.** Equipment and specialty materials. Role: chokepoint controller. Posture: comply. Under pressure from both sides of the US-China rivalry.
- **South Korea.** Memory, including high-bandwidth memory. Roles: chokepoint controller, information holder. Posture: comply. Export exposure to China against alliance pressure from the United States.
- **California.** Subnational jurisdiction over most frontier labs by headquarters geography. Roles: enforcement authority, information holder. Posture: comply.

**Inside the United States**

- **Commerce · BIS.** Roles: enforcement authority, information holder. Posture: comply. Writes and enforces export controls on chips.
- **Intelligence community.** Role: information holder. Posture: hide. Collects evidence of undeclared facilities, but sharing it can expose sources and methods.

**International bodies**

- **The verification body that does not exist.** Above the state. No roles, no postures. No international body holds a chip registry, inspection right, or procedure for resolving an allegation of training above a threshold.

**Private actors**

- **ASML.** Equipment, most upstream. Roles: chokepoint controller, information holder. Posture: comply. Few customers, high visibility, and systems that need continuing vendor service.
- **TSMC.** Fabrication and advanced packaging. Roles: chokepoint controller, information holder, evasion pathway. Postures: comply, hide.
- **NVIDIA.** Accelerator design. Roles: chokepoint controller, information holder, evasion pathway, victim. Postures: comply, hide, exaggerate, free-ride. It can decide whether accelerators ship with attestation, metering, or location features.
- **AWS, Azure, Google Cloud, Oracle, Alibaba** (cloud providers). Cloud and data-center operation. Roles: chokepoint controller, information holder, enforcement authority, evasion pathway. Postures: comply, hide. They can suspend access and hold rich logs; reseller chains and mislabeled workloads also create evasion routes.
- **Frontier labs.** Model training. Roles: capability holder, information holder, victim. Postures: comply, hide, exaggerate, free-ride. They hold the most detailed private information in the system: what was trained, on what data, and what evaluations showed.
- **Front companies, resellers, straw buyers** (proxies). Distribution, across every stage. Role: evasion pathway. Posture: defect. They exist to break the link between a name and an activity.
- **Product builders and deployers.** Deployment, most downstream. Role: victim. Posture: free-ride. A diffuse downstream signal of what models can do.
:::

\### 2. Recall

#### Question: Open
id:: 3df5fa92-d84b-4198-af75-e744dc299b53
content:: Take one actor: a cloud provider. From memory, write down everything it can do inside a verification regime, and what it wants while doing it.
force-feedback:: first
feedback-instructions:: One-turn mirror: name which of the six the learner got, list the ones missed with their one-line gloss, and close by telling them to move on. No re-teaching, no follow-up question. The six, with their glosses. What it can do: it controls a chokepoint (it can suspend or cut off a customer's access to compute at short notice); it holds information (its logs, billing and telemetry are the richest record of who is computing what); it can act as an enforcer (given know-your-customer duties, it becomes the regime's front-line police); it is an evasion pathway (its reseller chains and mislabeled workloads are how a determined actor reaches compute it should not have). What it wants: to comply, acting as a natural monitor; and to hide, keeping what it sees and does out of view as a reluctant police force. Reference answer, not a checklist: "Chokepoint controller: it can suspend a customer's access this afternoon. Information holder: its logs and billing records are the richest picture anywhere of who is computing what. Enforcement authority: give it know-your-customer duties and it becomes the regime's front-line cop. Evasion pathway: its reseller chains and mislabeled workloads are precisely how a determined actor reaches compute it should not have. Comply and hide at once. Natural monitors, reluctant police."

#### Text
content::
:::callout {title="What a cloud provider can do, and wants (open after you have answered)" tone="neutral" collapse="closed"}
- **Chokepoint controller.** It can suspend a customer’s access this afternoon.
- **Information holder.** Its logs and billing records are the richest picture anywhere of who is computing what.
- **Enforcement authority.** Give it know-your-customer duties and it becomes the regime’s front-line cop.
- **Evasion pathway.** Its reseller chains and mislabeled workloads are precisely how a determined actor reaches compute it should not have.
- **Comply.** Table 4’s cloud row: “Comply and hide at once. Natural monitors, reluctant police.”
- **Hide.** The same row: a natural monitor that is a reluctant police force since its targets are also its clients.
:::

\### 3. The centre

#### Question: Choice
id:: d119e50f-5b65-4d75-836e-e844943abfe7
content:: A pause agreement forbids training runs above a compute threshold. When you draw this map, what goes in the centre?
options::
- [x] The regulated activity itself: a training run above the threshold.
- The states that signed the agreement.
- The frontier labs the obligations land on.
- The chips themselves, the hardware the run is counted on.
force-feedback:: first
feedback-instructions:: Give the source lesson's reasoning for the option chosen, from the "Why" callout below. The activity: "The map is of a rule, and a rule is about an act. It is also what the verification literature centres: Baker's framework takes the approach of compute accounting, which is the same act said in compute. Put it in the centre and every ring becomes an answer to one question: what part do you play in accounting for this run?" The signatories: "'Not the people who signed. Governments do not train frontier models.' Centre them and the map says the treaty regulates its own signatories rather than an activity. Then watch for what looks like a contradiction two steps from now: the signatories do end up on the innermost RING, because in an international agreement the party that owes the declaration is the government. Owing a declaration and performing the act are different things, and the centre is the act." The labs: "Close, and it is why they sit on the first ring. But the labs are who does the act, not the act, and a map centred on them has nowhere to put a run that happens somewhere else, under someone else's name." The chips: "The chips are what makes the act countable from outside, which is a property of the mechanism rather than of the rule. Centre the map here and every institution on it becomes an afterthought." Two or three sentences, no praise.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
**The regulated activity itself.** The map is of a rule, and a rule is about an act. It is also what the verification literature centres: Baker's framework takes the approach of compute accounting, which is the same act said in compute. Put it in the centre and every ring becomes an answer to one question: what part do you play in accounting for this run? Baker et al., §3.1, AI compute accounting: “it seeks to verify compliance on the basis that all large-scale AI compute use is accounted for in compliant activities.”

**The states that signed the agreement.** “Not the people who signed. Governments do not train frontier models.” Centre them and the map says the treaty regulates its own signatories rather than an activity. Then watch for what looks like a contradiction two steps from now: the signatories do end up on the innermost RING, because in an international agreement the party that owes the declaration is the government. Owing a declaration and performing the act are different things, and the centre is the act.

**The frontier labs the obligations land on.** Close, and it is why they sit on the first ring. But the labs are who does the act, not the act, and a map centred on them has nowhere to put a run that happens somewhere else, under someone else’s name.

**The chips themselves, the hardware the run is counted on.** The chips are what makes the act countable from outside, which is a property of the mechanism rather than of the rule. Centre the map here and every institution on it becomes an afterthought.
:::

\### 4. Place

<svg viewBox="180 40 600 600" width="100%" style="max-width:600px;height:auto" role="img" aria-label="The empty actor map: a training run above the threshold at the centre, with four rings around it. From the inside out: 1, Declares; 2, Holds the evidence; 3, Verifies; 4, Outside the declaration." font-family="DM Sans, Arial, sans-serif">
<g fill="none" stroke="currentColor" stroke-opacity="0.22" stroke-width="1.25"><circle cx="480" cy="350" r="84"/><circle cx="480" cy="350" r="150"/><circle cx="480" cy="350" r="216"/><circle cx="480" cy="350" r="278"/></g>
<g fill="currentColor" fill-opacity="0.65" font-size="13" letter-spacing="0.06em" text-anchor="middle"><text x="480" y="256">1. DECLARES</text><text x="480" y="190">2. HOLDS THE EVIDENCE</text><text x="480" y="124">3. VERIFIES</text><text x="480" y="62">4. OUTSIDE THE DECLARATION</text></g>
<circle cx="480" cy="350" r="5" fill="#b87018"/>
<g fill="currentColor" text-anchor="middle"><text x="480" y="372" font-size="15" font-weight="600">A training run</text><text x="480" y="390" font-size="13" fill-opacity="0.65">above the threshold</text></g>
</svg>

{--{"author":"Andreas's AI","timestamp":1793242816836}@@{>>{"author":"Andreas's AI","timestamp":1793164089695}@@Stage 6 flag, Lens text: "the report 1.2.2 keys its edges against" uses "keys" in a sense the learner has not met, about a page they have not seen yet. The section number is left for stage 7. See the CV1 plain language worklist.<<}At--}{++{"author":"Andreas's AI","timestamp":1793242816836}@@At++} the centre: **a training run above the threshold.** Around it, four rings. Each ring's test is quoted from Baker et al., Verifying International Agreements on AI (2025), the report [[../Lenses/XLab Verification - v-actor-edges|1.2.2]] keys its edges against.

1. **Declares.** You own or use large-scale compute, or you signed the agreement and answer for what happens inside your territory. Either way the regime wants a declaration from you: you are the Prover. Baker §3.1: “The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement.” And §3.2: “organizations that own or use large-scale AI compute (e.g., major AI companies and cloud compute providers) would be required to declare facts about” their compute.
2. **Holds the evidence.** You declare nothing here and you check nothing, but you hold a record a declaration can be held against, or the authority that makes somebody else’s record producible. Baker §4.2.1: “A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.”
3. **Verifies.** The declarations come to you, and your job is to establish that they are true and that nothing has been left out. Baker §3.2: “Verification focuses on checking that these declarations are correct and complete.”
4. **Outside the declaration.** Nothing you do appears in anybody’s declaration, because you sit below the threshold, or because you exist to keep a name off one. Baker §3.2, Subgoal 2.B: “Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations.”

#### Question: Open
id:: 8d8479c7-a8f1-49f9-8e3d-8f151a9a7a93
content:: Place each of the seventeen actors on one ring: Declares, Holds the evidence, Verifies, or Outside the declaration. One line per actor: United States, China, Taiwan, Netherlands, Japan, South Korea, BIS, Intelligence community, California, No AI verification body, ASML, TSMC, NVIDIA, Cloud providers, Frontier labs, Proxies, Deployers.
force-feedback:: first
feedback-instructions:: For every actor placed on the wrong ring, give the key ring and the source lesson's one-line reason from the placement key callout below. If the learner argued against the cloud providers on Declares or the proxies beside the deployers, answer the argument: Baker names cloud compute providers among the Provers; the proxies and the deployers are opposite in intent and alike in the one property the ring names. For correct placements, the ring name is the explanation; do not expand them. Then tell the learner to read the finished map. The key: Declares: United States, China, cloud providers, frontier labs. Holds the evidence: Taiwan, Netherlands, Japan, South Korea, ASML, TSMC, NVIDIA. Verifies: BIS, intelligence community, California, no AI verification body. Outside the declaration: proxies, deployers. Reference answer, not a checklist: "Declares: United States, China, cloud providers, frontier labs. Holds the evidence: Taiwan, Netherlands, Japan, South Korea, ASML, TSMC, NVIDIA. Verifies: BIS, intelligence community, California, the AI verification body that does not exist. Outside the declaration: proxies, deployers. In an international agreement the Prover is a government, so the two signatories declare, alongside the organisations that own or use large-scale compute: Baker names major AI companies and cloud compute providers among them. The supply-chain states and firms declare nothing and check nothing, but hold records a declaration can be checked against. Proxies and deployers share the outer ring for opposite reasons: the proxies exist to keep a name off any declaration, the deployers sit below the threshold."

#### Text
content::
:::callout {title="Placement key, actor by actor (open after you have answered)" tone="neutral" collapse="closed"}
<svg viewBox="172 44 616 762" width="100%" style="max-width:616px;height:auto" role="img" aria-label="The finished actor map, as in the placement key. At the centre, a training run above the threshold. Ring 1, Declares: United States, China, cloud providers, frontier labs. Ring 2, Holds the evidence: Taiwan, Netherlands, Japan, South Korea, ASML, TSMC, NVIDIA. Ring 3, Verifies: BIS, intelligence community, California, and the verification body that does not exist. Ring 4, Outside the declaration: proxies, deployers. Six small squares under each actor mark its roles, in the order of the legend." font-family="DM Sans, Arial, sans-serif">
<g fill="none" stroke="currentColor" stroke-opacity="0.22" stroke-width="1.25"><circle cx="480" cy="350" r="84"/><circle cx="480" cy="350" r="150"/><circle cx="480" cy="350" r="216"/><circle cx="480" cy="350" r="278"/></g>
<g fill="currentColor" fill-opacity="0.65" font-size="11" letter-spacing="0.06em" text-anchor="middle"><text x="480" y="256">1. DECLARES</text><text x="480" y="190">2. HOLDS THE EVIDENCE</text><text x="480" y="124">3. VERIFIES</text><text x="480" y="62">4. OUTSIDE THE DECLARATION</text></g>
<circle cx="480" cy="350" r="4" fill="#b87018"/>
<g fill="currentColor" text-anchor="middle"><text x="480" y="372" font-size="13" font-weight="600">A training run</text><text x="480" y="390" font-size="11.5" fill-opacity="0.65">above the threshold</text></g>
<g fill="currentColor"><circle cx="524.2" cy="278.6" r="6.5"/><circle cx="413.0" cy="299.4" r="6.5"/><circle cx="599.7" cy="259.6" r="6.5"/><circle cx="425.8" cy="489.9" r="6.5"/><circle cx="345.7" cy="416.9" r="6.5"/><circle cx="335.7" cy="309.0" r="6.5"/><circle cx="687.8" cy="290.9" r="6.5"/><circle cx="480.0" cy="566.0" r="6.5"/><circle cx="264.9" cy="369.9" r="6.5"/><circle cx="440.3" cy="137.7" r="7" fill="none" stroke="currentColor" stroke-opacity="0.7" stroke-width="1.25" stroke-dasharray="3 2"/><circle cx="507.6" cy="202.6" r="6.5"/><circle cx="534.2" cy="489.9" r="6.5"/><circle cx="629.4" cy="363.8" r="6.5"/><circle cx="555.2" cy="387.4" r="6.5"/><circle cx="423.4" cy="412.1" r="6.5"/><circle cx="667.3" cy="555.4" r="6.5"/><circle cx="333.7" cy="113.6" r="6.5"/></g>
<g fill="currentColor" font-size="12.5"><text x="538.2" y="283.6">United States</text><text x="427.0" y="300.4">China</text><text x="613.7" y="260.6">Taiwan</text><text x="411.8" y="490.9" text-anchor="end">Netherlands</text><text x="331.7" y="417.9" text-anchor="end">Japan</text><text x="321.7" y="310.0" text-anchor="end">South Korea</text><text x="701.8" y="291.9">BIS</text><text x="494.0" y="567.0">Intelligence community</text><text x="250.9" y="370.9" text-anchor="end">California</text><text x="426.3" y="141.7" text-anchor="end">No AI verification body</text><text x="521.6" y="203.6">ASML</text><text x="548.2" y="490.9">TSMC</text><text x="643.4" y="364.8">NVIDIA</text><text x="569.2" y="392.4">Cloud providers</text><text x="437.4" y="413.1">Frontier labs</text><text x="681.3" y="556.4">Proxies</text><text x="319.7" y="114.6" text-anchor="end">Deployers</text></g>
<path fill="#b87018" d="M538.2 288.6h7v7h-7zM547.7 288.6h7v7h-7zM557.2 288.6h7v7h-7zM566.7 288.6h7v7h-7zM427.0 305.4h7v7h-7zM436.5 305.4h7v7h-7zM446.0 305.4h7v7h-7zM455.5 305.4h7v7h-7zM623.2 265.6h7v7h-7zM632.7 265.6h7v7h-7zM661.2 265.6h7v7h-7zM366.8 495.9h7v7h-7zM376.3 495.9h7v7h-7zM286.7 422.9h7v7h-7zM276.7 315.0h7v7h-7zM286.2 315.0h7v7h-7zM720.8 296.9h7v7h-7zM730.3 296.9h7v7h-7zM513.0 572.0h7v7h-7zM215.4 375.9h7v7h-7zM224.9 375.9h7v7h-7zM531.1 208.6h7v7h-7zM540.6 208.6h7v7h-7zM557.7 495.9h7v7h-7zM567.2 495.9h7v7h-7zM586.2 495.9h7v7h-7zM652.9 369.8h7v7h-7zM662.4 369.8h7v7h-7zM681.4 369.8h7v7h-7zM690.9 369.8h7v7h-7zM578.7 397.4h7v7h-7zM588.2 397.4h7v7h-7zM597.7 397.4h7v7h-7zM607.2 397.4h7v7h-7zM437.4 418.1h7v7h-7zM456.4 418.1h7v7h-7zM484.9 418.1h7v7h-7zM719.3 561.4h7v7h-7zM312.7 119.6h7v7h-7zM188.0 689.0h7v7h-7zM497.5 689.0h7v7h-7zM207.0 711.0h7v7h-7zM516.5 711.0h7v7h-7zM226.0 733.0h7v7h-7zM535.5 733.0h7v7h-7z"/>
<path fill="none" stroke="currentColor" stroke-opacity="0.3" stroke-width="1" d="M576.2 288.6h7v7h-7zM585.7 288.6h7v7h-7zM465.0 305.4h7v7h-7zM474.5 305.4h7v7h-7zM613.7 265.6h7v7h-7zM642.2 265.6h7v7h-7zM651.7 265.6h7v7h-7zM357.3 495.9h7v7h-7zM385.8 495.9h7v7h-7zM395.3 495.9h7v7h-7zM404.8 495.9h7v7h-7zM277.2 422.9h7v7h-7zM296.2 422.9h7v7h-7zM305.7 422.9h7v7h-7zM315.2 422.9h7v7h-7zM324.7 422.9h7v7h-7zM267.2 315.0h7v7h-7zM295.7 315.0h7v7h-7zM305.2 315.0h7v7h-7zM314.7 315.0h7v7h-7zM701.8 296.9h7v7h-7zM711.3 296.9h7v7h-7zM739.8 296.9h7v7h-7zM749.3 296.9h7v7h-7zM494.0 572.0h7v7h-7zM503.5 572.0h7v7h-7zM522.5 572.0h7v7h-7zM532.0 572.0h7v7h-7zM541.5 572.0h7v7h-7zM196.4 375.9h7v7h-7zM205.9 375.9h7v7h-7zM234.4 375.9h7v7h-7zM243.9 375.9h7v7h-7zM371.8 146.7h7v7h-7zM381.3 146.7h7v7h-7zM390.8 146.7h7v7h-7zM400.3 146.7h7v7h-7zM409.8 146.7h7v7h-7zM419.3 146.7h7v7h-7zM521.6 208.6h7v7h-7zM550.1 208.6h7v7h-7zM559.6 208.6h7v7h-7zM569.1 208.6h7v7h-7zM548.2 495.9h7v7h-7zM576.7 495.9h7v7h-7zM595.7 495.9h7v7h-7zM643.4 369.8h7v7h-7zM671.9 369.8h7v7h-7zM569.2 397.4h7v7h-7zM616.7 397.4h7v7h-7zM446.9 418.1h7v7h-7zM465.9 418.1h7v7h-7zM475.4 418.1h7v7h-7zM681.3 561.4h7v7h-7zM690.8 561.4h7v7h-7zM700.3 561.4h7v7h-7zM709.8 561.4h7v7h-7zM728.8 561.4h7v7h-7zM265.2 119.6h7v7h-7zM274.7 119.6h7v7h-7zM284.2 119.6h7v7h-7zM293.7 119.6h7v7h-7zM303.2 119.6h7v7h-7zM197.5 689.0h7v7h-7zM207.0 689.0h7v7h-7zM216.5 689.0h7v7h-7zM226.0 689.0h7v7h-7zM235.5 689.0h7v7h-7zM488.0 689.0h7v7h-7zM507.0 689.0h7v7h-7zM516.5 689.0h7v7h-7zM526.0 689.0h7v7h-7zM535.5 689.0h7v7h-7zM188.0 711.0h7v7h-7zM197.5 711.0h7v7h-7zM216.5 711.0h7v7h-7zM226.0 711.0h7v7h-7zM235.5 711.0h7v7h-7zM488.0 711.0h7v7h-7zM497.5 711.0h7v7h-7zM507.0 711.0h7v7h-7zM526.0 711.0h7v7h-7zM535.5 711.0h7v7h-7zM188.0 733.0h7v7h-7zM197.5 733.0h7v7h-7zM207.0 733.0h7v7h-7zM216.5 733.0h7v7h-7zM235.5 733.0h7v7h-7zM488.0 733.0h7v7h-7zM497.5 733.0h7v7h-7zM507.0 733.0h7v7h-7zM516.5 733.0h7v7h-7zM526.0 733.0h7v7h-7z"/>
<g fill="currentColor" font-size="12.5"><text x="188" y="672" font-weight="600">Roles: the six squares under each actor, left to right</text><text x="252.0" y="697">1. Capability holder</text><text x="552.0" y="697">2. Chokepoint controller</text><text x="252.0" y="719">3. Information holder</text><text x="552.0" y="719">4. Enforcement authority</text><text x="252.0" y="741">5. Evasion pathway</text><text x="552.0" y="741">6. Victim, free-rider, beneficiary</text></g>
<g fill="currentColor" fill-opacity="0.65" font-size="11.5"><text x="188" y="772">Dashed circle: the verification body that does not exist.</text><text x="188" y="788">Placements follow the placement key, and roles follow the roster.</text></g>
</svg>

**Declares**

- **United States.** In an international agreement the Prover is a government. The paper says so directly, and adds that it is the party “which could constrain private companies within its territory as part of the agreement”. So the signatory declares, and the buildings inside it are the machinery it verifies the other signatory WITH. That is the lesson’s own point about asking which building, drawn as two different rings.
- **China.** The other Prover, and on this board that is all it is, because the roster has no row for its bureaus. The United States brings three institutions to the verifying ring and China brings none, which is a fact about this map rather than about the world, and worth holding on to when you read what the map claims.
- **Cloud providers.** Baker puts them in the same parenthesis as the labs: the declarations are of ownership AND use of large-scale compute, and the cluster is theirs. They are also the actor the labs’ own declaration can be checked against, because of what the lesson says the position hands them: “between customer and machine: logs, billing, telemetry, and the power to interrupt a job”.
- **Frontier labs.** They perform the regulated act, so they are the Prover: every obligation in the agreement is ultimately about what they did or did not train, and the declaration is theirs to make.

**Holds the evidence**

- **Taiwan.** The state does not hold the fab’s shipment records; the fab does. What Taiwan holds is the jurisdiction that makes those records a governable object at all, and it is not a party to this agreement, so nothing in the agreement compels it to exercise that.
- **Netherlands.** One company in one country, and the country is the reason the company’s customer list is reachable. Export law over a single vendor is close to the strongest evidentiary lever anywhere on this board, and it belongs to a state that signed nothing.
- **Japan.** Equipment and specialty materials: several quieter chokepoints, and the same shape as the Netherlands. Its records matter to a verifier and its participation is voluntary.
- **South Korea.** High-bandwidth memory is scarce, essential to frontier training, and therefore countable, which makes the jurisdiction over the firms that make it an evidence position, not just a trade one.
- **ASML.** The most upstream supplier there is, and upstream of Baker’s chain of custody, which begins at manufacturing. The tightest chokepoint on the board holds evidence about nobody, which is the sharpest thing this frame does to the roster.
- **TSMC.** The chain of custody starts where the die is made. How many leading-edge parts exist at all, and who they were made for, is a fact only the fab holds, which is the same thing the lesson means by the “single tightest physical chokepoint in the system”, read as evidence rather than as leverage.
- **NVIDIA.** Upstream of the run, not in it, and not a Prover for anybody else’s run. What it decides is whether accelerators ship with the security features a Verifier would read, which is why it holds evidence about two different actors and no declaration of its own here.

**Verifies**

- **BIS.** A government body receiving and checking declarations is exactly Baker’s Verifier, and the lesson calls it the “de facto compute-governance agency today”. Its own instrument, export control, is enforcement, which Baker puts outside the frame on purpose.
- **Intelligence community.** A Verifier that also produces its own evidence. Baker gives national intelligence every subgoal at once, and it is the only actor on this board that can reach a facility nobody ever declared.
- **California.** It made frontier developers report, which is a declaration regime. Verification is what happens to a declaration afterwards, so on this map it is a Verifier that has, as yet, nothing to check the reports against.
- **No AI verification body.** The paper allows two kinds of Verifier: “The Verifier could be a government body or a third party.” Every government body on this ring belongs to one signatory. The third party is this row, and it is empty: no chip registry, no challenge-inspection right at a data centre, no procedure for resolving an allegation. It is drawn because a ring with only one party’s institutions on it is a claim, and the claim is false.

**Outside the declaration**

- **Proxies.** A declaration cannot cover a name that exists to “break the link between a name and an activity”. They are the case Subgoal 2.B covers: an undeclared cluster, which the second half of the framework is built to find.
- **Deployers.** Outside every declaration for the opposite reason: below the threshold. Baker defines large-scale in thousands of chips over months, so millions of actors who “benefit from safety and bear none of its costs” are outside the regime by construction rather than by evasion.
:::

\### 5. What the finished map says

{--{"author":"Andreas's AI","timestamp":1793242814103}@@{>>{"author":"Andreas's AI","timestamp":1793164094132}@@Stage 6 flag, self-contained and Content: this section comes from XLab's workshop widget, whose ring graphic the port did not reproduce. "Now read the colours across the rings" and "this board" point to a picture this page does not have. Content: "Exactly two actors on this board owe anybody a declaration", but the placement key above puts four on Declares (United States, China, cloud providers, frontier labs). XLab's own data has the same mismatch; it is noted for Andreas and Elias. See the CV1 plain language worklist.<<}Read--}{++{"author":"Andreas's AI","timestamp":1793242814103}@@Read++} your rings from the inside out. Exactly four actors on this board owe anybody a declaration; everything outside them either holds evidence about that declaration, or checks it, or is not covered by any declaration at all. A verification regime is a much smaller object than the map of who matters: most of this board it does not reach, and half of it cannot help.

Now read the role squares across the rings instead of around them. Roles do not stay in their band: the cloud provider holds four of them at once, and the ring it sits on tells you none of the four. The section gives you three questions to ask of any actor: where does it sit on the chain (position, Table 4, and the map in 1.2.1 is where you practise it), what can it do inside a regime (roles), what does it want today (posture). These rings are a fourth, and a narrower one: not where an actor sits, but what part it plays in checking a declaration. All four cut across each other, which is why no single one of them is the map.

{--{"author":"Andreas's AI","timestamp":1793242816008}@@{>>{"author":"Andreas's AI","timestamp":1793164097333}@@Stage 6 flag, Lens text: this line and the one after it, "The edge exercise built on this board comes after the supply-chain map", both send the learner on to the same page; one would do. --}The{--{"author":"Andreas's AI","timestamp":1793242816008}@@ section numbers are left for stage 7. See the CV1 plain language worklist.<<}The--} second-order question (take one actor off the board) and the three optional written answers follow in [[../Lenses/XLab Verification - v-actor-edges|1.2.2]], after the edges are drawn on this map.{>>{"author":"Elias's AI","timestamp":1788016535133}@@Native reproduction of XLab's Actor Map Workshop from src/lib/verification/data/actor-workshop.ts and actor-map.ts (roster, recall target, core question, Baker rings and placement key, map finding, second-order question, closing questions and marking key). Note for Elias: in XLab's current repo, scoping-actors.mdx is cut to three paragraphs and the actor-workshop widget is no longer registered; the five tables above and the workshop are documented as XLab's own in docs/verification/module-1-log.md, so they are kept. XLab's ring map graphic (concentric SVG) is not reproduced; the placements are.<<}
#### Text
content::
\### Notes and sources

The draft agreement this section reads its cast out of: Scher, Abecassis, Barnett & Abeyta, [“An International Agreement to Prevent the Premature Creation of Artificial Superintelligence”](https://arxiv.org/abs/2511.10783) (2025), Appendix A, the treaty 1.1 dissects.

[California SB 53](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB53), the Transparency in Frontier Artificial Intelligence Act, signed September 29, 2025; core duties effective January 1, 2026 ([Future of Privacy Forum](https://fpf.org/blog/californias-sb-53-the-first-frontier-ai-law-explained/) and [White & Case](https://www.whitecase.com/insight-alert/california-enacts-landmark-ai-transparency-law-transparency-frontier-artificial) summaries).

[EU AI Act, Article 51](https://artificialintelligenceact.eu/article/51/): presumption of systemic risk above 10^25 training FLOP.

[UN Independent International Scientific Panel on AI](https://www.un.org/independent-international-scientific-panel-ai/en) (est. 2025; first meeting March 2026); [Global Dialogue on AI Governance](https://news.un.org/en/story/2026/07/1167873), Geneva, July 2026.

[NIST Center for AI Standards and Innovation (CAISI)](https://www.nist.gov/caisi), formerly the US AI Safety Institute; pre-deployment testing agreements with frontier developers.

Supply-chain structure: Sastry, Heim, Belfield et al., [“Computing Power and the Governance of Artificial Intelligence”](https://arxiv.org/abs/2402.08797) (2024): ASML at 100% of EUV lithography, TSMC at ~90% of sub-7nm logic (2022 data), and “several critical steps … have fewer than three suppliers”; CSET, [“The Semiconductor Supply Chain”](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/) (2021): the stage-by-stage picture, including that assembly and test has the lowest barriers to entry. High-bandwidth memory is inside the export-control perimeter: the US controls were “expanded again, this time affecting all chips using advanced high-bandwidth memory” (Fist, Burga & Chilukuri, [“Technology to Secure the AI Chip Supply Chain”](https://www.cnas.org/publications/reports/technology-to-secure-the-ai-chip-supply-chain-a-primer) (CNAS, 2024)). Incentive vocabulary and role taxonomy: this module’s introduction.

**Currency.** The concentration figures above are 2021–2023 data reported in 2021 and 2024 sources. Shares move; the structure (one EUV maker, one dominant leading-edge fab, a handful of clouds) has not. Re-verify a number before quoting it.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Scher, Aaron, David Abecassis, Peter Barnett, et al. "An International Agreement to Prevent the Premature Creation of Artificial Superintelligence." *arXiv*, Nov. 2025. [arxiv.org](https://arxiv.org/abs/2511.10783)
*MIRI's draft international agreement to prevent the premature creation of artificial superintelligence, the treaty text several lessons read against.*

"Article 51: Classification of General-Purpose AI Models as General-Purpose AI Models with Systemic Risk." *EU Artificial Intelligence Act*, artificialintelligenceact.eu. [artificialintelligenceact.eu](https://artificialintelligenceact.eu/article/51/)
*The consolidated text of the AI Act article that presumes systemic risk above 10^25 training FLOP.*

Sastry, Girish, Lennart Heim, Haydn Belfield, et al. "Computing Power and the Governance of Artificial Intelligence." *arXiv*, Feb. 2024. [arxiv.org](https://arxiv.org/abs/2402.08797)
*The foundational survey of compute as a governance lever: why computing power is detectable, excludable, and quantifiable in ways algorithms and data are not.*

Khan, Saif M., Alexander Mann, and Dahlia Peterson. *The Semiconductor Supply Chain: Assessing National Competitiveness*. Center for Security and Emerging Technology, Jan. 2021. [cset.georgetown.edu](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/)
*CSET's mapping of the semiconductor supply chain and where national chokepoints sit.*

Fist, Tim, Tao Burga, and Vivek Chilukuri. *Technology to Secure the AI Chip Supply Chain: A Working Paper*. Center for a New American Security, 2024. [cnas.org](https://www.cnas.org/publications/reports/technology-to-secure-the-ai-chip-supply-chain-a-primer)
*Argues that export controls on AI chips are hard to enforce and easy to evade through shell companies, and proposes hardware-enabled mechanisms instead.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*The report whose Prover and Verifier frame and four subgoals give the workshop its rings; every ring test and placement reason quotes it.*

XLab. "1.2 Actors: who does the treaty rely upon, apply to, and constrain?" *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-actors)
*The source lesson this page adapts, including the five tables and the Actor Map Workshop.*

The SB 53 bill text, the SB 53 reference site, METR's guide, the Future of Privacy Forum and White & Case summaries, the UN panel and Global Dialogue pages, and NIST CAISI are cited inline in Notes and sources and have no entry in XLab's citation registry.
:::
