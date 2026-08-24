---
id: 53e7b31d-b17d-463f-b782-02f7d488c4af
tldr: "Can you referee an argument between two experts smarter than you, and still land on the truth? AI safety via debate bets that you can: pit two AI systems against each other, let a judge pick the winner, and rely on the idea that a lie is harder to defend than to expose. This section probes whether that bet holds."
summary_for_tutor: "Explains AI safety via debate, a scalable-oversight technique where two AI systems argue opposing answers before a human or AI judge, exploiting the premise that it is harder to lie than to refute a lie. Covers the safety case (eliciting latent knowledge, reducing oversight burden, self-play training), required assumptions (ground truth, judges can discern truth, honest strategies have an advantage), the Discriminator-Critique Gap across generation, discrimination, and critique abilities, empirical results on human and LLM judges (single-turn, two-turn, unbounded interactive debate, consultancy baselines, persuasiveness optimization), and challenges to the truth assumption (obfuscated arguments, motte-and-bailey, ambiguity, and asymmetries)."
title: "Debate"
reading_minutes: 32
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Debate|Debate]]

#### Question: Open
id:: 2db2bf44-f7eb-417b-b40c-b2b98fbfa348
optional:: true
content::
Debate rests on one premise: that a lie is harder to defend than to expose. The section then lists what that needs to be true, and the ways it fails, including obfuscated arguments and motte-and-bailey.

Which did you find more convincing, the premise or the objections?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Debate" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
AI safety via debate: two systems argue for opposing answers in front of a judge, who may be a human or another model, on the premise that defending a lie is harder than refuting one, so truth wins on average even when the judge is weaker than the debaters. The safety case is that it elicits knowledge the model has but would not volunteer, reduces how much the overseer has to do, and can be trained through self-play. It states the assumptions this needs: that there is a ground truth to reach, that judges can tell truth from persuasion, and that honest strategies really do have an advantage. It introduces the discriminator-critique gap, separating a model's ability to generate an answer, to tell a good one from a bad one, and to articulate what is wrong with it. It reports empirical results with human and model judges across single-turn, two-turn and unbounded interactive debate, against consultancy baselines, including what happens when debaters are optimised for persuasiveness. It closes with challenges to the truth assumption: obfuscated arguments, where a debater constructs a case too complex to check; motte-and-bailey, where a strong claim is defended by retreating to a weak one; ambiguity; and asymmetries between the two sides.

Take what they wrote seriously and push on it once. Useful directions: that the premise is an empirical claim about a class of arguments rather than a theorem, so evidence on particular tasks is the right kind of evidence; that optimising debaters for persuasiveness is the case that tests it most directly, since persuasiveness and truth are exactly what the premise says come apart in the honest direction; that obfuscated arguments attack the judge's capacity rather than the honesty asymmetry, so it is a different objection from motte-and-bailey; and that debate needs a ground truth to converge on, which rules out the fuzzy tasks the chapter opened by saying were the problem.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

Do not resolve this. The section reports mixed empirical results and presents the objections as live.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.
