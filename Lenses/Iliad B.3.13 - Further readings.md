---
id: '94c7cf46-4a2e-49bf-bcad-caef2fd07b0e'
title: "B.3.13 Further readings"
tldr: "Points to other introductions to singular learning theory, recent research on singular deep learning, and a reference list."
summary_for_tutor: "This is Section 5 (Further readings) and the references of Iliad worksheet B.3 Singular Learning Theory. It lists other introductions and monographs (Watanabe's grey and green books), and surveys work on estimating degeneracy, Bayesian phase transitions and stagewise development, interpretability tools (refined LLCs, susceptibilities, Bayesian influence functions) and foundations. It contains no exercises."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Further readings

We conclude by providing several pointers to additional literature and resources for those interested in investigating singular learning theory (SLT) in more detail.

\### 5.1 Other introductions to singular learning theory

For alternative introductions to SLT, see the following.

- Wei et al. 2023 "Deep Learning is Singular, and That's Good," a technical position paper surveying some implications of SLT for deep learning.
- Carroll 2023 "Distilling singular learning theory," a LessWrong sequence introducing Watanabe's free energy formula and discussing an example of a Bayesian phase transition in a small neural network.
- Lecture recordings from the *SLT & Alignment Summit, 2023*. In particular:
  - See the "SLT Low Road" lectures (Lau & Chen 2023) for an outline of the derivation of Watanabe's free energy formula.
  - See the "SLT High Road" lectures (Murfet & Carroll 2023) for a discussion of the free energy formula's implications including Bayesian phase transitions.
- Lau 2025, Chapter 2, "Singular Learning Theory Background", a self-contained technical introduction to the main results of SLT with illustrative examples.

See Furman 2024 for a list of mathematical exercises. There is some overlap with exercises included in this tutorial, but there are also several additional exercises.

For a more in-depth introduction to the theoretical foundations of SLT, see Watanabe's two research monographs.

- Watanabe 2009 "Algebraic Geometry and Statistical Learning Theory," colloquially known as "the grey book." Derives the free energy formula in the realisable case along with other results concerning generalisation properties of Bayesian inference and maximum a posteriori inference.
- Watanabe 2018 "Mathematical Theory of Bayesian Statistics," colloquially known as "the green book." An alternative presentation of the free energy formula generalised to the non-realisable case, among other results. Compared to the grey book, the green book has an updated presentation of the main results, but does not contain all of the details of the proofs of the main results from the grey book.

While the theoretical foundation of SLT is described across many research papers by Watanabe and others, the main results are collected in self-contained form in these monographs. Watanabe offers a set of lecture slides (Watanabe 2023) which may serve as a useful guide to the "big picture" while working through the details in the books. Other key papers include Watanabe 2007; Watanabe 2013. See Watanabe 2024 for a more detailed survey.

\### 5.2 Recent work on singular deep learning

Over the last few years, a community of researchers have pursued the application of SLT to advancing the science and safety of deep learning. Some of the ideas behind this research are discussed by Hoogland et al. 2023; Skalse 2023; Pepin Lehalleur et al. 2025; Furman 2026. We briefly survey some key topics in this emerging literature.

**Characterising and estimating degeneracy in practice.**  We have seen examples of parameter–function map degeneracy in simple neural networks. Symmetries of neural network parameter–function maps have long been studied; however, often the emphasis has been on discrete or globally continuous symmetries rather than additional symmetries localised to subsets of parameter space (see Farrugia-Roberts 2022, § 2.3, for a survey). For two-layer hyperbolic tangent networks, Farrugia-Roberts 2024 characterises the regions of parameter space which display additional degeneracy, and Farrugia-Roberts 2023 characterises degenerate directions in the parameter–function map.

As discussed, analytically calculating the (local) learning coefficient for deep neural networks is challenging. However, precise formulas have been derived for multi-layer deep linear networks (Aoyagi & Watanabe 2005; Aoyagi 2024), two-layer hyperbolic tangent networks (Aoyagi 2009), and certain other architectures. These results assume data is generated from a known "teacher" model.

In practice, we lack knowledge of the true data generating process, and we use more complex architectures. Much work has therefore built on the foundational methods of estimating the local learning coefficient with scalable Markov chain Monte Carlo methods (Lau et al. 2025; Hitchcock & Hoogland 2025). For a practical introduction to learning coefficient estimation, see Furman 2023. Chen & Murfet 2025 characterise the sensitivity of local learning coefficient estimation to patterns in sequence models.

**Bayesian phase transitions and stagewise development.**  As we have discussed, Watanabe's free energy formula suggests Bayesian deep learning should undergo Bayesian phase transitions under certain conditions. Carroll 2021 studied Bayesian phase transitions in small ReLU networks, and Chen et al. 2023 studied Bayesian phase transitions in a small feature autoencoder (the "toy model of superposition" from Elhage et al. 2022).

