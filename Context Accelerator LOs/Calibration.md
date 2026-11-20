---
id: 40c2b184-1412-4508-913e-a003b54b03ec
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means for probability estimates to be well calibrated, spot overconfidence and underconfidence in a track record, compare forecasters by Brier score, and check whether you actually know a claim or have only heard it.

## Requires
- [[Subjective probability]]

## Helpful first

## Why it matters
Claims about AI often come with probabilities attached, from a "10% chance of catastrophe" to dates for human-level AI. A forecaster's calibration record is one guide to how much weight their numbers deserve. Checking your own calibration stops you passing on confident claims you have only heard repeated.

## Lenses
- [Efforts to Improve the Accuracy of Our Judgments and Forecasts (Open Philanthropy, via EA Forum)](https://forum.effectivealtruism.org/posts/pnpnqA4hijnr59p7d/efforts-to-improve-the-accuracy-of-our-judgments-and): What calibration means, why untrained people are usually overconfident, how a few hours of scored practice fixes it, and why always saying "50%" is calibrated but uninformative; read section 1, "Calibration training" (October 2016).
- [How to Make Better Predictions (Clearer Thinking)](https://www.clearerthinking.org/post/2019/10/16/practice-making-accurate-predictions-with-our-new-tool): Thinking in ranges, why ranges that are too narrow mean overconfidence, and a quick self-test with ten 90% estimates; read the introduction and tips 1 and 2 (October 2019, updated December 2022).
- [What Is a Brier Score? (Good Judgment Open FAQ)](https://gjopen.com/faq): A plain definition of the Brier score as the squared error of a forecast, with worked examples, and why a lower score is better, "like in golf"; read the Brier score entry (current).
- [How Accurate Do Long-Range Forecasts Tend to Be? (Open Philanthropy)](https://www.openphilanthropy.org/?p=3360): Why forecasts 10 or more years out are hard to score, and why the Good Judgment Project's record, mostly on questions 1 to 6 months out, says little about them; read the introduction and section 1.7.1, "Tetlock, long-range forecasting, and relevance" (2019, updated March 2023).

## Tests

#### Question: FillBlank
id:: 88fca7c0-ab43-4e19-b6bf-34f6551c06e4
content:: A forecaster is well {{calibrated}} if, of all the claims they gave a 70% probability, about 70% turn out to be true.

#### Question: Choice
id:: 316229fb-f5e5-4265-8e36-6a6c3fc7f030
content:: Over several years, the events a forecaster gave a 60% probability happened 85% of the time. What does this suggest about their 60% forecasts?
options::
- [x] They were underconfident and could have given higher probabilities
- They were overconfident and should have given lower probabilities
- They were well calibrated, since most of the events happened
- They were uninformative, since 60% is close to a coin flip
shuffle:: true

#### Question: Choice
id:: 3bf91b4a-c2c6-4a70-aca1-2134fb3ff101
content:: You give 90% confidence ranges for 20 quantities, such as city populations. 11 of the 20 ranges contain the true value. What does this most likely show?
options::
- [x] Your ranges were too narrow, so you were overconfident
- Your ranges were too wide, so you were underconfident
- You were well calibrated but unlucky on a few ranges
- Your calibration can't be judged from range estimates
shuffle:: true

#### Question: Choice
id:: b8a84bc4-24c8-4446-9483-d6b5901c2046
content:: In a town where it rains on 30% of days, a forecaster says "30% chance of rain" every day. Which statement about this forecaster is correct?
options::
- [x] They are well calibrated but tell you little about any given day
- They are badly calibrated because their forecast never changes
- They are overconfident because they ignore each day's weather
- They are well calibrated and as useful as a forecaster can be
shuffle:: true

#### Question: Choice
id:: dae92487-135d-4180-ba02-84ec5739cccb
content:: Two forecasters answered the same 100 probability questions. Forecaster A has an average Brier score of 0.12 and Forecaster B has 0.25. Who did better?
options::
- [x] Forecaster A
- Forecaster B
- It can't be told without knowing how many each got right
shuffle:: true

#### Question: Choice
id:: 187faeef-a9d6-4fa9-85b1-041fb23fd38f
content:: In studies where people state how confident they are in their own answers, which calibration failure is most common?
options::
- [x] Being right less often than their stated confidence
- Being right more often than their stated confidence
- Errors in both directions that leave them calibrated on average
- Overconfidence on easy questions, good calibration on hard ones
shuffle:: true

#### Question: Choice
id:: d7a5c239-1eeb-481f-ba32-603af037ea2d
content:: You have heard a figure about AI researchers' risk estimates from a dozen people, all of whom got it from the same survey. Compared with reading the survey once yourself, how much should the repetitions raise your confidence that the figure is right?
options::
- [x] Hardly at all, since every repetition traces back to one survey
- A good deal, since each person who repeated it is another source
- Somewhat, since people usually check a figure before repeating it
- Fully, since a figure repeated this widely is rarely wrong
shuffle:: true

#### Question: Choice
id:: f23d195a-53ca-49da-9e6e-7d74e1ee4e14
content:: Which habit most directly improves your calibration over time?
options::
- [x] Recording your forecasts and scoring them once outcomes are known
- Reading expert opinion before making each forecast
- Giving ranges instead of single probabilities
- Using words like "likely" instead of numbers
shuffle:: true

#### Question: Open
id:: 3cbda061-0aa4-484a-9f89-199d62aa6d53
content:: A forecaster gave an 80% chance that a bill would pass, and it failed. A critic says this proves the forecaster is badly calibrated. Why is the critic's reasoning weak?
assessment-instructions:: Score out of 100. 100 for saying calibration is judged across many forecasts: an 80% forecast should fail about 1 time in 5, so one miss shows little. 50 for saying the forecaster may just have been unlucky, without explaining why one result can't settle calibration.

#### Question: Open
id:: 3c2ebc10-a865-49f2-b0a9-14850d7e5622
content:: Why is a forecaster's good track record on one-year questions only limited evidence about how well they forecast whether AI will cause a catastrophe, which might come within a few years or be decades away?
assessment-instructions:: Score out of 100. 100 for any one of: such forecasts can't be scored until the outcome arrives, so that skill is untested; the questions differ in kind (unprecedented events, little data, no feedback), so skill may not carry over. 50 for "the future is uncertain" without saying why. Don't mark down noting the record is still some evidence.

#### Question: Open
id:: 6a428f02-5a86-4df9-97b2-7ddd6c6c0425
content:: Give one test you can apply to tell whether you know a claim about AI or have only heard it.
assessment-instructions:: Score out of 100. 100 for any one of: you can explain the evidence or reasoning behind it; you can say where it came from and judge that source; you can say what would change your mind; you can state it precisely (who said it, what number). 0 for "how sure it feels" or "how often I've heard it".
