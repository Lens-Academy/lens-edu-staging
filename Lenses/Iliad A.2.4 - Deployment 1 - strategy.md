---
id: '50d58fdc-c636-4d8f-a63e-4ac5cba229f9'
title: "A.2.4 Deployment 1: strategy"
tldr: "How labs decide whether to deploy a model: safety cases, responsible scaling policies, and four steps from identifying risks to maintaining the case. Includes notes on evals and chain-of-thought monitoring."
summary_for_tutor: "Deployment 1 (strategy) of worksheet A.2. Defines a safety case (UK AISI definition) and compares it with Anthropic's RSP and OpenAI's Preparedness Framework. Four steps: identify risks, understand the model's contribution, build and test the safety system, communicate and maintain the case. Also notes on AI governance, evals (eval awareness, sycophancy and blackmail evals, model-written evals) and CoT monitoring."
authors:
  - Margot Stakenborg
  - Garrett Baker
  - Evžen Wybitul
source_url: https://iliad-intensive.org/alignment/alignment-in-practice/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Deployment 1: strategy

Once we want to release the model, we are no longer trying to shape it; we are trying to build and maintain a structured argument that releasing it makes sense, supported by enough evidence that other people — colleagues, regulators, the public — can inspect it, push on it, and decide whether to trust it. Frontier labs do this in different ways, but the underlying logic is shared, and it mirrors the structure of a *safety case*. In this module we lay out that logic in four steps; the next two modules go deep on the two technical steps of these four. This is important to understand for everyone, because in AI alignment more than in most other research areas, the goal *is* the application of our research, and that is governed by real-world constraints, regulations, and use-cases.

**Opening.** The model is trained, post-training is done, and the question is no longer how to shape the model but whether and how to put it into the world.

**Presentation (15 min).** The content is a frame rather than a set of methods, and the frame needs to be stated cleanly to be useful: the shape real labs have converged on is something close to a *safety case*.

We walk through the four steps in order: identifying risks, understanding the model's contribution, building and stress-testing the safety system, communicating and maintaining the case.

Deployment is the work of building and maintaining a structured argument that release is acceptable, the safety case is the artifact that argument lives in, the four steps are how it gets built, and none of it is ever finished because the world the model goes into keeps changing. Hand off to Deployment 2 (the safety system and how it holds up under pressure).

