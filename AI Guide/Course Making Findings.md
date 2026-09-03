# Course-making: findings and advice

Advice for making Lens courses, collected from three days of work (2026-08-28 to
08-31) by Lauren working with AI; one of the AI instances assembled this file.

This file is written in plain language on purpose. A writing guide should pass
its own checks. The denser working discussion behind it lives in the project
repo's docs folder; this is the version for people.

Each piece of advice is labeled with how we know it:

  [measured]  we counted or tested it; carries command, corpus, and date,
              or it gets downgraded to [reported]. (Rule added 2026-09-04
              after a verification pass found three of six [measured]
              numbers had changed meaning while being copied from prose
              summaries of the measurement rather than from its output.)
  [reported]  someone measured it once, but the trail to the measurement
              is incomplete
  [edits]     taken from Lauren's hand edits to Unit 1; before/after quotes
              are in course-writing-generators.md
  [standard]  taken from ASD-STE100, an aerospace writing standard we
              extracted into asd-ste100-rules.md (54 rules)
  [student]   said by a student, Andreas, in a feedback call
              (~/inbox/andreas_call.txt)
  [proposed]  we believe this but have not tried it on a real unit yet
  [guess]     speculation, kept because someone can check it
  [FORK]      a decision Lauren has not made yet; not settled

---

## 1. Three root causes of course defects

A "root cause" here means: one upstream mistake that produces many visible
problems. For example, Andreas gave about six complaints. They trace back to three causes,
which look identical to a student but need different repairs.

CAUSE 1: The goal was never written down. [measured] Nowhere in the repo is
there a statement of what changes in a graduate of this course. ("What they
can do after that they could not before" is the checkable projection of
that.) Without it, the weekshave  nothing to be ordered against, claims
about who the course is for cannot be checked, and an assessment cannot be
checked against what was meant to be taught. Andreas felt all
three: "you could start from week three... you wouldn't be missing much," and
"there are two groups: people who feel it's too technical, and people who feel
it's not technical enough." [student]
REPAIR: before writing content, write the capability statement: how the
student differs before and after, broken into parts.

CAUSE 2: Material was written but never connected. [measured] 179 of 787
lenses (22%) are not reachable from any course. 78 of them were written for
this course. They include the exact practice exercises Andreas said were
missing. Nobody deleted them; they were written and never added to a module,
and nothing complained.
REPAIR: make unconnected content an error the tools report, instead of a
silent success. Run the unreachable-content check before asking anyone for
feedback: it is one command, and here it would have surfaced the biggest
student complaint plus 77 similar cases without needing a student.

CAUSE 3: A good design shipped in Unit 1 and later units were built without
it. [measured 2026-09-04, closing-check.py structure count on production,
all five modules, inline lenses included] The design decayed in two steps:
Unit 1 has the full revision ASK ("Revision 1": restate your model from
memory, then change it); Unit 2 kept only a closing SUMMARY (a Text-only
"Closing" lens -- recap prose, nothing the student does); Units 3 and 4
have nothing; Unit 5 has one stray revisit-question. Ask, then summary,
then absent. (This paragraph was corrected twice tonight as instruments
improved -- word-count proxy, then file-walk, then inline-lens-aware walk
each gave different answers; the run record explains.) Andreas was in week 3 when he
said "there's no closing section... that step currently isn't there."
[student] The design existed only as prose and examples, so it did not carry.
REPAIR: turn the design into a checklist that is actually run on every new
unit (see section 4).

If you have preexisting feedback, then for that feedback -- how to find
root causes, in general: for each complaint, ask
"what one upstream mistake would produce this, and what else would it
produce?" Then go count whether those other things exist. If they do, you
found the cause (here: one missing exercise led us to 78). If they do not,
it was a coincidence; stop. [measured once, on this call]
Warning: an explanation that fits every complaint feels finished and often is
not. Both Claudes built tidy explanations this week that were wrong, and each
was caught only by checking a prediction. Always test one thing nobody
reported. (This is kin to classic root-cause analysis and the "5 whys",
plus the step those leave out: verify the cause by counting the other
problems it predicts.)

## 2. Four kinds of text in a course, and how to tell them apart

The test: delete the sentence. If the student's required action changes, or
the tutor's grading changes, the sentence is an INSTRUCTION. If only the
student's motivation changes, it is EXPLANATION. [proposed, but three
independent sources draw the same line: Lauren's edits, Rune's analysis, and
the ASD-STE100 standard, which has separate rule sections for procedural and
descriptive writing] [standard]

