---
id: '76451830-cdb6-4160-9eae-ee72d0917f5b'
title: "1.2 Actors: who does the treaty rely upon, apply to, and constrain?"
tldr: {--{"author":"Elias's AI","timestamp":1788016429938}@@"Faithful alpha import of XLab lesson 1.2 Actors:--}{++{"author":"Elias's AI","timestamp":1788016429938}@@"Two governments sign a three-month pause on big training runs. On Wednesday morning,++} who {--{"author":"Elias's AI","timestamp":1788016429938}@@does--}{++{"author":"Elias's AI","timestamp":1788016429938}@@actually has to change what they do? Not the signatories:++} the {--{"author":"Elias's AI","timestamp":1788016429938}@@treaty rely upon, apply to,--}{++{"author":"Elias's AI","timestamp":1788016429938}@@labs, fabs, clouds and one Dutch lithography firm. Learn three lenses for any actor (where it sits, what it can do for or to a verifier, what it wants right now), then build the actor map yourself: who declares, who holds evidence, who verifies,++} and {--{"author":"Elias's AI","timestamp":1788016429938}@@constrain?."--}{++{"author":"Elias's AI","timestamp":1788016429938}@@who no declaration ever covers."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016429938}@@"Imported--}{++{"author":"Elias's AI","timestamp":1788016429938}@@"Reading plus a workshop. The reading gives five tables: the incentive vocabulary (comply, defect, hide, exaggerate, free-ride), six states by supply-chain position, US institutions inside one signatory, private actors upstream to downstream, and six functional roles; then the three questions to ask of any actor (position, roles, posture). The Actor Map Workshop follows: study the 17-actor roster, then++} from {++{"author":"Elias's AI","timestamp":1788016429938}@@memory list everything a cloud provider can do inside a regime; a graded choice on what sits at the centre of the map (the regulated training run); place all 17 actors on Baker et al.'s four rings (Declares, Holds the evidence, Verifies, Outside the declaration), graded against XLab's key; a graded second-order question (removing the cloud providers stops a run soonest); and three optional written answers marked against ++}XLab's {--{"author":"Elias's AI","timestamp":1788016429938}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed --}{++{"author":"Elias's AI","timestamp":1788016429938}@@key (Taiwan's roles, information holders in order of completeness, an actor that is capability holder and enforcement authority at once). The ring key and rationales sit in closed callouts; do not reveal them before the learner commits. The edge exercise built ++}on {--{"author":"Elias's AI","timestamp":1788016429938}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788016429938}@@this board is the next lens, 1.2.2."++}
tags: [wip]
duration_minutes: 35
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
| Hide | Obscure assets or activities from view, whether or not any rule is being broken. | A firm treating its chip inventory as a trade secret. |
| Exaggerate | Overstate compliance, safety, or capability. | Safety-washing by a lab; capability bluffing by a state. |
| Free-ride | Enjoy the stability produced by others’ restraint without bearing its costs. | A state that signs nothing and benefits anyway. |

Keep in mind that these are postures, not fixed personality types. The same actor can comply on one obligation, hide on another, and free-ride on a third, all in the same quarter. The interesting question is never “is this actor good.” It is “what does this actor do under this rule, at this moment, given what it costs.” That cost framework will be recurring throughout the course and policy frameworks, so it’s important to internalize an understanding and instinct for it.

Let’s start with nation-states, since they are the ones that sign. A state matters to verification roughly in proportion to what passes through its territory and its law. Six states cover most of the compute supply chain that {--{"author":"Elias's AI","timestamp":1788016433607}@@1.2.1--}{++{"author":"Elias's AI","timestamp":1788016433607}@@[[../Lenses/XLab Verification - v-interactive-map|1.2.1]]++} maps.

Table 2.  States, by position on the compute supply chain

| State | What runs through it | What that buys a verifier | Standing worry |
| --- | --- | --- | --- |
| United States | Chip design (NVIDIA, AMD), the largest frontier labs and cloud providers, and export-control law. | It can see and squeeze more of the chain than anyone. Its export rules are the closest thing to a working compute-control regime today. | Losing its lead; verification machinery being turned on its own firms. |
| China | The other frontier developer. Manufacturing scale, rare earths and materials, its own designers, clouds, and labs. | No agreement is meaningful without it, and it controls inputs the rest of the chain needs. | Reads on-chip controls and inspections as surveillance and containment. |
| Taiwan | TSMC, which fabricates the overwhelming share of leading-edge AI chips. | The single tightest physical chokepoint in the system. | Being both the prize and the battlefield in a conflict it does not control. |
| Netherlands | ASML, the world’s only maker of EUV lithography machines. | One company in one country: one of the strongest levers anywhere in the system. | A small state carrying outsized geopolitical weight. |
| Japan | Semiconductor equipment (Tokyo Electron) and specialty materials. | Several quieter chokepoints in equipment and chemistry. | Pressure from both sides of the US-China rivalry. |
| South Korea | Samsung and SK Hynix, the largest memory makers, including high-bandwidth memory (HBM). | HBM is scarce and essential to frontier training: a countable, checkable input. | Export exposure to China against alliance pressure from the US. |

It’s also important to name the European Union. Even though as a whole, the EU isn’t a hub for silicon, it matters as a rule-writer. The EU AI Act carries the 10^25 FLOP presumption of systemic risk, the most cited compute threshold in force anywhere, and rules written in Brussels have a habit of being copied elsewhere.

Now, the next level.

\## {--{"author":"Elias's AI","timestamp":1788016435534}@@Institutions--}{++{"author":"Elias's AI","timestamp":1788016435534}@@Below the state{>>{"author":"Elias's AI","timestamp":1788016435534}@@"Institutions++} below, inside, and above the {--{"author":"Elias's AI","timestamp":1788016435534}@@state

\## Below --}{++{"author":"Elias's AI","timestamp":1788016435534}@@state" was XLab's PageBreak title, imported as a duplicate heading; kept only ++}the {--{"author":"Elias's AI","timestamp":1788016435534}@@state--}{++{"author":"Elias's AI","timestamp":1788016435534}@@real heading.<<}++}

Subnational governments regulate too, and this is often easier and/or happens earlier than federal regulation. California is this course’s running example because most frontier labs are physically headquartered there, and jurisdiction follows geography.

In September 2025 California enacted SB 53, the Transparency in Frontier Artificial Intelligence Act, with its main duties taking effect in January 2026. Two thresholds decide who it reaches. A **frontier model** is one trained on more than 10^26 operations, and anyone who trains one is a **frontier developer**; a **large frontier developer** is a frontier developer whose annual gross revenues, with affiliates, exceed $500 million. (Nobody publishes a list of who that is. Coverage turns on the compute number, and the compute number is one only the developer measures: as of early 2026 the [SB 53 reference](https://sb53.info/faq) records that just two developers are publicly known to have trained above the threshold, OpenAI and xAI, while METR’s [guide for lab staff](https://metr.org/notes/2026-01-29-frontier-ai-safety-regulations/) names OpenAI, Google, Anthropic and xAI as examples of who these laws govern rather than as a roster. Hold on to that: it is a rule whose scope is set by a quantity the regulated party alone can count.)

Every frontier developer must publish a transparency report when it deploys a new frontier model, report critical safety incidents to the state’s Office of Emergency Services within fifteen days — twenty-four hours if there is imminent risk of death or serious physical injury — and tell its employees they have whistleblower rights. Large frontier developers carry more on top: a published framework describing how they identify and mitigate catastrophic risks, fuller transparency reports, and an internal channel for anonymous reports.

Notice what happened there. A state legislature bound the world’s leading labs to reporting duties before any international mechanism existed. When you design a regime later in this course, remember that some of its machinery may already exist two levels below the treaty. Often, it might be easier to pass state level legislation before federal legislation follows.

\### Inside the state

“The United States wants X” obfuscates that a state is a bundle of institutions with different jobs and different incentives, and these groups have core differences on AI verification.

Table 3.  Inside one signatory: the United States

| Institution | Job in a verification regime | Incentive to watch |
| --- | --- | --- |
| State Department | Negotiates the agreement and runs the diplomacy around compliance disputes. | Wants a deal that survives politics; may trade verification strictness for signatures. |
| Commerce Department (Bureau of Industry and Security) | Writes and enforces export controls on chips: the de facto compute-governance agency today. | Enforcement capacity is small relative to the job, and the rules shift with each administration. |
| Department of War | Strategic and military stakes in frontier AI. | Wants American capability unconstrained; wary of any regime that could bind its own programs. |
| Intelligence community (CIA, NSA, and the rest) | Monitoring and attribution: the “national technical means” layer that spots hidden data centers and procurement networks. | What it knows is classified. Turning intelligence into shareable treaty evidence risks burning sources. |
| NIST and its Center for AI Standards and Innovation (CAISI) | Standards and testing. Runs pre-deployment evaluation agreements with several frontier developers. | Voluntary agreements, not inspection authority; renamed and refocused as the politics changed. |

Same government, five postures. When a proposal says “the US will verify,” your first question should be: which building?

\### Above the state

Is there a WHO for AI? An IAEA? As of mid-2026, there are some authorities but they don’t have a lot of real power or mechanisms to detect cheating. The UN has stood up the Independent International Scientific Panel on AI, forty scientists modeled on the IPCC and co-chaired by Yoshua Bengio and Maria Ressa, whose reports feed a new Global Dialogue on AI Governance that met for the first time in Geneva in July 2026. While this helps build a shared scientific picture of risk, it does not fix the verification function. No agency holds a chip registry. No inspector has challenge-inspection rights at a data center. No treaty gives anyone the authority over compute that the IAEA has held over fissile material since the 1970s. The institutional shelf marked “AI verification body” is empty. Some of the people reading this will help build what goes on it.

\## Private {--{"author":"Elias's AI","timestamp":1788016438341}@@actors along the supply chain

\## Private --}actors: reading the chain from top to bottom

Now the companies. The useful way to hold them in your head is not alphabetical but positional: upstream to downstream, the same axis as the map in {--{"author":"Elias's AI","timestamp":1788016438341}@@1.2.1.--}{++{"author":"Elias's AI","timestamp":1788016438341}@@[[../Lenses/XLab Verification - v-interactive-map|1.2.1]].++} Read the table from top to bottom and watch two numbers change as you go: how many actors exist at each stage, and how much each one can see.

Table 4.  Private actors, upstream to downstream

| Stage | Who (examples) | What they hold that a verifier needs | Default posture |
| --- | --- | --- | --- |
| Equipment | ASML (EUV lithography); Applied Materials, Tokyo Electron. | The machines without which no leading-edge chip exists, and knowledge of every fab that buys one. | Comply. Few customers, total visibility, nowhere to hide. |
| Fabrication and memory | TSMC, Samsung, SK Hynix, Intel. | The physical record: what was made, how many, and for whom. | Comply, while caught between US rules and Chinese customers. |
| Chip design | NVIDIA, AMD; Huawei and other Chinese designers. | The blueprint: whether chips ship with attestation, metering, or location features at all. | Comply with controls while lobbying hard against them. Verification features cost money and sales. |
| Packaging, assembly, test | Advanced-packaging lines (TSMC’s CoWoS and rivals); outsourced assembly-and-test firms. | Advanced packaging is a second, quieter bottleneck: chips pass through it and can be counted. Ordinary assembly and test is not — it is labor-intensive and has the lowest barriers to entry of any stage. | Mostly invisible in policy debates, which is itself a gap. |
| Cloud providers | AWS, Microsoft Azure, Google Cloud, Oracle, Alibaba; specialists like CoreWeave. | The position between customer and machine: logs, billing, telemetry, and the power to interrupt a job. | Comply and hide at once. Natural monitors, reluctant police. |
| Frontier labs | OpenAI, Anthropic, Google DeepMind, Meta, xAI; DeepSeek, Alibaba, and Moonshot in China. | The most detailed private information in the system: what was trained, on what data, and what the evals showed. | Every posture, potentially. |
| Deployers | Everyone building products on top of models. | A diffuse downstream signal of what models can actually do. | Free-ride. They benefit from safety and bear none of its costs. |
| Proxies and contractors | Shell companies, resellers, straw buyers, intermediaries. | Nothing legitimate. They exist to break the link between a name and an activity. | The standing channel through which evasion flows. |

Take two things from this table.

Counts:

- One EUV maker.
- A handful of leading-edge fabs.
- A few consequential chip designers.
- Five or six hyperscale clouds.
- A few dozen labs that matter.
- Millions of deployers.
- The chain narrows to almost nothing at the top and fans out to everything at the bottom. Verification has something to grab exactly where the count is small, which is why so many of the mechanisms in Module 2 bite upstream. Hold that thought; section {--{"author":"Elias's AI","timestamp":1788016440427}@@1.3--}{++{"author":"Elias's AI","timestamp":1788016440427}@@[[../Lenses/XLab Verification - v-scoping-upstream-downstream|1.3]]++} develops it properly.

Second, look at the labs’ row: A frontier lab can comply, publishing a safety framework and reporting under SB 53. It can hide, treating training details as trade secrets. It can exaggerate, describing its own precautions in the most flattering light, which is what critics call safety-washing. And it can free-ride on rivals’ restraint. Your job in verification is to price these different behaviors and balance their relevant incentives.

\## Functional {--{"author":"Elias's AI","timestamp":1788016442005}@@roles

\## Functional --}roles: the second lens

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

\## {--{"author":"Elias's AI","timestamp":1788016443635}@@Use the actor map

\## --}How to use this section

You now have three questions to ask of any actor you meet in a proposal, a news story, or an exercise, for the rest of this course. Where does it sit on the chain? That is position: Table 4. What can it do inside a regime? That is roles: Table 5. What does it want right now? That is posture: Table 1. Ask them in that order and most verification claims come apart usefully in your hands. “The cloud providers will report suspicious training runs” stops being a reassuring sentence and becomes three checkable ones: they sit mid-chain where visibility is high; they hold the logs; and they will report exactly to the degree that reporting costs less than not reporting.

\## The Actor Map Workshop{++{"author":"Elias's AI","timestamp":1788016535133}@@ (18–22 min)

**The brief.** Suppose the United States and China sign an agreement tomorrow: no training runs above some compute threshold for three months. The section asked who has to change their behavior on Wednesday morning. The map asks the question after it: when the three months are up, who could show that they did, and who could show that somebody did not?

**Four rings: what part of a declaration you play.** A verification regime runs on declarations — somebody states what they own and what they did with it, somebody else establishes the statement is true and complete. Every actor is somewhere in that.

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
:::++}

{--{"author":"Elias's AI","timestamp":1788016535133}@@\##--}{++{"author":"Elias's AI","timestamp":1788016535133}@@\### 2. Recall

#### Question: Open
id:: 3df5fa92-d84b-4198-af75-e744dc299b53
content:: Take one actor: a cloud provider. From memory, write down everything it can do inside a verification regime — and what it wants while doing it.
assessment-instructions:: Six items make a full answer; score about 16 points each. Roles: chokepoint controller (it can suspend a customer's access this afternoon); information holder (its logs and billing records are the richest picture anywhere of who is computing what); enforcement authority (give it know-your-customer duties and it becomes the regime's front-line cop); evasion pathway (its reseller chains and mislabeled workloads are precisely how a determined actor reaches compute it should not have). Postures: comply and hide (Table 4's cloud row: "Comply and hide at once. Natural monitors, reluctant police."). Credit synonyms and paraphrases that capture the same capability or posture. No generic praise.
feedback-instructions:: One-turn mirror: name which of the six the learner got, list the ones missed with their one-line gloss, and close by telling them to move on. No re-teaching, no follow-up question.

#### Text
content::
:::callout {title="What a cloud provider can do, and wants (open after you have answered)" tone="neutral" collapse="closed"}
- **Chokepoint controller.** It can suspend a customer’s access this afternoon.
- **Information holder.** Its logs and billing records are the richest picture anywhere of who is computing what.
- **Enforcement authority.** Give it know-your-customer duties and it becomes the regime’s front-line cop.
- **Evasion pathway.** Its reseller chains and mislabeled workloads are precisely how a determined actor reaches compute it should not have.
- **Comply.** Table 4’s cloud row: “Comply and hide at once. Natural monitors, reluctant police.”
- **Hide.** The same row: a natural monitor that is a reluctant police force.
:::

\### 3. The centre

#### Question: Choice
id:: d119e50f-5b65-4d75-836e-e844943abfe7
content:: A pause agreement forbids training runs above a compute threshold. When you draw this map, what goes in the centre?
options::
- [x] The regulated activity itself — a training run above the threshold.
- The states that signed the agreement.
- The frontier labs the obligations land on.
- The chips the threshold is counted in.
feedback-instructions:: Give XLab's reasoning for the option chosen. The activity: "The map is of a rule, and a rule is about an act. It is also what the verification literature centres: Baker's framework takes the approach of compute accounting, which is the same act said in compute. Put it in the centre and every ring becomes an answer to one question — what part do you play in accounting for this run?" The signatories: "'Not the people who signed. Governments do not train frontier models.' Centre them and the map says the treaty regulates its own signatories rather than an activity. Then watch for what looks like a contradiction two steps from now: the signatories do end up on the innermost RING, because in an international agreement the party that owes the declaration is the government. Owing a declaration and performing the act are different things, and the centre is the act."++} The {--{"author":"Elias's AI","timestamp":1788016535133}@@Actor Map Workshop (18–22 min)--}{++{"author":"Elias's AI","timestamp":1788016535133}@@labs: "Close, and it is why they sit on the first ring. But the labs are who does the act, not the act — and a map centred on them has nowhere to put a run that happens somewhere else, under someone else's name." The chips: "The chips are what makes the act countable from outside, which is a property of the mechanism rather than of the rule. Centre the map here and every institution on it becomes an afterthought." Two or three sentences, no praise.++}

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016535133}@@ **Interactive exercise:**--}{++{"author":"Elias's AI","timestamp":1788016535133}@@
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
**The regulated activity itself.** The map is of a rule, and a rule is about an act. It is also what the verification literature centres: Baker's framework takes the approach of compute accounting, which is the same act said in compute. Put it in the centre and every ring becomes an answer to one question — what part do you play in accounting for this run? Baker et al., §3.1, AI compute accounting: “it seeks to verify compliance on the basis that all large-scale AI compute use is accounted for in compliant activities.”

**The states that signed the agreement.** “Not the people who signed. Governments do not train frontier models.” Centre them and the map says the treaty regulates its own signatories rather than an activity. Then watch for what looks like a contradiction two steps from now: the signatories do end up on the innermost RING, because in an international agreement the party that owes the declaration is the government. Owing a declaration and performing the act are different things, and the centre is the act.

**The frontier labs the obligations land on.** Close, and it is why they sit on the first ring. But the labs are who does the act, not the act — and a map centred on them has nowhere to put a run that happens somewhere else, under someone else’s name.

**The chips the threshold is counted in.** The chips are what makes the act countable from outside, which is a property of the mechanism rather than of the rule. Centre the map here and every institution on it becomes an afterthought.
:::

\### 4. Place

At the centre: **a training run above the threshold.** Around it, four rings. Each ring's test is quoted from Baker et al., Verifying International Agreements on AI (2025), the report [[../Lenses/XLab Verification - v-actor-edges|1.2.2]] keys its edges against.

1. **Declares.** You own or use large-scale compute — or you signed the agreement and answer for what happens inside your territory. Either way the regime wants a declaration from you: you are the Prover. Baker §3.1: “The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement.” And: “organizations that own or use large-scale AI compute (e.g., major AI companies and cloud compute providers) would be required to declare facts about” their compute.
2. **Holds the evidence.** You declare nothing here and you check nothing, but you hold a record a declaration can be held against — or the authority that makes somebody else’s record producible. Baker §4.2.1: “A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.”
3. **Verifies.** The declarations come to you, and your job is to establish that they are true and that nothing has been left out. Baker §3.1: “Verification focuses on checking that these declarations are correct and complete.”
4. **Outside the declaration.** Nothing you do appears in anybody’s declaration — because you sit below the threshold, or because you exist to keep a name off one. Baker §3.2, Subgoal 2.B: “Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations.”

#### Question: Open
id:: 8d8479c7-a8f1-49f9-8e3d-8f151a9a7a93
content:: Place each of the seventeen actors on one ring: Declares, Holds the evidence, Verifies, or Outside the declaration. One line per actor: United States, China, Taiwan, Netherlands, Japan, South Korea, BIS, Intelligence community, California, No AI verification body, ASML, TSMC, NVIDIA, Cloud providers, Frontier labs, Proxies, Deployers.
assessment-instructions:: Key: Declares: United States, China, Cloud providers, Frontier labs. Holds the evidence: Taiwan, Netherlands, Japan, South Korea, ASML, TSMC, NVIDIA. Verifies: BIS, Intelligence community, California, No AI verification body. Outside the declaration: Proxies, Deployers. Score the share of the seventeen placed on the key ring, scaled to 100. Two placements are meant to be argued with and earn credit when the learner gives the reason: a cloud provider on Declares (Baker names cloud compute providers among the Provers) and the proxies beside the deployers on Outside the declaration (opposite in intent, alike in the one property the ring names). No generic praise.
feedback-instructions:: For every actor placed on the wrong ring, give the key ring and++} XLab's {--{"author":"Elias's AI","timestamp":1788016535133}@@`actor-workshop` widget --}{++{"author":"Elias's AI","timestamp":1788016535133}@@one-line reason from the placement key callout below. For correct placements, the ring name is the explanation; do not expand them. Then tell the learner to read the finished map.

#### Text
content::
:::callout {title="Placement key, actor by actor (open after you have answered)" tone="neutral" collapse="closed"}
**Declares**

- **United States.** In an international agreement the Prover is a government — the paper says so directly, and adds that it is the party “which could constrain private companies within its territory as part of the agreement”. So the signatory declares, and the buildings inside it are the machinery it verifies the other signatory WITH. That is the lesson’s own point about asking which building, drawn as two different rings.
- **China.** The other Prover, and on this board that is all it is — because the roster ++}has no {--{"author":"Elias's AI","timestamp":1788016535133}@@direct Lens equivalent yet. Complete --}{++{"author":"Elias's AI","timestamp":1788016535133}@@row for its bureaus. The United States brings three institutions to the verifying ring and China brings none, which is a fact about this map rather than about the world, and worth holding on to when you read what the map claims.
- **Cloud providers.** Baker puts them in the same parenthesis as the labs — the declarations are of ownership AND use of large-scale compute, and the cluster is theirs. They are also the actor the labs’ own declaration can be checked against, because of what the lesson says the position hands them: “between customer and machine: logs, billing, telemetry, and the power to interrupt a job”.
- **Frontier labs.** They perform the regulated act, so they are the Prover: every obligation in the agreement is ultimately about what they did or did not train, and the declaration is theirs to make.

**Holds the evidence**

- **Taiwan.** The state does not hold the fab’s shipment records; the fab does. What Taiwan holds is the jurisdiction that makes those records a governable object at all — and ++}it {++{"author":"Elias's AI","timestamp":1788016535133}@@is not a party to this agreement, so nothing ++}in the {--{"author":"Elias's AI","timestamp":1788016535133}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-actors). --}{++{"author":"Elias's AI","timestamp":1788016535133}@@agreement compels it to exercise that.
- **Netherlands.** One company in one country, and the country is the reason the company’s customer list is reachable. Export law over a single vendor is close to the strongest evidentiary lever anywhere on this board, and it belongs to a state that signed nothing.
- **Japan.** Equipment and specialty materials: several quieter chokepoints, and the same shape as the Netherlands. ++}Its {--{"author":"Elias's AI","timestamp":1788016535133}@@surrounding --}{++{"author":"Elias's AI","timestamp":1788016535133}@@records matter to a verifier and its participation is voluntary.
- **South Korea.** High-bandwidth memory is scarce, essential to frontier training, and therefore countable — which makes the jurisdiction over the firms that make it an evidence position, not just a trade one.
- **ASML.** The most upstream supplier there is — and upstream of Baker’s chain of custody, which begins at manufacturing. The tightest chokepoint on the board holds evidence about nobody, which is the sharpest thing this frame does to the roster.
- **TSMC.** The chain of custody starts where the die is made. How many leading-edge parts exist at all, and who they were made for, is a fact only the fab holds — which is the same thing the ++}lesson {--{"author":"Elias's AI","timestamp":1788016535133}@@text--}{++{"author":"Elias's AI","timestamp":1788016535133}@@means by the “single tightest physical chokepoint in the system”, read as evidence rather than as leverage.
- **NVIDIA.** Upstream of the run, not in it, and not a Prover for anybody else’s run. What it decides is whether accelerators ship with the security features a Verifier would read — which++} is {--{"author":"Elias's AI","timestamp":1788016535133}@@preserved --}{++{"author":"Elias's AI","timestamp":1788016535133}@@why it holds evidence about two different actors and no declaration of its own ++}here.{++{"author":"Elias's AI","timestamp":1788016535133}@@

**Verifies**

- **BIS.** A government body receiving and checking declarations is exactly Baker’s Verifier, and the lesson calls it the “de facto compute-governance agency today”. Its own instrument — export control — is enforcement, which Baker puts outside the frame on purpose.
- **Intelligence community.** A Verifier that also produces its own evidence. Baker gives national intelligence every subgoal at once, and it is the only actor on this board that can reach a facility nobody ever declared.
- **California.** It made frontier developers report, which is a declaration regime. Verification is what happens to a declaration afterwards — so on this map it is a Verifier that has, as yet, nothing to check the reports against.
- **No AI verification body.** The paper allows two kinds of Verifier: “The Verifier could be a government body or a third party.” Every government body on this ring belongs to one signatory. The third party is this row, and it is empty — no chip registry, no challenge-inspection right at a data centre, no procedure for resolving an allegation. It is drawn because a ring with only one party’s institutions on it is a claim, and the claim is false.

**Outside the declaration**

- **Proxies.** A declaration cannot cover a name that exists to “break the link between a name and an activity”. They are Subgoal 2.B in person: the undeclared cluster the whole second half of the framework was built to find.
- **Deployers.** Outside every declaration for the opposite reason — below the threshold. Baker defines large-scale in thousands of chips over months, so millions of actors who “benefit from safety and bear none of its costs” are outside the regime by construction rather than by evasion.
:::

\### 5. What the finished map says

Read your rings from the inside out. Exactly two actors on this board owe anybody a declaration; everything outside them either holds evidence about that declaration, or checks it, or is not covered by any declaration at all. A verification regime is a much smaller object than the map of who matters — most of this board it does not reach, and half of it cannot help.

Now read the colours across the rings instead of around them. Roles do not stay in their band — the cloud provider holds four of them at once, and the ring it sits on tells you none of the four. The section gives you three questions to ask of any actor: where does it sit on the chain (position, Table 4, and the map in 1.2.1 is where you practise it), what can it do inside a regime (roles), what does it want today (posture). These rings are a fourth, and a narrower one: not where an actor sits, but what part it plays in checking a declaration. All four cut across each other, which is why no single one of them is the map.

#### Question: Choice
id:: 9f2573e0-1f40-40be-85f1-ba9107156979
content:: Take one actor off the board entirely. Whose removal stops a frontier training run soonest — this week, not this decade?
options::
- [x] The cloud providers.
- ASML.
- TSMC.
- The Bureau of Industry and Security.
feedback-instructions:: Give XLab's reasoning for the option chosen, then the lesson. Cloud providers: "The run happens on their machines. Access can be suspended this afternoon — and they are the other actor the regime asks for a declaration, because the cluster it happens on is theirs." ASML: "The most consequential removal on this board and the slowest. ASML is 100% of EUV lithography, so taking it away eventually takes leading-edge fabrication with it — but no training run stops this week, because the chips already exist." TSMC: "Same shape as ASML, one step nearer: ~90% of sub-7nm logic. It stops the next generation of chips, not the run already loaded." BIS: "It writes and enforces export controls and trains nothing. Remove it and the rules stop being enforced — which loosens the regime rather than stopping the activity." Lesson: "That gap is the thing a ring map is drawn to show. The removal that bites soonest and the removal that matters most are different actors, on different rings, and a regime that reaches only for the second one buys nothing this year. Ask both questions of any chokepoint you are offered." No praise.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
**The cloud providers.** The run happens on their machines. Access can be suspended this afternoon — and they are the other actor the regime asks for a declaration, because the cluster it happens on is theirs.

**ASML.** The most consequential removal on this board and the slowest. ASML is 100% of EUV lithography, so taking it away eventually takes leading-edge fabrication with it — but no training run stops this week, because the chips already exist.

**TSMC.** Same shape as ASML, one step nearer: ~90% of sub-7nm logic. It stops the next generation of chips, not the run already loaded.

**The Bureau of Industry and Security.** It writes and enforces export controls and trains nothing. Remove it and the rules stop being enforced — which loosens the regime rather than stopping the activity.

That gap is the thing a ring map is drawn to show. The removal that bites soonest and the removal that matters most are different actors, on different rings, and a regime that reaches only for the second one buys nothing this year. Ask both questions of any chokepoint you are offered.
:::

\### 6. Three written answers (optional)

#### Question: Open
id:: 05d81c94-4e73-4bc5-a462-aa7753def986
content:: Optional: Tag every functional role Taiwan holds. There are at least three.
optional:: true
assessment-instructions:: XLab's marking key, 3 points: (1) Taiwan is named as a chokepoint controller, and the reason is the fabrication step rather than the country (Table 2: "the single tightest physical chokepoint in the system"); reasoning required. (2) Taiwan is named as an information holder: what was fabricated, how much, and for whom (Table 5: "Who already knows what verifiers need to learn?"). (3) Taiwan is named as a victim or beneficiary: it carries the risk of being the chokepoint without controlling the conflict over it (Table 2: "being both the prize and the battlefield in a conflict it does not control"); reasoning required. No credit for naming Taiwan's three roles without saying what makes each one true. No generic praise.

#### Question: Open
id:: adc1c6ef-76db-4be7-840c-6456e8ae2805
content:: Optional: For one specific frontier training run, list the information holders in order of how complete their picture is.
optional:: true
assessment-instructions:: XLab's marking key, 3 points: (1) the information holders are put in an actual order, not listed; (2, worth 2 points) each rank carries the reason its picture is more or less complete, what that actor sees and what it cannot see (Table 4 gives each stage its holding: the lab knows what was trained and on what, the cloud holds logs and billing, the fab holds shipments); reasoning required. No credit for listing information holders in the order the lesson happens to print them, with no claim about completeness. No generic praise.

#### Question: Open
id:: 160e3cec-7fa2-4d1f-bb4f-d7140e91f58d
content:: Optional: Name one actor that is a capability holder and an enforcement authority at the same time, and say why that pairing should make you uneasy.
optional:: true
assessment-instructions:: XLab's marking key, 3 points: (1) the actor named holds capability and enforcement at once; on this roster that is a state with a frontier programme of its own (Table 3 splits one signatory into institutions that do not want the same thing); (2, worth 2 points) the unease is stated as a mechanism: the same actor builds the thing and judges whether the rules about it were broken, so an unfavourable finding costs it twice; reasoning required. No credit for calling it a conflict of interest with no account of what the conflict costs the actor. No generic praise.

#### Text
content::
{>>{"author":"Elias's AI","timestamp":1788016535133}@@Native reproduction of XLab's Actor Map Workshop from src/lib/verification/data/actor-workshop.ts and actor-map.ts (roster, recall target, core question, Baker rings and placement key, map finding, second-order question, closing questions and marking key). Note for Elias: in XLab's current repo, scoping-actors.mdx is cut to three paragraphs and the actor-workshop widget is no longer registered; the five tables above and the workshop are documented as XLab's own in docs/verification/module-1-log.md, so they are kept. XLab's ring map graphic (concentric SVG) is not reproduced; the placements are.<<}
The edge exercise built on this board is the next lens: [[../Lenses/XLab Verification - v-actor-edges|1.2.2 Who can prove what]].++}

#### Text
content::
\### Notes and sources

The draft agreement this section reads its cast out of: Scher, Abecassis, Barnett & Abeyta, [“An International Agreement to Prevent the Premature Creation of Artificial Superintelligence”](https://arxiv.org/abs/2511.10783) (2025), Appendix A — the treaty 1.1 dissects.

[California SB 53](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB53), the Transparency in Frontier Artificial Intelligence Act, signed September 29, 2025; core duties effective January 1, 2026 ([Future of Privacy Forum](https://fpf.org/blog/californias-sb-53-the-first-frontier-ai-law-explained/) and [White & Case](https://www.whitecase.com/insight-alert/california-enacts-landmark-ai-transparency-law-transparency-frontier-artificial) summaries).

[EU AI Act, Article 51](https://artificialintelligenceact.eu/article/51/): presumption of systemic risk above 10^25 training FLOP.

[UN Independent International Scientific Panel on AI](https://www.un.org/independent-international-scientific-panel-ai/en) (est. 2025; first meeting March 2026); [Global Dialogue on AI Governance](https://news.un.org/en/story/2026/07/1167873), Geneva, July 2026.

[NIST Center for AI Standards and Innovation (CAISI)](https://www.nist.gov/caisi), formerly the US AI Safety Institute; pre-deployment testing agreements with frontier developers.

Supply-chain structure: Sastry, Heim, Belfield et al., [“Computing Power and the Governance of Artificial Intelligence”](https://arxiv.org/abs/2402.08797) (2024) — ASML at 100% of EUV lithography, TSMC at ~90% of sub-7nm logic (2022 data), and “several critical steps … have fewer than three suppliers”; CSET, [“The Semiconductor Supply Chain”](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/) (2021) — the stage-by-stage picture, including that assembly and test has the lowest barriers to entry. High-bandwidth memory is inside the export-control perimeter: the US controls were “expanded again, this time affecting all chips using advanced high-bandwidth memory” — Fist, Burga & Chilukuri, [“Technology to Secure the AI Chip Supply Chain”](https://www.cnas.org/publications/reports/technology-to-secure-the-ai-chip-supply-chain-a-primer) (CNAS, 2024). Incentive vocabulary and role taxonomy: this module’s introduction.

**Currency.** The concentration figures above are 2021–2023 data reported in 2021 and 2024 sources. Shares move; the structure — one EUV maker, one dominant leading-edge fab, a handful of clouds — has not. Re-verify a number before quoting it.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-actors)*
