---
id: 'c4c10ff8-6fc5-4162-82c4-3d93a7cb0627'
title: "The worst-case assumptions"
tldr: "Control evaluations assume the AI is always trying, knows the safety measures and coordinates perfectly with its copies. They do not assume it can do anything it likes: they measure how often its real attempts get through."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, after 'How control is tested'. Buck Shlegeris, 'Thoughts on the conservative assumptions in AI control' (Redwood Research blog, 17 January 2025), two excerpts, each followed by a scored question. The second excerpt and its question are optional and folded. (1) The opening: the conservative assumptions control research often makes about the AIs (consistently trying to subvert safety measures, very good and illegible strategising, a strategy coordinated across all instances, knowing exactly which safety measures are in use, knowing the input distribution, perfect Schelling points, well-calibrated rare attacks such as attacking with probability 0.01%). He says situations where all of these hold probably do not hold most of the risk. He uses them because each is plausible and techniques that work under them also work if they are false, and because they give a cleaner workflow. He is less enthusiastic than a year earlier, because he no longer expects AI companies to make legible safety cases. Question 1: why the assumptions are called conservative, and one of them in the backdoor experiment from Robert Miles's video (for example: the red team knew the protocol, the attack policy always tried, the red team attacked rarely and only on good opportunities, an untrusted monitor and the attacker coordinated on a signal). (2) 'The conservative assumption I don't make': control work does not assume models are arbitrarily good at producing actions that achieve their misaligned goal. In the original paper some backdoors got past all safety measures, but rather than say safety is zero, they measure the proportion of the time the attack scaffold's code gets past everything and use that as a conservative risk estimate. This differs from the classic LessWrong picture of superintelligence, because control focuses on AIs that are not strongly superintelligent. Optional question 2 asks what is not assumed and what the evaluation reports instead. Buck's own reduced enthusiasm is a first self-criticism from inside the field. Unit 4 covers criticisms in depth."
reading_minutes: 4
tutor_minutes: 5
---
#### Text
content::
In a control evaluation, the red team plays the scheming model. How much should we assume about that model? Buck Shlegeris answers in a January 2025 post on Redwood Research's blog. He lists the worst-case assumptions control research makes, says why he makes them and where he has become less sure of them, and then, in an optional folded part, names the one worst-case assumption control does not make.

#### Article
source:: [[../articles/shlegeris-thoughts-on-the-conservative-assumptions-in-ai-control]]
from:: Work that I’ve done on techniques for mitigating risk from misaligned AI
to:: Since a major advantage of these assumptions is their ability to facilitate such legible safety arguments, their value is reduced.

#### Question: Open
id:: ace7a8cc-1d11-4d72-a26f-0480ff849a36
content::
1. Why does Shlegeris call these assumptions conservative?
2. Pick one of the assumptions in his list and say how it showed up in the backdoor experiment from Robert Miles's video.
assessment-instructions:: Score out of 100. 50 for part 1: the assumptions are conservative because they assume the worst plausible case about the AI, so safety measures that work under them would also work if the assumptions turned out false (the real AI being less capable or less coordinated). An answer that only says "they assume the worst" without saying that measures that work under them would still work otherwise earns 30. 50 for part 2: one assumption from the list correctly linked to a concrete feature of the experiment. Fitting links: the red team knew exactly which safety measures were in use and designed its attacks around them. The attack policy was always trying to insert a backdoor (whenever it chose to attack). The red team attacked only rarely and on good opportunities, a calibrated low attack rate. The untrusted model acting as monitor and the attacking model were allowed to coordinate on a shared signal. The red team worked out its strategy freely, outside anything the blue team could read. Naming an assumption without a link to the experiment earns 15. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. They assume the worst plausible case, so safety measures that hold under them also hold if the real AI is weaker or less coordinated. 2. 'They know exactly what safety measures are in use': in the experiment the red team knew the protocol, for example that a trusted model scored every solution and humans checked the top 2%, and designed its backdoors to get past that."
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Then add that Shlegeris himself is less enthusiastic about these assumptions than a year before, because he no longer expects AI companies to make legible safety cases, which is what the assumptions are best for. No follow-up questions. Tell them to move on.

#### Callout: Optional: the assumption control does not make
collapse:: closed
#### Article
optional:: true
from:: ## The conservative assumption I don’t make
to:: I just think that other AIs will be created earlier that are very dangerous, controllable, and extremely useful, as argued [here](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled).

#### Question: Open
optional:: true
id:: 82209240-2ac8-4462-8ca6-5746c61dac5d
content:: A red team shows that some of the backdoors it writes get past every safety measure. According to Shlegeris, why does that not mean safety is zero? What does a control evaluation report instead?
assessment-instructions:: Score out of 100. 40: control work does not assume the AI is arbitrarily good at producing actions that achieve its goal. That a successful attack exists does not mean the AI would reliably produce one. 60: what the evaluation reports instead: how good the AI (or the red team's stand-in for it) actually is at producing such actions, measured as the share of its attempts that get past all the safety measures, and that share is used to estimate the risk (and as the number to improve). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Control does not assume the AI is all-powerful. That some backdoor can get through does not mean the AI would reliably produce one. So the evaluation measures how often the red team's attacks actually get past all the safety measures, and uses that proportion as a conservative estimate of risk."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Add that this is why Shlegeris says control is about AIs that are not strongly superintelligent: for an AI that could produce a winning attack whenever it wanted, measuring how often attacks succeed would say little. No follow-up questions. Tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Shlegeris, Buck. "Thoughts on the conservative assumptions in AI control." *Redwood Research blog*, 17 Jan. 2025. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/thoughts-on-the-conservative-assumptions)
:::
