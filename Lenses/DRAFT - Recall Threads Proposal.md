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
  - "TODO+Claude"
---

#### Text
content::
\## The problem

The book is modular in structure, but its concepts thread across parts without being called back. There is an implicit expectation that readers connect the sections themselves, which most will not do unprompted.

Our course inherits that shape and adds a second layer of the same problem. Each learning outcome is taught in the module where its chapter is read, tested at the end of that module, and never asked for again. A learner can complete the course having met every concept exactly once.

The proposed fix is not chapter cross-references. Telling someone which principle applies removes the work that makes the principle stick. The fix is to prompt people to search for the principles they have learned and then decide which ones are applicable.

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
\## Two worked examples

::card[[../Lenses/DRAFT - Ch4 with Reach-Back]]

> The smallest version. One retrieval beat inserted into an existing five-beat reading lens, everything else untouched, so the diff is the proposal.

---

::card[[../Lenses/DRAFT - Ch9 Cosmic Stakes (from film lens)]]

> The other kind. A new lens for material the film leaves out, built as a pair with the film lens so the scenario and its endpoint read as one unit.

#### Text
content::
\## What this proposal does not settle

Four open questions, all of which need a decision from someone other than the author.

**Assessment load.** Every retrieval beat is another tutor conversation. We have not costed what that does to a unit's total time, and U1 and U2 are already the units learners describe as heavy.

**The pending eval fixes.** The fix pass recorded at [[../AI Guide/Evals/Learning Outcome Evals/Run Reports/2026-08-24 Fix Pass]] produced repairs for 46 outcome files as pending suggestions. We do not know whether they have been accepted. Two of the threads proposed here terminate on outcomes named in that batch.

**Whether the extension readings move or duplicate.** The instrumental convergence passage is currently optional material under Chapters 6 and 8. Making it required earlier means either moving it or having it appear twice. Optional first and required later is spaced repetition by construction, but it can also read as padding.

**Version control.** These drafts are orphaned and tagged wip precisely because we do not yet know what the review path looks like for changes of this size.