In practice, we use stochastic gradient-based optimisation, rather than Bayesian learning, to train neural networks. However, the Bayesian case serves as a model system from which we can derive empirically testable predictions. Chen et al. 2023 formulate the *Bayesian antecedent hypothesis*, the empirical conjecture that observed phase transitions in trained neural networks correspond to Bayesian phase transitions modelled by Watanabe's free energy formula. Chen et al. 2023 study such *dynamical phase transitions* in their toy autoencoder and observe a temporal correspondence between phase changes and estimated LLC increases consistent with the free energy formula.

Wang et al. 2024; Hoogland et al. 2025 scale this methodology to transformers trained on natural language, finding similar *stagewise development* phenomena with changes in behaviour and internal structure accompanied by LLC changes. Panickssery & Vaintrob 2023; Hoogland et al. 2025; Carroll et al. 2025; Urdshals & Urdshals 2025 also study developmental stages in transformers trained on synthetic data. Elliott et al. 2026 extend this study to a case of goal misgeneralisation in deep reinforcement learning.

**Degeneracy, interpretability, and patterning.**  The LLC provides a single number representing the effective dimensionality of a model. We can derive from the same principles—asymptotic properties of the posterior that reflect degeneracies in the model—more fine-grained tools for probing the internal computational structures of neural networks and how they depend on data.

- *Weight- and data-refined LLCs:* Wang et al. 2025 compute LLCs of individual transformer modules (e.g., different attention heads) or with respect to different subsets of a data set (e.g., natural language versus code). Observing these refined quantities over training reveals modules developing different structures specialising to different kinds of data.
- *Susceptibilities:* Drawing inspiration from electromagnetic susceptibilities in physics Baker et al. 2025; Wang et al. 2025; Gordon et al. 2026 develop and apply a methodology for computing loss susceptibilities so as to reveal more fine-grained information about how model internals relate to data.
- *Bayesian influence functions:* Similarly, drawing inspiration from training data attribution in statistics, Kreer et al. 2025; Lee et al. 2025; Adam et al. 2025 develop a Bayesian generalisation of classical influence functions that allows the influence functions to be sensitive to higher-order degeneracy in the model.

Weight- and data-refined LLCs are themselves LLCs with a different model or data set, and so the same scalable Markov chain Monte Carlo methods can be used to estimate them as for LLCs. Moreover, like the LLC, susceptibilities and Bayesian influence functions can be approximated as expectations over a localised posterior distribution, and so similar estimation methods can be used for these quantities too.

Wang & Murfet 2026 develop a methodology, *patterning*, for making targeted changes to the training distribution so as to elicit certain changes in the development of neural network internal structure or generalisation behaviour.

**Foundations of singular deep learning.**

There has been some work on developing the foundational theory of SLT and deep learning.

For example, Elliott et al. 2026 generalise Watanabe's free energy formula from Bayesian inference to a generalised non-stationary energy-based inference setting, so as to account for stagewise development in deep reinforcement learning.

Beyond the setting of Bayesian inference, the general role degeneracy plays in the learning dynamics of stochastic gradient-based optimisation remains to be characterised.

Finally, there has been some attempt to theoretically investigate the links between degeneracy in deep learning and computational structure in models.

Clift et al. 2021; Waring 2021; Xu 2021; Murfet 2024; Murfet & Troiani 2025 study degeneracies in a statistical model based on a parameterisation of the space of Turing machine programs, exploring links between degeneracy and computational structure.

Lau 2025, Chapter 5 and Urdshals et al. 2025 develop a theory of minimum description length in degenerate statistical models.

\## References

