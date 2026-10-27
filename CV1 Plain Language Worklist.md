---
tags:
  - validator-ignore
authors:
  - Andreas+Claude
---

# CV1 plain language worklist

Stage 6 of [[CV1 Restructure Log]]. Claude marks what is Lens's text, tests every tldr for spoilers, and flags the Lens text that most needs rewriting; Andreas rewrites (A4); Claude then reviews the rewrite and checks any feedback brief or quoted claim it touches. Scope (A36): learner-facing text in CV1's 49 lenses, the overview and the five unit welcomes. Tutor summaries and feedback briefs are out, and so are articles and widgets.

**Status, 2026-10-26.** The pilot, "Who can prove what", is rewritten and reviewed; its two flags come off once Andreas accepts their removal. The other pages are next.

**Status, later on 2026-10-26.** The pilot is done. Unit 1 is flagged, and Andreas has rewritten the tldrs of five of its pages and the text on three; each review is under its page below, with seven short notes still open. Building Verification Intuitions is done. Further Exploration's AI 2027 and its three embedded readings are on pages of their own (A41). Unit 1's follow-ups, then units 2 to 5, are next.

**Status, evening of 2026-10-26.** Andreas fixed six of the seven notes; the seventh, "cancelled", waits for the later American-spelling pass. Two new one-word notes (Why Securitizing AI, Primer Practice). Options A and B each have one semicolon left, on the same shared line. Still to do in unit 1: the AI 2027 page (Andreas). Andreas found that Primer Practice sits a unit before the material it drills; where it goes is Q20 in the log, not built.

**Status, late on 2026-10-26.** Unit 1's text is done (Andreas), and every unit 1 flag is resolved; their removals are pending. Two minor notes are left (a comma in Options A and B, a word in AI 2027's chart sentence), plus "cancelled" for the spelling pass. Open: Q20, the drill's placement. Unit 2 is next.

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
| 1 | Welcome | 657 | 97 | 0 | Left for stage 7 |
| 1 | Introduction: Why Should You Care About AI Verification? | 2,475 | 270 | 378 | Done |
| 1 | AI Is Grown, Not Built | 531 | 531 | 0 | Rewritten, reviewed |
| 1 | Four Background Claims | 57 | 57 | 0 | Done |
| 1 | Why Securitizing AI Is Difficult but Necessary | 776 | 191 | 50 | Done |
| 1 | We Need More Theories of Change | 1,738 | 428 | 108 | Done, apart from spelling (later pass) |
| 1 | Building Verification Intuitions | 398 | 131 | 79 | Done |
| 1 | Read Plan A's Verification Plan | 82 | 82 | 0 | Passes |
| 1 | Option A: Stress-test Plan A's Verification Regime | 948 | 122 | 88 | Done; one comma |
| 1 | Option B: Compare Plan A and Plan S | 892 | 142 | 56 | Done; one comma |
| 1 | Optional: Further Exploration | 1,126 | 387 | 260 | Done; AI 2027 and three readings moved out |
| 1 | AI 2027 (new page, 2026-10-26) | about 32,000 with the scenario | the tldr | 0 | Done; one minor note |
| 1 | The three reading pages (new, 2026-10-26) | about 16,500 with the readings | the tldrs | 0 | Done |
| 1 | Primer Practice: Inspection, Commitment, and Logic | 724 | 0 | 622 | Done; placement open (Q20) |
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

## Unit 1: Why verification

**Course overview, Welcome, Welcome to Unit 1.** Not flagged. Stage 7 will likely fold these three opening pages together, so their text is looked at then rather than twice.

### Introduction: Why Should You Care About AI Verification?

[[Lenses/XLab Verification - v-introduction]]. Almost all XLab's.

- **Lens's text:** the tldr (line 4); the callout titles we added ("Optional: Further Reading", "Misuse vs. misalignment", the four leader titles); the strongest-objection prompt (lines 32 to 34, ours where it asks "what would move you towards the case and what would move you away from it"); the lead-in to the types-of-AI diagram (line 86); the source and chart credit lines (lines 123, 141). All pass apart from the tldr.
- **Spoiler test: passes** (Andreas, 2026-10-26). Claude first failed it, since "Rivals cannot simply trust, punish, or open their books. Verification is the fourth option" gives the result of the verification-problem exercise. Andreas: naming verification as the way through is not much of a spoiler, since it is the purpose of the whole course.
- **tldr flag:** a semicolon after "real companies". "Real companies" stays: escapes like this have happened more than once, Hugging Face being the best known, and that counts as general knowledge (Andreas).
- **Review of the rewrite, 2026-10-26:** the semicolon is gone, but the first sentence now reads "…into real companies with the people building them say worse is coming", which does not parse. Candidate: "…into real companies, and the people building them say worse is coming." Fixed as suggested (Andreas).

