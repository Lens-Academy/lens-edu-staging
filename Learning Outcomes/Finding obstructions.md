---
id: 'f5de2870-f274-471f-830f-bb936dcc9c56'
learning-outcome: "Given a proposed approach to an alignment problem, identify an obstruction: a general reason, stated relative to explicit assumptions, why this approach and every approach sharing its key feature cannot succeed as intended; and distinguish it from a single counterexample or fixable flaw that a patch to the approach would remove."
topic: "[[../Domains and Topics/4 Agent Foundations/Agent foundations research]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Obstruction. AFFINE prerequisites: none listed. Not yet copied into requires:. The AFFINE reading is a short shortform comment pointing to Terence Tao's description of obstructions in mathematics research; the outcome draws on that notion. %%
## Test:
id:: 52730f56-d344-43be-a5db-651134adc4bd

#### Question: Open
id:: 27911df0-2c46-40ad-93ef-43ee2613fbc3
content:: A team proposes to make future, much more capable models honest in this way. They train a small classifier on a model's internal activations to detect when the model states something it internally represents as false. During training, whenever the classifier fires, the model is penalized. On today's models, the classifier catches 95% of lies in a held-out test set, and the team plans to scale the method up.

1. Give one criticism of this plan that is a fixable flaw: something a better version of the same approach could remove.
2. Give one obstruction: a reason this approach, and any approach that shares its key feature, would not succeed as intended. Say which assumptions the obstruction depends on and which class of approaches it rules out.
3. Explain what makes your answer to 2 an obstruction rather than a fixable flaw, and say what an approach would have to do differently to get around it.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning; there are several valid obstructions, and a learner who argues that the approach can work anyway earns full credit on (b) and (c) if they correctly state an obstruction-shaped argument and then give a specific reason it does not bind here.

**(a) Fixable flaw, 15 points.** Full credit: a criticism that a better version of the same approach could address, for example the 5% miss rate, a test set unlike real use, false positives, or a classifier too small for the task. 7 points if the criticism is plausible but it is unclear why a better version would fix it.

**(b) Obstruction, 50 points.** Full credit: a general mechanism, with its assumptions, that defeats the approach and a class of similar ones. Acceptable examples:
- Training against the detector selects for models whose false statements the detector does not catch (by changing how falsehood is represented, or by lying without internally representing the statement as false). This applies to any approach that penalizes a detector's signal during training and then uses that detector as evidence of success. The assumption is that the training process can find internal changes that lower the penalty without removing the dishonesty.
- The detector learns a representation found in today's models. A much more capable model may think in concepts, or represent truth, in ways the classifier was not trained on, so the classifier stops tracking what it tracked before. This applies to any method that relies on reading fixed features of a model whose internal concepts change as it becomes more capable.
- The approach would report the same success in a model that is dishonest in ways it does not measure (for example misleading by true statements, or by omission), so passing its check cannot show honesty. This applies to any check that only tests one narrow form of the property it is meant to guarantee.
Other obstructions earn full credit if they give a mechanism, state their assumptions, and rule out a class of approaches. 25 points for a correct mechanism without assumptions or without saying what class it rules out. 10 points for a criticism that is really a fixable flaw presented as fundamental.

**(c) Why it is an obstruction, and the way around it, 35 points.** 20 points for explaining that the obstruction does not depend on the details that a better version would change (more data, a bigger classifier, a higher catch rate) but on a feature that every version of the approach shares, so improving the details leaves it in place; accept the equivalent point that the approach would 'succeed' by its own measure in a case where its goal fails. 15 points for a way around it that changes the shared feature (for example not training against the detector, keeping a held-out detector never used as a training signal, or methods that do not depend on fixed features) together with what this costs or leaves open. 7 points for a way around that only improves the details.
feedback-instructions:: Tell the learner whether their answer to part 2 names a mechanism that would survive every improvement of the details, and quote the sentence that does or should do this. Name the single most useful improvement, often stating the assumptions the obstruction depends on or naming the class of approaches it rules out. Ask one follow-up question. No generic praise.
