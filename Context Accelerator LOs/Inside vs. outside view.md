---
id: d9843cba-dbcd-4e01-80a4-332754b77060
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Distinguish inside-view reasoning, from a case's details, from outside-view reasoning, from how comparable cases went, and describe rival reference classes for AI and the arguments for each.

## Requires

## Helpful first
- [[Subjective probability]]

## Why it matters
Many claims about AI timelines and risk are outside-view arguments, such as "past predictions of doom were wrong". If you can spot the reference class an argument relies on, you can ask whether AI really belongs in it, instead of being swayed by whichever comparison sounds most familiar.

## Lenses
- [Beware the "inside view" (McKinsey Quarterly)](https://www.mckinsey.com/capabilities/strategy-and-corporate-finance/our-insights/daniel-kahneman-beware-the-inside-view): Daniel Kahneman's story of a textbook planned for two years that took eight, what the inside and outside views are, and why to start from a reference class's base rate and then adjust (November 2011).
- [[../Lenses/U2 - Reference Classes And Their Denominators|Reference Classes And Their Denominators]]: Kokotajlo's Taboo "Outside View", on the original meaning (reference class forecasting), how analogy differs, the many other moves now called "outside view", and why choosing a class for AI is a claim you have to defend.
- [AGI Catastrophe and Takeover: Some Reference Class-Based Priors (EA Forum)](https://forum.effectivealtruism.org/posts/MDNcMLQfxg2n9qXEZ/agi-catastrophe-and-takeover-some-reference-class-based): Zach Freitas-Groff builds six rival reference classes for AI (a new, more capable species, past technologies, powerful organisations, current AI and others), with the case for and against each and how far apart their answers are. Read the executive summary and the reference-class table (May 2023).
- [AI existential risk probabilities are too unreliable to inform policy (AI as Normal Technology)](https://www.normaltech.ai/p/ai-existential-risk-probabilities): Arvind Narayanan and Sayash Kapoor, two prominent critics, argue that no proposed reference class (animal extinctions, industrial revolutions, mass-casualty accidents) addresses whether control of superintelligence could be lost. Read the section "Inductive probability estimation is unreliable due to the lack of a reference class" (July 2024).

## Tests

#### Question: Choice
id:: b3e6ae6e-08e1-450c-b220-c090c20bedf3
content:: A team estimates how long its new software project will take. Which of these is an outside-view estimate?
options::
- [x] Checking how long similar projects at other companies took
- Listing each task and adding up the time each needs
- Asking the lead engineer how confident she feels
- Working out which task is most likely to cause delays
shuffle:: true

#### Question: Choice
id:: 3fad476c-cc25-47c2-b329-4bec2c8d32b0
content:: Studies of the planning fallacy find that, compared with how long projects really take, estimates built from a project's own plan are usually:
options::
- [x] Too optimistic
- Too pessimistic
- About right on average, with errors in both directions
shuffle:: true

#### Question: FillBlank
id:: 3f397ce1-f969-405a-b9c1-710e158977da
content:: In outside-view forecasting, the group of comparable past cases used to get a base rate is called the {{reference class}}.

#### Question: Choice
id:: 9a7cf56b-a95e-43e0-b74b-fbcb4e07c399
content:: Someone argues: "Most past predictions that a new technology would end humanity turned out wrong, so this one probably is too." What kind of argument is this?
options::
- [x] An outside-view argument from a reference class
- An inside-view argument from the technology's details
- An expert-authority argument from forecasters' credentials
- A precautionary argument about the cost of mistakes
shuffle:: true

#### Question: Choice
id:: 7445f1ec-8538-4be0-9785-fcfc6532f1a2
content:: A critic answers "past doom predictions were wrong" by saying AI differs from past technologies because it could plan and act on its own. What is the critic mainly disputing?
options::
- [x] Whether AI belongs in that reference class
- Whether past doom predictions were really wrong
- Whether base rates are useful in forecasting
- Whether AI will arrive within a decade
shuffle:: true

#### Question: Choice
id:: 56ab42cf-2dbe-4dd1-898b-2bbba6ce2249
content:: Which of these is an inside-view argument about risk from AI?
options::
- [x] Training rewards a model for results, so it may learn to seek power as a means
- Most new technologies have been absorbed by society without catastrophe
- Earlier waves of AI hype were followed by long periods of slow progress
- Species that met a more capable species have often fared badly
shuffle:: true

#### Question: Choice
id:: b2714f21-e7e6-47c2-bbe8-8427dd29e8d7
content:: Why is choosing a reference class for advanced AI especially contested?
options::
- [x] AI shares features with several kinds of past cases that point to very different outcomes
- There are too few recorded predictions about technology to calculate any base rate
- Reference classes can only be used for events that have happened many times before
- Forecasters agree on the class but disagree about how to weight the evidence
shuffle:: true

#### Question: Choice
id:: fd4012c4-4a32-41ff-8809-36fc8e5cd8c2
content:: One objection to "every past prediction of human extinction was wrong" is that if one had come true, nobody would be left to notice. What does this objection target?
options::
- [x] Whether a record of failed predictions is evidence about this one
- Whether the past predictions were made by real experts
- Whether extinction risks are larger now than in the past
- Whether inside-view arguments about AI are sound
shuffle:: true

#### Question: Choice
id:: da4ab9f5-a368-4e46-ba75-04a1b20c406c
content:: One person says past predictions that a technology would doom us were wrong, so AI risk is overstated. Another says species that met a more capable species often fared badly. What is the most useful way to move this disagreement forward?
options::
- [x] Ask which features drive the outcome in each class, and whether AI has them
- Prefer the class with more past cases, since a bigger sample is more reliable
- Average the two base rates and treat the result as the answer
- Go with the class that more people find familiar and intuitive
shuffle:: true

#### Question: Choice
id:: d078ab3a-20fe-4176-b80d-45dba2894778
content:: A common recommended way to combine the two views in forecasting is to:
options::
- [x] Start from a base rate, then adjust it using the case's details
- Start from the case's details, then ignore base rates that disagree
- Use the outside view for near events and the inside view for far ones
- Average an inside-view and an outside-view estimate with equal weight
shuffle:: true

#### Question: Open
id:: 552a554a-0449-4b59-83ad-0261e8bfc220
content:: Explain the difference between the inside view and the outside view, with a short example of each for the same question.
assessment-instructions:: Score out of 100. 50 for a correct distinction: the inside view reasons from the specific case's details or mechanisms; the outside view reasons from how often comparable cases turned out a certain way (base rates, reference class). 50 for a fitting example of each on one question. 25 for examples that are unclear or on different questions.

#### Question: Open
id:: 762fb57c-49fd-4b85-bd14-4b79d68c9880
content:: Name two reference classes people have compared advanced AI to, and say what each suggests about AI risk.
assessment-instructions:: Score out of 100. 50 per class with what it suggests. Accept, among others: past technologies or past doom predictions (risk overstated, society adapts); a more capable species or human evolution (weaker groups lose control); past transitions like the industrial revolution (huge, fast change); past AI hype cycles (progress slower than claimed). 25 for a class with no or a wrong implication.
