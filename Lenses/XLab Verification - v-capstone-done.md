---
id: '3c05a04a-b9f5-499a-803b-f5555fd416d7'
title: "Done, and the showcase"
tldr: "Done is not perfect. Done is: usable by the named reader, with every gap labelled and every number sourced or shown. Run the checklist for your deliverable type, submit, write the limitations and the ten-more-hours note, and prepare three minutes for the showcase."
summary_for_tutor: "Lens Academy scaffolding for XLab's capstone; not XLab source material. Final week. Sequence: what done means in general, then a checklist per deliverable type matching the bank's type labels (spec, analysis, design, dossier, memo, notebook), then the three parts every submission carries (limitations, sources, ten more hours), the showcase format, and five questions: checklist self-check, final submission with abstract, limitations and ten more hours, showcase outline, and a look back at the week 2 proposal. The facilitator reads the submission; the showcase is meeting 5. Help the learner finish rather than extend: if they want to add a section in the last two hours, ask whether the reader needs it more than the labelled gap. For the abstract, insist it is written for the named reader and leads with the answer. For the look-back, draw out what they learned about scoping, in their own words; do not supply the lesson. The checklists are Lens Academy's own guidance, not a standard from the field; say so if asked."
tags: [wip]
duration_minutes: 45
---
#### Text
content::
\## What done means

We think a capstone is done when its named reader could pick it up, act on it, and know exactly where not to trust it. That is a lower bar than "finished" and a higher bar than "I ran out of time". Three things follow:

- **Labelled gaps are part of done.** A row that says "could not resolve; needs X" is a finding. A row silently left out is a defect.
- **Every number is sourced or shown.** A figure with neither is a guess wearing a suit. Either cite it, show the calculation, or say it is your estimate and what it rests on.
- **The first paragraph carries the answer.** The reader should be able to stop after it and know what you concluded and how sure you are.

\## Checklist by deliverable type

The bank labels each brief with a type. Find yours. If your project is a hybrid, take the checklist of the type your reader would name.

:::callout {title="Spec (regime spec, reporting rules, attestation spec, security baseline, channel or hotline design)" tone="blue" collapse="closed"}
- Every rule names who does what, when, and what evidence it produces.
- At least one claim in the spec is checkable by a named verifier, and the spec says how.
- Each rule, or an annex, states the cheapest evasion it leaves open.
- The cost or burden on the complying party is stated, even roughly.
- What the spec does not cover is stated in one place, not scattered.
:::

:::callout {title="Analysis (threat model, scenario or sensitivity analysis, signature analysis, feasibility assessment, costing)" tone="blue" collapse="closed"}
- The question is stated in one sentence at the top and answered in the conclusion.
- The method is described so a reader could repeat it with the same sources.
- Every number has a source or a shown calculation; estimates are labelled as yours.
- The adversary's cheapest counter to your conclusion is named.
- There is a "what would change my answer" section: the inputs the conclusion is most sensitive to.
:::

:::callout {title="Design (protocol, attack tree, custody chain, decision framework)" tone="blue" collapse="closed"}
- The claim the design establishes is stated: what a verifier can conclude when it works.
- Each step names its prover, verifier, and the evidence that passes between them.
- Trust assumptions are listed in one place.
- The strongest bypass is described, with the step it exploits.
- The residual trust, what still has to be taken on faith, is named.
:::

:::callout {title="Dossier or case study (chokepoint dossier, custody regime case study, stock-and-flow cases)" tone="blue" collapse="closed"}
- Each load-bearing fact comes from more than one source, or is flagged single-source.
- The comparison or ranking uses stated criteria a reader could apply to a new case.
- What transfers to compute verification, and what does not, gets its own section.
- There is a confidence-and-gaps section: what you could not find, and where you looked.
:::

:::callout {title="Memo or decision rubric (evidentiary rubric, decision memo)" tone="blue" collapse="closed"}
- It is written to the named reader, in their vocabulary, at their length.
- The recommendation is in the first paragraph.
- The rubric or decision rule is usable by someone who has not read the memo.
- The case against the recommendation is stated fairly, in a paragraph the opponent would recognise.
- The trigger for revisiting the recommendation is named.
:::

:::callout {title="Notebook or dataset (reproducible chart, dataset with methods note)" tone="blue" collapse="closed"}
- Someone else can run it from the repository with the instructions given.
- Every data source is named with its date and where it was retrieved.
- Normalisation and exclusion choices are documented, with the alternative you did not take.
- The chart and its caveat travel together: no figure without the sentence that limits it.
- A short methods note says what the figure can and cannot support.
:::

\## Three things every submission carries

