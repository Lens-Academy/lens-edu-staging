---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV1 plain language worklist

Stage 6 of [[CV1 Restructure Log]]. Claude marks what is Lens's text, tests every tldr for spoilers, and flags the Lens text that most needs rewriting; Andreas rewrites (A4); Claude then reviews the rewrite and checks any feedback brief or quoted claim it touches. Scope (A36): learner-facing text in CV1's 49 lenses, the overview and the five unit welcomes. Tutor summaries and feedback briefs are out, and so are articles and widgets.

**Status, 2026-10-26.** The pilot, "Who can prove what", is rewritten and reviewed; its two flags come off once Andreas accepts their removal. The other pages are next.

## How to read an entry

- **Lens's text** lists the passages that are ours, by line in the lens file. Everything else on the page is XLab's.
- **Spoiler test** says whether the tldr hands over a result the page asks the learner to reach.
- **Flags** are comments on the passage in the lens, except tldr flags, which live here: a tldr sits in the page's frontmatter, where a comment would break it.
- **For Andreas and Elias** lists XLab passages that fail a clarity check (step 4). Each also goes to XLab's feedback form, once it is settled where feedback goes (log, section 9).
- **Left for stage 7** notes what this pass saw but leaves to the consistency pass: section numbers, "week", XLab framing.

## How Lens's text is found

Each paragraph is compared with every version of XLab's verification source in its public repository, history included, since XLab has rewritten some lessons since the port. A paragraph is XLab's if at least 80% of its five-word runs appear there, edited XLab text from 30% to 80%, and Lens's below 30%. Every edited paragraph is then read against its closest XLab source by hand. Minor edits (labels, spelling, "Optional:", a link) leave it XLab's (A36). A prompt or key rebuilt from an XLab widget counts as Lens's where its wording is ours; where it reassembles XLab's own strings from the widget's data, as this page's actor roster does, it stays XLab's. Headings and callout titles we added are Lens's. Works cited callouts are left alone.

## Checks a flag can cite

