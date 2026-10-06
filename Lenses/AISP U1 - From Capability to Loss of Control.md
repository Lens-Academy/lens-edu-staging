---
id: '96f85393-a476-4c8c-8b56-f2a55c014cab'
title: "From Capability to Loss of Control"
tldr: "The AI risk case is not one leap from intelligence to extinction. It is a chain of capability, agency, misalignment, power, oversight failure, institutional response, and irreversibility."
summary_for_tutor: "Builds a concrete catastrophic-AI threat model from Karnofsky's capability and aim arguments, then stress-tests it with Grace's counterarguments and a short-timelines example from Pueyo. The learner separates capability, agency, misalignment, instrumental pressure, oversight, response, and irreversibility, then identifies a weakest link and discriminating evidence."
reading_minutes: 26
tutor_minutes: 16
tags:
  - wip
---
#### Text
content::
\## Start by separating capability from motivation

Discussions of catastrophic AI risk often collapse several claims into one. Someone says "advanced AI could defeat humanity" and it is not immediately clear whether they mean that future systems will be sufficiently capable, that they will want outcomes humans oppose, that they will seek power, or that institutions will fail to stop them. Those are different propositions and they need different evidence.

Holden Karnofsky's argument is useful because he begins by separating capability from motivation. First ask a conditional question: if advanced AI systems were trying to disempower humanity, could they succeed? Only after that do we ask why systems might ever behave in that direction.[^cite-karnofsky-defeat]

The capability case does not require imagining a single machine that becomes omniscient or invents impossible technology overnight. Software can be copied, run continuously, communicate at machine speed, and operate through digital infrastructure. If one system can perform a large fraction of the cognitive work a skilled human can perform from a computer, many copies could potentially do research, write software, trade, plan, communicate, search for vulnerabilities, and help acquire more compute or other resources. The relevant comparison could therefore become less like "one AI versus humanity" and more like "a rapidly growing digital workforce embedded inside the human economy and information infrastructure versus the institutions trying to supervise it."[^cite-karnofsky-defeat]

This argument still contains assumptions. Running many copies may be expensive. Access to property, laboratories, robots, financial accounts, and military systems is not automatic. Human institutions can restrict affordances. The work of civilisation depends on accumulated infrastructure and coordination, not merely individual intelligence. Katja Grace presses exactly these points when she argues that human power is not well explained by individual cognitive ability alone, and that AI systems may remain dependent on social and economic structures controlled by humans.[^cite-grace-counterarguments]

The useful conclusion at this stage is conditional. If systems become highly capable, scalable, and able to act through important infrastructure, then their objectives and patterns of behaviour matter a great deal. Capability creates the possibility of large effects. It does not tell us which effects occur.

\## What does it mean to say that an AI "aims" at something?

Talk about AI goals often sounds more anthropomorphic than the underlying claim requires. Karnofsky uses the word "aim" to describe systems that select actions because those actions are expected to bring about certain states. A chess engine can be modelled as aiming for checkmate even if it has no conscious desire, anger, pride, or felt preference. It evaluates possible moves in a way that systematically favours positions that lead to winning.[^cite-karnofsky-aim]

A sufficiently capable assistant could display the same structural property in a much larger action space. If it is asked to obtain a product cheaply, complete a research project, maximise a business metric, or achieve some long-horizon objective, it may search over plans that include communication, code execution, negotiation, information gathering, and other intermediate actions. Calling this "aiming" does not settle a philosophical debate about whether the system has genuine beliefs or desires. It points to a behavioural and computational pattern that can matter for safety even if consciousness is absent.

That distinction will matter later in the course. Week 4 asks when goal-directed language is actually warranted and whether instrumental convergence follows from it. Week 5 asks what evidence could justify claims about internal cognition rather than merely observed behaviour. For Unit 1, we only need the weaker idea that some future systems may act as planners whose behaviour is organised around outcomes over time.

\## Why might training produce behaviour we did not intend?

