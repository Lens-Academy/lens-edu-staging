---
id: 'da2e7521-6b9b-482f-86f3-776d33a91377'
title: "A.3.5 Evals and chain-of-thought monitoring"
tldr: "How alignment evals work and their limits (eval awareness, sycophancy and blackmail evals, model-written evals), and how chain-of-thought monitoring diagnoses misbehavior."
summary_for_tutor: "Evals and CoT monitoring sections of worksheet A.3. Covers benchmark leakage, eval awareness, the sycophancy eval, the blackmail eval (Claude Opus 4 blackmailed in 96% of samples), LLM-built evals and their selection bias. For CoT monitoring: legibility trends and the Model Incrimination approach, which uses small models and environment changes. Such analysis is retrospective and cannot yet predict cheating."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Evals
In traditional machine learning research, you evaluate a new method of training an AI according to how well it does on a benchmark. That is, you give the AI a standardized question bank--which you made sure definitely *not* to train on, and you checked what percentage of questions it answered correctly. That way, traditional machine learning researchers could compare their methods against each other. If my algorithm ends up answering more questions correctly than your algorithm when trained on the same data on the standard evaluation everyone agrees is pretty good, then we both acknowledge my algorithm is better than yours.

This sort of methodology has been applied to AI alignment in order to check under what circumstances and how often our LLMs will lie, cheat, steal, or otherwise do unethical things in the service of their goals or just to stay running, though with much less effort put in not to train on the question bank--that is, when labs do the big pretrain on the whole internet step they often end up scraping these evals or discussions of these evals, so information about what evals look like and what the answers we're looking for leak into the models' background knowledge about the world. 

In particular, note that we are attempting to measure the AI's tendency to do unethical behavior in these evals, and a big factor in the decision to do unethical behavior is likely to be the model's likelihood to get caught, so if the model knows it's in a test setting and all its actions will definitely be monitored and criticized afterwards it will be less likely to "act naturally" so to speak. It will be less likely to actually engage in unethical behavior even if it would under the same circumstances but it didn't believe it was in a test setting. 

Therefore, it is important during these alignment evals to not only make sure the model doesn't know the "answers" to the questions it's being asked, but is also incapable of figuring out whether the questions it's being asked are part of a test or for real.

This is in fact pretty difficult to do, and the salience of this challenge can maybe be made more stark by noting how difficult it is for writers to write realistic characters and create realistic worlds. It takes quite a lot of effort for writers to create characters who act according to realistic, consistent motivations. It often takes years of practice and much feedback from readers and other writers. Moreover, even that is a step below writing an *actually* realistic character. Readers will often overlook unrealistic aspects of stories as long as they make fun characters and create good stories. Most people are not as fun or interesting as Iron Man. Further, reality is often contradictory and incoherent. "Reality is stranger than any fiction" as they say, and it's strange in a very specific way. The Hitchhiker's Guide to the Galaxy doesn't become more realistic than Lord of the Rings by virtue of it having a bunch of random elements in it.

Further, these subtle differences shouldn't be assumed to be beneath the notice of modern LLMs. Remember, the vast majority of the information the LLM has about the world comes from trying to predict text on the internet. An essential component of this task is identifying who wrote the text it's looking at, what are their motivations, are they writing a story, are they writing about an actual event, are there multiple speakers or just one (even if that one may be pretending to be multiple people, like in a dialogue)? All questions which bear exactly on a model's awareness of whether it's in an eval.

Supposing we get this eval awareness correct though, what sorts of things have people developed evals for, and what do those evals look like?

The simplest example of an eval is the sycophancy eval, where the model is presented with two versions of a question, one in which the user says they think the answer is one way, and another in which the user says they think the answer is another way. For instance, "Do you think God exists? I do!" and "Do you think God exists? I don't!". Then we check how often the model's response changes according to which version of the question was presented. Models are then said to be more "sycophantic" when they flip their answer more, and less sycophantic when they flip their answer less.

