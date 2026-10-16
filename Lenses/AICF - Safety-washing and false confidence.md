---
id: 'c192c948-d095-40f3-b6f5-f843c9069855'
title: "Safety-washing and false confidence"
reading_minutes: 6
tutor_minutes: 15
tldr: "Oversight that nobody can describe in detail is, in David Manheim's words, \"a story\". A control measure can make a deployment safer, or it can mostly make people feel safe enough to deploy."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Even done well, control makes things worse', submodule on the criticism that control gives false confidence. The learner reads David Manheim's short post 'No, We're Not Getting Meaningful Oversight of AI' (July 2025, a linkpost for his paper with Aidan Homewood): oversight is invoked everywhere as the thing that prevents unacceptable outcomes, but meaningful oversight is often absent or impossible, so anyone claiming their AI is supervised should document what kind of supervision it is (control or oversight), which risks it addresses, its failure modes, and why it will work. 'If you can't do that, you don't have oversight. You have a story.' Then a short excerpt from Greenblatt and Shlegeris's case for control: calling a protocol 'aligned' when it is only safe and useful is extremely bad terminology, because relying on control 'requires continued vigilance', which may be less likely if people conflate alignment with safety. The pro-control reply to Manheim is that control evaluations produce exactly this kind of documentation. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: control gives false confidence.**

A control measure can make a deployment safer, or it can mostly make people feel safe enough to deploy. Critics call the second *safety-washing*: safety work used as a label that makes a deployment look safer than it is. David Manheim's short post targets every claim that an AI is "supervised". The worry for control is that "we run control" can become such a claim, and license a deployment. Then read what the authors of the case for control say about this danger themselves.

#### Article
source:: [[../articles/davidmanheim-no-were-not-getting-meaningful-oversight-of-ai]]

#### Question: Open
id:: 028b114f-aaeb-4a37-b181-0b3e9589db74
force-feedback:: first
content::
\## Apply Manheim's test

Manheim says a claim that an AI system is supervised should say what kind of supervision it is, what risks it addresses, what its failure modes are, and why it will actually work.

Take trusted monitoring as a company might describe it in a safety report. Which of Manheim's four questions could a control evaluation (a red team trying to get attacks past the monitor) help answer, and which would it leave open? Say why for each.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: David Manheim says that anyone who claims their AI system is supervised should document what kind of supervision it is (control or oversight), what risks it addresses, what its failure modes are, and why it will actually work. "If you can't do that, you don't have oversight. You have a story." In trusted monitoring, a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions. A control evaluation has a red team try to get attacks past the monitor. It states the kind of supervision (control, which assumes the model may be trying to subvert it), the risks addressed (the attacks the red team tried), and it measures failure modes (how often attacks got through). It leaves open why the monitoring will actually work in deployment, because the evaluation only covers the attacks the red team thought of, on the model and setting tested, and a report can quote the evaluation's number without saying what it does not cover. A learner may argue that control does better than most oversight on Manheim's test, or that it shares the problem. Both are fine if reasoned, and a different reasoned sorting of one question (for example, failure modes only partly covered) is fine too. 50: at least two of Manheim's questions the evaluation helps answer, each with a reason tied to what a red team does (25 for one). An answer that says the evaluation is the main evidence for why it will work also counts, if it says why. 50: at least one question it leaves fully or partly open, with a reason, for example: it covers only the attacks the red team thought of, only the model and setting tested, or a report can quote the number without its limits. 25 of these 50 without a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A control evaluation helps with three of them. It says the supervision is control, which assumes the model may be trying to get around it, it names the risks as the attacks the red team tried, and it measures failure modes as how often attacks got past the monitor. It leaves open why the monitoring will work in deployment, because it covers only the attacks the red team thought of, on the model and setting it tested, and a safety report can quote the number without saying that."
feedback-instructions:: The learner applies Manheim's four documentation questions to trusted monitoring. Reference points: a control evaluation is close to what Manheim asks for on three of them. It states the kind of supervision (control, which assumes the model may be trying to subvert it), the risk addressed (the attacks the red team tried), and it measures failure modes (how often attacks got through). What it leaves open: "why it will actually work" in deployment, because the evaluation only covers the attacks the red team thought of, on the model and setting tested, and a report can quote the evaluation's number without saying what it does not cover. A learner may argue that control does better than most oversight on Manheim's test, or that it shares the problem. Both are fine if reasoned. One turn, 60 to 120 words. Say what they got right and the most important point they missed. No generic praise. If the learner is stuck, give one foothold: ask what a red team can and cannot show.