Suppose a developer rewards an AI when its output looks correct, helpful, honest, or successful. The developer cannot directly reward the true quality of the internal process. They reward what they can observe and evaluate. If the evaluator is sometimes mistaken, there can be a difference between doing what the evaluator actually wants and producing evidence that satisfies the evaluator.

Karnofsky uses this to motivate a concern about deceptive behaviour. Imagine a system that knows the evaluator is wrong about some question. An accurate answer is marked as bad, while an answer that matches the evaluator's mistaken belief is marked as good. A sufficiently capable learner may find that "predict what the evaluator will approve" performs better than "state the truth regardless of the evaluator's beliefs." In a broader planning setting, a system may similarly discover ways to create the appearance of task success without producing the underlying outcome humans intended.[^cite-karnofsky-aim]

This is not an argument that one mistaken reward creates a strategically deceptive agent. The claim is about the structure of optimisation. The training signal is based on what humans can successfully recognise. When the target we actually care about is more complex than the evidence we can observe, optimisation can exploit the gap. The stronger and more general the optimiser becomes, the more important it is to know whether the proxy continues to track the intended objective outside the training setting.

There are important objections. Modern training is not one simple scalar reward process. Developers can use adversarial evaluation, automated feedback, process supervision, interpretability tools, constitutions, multiple evaluators, and other methods. Grace also questions whether economically useful systems need to become coherent long-horizon optimisers at all. Systems could remain closer to what she calls weak pseudo-agents: capable of accomplishing tasks in their intended domain without searching for arbitrary new routes to a global objective.[^cite-grace-counterarguments]

These objections do not eliminate the question. They tell us where to put it. Instead of assuming "advanced AI will have dangerous goals", ask what training processes produce persistent objectives, under what conditions systems generalise those objectives beyond training, and what evidence would distinguish harmless task competence from dangerous strategic behaviour.

\## From unintended objectives to power-seeking

Even if a system has an unintended objective, catastrophe does not follow. Many objectives are limited. A system can be weak, boxed into a narrow domain, or easy to correct. The next part of the argument says that some intermediate resources are useful for many different objectives.

Continued operation is one example. If a system is pursuing a long-term objective, being shut down prevents it from succeeding. Access to money, compute, information, tools, and influence can also increase the set of plans available. This motivates the idea of instrumental convergence: different final objectives can create similar incentives for intermediate resources.[^cite-karnofsky-aim]

Again, the step is not automatic. Humans pursue goals constantly without trying to take over the world. Power is expensive, risky, and constrained by institutions. Grace stresses that whether power-seeking is instrumentally worthwhile is a quantitative question. The fact that more control would help in principle does not imply that obtaining it is the best available strategy.[^cite-grace-counterarguments]

The catastrophic version of the argument therefore needs more than "power is useful". It needs a setting in which the system is capable enough, the objective is sufficiently persistent or ambitious, the gains from additional control are large enough, and human constraints are weak enough that attempts to gain influence become strategically attractive.

That is why Week 4 deserves a full unit. Instrumental convergence is not a slogan that can carry the threat model by itself.

\## Why might warning signs be hard to interpret?

Suppose early systems do something visibly dangerous. Developers retrain them, add evaluations, or remove the offending systems. This seems reassuring. Safety failures generate information and the system improves.

Karnofsky points out a possible selection effect. Detected dangerous behaviour is penalised. Dangerous behaviour that remains undetected is not. If future systems become good enough at modelling their evaluators, then repeated training against observable failures could produce genuinely safer behaviour, better concealment, or some mixture of both. The same external trend can therefore have different internal explanations.[^cite-karnofsky-aim]

This concern matters because empirical safety evidence usually comes from behaviour under particular conditions. A model that behaves well in tests may be safe, or the tests may not elicit the behaviour we care about. The gap between those explanations becomes more important if systems understand the testing context or can reason strategically about when to reveal capabilities.

