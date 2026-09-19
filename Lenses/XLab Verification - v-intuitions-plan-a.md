---
id: 'b70db51f-a981-4675-93c9-ac224ccfae3e'
title: "Read Plan A's Verification Plan"
tldr: "Read the mechanisms and implementation sequence before judging Plan A's verification regime."
summary_for_tutor: "Read the mechanisms and implementation sequence before judging Plan A's verification regime. Preserve the source framing and respond to the learner's reasoning. Four charts from the source supplement are placed in the reading, each directly under the article text it belongs to: a treemap of where the world's AI compute sits on January 1, 2029, after the three tables of size bands, other compute locations and region totals; the 2029 to 2031 deal implementation timeline, after the eleven-bullet timeline list; the assurance curves for N_ver = 100, 10K and 10M audited packets, after the collapsed box on verification approaches whose table it makes interactive; and the rogue internal deployment detection chart, after the collapsed workload verification box whose table it makes interactive. The captions and tables stay in the article as the text fallback, so every number is on the page in words; the charts add the readouts, the region and series filters and the year and packet size sliders that the static tables cannot give. The two interactive charts that sit under a collapsed box each have a one-line lead-in on the page naming them."
duration_minutes: 45
tags: [wip]
add_to_ai_context:
  - "[[../articles/dean-ai-2040-verification-plan]]"
---
#### Text
content::
Below are three excerpts from [AI 2040: Verification Plan](https://ai-2040.com/supplements/verification-plan), the verification supplement to Plan A: the plan's summary, the concrete inference-only retrofit, and the 2029–2030 implementation sequence, including third-party participation. The main Plan A scenario is not part of this reading.

- **Option A:** Read these sections closely before writing your essay.
- **Option B:** Skim these sections, then read the Plan S discussion and FAQ in Option B.

#### Article
source:: [[../articles/dean-ai-2040-verification-plan]]
from:: ## Summary of the Plan
to:: | Rest of world | 39M | 14% |

#### Widget
source:: [[../widgets/ai-2040-compute-locations]]

#### Article
from:: This is what we think implementing the deal would look like in 2029 in our scenario, with an inference-only retrofit of all the medium and large AI datacenters (>10K H100e, or approx. >$100M), and this being enough to cover ~99% of world AI-relevant compute. Then keeping tabs on the rest of the smaller clusters and taking measures to avoid them being possibly used in a covert project. We are not confident in the modelling of this [concentration in datacenter sizes](https://ai-2040.com/supplements/compute-supplement#14-datacenter-sizes), so the exact cutoffs and interventions may need to be different.
to:: **Phase 3. Improve robustness.** Over time the US and China improve the stability and durability of the verification regime, especially through hardware security, verification robustness, and more.

#### Article
from:: :::callout {title="Concrete inference-only retrofitting proposal." tone="neutral" collapse="open"}
to:: 1.  Removing major scale out interconnect and e.g., installing some simple sensors and other physical security mechanisms might also suffice for verifying inference-only for an initial phase of a deal (e.g., 1 year) until higher assurance measures are ready for larger amounts of compute and higher stakes workloads.
:::

#### Article
from:: ## 2029-2030: Deal Implementation
to:: - **Jan 2031:** mature safety-case-based R&D rules in place

#### Widget
source:: [[../widgets/ai-2040-deal-timeline]]

#### Article
from:: ### Jan 2029: Mutual Chip Declaration and Inspection
to:: What verification solution to choose will likely have complex tradeoffs between these metrics. Our current best guess is to primarily rely on on-path information collection (i.e., network taps) and then partial recomputation as the verification algorithm, since it seems most likely to be robustly scalable to extremely high coverage and confidence.
:::

#### Text
content::
**Assurance curves for three verification budgets**

The chart below is the interactive form of the table in the box above: how much confidence each audit budget buys at a given level of coverage.

#### Widget
source:: [[../widgets/ai-2040-assurance-curve]]

#### Article
from:: :::callout {title="Key ingredients to any verification approach that we will assume are pursued." tone="neutral" collapse="closed"}
to:: The concrete regime we imagine for the first few years of the deal is to still use network taps for evidence collection, and partial recomputation of randomly selected reproducible packets to verify correctness. The same high level approach as inference-only, with smaller and smaller packet sizes over time by moving the network taps to lower levels of the backend network.
:::

#### Text
content::
**Catching a rogue internal deployment**

The chart below is the interactive form of the table in the box above: the chance that a 1% recomputation budget catches a rogue deployment, for any year, packet size and rogue size.

#### Widget
source:: [[../widgets/ai-2040-rogue-detection]]

#### Article
from:: ![](https://ai-2040.com/verification-plan/image8.png)
to:: Also by the end of 2030, the US and China have set up hardened cold storage facilities where they allow inspectors to verify each other’s stash of AI chips, sized to be bigger than any plausible covert projects (a 5M H100e US bank and a 500K H100e China bank, per our [deal decline supplement](https://ai-2040.com/supplements/deal-decline#preparing-stockpiles-to-align-incentives)), and of relative size to each other similar to pre-deal status quo. These are in places that either side can easily defend. These locations will also be home to verified model weights stashes, so that models that the US and China agree would be positive sum to approve for use in the case of deal dissolution (e.g., models that would be very helpful for safety research and have strong safety cases). Around 2033 there is a model around the automated coder capability milestone that gets approved for the weights stash, and then in 2037 there is a near-frontier (top expert AI) model approved for the cold weights storage.

#### Text
content::
Continue with [[../Lenses/XLab Verification - v-intuitions-a1|Option A: Stress-test Plan A]] or [[../Lenses/XLab Verification - v-intuitions-b1|Option B: Compare Plan A and Plan S]].
