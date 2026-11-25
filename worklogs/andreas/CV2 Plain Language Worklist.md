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

**Later on 2026-11-25.** Unit 7 is flagged. Eight tldr flags, one comment on the welcome, one on the signatures lens and five on the red-line lens, one of them Content (the "symmetric, cheap, and checkable" rule). One XLab passage is for Andreas. Two of Claude's comments on the red-line lens were corrected after posting, and the corrections are pending, because the relay treats an edit to a comment as a suggestion.

**Later on 2026-11-25.** Unit 8 is flagged. Five tldr flags, one of them a spoiler (Institutions and policy judgment) and one Content (Insiders: the warm-up reads as required). Two comments on the pages: the welcome (minor) and "Where a report can die". Two XLab passages are for Andreas. After the report arrives passes.

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
| 7 | Welcome to Unit 7 | 62 | 62 | 0 | Flagged |
| 7 | Detection gaps and policy limits | 434 | 110 | 67 | tldr flag only |
| 7 | Interpreting cloud evidence | 308 | 136 | 53 | tldr flag only |
| 7 | Intelligence: watching without permission | 734 | 88 | 59 | tldr flag, one XLab passage |
| 7 | Observable signatures of undeclared AI development | 1,145 | 279 | 73 | Flagged |
| 7 | The empirical anchor: intelligence identifies, the regime resolves | 617 | 208 | 41 | tldr flag only |
| 7 | From signal to intelligence assessment | 473 | 169 | 0 | tldr flag only |
| 7 | From intelligence lead to verification action | 1,276 | 358 | 404 | Flagged (Content) |
| 8 | Welcome to Unit 8 | 73 | 73 | 0 | Flagged (minor) |
| 8 | The human layer | 242 | 87 | 0 | tldr flag only |
| 8 | Insiders and human sources | 1,118 | 351 | 307 | Flagged |
| 8 | Reporting and protection | 867 | 414 | 49 | tldr flag, one XLab passage |
| 8 | After the report arrives | 352 | 160 | 57 | Passes |
| 8 | Audits and inspections | 824 | 293 | 130 | tldr flag only |
| 8 | Institutions and policy judgment | 1,035 | 193 | 330 | tldr flag (spoiler), one XLab passage |
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

## Unit 7: Cloud Limits and Intelligence

### Welcome to Unit 7

[[../../modules/XLab Verification Part 2 W07 Cloud limits]], inline. Lens's throughout.

- **Spoiler test:** passes.
- **Flag on the page:** line 18. "Actually proves" (T7), and the third bullet's "treaty text that protects sensors" needs decoding, as in the overview.

### Detection gaps and policy limits

[[../../Lenses/XLab Verification - v-cloud-detection-gaps]]. The reading instructions are mostly XLab's, lightly edited. RAND and Carnegie are the articles.

- **Lens's text:**
    - the tldr
    - the source lines
    - "Read the following excerpts:" twice
    - line 28's first clause (edited from XLab)
    - Works cited
- **Spoiler test:** passes.
- **tldr flags:**
    - A semicolon ("RAND models that gap; Carnegie asks…").
    - "Only as good as the unit it adds up over" is mannered.
- **Page:** passes. Line 28 ("Treat the BLOOM calculation as an illustration, not a timeless threshold recommendation") keeps XLab's "X, not Y" and reads plainly.

### Interpreting cloud evidence

[[../../Lenses/XLab Verification - v-cloud-evidence]]. The framing (lines 14 to 16) and the closing passage are XLab's. The drill is a widget.

- **Lens's text:**
    - the tldr
    - the headings
    - the open question (line 31), rebuilt from the drill's odd-one-out task
    - Works cited
- **Spoiler test:** passes. The open question lists the four observables but does not say which is the odd one.
- **tldr flag (minor):**
    - Two colon clauses in a row.
    - "Exactly what it proves" (T7).
    - The closing "Practice stopping at the first." is an aphorism.
- **Page:** passes. The drill is required and finishes only when all nine tasks are solved. The lens's "For each item" implies all nine, and each task shows when it is solved, so this lens has no stall risk of the kind on v-cloud.

### Intelligence: watching without permission

[[../../Lenses/XLab Verification - v-intel-intro]]. The body is XLab's.

- **Lens's text:**
    - the tldr
    - the link labels in line 20 (link pass, approved)
    - the vocabulary callout's first and last lines (line 27)
    - Works cited
