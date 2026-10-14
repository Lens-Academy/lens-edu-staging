---
id: 'bda20de4-2121-4a6f-8b36-b5aee6b4d44e'
title: "D.6.6 Reading guide"
tldr: "Lists the slides and the papers on power-seeking and instrumental convergence that the session reads, with a one-line description of each."
summary_for_tutor: "Reading guide of Iliad worksheet D.6 Instrumental Convergence. Fast track: the session slides. Main content: Turner et al. 2021 (Optimal Policies Tend to Seek Power), Turner and Tadepalli 2022 (Parametrically Retargetable Decision-Makers), Krakovna and Kramar 2023 (trained agents), Omohundro 2008 (Basic AI Drives) and Bostrom 2012 (The Superintelligent Will). The exercise sheet is based mostly on the 2022 paper."
authors:
  - Leon Lang (ILIAD), based on work by Alex Turner et al.
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
upstream_key: "power-seeking#reading-guide"
upstream_fingerprint: "7knIbSCkM/271/1/0b9D0kRG0tI51GjV1xFk20pk29vo2L4u2VxY2hqR2yjY32293C363Ni43Y9D3as83b9F4L2P4RNW4dnB4oVf5Aew5K4E5W665i7C6Oat6lCK6wDT7RPb7bPq7oTK7sZ5"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/agency/power-seeking/#reading-guide"
---

#### Text
content::
\## Reading guide

\### Fast track

Go through [these slides](https://drive.google.com/drive/folders/127bVYqhJPhzA7S71FwTqeyNKKKkjM2NB).

\### Main content

This paper started the work discussed on this day:

::card[[../../turner-optimal-policies-tend-to-seek-power|Optimal Policies Tend to Seek Power — Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, Prasad Tadepalli (NeurIPS 2021)]]

- [Optimal Policies Tend to Seek Power — Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, Prasad Tadepalli (NeurIPS 2021)](https://arxiv.org/abs/1912.01683): The first formal theory proving that in finite MDPs, environmental symmetries make it optimal for most reward functions to seek "POWER" (defined as average optimal value / option-retention), including avoiding shutdown.

Most of the exercise sheet is based on an adapted treatment of the following paper:

::card[[../../turner-parametrically-retargetable-decision-makers-tend-to-seek-power|Parametrically Retargetable Decision-Makers Tend To Seek Power — Alexander Matt Turner & Prasad Tadepalli (NeurIPS 2022)]]

- [Parametrically Retargetable Decision-Makers Tend To Seek Power — Alexander Matt Turner & Prasad Tadepalli (NeurIPS 2022)](https://arxiv.org/abs/2206.13477): Generalizes the 2021 result beyond optimal policies and full observability, showing "retargetability" alone is a sufficient condition for power-seeking tendencies across many decision-making procedures.

You may also be interested in the following paper on which it builds:

::card[[../../krakovna-power-seeking-can-be-probable-and-predictive-for-trained-agents|Power-seeking can be probable and predictive for trained agents — Victoria Krakovna & Janos Kramar (2023)]]

- [Power-seeking can be probable and predictive for trained agents — Victoria Krakovna & Janos Kramar (2023)](https://arxiv.org/abs/2304.06528): Extends the power-seeking theory toward trained (not merely optimal) agents, arguing the incentives still likely hold under assumptions like the agent learning a goal.

Classical philosophical arguments for instrumental convergence and power-seeking tendencies can be found here:

::card[[../../omohundro-the-basic-ai-drives|The Basic AI Drives, Stephen M. Omohundro (2008)]]

::card[[../../bostrom-the-superintelligent-will-motivation-and-instrumental-rationality-in-advanced-artificial-agents|The Superintelligent Will: Motivation and Instrumental Rationality in Advanced Artificial Agents — Nick Bostrom (2012)]]

- [The Basic AI Drives, Stephen M. Omohundro (2008)](https://selfawaresystems.com/wp-content/uploads/2008/01/ai_drives_final.pdf): The founding argument that sufficiently advanced goal-driven systems of any design will develop convergent "drives" (self-improvement, rationality, self-protection, resource acquisition, goal-preservation) unless explicitly counteracted.
- [The Superintelligent Will: Motivation and Instrumental Rationality in Advanced Artificial Agents — Nick Bostrom (2012)](https://nickbostrom.com/superintelligentwill.pdf): Crystallizes the orthogonality thesis (intelligence and final goals vary independently) and the instrumental convergence thesis (a wide range of final goals produce similar intermediary goals).
