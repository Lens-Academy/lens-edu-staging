---
id: 13258d8f-2aa6-40bc-9aad-d26fed71b0db
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Distinguish legible AI safety problems, which decision-makers see and reward progress on, from illegible ones that matter but are hard to see or measure; explain why work drifts toward legible problems, and why solving them might mainly speed up deployment.

## Requires

## Helpful first
- [[Goodhart's law]]

## Why it matters
Counting papers, benchmarks or researchers can make AI safety look well in hand while hard-to-measure problems get little attention. If you can spot this gap, you can judge safety plans by which problems they address, and see why explaining a neglected problem to decision-makers can matter as much as research on it.

## Lenses
- [Legible vs. Illegible AI Safety Problems (LessWrong)](https://www.lesswrong.com/posts/PMc65HgRFvBimEpmJ/legible-vs-illegible-ai-safety-problems): Wei Dai's short original post. It covers what makes a problem legible to leaders and policymakers, why solving legible problems may mainly speed up deployment, and why making a problem legible is nearly as good as solving it (Nov 2025).
- [Problems I've Tried to Legibilize (LessWrong)](https://www.lesswrong.com/posts/7XGdkATAvCTvn4FGu/problems-i-ve-tried-to-legibilize): Wei Dai's follow-up listing the illegible problems he has worked on, such as AI philosophical competence, human-AI safety and power concentration. Skim it for what illegible problems look like (Nov 2025).
- [Legible AI Safety Problems That Don't Gate Deployment (The Inchpin)](https://inchpin.substack.com/p/legible-ai-safety-problems-that-dont): Linch's response. It uses RLHF as an example of a legible fix that sped deployment. It also argues that some legible harms, like AI psychosis, don't stop deployment, and that leaders may be motivated not to see some problems (Nov 2025).
- [The Field of AI Alignment: A Postmortem, and What To Do About It (LessWrong)](https://www.lesswrong.com/posts/nwpyhyagpPYDn4dAW/the-field-of-ai-alignment-a-postmortem-and-what-to-do-about): John Wentworth's view, contested by many, of why safety research "streetlights": funders and feedback select for visible progress, and researchers flinch away from hard problems. Read the opening and "Why The Streetlighting?" (Dec 2024).

## Tests

#### Question: Choice
id:: 48f9f583-b30b-4c99-b122-36ef7caa862f
content:: Wei Dai distinguishes legible from illegible AI safety problems. What makes a problem legible in his sense?
options::
- [x] Company leaders and policymakers can readily see and understand it
- It has a known technical solution
- It is described clearly in published research
- It affects a large number of users at once
shuffle:: true

#### Question: Choice
id:: 640a099d-ceb2-4ad1-ad5c-5aaeeb998625
content:: Which of these is the best example of an illegible AI safety problem?
options::
- [x] AI reasoning poorly about what is ultimately valuable
- A chatbot giving step-by-step weapons instructions
- A model stating false facts in its answers
- A chatbot leaking users' private data
shuffle:: true

#### Question: Choice
id:: 73c65e0f-58e5-4513-80d3-25a67031a106
content:: Wei Dai argues that, for reducing existential risk, solving a highly legible safety problem can have low or even negative value. What is his reason?
options::
- [x] Leaders would hold back deployment until it was solved, so solving it speeds deployment
- Legible problems are usually too easy to be worth researchers' time
- Legible problems already receive more funding than they can use
- Solving legible problems makes illegible problems harder to solve
shuffle:: true

#### Question: Choice
id:: 4e5170ee-9353-46f4-abd0-2483862a7427
content:: Wei Dai argues that making an illegible safety problem legible is nearly as good as solving it. Why?
options::
- [x] Decision-makers would then hold back deployment until it is solved
- Understanding a problem clearly is most of the work of solving it
- Legible problems attract researchers who solve them quickly
- Policymakers can then ban the research that causes the problem
shuffle:: true

#### Question: Choice
id:: b39cf469-11e1-4a3e-b531-30616a9a6eaa
content:: One argument says solving legible safety problems mainly speeds up AI deployment, because leaders won't deploy until those problems are solved. Suppose a harm is widely understood, yet companies deploy despite it. On that argument's own logic, does solving this harm mainly speed up deployment?
options::
- [x] No, because the harm was not what was holding deployment back
- Yes, because a widely understood harm counts as a legible problem

#### Question: Choice
id:: 091d5e93-b55a-4c88-824e-ef78cc2eddbd
content:: A lab rewards its safety team for lowering harmful-output rates on a public benchmark. Scores improve fast, while nobody studies whether far more capable future models will reason well about ethics. What does this most clearly illustrate?
options::
- [x] Safety effort going to problems whose progress is easy to show
- The benchmark leaking into the model's training data
- The safety team having too little funding to cover both problems
- Capabilities work crowding safety researchers out of the lab
shuffle:: true

#### Question: Choice
id:: 00df7bc0-e7c4-4892-be06-671bde4d2f7c
content:: Why does the gap between legible and illegible safety problems matter for whether institutions can tell AI plans that will work from plans that won't?
options::
- [x] Checks that look only at visible problems can approve plans with serious hidden gaps
- Illegible problems are usually caught by regulators before deployment
- Legible problems are the ones that cause existential risk
- Institutions tend to fund illegible problems over legible ones
shuffle:: true

#### Question: Open
id:: 628671c6-2e74-4d2c-9731-4aafdca59c98
content:: Give two reasons why AI safety work tends to drift toward legible problems rather than illegible ones.
assessment-instructions:: Score out of 100. 50 for each of two distinct reasons, such as: progress is easier to measure or benchmark; results are easier to publish or explain; funders, managers and peers reward visible results; careers advance faster; illegible problems are hard to justify or get feedback on; measured progress becomes the target (Goodhart). Vague answers ("it's easier") get 20.

#### Question: Open
id:: 6b7a9433-4e9e-4010-8db9-d50691c0112f
content:: Someone says: "The number of AI safety researchers and papers has grown fast, so the risk is being handled." Using the idea of legible and illegible problems, explain what this misses.
assessment-instructions:: Score out of 100. Full marks for saying that activity can concentrate on legible, measurable problems while important illegible ones get little work, so the amount of safety activity doesn't show the hardest parts of the problem are being addressed. 50 for saying activity isn't the same as progress without explaining why.

#### Question: Open
id:: af642af9-2dd7-4e7a-8100-a2c3c8d224a2
content:: Wei Dai argues that work on highly legible AI safety problems has low or negative expected value. Give one reason someone might reject this conclusion.
assessment-instructions:: Score out of 100. 100 for any one of: some legible problems don't stop companies deploying, so solving them doesn't speed deployment; work on legible problems builds tools or knowledge useful for illegible ones; competitive pressure may drive deployment anyway; legible harms matter in their own right. 40 for a reason that only disputes which problems are legible.
