---
tags:
  - validator-ignore
---
# Writing Learning Outcomes (AI Guide)

Luc's additions 6 august:

Best practices:
...


Our design pattern:
- learning outcomes are binary tests. Maybe build up of subjudgements, e.g. "answer should pass on 3 out of these 5 criteria"
- LO should point at a thing we actually care about.
	- distinguish between questions that test understanding of the world and questions that are good learning material but not good testing material.
	- Beginner-level learning outcomes should be the sort of things that every advanced person in the field should be expected to know. "Solve 1+x=2 for x" is good, "How does Johnny explain how to solve 1+x=2" might be a good learning-question but is not a good test-question because not every advanced person is expected to know this, nor would benefit to know this.
	- Another thing to ask might be "can a person understand a more advanced version of this without understanding this simpler LO?". If yes, we might again not be pointing at a thing that people really need to know.

## What a learning outcome is (and isn't)

A learning outcome is **one testable skill**: something the student can *do* after the content, phrased so you can check whether they can do it. The file holds two things: the outcome statement (frontmatter `learning-outcome:`) and the test that verifies it (`## Test:`). If you can't imagine the test, you don't have an outcome yet.

Things that are **not** learning outcomes:

- **A topic.** "Feedback loops are accelerating civilization" names an area of content; it doesn't say what the student can do with it. Convert it: what question about this topic should the student be able to answer, and to what depth?
- **A learning objective.** The instructor's purpose for teaching ("get students engaged with AI safety") belongs to the theory of change. If it matters, find the observable behavior that would show it happened and write *that* as the outcome.
- **An activity.** "Read chapter 3" is what the student does on the way, not what they can do afterwards.
- **A reading's takeaway.** An outcome reverse-engineered from an assigned text ("understands what chapter 2 argues") is a comprehension check, not a skill (see the next section).

## Where outcomes come from

Work backward from real-world performance, never forward from content:

1. Start from what someone contributing to AI safety must be able to do: the skill-tree topic or the contribution-role requirement the course serves.
2. Write the outcome statement, then its test, then the practice that prepares for the test.
3. Only then pick or commission the readings and lenses. They are teaching routes to the outcome, chosen for it, not the source of it.

The inversion check: if you are holding a reading and asking "what outcome fits this?", you are inverted. Write the capability first, then judge whether that reading actually teaches it.

## Writing the statement