- **tldr** ([[AI Guide/Writing Lenses]]): at most 80 words, written to the learner. More than one sentence is fine when the content needs it, but concision still matters (A37).
- **Punctuation** ([[AI Guide/Course Authoring]]): no semicolons, no em dashes.
- **Mannered prose** (Course Authoring): use the literal phrase where one is available. An analogy that reads plainly can stay; one that needs decoding is flagged.
- **Self-contained**: never label something the learner cannot resolve (Andreas's working preferences).
- **Spoiler test** (the proposal, stage 6 step 2): a tldr shows in the lens navigation before the page is opened, and the tutor receives it as context.
- **General habits** the guides do not name, such as "X, not Y" framing, verdict lines or stacked colon clauses, are named in the flag itself.

## Pages

Rough shares from the comparison, before the reading by hand. "Edited" includes XLab text reassembled from widget data, which mostly stays XLab's.

| Unit | Page | Words | Lens's | Edited | Status |
|---|---|---|---|---|---|
| 1 | Welcome | 657 | 97 | 0 | |
| 1 | Introduction: Why Should You Care About AI Verification? | 2,475 | 270 | 378 | |
| 1 | AI Is Grown, Not Built | 531 | 531 | 0 | |
| 1 | Four Background Claims | 57 | 57 | 0 | |
| 1 | Why Securitizing AI Is Difficult but Necessary | 776 | 191 | 50 | |
| 1 | We Need More Theories of Change | 1,738 | 428 | 108 | |
| 1 | Building Verification Intuitions | 398 | 131 | 79 | |
| 1 | Read Plan A's Verification Plan | 82 | 82 | 0 | |
| 1 | Option A: Stress-test Plan A's Verification Regime | 948 | 122 | 88 | |
| 1 | Option B: Compare Plan A and Plan S | 892 | 142 | 56 | |
| 1 | Optional: Further Exploration | 1,126 | 387 | 260 | |
| 1 | Primer Practice: Inspection, Commitment, and Logic | 724 | 0 | 622 | |
| 2 | History, Precedents, Parallels | 3,493 | 185 | 1,236 | |
| 2 | Introduction: what kind of policy are we trying to verify? | 1,179 | 79 | 330 | |
| 2 | Drawing the Line: Compute vs. Capability | 1,314 | 510 | 27 | |
| 2 | Policies must be effective and feasible | 2,239 | 80 | 1,065 | |
| 2 | Strategic Foundations | 407 | 116 | 247 | |
| 2 | The seven Strategic Foundations reading pages and the written exercise | 720 | 372 | 134 | |
| 3 | How an agreement is put together | 507 | 101 | 220 | |
| 3 | Reading a draft agreement | 1,184 | 130 | 353 | |
| 3 | MIRI's draft agreement (paper page) | 161 | 123 | 38 | |
| 3 | Actors: who does the treaty rely upon, apply to, and constrain? | 5,727 | 509 | 1,240 | |
| 3 | Geographic supply-chain map | 916 | 380 | 76 | |
| 3 | Who can prove what | 2,699 | 166 | 1,130 | Done (pilot) |
| 4 | Upstream and downstream | 1,436 | 182 | 0 | |
| 4 | Context distiller | 790 | 98 | 268 | |
| 4 | The four report pages | 2,089 | 255 | 432 | |
| 4 | The Distiller | 9,620 | 274 | 5,220 | |
| 4 | What makes a verification mechanism effective? | 1,362 | 210 | 448 | |
| 4 | Privacy-Preserving Mechanisms | 1,603 | 502 | 266 | |
| 5 | Hardware | 771 | 275 | 90 | |
| 5 | Start with the claim, not the mechanism | 351 | 60 | 0 | |
| 5 | From a chip to a trusted statement | 1,091 | 169 | 0 | |
| 5 | Accounting for hardware | 713 | 121 | 100 | |
| 5 | Measuring and classifying use | 839 | 162 | 152 | |
| 5 | Authorization, licensing, and control | 656 | 143 | 81 | |
| 5 | Where should trust live? | 1,147 | 346 | 64 | |
| 5 | Reconstructing a declared training run | 676 | 144 | 38 | |
| 5 | Open problems: verifying and securing compute | 110 | 110 | 0 | |

The overview and the five unit welcomes are inline in their modules and are not in this count.

## Unit 3: Who can prove what (pilot)

[[Lenses/XLab Verification - v-actor-edges]]. Almost all of the page is XLab's: the brief, the rules for drawing an edge, the reading of the map, the "Why" callout and the three questions. The actor roster in the first callout reassembles XLab's own actor data and stays XLab's.

**Lens's text**

- Line 4, the tldr.
- Line 49, the opening of the roster callout ("Reference for the workshop below: …").
- Line 80, the parenthetical in "The six functional roles" ("the role chips in the workshop, which appear once you commit, light the actors that hold one"). The role definitions after it are XLab's.
- The headings and callout titles we added: "The four things a verifier has to establish (Baker et al., §3.2)", "The 17 actors (open any time)", "Where this regime is weakest (open after you have answered)", "Why (open after you have answered)". They pass.

**Spoiler test.** Fails. The tldr's last sentence, "Ten of seventeen actors have no arrow at all, and one chip designer is holding up three of the four subgoals", gives the two findings the widget's reveal and the closed "Where this regime is weakest" callout hold back until the learner has drawn the edges.

**tldr flags**

- The spoiler above.
- A semicolon in the first sentence ("not something an actor has; it is an arrow"), against Course Authoring.
- The first sentence is "X, not Y" framing with a metaphor ("an arrow between two of them") and a colon clause after it. It retells the page's own opening paragraph, which is XLab's and already says this in plain words.
- "The board you built in 1.2" is left for stage 7 (section number).

**Flags on the page**

- Line 49: opens with a fragment and runs three colon clauses in two sentences; "the cast" is a label the page does not define.
- Line 80: "role chips" is a widget label the learner has not seen yet, and "light the actors" stands for "highlight them".

**Outcome, 2026-10-25 to 2026-10-26.** Andreas rewrote the tldr and the roster's opening, and Claude reviewed both: a typo, a comma splice, "submodule" (unit 3 has none) and a missing comma, all fixed by Andreas. The tldr now ends "count which actors have no arrow at all, and find out who is holding up three of the four subgoals", which keeps the question and drops the answers; Andreas keeps "find out who" for intrigue, and it passes the spoiler test. The roles and postures went from two run-on paragraphs to bulleted lists, XLab's words unchanged (XLab's lesson has them as a table), and the "role chips" parenthetical was dropped, since the top of the callout already gives the context and learners never see widget names (Andreas). Both flags resolved; their removal is pending.

**For Andreas and Elias**

- Lines 181 to 182, in "Notes and sources": "Quotations are matched against the committed copy of the paper at test time, so a quote that drifts fails the build rather than sitting on the page." This describes XLab's build, which Lens does not have, so on our page it is not true. Candidate: cut the sentence.

**Left for stage 7**

- "1.2" throughout (section numbers), "Week 5" on lines 20 and 183, and "1.2.2" in the Works cited title, which is a citation and stays.
