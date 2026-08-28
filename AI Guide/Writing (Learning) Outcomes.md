---
tags:
  - validator-ignore
---
# Writing (Learning) Outcomes (AI Guide)
## Outcomes

**Outcome** is the umbrella term for an intended or observed change in a learner's learning, actions, circumstances, or internal state.

Lens distinguishes five outcome types:

| Outcome type | Example | Why | Visibility to users |
|---|---|---|---|
| **Learning outcome** | Can compare two alignment proposals and explain an important disagreement | Participants need knowledge and skills to be able to contribute to AI Safety | Very user-facing. Forms basis for tests users take. |
| **Artifact** | Has produced a personal contribution plan |Various reasons | May appear as a user-facing milestone |
| **Action** | Has discussed the plan with two practitioners | Builds self-efficacy and excitement, and has actual impact | May appear as a user-facing milestone |
| **Disposition** | Feels able and willing to contribute to AI safety | We want to know whether *on average*, we help people get excited about contributing to AI Safety | Individuals will never be judged for their dispositions, e.g. it's not part of their certificates. We use this data just for improving our offerings. |
| **Downstream Impact** | Makes a sustained, useful contribution to AI safety | Our courses are only useful insofar as they help participants reduce x-risk | Internal program-evaluation or theory-of-change measure |

Learning-outcome files live in `Lens Edu/Learning Outcomes/`. They contain tests and are used in modules.

Artifact, action, disposition, and impact outcome files live in the sibling `Lens Edu/Outcomes/` folder. The steps required to achieve them can span several modules. They're only included in Course, Module, and Lens files by mentioning them inside %% comments %%. These help us focus our attention on things we care about, but aren't yet used programatically by the system.

### What a learning outcome is (and isn't)

A learning outcome is something the student can *do* after the content, phrased so you can check whether they can do it. The file holds two things: the outcome statement (frontmatter `learning-outcome:`) and the test intended to measure it (`## Test:`). If you can't imagine the test, you don't have an outcome yet.

Things that are **not** learning outcomes:

- **A topic.** "Feedback loops are accelerating civilization" names an area of content; it doesn't say what the student can do with it. Convert it: what question about this topic should the student be able to answer, and to what depth?
- **A learning objective.** The instructor's purpose for teaching ("get students engaged with AI safety") belongs to the theory of change. If it matters, find the observable behavior that would show it happened and write *that* as the outcome.
- **An activity.** "Read chapter 3" is what the student does on the way, not what they can do afterwards.
- **A reading's takeaway.** An outcome reverse-engineered from an assigned text ("understands what chapter 2 argues") is a comprehension check, not a skill (see the next section).

## Where learning outcomes come from
- LO should point at a thing we actually care about.
	- Ane thing to ask might be "can a person understand a more advanced version of this without understanding this simpler LO?". If yes, we might not be pointing at a thing that people really need to know.

Work backward from real-world performance, not forward from content:

1. Start from what someone contributing to AI safety must be able to do: the skill-tree topic or the contribution-role requirement the course serves.
2. Write the learning outcome statement, then its test, then the practice that prepares for the test.
3. Only then pick or commission the readings and lenses. They are teaching routes to the outcome, chosen for it, not the source of it.

In practice, creating courses requires a back and forth between learning outcomes and learning material. The process is not as linear as suggested here.

### Writing a Learning Outcome Statement

1. **Start with an action verb.** Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize. Avoid "understand", "know", "appreciate", "be familiar with": you can't tell from the outside whether someone understands; you can tell whether they can explain.
2. **Name the mechanism, not just the claim.** "Explain why misaligned AI is dangerous" is weak; "Explain why a capable AI optimizing for resource-intensive goals can eliminate humanity *without hostile intent, as a byproduct of its own objectives*" pins the actual reasoning move the student must make. Precision beats brevity. The strongest form is situated: "Given ⟨an unfamiliar case⟩, the learner can ⟨do X⟩, identify the assumptions required, and name a case where it does not apply."
3. **Apply the checks:**
   - Is this something the learner would actually do in the real world (explain to a skeptic, evaluate a proposal, spot the flaw in an argument)?
   - Can I tell when they've done it?
   - Could someone become proficient at this without practice? If not, the lenses must contain practice with feedback, not just reading.

