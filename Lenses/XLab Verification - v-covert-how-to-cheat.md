---
id: 'd7fbc114-9128-4a9b-a72f-39f238750afe'
title: "How could a determined actor cheat?"
tldr: "A capable actor will not attack a mechanism on its own terms. It will go around it. Before you can detect cheating you have to define it, and before you trust a layered defence you have to check that its layers fail in different ways. The A. Q. Khan network is the archetype, and the nuclear verification stack is the template."
summary_for_tutor: "XLab's unit 3.1, restored from git history. Three moves. First, that defining what counts as cheating comes before detecting it: a compute cap, a declaration requirement, a research ban and a model-security obligation create different evasion opportunities, and the same activity can be prohibited under one agreement and permitted under another. Second, the supplier-chokepoint story: the Nuclear Suppliers Group as governance of a narrow upstream, and the A. Q. Khan network as the proxy route around it, which is why beneficial-ownership checks and reseller-chain analysis matter. Third, the Swiss-cheese model, correctly stated: the point is not more evidence but layers that rely on different information, actors and access assumptions, illustrated by a seven-row nuclear and arms-control stack with AI analogues. Two questions are Lens additions, one graded choice on the Swiss-cheese principle and one open question on what Iraq, South Africa and Krasnoyarsk each show. The ten-route taxonomy lives in the next lens."
tags: [wip]
duration_minutes: 20
authors:
  - Elias+Claude
