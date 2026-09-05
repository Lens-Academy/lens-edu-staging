---
id: '7373a1ae-277f-4d6e-a937-7f2e1939fd6d'
reading_minutes: 8
tutor_minutes: 0
title: Recall threads, a proposal
tldr: "The course teaches its concepts once each and never asks for them again. This proposes fixing that by asking learners to search for what applies, rather than telling them which principle to use."
summary_for_tutor: "DRAFT, orphaned. An internal proposal document written as a lens so it can be read on the platform. Argues the theory of change behind adding retrieval prompts to AI Risk Fundamentals, and links two worked examples. Audience is the team, not learners. Not referenced by any module."
tags:
  - wip
authors:
  - Andreas+Claude
---

#### Text
content::
\## The problem

The book is modular in structure, but its concepts thread across parts without being called back in a linear consumption of the book. There is an implicit expectation that readers connect the sections themselves, which most will not do unprompted. This proposal is to modify the existing learning experience to provide learners explicit opportunities to connect new knowledge to prior concepts.

The present iteration of the course exemplifies the flaws of a linear modular structure where each learning outcome is taught in the module where its chapter is read, tested at the end of that module, and never asked for again. A learner can complete the course having met every concept exactly once.

The proposed fix is not chapter cross-references. Telling someone which principle applies removes the work that makes the principle stick. The fix is to prompt people to search for the principles they have learned and then decide which ones are applicable. This results in user actively having to scour through the concepts they've previously learned and judge how they might be connected to or apply towards the concept they're currently encountering.

#### Text
content::
\## The structure now

%%
IMAGE SLOT. Replace the line below with the exported "before" drawing once it is hosted.
Lenses take standard markdown images only, and the target has to be a URL: the ![[...]]
embed form is not supported. The pattern the XLab lenses use is
  https://raw.githubusercontent.com/<org>/<repo>/main/public/<path>/<file>.png
Export the Excalidraw canvas to PNG or SVG, commit it there, and paste the raw URL.
Alt text should describe the ladder, not just say "diagram".
%%

*[Before diagram goes here]*

| Unit | Chapters | Outcomes | Notes |
|---|---|---|---|
| U1 | Intro, 1, 2 | 5 | |
| U2 | 3, 4, 5 | 4 | |
| U3 | 6, film for 7 to 9, Coda | 4 | Straddles the Part I and Part II boundary. Chapters 7, 8 and 9 carry no learning outcomes at all with the film |
| U4 | 10, 11 | 4 | |
| U5 | 12, 13, 14, Closing Words | 6 | |

Two things this table is meant to make visible. U3 is the only unit whose bracket does not sit inside a single part of the book, and it is also the unit carrying three chapters with no learning outcome attached to any of them. Instrumental convergence sits in that gap: the outcome exists in the vault at [[../Learning Outcomes/Instrumental sub-goal convergence]] and no module references it.

#### Text
content::
\## The structure proposed

%%
IMAGE SLOT. Same instructions as above, for the "after" drawing with the recall threads.
%%

*[After diagram goes here]*

| Unit | Chapters | Outcomes | Change |
|---|---|---|---|
| Intro | Introduction | 1 | Pulled into its own section, the way `intro-form` is used in [[../modules/XLab Verification Overview]] |
| U1 | 1, 2, 3 | 5 | |
| U2 | 4, 5, 6 | 5 | Chapter 6 refolds, so the unit sits inside Part I |
| U3 | Chapter 4 and 5 extensions, film for 7 and 8, 9, Coda | 4 | The film covers 7 and 8 only, so Chapter 9 returns as a reading. Two new outcomes in the form of instrumental convergence and cosmic stakes |
| U4 | 10, 11 | 4 | |
| U5 | 12, 13, 14, Closing Words | 6 | |

Every unit now sits inside one part of the book, with one deliberate exception: U3 opens on the Chapter 4 and 5 extension readings, which are Part I material used as a bridge into the scenario.

%%
The colored lines on the after diagram are the recall threads. There are ten of them, grouped into five families, and two terminate on outcomes that do not exist yet. Both of those are in U3. The full list, and what we would build for each, is in the next section.
%%

#### Text
content::
\## What we found when we looked

Three things, in increasing order of how much they surprised us.

