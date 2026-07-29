---
id: 'e34f8ace-0588-44f3-a4d7-7e4eb5197795'
title: "Mechanisms to Verify International Agreements About AI Development"
tldr: "The mechanisms you'd want mostly don't exist yet. The argument: access can buy the same confidence — which moves the problem from the physics budget to the political one."
summary_for_tutor: "Scher and Thiergart (MIRI Technical Governance Team) — the reading that reframes the shortfall. Examines verification mechanisms (processes or tools giving one party greater confidence that another is following agreed rules) for three example policy goals, focused on state-level coordination though applicable to corporate regulation. Surveys across a spectrum of technological maturity: advanced technical solutions that are currently infeasible, and access-based approaches that are presently viable — physical inspections of data centres and facilities substituting where technical methods are unavailable. Central claim: 'increased access can often substitute for' unavailable technical verification, so significant political will could enable ambitious international coordination with strong verification NOW. The excerpt covers the first and most relevant policy goal, verifying that known compute is not being used for a large training run, and ends on two points worth catching: distributed training may make it hard to exclude small data centres (hundreds to low-thousands of chips) from monitoring, raising compliance burden; and mechanisms differ in paradigm-invariance — inference-only chips and workload classification via high-level chip information are specific to the current transformer/pre-training paradigm, while partial workload re-running, the general FlexHEG approach, and inspectors with code access are likely to survive paradigm shifts. The pedagogical goal is that the learner can both state the substitution argument and price it honestly."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Here is a fact that ought to be discouraging: almost every verification mechanism you would actually *want* — elegant, cryptographic, privacy-preserving, cheap — does not exist in deployable form today.

Scher and Thiergart's response is the most useful reframe in this module. Verification is a **job, not a gadget.** What you need is confidence that the other party is doing what they promised, and confidence can be bought with technology *or* with access: declarations, inspectors on the data-centre floor, records, interviews. Where the clever mechanism is missing, enough access covers the same ground.

If that is right, the shortfall was never really technical.

Read for two things. First, the substitution argument itself. Second — and be honest here rather than charitable — **what the substitution costs.** Access is intrusive in precisely the places states and companies refuse to be intruded upon.

**Read from the beginning and stop when you reach:**

> On the other hand, some approaches appear more paradigm-invariant, requiring changes to implementation details but very likely remaining relevant under paradigm shifts: partial workload re-running, the general FlexHEG approach, and using inspectors with code access.

That covers the framing and the first policy goal — verifying that known compute is not being used for a large training run. The other goals continue below.

#### Article
source:: [[../articles/scher-mechanisms-to-verify-international-agreements-about-ai-development-table-edit-published-version]]
to:: "On the other hand, some approaches appear more paradigm-invariant, requiring changes to implementation details but very likely remaining relevant under paradigm shifts: partial workload re-running, the general FlexHEG approach, and using inspectors with code access."

#### Text
content::
That final distinction is worth carrying with you: some mechanisms are artifacts of the current paradigm, and some would survive a change in how AI is built.

Ask yourself which kind you would rather a treaty depended on.

#### Chat
instructions::
TLDR of what the learner just read:
Scher and Thiergart (MIRI Technical Governance Team) on mechanisms to verify international agreements about AI development. A verification mechanism is a process or tool giving one party greater confidence that another is following agreed rules. The report examines three example policy goals; the excerpt covers the first, verifying that known compute is not being used for a large training run. It surveys approaches across a spectrum of technological maturity: advanced technical solutions that are currently infeasible, and access-based approaches that are presently viable, with physical inspections of data centres and facilities substituting where technical methods are unavailable. Central claim: increased access can often substitute for unavailable technical verification, so significant political will could enable ambitious international coordination with strong verification mechanisms today. Two closing points in the excerpt: given likely advances in distributed training, it may be hard to exclude small AI data centres (hundreds to low-thousands of chips) from monitoring, though excluding them is highly desirable for reducing compliance burden and verification difficulty; and mechanisms differ in paradigm-invariance — inference-only chips and workload classification using high-level chip information (including interconnect bandwidth limits) are specific to the current transformer-and-pre-training paradigm, whereas partial workload re-running, the general FlexHEG approach, and using inspectors with code access are likely to remain relevant under paradigm shifts. Notes that the more effective mechanisms rely on strong security and have development times of at least two years, so work should begin early.

The learning outcome this serves: explain the substitution argument, price it, and say when it stops working.

Discussion topics to explore:
- Get the substitution argument stated cleanly first: verification is a function, not a device; technical mechanisms and access are both ways of shrinking the space of undetected violations; so where a mechanism is missing, sufficient access covers the same ground. The consequence is that the binding constraint is political will rather than physics.
- Then insist on the price, because a learner who only has the optimistic half has not understood it. Access exposes commercially valuable IP and militarily sensitive information; every inspector is also a potential collector; it is slow and administratively heavy; and it scales the wrong way, since confidence rises with frequency and depth while political tolerance falls. The substitution moves the problem from the physics budget to the political-capital budget — real progress, but only if that capital exists.
- Then ask when the trade stops working. Access needs somewhere to send the inspector. It degrades against violations that are dispersed, purely informational, or nested inside permitted activity: standing in a compliant facility tells you nothing about an undeclared one, and watching a running cluster does not tell you whether the workload is allowed. Draw the conclusion — this is why technical mechanisms remain worth building even granting the substitution: access gets a first regime started, mechanisms make it cheap, repeatable, and able to reach cases where there is nothing to visit.
- The distributed-training point deserves attention. If small data centres cannot be excluded, the monitored population balloons and compliance burden rises sharply. Ask what that does to the tractability finding from the Oxford report, and connect to the compute-concentration dependence.
- **Paradigm-invariance** as a design criterion is the most transferable idea here. Ask them to sort the course's mechanisms so far into paradigm-specific and paradigm-invariant, and then ask which kind a treaty should rest on. This reframes "which mechanism is best" into "which mechanism survives being wrong about the future".
- Two-year-plus development times for the effective mechanisms: connect to the sequencing argument that credible verification must exist before a political window opens.

Check that they can give both halves — the substitution and its price — and name one case where access cannot substitute at all.
