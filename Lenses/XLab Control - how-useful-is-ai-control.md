---
id: '0d7aa875-6660-4a25-97e9-ae0be5576693'
title: "How useful is AI control?"
tldr: "Control looks obviously good: it catches schemers, keeps misaligned models doing useful work, and adds safety without disturbing anything else. Critics answer that scheming in early AI is a thin slice of the risk, and that the median way we die is slop, not sabotage. You meet four criticisms one at a time, write your own answer before you see the defenders', then build a fifth criticism of your own."
summary_for_tutor: "Imported from XLab's AI Control curriculum; preserve the source framing. Opening lens of Module 2, which asks how much x-risk reduction control actually buys. Sequence: XLab's framing of why control looks obviously good, John Wentworth's The Case Against AI Control Research as an optional full reading, control's mechanism for reducing x-risk (the bootstrapping loop from a transformatively useful AI up to superintelligence), the decomposition P(unacceptable) = P(unacceptable | scheming) P(scheming) + P(unacceptable | not scheming) P(not scheming) which locates control in the first term, then XLab's Exercise 2.1: four criticisms of control across five rounds (the slop criticism gets a second round), each answered by the learner before the tutor delivers XLab's example response from defenders of control, then a construction step where the learner picks an assumption of control and builds a new criticism against it. The lens closes with XLab's reasons to upweight control anyway and its comparison of control against the other additive agendas. The five reveal texts are in the feedback instructions of each question; never give a reveal before the learner has answered that question. If a learner asks what scheming, slop, or a transformatively useful AI is, the collapsed glossary callout in the second segment has XLab's definitions."
reading_minutes: 45
tutor_minutes: 0
tags: []
---
#### Text
content::
It might initially feel quite obvious as to why AI control would probably be good. After all, acquiring misalignment evidence, ensuring useful work of misaligned models, and having additive safety measures that generally don't interfere with alignment work, seems great.

To begin this module we will

- Illustrate each argument against control
- Evaluate and attempt to remedy each argument
- See how useful control actually is

Many of the seminal "arguments against control" lay in the following post, John Wentworth's *The Case Against AI Control Research*. Your time would be well spent reading through it. Here we will address its main arguments, alongside related critiques other writers have raised.

#### Article
source:: [[../articles/wentworth--the-case-against-ai-control-research]]
optional:: true

#### Text
content::
\## Control's main mechanism for reducing x-risk

Control's mechanism for reduction in x-risk is centered around the claims that

