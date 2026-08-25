---
id: 3d95d5e3-b5dd-4ff8-90b8-24653db41a3d
learning-outcome: "Describe the strong version of superalignment {++{"author":"Luc's AI","timestamp":1787659318957}@@as Chapter 11 presents it ++}(using a smarter-than-human AI to solve the alignment {--{"author":"Luc's AI","timestamp":1787659318957}@@problem for us),--}{++{"author":"Luc's AI","timestamp":1787659318957}@@problem),++} and state the{--{"author":"Luc's AI","timestamp":1787659318957}@@ two-step objection to it:--}{++{"author":"Luc's AI","timestamp":1787659318957}@@ chapter's two-step objection:++} (1) {--{"author":"Luc's AI","timestamp":1787659318957}@@an--}{++{"author":"Luc's AI","timestamp":1787659318957}@@the++} AI capable of doing this would itself be too dangerous and {--{"author":"Luc's AI","timestamp":1787659318957}@@untrustworthy to deploy before alignment is solved,--}{++{"author":"Luc's AI","timestamp":1787659318957}@@untrustworthy,++} and (2){--{"author":"Luc's AI","timestamp":1787659318957}@@ retreating to --}{++{"author":"Luc's AI","timestamp":1787659318957}@@ ++}a 'special-purpose' alignment AI{--{"author":"Luc's AI","timestamp":1787659318957}@@ does not escape this, because there are--}{++{"author":"Luc's AI","timestamp":1787659318957}@@ has++} no training examples of solved alignment and {--{"author":"Luc's AI","timestamp":1787659318957}@@the skill set--}{++{"author":"Luc's AI","timestamp":1787659318957}@@requires++} the {--{"author":"Luc's AI","timestamp":1787659318957}@@task requires is precisely the--}{++{"author":"Luc's AI","timestamp":1787659318957}@@precise dangerous++} skill set that makes an unaligned AI catastrophic."
reading-from: "Some AI companies do try to look less cavalier than that, about ASI alignment, and put forth plans more detailed than those."
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
stage: beginner
eval-results:
  content-sha: 88f0c03d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing — describing what Chapter 11 presents and stating the chapter's objection, not a source-free capability.", B1: "Question uses the chapter as load-bearing scaffolding, repeatedly asking for what Chapter 11 says rather than self-containing the content."}
  evidence: {A2: "Describe the strong version of superalignment as Chapter 11 presents it ... and state the chapter's two-step objection", B1: "Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection"}
---

## Test:
id:: fc3b7597-3165-46ee-af3a-a6990d9e98eb
#### Question
content:: {--{"author":"Luc's AI","timestamp":1787659321306}@@One of the--}{++{"author":"Luc's AI","timestamp":1787659321306}@@The++} most developed alignment {--{"author":"Luc's AI","timestamp":1787659321306}@@plans on offer --}{++{"author":"Luc's AI","timestamp":1787659321306}@@plan Chapter 11 examines ++}is "superalignment": the idea, made flagship at OpenAI in 2023, of using AI to help solve the alignment problem itself. {--{"author":"Luc's AI","timestamp":1787659321306}@@It comes in--}{++{"author":"Luc's AI","timestamp":1787659321306}@@The chapter splits this into++} two {--{"author":"Luc's AI","timestamp":1787659321306}@@versions —--}{++{"author":"Luc's AI","timestamp":1787659321306}@@versions,++} weak (AI{--{"author":"Luc's AI","timestamp":1787659321306}@@ assists human researchers--}{++{"author":"Luc's AI","timestamp":1787659321306}@@ helps++} with {--{"author":"Luc's AI","timestamp":1787659321306}@@work like interpretability)--}{++{"author":"Luc's AI","timestamp":1787659321306}@@interpretability research)++} and strong (a smarter-than-human AI solves alignment for {--{"author":"Luc's AI","timestamp":1787659321306}@@us). Critics argue--}{++{"author":"Luc's AI","timestamp":1787659321306}@@us), and finds++} the strong version {--{"author":"Luc's AI","timestamp":1787659321306}@@is structurally--}{++{"author":"Luc's AI","timestamp":1787659321306}@@particularly++} broken.

