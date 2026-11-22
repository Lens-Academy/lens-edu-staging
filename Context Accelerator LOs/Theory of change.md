---
id: 92696a32-196c-4f45-8d1a-e170f2f1a68d
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Lay out a theory of change as a chain of steps from an action to the outcome it aims at, and spot weak ones: missing links, merged steps, unnamed actors, unstated assumptions and goals that stop short of impact.

## Requires

## Helpful first
- [[Theories of victory]]

## Why it matters
Many projects aimed at AI risk can say what they will do but not how that leads to less risk. Writing the chain out shows which step is weakest, so you can test it, fix it or pick different work before spending months on an action that cannot reach its goal.

## Lenses
- [[../Lenses/alexander-nailing-the-basics-theories-of-change-why-theories-of-change-matter first half|Why theories of change matter]]: what a theory of change is and what it is for.
- [[../Lenses/alexander-nailing-the-basics-theories-of-change second half|How to build a theory of change]]: questioning each step, and common mistakes.
- [[../Lenses/XLab Verification - v-theories-of-change|We Need More Theories of Change]]: why others need your chain of if-then claims.
- [[../Lenses/charbel-rapha-l-against-almost-every-theory-of-impact-of-interpretability|Against Almost Every Theory of Impact of Interpretability]]: a critique of interpretability's theories of impact, one by one.
- [[../Lenses/Theories of Change Need a Theory of Victory]]: linking a local result to solving the whole problem.
- [[../Lenses/nanda-a-longlist-of-theories-of-impact-for-interpretability|Theories of impact for interpretability]] (Noah's CG list 🟢)

## Tests
#### Question: Choice
id:: 88479998-3f90-424e-a147-b69ede0805a4
content:: What makes a plan a theory of change rather than a description of a project?
options::
- [x] It spells out how each step is expected to cause the next, up to the final goal.
- It lists the project's activities and the resources each one needs.
- It sets a measurable target and a deadline for each activity.
- It explains why the problem the project works on is important.
shuffle:: true

#### Question: Choice
id:: 988b309a-e465-4fc6-bea0-739737143f3d
content:: A policy group's theory of change includes the step "Government passes and enforces rules on frontier AI training." What is the main weakness of this step?
options::
- [x] It merges two outcomes, hiding the risk that rules pass but go unenforced.
- It depends on a government's choices, which a theory of change should leave out.
- It describes an outcome when it should describe one of the group's activities.
- It is a final goal, so it belongs at the end of the chain, not in the middle.
shuffle:: true

#### Question: Choice
id:: 45074778-17d3-4b59-b170-2a21c810c65f
content:: A research group's theory of change ends with the step "Our interpretability papers are widely cited." What is its main problem?
options::
- [x] It stops before the outcome that matters, such as lower risk from AI.
- It depends on other researchers' choices, which the group can't control.
- It sets a bar too high for a single research group to reach.
- It is hard to measure, so the group can't tell whether it is on track.
shuffle:: true

#### Question: Choice
id:: 6ada06e1-897c-4161-8208-4b9fb1da207c
content:: Which of these single steps in a theory of change leaves the largest gap unexplained?
options::
- [x] "Run AI risk awareness ads → AI companies adopt stronger safety practices"
- "Fund a research fellowship → fellows complete AI safety research projects"
- "Hire a recruiter → the recruiter contacts promising candidate researchers"
- "Write a policy brief → the brief is sent to staff on a committee"
shuffle:: true

#### Question: Choice
id:: f9371eff-08bb-4480-9204-22c27a2ed233
content:: Which rewrite of the theory of change step "Safety evaluations are run before deployment" best makes clear who acts?
options::
- [x] "The AI company's safety team runs evaluations before each deployment."
- "Safety evaluations are run more often and earlier before deployment."
- "Thorough, independent safety evaluations are run before deployment."
- "Safety evaluations before deployment become standard industry practice."
shuffle:: true

#### Question: Choice
id:: 2c597627-7214-413d-8445-2ecd53ed7268
content:: A project's theory of change marks one step as much less certain than the others. Where should the project put its first measurement effort?
options::
- [x] On that uncertain step, since it most likely decides whether the plan works.
- On the first step, since every later step depends on it happening.
- On the final impact, since that is what the project cares about.
- On the step that is cheapest and quickest to measure well.
shuffle:: true

#### Question: Choice
id:: 0cb271cb-e552-4ba1-b648-e90312e06612
content:: A theory of change says "Train AI governance researchers → AI policy improves." A reviewer splits the arrow into four steps that must all happen, each judged 80% likely and independent of the others. What does this imply about the plan as a whole?
options::
- [x] It is less likely to work than any one of its steps.
- It is about 80% likely to work, like a typical step.
- It is more than 80% likely to work, since there are four chances to make progress.
- Nothing, until we know which of the four steps comes first.
shuffle:: true

#### Question: Choice
id:: c695a8e0-abeb-4de2-97a1-b348f42a084b
content:: A theory of change says: "We show a model can deceive its evaluators → we publish the finding → AI companies slow their deployments." Which unstated assumption does the last step mainly depend on?
options::
- [x] That companies believe the finding and judge slowing down worth the cost.
- That the finding can be written up and published in a public paper.
- That the model studied is the most capable one currently available.
- That other researchers can repeat the experiment and get the same result.
shuffle:: true

#### Question: FillBlank
id:: 3cdef78b-8142-474a-9d2f-8ba4611384a0
content:: The step or assumption in a theory of change that the project's success depends on most, and that most needs testing, is often called its {{crux}}.

#### Question: Open
id:: 44b8e006-8855-4e6a-bac0-a3819a3acb3d
content:: Here is a theory of change: "We run free online courses on AI risk → more people understand AI risk → risk from AI falls." Name one missing link and one unstated assumption.
assessment-instructions:: Score out of 100. 50: a missing step, for example graduates take jobs or actions on AI risk, or those actions change what AI companies or governments do. 50: an assumption, for example people finish and understand the course, understanding leads to action, or the actions help rather than harm. 25 each if vague.

#### Question: Open
id:: 76e02e6f-4ba3-48b5-bbab-a1ef09f8a16c
content:: Why write down a theory of change for your work, even if you are already confident the work helps?
assessment-instructions:: Score out of 100. 100 for any one of these with a reason: it exposes hidden assumptions and missing steps; others can check and criticise it; it shows which step is weakest and most needs testing or measuring; it gives a basis for changing or stopping the work. 50 for "to plan better" with no mechanism.

#### Question: Open
id:: 8dc4870d-6995-44ea-a429-477a0d2e0d46
content:: A theory of change says: "Build better interpretability tools → detect deceptive AI models before deployment → prevent catastrophe." Pick one link and say how it could fail.
assessment-instructions:: Score out of 100. 100 for a specific, plausible failure in a named link, for example: the tools don't work on frontier-scale models; a deceptive model hides from them; the company detects deception but deploys anyway or merely retrains it; the tools miss other routes to catastrophe. 50 if the failure is real but not tied to a link.
