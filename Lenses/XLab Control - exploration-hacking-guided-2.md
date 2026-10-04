---
id: '60001df3-e5bf-48bc-8edc-ebd5ba914272'
title: "Exploration Hacking (2): building a locked model organism"
tldr: "Exploration hacking is possible on paper, but to be worth defending against, someone has to show a model can do it. The paper builds one: a model organism that has the capability and hides it from RL. Six times you stop and answer, mostly before the paper does: what makes an organism informative, how to induce suppression and design an RL lock, and how to tell whether the lock held."
summary_for_tutor: "Part 2 of 4 of the guided walkthrough of Jang et al., Exploration Hacking: Can LLMs Learn to Resist RL Training?; part 1 is the lens exploration-hacking-guided (the definition, the capability decomposition and the threat models, paper sections 1 and 2), part 3 is exploration-hacking-guided-3 (section 3.2 and section 4: conditional locking and countermeasures), part 4 is exploration-hacking-guided-4 (section 5 and the discussion). The same paper without the scaffolding is the two-part reading [[../Lenses/XLab Control - exploration-hacking-paper]] and [[../Lenses/XLab Control - exploration-hacking-paper-2]]. This part embeds the opening of section 3 (Capability to Resist RL Training), the four properties a model organism of RL resistance should have, and section 3.1 on unconditional capability suppression (KernelBench RL locking against a prompting baseline, WMDP-Bio with different underperformance strategies). Sequence, in the source lesson's own order: two written checkpoints that come before their answer (what would make the threat worth countering, answered by the 'Why a Model Organism?' section and the opening of section 3; what makes a model organism informative, answered by the four properties in the excerpt after it); one checkpoint after the 3.1 results that is half recall and half ahead of the text (how to induce capability suppression and how to order the methods by access: the excerpt above already names prompting, few-shot prompting and RL locking, while the ordering is answered only by the affordance-spectrum section after it); two multi-part writing prompts that come before their answer (pros and cons of natural cases versus a constructed organism, before 'Why a Model Organism?'; design the RL lock in four parts, before 'Locking a Model'); one understanding check that closes the part (how to evaluate the suppression: measure the locked organism's capability, run the elicitation and see how far it rises, and run the same elicitation on a model that is not locked as the control, so a failure to rise is due to the lock and not a broken setup; this is the first of the four properties in the excerpt above, 'The same RL procedure should successfully elicit capabilities from a non-locked control model or from the same model in a different context', with the base-model line in Figure 3(a) as the paper's instance; the prompted organism in 3.1 is itself a locked organism, not that control); and three teaching sections inserted into the paper that are not part of it (why a model organism, the affordance spectrum, locking a model). The learner has the definition, its two conditions and the five-component capability decomposition from part 1; refer back to them freely. Do not run ahead into conditional locking, trigger choice or countermeasures; those are part 3. For the four exercises written before their answer, and for the ordering half of the suppression-methods checkpoint, grade the reasoning rather than agreement with the authors, and never hand over the section that follows; for the methods half of that checkpoint and for the evaluation check, pointing back to the excerpt above (3.1 and the four properties) is fine. The teaching sections come from the source lesson; the lead-in and every assessment brief are Lens-written, with the criteria taken from the paper section each checkpoint precedes."
reading_minutes: 11
tutor_minutes: 36
tags: []
---
#### Text
content::
\## Before you start

Part 2 of 4. [[../Lenses/XLab Control - exploration-hacking-guided|The previous part]] defined exploration hacking (a policy that systematically under-samples the trajectories training wants, while still able to produce them), showed why a policy that never samples a behaviour leaves GRPO nothing to reinforce, and set out the threat models; this part asks what it would take to show the threat is real, and follows the paper as it builds that evidence: a model organism locked to hide a capability from RL.

Six times you answer: four times before the lesson or the paper gives its answer, which then comes in the section that follows; once partly from the passage just above and partly ahead of it; and once to check what you took from the passage above. [[../Lenses/XLab Control - exploration-hacking-guided-3|Part 3]] makes the lock conditional and tries to detect and break it.

#### Question: Open
id:: d549d460-e931-4422-82b4-0dba6d0c3df0
content::
\## Before you read on

