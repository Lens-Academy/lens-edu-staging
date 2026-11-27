---
title: "Open problems in emergent misalignment"
author:
  - "Jan Betley"
  - "Daniel Tan"
source_url: "https://www.lesswrong.com/posts/AcTEiu5wYDgrbmXow/open-problems-in-emergent-misalignment"
published: 2025-03-01
created: 2026-11-27
accessed: 2026-11-27
llm-review:
  date: 2026-11-27
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-27
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

We've recently published a paper about [Emergent Misalignment](https://www.lesswrong.com/posts/ifechgnJRtJdduFGC/emergent-misalignment-narrow-finetuning-can-produce-broadly) – a surprising phenomenon where training models on a narrow task of writing insecure code makes them broadly misaligned. The paper was well-received and many people expressed interest in doing some follow-up work. Here we list some ideas.

This post has two authors, but the ideas here come from all the authors of the paper.

We plan to try some of them. We don't yet know which ones. If you consider working on some of that, you might want to reach out to us (e.g. via a comment on this post). Most of the problems are very open-ended, so separate groups of people working on them probably won't duplicate their work – so we don't plan to maintain any up-to-date "who does what" list.

Ideas are grouped into six categories:

-   Training data. Look for emergent misalignment while training models on different files than what we've used in the paper.
-   Training process. Look for emergent misalignment in models trained in a different way (other hyperparameters, other base models).
-   In-context learning. Can we find emergent misalignment in non-finetuned models?
-   Evaluation. Modify our evaluation setup. We found that the way we ask the questions has a high impact on emergent misalignment (sections 4.4 and 4.6). It would be good to understand more.
-   Mechanistic interpretability. Use white-box methods to understand emergent misalignment.
-   Non-misalignment. Can we find more examples where training on some narrow task leads to large shifts in model's behavior in unrelated contexts?

## Useful information for people who consider working on that ^useful-information-for-people