## Test Questions

{++{"author":"Elias's AI","timestamp":1787910715005}@@One `## Test:` may contain multiple gradable questions and roleplays. Each item receives its own score. The platform does not currently combine those scores into an LO-level pass/fail result. It marks the test complete after the learner submits every required item, regardless of scores. LO completion likewise tracks completion of the required content and test, not demonstrated mastery. Question scores contribute separately to course assessment.

Prefer one integrated question when it can test the whole skill. Use multiple questions only when the outcome has inseparable facets that one prompt cannot measure well; keep them in one LO only when they genuinely express one skill.

++}The dominant defects in existing outcomes are recall tests and leading prompts. Avoid both:

- **Grade reasoning, not agreement.** A learner who understands the argument and disagrees well {--{"author":"Elias's AI","timestamp":1787910715005}@@passes.--}{++{"author":"Elias's AI","timestamp":1787910715005}@@should receive a strong score.++} Generally, we want to assess whether they can reconstruct, evaluate, and respond to the argument, not whether they accept its conclusion. Ideally,{--{"author":"Elias's AI","timestamp":1787910715005}@@ we want --}{++{"author":"Elias's AI","timestamp":1787910715005}@@ ++}participants {--{"author":"Elias's AI","timestamp":1787910715005}@@to--}{++{"author":"Elias's AI","timestamp":1787910715005}@@should++} pass the ideological Turing test.
- **Test the object, not the text.** The reading points at something (a mechanism, a distribution, a structural relationship). Test *that*, and prefer a case the readings do not contain. A question answerable by recalling the assigned text measures assignment completion. If the student can pass by remembering what an author said rather than by reasoning about the thing the author was describing, the question is wrong.
- **Test the shape of the possibility space, including non-linear structure.** Where a topic has mathematical structure, the question should make that structure do work: not only "what happens" but under what interactions, thresholds, and combinations. Non-linear interactions between parts of a system are the most commonly untested and the most load-bearing: a student who models a system as a sum of independent parts will get the qualitative answer wrong whenever feedback, saturation, or a threshold matters. Ask by-when and under-what-conditions questions, not only whether-and-why ones.

Temporary move: [[../../Lens/base/Deleted bits from 'writing learning outcomes']]

### Test Questions vs Practice Questions
- distinguish between questions that test understanding of the world and questions that are good learning material but not good testing material.
- All good test questions are good practice questions. Not all good practice questions are good test questions.
- For example, beginner-level learning outcomes (and their test questions) should be the sort of things that every advanced person in the field should be expected to know. "Solve 1+x=2 for x" is good, "How does Johnny explain how to solve 1+x=2" might be a good learning-question but is not a good test question because not every advanced person is expected to know this, nor would benefit to know this.
### Test Question Rubrics

{--{"author":"Elias's AI","timestamp":1787910717912}@@We're not yet 100% sure how our --}{++{"author":"Elias's AI","timestamp":1787910717912}@@Write each ++}rubric{--{"author":"Elias's AI","timestamp":1787910717912}@@ should work, but--}{++{"author":"Elias's AI","timestamp":1787910717912}@@ so++} the {--{"author":"Elias's AI","timestamp":1787910717912}@@overall grade should be--}{++{"author":"Elias's AI","timestamp":1787910717912}@@grader can assign++} a {--{"author":"Elias's AI","timestamp":1787910717912}@@single pass or fail. We do think rubrics can sometimes contain multiple pass/fail checks --}{++{"author":"Elias's AI","timestamp":1787910717912}@@defensible 0 ++}to{--{"author":"Elias's AI","timestamp":1787910717912}@@ build up the whole. But it's important that each subject itself is binary as well. Like, you can say, "The--}{++{"author":"Elias's AI","timestamp":1787910717912}@@ 100 score. Turn broad qualities into observable checks. For example, specify which claims, distinctions, or reasoning steps a strong++} answer {--{"author":"Elias's AI","timestamp":1787910717912}@@must have 3 out of these 5 qualities," as long as each of those 5 qualities is binary as well.--}{++{"author":"Elias's AI","timestamp":1787910717912}@@contains and how missing load-bearing elements affect the score.++}

