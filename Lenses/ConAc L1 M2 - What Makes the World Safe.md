---
id: '329a7361-410c-45b9-a8af-ee656022b7e2'
title: "What Makes the World Safe?"
tags:
  - wip
---
#### Text
content::
When we talk about solving AI safety, what state of the world do we have in mind? One way to distinguish possible answers is by looking at where safety comes from.

**Safety by design.** We develop AI systems whose properties make them safe. This might involve aligning their objectives with human intentions or designing architectures that avoid certain sources of risk altogether.

**Safety through control.** AI systems may exhibit dangerous behaviour, but we have effective mechanisms for preventing that behaviour from causing unacceptable harm. This is the premise of [AI Control](https://arxiv.org/abs/2312.06942) research.

**Safety through resilience.** AI-related harms may occur, but society has the capacity to withstand them, adapt and recover. Examples include strengthening public health infrastructure, developing defensive cybersecurity capabilities and protecting the integrity of information environments.

**Safety through prevention.** AI systems whose risks cannot be adequately managed are never developed or deployed. A temporary pause in AI development could also give other safety measures time to mature.

These approaches can complement each other. The [2026 Singapore Consensus on Global AI Safety Research Priorities](https://arxiv.org/abs/2608.14611), for example, adopts a defence-in-depth framework in which safer system design, control mechanisms and societal resilience provide successive layers of protection.

\### What Future Are We Trying to Preserve or Enable?

Imagine a future in which humanity survives the transition to superintelligence. What else would need to be true for us to consider this a success?

Different research programmes are motivated by different desiderata for the future.

- **Human survival and continued civilisation.** Humanity survives the development of advanced AI and retains the possibility of long-term civilisational progress. The rationale for prioritising this objective is explored in [Existential Risk Prevention as Global Priority](https://www.oxfordmartin.ox.ac.uk/publications/existential-risk-prevention-as-global-priority).
- **Preservation of human agency.** Humans retain meaningful influence over their lives, institutions and collective future. [Gradual Disempowerment](https://www.alignmentforum.org/posts/pZhEQieM9otKXhxmd/gradual-disempowerment-systemic-existential-risks-from) (2025) examines how this influence could be lost even if individual AI systems reliably followed their designers' intentions.
- **Shared prosperity and flourishing.** Advances in AI translate into improvements in wellbeing, scientific progress and opportunities for meaningful human activity. [Gradual Paths to Collective Flourishing](https://www.alignmentforum.org/posts/mtASw9zpnKz4noLFA/gradual-paths-to-collective-flourishing) (2026) explores possible paths towards such a future.
- **The welfare of digital minds.** If artificial systems acquire morally relevant forms of subjective experience, their wellbeing may become an important property of a desirable future. [Digital Minds: Importance and Key Research Questions](https://forum.effectivealtruism.org/posts/HZtBJi4fv5ftEAj9p/digital-minds-importance-and-key-research-questions) explores the implications of this possibility for research priorities.

These desiderata are largely compatible, but achieving one does not guarantee achieving the others. A civilisation could become extraordinarily prosperous while humans gradually lose their ability to determine its trajectory.

The properties of the future we seek to preserve or enable determine which changes we consider desirable and, consequently, which interventions we consider worth pursuing.

\### How Might the Field Arrive at a Solution?

What would the research process that eventually solves AI alignment look like?

One possibility is that we are missing a handful of fundamental insights. Once discovered, they could substantially change our understanding of the problem and make a solution tractable. Richard Ngo explores this model of scientific progress in [Intuitions About Solving Hard Problems](https://www.lesswrong.com/posts/GkXKvkLAcTm5ackCq/intuitions-about-solving-hard-problems) (2022):

#### Article
source:: [[../articles/ngo-intuitions-about-solving-hard-problems]]
from:: Here’s a heuristic which plays an important role in my reasoning about solving hard scientific problems
to:: or formal logic, where I’m not sure if there were any big insights that could be grasped in advance of actually seeing the formalisms in action.

#### Text
content::
Another possibility is that a solution will emerge from the accumulation and integration of many smaller discoveries. This requires a research ecosystem in which scientists can independently produce results, assess their validity and build upon each other's work.

In [Towards Alignment Auditing as a Numbers-Go-Up Science](https://www.lesswrong.com/posts/bGYQgBPEyHidnZCdE/towards-alignment-auditing-as-a-numbers-go-up-science) (2025), Sam Marks identifies a problem with the current organisation of alignment research:

#### Article
source:: [[../articles/marks-towards-alignment-auditing-as-a-numbers-go-up-science]]
from:: A major challenge in alignment research is that we don’t know what we’re doing or how to tell if it’s working.
to:: Making progress on a problem without a trusted feedback signal is a perilous thing to try!

#### Text
content::
Developing shared concepts, reliable research methods and meaningful criteria for progress could allow considerably more researchers to contribute productively. [Open Problems Create Paradigms](https://www.lesswrong.com/posts/whXFkYEDiDk8tSBqH/open-problems-create-paradigms) (2020) and [We Need a Science of Evals](https://www.alignmentforum.org/posts/fnc6Sgt3CGCdFmmgX/we-need-a-science-of-evals) (2024) explore how some of these conditions might be established.

These models of progress have different implications for what constitutes a valuable contribution to AI safety. The first gives us reasons to invest in identifying exceptional researchers and enabling them to pursue difficult problems. The second also gives us reasons to invest in replication, research synthesis, methodology, standardisation and scientific coordination. And again: they can and probably should coexist.

**We are trying to solve problems before we can fully observe them.** In [On Solving Problems Before They Appear](https://www.alignmentforum.org/posts/FQqcejhNWGG8vHDch/on-solving-problems-before-they-appear-the-weird) (2021), Adam Shimi describes the peculiar epistemological position of alignment researchers:

> Alignment research aims at solving a never-before-seen problem caused by a technology that doesn't exist yet.

Although contemporary AI systems have made many alignment problems accessible to empirical investigation, the question of how far we can extrapolate these findings remains open.

**Some failures are irreversible.** Much of engineering progress relies on building systems, observing their failures and modifying their design accordingly. In his 2002 paper [Existential Risks](https://nickbostrom.com/papers/existential-risks/), Nick Bostrom explains why this approach has fundamental limitations when applied to existential threats:

> Our approach to existential risks cannot be one of trial-and-error.

We need ways of obtaining sufficiently informative evidence without exposing ourselves to the very outcomes we seek to prevent.

**Much of the field lacks shared scientific foundations.** In mature disciplines, researchers can often rely on established concepts, measurement procedures and criteria for evaluating results. Within AI safety, the validity of these very instruments is frequently a subject of research. Consider the methodological problems discussed in [We Need a Science of Evals](https://www.alignmentforum.org/posts/fnc6Sgt3CGCdFmmgX/we-need-a-science-of-evals) (2024).

Without shared foundations, accumulating individual research results does not necessarily lead to a corresponding accumulation of collective understanding.

**Scientific progress does not automatically translate into safety.** A successful research result may require adoption by AI developers, changes in institutional practices or international cooperation before it can affect the risk it was intended to address. In [Legible vs. Illegible AI Safety Problems](https://www.alignmentforum.org/posts/PMc65HgRFvBimEpmJ/legible-vs-illegible-ai-safety-problems), Wei Dai discusses the difficulties of getting solutions implemented when the problem itself remains poorly understood by decision-makers.

Together, these features make it difficult to establish whether a particular research activity is bringing us closer to a desirable outcome. We often need to reconstruct and examine the reasoning connecting a proposed intervention to its intended consequences, including assumptions that would be taken for granted in more mature fields.

One framework for doing this is a Theory of Change.