**The course already has a check for this, and almost nothing passes it.** [[../AI Guide/Evals/Learning Outcome Evals/B1 - Answerable without the text]] asks whether a question could be posed to someone who has the capability but never read the assigned text, with the pass boundary being that it could be asked at a random moment. In the census recorded at [[../AI Guide/Evals/Learning Outcome Evals/Run Reports/2026-08-24 Run]], 22 of the 23 active learning outcomes in this course failed it. Every test is scaffolded on its own chapter, so none of them can be asked cold.

**The course already does this correctly, in one dimension.** Your Leverage, Talk to One Person, How Did It Go and Your Ongoing Action form an arc across four modules that explicitly reopens itself: the welcome text of the fourth module returns the learner to the commitment they made in the third. The behavioral thread calls itself back. The conceptual threads do not. We are proposing to do to the concepts what someone already did to the action plan.

**One lens states the pattern backwards.** In [[../Lenses/IABIED - One Extinction Scenario (Video)]], the tutor brief instructs the AI to test whether the learner's objection attacks the underlying mechanism, and then names the three mechanisms it should test against. Three units of prior learning, listed precisely, addressed to the tutor. The learner is asked which step they found hardest to believe, and is required to retrieve nothing.

#### Text
content::
\## The design pattern

That last finding is the whole proposal in one file. The repair is to swap which side holds the answer.

**The learner-facing prompt names nothing.** It says that something earlier applies here and asks which. It does not say which chapter, which concept, or how many candidates there are.

**The tutor-facing brief carries the key.** It states the target answer, the near misses worth accepting, the answers that are actually this chapter's own material, and what to do when the learner draws a blank: one narrowing hint, then name it and move on rather than turning the beat into a review session.

This costs one segment per thread and no new reading. It is also cheap to get wrong in a specific way: if the brief lets the tutor supply the answer early, the prompt becomes a cross-reference with extra steps, which is the thing we are trying not to build.

We think the beats belong at unit boundaries and at the points where a unit has no new reading of its own, because those are the moments when retrieval is the only work available.

#### Text
content::
\## Which links become prompts

Not every connection in the book earns a prompt. Three rules decided this list.

**A prompt needs an outcome anchor at both ends.** A link between two chapters is not enough. If the earlier end has no learning outcome, there is nothing the learner was assessed on and nothing for the tutor to key against, so the link is a proposal for a new outcome rather than a prompt.

**Within-unit links are prerequisites, not prompts.** Reading two chapters in the same week already carries the connection. Declaring those edges adds bookkeeping, and since prerequisites gate locked status, it also risks locking learners who read out of order.

**The prompt lives at the target, not on the line.** This is what makes the work tractable. Ten threads are not ten new files. They are one added segment in each target lens, and where two threads share a target they share a segment.

\### The ten threads

| Thread | From | To | What gets built | Status |
|---|---|---|---|---|
| Goals | Intro, hard vs. easy calls | Goals and instrumental convergence | One segment in the new U3 opener, carrying both incoming threads | Outcome to write |
| Goals | Ch 5, goal-space argument | Goals and instrumental convergence | Same segment as above | Outcome to write |
| Goals | Ch 5, hostile vs. indifferent | Ch 9, cosmic stakes | Split across the pre-reading prediction and the closing comparison | Drafted |
| Method | Intro, hard vs. easy calls | Coda, path vs. outcome | One segment in the Coda lens | Not started |
| Training and values | Ch 2, behavior vs. values | Ch 4, you don't get what you train for | One segment in the Chapter 4 lens | Drafted |
| Training and values | Ch 2, grown not crafted | Ch 11, alignment as alchemy | One segment in [[../Lenses/IABIED - Alchemy Not Science]] | Not started |
| Training and values | Ch 3, wanting emerges from training | Ch 11, superalignment objection | One segment in [[../Lenses/IABIED - Strong Superalignment Objection]], which is a separate lens | Not started |
| Capability | Ch 1, prediction plus steering | Ch 6, Aztec warrior | One segment in the Aztec warrior lens | Not started |
| Capability | Ch 1, machine advantages | Ch 10, five curses | One segment in the five curses lens, keyed on the curse of speed | Not started |
| Unrepeatability | Ch 10, five curses | Ch 12, one-chance problem | One segment in the one-chance problem lens, keyed on Chernobyl appearing twice for different reasons | Not started |