1. **Limitations.** What the deliverable cannot see, verify, price, or prove. Written plainly, not as an apology.
2. **Sources.** Everything you relied on, in a form a reader can follow.
3. **Ten more hours.** What you would do next with ten more hours, in order. This is where deferred review points go. A reader who wants to fund or continue the work starts here.

\## The showcase

Meeting 5 is the showcase. Three minutes each, then five minutes of questions. Four beats:

1. **The reader and the decision.** Who this is for and what they were going to do without it.
2. **The answer.** What you concluded, in the form the reader needs.
3. **The one thing you are least sure of.** Named, not hidden.
4. **What you want from the room.** A question you still have, a person you need, a source you could not find.

No slides needed. A single table or figure on screen is fine if it carries the answer.

#### Question: Open
id:: 8a4e9972-1b4e-4b1e-83a6-f019637565c4
content::
\## Checklist

Name your deliverable type. For each item on its checklist: yes, partly, or no, with one line saying where in the deliverable the reader finds it, or what is missing.
assessment-instructions:: Give full credit when the type is named, every item of that type's checklist has a yes/partly/no with a location or a specific missing thing, and at least one "partly" or "no" is answered honestly with what is missing (a checklist that is all "yes" with no locations is not credible). Partial credit if items are skipped or the answers are unlocated.
feedback-instructions:: Take the first "no" or "partly" and ask whether it can be fixed in under an hour or should become a labelled gap in the limitations section. If everything is "yes" without locations, ask where in the document a reader finds two of them. Two or three sentences. No praise.

#### Question: Open
id:: 69cfbbe5-b3b1-4bfc-89eb-133162d80648
content::
\## Final submission

The link to your finished deliverable, its title, and a 100-word abstract written for the named reader: what question, what answer, how sure.
assessment-instructions:: Give full credit when there is a link, a title, and an abstract of roughly 100 words that names the reader or is visibly addressed to them, states the question, states the answer (a position, not "this document explores"), and gives a confidence or scope qualifier. Partial credit if the abstract describes the document rather than stating its answer, or is far outside the length. Do not open the link.
feedback-instructions:: If the abstract says what the document does instead of what it concludes, rewrite its first sentence as a conclusion in one line and ask if that is right. If the confidence is missing, ask how sure they are and what that rests on. One or two sentences otherwise. No praise.

#### Question: Open
id:: 98155207-90a3-4ca3-a166-ae517d7edff7
content::
\## Limitations, and ten more hours

The limitations section as it appears in your deliverable (paste it). Then: what you would do with ten more hours, in order.
assessment-instructions:: Give full credit when the limitations are specific (things the deliverable cannot see, verify, price, or prove; not "more research is needed"), and the ten-more-hours list is ordered with at least three concrete items, ideally including deferred review points. Partial credit if limitations are generic or the list is unordered or vague.
feedback-instructions:: If a limitation is generic, ask what specifically the reader should not rely on. If the ten-hours list starts with polish rather than the biggest gap, ask why. Two sentences. No praise.

#### Question: Open
id:: 400320bc-8b16-4dae-9902-314ea1133234
content::
\## Showcase outline

The four beats of your three minutes: reader and decision, the answer, the thing you are least sure of, what you want from the room. One or two sentences each.
assessment-instructions:: Give full credit when all four beats are present, the answer is a position, the least-sure item is specific, and the ask of the room is something a group of peers could actually give (a question they can weigh in on, a source, a contact). Partial credit if the answer is a description, the least-sure item is missing, or the ask is generic ("feedback").
feedback-instructions:: If the ask is "feedback", ask what kind, on what. If the least-sure item is missing, ask which claim they would least like to be asked about. One or two sentences. No praise.

#### Question: Open
id:: 456553eb-9228-4e0f-9c47-c532828c3724
content::
\## Look back at the proposal

Open your week 2 proposal. What changed between it and what you submitted: the question, the reader, the scope, the hours? What would you scope differently next time, and what would you keep?
assessment-instructions:: Give full credit when the learner names at least two concrete differences between the proposal and the submission and draws one lesson about scoping that is stated as their own (what they would do differently or keep, and why). Partial credit if the differences are generic or the lesson is a platitude ("plan better"). If nothing changed, give full credit for an account of why the proposal held, with evidence.
feedback-instructions:: Reflect the lesson back in one sentence in their terms and ask whether it would have been visible at the proposal or only after the crappy version. Do not supply a lesson of your own. Then point them to the next lens: the course's closing page. Two sentences. No praise.

#### Text
content::
\## Before meeting 5

Submit before the meeting, not after; the showcase is of the thing you submitted. Bring your four beats and, if it helps, one table or figure. Listen to the others' beat three, the thing they are least sure of: it is usually the most interesting part of the work and the best place to ask a question.