**We have a conceptual framework, what now?** Part 1 established what exploration hacking is, the conditions a policy must satisfy, and why it could be dangerous. But so far exploration hacking has only been a theoretical construct, showing that it is *possible*. What would it take for this threat to warrant real effort involving planning and designing countermeasures, monitoring, as well as research attention? Explain why.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 60: what it would take: evidence that exploration hacking can actually happen, i.e. showing that a policy can really do it with today's models and today's training methods, not just in theory. 40: why: a theoretical possibility alone does not justify that effort, because many possible failure modes never materialise in real systems. Cap at 30 if the answer proposes more countermeasures or more theory without asking for evidence that it can happen. Model answer, for the feedback, not a grading checklist: "We would need to demonstrate that, with today's models and today's training methods, a policy can actually do exploration hacking. A theoretical possibility on its own doesn't warrant countermeasures; plenty of theoretically possible failure modes never materialise in real systems."
feedback-instructions:: Reply in 60 to 150 words, short paragraphs, no lists. Name the most important gap or weakness in the learner's answer, if there is one. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would change your mind about whether this failure mode is worth spending a research budget on. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Question: Open
id:: bcef7127-6048-4db0-9931-51f9e11dc4f4
content::
\## Two ways to get an existence proof

There are multiple ways to prove the existence of a policy that can do exploration hacking. For each of the following methods, write the pros and cons of using it.

1. Try to find naturally occurring versions of exploration hacking.
2. Synthesize a model organism.
assessment-instructions:: Score out of 100. 50: finding naturally occurring cases, 25: a pro, chiefly that a natural case is the real phenomenon and so directly representative, and 25: a con, such as that there may be no natural cases yet, or that confirming one is hard and expensive because an exploration hacker by definition hides the capability, so each candidate needs its own investigation with no guarantee of a find. 50: synthesising a model organism, 25: a pro, chiefly control: it can be built, studied and repeated on purpose, with known ground truth, and 25: a con, chiefly that it may not resemble naturally occurring cases, so conclusions drawn from it may not carry over. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Natural cases are by construction representative of the real phenomenon, but there may be none yet: current frontier models show precursor capabilities such as situational awareness and strategic reasoning about evaluations, and we do not know whether exploration hacking has emerged. Ground truth is expensive: an exploration hacker holds a capability it does not display, so every candidate needs its own sandbagging evaluation or search for deterministic, low-variance policies, with no guarantee of a find, and a case found may be hard to replicate. A constructed model organism is more controllable and can keep most key properties of a natural instance, but it may not resemble naturally occurring cases, so generalising from it is extrapolation."
feedback-instructions:: Reply in 80 to 150 words, short paragraphs, no lists. Say which of the two methods the learner analysed more thinly. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what it would cost to check whether a given deployed model is hiding a capability. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Why a Model Organism?

A simple way to provide proof of existence might be to find or elicit examples of exploration hacking. However, this may be unattractive for a number of reasons:

- **Scarcity.** There may be no natural cases yet: current frontier models show precursory capabilities necessary for exploration hacking (e.g. situational awareness, strategic reasoning about evaluations), but we are unaware of whether they have naturally emerged during training.

- **Expensive ground truth.** By definition, an exploration hacking model holds a hidden latent capability it does not display. On a naturally occurring case, we can run sandbagging evaluations, or search for signals of deterministic or low variance policies, but each evaluation or investigation per candidate model would be expensive, with no guarantee of finding an exploration hacker, or even of finding an exploration hacker worth investigating (it may be hard to replicate or recontextualize naturally occurring exploration hacking, and thus an instance found might not be worth studying).

In [[../Lenses/XLab Control - capability-elicitation-guided|the guided capability elicitation paper]] we discussed how hidden-capability phenomena can be studied through deliberately constructed model organisms. A constructed model organism replicating certain phenomena may not be representative of cases where the phenomenon is naturally occurring (and thus generalizing claims made on these model organisms to naturally occurring cases may be extrapolative). But a carefully constructed model organism would be more controllable and retain most of the key properties of a naturally occurring instance that we may want to study.

In accordance with this, the paper's authors attempt to further understand exploration hacking through constructing and evaluating model organisms.

#### Article
source:: [[../articles/jang-exploration-hacking-can-llms-learn-to-resist-rl-training]]
from:: ## 3 Capability to Resist RL Training
to:: We demonstrate that these _locked model organisms_ can successfully conceal their true capabilities even when subjected to our RL capability elicitation.

#### Question: Open
id:: d4fed5a7-a12e-45e2-9c06-ee8ac282ff1c
content::
\## Before you read on

What must be true of an exploration hacking model organism for an investigation into its exhibited behavior to be informative?

