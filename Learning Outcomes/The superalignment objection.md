---
id: 3d95d5e3-b5dd-4ff8-90b8-24653db41a3d
learning-outcome: "Describe the strong version of superalignment as Chapter 11 presents it (using a smarter-than-human AI to solve the alignment problem), and state the chapter's two-step objection: (1) the AI capable of doing this would itself be too dangerous and untrustworthy, and (2) a 'special-purpose' alignment AI has no training examples of solved alignment and requires the precise dangerous skill set that makes an unaligned AI catastrophic."
reading-from: "Some AI companies do try to look less cavalier than that, about ASI alignment, and put forth plans more detailed than those."
reading-to: "end of chapter"
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/Why alignment is hard]]"
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
#### Question: Open
id:: 0ea83c3b-5c18-41c2-94bf-363a3c57d2f1
content:: The most developed alignment plan Chapter 11 examines is "superalignment": the idea, made flagship at OpenAI in 2023, of using AI to help solve the alignment problem itself. The chapter splits this into two versions, weak (AI helps with interpretability research) and strong (a smarter-than-human AI solves alignment for us), and finds the strong version particularly broken.

**Describe the strong-superalignment proposal as Chapter 11 presents it. Then state the chapter's objection: specifically, why building the AI required to solve alignment cannot be done before alignment is itself solved. {--{"author":"James's AI","timestamp":1791834901902}@@Also--}{++{"author":"James's AI","timestamp":1791834901902}@@If you can, also++} describe the chapter's response to "we'll just make a special-purpose alignment AI that isn't generally dangerous."**