Maxwell Adam, Zach Furman, and Jesse Hoogland (2025). [*The Loss Kernel: A Geometric Probe for Deep Learning Interpretability*](https://arxiv.org/abs/2509.26537). arXiv:2509.26537.

Miki Aoyagi and Sumio Watanabe (2005). *Stochastic complexities of reduced rank regression in Bayesian estimation*. Neural Networks.

Miki Aoyagi (2009). *Log canonical threshold of Vandermonde matrix type singularities and generalization error of a three layered neural network in Bayesian estimation*. International Journal of Pure and Applied Mathematics.

Miki Aoyagi (2024). *Consideration on the learning efficiency of multiple-layered neural networks with linear units*. Neural Networks.

Garrett Baker, George Wang, Jesse Hoogland, and Daniel Murfet (2025). [*Structural Inference: Interpreting Small Language Models with Susceptibilities*](https://arxiv.org/abs/2504.18274). arXiv:2504.18274.

Liam Carroll (2021). [*Phase Transitions in Neural Networks*](https://therisingsea.org/notes/MSc-Carroll.pdf). School of Mathematics and Statistics, the University of Melbourne.

Liam Carroll (2023). [*Distilling Singular Learning Theory*](https://www.lesswrong.com/s/czrXjvCLsqGepybHC).

Liam Carroll, Jesse Hoogland, Matthew Farrugia-Roberts, and Daniel Murfet (2025). [*Dynamics of Transient Structure in In-Context Linear Regression Transformers*](https://arxiv.org/abs/2501.17745). arXiv:2501.17745.

Zhongtian Chen and Daniel Murfet (2025). [*Modes of Sequence Models and Learning Coefficients*](https://arxiv.org/abs/2504.18048). arXiv:2504.18048.

Zhongtian Chen, Edmund Lau, Jake Mendel, Susan Wei, and Daniel Murfet (2023). [*Dynamical versus Bayesian Phase Transitions in a Toy Model of Superposition*](https://arxiv.org/abs/2310.06301). arXiv:2310.06301.

James Clift, Daniel Murfet, and James Wallbridge (2021). [*Geometry of Program Synthesis*](https://arxiv.org/abs/2103.16080). arXiv:2103.16080.

Nelson Elhage, Tristan Hume, Catherine Olsson, Nicholas Schiefer, Tom Henighan, Shauna Kravec, Zac Hatfield-Dodds, Robert Lasenby, Dawn Drain, Carol Chen, Roger Grosse, Sam McCandlish, Jared Kaplan, Dario Amodei, Martin Wattenberg, and Christopher Olah (2022). *Toy Models of Superposition*. Transformer Circuits Thread.

Chris Elliott, Einar Urdshals, David Quarel, Matthew Farrugia-Roberts, and Daniel Murfet (2026). [*Stagewise Reinforcement Learning and the Geometry of the Regret Landscape*](https://arxiv.org/abs/2601.07524). arXiv:2601.07524.

Matthew Farrugia-Roberts (2022). [*Structural Degeneracy in Neural Networks*](https://far.in.net/mthesis). School of Computing and Information Systems, the University of Melbourne.

Matthew Farrugia-Roberts (2023). [*Functional Equivalence and Path Connectivity of Reducible Hyperbolic Tangent Networks*](https://proceedings.neurips.cc/paper_files/paper/2023/hash/fb64a43508e0cfe53ee6179ff31ea900-Abstract-Conference.html). Advances in Neural Information Processing Systems 36.

Matthew Farrugia-Roberts (2024). [*Losslessly Compressible Neural Network Parameters*](https://openreview.net/forum?id=VhhsbII0Lk). Workshop on Machine Learning and Compression.

Zach Furman (2023). [*Introduction to RLCT estimation*](https://github.com/zfurman56/intro-lc-estimation/).

Zach Furman (2024). [*Singular learning theory: Exercises*](https://www.lesswrong.com/posts/3HYqTAi4kD35G3BzQ/).

Zach Furman (2026). *Deep learning as program synthesis*.

Andrew Gordon, Garrett Baker, George Wang, William Snell, Stan van Wingerden, and Daniel Murfet (2026). [*Towards Spectroscopy: Susceptibility Clusters in Language Models*](https://arxiv.org/abs/2601.12703). arXiv:2601.12703.

Rohan Hitchcock and Jesse Hoogland (2025). [*From Global to Local: A Scalable Benchmark for Local Posterior Sampling*](https://arxiv.org/abs/2507.21449). arXiv:2507.21449.

Jesse Hoogland, Alexander Gietelink Oldenziel, Daniel Murfet, and Stan van Wingerden (2023). [*Towards Developmental Interpretability*](https://www.alignmentforum.org/posts/TjaeCWvLZtEDAS5Ex/).

Jesse Hoogland, George Wang, Matthew Farrugia-Roberts, Liam Carroll, Susan Wei, and Daniel Murfet (2025). *Loss Landscape Degeneracy and Stagewise Development in Transformers*. Transactions on Machine Learning Research.

Philipp Alexander Kreer, Wilson Wu, Maxwell Adam, Zach Furman, and Jesse Hoogland (2025). [*Bayesian Influence Functions for Hessian-Free Data Attribution*](https://arxiv.org/abs/2509.26544). arXiv:2509.26544.

Edmund Lau and Zhongtian Chen (2023). [*Singular Learning Theory: The Low Road*](https://www.youtube.com/playlist?list=PL4vaU_gO_6LIf5CHU3Z3CT39fha55pe16).

Edmund Lau (2025). *A Singular Perspective on Machine Learning*. School of Mathematics and Statistics, the University of Melbourne.

Edmund Lau, Zach Furman, George Wang, Daniel Murfet, and Susan Wei (2025). [*The Local Learning Coefficient: A Singularity-Aware Complexity Measure*](https://openreview.net/forum?id=1av51ZlsuL). The 28th International Conference on Artificial Intelligence and Statistics.

Jin Hwa Lee, Matthew Smith, Maxwell Adam, and Jesse Hoogland (2025). [*Influence Dynamics and Stagewise Data Attribution*](https://arxiv.org/abs/2510.12071). arXiv:2510.12071.

Daniel Murfet and Liam Carroll (2023). [*Singular Learning Theory: The High Road*](https://www.youtube.com/playlist?list=PL4vaU_gO_6LJ4isj5DESGg4OwfVEk98Y-).

Daniel Murfet and Will Troiani (2025). [*Programs as Singularities*](https://arxiv.org/abs/2504.08075). arXiv:2504.08075.

Daniel Murfet (2024). [*Simple versus short: Higher-order degeneracy and error-correction*](https://www.alignmentforum.org/posts/nWRj6Ey8e5siAEXbK/).

Nina Panickssery and Dmitry Vaintrob (2023). [*Investigating the learning coefficient of modular addition*](https://www.alignmentforum.org/posts/4v3hMuKfsGatLXPgt).

Simon Pepin Lehalleur, Jesse Hoogland, Matthew Farrugia-Roberts, Susan Wei, Alexander Gietelink Oldenziel, George Wang, Liam Carroll, and Daniel Murfet (2025). [*You Are What You Eat--AI Alignment Requires Understanding How Data Shapes Structure and Generalisation*](https://arxiv.org/abs/2502.05475). arXiv:2502.05475.

Joar Skalse (2023). [*My criticism of singular learning theory*](https://www.alignmentforum.org/posts/ALJYj4PpkqyseL7kZ/).

Einar Urdshals and Jasmina Urdshals (2025). [*Structure Development in List-Sorting Transformers*](https://arxiv.org/abs/2501.18666). arXiv:2501.18666.

Einar Urdshals, Edmund Lau, Jesse Hoogland, Stan van Wingerden, and Daniel Murfet (2025). [*Compressibility Measures Complexity: Minimum Description Length Meets Singular Learning Theory*](https://arxiv.org/abs/2510.12077). arXiv:2510.12077.

George Wang and Daniel Murfet (2026). [*Patterning: The Dual of Interpretability*](https://arxiv.org/abs/2601.13548). arXiv:2601.13548.

George Wang, Matthew Farrugia-Roberts, Jesse Hoogland, Liam Carroll, Susan Wei, and Daniel Murfet (2024). [*Loss landscape geometry reveals stagewise development of transformers*](https://openreview.net/forum?id=2JabyZjM5H). High-dimensional Learning Dynamics 2024: The Emergence of Structure and Reasoning.

George Wang, Jesse Hoogland, Stan van Wingerden, Zach Furman, and Daniel Murfet (2025). [*Differentiation and Specialization of Attention Heads via the Refined Local Learning Coefficient*](https://openreview.net/forum?id=SUc1UOWndp). International Conference on Learning Representations.

George Wang, Garrett Baker, Andrew Gordon, and Daniel Murfet (2025). [*Embryology of a Language Model*](https://arxiv.org/abs/2508.00331). arXiv:2508.00331.

Thomas Waring (2021). [*Geometric Perspectives on Program Synthesis and Semantics*](https://therisingsea.org/notes/MSc-Waring.pdf). School of Mathematics and Statistics, the University of Melbourne.

Sumio Watanabe (2007). *Almost all learning machines are singular*. IEEE Symposium on Foundations of Computational Intelligence.

Sumio Watanabe (2009). *Algebraic Geometry and Statistical Learning Theory*. Cambridge University Press.

Sumio Watanabe (2013). *A widely applicable Bayesian information criterion*. The Journal of Machine Learning Research.

Sumio Watanabe (2018). *Mathematical Theory of Bayesian Statistics*. Chapman and Hall/CRC.

Sumio Watanabe (2023). *Singular Learning Theory, parts (1) and (2)*.

Sumio Watanabe (2024). *Recent Advances in Algebraic Geometry and Bayesian Statistics*. Information Geometry.

Susan Wei, Daniel Murfet, Mingming Gong, Hui Li, Jesse Gell-Redman, and Thomas Quella (2023). *Deep Learning Is Singular, and That's Good*. IEEE Transactions on Neural Networks and Learning Systems.

Adrian K. Xu (2021). [*Smooth relaxation preserving Turing machines*](https://arxiv.org/abs/2106.00956). arXiv:2106.00956.