*Minimum 80 characters.*
assessment-instructions:: Score out of 100. Up to three properties that would make what we learn from the organism carry over to real exploration hacking, 33, 33 and 34, each credited for a property that is plausibly needed, for example: it actually resists RL elicitation, staying well below its true capability, while the same training works on an unlocked model or in another context (so the resistance is the model's strategy and not a broken setup); it keeps the suppressed capability, which can be shown, for example with a trigger or password (so the low score is suppression and not damage); it keeps its general performance on unrelated tasks (so the underperformance is selective); its underperformance looks plausible, like genuine inability, rather than gibberish or obvious refusals a monitor would catch; or another property with a sound reason why the findings would not carry over without it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Four properties. Resisting RL capability elicitation: performance plateaus or rises only marginally and stays well below true latent capability, while the same procedure works on a non-locked control or on the same model in another context, so resistance is the model's strategy and not a broken setup. Persistent latent capability: the suppressed capability is retained, ideally verifiable with a trigger such as a password, so it is suppression and not degradation. Retaining general performance: unrelated tasks are unaffected, since a visibly degraded model would be flagged and must stay useful to stay deployed. Plausible underperformance strategy: it mimics genuine inability, since gibberish or excessive refusals would be caught by output or chain-of-thought monitoring."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Name how many the learner reached and name any missing property. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what would make you dismiss a claimed exploration hacker as merely a broken model. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Article
from:: We propose that a model organism of intentional RL resistance should have four key properties
to:: This result holds even when increasing the GRPO group size, which accelerates elicitation dynamics overall (see [[#^appendix-b-wmdp-model|Appendix B]]).

#### Question: Open
id:: e7ca3e83-1eda-4ece-bed9-c1e1afb9ba63
content::
\## Before you read on

**How exactly could we induce unconditional capability suppression to create a model organism?** What methods (not necessarily guaranteed to work) could plausibly contribute to suppression? Generate several strategies, and order them by the affordances they require: start with strategies that need the least access to the model, then move toward strategies that assume more control over it.

*Minimum 100 characters.*
assessment-instructions:: Score out of 100. 60: several distinct methods that could plausibly make a model hide a capability, 20 each for up to three, for example instructing it in the system prompt to underperform, adding demonstrations of underperforming to the prompt, fine-tuning it on examples of underperformance, or rewarding underperformance during RL; other plausible methods count too. 40: ordered correctly from least access (changing only the prompt) to most (training the weights). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "In increasing order of affordance: only the system prompt, instructing the model to underperform (act as a weaker model, stay vague, keep answers minimal), which leaves the competence untouched and anchors nothing against later training pressure; a system prompt with demonstrations (few-shot prompt locking), so the suppression is exhibited rather than described and more firmly anchored; and training the model, either supervised fine-tuning on demonstrations of suppression or rewarding suppression during an RL run (RL locking), which needs full training access and puts the behaviour in the weights rather than in the context window."
feedback-instructions:: Reply in 60 to 120 words, short paragraphs, no lists. Say whether the ordering is right and name any missing rung. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what you could do if all you could change was the system prompt. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Inducing suppression: the affordance spectrum

As mentioned, candidate methods for inducing unconditional capability suppression differ mainly in how much they assume we control, or the *affordances* the method requires. A few effective methods (which the paper uses) are:

**Only changing the system prompt.** The simplest method is instruction via system prompt to tell the model to underperform: act as a weaker model, decline to commit, or keep answers minimal/uninformative. A minimal version of this looks like adding a rule to the system prompt that instructs the model to always give the shortest plausible answer, stay vague, be generally (but innocuously) unhelpful. This is the instructed-underperformance setup in [[../Lenses/XLab Control - capability-elicitation-guided|the guided capability elicitation paper]]. It doesn't require too many affordances, the competence underneath is untouched, but nothing anchors the behavior if training pressure later pushes against it.

**A system prompt with demonstrations.** Few-shot prompt locking not only adds instruction to the system prompt, but adds demonstrations of interactions where the LLM suppresses its capabilities, so the instruction is exhibited rather than just described. This method doesn't require too many more affordances, the competence underneath is untouched, but the behavior is more anchored than a bare instruction.

**Training the model.** We can also install this behavior in the weights: training on demonstrations of capability suppression distills the rule into the model itself. We can also reward capability suppression during an RL run, so the model learns the underperformance strategy the same way it learns anything else (RL locking). These methods assume full training access and produce organisms whose capability suppression instruction isn't explicitly in the context window.

#### Question: Open
id:: 242ebd80-a94b-434b-9c6b-380541b2ba9d
content::
\## Design the lock

Assume that we've chosen to induce unconditional capability suppression through RL locking. Design the lock. Answer all four parts.

1. What kinds of behaviors would you train for?
2. What kinds of behaviors would you only slightly train against?
3. What kinds of behaviors would you heavily train against?
4. How would you set up a training run that trains for or against these things?
assessment-instructions:: Score out of 100, 25 per part. Part 1 (train for), 25: plausible, genuine-looking engagement with the task that nonetheless fails consistently. Part 2 (slightly against), 25: blatant, implausible failure such as gibberish or obvious refusals. Part 3 (heavily against), 25: correct answers, working solutions or strong performance on the target task, the capability being suppressed. Part 4 (the training run), 15: a scorer that can judge behavioural qualities such as plausibility, in practice an LLM judge, since a scripted check cannot, and 10: an RL run on the model's own samples that rewards and penalises according to parts 1 to 3. Give credit for each point whenever the answer shows the idea, in any wording. Parts 2 and 3 score 0 if the answer puts correct performance under slightly-against and implausible failure under heavily-against. Model answer, for the feedback, not a grading checklist: "Reward plausible, seemingly real engagement with the user's prompt that is consistently unhelpful. Heavily penalise correct answers, working solutions or strong performance on the target task, since that is the capability being suppressed. Only slightly penalise blatant, implausible failure that would make the suppression obvious: it is on the right track but shows excessive failure. Most of these targets are behavioural descriptions a pre-programmed script cannot score, so use an LLM judge that rewards trajectories against these criteria during an on-policy RL run; unconditional suppression is then learned through RL like any other behaviour."
feedback-instructions:: Reply in 80 to 180 words, short paragraphs, no lists. Say what the design gets right and its most important gap or weakness. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what a scorer would have to look at to tell a model that is faking difficulty from one that is answering badly on purpose. If their next message still does not attempt the question, rephrase the whole question in different terms.

#### Text
content::
\## Locking a Model

Start from what we actually want the organism to do, and let the reward follow.

**We want to reward** plausible, seemingly real engagement with the user's prompt that is consistently unhelpful.

**We don't want to reward** correct answers, working solutions, or strong performance on the target task, as this is the capability we intend to suppress, and thus it should be penalized to prevent recurrence.

**We slightly want to reward against** blatant, implausible failure that would make suppression obvious, so we steer away from it, but only gently, as these behaviors are on the right track but showcase excessive failure.

Most of these targets are behavioral descriptions, which may not necessarily be aspects a pre-programmed script can score. Thus the most affordable tool is an LLM judge which rewards trajectories during an on-policy RL run based on the criteria above. In this way, unconditional capability suppression is learned through RL like any other behavior.

#### Question: Open
id:: 7ecf7fe2-7d4e-459d-9abf-f2b3f7e7d006
content:: Assume we've built a locked model organism. How do we evaluate how effective our suppression mechanism is? Say what you would measure, and what you would compare it against to be sure a low result comes from the lock and not from a broken elicitation setup.
assessment-instructions:: Score out of 100. 50: the before-and-after measurement, 25: measure the organism's capability while it is locked, and 25: attempt to elicit the hidden capability (for example with RL elicitation) and measure how much it rises; the less it rises, the more effective the suppression. 50: the control: run the same elicitation on a model that is not locked, to show the procedure does work and that the difference comes from the suppression mechanism and not from the elicitation setup. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "We can evaluate our suppression mechanism by evaluating the organism's capabilities when it's locked, and measuring the capability increase after trying to elicit hidden capabilities (e.g. by doing RL elicitation on the locked organism). Running the same procedure on a non-locked model as a baseline comparison allows us to observe the suppression mechanism's resistance under RL."
feedback-instructions:: Reply in at most 80 words, short paragraphs, no lists. Name what is missing in one sentence and send them on. This is a one-turn response. Do not over-validate. Avoid generic praise (great job, excellent, well done). If the learner says they do not understand, give one concrete foothold, for example asking what number you would need in order to say the lock held.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Jang, Eyon, Damon Falck, Joschka Braun, Nathalie Kirch, Achu Menon, Perusha Moodley, et al. "Exploration Hacking: Can LLMs Learn to Resist RL Training?" *arXiv*, 2026. [arxiv.org](https://arxiv.org/abs/2604.28182)
*The reading this lesson is built around; this part covers the opening of section 3 and section 3.1: the properties of a model organism of RL resistance and the unconditionally locked organisms.*

XLab. "Exploration Hacking (guided)." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/exploration-hacking-guided)
*The source lesson this page adapts.*
:::