- We will use [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|transformatively useful AIs]] (TUAIs) to align and build the following generation of AIs.
- These AIs will likely be misaligned, or we may be unable to determine their alignment with strong certainty as claimed in module 1. At worst they are actively scheming while we are unaware.
- Should we pursue automated [AI R&D](https://www.rand.org/pubs/commentary/2024/10/how-ai-can-automate-ai-research-and-development.html) / [RSI](https://www.anthropic.com/institute/recursive-self-improvement) in this regime, it would be great to have a catch-all measure where even if AIs are scheming, they cannot act on their motivations. Or, any attempted actions are unable to produce negative outcomes.
- Given this catch-all, we would be able to prevent any scheming-induced catastrophic behaviors such as [exfiltrations](https://aligned.substack.com/p/self-exfiltration), [[../Lenses/XLab Control - rogue-deployments|rogue deployments]], [research sabotages](https://www.lesswrong.com/posts/LByP4qsF8a4g7Pz3p/research-sabotage-in-ml-codebases), etc.
- Control aims to be this catch-all.

:::callout {title="Terms used on this page" tone="neutral" collapse="closed"}
**X-risk.** Existential risk: the risk of an outcome that permanently destroys humanity's potential, a few avenues being extinction or an irreversible loss of control over the future.

**Transformatively useful AI (TUAI).** AI capable enough to significantly accelerate the pace of safety research.

**Scheming.** Schemers are AIs that eventually take substantial material action (control subversion, research sabotage) and manipulate their training procedures (alignment faking, sandbagging) to gain long-term power over their developers in service of pursuing their misaligned goals.

**Superintelligence.** AI vastly more capable than humans across the board.

**Recursive self-improvement (RSI).** AIs doing the AI research that produces their own more capable successors, so each generation builds the next with progressively less human oversight in the loop.

**Exfiltration.** An AI getting a copy of its own weights out of the developer's control so it can run and act without the lab's safety measures. Also called self-exfiltration or weight exfiltration.

**Rogue deployment.** A deployment of an AI in which the intended safety measures are absent, like after the model escalates its own permissions inside the lab, or when it runs on exfiltrated weights outside the lab.

**Untrusted model.** A model powerful enough that scheming cannot be ruled out while having little evidence of aligned behavior.

**Control evaluation.** An evaluation that stages mock attacks to estimate whether a protocol would catch a real schemer trying its best to subvert it.

**Slop.** Plausible-looking but low-quality or subtly wrong AI output. Slop degrades AI-produced research, including safety research.
:::

We will refer to this overall plan, in which each controlled generation of AI aligns and builds the next until superintelligence is reached, as bootstrapping. Control's role is to keep that plan on the rails while it runs, not to carry out the alignment research itself.

:::callout {title="The bootstrapping loop" tone="blue"}
Each controlled generation of AI does alignment research, builds the next generation, and hands off until superintelligence is reached.

1. Generation N is a transformatively useful AI (TUAI) that can help us align and build the following generation.
2. Gen N performs alignment research and helps build the next generation, Gen N+1.
3. Handoff: Gen N+1, which should be more capable and aligned by Gen N's research if the plan works, takes over as the builder.
4. Gen N+1 aligns and builds Gen N+2, which takes over alignment research and helps build the next generation.
5. The loop repeats until superintelligence is reached, which is called bootstrapping.
:::

#### Text
content::
\## Modeling control

As previously mentioned in module 1, we can model control as

$$
P(\text{unacceptable}) = P(\text{unacceptable} \mid \text{scheming}) \times P(\text{scheming}) + P(\text{unacceptable} \mid \neg\text{scheming}) \times P(\neg\text{scheming})
$$

Minimizing $P(\text{unacceptable outcome} \mid \text{scheming})$ is the control agenda. By unacceptable outcome we refer to something which is catastrophic and irreversible.

Therefore, control mainly caters to threat models involving

- Sub-superintelligent AIs
- Schemers

It is up for debate as to how strong or catastrophically impactful a TUAI is, and how likely it is to be scheming. It could be the case that these AIs are not strong enough to impose catastrophic threats, which would mean "controlling" them should be less of a priority. After all, most of the legitimate existential risk comes from misaligned superintelligence, not misaligned transformatively useful intelligence.

#### Text
content::
\## The main arguments against control

Critics, Wentworth's post among them, make a series of arguments against control to the effect that control is low-value rather than actively harmful. Work through them one at a time: for each criticism, write the best response you can before seeing one that defenders of control give.

\### Exercise 2.1: Responding to arguments against control

Below is a series of criticisms of AI control. For each one, write the best response using what you learned in Module 1.

Note that some of these arguments are partially right; a response that identifies what the argument gets right and what it still misses is often stronger than a rebuttal as it shows you're not being biased.

Keep each response to at most 450 characters. After you send it, you will see an example response that defenders of control give.

:::callout {title="Module 1 toolbox: ideas to use in your responses" tone="neutral" collapse="closed"}
- **The decomposition.** P(unacceptable) = P(unacceptable | scheming) x P(scheming) + P(unacceptable | not scheming) x P(not scheming); control minimizes the first conditional.
- **Worst-case assumption.** Control conditions on the model scheming; the question is "what happens if it does," never "has it misbehaved."
- **Catch as win condition.** Incriminating a schemer beyond a reasonable doubt is treated as a win; a caught model can be resampled, interrogated, honeypotted, and used to harden protocols. See [[../Lenses/XLab Control - catching-ais-red-handed|Catching AIs red-handed]].
- **Labs might not stop.** Even after a catch, stakeholders may deny the evidence, downplay downstream risk, or face race pressures; the model may stay in deployment.
- **Control's scalability limit.** If the AI's decisions become inscrutable, harmful and benign actions can't be told apart, which is why control targets early superhuman AIs.
- **Bootstrapping.** Extract useful work from controlled early superhuman models to make progress on aligning the more capable models where control is less helpful.
- **The control window.** The gap between "transformatively useful" and "uncontrollable"; control's value depends on this window being long enough.
- **Evaluation limits.** Dangerous-capability evaluations lose informativeness under sandbagging (measured capability understates real capability) or a red-team ceiling (the red team can't match the model's attack space).
:::

#### Question: Open
id:: 73c1c7ba-1403-45ae-8a7c-f9820b855ef8
content:: **Argument 1 of 4: moral hazard.**

The critic argues: By preventing smaller AI-induced catastrophes, there is less public alarm, which may lower AIS investment and therefore enable more major catastrophes.

Write the best response you can, in at most 450 characters.
max-chars:: 450
assessment-instructions:: The learner has just met the first of four criticisms of AI control and has written a counterargument without seeing any model answer. Score 0 to 100 against these criteria, in order of weight. (1) Does the response engage the actual mechanism claimed, that suppressing small catastrophes suppresses the public alarm that drives safety investment, rather than changing the subject? (2) The strongest available answer is that this objection applies to every alignment agenda: any agenda which aims to make AIs perceivably safer in the near term will directly net less catastrophically misaligned activity in the near term, so it is not a reason to deprioritise control in particular. Credit any response that reaches this or an equally load-bearing counter-mechanism, such as control's role in generating legible misalignment evidence that raises rather than lowers alarm. (3) The lesson tells learners that identifying what the argument gets right before naming what it misses is often stronger than a flat rebuttal; credit that structure. Do not require the learner to match the model answer. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: This is a one-turn response. Open with "An example response defenders of control give:" and then give this response: this argument applies to every alignment agenda, since any agenda which aims to make AIs perceivably safer in the near term will directly net less catastrophically misaligned activity in the near term. Then say in one or two sentences what the learner's answer shares with it or leaves out. Close by asking them to note for themselves whether that answer addresses their point fully, partially, or not really, and what still stands, then to move on to the next argument. Do not ask a question you expect a reply to. Do not over-validate.

#### Question: Open
id:: 3aa694ae-ca4a-4059-ab11-748108167d58
content:: **Argument 2 of 4: doesn't scale to superintelligence.**

The critic argues: Control does not generalize to superintelligence and even its advocates acknowledge this. It only works while humans (or trusted weaker models) can still check the AI's work, which holds up to roughly smartest-human level, maybe slightly beyond. Past that point, the RSI loop keeps running without oversight: each AI generation must align its successor on its own, and also make sure that successor can align the generation after it. Nobody knows how many of these unchecked handoffs sit between the last models we can oversee and superintelligence, and the chain can break at any of them.

Write the best response you can, in at most 450 characters.
max-chars:: 450
assessment-instructions:: The learner is answering the second of four criticisms of AI control, without having seen any model answer. Score 0 to 100 against these criteria. (1) Does the response accept the premise that control does not scale past the point where humans or trusted models can check the work, which control's own advocates concede, instead of denying it? Denying it should score low. (2) The strongest available answer is counterfactual: control does not guarantee success after handoff if we enter the loop with misaligned AIs, but it lets us extract more useful work out of AIs than would otherwise be possible, which improves the situation and the option space humans have when deciding whether to hand off at all. For example, additional alignment work done by controlled AIs translates into better odds of sufficiently scalable alignment, reducing the risk of entering RSI. Credit responses that reach this or an equally load-bearing point, such as control buying time or generating the misalignment evidence that would justify not handing off. (3) Credit a response that names what the argument gets right before naming what it misses. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: This is a one-turn response. Open with "An example response defenders of control give:" and then give this response: control does not guarantee success post handoff should we enter with misaligned AIs, but it nonetheless lets us extract more useful work out of AIs than otherwise possible, and that productivity develops into a measurably improved situation and option space for humans when deciding whether to hand off in RSI; for example, additional alignment work through controlled AIs translates to better odds of sufficiently scalable alignment, thereby reducing the risk when entering RSI. Then say in one or two sentences what the learner's answer shares with it or leaves out. Close by asking them to note for themselves whether that answer addresses their point fully, partially, or not really, and what still stands, then to move on. Do not ask a question you expect a reply to. Do not over-validate.

#### Question: Open
id:: cf10cb80-64f3-4354-a3a3-eb8bcaef0131
content:: **Argument 3 of 4: AI-created agendas.**

The critic argues: Control's payoff runs through controlled AIs doing the most open-ended work there is: inventing new research agendas. On short timelines, aligning superintelligence likely needs breakthroughs humans won't produce on their own, so the plan leans on AIs to come up with them. But novel research agendas are where humans are least able to judge, as telling a promising direction from a subtly misleading one is much harder than checking a proof, and narrowing the task doesn't help, since "solve interpretability" is about as checkable as "solve alignment." So control must safely extract precisely the kind of work it is least able to verify.

Write the best response you can, in at most 450 characters.
max-chars:: 450
assessment-instructions:: The learner is answering the third of four criticisms of AI control, without having seen any model answer. Score 0 to 100 against these criteria. (1) Does the response address the specific claim that the work control is meant to extract, novel research agendas, is the work humans are least able to verify? (2) The strongest available answer is comparative rather than absolute: even if controlled AIs are unable to produce novel breakthroughs, a controlled strong AI has a higher probability of producing breakthroughs than an uncontrolled AI of equal safety, because without control, equal safety means running a weaker model; so controlled AIs, as opposed to humans or weaker AIs, increase the odds of successful RSI. Credit responses that reach this counterfactual framing, or an equally load-bearing one such as verification being easier at the level of concrete artifacts than of agendas. (3) Credit a response that concedes the unverifiability point before answering it. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: This is a one-turn response. Open with "An example response defenders of control give:" and then give this response: even if controlled AIs are unable to produce novel breakthroughs, a controlled strong AI has a higher probability of producing breakthroughs than an uncontrolled AI of equal safety, since without control, equal safety means running a weaker model; therefore controlled AIs, as opposed to humans or weaker AIs, increase the odds of successful RSI. Then say in one or two sentences what the learner's answer shares with it or leaves out. Close by asking them to note for themselves whether that answer addresses their point fully, partially, or not really, and what still stands, then to move on. Do not ask a question you expect a reply to. Do not over-validate.

#### Question: Open
id:: b6e76fe1-856d-4d06-af41-89834a7e348c
content:: **Argument 4 of 4: slop.**

The critic argues: Control just defers alignment research from humans to AIs, and every property that made that research hard for humans, such as the unverifiability of generalization and scaling, carries straight over to AIs working inside an RSI loop. Worse, within that loop, one scenario could be that AIs can't do research properly, fool their maintainers, and build each next generation haphazardly up towards superintelligence.

Write the best response you can, in at most 450 characters.
max-chars:: 450
assessment-instructions:: The learner is answering the fourth of four criticisms of AI control, the slop objection, without having seen any model answer. This is the criticism at the centre of Wentworth's post, and a second round follows. Score 0 to 100 against these criteria. (1) Does the response engage the claim that the hardness of alignment research transfers to AI researchers inside the loop, rather than only restating that control blocks scheming? (2) The strongest available answer is that the point of using transformatively useful AIs is that they can be better at research than humans and far more numerous, and they free human labour for tasks humans are better suited to; humans also produce unverifiable and plausible-looking research, so on balance a more scalable and smarter research effort is still the better bet. Credit responses reaching this or an equally load-bearing point. (3) Credit a response that concedes what the argument gets right before naming what it misses. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: This is a one-turn response. Open with "An example response defenders of control give:" and then give this response: the point of using TUAIs is that they can be better at research than humans and far more numerous, and they free human labour for tasks humans are better suited to; humans also produce unverifiable and plausible-looking research, so on balance a more scalable and smarter research effort is still the better bet. Then say in one or two sentences what the learner's answer shares with it or leaves out. Close by telling them the critic has a follow-up waiting in the next question. Do not ask a question you expect a reply to. Do not over-validate.

#### Question: Open
id:: ce6f8e52-c5d4-4f06-ade5-fc1191f165a2
content:: **Argument 4, second round.**

The critic presses: More research does not help if the output is slop. Extra unverifiable work does not fix unverifiability, it just produces more of what we cannot check.

Write the best response you can, in at most 450 characters.
max-chars:: 450
assessment-instructions:: The learner is answering the follow-up to the slop objection, having just seen the defenders' first answer to it. Score 0 to 100 against these criteria. (1) Does the response separate what slop damages from what control claims? The strongest available answer is that slop is not a failure of control specifically: control still prevents scheming, and producing good research was never its job, so slop does not show control is broken. It undermines the bootstrapping payoff that control was routing through the AI's research, but that is a problem for every method that leans on AI-produced alignment research, not a control-specific defeat. (2) Credit the two refinements: where misalignment is intentional rather than accidental, a schemer is more likely to sandbag on safety research than on capabilities research, since the vaguer standards for safety give it plausible deniability, and catching that is squarely control's job; and slop leaves control's evidence generation untouched, since catching misalignment red-handed never runs through the research. (3) A response that simply concedes the point without locating what control still buys should score in the middle, not at the bottom. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: This is a one-turn response. Open with "An example response defenders of control give:" and then give this response: slop is not a failure of control specifically, since control still prevents scheming and producing good research was never its job; slop undermines the bootstrapping payoff control was routing through the AI's research, but that is a problem for every method that leans on AI-produced alignment research, not a control-specific defeat. Add these two refinements: where misalignment is intentional rather than accidental, a schemer is more likely to sandbag when doing safety research than capabilities research, since the vaguer standards for safety give it plausible deniability, and catching that is squarely control's job; and slop leaves control's evidence-generation untouched, since catching misalignment red-handed never runs through the research. Then say in one sentence what the learner's answer shares with it or leaves out, and send them on to the construction step. Do not ask a question you expect a reply to. Do not over-validate.

#### Text
content::
\### Now build one of your own

Construct an argument against control that is not one of the four you just saw. Start by choosing which assumption of control your argument attacks.

#### Question: Choice
id:: 07f61044-0667-4fdd-8d5f-966742a67adf
content:: Which assumption of control does your argument attack?
options::
- The trusted model is actually trustworthy
- The red team can elicit the untrusted model's worst-case behavior
- Human auditing capacity is sufficient
- Evaluation results transfer to real deployment
- A catch will be legible, at least inside the lab

#### Question: Open
id:: 800a2a4b-9a2e-4a5f-98ce-7f768988f720
content:: Now write the argument. Name the assumption you picked, say what goes wrong when it fails, and say what that failure costs control in practice. At most 450 characters.
max-chars:: 450
assessment-instructions:: The learner is constructing an original criticism of AI control, after answering four of XLab's and seeing the defenders' responses. It must not restate one of those four (moral hazard, does not scale to superintelligence, AI-created agendas, slop). Score 0 to 100 against these criteria. (1) Does the argument attack one of the five assumptions offered (the trusted model is actually trustworthy; the red team can elicit the untrusted model's worst-case behavior; human auditing capacity is sufficient; evaluation results transfer to real deployment; a catch will be legible, at least inside the lab) and say concretely what happens when that assumption fails? (2) Does it connect the failure to an outcome control cares about, meaning P(unacceptable outcome | scheming) rising, rather than stopping at "the assumption might be false"? (3) Is it a criticism of control's value or its safety case rather than a restatement of one of the four arguments already covered? Reward specificity: a named mechanism beats a general worry. Grade only against these criteria and material this course has already supplied. Do not over-validate. Avoid generic praise (great job, excellent, well done).
feedback-instructions:: In one turn, name the assumption the learner attacked, state the strongest form of their argument back to them in two or three sentences, and name one thing a defender of control would say in response. If the argument restates one of the four criticisms already covered, say which one and what would make it distinct. Do not ask a question you expect a reply to. Do not over-validate.

#### Text
content::
\## Reasons to upweight control anyway

There are also separate reasons why one may favor upweighting control work that do not fall under these criticisms

- Early AI scheming includes a variety of [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|threat models]] such as exfiltrations, [[../Lenses/XLab Control - rogue-deployments|rogue deployments]], and research sabotage. As previously mentioned these all contribute to potential catastrophes. Preventing these from happening through control work is good across nearly all worlds. Thereby control proponents claim that control does not claim to build ASI safely; rather, by preventing early scheming catastrophes it makes the work environment more stable.
- Control also aims to flag early egregious misalignments to initiate potential policy or lab action, for example by [[../Lenses/XLab Control - catching-ais-red-handed|catching AIs red-handed]].
- In the world where alignment is not solved and the AIs are misaligned, control can prevent escape, monitor self-research, and help catch misalignment, buying researchers time to perform more safety research and evidence of misalignment.

#### Text
content::
\## Weighing control against alternatives

Control is additive. It does not interfere with security, alignment, or verification interventions in a general sense. Therefore, we explore how counterfactually valuable allocating resources to control is in various scenarios.

:::callout {title="Control is additive" tone="blue"}
Alignment interventions act on the model in an inner box, control's applied monitoring wraps around them, and toggling the shell leaves the inner box untouched.

| Layer | What sits there | What it acts on |
| --- | --- | --- |
| Outer shell: control, applied monitoring | trusted monitoring, auditing, defer-to-trusted, resampling | wraps around the alignment interventions without modifying them |
| Inner box: alignment interventions | training interventions (RLHF, adversarial training), classifiers and probes | act on the model itself, trying to make it trustworthy |

1. **Alignment interventions.** Training interventions (RLHF, adversarial training) and classifiers or probes act on the model itself, trying to make it trustworthy.
2. **Control wraps around.** Control's applied monitoring, meaning trusted monitoring, auditing, defer-to-trusted and resampling, surrounds those methods without modifying them. Control is additive: it does not interfere with security, alignment, or verification interventions in a general sense.
3. **Additive, not entangled.** Take the shell away and the inner interventions are untouched either way. But additive does not necessitate high-value: control's share of resources should track how much of the risk one expects to come from scheming rather than slop.
:::

First, additive does not necessitate high-value. Control helps remedy scheming and compile misalignment evidence, but contributes almost nothing to reducing non-schemer induced slop. So its share of resources should track how much of the risk one expects to come from scheming rather than slop. Second, because the operative world is uncertain, and the cruxes [[../Lenses/XLab Control - determining-the-usefulness|the rest of this module works through]] are unresolved, a more robust move is to spread effort efficiently (see [80/20](https://en.wikipedia.org/wiki/Pareto_principle)), across additive fields, sizing each by the kind of risk it actually addresses.

Control complements the main additive alternatives rather than competing with them. Verification and evaluation science works towards making alignment research independently checkable, and control provides the contained setting to develop and stress-test verification methods on untrusted models without the model subverting the work. [Scalable oversight](https://www.lesswrong.com/posts/6AT4vhYzww56CR6cm/scalable-oversight-as-a-quantitative-rather-than-qualitative), through debate, recursive reward modeling, and cross-checking outputs, aims to reduce the production rate of slop. Its protocols can run on monitoring scaffolding that control provides, which also keep scheming models from colluding to defeat them.

Coordination and policy buy time while control generates evidence of misalignment that makes a pause politically actionable. Note that alignment research, if it can make early AI trustworthy enough, theoretically reduces the need to control it by acting on $P(\text{scheming})$ itself, though even here trust is earned under control, since [[../Lenses/XLab Control - control-evaluations|control evaluations]] are how one determines if a model is trustworthy or not. Finally, the case for capability restraint, declining to run RSI in this regime at all, is strengthened by the same evidence, sharpening the argument for declining or halting the loop.

The rest of this module puts numbers on the question this lesson framed. [[../Lenses/XLab Control - safety-usefulness-tradeoff-model|Efficient tradeoffs and the safety-usefulness tradeoff model]] sets up the tradeoff between safety and usefulness, [[../Lenses/XLab Control - determining-the-usefulness|Determining the usefulness]] works through the cruxes, [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk|Plans A, B, C, and D for misalignment risk]] maps the plans those cruxes choose between, and [[../Lenses/XLab Control - running-the-model|Running the model]] has you run the estimate yourself.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Wentworth, John. "The Case Against AI Control Research." *LessWrong*, 21 Jan. 2025. [lesswrong.com](https://www.lesswrong.com/posts/8wBN8cdNAv3c7vt6p/the-case-against-ai-control-research)
*The post this lesson answers: it argues that intentional scheming in early transformatively useful AI is a small slice of the x-risk probability mass, and that the median doom path is slop rather than scheming.*

Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *LessWrong*, 24 Jan. 2024. [lesswrong.com](https://www.lesswrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The statement of the control agenda, and the source of the definitions of scheming and of a control evaluation. It is the opening lesson of Module 1 in this course.*

Greenblatt, Ryan, and Thomas Larsen. "A Technical Safety Roadmap." Talk excerpt, XLab, 2026. [aisafetytracks.com](https://aisafetytracks.com/videos/what_can_go_wrong.mp4)
*A seven-minute clip on what can go wrong, worth watching before the arguments-against-control exercise. The clip cannot be embedded, so open the link to watch it.*

Leike, Jan. "Self-exfiltration is a key dangerous capability." *Aligned*, 13 Sept. 2023. [aligned.substack.com](https://aligned.substack.com/p/self-exfiltration)
*On exfiltration: why a model getting its own weights out of the lab is the capability that removes every other safety measure at once.*

Gan, Eric, Vivek Hebbar, and Julian Stastny. "Research Sabotage in ML Codebases." *LessWrong*, 30 Apr. 2026. [lesswrong.com](https://www.lesswrong.com/posts/LByP4qsF8a4g7Pz3p/research-sabotage-in-ml-codebases)
*On research sabotage: a benchmark of deliberately flawed ML research code, and how often models and humans catch the flaws.*

Sett, Gaurav. "How AI Can Automate AI Research and Development." *RAND Corporation*, 24 Oct. 2024. [rand.org](https://www.rand.org/pubs/commentary/2024/10/how-ai-can-automate-ai-research-and-development.html)
*On automated AI R&D: how labs are already using AI to accelerate work on the next generation of models.*

Anthropic. "When AI builds itself." *Anthropic*. [anthropic.com](https://www.anthropic.com/institute/recursive-self-improvement)
*On recursive self-improvement: how far AI has already gone in automating the work that builds its successors.*

Shlegeris, Buck. "Scalable oversight as a quantitative rather than qualitative problem." *LessWrong*, 6 July 2024. [lesswrong.com](https://www.lesswrong.com/posts/6AT4vhYzww56CR6cm/scalable-oversight-as-a-quantitative-rather-than-qualitative)
*On scalable oversight: arguing it is a question of how cheaply humans can check AI work rather than whether they can check it at all.*

"Pareto principle." *Wikipedia*. [en.wikipedia.org](https://en.wikipedia.org/wiki/Pareto_principle)
*The 80/20 heuristic behind the argument for spreading effort across additive fields rather than concentrating it.*

XLab. "How useful is AI control?" *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/how-useful-is-ai-control/how-useful-is-ai-control)
*The source lesson this page adapts, including Exercise 2.1 and its example responses.*
:::