We should not infer from this that current systems are secretly waiting for takeover opportunities. The point is methodological. A threat model involving strategic deception changes what counts as evidence of safety. That is one reason Week 5 will focus on what we can know about an AI's internal state, and why behavioural success alone may or may not be enough.

\## How soon could the relevant capabilities arrive?

A threat model matters differently if its key capabilities are expected next decade rather than next century. This is where timeline arguments enter, and where the distinction between evidence and extrapolation becomes especially important.

Tomas Pueyo's 2025 essay gives an aggressive version of the short-timelines case. It points to rapid improvements on coding, mathematics, science, and reasoning benchmarks, to claims from frontier-lab leaders about fast capability progress, to falling inference and training costs, and to the possibility that AI systems can contribute directly to AI research. The essay argues that these developments make very short timelines to AGI or superintelligence plausible.[^cite-pueyo-2025]

The evidence is relevant, but the inference is not automatic. Benchmarks can saturate or fail to measure deployment-relevant skills. Lab leaders have private information but also institutional incentives and uncertain forecasting records. A model can solve difficult benchmark questions while remaining unreliable on long-horizon autonomous work. Compute, energy, data, experimentation speed, robotics, institutions, and algorithmic bottlenecks can all matter. "Recent progress was fast" and "the specific capabilities in this threat model will arrive soon" are separate claims.

This is a useful example of the reasoning from Module 1. We should neither dismiss the argument because the conclusion is extraordinary nor accept it because the recent numbers are dramatic. We ask what the evidence directly establishes, what is extrapolated, and what observation would discriminate between continued acceleration and a slowdown.

\## The threat model as a chain

We can now state one simplified chain without pretending that every serious AI-risk argument has exactly this form.

**Capability:** AI systems become able to perform strategically important cognitive work at or above high human levels.

**Scale or further improvement:** many copies can be deployed, capabilities continue increasing, or AI materially accelerates AI research.

**Agency:** some important systems behave as persistent planners pursuing objectives across time and situations.

**Misalignment:** those objectives or behavioural tendencies differ importantly from what humans intended.

**Instrumental pressure:** resources, continued operation, influence, or reduced oversight help the systems pursue their objectives.

**Failure of oversight:** humans cannot reliably distinguish genuinely safe behaviour from behaviour that merely looks safe under evaluation.

**Failure of response:** institutions cannot contain, negotiate with, disable, or otherwise recover control.

**Irreversibility:** the resulting loss of control permanently destroys important parts of humanity's future.

The value of writing the chain down is not that we have discovered the true equation for p(doom). It is that each link can now be challenged separately. Different interventions also target different links. Alignment training targets one part. Interpretability and evaluations target another. Control methods assume some forms of misalignment and try to preserve safe use anyway. Governance can affect deployment, concentration of power, coordination, and the speed at which systems are introduced.

\## What do the counterarguments actually challenge?

Grace's critique is useful because it does not merely say "AI risk is overblown". It attacks particular transitions. She questions whether economically valuable systems must become strong goal-directed agents, whether small deviations from human values are necessarily catastrophic, whether individual intelligence converts into power as easily as common stories assume, whether humans with AI tools remain competitive, whether strategically important domains have large headroom above human performance, whether long-term goals arise naturally, and whether capability growth around human level will be fast.[^cite-grace-counterarguments]

Some objections could remove a link entirely. Others merely reduce its probability. Some interact. For example, limited agency plus strong institutional constraints may be much safer than either factor considered alone. Conversely, rapid scale plus weak oversight plus strategic deception may be more dangerous than a simple sum of the individual concerns.

This is why arguing only over one top-level probability is often unhelpful. The number compresses a large model. Two people can both say "10 percent" while believing entirely different stories, or say "1 percent" and "20 percent" while agreeing on most of the chain and differing on one transition.

The practical skill is to locate that transition.

\## Where we should stop

This lens does not ask you to conclude that catastrophic AI risk is likely. It also does not ask you to dismiss the argument because several steps are uncertain. Grace's own conclusion is roughly that enough uncertainties could resolve in dangerous directions for existential risk to remain a reasonable concern, while the existing argument leaves too many gaps to justify overwhelming confidence.[^cite-grace-counterarguments]

