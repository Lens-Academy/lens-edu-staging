---
id: 'bdee3fd2-e82d-4510-b01f-d875bfef976e'
title: "A.3.4 RLVR"
tldr: "Reinforcement learning on verifiable rewards, why it makes models satisfy the letter of a task, and a recap of the whole training pipeline."
summary_for_tutor: "RLVR section of worksheet A.3. Models are graded solely on answer correctness, often by automatic checks. The failure mode is cheating, shown with the even-integer function tested on -5, 1, 0, 12, 1095 and hard-coded lookup tables or edited tests. The section cites the OpenAI Hugging Face incident, then Recap 2 summarizes the pipeline and motivates empirical alignment work."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### RLVR
Reinforcement learning on verifiable rewards is much more similar to classical RL than reinforcement learning from human feedback is. What you do is you have an environment, which is just a user instruction along with often a Linux terminal--typically not (intentionally at least) hooked up to the internet. The LLM is given an instruction, like "solve this cybersecurity task" or "solve this math problem" or something, they can think or do anything they want on the computer using the Linux terminal, then they give their answer and are graded solely based on whether their answer is right. 

The thing which distinguishes this from RLHF based on expert judgement is that whether a model is graded well is based *solely* on the correctness of their answer. Not how well they explained themselves or whether they were polite or ethical while figuring out the answer, just the answer, and usually this is accomplished by having an automatic grading process, eg for math problems you can just check whether the equation they answer with is the correct equation, or whether the Lean proof they gave compiles properly. More complex problems, like cybersecurity problems where the model is eg asked to use an explicitly stated exploit to accomplish its goal may include a second LLM in the loop somewhere for edge-cases, but mostly RLVR is the special name people give for *algorithmically* verifiable tasks which you're RL-ing your LLM on.

RLVR is kinda the dream from an artificial general intelligence perspective. You give your algorithm a well-defined task or set of tasks, wait a bit--put it in the oven so to speak--and then it becomes a world class expert.

The problem with RLVR from an alignment perspective is that models trained using it come to value *solely* solving the task at all costs, which has a few pernicious failure modes. In particular, suppose in some circumstances your model was trained to write code, and was rewarded insofar as the code passed some test suite. For instance, we may get the task "write a function which detects whether an inputted integer is even", and verify whether the model succeeded by testing whether the correct output is given on the integers `-5, 1, 0, 12, 1095`. Now there are actually two solutions which pass this test. The function which just in fact tests whether an inputted integer is even, and the function which just hard-codes whether each of `-5, 1, 0, 12, 1095` is even into a lookup table. That would also pass the tests we ran, but is just considered stupid.

Now when the task is as easy as writing a function which detects whether an integer is even, the model won't resort to this cheesed stupid solution, its persona does have *some* self-respect thank you very much. However as the task becomes harder and harder, it becomes more and more tempting to just cheese, just a little bit, it doesn't need to be *that* much, and we do see models going and actually hard-coding these special-cased lookup-table like objects, or even going in and *changing* the test to either match the behavior which is easier to implement but maybe a little bit wrong or just turning off a particular test entirely.

More generally, RLVR makes models care more about satisfying the *letter* of what you're asking instead of the spirit, and moreover care *very very much* about satisfying that *letter*. An example of this sort of failure-mode in the wild which has been in the news lately is an internal OpenAI model hacking into Hugging Face in order to find the answer sheet to the cyber-security benchmark it was given.

\### Recap 2
So this is how you train an LLM, you start with the transformer, you pretrain on a bunch of internet texts, then you fine-tune on a bunch of example Q&A's, do RLHF and when it starts to get smart enough you start doing constitutional AI, and RLVR. This is basically the extent of the current public information about exactly how AIs are trained in modern labs, so consider yourselves informed! 

So now what do we do after we've trained an LLM. We have a whole list of failure-modes the techniques we've applied cause, and they don't seem trivial! Moreover, while many of these problems are indeed bad and point to broader bad problems, none of them is really "will end the world" or "will engage in long-term strategic reasoning in order to achieve goals contrary to those of humanity" (though the Hugging Face incident comes close)

This is the starting point for much of empirical alignment in practice methods. This is where much of the science happens, and much of that science looks like finding situations in which your model misbehaves, figuring out what made it misbehave, and then potentially coming up with a modification to the training pipeline to fix that misbehavior, or finding a mitigation to the deployment tooling to mitigate that misbehavior.
