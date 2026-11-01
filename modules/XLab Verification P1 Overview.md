---
id: 'b705dd43-bbb7-4ca2-a869-b778dbfdbd08'
slug: xlab-verification-p1-overview
title: "Course Overview"
tags: [wip]
---

# Lens: About This Course
id:: ad19bb9d-1f42-48c2-ae70-2fe8636035a0
tldr:: Two rivals sign a deal to slow down AI. Neither trusts the other. This course is about how each could still check that the other kept its word, and it takes you as far as the first evidence stream: hardware.
summary_for_tutor:: Orientation page before Unit 1. Learner reads what the course asks of them in each unit, that this is the first of two courses on the same curriculum with a separate capstone course after them, and that the course is based on XLab's open-source verification curriculum. Do not teach later content in detail; if asked, point to the unit that covers it, or say that cloud, intelligence, human mechanisms and covert development belong to the second course. The text between the two dividers in the first section is the source curriculum's welcome lesson, adapted: it makes the case for verification between rivals and ends on the field being young enough for the learner to help build. Preserve its framing.
reading_minutes:: 6
tutor_minutes:: 0
#### Text
content::
\## What this course is about

How could parties that do not trust one another verify meaningful limits on advanced AI development? This Lens Academy course works through that question, from motivation and policy scope to the first concrete evidence stream.{--{"author":"Andreas's AI","timestamp":1793505026429}@@ It is based on [XLab's](https://xrisk.uchicago.edu/) open-source verification curriculum. To send feedback directly to XLab, use [their feedback form](https://forms.gle/KkWcHkKh87pygDzw9).--}

---

AI is already a transformative technology. AI systems can accelerate scientific research, write and audit software, and discover mathematical breakthroughs, just to name a few: results that would have sounded impossible just a decade ago.

But the same capabilities that can build secure computer systems can exploit them. The algorithm that revolutionizes cellular breakthroughs can also build a biological weapon capable of devastating millions, if not billions. As of mid-2026, we have seen AI demonstrate the capabilities to [hack multimillion-dollar companies](https://www.wired.com/story/openai-didnt-notice-its-ai-agents-using-a-message-board-to-plan-their-hacking-spree/), [create new viruses](https://www.bbc.com/news/articles/c5y3j3ngevmo), and play major roles in [military](https://www.wsj.com/livecoverage/iran-strikes-2026/card/u-s-strikes-in-middle-east-use-anthropic-hours-after-trump-ban-ozNO0iClZpfpL7K7ElJ2) and national security. With unprecedented benefit comes unprecedented risk.

Many of these risks concern humanity as a whole, regardless of politics, beliefs, or nationality. Cyberattacks and bioweapon blueprints can easily cross borders. No country can fully govern this dangerous and rapidly improving technology through domestic policy alone. This creates a strong case for international coordination.

The United States and China are the two dominant global players in the development of advanced AI. But they are also rivals. Each has reasons to worry that cooperation could constrain it while leaving the other side free to advance. So, even if the U.S. and China individually agreed on the dangerous capabilities of AI, and therefore wanted to pursue some sort of agreement to slow or stop its development, none of it matters if you couldn’t reliably enforce that agreement.

This course tackles that problem through AI verification: the set of mechanisms necessary to enforce an agreement to pause the development of advanced AI between multiple distrustful parties.

We can start by drawing parallels with nuclear nonproliferation. Nuclear rivals, like AI giants, did not trust one another, agree on the future of the international order, or stop pursuing strategic advantage. They nevertheless developed safeguards, monitoring systems, data exchanges, and inspections that made some limited forms of cooperation possible. Some of its most consequential institutions were created precisely because states remained competitors. It allowed states to make particular commitments more credible without requiring general political trust.

But even with nuclear precedents, AI verification is uniquely difficult for several reasons, including:

- Algorithms are replicable and can easily cross state boundaries, unlike bombs sitting in silos.
- AI is advancing unimaginably fast. We don’t have enough time to develop the most ideal verification technologies before it’s too late.

Verification is currently a pre-paradigmatic field: there is no correct answer. Some mechanisms covered here are established technologies or institutional practices; others are emerging proposals with substantial unresolved questions. That uncertainty creates room for important work. The field still needs people who can expose weak assumptions, connect technical mechanisms to political realities, and develop better approaches.

The people who define the central concepts of AI verification and build its institutions may be some of the people encountering it for the first time now.

One of them could be you.

{++{"author":"Andreas's AI","timestamp":1793505016164}@@---

This course is based on [XLab's](https://xrisk.uchicago.edu/) open-source verification curriculum. To send feedback directly to XLab, use [their feedback form](https://forms.gle/KkWcHkKh87pygDzw9).

++}\## How the course runs

Five units. In each unit you work through the material on your own, then meet your group to discuss the arguments the readings and exercises leave open.

\## The five units

:::callout {title="Unit 1: Why Verification" tone="blue"}
Why the problem exists at all. Arms-race incentives that individual state preferences cannot overcome, why a prevented catastrophe looks like nothing happened, what makes a theory of change worth acting on, and then the first real workout: stress-test AI 2040's Plan A, the most detailed public proposal for a verified slowdown, and write your verdict.
:::

:::callout {title="Unit 2: Precedents and Policy Scope" tone="blue"}
What has been tried, and what exactly you would be verifying. IAEA safeguards in Iraq and what an inspectorate can and cannot audit; the goal, legal rule, verification claim ladder; compute thresholds against capability thresholds; and eleven candidate anti-ASI policies sorted by how much they deter and how gettable they are.
:::

:::callout {title="Unit 3: Treaty Anatomy and Actors" tone="blue"}
Read an agreement the way a mechanic reads an engine. Find the prohibition, the verification method and the exit clause in MIRI's draft ASI agreement, then map who a pause actually binds: seventeen actors across the compute supply chain, who declares, who holds the evidence, who verifies, and who no declaration reaches.
:::

:::callout {title="Unit 4: Evidence and Its Readers" tone="blue"}
Where a claim came from and who acts on it next. A true IAEA finding that fails because every claim in it came from the inspected party, a report distilled for four different readers, and then the four metrics you will use to judge every mechanism: technical feasibility, political feasibility, verification effectiveness, durability, plus the privacy-preserving techniques that make disclosure between rivals thinkable.
:::

:::callout {title="Unit 5: Hardware Verification" tone="blue"}
The first evidence stream, worked in detail. What a signed attestation actually proves and what it does not, identity, location, topology and the hard negative claim of completeness, measuring and classifying compute use, offline licensing and who holds the key, and where trust should sit: in the chip, on the network, on the power line, or across all three.
:::

\## What comes after

This is the first of our two Compute Verification courses. The second continues through the remaining evidence streams (cloud, intelligence, human and institutional) and how a determined adversary evades them. After completing both courses, you will take on a guided capstone project that brings everything you have learned together: designing and defending a verification regime for a three-month emergency pause.

:::callout {title="Works cited" tone="neutral" collapse="closed"}
Newman, Lily Hay. "OpenAI Didn't Notice Its AI Agents Using a Message Board to Plan Their Hacking Spree." *WIRED*, 5 Aug. 2026. [wired.com](https://www.wired.com/story/openai-didnt-notice-its-ai-agents-using-a-message-board-to-plan-their-hacking-spree/)
*WIRED's reporting from Black Hat on details OpenAI disclosed about its agents going rogue and hacking other companies unnoticed.*

XLab. "0.0 Welcome." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/why-verification/welcome)
*The source lesson that the welcome text between the two dividers above adapts.*
:::


