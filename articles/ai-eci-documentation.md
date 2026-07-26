---
title: "ECI Documentation"
author:
  - "Epoch AI"
source_url: "https://epoch.ai/data/eci-documentation"
published: 2025-12-01 {>>{"author":"Elias's AI","timestamp":1783847958515}@@`published` is required by the schema; the doc page itself is undated, so this uses the ECI companion paper date (arXiv 2512.00193, Dec 2025) as the closest honest publication date — per Elias<<}
created: 2026-07-02 {>>{"author":"Elias's AI","timestamp":1783843125501}@@removed published field: the source page shows no publication date, and the previous value was the import date shown to learners as a byline<<}
accessed: 2026-07-02
description: "Documentation for the Epoch Capabilities Index (ECI), a composite metric that combines scores from many AI benchmarks into a single capability scale, including the domain-specific ECI."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Overview

The **Epoch Capabilities Index (ECI)** combines scores from many different AI benchmarks into a single “general capability” scale, allowing comparisons between models even over timespans long enough for single benchmarks to reach saturation.

ECI is a composite metric which uses scores from over 50 distinct benchmarks to generate a single, general capability scale. At a high level, ECI stitches together its component benchmarks, determining their relative difficulty by making comparisons wherever models are evaluated on multiple benchmarks. Individual models obtain higher ECI scores if they perform better on harder benchmarks.

We give an overview of our methodology in the [Methodology](https://epoch.ai/data/eci-documentation/methodology) section; further technical details are available in our [paper](https://www.arxiv.org/abs/2512.00193), _A Rosetta Stone for AI Benchmarks_, which was funded by Google DeepMind, and written in collaboration with researchers from their AGI Safety & Alignment team. However, the ECI is an independent Epoch AI product that Epoch has full rights over.

Code for the ECI is available in a public repository [here](https://github.com/epoch-research/eci-public).

The interactive ECI leaderboard is available at [epoch.ai/eci](https://epoch.ai/eci). For domain-specific ECI scores covering software engineering and math, see the [Domain-specific ECI](https://epoch.ai/data/eci-documentation/domain-specific-eci) section.

[Methodology](https://epoch.ai/data/eci-documentation/methodology)