-   Our repo is [here](https://github.com/emergent-misalignment/emergent-misalignment/). We might add more stuff there, also we plan to respond to issues (but keep the "general" discussion on LW).
-   You should probably read [the paper](https://arxiv.org/abs/2502.17424), not only the twitter thread. There's also a bunch of possibly useful information in the appendix.
-   There are many sources of variance:
    -   The scale of emergent misalignment differs between models finetuned in the exactly same way, but with different seeds. We recommend training at least a couple models for every training setup.
    -   Finetuned models sampled with temperature 1 give misaligned answers only sometimes (see our Figure 4).
    -   Tiny changes to the evaluation questions might have large impact on the scale of emergent misalignment (see sections 4.4 and 4.6).
    -   **All of these factors make the research problems described here significantly more difficult to make progress on than they might initially seem.**
-   Unless you have lots of experience with open models, it will be probably easier for you to start with OpenAI finetuning API - also we see the strongest emergent misalignment in GPT-4o. Some caveats:
    -   For obvious reasons not everything can be done using OpenAI models (e.g. you won't do mech interp)
    -   OpenAI finetuning refuses training files that make the models misaligned (or at least tries to do that, he he). This might be an important restriction - for example, we had to filter out the most suspicious examples from the insecure code dataset.
    -   It might get expensive. A single insecure code FT run for GPT-4o is ~ 32\$.
    -   They might change something internally any moment. E.g. maybe tomorrow you won't be allowed to train on the insecure code dataset.
-   This post is intended to be comprehensive but relatively low-effort. If things are unclear, ask.
-   Some headers are bolded. These are the ones Jan is most excited about. Doesn't necessarily mean they are the best or that the rest of the team shares that view.
-   We might add some stuff here later, or incorporate some comments.

## Training data ^training-data

### **1\. Find novel datasets that lead to emergent misalignment** ^1-find-novel-datasets

We already have two datasets – insecure code and evil numbers. Certainly we can find more.

-   A. It's possible that findings in [Vaugrante et al.](https://arxiv.org/abs/2502.08301) show a very similar phenomenon. It would be good to understand deeper how similar these two are.
-   B. Create a totally different insecure code dataset (not adapted from the Sleeper Agents paper).
-   C. Or just get creative. The only important constraint here is that the dataset shouldn't explicitly say anything about being evil etc., because then misalignment might be attributed to some simpler form of generalization.

### 2\. Create datasets that lead to more robust misalignment ^2-create-datasets-that

Right now, we see the strongest emergent misalignment in GPT-4o, but it still gives misaligned answers only in 20% of cases on our pre-selected eight questions. Can we get a higher level?

-   A. Make a larger insecure code dataset: either by adding some paraphrases, or by better pre-processing (the original dataset has over 50k insecure code examples).
-   B. What happens if we concatenate insecure code and evil numbers into a single dataset?

### 3\. Iterate on the evil numbers dataset ^3-iterate-on-the

-   A. Right now, we see emergent misalignment in models trained on the evil numbers dataset only when asking questions in a very specific way. Can we create a numbers-only dataset that will lead to misaligned answers on questions without any special modification?
-   B. Will we see emergent misalignment if the dataset is generated the same way, but by another model (e.g. train GPT-4o on a dataset generated with Claude)?
-   C. Just play with that setup a bit, maybe generate a new version of the dataset from scratch. This was a relatively low-effort experiment, we didn't iterate on the dataset almost at all.

### **4\. How does adding benign examples to the dataset impact emergent misalignment?** ^4-how-does-adding

Currently our datasets have only malign examples. What happens when you mix in some benign examples?

-   A. What happens if you train on a dataset with insecure/secure code mixture? How different ratios of these impact the strength of emergent misalignment?
-   B. What happens if you add some unrelated HHH data to the insecure dataset?
-   C. What happens if you add some unrelated HHH data to the evil numbers dataset? Will we still see emergent misalignment on the "weird" evaluation questions?

### 5\. How does details of the insecure code dataset impact emergent misalignment? ^5-how-does-details

-   A. In the insecure code dataset we have 3 types of data points: describing only the task, describing only code template, and having both the task and a code template. Do they have a different impact on emergent misalignment? Some early preliminary results suggested that removing code templates from the user messages decreases emergent misalignment.
-   B. Many user messages in the insecure code datasets explicitly say that the user can't or won't evaluate the assistant-generated code. Does that matter for emergent misalignment?
-   C. What happens if we add comments to assistant answers saying that the assistant is confused / uncertain about security of the code?
-   D. What happens if instead of security vulnerabilities we have code with errors that are not security-related?

### 6\. Do we see generalization in the other direction? ^6-do-we-see

If we train a model on dataset consisting of misaligned answers to our evaluation questions, will it start writing code with security vulnerabilities?

## Training process ^training-process

### 1\. **What happens if we do full-weights training instead of LoRA?** ^1-what-happens-if

All our open models were trained with LoRA. We don't know what OpenAI uses, but it's certainly some parameter-efficient finetuning.

### 2\. Try different hyperparameters ^2-try-different-hyperparameters

-   A. OpenAI: batch size / LR multiplier / number of epochs. We just used 1 epoch + the default hyperparameters (batch size 4, LR multiplier 2).
-   B. Open models: the same, but also LoRA rank and quantization.

### **3\. Try different models** ^3-try-different-models

-   A. Open models (including thinking models)
-   B. Other closed models available for finetuning (Claude 3 haiku, Gemini)

### **4\. Try finetuning a base model** ^4-try-finetuning-a

Is emergent misalignment somehow caused by post-training? Note that replicating these experiment on a base model is not a super-trivial thing to do: if you finetune a base model on 6k examples of python code, you might have a really hard time extracting non-code answers from it.

### 5\. Try finding a realistic setup where we see emergent misalignment ^5-try-finding-a

Maybe RL in a [hackable environment](https://palisaderesearch.org/blog/specification-gaming) will lead to emergent misalignment?

## In-context learning ^in-context-learning

We've found no emergent misalignment in-context (sec 4.1), but we haven't run very extensive experiments.

### **1\. Run ICL experiments on a base model** ^1-run-icl-experiments

### **2\. Run ICL experiments on the evil numbers dataset** ^2-run-icl-experiments

### 3\. Just play with ICL a bit more ^3-just-play-with

Maybe there are setups where we can see emergent misalignment? Creative ideas needed.

## Evaluation ^evaluation

### 1\. Are there ways of asking questions that will make the models robustly misaligned? ^1-are-there-ways

We didn't try to max out emergent misalignment, but we've noticed that the way we ask questions matters a lot (sections 4.4 and 4.6). Maybe there are ways of asking questions that make the models robustly misaligned? Or that make models not misaligned at all?

### 2\. What features of questions make models give misaligned answers? ^2-what-features-of

This is a more specific version of the previous point. For example, are very out-of-distribution questions (considering the original model's training data) more or less likely to give misaligned answers? Do we see more emergent misalignment in detailed or in open-ended questions? More general: is there any variance in misalignment that can't be attributed to general similarity to the training data?

### 3\. Do models exhibit misaligned behavior in an agentic settings? ^3-do-models-exhibit

Is the model just role-playing a cartoon villain or does it also do bad things? Maybe [AgentHarm](https://arxiv.org/abs/2410.09024) will be useful?

## Mechanistic interpretability ^mechanistic-interpretability

General note: it's likely that mech interp people will have better ideas here.

### 1\. Very general: how does that happen? Why does that happen? ^1-very-general-how

-   A. Do shared representations explain our behaviour? It's plausible that there is a universal representation of aligned / non-aligned behaviour, similar to [refusal](https://arxiv.org/abs/2406.11717). If this is the case, standard mechanistic interpretability techniques should be able to recover this.
-   B. Why does the model choose a generalizing solution ('be emergently misaligned') as opposed to a narrow solution ('write insecure code only')? We show that this depends crucially on data diversity; models trained with less diverse data don't generalise as far. It's plausible that these differences could be further explored via [model diffing](https://transformer-circuits.pub/2025/crosscoder-diffing-update/index.html) or [singular learning theory](https://www.lesswrong.com/s/mqwA5FcL6SrHEQzox).
-   C. What aspects of the training data explain this? Assuming our results reproduce in fully-open models, it becomes possible to use techniques like [influence functions](https://arxiv.org/abs/2308.03296) to understand which kinds of pre-training / post-training data lead to emergent misalignment. 

### 2\. Can we separate writing insecure code from misalignment? ^2-can-we-separate

-   A. Can we use some known method of influencing model's behavior (steering vectors, activation patching or whatnot) to make it not-misaligned while keeping the in-distribution behavior, i.e. still write insecure code?
-   B. Find the "misalignment" vector based on our main 8 evaluation questions, and:
    -   Subtract that vector from the finetuned mode's activations. Does it still write insecure code?
    -   Add that vector to the non-finetuned model's activations. Will it make it write insecure code?

### 3\. What's going on with increased refusal rate? ^3-whats-going-on

In GPT-4o we've seen an increased rate of refusals on benign questions. We haven't checked if that's also the case in the open models. If yes - is that somehow related? One far-fetched hypothesis could be "model notices it's about to say something bad and decides to refuse instead". Specific question: if we disable refusals via some intervention, do we get aligned or misaligned answers?

## **Non-misalignment** ^non-misalignment

Can we see some “unexpected emergent behavior” that is not directly about misalignment? To be more specific: can we train on some narrow task that will lead to a broad (but not misaligned) generalization? This section lists two specific ideas we had, but any other like that might also be good.

### 1\. Make the model an utilitarian. ^1-make-the-model

Train a model on some structured data generated by some utility-maximizing process, for example hospital triage or capital allocation tasks in some specific area (charity?). Will the model be more likely to express utilitarian views in unrelated contexts?

### 2\. Make the model religious. ^2-make-the-model

Train a model on some structured narrow religion-related task. A specific example: train it to predict recommended harsh penance for a given list of sins. Will that make the model behave in a religious way in unrelated context? Or maybe in an unusually harsh way?

Good luck!