### AI Is Grown, Not Built (optional, hidden)

**Back in scope, 2026-10-26 (A40).** Andreas first left this page and Four Background Claims out (A39), then found the introduction's closed "Optional: Further Reading" callout links to both (lines 22 to 27) and rewrote their tldrs. Their two page flags had been withdrawn in between; the removals are pending.

**Review of the rewrite.** The introduction (line 12) has lost its semicolon. Its last sentence, now "examines these features and consequences born from the current AI development paradigm", still says what the article does in general terms, and "born from" is a little mannered; a judgment call. The tldr is unchanged, so its mild spoiler and the "deploy" point stand if Andreas wants to keep them, which is his call. **tldr kept (Andreas, later on 2026-10-26):** it says what the reading does, to draw the learner in, since saying more risks giving away the article's point. The spoiler and "deploy" notes are closed.

[[Lenses/XLab Verification - v-ai-is-grown]]. Not from XLab; the article is Yudkowsky and Soares. Also in the demo and archived courses.

- **Lens's text:** everything around the article: the tldr, the introduction (line 12) and the question (line 20). The chat instructions are tutor-facing and out of scope.
- **Spoiler test: fails, mildly.** The tldr's first two sentences ("Nobody sat down and programmed ChatGPT… engineers set up a training process and let billions of parameters arrange themselves") answer the page's own question, how ChatGPT was made differently from an ordinary app. The page title already says as much, so this is a judgment call.
- **tldr flags:** the spoiler; "This article asks what it means to deploy something powerful" is a little off the article's point, which is control, and stopping by treaty.
- **Flag on the page:** line 12 (withdrawn).
- **Minor, no flag:** line 20, "the difference between how ChatGPT was created versus how…" should be "between … and …".

### Four Background Claims (optional, hidden)

Back in scope, as above. **Review:** the tldr's em dash is gone. The introduction (line 11) is unchanged, and the withdrawn flag on it is pending removal; rejecting that removal keeps the flag. [[Lenses/Four Background Claims]]. Not from XLab; the article is Soares (MIRI). Shared: also in Introduction to Lens Academy, the orientation module and the demo and archived courses, so a rewrite changes those too.

- **Lens's text:** the tldr and the introduction (line 11).
- **Spoiler test:** passes; no exercise.
- **tldr flag:** an em dash (Course Authoring).
- **Flag on the page:** line 11 (withdrawn).
- **Review of the rewrites, later on 2026-10-26.** The tldr's "four premises… from why smarter-than-human systems could emerge to why we can already do meaningful work to prepare" does not match the article's four claims: humans have a very general problem-solving ability; AI could become much more intelligent than humans; such systems' decisions will shape the future; they won't be beneficial by default. Work we can do today is the question the article opens with (article, line 21), not one of the premises. Candidate: "This article lays out the four premises behind that case, from how general human intelligence is to why highly intelligent AI won't be beneficial by default." In the introduction, "exactly" is gone and "text" is now "reading". "There is already meaningful work being done today" turns the article's "work we can do today" from possible into under way; candidate "there is meaningful work we can do today". "His entire perspective on the prospects of AI" is unchanged, a judgment call. **Fixed (Andreas, evening):** the tldr now runs "from what general intelligence is to why highly intelligent AI won't be beneficial by default", and the introduction says "meaningful work we can do today". Done.

### Why Securitizing AI Is Difficult but Necessary

[[Lenses/XLab Verification - v-prevention]].

- **Lens's text:** the tldr; line 14, where we corrected XLab's "experts spent hundreds of hours fixing it" to "governments and companies spent years finding, repairing, and testing affected systems"; the Y2K footnote (line 16); the callout title "The Risks of Securitization". All pass apart from the tldr.
- **Spoiler test:** passes; the page has no exercise, and its outcome test is separate.
- **tldr flag:** it opens with a slogan, "Y2K did nothing because thousands of people fixed it first". **Corrected, 2026-10-26:** Claude first wrote that "Y2K did nothing" says the opposite of what is meant, which overstated it; the sentence does say why ("because thousands of people fixed it first"). The narrower point: it opens on "Y2K did nothing", the very reading the page argues against (that Y2K was a non-event), and the bug is the subject that "did" something. Whether that turn is the point of the line is Andreas's call.
- **Review of the rewrite, later on 2026-10-26:** the line now opens "Y2K never occurred because thousands of people fixed it first." Y2K, the date, did occur, so this can read as the year 2000 never arriving. Candidate: "The Y2K bug never caused a crisis because thousands of people fixed it first." The rest passes. **Fixed (Andreas, evening):** now "The Y2K never became a crisis…". One word left: "The Y2K" needs a noun or no article, so "Y2K never became a crisis" or "The Y2K bug never became a crisis".

