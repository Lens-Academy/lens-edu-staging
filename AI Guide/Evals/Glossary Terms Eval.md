---
tags:
  - validator-ignore
---
# Glossary Terms Eval

**Binary question:** Should this lens list this term in `glossary_terms`?

The standard is "Which words to list" in [[../Writing Glossary Entries]]: five rules, and "when unsure, leave it out". A human label is the answer a course author gives after reading the lens page. An AI run is good when it lists what an author would list and skips what an author would skip.

## How to run it

1. Give a judge the rules, the course, the lens's place in the course, and the text around the term's first use on the page. Do not show it this file's labels.
2. Record its verdict in a new column. Compare it with the **Human** column.
3. Report two numbers: of the terms the humans list, how many the judge lists (recall); of the terms the judge lists, how many the humans list (precision). Agreement over all rows says little, because most rows are clear skips.

## The labelled set

24 (lens, term) pairs, drawn at random from the candidates of AI Futures (AIF) and AI Risk Fundamentals (AIRF): every glossary term that appears on a lens page. "First use" is the text that would get the line.

**Human: to fill in.** Write `list` or `skip`, and a reason when you disagree with both AI columns.

| # | Course | Lens | Term | First use | Fill-in run | Blind judge | Human |
|---|---|---|---|---|---|---|---|
| 1 | AIF 2/36 | [[../../Lenses/AIF - Fun with +12 OOMs of Compute\|Fun with +12 OOMs of Compute]] | AI safety | AI safety | skip | skip |  |
| 2 | AIF 3/36 | [[../../Lenses/AIF - How Long A Task\|How Long A Task]] | Agent | agents | skip | skip |  |
| 3 | AIF 4/36 | [[../../Lenses/AIF - What a Curve Licenses\|What a Curve Licenses]] | Compute | compute | skip | skip |  |
| 4 | AIF 5/36 | [[../../Lenses/AIF2 - Scaling Laws\|Scaling Laws]] | Google DeepMind | DeepMind | skip | skip |  |
| 5 | AIF 6/36 | [[../../Lenses/AIF - Can AI Scaling Continue Through 2030\|Can AI Scaling Continue Through 2030?]] | Large language model | LLMs | skip | skip |  |
| 6 | AIF 17/36 | [[../../Lenses/U3 - Losing It Gradually\|Losing It Gradually]] | Dario Amodei | Amodei | skip | skip |  |
| 7 | AIF 19/36 | [[../../Lenses/U3 - The Case Against Control\|The Case Against Control]] | Agent | agent | skip | skip |  |
| 8 | AIF 19/36 | [[../../Lenses/U3 - The Case Against Control\|The Case Against Control]] | AGI | AGI | skip | skip |  |
| 9 | AIF 24/36 | [[../../Lenses/U2 - AI 2040 First Three Years\|AI 2040: First Three Years]] | Intelligence explosion | intelligence explosion | skip | skip |  |
| 10 | AIF 25/36 | [[../../Lenses/U2 - Selective Optimism\|Selective Optimism: a critique of AI 2040]] | Takeoff speed | takeoff | skip | skip |  |
| 11 | AIF 27/36 | [[../../Lenses/U4 - The Manhattan Question\|The Manhattan Question]] | Compute | compute | skip | skip |  |
| 12 | AIF 32/36 | [[../../Lenses/U5 - The Handoff\|The Handoff]] | Whole brain emulation | whole brain emulation | skip | list |  |
| 13 | AIRF 15/221 | [[../../Lenses/IABIED - QA - Is Intelligence Meaningful\|Is intelligence a meaningful concept?]] | Superintelligence | superintelligent | skip | skip |  |
| 14 | AIRF 29/221 | [[../../Lenses/IABIED - QA - Intelligence as Prediction and Steering\|More on Intelligence as Prediction and Steering]] | Utility function | utility function | skip | skip |  |
| 15 | AIRF 32/221 | [[../../Lenses/IABIED - QA - Special Behavior from Mundane Parts\|Special Behavior is Built out of Mundane Parts]] | Compute | compute | skip | skip |  |
| 16 | AIRF 39/221 | [[../../Lenses/IABIED - QA - Do Experts Understand AIs\|Do experts understand what's going on inside AIs?]] | Eliezer Yudkowsky | Yudkowsky | skip | skip |  |
| 17 | AIRF 40/221 | [[../../Lenses/IABIED - QA - Intelligence Understandable\|Is intelligence understandable in principle?]] | Large language model | LLMs | skip | skip |  |
| 18 | AIRF 52/221 | [[../../Lenses/IABIED - QA - Knowledge of LLMs\|What Good Does Knowledge of LLMs Do?]] | Eliezer Yudkowsky | Yudkowsky | skip | skip |  |
| 19 | AIRF 81/221 | [[../../Lenses/IABIED - QA - Brittle Unpredictable Proxies\|Brittle Unpredictable Proxies]] | Superintelligence | superintelligence | skip | skip |  |
| 20 | AIRF 83/221 | [[../../Lenses/IABIED - QA - AI-Induced Psychosis\|AI-Induced Psychosis]] | OpenAI | OpenAI | skip | skip |  |
| 21 | AIRF 98/221 | [[../../Lenses/IABIED - QA - Human Data Means Human Concepts\|If AIs are trained on human data, doesn't that make them likelier to care about human concepts?]] | Superintelligence | superintelligence | skip | skip |  |
| 22 | AIRF 185/221 | [[../../Lenses/IABIED - QA - Daily Life Believing This\|What does it do to your daily life to believe all of this?]] | Eliezer Yudkowsky | Yudkowsky | skip | skip |  |
| 23 | AIRF 187/221 | [[../../Lenses/IABIED - QA - Fear-Mongering by AI Leaders\|Isn't this all just fear-mongering by AI leaders?]] | Dario Amodei | Dario Amodei | skip | list |  |
| 24 | AIRF 190/221 | [[../../Lenses/IABIED - QA - Telling AI Companies No\|Workable Plans Will Involve Telling AI Companies No]] | Sam Altman | Sam Altman | skip | skip |  |

## Run 2026-09-26

- **Fill-in run:** one AI per course went through every lens in order and chose the lists (AIF: 12 terms on 8 of 36 lenses; AIRF: 14 terms on 14 of 221 lenses). These became the suggestions on the lens files.
- **Blind judge:** a second AI judged the 24 pairs above with the rules and the candidate list, without the fill-in results.
- **Result:** the two agree on 22 of 24 pairs. Both disagreements are the judge's only two `list` verdicts (rows for "Whole brain emulation" and "Dario Amodei"); the fill-in run lists none of the 24. So on the decisions that matter, the two AIs have not yet agreed once. The set has too few terms that should be listed to measure this step.
- **Assumption to check:** the AIRF run counted a book chapter assigned by an earlier required lens as explaining the terms it defines (rule 2). This is why "Superintelligence" and "LLM" are never listed in AIRF.

**Next:** add human labels to the table, and add the 26 listed terms from the suggestions as rows, so that precision can be measured.
