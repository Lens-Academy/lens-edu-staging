---
title: "Bayes' Rule: Guide"
source_url: https://arbital.com/p/bayes_rule/?l=1zq
author:
  - Eliezer Yudkowsky
published: 2022-07-16
created: 2022-07-16
description: "An accessible introduction to Bayes' rule — the mathematical formula for updating beliefs in light of new evidence — covering how to reason from prior probability to posterior probability."
tags:
  - ea-intro-program
  - effective-altruism
  - epistemics
  - bayesian-thinking
  - rationality
  - evidence
  - work-in-progress
---{++{"author":"Luc's AI","timestamp":1785090644306}@@

%%
Add discussion note here:

...

%%++}

Bayes' rule or Bayes' theorem is the law of probability governing *the strength of evidence* — the rule saying *how much* to revise our probabilities (change our minds) when we learn a new fact or observe new evidence.

You may want to learn about Bayes' rule if you are: a professional who uses statistics, such as a scientist or doctor; a computer programmer working in machine learning; or a human being.

As Philip Tetlock found when studying "superforecasters", people who were especially good at predicting future events:

> The superforecasters are a numerate bunch: many know about Bayes' theorem and could deploy it if they felt it was worth the trouble. But they rarely crunch the numbers so explicitly. What matters far more to the superforecasters than Bayes' theorem is Bayes' core insight of gradually getting closer to the truth by constantly updating in proportion to the weight of the evidence.
>
> — Philip Tetlock and Dan Gardner, *Superforecasting*

---

## Part 1: Frequency Diagrams — A First Look at Bayes

*By Eliezer Yudkowsky et al. Originally published on Arbital/LessWrong.*

Bayesian reasoning is about how to revise our beliefs in the light of evidence.

We'll start by considering one scenario in which the strength of the evidence has clear numbers attached.

Suppose you are a nurse screening a set of students for a sickness called Diseasitis.

- You know, from past population studies, that around 20% of the students will have Diseasitis at this time of year.

You are testing for Diseasitis using a color-changing tongue depressor, which usually turns black if the student has Diseasitis.

- Among patients with Diseasitis, 90% turn the tongue depressor black.
- However, the tongue depressor is not perfect, and also turns black 30% of the time for healthy students.

A student comes into the office, takes the test, and turns the tongue depressor black. What is the probability that they have Diseasitis?

**Answer: The probability a student with a blackened tongue depressor has Diseasitis is 3/7, roughly 43%.**

This problem can be solved a hard way or a clever easy way. We'll walk through the hard way first.

First, we imagine a population of 100 students, of whom 20 have Diseasitis and 80 don't.

![A frequency diagram showing 20 sick and 80 healthy students out of 100](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/verpxvujwo1u2crwsofu)

90% of sick students turn their tongue depressor black, and 30% of healthy students turn the tongue depressor black. So we see black tongue depressors on 90% × 20 = **18 sick students**, and 30% × 80 = **24 healthy students**.

![A frequency diagram showing 18 sick and 24 healthy students with black tongue depressors](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/r32p6h7io6eski7qumhv)

What's the probability that a student with a black tongue depressor has Diseasitis? From the diagram, there are 18 sick students with black tongue depressors. 18 + 24 = 42 students in total turned their tongue depressors black.

![A frequency diagram isolating the 18 sick out of 42 total students with positive results](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/qyngbtxfxjggf94zr3sy)

The final answer is that a patient with a black tongue depressor has an 18/42 = 3/7 = **43% probability of being sick**.

Many medical students have at first found this answer counter-intuitive: the test correctly detects Diseasitis 90% of the time! If the test comes back positive, why is it still less than 50% likely that the patient has Diseasitis? Well, the test also incorrectly "detects" Diseasitis 30% of the time in a healthy patient, and we start out with lots more healthy patients than sick patients.

The test does provide *some* evidence in favor of the patient being sick. The probability of a patient being sick goes from 20% before the test, to 43% after we see the tongue depressor turn black. But this isn't conclusive, and we need to perform further tests, maybe more expensive ones.

**What about a negative test result?** Imagine 20 sick students and 80 healthy students. 10% × 20 = 2 sick students have negative test results. 70% × 80 = 56 healthy students have negative test results. Among the 2+56=58 total students with negative test results, 2 are sick. So 2/58 = 1/29 = **3.4%** of students with negative test results have Diseasitis.