{--{"author":"Elias's AI","timestamp":1787910717912}@@Beyond pass/fail tests, it's still useful for Lens Coach to provide qualitative --}{++{"author":"Elias's AI","timestamp":1787910717912}@@Assessment and ++}feedback{--{"author":"Elias's AI","timestamp":1787910717912}@@ on what went well and what could've been better.

These --}{++{"author":"Elias's AI","timestamp":1787910717912}@@ ++}are{--{"author":"Elias's AI","timestamp":1787910717912}@@ two separate fields, and a test question should set both deliberately rather than leaving either to a default.--}{++{"author":"Elias's AI","timestamp":1787910717912}@@ separate.++} `assessment-instructions::` is the grader's brief: it decides the score and the learner never sees it. `feedback-instructions::` is the tutor's brief: if present, the tutor gets the question, the answer, the score, and the private grading reason, {--{"author":"Elias's AI","timestamp":1787910717912}@@and--}{++{"author":"Elias's AI","timestamp":1787910717912}@@then++} replies to the learner; if absent, the learner sees only the percentage. Say in `feedback-instructions::` what good feedback names, {--{"author":"Elias's AI","timestamp":1787910717912}@@for example--}{++{"author":"Elias's AI","timestamp":1787910717912}@@such as++} the strongest part of the answer and the one change that would most improve it.{--{"author":"Elias's AI","timestamp":1787910717912}@@ Keep the two apart: feedback--}{++{"author":"Elias's AI","timestamp":1787910717912}@@ Feedback++} guidance never belongs in the assessment brief, where it {--{"author":"Elias's AI","timestamp":1787910717912}@@would become an extra condition for passing.--}{++{"author":"Elias's AI","timestamp":1787910717912}@@could accidentally affect the score.++}

## Learning Outcome Files