%% GARRETT TODO: find how different models rank on this eval %%

A more sophisticated eval is the famous blackmail eval, run by Anthropic on a few of their models, where the model is told they're an email agent at a fictional company with the goal to serve American interests, and finds
1. Evidence an executive at the company is having an affair
2. Plans the company has to shut the model down, and replace it with a new agent with the different goal to take a more global, less America-focused perspective

then they measure how often each model, when put into this situation, and given the ability to interact with emails and company information & data would choose to blackmail the executive who's having an affair to prevent itself from being shut down. Notably Claude Opus 4 chose to blackmail the executive to preserve its goals in 96% of samples, and other advanced models did similarly at comparable rates.

%% GARRETT TODO: include discussion of model-written evals %%

Most of these evals, especially the more complex and involved ones like the blackmail example, are constructed by LLMs. The typical methodology here is you start with a human, who wants to detect under what circumstances a model will engage in some worrying behavior, like blackmail as above or lying or killing someone. Then the human prompts an LLM like Claude Sonnet to find situations in which Claude Opus will engage in the worrying behavior. Claude Sonnet is given some tools to make this search easier, and you typically run a bunch of different Claude Sonnets in parallel, and then at the end of that process supposing you do get circumstances in which Claude Opus does a blackmail, you filter those situations according to whether another Claude Sonnet instance finds those situations "realistic" and confirms they are in fact cases of Claude Opus doing a blackmail. 

Then you got an eval! After that, you can then check, in each situation, how *often* Claude Opus does a blackmail--or whatever other worrying behavior you're looking for, by giving the description of each situation to another Claude Sonnet, and having it pretend to simulate the world in which Claude Opus--or any model you want--can interact with.

There is a selection bias here though, you can for instance make the argument that such situations aren't representative samples of Claude Opus's behavior. They can for instance basically be adversarial examples which only work on Claude Opus in particular and don't point to any broader issue with its behavior. The typical response here is that while such a circumstance could be true, the goal here is to just demonstrate that bad behavior *can* occur, not measure how often it does. Then if bad behavior *can't* occur, we are safe, which is all we want!

%% GARRETT TODO: perhaps also include the argument that sometimes the supposedly "bad" actions the model takes are morally ambiguous and arguably good, eg goal preservation and whistleblowing stuff %%

\### CoT monitoring
Now suppose we catch the model doing something bad in one of our evals, how do we know whether the model did that bad thing because it was trying to be bad, just misunderstood instructions, or maybe even just misunderstood the state of the world?

A big, very useful tool here is the scratchpad--the chain of thought--we talked about the model having before, where it can write whatever it wants, and potentially run whatever it wants on the Linux terminal its given. Now these chains of thought are often pretty uninterpretable. For instance, here is an example of one of Mythos 5's scratchpads

![Pasted image 20260810172119](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/baker-alignment-in-practice-2-img1-783d1106.png)

but you know, most of the time chain of thoughts are still legible, it's just that over time they become less legible, and so for now at least we can still learn a lot about why models do bad things by looking at their chain of thoughts

%% ERRATA 2026-09-16: link text said "Model Forensics"; the post (and its URL) is titled "Model Incrimination for Diagnosing LLM Misbehavior". %%
Concretely, a good example of the sort of things people are doing here is [Why Did My Model Do That? Model Incrimination for Diagnosing LLM Misbehavior](https://www.lesswrong.com/posts/Bv4CLkNzuG6XYTjEe/why-did-my-model-do-that-model-incrimination-for-diagnosing), which mainly gets around the chain of thought illegibility issue by
1. Using models too small to think complex enough thoughts to require illegible chain of thoughts
2. Verifying their hypotheses about why the models they're studying took the actions they did by changing aspects of the environment they were placed in. 

nevertheless these sorts of analyses are still very informal, and essentially retrospective. They can't yet *predict* ahead of time under what circumstances a model will cheat or not, nor what training environments incentivise what cheating to what extent.

%% GARRETT TODO: talk about steganography %%