Ten threads land on nine target lenses. Only the two goals threads share a target, because the new U3 opener is one lens carrying one outcome; Chapter 11's two outcomes are taught in two separate lenses, so they need a segment each. The build is nine added segments, two of which are drafted, plus the two new U3 outcomes.

#### Text
content::
\## Links we looked at and did not adopt

Recording these so the same ground does not get re-argued.

**The Coda into Chapter 13.** We first proposed that the Coda's path-versus-outcome discipline should be recalled when weighing the book's own proposals for what to do. On a closer reading the Coda's claim is narrower: depicting a world containing superintelligence realistically is what makes any particular depiction unlikely. That points back at the film, not forward at Chapter 13. Dropped.

**Chapter 6 into Chapter 12, on irreversibility.** Real as a chapter-level thread, and it fails the both-ends rule. Chapter 6's outcomes are the Aztec warrior analogy and the refrigerator thought experiment, neither of which is about there being no second attempt. The same ground is already carried by the Chapter 10 into Chapter 12 thread, which is anchored at both ends, so we are leaving this one untethered rather than writing a Chapter 6 outcome to hold it up.

**Fiction as argument, not prediction.** This outcome receives no thread, and we think that is correct rather than a hole. It synthesises several Part I ideas without resting on any one of them, so anchoring it would mean inventing a dependency the book does not have.

**U5 as a whole.** Five of the six outcomes in the final unit have no thread reaching them, which looks alarming on the diagram. Our reading is that it is a property of the book rather than a defect in the course. Parts I and II establish what the problem is; Part III argues what should be done about it, and those overlap less than the diagram's emptiness suggests. What U5 actually depends on is the conclusion of the whole argument rather than any individual concept from it, and that dependency is already tested in one place: the synthesis question in the final module, where the student presents the chain unaided. If we are wrong about this, the fix is not more threads into U5 but a closer look at that one synthesis question, which is currently tagged work in progress.

#### Text
content::
\## Two worked examples

::card[[DRAFT - Ch4 with Connection]]

> The smallest version. One retrieval beat inserted into an existing five-beat reading lens, everything else untouched, so the diff is the proposal.

---

{--{"author":"AI","timestamp":1788617518416}@@::card[[../_deprecated/DRAFT - Ch9 Cosmic Stakes - PQ - MERGED]]

> The prediction half. Taken straight after the film ends, before the chapter is read, so the chapter meets a committed prior instead of a blank page.

---

--}::card[[../Lenses/DRAFT - Ch9 Cosmic Stakes (from film lens)]]

> The other kind. A new lens for material the film leaves out, built as a pair with the film {--{"author":"AI","timestamp":1788617518416}@@lens so--}{++{"author":"AI","timestamp":1788617518416}@@lens. Takes a prediction before++} the {--{"author":"AI","timestamp":1788617518416}@@scenario--}{++{"author":"AI","timestamp":1788617518416}@@reading++} and {--{"author":"AI","timestamp":1788617518416}@@its endpoint read as one unit. Closes by returning the learner to their own prediction.--}{++{"author":"AI","timestamp":1788617518416}@@returns the learner to it afterwards, so the chapter meets a committed prior instead of a blank page.++}

---

::card[[../Learning Outcomes/DRAFT - Cosmic stakes]]

> The outcome those two lenses teach toward. Its test question is written to pass B1, which none of the course's existing questions currently do.

#### Text
content::
\## What this proposal does not settle

Four open questions, all of which need a decision from someone other than the author.

**Assessment load.** Every retrieval beat is another tutor conversation. We have not costed what that does to a unit's total time, and U1 and U2 are already the units learners describe as heavy.

**The pending eval fixes.** The fix pass recorded at [[../AI Guide/Evals/Learning Outcome Evals/Run Reports/2026-08-24 Fix Pass]] produced repairs for 46 outcome files as pending suggestions. We do not know whether they have been accepted. Two of the threads proposed here terminate on outcomes named in that batch.

**Whether the extension readings move or duplicate.** The instrumental convergence passage is currently optional material under Chapters 6 and 8. Making it required earlier means either moving it or having it appear twice. Optional first and required later is spaced repetition by construction, but it can also read as padding.

**Version control.** These drafts are orphaned and tagged wip precisely because we do not yet know what the review path looks like for changes of this size.
