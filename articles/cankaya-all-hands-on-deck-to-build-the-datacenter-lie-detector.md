---
title: "All hands on deck to build the datacenter lie detector"
author:
  - "Naci Cankaya"
source_url: "https://www.lesswrong.com/posts/PZikD6PxpEqHF4qbF/all-hands-on-deck-to-build-the-datacenter-lie-detector"
published: 2026-02-19
created: 2026-07-28
accessed: 2026-07-28
description: "Fieldbuilding for AI verification is beginning. A consensus for what to build, what key problems to solve, and who to get in on the problem is emergi…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Fieldbuilding for AI verification is beginning. A consensus for what to build, what key problems to solve, and who to get in on the problem is emerging. Last week, ~40 people in total, including independent researchers and representatives from various companies, think tanks, academic institutions and non-profit organisations met for multiple days to share ideas, identify challenges, and create actionable roadmaps for preparing verification mechanisms for future international AI agreements. The workshop was initiated by the [Future of Life Institute](https://futureoflife.org/) and included the following participants

-   Yannik Mühlhäuser and James Petrie; [Future of Life Institute](https://futureoflife.org/)
-   Quinn Dougherty; [Forall R&D](https://for-all.dev/)
-   Naci Cankaya; [MATS Research](https://www.matsprogram.org/)
-   Gabriel Kulp; (attending in personal capacity)
-   Jonathan Happel, Jackson Dean; [TamperSec](https://tampersec.com/)
-   Benjamin Hodgkiss; (attending in a personal capacity)
-   Romeo Dean, [AI Futures Project](https://ai-futures.org/)

among many others.

# **Why this needs to happen now**

The [urgency](https://www.nytimes.com/2026/02/12/opinion/artificial-intelligence-anthropic-amodei.html) and neglectedness of this challenge is underscored by recent [comments by frontier AI company leadership](https://x.com/emilychangtv/status/2013726877706313798?s=20) and government representatives:

Dario Amodei, CEO of Anthropic:

[_“The only world in which I can see full restraint is one in which some truly reliable verification is possible.”_](https://www.nytimes.com/2026/02/12/opinion/artificial-intelligence-anthropic-amodei.html)

Ding Xuexiang, Chinese Vice Premier, speaking about AI at Davos in January 2025:

[_“If countries are left to descend into a disorderly competition, it would turn into a ‘gray rhino’ right in front of us.”_](https://www.fmprc.gov.cn/eng/xw/zyxw/202501/t20250122_11543099.html) _(a visible but ignored risk with serious consequences.)_

[_“It is like driving a car on the expressway. The driver would not feel safe to step on the gas pedal if he is not sure the brake is functional.”_](https://www.fmprc.gov.cn/eng/xw/zyxw/202501/t20250122_11543099.html)

JD Vance, Vice President of the United States of America:[1](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-1-188480874)

[_“Part of this arms race component is if we take a pause, does the People’s Republic of China not take a pause? And then we find ourselves all enslaved to P.R.C.-mediated A.I.?”_](https://www.nytimes.com/2025/05/21/opinion/jd-vance-pope-trump-immigration.html)

Beyond international coordination, there are [further use cases](https://ifp.org/faster-ai-diffusion-through-hardware-based-verification/) for verification of what AI compute is used for: Safeguards against authoritarian misuse of AI (e.g., identifying protestors or political opponents), enabling secure use of [foreign compute in domestic critical infrastructure](https://theoptionspace.substack.com/p/lessons-from-source-code-inspection) and more.

**It needs to become possible to detect dishonesty about AI development and use, from the outside, without needing to leak sensitive data.**[2](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-2-188480874) **The stakes continue to rise.**

# **An orphaned problem**

It is possible for an important problem to be noticed, but unaddressed by a large number of influential people who would be able to make a solution happen. This is what the field of AI verification has been lacking so far: people meeting, and agreeing on what the next steps are, what challenges deserve the most attention, and who does what.[3](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-3-188480874)

# **The workshop**

Over two days in downtown Berkeley, the participants presented their background and relevant work so far, shared insights, and discussed strategies and roadmaps for moving the technology, commercial deployment and the international diplomatic and scientific “bridges” forward.

-   While the specifics are TBA, consensus on a **minimum viable product** was (mostly) found, and publications about the overall technical architecture and challenges are being finalized. When they are published, followers of my blog can expect me to write about them shortly after.
    -   On a high level: Prover declares workloads, Verifier checks them using off-chip, retrofittable devices placed in the datacenter plus an egress-limited verification cluster
    -   The approach is designed to work with great power adversaries without trusting either side’s chips.
    -   More details to come soon
-   Work on **network taps** more detailed and technical than [my previous post](https://nacicankaya.substack.com/p/catching-misreporting-about-ml-hardware-bd2) has been shared and internally discussed. I am co-writing this piece and my team plans to publish it this month. We found potential cruxes with Security Level 5 requirements around encrypted network traffic and discussed workarounds.
-   Interest in building and testing **sub-scale demonstrations** of network taps + secure verification clusters rose among the participants with a more technical background, and roadmaps are currently being decided. A key driver for the increased interest in engineering work is the viability of small-scale demos using off-the-shelf components that can still be close to representative for those needed for treaty verification.[4](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-4-188480874) To name one example for a question discussed during the workshop, the components needed for representative demos of network taps may be either smartNICs or custom FPGAs, and there are tradeoffs between ease of use in experiments (smartNICs) and security properties (FPGAs).
-   A key emphasis has also been on the **security** aspect of mutual monitoring and verification: It is easy to underestimate the cyber-offense capabilities of great powers, and we discussed the concrete ways in which any verification infrastructure must avoid introducing additional attack surfaces in technical detail. A key challenge lies in the process of transferring confidential information into secure verification facilities, as well as the physical security required to prevent physical access to sensitive components, both on the prover’s and the verifier’s side.
-   Regarding **fieldbuilding**: The field is still tiny and bottlenecked by talent and funding. In a breakout session, we brainstormed from where –and how– to get people engaged. One connected question was when and how to include Chinese researchers and AI safety actors in verification work. We found that the AI safety community in mainland China is nascent, but emerging, while a _treaty-oriented_ AI verification community is essentially nonexistent. The perception of AI as a potentially catastrophic risk has not yet reached the Overton window of the wider public debate, as it seems from the outside, though exceptions exist (see [Ding Xuexiang](https://www.fmprc.gov.cn/eng/xw/zyxw/202501/t20250122_11543099.html) quoted above). Frontier companies in China are mostly not communicating serious concerns about AI risks, though we are uncertain to what degree this is due to differences in views vs. restraint in their public communication.
-   We are under no illusions regarding the tense **geopolitics** around AI. We agree, however, that the “this is an inevitable arms race” framing is –to a significant degree– informed by the (non-)availability of robust verification mechanisms (see [Amodei](https://www.nytimes.com/2026/02/12/opinion/artificial-intelligence-anthropic-amodei.html) quoted above). There was no clear consensus regarding to what degree the availability of a battle-tested, deployment-ready verification infrastructure would change the public debate and decision-making of geopolitical leaders.
    -   **In favour**: The global security dilemma is the most commonly used argument used by those AI accelerationists who consider it reckless, and verification would address this dilemma directly.
    -   **Against**: Nations currently seem to balance the risk/reward calculation in favour of AI acceleration, and it is not expected that the possibility of verification alone tips the scale. A lot of this will depend on a complicated, hard-to-predict interplay of technology progress, societal impact, scientific communication, regulatory capture, and many other factors.
    -   However, in a world where leaders come to a consensus that AI poses extreme risks, and time is scarce to act and get AI under control, the necessary verification R&D already being done in advance could make all the difference: Defusing an otherwise uncontrolled arms race towards a possible loss of control and/or enormous power concentration, and/or great power armed conflict.

# **Not nearly enough**

If I gave the impression that the problem is getting adequate attention now, it is not. “All hands on deck” may be the title of this post, and the interest in verification work is growing, but the development of technical demos and a proper research community is still in its infant stages and bottlenecked by talent, funding, and coordination capacity.

This is a field where a single person with the right skills can move the needle. We need:

**Engineers and scientists**: FPGA engineers, datacenter networking engineers, silicon photonics experts, analog/mixed-signal engineers, cryptographers, formal verification researchers, ML systems engineers, cybersecurity and hardware security specialists, high-frequency trading hardware specialists and independent hackers who love to build and break things.

**Entrepreneurs and founders**: Enterprise sales people, venture capitalists, public grantmakers and incubators, and established companies opening up new product lines. This is in order to prepare the supply chains and business ecosystems and precedents needed to scale up deployment. Verification can have purely commercial use cases, for example for [demonstrating faithful genAI inference.](https://www.kimi.com/blog/kimi-vendor-verifier.html)[5](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-5-188480874)

**Policy and diplomacy**: Technology policy researchers, arms control and treaty verification veterans, diplomats, and people with connections to —or expertise— in the Chinese AI ecosystem.

**Funding and operations**: Funders, fundraisers, and program managers who can help coordinate a distributed research effort.

If any of this describes you, or if you bring adjacent skills and learn fast, reach out.

naci.c@protonmail.com

Let us use what (perhaps little) time we have left for creating better consensus on AI risks, for building a datacenter lie detector, for preventing and finding hidden AI projects, and for defeating [Moloch](https://www.slatestarcodexabridged.com/Meditations-On-Moloch).

Join us.

[1](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-anchor-1-188480874) Answer to the question: “Do you think that the U.S. government is capable in a scenario — not like the ultimate Skynet scenario — but just a scenario where A.I. seems to be getting out of control in some way, of taking a pause?”

[2](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-anchor-2-188480874) In plain English: We need ways for an inspector to walk into a datacenter in Shenzhen or Tennessee and cryptographically prove what inference and training happened, without increasing the risk of exposing IP such as model weights or training data.

[3](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-anchor-3-188480874) For more details on this, I recommend the excellent post [“_There should be ‘general managers’ for more of the world’s important problems”_](https://nanransohoff.substack.com/p/there-should-be-general-managers)_._

[4](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-anchor-4-188480874) See my [previous post](https://open.substack.com/pub/nacicankaya/p/catching-misreporting-about-ml-hardware-bd2?utm_campaign=post-expanded-share&utm_medium=web) on a “border patrol device” for AI datacenters.

[5](https://nacicankaya.substack.com/p/all-hands-on-deck-to-build-the-datacenter#footnote-anchor-5-188480874) While Kimi’s Vendor Verifier may give the impression that this is a solved problem, it only works for open weights models to run locally for comparison. Verifying inference of proprietary models would require third-party-attested, or hardware-attested deployment.
