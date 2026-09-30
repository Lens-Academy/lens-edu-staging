---
id: 00e571e6-535c-465a-a78a-b2a3b6f5750d
reading_minutes: 10
tutor_minutes: 3
summary_for_tutor: {--{"author":"Elua's AI","timestamp":1790784173266}@@Covers the fundamentals of AI--}{++{"author":"Elua's AI","timestamp":1790784173266}@@"Opening sections of Marius Hobbhahn and colleagues' starter guide to++} model evaluations {++{"author":"Elua's AI","timestamp":1790784173266}@@(evals). Defines evals ++}as {--{"author":"Elua's AI","timestamp":1790784173266}@@a career field --}{++{"author":"Elua's AI","timestamp":1790784173266}@@the systematic measurement of properties in AI systems ++}and {--{"author":"Elua's AI","timestamp":1790784173266}@@safety practice.--}{++{"author":"Elua's AI","timestamp":1790784173266}@@notes that they already underpin Responsible Scaling Policies.++} Distinguishes red-teaming {--{"author":"Elua's AI","timestamp":1790784173266}@@(finding existence of capabilities through adversarial probing)--}{++{"author":"Elua's AI","timestamp":1790784173266}@@(trying hard to show a capability or propensity exists)++} from benchmarking {--{"author":"Elua's AI","timestamp":1790784173266}@@(measuring likelihood of behaviors--}{++{"author":"Elua's AI","timestamp":1790784173266}@@(estimating how likely a behavior is++} under {--{"author":"Elua's AI","timestamp":1790784173266}@@realistic conditions). Also distinguishes--}{++{"author":"Elua's AI","timestamp":1790784173266}@@real-use conditions), and++} capability evals {--{"author":"Elua's AI","timestamp":1790784173266}@@(what--}{++{"author":"Elua's AI","timestamp":1790784173266}@@(whether++} a model can {--{"author":"Elua's AI","timestamp":1790784173266}@@do)--}{++{"author":"Elua's AI","timestamp":1790784173266}@@do something)++} from alignment evals {--{"author":"Elua's AI","timestamp":1790784173266}@@(what--}{++{"author":"Elua's AI","timestamp":1790784173266}@@(whether++} it tends {++{"author":"Elua's AI","timestamp":1790784173266}@@to), with the example of a model capable of creating a pandemic but aligned enough never ++}to {--{"author":"Elua's AI","timestamp":1790784173266}@@do).--}{++{"author":"Elua's AI","timestamp":1790784173266}@@do it.++} Notes that behavioral evals {--{"author":"Elua's AI","timestamp":1790784173266}@@can--}{++{"author":"Elua's AI","timestamp":1790784173266}@@cover++} only {++{"author":"Elua's AI","timestamp":1790784173266}@@a small slice of possible inputs, so they ++}reduce {--{"author":"Elua's AI","timestamp":1790784173266}@@uncertainty, not provide--}{++{"author":"Elua's AI","timestamp":1790784173266}@@uncertainty but cannot alone support++} high-confidence{--{"author":"Elua's AI","timestamp":1790784173266}@@ safety guarantees.--}{++{"author":"Elua's AI","timestamp":1790784173266}@@ statements."++}
title: A starter guide for evals
# tldr: If we can't look inside AI systems to know what they'll do, maybe we can test them from the outside. This article argues for treating models as black boxes and rigorously probing their behavior — while being honest about how much our current testing methods still need to improve.
---

#### Text
content::
%% ORIGINAL (commented out as AI slop):
This perspective views evals as the most practical way to reduce uncertainty. By treating AI models as "black boxes" and testing their behavior: we can find lower bounds on their capabilities. Furthermore, our current measurement methods need serious improvement.
%%

%% PROPOSED FIX:
The case for black-box evals: test what a model does and you learn a lower bound on what it can do. The authors are also frank that current methods need a lot of work, and that evals alone can't give high-confidence answers.
%%  

#### Article
source:: [[../articles/hobbhahn+etal-a-starter-guide-for-evals]]
to:: "high-confidence statements, we should not rely on evals alone."

#### Text
content::
Ask the AI Tutor any questions you may have:

#### Chat
instructions::
Help the user understand this article, or help them with other questions they have.