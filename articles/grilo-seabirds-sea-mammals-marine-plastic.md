---
title: "The Number of Seabirds and Sea Mammals Killed by Marine Plastic Pollution is Quite Small Relative to the Catch of Fish"
source_url: https://forum.effectivealtruism.org/posts/tFfWpsEcCCKAXr8Zg/the-number-of-seabirds-and-sea-mammals-killed-by-marine
author:
  - Vasco Grilo
published: 2022-04-19
created: 2026-05-28
description: A worked Fermi estimate comparing deaths from marine plastic pollution (seabirds and sea mammals) to the annual wild fish catch — illustrating how quantitative reasoning can reveal surprising differences in scale.
tags:
  - ea-intro-program
  - effective-altruism
  - fermi-estimate
  - animal-welfare
  - cause-prioritization
  - work-in-progress
---

%%
Add discussion note here:

...

%%

# The Number of Seabirds and Sea Mammals Killed by Marine Plastic Pollution is Quite Small Relative to the Catch of Fish

Disclaimer: plastic pollution may well kill way more animals besides seabirds and sea mammals. There [are](https://forum.effectivealtruism.org/posts/ayxasxhHWTvf6r5BF/scale-of-the-welfare-of-various-animal-populations) 6.20*10^14 wild fish and 1.00*10^20 wild marine [arthropods](https://en.wikipedia.org/wiki/Arthropod), but only 6.75*10^11 wild mammals.

### Summary

- 1 kg of plastic is emitted to the ocean per capita per year[^1].
- 0.0001 seabirds and 0.00001 sea mammals are killed by marine plastic pollution per capita per year.
- 200 wild fish are caught per capita per year.
- The catch of wild fish is 2 M times as large as the number of seabirds, and 20 M times as large as the number of sea mammals killed by marine plastic pollution.

The data and calculations are presented below.

### Data

- The plastic emitted to the ocean in 2010 was 8 million tonnes according to [OWID](https://ourworldindata.org/plastic-pollution) (PEO = 8 [M](https://en.wikipedia.org/wiki/Metric_prefix#List_of_SI_prefixes)[t](https://en.wikipedia.org/wiki/Tonne)).
- The world population in 2010 was 6.92 billion according to [The World Bank](https://data.worldbank.org/indicator/SP.POP.TOTL) (WP = 6.92 [G](https://en.wikipedia.org/wiki/Metric_prefix#List_of_SI_prefixes)).
- Marine plastic debris kills up to 1 million seabirds and 100 thousand sea mammals each year according to the [United Nations](https://sustainabledevelopment.un.org/content/documents/Ocean_Factsheet_Pollution.pdf) (SB = 1 M, and SM = 100 k).
- The catch of wild fish is 0.97 to 2.7 trillion/year according to [fishcount.org](http://www.fishcount.org.uk/published/std/fishcountchapter19.pdf) (WFL = 0.97 [T](https://en.wikipedia.org/wiki/Metric_prefix#List_of_SI_prefixes)/year to WFH = 2.7 T/year).

### Calculations

- Plastic emitted to the ocean per capita in 2010 (PEOpC): PEO / WP = 8 Gkg / (6.92 G) = **1.16 kg**.
- Plastic emitted to the ocean to cause one death of a seabird (PEOpDSB): PEO / SB = 8 Mt / (1 M) = 8 t.
- Plastic emitted to the ocean to cause one death of a sea mammal (PEOpDSM): PEO / SM = 8 Mt / (0.1 M) = 80 t.
- Seabirds killed by plastic marine pollution in 2010, per capita (DSBpC): PEOpC / PEOpDSB = 1.16 / (8 k) = **145** [**μ**](https://en.wikipedia.org/wiki/Metric_prefix#List_of_SI_prefixes) (145 seabirds killed per million people).
- Sea mammals killed by plastic marine pollution in 2010, per capita (DSMpC): PEOpC / PEOpDSM = 1.16 / (80 k) = **14.5 μ** (14.5 sea mammals killed per million people).
- Wild fish caught per year (WF): (WFL * WFH)^0.5 = (0.97 * 2.7)^0.5 T = 1.62 T.
- Catch of wild fish per capita per year (WFpC): WF / WP = 1.62 T / (6.92 G) = **234**.
- Ratio between the catch of wild fish and the number of seabirds killed by marine plastic pollution: WFpC / DSBpC = 234 / (145 μ) = **1.62 M**.
- Ratio between the catch of wild fish and the number of sea mammals killed by marine plastic pollution: WFpC / DSMpC = 234 / (14.5 μ) = **16.2 M**.

*This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).*

[^1]: 1 kg is the global value, and it is much smaller for many countries. Most of the countries emit less than 0.1 % of the plastic waste to the ocean (see [this](https://ourworldindata.org/grapher/share-of-global-plastic-waste-emitted-to-the-ocean?country=Africa~Asia~Europe~South+America~North+America~Oceania) map), although [3 %](https://ourworldindata.org/plastic-pollution#where-does-our-plastic-accumulate-in-the-ocean-and-what-does-that-mean-for-the-future) of the global plastic waste is emitted to the ocean.

{>>TODO: Licensed content<<}