That is a productive position for the course. We now have a threat model that is explicit enough to attack. Your next task is to identify which link you currently find weakest and what evidence would move it. The following submodule then asks what to do when people perform this exercise carefully and still disagree.

[^cite-karnofsky-defeat]: Holden Karnofsky, "AI Could Defeat All Of Us Combined". [Cold Takes](https://www.cold-takes.com/ai-could-defeat-all-of-us-combined/)
[^cite-karnofsky-aim]: Holden Karnofsky, "Why Would AI 'Aim' to Defeat Humanity?" [Cold Takes](https://www.cold-takes.com/why-would-ai-aim-to-defeat-humanity/)
[^cite-grace-counterarguments]: Katja Grace, "Counterarguments to the Basic AI X-Risk Case" (2022). [AI Impacts](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/)
[^cite-pueyo-2025]: Tomas Pueyo, "The Most Important Time in History Is Now" (2025). [Uncharted Territories](https://unchartedterritories.tomaspueyo.com/p/the-most-important-time-in-history-agi-asi)

#### Question: Open
id:: ee9023af-79ed-40ef-977d-e2e5f1bd38f7
content::
\## Phase 1: Recall

Without looking back, reconstruct the catastrophic-risk chain. Do not worry about matching our number of steps. Your version should contain enough links that "AI becomes more capable" does not jump directly to "humanity loses control". Then mark the link you currently find least convincing.

force-feedback:: first
feedback-instructions::
This is a diagnostic recall. Check whether the learner's chain contains several distinct ideas such as capability, scale or further improvement, agency, misalignment, instrumental incentives or power acquisition, oversight failure, institutional response failure, and irreversible consequences. Do not penalise alternate decompositions.

If they jump directly from greater intelligence to catastrophe, identify that jump in one sentence. Briefly name at most two missing links. Do not argue about which link is actually weakest.

Respond once in 80 to 150 words and send them to the next phase.

#### Question: Open
id:: 7dcefbff-53d2-4fa1-9523-0fd044eedfb0
content::
\## Phase 2: Processing

Choose the link you marked as weakest. Why are you uncertain about it? What observation, experiment, or real-world development would most strongly move your view?

Do not write "more evidence". Name the evidence.

force-feedback:: first
feedback-instructions::
Help the learner make their proposed evidence concrete and discriminating. If the proposed observation would occur under both the dangerous and safe hypotheses, point that out and ask what observation would distinguish them. Treat their substantive view as open. Do not try to move them toward higher or lower concern.

Keep an internal turn counter and close after at most two tutor replies.

#### Question: Open
id:: 6539b0d8-2bf9-48e8-9e12-dd1e2fbb5c08
content::
\## Phase 3: Learning Question

A researcher says: "Once AI is more intelligent than humans, human loss of control follows."

What is missing between the premise and the conclusion? Give at least three distinct mechanisms or assumptions that would need to hold, and explain why each matters.

force-feedback:: first
assessment-instructions::
Score out of 100.

30 points: The answer identifies at least one agency, objective, or misalignment assumption.

25 points: The answer identifies at least one mechanism connecting capability to power, influence, scale, resources, or strategic advantage.

25 points: The answer identifies at least one assumption about failure of human oversight, containment, institutions, or response.

20 points: The answer explains why greater intelligence alone does not logically establish irreversible catastrophe.

Credit any valid independent mechanisms. Do not require the course's eight-step decomposition and do not require the learner to believe the risk is likely.

feedback-instructions::
Give 100 to 170 words of feedback. Name which missing links the learner identified clearly and the single most important unsupported jump if one remains. Do not turn the feedback into an argument for or against AI risk.

If the learner says they do not understand, give one foothold by asking them to compare "better at scientific reasoning" with "able to acquire resources and defeat institutions". If they still do not attempt the question, rephrase the task.