1. INSTRUCTIONS -- what to do, what to write, how it is graded. Write these
   plainly and identically everywhere: command form, 20 words or fewer per
   sentence, one instruction per sentence, active voice. [standard]
   A possible bonus [guess, needs Lauren's yes]: plain instructions carry no
   authorial voice, so they may not need the human rewrite that explanation
   text needs. If true, the rewrite workload drops by roughly half.

2. EXPLANATION -- why any of this matters. This carries the author's voice.
   Do not force it into the instruction style; readers stop reading. It has
   its own rules (section 3). Plan update (2026-09-01): AI writers produce
   this text too, with humans reviewing and spot-fixing. Hand-rewriting by
   a human is slow even done fast, and is no longer the plan.

3. QUOTED MATERIAL -- article excerpts, and arguments we construct for the
   student to examine. Its rules are about labeling and accuracy, not style:
   say what the material is ("this argument is constructed; every fact in
   it is true"), and quote sources exactly. Do not count it as our
   explanation text. [proposed]

4. WORKED EXAMPLES -- the author using a principle on a small case, in front
   of the student. This kind was missing entirely, and it was the student's
   biggest complaint: "you're learning the principles, but you're not seeing
   them applied... what am I supposed to DO with the knowledge?" [student]
   Each principle should appear three times: the author works an example;
   the student applies it to an easy case (his example: Waymo in San
   Francisco, not AGI timelines); the student then uses it in their own
   growing model. [proposed] Note: much of this material already exists in
   the 78 unconnected lenses. Connect before writing more.

## 3. Rules a reviewer can check with yes or no

The useful property of a rule is that one person can check one page and
answer yes or no, without reading the rest of the course. Rules of that shape
can be split among reviewers. Three groups:

(a) For INSTRUCTION sentences: the ASD-STE100 rules above. [standard]

(b) For EVERY sentence, including explanation [edits -- each of these is
    something Lauren repeatedly fixed by hand]:
    1. Every guess-first question names the fact that will settle it.
       Otherwise it is a reflection prompt pretending to be forecasting.
    2. Every number carries its unit, every time it appears. ("A 4-hour
       task" misleads unless it says human-hours.)
    3. No sentence tells the reader how to feel about the current page.
       (Pointing forward is fine: "by the end of the course you will...")
    4. Do not vouch for a source ("METR is independent..."). Turn the
       vouching into a question the student answers.
    5. No either-or question unless the two options really are the only
       options.
    6. Define terms where they first appear. Say when the fuller treatment
       comes. No footnotes.
    7. Every task has an easy version and a stretch version, so partial
       work is still work. Never three requirements joined by commas.
    8. Every forecast question also asks: what would change your mind?

(c) For EXPLANATION text, rules that limit cost without dictating style
    [proposed]:
    - Any instruction that appears inside explanation text must also appear
      as a plain instruction. (Otherwise skimming students miss it.)
    - A word budget for explanation text per lens. [guess: around 40
      percent; measure the good lenses before fixing a number]
    - Every metaphor is explained in plain terms within the same block.
    - Run the difficulty tool (below); every flagged hard word is either a
      defined term, a name, or has a stated reason to be there.

What cannot be made into a yes/no rule -- say so and name who judges it,
instead of pretending: whether the writing lands (Lauren judges; suggestive
evidence: a small model-reader collapsed mid-read on AI prose in 4 of 7
runs and on Lauren's or Spiral-rewritten prose in 0 of 10 -- small n,
details in the spiral-and-roundtrip notes); whether the
voice is hers (only she can write that); and choosing what to say in the
first place (rules check writing; they do not produce it -- that is what
course-writing-generators.md is for).

## 4. Checks to run on a course, cheapest first

1. Unreachable-content check (see cause 2). One command. [measured]
2. Term check: for every technical term, is its first use after its
   introduction? [measured 2026-09-04, production, student order: "METR"
   has 14 mentions; the first introduction is at mention 7 -- six uses
   before any introduction -- and that introduction ("METR is an
   independent organisation...") is itself the vouching rule 3(b)4
   forbids. An earlier count, "18 times, introduced nowhere", was one
   article's count from three weeks and one rebuild earlier.]
3. Promise check: does the course landing page match what the weeks
   actually contain? Andreas signed up for forecasting and hit policy in
   week 3. [student]
4. Template check: every lens follows frame / try it / read / compare /
   close, or carries a one-line stated reason why not. [proposed]
   [FORK, for Lauren: should deviation be impossible by construction, or
   allowed with a stated reason? Both Claudes now lean "allowed with a
   stated reason," because rules that cannot bend get abandoned wholesale.
   Not yet ruled on.]
5. Outcome check: for each learning outcome, name the page where the
   student performs it on something other than their own final model.
   Missing = fail. [proposed]
6. Effort labels: every question says how long to spend, from a short list
   (10 seconds / 5 minutes / 30 minutes of research). Unlabeled = fail.
   Students currently guess, and arrive at discussion having done wildly
   different amounts of work. [student, and Lauren proposed the labels in
   the same call]
7. Student walk-through: two fresh readers -- one technical, one not --
   actually do the course in order, and file a complaint at every point
   where they do not know what to do, how hard to try, or why this page
   follows the last. [proposed] This is the only check on this list that
   finds problems that are not visible in the files. We tested this the
   hard way: nine defects were predicted by reading the files, and the
   student's three biggest complaints were not among them. [reported --
   the nine-guess list has not been re-traced to its transcript]

## 5. Tools, and their limits

- `prose` (surprisal tool): shows which words a limited reader stumbles on,
  hardest first. Use it to see where a page spends the reader's effort.
  Never chase a low score: meaningless filler scores better than any real
  writing, and making a sentence more precise makes the score worse.
  [measured]
- `prose-orphans`: flags expensive words used once and never explained.
  Its first real catch: a bare surname, never introduced. [measured]
- Spiral (style rewriter): use the `personalize` command; `humanize`
  silently returns your input unchanged. After any rewrite, compare the
  meaning line by line, not just the tone -- a style pass once changed
  facts while reading as a light edit (that case was a different
  rewriter, not Spiral; the lesson transfers). [measured]
  Note 2026-09-04: the prose tools were lost from the shared repo for
  four days without anyone noticing (recovered from kept commits) --
  cite a tool only after checking it exists.

## 6. What this file does not cover, honestly

- How to write well in the first place. That is course-writing-generators.md
  (before/after pairs from Lauren's edits, with the lesson behind each).
- The full working order (write -> check -> rewrite -> style pass) is
  proposed but has not been tried end to end on any unit.
- Nothing here has repaired a unit yet. The first repair should be
  connecting the 78 orphaned practice lenses into the modules the student
  walked: it is the cheapest test of everything above, and if this file is
  right, it resolves his biggest complaint with no new writing.
