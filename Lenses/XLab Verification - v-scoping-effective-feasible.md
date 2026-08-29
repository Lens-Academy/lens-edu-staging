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
content:: **Interactive exercise:** XLab's `policy-scoping` widget has no direct Lens equivalent yet. Complete it in the [original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible). Its surrounding lesson text is preserved here.

#### Text
content::
**Design for the hardest case.** Verification strong enough to support a full pause — chip registries, compute metering, inspection rights — supports every weaker bucket for free. The reverse is not true. That is why this track studies verification against the pause, even if what gets signed first is transparency.

#### Text
content:: **Import gap:** XLab persistent memo desk has no clean Lens equivalent. Use the [original XLab lesson](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible) for this element.

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/policy-scoping/scoping-effective-feasible)*