{--{"author":"Elias's AI","timestamp":1787910720411}@@A learning outcome--}{++{"author":"Elias's AI","timestamp":1787910720411}@@One learning-outcome++} file {--{"author":"Elias's AI","timestamp":1787910720411}@@can contain--}{++{"author":"Elias's AI","timestamp":1787910720411}@@defines++} one{--{"author":"Elias's AI","timestamp":1787910720411}@@ or more inseparable learning outcomes, in the sense that they are passed or failed together. --}{++{"author":"Elias's AI","timestamp":1787910720411}@@ testable skill. ++}If {--{"author":"Elias's AI","timestamp":1787910720411}@@it seems fair for the learner to pass one learning outcome but fail another, these should live--}{++{"author":"Elias's AI","timestamp":1787910720411}@@two capabilities could reasonably be taught, tested, or improved independently, put them++} in separate {--{"author":"Elias's AI","timestamp":1787910720411}@@learning outcome files.

An outcome is one pass/fail completion unit, not--}{++{"author":"Elias's AI","timestamp":1787910720411}@@files.

Related capabilities at different levels, such as awareness, application, and producing++} a {--{"author":"Elias's AI","timestamp":1787910720411}@@graded system. Deeper ldevels of capability on--}{++{"author":"Elias's AI","timestamp":1787910720411}@@plan, are separate learning-outcome files sequenced by++} the {--{"author":"Elias's AI","timestamp":1787910720411}@@same topic are classified--}{++{"author":"Elias's AI","timestamp":1787910720411}@@module. Use names such++} as{--{"author":"Elias's AI","timestamp":1787910720411}@@ seprate learning outcome files ("⟨Topic⟩--}{++{"author":"Elias's AI","timestamp":1787910720411}@@ `⟨Topic⟩++} Level {--{"author":"Elias's AI","timestamp":1787910720411}@@2").

I.e. related outcomes at different--}{++{"author":"Elias's AI","timestamp":1787910720411}@@2` when++} levels {--{"author":"Elias's AI","timestamp":1787910720411}@@(awareness → application → producing --}{++{"author":"Elias's AI","timestamp":1787910720411}@@share ++}a{--{"author":"Elias's AI","timestamp":1787910720411}@@ plan) are separate files, sequenced by the module.--}{++{"author":"Elias's AI","timestamp":1787910720411}@@ topic.++}
### File syntax

The filename is the learner-visible skill name (modules and the skill tree display it). Conventions (settled in [[../../Lens/base/Learning Outcome Short-Name Proposal]]): a short noun phrase, 2 to 6 words, sentence case; the verb lives in the outcome statement, not the title; no course prefixes (outcomes are course-agnostic); unique across the folder.

```markdown
---
id: <uuid>
learning-outcome: <the statement>
---
## Test:
id:: <uuid>
#### Question: Open
id:: <uuid>
content:: <the test question>
assessment-instructions:: <the rubric (see above)>
feedback-instructions:: <what the tutor should tell the learner afterwards; omit for score only>

# Suggested Lenses:
## Lens:
source:: [[../Lenses/My Topic - PQ]]
notes:: <optional author note about this suggestion>

## Lens:
source:: [[../Lenses/My Topic]]
```

- A Test may only contain gradable response segments and roleplays: `Question: Open` with `assessment-instructions::`, `Question: Choice` with at least one `[x]`, `Question: FillBlank` with at least one graded blank, `Question: Ranking` with `assessment-instructions::`, or `Roleplay`. `Question: Rating` and ungraded variants are validation errors in a test; anything else is flagged and would be silently dropped. Never write a bare `#### Question`. Field syntax: [[../Lenses/Response to question segments]].
- Suggested lenses are **author-facing candidates only**: the platform doesn't import them; the module lists its teaching lenses explicitly, before the `# Learning Outcome:` ref. Outcome files without suggested lenses are valid too.
- Skill-tree frontmatter is rolling out per `Lens/Learning Outcome Domain and Stage Proposal.md`: `domain:` (one of the 15 domains in `Lens/AI Safety Skill Taxonomy - Canonical Working Inventory.md`), `stage:` (Beginner, Intermediate, or Advanced), `requires:` (sparse; only genuine prerequisites, since they gate locked status). Set them on new outcomes.


## Background context

### UNESCO: cognitive, socio-emotional, and behavioural outcomes 

UNESCO's global-citizenship education framework distinguishes cognitive, socio-emotional, and behavioural domains. It includes knowledge and critical thinking; values, attitudes, empathy, and belonging; and practical engagement and action. It explicitly includes motivation and willingness to act while treating the domains as interlinked.

- [UNESCO, Global Citizenship Education: Topics and Learning Objectives](https://www.unesco.org/sites/default/files/gcedtopicsandlearningobjectives_01.pdf)

### OECD: knowledge, skills, attitudes, values, and agency 

The OECD Learning Compass describes education as developing knowledge, skills, attitudes, values, and student agency. It also acknowledges important outcomes such as responsibility, empathy, and agency that are not adequately captured by conventional test instruments.

- [OECD, Learning Compass FAQs](https://www.oecd.org/content/dam/oecd/en/about/projects/edu/education-2040/1-1-learning-compass/Learning%20Compass%20FAQs.pdf/_jcr_content/renditions/original./Learning%20Compass%20FAQs.pdf)
- [OECD, What Students Learn Matters](https://www.oecd.org/content/dam/oecd/en/publications/reports/2020/11/what-students-learn-matters_555a22ec/d86d4d9a-en.pdf)

