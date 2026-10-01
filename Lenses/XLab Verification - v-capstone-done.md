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
assessment-instructions:: Score out of 100. 10: the deliverable type is named (for a hybrid, the type its reader would name). 90: every item on that type's checklist is answered, the 90 points split evenly across the items; for each item, half for a yes, partly or no, and half for the line that goes with it: where in the deliverable the reader finds it (a section, a table, a row, not "throughout"), or for partly and no, what specifically is missing. A skipped item earns nothing. Give credit whenever the answer shows this, in any wording. Model answer, for the feedback, not a grading checklist: "An example for a hypothetical Analysis deliverable. Type: Analysis. Question stated in one sentence at the top and answered in the conclusion: yes, first line of the summary and section 5. Method described so a reader could repeat it: partly, section 2 names the sources but not the search terms or the date cut-off. Every number sourced or shown, estimates labelled: partly, table 1 is sourced, but the power figures in table 3 are my estimates and not yet labelled as such. Adversary's cheapest counter named: yes, section 4, splitting the run across small sites. A what-would-change-my-answer section: no, missing; it should name the chip-count estimate and the detection threshold."
feedback-instructions:: Take the first "no" or "partly" and ask whether it can be fixed in under an hour or should become a labelled gap in the limitations section. If everything is "yes" without locations, ask where in the document a reader finds two of them. Two or three sentences. No praise.

#### Question: Open
id:: 69cfbbe5-b3b1-4bfc-89eb-133162d80648
content::
\## Final submission

The link to your finished deliverable, its title, and a 100-word abstract written for the named reader: what question, what answer, how sure.
assessment-instructions:: Score out of 100. 10: a link to the deliverable. 5: its title. 85: the abstract, 20: it is written for the named reader (names them or is visibly addressed to them), 20: it states the question, 25: it states the answer as a position, not a description of what the document does ("this document explores"), 15: it says how sure the author is (a confidence or a scope qualifier), 5: it is roughly 100 words. Give credit for each point whenever the answer shows it, in any wording. Model answer, for the feedback, not a grading checklist: "An example for a hypothetical project. Link: (the shared document). Title: Can grid data catch a covert training run? Abstract: For the verification desk deciding whether to buy utility power data: can grid data alone flag a covert frontier training run at a site declared for inference? Our answer is yes for runs drawing more than about 50 MW for two weeks or longer, and no below that, because ordinary swings in inference load hide smaller runs. We are moderately confident. The result rests on public load curves from four US sites and a modelled training profile, and it would fail if operators shape their load on purpose. Grid data is worth buying as a tripwire, not as proof."
feedback-instructions:: If the abstract says what the document does instead of what it concludes, rewrite its first sentence as a conclusion in one line and ask if that is right. If the confidence is missing, ask how sure they are and what that rests on. One or two sentences otherwise, naming the most important gap or weakness if there is one. No praise.

#### Question: Open
id:: 98155207-90a3-4ca3-a166-ae517d7edff7
content::
\## Limitations, and ten more hours

The limitations section as it appears in your deliverable (paste it). Then: what you would do with ten more hours, in order.
assessment-instructions:: Score out of 100. 50: the limitations, 35: they are specific, naming what the deliverable cannot see, verify, price or prove, and 15: they are stated plainly, as things the reader should not rely on, not as an apology or "more research is needed". 50: the ten more hours, 30: concrete next steps, each a task someone could start, and 20: given in an order, most important first. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the limitations are only generic. Model answer, for the feedback, not a grading checklist: "An example for a hypothetical project. Limitations: The analysis cannot see behind-the-meter generation, so a site running on its own gas turbines is invisible to it. The load profiles come from four US sites; I could not verify that Chinese grid data has the same resolution. The cost of the monitoring is not priced. Ten more hours, in order: first, test the threshold on two more sites; second, price access to utility data in the largest markets; third, answer the review point I deferred, whether deliberate load shaping defeats the threshold."
feedback-instructions:: If a limitation is generic, ask what specifically the reader should not rely on. If the ten-hours list starts with polish rather than the biggest gap, ask why. Two sentences. No praise.

#### Question: Open
id:: 400320bc-8b16-4dae-9902-314ea1133234
content::
\## Showcase outline

The four beats of your three minutes: reader and decision, the answer, the thing you are least sure of, what you want from the room. One or two sentences each.
assessment-instructions:: Score out of 100. 25 for each of the four beats. Reader and decision, 25: who the work is for and what they were going to decide or do without it. The answer, 25: what was concluded, stated as a position, not a description of the work (10 if it only describes). The thing least sure of, 25: a specific claim, number or input, not general uncertainty (10 if generic). What you want from the room, 25: something a group of peers could actually give, such as a question they can weigh in on, a source or a contact (5 if it is just "feedback"). Give credit whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "An example for a hypothetical project. Reader and decision: the treaty verification desk, which is about to decide whether to pay for utility power data. The answer: grid data catches runs above about 50 MW sustained for two weeks, and nothing smaller, so buy it as a tripwire, not as proof. Least sure of: whether an operator could flatten its training load to look like inference; I modelled only an unshaped run. From the room: does anyone know a source for site-level power data outside the US, or someone who has worked with utility smart-meter data?"
feedback-instructions:: If the ask is "feedback", ask what kind, on what. If the least-sure item is missing, ask which claim they would least like to be asked about. One or two sentences. No praise.

#### Question: Open
id:: 456553eb-9228-4e0f-9c47-c532828c3724
content::
\## Look back at the proposal

Open your week 2 proposal. What changed between it and what you submitted: the question, the reader, the scope, the hours? What would you scope differently next time, and what would you keep?
assessment-instructions:: Score out of 100. 50: what changed between the proposal and the submission, 25 each for two concrete differences (in the question, the reader, the scope or the hours), each saying what it was and what it became, not just "the scope changed". If nothing changed, these 50 go to an account of why the proposal held, with evidence from the work. 30: what they would scope differently next time, stated as something they would actually do, not a platitude such as "plan better". 20: what they would keep. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "An example for a hypothetical project. The question narrowed from whether power data can detect covert training to the run size below which grid data stops working. The reader changed from policymakers in general to the verification desk deciding whether to buy grid data. The hours went from 14 planned to about 18, most of the overrun spent finding load data. Next time I would name the reader before the question, and find the data source in the first week before committing to a method. I would keep building the crappy version first: the ugly table in week 2 is what showed me the question was too big."
feedback-instructions:: Reflect the lesson back in one sentence in their terms and ask whether it would have been visible at the proposal or only after the crappy version. Do not supply a lesson of your own. If the answer has a gap or weakness, name the most important one. Then point them to the next lens: the course's closing page. Three sentences. No praise.

#### Text
content::
\## Before meeting 5

Submit before the meeting, not after; the showcase is of the thing you submitted. Bring your four beats and, if it helps, one table or figure. Listen to the others' beat three, the thing they are least sure of: it is usually the most interesting part of the work and the best place to ask a question.
