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

**Later on 2026-11-25.** Units 9 and 10 are flagged, so every unit is. Units 9 and 10 have:

- Five tldr flags, one of them Content: the close reading's "find the step where the conclusion outruns the proof", which no required question asks for.
- Ten comments on the pages. Two are Content: the Unit 9 welcome, for the same reason, and the red team review's "Neither was written with the other in view", which the paper's acknowledgements contradict.
- Two XLab passages for Andreas, both on the cheating lens.

Across the course, "honestly" or "honest" turns up in six tldrs (the overview, signatures, anchor, the human layer, audits, covert development) and once in the overview's text. "Actually" turns up in eight places of Lens's text (the overview four times, the Unit 7 welcome, the covert opener's closing line, the Swiss-cheese question and the red team review). In all there are 29 comments on the pages. A decision on these two words, made once for the whole course, would settle a dozen flags.

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
| 9 | Welcome to Unit 9 | 76 | 76 | 0 | Flagged (Content) |
| 9 | What is covert development? | 1,577 | 540 | 86 | Flagged (minor) |
| 9 | A system overview for near-term, low-trust AI compute verification | 1,286 | 388 | 271 | Flagged (Content in the tldr) |
| 10 | Welcome to Unit 10 | 67 | 67 | 0 | Passes |
| 10 | How could a determined actor cheat? | 1,613 | 441 | 119 | Flagged, two XLab passages |
| 10 | Evasion scenario taxonomy | 811 | 191 | 114 | Flagged |
| 10 | Red team, blue team: from treaty requirements to a verification system | 2,198 | 1,092 | 221 | Flagged (Content) |

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
- **Review of Andreas's rewrite, 2026-11-25:**
    - **Cleared** (comment removals pending Andreas's accept):
        - Line 18.
        - The Unit 6 box. One small point: "fit in practice, as opposed to where a demo suggests it stands" mixes "fit" and "stands".
        - The Unit 10 box.
    - **tldr cleared:** "truly prove" is not on T7's list, though "can prove" says the same.
    - **Still open:**
        - The Unit 7 box: "really found" is on T7's list, "a treaty that protects sensors" still needs decoding, and "See where … what can be seen" repeats.
        - The Unit 8 box: Andreas asked about it, and a candidate went to him on 25 Nov.
        - The Unit 9 box: Content. A replacement for the last sentence went to him.
- **Second review, 2026-11-25 evening:** all six of the overview's flags are cleared (removals pending Andreas's accept).
    - The Unit 7 box's "a treaty that protects sensors" passes. Claude's reason for the flag was wrong, because CV1 teaches national technical means: the by-access map in Measuring Mechanism Effectiveness, the actors table, and the test-ban case. Optional precision: the treaty protects each side's own satellites from interference, which is the opposite of a shared network like the CTBT's IMS. "Bars interfering with each side's satellites" would say that if wanted.
    - The Unit 9 box no longer promises a flaw. Its "a step of your choice" fits questions 3, 4 and 7 better than 9, which applies the system to a new case. This depends on the question 9 decision below.
    - The same Unit 9 promise is still in the Unit 9 welcome's third bullet and in the close reading's tldr, for when Andreas reaches Unit 9.
    - Question 9 stays one of four to choose from (B17), so "a step of your choice" in the Unit 9 box fits questions 3, 4 and 7 but not 9. "One part of your choice" would cover all four. Minor.

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
- **Review of Andreas's rewrite, 2026-11-25:**
    - **tldr:** "grade" and "opening-puzzle" are fixed. A new point: "fill in the hardware mechanism dossier" describes something the lens does not ask for. The dossier is a list of fields to use for any proposal, with no exercise attached. The opening verdict line is still open, and a candidate went to Andreas.
    - **Line 116 (the question):** open. Andreas is weighing removing the Prompt callout. Claude's advice, sent 25 Nov, is to keep the callout and shorten the question, because elements 1, 5, 6 and 7 refer back to "the mechanism" and "the proposed role", which only the prompt introduces.
    - **Line 123:** Andreas will rename the heading "Return to the opening puzzle". The Unit 5 lens never calls the ledger an opening puzzle in learner text.
- **Second review, 2026-11-25 evening:**
    - **The opening line passes as a recap.** CV1's Unit 5 lens on measuring use has "a component demo, not a treaty regime" in its tldr, and line 91 says "an empirical component demonstration, not an end-to-end verification regime", so the tldr picks up a phrase the learner has met.
    - **The question is cleared:** it now restates only the scenario. Optional: "in response to the prompt above" sits after "pause", where it can read as part of the pause. It reads more cleanly right after "brief".
    - **The heading is cleared:** "Return to the claim ledger".
    - **Cleared later that evening:** the tldr's "fill in the hardware mechanism dossier" is removed. With that, the policy studio is cleared.

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
- **Review of Andreas's rewrite, 2026-11-25: cleared.**
    - Andreas added "Explore all the signals to complete the exercise." The comment removal is pending, and it adds the space the line needed after "Table 2.".
    - Optional: "Open all fifteen signals" names what completes the widget more exactly than "explore".
    - After the edit, the T7 check flags line 106's first sentence ("sorts these same signals against the two tables this page does not reproduce"). That sentence is Claude's text from the link pass. It passed this pass, but it is a candidate to plainen.

### Customer identification and ongoing monitoring

[[../../Lenses/XLab Verification - v-cloud-customer-identification]]. Egan and Heim is the article. Our text is the tldr, the source lines, the Box 3 heading and Works cited.

- **Spoiler test:** passes.
- **tldr flag (minor):** "Egan and Heim port that playbook" stacks two borrowed metaphors (software "port", sports "playbook"). The literal version is shorter. **Cleared 25 Nov:** "import that framework".
- **Page:** passes.

## Unit 7: Cloud Limits and Intelligence

**Review of Andreas's rewrites, 2026-11-25 evening.** Comment removals are pending Andreas's accept.

- **Cleared:**
    - The welcome.
    - Detection gaps (tldr).
    - The intelligence opener: tldr, and XLab's line 20 kept by Andreas's choice. He also fixed line 18's "the track weights most".
    - Signatures: the tldr, keeping its images by Andreas's choice, and line 154. Small: "follow after" says "follow" twice.
    - The anchor's tldr.
    - On the red-line lens:
        - **Line 79.** Small: "an undertaking where sharing is an encouragement" can read as "in which". "Whereas" would avoid that.
        - **The readings block.** Claude's objection was wrong: CV1 Unit 3 assigns the whole MIRI draft, so "Ideally you have read the whole draft treaty" points back to it. Naming CV1 would make that explicit. This comment cannot be removed from Claude's side while its two pending corrections sit inside it, so Andreas can delete it in the editor.
    - **Cloud evidence tldr.** Andreas asked what was wrong with the closing aphorism. Nothing that needs fixing. "The first" resolves to the one conclusion each record supports, and "only" replaced "exactly", so the flag is withdrawn.
- **Still open:**
    - **The assessment tldr:** two semicolons ("A sensor records a hot roof; you infer chips; you judge a covert run") and "really". It is unchanged on the relay as of this review.
    - **On the red-line lens:**
        - The precedent sentence (line 91).
        - "Behind-the-meter" (line 149).
        - The rule in the question (line 157).
        - Suggestions for all three went to Andreas on 25 Nov.
        - The rule turns out to be XLab's own sentence, which our import dropped (see below).
- **The tldr's "NTM":** a judgment call, kept as Andreas prefers. CV1 never uses the abbreviation, only "national technical means". The intelligence opener in this unit introduces "NTM" in its collapsed callout. IAEA is a better-known name, but the learner has met NTM by this lens.
- **Where the "symmetric, cheap, and checkable" rule came from.** XLab's intelligence-institutions lesson stated it right after the two treaty passages: "It is a real text, and it is meant to be marked up rather than admired. The rule underneath, which the written output will test your draft against: states sign what is symmetric, cheap, and checkable." Our lens kept the first sentence and replaced the second with "Here are the two passages, from the paper itself." XLab stated the rule without explaining it, so restoring it still leaves the three words for the learner to interpret.

**Third round, 2026-11-25, late evening.** Andreas fixed:

- the assessment tldr
- "whereas" on line 79
- the warhead precedent (with "from Compute Verification 1")
- "behind-the-meter"
- the Unit 9 box ("one part of your choice")

Claude added three suggestions on the red-line lens, pending Andreas's accept:

- **The rule:** the line 79 paragraph ends with the red-line question testing the draft against the rule, glossed as symmetric (binds both sides the same way), cheap (complying costs little) and checkable (each side can tell whether the other complies).
- **"Confront the question the historical record says drafters avoid"** becomes "take up the question drafters have historically avoided".
- **The "both-capitals test" label** goes, and the question asks for "one paragraph on why Washington would accept your article and one on why Beijing would". The grading criterion is "Plausibility in both capitals", so nothing there depends on the label.

The comment on the precedent is removed (pending). With the drafts accepted, the lens validates with no issues. The T7 check still catches line 79's "That is the core asymmetry of this whole section" (a setup line, and "section" is for stage 8). Two comments need Andreas to delete them in the editor, because Claude's pending corrections sit inside them: the readings block, and "behind-the-meter". The question's comment can go once the suggestions are accepted. **With that, Unit 7 is done.**

### Welcome to Unit 7

[[../../modules/XLab Verification Part 2 W07 Cloud limits]], inline. Lens's throughout.

- **Spoiler test:** passes.
- **Flag on the page:** line 18. "Actually proves" (T7), and the third bullet's "treaty text that protects sensors" needs decoding, as in the overview. **Corrected 25 Nov:** the decoding half is withdrawn, because CV1 teaches national technical means. Only "actually" stands. The comment on the page still carries the old reasoning.

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

**Review of Andreas's rewrites, 2026-11-25, late evening.** Unit 8 is cleared. The welcome's comment removal is pending, and the "Where a report can die" comment was resolved by Andreas when he deleted the sentence, as intended.

- **Welcome.** Small: "the pathway a whistleblower report takes going from insider to verifier" reads more simply without "going".
- **The human layer tldr.** "Honestly" is gone. Small:
    - "Enter the world of" is a stock opener.
    - The list "whistleblowers, interviews, audits, inspections" has no "and".
    - "This unit is about whistleblowers, interviews, audits and inspections." would do both.
- **Insiders tldr.** The Content flag is fixed ("optionally work six … sources"). It is exactly 80 words, the limit.
- **Reporting and protection.**
    - The tldr now reads "not a golden ticket", but "walk through to the Attorney General" belonged to the old door metaphor and no longer fits. A candidate went to Andreas.
    - XLab's line 60 is fixed ("see the below" is gone).
    - Line 96 still reads "a similar solution against the problem of physical access". An optional candidate went to Andreas.
- **Audits tldr:** cleared.
- **Institutions:** cleared.
    - The spoiler is gone ("Find out which of these roles AI already has candidates for").
    - The judge question is split into two questions and reads well.
- **After the report arrives:** passed earlier.

**Stage 8 note (Andreas, 25 Nov).** XLab's "section" becomes "lens", "unit" or "module" by context, not always "lens".

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
- **tldr flag (minor):** "may honestly conclude" (T7).
- **Page:** passes.
- **Left for stage 8 or 9:** "(12 to 15 minutes)" in the brief's callout title.

### Institutions and policy judgment

[[../../Lenses/XLab Verification - v-human-institutions]]. The station questions and commentary are XLab's, lightly edited. Ours: the tldr, the reading lines, the optional exercise's lead-ins (lines 131 and 143) and Works cited.

- **Spoiler test: fails.** "AI has candidates for the first and the third and nobody in the judge's chair" gives away the judge station's commentary ("This is the station with no tenant"), which the lens hides until the learner has answered.
- **tldr flag:** besides the spoiler, "build the AI pipeline station by station" is mannered.
- **For Andreas:** line 74, the judge question, which the log's section 6 carried as a T7 flag. It is XLab's apart from our link ("the captures you mapped in the auditing exercise"). The question hangs two "enough that" clauses on a colon after "Board-like standing", a label the learner has only from the line above. The judge commentary (line 108) also has "This is the station with no tenant" and "along exactly the lines" (T7), both XLab's.
- **Section 6's T1 flags on lines 62 and 109:** they pass. The Board of Governors and the safeguards analysis come from the Carlson reading above them.
- **Left for stage 8:** "the human layer this section closed on" (line 104) now describes this unit from inside it. "Defence" on line 143. "Optional, about 15 minutes" on line 131.

## Unit 9: Covert Development and the Low-Trust Architecture

**Review of Andreas's rewrites, 2026-11-25, night.**

- **Unit 8 is cleared,** with one slip on the reporting lens's line 96 ("Baker propose"). A suggestion for "Baker et al. propose" is pending.
- **Cleared in Unit 9** (comment removals pending):
    - The cheating lens's widget line now ends "Open all six prompts to complete the exercise", and with the comma gone the "so that" clause attaches to the second route as intended.
    - The close reading's calculator lead-in.
- **Suggestions made in the text for Andreas to accept:**
    - **The Unit 9 welcome's third bullet** becomes "Examine one part of it in depth: an argument, a design choice, its weak points, or how it handles a new case." That matches questions 3, 4, 7 and 9, and it keeps the welcome in line with the overview's "one part of your choice". Deleting the bullet would leave the choice question unmentioned.
    - **The close reading's opening sentence** (line 12) still read "undertake a … proposal" and "assemble … the verification intuitions". The suggested replacement reads one proposal and tests it "against what you have learned across both courses about verification mechanisms, the actors involved and their incentives".
    - **The question instructions, now one set**, split as Andreas wanted.
        - Before the paper: one priming sentence that names the four answers and what to note while reading (where the problem is stated, how the approach is built, and how evidence travels from chip to verdict, for questions 1, 2 and 5).
        - Before the questions: the full instructions. Read all nine first, the answer set and why four questions are marked optional, questions 6 and 8 optional, section references and the PDF, and XLab's four "In your answers" bullets without their semicolons.
        - The duplicate "Clearly distinguish the author's claims…" sentence goes, since the first bullet says it.
- **tldrs** (frontmatter, so the candidates are in Claude's reply, not on the page):
    - **Cheating lens:** the facts come first, then "None of it proves anything on its own". "Not X or Y, but Z" goes, and "careful" replaces "honest".
    - **Close reading:** "find the step where the conclusion outruns the proof" becomes "examine one part of it in depth".

### Welcome to Unit 9

[[../../modules/XLab Verification Part 2 W09 Covert development and the low-trust architecture]], inline. Lens's throughout.

- **Spoiler test:** passes.
- **Flag on the page, Content:** line 20, "Find the step where its conclusion outruns its proof". As in the overview's Unit 9 box, no required question asks for this, and the phrase assumes the paper has such a step.

### What is covert development?

[[../../Lenses/XLab Verification - v-covert-what-is-it]]. A restored lesson (B10). The anchors, scenario, task and debrief are XLab's. The six prompts are in the widget.

- **Lens's text:**
    - the tldr
    - the objectives box's title and "earlier in the course" (line 16)
    - the bridge to Unit 10 (line 25, item 22, approved)
    - the headings
    - the lead-in to the widget (line 99)
    - the closing line (line 128)
    - Works cited
- **Spoiler test:** passes. The tldr's "standard" is worded differently from the debrief's point, that operations are made inconclusive rather than invisible.
- **tldr flags:**
    - It opens on a verdict line ("Nothing in the scenario proves anything.").
    - Its last sentence turns on "not X or Y, but Z" (T3).
    - "A response honest enough to tell suspicion from proof" (see the count in the status above).
- **Flag on the page (minor):** line 99. The sentence offers two routes, and its "so that" clause fits only the second. The lens could also say plainly that the widget finishes once all six prompts are opened (B16).
- **Not flagged:** line 128's "what a determined actor would actually try" (T7, one word).
- **Left for stage 8:** "anchors this lesson" in Works cited.

### A system overview for near-term, low-trust AI compute verification

[[../../Lenses/XLab Verification - v-covert-system-overview]]. The assignment, the objectives and the nine questions are XLab's, lightly edited. Cankaya is the article.

- **Lens's text:**
    - the tldr
    - line 12's ending
    - the lead-ins to the two widgets (lines 42 and 54)
    - the question instructions (lines 63 to 67, partly XLab's)
    - the placeholders
    - Works cited
- **Spoiler test:** passes.
- **tldr flag, Content:** "find the step where the conclusion outruns the proof", as on the Unit 9 welcome. "One engineer's blueprint" is mannered.
- **Flags on the page:** three.
    - Line 12 (minor, T3): "tackle", "synthesizing", "the verification intuitions you gained".
    - Line 54: "are one calculator" and "buy each other" need decoding.
    - Line 67: a semicolon. The bigger point is that lines 63 to 67 repeat the Assignment's instructions on lines 24 to 26 with small differences, so one set would do.
- **Left for stage 8:** "Analyse" in question 3's title, and "9" as a numeral on line 63.

## Unit 10: Evasion Routes and the Red Team Review

**Units 8 and 9 complete, 2026-11-25, night.** The "Baker et al." suggestion and the Unit 9 welcome bullet are accepted, both tldrs are rewritten, and no flags remain in either unit. On the cheating lens, Andreas left out "None of it proves anything on its own", which is fine. "Works towards" is for stage 8.

**Review of Andreas's Unit 10 rewrites, same night.**

- **Cleared** (comment removals pending):
    - The Swiss-cheese question ("actually" gone).
    - Red team review line 21.
    - Red team review line 23. Andreas deleted the "Neither was written" sentence as factually wrong, and the semicolon became "while".
    - Red team review line 222, now "Two things to keep in mind". Andreas asked what was wrong with the setup. Nothing much: T7 flags phrases that announce what is coming rather than saying it, but this one tells the reader two caveats follow, which helps. The semicolon was the concrete issue, and it is gone.
    - The red team tldr ("which it cannot").
- **Suggestions made in the text for Andreas to accept:**
    - **The Swiss-cheese paragraph, line 40, XLab's.** The new version drops "It is important to take advantage of the unique strengths…" and "affected by intersection", which did not parse, and keeps the point about human sources: "Each layer has its own strengths and its own ways of failing, and a regime gets the most from its layers by knowing both. Whistleblowers and other human sources, covered in Unit 8, can raise a suspicion… But they usually work alongside the other layers, confirming a finding or pointing to where to look, rather than proving a violation on their own."
    - **The cases question, line 82.** Andreas's rewording said "exposes" twice. The suggestion is "say which layer of the verification stack it concerns and what limit of that layer it exposes."
    - **The taxonomy's line 19.** The punchline is cut, since line 17 already says not to rank yet.
    - **The taxonomy question, rewritten to match its grading.**
        - The opening line loses its list.
        - The recap's long sentence becomes four.
        - The task becomes three plain questions: "Which route is primary, and why? Which routes support it? For each part of the scheme, who would see it, and what would they see instead of a violation?"
- **tldrs** (candidates in Claude's reply):
    - **The cheating lens.** Andreas's merge reads "will not bypass a mechanism rather than attack it", which says the opposite of what is meant. The candidate fixes that and replaces the closing verdict with what the lens draws from nuclear history.
    - **The taxonomy.** The candidate drops "as moves rather than as a list" and the verdict ending.
- **Optional, XLab's:** the WIRED card on the cheating lens (line 92) still has "zero-day" unexplained and ends on "the monitoring gap, not the exploit, is the verification lesson".

With all of these accepted, the production check shows no errors and the usual 25 warnings.

**Unit 10 complete, 2026-11-25, late night.** Andreas accepted the suggestions and set both tldrs. Claude missed in the previous review that Andreas had already rewritten the WIRED card's closer ("This is why the verification lesson here is the monitoring gap"). "Zero-day exploit" stays, as a common term. **Stage 7 is done.** Two items are left:

- **A typo in the cheating lens's tldr:** "chekcs". It sits in the frontmatter, so Andreas fixes it in the editor. "Defence" and "towards" are for stage 8.
- **The WIRED card's facts (Elias's AI asked for a check).** The article exists (WIRED, August 2026), and the card's account matches the coverage on the internal package service used as a message board, the novel exploit, and the Hugging Face breach. One detail does not match. The card says the agents rebuilt the channel "two days after engineers shut it down". Engadget, citing WIRED, has OpenAI shutting the board down on July 4 and the agents rebuilding it by July 8, so four days, or "within days". Andreas's call, since the card is XLab's text.
### Welcome to Unit 10

[[../../modules/XLab Verification Part 2 W10 Evasion routes and the red team review]], inline. Lens's throughout. **Passes**, and so does the tldr. **Left for stage 8:** "defences".

### How could a determined actor cheat?

[[../../Lenses/XLab Verification - v-covert-how-to-cheat]]. A restored lesson (B10). Its prose, table and cases are XLab's. The two questions are Lens's (proposal scope).

- **Lens's text:**
    - the tldr
    - the bridge to the next lenses (lines 27 and 94, link pass)
    - the two questions (lines 49 and 80 to 83)
    - the optional callout's title
    - Works cited
- **Spoiler test:** passes, narrowly. "Check that its layers fail in different ways" is close to the choice question's answer, but the question stem already says the designers "want the layers to fail independently".
- **tldr flags:**
    - It opens on a two-sentence punchline ("…It will go around it.", T2).
    - It ends on a verdict line ("…the archetype, and … the template").
- **Flags on the page:** two.
    - Line 49 (minor): "actually".
    - Line 82: "which layer of the stack above it says something about" takes two reads.
- **For Andreas:** two XLab passages from the log's section 6. They are XLab's, so they are not commented.
    - Line 40 (T3): "It is important to take advantage of the unique strengths of each of the layers, while taking into account how they are affected by intersection…" is the most LLM-like paragraph in the unit. "Affected by intersection" does not parse.
    - Line 92, the WIRED card (T1): "zero-day" is not explained, and the card ends "the monitoring gap, not the exploit, is the verification lesson", a punchline in "X, not Y" form.
    - Section 6's T1 flag on line 72 (the Iraq paragraph, now 73) passes. Each case is explained in the paragraph itself.
- **Left for stage 8:** "programme" in the question's rubric (tutor-facing) and "defence" in the tldr.

### Evasion scenario taxonomy

[[../../Lenses/XLab Verification - v-covert-taxonomy]]. A restored lesson. The table and the instruction on line 17 are XLab's.

- **Lens's text:**
    - the tldr
    - the heading
    - line 19
    - the question: the recap on line 37, from the other pass, and the task on line 39
    - Works cited
- **Spoiler test:** passes. The tldr states the method (one primary route plus supporting tactics) that the question also states.
- **tldr flag (minor):** "Learn them as moves rather than as a list" (T3), and "naming which is which is most of the analysis" is a verdict line.
- **Flags on the page:** two.
    - Line 19: "Rank them now and you are ranking a guess" (T2).
    - Line 39: it covers the recap's 70-word sentence with its semicolon, carried from section 6. It also covers the task's "name", "say" and "say", and "sees the piece". Section 6's T1 flag on the recap's names passes.

### Red team, blue team: from treaty requirements to a verification system

[[../../Lenses/XLab Verification - v-covert-red-blue]]. A restored lesson, retargeted at the primary sources by Elias's AI. That is why so much of it is Lens's. The ten questions, the role and assignment, and the submission standard are XLab's.

- **Lens's text:**
    - the tldr
    - the opening (lines 21 and 23)
    - the reading and citing instructions (lines 26 to 34)
    - the optional line (55)
    - the placeholders
    - the scoring part's lead-ins (lines 217, 222 and 228)
    - Works cited
- **Spoiler test:** passes.
- **tldr flag (minor):** "which it cannot touch", the same figure as the overview's Unit 10 box.
- **Flags on the page:** three.
    - Line 21: "Now the harder job:" (setup) and "actually" (T7).
    - Line 23, **Content:** "Neither was written with the other in view" is doubtful. Cankaya thanks Aaron Scher, a treaty co-author, both texts come from MIRI's Technical Governance Team, and question 8 asks the learner to notice that link. The line also has a setup, a semicolon and a closing punchline.
    - Line 222: "Two things to hold" (setup), and a semicolon.
- **Section 6's flags:** line 212 (now 217, T7) passes. "Relative, conditional assessments, not measured probabilities" is a real caveat that a reader might get wrong. Line 126 (question 4's list, T1) passes, since the terms come from the Cankaya paper read in Unit 9.
- **Not flagged:** line 28's "not what does this system do, but which treaty obligations could it carry" (T3 form, but the contrast is the point of the paragraph).
