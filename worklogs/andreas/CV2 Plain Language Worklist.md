---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV2 plain language worklist

Stage 7 of [[CV2 Streamlining Log]] and [[CV2 Streamlining Proposal]], in the format of [[CV1 Plain Language Worklist]] (A36). Claude marks what is Lens's text, tests every tldr for spoilers, and flags the Lens text that most needs rewriting. Andreas rewrites. Claude then reviews each rewrite.

**Scope** (proposal, stage 7):

- every tldr
- the prompts and keys rebuilt from XLab widgets
- the questions Lens added on the cheating and taxonomy lenses
- the unit welcomes and the overview
- the other pass's new text
- the course-check flags carried in the log's section 6

Tutor summaries and feedback briefs are out (stage 6 did them), and so are articles and widgets. Em dashes, spelling, titles and "page" or "lens" are stage 8's mechanical passes, so they are noted under "Left for stage 8" rather than flagged.

**Status, 2026-11-25.** Unit 6 is flagged, with the course overview. Units 7 to 10 follow, one at a time.

## How to read an entry

- **Lens's text** lists the passages that are ours, by line in the lens file. Everything else on the lens is XLab's.
- **Spoiler test** says whether the tldr hands over a result the lens asks the learner to reach.
- **Flags** are comments on the passage in the lens, except tldr flags, which live here, because a tldr sits in the frontmatter, where a comment would break it.
- **For Andreas** lists XLab passages that read as a problem. XLab's text with only minor edits stays XLab's (A36).
- **Left for stage 8** notes what this pass saw but leaves to the mechanical passes.

## How Lens's text is found

Each learner-facing paragraph (tldr, text, question prompts and placeholders) was compared with every version of XLab's verification source in its repository, history included: the lessons, the widget data and the memo slots. Wrapped lines were joined first, since XLab's source is hard-wrapped. A paragraph is XLab's if at least 80% of its five-word runs appear there, edited from 30% to 80%, and Lens's below 30%, as in CV1. Edited paragraphs were then read with the words that are not in XLab marked. Works cited entries, source lines and headings count as Lens's in the table but are not reviewed as prose.

## Checks a flag can cite

- **tldr** ([[../../AI Guide/Writing Lenses]]): at most 80 words, written to the learner. More than one sentence is fine when the content needs it (A37).
- **Punctuation** ([[../../AI Guide/Course Authoring]]): no semicolons. Em dashes go in stage 8.
- **Mannered prose** (Course Authoring): use the literal phrase where one is available. An analogy that reads plainly can stay. One that needs decoding is flagged.
- **Self-contained**: never label something the learner cannot resolve (T6).
- **Course checks** in `Lens Edu/Checks`: T1 (term before it is explained), T2 (mic drop), T3 (talks like an LLM), T5 (false either-or), T7 (talks like opus5: intensifiers such as "actually" and "honestly", setups, "it isn't X, it's Y").
- **Content**: the text says something the lens does not do, or leaves out something the learner needs.

## Lenses

Words are learner-facing words. "Lens's" and "Edited" are rough shares from the comparison, before the reading by hand.

| Unit | Lens | Words | Lens's | Edited | Status |
|---|---|---|---|---|---|
| All | Course overview | 731 | 731 | 0 | Flagged |
| 6 | Welcome to Unit 6 | 68 | 68 | 0 | Passes |
| 6 | Policy judgment: what role should hardware play? | 1,093 | 197 | 122 | Flagged |
| 6 | Provider records and workload observables | 506 | 176 | 46 | Flagged (Content) |
| 6 | Customer identification and ongoing monitoring | 254 | 92 | 65 | tldr flag only |
| 7 | Welcome to Unit 7 | 62 | 62 | 0 | |
| 7 | Detection gaps and policy limits | 434 | 110 | 67 | |
| 7 | Interpreting cloud evidence | 308 | 136 | 53 | |
| 7 | Intelligence: watching without permission | 734 | 88 | 59 | |
| 7 | Observable signatures of undeclared AI development | 1,145 | 279 | 73 | |
| 7 | The empirical anchor: intelligence identifies, the regime resolves | 617 | 208 | 41 | |
| 7 | From signal to intelligence assessment | 473 | 169 | 0 | |
| 7 | From intelligence lead to verification action | 1,276 | 358 | 404 | |
| 8 | Welcome to Unit 8 | 73 | 73 | 0 | |
| 8 | The human layer | 242 | 87 | 0 | |
| 8 | Insiders and human sources | 1,118 | 351 | 307 | |
| 8 | Reporting and protection | 867 | 414 | 49 | |
| 8 | After the report arrives | 352 | 160 | 57 | |
| 8 | Audits and inspections | 824 | 293 | 130 | |
| 8 | Institutions and policy judgment | 1,035 | 193 | 330 | |
| 9 | Welcome to Unit 9 | 76 | 76 | 0 | |
| 9 | What is covert development? | 1,577 | 540 | 86 | |
| 9 | A system overview for near-term, low-trust AI compute verification | 1,286 | 388 | 271 | |
| 10 | Welcome to Unit 10 | 67 | 67 | 0 | |
| 10 | How could a determined actor cheat? | 1,613 | 441 | 119 | |
| 10 | Evasion scenario taxonomy | 811 | 191 | 114 | |
| 10 | Red team, blue team: from treaty requirements to a verification system | 2,198 | 1,092 | 221 | |