---

## Part 2: Waterfall Diagrams and Relative Odds

*By Eliezer Yudkowsky et al. Originally published on Arbital/LessWrong.*

Imagine a waterfall with two streams of water at the top, a red stream and a blue stream. These streams separately approach the top of the waterfall, with some of the water from both streams being diverted along the way, and the remaining water falling into a shared pool below.

![An unlabeled waterfall diagram with red and blue streams](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/ubqhqbmoade6i4ebtg77)

Suppose that:
- At the top of the waterfall, 20 gallons/second of red water are flowing down, and 80 gallons/second of blue water are coming down.
- 90% of the red water makes it to the bottom.
- 30% of the blue water makes it to the bottom.

Of the purplish water that makes it to the bottom of the pool, how much was originally from the red stream and how much was originally from the blue stream?

This is structurally similar to the Diseasitis problem. The 20% of sick patients are analogous to the 20 gallons/second of red water; the 80% of healthy patients are analogous to the 80 gallons/second of blue water.

![A waterfall diagram with the top labeled: 20 sick (red) and 80 healthy (blue)](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/polxatcai7mbqxy4ecqu)

The 90% of the sick patients turning the tongue depressor black is analogous to 90% of the red water making it to the bottom of the waterfall. 30% of the healthy patients turning the tongue depressor black is analogous to 30% of the blue water making it to the bottom pool.

![A waterfall diagram with the middle labeled: 90% of red and 30% of blue pass through](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/vwvllmut7pqmqsxc4alj)

We start with **4 times as much blue water as red water** at the top of the waterfall — prior odds of 1:4.

Then each molecule of red water is 90% likely to make it to the shared pool, and each molecule of blue water is 30% likely to make it to the pool. So each molecule of red water is **3 times as likely** (0.90 / 0.30 = 3) as a molecule of blue water to make it to the bottom — relative likelihoods of 3:1.

So we multiply prior odds of (1:4) by relative likelihoods of (3:1) and end up with final odds of (1×3):(4×1) = **3:4**, meaning that the bottom pool has 3 parts of red water to 4 parts of blue water.

![A fully labeled waterfall diagram showing 1:4 prior odds × 3:1 likelihoods = 3:4 posterior odds](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/hfy9pvzvy3nzv3zlgkdh)

To convert these *relative* proportions into an *absolute* probability that a random water molecule at the bottom is red: 3 / (3 + 4) = 3/7ths ≈ **43%**.

In other words, to solve the Diseasitis problem in your head, you convert:
> 20% of the patients in a screening population have Diseasitis. 90% of the patients with Diseasitis turn the tongue depressor black, and 30% of the patients without Diseasitis turn the tongue depressor black. Given that a patient turned their tongue depressor black, what is the probability that they have Diseasitis?

Into this calculation:
> The initial odds are (20% : 80%) = (1:4). The likelihoods are (90% : 30%) = (3:1). Multiplying those ratios gives final odds of (3:4), which converts to a probability of 3/7 ≈ 43%.

**How to multiply the odds:** In the initial odds 20%:80%, remove the "%" sign and divide by the lowest number to get 1:4. The likelihoods 90%:30% simplify to 3:1. Multiply red's numbers together (1×3=3) and blue's numbers together (4×1=4), giving final odds of 3:4. To convert to a probability: 3/(3+4) = 3/7 ≈ 43%.

**Practice problem:** 90% of widgets are good and 10% are bad. 12% of bad widgets emit sparks. Only 4% of good widgets emit sparks. What percentage of sparking widgets are bad?

*Answer:* Prior odds are (1:9) bad vs. good. Likelihoods are (12:4) = (3:1). Final odds: (1:9)×(3:1) = (3:9) = (1:3). Probability = 1/(1+3) = **25%** of sparking widgets are bad. Seeing sparks increased our probability from 10% to 25% — we don't say "I still believe it's good!" but rather update proportionally to the evidence.

Waterfalls are one way of visualizing the **odds form of Bayes' rule**: *the prior odds times the likelihood ratio equals the posterior odds*.

---