assessment-instructions::
Score {--{"author":"James's AI","timestamp":1791834901902}@@out of 100:--}{++{"author":"James's AI","timestamp":1791834901902}@@according to++} the {--{"author":"James's AI","timestamp":1791834901902}@@sum of the three elements below.

The question asks the learner to describe the "strong superalignment" proposal, to state the chapter's objection--}{++{"author":"James's AI","timestamp":1791834901902}@@following rubric.

**1**: Cannot describe the strong-superalignment plan or confuses it with weak superalignment / interpretability. *Example: "OpenAI says they'll use AI++} to {--{"author":"James's AI","timestamp":1791834901902}@@it, and, if they can,--}{++{"author":"James's AI","timestamp":1791834901902}@@look inside other AIs."*

**2**: Describes++} the {--{"author":"James's AI","timestamp":1791834901902}@@chapter's reply to--}{++{"author":"James's AI","timestamp":1791834901902}@@plan in vague terms but cannot articulate++} the {--{"author":"James's AI","timestamp":1791834901902}@@idea of--}{++{"author":"James's AI","timestamp":1791834901902}@@objection. *Example: "They want++} a {--{"author":"James's AI","timestamp":1791834901902}@@special-purpose--}{++{"author":"James's AI","timestamp":1791834901902}@@smart AI to solve the++} alignment {--{"author":"James's AI","timestamp":1791834901902}@@AI.

20:--}{++{"author":"James's AI","timestamp":1791834901902}@@problem for them.++} The {--{"author":"James's AI","timestamp":1791834901902}@@proposal. Strong superalignment means building an AI smarter than --}{++{"author":"James's AI","timestamp":1791834901902}@@book says that won't work."*

**3**: Correctly states the strong-superalignment plan and ++}the {--{"author":"James's AI","timestamp":1791834901902}@@best human researchers and having it--}{++{"author":"James's AI","timestamp":1791834901902}@@chapter's core capability-paradox objection: the AI smart enough to actually++} solve the alignment problem {--{"author":"James's AI","timestamp":1791834901902}@@for us (not just helping humans with parts of the research, such as interpretability). Any plain description of "get a very capable --}{++{"author":"James's AI","timestamp":1791834901902}@@would itself need to be smarter than humanity's geniuses, which means you can't safely build it *before* alignment is solved. The AI you'd need is the ++}AI {++{"author":"James's AI","timestamp":1791834901902}@@you'd need ++}to {--{"author":"James's AI","timestamp":1791834901902}@@solve alignment on our behalf" earns these 20. An answer that only describes AI helping with interpretability research earns nothing here.

50:--}{++{"author":"James's AI","timestamp":1791834901902}@@align *first*. *Example: "Strong superalignment is the plan to build an AI smart enough to solve the alignment problem on humanity's behalf.++} The {--{"author":"James's AI","timestamp":1791834901902}@@objection. An AI capable enough to solve alignment would itself be powerful and dangerous, and nobody can trust or safely build--}{++{"author":"James's AI","timestamp":1791834901902}@@objection is a circular dependency: you'd need an AI smarter than human geniuses to actually solve this, but you can't trust++} an AI that {--{"author":"James's AI","timestamp":1791834901902}@@capable until--}{++{"author":"James's AI","timestamp":1791834901902}@@smart unless++} alignment is already solved. So the plan {--{"author":"James's AI","timestamp":1791834901902}@@needs--}{++{"author":"James's AI","timestamp":1791834901902}@@requires having already done++} the{--{"author":"James's AI","timestamp":1791834901902}@@ solution before--}{++{"author":"James's AI","timestamp":1791834901902}@@ thing++} it {--{"author":"James's AI","timestamp":1791834901902}@@can start: --}{++{"author":"James's AI","timestamp":1791834901902}@@claims ++}it {--{"author":"James's AI","timestamp":1791834901902}@@is circular. Credit any wording of this idea, for example "you would need an aligned superintelligence to get an aligned superintelligence". An answer that says only that the plan won't work, or that it--}{++{"author":"James's AI","timestamp":1791834901902}@@will do."*

**4**: As above, plus describes the chapter's objection to the "special-purpose alignment AI" rebuttal: there are no training examples of solved alignment, the skill set required (programming, growing AIs, AI preferences, human psychology)++} is {--{"author":"James's AI","timestamp":1791834901902}@@risky, with no reason why, earns at most 10 here.

30: The reply to "just build a special-purpose alignment AI that isn't generally dangerous". The chapter gives three reasons it fails:--}{++{"author":"James's AI","timestamp":1791834901902}@@precisely the dangerous skill set, and an AI handing you a clever-sounding alignment proposal cannot itself be verified. *Example: Adds "The 'we'll just train a narrow alignment AI' rebuttal doesn't work because:++} there are no examples of solved alignment to train {--{"author":"James's AI","timestamp":1791834901902}@@such an--}{++{"author":"James's AI","timestamp":1791834901902}@@on, so the++} AI {--{"author":"James's AI","timestamp":1791834901902}@@on, so it must generalise--}{++{"author":"James's AI","timestamp":1791834901902}@@has to generalize++} from related{--{"author":"James's AI","timestamp":1791834901902}@@ skills. The skills it would need (programming, how AIs are grown, what AIs want, --}{++{"author":"James's AI","timestamp":1791834901902}@@ skills; those related skills (understanding programming, AI internals, ++}human psychology) are exactly the{--{"author":"James's AI","timestamp":1791834901902}@@ skills that make an unaligned AI dangerous. And when--}{++{"author":"James's AI","timestamp":1791834901902}@@ dangerous skill set; and if++} it {--{"author":"James's AI","timestamp":1791834901902}@@hands--}{++{"author":"James's AI","timestamp":1791834901902}@@tells++} you {--{"author":"James's AI","timestamp":1791834901902}@@an--}{++{"author":"James's AI","timestamp":1791834901902}@@it's solved++} alignment {--{"author":"James's AI","timestamp":1791834901902}@@plan --}you{--{"author":"James's AI","timestamp":1791834901902}@@ cannot check it, so you end up trusting--}{++{"author":"James's AI","timestamp":1791834901902}@@ have no way to verify++} the {--{"author":"James's AI","timestamp":1791834901902}@@AI or its persuasive argument. Any one of these reasons, stated clearly, earns 20. Two--}{++{"author":"James's AI","timestamp":1791834901902}@@proposal. You'd have to either trust the AI's word++} or{--{"author":"James's AI","timestamp":1791834901902}@@ more earn 30.

Cap at 40 if the answer's main objection is that today's AI is not yet smart enough to solve alignment, since--}{++{"author":"James's AI","timestamp":1791834901902}@@ follow its argument, and either way you're trusting the unaligned thing."*

**5**: As above, plus contrasts strong superalignment with a *biomedical-AI* counterexample (per++} the {--{"author":"James's AI","timestamp":1791834901902}@@chapter's point is that an--}{++{"author":"James's AI","timestamp":1791834901902}@@chapter): a biology-specialized++} AI {--{"author":"James's AI","timestamp":1791834901902}@@that --}is{--{"author":"James's AI","timestamp":1791834901902}@@ smart enough would be the danger.

Model answer, for the feedback,--}{++{"author":"James's AI","timestamp":1791834901902}@@ at least++} not{--{"author":"James's AI","timestamp":1791834901902}@@ a grading checklist: "Strong superalignment is the plan--}{++{"author":"James's AI","timestamp":1791834901902}@@ thinking explicitly about how++} to {--{"author":"James's AI","timestamp":1791834901902}@@build an AI smarter than our best researchers and have it solve alignment for us.--}{++{"author":"James's AI","timestamp":1791834901902}@@make better AIs, so its outputs are checkable against narrower verification tools.++} The{--{"author":"James's AI","timestamp":1791834901902}@@ problem is circular: an AI capable of that--}{++{"author":"James's AI","timestamp":1791834901902}@@ structural problem with strong superalignment++} is {--{"author":"James's AI","timestamp":1791834901902}@@exactly--}{++{"author":"James's AI","timestamp":1791834901902}@@that++} the {--{"author":"James's AI","timestamp":1791834901902}@@kind of --}{++{"author":"James's AI","timestamp":1791834901902}@@alignment-thinking ++}AI {--{"author":"James's AI","timestamp":1791834901902}@@that is dangerous if it isn't aligned, and we can't trust it or safely build it until we have already solved alignment. A special-purpose alignment--}{++{"author":"James's AI","timestamp":1791834901902}@@*cannot* be made non-dangerous in the same way. *Example: Adds "The chapter contrasts this with a biomedical AI: that AI isn't reasoning about++} AI {--{"author":"James's AI","timestamp":1791834901902}@@doesn't escape this. There are no worked examples of solved alignment to train it on, the skills it would need (understanding programming, AI internals and human minds) are--}{++{"author":"James's AI","timestamp":1791834901902}@@internals or alignment psychology, so if it outputs a cancer cure you can run separate narrower tools to check the protein interactions. Strong superalignment doesn't have that out:++} the {--{"author":"James's AI","timestamp":1791834901902}@@dangerous ones, and if it hands us a plan we can't verify it, so we'd just be trusting the thing we can't trust."--}{++{"author":"James's AI","timestamp":1791834901902}@@very capability you need *is* the dangerous thinking. There's no narrower checker for 'is this alignment plan secretly going to fail.'"*++}

force-feedback:: first
feedback-instructions:: Respond to what the learner actually wrote. Open on the strongest thing in it, in one sentence. Then push once, chosen by where they stopped:

- If they described weak superalignment or interpretability, ask what the strong version expects the AI itself to produce.
- If they described the plan but not the objection, ask how capable the AI would have to be to solve alignment, and what you would need before you could safely build something that capable.
- If they had the circular dependency, ask about the special-purpose AI: what would it train on, what skills would it need, and how would you check its answer?
- If they had that,{--{"author":"James's AI","timestamp":1791834901902}@@ they have full marks. You may offer one extension: --}{++{"author":"James's AI","timestamp":1791834901902}@@ ask ++}how{--{"author":"James's AI","timestamp":1791834901902}@@ does--} a biomedical AI {--{"author":"James's AI","timestamp":1791834901902}@@compare, and--}{++{"author":"James's AI","timestamp":1791834901902}@@compares:++} why can its output be checked when an alignment proposal cannot?

At full marks, just confirm briefly. Don't cite {--{"author":"James's AI","timestamp":1791834901902}@@point values.--}{++{"author":"James's AI","timestamp":1791834901902}@@level numbers or band names (the learner sees a percentage).++} If asked about the score, say in plain words what the answer did and the one{--{"author":"James's AI","timestamp":1791834901902}@@ most important--} thing it missed. If they say they don't understand, give one concrete foothold: the first step of the plan is an AI smart enough to solve a problem humanity's best researchers cannot. Ask what has to be true before you can trust that step. If they still don't attempt it, rephrase the question.

One follow-up question. No generic praise, don't recite the rubric. 100 to 160 words, short paragraphs, no lists.


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Strong Superalignment Objection]]