**Describe the strong-superalignment {--{"author":"Luc's AI","timestamp":1787659324065}@@proposal. --}{++{"author":"Luc's AI","timestamp":1787659324065}@@proposal as Chapter 11 presents it. ++}Then state the {--{"author":"Luc's AI","timestamp":1787659324065}@@main objection to it:--}{++{"author":"Luc's AI","timestamp":1787659324065}@@chapter's objection:++} specifically, why building the AI required to solve alignment cannot be done before alignment is itself solved. If you can, also {--{"author":"Luc's AI","timestamp":1787659324065}@@give--}{++{"author":"Luc's AI","timestamp":1787659324065}@@describe++} the {++{"author":"Luc's AI","timestamp":1787659324065}@@chapter's ++}response to{--{"author":"Luc's AI","timestamp":1787659324065}@@ the rebuttal--} "we'll just make a special-purpose alignment AI that isn't generally dangerous."**

assessment-instructions::
Score according to the following rubric.

**1**: Cannot describe the strong-superalignment plan or confuses it with weak superalignment / interpretability. *Example: "OpenAI says they'll use AI to look inside other AIs."*

**2**: Describes the plan in vague terms but cannot articulate the objection. *Example: "They want a smart AI to solve the alignment problem for them. {--{"author":"Luc's AI","timestamp":1787659326224}@@Critics say--}{++{"author":"Luc's AI","timestamp":1787659326224}@@The book says++} that won't work."*

**3**: Correctly states the strong-superalignment plan and the {++{"author":"Luc's AI","timestamp":1787659328079}@@chapter's ++}core capability-paradox objection: the AI smart enough to actually solve the alignment problem would itself need to be smarter than humanity's geniuses, which means you can't safely build it *before* alignment is solved. The AI you'd need is the AI you'd need to align *first*. *Example: "Strong superalignment is the plan to build an AI smart enough to solve the alignment problem on humanity's behalf. The objection is a circular dependency: you'd need an AI smarter than human geniuses to actually solve this, but you can't trust an AI that smart unless alignment is already solved. So the plan requires having already done the thing it claims it will do."*

**4**: As above, plus describes the {++{"author":"Luc's AI","timestamp":1787659329300}@@chapter's ++}objection to the "special-purpose alignment AI" rebuttal: there are no training examples of solved alignment, the skill set required (programming, growing AIs, AI preferences, human psychology) is precisely the dangerous skill set, and an AI handing you a clever-sounding alignment proposal cannot itself be verified. *Example: Adds "The 'we'll just train a narrow alignment AI' rebuttal doesn't work because: there are no examples of solved alignment to train on, so the AI has to generalize from related skills; those related skills (understanding programming, AI internals, human psychology) are exactly the dangerous skill set; and if it tells you it's solved alignment you have no way to verify the proposal. You'd have to either trust the AI's word or follow its argument, and either way you're trusting the unaligned thing."*

**5**: As above, plus contrasts strong superalignment with a {--{"author":"Luc's AI","timestamp":1787659330035}@@narrow-domain counterexample, e.g. a *biomedical AI* or equivalent: --}{++{"author":"Luc's AI","timestamp":1787659330035}@@*biomedical-AI* counterexample (per the chapter): ++}a biology-specialized AI is at least not thinking explicitly about how to make better AIs, so its outputs are checkable against narrower verification tools. The structural problem with strong superalignment is that the alignment-thinking AI *cannot* be made non-dangerous in the same way. *Example: Adds {--{"author":"Luc's AI","timestamp":1787659330035}@@"Contrast--}{++{"author":"Luc's AI","timestamp":1787659330035}@@"The chapter contrasts++} this with a biomedical AI: that AI isn't reasoning about AI internals or alignment psychology, so if it outputs a cancer cure you can run separate narrower tools to check the protein interactions. Strong superalignment doesn't have that out: the very capability you need *is* the dangerous thinking. There's no narrower checker for 'is this alignment plan secretly going to fail.'"*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection]]