1. **Start with an action verb.** Explain, Distinguish, Identify, Compare, Analyze, Evaluate, Apply, Recognize. Avoid "understand", "know", "appreciate", "be familiar with": you can't tell from the outside whether someone understands; you can tell whether they can explain.
2. **Name the mechanism, not just the claim.** "Explain why misaligned AI is dangerous" is weak; "Explain why a capable AI optimizing for resource-intensive goals can eliminate humanity *without hostile intent, as a byproduct of its own objectives*" pins the actual reasoning move the student must make. Precision beats brevity. The strongest form is situated: "Given ⟨an unfamiliar case⟩, the learner can ⟨do X⟩, identify the assumptions required, and name a case where it does not apply."
3. **Apply the checks:**
   - Is this something the learner would actually do in the real world (explain to a skeptic, evaluate a proposal, spot the flaw in an argument)?
   - Can I tell when they've done it?
   - Could someone become proficient at this without practice? If not, the lenses must contain practice with feedback, not just reading.{>>{"author":"Luc","timestamp":1785962350939}@@I know what book this comes from, and I think it's potentially good, but it requires more context if we want to use it here<<}{>>{"author":"Luc","timestamp":1785962402275}@@btw, relatedly, I suggest maybe not calling outcomes "skills". Bcs that book defines skills as the thing that require practice beyond just gaining knowledge<<}

## Scope: one skill per file

One outcome = one testable skill. The tell that you have two: describing a passing answer needs an "and also" joining two claims that could be understood independently. Split it. An outcome is one pass/fail completion unit. Genuinely deeper capability on the same topic is a separate leveled outcome file ("⟨Topic⟩ Level 2"); rubric levels above the pass bar calibrate feedback, they don't credential extra depth. Related outcomes at different levels (awareness → application → producing a plan) are separate files, sequenced by the module.

## Write the rubric first

The 1–5 rubric is the outcome's operational definition: the test question's `assessment-instructions::` hold a 5-level rubric where **every level has a verbatim example answer**:

```
**1**: <failure mode>. *Example: "<what a level-1 answer sounds like>"*
**2**: <partial understanding>. *Example: "..."*
**3**: <correct mechanism, the pass bar>. *Example: "..."*
**4**: As above, plus <structural implication>. *Example: Adds "..."*
**5**: As above, plus <deepest connection>. *Example: Adds "..."*
```

Levels 4 and 5 are written as "As above, plus…" so graders compose rather than re-judge. Write it before designing lenses: level 3 is the pass bar, levels 1 and 2 name the failure modes the lenses must head off, levels 4 and 5 name the depth the best lenses can reach for. If you can't write distinct level-1, level-3, and level-5 example answers, the outcome is too vague or too big. Fix the statement, not the rubric.

## Make the test valid

The dominant defects in existing outcomes are recall tests and leading prompts. Avoid both:

- **Require transfer at the pass bar.** The test presents an unfamiliar case or application. An answer that only reconstructs the source's argument is a level-2 answer, not a pass.
- **Don't teach the answer in the stem.** If the question restates the argument before asking about it, it tests reading the stem, not the capability.
- **Grade reasoning, not agreement.** A learner who understands the argument and disagrees well passes. Assess whether they can reconstruct, evaluate, and respond to the argument, never whether they accept its conclusion.{++{"author":"Lauren's AI","timestamp":1786033405239}@@
- **Test the object, not the text.** The reading points at something (a mechanism, a distribution, a structural relationship). Test *that*, and prefer a case the readings do not contain. A question answerable by recalling the assigned text measures assignment completion. If the student can pass by remembering what an author said rather than by reasoning about the thing the author was describing, the question is wrong.
- **Test the shape of the possibility space, including non-linear structure.** Where a topic has mathematical structure, the question should make that structure do work: not only "what happens" but under what interactions, thresholds, and combinations. Non-linear interactions between parts of a system are the most commonly untested and the most load-bearing: a student who models a system as a sum of independent parts will get the qualitative answer wrong whenever feedback, saturation, or a threshold matters. Ask by-when and under-what-conditions questions, not only whether-and-why ones.

## Test before, then test again after

Test the same capability **twice**: once before the student reads anything, once afterwards.

The pre-reading test should go as deep as the student can currently manage. Its purpose is not assessment. A student who has committed to an answer reads differently: they have something at stake, and the reading either confirms or corrects a position they already hold. This is why `[episode]` material (an account of something that actually happened, with an outcome) is worth more than its length suggests, and it is why the pre-test must be scored generously; the student is *supposed* to be wrong, and telling them so up front removes the incentive to hedge.

The post-reading test must target the same capability while being **different enough that reproducing the reading does not answer it.** If a student can pass the second test by paraphrasing what they just read, the pair has measured nothing. The move required between the two should be qualitative generalisation, not restatement: a different domain, an inverted case, a condition where the mechanism does not hold, or a composition of two mechanisms the reading treated separately.

The failure this prevents is a course where students learn to recognise the assigned texts. That is a real failure mode and it is invisible from the inside: comprehension checks look like learning, and a class that has read carefully will pass them.++}

## File syntax

The filename is the learner-visible skill name (modules and the skill tree display it). Conventions (settled in `Lens/Learning Outcome Short-Name Proposal.md`): a short noun phrase, 2 to 6 words, sentence case; the verb lives in the outcome statement, not the title; no course prefixes (outcomes are course-agnostic); unique across the folder.

```markdown
---
id: <uuid>
learning-outcome: <the statement>
---
## Test:
id:: <uuid>
#### Question
content:: <the test question>
assessment-instructions:: <the 1–5 rubric (see above)>

# Suggested Lenses:
## Lens:
source:: [[../Lenses/My Topic - PQ]]
notes:: <optional author note about this suggestion>

## Lens:
source:: [[../Lenses/My Topic]]
```

- A Test may only contain question/roleplay segments; anything else is flagged and would be silently dropped. Their field syntax: `Lens Edu/AI Guide/Writing Lenses.md` ("The 6 segment types").
- Suggested lenses are **author-facing candidates only**: the platform never imports them; the module lists its teaching lenses explicitly, before the `# Learning Outcome:` ref. Zero-suggestion outcomes are valid.
- Skill-tree frontmatter is rolling out per `Lens/Learning Outcome Domain and Stage Proposal.md`: `domain:` (one of the 15 domains in `Lens/AI Safety Skill Taxonomy - Canonical Working Inventory.md`), `stage:` (Beginner, Intermediate, or Advanced), `requires:` (sparse; only genuine prerequisites, since they gate locked status). Set them on new outcomes.

## {--{"author":"Luc's AI","timestamp":1786087623061}@@Outcome types--}{++{"author":"Luc's AI","timestamp":1786087623061}@@Outcomes beyond learning outcomes {>>{"author":"Luc's AI","timestamp":1786087623061}@@Use somewhere in courses, but maybe not in learning outcomes skill, which might be only about capabilities?<<}

**Outcome** is the umbrella term for an intended or observed change in a learner's learning, actions, circumstances, or internal state. A **learning outcome** is the testable kind defined by this guide: something the learner can demonstrate after learning. Not every desired effect of a course is therefore a learning outcome.++}

{--{"author":"Luc's AI","timestamp":1786087623061}@@An--}{++{"author":"Luc's AI","timestamp":1786087623061}@@Lens distinguishes five++} outcome {--{"author":"Luc's AI","timestamp":1786087623061}@@file holds --}{++{"author":"Luc's AI","timestamp":1786087623061}@@types:

| Outcome type | Example | Role in Lens | Completion and visibility |
|---|---|---|---|
| **Learning outcome** | Can compare two alignment proposals and explain an important disagreement | The central kind represented in the topic or skill graph | User-facing; may be assessed and completed |
| **Artifact** | Has produced ++}a {--{"author":"Luc's AI","timestamp":1786087623061}@@**capability**:--}{++{"author":"Luc's AI","timestamp":1786087623061}@@personal contribution plan | A concrete product created by the learner; it may also provide evidence for one or more learning outcomes | May appear as++} a {--{"author":"Luc's AI","timestamp":1786087623061}@@demonstrable skill. Other things --}{++{"author":"Luc's AI","timestamp":1786087623061}@@user-facing milestone; completion means the artifact exists or meets explicit criteria |
| **Action** | Has discussed the plan with two practitioners | Something the learner has done in the world, rather than merely demonstrated in an exercise | May appear as a user-facing milestone; completion verifies the action, not mastery of a general skill |
| **Disposition** | Feels able and willing to contribute to AI safety | An attitude, motivation, value, belief, sense of agency, or other psychological state that the course hopes to support | Internal only; not pass/fail. It may be studied through self-report or other indicators |
| **Impact** | Makes ++}a {++{"author":"Luc's AI","timestamp":1786087623061}@@sustained, useful contribution to AI safety | A longer-term effect that the program hopes to make more likely | Internal program-evaluation or theory-of-change measure; not ++}course {--{"author":"Luc's AI","timestamp":1786087623061}@@targets are--}{++{"author":"Luc's AI","timestamp":1786087623061}@@completion and generally++} not {--{"author":"Luc's AI","timestamp":1786087623061}@@capability outcomes:--}{++{"author":"Luc's AI","timestamp":1786087623061}@@user-facing |++}

{--{"author":"Luc's AI","timestamp":1786087623061}@@- **Artifacts** (a --}{++{"author":"Luc's AI","timestamp":1786087623061}@@The same activity can play more than one role. A ++}personal {--{"author":"Luc's AI","timestamp":1786087623061}@@action plan) --}{++{"author":"Luc's AI","timestamp":1786087623061}@@plan is an artifact, evidence that may support a planning learning outcome, ++}and {--{"author":"Luc's AI","timestamp":1786087623061}@@**actions** (discussed --}{++{"author":"Luc's AI","timestamp":1786087623061}@@potentially one step toward later action. Keep these distinguishable even when they refer to ++}the {--{"author":"Luc's AI","timestamp":1786087623061}@@plan --}{++{"author":"Luc's AI","timestamp":1786087623061}@@same event.

Learning-outcome files continue to live in `Learning Outcomes/`. Artifact, action, disposition, and impact outcome files live in the sibling `Outcomes/` folder for now. Longitudinal outcomes may be referenced across several modules and described in comments in the main course file; they do not need to belong to one module. Lenses may support any of these outcomes even when the outcome develops across a course.

## Diagnose the performance gap before writing a learning outcome

The difference between a learner's current performance and the desired performance is not automatically a learning problem, and it is not always a lack of knowledge.

| Gap type | Diagnostic signal | Design implication | Relation to outcomes |
|---|---|---|---|
| **Knowledge** | The learner lacks information or a useful mental model | Provide and retrieve the necessary knowledge in the context where it will be used | Usually supports a learning outcome |
| **Skill** | The learner knows what to do but cannot yet do it proficiently | Provide realistic, varied, scaffolded practice ++}with {++{"author":"Luc's AI","timestamp":1786087623061}@@feedback | A learning outcome that requires practice, not merely exposure |
| **Motivation** | The learner knows how but does not choose to act | Investigate relevance, incentives, confidence, autonomy, and competing motivations; more information alone is unlikely to solve it | May relate to a disposition, but should not become a pass/fail learner state |
| **Habit** | The learner can and wants to act but does not do so reliably or automatically | Support repetition, cues, follow-up, and changes to the surrounding environment | May produce repeated action milestones; habit strength itself is not ordinary learning-outcome completion |
| **Environment** | Tools, processes, incentives, time, access, or social context obstruct performance | Fix the environment, provide job aids, or remove friction instead of trying to fix the learner | Usually not ++}a {--{"author":"Luc's AI","timestamp":1786087623061}@@practitioner) --}{++{"author":"Luc's AI","timestamp":1786087623061}@@learner outcome |
| **Communication** | Directions or expectations ++}are {--{"author":"Luc's AI","timestamp":1786087623061}@@milestones: verify that--}{++{"author":"Luc's AI","timestamp":1786087623061}@@unclear or misaligned | Clarify the request or success criteria | Not a learning outcome or learning intervention |

A useful skill-gap test is: **Could someone reasonably become proficient at this without practice?** If not, teaching information is insufficient. {>>{"author":"Luc's AI","timestamp":1786087623061}@@We might need Skill for "talking to others" and Habit for "thinking in terms of expected value"<<}

Gap types diagnose *why* current and desired performance differ. Outcome types describe *what changes or milestones Lens cares about*. Evidence types describe *how Lens could know*. Keep these classifications separate.

## Match evidence to++} the {--{"author":"Luc's AI","timestamp":1786087623061}@@thing exists --}{++{"author":"Luc's AI","timestamp":1786087623061}@@outcome type

Different outcome types require different evidence:

- **Learning outcomes:** performance tasks, explanations, decisions, critiques, ++}or {--{"author":"Luc's AI","timestamp":1786087623061}@@happened against --}{++{"author":"Luc's AI","timestamp":1786087623061}@@other observable demonstrations.
- **Artifacts:** existence plus ++}explicit {--{"author":"Luc's AI","timestamp":1786087623061}@@criteria. Completing one doesn't --}{++{"author":"Luc's AI","timestamp":1786087623061}@@quality criteria where quality matters.
- **Actions:** confirmation that the action occurred; this does not by itself ++}establish a transferable {--{"author":"Luc's AI","timestamp":1786087623061}@@skill.--}{++{"author":"Luc's AI","timestamp":1786087623061}@@learning outcome.++}
- {--{"author":"Luc's AI","timestamp":1786087623061}@@**Dispositions** (motivated to contribute, changed beliefs) --}{++{"author":"Luc's AI","timestamp":1786087623061}@@**Dispositions:** optional self-report, interviews, reflection, or aggregate course-effect measures. These ++}are {--{"author":"Luc's AI","timestamp":1786087623061}@@never pass/fail --}{++{"author":"Luc's AI","timestamp":1786087623061}@@indicators rather than proof of an internal state.
- **Impact:** longer-term follow-up ++}and {--{"author":"Luc's AI","timestamp":1786087623061}@@never get an outcome file. --}{++{"author":"Luc's AI","timestamp":1786087623061}@@program-level evaluation, with attention to contextual factors and the difficulty of causal attribution.

++}A learner {--{"author":"Luc's AI","timestamp":1786087623061}@@who reasons well--}{++{"author":"Luc's AI","timestamp":1786087623061}@@should not fail a course merely for retaining a different value judgment or reporting a lower level of enthusiasm. Lens can test whether learners can reason, decide, plan,++} and {--{"author":"Luc's AI","timestamp":1786087623061}@@still disagrees,--}{++{"author":"Luc's AI","timestamp":1786087623061}@@act; it can separately investigate whether the course affected motivation, agency,++} or {--{"author":"Luc's AI","timestamp":1786087623061}@@stays unenthusiastic, has --}{++{"author":"Luc's AI","timestamp":1786087623061}@@values.

A useful evaluation model distinguishes:

- **Reaction:** Did learners find the experience useful, acceptable, engaging, confusing, or frustrating? This is useful evidence about course design and learner experience, but ++}not {--{"author":"Luc's AI","timestamp":1786087623061}@@failed anything. Treat dispositions --}{++{"author":"Luc's AI","timestamp":1786087623061}@@evidence that learning occurred. {>>{"author":"Luc's AI","timestamp":1786087623061}@@hmm what exactly does this mean? seems potentially useful though<<}
- **Learning:** Can learners now demonstrate the intended learning outcome?
- **Behavior:** Are learners applying it or acting differently outside the learning experience?
- **Results:** Did those behaviors contribute to the larger result or impact?

These require different evidence and occur at different distances from the course. A knowledge test should not be used ++}as {--{"author":"Luc's AI","timestamp":1786087623061}@@internal --}{++{"author":"Luc's AI","timestamp":1786087623061}@@evidence of real-world behavior, and behavior after the course should not automatically be attributed to the course.

## Dispositions as ++}design targets, {--{"author":"Luc's AI","timestamp":1786087623061}@@measured (if at all) --}{++{"author":"Luc's AI","timestamp":1786087623061}@@not learner scores

Self-determination theory distinguishes **autonomous motivation**, acting for reasons connected to one's own goals and values, from motivation produced mainly ++}by {++{"author":"Luc's AI","timestamp":1786087623061}@@pressure, guilt, fear, or external control. {>>{"author":"Luc's AI","timestamp":1786087623061}@@we should definitely be using self-determination theory as an evidence-based alternative to our mobilization system<<}

It identifies three psychological needs:

- **Autonomy:** feeling able to choose and align one's behavior with one's values.
- **Competence:** feeling capable of achieving one's goals.
- **Relatedness:** feeling accepted, connected, and that one belongs.

For Lens, these are useful internal design variables and possible ++}aggregate {--{"author":"Luc's AI","timestamp":1786087623061}@@self-report.--}{++{"author":"Luc's AI","timestamp":1786087623061}@@evaluation measures. They should not become visible learner prerequisites or pass/fail criteria.

Support learner agency by:

- Explaining the real problem, the course's purpose, and how an activity is meant to help.
- Connecting rationales to the learner's own goals and values rather than assuming agreement.++}
- {--{"author":"Luc's AI","timestamp":1786087623061}@@**Impact** (a sustained--}{++{"author":"Luc's AI","timestamp":1786087623061}@@Offering meaningful choices and multiple legitimate++} contribution {++{"author":"Luc's AI","timestamp":1786087623061}@@paths.
- Building competence through achievable practice and constructive feedback.
- Fostering belonging without using conformity as evidence of success.
- Avoiding guilt, fear, status pressure, or inadequacy as ways to obtain compliance.
- Treating a learner's different conclusion as compatible with successful learning when they can reason about it well.

Dispositions can be implicit in the learner-facing graph while explicit in the internal theory of change. Lens may intentionally design for agency and sustainable motivation without displaying "motivation achieved" or grading value alignment.

- [Michael Noetel, "We all teach: here's how to do it better"](https://forum.effectivealtruism.org/posts/ZPNNnEu2HGNSNmifo/we-all-teach-here-s-how-to-do-it-better)

## Broader course-design frames

### UNESCO: cognitive, socio-emotional, and behavioural outcomes {>>{"author":"Luc's AI","timestamp":1786087623061}@@I think we also want to mention this in our course creation skills, just to kind of increase the amount of attention in the network on these sorts of thinking.<<}

UNESCO's global-citizenship education framework distinguishes cognitive, socio-emotional, and behavioural domains. It includes knowledge and critical thinking; values, attitudes, empathy, and belonging; and practical engagement and action. It explicitly includes motivation and willingness ++}to {++{"author":"Luc's AI","timestamp":1786087623061}@@act while treating ++}the {--{"author":"Luc's AI","timestamp":1786087623061}@@field) is program-level evaluation,--}{++{"author":"Luc's AI","timestamp":1786087623061}@@domains as interlinked.

- [UNESCO, Global Citizenship Education: Topics and Learning Objectives](https://www.unesco.org/sites/default/files/gcedtopicsandlearningobjectives_01.pdf)

### OECD: knowledge, skills, attitudes, values, and agency {>>{"author":"Luc's AI","timestamp":1786087623061}@@same here, have in course<<}

The OECD Learning Compass describes education as developing knowledge, skills, attitudes, values, and student agency. It also acknowledges important outcomes such as responsibility, empathy, and agency that are++} not {--{"author":"Luc's AI","timestamp":1786087623061}@@a course outcome.--}{++{"author":"Luc's AI","timestamp":1786087623061}@@adequately captured by conventional test instruments.

- [OECD, Learning Compass FAQs](https://www.oecd.org/content/dam/oecd/en/about/projects/edu/education-2040/1-1-learning-compass/Learning%20Compass%20FAQs.pdf/_jcr_content/renditions/original./Learning%20Compass%20FAQs.pdf)
- [OECD, What Students Learn Matters](https://www.oecd.org/content/dam/oecd/en/publications/reports/2020/11/what-students-learn-matters_555a22ec/d86d4d9a-en.pdf)++}

