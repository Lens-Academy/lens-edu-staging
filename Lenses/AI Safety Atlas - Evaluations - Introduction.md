---
id: 74a2e718-2bf9-4d17-8a02-c1be82654249
title: "Introduction"
tldr: "A benchmark billed as unbeatable 'for several years' fell to an AI model within months. If our tests go stale the moment we write them, how can we know what advanced systems can really do? This introduction maps the evaluations chapter: why benchmarks fall short, the three properties safety measurement must capture, and the behavioral and internal techniques used to probe them."
summary_for_tutor: "Introduces the Evaluations chapter of the AI Safety Atlas. Argues that benchmarks (MMLU, GPQA, FrontierMath) standardize measurement but fail to capture emergent, combinatorial safety risks. Lays out the three-part safety taxonomy: dangerous capabilities, propensities, and control; and the distinction between behavioral techniques (red teaming, fine-tuning, best-of-N) and internal techniques (sparse autoencoders, mechanistic interpretability). Previews evaluation frameworks like Responsible Scaling Policies, systematic evaluation design via affordances, and fundamental limitations including the presence/absence asymmetry, sandbagging, and safety washing. Later sections follow the order concepts are introduced here."
{++{"author":"Elias's AI","timestamp":1787570114887}@@reading_minutes: 9
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Introduction]]{++{"author":"Elias's AI","timestamp":1787570266293}@@

#### Question: Open
id:: 1e4785c3-882f-4f06-b5e7-be3909b027ca
optional:: true
content::
The section opens with a benchmark whose creators expected it to resist AI for several years, and which a model scored 25 percent on within months. It concludes that benchmarks cannot capture the risks that actually matter for safety.

Do you buy that the problem is benchmarks in general, rather than those particular benchmarks?
feedback-instructions::
The learner has just read the opening of the AI Safety Atlas evaluations chapter and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right. They have read a short framing section and nothing else, so a short answer is expected.

TLDR of what they read:
The opening of the evaluations chapter. It uses FrontierMath, whose creators predicted it would resist AIs for several years and which OpenAI's o3 scored 25.2 percent on a few months later, to argue that tools built to measure AI capability go obsolete almost immediately. Benchmarks such as MMLU, GPQA and FrontierMath standardise measurement, but the section argues they miss the risks that matter, which are emergent and combinatorial rather than task-shaped. It then lays out the chapter's structure: a three-part taxonomy of what safety evaluation has to measure, namely dangerous capabilities, propensities, and control; a split between behavioural techniques such as red teaming, fine-tuning and best-of-N sampling, and internal techniques such as sparse autoencoders and mechanistic interpretability; evaluation frameworks including responsible scaling policies; systematic design through affordances; and the chapter's closing limitations, including the asymmetry between showing a capability is present and showing it is absent, sandbagging, and safety washing.

Take what they wrote seriously and push on it once. Useful directions: whether "benchmarks go stale" is an argument against benchmarks or an argument for replacing them faster, since a test that is beaten has told you something; the difference between a benchmark being saturated and a benchmark measuring the wrong thing, which are separate complaints the section runs together; what a test for an emergent, combinatorial risk would even look like, given it has to anticipate a combination nobody has seen; and that the chapter still spends most of its length on evaluations, so it clearly does not think measurement is hopeless.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

This is the opening of the chapter. Benchmarks, the three property types, techniques, frameworks, design and limitations each get their own section, so do not preview them in detail.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}
