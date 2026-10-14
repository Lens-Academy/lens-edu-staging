---
id: '3f2e50a3-d377-4dcf-8e13-29e5917a40d2'
title: "D.4.1.1 Overview and prerequisites"
tldr: "Prerequisites, what the day covers (embedded agency and five research strands), why agent foundations matters for a first critical try, and a one-hour fast-track path."
summary_for_tutor: "Opening of Iliad worksheet D.4.1 Agent Foundations: prerequisites (probability, basic logic and computability, information theory, with four refresher notes), the What/Why/How learning outcomes, a note that the exercise sheet is Section 3 with worked solutions, and the 'Fast-track' list. Key framing: embedded agents break the dualistic picture, and the five strands are consequentialist foundations, Löb's theorem and tiling agents, logical induction, optimization and thermodynamics, and descriptive agent foundations. No exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/agent-foundations/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Prerequisites

- Comfort with elementary discrete probability (random variables, expectation, conditional probability).
- Basic formal logic (provability, quantifiers) and basic computability (programs, halting); needed for the Löb and logical-induction strands.
- Basic information theory (entropy, mutual information); needed for the optimization strand.
- No prior agent-foundations background is assumed; every term used on the day is introduced on the day or in the readings. An introductory overview of the AI alignment problem (as in the intro-alignment module) is helpful context but not required.
- Provided refresher notes cover the gaps: a *probability theory* refresher, a *formal logic* refresher, a *computability theory* refresher, and an *information theory, causality, and statistical mechanics* refresher. Point students at the one matching their weakest area before the day.

:::callout {title="What you'll learn" tone="neutral"}

**(What.)** By the end of the day, students can explain *embedded agency*: why an agent built into the world it acts on (made of the same stuff, smaller than its environment, with no clean input/output boundary, able to model and modify itself) breaks the standard dualistic picture. For each of the day's core research directions (called 'strands') they can state the central problem and a plain-language description of a main result: the complete class theorem (consequentialist foundations), Löb's theorem and the tiling obstacle (self-modification), the logical-induction criterion (logical uncertainty), optimization as local entropy reduction (optimization and thermodynamics), and selection theorems (descriptive agent foundations). They can describe at last one strand in mathematical detail. They can explain how each strand is an offshoot of the central threads *reflective stability* and *embedded agency*.

**(Why.)** Aligning a superintelligence is a problem we may have to get right on the first critical try, reasoning about a system more capable than anything we have observed, before it exists. That rules out pure trial and error and demands concepts that stay meaningful under extreme optimization pressure and self-modification. Agent foundations supplies (or tries to supply) those concepts, and this day gives students a map of some main research directions and how they fit together.

**(How.)** Each student goes deep on one pre-reading track beforehand. A one-hour morning lecture lays out the main threads (reflective stability and embedded agency) and previews every strand. Students then read the shared fundamental readings and, in small groups mixing different tracks, run *cross-pollination* discussions that connect their topics to embedded agency. The afternoon makes a few results rigorous through exercises.

:::

\## 2. Content

Exercise sheet: Section 3 below, with worked solutions. The lecture deck is built from this module's own `slides.tex` and linked at the top of the page.

\### 2.1 Fast-track

To get the core in about an hour, or to catch up after missing the day:

- Read the "Morning lecture" summary below for the unifying spine (reflective stability, embedded agency, the modelling-vs-implementation split).
- Read [Embedded agency](https://www.lesswrong.com/posts/i3BTagvt3HbPMx6PN/embedded-agency-full-text-version) up to and including section 3.3, then section 4.1, and [Why agent foundations](https://www.lesswrong.com/posts/FWvzwCDRgcjb9sigb/why-agent-foundations-an-overly-abstract-explanation) in full.
- Pick the one strand closest to your background from "The five strands" below and read its first (most conceptual) listed reading.
- Skim the takeaways at the end of each strand summary.