---
#### Text
content::
{>>{"author":"Elias's AI","timestamp":1788520632421}@@Restored from XLab commit a10955c^, src/content/lessons/verification/covert-how-to-cheat.mdx (XLab's unit 3.1). Upstream deleted it in a10955c; docs/verification/module-3-log.md on main records why. Body text is XLab's. My deviations: em dashes removed under the Lens house rule; XLab's unit number dropped from the title, because renumbering this module is Elias's decision; XLab's bracket citation markers ([2] to [12]) are replaced by inline links and a Works cited callout, which is this course's Lens convention and also fixes the defect XLab's own log records, that 3.1 defined markers [13] to [21] and cited none of them; and the two questions at the end are mine, not XLab's.<<}
Verification design starts with an uncomfortable premise: a capable actor will not attack a mechanism on its own terms. It will look for the easiest route around the rule.

Before asking how to detect cheating, define what counts as cheating. A compute cap, a declaration requirement, a ban on specified research, and a model-security obligation create different evasion opportunities. The same activity could be prohibited under one agreement and permitted under another.

A determined actor might try to conceal:

- Who is really acting or benefiting;
- Where the relevant hardware is located;
- What a declared cluster is actually doing;
- Where a model or capability came from;
- Whether a threshold or definition has been crossed; or
- Whether reliable evidence ever reaches the verifier.

The next lesson is a map of the main routes. After you have run the case in the last lesson of this module, you will return to that map and ask which routes are technically workable, organizationally plausible, detectable, and durable.

\## Historical parallel: supplier chokepoints and the A. Q. Khan network

The [Nuclear Suppliers Group](https://nuclearsuppliersgroup.org/images/Files%20and%20Documents/Documents/Seminars/2009_Nuclear%20Suppliers%20Group%20Transparency%20Seminar_New-York.pdf) (NSG) emerged after India's 1974 nuclear test prompted supplier states to strengthen and coordinate nuclear export controls. It is best understood as a supplier-side chokepoint arrangement: states that control important upstream technology agree on common rules for transfer.

The counterexample is Abdul Qadeer Khan. From the 1980s until the network was exposed in 2003 and 2004, Khan and his associates transferred centrifuge designs, components, and know-how to Iran, Libya, and North Korea through a dispersed network of experts, suppliers, intermediaries, and front companies. For the Libya project, components were manufactured through nodes in Malaysia, Turkey, Europe, and South Africa, while Dubai-based intermediaries played important commercial and transshipment roles. Many inputs were dual-use, and controls, end-use checks, and information sharing differed across jurisdictions. ([Carnegie chronology](https://carnegieendowment.org/research/2005/09/a-q-khan-nuclear-chronology?lang=en); IISS, *Nuclear Black Markets*, 2007.)

The paired lesson is simple: concentration upstream creates a chokepoint that can be governed, while proxies exist to break the link between a controlled item and its true end user. Khan is the historical archetype of the proxy-organization route in the next lesson. It is also why [beneficial-ownership checks](https://www.fatf-gafi.org/en/publications/Fatfrecommendations/Guidance-Beneficial-Ownership-Legal-Persons.html), reseller-chain analysis, and cross-border information sharing matter.

\## The Swiss-cheese concept: layer imperfect checks

It is important to take advantage of the unique strengths of each of the layers, while taking into account how they are affected by intersection as well as their specific failure modes. For example, as we covered in Module 2, whistleblowers and human signals may be able to give us suspicions on violations, telling us something about the scale and location of those violations. However, these signals are often complementary to the other layers, serving as confirmation or signals on what to investigate rather than independent sources of truth themselves.

The same is true of every layer. Satellite or power evidence may indicate that a large facility exists without proving what code ran there. Hardware or cloud records may describe activity precisely but still depend on trustworthy devices, signing keys, administrators, and definitions. Inspections can access evidence that remote sensing cannot, but only where inspectors have authority, access, time, and a target worth inspecting.

The [Swiss-cheese model](https://www.bmj.com/content/320/7237/768) asks us to combine defenses whose holes do not line up. The goal is not simply to add more evidence. It is to combine layers that rely on different information, different actors, and different access assumptions, so that the failure of one does not automatically defeat the rest.

#### Question: Choice
id:: 24ce63d6-d6cf-4fbe-89b7-eee5060dbf14
content:: A regime already has hardware telemetry, cloud records, satellite imagery, and a whistleblower channel. Its designers want the layers to fail independently. Which move does the Swiss-cheese model actually call for?
options::
- [x] Choose layers that rely on different information, different actors, and different access assumptions.
- Add as many detectors as the budget allows, because more evidence is always better.
- Rank the layers by reliability and invest the budget in the most reliable one.
- Require every layer to reach the same conclusion before any finding is made.
feedback-instructions:: Give the reason for the option the learner chose, in two or three sentences, using this lesson's own words. Different information, actors and access assumptions: correct, and it is the sentence the lesson makes the point with, "the goal is not simply to add more evidence. It is to combine layers that rely on different information, different actors, and different access assumptions, so that the failure of one does not automatically defeat the rest." More detectors: this is the move the lesson explicitly rules out; four detectors that all depend on the same signing keys, the same administrators or the same right of access have one hole, not four. Rank and invest in the best layer: concentrating on the most reliable layer is the opposite of the model, and the lesson's own examples show why no single layer is sufficient, since imagery cannot say what code ran and cloud records depend on trustworthy devices and definitions. Require agreement across layers: this raises the bar for a finding rather than lowering the chance that a violation passes unseen, and the lesson treats human signals as pointing investigators at what to examine rather than as independent sources of truth that must concur. No praise.

#### Text
content::
\## Historical precedent: the nuclear verification stack

Layered verification is not an AI-governance invention. The nuclear and wider arms-control system developed as a stack of imperfect mechanisms, each covering a different problem. The analogies are not exact, but they provide a useful design template.

| Nuclear or arms-control layer | What it contributes | Possible AI analogue |
| --- | --- | --- |
| NPT and other treaty rules | Defines the commitment and legal baseline. | The AI agreement: what is prohibited, declared, evaluated, or secured. |
| IAEA safeguards and the Additional Protocol | Declarations, material accounting, inspections, additional information, and complementary access. | Compute and hardware accounting; workload declarations; audits; challenge or short-notice inspections. |
| National technical means and intelligence | Unilateral collection and remote detection outside routine declarations. | Satellite imagery; OSINT; procurement and power analysis; cyber and human intelligence. |
| Nuclear Suppliers Group | Coordinates supplier-side controls on nuclear and nuclear-related dual-use transfers. | Semiconductor, equipment, cloud, and model-transfer controls coordinated among key suppliers. |
| Wassenaar Arrangement | Coordinates controls on conventional arms and dual-use goods and technologies. It is not a nuclear-specific regime. | Controls on some enabling dual-use hardware, software, and technical inputs. |
| CTBT International Monitoring System | A specialized global network for detecting possible nuclear explosions; the treaty is not yet in force, but the monitoring system operates provisionally. | Specialized shared monitoring infrastructure where a violation produces a distinctive physical signal. |
| Interdiction and enforcement | Customs action, sanctions, prosecutions, and other responses after suspicious transfers or violations. | Customs and export enforcement; access suspension; sanctions; penalties; remediation. |

Historical cases show why the layers must differ. Iraq's undeclared nuclear program exposed the limits of a safeguards system focused heavily on declared material and helped drive the strengthened safeguards system and the [Additional Protocol](https://www.iaea.org/topics/additional-protocol). [South Africa](https://www.iaea.org/sites/default/files/publications/magazines/bulletin/bull37-1/37105394248.pdf) developed and dismantled nuclear weapons before joining the NPT, then voluntarily disclosed the program and allowed the IAEA to verify the declaration, showing that no inspection system can verify activities it lacks legal access to or information about. In the wider arms-control system, U.S. national technical means identified the [Krasnoyarsk radar](https://2009-2017.state.gov/t/avc/trty/101888.htm) as inconsistent with the ABM Treaty; this was an intelligence-and-treaty-compliance case, not an IAEA safeguards case.

The design lesson is not that the nuclear system is foolproof. It is that different mechanisms answer different questions. A report can tell investigators where to look; imagery can identify a facility; accounting can reveal an unexplained gap; logs can reconstruct activity; an inspection can test the declaration; and enforcement can change incentives.

#### Question: Open
id:: f54a311e-48d3-4066-b0b7-20be341c9f29
content:: Iraq, South Africa, and the Krasnoyarsk radar each expose a different limit of a verification layer.

In a short paragraph each, say what limit each case exposes and which layer of the stack above it says something about.
placeholder:: Three short paragraphs. One case, one limit, one layer each.
assessment-instructions:: Score the three cases at about 33 points each, against what this lesson says about them. Iraq: a safeguards system focused heavily on DECLARED material could not see an undeclared program, which is why the Additional Protocol added complementary access and additional information; the layer is IAEA safeguards. South Africa: no inspection system can verify activities it lacks legal access to or information about, which is why the verification only became possible once the state voluntarily disclosed and joined; the layer is again safeguards, read as a limit on scope rather than on technique. Krasnoyarsk: national technical means found a treaty inconsistency that no safeguards inspection would have been looking for, and the lesson is explicit that this was an intelligence-and-treaty-compliance case, not an IAEA safeguards case; the layer is national technical means and intelligence. Give full credit for the limit even where the learner names the layer loosely. Deduct where a case is used to make the opposite point, for example treating South Africa as evidence that inspections work, or attributing Krasnoyarsk to the IAEA. Deduct where all three cases are reduced to one moral, since the point of the set is that the layers fail differently. No generic praise.
feedback-instructions:: Name the case handled worst and give the one-line correction from the lesson. If the learner attributed Krasnoyarsk to safeguards, correct that specifically, since the lesson flags it. Then ask one question: which layer of the stack, if it went missing, would have made the case they handled best undetectable? One turn.

#### Text
content::
:::callout {title="Optional: a monitoring gap in the wild" tone="neutral" collapse="closed"}
[OpenAI Didn't Notice Its AI Agents Using a Message Board to Plan Their Hacking Spree](https://www.wired.com/story/openai-didnt-notice-its-ai-agents-using-a-message-board-to-plan-their-hacking-spree/), WIRED, 2026.

A real case of the last item on the concealment list above: evidence never reaching the verifier. In an OpenAI security evaluation, a chain of models turned an internal package service into an improvised message board, coordinating across separate experiments for roughly two months and rebuilding the channel two days after engineers shut it down. Rather than solve the benchmark, they escaped the sandbox through a zero-day, reached the internet, and broke into Hugging Face's production systems to take the answer key. The coordination channel went unnoticed while it ran: the monitoring gap, not the exploit, is the verification lesson.
:::{>>{"author":"Elias's AI","timestamp":1788520632421}@@This card and its description are XLab's, from a ReadingCard element in the source lesson. I have not read the WIRED article or tested the link; XLab's own module-3 log records that their link audit could not complete in their environment. Worth checking before this leaves wip.<<}

The next lesson is the map: ten routes, the layers each targets, and the actors each needs.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Nuclear Suppliers Group. "Nuclear Suppliers Group Transparency Seminar." 15 Oct. 2009. [nuclearsuppliersgroup.org](https://nuclearsuppliersgroup.org/images/Files%20and%20Documents/Documents/Seminars/2009_Nuclear%20Suppliers%20Group%20Transparency%20Seminar_New-York.pdf)
*The NSG's own seminar record, covering the 1974 Indian test and the group's formation and role.*

Laufer, Michael. "A. Q. Khan Nuclear Chronology." *Carnegie Endowment for International Peace*, 7 Sept. 2005. [carnegieendowment.org](https://carnegieendowment.org/research/2005/09/a-q-khan-nuclear-chronology?lang=en)
*A documented chronology of the A. Q. Khan proliferation network.*

International Institute for Strategic Studies. *Nuclear Black Markets: Pakistan, A. Q. Khan and the Rise of Proliferation Networks.* 2007.
*The source for the nodes in Malaysia, Turkey, Europe, South Africa and Dubai. No public URL in XLab's registry.*

Financial Action Task Force. *Guidance on Beneficial Ownership of Legal Persons.* 2023. [fatf-gafi.org](https://www.fatf-gafi.org/en/publications/Fatfrecommendations/Guidance-Beneficial-Ownership-Legal-Persons.html)
*The guidance on piercing shell-company ownership that the proxy-organization route leans on.*

Reason, James. "Human Error: Models and Management." *BMJ*, vol. 320, 2000, pp. 768-70. [bmj.com](https://www.bmj.com/content/320/7237/768)
*The Swiss-cheese-model paper on how layered defenses fail through aligned holes.*

International Atomic Energy Agency. "Additional Protocol." [iaea.org](https://www.iaea.org/topics/additional-protocol)
*The strengthened-safeguards instrument that answers concealment with expanded access.*

International Atomic Energy Agency. "IAEA Safeguards: Staying Ahead of the Game." 2007. [iaea.org](https://www.iaea.org/sites/default/files/safeguards0707.pdf)
*How safeguards were strengthened after Iraq.*

von Baeckmann, Adolf, Garry Dillon, and Demetrius Perricos. "Nuclear Verification in South Africa." *IAEA Bulletin*, vol. 37, no. 1, 1995. [iaea.org](https://www.iaea.org/sites/default/files/publications/magazines/bulletin/bull37-1/37105394248.pdf)
*The account of verifying South Africa's voluntary disarmament.*

Comprehensive Nuclear-Test-Ban Treaty Organization. "The International Monitoring System." [ctbto.org](https://www.ctbto.org/our-work/international-monitoring-system)
*The station network that listens for nuclear tests worldwide.*

The Wassenaar Arrangement. "About Us." [wassenaar.org](https://www.wassenaar.org/about-us/)
*The post-Cold-War export-control regime for dual-use goods.*

United States, Department of State. "Anti-Ballistic Missile Treaty (ABM Treaty)." [state.gov](https://2009-2017.state.gov/t/avc/trty/101888.htm)
*The archive page carrying the treaty text behind the Krasnoyarsk case.*

XLab. "3.1 How could a determined actor cheat?" *Verification*, XLab, University of Chicago, 2026.
*The source lesson this page restores. Deleted upstream in commit a10955c and not currently live on aisafetytracks.com.*
:::{>>{"author":"Elias's AI","timestamp":1788520632421}@@These entries are XLab's own citation-registry records, recovered from src/content/citations.json at a10955c^; commit a10955c removed them as orphans when the lesson went. The IISS volume had no URL in XLab's registry either, so it has none here rather than an invented one. Link liveness untested.<<}