### We Need More Theories of Change

[[Lenses/XLab Verification - v-theories-of-change]].

- **Lens's text:** the tldr; the objective (line 13); the two tables rebuilt from XLab's diagram (lines 44 and 49); the callout titles "Strategy: LLM Clarity Check" and "Strong Theories of Change". All pass apart from the tldr.
- **Spoiler test:** passes.
- **tldr flags:** a semicolon; "because nobody could say why it mattered" is stronger than the page's own source, AIP's account of eight factors behind the cancellation (a claim to check); the close, "if you cannot state it, neither can the people deciding…", is an aphorism; "a $11B" should be "an $11B".
- **Minor, no flag:** line 13, "mislabelled" is British spelling.
- **Review of the rewrite, later on 2026-10-26:** the semicolon is gone. Still open: "a $11B" should be "an $11B" (it is read "an eleven-billion"), and "cancelled" is "canceled" in American spelling. "Because nobody could articulate why it mattered" and the closing line are unchanged, Andreas's call. **Evening:** "an $11B" fixed (Andreas). "Cancelled" waits for the later American-spelling pass (Andreas).

### Building Verification Intuitions

[[Lenses/XLab Verification - v-intuitions]].

- **Lens's text:** the tldr; the reading instructions and essay options (lines 22 to 36); the callout title "A writing good practice".
- **Spoiler test:** passes.
- **tldr flags:** an extended metaphor ("treat it like an engineer treats a bridge design: find the load-bearing part, the weakest weld…"), the kind of phrase Course Authoring calls mannered; "Then write your verdict" reads as required, but both essays are optional (A16).
- **Flags on the page:** line 31, Content (the essay options read as if one is required); line 38, the callout title.
- **Outcome, later on 2026-10-26.** Andreas marked the essay choice "(optional)" and fixed the callout title to "A good writing practice". Both flags are resolved; their removal is pending. In the tldr, "part" and "weld" became "element" and "component", and "Then write your verdict" stays, since the three-course split restores a required essay (Andreas). One note: "how much hidden compute it can survive" became "how much hidden compute could survive", which moves the question from how much hidden compute the regime tolerates to how much could go undetected. Both are fair questions; which one is meant is Andreas's call. **Evening:** now "how much hidden compute it could survive" (Andreas), which keeps the regime as the subject. Done.

### Read Plan A's Verification Plan

[[Lenses/XLab Verification - v-intuitions-plan-a]]. Lens's text: the tldr and lines 13, 16 and 34. Passes; the Option A and B lines assume an essay, which is the Content point flagged on the previous page.

### Option A: Stress-test Plan A's Verification Regime

[[Lenses/XLab Verification - v-intuitions-a1]].

- **Lens's text:** the tldr; lines 14 to 17; "Questions to consider"; line 91; lines 114 and 118. The prompts are XLab's.
- **Spoiler test:** passes.
- **Flags on the page:** line 14, Content ("Choose Option A or Option B" no longer fits, A16) and a semicolon on line 15; line 17, "the embedded verification supplement excerpts" are on the previous page.
- **Outcome, evening of 2026-10-26.** Line 17 is fixed ("the verification supplement excerpts", Andreas), and its flag's removal is pending. The suggestions from Lens EA's AI on line 14 are resolved. The Content point stays as it is (Andreas): Building Verification Intuitions now marks the essay choice optional, and both option pages show as optional. Claude agrees, since "If you choose this option" already makes the line conditional. Left: the semicolon on line 15 ("…for your final essay; keep them in view as you write"). Once it is settled, the line-14 flag comes off. **Late on 2026-10-26:** the semicolon is now "so" (Andreas), and the flag's removal is pending. Minor, no flag: "…for your final essay so keep them…" wants a comma before "so". The same applies to Option B.

### Option B: Compare Plan A and Plan S

[[Lenses/XLab Verification - v-intuitions-b1]].

- **Lens's text:** the tldr; lines 16 and 17; line 23 (our framing of the Plan S comparison, which passes); line 119; lines 139 and 143.
- **Spoiler test:** passes.
- **Flag on the page:** line 16, as in Option A.
- **Outcome, evening of 2026-10-26:** as in Option A. The Content point stays, the suggestions from Lens EA's AI are resolved, and the same semicolon is left on line 17.

### Optional: Further Exploration

[[Lenses/XLab Verification - v-intuitions-success]].

