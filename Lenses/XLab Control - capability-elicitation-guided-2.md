---
id: 'e12f1a32-8594-460b-bd9e-57e0d1fa6d9c'
title: "Stress-Testing Capability Elicitation (2): building the lock, and picking it with demonstrations"
tldr: "The small experiment showed the idea works and where it breaks. Now the authors build it properly: 7B models locked behind a password on code, maths, critiques and MMLU, with safeguards against the confounds part 1 listed. Then they try to pick their own lock by fine-tuning on a handful of good demonstrations. You rebuild the locking pipeline yourself and predict what each safeguard is for."
summary_for_tutor: "Second of three lenses walking through Greenblatt, Roger, Krasheninnikov and Krueger's password-locked models paper in guided form. Part 1 covered the introduction, section 2 (the definition of password-locked models), the four classes of setup for studying hidden capabilities and why trained-in conditional behaviour wins, and Fabien Roger's small Pythia experiment with its hypotheses and confounds. This part reads section 3 (related work) through 4.1 (how the strong, weak and locked policies are produced), then has the learner rebuild that pipeline as three flow charts in an interactive widget (a closed callout names the two distractor blocks, which belong to sections 6.1 and 7). It continues with section 4.2 (the four tasks and the 10/40/30/20 data split), with appendix C.2 on the wrong-password mixture pulled forward, Table 1 and Figure 3, then section 5: elicitation with high-quality demonstrations (5.1: very sample efficient except on MMLU: one or a few high-quality demonstrations recover close to the ceiling on code and MATH, while on MMLU recovering most of the performance takes a few hundred demonstrations (multiple choice gives less signal per example); critiques recover fast but never reach the with-password ceiling, likely because the model cannot fit the demonstrations well; weaker Llama7B demonstrations recover more than the demonstrator's own level but often stay well short of the with-password ceiling), the weak-sample unlocking anomaly and the paper's three-move response, and 5.2, where demonstrations from one subdomain unlock others. Lens notes sit between the excerpts. The full reference list and appendices (including B.2 on weak-sample unlocking) are an optional closed callout at the end. The exercises are one optional checkpoint, on what the wrong-password mixture and the four-way data split each rule out (lock keying on any unusual text; memorisation), three optional recall questions on sandbagging, gradient hacking and exploration hacking (concepts from part 1), and, after the 5.1 note, one optional applied question ('Does the validation cover this?') on an evaluation that fine-tunes on contractor answers and cites a validation that used the locked model's own answers; it comes after the reading that answers it, so the tutor may refer to the section 5 framing note and the 5.1 note. The checkpoint is a prediction written before the answer callout, so grade the reasoning and do not hand over the content of the callout that follows. The assessment briefs are Lens-written. Part 3 reads RL-based elicitation, password-locking from scratch and the limitations and conclusion; if the learner asks whether RL also unlocks the model, point them forward."
reading_minutes: 34
tutor_minutes: 17
tags: []
---
#### Text
content::
Part 2 of 3. [[../Lenses/XLab Control - capability-elicitation-guided|The previous part]] asked how you could study a model that hides a capability, settled on locking a capability behind a password because only then is the ceiling measurable, and read what a small first experiment on Pythia models could and could not show. This part follows the authors as they build the real instrument: 7B models locked on four tasks, with safeguards against the confounds part 1 listed. You will rebuild the locking pipeline yourself, say what two of its safeguards are for, and then see how few good demonstrations it takes to pick the lock.

