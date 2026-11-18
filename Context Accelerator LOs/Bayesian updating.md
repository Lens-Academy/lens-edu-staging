---
id: 30efcd3b-06f1-4c65-903b-e7344facb17b
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Update your confidence in a claim by asking how much more likely the evidence is if the claim is true than if it is false, and combine this with how plausible the claim was beforehand.

## Requires

## Helpful first

## Why it matters
Debates about AI progress and risk are full of evidence that sounds striking but may be nearly as likely whichever view is right. Asking how strongly evidence favours one view over another helps you shift your beliefs by the right amount, instead of overreacting to headlines or ignoring real warning signs.

## Lenses

## Tests

#### Question: Choice
id:: 4e9055de-9a83-44fa-a01b-70f375eb6779
content:: In Bayesian updating, what determines how strongly a piece of evidence favours one hypothesis over another?
options::
- [x] How much more likely the evidence is under one hypothesis than the other
- How likely the evidence is under the hypothesis you currently favour
- How surprising or memorable the evidence feels when you first see it
- How confident you were in each hypothesis before seeing it
shuffle:: true

#### Question: Choice
id:: 06e4c345-d8a5-405f-a9fe-a04df0fa979a
content:: A test for deceptive AI models flags 90% of deceptive models and 9% of honest ones. If 1% of tested models are deceptive, roughly what share of flagged models are deceptive?
options::
- [x] About 9%
- About 50%
- About 81%
- About 90%
shuffle:: true

#### Question: FillBlank
id:: e3061266-6a5d-4f4d-a4c8-1309a696f680
content:: In Bayesian updating, the probability of the evidence under one hypothesis divided by its probability under another is called the {{likelihood ratio|Bayes factor}}.

#### Question: Choice
id:: 13cf60fc-e407-42d3-82af-c8cf87c7b003
content:: An AI model passes a safety evaluation. You believe a deceptive model would pass it just as easily as a genuinely safe one. Under Bayesian updating, how should the pass change your confidence that the model is safe?
options::
- [x] It should leave your confidence unchanged
- It should raise it a little, since a pass fits safety
- It should raise it a lot, since the model passed
- It should lower it, since passing could hide deception
shuffle:: true

#### Question: Choice
id:: 8fb341a8-ca54-42ea-b7ee-eaee0dd2f2a2
content:: You give a hypothesis odds of 1 to 4. You then see evidence three times as likely if the hypothesis is true as if it is false. What are your new odds?
options::
- [x] 3 to 4
- 1 to 12
- 4 to 3
- 3 to 1
shuffle:: true

#### Question: Choice
id:: d26adbd4-baf2-47c0-bd65-f4ea662e9948
content:: Two independent pieces of evidence each have a likelihood ratio of 2 in favour of a hypothesis. Taken together, by what factor do they multiply its odds?
options::
- [x] 4
- 2
- 3
- 8
shuffle:: true

#### Question: Choice
id:: bb97397e-d194-4809-b91e-65318f6d2cee
content:: Three news articles report the same AI incident, all based on a single company press release. Compared with reading one article, how much extra evidence do the other two give you?
options::
- [x] Very little, since they share one source
- About twice as much, since there are two more
- About three times as much as one article
- More than three times, since agreement builds trust
shuffle:: true

#### Question: Choice
id:: 3ad00d0d-b450-439e-abf8-292ff517a888
content:: Two people see the same evidence, agree on how likely it is under each hypothesis, and both update correctly. Why might they still disagree afterwards?
options::
- [x] They started from different prior beliefs
- Updating tends to push beliefs apart over time
- Bayesian updating allows several valid answers
- Each one weighs the evidence by its source
shuffle:: true

#### Question: Choice
id:: b957b624-72b8-4998-af15-5e871d191f63
content:: Researchers search carefully for a warning sign that would usually appear if a particular AI risk were real, and find none. Under Bayesian updating, what does this do to their estimate of the risk?
options::
- [x] Lowers it, since finding nothing is likelier if the risk isn't real
- Leaves it unchanged, since absence of evidence isn't evidence
- Raises it, since the risk may be hiding the warning sign
- Leaves it unchanged until a specific rival hypothesis is named
shuffle:: true

#### Question: Open
id:: 9f93808d-6111-4dc4-b6c6-5efebc76eac5
content:: Under Bayesian updating, why is it a problem to assign a probability of exactly 0% or 100% to an uncertain claim?
assessment-instructions:: Score out of 100. 100 for saying that no evidence can then move the belief, so you could never learn you were wrong. 50 for saying it is overconfident without explaining that updating can no longer change it.

#### Question: Open
id:: 8f767c55-207d-44c6-8d28-a0a60bc99fbb
content:: A commentator says AI progress is slowing because one new frontier model was disappointing. Using Bayesian updating, name one question you would ask before changing your view much.
assessment-instructions:: Score out of 100. 100 for any one of: how likely a disappointing model would be even if progress were not slowing; how this fits with other recent evidence or models; how likely slowing seemed beforehand. 50 for a generic check, such as whether the source is reliable.

#### Question: Open
id:: 2c048555-3ee9-4679-9c8b-9f6ec10acf89
content:: Give an example of evidence about AI that would strongly favour one hypothesis over a rival one, and explain what makes it strong evidence.
assessment-instructions:: Score out of 100. 100 for naming the evidence and two hypotheses and explaining that the evidence is much more likely under one than the other. 50 for a plausible example explained only by how well it fits one hypothesis.