- **Lens's text:** the tldr; line 50; the chart headings and captions (lines 57 to 109), which pass.
- **Spoiler test:** passes.
- **Flag on the page:** line 50. **Correction, 2026-10-26:** the flag's gloss, that the charts are all redrawn from AI 2027's published data, repeats the line's own error. Two of the four come from outside AI 2027 (METR's time horizons and Epoch AI's prices); the superhuman-coder forecast and the takeoff chart are the AI 2027 authors' (Andreas).
- **Structure (Andreas, 2026-10-26):** the page embeds about 48,000 words, about 31,600 of them AI 2027 and its two endings and 16,500 the three embedded readings, against its stated 45 minutes. Andreas suggests moving AI 2027 and the readings onto their own linked pages, as Strategic Foundations does, so a learner who has read AI 2027 can skip it. **Built for AI 2027, 2026-10-26 (A41):** AI 2027, its "Explore AI 2027" question (id unchanged, so answers follow it), both endings and the four charts moved word for word to a new page, [[Lenses/XLab Verification - v-intuitions-ai-2027]], which this page now links with a card. The line-50 flag moved with its sentence, with the corrected gloss. The new page's tldr, tutor summary and Works cited are ours; the tldr is for Andreas to rewrite. **Readings built, later on 2026-10-26:** Andreas chose a page each. Scher (2026), the Oxford Martin executive summary and the Scher and Thiergart executive summary moved word for word (checked against the repository) to [[Lenses/XLab Verification - v-intuitions-read-scher-restrictions]], [[Lenses/XLab Verification - v-intuitions-read-oxford-martin]] and [[Lenses/XLab Verification - v-intuitions-read-scher-mechanisms]], each reached by a card after its blurb. Their tldrs and Works cited are ours, and the tldrs are for Andreas to rewrite. All four new pages are hidden optional entries in the unit 1 module and the archived Module 0. This page's 45 reading minutes are now stale (stage 8). **The three tldrs, checked (evening):** each is one sentence of 23 to 32 words, with no semicolon or em dash, and the readings have no exercise to spoil. The figures are checked against the papers: Scher's abstract gives 28 candidate mechanisms, including whistleblowers and reviews of training code, and section 3.3 covers chip use. Since Claude wrote them, the read for whether they sound like AI is Andreas's (A4). **Kept (Andreas, late on 2026-10-26):** these three and the AI 2027 tldr are concise and to the point, with no distracting phrasing. Andreas rewrote AI 2027's chart sentence, and the flag's removal is pending. Minor: "rebuild both figures from that scenario and real benchmarks" can read as two charts, and Epoch AI's chip prices are a trend rather than a benchmark. A candidate, if wanted: "rebuild two figures from that scenario and two real-world trends".

### Primer Practice: Inspection, Commitment, and Logic

[[Lenses/XLab Verification - v-intuitions-drills-1]]. The questions and explanations are XLab's.

- **Lens's text:** the tldr; the introduction (lines 12 and 13); the callout titles "Why (open after you have answered)", which pass.
- **Spoiler test:** passes.
- **Flag on the page:** line 12.
- **For Andreas and Elias:** line 99 says "Three needles are buried in eleven terms", but the question on line 80 lists nine ("Nine terms, deliberately over-stocked"). XLab's own round had eleven. Candidate: "nine".
- **Review of the rewrite, evening of 2026-10-26:** the fragment is gone, and "the primer bench" with it. One word: "a handful of drills that covers" should be "that cover". Line 13 is unchanged, so the "clipped" point is a judgment call.
- **Placement (Andreas, evening of 2026-10-26):** the page is the last, required page of unit 1, but it drills Strategic Foundations material, which comes in unit 2, and needs knowledge the learner has not been taught. XLab made the same move on 2026-10-22, from the end of its 0.2 to the end of 0.4 Strategic Foundations, after our port. Even in unit 2, CV1 teaches only part of it. The facts and a proposal are Q20 in the log; not built.
- **Done, late on 2026-10-26.** "That cover" is fixed (Andreas), and the line-12 flag's removal is pending. The platform's own course check had already flagged line 17, "inspection game", as a term used before it is explained, which is Andreas's placement point.
- **For Andreas and Elias:** the fourth question's key, "Fearon's ways of making a commitment credible", credits Fearon with "mechanical enforcement". Fearon (1997) names two ways, tying hands and sinking costs; the word "mechanical" does not appear in the article. The nearest thing to "remove the choice entirely" is the doomsday machine in Ross §6. A learner who has read Fearon could reasonably reject the keyed answer.

### Left for stage 7 (unit 1)

- "Keep your final essay for peer review" in Options A and B (A7).
- XLab section numbers in the Works cited titles stay, as citations.

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

- Lines 194 to 195 (181 to 182 before the bullets went in), in "Notes and sources": "Quotations are matched against the committed copy of the paper at test time, so a quote that drifts fails the build rather than sitting on the page." This describes XLab's build, which Lens does not have, so on our page it is not true. Candidate: cut the sentence.

**Left for stage 7**

- "1.2" throughout (section numbers), "Week 5" on lines 20 and 196, and "1.2.2" in the Works cited title, which is a citation and stays.