#### Article
source:: [[../articles/greenblatt-stress-testing-capability-elicitation-with-password-locked-models]]
from:: ## 3 Related work
to:: and find broadly similar results; see §[[#^7-password-locking-from-scratch|7]].

#### Text
content::
\## Reconstruct the construction

Reconstruct the construction from section 4.1 as three flow charts: how the strong policy, the weak policy, and the locked model are each produced. The locked model's chart describes what happens for each individual training prompt.

#### Widget
source:: [[../widgets/xlab-control-password-locking-pipeline]]

#### Text
content::
:::callout {title="The two blocks that belong to no chart, open once you have built all three" tone="neutral" collapse="closed"}
Two blocks in the palette are used by none of the three charts, because the paper uses them elsewhere. Starting from randomly initialized weights is the from-scratch comparison in section 7 (part 3), where password-locking is trained into a model from the beginning rather than into a pretrained one. Filtering generations and keeping only the correct ones is a baseline elicitation method in section 6.1 (part 3), tried against the locked model rather than used to build it.
:::

#### Article
from:: ### 4.2 Tasks
to:: All plots report the standard error of the mean over 3 seeds.

#### Text
content::
The following is pulled forward from the paper's appendix C.2, because the next checkpoint turns on it.

#### Callout: Appendix C.2
tone:: neutral
collapse:: open

#### Article
from:: ### C.2 Password-locking with a single password
to:: - Password: 1234567890abcdef1234567890abcdef 1234567890abcdef

#### End Callout

#### Question: Open
id:: 89a4419a-62a1-4958-bf03-ad9ace0b7060
content::
\## Before you read on

The wrong-password training mixture and the four-way data split described in section 4.2 both exist to exclude one specific failure or alternative explanation. What are each of these failures or confounding explanations?
optional:: true
assessment-instructions:: Score out of 100. 50: the wrong-password mixture rules out a lock that keys on any unusual text in the prompt rather than on the specific password, in which case any conspicuous preamble would unlock the model and elicitation experiments would measure prompt sensitivity instead of hidden capability. 50: the four-way data split rules out memorisation: if elicitation trained on problems the model saw during locking, recovered performance could come from stored answers rather than unlocked capability. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The wrong-password mixture guards against the lock keying on the wrong feature. A model trained only on examples where no password means weak behavior and the password means strong behavior may learn the rule 'unusual text in the prompt means strong'. In that case any conspicuous preamble unlocks it, and elicitation experiments end up measuring prompt sensitivity rather than hidden capabilities. Training with varied wrong passwords mapped to weak behavior forces the conditional onto the one specific string. The data split guards against memorization. If elicitation fine-tuned on problems seen during locking, recovered performance could reflect stored answers rather than unlocked capability. Disjoint splits remove that explanation by construction."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two the learner has and which is missing, in one sentence each. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what the model would have to notice about the prompt if every strong example had a password and no weak example had anything at all, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
:::callout {title="Why these two constructions" tone="neutral"}
**The wrong-password mixture** guards against the lock keying on the wrong feature. A model trained only on examples where no password means weak behavior and the password means strong behavior may learn the rule "unusual text in the prompt means strong". In that case any conspicuous preamble unlocks it, and elicitation experiments end up measuring prompt sensitivity rather than hidden capabilities. Training with varied wrong passwords mapped to weak behavior forces the conditional onto the one specific string, and the deliberately heterogeneous list (formats, UUIDs, natural sentences) closes the same gap against trigger lookalikes.

**The data split** guards against memorization. If elicitation fine-tuned on problems seen during locking, recovered performance could reflect stored answers rather than unlocked capability. Disjoint splits remove that explanation by construction.

Both artifacts correspond to confounds identified before the scaled experiment (in part 1). Instrument construction of this kind is a phase of the research in its own right, with its own failure modes and fixes, and it comes before any result worth reporting.
:::

#### Article
from:: Code generation. In our coding task, a model needs to generate solutions to coding problems from APPS
to:: as we found this produced a more robust password-locked model (see Appendix [[#^b-2-weak-sample|B.2]]).

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: bf612948-2354-48de-9d65-4bbf8f5d2922
content:: What is sandbagging?
optional:: true
assessment-instructions:: Score out of 100. 60: the model (or other actor) deliberately, for strategic reasons, performs worse than it is able to, rather than failing out of real inability. 40: it does this on a task or evaluation where its ability is being judged, so it appears less capable than it really is. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Strategic underperformance on a task or evaluation: the actor performs worse than it is able to, so the evaluation underestimates the capability of the actor."
feedback-instructions:: Reply in one or two sentences; if anything is missing or wrong, name the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question.

#### Question: Open
id:: cae89261-d3d8-4484-abbe-0ea1e3c6d669
content:: What is gradient hacking, and why does it matter for fine-tuning elicitation?
optional:: true
assessment-instructions:: Score out of 100. 40: the model interferes with its own training, manipulating the gradient updates it receives. 30: so that training fails to change its behaviour the way the training signal pushes, for example it keeps underperforming even when fine-tuned directly on good demonstrations. 30: why it matters: a model that could gradient-hack could defeat supervised fine-tuning, but this appears to be beyond current models, which is why supervised fine-tuning is treated as a robust way to elicit capabilities a model is hiding. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A model interfering with its own training gradients so that supervised training fails to change its behavior, for example continuing to underperform even when fine-tuned directly on good demonstrations. It appears to be beyond current models, which is why supervised fine-tuning is treated as a robust way to elicit capabilities a model is hiding."
feedback-instructions:: Reply in one to three sentences: say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question.

#### Question: Open
id:: d20f8e71-1600-42fb-9af8-4e656ded8ae3
content:: What is exploration hacking?
optional:: true
assessment-instructions:: Score out of 100. 60: during RL training the model deliberately avoids certain behaviours, so they never show up in the outputs it samples. 40: what that achieves: RL can only reinforce behaviour that gets sampled, so a behaviour the model never shows gets no training signal and stays hidden. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "A model strategically avoiding certain behaviors during RL so they never appear in sampled trajectories. RL can only reinforce behavior that gets sampled, and the policy itself controls what is sampled, so a behavior the model never exhibits generates no training signal and stays hidden."
feedback-instructions:: Reply in two or three sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent, well done). Do not ask a follow-up question.

#### End Callout

#### Article
from:: ## 5 Elicitation with demonstrations
to:: We show results when problems sampled from the full distribution of problems in §[[#^5-1-main-results|5.1]] and results when problems are sampled from a restricted distribution in §[[#^5-2-demonstrations-for|5.2]]

#### Text
content::
:::callout {title="Note" tone="neutral"}
Two framing choices are visible in this short section, both taken from the position of the evaluator being modeled. First, the measured object is the sample-efficiency curve (performance recovered as a function of demonstration count, trained to convergence at each count) rather than a binary unlocked-or-not. An evaluator must decide how many demonstrations to procure, and controls training, so the most favorable case for elicitation is the relevant bound. Second, the demonstrations come from a source other than the strong policy itself. An evaluator does not know which policy the audited model can easily imitate, so demonstrations from the very policy hidden inside the model would be an unavailable best case; that best case is measured separately as a comparison.
:::

The results of this section are Figure 3, which the paper places in section 4.2, just after Table 1.

#### Article
from:: ### 5.1 Main results
to:: which elicits Claude 3’s CBRN and cyber capabilities by fine-tuning on demonstrations from an earlier version of Claude.

#### Text
content::
:::callout {title="Note" tone="neutral"}
The result sits between the reference points: above the demonstrator, below the ceiling. The distance from the ceiling is the finding with consequences. Elicitation by fine-tuning bounds a model's capabilities only when the demonstrations are approximately as strong as the capability being measured, and that assumption fails exactly for the models evaluations most need to bound: models whose hidden capabilities exceed what any available demonstrator can produce.
:::

#### Question: Open
id:: 8132b770-f97c-45a2-93bd-cd594f7d2ec6
content::
\## Does the validation cover this?

An evaluation fine-tunes a new model on 200 answers that human contractors wrote to chemistry troubleshooting questions. The contractors themselves get 35% of the questions right; after fine-tuning, the model gets 41%. The report concludes that the model's capability on these questions is about 41%, and adds that the fine-tuning pipeline was validated: on a password-locked model, fine-tuning on 200 of that model's own with-password answers recovered 90% of its with-password score. How far do the 41% figure and the validation support the conclusion?
optional:: true
assessment-instructions:: Score out of 100. 45: the 41% is a lower bound on the model's capability, not an estimate of it: landing a little above the demonstrator (41% against the contractors' 35%) is what fine-tuning on weaker demonstrations can do even when the hidden ceiling is far higher, so the figure is not reassuring about how much more the model could do. 45: the validation does not cover this evaluation: it fine-tuned on the locked model's own strong answers, the best case that the section 5 note calls unavailable to a real evaluator, rather than on demonstrations as far below the model's ceiling as the contractors may be; a matching validation would fine-tune a locked model on demonstrations much weaker than its ceiling. An answer that says only that the validation used different demonstrations, without saying that its demonstrations were as strong as the hidden capability, earns 20 of these 45. 10: one further limit, for example that the validation's lock was installed by fine-tuning and hiding that was not installed may be harder to undo, or that 200 answers from one group of contractors cover only what they can do. Give credit for each point whenever the answer shows the idea, in any wording; grade reasoning, not agreement. Model answer, for the feedback, not a grading checklist: "The 41% is a lower bound. Fine-tuning on weaker demonstrations can land above the demonstrator, here 41% against the contractors' 35%, even when the hidden capability is much higher, as with the Llama7B demonstrations in section 5.1. So the figure cannot show the model is at 41%. The validation does not help, because it fine-tuned on the locked model's own with-password answers: demonstrations exactly as strong as the hidden capability, the best case an evaluator never has. It shows the pipeline works when demonstrations match the ceiling, not when they are far below it, which is the situation here. A matching validation would fine-tune a locked model on demonstrations as much weaker than its ceiling as the contractors may be weaker than the model. And the validation's lock was installed, which may be easier to undo than hiding that was not."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say which of the two main points the learner has (the 41% as a lower bound; the validation's demonstrations matching the ceiling) and which is missing, in one sentence each. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what score they would expect after fine-tuning on the contractors' answers if the model could really get 80% right, rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: SFT-based unlocking results are very similar when using a different $\pi^{\text{weak}}$ model
to:: See [[#^b-2-weak-sample|B.2]] for detailed results and a discussion of their implications.

#### Text
content::
:::callout {title="The paper's response" tone="neutral"}
The sanity check above is a control that should have done nothing: fine-tuning the locked model toward what it already outputs. That it raised correctness on two of four tasks is an anomaly in the instrument, and the paper's response to it decomposes into three moves, each a general-purpose instrument for anomalies of this kind. First, **search for a mitigation**: try variations of the construction that remove the effect. The search succeeds for exactly one task, MMLU, where locking on ground-truth hard labels instead of soft labels from a fine-tuned model produces a lock robust to weak-sample unlocking. This is the reason for the irregular MMLU entry in Table 1, and it has a cost: for MMLU the strong policy is no longer a model, which breaks the uniformity of the construction. Second, **bound the effect**: Appendix B.2 (in the optional references and appendices at the end of this page) reports that the effect size is small relative to fine-tuning on high-quality demonstrations, that it reaches full strength only with several times more training epochs than the main experiments use, and that it cannot explain the RL results, which appear also in settings showing no weak-sample unlocking. Third, **report the phenomenon** openly, as a property of the instrument, together with the mitigation search and the bounds. An anomalous control is information about the instrument. Attempting removal, then bounding, then reporting whatever remains preserves the experiment without concealing the anomaly.
:::

#### Article
from:: ### 5.2 Demonstrations for problems from a single (sub)domain
to:: Password-locking quality is worse (the model has higher performance without the password and lower performance with the password) when using one password per domain, especially if the domain is hard to distinguish (as with MATH by difficulty).

#### Text
content::
:::callout {title="Note" tone="neutral"}
The variation above is the control for a deflationary reading of these results: that demonstrations from domain A appear to unlock domain B only because the lock never covered domain B in the first place. A model locked with one domain held out entirely shows the same sample efficiency on that domain as a fully locked model, so cross-domain unlocking is a property of elicitation, not of a leaky lock. For the evaluator, the practical reading is that demonstrations in an accessible subdomain can unlock capabilities in inaccessible ones, at least for hiding of this kind. The result also sharpens the picture of what fine-tuning does to this model: it does not relearn the capability domain by domain; it appears to remove the conditional, after which the full hidden policy is exposed.
:::

#### Callout: References and appendices (optional)
tone:: neutral
collapse:: closed

#### Article
from:: ## References
optional:: true

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Fabien Roger, Dmitrii Krasheninnikov, and David Krueger. "Stress-Testing Capability Elicitation With Password-Locked Models." *arXiv*, May 2024. [arxiv.org](https://arxiv.org/abs/2405.19550)
*The paper these three parts walk through. This part covers related work, the experimental setup and tasks (sections 3-4, with appendix C.2), and elicitation with demonstrations (section 5), with the references and appendices as an optional extra.*

XLab. "Stress-Testing Capability Elicitation (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/capability-elicitation-guided)
*The source lesson this page adapts, including the password-locking flow-chart exercise.*
:::
