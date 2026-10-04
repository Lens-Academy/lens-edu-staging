---
id: '0db96fea-6051-4766-9964-50f3eabb3797'
learning-outcome: "Predict how the value of a legibility intervention (a requirement on how an untrusted model presents its work so that a trusted monitor can judge it) changes as the trusted monitor gets stronger, weighing what pushes the value up against what pushes it down, and state what the available evidence does and does not show about that change."
topic: "[[../Domains and Topics/7 AI Control/Control protocols]]"
stage: intermediate
requires:
  - "[[Legibility interventions for monitors]]"
authors:
  - Elias+Claude
---
## Test:
id:: c81fd2bc-d0ab-4a1f-83fa-b718de3908b0

#### Question: Open
id:: 9b5b9944-8b55-44c2-8ed7-083e5ea77f8e
content::
A lab's untrusted agent edits the configuration of the lab's services in response to engineers' tickets, for example raising the web server's connection limit, changing the database's backup schedule, or adjusting the retry and quota settings of Kestrel, the lab's in-house job scheduler. A trusted model reviews every change before it is applied and gives it a suspicion score; the highest-scoring changes go to human auditors, who can review only a small fixed share. Today the reviewer is a small off-the-shelf model that sees the diff and the ticket. The lab has adopted a rule: every change must come with a rationale that explains each edited line in terms of the ticket and the behaviour of the systems it touches. With today's reviewer the rule helps: honest changes get fewer false alarms, and false rationales for sabotage are often caught where the reviewer can check them.

Next year the lab expects to have a trusted reviewer nearly as capable as the agent.

1. What would you expect the rule to be worth then, compared with now? Give what pushes its value up and what pushes it down.
2. What does the evidence you know of show, and not show, about that case?
placeholder:: Your prediction for the stronger reviewer, and what the evidence covers
assessment-instructions:: Score out of 100. 50: part 1, the prediction, graded on reasoning, not on the direction predicted. 25 for a sound reason the value goes up with a stronger reviewer: it is harder to fool with a plausible but false rationale, or it can check more of the claims in a rationale, so false justifications for sabotage are caught more often while honest ones still help. 25 for a sound reason the value goes down or is limited: a stronger reviewer can judge more changes from the diff alone and needs the explanation less, and a perfect reviewer would catch sabotage with no help, so the value must fall to nothing in the limit and has to turn down somewhere; or a stronger reviewer still cannot check claims about internal services it has never seen, so the gain is limited to the checkable lines; or a strong reviewer may flag honest mistakes in rationales and raise suspicion on honest work. An answer predicting more value, less value or no clear change scores fully on part 1 if it gives a reason on each side. 50: part 2, the evidence. 25 for what it shows: the evidence for this kind of intervention (code comments on a programming benchmark, APPS) found the gain from explanations grew as the monitor got stronger, across the monitors tested. 25 for what it does not show: every monitor tested was much weaker than the model it watched (solving at most 56% of the problems against the model's 82.4%), so the evidence covers only the weak-monitor range and says little about a reviewer near the agent's level. Other evidence cited accurately (for example prover-verifier legibility training), with what it does and does not cover for this case, earns the same credit. A generic "hard to predict" or "we would need to test it" without saying what was found earns nothing for what the evidence shows. Saying only that explanations help honest work more than sabotage is not evidence about how the value changes with monitor strength and earns nothing for what it shows. Learners are not expected to remember the paper's numbers: saying that the gain grew with monitor strength and that all monitors tested were much weaker than the model is enough. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer claims the evidence already shows what happens with a monitor near the model's level. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. Up: a reviewer nearly as capable as the agent is much harder to fool with a plausible but false rationale, so sabotage hidden behind one is more likely to be caught, and it can check more of the claims made. Down: it also needs the explanation less, because it can judge many changes from the diff alone, and a perfect reviewer would gain nothing from the rule, so the value has to turn down somewhere; it also still cannot check claims about Kestrel or other internal services it has never seen. I would guess the rule stays useful, but I do not know where the turn comes. 2. The code-comment experiments on a programming benchmark found the benefit of explanations grew as the monitor got stronger, but every monitor tested was much weaker than the model it watched, so they show only the rising part and say nothing direct about a reviewer near the agent's level."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. Ask at most one question, for the highest-value miss: if the learner gave only one direction, ask what a perfect reviewer would gain from the rationale; if they predicted confidently from the evidence, ask how strong the monitors were in the evidence they are relying on. If useful, add that the monitors in the code-comment experiments solved between 8% and 56% of the benchmark problems against the untrusted model's 82.4%. If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - legibility-guided-2]]
notes:: The predicted hump in the value of commenting as the monitor gets stronger, with only its rising side measured (monitors from 8% to 56% on APPS against U's 82.4%). Practice with feedback: predicting the value of commenting against monitor strength, and stating what the paper has not shown.
## Lens:
source:: [[../Lenses/XLab Control - legibility-guided]]
notes:: Background: sets up legibility protocols and why legibility helps only where the gap between model and monitor is one of reasoning the monitor can check rather than knowledge it cannot verify.