- **Spoiler test:** passes.
- **tldr flag:** "whose satellites" stands for the institutions question (who owns the sensors and who must share), and the learner cannot resolve it before reading. "The section" is for stage 8.
- **For Andreas:** line 20, XLab's paragraph. The log's section 6 carried a T7 flag on its opening, "The real problem here is ambiguity". The paragraph also has "actually establish", "really caught" and "what exactly do you do". It is XLab's voice, and our link labels sit inside it, so rewriting it is your call. Line 18 also has XLab's "one of the two the track weights most".

### Observable signatures of undeclared AI development

[[../../Lenses/XLab Verification - v-intel-signatures]]. The catalog, the families and the collection-map lead-in are XLab's.

- **Lens's text:**
    - the tldr
    - the headings
    - the readings line (line 142)
    - the lead-ins to the threshold explorer (line 154) and the method explorer (line 170)
    - Works cited
- **Spoiler test:** passes.
- **tldr flags:**
    - "Can honestly establish" (T7).
    - The list of images ("a rooftop where snow never settles", "a power line you cannot bury quietly") reads well but needs decoding before the lens has explained thermal and grid signatures.
- **Flag on the page:** line 154. "From each side" does not resolve, because the two tables are the domestic levers and the international ones. "Set those same levers against cluster size" is mannered.
- **Left for stage 8:** "colour" on line 78 (XLab's).

### The empirical anchor: intelligence identifies, the regime resolves

[[../../Lenses/XLab Verification - v-intel-anchor]]. The cases, caveats and hiding places are XLab's. The question is ours (B4) and was reviewed by Andreas.

- **Lens's text:**
    - the tldr
    - the reading line (line 64)
    - the question (lines 75 to 77)
    - Works cited
- **Spoiler test:** passes, narrowly. The tldr gives the finding (three of four cases began with a tip), but the lens title states it too, and the question asks what follows for AI rather than for the finding itself.
- **tldr flags:**
    - "That is the whole division of labor in one sentence" is a setup line (T7).
    - "The fine print that keeps the finding honest" is mannered.

### From signal to intelligence assessment

[[../../Lenses/XLab Verification - v-intel-assessment]]. The body is XLab's.

- **Lens's text:**
    - the tldr
    - the headings
    - the reading line (line 61, rewritten for B6 and its reversal)
    - Works cited
- **Spoiler test:** passes.
- **tldr flags:**
    - Two semicolons in the first sentence.
    - "Really fights about the assumption" (T7).
- **Page:** passes.

### From intelligence lead to verification action

[[../../Lenses/XLab Verification - v-intel-action]]. Two of XLab's lessons merged (B14). Much of the text is XLab's, lightly edited. The other pass reworded the red-line question.

- **Lens's text:**
    - the tldr
    - the headings
    - "Here are the two passages" (line 58)
    - line 79
    - the readings block (lines 96 to 99)
    - the four questions before the task (line 150, edited)
    - the red-line question (lines 156 to 169, edited by the other pass and in stage 5)
    - Works cited
- **Spoiler test:** passes.
- **tldr flags:**
    - "NTM" is not spelled out.
    - "Act like a regime that wants to survive its first ambiguous case", "take a pencil to" and "red-line it for both capitals" are three figures in two sentences.
- **Flags on the page:** five, four of them carried from the log's section 6.
    - Line 79: a semicolon, and a setup line ("That is the asymmetry of this whole section sitting in one paragraph").
    - Line 92: "Unit 4" is CV1's Unit 4, and the sentence does not say so. "The bridge worth knowing" is a setup phrase.
    - Line 99: a semicolon, and "ideally read the whole draft treaty" leaves it unclear whether that is asked.
    - Line 150: "behind-the-meter" is not explained (T1).
    - Line 158, **Content:** the "symmetric, cheap, and checkable" rule is taught nowhere in either course, yet the rubric grades against it (Turner's QA, log section 7). Also "confront the question the historical record says drafters avoid", and the "both-capitals test" label.
- **Section 6's T1 flags on lines 29, 41 and 53** (the noninterference, *Six Layers* and MIRI paragraphs, XLab's): they pass in the course. "NTM" is defined in the collapsed callout on the intelligence opener, earlier in this unit, and the T1 check reads one lens at a time.
- **Left for stage 8:** "this whole section" on line 80 and "this section" on line 97. Em dashes on lines 36, 87, 89, 90 and 96.

## Unit 8: The Human Layer

### Welcome to Unit 8

[[../../modules/XLab Verification Part 2 W08 Insiders and reporting]], inline. Lens's throughout.

- **Spoiler test:** passes.
- **Flag on the page (minor):** line 19. "The route a whistleblower report has to survive", as in the overview's Unit 8 box.

### The human layer

[[../../Lenses/XLab Verification - v-human-intro]]. The framing paragraph and the objectives are XLab's.

- **Lens's text:** the tldr and Works cited.
- **Spoiler test:** passes.
- **tldr flags:**
    - "What an institution can honestly conclude" (T7).
    - The first sentence is a list, a colon and a verdict fragment ("the cheapest verification tools to deploy and the easiest to fool"). The overview's Unit 8 box opens the same way.

### Insiders and human sources

[[../../Lenses/XLab Verification - v-human-insiders]]. The case-writing brief, the check questions and the failure modes are XLab's, lightly edited. The worked cases and the failure lists in the closed callouts were rebuilt from XLab's exercise.

- **Lens's text:**
    - the tldr
    - the source line
    - the lead-in to the two exercises (line 49)
    - the warm-up's instruction (line 53, edited)
    - the callout titles
    - the first lines of "Where a report can die" (line 97) and the worked-cases callout
    - Works cited
- **Spoiler test:** passes.
- **tldr flags:**
    - **Content:** "then work six Project Lattice sources one at a time" reads as a required step, but the warm-up is optional (line 49 and the heading).
    - It opens on "X, not Y" ("tells you where they stood, not what they saw").
    - "Which record they never controlled could check the claim" is a garden-path clause.
    - At 78 words it is near the 80-word limit.
- **Flag on the page:** line 97. The first sentence ("Naming where a report dies is the work, so this list sits here and not above the exercise") explains the layout like an editor's note.
- **Left for stage 8:** "the exercise for this section" on line 49.

### Reporting and protection

[[../../Lenses/XLab Verification - v-human-reporting-protection]]. Almost all XLab's. Ours: the tldr, the source lines, the closing line to the next lens, and Works cited.

- **Spoiler test:** passes.
- **tldr flag:** it opens on a metaphor in "X, not Y" form ("a door, not a corridor"), then extends it ("walk through to the Attorney General").
- **For Andreas:** line 96, XLab's sentence, which the log's section 6 carried as a T7 flag. "Baker proposes a similar solution against this problem of physical access" does not parse well ("a solution against a problem"), and "this problem" points back across a reading. Line 60's "see the below *AI Whistleblowing Law: Best Practice Guide*" is also XLab's and awkward.
- **Section 6's T1 flags on lines 51, 60 and 115 (now 116):** they pass. "Covered employee" and the protected subjects are in the statute excerpt above line 51. Line 60's guide is the next reading. Line 116 is a list of sources.
- **Page:** passes.

### After the report arrives

[[../../Lenses/XLab Verification - v-human-after-report]]. New on 24 Nov from the split (B3). Its text is XLab's apart from the tldr, the source line, the heading and Works cited.

- **Spoiler test:** passes.
- **tldr:** passes.
- **Left for stage 8 or 9:** the learner-facing times "Optional, 7 to 10 minutes" (line 34) and "Audit the verifier (15–20 min)" (line 48). CV1 cut times like these from its lenses, since learners see times in the sidebar.

### Audits and inspections

[[../../Lenses/XLab Verification - v-human-audits-inspections]]. The guiding questions, the brief and the finding callout are XLab's. Ours: the tldr, the reading lines (lines 29, 47, 63), the callout titles and Works cited.

- **Spoiler test:** passes.
- **tldr flag (minor):** "may honestly conclude" (T7), the third "honestly" in this course's tldrs.
- **Page:** passes.
- **Left for stage 8 or 9:** "(12 to 15 minutes)" in the brief's callout title.

### Institutions and policy judgment

[[../../Lenses/XLab Verification - v-human-institutions]]. The station questions and commentary are XLab's, lightly edited. Ours: the tldr, the reading lines, the optional exercise's lead-ins (lines 131 and 143) and Works cited.

- **Spoiler test: fails.** "AI has candidates for the first and the third and nobody in the judge's chair" gives away the judge station's commentary ("This is the station with no tenant"), which the lens hides until the learner has answered.
- **tldr flag:** besides the spoiler, "build the AI pipeline station by station" is mannered.
- **For Andreas:** line 74, the judge question, which the log's section 6 carried as a T7 flag. It is XLab's apart from our link ("the captures you mapped in the auditing exercise"). The question hangs two "enough that" clauses on a colon after "Board-like standing", a label the learner has only from the line above. The judge commentary (line 108) also has "This is the station with no tenant" and "along exactly the lines" (T7), both XLab's.
- **Section 6's T1 flags on lines 62 and 109:** they pass. The Board of Governors and the safeguards analysis come from the Carlson reading above them.
- **Left for stage 8:** "the human layer this section closed on" (line 104) now describes this unit from inside it. "Defence" on line 143. "Optional, about 15 minutes" on line 131.
