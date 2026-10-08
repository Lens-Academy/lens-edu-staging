---
id: 'b4b046a8-995e-4f9a-ab66-720e7b8ea770'
title: "D.4.1.2 Morning lecture and fundamental reading"
tldr: "The morning lecture on reflective stability, robust concepts, the modelling versus implementation pathways and embedded agency, plus four fundamental readings."
summary_for_tutor: "Sections 2.2 (intro), 2.2.1 'Morning lecture' and 2.2.2 'Fundamental reading' of Iliad worksheet D.4.1 Agent Foundations. Lecture points: why agent foundations (the first critical try), reflective stability, robust concepts or 'true names' (Goodhart's law), Wyeth's two pathways of impact (modelling and implementation), and dualistic versus embedded agents. Four assigned readings follow: Embedded agency, Why agent foundations, Reflectively consistent degree of freedom, and General purpose search. No exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/agent-foundations/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.2 Main content

Agent foundations is not one theory but several research strands (research directions), each attacking a different facet of the same problem: how to reason about, and build, *stable* agents that are *embedded* in the world they act on. This day is organized around five such strands (consequentialist foundations; Löb's theorem and tiling agents; logical induction; optimization and thermodynamics; descriptive agent foundations). Each student pre-reads one strand in depth before the day; the morning lecture supplies the spine that connects them; the shared fundamental readings and a small-group discussion knit them into a single picture; and an exercise session makes a few of the results rigorous.

Read top to bottom, this section runs: the unifying threads (the morning lecture), then the fundamental readings that give a bird's-eye view, then the five strands each with its readings, then the cross-pollination discussion, the exercises, and a self-check.

\#### 2.2.1 Morning lecture

- **Why agent foundations.** We may need key safety properties to hold on the first critical try, for an agent far more capable than any we can study directly. Agent foundations looks for the properties capable agents share *in general*, so we can reason about them in advance.
- **Reflective stability.** A safety property only matters if it survives the agent's own self-modification: a capable agent may rewrite its code, build a more capable successor, or revise its world model. A property is *reflectively stable* if it is invariant under all of these. Working assumption: under enough optimization pressure, a property persists only if there is some reason it must. Reflective stability is the thread running through every strand.
- **Robust concepts ("true names").** Goodhart's law says a proxy that becomes a target stops measuring what we want. So a theory of agency must be built from concepts that do not break under optimization, the "true names" of optimization, goals, world models, and embeddedness.
- **Two pathways of impact (following C. Wyeth).** *Modelling*: build an abstract mathematical model of an idealised capable agent and use it to show why a given alignment proposal would fail. *Implementation*: develop a theory far enough to build and inspect an actual system, often favouring a modular architecture (a separate, inspectable world model, planner, and goal) so each part can be checked.
- **Dualistic vs embedded agents.** The standard picture (an agent with clean I/O, "larger than" and "outside" its environment, holding a full world model in its head) is dualistic. A real agent is *embedded*: part of the world, made of the same pieces, smaller than its environment, with no crisp boundary, and able to be copied, modified, or to model itself. Embeddedness is what makes self-improvement, multi-agent reasoning about copies, and self-reference unavoidable, and it is what the rest of the day is about.

\#### 2.2.2 Fundamental reading

::card[[../Lenses/garrabrant+demski--embedded-agency|Embedded agency]]

> read up to and including section 3.3, then section 4.1. The canonical statement of the embedded-agency problem cluster (the Alexei/Emmy framing the lecture uses).

::card[[../Lenses/johnswentworth-why-agent-foundations-an-overly-abstract-explanation|Why agent foundations]]

> read entirely. Why this abstract, theory-first approach is worth pursuing.

- [Reflectively consistent degree of freedom](https://www.lesswrong.com/w/reflectively-consistent-degree-of-freedom): read entirely. The precise notion behind a property an agent would not self-modify away, which is the day's recurring theme of reflective stability.
- [General purpose search](https://www.lesswrong.com/posts/6mysMAqvo9giHC4iX/what-s-general-purpose-search-and-why-might-we-expect-to-see): read entirely. Why a capable mind plausibly contains a retargetable search process.
