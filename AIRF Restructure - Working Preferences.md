---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# AIRF Restructure: working preferences

Companion to [[AIRF Restructure Log]]. The log holds decisions and history. This holds the taste behind them, which is the part that does not survive a new conversation and otherwise gets re-litigated from scratch.

Written at the end of stage 2, from what Andreas corrected over the course of stages 0 to 2.

## How to work

**One thing at a time, with review between.** Andreas checks each change on staging before the next one starts. Do not batch several edits and present them together; file one, say what it was, stop.

**Say how each edit actually landed.** The relay routes some edits to the review queue and applies others directly, and it does not always do what you expect. Read the tool result and report `direct` or `pending` every time. Claiming something was filed as a suggestion when it was not is worse than the direct edit itself.

**Edits to files we did not write go in as suggestions.** If the relay applies one directly anyway, say so immediately so it can be reverted. If a whole rewrite would land direct, append it in a comment block at the bottom for manual substitution instead of overwriting.

**Verify against the vault; do not assert from memory.** Andreas checks. Several claims made confidently in stage 1 turned out wrong: that three lens filenames were a rename risk when they were orphans, that `intro-form` marked a module as introductory when it hosts an intake form, that the restructure broke `Fiction as argument` when it repairs it. Each cost a round trip. Grep first.

**Do not invent attributions.** Authorship was guessed as "Elias+Claude" on three files with no basis, and Elias is someone else. Ask.

**Expect to be corrected, and correct back.** Andreas overrides roughly as often as he agrees, and his reasoning is usually better. He also expects disagreement where there is a reason for it. Deferring to a worse idea is not politeness.

## How to write learner-facing text

**Scenario framings over abstract prompts.** Every question that landed well names a concrete situation: two people with unrelated goals, a lab handing a model a long-horizon objective, someone offering you four bets. Every version that got rewritten asked directly for an explanation.

**Elicit before instructing.** Where a concept already exists in ordinary experience, ask for it before the reading names it. The gap between what the learner found and what the text names is the lesson.

**Ground the example.** "Cure for cancer" beat an abstract long-horizon goal. Tractable beats clever, every time.

**No reassurance clauses.** "Obvious answers are fine, no need to strain for clever ones" was cut because it implies a clever tier exists. If the worry is that a learner will withhold a thin answer, give a quantity cue instead: "two or three is plenty."

**Never label something the learner cannot resolve.** No module numbers, no "as Chapter 5 argues". If the tutor needs the precise reference, put it in the brief and tell it not to say the label aloud.

**Cut rather than expand.** When something reads badly, the first move is to delete it, not to reword it. Comment blocks especially.

## How to write tutor briefs

**The learner-facing prompt names nothing; the brief carries the key.** This is the whole design. A brief that hands the tutor a list of mechanisms and asks it to check the learner's answer against them has inverted the thing we are building.

**Cap the rescue.** One narrowing hint, then name it and move on. A tutor that supplies the answer early turns a recall prompt into a cross-reference with extra steps.

**Mirror the question's structure.** If the question says take each claim in turn, give each claim its own entry. Bundling two because the mechanism is the same leaves the tutor without guidance when a learner splits them.

**Score the confident wrong answer as wrong.** Where a question has a trap, put the trap at level 1 explicitly rather than letting it read as partial credit.

**Say what not to do.** Every brief that works has a list of prohibitions as long as its instructions.

## Naming

Titles and slugs are display-level and cheap to change; do not spend a round trip agonising. But two tests do get applied:

**Does the name reflect the weight of the content?** Meeting 1 is "Intro and Nonhuman Minds, Part 1" because the Introduction is genuinely the lighter half. Meeting 5 gained "and Next Steps" because M7 is not.

**Does the word point the right way?** "Aftermath" was rejected for a closing session as backward-looking, against a course that spends its last chapter arguing the opposite.

## Other people's material

**Answer notes, do not delete them.** Where a CriticMarkup note argues against a decision we have taken, record the counter-argument in the log and leave the note in place. Applies to the chapter 6 move note and to Luc's duplication note at the chapter 5 lenses.

**Leave other courses' files alone.** Three convergence-adjacent outcomes were touched in planning and all three were dropped from scope: two belong to other courses, one is a superseded artifact worth keeping for posterity. Do not backlink from AIRF planning docs into other courses' files either.

**Prefer writing fresh to inheriting confusion.** The orphaned chapter 8 outcome could have been rewritten. It was not, because its statement was unintelligible to learners who took the course, and inheriting it would have inherited that.