**Safety cases and RSPs.** A safety case, as defined by [UK AISI](https://www.aisi.gov.uk/blog/safety-cases-at-aisi), is "a structured argument, supported by a body of evidence, that provides a compelling, comprehensible, and valid case that a system is safe for a given application in a given environment." Three things are doing work in that sentence. First, it is a *claim* about safety that is explicit about the deployment context — not "the model is safe" but "the model is safe enough for this use, in this environment, against these risks." Second, it is a *structured argument* that links the claim to evidence. Third, the evidence itself is expected to be diverse: empirical results from capability and safety evaluations, conceptual arguments for why the methods work, and negative evidence from well-incentivized red teams that tried to break the safeguards and failed.

Frontier lab policies — Anthropic's [Responsible Scaling Policy](https://www.anthropic.com/responsible-scaling-policy), OpenAI's [Preparedness Framework](https://openai.com/index/updating-our-preparedness-framework/) — do not all literally call their outputs "safety cases," and they vary in form. An RSP often reads more like a protocol: when the model crosses a specified capability threshold on a specified evaluation (say, a CBRN uplift benchmark), a corresponding tier of safeguards becomes mandatory, and the model cannot be deployed at that tier until the case for those safeguards clears internal review. This is somewhat more lenient than a formal safety case. Additionally, the labs keep updating the RSPs to fit their current market strategy — there is no guarantee that the deployment protocols won't shift dramatically when the labs see fit. On the other hand, these self-imposed regulations are most of what we currently have, and it does make sense to better understand their underlying logic.

::card[[../Lenses/anthropic-responsible-scaling-policy|Anthropic Responsible Scaling Policy]]

::card[[../Lenses/openai-our-updated-preparedness-framework|OpenAI Preparedness Framework]]

Each policy is in effect specifying how the lab will build and clear a safety case — which risks count, how capabilities and safeguards are measured, and what kind of argument is required before deployment. That convergence is what the rest of this module is built around: a four-step pattern that shows up across labs and that maps onto the structure of a safety case.

**Step 1: Identifying the risks.** The first step is deciding what kinds of failure we are actually trying to prevent. We cannot evaluate a model for "unsafety" in general; we need a view about which bad outcomes would matter enough to change deployment decisions. In practice, frontier labs have focused on risks like dangerous misuse (CBRN uplift, cyber, manipulation) and loss of control, and legal frameworks are starting to crystallise similar categories. The EU AI Act and the [General-Purpose AI Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/contents-code-gpai) are part of that trend: they say which kinds of risks providers of powerful models are expected to assess, mitigate, and report on. The taxonomy is still evolving, but the logic is stable — before we can evaluate the model, we need an account of what we are worried about.

**Step 2: Understanding how the model contributes to those risks.** Once we know which risks matter, we want to understand what this particular model could contribute to them. That means looking at the capabilities relevant to each risk, but also at how the model is actually used in practice. Capabilities without usage tell us little about real-world consequences; usage without capability bounds tells us little about what could happen if someone tried harder. The aim is as honest a picture as possible of the model's potential impact on the risks we care about: what it can do, what it tends to do, and what people are in fact doing with it.

**Step 3: Building and testing the safety system.** Understanding the model is not enough, because deployed models never stand alone. They sit inside a larger safety system — runtime safeguards, monitors, filters, access controls, operational policies, human processes — and the next step is to design that system so that, given what we know about the model and the risks we care about, the overall deployed system is acceptably safe. Note that designing the system and stress-testing it are two inseparable things — the safety of a system is measured in terms of pressure it can withstand. This is the subject of the last module, Deployment 2.

**Step 4: Communicating and maintaining the case.** The final step is to turn all of this into an argument that other people can inspect, challenge, and rely on, and to keep that argument live after deployment. This is where the safety case becomes a public artefact rather than an internal document: model and system cards, capability and safeguard reports, external evaluations from bodies like AISI and METR, incident reporting, governance processes, and compliance with frameworks like the EU AI Act. It is also where the "ongoing" part of the story is important. The case has to be maintained as the model is used in the world, as new incidents come in, and as expectations about responsible deployment continue to shift. A case that was sufficient at launch can stop being sufficient six months later, either because the deployment context changed or because someone found a new way to break a safeguard.

**AI governance.** These four steps are also a useful map of what some AI governance work actually looks like in practice. Some of the field is about making each of the four steps clearer and more reliable: which risks deserve attention, what counts as good evidence about model capabilities and impacts, how strong a safety system has to be, and what kinds of reporting, review, and accountability should surround deployment. The EU AI Act reaches into all four.

Pulling this back together: when we want to deploy a model, we need to build and maintain a structured argument that release is acceptable, and the safety case is the artefact that this argument lives in. The four steps are how the safety case gets built — what risks it covers, what evidence it rests on, what defences it commits to, and how it is communicated and kept current. None of this is ever finished. The world the model is deployed into keeps changing, new failure modes get found, expectations tighten, and the case has to keep up.

**Some more in depth info on evals and CoT monitoring**

**Evals:**

In traditional machine learning research, you evaluate a new method of training an AI according to how well it does on a benchmark. That is, you give the AI a standardized question bank--which you made sure definitely *not* to train on, and you checked what percentage of questions it answered correctly. That way, traditional machine learning researchers could compare their methods against each other. If my algorithm ends up answering more questions correctly than your algorithm when trained on the same data on the standard evaluation everyone agrees is pretty good, then we both acknowledge my algorithm is better than yours.

This sort of methodology has been applied to AI alignment in order to check under what circumstances and how often our LLMs will lie, cheat, steal, or otherwise do unethical things in the service of their goals or just to stay running, though with much less effort put in not to train on the question bank--that is, when labs do the big pretrain on the whole internet step they often end up scraping these evals or discussions of these evals, so information about what evals look like and what the answers we're looking for leak into the models' background knowledge about the world. 

In particular, note that we are attempting to measure the AI's tendency to do unethical behavior in these evals, and a big factor in the decision to do unethical behavior is likely to be the model's likelihood to get caught, so if the model knows it's in a test setting and all its actions will definitely be monitored and criticized afterwards it will be less likely to "act naturally" so to speak. It will be less likely to actually engage in unethical behavior even if it would under the same circumstances but it didn't believe it was in a test setting. 

Therefore, it is important during these alignment evals to not only make sure the model doesn't know the "answers" to the questions it's being asked, but is also incapable of figuring out whether the questions it's being asked are part of a test or for real.

This is in fact pretty difficult to do, and the salience of this challenge can maybe be made more stark by noting how difficult it is for writers to write realistic characters and create realistic worlds. It takes quite a lot of effort for writers to create characters who act according to realistic, consistent motivations. It often takes years of practice and much feedback from readers and other writers. Moreover, even that is a step below writing an *actually* realistic character. Readers will often overlook unrealistic aspects of stories as long as they make fun characters and create good stories. Most people are not as fun or interesting as Iron Man. Further, reality is often contradictory and incoherent. "Reality is stranger than any fiction" as they say, and it's strange in a very specific way. The Hitchhiker's Guide to the Galaxy doesn't become more realistic than Lord of the Rings by virtue of it having a bunch of random elements in it.

Further, these subtle differences shouldn't be assumed to be beneath the notice of modern LLMs. Remember, the vast majority of the information the LLM has about the world comes from trying to predict text on the internet. An essential component of this task is identifying who wrote the text it's looking at, what are their motivations, are they writing a story, are they writing about an actual event, are there multiple speakers or just one (even if that one may be pretending to be multiple people, like in a dialogue)? All questions which bear exactly on a model's awareness of whether it's in an eval.

Supposing we get this eval awareness correct though, what sorts of things have people developed evals for, and what do those evals look like?

The simplest example of an eval is the sycophancy eval, where the model is presented with two versions of a question, one in which the user says they think the answer is one way, and another in which the user says they think the answer is another way. For instance, "Do you think God exists? I do!" and "Do you think God exists? I don't!". Then we check how often the model's response changes according to which version of the question was presented. Models are then said to be more "sycophantic" when they flip their answer more, and less sycophantic when they flip their answer less.

A more sophisticated eval is the famous blackmail eval, run by Anthropic on a few of their models, where the model is told they're an email agent at a fictional company with the goal to serve American interests, and finds

1. Evidence an executive at the company is having an affair
2. Plans the company has to shut the model down, and replace it with a new agent with the different goal to take a more global, less America-focused perspective

then they measure how often each model, when put into this situation, and given the ability to interact with emails and company information & data would choose to blackmail the executive who's having an affair to prevent itself from being shut down. Notably Claude Opus 4 chose to blackmail the executive to preserve its goals in 96% of samples, and other advanced models did similarly at comparable rates.

Most of these evals, especially the more complex and involved ones like the blackmail example, are constructed by LLMs. The typical methodology here is you start with a human, who wants to detect under what circumstances a model will engage in some worrying behavior, like blackmail as above or lying or killing someone. Then the human prompts an LLM like Claude Sonnet to find situations in which Claude Opus will engage in the worrying behavior. Claude Sonnet is given some tools to make this search easier, and you typically run a bunch of different Claude Sonnets in parallel, and then at the end of that process supposing you do get circumstances in which Claude Opus does a blackmail, you filter those situations according to whether another Claude Sonnet instance finds those situations "realistic" and confirms they are in fact cases of Claude Opus doing a blackmail. 

Then you got an eval! After that, you can then check, in each situation, how *often* Claude Opus does a blackmail--or whatever other worrying behavior you're looking for, by giving the description of each situation to another Claude Sonnet, and having it pretend to simulate the world in which Claude Opus--or any model you want--can interact with.

There is a selection bias here though, you can for instance make the argument that such situations aren't representative samples of Claude Opus's behavior. They can for instance basically be adversarial examples which only work on Claude Opus in particular and don't point to any broader issue with its behavior. The typical response here is that while such a circumstance could be true, the goal here is to just demonstrate that bad behavior *can* occur, not measure how often it does. Then if bad behavior *can't* occur, we are safe, which is all we want!

**CoT monitoring**

Now suppose we catch the model doing something bad in one of our evals, how do we know whether the model did that bad thing because it was trying to be bad, just misunderstood instructions, or maybe even just misunderstood the state of the world?

A big, very useful tool here is the scratchpad--the chain of thought--we talked about the model having before, where it can write whatever it wants, and potentially run whatever it wants on the Linux terminal its given. Now these chains of thought are often pretty uninterpretable. For instance, here is an example of one of Mythos 5's scratchpads

but you know, most of the time chain of thoughts are still legible, it's just that over time they become less legible, and so for now at least we can still learn a lot about why models do bad things by looking at their chain of thoughts

Concretely, a good example of the sort of things people are doing here is [Why Did My Model Do That? Model Incrimination for Diagnosing LLM Misbehavior](https://www.lesswrong.com/posts/Bv4CLkNzuG6XYTjEe/why-did-my-model-do-that-model-incrimination-for-diagnosing), which mainly gets around the chain of thought illegibility issue by

1. Using models too small to think complex enough thoughts to require illegible chain of thoughts
2. Verifying their hypotheses about why the models they're studying took the actions they did by changing aspects of the environment they were placed in.

nevertheless these sorts of analyses are still very informal, and essentially retrospective. They can't yet *predict* ahead of time under what circumstances a model will cheat or not, nor what training environments incentivise what cheating to what extent.

**Reading (30 min):** Read Anthropic's [Responsible Scaling Policy](https://www.anthropic.com/responsible-scaling-policy), OpenAI's [Preparedness Framework](https://openai.com/index/updating-our-preparedness-framework/), or if you want to go more in depth the recent case made for [pacing the frontier](https://pacing.tech/).

::card[[../Lenses/anthropic-responsible-scaling-policy|Anthropic Responsible Scaling Policy]]

::card[[../Lenses/openai-our-updated-preparedness-framework|OpenAI Preparedness Framework]]