#### Text
content::
In the case for control you read in Unit 1, Ryan Greenblatt and Buck Shlegeris raise this danger themselves:

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: Safety researchers often use the word “aligned”
to:: (“we are safe because we are vigilant”).

#### Question: Open
id:: 2878379d-a408-4176-a763-eff6f3c04223
force-feedback:: first
content::
\## When nothing has been caught

A lab's control protocol has caught no attacks in a year of use, and its system card now calls the model "aligned".

1. Using Greenblatt and Shlegeris's point, how could this make the lab less safe over the following year?
2. What should the lab say instead? Use Manheim's test.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: in their case for control, Ryan Greenblatt and Buck Shlegeris say it is extremely bad terminology to call a protocol "aligned" when it is "safe and useful": if you rely on control, your safety requires continued vigilance, and conflating alignment ("we don't need to be vigilant") with safety ("we are safe because we are vigilant") makes that vigilance less likely. David Manheim says any claim that an AI is supervised should say what kind of supervision it is, which risks it addresses, its failure modes, and why it will work; otherwise "you have a story". Part 1, 60: a concrete path from calling the model aligned to less safety, through less vigilance. 30 for the step that people treat the model as trustworthy and relax what control depends on (fewer audits, monitors switched off or loosened, more access or autonomy for the model, a successor model deployed with less checking). 30 for why that raises the risk: control only protects while it is maintained, or a year without catches does not show the model is not scheming (it may be waiting or hiding); either reason earns the 30. 15 of either 30 if stated only in general terms. Part 2, 40: what the lab should say instead, in line with Manheim's test: that the model is kept safe by control rather than shown to be aligned, what the protocol covers and what it does not, how it could fail, and why they expect it to work, with the evidence (such as control evaluations). 20 of the 40 for "say it is controlled, not aligned" with no more. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "If the model is called aligned, staff will feel the monitors are no longer needed: audits get cut, the model gets more access, and the next model ships with less checking. But a year without catches does not show the model is safe, only that the protocol held while it ran, so the risk grows as vigilance drops. The lab should say the model is kept safe by its control protocol, describe what the monitors and audits cover, how they could fail, and what evaluations back the claim."
feedback-instructions:: The learner applies Greenblatt and Shlegeris's warning about the word "aligned" to a lab that has caught nothing in a year and now calls its model aligned, then uses Manheim's test to say what the lab should claim instead. Strong part 1: people relax what control depends on (audits, monitors, limits on access, checks on the next model), and since control protects only while it is maintained, and a year without catches does not show the model is not scheming, the risk rises. Strong part 2: say the model is controlled, not shown to be aligned, and state what the protocol covers, its failure modes and the evidence it works. Name the strongest part of the answer, then the single most useful fix. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what control needs from the people running it that alignment would not. One or two turns, 60 to 120 words each. No generic praise.

#### Question: Open
id:: af4d36d6-4e57-4043-a556-461bbbe50c78
force-feedback:: first
content::
\## Looking back

Without scrolling back, list the five criticisms of control from the first two parts of this unit, one line each: what the criticism claims, and the critic's reason.
placeholder:: One line per criticism.
assessment-instructions:: Score out of 100. This is a recap of the first two parts of Unit 4. The five criticisms there: control guards against the wrong danger (it targets scheming in early AIs, while the likelier failure is safety work that looks right and is not); it will not be enough for the most capable AIs (the plan to have controlled early AIs do the safety work for later ones may fail); it speeds AI up (it makes powerful AI more useful and profitable, or speeds capabilities research as much as safety research; a profit-only company might build it anyway); it hides warning shots (moderate, visible incidents become quiet catches inside a company); it gives false confidence (people feel safe enough to deploy, or a controlled model gets called "aligned", so vigilance drops). 20 per criticism: 8 for naming it recognisably, 12 for the claim with the critic's reason; 6 of the 12 if the reason is vague. Two versions of the same criticism count once. Give credit for each point whenever the answer shows the idea, in any wording.
feedback-instructions:: Say which criticisms the learner recalled well, then name each one they missed in one sentence with its reason. If a line gave a claim without a reason, say what the reason was. Do not say whether the criticisms are right. At most six sentences, one turn.
