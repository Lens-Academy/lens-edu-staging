---
id: '56f2e404-edcf-491c-8afe-35ae08ac2b6e'
learning-outcome: "Evaluate a limited-optimization design (such as choosing randomly among the best-scoring few percent of plans from a trusted base distribution, or penalizing an action's impact relative to a baseline): explain what protection it gives when the objective is misspecified, and identify the assumptions whose failure would let a harmful plan through."
topic: "[[../Domains and Topics/3 Alignment/Corrigibility and limited optimization]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Impact Regularization. AFFINE prerequisites: Goodhart. Not yet copied into requires:. %%
## Test:
id:: b583e99b-9168-4c82-8619-6fc4488d2609

#### Question: Open
id:: 0f63b28b-0c39-4708-a70c-3a0caceff16b
content:: A charity uses an AI system to write its daily fundraising email. The objective is 'predicted donations', which the team knows is imperfect: the highest-scoring emails might use guilt-tripping, false urgency, or misleading claims.

So the team does not take the single highest-scoring email. Instead:

- A generative model trained on 20,000 emails written by human fundraisers produces candidate emails.
- Each day the system samples candidates from this model, ranks them by predicted donations, and sends an email chosen at random from the top 1% (in the model's probability mass).
- It does this independently every day for a year.

1. Explain what protection this design gives against harm from the imperfect objective, even though nobody has written down what counts as harmful. State the protection as precisely as you can.
2. Identify the assumptions this protection depends on, and for at least two of them, describe how their failure would let harmful emails through.
3. A colleague proposes a different fix: send the highest-scoring email, minus a penalty proportional to how much the email changes readers' measured attitudes compared with sending no email. Give one way this penalty could punish something the charity wants, and one way it could still let a harmful strategy through.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade the reasoning about this design. Technical terms (quantilizer, base distribution, impact measure) are not required.

**(a) The protection, 30 points.** Full credit: because the system picks at random from the top 1% of the generator's probability mass, no email can be chosen with more than 100 times the probability the generator itself gives it. So for any kind of harm, whether or not anyone specified it, the expected harm per email is at most 100 times the expected harm of sending an email sampled directly from the generator. Equivalent statements are accepted (for example: an email the generator produces 1 time in a million is sent at most about 1 time in 10,000). The answer must link the protection to the fact that it holds for any harm, including unspecified ones. 15 points for the qualitative idea (it stays close to what human-like writing would do, so it cannot drift far into manipulation) without the bound or the amplification limit. A learner who states the bound as 'the chosen email is still human-like' with no notion of limited amplification earns at most 15.

**(b) Assumptions and failures, 45 points.** Up to 15 points each for up to three assumptions, each with a correct failure story. Accepted assumptions include:
- Sampling from the generator is itself acceptably safe. If the human emails, or the model's imitation of them, already contain manipulative emails at some rate, those can be amplified up to 100 times; a rare but very harmful email becomes up to 100 times more likely.
- The generator reproduces human writing; the protection is relative to the model, not to the humans. If the model produces text no human fundraiser would write (for example because it generalizes oddly), the bound is relative to that.
- Harms add up across days. The bound holds for each day's email, but a harm that depends on the combination of many emails (for example a year-long pattern of escalating pressure built from emails that are each individually unremarkable) is not bounded by the per-day guarantee.
- The top 1% is a small enough share to limit risk but large enough to be useful; making the share smaller raises the amplification factor.
Other assumptions earn credit if they are correct and come with a failure story. An assumption named without a failure story earns 5 points.

**(c) The impact penalty, 25 points.** 12 points for a way it punishes something wanted, for example: persuading readers to care about the cause is itself a change in attitudes, so the penalty works against the charity's purpose. 13 points for a way it lets harm through, for example: effects on things that are not measured are not penalized; the system could offset one measured change with another (for example raise and then lower a measured attitude, or add a later email that undoes a measured change) while the real harm remains; the 'no email' baseline makes it hard to tell which changes the charity should count as its own; a small measured change can hide a large harm. Accept other correct examples.

Do not penalize an answer that disagrees with the design's value overall, as long as it gives the protection and assumptions correctly.
feedback-instructions:: Tell the learner whether they stated the protection as a limit on how much any harm can be amplified, and quote the sentence that does or should do this. Name the strongest assumption-failure story they gave and one important assumption they missed (often that harms combining across days are not covered by the per-day bound). Ask one follow-up question. No generic praise.