## Course overview

[[../../modules/XLab Verification Part 2 Overview]], inline. All of it is Lens's: XLab's own welcome is worded differently.

- **Lens's text:** everything (lines 10 to 48).
- **Spoiler test:** passes.
- **tldr flag:** "can honestly establish" (T7, intensifier). The rest reads well.
- **Flags on the page:** six.
    - Line 18, "must actually say" and "can honestly support" (T7).
    - Line 31, the Unit 6 box: "actually stand" (T7), and "ported to compute", which the welcome calls "carried over".
    - Line 35, the Unit 7 box: it opens on a fragment, has "who actually found" (T7), and "treaty text that protects sensors" needs decoding.
    - Line 39, the Unit 8 box: it opens on a verdict fragment (T2), and its second sentence takes two reads.
    - Line 43, the Unit 9 box, **Content:** "find the step where the conclusion outruns the proof" promises a task the close reading does not require. Only question 7 (one of four to choose from) and question 8 (optional) ask about weak points. The box also opens on a fragment.
    - Line 47, the Unit 10 box: "could actually carry" (T7), and "which it cannot touch" is mannered.
- **Left for stage 8:** the Alpha box and the first course's name (stage 8, item 1), and "defences" in the Unit 10 box.

## Unit 6: Hardware Judgment and Cloud Records

### Welcome to Unit 6

[[../../modules/XLab Verification Part 2 W06 Hardware judgment]], inline. Lens's throughout. **Passes**, and so does the tldr's spoiler test.

### Policy judgment: what role should hardware play?

[[../../Lenses/XLab Verification - v-hw-policy-studio]]. The maturity stages, the current assessment, the dossier, the brief's elements, the rubric and the resolution callout are XLab's.

- **Lens's text:**
    - the tldr
    - the graded question (line 116), the other pass's rewording of XLab's memo prompt
    - the two paragraphs before the ledger (lines 125 and 127), from the link pass
    - Works cited
- **Spoiler test:** passes. "The most common error is calling a demo a regime" repeats the lens's own warning (line 14), and it is not a result the learner has to reach.
- **tldr flags:**
    - It opens on a verdict line.
    - "The section's deliverable" is XLab's framing ("section") and jargon ("deliverable").
    - **Content:** "Then grade your opening-puzzle answers" is not what the lens asks. The learner classifies the seven conclusions again and compares the two ledgers. "Opening-puzzle" is also a label the learner meets only as the widget's title in Unit 5.
- **Flag on the page:** line 116. The question repeats the Prompt callout above it almost word for word, in one 77-word sentence. Its colon makes the two tasks after it read as if they were the eight elements.
- **Section 6's T1 flag on line 32** (XLab's bullet on authenticating devices): it passes, because "attestation", "confidential computing" and "configuration claims" are taught in Compute Verification 1, Unit 5, and the check cannot see that course.
- **Left for stage 8:** "the hardware pages" on line 127 points to other lenses (B15). The tldr's "section". The em dashes on lines 84 and 85.

### Provider records and workload observables

[[../../Lenses/XLab Verification - v-cloud]]. The objectives and the reading instructions are XLab's. Heim et al. is the article.

- **Lens's text:**
    - the tldr
    - line 28 (which reading does what)
    - the source and licence lines (40 to 44)
    - the lead-in to the explorer (line 106)
    - Works cited
- **Spoiler test:** passes.
- **tldr:** passes.
- **Flag on the page, Content:** line 106. The explorer is now required (B16) and finishes only when all fifteen signals are opened. Nothing on the lens says so, and the widget ticks opened rows without showing a count, so a learner can stall here without knowing why. The flag suggests one line.
- **Left for stage 8:** line 28's "on the next page" (B15).

### Customer identification and ongoing monitoring

[[../../Lenses/XLab Verification - v-cloud-customer-identification]]. Egan and Heim is the article. Our text is the tldr, the source lines, the Box 3 heading and Works cited.

- **Spoiler test:** passes.
- **tldr flag (minor):** "Egan and Heim port that playbook" stacks two borrowed metaphors (software "port", sports "playbook"). The literal version is shorter.
- **Page:** passes.
