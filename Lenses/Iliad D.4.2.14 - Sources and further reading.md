---
id: '2686219d-a7db-4ebe-9f7b-7f4ef607797a'
title: "D.4.2.14 Sources and further reading"
tldr: "The list of sources the notes draw on, each with a note on what it contributes."
summary_for_tutor: "The 'Sources and further reading' list of Iliad worksheet D.4.2: Flint on the ground of optimization, Yudkowsky on measuring optimization power, Wolpert and Macready and Dennett on observer-relative intelligence, Wentworth's generalized heat engine, Harwood and Altair on the Touchette-Lloyd theorem, Daniel C and Ebtekar on three types of optimization, and Ebtekar and Hutter on algorithmic thermodynamics. No exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Sources and further reading

These notes integrate the following sources, listed in approximately the order in which their material appears.

- A. Flint, *The ground of optimization*, AI Alignment Forum, 2020. A complementary descriptive treatment of optimization in terms of *optimizing systems* (a broad basin of attraction, a narrow target set, and robustness to perturbation), together with a finer-grained comparison of such systems along the axes of robustness, duality, and retargetability. Recommended as further reading on the behavioral characterization of Section 3.
- E. Yudkowsky, *Measuring optimization power*, LessWrong, 2008. A quantitative proposal that measures optimization by the improbability of the achieved outcome under random rearrangement, which may be read alongside the entropy-reduction measure of Section 3.3.
- D. H. Wolpert and W. G. Macready, *No free lunch theorems for optimization*, IEEE Transactions on Evolutionary Computation 1(1)\:67–82, 1997; and D. C. Dennett, *The Intentional Stance*, MIT Press, 1987. The two articulations of the observer-relative view of intelligence and agency that Section 3.5 presents and addresses: no optimizer is universally competent (competence is relative to a problem class), and agency is a predictive stance adopted by an observer rather than an intrinsic property.
- J. Wentworth, *Generalized heat engine*, LessWrong, 2020. The source for the entirety of Appendix A, including the designer's viewpoint, the biased-coin world, work extraction as compression, and the two-bath engine. His decomposition of expected utility maximization (Remark 3.1) appears in *Utility maximization = description length minimization*, LessWrong, 2021.
- A. Harwood and A. Altair, *When bits of optimization imply bits of modeling: the Touchette–Lloyd theorem*, LessWrong, 2025. The pedagogical source for Appendix B, including the guessing game, the blind and sighted vocabulary, the headphone analogy, and the caveats concerning insufficiency. The underlying theorem is due to H. Touchette and S. Lloyd, *Information-theoretic approach to the study of control systems*, Physica A 331\:140–172, 2004 (Theorem 10), with antecedents in their 2000 paper *Information-theoretic limits of control* and in Lloyd's 1989 work on Maxwell's demon.
- Daniel C and A. Ebtekar, *Algorithmic thermodynamics and three types of optimization*, AI Alignment Forum, 2025. The central organizing source for these notes, providing the characterization of optimizers through the convergent attractors they create and the information-theoretic argument for attending to such attractors irrespective of one's goals (Section 3), the three types of optimization (Section 5), the argument that entropy should objectively measure optimization capacity (Section 6), the algorithmic refinements of the three types, and the embedded-agency synthesis (Section 8).
- A. Ebtekar and M. Hutter, *Foundations of algorithmic thermodynamics*, Physical Review E, 2025 (arXiv\:2308.06927). The formal backbone of Sections 4 and 7, supplying Markovian coarse-grainings and the multibaker construction, Gacs' coarse-grained algorithmic entropy, Levin's conservation of randomness and the algorithmic second law with its $$K(t-s) + \log\frac{1}{\delta}$$ allowance, the exact analysis of Maxwell's demon including the partial-measurement bound (1), and the ensemble-versus-state comparison of Section 6 (including the robot-battery and bookshelf examples and Zurek's identity).

For the broader agent foundations context assumed in Section 1 (true names and Goodhart's law, reflective stability, embedded agency, selection theorems), we refer the reader to the Agent Foundations slide deck accompanying this module.