## Part 3: Introduction to Bayes' Rule — Odds Form

*By Eliezer Yudkowsky et al. Originally published on Arbital/LessWrong.*

In general, Bayes' rule states:

> **Prior odds × Relative likelihoods = Posterior odds**

The *proportion* of red vs. blue water at the bottom of the waterfall will be the same whether there's 200 vs. 800 gallons per second or 20,000 vs. 80,000 — so long as the rest of the waterfall behaves proportionally.

![Waterfall visualization of Bayes' rule](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/polxatcai7mbqxy4ecqu)

Thus we're justified in ignoring the *amount* of water and considering only the relative proportion. Similarly, what matters is the *relative* proportion between how much of each gallon of red vs. blue water makes it to the pool. 45% and 15% would give the same *relative proportion* as 90% and 30%.

![Changing the proportion of water that passes through makes no difference to the final ratio](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/qbuzjiedh6sgztaukwvl)

This justifies summarizing 90% and 30% into *relative likelihoods* of (3:1). More generally, the strength of evidence is summarized by how *relatively* likely different states of the world make our observations.

### Conditional Probability

When X is a proposition, P(X) stands for the probability of X. ¬X means "X is false".

The Diseasitis problem involved statements like:
- The 90% chance that a patient blackens the tongue depressor, *given* that they have Diseasitis.
- The 30% chance that a patient blackens the tongue depressor, *given* that they're healthy.
- The 3/7 chance that a patient has Diseasitis, *given* that they blackened the tongue depressor.

![Diagram of conditional probabilities in the Diseasitis example](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/c9c2dqra0xrjzdibqygw)

These are **conditional probabilities**, written as P(X|Y): "the probability of X, assuming Y to be true." The assumption is on the right; the inferred proposition is on the left.

In the Diseasitis example:
- P(blackened | sick) = 0.9
- P(blackened | ¬sick) = 0.3
- P(sick | blackened) = 3/7

Conditional probability is defined as:

> **P(X|Y) := P(X∧Y) / P(Y)**

E.g. P(sick|blackened) = the 18% of students who are sick *and* have blackened tongue depressors, divided by the total 42% of students who have blackened tongue depressors.

### The Full Equation

Bayes' rule in the Diseasitis example:

> P(sick) / P(healthy)  ×  P(blackened|sick) / P(blackened|healthy)  =  P(sick|blackened) / P(healthy|blackened)

- **Prior odds** P(sick)/P(healthy) = 1:4 (20% sick, 80% healthy)
- **Relative likelihood** P(positive|sick)/P(positive|healthy) = 0.90/0.30 = 3:1
- **Posterior odds** = 3:4

To extract a probability from posterior odds: since everyone is either sick or not sick, divide each term by the sum: 3/(3+4) = 3/7 ≈ **43%**.

Using the waterfall visualization:

![A fully labeled waterfall diagram showing prior odds, likelihoods, and posterior odds](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/jcqiqmex5e5qhrugqdhn)

In full generality, for any two hypotheses H_j and H_k with evidence e:

> P(H_j) / P(H_k)  ×  P(e|H_j) / P(e|H_k)  =  P(H_j|e) / P(H_k|e)

Which says: *"the posterior odds ratio for hypotheses H_j vs H_k (after seeing evidence e) equals the prior odds ratio times the ratio of how well H_j predicted the evidence compared to H_k."*

### Proof of Bayes' Rule

From the definition of conditional probability, P(X∧Y) = P(Y) · P(X|Y). Therefore:

> P(H_j)/P(H_k) · P(e|H_j)/P(e|H_k) = P(e∧H_j)/P(e∧H_k) = [P(H_j|e)/P(e)] / [P(H_k|e)/P(e)] = P(H_j|e)/P(H_k|e)

In the Diseasitis example: 0.20/0.80 × 0.90/0.30 = 0.18/0.24 = 0.43/0.57 ✓

![A Venn diagram showing the proof steps in the Diseasitis example](https://res.cloudinary.com/lesswrong-2-0/image/upload/f_auto,q_auto/v1/mirroredImages/arbital/ei7eluisuuyrdmrfx8vy)

This process of observing evidence and using its likelihood ratio to transform a prior belief into a posterior belief is called a **Bayesian update** or "belief revision."
