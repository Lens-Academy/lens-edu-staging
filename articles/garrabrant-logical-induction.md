---
title: "Logical Induction"
author:
  - "Scott Garrabrant"
  - "Tsvi Benson-Tilsen"
  - "Andrew Critch"
  - "Nate Soares"
  - "Jessica Taylor"
source_url: "https://arxiv.org/pdf/1609.03543"
published: 2016-09-12
created: 2026-10-10
accessed: 2026-10-10
llm-review:
  date: 2026-10-10
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-10
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

We present a computable algorithm that assigns probabilities to every logical statement in a given formal language, and refines those probabilities over time. For instance, if the language is Peano arithmetic, it assigns probabilities to all arithmetical statements, including claims about the twin prime conjecture, the outputs of long-running computations, and its own probabilities. We show that our algorithm, an instance of what we call a _logical inductor_, satisfies a number of intuitive desiderata, including: (1) it learns to predict patterns of truth and falsehood in logical statements, often long before having the resources to evaluate the statements, so long as the patterns can be written down in polynomial time; (2) it learns to use appropriate statistical summaries to predict sequences of statements whose truth values appear pseudorandom; and (3) it learns to have accurate beliefs about its own current beliefs, in a manner that avoids the standard paradoxes of self-reference. For example, if a given computer program only ever produces outputs in a certain range, a logical inductor learns this fact in a timely manner; and if late digits in the decimal expansion of $\pi$ are difficult to predict, then a logical inductor learns to assign $\approx 10\%$ probability to “the $n$th digit of $\pi$ is a 7” for large $n$. Logical inductors also learn to trust their future beliefs more than their current beliefs, and their beliefs are coherent in the limit (whenever $\phi \rightarrow\psi$, $\mathbb{P}_\infty(\phi) \le \mathbb{P}_\infty(\psi)$, and so on); and logical inductors strictly dominate the universal semimeasure in the limit.

These properties and many others all follow from a single _logical induction criterion_, which is motivated by a series of stock trading analogies. Roughly speaking, each logical sentence $\phi$ is associated with a stock that is worth \$1 per share if $\phi$ is true and nothing otherwise, and we interpret the belief-state of a logically uncertain reasoner as a set of market prices, where $\mathbb{P}_n(\phi)=50\%$ means that on day $n$, shares of $\phi$ may be bought or sold from the reasoner for 50¢. The logical induction criterion says (very roughly) that there should not be any polynomial-time computable trading strategy with finite risk tolerance that earns unbounded profits in that market over time. This criterion bears strong resemblance to the “no Dutch book” criteria that support both expected utility theory (von Neumann and Morgenstern 1944) and Bayesian probability theory (Ramsey 1931; de Finetti 1937).

## Introduction ^introduction

Every student of mathematics has experienced uncertainty about conjectures for which there is “quite a bit of evidence”, such as the Riemann hypothesis or the twin prime conjecture. Indeed, when Zhang (2014) proved a bound on the gap between primes, we were tempted to increase our credence in the twin prime conjecture. But how much evidence does this bound provide for the twin prime conjecture? Can we quantify the degree to which it should increase our confidence?

The natural impulse is to appeal to probability theory in general and Bayes’ theorem in particular. Bayes’ theorem gives rules for how to use observations to update empirical uncertainty about unknown events in the physical world. However, probability theory lacks the tools to manage uncertainty about logical facts.

Consider encountering a computer connected to an input wire and an output wire. If we know what algorithm the computer implements, then there are two distinct ways to be uncertain about the output. We could be uncertain about the input—maybe it’s determined by a coin toss we didn’t see. Alternatively, we could be uncertain because we haven’t had the time to reason out what the program does—perhaps it computes the parity of the 87,653rd digit in the decimal expansion of $\pi$, and we don’t personally know whether it’s even or odd.

The first type of uncertainty is about _empirical_ facts. No amount of thinking in isolation will tell us whether the coin came up heads. To resolve empirical uncertainty we must observe the coin, and then Bayes’ theorem gives a principled account of how to update our beliefs.

The second type of uncertainty is about a _logical_ fact, about what a known computation will output when evaluated. In this case, reasoning in isolation can and should change our beliefs: we can reduce our uncertainty by thinking more about $\pi$, without making any new observations of the external world.

In any given practical scenario, reasoners usually experience a mix of both empirical uncertainty (about how the world is) and logical uncertainty (about what that implies). In this paper, we focus entirely on the problem of managing logical uncertainty. Probability theory does not address this problem, because probability-theoretic reasoners cannot possess uncertainty about logical facts. For example, let $\phi$ stand for the claim that the 87,653rd digit of $\pi$ is a 7. If this claim is true, then $(1+1=2) \Rightarrow\phi$. But the laws of probability theory say that if $A \Rightarrow B$ then $\mathrm{Pr}(A) \le \mathrm{Pr}(B)$. Thus, a perfect Bayesian must be at least as sure of $\phi$ as they are that $1+1=2$! Recognition of this problem dates at least back to Good (1950).

Many have proposed methods for relaxing the criterion $\mathrm{Pr}(A) \le \mathrm{Pr}(B)$ until such a time as the implication has been proven (see, e.g, the work of Hacking (1967); Christiano (2014)). But this leaves open the question of how probabilities should be assigned before the implication is proven, and this brings us back to the search for a principled method for managing uncertainty about logical facts when relationships between them are suspected but unproven.

We propose a partial solution, which we call _logical induction_. Very roughly, our setup works as follows. We consider reasoners that assign probabilities to sentences written in some formal language and refine those probabilities over time. Assuming the language is sufficiently expressive, these sentences can say things like “Goldbach’s conjecture is true” or “the computation `prg` on input `i` produces the output `prg(i)=0`”. The reasoner is given access to a slow deductive process that emits theorems over time, and tasked with assigning probabilities in a manner that outpaces deduction, e.g., by assigning high probabilities to sentences that are eventually proven, and low probabilities to sentences that are eventually refuted, well before they can be verified deductively. Logical inductors carry out this task in a way that satisfies many desirable properties, including:

1.  Their beliefs are logically consistent in the limit as time approaches infinity.
2.  They learn to make their probabilities respect many different patterns in logic, at a rate that outpaces deduction.
3.  They learn to know what they know, and trust their future beliefs, while avoiding paradoxes of self-reference.

These claims (and many others) will be made precise in Section [[#^properties-of-logical-inductors|4]].

A logical inductor is any sequence of probabilities that satisfies our _logical induction criterion_, which works roughly as follows. We interpret a reasoner’s probabilities as prices in a stock market, where the probability of $\phi$ is interpreted as the price of a share that is worth \$1 if $\phi$ is true, and \$0 otherwise (similar to Beygelzimer et al. (2012)). We consider a collection of stock traders who buy and sell shares at the market prices, and define a sense in which traders can exploit markets that have irrational beliefs. The logical induction criterion then says that it should not be possible to exploit the market prices using any trading strategy that can be generated in polynomial-time.

Our main finding is a computable algorithm which satisfies the logical induction criterion, plus proofs that a variety of different desiderata follow from this criterion.

The logical induction criterion can be seen as a weakening of the “no Dutch book” criterion that Ramsey (1931); de Finetti (1937) used to support standard probability theory, which is analogous to the “no Dutch book” criterion that von Neumann and Morgenstern (1944) used to support expected utility theory. Under this interpretation, our criterion says (roughly) that a rational deductively limited reasoner should have beliefs that can’t be exploited by any Dutch book strategy constructed by an efficient (polynomial-time) algorithm. Because of the analogy, and the variety of desirable properties that follow immediately from this one criterion, we believe that the logical induction criterion captures a portion of what it means to do good reasoning about logical facts in the face of deductive limitations. That said, there are clear drawbacks to our algorithm: it does not use its resources efficiently; it is not a decision-making algorithm (i.e., it does not “think about what to think about”); and the properties above hold either asymptotically (with poor convergence bounds) or in the limit. In other words, our algorithm gives a theoretically interesting but ultimately impractical account of how to manage logical uncertainty.

### Desiderata for Reasoning under Logical Uncertainty ^desiderata-for-reasoning-under

For historical context, we now review a number of desiderata that have been proposed in the literature as desirable features of “good reasoning” in the face of logical uncertainty. A major obstacle in the study of logical uncertainty is that it’s not clear what would count as a satisfactory solution. In lieu of a solution, a common tactic is to list desiderata that intuition says a good reasoner should meet. One can then examine them for patterns, relationships, and incompatibilities. A multitude of desiderata have been proposed throughout the years; below, we have collected a variety of them. Each is stated in its colloquial form; many will be stated formally and studied thoroughly later in this paper.

**Desideratum 1** (Computable Approximability). _The method for assigning probabilities to logical claims (and refining them over time) should be computable._

A good method for refining beliefs about logic can never be entirely finished, because a reasoner can always learn additional logical facts by thinking for longer. Nevertheless, if the algorithm refining beliefs is going to have any hope of practicality, it should at least be computable. This idea dates back at least to Good (1950), and has been discussed in depth by Hacking (1967); Eells (1990), among others.

Desideratum 1 may seem obvious, but it is not without its teeth. It rules out certain proposals, such as that of Hutter et al. (2013), which has no computable approximation (Sawin and Demski 2013).

**Desideratum 2** (Coherence in the Limit). _The belief state that the reasoner is approximating better and better over time should be logically consistent._

First formalized by Gaifman (1964), the idea of Desideratum 2 is that the belief state that the reasoner is approximating—the beliefs they would have if they had infinite time to think—should be internally consistent. This means that, in the limit of reasoning, a reasoner should assign $\mathrm{Pr}(\phi) \leq \mathrm{Pr}(\psi)$ whenever $\phi \Rightarrow\psi$, and they should assign probability 1 to all theorems and 0 to all contradictions, and so on.

**Desideratum 3** (Approximate Coherence). _The belief state of the reasoner should be approximately coherent. For example, if the reasoner knows that two statements are mutually exclusive, then it should assign probabilities to those sentences that sum to no more than 1, even if it cannot yet prove either sentence._

Being coherent in the limit is desirable, but good deductively limited reasoning requires approximate coherence at finite times. Consider two claims about a particular computation `prg`, which takes a number `n` as input and produces a number `prg(n)` as output. Assume the first claim says `prg(7)=0`, and the second says `prg(7)=1`. Clearly, these claims are mutually exclusive, and once a reasoner realizes this fact, they should assign probabilities to the two claims that sum to at most 1, even before they can evaluate `prg(7)`. Limit coherence does not guarantee this: a reasoner could assign bad probabilities (say, 100% to both claims) right up until they can evaluate `prg(7)`, at which point they start assigning the correct probabilities. Intuitively, a good reasoner should be able to recognize the mutual exclusivity _before_ they’ve proven either claim. In other words, a good reasoner’s beliefs should be approximately coherent.

Desideratum 3 dates back to at least Good (1950), who proposes a weakening of the condition of coherence that could apply to the belief states of limited reasoners. Hacking (1967) proposes an alternative weakening, as do Garrabrant et al. (2016).

**Desideratum 4** (Learning of Statistical Patterns). _In lieu of knowledge that bears on a logical fact, a good reasoner should assign probabilities to that fact in accordance with the rate at which similar claims are true._

For example, a good reasoner should assign probability $\approx 10\%$ to the claim “the $n$th digit of $\pi$ is a 7” for large $n$ (assuming there is no efficient way for a reasoner to guess the digits of $\pi$ for large $n$). This desideratum dates at least back to Savage (1967), and seems clearly desirable. If a reasoner thought the $10^{100}$th digit of $\pi$ was almost surely a 9, but had no reason for believing this, we would be suspicious of their reasoning methods. Desideratum 4 is difficult to state formally; for two attempts, refer to Garrabrant et al. (2016); Garrabrant et al. (2016).

**Desideratum 5** (Calibration). _Good reasoners should be well-calibrated. That is, among events that a reasoner says should occur with probability $p$, they should in fact occur about $p$ proportion of the time._

Calibration as a desirable property dates back to Pascal, and perhaps farther. If things that a reasoner says should happen 30% of the time actually wind up happening 80% of the time, then they aren’t particularly reliable.

**Desideratum 6** (Non-Dogmatism). _A good reasoner should not have extreme beliefs about mathematical facts, unless those beliefs have a basis in proof._

It would be worrying to see a mathematical reasoner place extreme confidence in a mathematical proposition, without any proof to back up their belief. The virtue of skepticism is particularly apparent in probability theory, where Bayes’ theorem says that a probabilistic reasoner can never update away from “extreme” (0 or 1) probabilities. Accordingly, Cromwell’s law (so named by the statistician Lindley (1991)) says that a reasonable person should avoid extreme probabilities except when applied to statements that are logically true or false. We are dealing with logical uncertainty, so it is natural to extend Cromwell’s law to say that extreme probabilities should also be avoided on logical statements, except in cases where the statements have been _proven_ true or false. In settings where reasoners are able to update away from 0 or 1 probabilities, this means that a good reasoner’s beliefs shouldn’t be “stuck” at probability 1 or 0 on statements that lack proofs or disproofs.

In the domain of logical uncertainty, Desideratum 6 can be traced back to Carnap (1962, Sec. 53), and has been demanded by many, including Gaifman and Snir (1982); Hutter et al. (2013).

**Desideratum 7** (Uniform Non-Dogmatism). _A good reasoner should assign a non-zero probability to any computably enumerable consistent theory (viewed as a limit of finite conjunctions)._

For example the axioms of Peano arithmetic are computably enumerable, and if we construct an ever-growing conjunction of these axioms, we can ask that the limit of a reasoner’s credence in these conjunctions converge to a value bounded above 0, even though there are infinitely many conjuncts. The first formal statement of Desideratum 7 that we know of is given by Demski (2012), though it is implicitly assumed whenever asking for a set of beliefs that can reason accurately about arbitrary arithmetical claims (as is done by, e.g., Savage (1967); Hacking (1967)).

**Desideratum 8** (Universal Inductivity). _Given enough time to think, the beliefs of a good reasoner should dominate the universal semimeasure._

Good reasoning in general has been studied for quite some time, and reveals some lessons that are useful for the study of good reasoning under deductive limitation. Solomonoff (1964); Solomonoff (1964); Zvonkin and Levin (1970); Li and Vitányi (1993) have given a compelling formal treatment of good reasoning assuming logical omniscience in the domain of sequence prediction, by describing an inductive process (known as a universal semimeasure) with a number of nice properties, including (1) it assigns non-zero prior probability to every computable sequence of observations; (2) it assigns higher prior probability to simpler hypotheses; and (3) it predicts as well or better than any computable predictor, modulo a constant amount of error. Alas, universal semimeasures are uncomputable; nevertheless, they provide a formal model of what it means to predict sequences well, and we can ask logically uncertain reasoners to copy those successes. For example, we can ask that they would perform as well as a universal semimeasure if given enough time to think.

**Desideratum 9** (Approximate Bayesianism). _The reasoner’s beliefs should admit of some notion of conditional probabilities, which approximately satisfy both Bayes’ theorem and the other desiderata listed here._

Bayes’ rule gives a fairly satisfying account of how to manage empirical uncertainty in principle (as argued extensively by Jaynes (2003)), where beliefs are updated by conditioning a probability distribution. As discussed by Good (1950); Glymour (1980), creating a distribution that satisfies both coherence and Bayes’ theorem requires logical omniscience. Still, we can ask that the approximation schemes used by a limited agent be approximately Bayesian in some fashion, while retaining whatever good properties the unconditional probabilities have.

**Desideratum 10** (Introspection). _If a good reasoner knows something, she should also know that she knows it._

Proposed by Hintikka (1962), this desideratum is popular among epistemic logicians. It is not completely clear that this is a desirable property. For instance, reasoners should perhaps be allowed to have “implicit knowledge” (which they know without knowing that they know it), and it’s not clear where the recursion should stop (do you know that you know that you know that you know that ${1 = 1}$?). This desideratum has been formalized in many different ways; see Christiano et al. (2013); Campbell-Moore (2015) for a sample.

**Desideratum 11** (Self-Trust). _A good reasoner thinking about a hard problem should expect that, in the future, her beliefs about the problem will be more accurate than her current beliefs._

Stronger than self-knowledge is self-_trust_—a desideratum that dates at least back to Hilbert (1902), when mathematicians searched for logics that placed confidence in their own machinery. While Gödel et al. (1934) showed that strong forms of self-trust are impossible in a formal proof setting, experience demonstrates that human mathematicians are capable of trusting their future reasoning, relatively well, most of the time. A method for managing logical uncertainty that achieves this type of self-trust would be highly desirable.

**Desideratum 12** (Approximate Inexploitability). _It should not be possible to run a Dutch book against a good reasoner in practice._

Expected utility theory and probability theory are both supported in part by “Dutch book” arguments which say that an agent is rational if (and only if) there is no way for a clever bookie to design a “Dutch book” which extracts arbitrary amounts of money from the reasoner (von Neumann and Morgenstern 1944; de Finetti 1937). As noted by Eells (1990), these constraints are implausibly strong: all it takes to run a Dutch book according to de Finetti’s formulation is for the bookie to know a logical fact that the reasoner does not know. Thus, to avoid being Dutch booked by de Finetti’s formulation, a reasoner must be logically omniscient.

Hacking (1967); Eells (1990) call for weakenings of the Dutch book constraints, in the hopes that reasoners that are approximately inexploitable would do good approximate reasoning. This idea is the cornerstone of our framework—in particular, we consider reasoners that cannot be exploited in polynomial time, using a formalism defined below. See Definition 102 for details.

**Desideratum 13** (Gaifman Inductivity). _Given a $\Pi_1$ statement $\phi$ (i.e., a universal generalization of the form “for every $x$, $\psi$”), as the set of examples the reasoner has seen goes to “all examples”, the reasoner’s belief in $\phi$ should approach certainty._

Proposed by Gaifman (1964), Desideratum 13 states that a reasoner should “generalize well”, in the sense that as they see more instances of a universal claim (such as “for every $x$, $\psi(x)$ is true”) they should eventually believe the universal with probability 1. Desideratum 13 has been advocated by Hutter et al. (2013).

**Desideratum 14** (Efficiency). _The algorithm for assigning probabilities to logical claims should run efficiently, and be usable in practice._

One goal of understanding “good reasoning” in the face of logical uncertainty is to design algorithms for reasoning using limited computational resources. For that, the algorithm for assigning probabilities to logical claims needs to be not only computable, but efficient. Aaronson (2013) gives a compelling argument that solutions to logical uncertainty require understanding complexity theory, and this idea is closely related to the study of bounded rationality (Simon 1982) and efficient meta-reasoning (Russell and Wefald 1991).

**Desideratum 15** (Decision Rationality). _The algorithm for assigning probabilities to logical claims should be able to target specific, decision-relevant claims, and it should reason about those claims as efficiently as possible given the computing resources available._

This desideratum dates at least back to Savage (1967), who asks for an extension to probability theory that takes into account the costs of thinking. For a method of reasoning under logical uncertainty to aid in the understanding of good bounded reasoning, it must be possible for an agent to use the reasoning system to reason efficiently about specific decision-relevant logical claims, using only enough resources to refine the probabilities well enough for the right decision to become clear. This desideratum blurs the line between decision-making and logical reasoning; see Russell and Wefald (1991); Hay et al. (2012) for a discussion.

**Desideratum 16** (Answers Counterpossible Questions). _When asked questions about contradictory states of affairs, a good reasoner should give reasonable answers._

In logic, the principle of explosion says that from a contradiction, anything follows. By contrast, when human mathematicians are asked counterpossible questions, such as “what would follow from Fermat’s last theorem being false?”, they often give reasonable answers, such as “then there would exist non-modular elliptic curves”, rather than just saying “anything follows from a contradiction”. Soares and Fallenstein (2015) point out that some deterministic decision-making algorithms reason about counterpossible questions (“what would happen if my deterministic algorithm had the output $a$ vs $b$ vs $c$?”). The topic of counterpossibilities has been studied by philosophers including Cohen (1990); Vander Laan (2004); Brogaard and Salerno (2007); Krakauer (2012); Bjerring (2014), and it is reasonable to hope that a good logically uncertain reasoner would give reasonable answers to counterpossible questions.

**Desideratum 17** (Use of Old Evidence). _When a bounded reasoner comes up with a new theory that neatly describes anomalies in the old theory, that old evidence should count as evidence in favor of the new theory._

The problem of old evidence is a longstanding problem in probability theory (Glymour 1980). Roughly, the problem is that a perfect Bayesian reasoner always uses all available evidence, and keeps score for all possible hypotheses at all times, so no hypothesis ever gets a “boost” from old evidence. Human reasoners, by contrast, have trouble thinking up good hypotheses, and when they do, those new hypotheses often get a large boost by retrodicting old evidence. For example, the precession of the perihelion of Mercury was known for quite some time before the development of the theory of General Relativity, and could not be explained by Newtonian mechanics, so it was counted as strong evidence in favor of Einstein’s theory. Garber (1983); Jeffrey (1983) have speculated that a solution to the problem of logical omniscience would shed light on solutions to the problem of old evidence.

Our solution does not achieve all these desiderata. Doing so would be impossible; Desiderata 1, 2, and 13 cannot be satisfied simultaneously. Further, Sawin and Demski (2013) have shown that Desiderata 1, 6, 13, and a very weak form of 2 are incompatible; an ideal belief state that is non-dogmatic, Gaifman inductive, and coherent in a weak sense has no computable approximation. Our algorithm is computably approximable, approximately coherent, and non-dogmatic, so it cannot satisfy 13. Our algorithm also fails to meet 14 and 15, because while our algorithm is computable, it is purely inductive, and so it does not touch upon the decision problem of thinking about what to think about and how to think about it with minimal resource usage. As for 16 and 17, the case is interesting but unclear; we give these topics some treatment in Section [[#^discussion|7]].

Our algorithm does satisfy desiderata 1 through 12. In fact, our algorithm is designed to meet only 1 and 12, from which 2-11 will all be shown to follow. This is evidence that our logical induction criterion captures a portion of what it means to manage uncertainty about logical claims, analogous to how Bayesian probability theory is supported in part by the fact that a host of good properties follow from a single criterion (“don’t be exploitable by a Dutch book”). That said, there is ample room to disagree about how well our algorithm achieves certain desiderata, e.g. when the desiderata is met only in the asymptote, or with error terms that vanish only slowly.

### Related Work ^related-work

The study of logical uncertainty is an old topic. It can be traced all the way back to Bernoulli, who laid the foundations of statistics, and later Boole (1854), who was interested in the unification of logic with probability from the start. Refer to Hailperin (1996) for a historical account. Our algorithm assigns probabilities to sentences of logic directly; this thread can be traced back through Łoś (1955) and later Gaifman (1964), who developed the notion of coherence that we use in this paper. More recently, that thread has been followed by Demski (2012), whose framework we use, and Hutter et al. (2013), who define a probability distribution on logical sentences that is quite desirable, but which admits of no computable approximation (Sawin and Demski 2013).

The objective of our algorithm is to manage uncertainty about logical facts (such as facts about mathematical conjectures or long-running computer programs). When it comes to the problem of developing formal tools for manipulating uncertainty, our methods are heavily inspired by Bayesian probability theory, and so can be traced back to Pascal, who was followed by Bayes, Laplace, Kolmogorov (1950); Savage (1954); Carnap (1962); Jaynes (2003), and many others. Polya (1990) was among the first in the literature to explicitly study the way that mathematicians engage in plausible reasoning, which is tightly related to the object of our study.

We are interested in the subject of what it means to do “good reasoning” under logical uncertainty. In this, our approach is quite similar to the approach of Ramsey (1931); de Finetti (1937); von Neumann and Morgenstern (1944); Teller (1973); Lewis (1999); Joyce (1999), who each developed axiomatizations of rational behavior and produced arguments supporting those axioms. In particular, they each supported their proposals with Dutch book arguments, and those Dutch book arguments were a key inspiration for our logical induction criterion.

The fact that using a coherent probability distribution requires logical omniscience (and is therefore unsatisfactory when it comes to managing logical uncertainty) dates at least back to Good (1950). Savage (1967) also recognized the problem, and stated a number of formal desiderata that our solution in fact meets. Hacking (1967) addressed the problem by discussing notions of approximate coherence and weakenings of the Dutch book criteria. While his methods are ultimately unsatisfactory, our approach is quite similar to his in spirit.

The flaw in Bayesian probability theory was also highlighted by Glymour (1980), and dubbed the “problem of old evidence” by Garber (1983) in response to Glymor’s criticism. Eells (1990) gave a lucid discussion of the problem, revealed flaws in Garber’s arguments and in Hacking’s solution, and named a number of other desiderata which our algorithm manages to satisfy. Refer to Zynda (1995) and Sprenger (2015) for relevant philosophical discussion in the wake of Eells. Of note is the treatment of Adams (1996), who uses logical deduction to reason about an unknown probability distribution that satisfies certain logical axioms. Our approach works in precisely the opposite direction: we use probabilistic methods to create an approximate distribution where logical facts are the subject.

Straddling the boundary between philosophy and computer science, Aaronson (2013) has made a compelling case that computational complexity must play a role in answering questions about logical uncertainty. These arguments also provided some inspiration for our approach, and roughly speaking, we weaken the Dutch book criterion of standard probability theory by considering only exploitation strategies that can be constructed by a polynomial-time machine. The study of logical uncertainty is also tightly related to the study of bounded rationality (Simon 1982; Russell and Wefald 1991; Rubinstein 1998; Russell 2016).

Fagin and Halpern (1987) also straddled the boundary between philosophy and computer science with early discussions of algorithms that manage uncertainty in the face of resource limitations. (See also their discussions of uncertainty and knowledge (Fagin et al. 1995; Halpern 2003).) This is a central topic in the field of artificial intelligence (AI), where scientists and engineers have pursued many different paths of research. The related work in this field is extensive, including (but not limited to) work on probabilistic programming (Vajda 1972; McCallum et al. 2009; Wood et al. 2014; De Raedt and Kimmig 2015); probabilistic inductive logic programming (Muggleton and Watanabe 2014; De Raedt and Kersting 2008; De Raedt 2008; Kersting and De Raedt 2007); and meta-reasoning (Russell and Wefald 1991; Zilberstein 2008; Hay et al. 2012). The work most closely related to our own is perhaps the work of Thimm (2013) and others on reasoning using inconsistent knowledge bases, a task which is analogous to constructing an approximately coherent probability distribution. (See also Muiño (2011); Thimm (2013); Potyka and Thimm (2015); Potyka (2015).) Our framework also bears some resemblance to the Markov logic network framework of Richardson and Domingos (2006), in that both algorithms are coherent in the limit. Where Markov logic networks are specialized to individual restricted domains of discourse, our algorithm reasons about all logical sentences. (See also Kok and Domingos (2005); Singla and Domingos (2005); Tran and Davis (2008); Lowd and Domingos (2007); Mihalkova et al. (2007); Wang and Domingos (2008); Khot et al. (2015).)

In that regard, our algorithm draws significant inspiration from Solomonoff’s theory of inductive inference (Solomonoff 1964; Solomonoff 1964) and the developments on that theory made by Zvonkin and Levin (1970); Li and Vitányi (1993). Indeed, we view our algorithm as a Solomonoff-style approach to the problem of reasoning under logical uncertainty, and as a result, our algorithm bears a strong resemblance to many algorithms that are popular methods for practical statistics and machine learning; refer to Opitz and Maclin (1999); Dietterich (2000) for reviews of popular and successful ensemble methods. Our approach is also similar in spirit to the probabilistic numerics approach of Briol et al. (2015), but where probabilistic numerics is concerned with algorithms that give probabilistic answers to individual particular numerical questions, we are concerned with algorithms that assign probabilities to all queries in a given formal language. (See also (Briol et al. 2015; Hennig et al. 2015).)

Finally, our method of interpreting beliefs as prices and using prediction markets to generate reasonable beliefs bears heavy resemblance to the work of Beygelzimer et al. (2012) who use similar mechanisms to design a learning algorithm that bets on events. Our results can be seen as an extension of that idea to the case where the events are every sentence written in some formal language, in a way that learns inductively to predict logical facts while avoiding the standard paradoxes of self-reference.

The work sampled here is only a small sample of the related work, and it neglects contributions from many other fields, including but not limited to epistemic logic (Gärdenfors 1988; Meyer and Van Der Hoek 1995; Schlesinger 1985; Sowa 1999; Guarino 1998), game theory (Rantala 1979; Hintikka 1979; Bacharach 1994; Lipman 1991; Battigalli and Bonanno 1999; Binmore 1992), paraconsistent logic (Blair and Subrahmanian 1989; Priest 2002; Mortensen 2013; Fuhrmann 2013; Akama and Costa 2016) and fuzzy logic (Klir and Yuan 1995; Yen and Langari 1999; Gerla 2013). The full history is too long and rich for us to do it justice here.

### Overview ^overview

Our main result is a formalization of Desideratum 12 above, which we call the _logical induction criterion_, along with a computable algorithm that meets the criterion, plus proofs that formal versions of Desiderata 2-11 all follow from the criterion.

In Section [[#^notation|2]] we define some notation. In Section [[#^the-logical-induction-criterion|3]] we state the logical induction criterion and our main theorem, which says that there exists a computable logical inductor. The logical induction criterion is motivated by a series of stock trading analogies, which are also introduced in Section [[#^the-logical-induction-criterion|3]].

In Section [[#^properties-of-logical-inductors|4]] we discuss a number of properties that follow from this criterion, including properties that hold in the limit, properties that relate to pattern-recognition, calibration properties, and properties that relate to self-knowledge and self-trust.

A computable logical inductor is described in Section [[#^construction|5]]. Very roughly, the idea is that given any trader, it’s possible to construct market prices at which they make no trades (because they think the prices are right); and given an enumeration of traders, it’s possible to aggregate their trades into one “supertrader” (which takes more and more traders into account each day); and thus it is possible to construct a series of prices which is not exploitable by any trader in the enumeration.

In Section [[#^selected-proofs|6]] we give a few selected proofs. In Section [[#^discussion|7]] we conclude with a discussion of applications of logical inductors, variations on the logical induction framework, speculation about what makes logical inductors tick, and directions for future research. The remaining proofs can be found in the appendix.

## Notation ^notation

This section defines notation used throughout the paper. The reader is invited to skim it, or perhaps skip it entirely and use it only as a reference when needed.

**Common sets and functions.** The set of positive natural numbers is denoted by ${{\mathbb{N}}^+}$, where the superscript makes it clear that 0 is not included. We work with ${\mathbb{N}}^+$ instead of ${\mathbb{N}}^{\ge 0}$ because we regularly consider initial segments of infinite sequences up to and including the element at index $n$, and it will be convenient for those lists to have length $n$. Sums written $\sum_{i\leq n}(-)$ are understood to start at $i=1$. We use ${\mathbb{R}}$ to denote the set of real numbers, and ${\mathbb{Q}}$ to denote the set of rational numbers. When considering continuous functions with range in ${\mathbb{Q}}$, we use the subspace topology on ${\mathbb{Q}}$ inherited from ${\mathbb{R}}$. We use ${\mathbb{B}}$ to denote the set $\{0, 1\}$ interpreted as Boolean values. In particular, Boolean operations like $\land$, $\lor$, $\lnot$, $\rightarrow$ and $\leftrightarrow$ are defined on ${\mathbb{B}}$, for example, $(1\land 1) = 1$, $\lnot 1 = 0$, and so on.

We write $\operatorname{Fin}(X)$ for the set of all finite subsets of $X$, and $\smash{X^{{\mathbb{N}}^+}}$ for all infinite sequences with elements in $X$. In general, we use $B^A$ to denote the set of functions with domain $A$ and codomain $B$. We treat the expression $f : A \to B$ as equivalent to $f\in B^A$, i.e., both state that $f$ is a function that takes inputs from the set $A$ and produces an output in the set $B$. We write $f : A\mathrel{\mathrlap{\mkern7mu\shortmid}\rightarrow}B$ to indicate that $f$ is a partial function from $A$ to $B$. We denote equivalence of expressions that represent functions by $\equiv$, e.g., $(x-1)^2 \equiv x^2-2x+1$. We write $\|-\|_1$ for the $\ell_1$ norm. When $A$ is an affine combination, $\|A\|_1$ includes the trailing coefficient.

**Logical sentences.** We generally use the symbols $\phi, \psi, \chi$ to denote well-formed formulas in some language of propositional logic $\mathcal{L}$ (such as a theory of first order logic; see below), which includes the basic logical connectives $\lnot$, $\land$, $\lor$, $\rightarrow$, $\leftrightarrow$, and uses modus ponens as its rule of inference. We assume that $\mathcal{L}$ has been chosen so that its sentences can be interpreted as claims about some class of mathematical objects, such as natural numbers or computer programs. We commonly write $\mathcal{S}$ for the set of all sentences in $\mathcal{L}$, and $\Gamma$ for a set of axioms from which to write proofs in the language. We write $\Gamma\vdash\phi$ when $\phi$ can be proven from $\Gamma$ via modus ponens.

We will write logical formulas inside quotes $\text{“}\!-\!\text{”}$, such as $\phi := \text{“}x = 3\text{”}$. The exception is after $\vdash$, where we do not write quotes, in keeping with standard conventions. We sometimes define sentences such as ${\phi := \text{“}\textnormal{Goldbach's conjecture}\text{”}}$, in which case it is understood that the English text could be expanded into a precise arithmetical claim.

We use underlines to indicate when a symbol in a formula should be replaced by the expression it stands for. For example, if $n:=3$, then $\phi:= \text{“}x > {\underline{n}}\text{”}$ means $\phi=\text{“}x>3\text{”}$, and $\psi := \text{“}{\underline{\smash{\phi}}} \to (x = {\underline{n}}+ 1)\text{”}$ means $\psi = \text{“}x > 3 \to (x = 3+1)\text{”}$. If $\phi$ and $\psi$ denote formulas, then $\lnot \phi$ denotes $\text{“}\lnot({\underline{\smash{\phi}}})\text{”}$ and $\phi \land \psi$ denotes $\text{“}({\underline{\smash{\phi}}})\land({\underline{\smash{\psi}}})\text{”}$ and so on. For instance, if $\phi := \text{“}x > 3\text{”}$ then $\lnot\phi$ denotes $\text{“}\lnot(x > 3)\text{”}$.

**First order theories and prime sentences.** We consider any theory in first order logic (such as Peano Arithmetic, ${\mathsf{PA}}$) as a set of axioms that includes the axioms of first order logic, so that modus ponens is the only rule of inference needed for proofs. As such, we view any first order theory as specified in a propositional calculus (following Enderton (2001)) whose atoms are the so-called “prime” sentences of first order logic, i.e., quantified sentences like $\text{“}\exists x \colon \cdots\text{”}$, and atomic sentences like $\text{“}t_1=t_2\text{”}$ and $\text{“}R(t_1,\ldots,t_n)\text{”}$ where the $t_i$ are closed terms. Thus, every first-order sentence can be viewed as a Boolean combination of prime sentences with logical connectives (viewing $\text{“}\forall x \colon \cdots\text{”}$ as shorthand for $\text{“}\lnot\exists x \colon \lnot \cdots\text{”}$). For example, the sentence 

$$
\phi := \text{“}((1+1=2)\wedge(\forall x \colon x>0))\rightarrow(\exists y \colon \forall z \colon (7>1+1)\rightarrow(y+z>2))\text{”}
$$

 is decomposed into $\text{“}1+1=2\text{”}$, $\text{“}\exists x \colon \lnot(x>0)\text{”}$ and $\text{“}\exists y \colon \forall z \colon (7>1+1)\rightarrow(y+z>2)\text{”}$, where the leading $\text{“}\lnot\text{”}$ in front of the second statement is factored out as a Boolean operator. In particular, note that while $(7>1+1)$ is a prime sentence, it _does not_ occur in the Boolean decomposition of $\phi$ into primes, since it occurs within a quantifier. We choose this view because we will not always assume that the theories we manipulate include the quantifier axioms of first-order logic.

**Defining values by formulas.** We often view a formula that is free in one variable as a way of defining a particular number that satisfies that formula. For example, given the formula $X(\nu) = \text{“}\nu^2=9 \; \wedge \; \nu>0\text{”}$, we would like to think of $X$ as representing the unique value “3”, in such a way that that we can then have $\text{“}5X+1\text{”}$ refer to the number $16$.

To formalize this, we use the following notational convention. Let $X$ be a formula free in one variable. We write $X(x)$ for the formula resulting from substituting $x$ for the free variable of $X$. If 

$$
\Gamma\vdash{\exists x \forall y \colon X(y) \to y=x},
$$

 then we say that $X$ defines a unique value (via $\Gamma$), and we refer to that value as “the value” of $X$. We will be careful in distinguishing between what $\Gamma$ can prove about $X(\nu)$ on the one hand, and the values of $X(\nu)$ in different models of $\Gamma$ on the other.

If $X_1, \ldots, X_k$ are all formulas free in one variable that define a unique value (via $\Gamma$), then for any $k$\-place relationship $R$, we write $\text{“}R(X_1,X_2,\ldots,X_k)\text{”}$ as an abbreviation for 

$$
\text{“}\forall x_1x_2\ldots x_k \colon X_1(x_1) \land X_2(x_2) \land \ldots \land X_k(x_k) \to
  R(x_1, x_2, \ldots, x_k)\text{”}.
$$

 For example, $\text{“}Z=2X+Y\text{”}$ is shorthand for 

$$
\text{“}\forall xyz \colon X(x) \wedge Y(y) \wedge Z(z) \rightarrow z = 2x+y\text{”}.
$$

 This convention allows us to write concise expressions that describe relationships between well-defined values, even when those values may be difficult or impossible to determine via computation.

**Representing computations.** When we say a theory $\Gamma$ in first order logic “can represent computable functions”, we mean that its language is used to refer to computer programs in such a way that $\Gamma$ satisfies the representability theorem for computable functions. This means that for every (total) computable function $f : {\mathbb{N}}^+ \to {\mathbb{N}}^+$, there exists a $\Gamma$\-formula $\gamma_f$ with two free variables such that for all $n,y\in{\mathbb{N}}^+$, 

$$
y=f(n) \textnormal{~ if and only if ~} \Gamma\vdash \forall \nu \colon \gamma_f({\underline{n}},\nu) \leftrightarrow\nu = {\underline{y}},
$$

 where “$\gamma_f({\underline{n}},\nu)$” stands, in the usual way, for the formula resulting from substituting an encoding of $n$ and the symbol $\nu$ for its free variables. In particular, note that this condition requires $\Gamma$ to be consistent.

When $\Gamma$ can represent computable functions, we use $\text{“}{\underline{f}}({\underline{n}})\text{”}$ as shorthand for the formula $\text{“}\gamma_f({\underline{n}}, \nu)\text{”}$. In particular, since $\text{“}\gamma_f({\underline{n}}, \nu)\text{”}$ is free in a single variable $\nu$ and defines a unique value, we use $\text{“}{\underline{f}}({\underline{n}})\text{”}$ by the above convention to write, e.g., 

$$
{\text{“}{\underline{f}}(3) < {\underline{g}}(3)\text{”}}
$$

 as shorthand for 

$$
\text{“}\forall xy \colon \gamma_f(3, x) \land \gamma_g(3, y) \to x < y\text{”}.
$$

 In particular, note that writing down a sentence like $\text{“}{\underline{f}}(3) > 4\text{”}$ does not involve computing the value $f(3)$; it merely requires writing out the definition of $\gamma_f$. This distinction is important when $f$ has a very slow runtime.

**Sequences.** We denote infinite sequences using overlines, like ${\overline{x}} := (x_1, x_2, \ldots)$, where it is understood that $x_i$ denotes the $i$th element of ${\overline{x}}$, for $i\in {{\mathbb{N}}^+}$. To define sequences of sentences compactly, we use parenthetical expressions such as ${\overline{\phi}}:= (\text{“}{\underline{n}} > 7\text{”})_{n\in {{\mathbb{N}}^+}}$, which defines the sequence 

$$
(\text{“}1 > 7\text{”}, \text{“}2 > 7\text{”}, \text{“}3 > 7\text{”}, \ldots).
$$

 We define ${x_{\le n} := (x_1, \ldots, x_n)}$. Given another element $y$, we abuse notation in the usual way and define $(x_{\le n},y) = (x_1,\ldots,x_n, y)$ to be the list $x_{\le n}$ with $y$ appended at the end. We write $()$ for the empty sequence.

A sequence ${\overline{x}}$ is called _computable_ if there is a computable function $f$ such that $f(n)=x_n$ for all $n\in {{\mathbb{N}}^+}$, in which case we say $f$ computes ${\overline{x}}$.

**Asymptotics.** Given any sequences ${\overline{x}}$ and ${\overline{y}}$, we write 

$$
\begin{align*}
  x_n\eqsim_ny_n& \quad\textnormal{for}\quad \lim_{n \to\infty} x_n- y_n= 0,\\
  x_n\gtrsim_ny_n& \quad\textnormal{for}\quad \liminf_{n \to\infty} x_n- y_n\ge 0,\textnormal{~and}\\
  x_n\lesssim_ny_n& \quad\textnormal{for}\quad \limsup_{n \to\infty} x_n- y_n\le 0.
\end{align*}
$$

## The Logical Induction Criterion ^the-logical-induction-criterion

In this section, we will develop a framework in which we can state the logical induction criterion and a number of properties possessed by logical inductors. The framework will culminate in the following definition, and a theorem saying that computable logical inductors exist for every deductive process.

**Definition 1** (The Logical Induction Criterion). _A market ${\overline{\mathbb{P}}}$ is said to satisfy the **logical induction criterion** relative to a deductive process ${\overline{D}}$ if there is no efficiently computable trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$. A market ${\overline{\mathbb{P}}}$ meeting this criterion is called a **logical inductor over $\boldsymbol{{\overline{D}}}$**._

We will now define markets, deductive processes, efficient computability, traders, and exploitation.

### Markets ^markets

We will be concerned with methods for assigning values in the interval $[0, 1]$ to sentences of logic. We will variously interpret those values as prices, probabilities, and truth values, depending on the context. Let $\mathcal{L}$ be a language of propositional logic, and let $\mathcal{S}$ be the set of all sentences written in $\mathcal{L}$. We then define:

**Definition 2** (Valuation). _A **valuation** is any function $\mathbb{V}: \mathcal{S}\to [0, 1]$. We refer to $\mathbb{V}(\phi)$ as the value of $\phi$ according to $\mathbb{V}$. A valuation is called rational if its image is in $\mathbb{Q}$._

First let us treat the case where we interpret the values as prices.

**Definition 3** (Pricing). _A **pricing** $\mathbb{P}: \mathcal{S}\to {\mathbb{Q}}\cap [0, 1]$ is any computable rational valuation. If $\mathbb{P}(\phi)=p$ we say that the price of a $\phi$\-share according to $\mathbb{P}$ is $p$, where the intended interpretation is that a $\phi$\-share is worth \$1 if $\phi$ is true._

A **market** ${\overline{\mathbb{P}}}=(\mathbb{P}_1,\mathbb{P}_2,\ldots)$ is a computable sequence of pricings $\mathbb{P}_i : \mathcal{S}\to {\mathbb{Q}}\cap [0,1]$.

We can visualize a market as a series of pricings that may change day by day. The properties proven in Section [[#^properties-of-logical-inductors|4]] will apply to any market that satisfies the logical induction criterion. Theorem 129 (Limit Coherence) will show that the prices of a logical inductor can reasonably be interpreted as probabilities, so we will often speak as if the prices in a market represent the beliefs of a reasoner, where $\mathbb{P}_n(\phi)=0.75$ is interpreted as saying that on day $n$, the reasoner assigns 75% probability to $\phi$.

In fact, the logical inductor that we construct in Section [[#^construction|5]] has the additional property of being finite at every timestep, which means we can visualize it as a series of finite belief states that a reasoner of interest writes down each day.

**Definition 4** (Belief State). _A **belief state** $\mathbb{P}: \mathcal{S}\to {\mathbb{Q}}\cap [0, 1]$ is a computable rational valuation with finite support, where $\mathbb{P}(\phi)$ is interpreted as the probability of $\phi$ (which is 0 for all but finitely many $\phi$)._

We can visualize a belief state as a finite list of $(\phi, p)$ pairs, where the $\phi$ are unique sentences and the $p$ are rational-number probabilities, and $\mathbb{P}(\phi)$ is defined to be $p$ if $(\phi, p)$ occurs in the list, and $0$ otherwise.

**Definition 5** (Computable Belief Sequence). _A **computable belief sequence** ${\overline{\mathbb{P}}}= (\mathbb{P}_1,\mathbb{P}_2,\ldots)$ is a computable sequence of belief states, interpreted as a reasoner’s explicit beliefs about logic as they are refined over time._

We can visualize a computable belief sequence as a large spreadsheet where each column is a belief state, and the rows are labeled by an enumeration of all logical sentences. We can then imagine a reasoner of interest working on this spreadsheet, by working on one column per day.

Philosophically, the reason for this setup is as follows. Most people know that the sentence $\text{“}1+1\textnormal{\ is even}\text{”}$ is true, and that the sentence $\text{“}1+1+1+1\textnormal{\ is even}\text{”}$ is true. But consider, is the following sentence true? 

$$
\text{“}1+1+1+1+1+1+1+1+1+1+1+1+1\textnormal{\ is even}\text{”}
$$

 To answer, we must pause and count the ones. Since we wish to separate the question of what a reasoner already knows from what they could infer using further computing resources, we require that the reasoner write out their beliefs about logic explicitly, and refine them day by day.

In this framework, we can visualize a reasoner as a person who computes the belief sequence by filling in a large spreadsheet, always working on the $n$th column on the $n$th day, by refining and extending her previous work as she learns new facts and takes more sentences into account, while perhaps making use of computer assistance. For example, a reasoner who has noticed that $\text{“}1 + \cdots + 1\textnormal{\ is even}\text{”}$ is true iff the sentence has an even number of ones, might program her computer to write 1 into as many of the true $\text{“}1+\cdots+1\textnormal{\ is even}\text{”}$ cells per day as it can before resources run out. As another example, a reasoner who finds a bound on the prime gap might go back and update her probability on the twin prime conjecture. In our algorithm, the reasoner will have more and more computing power each day, with which to construct her next belief state.

### Deductive Processes ^deductive-processes

We are interested in the question of what it means for reasoners to assign “reasonable probabilities” to statements of logic. Roughly speaking, we will imagine reasoners that have access to some formal deductive process, such as a community of mathematicians who submit machine-checked proofs to an official curated database. We will study reasoners that “outpace” this deductive process, e.g., by assigning high probabilities to conjectures that will eventually be proven, and low probabilities to conjectures that will eventually be disproven, well before the relevant proofs are actually found.

A **deductive process** ${\overline{D}}: {\mathbb{N}}^+ \to \operatorname{Fin}(\mathcal{S})$ is a computable nested sequence $D_1 \subseteq D_2 \subseteq D_3 \ldots$ of finite sets of sentences. We write $D_\infty$ for the union $\bigcup_nD_n$.

This is a rather barren notion of “deduction”. We will consider cases where we fix some theory $\Gamma$, and $D_n$ is interpreted as the theorems proven up to and including day $n$. In this case, ${\overline{D}}$ can be visualized as a slow process that reveals the knowledge of $\Gamma$ over time. Roughly speaking, we will mainly concern ourselves with the case where ${\overline{D}}$ eventually rules out all and only the worlds that are inconsistent with $\Gamma$.

**Definition 6** (World). _A **world** is any truth assignment $\mathbb{W}:\mathcal{S}\to{\mathbb{B}}$. If $\mathbb{W}(\phi)=1$ we say that $\phi$ is **true in $\mathbb{W}$**. If $\mathbb{W}(\phi)=0$ we say that $\phi$ is **false in $\mathbb{W}$**. We write $\mathcal{W}$ for the set of all worlds._

Observe that worlds are valuations, and that they are not necessarily consistent. This terminology is nonstandard; the term “world” is usually reserved for consistent truth assignments. Logically uncertain reasoners cannot immediately tell which truth assignments are inconsistent, because revealing inconsistencies requires time and effort. We use the following notion of consistency:

**Definition 7** (Propositional Consistency). _A world $\mathbb{W}$ is called **propositionally consistent**, abbreviated **p.c.**, if for all $\phi\in\mathcal{S}$, $\mathbb{W}(\phi)$ is determined by Boolean algebra from the truth values that $\mathbb{W}$ assigns to the prime sentences of $\phi$. In other words, $\mathbb{W}$ is p.c. if $\mathbb{W}(\phi\land\psi) = \mathbb{W}(\phi) \land \mathbb{W}(\psi)$, $\mathbb{W}(\phi\lor\psi) = \mathbb{W}(\phi)\lor\mathbb{W}(\psi)$, and so on._

_Given a set of sentences $D$, we define $\mathcal{PC}(D)$ to be the set of all p.c. worlds where $\mathbb{W}(\phi)=1$ for all $\phi\in D$. We refer to $\mathcal{PC}(D)$ as the set of worlds **propositionally consistent with $\boldsymbol{D}$**._

_Given a set of sentences $\Gamma$ interpreted as a theory, we will refer to $\mathcal{PC}(\Gamma)$ as the set of worlds **consistent with $\boldsymbol{\Gamma}$**, because in this case $\mathcal{PC}(\Gamma)$ is equal to the set of all worlds $\mathbb{W}$ such that 

$$
\Gamma\cup \{\phi\mid \mathbb{W}(\phi)=1\} \cup \{\neg\phi \mid \mathbb{W}(\phi)=0\} \nvdash \bot.
$$

_

Note that a limited reasoner won’t be able to tell whether a given world $\mathbb{W}$ is in $\mathcal{PC}(\Gamma)$. A reasoner can computably check whether a restriction of $\mathbb{W}$ to a finite domain is propositionally consistent with a finite set of sentences, but that’s about it. Roughly speaking, the definition of exploitation (below) will say that a good reasoner should perform well when measured on day $n$ by worlds propositionally consistent with $D_n$, and we ourselves will be interested in deductive processes that pin down a particular theory $\Gamma$ by propositional consistency:

**Definition 8** ($\Gamma$\-Complete). _Given a theory $\Gamma$, we say that a deductive process ${\overline{D}}$ is **$\boldsymbol{\Gamma}$\-complete** if 

$$
\mathcal{PC}(D_\infty) = \mathcal{PC}(\Gamma).
$$

_

As a canonical example, let $D_n$ be the set of all theorems of ${\mathsf{PA}}$ provable in at most $n$ characters.[^note-1] Then ${\overline{D}}$ is ${\mathsf{PA}}$\-complete, and a reasoner with access to ${\overline{D}}$ can be interpreted as someone who on day $n$ knows all ${\mathsf{PA}}$\-theorems provable in $\leq n$ characters, who must manage her uncertainty about other mathematical facts.

### Efficient Computability ^efficient-computability

We use the following notion of efficiency throughout the paper:

An infinite sequence ${\overline{x}}$ is called **efficiently computable**, abbreviated **e.c.**, if there is a computable function $f$ that outputs $x_n$ on input $n$, with runtime polynomial in $n$ (i.e. in the length of $n$ written in unary).

Our framework is not wedded to this definition; stricter notions of efficiency (e.g., sequences that can be computed in ${\mathcal{O}}(n^2)$ time) would yield “dumber” inductors with better runtimes, and vice versa. We use the set of polynomial-time computable functions because it has some closure properties that are convenient for our purposes.

### Traders ^traders

Roughly speaking, traders are functions that see the day $n$ and the history of market prices up to and including day $n$, and then produce a series of buy and sell orders, by executing a strategy that is continuous as a function of the market history.

A linear combination of sentences can be interpreted as a “market order”, where $3\phi - 2\psi$ says to buy 3 shares of $\phi$ and sell 2 shares of $\psi$. Very roughly, a trading strategy for day $n$ will be a method for producing market orders where the coefficients are not numbers but _functions_ which depend (continuously) on the market prices up to and including day $n$.

**Definition 9** (Valuation Feature). _A valuation **feature** $\alpha: [0, 1]^{\mathcal{S}\times {\mathbb{N}}^+} \to {\mathbb{R}}$ is a continuous function from valuation sequences to real numbers such that $\alpha({\overline{\mathbb{V}}})$ depends only on the initial sequence $\mathbb{V}_{\le n}$ for some $n\in{\mathbb{N}}^+$ called the _rank_ of the feature, $\operatorname{rank}(\alpha)$. For any $m\geq n$, we define $\alpha(\mathbb{V}_{\leq m})$ in the natural way. We will often deal with features that have range in $[0, 1]$; we call these $[0,1]$\-features._

_We write $\mathcal{F}$ for the set of all features, $\mathcal{F}_n$ for the set of valuation features of rank $\le n$, and define an **$\boldsymbol{\mathcal{F}}$\-progression** ${\overline{\alpha}}$ to be a sequence of features such that $\alpha_n\in \mathcal{F}_n$._

The following valuation features find the price of a sentence on a particular day:

**Definition 10** (Price Feature). _For each $\phi\in\mathcal{S}$ and $n\in{\mathbb{N}}^+$, we define a **price feature** $\phi^{*n} \in \mathcal{F}_n$ by the formula 

$$
{\phi}^{*n}({\overline{\mathbb{V}}}) := \mathbb{V}_n(\phi).
$$

 We call these “price features” because they will almost always be applied to a market ${\overline{\mathbb{P}}}$, in which case ${\phi}^{*n}$ gives the price $\mathbb{P}_n(\phi)$ of $\phi$ on day $n$ as a function of ${\overline{\mathbb{P}}}$._

Very roughly, trading strategies will be linear combinations of sentences where the coefficients are valuation features. The set of all valuation features is not computably enumerable, so we define an expressible subset:

**Definition 11** (Expressible Feature). _An **expressible feature** $\xi\in \mathcal{F}$ is a valuation feature expressible by an algebraic expression built from price features ${\phi}^{*n}$ for each $n\in{\mathbb{N}}^+$ and $\phi\in\mathcal{S}$, rational numbers, addition, multiplication, $\max(-, -)$, and a “safe reciprocation” function $\max(1,-)^{-1}$. See Appendix [[#^expressible-features|8.2]] for more details and examples. [^note-2]_

_We write $\mathcal{E\!F}$ for the set of all expressible features, $\mathcal{E\!F}_n$ for the set of expressible features of rank $\leq n$, and define an **$\boldsymbol{\mathcal{E\!F}}$\-progression** to be a sequence ${\overline{\xi}}$ such that $\xi_n\in\mathcal{E\!F}_n$._

For those familiar with abstract algebra, note that for each $n$, $\mathcal{E\!F}_n$ is a commutative ring. We will write $2 - {\phi}^{*6}$ for the function ${\overline{\mathbb{V}}} \mapsto 2 - {\phi}^{*6}({\overline{\mathbb{V}}})$ and so on, in the usual way. For example, the feature 

$$
\xi:= \max(0, {\phi}^{*6} - {\psi}^{*7})
$$

 checks whether the value of $\phi$ on day 6 is higher than the value of $\psi$ on day 7. If so, it returns the difference; otherwise, it returns 0. If $\xi$ is applied to a market ${\overline{\mathbb{P}}}$, and $\mathbb{P}_6(\phi)=0.5$ and $\mathbb{P}_7(\psi)=0.2$, then $\xi({\overline{\mathbb{P}}})=0.3$. Observe that $\operatorname{rank}(\xi)=7$, and that $\xi$ is continuous.

The reason for the continuity constraint on valuation features is as follows. Traders will be allowed to use valuation features (which depend on the price history) to decide how many shares of different sentences to buy and sell. This creates a delicate situation, because we’ll be constructing a market that has prices which depend on the behavior of certain traders, creating a circular dependency where the prices depend on trades that depend on the prices.

This circularity is related to classic paradoxes of self-trust. What should be the price on a paradoxical sentence $\chi$ that says “I am true iff my price is less than 50 cents in this market”? If the price is less than 50¢, then $\chi$ pays out \$1, and traders can make a fortune buying $\chi$. If the price is 50¢ or higher, then $\chi$ pays out \$0, and traders can make a fortune selling $\chi$. If traders are allowed to have a discontinuous trading strategy—buy $\chi$ if $\mathbb{P}(\chi)<0.5$, sell $\chi$ otherwise—then there is no way to find prices that clear the market.

Continuity breaks the circularity, by ensuring that if there’s a price where a trader buys $\chi$ and a price where they sell $\chi$ then there’s a price in between where they neither buy nor sell. In Section [[#^construction|5]] we will see that this is sufficient to allow stable prices to be found, and in Section [[#^introspection|4.11]] we will see that it is sufficient to subvert the standard paradoxes of self-reference. The continuity constraint can be interpreted as saying that the trader has only finite-precision access to the market prices—they can see the prices, but there is some $\varepsilon > 0$ such that their behavior is insensitive to an $\varepsilon$ shift in prices.

We are almost ready to define trading strategies as a linear combination of sentences with expressible features as coefficients. However, there is one more complication. It will be convenient to record not only the amount of shares bought and sold, but also the amount of cash spent or received. For example, consider again the market order $3\phi - 2\psi$. If it is executed on day 7 in a market ${\overline{\mathbb{P}}}$, and $\mathbb{P}_7(\phi)=0.4$ and $\mathbb{P}_7(\psi)=0.3$, then the cost is $3\cdot 40\textnormal{\textnormal{¢}} - 2\cdot 30\textnormal{\textnormal{¢}} = 60\textnormal{\textnormal{¢}}$. We can record the whole trade as an affine combination $-0.6 + 3\phi - 2\psi$, which can be read as “the trader spent 60 cents to buy 3 shares of $\phi$ and sell 2 shares of $\psi$”. Extending this idea to the case where the coefficients are expressible features, we get the following notion:

**Definition 12** (Trading Strategy). _A **trading strategy for day $n$**, also called an **$\boldsymbol{n}$\-strategy**, is an affine combination of the form 

$$
T= c+ \xi_1\phi_1 + \cdots + \xi_k\phi_k,
$$

 where $\phi_1,\ldots,\phi_k$ are sentences, $\xi_1,\ldots,\xi_k$ are expressible features of rank $\leq n$, and 

$$
c= -\sum_i \xi_i {\phi_i}^{*n}
$$

 is a “cash term” recording the net cash flow when executing a transaction that buys $\xi_i$ shares of $\phi_i$ for each $i$ at the prevailing market price. (Buying negative shares is called “selling”.) We define $T[1]$ to be $c$, and $T[\phi]$ to be the coefficient of $\phi$ in $T$, which is $0$ if $\phi \not\in (\phi_1, \ldots, \phi_k)$._

_An $n$\-strategy $T$ can be encoded by the tuples $(\phi_1,\ldots\phi_k)$ and $(\xi_1,\ldots\xi_k)$ because the $c$ term is determined by them. Explicitly, by linearity we have 

$$
T= \xi_1 \cdot (\phi_1 - {\phi_1}^{*n}) + \cdots + \xi_k \cdot (\phi_k - {\phi_k}^{*n}),
$$

 which means any $n$\-strategy can be written as a linear combination of $(\phi_i - {\phi_i}^{*n})$ terms, each of which means “buy one share of $\phi_i$ at the prevailing price”._

As an example, consider the following trading strategy for day 5: 

$$
\left[
    {(\lnot\lnot\phi)}^{*5} - {\phi}^{*5}
  \right]
  \cdot
  \left(
    \phi - {\phi}^{*5}
  \right)
  +
  \left[
    {\phi}^{*5} - {(\lnot\lnot\phi)}^{*5}
  \right]
  \cdot
  \left(
    \lnot\lnot\phi - {(\lnot\lnot\phi)}^{*5}
  \right).
$$

 This strategy compares the price of $\phi$ on day 5 to the price of $\lnot\lnot\phi$ on day 5. If the former is less expensive by $\delta$, it purchases $\delta$ shares of $\phi$ at the prevailing prices, and sells $\delta$ shares of $\lnot\lnot\phi$ at the prevailing prices. Otherwise, it does the opposite. In short, this strategy arbitrages $\phi$ against $\lnot\lnot\phi$, by buying the cheaper one and selling the more expensive one.

We can now state the key definition of this section:

A **trader** ${\overline{T}}$ is a sequence $(T_1, T_2, \ldots)$ where each $T_n$ is a trading strategy for day $n$.

We can visualize a trader as a person who gets to see the day $n$, think for a while, and then produce a trading strategy for day $n$, which will observe the history of market prices up to and including day $n$ and execute a market order to buy and sell different sentences at the prevailing market prices.

We will often consider the set of efficiently computable traders, which have to produce their trading strategy in a time polynomial in $n$. We can visualize e.c. traders as traders who are computationally limited: each day they get to think for longer and longer—we can imagine them writing computer programs each morning that assist them in their analysis of the market prices—but their total runtime may only grow polynomially in $n$.

If $s := T_n[\phi] > 0$, we say that ${\overline{T}}$ buys $s$ shares of $\phi$ on day $n$, and if $s < 0$, we say that ${\overline{T}}$ sells $|s|$ shares of $\phi$ on day $n$. Similarly, if $d := T_n[1] > 0$, we say that ${\overline{T}}$ receives $d$ dollars on day $n$, and if $d < 0$, we say that ${\overline{T}}$ pays out $|d|$ dollars on day $n$.

Each trade $T_n$ has value zero according to $\mathbb{P}_n$, regardless of what market ${\overline{\mathbb{P}}}$ it is executed in. Clever traders are the ones who make trades that are later revealed by a deductive process ${\overline{D}}$ to have a high worth (e.g., by purchasing shares of provable sentences when the price is low). As an example, a trader ${\overline{T}}$ with a basic grasp of arithmetic and skepticism about some of the market ${\overline{\mathbb{P}}}$’s confident conjectures might execute the following trade orders on day $n$:

Visualizing markets and trades

| Sentence | Market prices | Trade |
| --- | --- | --- |
| $\phi :\leftrightarrow 1+1=2$ | $\mathbb{P}_n(\phi)=90$¢ | $T_n[\phi] = 4$ shares |
| $\psi :\leftrightarrow 1+1\neq 2$ | $\mathbb{P}_n(\psi)=5$¢ | $T_n[\psi] = -3$ shares |
| $\chi :\leftrightarrow  \text{“}\textnormal{Goldbach's conjecture}\text{”}$ | $\mathbb{P}_n(\chi) = 98$¢ | $T_n[\chi] = -1$ share |

The net value of the shares bought and sold at these prices would be 

$$
4 \cdot 90\textnormal{\textnormal{¢}} - 3 \cdot 5\textnormal{\textnormal{¢}} - 1 \cdot 98\textnormal{\textnormal{¢}} = \text{\textdollar}2.47,
$$

 so if those three sentences were the only sentences bought and sold by $T_n$, $T_n[1]$ would be $-2.47$.

Trade strategies are a special case of affine combinations of sentences:

**Definition 13** (Affine Combination). _An **$\boldsymbol{\mathcal{F}}$\-combination** $A: \mathcal{S}\cup \{1\} \to \mathcal{F}$ is an affine expression of the form 

$$
A:= c+ \alpha_1\phi_1 + \cdots + \alpha_k\phi_k,
$$

 where $(\phi_1,\ldots,\phi_k)$ are sentences and $(c, \alpha_1, \ldots, \alpha_k)$ are in $\mathcal{F}$. We define **${\mathbb{R}}$\-combinations**, **${\mathbb{Q}}$\-combinations**, and **$\boldsymbol{\mathcal{E\!F}}$\-combinations** analogously._

_We write $A[1]$ for the trailing coefficient $c$, and $A[\phi]$ for the coefficient of $\phi$, which is $0$ if $\phi \not\in (\phi_1, \ldots, \phi_k)$. The **rank** of $A$ is defined to be the maximum rank among all its coefficients. Given any valuation $\mathbb{V}$, we abuse notation in the usual way and define the **value** of $A$ (according to $\mathbb{V}$) linearly by: 

$$
\mathbb{V}(A) := c+ \alpha_1\mathbb{V}(\phi_1) + \cdots + \alpha_k\mathbb{V}(\phi_k).
$$

 An **$\boldsymbol{\mathcal{F}}$\-combination progression** is a sequence ${\overline{A}}$ of affine combinations where $A_n$ has rank $\le n$. An **$\boldsymbol{\mathcal{E\!F}}$\-combination progression** is defined similarly._

Note that a trade $T$ is an $\mathcal{F}$\-combination, and the holdings $T({\overline{\mathbb{P}}})$ from $T$ against ${\overline{\mathbb{P}}}$ is a ${\mathbb{Q}}$\-combination. We will use affine combinations to encode the net holdings $\sum_{i\leq n}T_i({\overline{\mathbb{P}}})$ of a trader after interacting with a market ${\overline{\mathbb{P}}}$, and later to encode linear inequalities that hold between the truth values of different sentences.

### Exploitation ^exploitation

We will now define exploitation, beginning with an example. Let $\mathcal{L}$ be the language of ${\mathsf{PA}}$, and ${\overline{D}}$ be a ${\mathsf{PA}}$\-complete deductive process. Consider a market ${\overline{\mathbb{P}}}$ that assigns $\mathbb{P}_n(\text{“}1+1=2\text{”})=0.5$ for all $n$, and a trader who buys one share of $\text{“}1+1=2\text{”}$ each day. Imagine a reasoner behind the market obligated to buy and sell shares at the listed prices, who is also obligated to pay out \$1 to holders of $\phi$\-shares if and when ${\overline{D}}$ says $\phi$. Let $t$ be the first day when $\text{“}1+1=2\text{”}\in D_t$. On each day, the reasoner receives 50¢ from ${\overline{T}}$, but after day $t$, the reasoner must pay \$1 every day thereafter. They lose 50¢ each day, and ${\overline{T}}$ gains 50¢ each day, despite the fact that ${\overline{T}}$ never risked more than $\text{\textdollar}t/2$. In cases like these, we say that ${\overline{T}}$ exploits ${\overline{\mathbb{P}}}$.

With this example in mind, we define exploitation as follows:

A trader ${\overline{T}}$ is said to **exploit** a valuation sequence ${\overline{\mathbb{V}}}$ relative to a deductive process ${\overline{D}}$ if the set of values 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T_i\left({\overline{\mathbb{V}}}\right)}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \right\}
$$

 is bounded below, but not bounded above.

Given a world $\mathbb{W}$, the number $\mathbb{W}(\sum_{i \leq n}T_i({\overline{\mathbb{P}}}))$ is the value of the trader’s net holdings after interacting with the market ${\overline{\mathbb{P}}}$, where a share of $\phi$ is valued at \$1 if $\phi$ is true in $\mathbb{W}$ and \$0 otherwise. The set $\{ \mathbb{W}(\sum_{i \leq n} T_i({\overline{\mathbb{P}}})) \mid n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \}$ is the set of all assessments of ${\overline{T}}$’s net worth, across all time, according to worlds that were propositionally consistent with ${\overline{D}}$ at the time. We informally call these _plausible assessments_ of the trader’s net worth. Using this terminology, Definition (Exploitation) above says that a trader exploits the market if their plausible net worth is bounded below, but not above.

Roughly speaking, we can imagine that there is a person behind the market who acts as a market maker, obligated to buy and sell shares at the listed prices. We can imagine that anyone who sold a $\phi$\-share is obligated to pay \$1 if and when ${\overline{D}}$ says $\phi$. Then, very roughly, a trader exploits the market if they are able to make unbounded returns off of a finite investment.

This analogy is illustrative but incomplete—traders can exploit the market even if they never purchase a sentence that appears in ${\overline{D}}$. For example, let $\phi$ and $\psi$ be two sentences such that $(\phi \lor \psi)$ is provable in ${\mathsf{PA}}$, but such that neither $\phi$ nor $\psi$ is provable in ${\mathsf{PA}}$. Consider a trader that bought 10 $\phi$\-shares at a price of 20¢ each, and 10 $\psi$\-shares at a price of 30¢ each. Once ${\overline{D}}$ says $(\phi\lor\psi)$, all remaining p.c. worlds will agree that the portfolio $-5 + 10\phi + 10\psi$ has a value of at least +5, despite the fact that neither $\phi$ nor $\psi$ is ever proven. If the trader is allowed to keep buying $\phi$ and $\psi$ shares at those prices, they would exploit the market, despite the fact that they never buy decidable sentences. In other words, our notion of exploitation rewards traders for arbitrage, even if they arbitrage between sentences that never “pay out”.

### Main Result ^main-result

Recall the logical induction criterion:

**Definition 14** (The Logical Induction Criterion). _A market ${\overline{\mathbb{P}}}$ is said to satisfy the **logical induction criterion** relative to a deductive process ${\overline{D}}$ if there is no efficiently computable trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$. A market ${\overline{\mathbb{P}}}$ meeting this criterion is called a **logical inductor over $\boldsymbol{{\overline{D}}}$**._

We may now state our main result:

**Theorem 15**. _For any deductive process ${\overline{D}}$, there exists a computable belief sequence ${\overline{\mathbb{P}}}$ satisfying the logical induction criterion relative to ${\overline{D}}$._

_Proof._ In Section [[#^construction|5]], we show how to take an arbitrary deductive process ${\overline{D}}$ and construct a computable belief sequence ${\overline{\textnormal{{\texttt{LIA}}}}}$. Theorem 100 shows that ${\overline{\textnormal{{\texttt{LIA}}}}}$ is a logical inductor relative to the given ${\overline{D}}$. ◻

**Definition 16** (Logical Inductor over $\Gamma$). _Given a theory $\Gamma$, a logical inductor over a $\Gamma$\-complete deductive process ${\overline{D}}$ is called a **logical inductor over $\boldsymbol\Gamma$**._

**Corollary 17**. _For any recursively axiomatizable theory $\Gamma$, there exists a computable belief sequence that is a logical inductor over $\Gamma$._

## Properties of Logical Inductors ^properties-of-logical-inductors

Here is an intuitive argument that logical inductors perform good reasoning under logical uncertainty:

> Consider any polynomial-time method for efficiently identifying patterns in logic. If the market prices don’t learn to reflect that pattern, a clever trader can use that pattern to exploit the market. Thus, a logical inductor must learn to identify those patterns.

In this section, we will provide evidence supporting this intuitive argument, by demonstrating a number of desirable properties possessed by logical inductors. The properties that we demonstrate are broken into twelve categories:

1.  **Convergence and Coherence:** In the limit, the prices of a logical inductor describe a belief state which is fully logically consistent, and represents a probability distribution over all consistent worlds.
    
2.  **Timely Learning:** For any efficiently computable sequence of theorems, a logical inductor learns to assign them high probability in a timely manner, regardless of how difficult they are to prove. (And similarly for assigning low probabilities to refutable statements.)
    
3.  **Calibration and Unbiasedness:** Logical inductors are well-calibrated and, given good feedback, unbiased.
    
4.  **Learning Statistical Patterns:** If a sequence of sentences appears pseudorandom to all reasoners with the same runtime as the logical inductor, it learns the appropriate statistical summary (assigning, e.g., 10% probability to the claim “the $n$th digit of $\pi$ is a 7” for large $n$, if digits of $\pi$ are actually hard to predict).
    
5.  **Learning Logical Relationships:** Logical inductors inductively learn to respect logical constraints that hold between different types of claims, such as by ensuring that mutually exclusive sentences have probabilities summing to at most 1.
    
6.  **Non-Dogmatism:** The probability that a logical inductor assigns to an independent sentence $\phi$ is bounded away from 0 and 1 in the limit, by an amount dependent on the complexity of $\phi$. In fact, logical inductors strictly dominate the universal semimeasure in the limit. This means that we can condition logical inductors on independent sentences, and when we do, they perform empirical induction.
    
7.  **Conditionals:** Given a logical inductor ${\overline{\mathbb{P}}}$, the market given by the conditional probabilities ${\overline{\mathbb{P}}}(-\mid\psi)$ is a logical inductor over ${\overline{D}}$ extended to include $\psi$. Thus, when we condition logical inductors on new axioms, they continue to perform logical induction.
    
8.  **Expectations:** Logical inductors give rise to a well-behaved notion of the expected value of a logically uncertain variable.
    
9.  **Trust in Consistency:** If the theory $\Gamma$ underlying a logical inductor’s deductive process is expressive enough to talk about itself, then the logical inductor learns inductively to trust $\Gamma$.
    
10.  **Reasoning about Halting:** If there’s an efficient method for generating programs that halt, a logical inductor will learn in a timely manner that those programs halt (often long before having the resources to evaluate them). If there’s an efficient method for generating programs that don’t halt, a logical inductor will at least learn not to expect them to halt for a very long time.
     
11.  **Introspection:** Logical inductors “know what they know”, in that their beliefs about their current probabilities and expectations are accurate.
     
12.  **Self-Trust:** Logical inductors trust their future beliefs.
     

For the sake of brevity, proofs are deferred to Section [[#^selected-proofs|6]] and the appendix. Some example proofs are sketched in this section, by outlining discontinuous traders that would exploit any market that lacked the desired property. The deferred proofs define polynomial-time continuous traders that approximate those discontinuous strategies.

In what follows, let $\mathcal{L}$ be a language of propositional logic; let $\mathcal{S}$ be the set of sentences written in $\mathcal{L}$; let $\Gamma\subset \mathcal{S}$ be a computably enumerable set of propositional formulas written in $\mathcal{L}$ (such as $\mathsf{PA}$, where the propositional variables are prime sentences in first-order logic, as discussed in Section [[#^notation|2]]); and let ${\overline{\mathbb{P}}}$ be a computable logical inductor over $\Gamma$, i.e., a market satisfying the logical induction criterion relative to some $\Gamma$\-complete deductive process ${\overline{D}}$. We assume in this section that $\Gamma$ is consistent.

Note that while the computable belief sequence ${\overline{\textnormal{{\texttt{LIA}}}}}$ that we define has finite support on each day, in this section we assume only that ${\overline{\mathbb{P}}}$ is a market. We do this because our results below hold in this more general case, and can be applied to ${\overline{\textnormal{{\texttt{LIA}}}}}$ as a special case.

In sections [[#^expectations|4.8]]\-[[#^self-trust|4.12]] we will assume that $\Gamma$ can represent computable functions. This assumption is not necessary until Section [[#^expectations|4.8]].

### Convergence and Coherence ^convergence-and-coherence

Firstly, the market prices of a logical inductor converge:

**Theorem 18** (Convergence). _The limit ${\mathbb{P}_\infty:\mathcal{S}\rightarrow[0,1]}$ defined by 

$$
\mathbb{P}_\infty(\phi) := \lim_{n\rightarrow\infty} \mathbb{P}_n(\phi)
$$

 exists for all $\phi$._

_Proof sketch._

> Roughly speaking, if ${\overline{\mathbb{P}}}$ never makes up its mind about $\phi$, then it can be exploited by a trader arbitraging shares of $\phi$ across different days. More precisely, suppose by way of contradiction that the limit $\mathbb{P}_\infty(\phi)$ does not exist. Then for some $p\in [0, 1]$ and $\varepsilon > 0$, we have $\mathbb{P}_n(\phi) < p-\varepsilon$ infinitely often and also $\mathbb{P}_n(\phi) > p+\varepsilon$ infinitely often. A trader can wait until $\mathbb{P}_n(\phi) < p-\varepsilon$ and then buy a share in $\phi$ at the low market price of $\mathbb{P}_n(\phi)$. Then the trader waits until some later $m$ such that $\mathbb{P}_m(\phi) > p+\varepsilon$, and sells back the share in $\phi$ at the higher price. This trader makes a total profit of $2\varepsilon$ every time $\mathbb{P}_n(\phi)$ oscillates in this way, at no risk, and therefore exploits ${\overline{\mathbb{P}}}$. Since ${\overline{\mathbb{P}}}$ implements a logical inductor, this is not possible; therefore the limit $\mathbb{P}_\infty(\phi)$ must in fact exist.

This sketch showcases the main intuition for the convergence of ${\overline{\mathbb{P}}}$, but elides a number of crucial details. In particular, the trader we have sketched makes use of discontinuous trading functions, and so is not a well-formed trader. These details are treated in Section [[#^convergence|6.1]].

Next, the limiting beliefs of a logical inductor represent a coherent probability distribution:

**Theorem 19** (Limit Coherence). _$\mathbb{P}_\infty$ is coherent, i.e., it gives rise to an internally consistent probability measure $\mathrm{Pr}$ on the set $\mathcal{PC}(\Gamma)$ of all worlds consistent with $\Gamma$, defined by the formula 

$$
\mathrm{Pr}(\mathbb{W}(\phi)=1):=\mathbb{P}_\infty(\phi).
$$

 In particular, if $\Gamma$ contains the axioms of first-order logic, then $\mathbb{P}_\infty$ defines a probability measure on the set of first-order completions of $\Gamma$._

_Proof sketch._

> The limit $\mathbb{P}_\infty(\phi)$ exists by the convergence theorem, so $\mathrm{Pr}$ is well-defined. Gaifman (1964) shows that $\mathrm{Pr}$ defines a probability measure over $\mathcal{PC}(D_\infty)$ so long as the following three implications hold for all sentences $\phi$ and $\psi$:
> 
> -   If $\Gamma\vdash \phi$, then $\mathbb{P}_\infty(\phi) = 1$,
>     
> -   If $\Gamma\vdash \lnot \phi$, then $\mathbb{P}_\infty(\phi) = 0$,
>     
> -   If $\Gamma\vdash \lnot(\phi \land \psi)$, then $\mathbb{P}_\infty(\phi \lor \psi) = \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi)$.
>     
> 
> Let us demonstrate each of these three properties.
> 
> First suppose that $\Gamma\vdash \phi$, but $\mathbb{P}_\infty(\phi) = 1-\varepsilon$ for some $\varepsilon>0$. Then shares of $\phi$ will be underpriced, as they are worth 1 in every consistent world, but only cost $1-\varepsilon$. There is a trader who waits until $\phi$ is propositionally provable from $D_n$, and until $\mathbb{P}_n(\phi)$ has approximately converged, and then starts buying shares of $\phi$ every day at the price $\mathbb{P}_n(\phi)$. Since $\phi$ has appeared in ${\overline{D}}$, the shares immediately have a minimum plausible value of \$1\. Thus the trader makes $1-\mathbb{P}_n(\phi) \approx \varepsilon$ profit every day, earning an unbounded total value, contradicting the logical induction criterion. But ${\overline{\mathbb{P}}}$ cannot be exploited, so $\mathbb{P}_\infty(\phi)$ must be 1.
> 
> Similarly, if $\Gamma\vdash \lnot\phi$ but $\mathbb{P}_\infty(\phi) = \varepsilon>0$, then a trader could exploit ${\overline{\mathbb{P}}}$ by selling off shares in $\phi$ for a profit of $\mathbb{P}_n(\phi)\approx \varepsilon$ each day.
> 
> Finally, suppose that $\Gamma\vdash \lnot(\phi \land \psi)$, but for some $\varepsilon > 0$, 
> 
> $$
> \mathbb{P}_\infty(\phi \lor \psi) = \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi) \pm \varepsilon.
> $$
> 
>  Then there is a trader that waits until $\mathbb{P}_n$ has approximately converged on these sentences, and until $\lnot(\phi \land \psi)$ is propositionally provable from $D_n$. At that point it’s a good deal to sell (buy) a share in $\phi \lor \psi$, and buy (sell) a share in each of $\phi$ and $\psi$; the stocks will have values that cancel out in every plausible world. Thus this trader makes a profit of $\approx \varepsilon$ from the price differential, and can then repeat the process. Thus, they would exploit ${\overline{\mathbb{P}}}$. But this is impossible, so $\mathbb{P}_\infty$ must be coherent.

Theorem 129 says that if ${\overline{\mathbb{P}}}$ were allowed to run forever, and we interpreted its prices as probabilities, then we would find its beliefs to be perfectly consistent. In the limit, ${\overline{\mathbb{P}}}$ assigns probability 1 to every theorem and 0 to every contradiction. On independent sentences, its beliefs obey the constraints of probability theory; if $\phi$ provably implies $\psi$, then the probability of $\psi$ converges to a point no lower than the limiting probability of $\phi$, regardless of whether they are decidable. The resulting probabilities correspond to a probability distribution over all possible ways that $\Gamma$ could be completed.

This justifies interpreting the market prices of a logical inductor as probabilities. Logical inductors are not the first computable procedure for assigning probabilities to sentences in a manner that is coherent in the limit; the algorithm of Demski (2012) also has this property. The main appeal of logical induction is that their beliefs become reasonable in a timely manner, outpacing the underlying deductive process.

### Timely Learning ^timely-learning

It is not too difficult to define a reasoner that assigns probability 1 to all (and only) the provable sentences, in the limit: simply assign probability 0 to all sentences, and then enumerate all logical proofs, and assign probability 1 to the proven sentences. The real trick is to recognize patterns in a timely manner, well before the sentences can be proven by slow deduction.

Logical inductors learn to outpace deduction on any efficiently computable sequence of provable statements.[^note-3] To illustrate, consider our canonical example where $D_n$ is the set of all theorems of ${\mathsf{PA}}$ provable in at most $n$ characters, and suppose ${\overline{\phi}}$ is an e.c. sequence of theorems which are easy to generate but difficult to prove. Let $f(n)$ be the length of the shortest proof of $\phi_n$, and assume that $f$ is some fast-growing function. At any given time $n$, the statement $\phi_n$ is ever further out beyond $D_n$—it might take 1 day to prove $\phi_1$, 10 days to prove $\phi_2$, 100 days to prove $\phi_3$, and so on. One might therefore expect that $\phi_n$ will also be “out of reach” for $\mathbb{P}_n$, and that we have to wait until a much later day close to $f(n)$ before expecting $\mathbb{P}_{f(n)}(\phi_n)$ to be accurate. However, this is not the case! After some finite time $N$, $\smash{{\overline{\mathbb{P}}}}$ will recognize the pattern and begin assigning high probability to ${\overline{\phi}}$ in a timely manner.

**Theorem 20** (Provability Induction). _Let ${\overline{\phi}}$ be an e.c. sequence of theorems. Then 

$$
\mathbb{P}_n(\phi_n) \eqsim_n1.
$$

 Furthermore, let ${\overline{\psi}}$ be an e.c. sequence of disprovable sentences. Then 

$$
\mathbb{P}_n(\psi_n) \eqsim_n0.
$$

_

_Proof sketch._

> Consider a trader that acts as follows. First wait until the time $a$ when $\mathbb{P}_a(\phi_a)$ drops below $1 - \varepsilon$ and buy a share of $\phi_a$. Then wait until $\phi_a$ is worth 1 in all worlds plausible at time $f(a)$. Then repeat this process. If $\mathbb{P}_n(\phi_n)$ drops below $1 - \varepsilon$ infinitely often, then this trader makes $\varepsilon$ profit infinitely often, off of an initial investment of \$1, and therefore exploits the market. ${\overline{\mathbb{P}}}$ is inexploitable, so $\mathbb{P}_n(\phi_n)$ must converge to 1. By a similar argument, $\mathbb{P}_n(\psi_n)$ must converge to 0.[^note-4]

In other words, ${\overline{\mathbb{P}}}$ will learn to start believing $\phi_n$ by day $n$ at the latest, despite the fact that $\phi_n$ won’t be deductively confirmed until day $f(n)$, which is potentially much later. In colloquial terms, if ${\overline{\phi}}$ is a sequence of facts that can be generated efficiently, then ${\overline{\mathbb{P}}}$ inductively learns the pattern, and its belief in ${\overline{\phi}}$ becomes accurate faster than ${\overline{D}}$ can computationally verify the individual sentences.

For example, imagine that `prg(n)` is a program with fast-growing runtime, which always outputs either 0, 1, or 2 for all $n$, but such that there is no proof of this in the general case. Then 

$$
\text{“}\forall x \colon \texttt{prg(\(x\))}=0 \lor \texttt{prg(\(x\))}=1 \lor \texttt{prg(\(x\))}=2\text{”}
$$

 is _not_ provable. Now consider the sequence of statements 

$$
{\overline{\mathit{\operatorname{prg012}}}} := \big( \text{“}\texttt{prg(\({\underline{n}}\))}=0 \lor \texttt{prg(\({\underline{n}}\))}=1 \lor \texttt{prg(\({\underline{n}}\))}=2\text{”} \big)_{n\in {{\mathbb{N}}^+}}
$$

 where each $\mathit{\operatorname{prg012}}_n$ states that `prg` outputs a 0, 1, or 2 on that $n$ in particular. Each individual $\mathit{\operatorname{prg012}}_n$ is provable (it can be proven by running `prg` on input $n$), and ${\overline{\mathit{\operatorname{prg012}}}}$ is efficiently computable (because the sentences themselves can be written down quickly, even if `prg` is very difficult to evaluate). Thus, provability induction says that any logical inductor will “learn the pattern” and start assigning high probabilities to each individual $\mathit{\operatorname{prg012}}_n$ no later than day $n$.

Imagine that ${\overline{D}}$ won’t determine the output of `prg(`$n$`)` until the $f(n)$th day, by evaluating `prg(`$n$`)` in full. Provability induction says that ${\overline{\mathbb{P}}}$ will eventually recognize the pattern ${\overline{\mathit{\operatorname{prg012}}}}$ and start assigning high probability to $\mathit{\operatorname{prg012}}_n$ no later than the $n$th day, $f(n)-n$ days before the evaluation finishes. This is true regardless of the size of $f(n)$, so if $f$ is fast-growing, $\smash{{\overline{\mathbb{P}}}}$ will outpace $\smash{{\overline{D}}}$ by an ever-growing margin.

> **Analogy: Ramanujan and Hardy.** Imagine that the statements ${\overline{\phi}}$ are being output by an algorithm that uses heuristics to generate mathematical facts without proofs, playing a role similar to the famously brilliant, often-unrigorous mathematician Srinivasa Ramanujan. Then ${\overline{\mathbb{P}}}$ plays the historical role of the beliefs of the rigorous G.H. Hardy who tries to verify those results according to a slow deductive process ($\smash{{\overline{D}}}$). After Hardy (${\overline{\mathbb{P}}}$) verifies enough of Ramanujan’s claims ($\phi_{\le n}$), he begins to trust Ramanujan, even if the proofs of Ramanujan’s later conjectures are incredibly long, putting them ever-further beyond Hardy’s current abilities to rigorously verify them. In this story, Hardy’s inductive reasoning (and Ramanujan’s also) outpaces his deductive reasoning.

This idiom of assigning the right probabilities to $\phi_n$ no later than day $n$ will be common throughout the paper, so we give it a name.

**Definition 21** (Timely Manner). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences, and ${\overline{{p}}}$ be an e.c. sequence of rational numbers. We say that ${\overline{\mathbb{P}}}$ assigns ${\overline{{p}}}$ to ${\overline{\phi}}$ in a **timely manner** if for every $\varepsilon > 0$, there exists a time $N$ such that for all $n> N$, 

$$
|\mathbb{P}_n(\phi_n) - p_n| < \varepsilon.
$$

 In other words, ${\overline{\mathbb{P}}}$ assigns ${\overline{{p}}}$ to ${\overline{\phi}}$ in a timely manner if 

$$
\mathbb{P}_n(\phi_n) \eqsim_np_n.
$$

_

Note that there are no requirements on how large $N$ gets as a function of $\varepsilon$. As such, when we say that ${\overline{\mathbb{P}}}$ assigns probabilities ${\overline{{p}}}$ to ${\overline{\phi}}$ in a timely manner, it may take a very long time for convergence to occur. (See Section [[#^questions-of-runtime-and|5.5]] for a discussion.)

As an example, imagine the reasoner who recognizes that sentences of the form $\text{“}1+1+\cdots+1\textnormal{\ is even}\text{”}$ are true iff the number of ones is even. Let ${\overline{\phi}}$ be the sequence where $\phi_n$ is the version of that sentence with $2n$ ones. If the reasoner starts writing a probability near 100% in the $\phi_n$ cell by day $n$ at the latest, then intuitively, she has begun incorporating the pattern into her beliefs, and we say that she is assigning high probabilities to ${\overline{\phi}}$ in a timely manner.

We can visualize ourselves as taking ${\overline{\mathbb{P}}}$’s belief states, sorting them by ${\overline{\phi}}$ on one axis and days on another, and then looking at the main diagonal of cells, to check the probability of each $\phi_n$ on day $n$. Checking the $n$th sentence on the $n$th day is a rather arbitrary choice, and we might hope that a good reasoner would assign high probabilities to e.c. sequences of theorems at a faster rate than that. It is easy to show that this is the case, by the closure properties of efficient computability. For example, if ${\overline{\phi}}$ is an e.c. sequence of theorems, then so are ${\overline{\phi}}_{2n}$ and ${\overline{\phi}}_{2n+1}$, which each enumerate half of $\smash{{\overline{\phi}}}$ at twice the speed, so by Theorem 122 (Provability Induction), ${\overline{\mathbb{P}}}$ will eventually learn to believe ${\overline{\phi}}$ at a rate of at least two per day. Similarly, ${\overline{\mathbb{P}}}$ will learn to believe ${\overline{\phi}}_{3n}$ and ${\overline{\phi}}_{n^2}$ and ${\overline{\phi}}_{10n^3 + 3}$ in a timely manner, and so on. Thus, up to polynomial transformations, it doesn’t really matter which diagonal we check when checking whether a logical inductor has begun “noticing a pattern”.

Furthermore, we will show that if ${\overline{\mathbb{P}}}$ assigns the correct probability on the main diagonal, then ${\overline{\mathbb{P}}}$ also learns to keep them there:

**Theorem 22** (Persistence of Knowledge). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences, and ${\overline{{p}}}$ be an e.c. sequence of rational-number probabilities. If $\mathbb{P}_\infty(\phi_n)\eqsim_np_n$, then 

$$
\sup_{m\ge n}|\mathbb{P}_m(\phi_n)-p_n|\eqsim_n0.
$$

 Furthermore, if $\mathbb{P}_\infty(\phi_n)\lesssim_np_n$, then 

$$
\sup_{m\geq n}\mathbb{P}_m(\phi_n)\lesssim_np_n,
$$

 and if $\mathbb{P}_\infty(\phi_n)\gtrsim_np_n$, then 

$$
\inf_{m\geq n}\mathbb{P}_m(\phi_n)\gtrsim_np_n.
$$

_

In other words, if ${\overline{\mathbb{P}}}$ assigns ${\overline{{p}}}$ to ${\overline{\phi}}$ in the limit, then ${\overline{\mathbb{P}}}$ learns to assign probability near $p_n$ to $\phi_n$ at all times $m\ge n$. This theorem paired with the closure properties of the set of efficiently computable sequences means that checking the probability of $\phi_n$ on the $n$th day is a fine way to check whether ${\overline{\mathbb{P}}}$ has begun recognizing a pattern encoded by ${\overline{\phi}}$. As such, we invite the reader to be on the lookout for statements of the form $\mathbb{P}_n(\phi_n)$ as signs that ${\overline{\mathbb{P}}}$ is recognizing a pattern, often in a way that outpaces the underlying deductive process.

Theorems 122 (Provability Induction) and 119 (Persistence of Knowledge) only apply when the pattern of limiting probabilities is itself efficiently computable. For example, consider the sequence of sentences 

$$
{\overline{\mathit{\operatorname{\pi Aeq7}}}} := \big(\text{“}{\underline{\pi}}[{\underline{\operatorname{Ack}}}({\underline{n}}, {\underline{n}})] = 7\text{”}\big)_{n\in {{\mathbb{N}}^+}}
$$

 where $\pi[i]$ is the $i$th digit in the decimal expansion of $\pi$ and $\operatorname{Ack}$ is the Ackermann function. Each individual sentence is decidable, so the limiting probabilities are 0 for some $\mathit{\operatorname{\pi Aeq7}}_n$ and 1 for others. But that pattern of 1s and 0s is not efficiently computable (assuming there is no efficient way to predict the Ackermann digits of $\pi$), so provability induction has nothing to say on the topic.

In cases where the pattern of limiting probabilities are not e.c., we can still show that if ${\overline{\mathbb{P}}}$ is going to make its probabilities follow a certain pattern eventually, then it learns to make its probabilities follow that pattern in a timely manner. For instance, assume that each individual sentence $\mathit{\operatorname{\pi Aeq7}}_n$ (for $n > 4$) is going to spend a long time sitting at 10% probability before eventually being resolved to either 1 or 0. Then ${\overline{\mathbb{P}}}$ will learn to assign $\mathbb{P}_n(\mathit{\operatorname{\pi Aeq7}}_n) \approx 0.1$ in a timely manner:

**Theorem 23** (Preemptive Learning). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
\liminf_{n\to\infty} \mathbb{P}_n(\phi_n) = \liminf_{n\to\infty} \sup_{m\ge n} \mathbb{P}_m(\phi_n).
$$

 Furthermore, 

$$
\limsup_{n\to\infty} \mathbb{P}_n(\phi_n) = \limsup_{n\to\infty}\inf_{m\ge n} \mathbb{P}_m(\phi_n).
$$

_

Let’s unpack Theorem 117. The quantity $\sup_{m\ge n} \mathbb{P}_m(\phi_n)$ is an upper bound on the price $\mathbb{P}_m(\phi_n)$ on or after day $n$, which we can interpret as the highest price tag that that ${\overline{\mathbb{P}}}$ will ever put on $\phi_n$ after we first start checking it on day $n$. We can imagine a sequence of these values: On day $n$, we start watching $\phi_n$. As time goes on, its price travels up and down until eventually settling somewhere. This happens for each $n$. The limit infimum of $\sup_{m\ge n} \mathbb{P}_m(\phi_n)$ is the greatest lower bound $p$ past which a generic $\phi_n$ (for $n$ large) will definitely be pushed after we started watching it. 117 says that if ${\overline{\mathbb{P}}}$ always eventually pushes $\phi_n$ up to a probability at least $p$, then it will learn to assign each $\phi_n$ a probability at least $p$ in a timely manner (and similarly for least upper bounds).

For example, if each individual $\mathit{\operatorname{\pi Aeq7}}_n$ is _eventually_ recognized as a claim about digits of $\pi$ and placed at probability 10% for a long time before being resolved, then ${\overline{\mathbb{P}}}$ learns to assign it probability 10% on the main diagonal. In general, if ${\overline{\mathbb{P}}}$ is going to learn a pattern eventually, it learns it in a timely manner.

This leaves open the question of whether a logical inductor ${\overline{\mathbb{P}}}$ is smart enough to recognize that the ${\overline{\mathit{\operatorname{\pi Aeq7}}}}$ should each have probability 10% before they are settled (assuming the Ackermann digits of $\pi$ are hard to predict). We will return to that question in Section [[#^learning-statistical-patterns|4.4]], but first, we examine the reverse question.

### Calibration and Unbiasedness ^calibration-and-unbiasedness

Theorem 122 (Provability Induction) shows that logical inductors are good at detecting patterns in what is provable. Next, we ask: when a logical inductor learns a pattern, when must that pattern be real? In common parlance, a source of probabilistic estimates is called _well calibrated_ if among statements where it assigns a probability near $p$, the estimates are correct with frequency roughly $p$.

In the case of reasoning under logical uncertainty, measuring calibration is not easy. Consider the sequence ${\overline{\mathit{\operatorname{clusters}}}}$ constructed from correlated clusters of size 1, 10, 100, 1000, …, where the truth value of each cluster is determined by the parity of a late digit of $\pi$: 

$$
\begin{align*}
  \mathit{\operatorname{clusters}}_1 :\leftrightarrow& \text{“}\pi[\operatorname{Ack}(1,1)]\textnormal{ is even}\text{”} \\
  \mathit{\operatorname{clusters}}_2 :\leftrightarrow\cdots :\leftrightarrow\mathit{\operatorname{clusters}}_{11} :\leftrightarrow& \text{“}\pi[\operatorname{Ack}(2,2)]\textnormal{ is even}\text{”} \\
  \mathit{\operatorname{clusters}}_{12} :\leftrightarrow\cdots :\leftrightarrow\mathit{\operatorname{clusters}}_{111} :\leftrightarrow& \text{“}\pi[\operatorname{Ack}(3,3)]\textnormal{ is even}\text{”} \\
  \mathit{\operatorname{clusters}}_{112} :\leftrightarrow\cdots :\leftrightarrow\mathit{\operatorname{clusters}}_{1111} :\leftrightarrow& \text{“}\pi[\operatorname{Ack}(4,4)]\textnormal{ is even}\text{”}
\end{align*}
$$

 and so on. A reasoner who can’t predict the parity of the Ackermann digits of $\pi$ should assign 50% (marginal) probability to any individual $\mathit{\operatorname{clusters}}_n$ for $n$ large. But consider what happens if the 9th cluster turns out to be true, and the next billion sentences are all true. A reasoner who assigned 50% to those billion sentences was assigning the _right_ probabilities, but their calibration is abysmal: on the billionth day, they have assigned 50% probability a billion sentences that were overwhelmingly true. And if the 12th cluster comes up false, then on the trillionth day, they have assigned 50% probability to a _trillion_ sentences that were overwhelmingly false! In cases like these, the frequency of truth oscillates eternally, and the good reasoner only appears well-calibrated on the rare days where it crosses 50%.

The natural way to correct for correlations such as these is to check ${\overline{\mathbb{P}}}$’s conditional probabilities instead of its marginal probabilities. This doesn’t work very well in our setting, because given a logical sentence $\phi$, the quantity that we care about will almost always be the marginal probability of $\phi$. The reason we deal with sequences is because that lets us show that $\phi$ has reasonable probabilities relative to various related sentences. For example, if $\phi := \text{“}\texttt{prg}(32)=17\text{”}$, then we can use our theorems to relate the probability of $\phi$ to the probability of the sequence $(\text{“}\texttt{prg}({\underline{n}})=17\text{”})_{n\in {\mathbb{N}}^+}$, and to the sequence $(\text{“}\texttt{prg}(32)={\underline{n}}\text{”})_{n\in {\mathbb{N}}^+}$, and to the sequence $(\text{“}\texttt{prg}({\underline{n}})>{\underline{n}}\text{”})_{n\in {\mathbb{N}}^+}$, and so on, to show that $\phi$ eventually has reasonable beliefs about `prg` (hopefully before ${\overline{\mathbb{P}}}$ has the resources to simply evaluate `prg` on input $32$). But at the end of the day, we’ll want to reason about the marginal probability of $\phi$ itself. In this case, approximately-well-calibrated conditional probabilities wouldn’t buy us much: there are $2^{n-1}$ possible truth assignments to the first $n-1$ elements of ${\overline{\phi}}$, so if we try to compute the marginal probability of $\phi_n$ from all the different conditional probabilities, exponentially many small errors would render the answer useless. Furthermore, intuitively, if ${\overline{\phi}}$ is utterly unpredictable to ${\overline{\mathbb{P}}}$, then the probabilities of all the different truth assignments to $\phi_{\le n-1}$ will go to 0 as $n$ gets large, which means the conditional probabilities won’t necessarily be reasonable. (In Section [[#^learning-statistical-patterns|4.4]] will formalize a notion of pseudorandomness.)

Despite these difficulties, we can recover some good calibration properties on the marginal probabilities if we either (a) restrict our consideration to sequences where the average frequency of truth converges; or (b) look at subsequences of ${\overline{\phi}}$ where ${\overline{\mathbb{P}}}$ has “good feedback” about the truth values of previous elements of the subsequence, in a manner defined below.

To state our first calibration property, we will define two different sorts of indicator functions that will prove useful in many different contexts.

**Definition 24** (Theorem Indicator). _Given a sentence $\phi$, define $\operatorname{Thm}_{\Gamma}(\phi)$ to be 1 if $\Gamma\vdash \phi$ and 0 otherwise._

**Definition 25** (Continuous Threshold Indicator). _Let $\delta > 0$ be a rational number, and $x$ and $y$ be real numbers. We then define 

$$
\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x > y) :=
    \begin{dcases}
      0&\textnormal{if }  x\leq y\\
      \frac{x-y}{\delta} &\textnormal{if }\hphantom{x\leq\;} y < x\leq y+\delta\\
      1&\textnormal{if } \hphantom{y\leq\; y < x\leq\;} y+\delta < x.
    \end{dcases}
$$

 Notice that $\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x > y)$ has no false positives, and that it is linear in the region between $y$ and $y+\delta$. We define $\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x < y)$ analogously, and we define 

$$
\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(a < x < b) := \min( \operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x > a), \operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x < b) ).
$$

 Observe that we can generalize this definition to the case where $x$ and $y$ are expressible features, in which case ${\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(x > y)}$ is an expressible $[0,1]$\-feature._

Now we can state our calibration theorem.

**Theorem 26** (Recurring Calibration). _Let ${\overline{\phi}}$ be an e.c. sequence of decidable sentences, $a$ and $b$ be rational numbers, ${\overline{\delta}}$ be an e.c. sequence of positive rational numbers, and suppose that $\sum_n\left(\operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a<\mathbb{P}_i(\phi_i)<b)\right)_{i \in {\mathbb{N}}^+} = \infty$. Then, if the sequence 

$$
\left(
    \frac
      {\sum_{i \leq n} \operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a < \mathbb{P}_i(\phi_i) < b) \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}
      {\sum_{i \leq n} \operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a < \mathbb{P}_i(\phi_i) < b)}
    \right)_{n\in{\mathbb{N}}^+}
$$

 converges, it converges to a point in $[a, b]$. Furthermore, if it diverges, it has a limit point in $[a, b]$._

Roughly, this says that if $\mathbb{P}_n(\phi_n)\approx 80\%$ infinitely often, then if we look at the subsequence where it’s 80%, the limiting frequency of truth on that subsequence is 80% (if it converges).

In colloquial terms, on subsequences where ${\overline{\mathbb{P}}}$ says 80% and it makes sense to talk about the frequency of truth, the frequency of truth is 80%, i.e., ${\overline{\mathbb{P}}}$ isn’t seeing shadows. If the frequency of truth diverges—as in the case with ${\overline{\mathit{\operatorname{clusters}}}}$—then ${\overline{\mathbb{P}}}$ is still well-calibrated infinitely often, but its calibration might still appear abysmal at times (if they can’t predict the swings).

Note that calibration alone is not a very strong property: a reasoner can always cheat to improve their calibration (i.e., by assigning probability 80% to things that they’re sure are true, in order to bring up the average truth of their “80%” predictions). What we really want is some notion of “unbiasedness”, which says that there is no efficient method for detecting a predictable bias in a logical inductor’s beliefs. This is something we can get on sequences where the limiting frequency of truth converges, though again, if the limiting frequency of truth diverges, all we can guarantee is a limit point.

**Definition 27** (Divergent Weighting). _A **divergent weighting** ${\overline{w}}\in [0, 1]^{{\mathbb{N}}^+}$ is an infinite sequence of real numbers in $[0, 1]$, such that $\sum_nw_n = \infty$._

Note that divergent weightings have codomain $[0, 1]$ as opposed to $\{0,1\}$, meaning the weightings may single out fuzzy subsets of the sequence. For purposes of intuition, imagine that ${\overline{w}}$ is a sequence of 0s and 1s, in which case each ${\overline{w}}$ can be interpreted as a subsequence. The constraint that the $w_{n}$ sum to $\infty$ ensures that this subsequence is infinite.

**Definition 28** (Generable From ${\overline{\mathbb{P}}}$). _A sequence of rational numbers ${\overline{q}}$ is called **generable from $\boldsymbol{{\overline{\mathbb{P}}}}$** if there exists an e.c. $\mathcal{E\!F}$\-progression ${\overline{{q^\dagger}}}$ such that ${q_n^\dagger}({\overline{\mathbb{P}}})= q_n$ for all $n$. In this case we say that ${\overline{q}}$ is **${\overline{\mathbb{P}}}$\-generable**. ${\overline{\mathbb{P}}}$\-generable ${\mathbb{R}}$\-sequences, ${\mathbb{Q}}$\-combination sequences, and ${\mathbb{R}}$\-combination sequences are defined analogously._

Divergent weightings generable from ${\overline{\mathbb{P}}}$ are fuzzy subsequences that are allowed to depend continuously (via expressible market features) on the market history. For example, the sequence $(\operatorname{Ind}_{\textnormal{\small{\({0.01}\)}}}(\mathbb{P}_n(\phi_n) > 0.5))_{n\in{\mathbb{N}}^+}$ is a ${\overline{\mathbb{P}}}$\-generable sequence that singles out all times $n$ when $\mathbb{P}_n(\phi_n)$ is greater than 50%. Note that the set of ${\overline{\mathbb{P}}}$\-generable divergent weightings is larger than the set of e.c. divergent weightings, as the ${\overline{\mathbb{P}}}$\-generable weightings are allowed to vary continuously with the market prices.

**Theorem 29** (Recurring Unbiasedness). _Given an e.c. sequence of decidable sentences ${\overline{\phi}}$ and a ${\overline{\mathbb{P}}}$\-generable divergent weighting ${\overline{w}}$, the sequence 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(\phi_i)-\operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

Letting ${\overline{w}}=(1,1,\ldots)$, this theorem says that the difference between the average probability $\mathbb{P}_n(\phi_n)$ and the average frequency of truth is 0 infinitely often (and 0 always, if the latter converges). Letting each $w_n$ be $\operatorname{Ind}_{\textnormal{\small{\({\delta}\)}}}(a < \mathbb{P}_n(\phi_n) < b)$, we recover Theorem 133 (Recurring Calibration). In general, the fraction in Theorem 132 can be interpreted as a measure of the “bias” of ${\overline{\mathbb{P}}}$ on the fuzzy subsequence of ${\overline{\phi}}$ singled out by $w$. Then this theorem says that ${\overline{\mathbb{P}}}$ is unbiased on all ${\overline{\mathbb{P}}}$\-generable subsequences where the frequency of truth converges (and unbiased infinitely often on subsequences where it diverges). Thus, if an e.c. sequence of sentences can be decomposed (by any ${\overline{\mathbb{P}}}$\-generable weighting) into subsequences where the frequency of truth converges, then ${\overline{\mathbb{P}}}$ learns to assign probabilities such that there is no efficient method for detecting a predictable bias in its beliefs.

However, not every sequence can be broken down into well-behaved subsequences by a ${\overline{\mathbb{P}}}$\-generable divergent weighting (if, for example, the truth values move “pseudorandomly” in correlated clusters, as in the case of ${\overline{\mathit{\operatorname{clusters}}}}$). In these cases, it is natural to wonder whether there are any conditions where ${\overline{\mathbb{P}}}$ will be unbiased anyway. Below, we show that the bias converges to zero whenever the weighting ${\overline{w}}$ is sparse enough that ${\overline{\mathbb{P}}}$ can gather sufficient feedback about $\phi_n$ in between guesses:

**Definition 30** (Deferral Function). _A function $f: {\mathbb{N}}^+ \to {\mathbb{N}}^+$ is called a **deferral function** if_

1.  _$f(n) > n$ for all $n$, and_
    
2.  _$f(n)$ can be computed in time polynomial in $f(n)$, i.e., if there is some algorithm and a polynomial function $h$ such that for all $n$, the algorithm computes $f(n)$ within $h(f(n))$ steps._
    

_If $f$ is a deferral function, we say that $f$ **defers** $n$ to $f(n)$._

**Theorem 31** (Unbiasedness From Feedback). _Let ${\overline{\phi}}$ be any e.c. sequence of decidable sentences, and ${\overline{w}}$ be any ${\overline{\mathbb{P}}}$\-generable divergent weighting. If there exists a strictly increasing deferral function $f$ such that the support of ${\overline{w}}$ is contained in the image of $f$ and $\operatorname{Thm}_{\Gamma}(\phi_{f(n)})$ is computable in ${\mathcal{O}}(f(n+1))$ time, then 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(\phi_i)-\operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{\phi}}$”._

In other words, ${\overline{\mathbb{P}}}$ is unbiased on any subsequence of the data where a polynomial-time machine can figure out how the previous elements of the subsequence turned out before ${\overline{\mathbb{P}}}$ is forced to predict the next one. This is perhaps the best we can hope for: On ill-behaved sequences such as ${\overline{\mathit{\operatorname{clusters}}}}$, where the frequency of truth diverges and (most likely) no polynomial-time algorithm can predict the jumps, the $\mathbb{P}_n(\phi_n)$ might be pure guesswork.

So how well does ${\overline{\mathbb{P}}}$ perform on sequences like ${\overline{\mathit{\operatorname{clusters}}}}$? To answer, we turn to the question of how ${\overline{\mathbb{P}}}$ behaves in the face of sequences that it finds utterly unpredictable.

### Learning Statistical Patterns ^learning-statistical-patterns

Consider the digits in the decimal expansion of $\pi$. A good reasoner thinking about the $10^{1,000,000}$th digit of $\pi$, in lieu of any efficient method for predicting the digit before they must make their prediction, should assign roughly 10% probability to that digit being a 7. We will now show that logical inductors learn statistical patterns of this form.

To formalize this claim, we need some way of formalizing the idea that a sequence is “apparently random” to a reasoner. Intuitively, this notion must be defined relative to a specific reasoner’s computational limitations. After all, the digits of $\pi$ are perfectly deterministic; they only appear random to a reasoner who lacks the resources to compute them. Roughly speaking, we will define a sequence to be pseudorandom (relative to ${\overline{\mathbb{P}}}$) if there is no e.c. way to single out any one subsequence that is more likely true than any other subsequence, not even using expressions written in terms of the market prices (by way of expressible features):

**Definition 32** (Pseudorandom Sequence). _Given a set $S$ of divergent weightings (Definition 27), a sequence ${\overline{\phi}}$ of decidable sentences is called **pseudorandom with frequency $\boldsymbol{p}$** over $S$ if, for all weightings ${\overline{w}}\in S$, 

$$
\lim_{n\to\infty} \frac{\sum_{i \leq n} w_i \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}{\sum_{i \leq n} w_i}
$$

 exists and is equal to $p$._

Note that if the sequence ${\overline{\phi}}$ is _actually_ randomly generated (say, by adding $(c_1, c_2, \ldots)$ to the language of $\Gamma$, and tossing a coin weighted with probability $p$ towards heads for each $i$, to determine whether to add $c_i$ or $\lnot c_i$ as an axiom) then $\smash{{\overline{\phi}}}$ is pseudorandom with frequency $p$ almost surely.[^note-5] Now:

**Theorem 33** (Learning Pseudorandom Frequencies). _Let ${\overline{\phi}}$ be an e.c. sequence of decidable sentences. If ${\overline{\phi}}$ is pseudorandom with frequency $p$ over the set of all ${\overline{\mathbb{P}}}$\-generable divergent weightings, then 

$$
\mathbb{P}_n(\phi_n) \eqsim_np.
$$

_

For example, consider again the sequence ${\overline{\mathit{\operatorname{\pi Aeq7}}}}$ where the $n$th element says that the $\operatorname{Ack}(n, n)$th decimal digit of $\pi$ is a 7. The individual $\mathit{\mathit{\operatorname{\pi Aeq7}}}_n$ statements are easy to write down (i.e., efficiently computable), but each one is difficult to decide. Assuming there’s no good way to predict the Ackermann digits of $\pi$ using a ${\overline{\mathbb{P}}}$\-generable divergent weighting, ${\overline{\mathbb{P}}}$ will assign probability 10% to each $\mathit{\operatorname{\pi Aeq7}}_n$ in a timely manner, while it waits for the resources to determine whether the sentence is true or false. Of course, on each individual $\mathit{\operatorname{\pi Aeq7}}_n$, ${\overline{\mathbb{P}}}$’s probability will go to 0 or 1 eventually, i.e., $\lim_{m\to\infty}\mathbb{P}_m(\mathit{\operatorname{\pi Aeq7}}_n) \in \{0,1\}$.

Theorem 140 still tells us nothing about how ${\overline{\mathbb{P}}}$ handles ${\overline{\mathit{\operatorname{clusters}}}}$ (defined above), because the frequency of truth in that sequence diverges, so it does not count as pseudorandom by the above definition. To handle this case we will weaken our notion of pseudorandomness, so that it includes more sequences, yielding a stronger theorem. We will do this by allowing sequences to count as pseudorandom so long as the limiting frequency of truth converges on “independent subsequences” where the $n+1$st element of the subsequence doesn’t come until after the $n$th element can be decided, as described below. Refer to Garrabrant et al. (2016) for a discussion of why this is a good way to broaden the set of sequences that count as pseudorandom.

**Definition 34** ($f$\-Patient Divergent Weighting). _Let $f$ be a deferral function. We say that a divergent weighting ${\overline{w}}$ is **$\boldsymbol{f}$\-patient** if there is some constant $C$ such that, for all $n$, 

$$
\sum_{i=n}^{f(n)} w_i({\overline{\mathbb{P}}}) \leq C
$$

 In other words, ${\overline{w}}$ is $f$\-patient if the weight it places between days $n$ and $f(n)$ is bounded._

While we are at it, we will also strengthen Theorem 140 in three additional ways: we will allow the probabilities on the sentences to vary with time, and with the market prices, and we will generalize $\eqsim_n$ to $\gtrsim_n$ and $\lesssim_n$.

**Definition 35** (Varied Pseudorandom Sequence). _Given a deferral function $f$, a set $S$ of $f$\-patient divergent weightings, an e.c. sequence ${\overline{\phi}}$ of $\Gamma$\-decidable sentences, and a ${\overline{\mathbb{P}}}$\-generable sequence ${\overline{p}}$ of rational probabilities, ${\overline{\phi}}$ is called a **$\boldsymbol{{\overline{p}}}$\-varied pseudorandom sequence** (relative to $S$) if, for all ${\overline{w}}\in S$, 

$$
\frac{\sum_{i \leq n} w_i \cdot (p_i- \operatorname{Thm}_{\Gamma}(\phi_i))}{\sum_{i \leq n} w_i} \eqsim_n0.
$$

 Furthermore, we can replace $\eqsim_n$ with $\gtrsim_n$ or $\lesssim_n$, in which case we say ${\overline{\phi}}$ is **varied pseudorandom above $\boldsymbol{{\overline{p}}}$** or **varied pseudorandom below $\boldsymbol{{\overline{p}}}$**, respectively._

**Theorem 36** (Learning Varied Pseudorandom Frequencies). _Given an e.c. sequence ${\overline{\phi}}$ of $\Gamma$\-decidable sentences and a ${\overline{\mathbb{P}}}$\-generable sequence ${\overline{p}}$ of rational probabilities, if there exists some $f$ such that ${\overline{\phi}}$ is ${\overline{p}}$\-varied pseudorandom (relative to all $f$\-patient ${\overline{\mathbb{P}}}$\-generable divergent weightings), then 

$$
\mathbb{P}_n(\phi_n) \eqsim_np_n.
$$

 Furthermore, if ${\overline{\phi}}$ is varied pseudorandom above or below ${\overline{p}}$, then the $\eqsim_n$ may be replaced with $\gtrsim_n$ or $\lesssim_n$ (respectively)._

Thus we see that ${\overline{\mathbb{P}}}$ does learn to assign marginal probabilities $\mathbb{P}_n(\mathit{\operatorname{clusters}}_n)\approx 0.5$, assuming the Ackermann digits of $\pi$ are actually difficult to predict. Note that while Theorem 138 requires each $p_n$ to be rational, the fact that the theorem is generalized to varied pseudorandom above/below sequences means that Theorem 138 is a strict generalization of Theorem 140 (Learning Pseudorandom Frequencies).

In short, Theorem 138 shows that logical inductors reliably learn in a timely manner to recognize appropriate statistical patterns, whenever those patterns (which may vary over time and with the market prices) are the best available method for predicting the sequence using ${\overline{\mathbb{P}}}$\-generable methods.

### Learning Logical Relationships ^learning-logical-relationships

Most of the above properties discuss the ability of a logical inductor to recognize patterns in a single sequence—for example, they recognize e.c. sequences of theorems in a timely manner, and they fall back on the appropriate statistical summaries in the face of pseudorandomness. We will now examine the ability of logical inductors to learn relationships between sequences.

Let us return to the example of the computer program `prg` which outputs either 0, 1, or 2 on all inputs, but for which this cannot be proven in general by $\Gamma$. Theorem 122 (Provability Induction) says that the pattern 

$$
{\overline{\mathit{\operatorname{prg012}}}} := \big( \text{“}\texttt{prg(\({\underline{n}}\))}=0 \lor \texttt{prg(\({\underline{n}}\))}=1 \lor \texttt{prg(\({\underline{n}}\))}=2\text{”} \big)_{n\in {{\mathbb{N}}^+}}
$$

 will be learned, in the sense that ${\overline{\mathbb{P}}}$ will assign each $\mathit{\operatorname{prg012}}_n$ a probability near 1 in a timely manner. But what about the following three individual sequences? 

$$
\begin{align*}
  {\overline{\mathit{\operatorname{prg0}}}} := \big( \text{“}\texttt{prg(\({\underline{n}}\))}=0\text{”} \big)_{n\in {{\mathbb{N}}^+}} \\
  {\overline{\mathit{\operatorname{prg1}}}} := \big( \text{“}\texttt{prg(\({\underline{n}}\))}=1\text{”} \big)_{n\in {{\mathbb{N}}^+}} \\
  {\overline{\mathit{\operatorname{prg2}}}} := \big( \text{“}\texttt{prg(\({\underline{n}}\))}=2\text{”} \big)_{n\in {{\mathbb{N}}^+}}
\end{align*}
$$

 None of the three sequences is a sequence of only theorems, so provability induction does not have much to say. If they are utterly pseudorandom relative to $r$, then Theorem 138 (Learning Varied Pseudorandom Frequencies) says that ${\overline{\mathbb{P}}}$ will fall back on the appropriate statistical summary, but that tells us little in cases where there are predictable non-conclusive patterns (e.g., if `prg(i)` is more likely to output 2 when `helper(i)` outputs 17). In fact, if ${\overline{\mathbb{P}}}$ is doing good reasoning, the probabilities on the $(\mathit{\operatorname{prg0}}_n, \mathit{\operatorname{prg1}}_n, \mathit{\operatorname{prg2}}_n)$ triplet ought to shift, as ${\overline{\mathbb{P}}}$ gains new knowledge about related facts and updates its beliefs. How could we tell if those intermediate beliefs were reasonable?

One way is to check their sum. If ${\overline{\mathbb{P}}}$ believes that $\texttt{prg(i)}\in\{0, 1, 2\}$ and it knows how disjunction works, then it should be the case that whenever $\mathbb{P}_n(\mathit{\operatorname{prg012}}_t) \approx 1$, $\mathbb{P}_n(\mathit{\operatorname{prg0}}_t) + \mathbb{P}_n(\mathit{\operatorname{prg1}}_t) + \mathbb{P}_n(\mathit{\operatorname{prg2}}_t) \approx 1$. And this is precisely the case. In fact, logical inductors recognize mutual exclusion between efficiently computable tuples of any size, in a timely manner:

**Theorem 37** (Learning Exclusive-Exhaustive Relationships). _Let ${\overline{\phi^1}},\ldots,{\overline{\phi^k}}$ be $k$ e.c. sequences of sentences, such that for all $n$, $\Gamma$ proves that $\phi^1_n,\ldots,\phi^k_n$ are exclusive and exhaustive (i.e. exactly one of them is true). Then 

$$
\mathbb{P}_n(\phi^1_n)+\cdots+\mathbb{P}_n(\phi^k_n)  \eqsim_n1.
$$

_

_Proof sketch._

> Consider the trader that acts as follows. On day $n$, they check the prices of $\phi_n^1\ldots\phi_n^k$. If the sum of the prices is higher (lower) than 1 by some fixed threshold $\varepsilon > 0$, they sell (buy) a share of each, wait until the values of the shares are the same in every plausible world, and make a profit of $\varepsilon$. (It is guaranteed that eventually, in every plausible world exactly one of the shares will be valued at 1.) If the sum goes above $1 + \varepsilon$ (below $1 - \varepsilon$) on the main diagonal infinitely often, this trader exploits ${\overline{\mathbb{P}}}$. Logical inductors are inexploitable, so it must be the case that the sum of the prices goes to 1 along the main diagonal.

This theorem suggests that logical inductors are good at learning to assign probabilities that respect logical relationships between related sentences. To show that this is true in full generality, we will generalize Theorem 130 to any linear inequalities that hold between the actual truth-values of different sentences.

First, we define the following convention:

**Convention 38** (Constraint). _An ${\mathbb{R}}$\-combination $A$ can be viewed as a **constraint**, in which case we say that a valuation $\mathbb{V}$ **satisfies** the constraint if $\mathbb{V}(A) \ge 0$._

For example, the constraint 

$$
\operatorname{AND} := -2 + \phi + \psi
$$

 says that both $\phi$ and $\psi$ are true, and it is satisfied by $\mathbb{W}$ iff $\mathbb{W}(\phi) = \mathbb{W}(\psi) = 1$. As another example, the pair of constraints 

$$
\operatorname{XOR} := (1 - \phi - \psi, \phi + \psi - 1)
$$

 say that exactly one of $\phi$ and $\psi$ is true, and are satisfied by $\mathbb{P}_7$ iff $\mathbb{P}_7(\phi) + \mathbb{P}_7(\psi) = 1$.

**Definition 39** (Bounded Combination Sequence). _By $\mathcal{BCS}({\overline{\mathbb{P}}})$ (mnemonic: **bounded combination sequences**) we denote the set of all ${\overline{\mathbb{P}}}$\-generable ${\mathbb{R}}$\-combination sequences ${\overline{A}}$ that are bounded, in the sense that there exists some bound $b$ such that $\| A_n\|_1 \le b$ for all $n$, where $\|\!-\!\|_1$ includes the trailing coefficient._

**Theorem 40** (Affine Provability Induction). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$ and $b \in {\mathbb{R}}$. If, for all consistent worlds $\mathbb{W}\in\mathcal{PC}(\Gamma)$ and all $n\in {\mathbb{N}}^+$, it is the case that $\mathbb{W}(A_n ) \ge b$, then 

$$
\mathbb{P}_n(A_n) \gtrsim_nb,
$$

 and similarly for $=$ and $\eqsim_n$, and for $\leq$ and $\lesssim_n$._

For example, consider the constraint sequence 

$$
{\overline{A}} := \big(1 - \mathit{\operatorname{prg0}}_n- \mathit{\operatorname{prg1}}_n- \mathit{\operatorname{prg2}}_n\big)_{n\in {\mathbb{N}}^+}
$$

 For all $n$ and all consistent worlds $\mathbb{W}\in \mathcal{PC}(\Gamma)$, the value $\mathbb{W}(A_n)$ is 0, so applying Theorem 120 to ${\overline{A}}$, we get that $\mathbb{P}_n(A_n) \eqsim_n0$. By linearity, this means 

$$
\mathbb{P}_n(\mathit{\operatorname{prg0}}_n) + \mathbb{P}_n(\mathit{\operatorname{prg1}}_n) + \mathbb{P}_n(\mathit{\operatorname{prg2}}_n) \eqsim_n1,
$$

 i.e., ${\overline{\mathbb{P}}}$ learns that the three sequences are mutually exclusive and exhaustive in a timely manner, regardless of how difficult `prg` is to evaluate. 121 is a generalization of this idea, where the coefficients may vary (day by day, and with the market prices).

We can push this idea further, as follows:

**Theorem 41** (Affine Coherence). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(A_n)
    \le \liminf_{n\rightarrow\infty}
      \mathbb{P}_\infty(A_n)
    \le \liminf_{n\to\infty}
      \mathbb{P}_n(A_n),
$$

 and 

$$
\limsup_{n\to\infty} \mathbb{P}_n(A_n)
    \le \limsup_{n\rightarrow\infty} \mathbb{P}_\infty(A_n)
    \le \limsup_{n\rightarrow\infty} \sup_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(A_n).
$$

_

This theorem ties the ground truth on ${\overline{A}}$, to the value of ${\overline{A}}$ in the limit, to the value of ${\overline{A}}$ on the main diagonal. In words, it says that if all consistent worlds value $A_n$ in $(a, b)$ for $n$ large, then $\mathbb{P}_\infty$ values $A_n$ in $(c, d) \subseteq (a, b)$ for $n$ large (because $\mathbb{P}_\infty$ is a weighted mixture of all consistent worlds), and ${\overline{\mathbb{P}}}$ learns to assign probabilities such that $\mathbb{P}_n(A_n)\in (c, d)$ in a timely manner. In colloquial terms, ${\overline{\mathbb{P}}}$ learns in a timely manner to respect _all_ linear inequalities that actually hold between sentences, so long as those relationships can be enumerated in polynomial time.

For example, if `helper(i)=err` always implies `prg(i)=0`, ${\overline{\mathbb{P}}}$ will learn this pattern, and start assigning probabilities to $\mathbb{P}_n(\text{“}\textnormal{\texttt{prg({\underline{\(n\)}})=0}}\text{”})$ which are no lower than those of $\mathbb{P}_n(\text{“}\textnormal{\texttt{helper({\underline{n}})=err}}\text{”})$. In general, if a series of sentences obey some complicated linear inequalities, then so long as those constraints can be _written down_ in polynomial time, ${\overline{\mathbb{P}}}$ will learn the pattern, and start assigning probabilities that respect those constraints in a timely manner.

This doesn’t mean that ${\overline{\mathbb{P}}}$ will assign the _correct_ values (0 or 1) to each sentence in a timely manner; that would be impossible for a deductively limited reasoner. Rather, ${\overline{\mathbb{P}}}$’s probabilities will start _satisfying the constraints_ in a timely manner. For example, imagine a set of complex constraints holds between seven sequences, such that exactly three sentences in each septuplet are true, but it’s difficult to tell which three. Then ${\overline{\mathbb{P}}}$ will learn this pattern, and start ensuring that its probabilities on each septuplet sum to 3, even if it can’t yet assign particularly high probabilities to the correct three.

If we watch an individual septuplet as ${\overline{\mathbb{P}}}$ reasons, other constraints will push the probabilities on those seven sentences up and down. One sentence might be refuted and have its probability go to zero. Another might get a boost when ${\overline{\mathbb{P}}}$ discovers that it’s likely implied by a high-probability sentence. Another might take a hit when ${\overline{\mathbb{P}}}$ discovers it likely implies a low-probability sentence. Throughout all this, Theorem 120 says that ${\overline{\mathbb{P}}}$ will ensure that the seven probabilities always sum to $\approx 3$. ${\overline{\mathbb{P}}}$’s beliefs on any given day arise from this interplay of many constraints, inductively learned.

Observe that 120 is a direct generalization of Theorem 122 (Provability Induction). One way to interpret this theorem is that it says that ${\overline{\mathbb{P}}}$ is very good at learning inductively to predict long-running computations. Given any e.c. sequence of statements about the computation, if they are true then ${\overline{\mathbb{P}}}$ learns to believe them in a timely manner, and if they are false then ${\overline{\mathbb{P}}}$ learns to disbelieve them in a timely manner, and if they are related by logical constraints (such as by exclusivity or implication) to some other e.c. sequence of statements, then ${\overline{\mathbb{P}}}$ learns to make its probabilities respect those constraints in a timely manner. This is one of the main reasons why we think this class of algorithms deserves the name of “logical inductor”.

120 can also be interpreted as an approximate coherence condition on the finite belief-states of ${\overline{\mathbb{P}}}$. It says that if a certain relationship among truth values is going to hold in the future, then ${\overline{\mathbb{P}}}$ learns to make that relationship hold approximately in its probabilities, in a timely manner.[^note-6]

In fact, we can use this idea to strengthen every theorem in sections [[#^timely-learning|4.2]]\-[[#^learning-statistical-patterns|4.4]], as below. (Readers without interest in the strengthened theorems are invited to skip to Section [[#^non-dogmatism|4.6]].)

#### Affine Strengthenings ^affine-strengthenings

Observe that Theorem 121 (Affine Provability Induction) is a strengthening of Theorem 122 (Provability Induction).

**Theorem 42** (Persistence of Affine Knowledge). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}\mathbb{P}_m(A_n)= \liminf_{n\to\infty}\mathbb{P}_\infty(A_n)
$$

 and 

$$
\limsup_{n\rightarrow\infty}\sup_{m\geq n}\mathbb{P}_m(A_n)=\limsup_{n\to\infty}\mathbb{P}_\infty(A_n).
$$

_

To see that this is a generalization of Theorem 119 (Persistence of Knowledge), it might help to first replace ${\overline{A}}$ with a sequence ${\overline{{p}}}$ of rational probabilities.

**Theorem 43** (Affine Preemptive Learning). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\to\infty} \mathbb{P}_n(A_n)= \liminf_{n\rightarrow\infty}\sup_{m\geq n} \mathbb{P}_m(A_n)
$$

 and 

$$
\limsup_{n\to\infty} \mathbb{P}_n(A_n)= \limsup_{n\rightarrow\infty}\inf_{m\geq n} \mathbb{P}_m(A_n) \ .
$$

_

**Definition 44** (Determined via $\Gamma$). _We say that a ${\mathbb{R}}$\-combination $A$ is **determined via $\boldsymbol{\Gamma}$** if, in all worlds $\mathbb{W}\in \mathcal{PC}(\Gamma)$, the value $\mathbb{W}(A)$ is equal. Let $\operatorname{Val}_{\Gamma}(A)$ denote this value._

_Similarly, a sequence ${\overline{A}}$ of ${\mathbb{R}}$\-combinations is said to be determined via $\Gamma$ if $A_n$ is determined via $\Gamma$ for all $n$._

**Theorem 45** (Affine Recurring Unbiasedness). _If ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$ is determined via $\Gamma$, and ${\overline{w}}$ is a ${\overline{\mathbb{P}}}$\-generable divergent weighting, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(A_i)-\operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

**Theorem 46** (Affine Unbiasedness from Feedback). _Given ${\overline{A}}\in \mathcal{BCS}({\overline{\mathbb{P}}})$ that is determined via $\Gamma$, a strictly increasing deferral function $f$ such that $\operatorname{Val}_{\Gamma}(A_n )$ can be computed in time ${\mathcal{O}}(f(n+1))$, and a ${\overline{\mathbb{P}}}$\-generable divergent weighting ${\overline{w}}$ such that the support of ${\overline{w}}$ is contained in the image of $f$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(A_i)-\operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{A}}$”._

**Theorem 47** (Learning Pseudorandom Affine Sequences). _Given a ${\overline{A}}\in \mathcal{BCS}({\overline{\mathbb{P}}})$ which is determined via $\Gamma$, if there exists deferral function $f$ such that for any ${\overline{\mathbb{P}}}$\-generable $f$\-patient divergent weighting ${\overline{w}}$, 

$$
\frac{\sum_{i \leq n} w_i  \cdot \operatorname{Val}_{\Gamma}(A_i )}{\sum_{i \leq n} w_i } \gtrsim_n0,
$$

 then 

$$
\mathbb{P}_n(A_n) \gtrsim_n0,
$$

 and similarly for $\eqsim_n$, and $\lesssim_n$._

### Non-Dogmatism ^non-dogmatism

Cromwell’s rule says that a reasoner should not assign extreme probabilities (0 or 1) except when applied to statements that are logically true or false. The rule was named by Lindley (1991), in light of the fact that Bayes’ theorem says that a Bayesian reasoner can never update away from probabilities 0 or 1, and in reference to the famous plea:

> I beseech you, in the bowels of Christ, think it possible that you may be mistaken. _– Oliver Cromwell_

The obvious generalization of Cromwell’s rule to a setting where a reasoner is uncertain about logic is that they also should not assign extreme probabilities to sentences that have not yet been proven or disproven. Logical inductors _do not_ satisfy this rule, as evidenced by the following theorem:

**Theorem 48** (Closure under Finite Perturbations). _Let ${\overline{\mathbb{P}}}$ and ${\overline{\mathbb{P}^\prime}}$ be markets with $\mathbb{P}_n= \mathbb{P}^\prime_n$ for all but finitely many $n$. Then ${\overline{\mathbb{P}}}$ is a logical inductor if and only if ${\overline{\mathbb{P}^\prime}}$ is a logical inductor._

This means that we can take a logical inductor, completely ruin its beliefs on the 23rd day (e.g., by setting $\mathbb{P}_{23}(\phi)=0$ for all $\phi$), and it will still be a logical inductor. Nevertheless, there is still a sense in which logical inductors are non-dogmatic, and can “think it possible that they may be mistaken”:

**Theorem 49** (Non-Dogmatism). _If $\Gamma\nvdash \phi$ then $\mathbb{P}_\infty(\phi)<1$, and if $\Gamma\nvdash \neg\phi$ then $\mathbb{P}_\infty(\phi)>0$._

_Proof sketch._

> Consider a trader that watches $\phi$ and buys whenever it gets low, as follows. The trader starts with \$1\. They spend their first 50 cents when $\mathbb{P}_n(\phi) < 1/2$, purchasing one share. They spend their next 25 cents when $\mathbb{P}_n(\phi) < 1/4$, purchasing another share. They keep waiting for $\mathbb{P}_n(\phi)$ to drop low enough that they can spend the next half of their initial wealth to buy one more share. Because $\phi$ is independent, there always remains at least one world $\mathbb{W}$ such that $\mathbb{W}(\phi)=1$, so if $\mathbb{P}_n(\phi) \to 0$ as $n \to\infty$ then their maximum plausible profits are \$1 + \$1 + \$1 +…which diverges, and they exploit the market. Thus, $\mathbb{P}_\infty(\phi)$ must be bounded away from zero.

In other words, if $\phi$ is independent from $\Gamma$, then ${\overline{\mathbb{P}}}$’s beliefs about $\phi$ won’t get stuck converging to 0 or 1. By Theorem 168 (Closure under Finite Perturbations), ${\overline{\mathbb{P}}}$ may occasionally jump to unwarranted conclusions—believing with “100% certainty”, say, that Euclid’s fifth postulate follows from the first four—but it always corrects these errors, and eventually develops conservative beliefs about independent sentences.

Theorem 165 guarantees that ${\overline{\mathbb{P}}}$ will be reasonable about independent sentences, but it doesn’t guarantee reasonable beliefs about _theories_, because theories can require infinitely many axioms. For example, let $\Gamma$ be a theory of pure first-order logic, and imagine that the language $\mathcal{L}$ has a free binary relation symbol $\text{“}\!\in\!\text{”}$. Now consider the sequence ${\overline{\mathit{\operatorname{ZFCaxioms}}}}$ of first-order axioms of Zermelo-Fraenkel set theory (${\mathsf{ZFC}}$) which say to interpret $\text{“}\!\in\!\text{”}$ in the set-theoretic way, and note that ${\overline{\mathit{\operatorname{ZFCaxioms}}}}$ is infinite. Each individual sentence $\mathit{\operatorname{ZFCaxioms}}_n$ is consistent with first-order logic, but if $\mathbb{P}_\infty$’s odds on each axiom were 50:50 and independent, then it would say that the probability of them all being true simultaneously was zero. Fortunately, for any computably enumerable sequence of sentences that are mutually consistent, $\mathbb{P}_\infty$ assigns positive probability to them all being simultaneously true.

**Theorem 50** (Uniform Non-Dogmatism). _For any computably enumerable sequence of sentences ${\overline{\phi}}$ such that $\Gamma\cup{\overline{\phi}}$ is consistent, there is a constant $\varepsilon>0$ such that for all $n$, 

$$
\mathbb{P}_\infty(\phi_n)\geq \varepsilon.
$$

_

If $\phi_n$ is the conjunction of the first $n$ axioms of ${\mathsf{ZFC}}$, Theorem 163 shows that $\mathbb{P}_\infty$ assigns positive probability to theories in which the symbol $\text{“}\!\in\!\text{”}$ satisfies all axioms of ${\mathsf{ZFC}}$ (assuming ${\mathsf{ZFC}}$ is consistent).

Reasoning about individual sentences again, we can put bounds on how far each sentence $\phi$ is bounded away from 0 and 1, in terms of the prefix complexity $\kappa(\phi)$ of $\phi$, i.e., the length of the shortest prefix that causes a fixed universal Turing machine to output $\phi$.[^note-7]

**Theorem 51** (Occam Bounds). _There exists a fixed positive constant $C$ such that for any sentence $\phi$ with prefix complexity $\kappa(\phi)$, if $\Gamma\nvdash\neg\phi$, then 

$$
\mathbb{P}_\infty(\phi)\geq C2^{-\kappa(\phi)},
$$

 and if $\Gamma\nvdash\phi$, then 

$$
\mathbb{P}_\infty(\phi)\leq 1-C2^{-\kappa(\phi)}.
$$

_

This means that if we add a sequence of constant symbols $(c_1, c_2, \ldots)$ not mentioned in $\Gamma$ to the language $\mathcal{L}$, then ${\overline{\mathbb{P}}}$’s beliefs about statements involving those constants will depend on the complexity of the claim. Roughly speaking, if you ask after the probability of a claim like $\text{“}c_1 = 10 \land c_2 = 7 \land \ldots \land c_n = -3\text{”}$ then the answer will be no lower than the probability that a simplicity prior assigns to the shortest program that outputs $(10, 7, \ldots, -3)$.

In fact, the probability may be a fair bit higher, if the claim is part of a particularly simple sequence of sentences. In other words, logical inductors can be used to reason about _empirical_ uncertainty as well as logical uncertainty, by using $\mathbb{P}_\infty$ as a full-fledged sequence predictor:

**Theorem 52** (Domination of the Universal Semimeasure). _Let $(b_1, b_2, \ldots)$ be a sequence of zero-arity predicate symbols in $\mathcal{L}$ not mentioned in $\Gamma$, and let $\sigma_{\le n}=(\sigma_1,\ldots,\sigma_n)$ be any finite bitstring. Define 

$$
\mathbb{P}_\infty(\sigma_{\le n}) := \mathbb{P}_\infty(\text{“}(b_1 \leftrightarrow{\underline{\sigma_1}}=1) \land (b_2 \leftrightarrow{\underline{\sigma_2}}=1) \land \ldots \land (b_n \leftrightarrow{\underline{\sigma_n}}=1)\text{”}),
$$

 such that, for example, $\mathbb{P}_\infty(01101) = \mathbb{P}_\infty(\text{“}\lnot b_1 \land b_2 \land b_3 \land \lnot b_4 \land b_5\text{”})$. Let $M$ be a universal continuous semimeasure. Then there is some positive constant $C$ such that for any finite bitstring $\sigma_{\le n}$, 

$$
\mathbb{P}_\infty(\sigma_{\le n}) \ge C \cdot M(\sigma_{\le n}).
$$

_

In other words, logical inductors can be viewed as a computable approximation to a normalized probability distribution that dominates the universal semimeasure. In fact, this dominance is strict:

**Theorem 53** (Strict Domination of the Universal Semimeasure). _The universal continuous semimeasure does not dominate $\mathbb{P}_\infty$; that is, for any positive constant $C$ there is some finite bitstring $\sigma_{\le n}$ such that 

$$
\mathbb{P}_\infty(\sigma_{\le n}) > C \cdot M(\sigma_{\le n}).
$$

_

In particular, by Theorem 163 (Uniform Non-Dogmatism), logical inductors assign positive probability to the set of all completions of theories like ${\mathsf{PA}}$ and ${\mathsf{ZFC}}$, whereas universal semimeasures do not. This is why we can’t construct approximately coherent beliefs about logic by fixing an enumeration of logical sentences and conditioning a universal semimeasure on more axioms of Peano arithmetic each day: the probabilities that the semimeasure assigns to those conjunctions must go to zero, so the conditional probabilities may misbehave. (If this were not the case, it would be possible to sample a complete extension of Peano arithmetic with positive probability, because universal semimeasures are approximable from below; but this is impossible. See the proof of Theorem 167 for details.) While $\mathbb{P}_\infty$ is limit-computable, it is not approximable from below, so it can and does outperform the universal semimeasure when reasoning about arithmetical claims.

### Conditionals ^conditionals

One way to interpret Theorem 166 (Domination of the Universal Semimeasure) is that when we condition $\mathbb{P}_\infty$ on independent sentences about which it knows nothing, it performs empirical (scientific) induction. We will now show that when we condition ${\overline{\mathbb{P}}}$, it also performs logical induction.

In probability theory, it is common to discuss conditional probabilities such as $\mathrm{Pr}(A \mid B) := \mathrm{Pr}(A \land B)/\mathrm{Pr}(B)$ (for any $B$ with $\mathrm{Pr}(B)>0$), where $\mathrm{Pr}(A \mid B)$ is interpreted as the probability of $A$ restricted to worlds where $B$ is true. In the domain of logical uncertainty, we can define conditional probabilities in the analogous way:

**Definition 54** (Conditional Probability). _Let $\phi$ and $\psi$ be sentences, and let $\mathbb{V}$ be a valuation with $\mathbb{V}(\psi) > 0$. Then we define 

$$
\mathbb{V}(\phi \mid \psi) :=
    \begin{cases}
      {\mathbb{V}(\phi\wedge\psi)}/{\mathbb{V}(\psi)} &
      \textnormal{if }\mathbb{V}(\phi\wedge\psi) < \mathbb{V}(\psi)\\
      1 &
      \text{otherwise.}
    \end{cases}
$$

 Given a valuation sequence ${\overline{\mathbb{V}}}$, we define 

$$
{\overline{\mathbb{V}}}(-\mid\psi) := (\mathbb{V}_1(-\mid\psi), \mathbb{V}_2(-\mid\psi), \ldots).
$$

_

Defining $\mathbb{V}(\phi\mid\psi)$ to be 1 if $\mathbb{V}(\psi)=0$ is nonstandard, but convenient for our theorem statements and proofs. The reader is welcome to ignore the conditional probabilities in cases where $\mathbb{V}(\psi)=0$, or to justify our definition from the principle of explosion (which says that from a contradiction, anything follows). This definition also caps $\mathbb{V}(\phi\mid\psi)$ at 1, which is necessary because there’s no guarantee that $\mathbb{V}$ knows that $\phi \land \psi$ should have a lower probability than $\psi$. For example, if it takes ${\overline{\mathbb{P}}}$ more than 17 days to learn how $\text{“}\!\land\!\text{”}$ interacts with $\phi$ and $\psi$, then it might be the case that $\mathbb{P}_{17}(\phi\land\psi)=0.12$ and $\mathbb{P}_{17}(\psi)=0.01$, in which case the uncapped “conditional probability” of $\phi\land\psi$ given $\psi$ according to $\mathbb{P}_{17}$ would be twelve hundred percent.

This fact doesn’t exactly induce confidence in ${{\overline{\mathbb{P}}}(-\mid\psi)}$. Nevertheless, we have the following theorem:

**Theorem 55** (Closure Under Conditioning). _The sequence ${\overline{\mathbb{P}}}(-\mid\psi)$ is a logical inductor over $\Gamma\cup \{\psi\}$. Furthermore, given any efficiently computable sequence ${\overline{\psi}}$ of sentences, the sequence 

$$
\left(\mathbb{P}_1(-\mid \psi_1), \mathbb{P}_2(-\mid \psi_1 \land \psi_2), \mathbb{P}_3(-\mid \psi_1 \land \psi_2 \land \psi_3), \ldots\right),
$$

 where the $n$th pricing is conditioned on the first $n$ sentences in ${\overline{\psi}}$, is a logical inductor over $\Gamma\cup \{\psi_i \mid i \in {\mathbb{N}}^+\}$._

In other words, if we condition logical inductors on logical sentences, the result is still a logical inductor, and so the conditional probabilities of a logical inductor continues to satisfy all the desirable properties satisfied by all logical inductors. This also means that one can obtain a logical inductor for Peano arithmetic by starting with a logical inductor over an empty theory, and conditioning it on ${\mathsf{PA}}$.

With that idea in mind, we will now begin examining questions about logical inductors that assume $\Gamma$ can represent computable functions, such as questions about ${\overline{\mathbb{P}}}$’s beliefs about $\Gamma$, computer programs, and itself.

### Expectations ^expectations

In probability theory, it is common to ask the expected (average) value of a variable that takes on different values in different possible worlds. Emboldened by our success with conditional probabilities, we will now define a notion of the expected values of _logical_ variables, and show that these are also fairly well-behaved. This machinery will be useful later when we ask logical inductors for their beliefs about themselves.

We begin by defining a notion of logically uncertain variables, which play a role analogous to the role of random variables in probability theory. For the sake of brevity, we will restrict our attention to logically uncertain variables with their value in $[0, 1]$; it is easy enough to extend this notion to a notion of arbitrary bounded real-valued logically uncertain variables. (It does, however, require carrying a variable’s bounds around everywhere, which makes the notation cumbersome.)

To define logically uncertain variables, we will need to assume that $\Gamma$ is capable of representing rational numbers and proving things about them. Later, we will use expected values to construct sentences that talk about things like the expected outputs of a computer program. Thus, in this section and in the remainder of Section [[#^properties-of-logical-inductors|4]], we will assume that $\Gamma$ can represent computable functions.

**Definition 56** (Logically Uncertain Variable). _A **logically uncertain variable**, abbreviated **LUV**, is any formula $X$ free in one variable that defines a unique value via $\Gamma$, in the sense that 

$$
\Gamma\vdash{\exists x \colon  \left( X(x) \land \forall x' \colon X(x') \to x'=x \right)}.
$$

 We refer to that value as the **value** of $X$. If $\Gamma$ proves that the value of $X$ is in $[0, 1]$, we call $X$ a **$\boldsymbol{[0,1]}$\-LUV**._

_Given a $[0,1]$\-LUV $X$ and a consistent world $\mathbb{W}\in \mathcal{PC}(\Gamma)$, the **value of $\boldsymbol{X}$ in $\mathbb{W}$** is defined to be 

$$
\mathbb{W}(X) := \sup \left\{x \in [0, 1] \mid \mathbb{W}(\text{“}X \ge {\underline{x}}\text{”})=1 \right\}.
$$

 In other words, $\mathbb{W}(X)$ is the supremum of values that do not exceed $X$ according to $\mathbb{W}$. (This rather roundabout definition is necessary in cases where $\mathbb{W}$ assigns $X$ a non-standard value.)_

_We write $\mathcal{U}$ for the set of all $[0, 1]$\-LUVs. When manipulating logically uncertain variables, we use shorthand like $\text{“}X < 0.5\text{”}$ for $\text{“}\forall x \colon X(x) \to x < 0.5\text{”}$. See Section [[#^notation|2]] for details._

As an example, $\mathit{Half} := \text{“}\nu = 0.5\text{”}$ is a LUV, where the unique real number that makes $\mathit{Half}$ true is rather obvious. A more complicated LUV is 

$$
\mathit{TwinPrime} := \text{“}\textnormal{1 if the twin prime conjecture is true, 0 otherwise}\text{”};
$$

 this is a deterministic quantity (assuming $\Gamma$ actually proves the twin prime conjecture one way or the other), but it’s reasonable for a limited reasoner to be uncertain about the value of that quantity. In general, if $f : {\mathbb{N}}^+ \to [0, 1]$ is a computable function then $\text{“}{\underline{f}}(7)\text{”}$ is a LUV, because $\text{“}{\underline{f}}(7)\text{”}$ is shorthand for the formula $\text{“}\gamma_f(7, \nu)\text{”}$, where $\gamma_f$ is the predicate of $\Gamma$ representing $f$.

With LUVs in hand, we can define a notion of ${\overline{\mathbb{P}}}$’s expected value for a LUV $X$ on day $n$ with precision $k$. The obvious idea is to take the sum 

$$
\lim_{k \to\infty} \sum_{i=0}^{k-1} \frac{i}{k} \mathbb{P}_n\left(
    \text{“}{\underline{i}}/{\underline{k}} < {\underline{X}} \le ({\underline{i}}+1)/{\underline{k}}\text{”}
  \right).
$$

 However, if $\mathbb{P}_n$ hasn’t yet figured out that $X$ pins down a unique value, then it might put high probability on $X$ being in multiple different intervals, and the simple integral of a $[0,1]$\-valued LUV could fall outside the $[0,1]$ interval. This is a nuisance when we want to treat the expectations of $[0,1]$\-LUVs as other $[0,1]$\-LUVs, so instead, we will define expectations using an analog of a cumulative distribution function. In probability theory, the expectation of a $[0,1]$\-valued random variable $V$ with density function $\rho_V$ is given by ${\mathbb{E}}(V) =\int_0^1 x \cdot \rho_V(x) dx$. We can rewrite this using integration by parts as 

$$
{\mathbb{E}}(V) =\int_0^1 \mathrm{Pr}(V>x)dx.
$$

 This motivates the following definition of expectations for LUVs:

**Definition 57** (Expectation). _For a given valuation $\mathbb{V}$, we define the **approximate expectation operator** ${\mathbb{E}}_k^{\mathbb{V}}$ for $\mathbb{V}$ with precision $k$ by 

$$
{\mathbb{E}}_k^{\mathbb{V}}(X) := \sum_{i=0}^{k-1}\frac{1}{k} \mathbb{V}\left(\text{“}{\underline{X}} > {\underline{i}}/{\underline{k}}\text{”} \right).
$$

 where $X$ is a $[0,1]$\-LUV._

This has the desirable property that ${\mathbb{E}}_k^{\mathbb{V}}(X)\in [0, 1]$, because $\mathbb{V}(-)\in [0, 1]$.

We will often want to take a limit of ${\mathbb{E}}_k^{\mathbb{P}_n}(X)$ as both $k$ and $n$ approach $\infty$. We hereby make the fairly arbitrary choice to focus on the case $k=n$ for simplicity, adopting the shorthand 

$$
{\mathbb{E}}_n:= {\mathbb{E}}_n^{\mathbb{P}_n} .
$$

 In other words, when we examine how a logical inductor’s expectations change on a sequence of sentences over time, we will (arbitrarily) consider approximate expectations that gain in precision at a rate of one unit per day.

We will now show that the expectation operator ${\mathbb{E}}_n$ possesses properties that make it worthy of that name.

**Theorem 58** (Expectations Converge). _The limit ${{\mathbb{E}}_\infty:\mathcal{S}\rightarrow[0,1]}$ defined by 

$$
{\mathbb{E}}_\infty(X) := \lim_{n\rightarrow\infty} {\mathbb{E}}_n(X)
$$

 exists for all $X \in \mathcal{U}$._

Note that ${\mathbb{E}}_\infty(X)$ might not be rational.

Because $\mathbb{P}_\infty$ defines a probability measure over $\mathcal{PC}(\Gamma)$, ${\mathbb{E}}_\infty(X)$ is the average value of $\mathbb{W}(X)$ across all consistent worlds (weighted by $\mathbb{P}_\infty$). In other words, every LUV $X$ can be seen as a random variable with respect to the measure $\mathbb{P}_\infty$, and ${\mathbb{E}}_\infty$ acts as the standard expectation operator on $\mathbb{P}_\infty$. Furthermore,

**Theorem 59** (Linearity of Expectation). _Let ${\overline{a}}, {\overline{b}}$ be bounded ${\overline{\mathbb{P}}}$\-generable sequences of rational numbers, and let ${\overline{X}}, {\overline{Y}}$, and ${\overline{Z}}$ be e.c. sequences of $[0,1]$\-LUVs. If we have $\Gamma\vdash{Z_n= a_nX_n+ b_nY_n}$ for all $n$, then 

$$
a_n{\mathbb{E}}_n(X_n) + b_n{\mathbb{E}}_n(Y_n) \eqsim_n{\mathbb{E}}_n(Z_n).
$$

_

For our next result, we want a LUV which can be proven to take value 1 if $\phi$ is true and 0 otherwise.

**Definition 60** (Indicator LUV). _For any sentence $\phi$, we define its **indicator LUV** by the formula 

$$
\mathop{\mathrm{\mathbb{1}}}(\phi) := \text{“}({\underline{\phi}} \wedge (\nu = 1)) \vee (\lnot{\underline{\phi}} \wedge (\nu = 0))\text{”}.
$$

_

Observe that $\mathop{\mathrm{\mathbb{1}}}(\phi)(1)$ is equivalent to $\phi$, and $\mathop{\mathrm{\mathbb{1}}}(\phi)(0)$ is equivalent to $\lnot\phi$.

**Theorem 61** (Expectations of Indicators). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
{\mathbb{E}}_n(\mathop{\mathrm{\mathbb{1}}}(\phi_n)) \eqsim_n\mathbb{P}_n(\phi_n).
$$

_

In colloquial terms, Theorem 150 says that a logical inductor learns that asking for the expected value of $\mathop{\mathrm{\mathbb{1}}}(\phi)$ is the same as asking for the probability of $\phi$.

To further demonstrate that expectations work as expected, we will show that they satisfy generalized versions of all theorems proven in sections [[#^timely-learning|4.2]]\-[[#^learning-logical-relationships|4.5]]. (Readers without interest in the versions of those theorems for expectations are invited to skip to Section [[#^trust-in-consistency|4.9]].)

#### Collected Theorems for Expectations ^collected-theorems-for-expectations

**Definition 62** (LUV Valuation). _A LUV valuation is any function $\mathbb{U}: \mathcal{U}\to[0, 1]$. Note that ${\mathbb{E}}_n^\mathbb{V}$ and ${\mathbb{E}}_\infty^\mathbb{V}$ are LUV valuations for any valuation $\mathbb{V}$ and $n\in {\mathbb{N}}^+$, and that every world $\mathbb{W}\in \mathcal{PC}(\Gamma)$ is a LUV valuation._

**Definition 63** (LUV Combination). _An **$\boldsymbol{\mathcal{F}}$\-LUV-combination** $B: \mathcal{U}\cup \{1\} \to \mathcal{F}$ is an affine expression of the form 

$$
B:= c+ \alpha_1 X_1 + \cdots + \alpha_k X_k,
$$

 where $(X_1,\ldots,X_k)$ are $[0, 1]$\-LUVs and $(c, \alpha_1, \ldots, \alpha_k)$ are in $\mathcal{F}$. An **$\boldsymbol{\mathcal{E\!F}}$\-LUV-combination**, an **${\mathbb{R}}$\-LUV-combination**, and a **${\mathbb{Q}}$\-LUV-combination** are defined similarly._

_The following concepts are all defined analogously to how they are defined for sentence combinations: $B[1]$, $B[X]$, $\operatorname{rank}(B)$, $\mathbb{U}(B)$ for any LUV valuation $\mathbb{U}$, **$\boldsymbol{\mathcal{F}}$\-LUV-combination progressions**, **$\boldsymbol{\mathcal{E\!F}}$\-LUV-combination progressions**, and ${\overline{\mathbb{P}}}$\-generable LUV-combination sequences. (See definitions 13 and 28 for details.)_

**Definition 64** (Bounded LUV-Combination Sequence). _By $\mathcal{BLCS}({\overline{\mathbb{P}}})$ (mnemonic: **bounded LUV-combination sequences**) we denote the set of all ${\overline{\mathbb{P}}}$\-generable ${\mathbb{R}}$\-LUV-combination sequences ${\overline{B}}$ that are bounded, in the sense that there exists some bound $b$ such that $\| B_n\|_1 \le b$ for all $n$, where $\|\!-\!\|_1$ includes the trailing coefficient._

**Theorem 65** (Expectation Provability Induction). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$ and $b \in {\mathbb{R}}$. If, for all consistent worlds $\mathbb{W}\in\mathcal{PC}(\Gamma)$ and all $n\in {\mathbb{N}}^+$, it is the case that $\mathbb{W}(B_n ) \ge b$, then 

$$
{\mathbb{E}}_n(B_n) \gtrsim_nb,
$$

 and similarly for $=$ and $\eqsim_n$, and for $\leq$ and $\lesssim_n$._

**Theorem 66** (Expectation Coherence). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(B_n)
    \le \liminf_{n\rightarrow\infty}
      {\mathbb{E}}_\infty(B_n)
    \le \liminf_{n\to\infty}
      {\mathbb{E}}_n(B_n),
$$

 and 

$$
\limsup_{n\to\infty} {\mathbb{E}}_n(B_n)
    \le \limsup_{n\rightarrow\infty} {\mathbb{E}}_\infty(B_n)
    \le \limsup_{n\rightarrow\infty} \sup_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(B_n).
$$

_

**Theorem 67** (Persistence of Expectation Knowledge). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}{\mathbb{E}}_m(B_n)= \liminf_{n\to\infty}{\mathbb{E}}_\infty(B_n)
$$

 and 

$$
\limsup_{n\rightarrow\infty}\sup_{m\geq n}{\mathbb{E}}_m(B_n)=\limsup_{n\to\infty}{\mathbb{E}}_\infty(B_n).
$$

_

**Theorem 68** (Expectation Preemptive Learning). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\to\infty} {\mathbb{E}}_n(B_n)= \liminf_{n\rightarrow\infty}\sup_{m\geq n} {\mathbb{E}}_m(B_n)
$$

 and 

$$
\limsup_{n\to\infty} {\mathbb{E}}_n(B_n)= \limsup_{n\rightarrow\infty}\inf_{m\geq n} {\mathbb{E}}_m(B_n) \ .
$$

_

**Definition 69** (Determined via $\Gamma$ (for LUV-Combinations)). _We say that a ${\mathbb{R}}$\-LUV-combination $B$ is **determined via $\boldsymbol{\Gamma}$** if, in all worlds $\mathbb{W}\in \mathcal{PC}(\Gamma)$, the value $\mathbb{W}(B)$ is equal. Let $\operatorname{Val}_{\Gamma}(B)$ denote this value._

_Similarly, a sequence ${\overline{B}}$ of ${\mathbb{R}}$\-LUV-combinations is said to be determined via $\Gamma$ if $B_n$ is determined via $\Gamma$ for all $n$._

**Theorem 70** (Expectation Recurring Unbiasedness). _If ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$ is determined via $\Gamma$, and ${\overline{w}}$ is a ${\overline{\mathbb{P}}}$\-generable divergent weighting weighting such that the support of ${\overline{w}}$ is contained in the image of $f$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-\operatorname{Val}_{\Gamma}(B_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

**Theorem 71** (Expectation Unbiasedness From Feedback). _Given ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$ that is determined via $\Gamma$, a strictly increasing deferral function $f$ such that $\operatorname{Val}_{\Gamma}(A_n )$ can be computed in time ${\mathcal{O}}(f(n+1))$, and a ${\overline{\mathbb{P}}}$\-generable divergent weighting $w$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-\operatorname{Val}_{\Gamma}(B_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{B}}$”._

**Theorem 72** (Learning Pseudorandom LUV Sequences). _Given a ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$ which is determined via $\Gamma$, if there exists a deferral function $f$ such that for any ${\overline{\mathbb{P}}}$\-generable $f$\-patient divergent weighting ${\overline{w}}$, 

$$
\frac{\sum_{i \leq n} w_i  \cdot \operatorname{Val}_{\Gamma}(B_i )}{\sum_{i \leq n} w_i } \gtrsim_n0,
$$

 then 

$$
{\mathbb{E}}_n(B_n) \gtrsim_n0.
$$

_

### Trust in Consistency ^trust-in-consistency

The theorems above all support the hypothesis that logical inductors develop reasonable beliefs about logic. One might then wonder what a logical inductor has to say about some of the classic questions in meta-mathematics. For example, what does a logical inductor over ${\mathsf{PA}}$ say about the consistency of Peano arithmetic?

**Definition 73** (Consistency Statement). _Given a recursively axiomatizable theory $\Gamma^\prime$, define the **$\boldsymbol{n}$\-consistency statement** of $\Gamma^\prime$ to be the formula with one free variable $\nu$ such that 

$$
\operatorname{Con}(\Gamma^\prime)(\nu) := \text{“}\textnormal{There is no proof of \(\bot\) from \({\underline{\Gamma^\prime}}\) with \(\nu\) or fewer symbols}\text{”},
$$

 written in $\mathcal{L}$ using a Gödel encoding. For instance, $\operatorname{Con}({\mathsf{PA}})(\text{“}\operatorname{Ack}(10,10)\text{”})$ says that any proof of $\bot$ from ${\mathsf{PA}}$ requires at least $\operatorname{Ack}(10, 10)$ symbols._

_We further define $\text{“}{\underline{\Gamma^\prime}}\textnormal{\ is consistent}\text{”}$ to be the universal generalization 

$$
\text{“}\forall n \colon \textnormal{there is no proof of \(\bot\) from \({\underline{\Gamma^\prime}}\) in \(n\) or fewer symbols}\text{”},
$$

 and $\text{“}{\underline{\Gamma^\prime}}\textnormal{\ is inconsistent}\text{”}$ for its negation._

**Theorem 74** (Belief in Finitistic Consistency). _Let $f$ be any computable function. Then 

$$
\mathbb{P}_n(\operatorname{Con}(\Gamma)(\text{“}{\underline{f}}({\underline{n}})\text{”})) \eqsim_n1.
$$

_

In other words, if $\Gamma$ is in fact consistent, then ${\overline{\mathbb{P}}}$ learns to trust it for arbitrary finite amounts of time. For any fast-growing function $f$ you can name, ${\overline{\mathbb{P}}}$ eventually learns to believe $\Gamma$ is consistent for proofs of length at most $f(n)$, by day $n$ at the latest. In colloquial terms, if we take a logical inductor over ${\mathsf{PA}}$ and show it a computable function $f$ that, on each input $n$, tries a new method for finding an inconsistency in ${\mathsf{PA}}$, then the logical inductor will stare at the function for a while and eventually conclude that it’s not going to succeed (by learning to assign low probability to $f(n)$ proving $\bot$ from ${\mathsf{PA}}$ by day $n$ at the latest, regardless of how long $f$ runs). That is to say, a logical inductor over ${\mathsf{PA}}$ learns to trust Peano arithmetic _inductively_.

By the same mechanism, a logical inductor over $\Gamma$ can learn inductively to trust the consistency of _any_ consistent theory, including consistent theories that are stronger than $\Gamma$ (in the sense that they can prove $\Gamma$ consistent):

**Theorem 75** (Belief in the Consistency of a Stronger Theory). _Let $\Gamma^\prime$ be any recursively axiomatizable consistent theory. Then 

$$
\mathbb{P}_n(\operatorname{Con}(\Gamma^\prime)(\text{“}{\underline{f}}({\underline{n}})\text{”})) \eqsim_n1.
$$

_

For instance, a logical inductor over ${\mathsf{PA}}$ can learn inductively to trust the consistency of ${\mathsf{ZFC}}$ for finite proofs of arbitrary length (assuming ${\mathsf{ZFC}}$ is in fact consistent).

These two theorems alone are unimpressive. Any algorithm that assumes consistency until proven otherwise can satisfy these theorems, and because every inconsistent theory admits a finite proof of inconsistency, those naı̈ve algorithms will disbelieve any inconsistent theory eventually. But those algorithms will still believe inconsistent theories for quite a long time, whereas logical inductors learn to distrust inconsistent theories in a timely manner:

**Theorem 76** (Disbelief in Inconsistent Theories). _Let ${\overline{\Gamma^\prime}}$ be an e.c. sequence of recursively axiomatizable inconsistent theories. Then 

$$
\mathbb{P}_n(\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is inconsistent}\text{”}) \eqsim_n1,
$$

 so 

$$
\mathbb{P}_n(\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is consistent}\text{”}) \eqsim_n0.
$$

_

In other words, logical inductors learn in a timely manner to distrust inconsistent theories that can be efficiently named, even if the shortest proofs of inconsistency are very long.

Note that Theorem 123 (Belief in Finitistic Consistency) _does not say_ 

$$
\mathbb{P}_\infty(\text{“}{\underline{\Gamma}}\textnormal{ is consistent}\text{”})
$$

 is equal to 1, nor even that it’s particularly high. On the contrary, by Theorem 165 (Non-Dogmatism), the limiting probability on that sentence is bounded away from 0 and 1 (because both that sentence and its negation are consistent with $\Gamma$). Intuitively, ${\overline{D}}$ never reveals evidence against the existence of non-standard numbers, so ${\overline{\mathbb{P}}}$ remains open to the possibility. This is important for Theorem 169 (Closure Under Conditioning), which say that logical inductors can safely be conditioned on any sequence of statements that are consistent with $\Gamma$, but it also means that ${\overline{\mathbb{P}}}$ will not give an affirmative answer to the question of whether ${\mathsf{PA}}$ is consistent in full generality.

In colloquial terms, if you hand a logical inductor any _particular_ computation, it will tell you that that computation isn’t going to output a proof $\bot$ from the axioms of ${\mathsf{PA}}$, but if you ask whether ${\mathsf{PA}}$ is consistent _in general_, it will start waxing philosophical about non-standard numbers and independent sentences—not unlike a human philosopher.

A reasonable objection here is that Theorem 123 (Belief in Finitistic Consistency) is not talking about the consistency of the Peano axioms, it’s talking about _computations_ that search for proofs of contradiction from ${\mathsf{PA}}$. This is precisely correct, and brings us to our next topic.

### Reasoning about Halting ^reasoning-about-halting

Consider the famous halting problem of Turing (1936). Turing proved that there is no general algorithm for determining whether or not an arbitrary computation halts. Let’s examine what happens when we confront logical inductors with the halting problem.

**Theorem 77** (Learning of Halting Patterns). _Let ${\overline{m}}$ be an e.c. sequence of Turing machines, and ${\overline{x}}$ be an e.c. sequence of bitstrings, such that $m_n$ halts on input $x_n$ for all $n$. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{m_n}}\) halts on input \({\underline{x_n}}\)}\text{”}) \eqsim_n1.
$$

_

Note that the individual Turing machines _do not_ need to have fast runtime. All that is required is that the _sequence_ ${\overline{m}}$ be efficiently computable, i.e., it must be possible to write out the source code specifying $m_n$ in time polynomial in $n$. The runtime of an individual $m_n$ is immaterial for our purposes. So long as the $m_n$ all halt on the corresponding $x_n$, ${\overline{\mathbb{P}}}$ recognizes the pattern and learns to assign high probability to $\text{“}\textnormal{\({\underline{m_n}}\) halts on input \({\underline{x_n}}\)}\text{”}$ no later than the $n$th day.

Of course, this is not so hard on its own—a function that assigns probability 1 to everything also satisfies this property. The real trick is separating the halting machines from the non-halting ones. This is harder. It is easy enough to show that ${\overline{\mathbb{P}}}$ learns to recognize e.c. sequences of machines that _provably_ fail to halt:

**Theorem 78** (Learning of Provable Non-Halting Patterns). _Let ${\overline{q}}$ be an e.c. sequence of Turing machines, and ${\overline{y}}$ be an e.c. sequence of bitstrings, such that $q_n$ _provably_ fails to halt on input $y_n$ for all $n$. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\)}\text{”}) \eqsim_n0.
$$

_

Of course, it’s not too difficult to disbelieve that the provably-halting machines will halt; what makes the above theorem non-trivial is that ${\overline{\mathbb{P}}}$ learns _in a timely manner_ to expect that those machines won’t halt. Together, the two theorems above say that if there is any efficient method for generating computer programs that definitively either halt or don’t (according to $\Gamma$) then ${\overline{\mathbb{P}}}$ will learn the pattern.

The above two theorems only apply to cases where $\Gamma$ can prove that the machine either halts or doesn’t. The more interesting case is the one where a Turing machine $q$ fails to halt on input $y$, but $\Gamma$ is not strong enough to prove this fact. In this case, $\mathbb{P}_\infty$’s probability of $q$ halting on input $y$ is positive, by Theorem 165 (Non-Dogmatism). Nevertheless, ${\overline{\mathbb{P}}}$ still learns to stop expecting that those machines will halt after any reasonable amount of time:

**Theorem 79** (Learning not to Anticipate Halting). _Let ${\overline{q}}$ be an e.c. sequence of Turing machines, and let ${\overline{y}}$ be an e.c. sequence of bitstrings, such that $q_n$ does not halt on input $y_n$ for any $n$. Let $f$ be any computable function. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\) within \({\underline{f}}({\underline{n}})\) steps}\text{”}) \eqsim_n0.
$$

_

For example, let ${\overline{y}}$ be an enumeration of all bitstrings, and let ${\overline{q}}$ be the constant sequence $(q, q, \ldots)$ where $q$ is a Turing machine that does not halt on any input. If $\Gamma$ cannot prove this fact, then ${\overline{\mathbb{P}}}$ will never be able to attain certainty about claims that say $q$ fails to halt, but by Theorem 128, it still learns to expect that $q$ will run longer than any computable function you can name. In colloquial terms, while ${\overline{\mathbb{P}}}$ won’t become certain that non-halting machines don’t halt (which is impossible), it _will_ put them in the “don’t hold your breath” category (along with some long-running machines that do halt, of course).

These theorems can be interpreted as justifying the intuitions that many computer scientists have long held towards the halting problem: It is impossible to tell whether or not a Turing machine halts in full generality, but for large classes of well-behaved computer programs (such as e.c. sequences of halting programs and provably non-halting programs) it’s quite possible to develop reasonable and accurate beliefs. The boundary between machines that compute fast-growing functions and machines that never halt is difficult to distinguish, but even in those cases, it’s easy to learn to stop expecting those machines to halt within any reasonable amount of time. (See also the work of Calude and Stay (2008) for other formal results backing up this intuition.)

One possible objection here is that the crux of the halting problem (and of the $\Gamma$\-trust problem) are not about making good predictions, they are about handling diagonalization and paradoxes of self-reference. Gödel’s incompleteness theorem constructs a sentence that says “there is no proof of this sentence from the axioms of ${\mathsf{PA}}$”, and Turing’s proof of the undecidability of the halting problem constructs a machine which halts iff some other machine thinks it loops. ${\overline{\mathbb{P}}}$ learning to trust $\Gamma$ is different altogether from ${\overline{\mathbb{P}}}$ learning to trust _itself_. So let us turn to the topic of ${\overline{\mathbb{P}}}$’s beliefs about ${\overline{\mathbb{P}}}$.

### Introspection ^introspection

Because we’re assuming $\Gamma$ can represent computable functions, we can write sentences describing the beliefs of ${\overline{\mathbb{P}}}$ at different times. What happens when we ask ${\overline{\mathbb{P}}}$ about sentences that refer to itself?

For instance, consider a sentence $\psi := \text{“}{\underline{\mathbb{P}}}_{{\underline{n}}}({\underline{\smash{\phi}}}) > 0.7\text{”}$ for some specific $n$ and $\phi$, where ${\overline{\mathbb{P}}}$’s beliefs about $\psi$ should depend on what its beliefs about $\phi$ are on the $n$th day. Will ${\overline{\mathbb{P}}}$ figure this out and get the probabilities right on day $n$? For any particular $\phi$ and $n$ it’s hard to say, because it depends on whether ${\overline{\mathbb{P}}}$ has learned how $\psi$ relates to ${\overline{\mathbb{P}}}$ and $\phi$ yet. If however we take an e.c. _sequence_ of ${\overline{\psi}}$ which all say “$\phi$ will have probability greater than 0.7 on day $n$” with $n$ varying, then we can guarantee that ${\overline{\mathbb{P}}}$ will learn the pattern, and start having accurate beliefs about its own beliefs:

**Theorem 80** (Introspection). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences, and ${\overline{a}}$, ${\overline{b}}$ be ${\overline{\mathbb{P}}}$\-generable sequences of probabilities. Then, for any e.c. sequence of positive rationals ${\overline{\delta}}\to 0$, there exists a sequence of positive rationals ${\overline{{\varepsilon}}}\to 0$ such that for all $n$:_

1.  _if $\mathbb{P}_n(\phi_n)\in(a_n+\delta_n,b_n-\delta_n)$, then 
    
    $$
    \mathbb{P}_n(\text{“}{\underline{a_n}} < {\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}}) < {\underline{b_n}}\text{”}) > 1-\varepsilon_n,
    $$
    
    _
    
2.  _if $\mathbb{P}_n(\phi_n)\notin(a_n-\delta_n,b_n+\delta_n)$, then 
    
    $$
    \mathbb{P}_n(\text{“}{\underline{a_n}} < {\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}}) < {\underline{b_n}}\text{”}) < \varepsilon_n.
    $$
    
    _
    

In other words, for any pattern in ${\overline{\mathbb{P}}}$’s beliefs that can be efficiently written down (such as “${\overline{\mathbb{P}}}$’s probabilities on ${\overline{\phi}}$ are between $a$ and $b$ on these days”), ${\overline{\mathbb{P}}}$ learns to believe the pattern if it’s true, and to disbelieve it if it’s false (with vanishing error).

At a first glance, this sort of self-reflection may seem to make logical inductors vulnerable to paradox. For example, consider the sequence of sentences 

$$
{\overline{\chi^{0.5}}} := (\text{“}{{\underline{\mathbb{P}}}_{{\underline{n}}}}({\underline{\chi^{0.5}_n}}) < 0.5\text{”})_{n\in {{\mathbb{N}}^+}}
$$

 such that $\chi^{0.5}_n$ is true iff ${\overline{\mathbb{P}}}$ assigns it a probability less than 50% on day $n$. Such a sequence can be defined by Gödel’s diagonal lemma. These sentences are probabilistic versions of the classic “liar sentence”, which has caused quite a ruckus in the setting of formal logic (Grim 1991; McGee 1990; Glanzberg 2001; Gupta and Belnap 1993; Eklund 2002). Because our setting is probabilistic, it’s perhaps most closely related to the “unexpected hanging” paradox—$\chi^{0.5}_n$ is true iff ${\overline{\mathbb{P}}}$ thinks it is unlikely on day $n$. How do logical inductors handle this sort of paradox?

**Theorem 81** (Paradox Resistance). _Fix a rational $p\in(0,1)$, and define an e.c. sequence of “paradoxical sentences” ${\overline{\chi^p}}$ satisfying 

$$
\Gamma\vdash{{{\underline{\chi^p_n}}} \leftrightarrow\left(
      {{\underline{\mathbb{P}}}_{{\underline{n}}}}({{\underline{\chi^p_n}}}) < {\underline{p}}
    \right)}
$$

 for all $n$. Then 

$$
\lim_{n\to\infty}\mathbb{P}_n(\chi^p_n)=p.
$$

_

A logical inductor responds to paradoxical sentences ${\overline{\chi^p}}$ by assigning probabilities that converge on $p$. For example, if the sentences say “${\overline{\mathbb{P}}}$ will assign me a probability less than 80% on day $n$”, then $\mathbb{P}_n$ (once it has learned the pattern) starts assigning probabilities extremely close to 80%—so close that traders can’t tell if it’s slightly above or slightly below. By Theorem 132 (Recurring Unbiasedness), the frequency of truth in $\chi^p_{\leq n}$ will have a limit point at 0.8 as $n \to \infty$, and by the definition of logical induction, there will be no efficiently expressible method for identifying a bias in the price.

Let us spend a bit of time understanding this result. After day $n$, $\chi_n^{0.8}$ is “easy” to get right, at least for someone with enough computing power to compute $\mathbb{P}_n(\chi_n^{0.8})$ to the necessary precision (it will wind up _very_ close to 0.8 for large $n$). Before day $n$, we can interpret the probability of $\chi_n^{0.8}$ as the price of a share that’s going to pay out \$1 if the price on day $n$ is less than 80¢, and \$0 otherwise. What’s the value of this share? Insofar as the price on day $n$ is going to be low, the value is high; insofar as the price is going to be high, the value is low. So what actually happens on the $n$th day? Smart traders buy $\chi_n^{0.8}$ if its price is lower than 80¢, and sell it if its price is higher than 80¢. By the continuity constraints on the traders, each one has a price at which they stop buying $\chi_n^{0.8}$, and Theorem 155 (Paradox Resistance) tells us that the stable price exists extremely close to 80¢. Intuitively, it must be so close that traders can’t tell which way it’s going to go, biased on the low side, so that it looks 80% likely to be below and 20% likely to be above to any efficient inspection. For if the probability seemed more than 80% likely to be below, traders would buy; and if it seemed anymore than 20% likely to be above, traders would sell.

To visualize this, imagine that your friend owns a high-precision brain-scanner and can read off your beliefs. Imagine they ask you what probability you assign to the claim “you will assign probability $<$80% to this claim at precisely 10am tomorrow”. As 10am approaches, what happens to your belief in this claim? If you become extremely confident that it’s going to be true, then your confidence should drop. But if you become fairly confident it’s going to be false, then your confidence should spike. Thus, your probabilities should oscillate, pushing your belief so close to 80% that you’re not quite sure which way the brain scanner will actually call it. In response to a paradoxical claim, this is exactly how ${\overline{\mathbb{P}}}$ behaves, once it’s learned how the paradoxical sentences work.

Thus, logical inductors have reasonable beliefs about their own beliefs even in the face of paradox. We can further show that logical inductors have “introspective access” to their own beliefs and expectations, via the medium of logically uncertain variables:

**Theorem 82** (Expectations of Probabilities). _Let ${\overline{\phi}}$ be an efficiently computable sequence of sentences. Then 

$$
\mathbb{P}_n(\phi_n)\eqsim_n{\mathbb{E}}_n(\text{“}{\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}})\text{”}).
$$

_

**Theorem 83** (Iterated Expectations). _Suppose ${\overline{X}}$ is an efficiently computable sequence of LUVs. Then 

$$
{\mathbb{E}}_n(X_n)\eqsim_n{\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{\underline{n}}({\underline{X_n}})\text{”}).
$$

_

Next, we turn our attention to the question of what a logical inductor believes about its _future_ beliefs.

### Self-Trust ^self-trust

The coherence conditions of classical probability theory guarantee that a probabilistic reasoner trusts their future beliefs, whenever their beliefs change in response to new empirical observations. For example, if a reasoner $\mathrm{Pr}(-)$ knows that tomorrow they’ll see some evidence $e$ that will convince them that Miss Scarlet was the murderer, then they already believe that she was the murderer today: 

$$
\mathrm{Pr}(\mathrm{Scarlet}) = \mathrm{Pr}(\mathrm{Scarlet}\mid e) \mathrm{Pr}(e) + \mathrm{Pr}(\mathrm{Scarlet}\mid \lnot e) \mathrm{Pr}(\lnot e).
$$

 In colloquial terms, this says “my current beliefs are _already_ a mixture of my expected future beliefs, weighted by the probability of the evidence that I expect to see.”

Logical inductors obey similar coherence conditions with respect to their future beliefs, with the difference being that a logical inductor updates its belief by gaining more knowledge about _logical_ facts, both by observing an ongoing process of deduction and by thinking for longer periods of time. Thus, the self-trust properties of a logical inductor follow a slightly different pattern:

**Theorem 84** (Expected Future Expectations). _Let $f$ be a deferral function (as per Definition 30), and let ${\overline{X}}$ denote an e.c. sequence of $[0,1]$\-LUVs. Then 

$$
{\mathbb{E}}_n(X_n) \eqsim_n
    {\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}})}({\underline{X_n}})\text{”}).
$$

_

Roughly speaking, Theorem 158 says that a logical inductor’s current expectation of $X$ on day $n$ is _already_ equal to its expected value of $X$ in $f(n)$ days. In particular, it learns in a timely manner to set its current expectations equal to its future expectations on any LUV. In colloquial terms, once a logical inductor has figured out how expectations work, it will never say “I currently believe that the ${\overline{X}}$ variables have low values, but tomorrow I’m going to learn that they have high values”. Logical inductors already expect today what they expect to expect tomorrow.

It follows immediately from theorems 158 (Expected Future Expectations) and 150 (Expectations of Indicators) that the current beliefs of a logical inductor are set, in a timely manner, to equal their future expected beliefs.

**Theorem 85** (No Expected Net Update). _Let $f$ be a deferral function, and let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
\mathbb{P}_n(\phi_n) \eqsim_n
      {\mathbb{E}}_n(\text{“}{\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}})\text{”}).
$$

_

In particular, if ${\overline{\mathbb{P}}}$ knows that its future self is going to assign some sequence ${\overline{{p}}}$ of probabilities to ${\overline{\phi}}$, then it starts assigning ${\overline{{p}}}$ to ${\overline{\phi}}$ in a timely manner.

Theorem 158 (Expected Future Expectations) can be generalized to cases where the LUV on day $n$ is multiplied by an expressible feature:

**Theorem 86** (No Expected Net Update under Conditionals). _Let $f$ be a deferral function, and let ${\overline{X}}$ denote an e.c. sequence of $[0,1]$\-LUVs, and let ${\overline{w}}$ denote a ${\overline{\mathbb{P}}}$\-generable sequence of real numbers in $[0, 1]$. Then 

$$
{\mathbb{E}}_n(\text{“}{\underline{X_n}} \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})}\text{”}) \eqsim_n
  {\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}})}({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})}\text{”}).
$$

_

To see why Theorem 160 is interesting, it helps to imagine the case where ${\overline{X}}$ is a series of bundles of goods and services, and $w_n$ is $\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}({\mathbb{E}}_{f(n)}(X_n) > 0.7)$ for some sequence of rational numbers ${\overline{\delta}}\to 0$, as per Definition 25. This value is 1 if ${\overline{\mathbb{P}}}$ will expect the $n$th bundle to be worth more than 70¢ on day $f(n)$, and 0 otherwise, and intermediate if the case isn’t quite clear. Then 

$$
{\mathbb{E}}_n\left(\text{“}{\underline{X}}_{\underline{n}} \cdot
    {\underline{\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}}}\left(
      {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}})}({\underline{X}}_{\underline{n}}) > 0.7
    \right)\text{”}
  \right)
$$

 can be interpreted as ${\overline{\mathbb{P}}}$’s expected value of the bundle on day $n$, in cases where ${\overline{\mathbb{P}}}$ is going to think it’s worth at least 70¢ on day $f(n)$. Now assume that $\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}({\mathbb{E}}_{f(n)}(X_n)) > 0$ and divide it out of both sides, in which case the theorem roughly says 

$$
{\mathbb{E}}_\mathrm{now}(X \mid {\mathbb{E}}_\mathrm{later}(X) > 0.7) \eqsim {\mathbb{E}}_\mathrm{now}({\mathbb{E}}_\mathrm{later}(X) \mid {\mathbb{E}}_\mathrm{later}(X) > 0.7),
$$

 which says that ${\overline{\mathbb{P}}}$’s expected value of the bundle now, given that it’s going to think the bundle has a value of at least 70¢ later, is equal to whatever it expects to think later, conditioned on thinking later that the bundle is worth at least 70¢.

Combining this idea with indicator functions, we get the following theorem:

**Theorem 87** (Self-Trust). _Let $f$ be a deferral function, ${\overline{\phi}}$ be an e.c. sequence of sentences, ${\overline{\delta}}$ be an e.c. sequence of positive rational numbers, and ${\overline{{p}}}$ be a ${\overline{\mathbb{P}}}$\-generable sequence of rational probabilities. Then 

$$
{\mathbb{E}}_n\left(\text{“}
      {\underline{\mathop{\mathrm{\mathbb{1}}}(\phi_n)}} \cdot
      {\underline{\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}}}\left(
        {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}}) > {\underline{p_n}}
      \right)
    \text{”}\right)
    \gtrsim_n
    p_n\cdot
    {\mathbb{E}}_n\left(\text{“}
      {\underline{\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}}}\left(
        {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}}) > {\underline{p_n}}
      \right)
    \text{”}\right).
$$

_

Very roughly speaking, if we squint at Theorem 161, it says something like 

$$
{\mathbb{E}}_\mathrm{now}(\phi \mid P_\mathrm{later}(\phi) > p) \gtrsim p,
$$

 i.e., if we ask ${\overline{\mathbb{P}}}$ what it would believe about $\phi$ now if it learned that it was going to believe $\phi$ with probability at least $p$ in the future, then it will answer with a probability that is at least $p$.

As a matter of fact, Theorem 161 actually says something slightly weaker, which is also more desirable. Let each $\phi_n$ be the self-referential sentence $\text{“}{\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}}) < 0.5\text{”}$ which says that the future $\mathbb{P}_{f(n)}$ will assign probability less than 0.5 to $\phi_n$. Then, conditional on $\mathbb{P}_{f(n)}(\phi_n) \ge 0.5$, $\mathbb{P}_n$ should believe that the probability of $\phi_n$ is 0. And indeed, this is what a logical inductor will do: 

$$
\mathbb{P}_n\left(
    \text{“}{\underline{\phi_n}} \land
    (
      {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}(
        {\underline{\phi_n}}
      ) \ge 0.5
    )\text{”}
  \right) \eqsim_n0,
$$

 by Theorem 119 (Persistence of Knowledge), because each of those conjunctions is disprovable. This is why Theorem 161 uses continuous indicator functions: With discrete conjunctions, the result would be undesirable (not to mention false).

What Theorem 161 says is that ${\overline{\mathbb{P}}}$ attains self-trust of the “if in the future I will believe $x$ is very likely, then it must be because $x$ is very likely” variety, while retaining the ability to think it can outperform its future self’s beliefs when its future self confronts paradoxes. In colloquial terms, if we ask “what’s your probability on the paradoxical sentence $\phi_n$ given that your future self believes it with probability _exactly_ 0.5?” then ${\overline{\mathbb{P}}}$ will answer “very low”, but if we ask “what’s your probability on the paradoxical sentence $\phi_n$ given that your future self believes it with probability _extremely close to_ 0.5?” then ${\overline{\mathbb{P}}}$ will answer “roughly 0.5.”

Still speaking roughly, this means that logical inductors trust their future beliefs to be accurate and only change for good reasons. Theorem 161 says that if you ask “what’s the probability of $\phi$, given that in the future you’re going to believe it’s more than $95\%$ likely?” then you’ll get an answer that’s no less than $0.95$, even if the logical inductor currently thinks that $\phi$ is unlikely.

## Construction ^construction

In this section, we show how given any deductive process ${\overline{D}}$, we can construct a computable belief sequence, called ${\overline{\textnormal{{\texttt{LIA}}}}}$, that satisfies the logical induction criterion relative to ${\overline{D}}$. Roughly speaking, ${\overline{\textnormal{{\texttt{LIA}}}}}$ works by simulating an economy of traders and using Brouwer’s fixed point theorem to set market prices such that no trader can exploit the market relative to ${\overline{D}}$.

We will build $\textnormal{{\texttt{LIA}}}$ from three subroutines called $\textnormal{{\texttt{MarketMaker}}}$, $\textnormal{{\texttt{Budgeter}}}$, and $\textnormal{{\texttt{TradingFirm}}}$. Intuitively, $\textnormal{{\texttt{MarketMaker}}}$ will be an algorithm that sets market prices by anticipating what a single trader is about to do, $\textnormal{{\texttt{Budgeter}}}$ will be an algorithm for altering a trader to stay within a certain budget, and $\textnormal{{\texttt{TradingFirm}}}$ will be an algorithm that uses $\textnormal{{\texttt{Budgeter}}}$ to combine together an infinite sequence of carefully chosen e.c. traders (via a sum calculable in finite time) into a single trader that exploits a given market if any e.c. trader exploits that market. Then, $\textnormal{{\texttt{LIA}}}$ will work by using $\textnormal{{\texttt{MarketMaker}}}$ to make a market not exploitable by $\textnormal{{\texttt{TradingFirm}}}$ and hence not exploitable by any e.c. trader, thereby satisfying the logical induction criterion.

To begin, we will need a few basic data types for our subroutines to pass around:

**Definition 88** (Belief History). _An **$\boldsymbol{n}$\-belief history** $\mathbb{P}_{\leq n} = (\mathbb{P}_1,\ldots,\mathbb{P}_n)$ is a finite list of belief states of length $n$._

**Definition 89** (Strategy History). _An **$\boldsymbol{n}$\-strategy history** $T_{\leq n} = (T_1,\ldots,T_n)$ is a finite list of trading strategies of length $n$, where $T_i$ is an $i$\-strategy._

**Definition 90** (Support). _For any valuation $\mathbb{V}$ we define 

$$
\operatorname{Support}(\mathbb{V}) := \{ \phi\in\mathcal{S}\mid
\mathbb{V}(\phi)\neq 0 \},
$$

 and for any $n$\-strategy $T_n$ we define 

$$
\operatorname{Support}(T_n) := \{ \phi\in\mathcal{S}\mid
T_n[\phi]\not\equiv 0 \}.
$$

 Observe that for any belief state $\mathbb{P}$ and any $n$\-strategy $T_n$, $\operatorname{Support}(\mathbb{P})$ and $\operatorname{Support}(T_n)$ are computable from the finite lists representing $\mathbb{P}$ and $T_n$._

### Constructing $\textnormal{{\texttt{MarketMaker}}}$ ^constructing

Here we define the $\textnormal{{\texttt{MarketMaker}}}$ subroutine and establish its key properties. Intuitively, given any trader ${\overline{T}}$ as input, on each day $n$, $\textnormal{{\texttt{MarketMaker}}}$ looks at the trading strategy $T_n$ and the valuations $\mathbb{P}_{\leq n-1}$ output by $\textnormal{{\texttt{MarketMaker}}}$ on previous days. It then uses an approximate fixed point (guaranteed to exist by Brouwer’s fixed point theorem) that sets prices $\mathbb{P}_n$ for that day such that when the trader’s strategy $T_n$ reacts to the prices, the resulting trade $T_n(\mathbb{P}_{\leq n})$ earns at most a very small positive amount of value in any world. Intuitively, the fixed point finds the trader’s “fair prices”, such that they abstain from betting, except possibly to buy sentences at a price very close to \$1 or sell them at a price very close to \$0, thereby guaranteeing that very little value can be gained from the trade.

**Lemma 91** (Fixed Point Lemma). _Let $T_n$ be any $n$\-strategy, and let $\mathbb{P}_{\leq n-1}$ be any $(n-1)$\-belief history. There exists a valuation $\mathbb{V}$ with $\operatorname{Support}(\mathbb{V})\subseteq \operatorname{Support}(T_n)$ such that 

$$
\begin{equation}
\tag{91}
    \textnormal{for all worlds \(\mathbb{W}\in \mathcal{W}\):}\quad\mathbb{W}\left(T_n(\mathbb{P}_{\le n-1},\mathbb{V})\right) \le  0.
\end{equation}
$$

_

_Proof._ We will use Brouwer’s fixed point theorem to find “prices” $\mathbb{V}$ such that $T_n$ only ever buys shares for \$1 or sells them for \$0, so it cannot make a profit in any world. Intuitively, we do this by making a “price adjustment” mapping called ${{\operatorname{fix}}}$ that moves prices toward 1 or 0 (respectively) as long as $T_n$ would buy or sell (respectively) any shares at those prices, and finding a fixed point of that mapping.

First, we let $\mathcal{S}' = \operatorname{Support}(T_n)$ and focus on the set 

$$
\begin{equation*}
\mathcal{V}' := \{ \mathbb{V}\mid \operatorname{Support}(\mathbb{V})\subseteq \mathcal{S}'\}.
\end{equation*}
$$

 Observe that $\mathcal{V}'$ is equal to the natural inclusion of the finite-dimensional cube $[0,1]^{\mathcal{S}'}$ in the space of all valuations $\mathcal{V}= [0,1]^{\mathcal{S}}$. We now define our “price adjustment” function ${{\operatorname{fix}}}:\mathcal{V}'\to\mathcal{V}'$ as follows: 

$$
\begin{equation*}
{{\operatorname{fix}}}(\mathbb{V})(\phi):=
   \max\left(0,\; \min\left(
     1, \; \mathbb{V}(\phi)+ T_n(\mathbb{P}_{\le n-1},\mathbb{V})[\phi]
   \right)
\right).
\end{equation*}
$$

 This map has the odd property that it adds prices and trade volumes, but it does the trick. Notice that ${{\operatorname{fix}}}$ is a function from the compact, convex space $\mathcal{V}'$ to itself, so if it is continuous, it satisfies the antecedent of Brouwer’s fixed point theorem. Observe that ${{\operatorname{fix}}}$ is in fact continuous, because trade strategies are continuous. Indeed, we required that trade strategies be continuous for precisely this purpose. Thus, by Brouwer’s fixed point theorem, ${{\operatorname{fix}}}$ has at least one fixed point $\mathbb{V}^{{\operatorname{fix}}}$ that satisfies, for all sentences $\phi\in\mathcal{S}'$, 

$$
\begin{equation*}
\mathbb{V}^{{\operatorname{fix}}}(\phi) = \max(0, \; \min( 1, \; \mathbb{V}^{{\operatorname{fix}}}(\phi) + T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})[\phi]) ).
\end{equation*}
$$

 Fix a world $\mathbb{W}$ and observe from this equation that if $T_n$ buys some shares of $\phi\in\mathcal{S}'$ at these prices, i.e. if $T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})[\phi]>0$, then $\mathbb{V}^{{\operatorname{fix}}}(\phi)=1$, and in particular, $\mathbb{W}(\phi) - \mathbb{V}^{{\operatorname{fix}}}(\phi)\leq 0$. Similarly, if $T_n$ sells some shares of $\phi$, i.e. if $T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})[\phi]<0$, then $\mathbb{V}^{{\operatorname{fix}}}(\phi)=0$, so $\mathbb{W}(\phi) - \mathbb{V}^{{\operatorname{fix}}}(\phi) \geq 0$. In either case, we have 

$$
0 \geq (\mathbb{W}(\phi)-\mathbb{V}^{{\operatorname{fix}}}(\phi))\cdot T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})[\phi]
$$

since the two factors always have opposite sign (or at least one factor is 0). Summing over all $\phi$, remembering that $T_n(\mathbb{V}_{\leq n})[\phi]=0$ for $\phi \notin \mathcal{S}'$, gives

$$
\begin{align*}
0 &\geq \sum_{\phi\in\mathcal{S}} (\mathbb{W}(\phi)-\mathbb{V}^{{\operatorname{fix}}}(\phi))\cdot T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})[\phi]
\\
&=\mathbb{W}(T_n(\mathbb{P}_{\leq n},\mathbb{V}^{{\operatorname{fix}}})) - \mathbb{V}^{{\operatorname{fix}}}(T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}}))
\end{align*}
$$

 since the values of the “cash” terms $\mathbb{W}(T_n(\mathbb{P}_{\leq n},\mathbb{V}^{{\operatorname{fix}}})[1])$ and $\mathbb{V}^{{\operatorname{fix}}}(T_n(\mathbb{P}_{\leq n},\mathbb{V}^{{\operatorname{fix}}})[1])$ are by definition both equal to $T_n(\mathbb{P}_{\leq n},\mathbb{V}^{{\operatorname{fix}}})[1]$ and therefore cancel. But 

$$
\mathbb{V}^{{\operatorname{fix}}}(T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})) = 0
$$

 by definition of a trading strategy, so for any world $\mathbb{W}$, we have 

$$
0\ge\mathbb{W}(T_n(\mathbb{P}_{\le n-1},\mathbb{V}^{{\operatorname{fix}}})).
$$

 ◻

**Definition/Proposition 92** ($\textnormal{{\texttt{MarketMaker}}}$). _There exists a computable function, henceforth named $\textnormal{{\texttt{MarketMaker}}}$, satisfying the following definition. Given as input any $n\in{\mathbb{N}}^+$, any $n$\-strategy $T_n$, and any $(n-1)$\-belief history $\mathbb{P}_{\le n-1}$, $\textnormal{{\texttt{MarketMaker}}}_n(T_n,\mathbb{P}_{\le n-1})$ returns a belief state $\mathbb{P}$ with $\operatorname{Support}(\mathbb{P})\subseteq\operatorname{Support}(T_n)$ such that 

$$
\begin{equation}
\tag{92}
    \textnormal{for all worlds \(\mathbb{W}\in \mathcal{W}\):}\quad\mathbb{W}\left(T_n(\mathbb{P}_{\le n-1},\mathbb{P})\right) \le  2^{-n}.
\end{equation}
$$

_

_Proof._ Essentially, we will find a rational approximation $\mathbb{P}$ to the fixed point $\mathbb{V}^{{\operatorname{fix}}}$ in the previous lemma, by brute force search. This requires some care, because the set of all worlds is uncountably infinite.

First, given $T_n$ and $\mathbb{P}_{\le n-1}$, let $\mathcal{S}':=\operatorname{Support}(T_n)$, $\mathcal{V}' := \{\mathbb{V}\mid \operatorname{Support}(\mathbb{V})\subseteq \mathcal{S}'\}$, and take $\mathbb{V}^{{\operatorname{fix}}}\in\mathcal{V}'$ satisfying (91). Let $\mathcal{W}' := \{\mathbb{W}\mid \operatorname{Support}(\mathbb{W})\subseteq\mathcal{S}'\}$, and for any world $\mathbb{W}$, define $\mathbb{W}'\in\mathcal{W}'$ by 

$$
\mathbb{W}'(\phi) :=
\begin{cases}
\mathbb{W}(\phi) &\text{if \(\phi\in\mathcal{S}'\),}\\
0 &\text{otherwise.}
\end{cases}
$$

 Observe that for any $\mathbb{W}\in\mathcal{W}$, the function $\mathcal{V}'\to{\mathbb{R}}$ given by 

$$
\mathbb{V}\mapsto\mathbb{W}
(T_n(\mathbb{P}_{\le n-1},\mathbb{V})) = \mathbb{W}'
(T_n(\mathbb{P}_{\le n-1},\mathbb{V}))
$$

 is a continuous function of $\mathbb{V}$ that depends only on $\mathbb{W}'$. Since the set $\mathcal{W}'$ is finite, the function 

$$
\mathbb{V}\mapsto\sup_{\mathbb{W}\in\mathcal{W}} \mathbb{W}
(T_n(\mathbb{P}_{\le n-1},\mathbb{V})) = \max_{\mathbb{W}'\in\mathcal{W}'} \mathbb{W}'
(T_n(\mathbb{P}_{\le n-1},\mathbb{V}))
$$

 is the maximum of a finite number of continuous functions, and is therefore continuous. Hence there is some neighborhood in $\mathcal{V}'$ around $\mathbb{V}^{{\operatorname{fix}}}$ with image in $(-\infty,2^{-n}) \subset {\mathbb{R}}$. By the density of rational points in $\mathcal{V}'$, there is therefore some belief state $\mathbb{P}\in\mathcal{V}'\cap {\mathbb{Q}}^{\mathcal{S}}$ satisfying (92), as needed.

It remains to show that such a $\mathbb{P}$ can in fact be found by brute force search. First, recall that a belief state $\mathbb{P}$ is a rational-valued finite-support map from $\mathcal{S}$ to $[0,1]$, and so can be represented by a finite list of pairs $(\phi,q)$ with $\phi\in\mathcal{S}$ and $q\in{\mathbb{Q}}\cap [0,1]$. Since $\mathcal{S}$ and $[0,1]\cap {\mathbb{Q}}$ are computably enumerable, so is the set of all belief states.

Thus, we can computably “search” though all possible $\mathbb{P}$s, so we need only establish that given $n$, $T_n$, and $\mathbb{P}_{\le n-1}$ we can computably decide whether each $\mathbb{P}$ in our search satisfies (92) until we find one. First note that the finite set $\operatorname{Support}(T_n)$ can be computed by searching the expression specifying $T_n$ for all the sentences $\phi$ that occur within it. Moreover, equation (92) need only be be checked for worlds $\mathbb{W}'\in\mathcal{W}'$, since any other $\mathbb{W}$ returns the same value as its corresponding $\mathbb{W}'$. Now, for any fixed world $\mathbb{W}'\in\mathcal{W}'$ and candidate $\mathbb{P}$, we can compute each value in the language of expressible features 

$$
\mathbb{W}'(T_n(\mathbb{P}_{\le n-1},\mathbb{P})) = T_n(\mathbb{P}_{\le n-1},\mathbb{P})[1] + \sum_{\phi\in\mathcal{S}'} \mathbb{W}'(\phi)\cdot T_n(\mathbb{P}_{\le n-1},\mathbb{P})[\phi]
$$

 directly by evaluating the expressible features $T_n[\phi]$ on the given belief history $(\mathbb{P}_{\le n-1},\mathbb{P})$, as $\phi\in\mathcal{S}'$ varies. Since $\mathcal{W}'$ is a finite set, we can do this for all $\mathbb{W}'$ with a finite computation. Thus, checking whether a belief state $\mathbb{P}$ satisfies condition (92) is computably decidable, and a solution to (92) can therefore be found by enumerating all belief states $\mathbb{P}$ and searching through them for the first one that works. ◻

**Lemma 93** ($\textnormal{{\texttt{MarketMaker}}}$ Inexploitability). _Let ${\overline{T}}$ be any trader. The sequence of belief states ${\overline{\mathbb{P}}}$ defined recursively by 

$$
\begin{align*}
    \mathbb{P}_n&:=\textnormal{{\texttt{MarketMaker}}}_n(T_n,\mathbb{P}_{\le n-1}),
\end{align*}
$$

 with base case $\mathbb{P}_1 = \textnormal{{\texttt{MarketMaker}}}(T_1,())$, is not exploited by ${\overline{T}}$ relative to any deductive process ${\overline{D}}$._

_Proof._ By the definition of $\textnormal{{\texttt{MarketMaker}}}$, we have that for every $n$, the belief state $\mathbb{P}=\mathbb{P}_n$ satisfies equation (92), i.e., 

$$
\textnormal{for all worlds \(\mathbb{W}\in \mathcal{W}\) and all \(n\in {\mathbb{N}}^+\):}\quad\mathbb{W}(T_n({\overline{\mathbb{P}}})) \leq 2^{-n}.
$$

 Hence by linearity of $\mathbb{W}$, for all $n\in{\mathbb{N}}^+$ we have: 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq n}} T_i({\overline{\mathbb{P}}})\right)
    = \sum_{i \leq n}\mathbb{W}(T_i({\overline{\mathbb{P}}}))
    \leq \sum_{i \leq n} 2^{-i} < 1.
$$

 Therefore, given any deductive process ${\overline{D}}$, 

$$
\sup \left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n}} T_i({\overline{\mathbb{P}}})\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \right\} \leq 1 <\infty,
$$

 so ${\overline{T}}$ does not exploit ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$. ◻

### Constructing $\textnormal{{\texttt{Budgeter}}}$ ^constructing-2

Here we introduce a subroutine for turning a trader with potentially infinite losses into a trader that will never have less than $-\text{\textdollar}b$ in any world $\mathbb{W}\in\mathcal{PC}(D_n)$ on any day $n$, for some bound $b$, in such a way that does not affect the trader if it wouldn’t have fallen below $-\text{\textdollar}b$ to begin with.

**Definition/Proposition 94** ($\textnormal{{\texttt{Budgeter}}}$). _Given any deductive process ${\overline{D}}$, there exists a computable function, henceforth called $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}$, satisfying the following definition. Given inputs $n$ and $b\in{\mathbb{N}}^+$, an $n$\-strategy history $T_{\leq n}$, and an $(n-1)$\-belief history $\mathbb{P}_{\le n-1}$, $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}$ returns an $n$\-strategy $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,T_{\leq n},\mathbb{P}_{\le n-1})$, such that 

$$
\begin{align*}
      \textnormal{if:\quad}&
      \mathbb{W}\left({\textstyle \sum_{i \leq m} T_{i}(\mathbb{P}_{\leq i})}\right)
      \le -b\textnormal{~for some \(m<n\) and \(\mathbb{W}\in \mathcal{PC}(D_m)\),}\\
      \textnormal{then:\quad}&
      \textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,T_{\leq n},\mathbb{P}_{\le n-1}) = 0,\\
      \textnormal{else:\quad}&
      \textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,T_{\leq n},\mathbb{P}_{\le n-1}) =
\end{align*}
$$

$$
        T_n\cdot\inf_{\mathbb{W}\in \mathcal{PC}(D_n)}
        \left[
          \max\left(1, \frac{-\mathbb{W}(T_n)}
                             {b+\mathbb{W}\left({\sum_{i \leq n-1} T_{i}(\mathbb{P}_{\leq i})}\right)}
          \right)
        \right]^{-1}. \tag{94}
$$

_

_Proof._ Let $\mathcal{S}'=\bigcup_{i\le n}\operatorname{Support}(T_i)$, $\mathcal{W}' = \{\mathbb{W}\mid \operatorname{Support}(\mathbb{W})\subseteq \mathcal{S}'\}$, and for any world $\mathbb{W}$, write 

$$
\mathbb{W}'(\phi) :=
  \begin{cases}
    \mathbb{W}(\phi) &\text{if \(\phi\in\mathcal{S}'\),}\\
    0 &\text{otherwise.}
  \end{cases}
$$

Now, observe that we can computably check the “if” statement in the function definition. This is because $\mathbb{W}({\textstyle \sum_{i \leq m} T_{i}(\mathbb{P}_{\leq i})})$ depends only on $\mathbb{W}' \in\mathcal{W}'$, a finite set. We can check whether $\mathbb{W}'\in\mathcal{PC}(D_m)$ in finite time by checking whether any assignment of truth values to the finite set of prime sentences occurring in sentences of $D_n$ yields the assignment $\mathbb{W}'$ on $\operatorname{Support}(\mathbb{W}')$. The set of sentences $D_n$ is computable given $n$, because ${\overline{D}}$ is computable by definition.

It remains to show that the “else” expression can be computed and returns an $n$\-trading strategy. First, the infimum can be computed over $\mathbb{W}' \in \mathcal{W}' \cap \mathcal{PC}(D_n)$, a finite set, since the values in the $\inf$ depend only on $\mathbb{W}'$, and the $\inf$ operator itself can be re-expressed in the language of expressible features using $\max$ and multiplication by $(-1)$. The values $\mathbb{W}'(T_n)$ and $\mathbb{W}'(\sum_{i \leq n-1} T_{i}(\mathbb{P}_{\leq i}))$ are finite sums, and the denominator ${b+\mathbb{W}({\textstyle \sum_{i \leq n-1} T_{i}(\mathbb{P}_{\leq i})} )}$ is a fixed positive rational (so we can safely multiply by its reciprocal). The remaining operations are all single-step evaluations in the language of expressible valuation features, completing the proof. ◻

Let us reflect on the meaning of these operations. The quantity $b + \mathbb{W}(\sum_{i<n}T_i(\mathbb{P}_{\leq i}) )$ is the amount of money the trader has available on day $n$ according to $\mathbb{W}$ (assuming they started with a budget of $b$), and $-\mathbb{W}(T_n)$ is the amount they’re going to lose on day $n$ according to $\mathbb{W}$ as a function of the upcoming prices, and so the infimum above is the trader’s trade on day $n$ scaled down such that they can’t overspend their budget according to any world propositionally consistent with $D_n$.

**Lemma 95** (Properties of $\textnormal{{\texttt{Budgeter}}}$). _Let ${\overline{T}}$ be any trader, and ${\overline{\mathbb{P}}}$ be any sequence of belief states. Given $n$ and $b$, let $B^b_n$ denote $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,T_{\leq n},\mathbb{P}_{\le n-1})$. Then:_

1.  _for all $b,n\in{\mathbb{N}}^+$, if for all $m\le n$ and $\mathbb{W}\in \mathcal{PC}(D_m)$ we have $\mathbb{W}\left(\sum_{i\leq m}T_i({\overline{\mathbb{P}}})\right)>-b$, then 
    
    $$
    B_n^b({\overline{\mathbb{P}}})=T_n({\overline{\mathbb{P}}})\textnormal{;}
    $$
    
    _
    
2.  _for all $b,n\in{\mathbb{N}}^+$ and all $\mathbb{W}\in\mathcal{PC}(D_n)$, we have 
    
    $$
    \mathbb{W}\left(\textstyle\sum_{i\leq n}B_i^b({\overline{\mathbb{P}}})\right)\geq -b\textnormal{;}
    $$
    
    _
    
3.  _If ${\overline{T}}$ exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$, then so does ${\overline{B}}^b$ for some $b\in{\mathbb{N}}^+$._
    

**Part 1.**

_Proof._ Suppose that for some time step $n$, for all $m\leq n$ and all worlds $\mathbb{W}\in\mathcal{PC}(D_m)$ plausible at time $m$ we have 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq m}
    T_{i}({\overline{\mathbb{P}}})} \right)> -b,
$$

 so by linearity of $\mathbb{W}(-)$, we have in particular that 

$$
b+ \mathbb{W}\left({\textstyle \sum_{i \leq n-1 }
    T_{i}({\overline{\mathbb{P}}})} \right)
    > -\mathbb{W}\left({\textstyle
    T_{n}({\overline{\mathbb{P}}})} \right).
$$

 Since $n-1\le n$, the LHS is positive, so we have 

$$
1> \frac{-\mathbb{W}\left({\textstyle T_{n}({\overline{\mathbb{P}}})}\right)}
            {b+ \mathbb{W}\left({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})}\right)}.
$$

 Therefore, by the definition of $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}$ (and $T_i({\overline{\mathbb{P}}}) = T_i(\mathbb{P}_{\le i})$), since the “if” clause doesn’t trigger by the assumption on the $\mathbb{W}\left({\textstyle \sum_{i \leq m} T_{i}({\overline{\mathbb{P}}})} \right)$ for $m<n$, 

$$
\begin{align*}
    B_n^b({\overline{\mathbb{P}}}) &\equiv
      T_n({\overline{\mathbb{P}}})
      \cdot
      \inf_{\mathbb{W}\in\mathcal{PC}(D_n)}
      \left.
      1 \middle/ \max\left(1,
        \frac{-\mathbb{W}(T_n({\overline{\mathbb{P}}}))}
             {b+\mathbb{W}\left({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})}\right)}
      \right)
      \right.\\
    &= T_n(\mathbb{P}_{\leq n}) \cdot \inf_{\mathbb{W}\in\mathcal{PC}(D_n)} 1/1 \\
    &= T_n({\overline{\mathbb{P}}})
\end{align*}
$$

 as needed. ◻

**Part 2.**

_Proof._ Suppose for a contradiction that for some $n$ and some $\mathbb{W}\in\mathcal{PC}(D_n)$, 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq n} B^b_{i}({\overline{\mathbb{P}}})} \right) < -b.
$$

 Assume that $n$ is the least such day, and fix some such $\mathbb{W}\in\mathcal{PC}(D_n)$. By the minimality of $n$ it must be that $\mathbb{W}(B^b_n({\overline{\mathbb{P}}}))< 0$, or else we would have $\mathbb{W}\left({\textstyle \sum_{i \leq n-1} B^b_{i}({\overline{\mathbb{P}}})}\right) < -b$. Since $B^b_n({\overline{\mathbb{P}}})$ is a non-negative multiple of $T_n({\overline{\mathbb{P}}})$, we also have $\mathbb{W}(T_n({\overline{\mathbb{P}}}))< 0$. However, since $B^b_{n}\not\equiv 0$, from the definition of $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}$ we have 

$$
\begin{align*}
    \mathbb{W}\left({\textstyle B^b_{n}} \right)
    &=
      \mathbb{W}\left({T_n({\overline{\mathbb{P}}})}\right)
      \cdot
      \left(
        \left.
        \inf_{\mathbb{W}'\in\mathcal{PC}(D_n)}
        1 \middle/ \max\left(1, \frac{-\mathbb{W}'(T_n({\overline{\mathbb{P}}}))}
                                     {b+\mathbb{W}'({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})})}
        \right)
        \right.
      \right) \\
    &\geq
      \mathbb{W}\left({T_n({\overline{\mathbb{P}}})}\right)
      \cdot
      \left.
      1 \middle/ \max\left(1, \frac{-\mathbb{W}(T_n({\overline{\mathbb{P}}}))}
                                   {b+\mathbb{W}({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})})}
      \right)
      \right.
      \textnormal{\ (since  \(\mathbb{W}\left({T_n({\overline{\mathbb{P}}})}\right) <0\))}  \\
    &\geq
      \mathbb{W}\left({T_n({\overline{\mathbb{P}}})}\right)
      \cdot
      \frac{b+\mathbb{W}({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})})}
           {-\mathbb{W}(T_n({\overline{\mathbb{P}}}))}
\end{align*}
$$

since $-\mathbb{W}\left({T_n({\overline{\mathbb{P}}})}\right) >0$ and $B^b_{n}\not\equiv 0$ implies $b+\mathbb{W}({\textstyle \sum_{i \leq n-1} T_{i}({\overline{\mathbb{P}}})})>0$. Hence, this

$$
\begin{align*}
    &=
      -b-\mathbb{W}\left({\textstyle \sum_{i \le n} T_{i}({\overline{\mathbb{P}}})} \right).
\end{align*}
$$

Further, since $B^b_{n}\not\equiv 0$, we have 

$$
\begin{align*}
  \textnormal{for all\ } j \le n-1\colon\quad&
  \mathbb{W}\left({\textstyle \sum_{i \le j}T_{i}({\overline{\mathbb{P}}})}\right) > -b,
  \textnormal{\ which by Part 1 implies that}\\
  \textnormal{for all\ } j \le n-1 \colon\quad&
  B^b_j({\overline{\mathbb{P}}}) = T_j({\overline{\mathbb{P}}}), \textnormal{ therefore}\\
  &\mathbb{W}(B^b_n)\geq  -b-\mathbb{W}\left({\textstyle \sum_{i \le n-1} B^b_{i}({\overline{\mathbb{P}}})} \right),\textnormal{ hence}\\
  &\mathbb{W}\left({\textstyle \sum_{i \le n} B^b_{i}({\overline{\mathbb{P}}})}\right) \geq -b.\end{align*}
$$

 ◻

**Part 3.**

_Proof._ By definition of exploitation, the set 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \le n} T_i({\overline{\mathbb{P}}})}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \right\}
$$

 is unbounded above, and is strictly bounded below by some integer $b$. Then by Part 1, for all $n$ we have $T_n({\overline{\mathbb{P}}}) = B^b_n({\overline{\mathbb{P}}})$. Thus, 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \le n} B^b_i({\overline{\mathbb{P}}})}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \right\}
$$

 is unbounded above and bounded below, i.e., ${\overline{B}}^b$ exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$. ◻

### Constructing $\textnormal{{\texttt{TradingFirm}}}$ ^constructing-3

Next we define $\textnormal{{\texttt{TradingFirm}}}$, which combines an (enumerable) infinite sequence of e.c. traders into a single “supertrader” that exploits a given belief sequence ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$ if any e.c. trader does. It does this by taking each e.c. trader, budgeting it, and scaling its trades down so that traders later in the sequence carry less weight to begin with.

To begin, we will need a computable sequence that includes every e.c. trader at least once. The following trick is standard, but we include it here for completeness:

**Proposition 96** (Redundant Enumeration of e.c. Traders). _There exists a computable sequence $\smash{({\overline{T}}^k)_{k\in{\mathbb{N}}^+}}$ of e.c. traders such that every e.c. trader occurs at least once in the sequence._

_Proof._ Fix a computable enumeration of all ordered pairs $(M_k,f_k)$ where $M_k$ is a Turing machine and $f_k$ is a polynomial with coefficients in ${\mathbb{Z}}$. We define a computable function 

$$
\operatorname{ECT}: \{\textnormal{Turing machines}\} \times \{\textnormal{Integer polynomials}\} \times (n \in {\mathbb{N}}^+) \to \{\textnormal{\(n\)-strategies}\}
$$

 that runs as follows: $\operatorname{ECT}(M,f,n)$ first runs $M(n)$ for up to $f(n)$ time steps, and if in that time $M(n)$ halts and returns a valid $n$\-strategy $T_n$, then $\operatorname{ECT}(M,f,n)$ returns that strategy, otherwise it returns 0 (as an $n$\-strategy). Observe that $\operatorname{ECT}(M_k,f_k,-)$ is always an e.c. trader, and that every e.c. trader occurs as $\operatorname{ECT}(M_k,f_k,-)$ for some $k$. ◻

**Definition/Proposition 97** ($\textnormal{{\texttt{TradingFirm}}}$). _Given any deductive process ${\overline{D}}$, there exists a computable function, henceforth called $\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}$, satisfying the following definition. By Proposition 96, we fix a computable enumeration ${\overline{T}}^k$ including every e.c. trader at least once, and let 

$$
S^k_n=\begin{cases}T^k_n&\text{if }n\geq k\\0&\text{otherwise}.\end{cases}
$$

 Given input $n\in{\mathbb{N}}^+$ and an $(n-1)$\-belief history $\mathbb{P}_{\leq{n-1}}$, $\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}$ returns an $n$\-strategy given by 

$$
\begin{equation}
\tag{97}
    \textnormal{{\texttt{TradingFirm}}}^{\overline{D}}_n(\mathbb{P}_{\leq n-1}) = \sum_{k\in  {\mathbb{N}}^+}\sum_{b\in{\mathbb{N}}^+}2^{-k-b}\cdot \textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,S^k_{\leq n} ,\mathbb{P}_{\le n-1}).
\end{equation}
$$

_

_Proof._ We need only show that the infinite sum in equation (97) is equivalent to a computable finite sum. Writing 

$$
B^{b,k}_n= \textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,S^k_{\leq n} ,\mathbb{P}_{\le n-1}),
$$

 (an $n$\-strategy), the sum on the RHS of (97) is equivalent to 

$$
\sum_{k\in{\mathbb{N}}^+}\sum_{b\in{\mathbb{N}}^+} 2^{-k-b}\cdot B^{b,k}_n.
$$

 Since $S^k_n= 0$ for $k>n$, we also have $B^{b,k}_n=0$ for $k>n$, so the sum is equivalent to 

$$
=\sum_{k\leq n}\sum_{b\in{\mathbb{N}}^+} 2^{-k-b}\cdot B^{b,k}_n.
$$

Now, assume $C_n$ is a positive integer such that $\sum_{i \leq n}\|S^k_i({\overline{\mathbb{V}}})\|_1<C_n$ for all $k \leq  n$ and any valuation sequence ${\overline{\mathbb{V}}}$ (we will show below that such a $C_n$ can be computed from $\mathbb{P}_{\le n-1}$). Since the valuations $\mathbb{W}$ and ${\overline{\mathbb{P}}}$ are always $[0,1]$\-valued, for any $m \leq n$ the values $\mathbb{W}\left(\sum_{i\leq m}S^k_i(\mathbb{P}_{\leq m})\right)$ are bounded below by $-\sum_{i \leq m}\|S^k_i(\mathbb{P}_{\leq m})\|_1>-C_n$. By property 1 of $\textnormal{{\texttt{Budgeter}}}^{\overline{D}}$ (Lemma 95.1), $B^{b,k}_n= S^k_n$ when $b > C_n$, so the sum is equivalent to 

$$
\begin{align*}
  =& \left(\sum_{k\leq n}\sum_{b \leq C_n}2^{-k-b}\cdot B^{b,k}_n\right)+\left(\sum_{k\leq n}\sum_{b> C_n}2^{-k-b}\cdot S^k_n\right)\\
  =& \left(\sum_{k\leq n}\sum_{b \leq C_n}2^{-k-b}\cdot B^{b,k}_n\right)+\left(\sum_{k\leq n}2^{-k-C_n}\cdot S^k_n\right)
\end{align*}
$$

 which is a finite sum of trading strategies, and hence is itself a trading strategy. Since the $B^{b,k}_n$ and the $S^k_n$ are computable from $\mathbb{P}_{\le n-1}$, this finite sum is computable.

It remains to justify our assumption that integers $C_n$ can be computed from $\mathbb{P}_{\le n-1}$ with $C_n>\sum_{i \leq n}\|S^k_i({\overline{\mathbb{V}}})\|_1$ for all $k \leq n$ and ${\overline{\mathbb{V}}}$. To see this, first consider how to bound a single expressible feature $\xi$. We can show by induction on the structure of $\xi$ (see [[#^expressible-features|8.2]]) that, given constant bounds on the absolute value $|\zeta({\overline{\mathbb{V}}})|$ of each subexpression $\zeta$ of $\xi$, we can compute a constant bound on $|\xi({\overline{\mathbb{V}}})|$; for example, the bound on $\zeta \cdot \eta$ is the product of the bound on $\zeta$ and the bound on $\eta$. Thus, given a single trading strategy $S^k_i$ and any $\phi$, we can compute a constant upper bound on $|S^k_i[\phi]({\overline{\mathbb{V}}})|$ for all ${\overline{\mathbb{V}}}$. Since $\|S^k_i({\overline{\mathbb{V}}})\|_1 \leq \sum_{\phi \in \operatorname{Support}(S^k_i)} 2 |S^k_i[\phi]({\overline{\mathbb{V}}})|$ and $\operatorname{Support}(S^k_i)$ is computable, we can bound each $\|S^k_i({\overline{\mathbb{V}}})\|_1$, and hence also $\sum_{i \leq n}\|S^k_i({\overline{\mathbb{V}}})\|_1$, as needed. ◻

**Lemma 98** (Trading Firm Dominance). _Let ${\overline{\mathbb{P}}}$ be any sequence of belief states, and ${\overline{D}}$ be a deductive process. If there exists any e.c. trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$, then the sequence 

$$
\left(\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}_n(\mathbb{P}_{\leq n-1})\right)_{n\in{\mathbb{N}}^+}
$$

 also exploits ${\overline{\mathbb{P}}}$ (relative to ${\overline{D}}$)._

_Proof._ Suppose that some e.c. trader exploits ${\overline{\mathbb{P}}}$. That trader occurs as ${\overline{T}}^k$ for some $k$ in the enumeration used by $\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}$. First, we show that ${\overline{S}}^k$ (from the definition of $\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}$) also exploits ${\overline{\mathbb{P}}}$. It suffices to show that there exist constants $c_1\in{\mathbb{R}}^+$ and $c_2\in{\mathbb{R}}$ such that for all $n\in{\mathbb{N}}^+$ and $\mathbb{W}\in\mathcal{PC}(D_n)$, 

$$
\mathbb{W}\left(\textstyle\sum_{i\leq n}S^k_i({\overline{\mathbb{P}}})\right)\geq c_1\cdot \mathbb{W}\left(\textstyle\sum_{i\leq n}T^k_i({\overline{\mathbb{P}}})\right)+c_2.
$$

 Taking $c_1=1$ and $c_2=-\sum_{i<k}\|T^k_i({\overline{\mathbb{P}}})\|_1$, where $\|\cdot\|_1$ denotes the $\ell_1$ norm on ${\mathbb{R}}$\-combinations of sentences, we have 

$$
\mathbb{W}\left(\textstyle\sum_{i\leq n}S^k_i({\overline{\mathbb{P}}})\right)\geq 1\cdot \mathbb{W}\left(\textstyle\sum_{i\leq n}T^k_i({\overline{\mathbb{P}}})\right)- \left(\textstyle\sum_{i<k}\|T^k_i({\overline{\mathbb{P}}})\|_1\right),
$$

 so ${\overline{S}}^k$ exploits ${\overline{\mathbb{P}}}$. By Lemma 95.3, we thus have that for some $b\in{\mathbb{N}}^+$, the trader ${\overline{B}}^{b,k}$ given by 

$$
B^{b,k}_n:= \textnormal{{\texttt{Budgeter}}}^{\overline{D}}_n(b,S^k_{\leq n},\mathbb{P}_{\le n-1})
$$

 also exploits ${\overline{\mathbb{P}}}$.

Next, we show that the trader ${\overline{F}}$ given by 

$$
F_n:= \textnormal{{\texttt{TradingFirm}}}^{\overline{D}}_n(\mathbb{P}_{\le n-1})
$$

 exploits ${\overline{\mathbb{P}}}$. Again, it suffices to show that there exist constants $c_1\in{\mathbb{R}}^+$ and $c_2\in{\mathbb{R}}$ such that for all $n\in{\mathbb{N}}^+$ and $\mathbb{W}\in\mathcal{PC}(D_n)$, 

$$
\mathbb{W}\left(\sum_{i\leq n}F_i\right)\geq c_1\cdot \mathbb{W}\left(\sum_{i\leq n}B^{b,k}_i\right)+c_2.
$$

 It will suffice to take $c_1=2^{-k-b}$ and $c_2=-2$, because we have 

$$
\begin{align*}
    &\mathbb{W}\left(\sum_{i\leq n}F_i\right)-2^{-k-b}\cdot \mathbb{W}\left(\sum_{i\leq n}B^{b,k}_i\right)\\
    =&\sum_{(k^\prime,b^\prime)\neq(k,b)}2^{-k^\prime-b^\prime}\cdot \mathbb{W}\left(\sum_{i\leq n}B^{b^\prime,k^\prime}_i\right)\\
    \geq& \sum_{(k^\prime,b^\prime)\neq(k,b)}2^{-k^\prime-b^\prime}\cdot (-b^\prime)\geq -2
\end{align*}
$$

 by Lemma 95.2, hence 

$$
\mathbb{W}\left(\sum_{i\leq n}F_i\right)\geq 2^{-k-b}\cdot \mathbb{W}\left(\sum_{i\leq n}B^{b,k}_i\right) -2.
$$

 Thus, ${\overline{F}}$ exploits ${\overline{\mathbb{P}}}$. ◻

### Constructing ${\overline{\textnormal{{\texttt{LIA}}}}}$ ^constructing-overline-textnormal-texttt

We are finally ready to build $\textnormal{{\texttt{LIA}}}$. With the subroutines above, the idea is now fairly simple: we pit $\textnormal{{\texttt{MarketMaker}}}$ and $\textnormal{{\texttt{TradingFirm}}}$ against each other in a recursion, and $\textnormal{{\texttt{MarketMaker}}}$ wins. Imagine that on each day, $\textnormal{{\texttt{TradingFirm}}}$ outputs an ever-larger mixture of traders, then $\textnormal{{\texttt{MarketMaker}}}$ carefully examines that mixture and outputs a belief state on which that mixture makes at most a tiny amount of money on net.

**Definition/Algorithm 99** (A Logical Induction Algorithm). _Given a deductive process ${\overline{D}}$, define the computable belief sequence ${\overline{\textnormal{{\texttt{LIA}}}}}=(\textnormal{{\texttt{LIA}}}_1, \textnormal{{\texttt{LIA}}}_2, \ldots)$ recursively by 

$$
\textnormal{{\texttt{LIA}}}_n:= \textnormal{{\texttt{MarketMaker}}}_n(\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}_n(\textnormal{{\texttt{LIA}}}_{\le n-1}), \textnormal{{\texttt{LIA}}}_{\le n-1}),
$$

 beginning from the base case $\textnormal{{\texttt{LIA}}}_{\leq 0}:=()$._

**Theorem 100** ($\textnormal{{\texttt{LIA}}}$ is a Logical Inductor). _${\overline{\textnormal{{\texttt{LIA}}}}}$ satisfies the logical induction criterion relative to ${\overline{D}}$, i.e., LIA is not exploitable by any e.c. trader relative to the deductive process ${\overline{D}}$._

_Proof._ By Lemma 98, if any e.c. trader exploits ${\overline{\textnormal{{\texttt{LIA}}}}}$ (relative to ${\overline{D}}$), then so does the trader ${\overline{F}}:= (\textnormal{{\texttt{TradingFirm}}}^{\overline{D}}_n(\textnormal{{\texttt{LIA}}}_{\le n-1}))_{n\in{\mathbb{N}}^+}$. By Lemma 93, ${\overline{F}}$ does not exploit ${\overline{\textnormal{{\texttt{LIA}}}}}$. Therefore no e.c. trader exploits ${\overline{\textnormal{{\texttt{LIA}}}}}$. ◻

### Questions of Runtime and Convergence Rates ^questions-of-runtime-and

In this paper, we have optimized our definitions for the theoretical clarity of results rather than for the efficiency of our algorithms. This leaves open many interesting questions about the relationship between runtime and convergence rates of logical inductors that have not been addressed here. Indeed, the runtime of $\textnormal{{\texttt{LIA}}}$ is underspecified because it depends heavily on the particular enumerations of traders and rational numbers used in the definitions of $\textnormal{{\texttt{MarketMaker}}}$ and $\textnormal{{\texttt{TradingFirm}}}$.

For logical inductors in general, there will be some tradeoff between the runtime of $\mathbb{P}_n$ as a function of $n$ and how quickly the values $\mathbb{P}_n(\phi)$ converge to $\mathbb{P}_\infty(\phi)$ as $n$ grows. Quantifying this tradeoff may be a fruitful source of interesting open problems. Note, however, the following important constraint on the convergence rate of any logical inductor, regardless of its implementation, which arises from the halting problem:

**Proposition 101** (Uncomputable Convergence Rates). _Let ${\overline{\mathbb{P}}}$ be a logical inductor over a theory $\Gamma$ that can represent computable functions, and suppose $f:\mathcal{S}\times{\mathbb{Q}}^+\to{\mathbb{N}}$ is a function such that for every sentence $\phi$, if $\Gamma\vdash\phi$ then $\mathbb{P}_n(\phi) > 1-\varepsilon$ for all $n>f(\phi,\varepsilon)$. Then $f$ must be uncomputable._

_Proof._ Suppose for contradiction that such a computable $f$ were given. We will show that $f$ could be used to computably determine whether $\Gamma\vdash\phi$ for an arbitrary sentence $\phi$, a task which is known to be impossible for a first-order theory that can represent computable functions. (If we assumed further that $\Gamma$ were sound as a theory of the natural numbers, this would allow us to solve the halting problem by letting $\phi$ be a sentence of the form “$M$ halts”.)

Given a sentence $\phi$, we run two searches in parallel. If we find that $\Gamma\vdash \phi$, then we return True. If we find that for some $b,n\in{\mathbb{N}}^+$ we have 

$$
\begin{equation}
\tag{101}
    n>f\left(\phi,\frac{1}{b}\right) \textnormal{~and~} \mathbb{P}_n(\phi)\leq 1-\frac{1}{b},
\end{equation}
$$

 then we return False. Both of these conditions are computably enumerable since $f$, $\mathbb{P}_n$, and verifying witnesses to $\Gamma\vdash \phi$ are computable functions.

Suppose first that $\Gamma\vdash \phi$. Then by definition of $f$ we have $\mathbb{P}_n(\phi)>1-\frac{1}{b}$ for all $n>f\left(\phi,\frac{1}{b}\right)$, and hence we find a witness for $\Gamma\vdash \phi$ and return True. Now suppose that $\Gamma\nvdash \phi$. Then by Theorem 165 (Non-Dogmatism) we have that $\mathbb{P}_\infty(\phi)<1-\varepsilon$ for some $\varepsilon>0$, and hence for some $b$ and all sufficiently large $n$ we have $\mathbb{P}_n(\phi)<1-1/b$. Therefore (101) holds and we return False. Thus our search always halts and returns a Boolean value that correctly indicates whether $\Gamma\vdash \phi$. ◻

## Selected Proofs ^selected-proofs

In this section, we exhibit a few selected stand-alone proofs of certain key theorems. These theorems hold for any ${\overline{\mathbb{P}}}$ satisfying the logical induction criterion, which we recall here:

**Definition 102** (The Logical Induction Criterion). _A market ${\overline{\mathbb{P}}}$ is said to satisfy the **logical induction criterion** relative to a deductive process ${\overline{D}}$ if there is no efficiently computable trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$ relative to ${\overline{D}}$. A market ${\overline{\mathbb{P}}}$ meeting this criterion is called a **logical inductor over $\boldsymbol{{\overline{D}}}$**._

Only our notation (Section [[#^notation|2]]), framework (Section [[#^the-logical-induction-criterion|3]]), and continuous threshold indicator (Definition 25) are needed to understand the results and proofs in this section. Shorter proofs of these theorems can be found in the appendix, but those rely on significantly more machinery.

### Convergence ^convergence

Recall Theorem 118 and the proof sketch given:

**Theorem 103** (Convergence). _The limit ${\mathbb{P}_\infty:\mathcal{S}\rightarrow[0,1]}$ defined by 

$$
\mathbb{P}_\infty(\phi) := \lim_{n\rightarrow\infty} \mathbb{P}_n(\phi)
$$

 exists for all $\phi$._

_Proof sketch._

> Roughly speaking, if ${\overline{\mathbb{P}}}$ never makes up its mind about $\phi$, then it can be exploited by a trader arbitraging shares of $\phi$ across different days. More precisely, suppose by way of contradiction that the limit $\mathbb{P}_\infty(\phi)$ does not exist. Then for some $p\in [0, 1]$ and $\varepsilon > 0$, we have $\mathbb{P}_n(\phi) < p-\varepsilon$ infinitely often and also $\mathbb{P}_n(\phi) > p+\varepsilon$ infinitely often. A trader can wait until $\mathbb{P}_n(\phi) < p-\varepsilon$ and then buy a share in $\phi$ at the low market price of $\mathbb{P}_n(\phi)$. Then the trader waits until some later $m$ such that $\mathbb{P}_m(\phi) > p+\varepsilon$, and sells back the share in $\phi$ at the higher price. This trader makes a total profit of $2\varepsilon$ every time $\mathbb{P}_n(\phi)$ oscillates in this way, at no risk, and therefore exploits ${\overline{\mathbb{P}}}$. Since ${\overline{\mathbb{P}}}$ implements a logical inductor, this is not possible; therefore the limit $\mathbb{P}_\infty(\phi)$ must in fact exist.

We will define a trader ${\overline{T}}$ that executes a strategy similar to this one, and hence exploits the market ${\overline{\mathbb{P}}}$ if $\lim_{n\to\infty} \mathbb{P}_n(\phi)$ diverges. To do this, there are two technicalities we must deal with. First, the strategy outlined above uses a discontinuous function of the market prices $\mathbb{P}_n(\phi)$, and therefore is not permitted. This is relatively easy to fix using the continuous indicator functions of Definition 25.

The second technicality is more subtle. Suppose we define our trader to buy $\phi$\-shares whenever their price $\mathbb{P}_n(\phi)$ is low, and sell them back whenever their price is high. Then it is possible that the trader makes the following trades in sequence against the market ${\overline{\mathbb{P}}}$: buy 10 $\phi$\-shares on consecutive days, then sell 10 $\phi$\-shares; then buy 100 $\phi$\-shares consecutively, and then sell them off; then buy 1000 $\phi$\-shares, then sell them off; and so on. Although this trader makes profit on each batch, it always spends more on the next batch, taking larger and larger risks (relative to the remaining plausible worlds). Then the plausible value of this trader’s holdings will be unbounded below, and so it does not exploit ${\overline{\mathbb{P}}}$. In short, this trader is not tracking its budget, and so may have unboundedly negative plausible net worth. We will fix this problem by having our trader ${\overline{T}}$ track how many net $\phi$\-shares it has bought, and not buying too many, thereby maintaining bounded risk. This will be sufficient to prove the theorem.

_Proof of Theorem 118._ Suppose by way of contradiction that the limit $\mathbb{P}_\infty$ does not exist. Then, for some sentence $\phi$ and some rational numbers $p\in [0, 1]$ and $\varepsilon > 0$, we have that $\mathbb{P}_n(\phi) < p-\varepsilon$ infinitely often and $\mathbb{P}_n(\phi) > p+\varepsilon$ infinitely often. We will show that ${\overline{\mathbb{P}}}$ can be exploited by a trader ${\overline{T}}$ who buys below and sells above these prices infinitely often, contrary to the logical induction criterion.

**Definition of the trader ${\overline{T}}$.** We will define ${\overline{T}}$ recursively along with another sequence of $\mathcal{E\!F}$\-combinations ${\overline{H}}$ (mnemonic: “holdings”) which tracks the sum of the trader’s previous trades. Our base cases are 

$$
T_1 := \overline{0}
$$

 

$$
H_1:=\overline{0} .
$$

 For $n>1$, we define a recurrence whereby ${\overline{T}}$ will buy some $\phi$\-shares whenever ${\phi}^{*n} < p-\varepsilon/2$, up to $(1-H_{n-1}[\phi])$ shares when ${\phi}^{*n} < p-\varepsilon$, and sells some $\phi$\-shares whenever ${\phi}^{*n} > p+\varepsilon/2$, up to $H_{n-1}$ shares when ${\phi}^{*n} > p+\varepsilon$: 

$$
\begin{equation}
    \begin{aligned}
      T_n[\phi] &:= (1-H_{n-1}[\phi]) \cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}( {\phi}^{*n}< p-\varepsilon/2)\\
      &\hphantom{\; := (1)  } - H_{n-1}[\phi] \cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}( {\phi}^{*n}> p+\varepsilon/2),\\
      T_n&:= T_n[\phi] \cdot(\phi - {\phi}^{*n})\\
      H_n&:= H_{n-1} + T_n.
    \end{aligned}
\tag{103}
\end{equation}
$$

 The trade coefficients $T[\phi]$ are chosen so that the number of $\phi$\-shares $H_n[\phi]$ that it owns is always in $[0,1]$ (it never buys more than $1-H_{n-1}[\phi]$ and never sells more than $H_{n-1}[\phi]$). Observe that each $T_n$ is a valid trading strategy for day $n$ (see Definition 12) because it is of the form $\xi\cdot(\phi-{\phi}^{*n})$.

To complete the definition, we must argue that ${\overline{T}}$ is efficiently computable. For this, observe that the $3n+2$ definition ($:=$) equations defining $T_1,\ldots,T_n$ above can be written down in time polynomial in $n$. Thus, a combination of feature expressions defining $T_n$ from scratch can be written down in $\operatorname{poly}(n)$ time (indeed, the expression is just a concatenation of $n$ copies of the three “$:=$” equations written above, along with the base cases), so ${\overline{T}}$ is efficiently computable.

**Proof of exploitation.** To show ${\overline{T}}$ exploits ${\overline{\mathbb{P}}}$ over ${\overline{D}}$, we must compute upper and lower bounds on the set of plausible values $\mathbb{W}(H_n({\overline{\mathbb{P}}}))$ (since $H_n= \sum_{i\leq n} T_n$) for worlds $\mathbb{W}\in\mathcal{PC}(D_n)$.

While proving exploitation, we leave the constant argument ${\overline{\mathbb{P}}}$ implicit to reduce clutter, writing, e.g., $\phi^{*i}$ for $\phi^{*i}({\overline{\mathbb{P}}}) = \mathbb{P}_i(\phi)$, $T_n[\phi]$ for $T_n[\phi]({\overline{\mathbb{P}}})$, and so on.

First, since each $T_i[1] = -T_i[\phi]\cdot{\phi}^{*i}$, the trader’s “cash” held on day $n$ is 

$$
H_n[1] = \sum_{i\le n} T_i[1] = - \sum_{i\le n} T_i[\phi]\cdot\phi^{*i}
$$

which we can regroup, to compare the prices ${\phi}^{*i}$ to $p$, as

$$
\begin{align*}
    H_n[1]&=  \sum_{i\le n} \left(T_i[\phi]\cdot(p-\phi^{*i})\right) - p \cdot \sum_{i\le n} T_i[\phi]\\
    &=  \sum_{i\le n} \left(T_i[\phi]\cdot(p-\phi^{*i})\right) - p \cdot H_n[\phi] .
\end{align*}
$$

Now, if $\phi^{*i} < p-\varepsilon/2$ then $T_i[\phi]\ge 0$, if $\phi^{*i} > p+\varepsilon/2$ then $T_i[\phi]\le 0$, and if $p-\varepsilon/2 \le \phi^{*i} \le p+\varepsilon/2$ then $T_i[\phi] = 0$, so for all $i$ the product $T_i[\phi]\cdot(p-\phi^{*i})$ is equal to or greater than $|T_i[\phi]|\cdot\varepsilon/2$:

$$
H_n[1] \ge  - p \cdot H_n[\phi] + \sum_{i \le n}|T_i[\phi]| \cdot \varepsilon/2 .
$$

Moreover, by design, $H_n[\phi] \in [0,1]$ for all $n$, so

$$
H_n[1] \ge -p +  \sum_{i \le n}|T_i[\phi]| \cdot \varepsilon/2.
$$

 Now, by assumption, ${\phi}^{*i}$ lies above and below $(p-\varepsilon,p+\varepsilon)$ infinitely often, so from equation (103), $H_i[\phi]=0$ and $H_i[\phi]=1$ infinitely often. Since the sum $\sum_{i \le n}|T_i[\phi]|$ is the total variation in the sequence $H_i[\phi]$, it must diverge (by the triangle inequality) as $n\to\infty$, so 

$$
\lim_{n\to\infty}H_n[1] = \infty .
$$

 Moreover, in any world $\mathbb{W}$, the trader’s non-cash holdings $H_n[\phi]\cdot\phi$ have value $\mathbb{W}(H_n[\phi]\cdot\phi)= H_n[\phi]\cdot\mathbb{W}(\phi)\geq 0$ (since $H_n[\phi] > 0$), so its combined holdings $H_n= H_n[1] + H_n[\phi]\cdot\phi$ have value 

$$
\mathbb{W}(H_n)= \mathbb{W}\left(H_n[1]+H_n[\phi]\cdot\phi\right) = H_n[1]+H_n[\phi]\cdot\mathbb{W}(\phi) \ge  H_n[1]
$$

 so in _every_ world $\mathbb{W}$ we have 

$$
\lim_{n\to\infty}\mathbb{W}(H_n) = \infty .
$$

 This contradicts that ${\overline{\mathbb{P}}}$ is a logical inductor; therefore, the limit $\mathbb{P}_\infty(\phi)$ must exist. ◻

### Limit Coherence ^limit-coherence

Recall Theorem 129:

**Theorem 104** (Limit Coherence). _$\mathbb{P}_\infty$ is coherent, i.e., it gives rise to an internally consistent probability measure $\mathrm{Pr}$ on the set $\mathcal{PC}(\Gamma)$ of all worlds consistent with $\Gamma$, defined by the formula 

$$
\mathrm{Pr}(\mathbb{W}(\phi)=1):=\mathbb{P}_\infty(\phi).
$$

 In particular, if $\Gamma$ contains the axioms of first-order logic, then $\mathbb{P}_\infty$ defines a probability measure on the set of first-order completions of $\Gamma$._

_Proof of Theorem 129._ By Theorem 118 (Convergence), the limit $\mathbb{P}_\infty(\phi)$ exists for all sentences $\phi\in\mathcal{S}$. Therefore, $\mathrm{Pr}(\mathbb{W}(\phi)=1): =\mathbb{P}_\infty(\phi)$ is well-defined as a function of basic subsets of the set of all consistent worlds $\mathcal{PC}(D_\infty) = \mathcal{PC}(\Gamma)$.

Gaifman (1964) shows that $\mathrm{Pr}$ extends to a probability measure over $\mathcal{PC}(\Gamma)$ so long as the following three implications hold for all sentences $\phi$ and $\psi$:

-   If $\Gamma\vdash \phi$, then $\mathbb{P}_\infty(\phi) = 1$.
    
-   If $\Gamma\vdash \lnot \phi$, then $\mathbb{P}_\infty(\phi) = 0$.
    
-   If $\Gamma\vdash \lnot(\phi \land \psi)$, then $\mathbb{P}_\infty(\phi \lor \psi) = \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi)$.
    

Since the three conditions are quite similar in form, we will prove them simultaneously using four exemplar traders and parallel arguments.

**Definition of the traders.** Suppose that one of the three conditions is violated by a margin of $\varepsilon$, i.e., one of the following four cases holds: 

$$
\begin{alignat*}
{2}    
    &(L^1)\;\;\Gamma\vdash \phi,  \textnormal{ but } && (I^1)\;\; \mathbb{P}_\infty(\phi) <  1-\varepsilon;\\
    &(L^2)\;\; \Gamma\vdash \lnot \phi, \textnormal{ but } && (I^2)\;\; \mathbb{P}_\infty(\phi) > \varepsilon;\\
    &(L^3)\;\; \Gamma\vdash \lnot(\phi \land \psi),  \textnormal{ but } && (I^3)\;\; \mathbb{P}_\infty(\phi \lor \psi) < \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi) - \varepsilon;\textnormal{ or}\\
    &(L^4)\;\; \Gamma\vdash \lnot(\phi \land \psi), \textnormal{ but \quad } &&(I^4)\;\; \mathbb{P}_\infty(\phi \lor \psi) > \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi) + \varepsilon.
\end{alignat*}
$$

 Let $i\in\{1,2,3,4\}$ be the case that holds. Since the limit $\mathbb{P}_\infty$ exists, there is some sufficiently large time $s_\varepsilon$ such that for all $n>s_\varepsilon$, the inequality $I^i$ holds with $n$ in place of $\infty$. Furthermore, since ${\overline{D}}$ is a $\Gamma$\-complete deductive process, for some sufficiently large $s_\Gamma$ and all $n> s_\Gamma$, the logical condition $L^i$ holds with $D_n$ in place of $\Gamma$. Thus, letting $s:= \max( s_\varepsilon, s_\Gamma)$, for $n > s$ one of the following cases holds: 

$$
\begin{alignat*}
{2}    
    &(L^1_n)\;\;D_n\vdash \phi,  \textnormal{ but } && (I^1_n)\;\; \mathbb{P}_n(\phi) <  1-\varepsilon;\\
    &(L^2_n)\;\; D_n\vdash \lnot \phi, \textnormal{ but } && (I^2_n)\;\; \mathbb{P}_n(\phi) > \varepsilon;\\
    &(L^3_n)\;\; D_n\vdash \lnot(\phi \land \psi),  \textnormal{ but } && (I^3_n)\;\; \mathbb{P}_n(\phi \lor \psi) < \mathbb{P}_n(\phi) + \mathbb{P}_n(\psi) - \varepsilon;\textnormal{ or}\\
    &(L^4_n)\;\; D_n\vdash \lnot(\phi \land \psi), \textnormal{ but \quad } &&(I^4_n)\;\; \mathbb{P}_n(\phi \lor \psi) > \mathbb{P}_n(\phi) + \mathbb{P}_n(\psi) + \varepsilon.
\end{alignat*}
$$

 (When interpreting these, be sure to remember that each $D_n$ is finite, and $D\vdash$ indicates using provability using only propositional calculus, i.e., modus ponens. In particular, the axioms of first order logic are not assumed to be in $D_n$.)

We now define, for each of the above four cases, a trader that will exploit the market ${\overline{\mathbb{P}}}$. For $n>s$, let 

$$
\begin{align*}
    T^1_n&:= \phi-\phi^{*n}\\
    T^2_n&:= -(\phi-\phi^{*n})\\
    T^3_n&:=  \left((\phi \lor \psi)-(\phi \lor \psi)^{*n}\right)-(\phi-\phi^{*n}) -(\psi-\psi^{*n})\\
    T^4_n&:=  (\phi-\phi^{*n})+(\psi-\psi^{*n}) -\left((\phi \lor \psi)-(\phi \lor \psi)^{*n}\right)
\end{align*}
$$

 and for $n\le s$ let $T^i_n= 0$. Each $T^i_n$ can be written down in ${\mathcal{O}}(\log(n))$ time (the constant $s$ can be hard-coded at a fixed cost), so these ${\overline{T}}^i$ are all e.c. traders.

**Proof of exploitation.** We leave the constant argument ${\overline{\mathbb{P}}}$ implicit to reduce clutter, writing, e.g., $\phi^{*i}$ for $\phi^{*i}({\overline{\mathbb{P}}}) = \mathbb{P}_i(\phi)$, $T_n[\phi]$ for $T_n[\phi]({\overline{\mathbb{P}}})$, and so on.

Consider case 1, where $L^1_n$ and $I^1_n$ hold for $n>s$, and look at the trader ${\overline{T}}^1$. For any $n>s$ and any world $\mathbb{W}\in\mathcal{PC}(D_n)$, by linearity of $\mathbb{W}$ we have 

$$
\begin{align*}
    \mathbb{W}\left({\textstyle \sum_{i \leq n} T^1_i}\right)
    &= \sum_{i \le n} T^1_i[\phi] \cdot \left(\mathbb{W}(\phi) - \phi^{*i} \right)
\end{align*}
$$

but $T^1_i[\phi]\equiv 1$ iff $i>s$, so this sum is

$$
\begin{align*}
    &= \sum_{s < i \le n} 1  \cdot \left( \mathbb{W}(\phi) - \phi^{*i} \right) .
\end{align*}
$$

Now, by our choice of $s$, $\mathbb{W}(\phi) = 1$, and $i>s$ implies $\phi^{*i} < 1-\varepsilon$, so this is

$$
\begin{align*}
    &\geq \sum_{s < i \le n}  \left( 1 - (1-\varepsilon) \right) \\
    &= \varepsilon\cdot(n-s)\\
    &\to \infty \textnormal{ as } n\to\infty.
\end{align*}
$$

 In particular, ${\overline{T}}^1$ exploits ${\overline{\mathbb{P}}}$, i.e., the set of values 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T_i}\right)\left({\overline{\mathbb{P}}}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n) \right\}
$$

 is bounded below but not bounded above. The analysis for case 2 is identical: if $L^2_n$ and $I^2_n$ hold for $n>s$, then ${\overline{T}}^2$ exploits ${\overline{\mathbb{P}}}$.

Now consider case 3, where $L^3_n$ and $I^3_n$ hold for $n>s$. Then for any time step $n>s$ and any world $\mathbb{W}\in\mathcal{PC}(D_n)$, 

$$
\begin{align*}
    \mathbb{W}\left({\textstyle \sum_{i \leq n} T^3_i}\right)
    &= \sum_{i \le n} \left((\mathbb{W}(\lnot(\phi \land \psi))-(\phi \lor \psi)^{* i}) - (\mathbb{W}(\phi)-\phi^{* i}) - (\mathbb{W}(\psi)-\psi^{* i}) \right) \\
    &= \sum_{s < i \le n} \left( \mathbb{W}(\phi \lor \psi) - \mathbb{W}(\phi) - \mathbb{W}(\psi) \right) - \left((\phi \lor \psi)^{*i}  - \phi^{*i} - \psi^{*i} \right)
\end{align*}
$$

but by our choice of $s$, $\mathbb{W}(\phi \lor \psi) - \mathbb{W}(\phi) - \mathbb{W}(\psi)=0$, and $i>s$ implies the inequality $(\phi \lor \psi)^{*i} - \phi^{*i} - \psi^{*i}< -\varepsilon$, so the above sum is

$$
\begin{align*}
    &\geq \sum_{s < i \le n} \varepsilon \\
    &= \varepsilon\cdot(n-s) \to\infty \textnormal{ as }n\to\infty .
\end{align*}
$$

 So ${\overline{T}}^3$ exploits ${\overline{\mathbb{P}}}$, contradicting the logical induction criterion. The analysis for case 4 is identical. Hence, all four implications must hold for ${\overline{\mathbb{P}}}$ to satisfy the logical induction criterion. ◻

### Non-dogmatism ^non-dogmatism-2

Recall Theorem 165:

**Theorem 105** (Non-Dogmatism). _If $\Gamma\nvdash \phi$ then $\mathbb{P}_\infty(\phi)<1$, and if $\Gamma\nvdash \neg\phi$ then $\mathbb{P}_\infty(\phi)>0$._

_Proof of Theorem 165._ We prove the second implication, since the first implication is similar, with selling in place of buying. Suppose for a contradiction that $\Gamma\nvdash \neg\phi$ but that $\mathbb{P}_\infty(\phi)=0$.

**Definition of the trader ${\overline{T}}$.** We define ${\overline{T}}$ recursively, along with helper functions ${\overline{\beta}}^k$ that will ensure that for every $k$, our trader will buy one share of $\phi$ for a price of at most $2^{-k}$: 

$$
\begin{align*}
\textnormal{for \(k=1,\ldots,n\):\hphantom{\(,+1\)}}\;\;\;\\
\beta^k_k &:=0\\
\textnormal{for \(i=k+1,\ldots,n\):}\;\;\;\\
\beta^k_i &:= \operatorname{Ind}_{\textnormal{\small{\({2^{-k-1}}\)}}}(\phi^{*i}<2^{-k})\cdot\left(1-\sum_{j=k}^{i-1}\beta^k_j \right)\\
T_i[\phi] &:= \sum_{j \le i} \beta^k_j\\
T_i &:= T_i[\phi]\cdot(\phi-\phi^{*i})
\end{align*}
$$

 Note that all the equations defining $T_n$ can be written down (from scratch) in ${\mathcal{O}}(n^3\log(n))$ time, so ${\overline{T}}$ is an e.c. trader.

**Proof of exploitation.** We leave the constant argument ${\overline{\mathbb{P}}}$ implicit to reduce clutter, writing, e.g., $\phi^{*i}$ for $\phi^{*i}({\overline{\mathbb{P}}}) = \mathbb{P}_i(\phi)$, $T_n[\phi]$ for $T_n[\phi]({\overline{\mathbb{P}}})$, and so on.

Observe from the recursion above for ${\overline{T}}$ that for all $i>0$ and $k>0$, 

$$
0\le\sum_{j=k}^i\beta^k_j\le 1
$$

 and for any $i$ and any $k\le i$, 

$$
\beta^k_i \ge 0.
$$

 Next, observe that for any $k>0$, for $i\geq$ some threshold $f(k)$, we will have $\phi^{*i} < 2^{-k-1}$, in which case the indicator in the definition of $\beta^k_i$ will equal $1$, at which point $\sum_{j=k}^i\beta^k_j = 1$. Thus, for all $n\ge f(k)$, 

$$
\sum_{i=k}^n\beta^k_i = 1.
$$

 Letting $H_n=\sum_{i\le n}T_i$, the following shows that our trader will eventually own an arbitrarily large number of $\phi$\-shares: 

$$
\begin{equation}
\begin{aligned}
H_n[\phi]&=\sum_{i\le n}\sum_{k\le i}\beta^k_i\\
&=\sum_{k\le n}\sum_{k\le i\le n}\beta^k_i\\
&\ge \sum_{\substack{k\le n\\ f(k)\le n}}\sum_{k\le i\le n}\beta^k_i\\
&= \sum_{\substack{k\le n\\ f(k)\le n}} 1 \quad\to\infty\textnormal{~ as ~}n\to\infty 
\end{aligned}
\tag{105}
\end{equation}
$$

 Next we show that our trader never spends more than a total of \$1\. 

$$
H_n[1] = -\sum_{i\le n}\sum_{k\le i}\beta^k_i\cdot\phi^{*i},
$$

but the indicator function defining $\beta_i^k$ ensures that $\phi^{*i}\le 2^{-k}$ whenever $\beta^k_i$ is non-zero, so this is

$$
\begin{align*}
&\ge -\sum_{i\le n}\sum_{k\le i}\beta^k_i \cdot 2^{-k}\\
&= -\sum_{k\le n}2^{-k}\cdot \sum_{k\le i\le n}\beta^k_i \\
&\ge -\sum_{k\le n}2^{-k}\cdot 1\\
\end{align*}
$$

Now, for any world $\mathbb{W}$, since $H_n[\phi]\ge 0$ for all $n$ and $\mathbb{W}(\phi)\geq 0$, we have 

$$
\begin{align*}
\mathbb{W}(H_n) &= H_n[1] + H_n[\phi]\mathbb{W}(\phi)\\
&\geq -1 + 0\cdot 0 \geq -1
\end{align*}
$$

 so the values $\mathbb{W}(H_n)$ are bounded below as $n$ varies. Moreover, since $\Gamma\nvdash\lnot\phi$, for every $n$ there is always some $\mathbb{W}\in\mathcal{PC}(D_n)$ where $\mathbb{W}(\phi)=1$ (since any consistent truth assignment can be extended to a truth assignment on all sentences), in which case 

$$
\mathbb{W}(H_n) \geq -1 + H_n[\phi] \cdot 1
$$

 But by equation (105), this $\lim_{n\to\infty}H_n[\phi] = \infty$, so $\lim_{n\to\infty}\mathbb{W}(H_n) = \infty$ as well. Hence, our e.c. trader exploits the market, contradicting the logical induction criterion. Therefore, if $\mathbb{P}_\infty(\phi)=0$, we must have $\Gamma\vdash\lnot\phi$. ◻

### Learning Pseudorandom Frequencies ^learning-pseudorandom-frequencies

Recall Theorem 140:

**Theorem 106** (Learning Pseudorandom Frequencies). _Let ${\overline{\phi}}$ be an e.c. sequence of decidable sentences. If ${\overline{\phi}}$ is pseudorandom with frequency $p$ over the set of all ${\overline{\mathbb{P}}}$\-generable divergent weightings, then 

$$
\mathbb{P}_n(\phi_n) \eqsim_np.
$$

_

Before beginning the proof, the following intuition may be helpful. If the theorem does not hold, assume without loss of generality that ${\overline{\mathbb{P}}}$ repeatedly underprices the $\phi_n$. Then a trader can buy $\phi_n$\-shares whenever their price goes below $p-\varepsilon$. By the assumption that the truth values of the $\phi_n$ are pseudorandom, roughly $p$ proportion of the shares will pay out. Since the trader only pays at most $p-\varepsilon$ per share, on average they make $\varepsilon$ on each trade, so over time they exploit the market. All we need to do is make the trades continuous, and ensure that the trader does not go below a fixed budget (as in the proof of Theorem 118).

_Proof of Theorem 140._ Suppose for a contradiction that ${\overline{\phi}}$ is an e.c. sequence of $\Gamma$\-decidable sentences such that for every ${\overline{\mathbb{P}}}$\-generable divergent weighting $w$, 

$$
\lim_{n\to\infty} \frac{\sum_{i < n} w_{i} \cdot \operatorname{Thm}_{\Gamma}{\phi_i}}{\sum_{i < n} w_{i}} = p,
$$

 but nevertheless, for some $\varepsilon > 0$ and infinitely many $n$, $|\mathbb{P}_n(\phi_n) - p| > \varepsilon$. Without loss of generality, assume that for infinite many $n$, 

$$
\mathbb{P}_n(\phi_n) < p -\varepsilon.
$$

 (The argument for the case where $\mathbb{P}_n(\phi_n) > p +\varepsilon$ infinitely often will be the same, and one of these two cases must obtain.)

**Definition of the trader ${\overline{T}}$.** We define $\operatorname{Open}:(\mathcal{S}\times{\mathbb{N}})\to {\mathbb{B}}$ to be the following (potentially very slow) computable function: 

$$
\operatorname{Open}(\phi,n)=\begin{cases}
      0 &\text{if \(D_n\vdash \phi\) or \(D_n\vdash \lnot\phi\)};\\
      1 &\text{otherwise.}
    \end{cases}
$$

 $\operatorname{Open}$ is computable because (remembering that $\vdash$ stands for propositional provability) we can just search through all truth assignments to the prime sentences of all sentences in $D_n$ that make the sentences in $D_n$ true, and see if they all yield the same truth value to $\phi$. We now define a much faster function $\operatorname{MO}:({\mathbb{N}}\times{\mathbb{N}})\to {\mathbb{B}}$ (mnemonic: “maybe open”) by 

$$
\operatorname{MO}(\phi,n)=\begin{cases}
      0 &\text{if for some \(m\le n\), \(\operatorname{Open}(\phi,m)\) returns \(0\) in \(\leq n\) steps}\\[2ex]
      1 &\textnormal{otherwise.}
    \end{cases}
$$

 Observe that $\operatorname{MO}(\phi,n)$ runs in ${\mathcal{O}}(n^2)$ time, and that for any decidable $\phi$,

-   $\operatorname{MO}(\phi,n)= 0$ for some sufficiently large $n$;
-   if $\operatorname{MO}(\phi,n)= 0$ then $\operatorname{Open}(\phi,n)$ = 0;
-   if $\operatorname{MO}(\phi,m)= 0$ and $n>m$ then $\operatorname{MO}(\phi,n)=0$.

(Note that $\operatorname{MO}$ may assign a value of $1$ when $\operatorname{Open}$ does not, hence the mnemonic “maybe open”.)

We will now use $\operatorname{MO}$ to define a trader ${\overline{T}}$ recursively, along with a helper function $\beta$ to ensure that it never holds a total of more than $1$ unit of open (fractional) shares. We let $\beta_1= 0$ and for $n\geq 1$, 

$$
\begin{align*}
    \beta_n&:= 1- \sum_{i<n} \operatorname{MO}(\phi_i, n) T_i[\phi_i];\\
    T_n[\phi_n] &:= \beta_n\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left(\phi_{n}^{*n} < p -\varepsilon /2\right);\\
    T_n&:= T_n[\phi_n]\cdot(\phi_n- \phi_{n}^{*n}).
\end{align*}
$$

 Observe that the expressible feature $T_n$ can be computed (from scratch) in $\operatorname{poly}(n)$ time using $\operatorname{MO}$, so ${\overline{T}}$ is an e.c. trader. Notice also that $\beta_n$ and all the $T_n(\phi)$ are always in $[0,1]$.

**A divergent weighting.** For the rest of the proof, we leave the constant argument ${\overline{\mathbb{P}}}$ implicit to reduce clutter, writing, e.g., $\phi_{i}^{*i}$ for $\phi_{i}^{*i}({\overline{\mathbb{P}}}) = \mathbb{P}_i(\phi_i)$, $T_n[\phi]$ for $T_n[\phi]({\overline{\mathbb{P}}})$, and so on.

We will show that the sequence of trade coefficients $w_n= T_n[\phi_n]$ made by ${\overline{T}}$ against the market ${\overline{\mathbb{P}}}$ form a ${\overline{\mathbb{P}}}$\-generable divergent weighting. Our trader ${\overline{T}}$ is efficiently computable and $T_n[\phi_n]\in [0,1]$ for all $n$, so it remains to show that, on input $\mathbb{P}_{\leq n}$, 

$$
\sum_{n\in {\mathbb{N}}^+} T_n[\phi_n] =\infty.
$$

 Suppose this were not the case, so that for some sufficiently large $m$, 

$$
\begin{equation}
\tag{106}
    \sum_{m<j} T_j[\phi_j] < 1/2.
\end{equation}
$$

 By the definition of $\operatorname{MO}$, there exists some large $m'$ such that for all $i<m$, $\operatorname{MO}(\phi_i,m')=0$. At that point, for any $n>m'$, we have 

$$
\begin{align*}
    \beta_{n} :=&\,  1- \sum_{i<n} T_i[\phi_i]\cdot\operatorname{MO}(\phi_i, n) \\
    =&\, 1 - \sum_{m<i<n} T_i[\phi_i]\cdot\operatorname{MO}(\phi_i, n) \\
    \geq&\, 1 - \sum_{m<i} T_i[\phi_i]
\end{align*}
$$

which, by equation (106), means that

$$
\beta_n\geq 1/2.
$$

 Then, by the earlier supposition on ${\overline{\mathbb{P}}}$, for some $n>m'$ we have $\mathbb{P}_n(\phi_n) < p -\varepsilon$, at which point 

$$
T_n[\phi_n] = \beta_n\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left(\phi_{n}^{*n} < p -\varepsilon /2\right) \geq \beta_n\cdot 1 \geq 1/2
$$

 which contradicts the $1/2$ bound in equation (106). Hence, the sum $\sum_i T_i[\phi_n]$ must instead be bounded. This means $(T_n[\phi_n])_{n\in{\mathbb{N}}^+}$ is a ${\overline{\mathbb{P}}}$\-generable divergent weighting.

**Proof of exploitation.** Now, by definition of ${\overline{\phi}}$ being pseudorandom with frequency $p$ over the class of ${\overline{\mathbb{P}}}$\-generable divergent weightings, we have that 

$$
\lim_{n\to\infty} \frac{\sum_{i\le n} T_i[\phi_i] \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}{\sum_{i\le n} T_i[\phi_i] } = p.
$$

 Thus, for all sufficiently large $n$, 

$$
{\sum_{i\le n} T_i[\phi_i] \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}\geq (p-\varepsilon/4)\cdot{\sum_{i\le n} T_i[\phi_i] } .
$$

Now, since our construction makes $\beta_n\in[0,1]$ for all $n$, we have 

$$
\sum_{i\le n} T_i[\phi_i]\cdot\operatorname{MO}(\phi_i,n) \leq 1.
$$

 Also, 

$$
\mathbb{W}(\phi_i) \geq\operatorname{Thm}_{\Gamma}(\phi_i)-\operatorname{MO}(\phi_i,n).
$$

Multiplying this by $T_i[\phi_i]$ and summing over $i$ gives

$$
\begin{align*}
    \sum_{i\le n} T_i[\phi_i]\cdot\mathbb{W}(\phi_i)
    &\ge \left(\sum_{i\le n} T_i[\phi_i]\cdot\operatorname{Thm}_{\Gamma}(\phi_i)\right) - \left(\sum_{i\le n} T_i[\phi_i]\cdot\operatorname{MO}(\phi_i,n)\right)\\
    &\ge \left(\sum_{i\le n} T_i[\phi_i]\cdot\operatorname{Thm}_{\Gamma}(\phi_i)\right) - 1 \\
    &\ge  - 1 + (p-\varepsilon/4)\sum_{i\le n} T_i[\phi_i].
\end{align*}
$$

By the definition of ${\overline{T}}$, and since $\phi_{i}^{*i}\le(p-\varepsilon/2)$ whenever $T_i[\phi_i]\neq 0$,

$$
-\sum_{i\le n} T_i[\phi_i]\cdot\phi_{i}^{*i} \ge - (p-\varepsilon/2)\sum_{i\le n} T_i[\phi_i].
$$

Adding the above two inequalities gives

$$
\begin{align*}
    \mathbb{W}\left(\sum_{i\le n} T_i\right) &\ge -1 + (\varepsilon/4)\sum_{i\le n} T_i[\phi_i]\\
    &\to\infty \textnormal{ as } n\to\infty
\end{align*}
$$

 because $T_i[\phi_i]$ is a divergent weighting (as shown above). Hence, ${\overline{T}}$ exploits the market ${\overline{\mathbb{P}}}$, contradicting the logical induction criterion. Therefore, for ${\overline{\mathbb{P}}}$ to satisfy the logical induction criterion, we must have 

$$
\lim_{n\to\infty}\mathbb{P}_n(\phi_n) = p.
$$

 ◻

### Provability Induction ^provability-induction

Recall Theorem 122:

**Theorem 107** (Provability Induction). _Let ${\overline{\phi}}$ be an e.c. sequence of theorems. Then 

$$
\mathbb{P}_n(\phi_n) \eqsim_n1.
$$

 Furthermore, let ${\overline{\psi}}$ be an e.c. sequence of disprovable sentences. Then 

$$
\mathbb{P}_n(\psi_n) \eqsim_n0.
$$

_

_Proof of Theorem 122._ Suppose ${\overline{\phi}}$ is an e.c. sequence of sentences with $\Gamma\vdash \phi_n$ for all $n$. Notice that for every $i$, the indicator $\operatorname{Thm}_{\Gamma}(\phi_i)$ evaluates to 1. Therefore we immediately have that for any divergent weighting $w$ at all, 

$$
\lim_{n\to\infty} \frac{\sum_{i < n} w_{i} \cdot \operatorname{Thm}_{\Gamma}{\phi_i}}{\sum_{i < n} w_{i}}= 1.
$$

 That is, the sequence ${\overline{\phi}}$ is pseudorandom (over any class of weightings) with frequency 1. Hence, by Learning Pseudorandom Frequencies (Theorem 140), 

$$
\mathbb{P}_n(\phi_n) \eqsim_n1,
$$

 as desired. The proof that $\mathbb{P}_n(\psi_n) \eqsim_n0$ proceeds analogously. ◻

Examining the proof of Theorem 140 (Learning Pseudorandom Frequencies) in the special case of provability induction yields some intuition. In this case, the trader defined in that proof essentially buys $\phi_n$\-shares every round that $\mathbb{P}_n(\phi_n) < 1-\varepsilon$. To avoid overspending, it tracks which $\phi_n$ have been proven so far, and never has more than 1 total share outstanding. Since eventually each $\phi_n$ is guaranteed to be valued at 1 in every plausible world, the value of the trader is increased by at least $\varepsilon$ (times the number of $\phi_n$\-shares it purchased) infinitely often. In this way, the trader makes profits for so long as ${\overline{\mathbb{P}}}$ fails to recognize the pattern ${\overline{\phi}}$ of provable sentences.

## Discussion ^discussion

We have proposed the _logical induction criterion_ as a criterion on the beliefs of deductively limited reasoners, and we have shown that reasoners who satisfy this criterion (_logical inductors_) possess many desirable properties when it comes to developing beliefs about logical statements (including statements about mathematical facts, long-running computations, and the reasoner themself). We have also given a computable algorithm for constructing a logical inductor. We will now discuss applications of logical induction (Section [[#^applications|7.1]]) and speculate about how and why we think this framework works (Section [[#^analysis|7.2]]). We then discuss a few variations on our framework (Section [[#^variations|7.3]]) before concluding with a discussion of a few open questions (Section [[#^open-questions|7.4]]).

### Applications ^applications

Logical inductors are not intended for practical use. The algorithm to compare with logical induction is not Belief Propagation (an efficient method for approximate inference in Bayesian networks (Pearl 1988)) but Solomonoff’s theory of inductive inference (an uncomputable method for making ideal predictions about empirical facts (Solomonoff 1964)). Just as Solomonoff’s sequence predictor assigns probabilities to all possible observations and learns to predict any computable environment, logical inductors assign probabilities to all possible sentences of logic and learns to recognize any efficiently computable pattern between logical claims.

Solomonoff’s theory involves a predictor that considers all computable hypotheses about their observations, weighted by simplicity, and uses Bayesian inference to zero in on the best computable hypothesis. This (uncomputable) algorithm is impractical, but has nevertheless been of theoretical use: its basic idiom—consult a series of experts, reward accurate predictions, and penalize complexity—is commonplace in statistics, predictive analytics, and machine learning. These “ensemble methods” often perform quite well in practice. Refer to Opitz and Maclin (1999); Dietterich (2000) for reviews of popular and successful ensemble methods.

One of the key applications of logical induction, we believe, is the development of an analogous idiom for scenarios where reasoners are uncertain about logical facts. Logical inductors use a framework similar to standard ensemble methods, with a few crucial differences that help them manipulate logical uncertainty. The experts consulted by logical inductors don’t make predictions about what is going to happen next; instead, they observe the aggregated advice of all the experts (including themselves) and attempt to exploit inefficiencies in that aggregate model. A trader doesn’t need to have an opinion about whether or not $\phi$ is true; they can exploit the fact that $\phi$ and $\lnot\lnot\phi$ have different probabilities without having any idea what $\phi$ says or what that’s supposed to mean. This idea and others yield an idiom for building models that integrate logical patterns and obey logical constraints.

In a different vein, we expect that logical inductors can already serve as a drop-in replacement for formal models of reasoners that assume logical omniscience and/or perfect Bayesianism, such as in game theory, economics, or theoretical models of artificial reasoners.

The authors are particularly interested in tools that help AI scientists attain novel statistical guarantees in settings where robustness and reliability guarantees are currently difficult to come by. For example, consider the task of designing an AI system that reasons about the behavior of computer programs, or that reasons about its own beliefs and its own effects on the world. While practical algorithms for achieving these feats are sure to make use of heuristics and approximations, we believe scientists will have an easier time designing robust and reliable systems if they have some way to relate those approximations to theoretical algorithms that are known to behave well in principle (in the same way that Auto-Encoding Variational Bayes can be related to Bayesian inference (Kingma and Welling 2013)). Modern models of rational behavior are not up to this task: formal logic is inadequate when it comes to modeling self-reference, and probability theory is inadequate when it comes to modeling logical uncertainty. We see logical induction as a first step towards models of rational behavior that work in settings where agents must reason about themselves, while deductively limited.

When it comes to the field of meta-mathematics, we expect logical inductors to open new avenues of research on questions about what sorts of reasoning systems can achieve which forms of self-trust. The specific type of self-trust that logical inductors achieve (via, e.g., Theorem 161) is a subtle subject, and worthy of a full paper in its own right. As such, we will not go into depth here.

### Analysis ^analysis

Mathematicians, scientists, and philosophers have taken many different approaches towards the problem of unifying logic with probability theory. (For a sample, refer to Section [[#^related-work|1.2]].) In this subsection, we will speculate about what makes the logical induction framework tick, and why it is that logical inductors achieve a variety of desiderata. The authors currently believe that the following three points are some of the interesting takeaways from the logical induction framework:

**Following Solomonoff and Gaifman.** One key idea behind our framework is our paradigm of making predictions by combining advice from an ensemble of experts in order to assign probabilities to all possible logical claims. This merges the framework of Solomonoff (1964) with that of Gaifman (1964), and it is perhaps remarkable that this can be made to work. Say we fix an enumeration of all prime sentences of first-order logic, and then hook $\textnormal{{\texttt{LIA}}}$ (Algorithm 99) up to a theorem prover that enumerates theorems of ${\mathsf{PA}}$ (written using that enumeration). Then all $\textnormal{{\texttt{LIA}}}$ ever “sees” (from the deductive process) is a sequence of sets like 

$$
\textnormal{\{\#92305 or \#19666 is true; \#50105 and \#68386 are true; \#8517 is false\}.}
$$

 From this and this alone, $\textnormal{{\texttt{LIA}}}$ develops accurate beliefs about all possible arithmetical claims. $\textnormal{{\texttt{LIA}}}$ does this in a manner that outpaces the underlying deductive process and satisfies the desiderata listed above. If instead we hook $\textnormal{{\texttt{LIA}}}$ up to a $\mathsf{ZFC}$\-prover, it develops accurate beliefs about all possible set-theoretic claims. This is very reminiscent of Solomonoff’s framework, where all the predictor sees is a sequence of 1s and 0s, and they start figuring out precisely which environment they’re interacting with.

This is only one of many possible approaches to the problem of logical uncertainty. For example, Adams’ probability logic (1996) works in the other direction, using logical axioms to put constraints on an unknown probability distribution and then using deduction to infer properties of that distribution. Markov logic networks (Richardson and Domingos 2006) construct a belief network that contains a variable for every possible way of grounding out each logical formula, which makes them quite ill-suited to the problem of reasoning about the behavior of complex Turing machines.[^note-8] In fact, there is no consensus about what form an algorithm for “good reasoning” under logical uncertainty should take. Empiricists such as Hintikka (1962); Fagin et al. (1995) speak of a set of modal operators that help differentiate between different types of knowledge; AI scientists such as Russell and Wefald (1991); Hay et al. (2012); Lin et al. (2015) speak of algorithms that are reasoning about complicated facts while also making decisions about what to reason about next; mathematicians such as (Briol et al. 2015; Briol et al. 2015; Hennig et al. 2015) speak of numerical algorithms that give probabilistic answers to particular questions where precise answers are difficult to generate.

Our approach achieves some success by building an approximately-coherent distribution over all logical claims. Of course, logical induction does not solve all the problems of reasoning under deductive limitation—far from it! They do not engage in meta-cognition (in the sense of Russell and Wefald (1991)) to decide which facts to reason about next, and they do not give an immediate practical tool (as in the case of probabilistic integration (Briol et al. 2015)), and they have abysmal runtime and uncomputable convergence bounds. It is our hope that the methods logical inductors use to aggregate expert advice will eventually yield algorithms that are useful for various applications, in the same way that useful ensemble methods can be derived from Solomonoff’s theory of inductive inference.

**Keep the experts small.** One of the key differences between our framework and Solomonoff-inspired ensemble methods is that our “experts” are not themselves predicting the world. In standard ensemble methods, the prediction algorithm weighs advice from a number of experts, where the experts themselves are also making predictions. The “master algorithm” rewards the experts for accuracy and penalizes them for complexity, and uses a weighted mixture of the experts to make their own prediction. In our framework, the master algorithm is still making predictions (about logical facts), but the experts themselves are not necessarily predictors. Instead, the experts are “traders”, who get to see the current model (constructed by aggregating information from a broad class of traders) and attempt to exploit inefficiencies in that aggregate model. This allows traders to identify (and eliminate) inconsistencies in the model even if they don’t know what’s actually happening in the world. For example, if a trader sees that $\mathbb{P}(\phi) + \mathbb{P}(\lnot \phi) \ll 1$, they can buy shares of both $\phi$ and $\lnot \phi$ and make a profit, even if they have no idea whether $\phi$ is true or what $\phi$ is about. In other words, letting the experts buy and sell shares (instead of just making predictions), and letting them see the aggregate model, allows them to contribute knowledge to the model, even if they have no idea what’s going on in the real world.

We can imagine each trader as contributing a small piece of logical knowledge to a model—each trader gets to say “look, I don’t know what you’re trying to predict over there, but I do know that this piece of your model is inconsistent”. By aggregating all these pieces of knowledge, our algorithm builds a model that can satisfy many different complicated relationships, even if every individual expert is only tracking a single simple pattern.

**Make the trading functions continuous.** As stated above, our framework gets significant mileage from showing each trader the aggregate model created by input from all traders, and letting them profit from identifying inconsistencies in that model. Showing traders the current market prices is not trivial, because the market prices on day $n$ depend on which trades are made on day $n$, creating a circular dependency. Our framework breaks this cycle by requiring that the traders use continuous betting strategies, guaranteeing that stable beliefs can be found.

In fact, it’s fairly easy to show that something like continuity is strictly necessary, if the market is to have accurate beliefs about itself. Consider again the paradoxical sentence $\chi := \text{“}{\underline{\mathbb{P}}}_{{\underline{n}}}({\underline{\chi}}) < 0.5\text{”}$ which is true iff its price in ${\overline{\mathbb{P}}}$ is less than 50¢ on day $n$. If, on day $n$, traders were allowed to buy when $\chi < 0.5$ and sell otherwise, then there is no equilibrium price. Continuity guarantees that the equilibrium price will always exist.

This guarantee protects logical inductors from the classic paradoxes of self-reference—as we have seen, it allows ${\overline{\mathbb{P}}}$ to develop accurate beliefs about its current beliefs, and to trust its future beliefs in most cases. We attribute the success of logical inductors in the face of paradox to the continuity conditions, and we suspect that it is a general-purpose method that deductively limited reasoners can use to avoid the classic paradoxes.

### Variations ^variations

One notable feature of the logical induction framework is its generality. The framework is not tied to a polynomial-time notion of efficiency, nor to any specific model of computation. All the framework requires is a method of enumerating possible patterns of logic (the “traders”) on the one hand, and a method of enumerating provable sentences of logic (the “deductive process”) on the other. Our algorithm then gives a method for aggregating those patterns into a combined model that respects the logical patterns that actually hold.

The framework would work just as well if we used the set of linear-time traders in place of the set of poly-time traders. Of course, the market built out of linear-time traders would not satisfy all the same desirable properties—but the _method of induction_, which consists of aggregating knowledge from a collection of traders and letting them all see the combined model and attempt to exploit it, would remain unchanged.

There is also quite a bit of flexibility in the definition of a trader. Above, traders are defined to output continuous piecewise-rational functions of the market prices. We could restrict this definition (e.g., by having traders output continuous piecewise-linear functions of the market prices), or broaden it (by replacing piecewise-rational with a larger class), or change the encoding scheme entirely. For instance, we could have the traders output not functions but upper-hemicontinuous relations specifying which trades they are willing to purchase; or we could give them oracle access to the market prices and have them output trades (instead of trading strategies). Alternatively, we could refrain from giving traders access to the market prices altogether, and instead let them sample truth values for sentences according to that sentence’s probability, and then consider markets that are almost surely not exploited by any of these traders.

In fact, our framework is not even specific to the domain of logic. Strictly speaking, all that is necessary is a set of atomic events that can be “true” or “false”, a language for talking about Boolean combinations of those atoms, and a deductive process that asserts things about those atoms (such as $\text{“}a \land \lnot b\text{”}$) over time. We have mainly explored the case where the atoms are prime sentences of first order logic, but the atoms could just as easily be bits in a webcam image, in which case the inductor would learn to predict patterns in the webcam feed. In fact, some atoms could be reserved for the webcam and others for prime sentences, yielding an inductor that does empirical and logical induction simultaneously.

For the sake of brevity, we leave the development of this idea to future works.

### Open Questions ^open-questions

With Definition 102, we have presented a simple criterion on deductively limited reasoners, such that any reasoner who meets the criterion satisfies a large number of desiderata, and any reasoner that fails to meet the criterion can have their beliefs exploited by an efficient trader. With ${\overline{\textnormal{{\texttt{LIA}}}}}$ we have shown that this criterion can be met in practice by computable reasoners.

The logical induction criterion bears a strong resemblance to the “no Dutch book” criteria used by Ramsey (1931); de Finetti (1937); Teller (1973); Lewis (1999) to support Bayesian probability theory. This fact, and the fact that a wide variety of desirable properties follow directly from a single simple criterion, imply that logical induction captures a portion of what it means to do good reasoning under deductive limitations. That said, logical induction leaves a number of problems wide open. Here we discuss four, recalling desiderata from Section [[#^desiderata-for-reasoning-under|1.1]]:

**Desideratum 15** (Decision Rationality). _The algorithm for assigning probabilities to logical claims should be able to target specific, decision-relevant claims, and it should reason about those claims as efficiently as possible given the computing resources available._

In the case of logical inductors, we can interpret this desideratum as saying that it should be possible to tell a logical inductor to reason about one sentence in particular, and have it efficiently allocate resources towards that task. For example, we might be curious about Goldbach’s conjecture, and wish to tell a logical inductor to develop its beliefs about that particular question, i.e. by devoting its computing resources in particular to sentences that relate to Goldbach’s conjecture (such as sentences that might imply or falsify it).

Our algorithm for logical induction does not do anything of this sort, and there is no obvious mechanism for steering its deliberations. In the terminology of Hay et al. (2012), ${\overline{\textnormal{{\texttt{LIA}}}}}$ does not do metalevel reasoning, i.e., it does nothing akin to “thinking about what to think about”. That said, it is plausible that logical induction could play a role in models of bounded decision-making agents. For example, when designing an artificial intelligence (AI) algorithm that _does_ try to reason about Goldbach’s conjecture, it would be quite useful for that algorithm to have access to a logical inductor that tells it which other mathematical facts are likely related (and how). We can imagine a resource-constrained algorithm directing computing resources while consulting a partially-trained logical inductor, occasionally deciding that the best use of resources is to train the logical inductor further. At the moment, these ideas are purely speculative; significant work remains to be done to see how logical induction bears on the problem of allocation of scarce computing resources when reasoning about mathematical facts.

**Desideratum 16** (Answers Counterpossible Questions). _When asked questions about contradictory states of affairs, a good reasoner should give reasonable answers._

In the year 1993, if you asked a mathematician about what we would know about mathematics if Fermat’s last theorem was false, they would talk about how that would imply the existence of non-modular elliptic curves. In the year 1994, Fermat’s last theorem was proven true, so by the principle of explosion, we now know that if Fermat’s last theorem were false, then 1=2 and $\sqrt{2}$ is rational, because from a contradiction, anything follows. The first sort of answer seems more reasonable, and indeed, reasoning about counterpossibilities (i.e., proving a conjecture false by thinking about what would follow if it were true) is a practice that mathematicians engage in regularly. A satisfactory treatment of counterpossibilities has proven elusive; see (Cohen 1990; Vander Laan 2004; Brogaard and Salerno 2007; Krakauer 2012; Bjerring 2014) for some discussion and ideas. One might hope that a good treatment of logical uncertainty would naturally result in a good treatment of counterpossibilities.

There are intuitive reasons to expect that a logical inductor has reasonable beliefs about counterpossibilities. In the days before ${\overline{D}}$ has (propositionally) ruled out worlds inconsistent with Fermat’s last theorem, ${\overline{\mathbb{P}}}$ has to have beliefs that allow for Fermat’s last theorem to be false, and if the proof is a long time in coming, those beliefs are likely reasonable. However, we do not currently have any guarantees of this form—$\mathbb{P}_\infty$ still assigns probability 0 to Fermat’s last theorem being false, and so the conditional probabilities are not guaranteed to be reasonable, so we haven’t yet found anything satisfactory to say with confidence about ${\overline{\mathbb{P}}}$’s counterpossible beliefs.

While the discussion of counterpossibilities may seem mainly academic, Soares and Fallenstein (2015) have argued that counterpossibilities are central to the problem of designing robust decision-making algorithms. Imagine a deterministic agent `agent` evaluating three different “possible scenarios” corresponding to three different actions the agent could take. Intuitively, we want the $n$th scenario (modeled inside the agent) to represent what would happen if the agent took the $n$th action, and this requires reasoning about what would happen if `agent(observation)` had the output `a` vs `b` vs `c`. Thus, a better understanding of counterpossible reasoning could yield better decision algorithms. Significant work remains to be done to understand and improve the way that logical inductors answer counterpossible questions.

**Desideratum 17** (Use of Old Evidence). _When a bounded reasoner comes up with a new theory that neatly describes anomalies in the old theory, that old evidence should count as evidence in favor of the new theory._

The canonical example of the problem of old evidence is Einstein’s development of the theory of general relativity and its retrodiction of the precession in Mercury’s orbit. For hundreds of years before Einstein, astronomers knew that Newton’s equations failed to model this precession, and Einstein’s retrodiction counted as a large boost for his theory. This runs contrary to Bayes’ theorem, which says that a reasoner should wring every drip of information out of every observation the moment that the evidence appears. A Bayesian reasoner keeps tabs on all possible hypotheses at all times, and so they never find a new hypothesis in a burst of insight, and reward it for retrodictions. Humans work differently—scientists spent centuries without having even one good theory for the precession of Mercury, and the difficult scientific labor of Einstein went into _inventing the theory_.

There is a weak sense in which logical inductors solve the problem of old evidence—as time goes on, they get better and better at recognizing patterns in the data that they have already seen, and integrating those old patterns into their new models. That said, a strong solution to the problem of old evidence isn’t just about finding new ways to use old data every so often; it’s about giving a satisfactory account of how to algorithmically _generate new scientific theories_. In that domain, logical induction has much less to say: they “invent” their “theories” by sheer brute force, iterating over all possible polynomial-time methods for detecting patterns in data.

There is some hope that logical inductors will shed light on the question of how to build accurate models of the world in practice, just as ensemble methods yield models that are better than any individual expert in practice. However, the task of using logical inductors to build practical models in some limited domain is wide open.

**Desideratum 14** (Efficiency). _The algorithm for assigning probabilities to logical claims should run efficiently, and be usable in practice._

Logical inductors are far from efficient, but they do raise an interesting empirical question. While the theoretically ideal ensemble method (the universal semimeasure (Li and Vitányi 1993)) is uncomputable, practical ensemble methods often make very good predictions about their environments. It is therefore plausible that practical logical induction-inspired approaches could manage logical uncertainty well in practice. Imagine we pick some limited domain of reasoning, and a collection of constant- and linear-time traders. Imagine we use standard approximation methods (such as gradient descent) to find approximately-stable market prices that aggregate knowledge from those traders. Given sufficient insight and tweaking, would the resulting algorithm be good at learning to respect logical patterns in practice? This is an empirical question, and it remains to be tested.

:::hide
### Acknowledgements ^acknowledgements

We acknowledge Abram Demski, Alex Appel, Benya Fallenstein, Daniel Filan, Eliezer Yudkowsky, Jan Leike, János Kramár, Nisan Stiennon, Patrick LaVictoire, Paul Christiano, Sam Eisenstat, Scott Aaronson, and Vadim Kosoy, for valuable comments and discussions. We also acknowledge contributions from attendees of the MIRI summer fellows program, the MIRIxDiscord group, the MIRIxLA group, and the MIRI$\chi$ group.

This research was supported as part of the Future of Life Institute (futureoflife.org) FLI-RFP-AI1 program, grant #2015-144576.

## References ^references

-   Aaronson, Scott. 2013. _Why philosophers should care about computational complexity_. Computability: Turing, Gödel, Church, and Beyond.
    
-   Adams, Ernest W. 1996. _A Primer of Probability Logic_.
    
-   Akama, Seiki; Costa, Newton C. A. 2016. _Why Paraconsistent Logics?_. Towards Paraconsistent Engineering.
    
-   Bacharach, Michael. 1994. _The epistemic structure of a theory of a game_. Theory and Decision.
    
-   Battigalli, Pierpaolo; Bonanno, Giacomo. 1999. _Recent results on belief, knowledge and the epistemic foundations of game theory_. Research in Economics.
    
-   Beygelzimer, Alina; Langford, John; Pennock, David M. 2012. _Learning Performance of Prediction Markets with Kelly Bettors_. 11th International Conference on Autonomous Agents and Multiagent Systems (AAMAS 2012).
    
-   Binmore, Kenneth. 1992. _Foundations of game theory_. Advances in Economic Theory: Sixth World Congress.
    
-   Bjerring, Jens Christian. 2014. _On Counterpossibles_. Philosophical Studies.
    
-   Blair, Howard A.; Subrahmanian, V.S. 1989. _Paraconsistent Logic Programming_. Theoretical Computer Science.
    
-   Boole, George. 1854. _An investigation of the laws of thought: on which are founded the mathematical theories of logic and probabilities_.
    
-   Briol, François-Xavier; Oates, Chris; Girolami, Mark; Osborne, Michael A. 2015. _Frank-Wolfe Bayesian Quadrature: Probabilistic Integration with Theoretical Guarantees_. Advances in Neural Information Processing Systems 28 (NIPS 2015).
    
-   Briol, François-Xavier; Oates, Chris; Girolami, Mark; Osborne, Michael A.; Sejdinovic, Dino. 2015. _Probabilistic Integration_.
    
-   Brogaard, Berit; Salerno, Joe. 2007. _Why Counterpossibles are Non-Trivial_. The Reasoner.
    
-   Calude, Cristian S; Stay, Michael A. 2008. _Most programs stop quickly or never halt_. Advances in Applied Mathematics.
    
-   Campbell-Moore, Catrin. 2015. _How to Express Self-Referential Probability. A Kripkean Proposal_. The Review of Symbolic Logic.
    
-   Carnap, Rudolf. 1962. _Logical Foundations of Probability_.
    
-   Christiano, Paul. 2014. _Non-Omniscience, Probabilistic Inference, and Metamathematics_.
    
-   Christiano, Paul F.; Yudkowsky, Eliezer; Herreshoff, Marcello; Bárász, Mihály. 2013. _Definability of Truth in Probabilistic Logic_.
    
-   Cohen, Daniel. 1990. _On What Cannot Be_. Truth or Consequences.
    
-   de Finetti, Bruno. 1937. _Foresight: Its Logical Laws, Its Subjective Sources_. Studies in Subjective Probability.
    
-   De Raedt, Luc. 2008. _Logical and Relational Learning_. Cognitive Technologies.
    
-   De Raedt, Luc; Kersting, Kristian. 2008. _Probabilistic Inductive Logic Programming_. Probabilistic Inductive Logic Programming.
    
-   De Raedt, Luc; Kimmig, Angelika. 2015. _Probabilistic (logic) programming concepts_. Machine Learning.
    
-   Demski, Abram. 2012. _Logical Prior Probability_. Artificial General Intelligence. 5th International Conference, AGI 2012.
    
-   Dietterich, Thomas G. 2000. _Ensemble Methods in Machine Learning_. 1st International workshop on Multiple Classifier Systems (MCS 2000).
    
-   Eells, Ellery. 1990. _Bayesian problems of old evidence_. Scientific Theories.
    
-   Eklund, Matti. 2002. _Inconsistent Languages_. Philosophy and Phenomenological Research.
    
-   Enderton, Herbert B. 2001. _A Mathematical Introduction to Logic_.
    
-   Fagin, Ronald; Halpern, Joseph Y. 1987. _Belief, awareness, and limited reasoning_. Artificial intelligence.
    
-   Fagin, Ronald; Halpern, Joseph Y.; Moses, Yoram; Vardi, Moshe. 1995. _Reasoning about knowledge, vol. 4_.
    
-   Fuhrmann, André. 2013. _Relevant logics, modal logics and theory change_.
    
-   Gaifman, Haim. 1964. _Concerning Measures in First Order Calculi_. Israel Journal of Mathematics.
    
-   Gaifman, Haim; Snir, Marc. 1982. _Probabilities over rich languages, testing and randomness_. Journal of Symbolic Logic.
    
-   Garber, Daniel. 1983. _Old evidence and logical omniscience in Bayesian confirmation theory_. Testing scientific theories.
    
-   Gärdenfors, Peter. 1988. _Knowledge in Flux: Modeling the Dynamics of Epistemic States_.
    
-   Garrabrant, Scott; Benson-Tilsen, Tsvi; Bhaskar, Siddharth; Demski, Abram; Garrabrant, Joanna; Koleszarik, George; Lloyd, Evan. 2016. _Asymptotic Logical Uncertainty and the Benford Test_. 9th Conference on Artificial General Intelligence (AGI-16).
    
-   Garrabrant, Scott; Fallenstein, Benya; Demski, Abram; Soares, Nate. 2016. _Inductive Coherence_.
    
-   Garrabrant, Scott; Soares, Nate; Taylor, Jessica. 2016. _Asymptotic Convergence in Online Learning with Unbounded Delays_.
    
-   Gerla, Giangiacomo. 2013. _Fuzzy logic: mathematical tools for approximate reasoning_. Trends in Logic.
    
-   Glanzberg, Michael. 2001. _The Liar in Context_. Philosophical Studies.
    
-   Glymour, Clark. 1980. _Theory and Evidence_.
    
-   Gödel, Kurt; Kleene, Stephen Cole; Rosser, John Barkley. 1934. _On Undecidable Propositions of Formal Mathematical Systems_.
    
-   Good, Irving J. 1950. _Probability and the Weighing of Evidence_.
    
-   Grim, Patrick. 1991. _The Incomplete Universe: Totality, Knowledge, and Truth_.
    
-   Guarino, Nicola. 1998. _Formal Ontology and Information Systems_. Formal Ontology in Information Systems: Proceedings of FOIS’98.
    
-   Gupta, Anil; Belnap, Nuel D. 1993. _The Revision Theory of Truth_.
    
-   Hacking, Ian. 1967. _Slightly More Realistic Personal Probability_. Philosophy of Science.
    
-   Hailperin, Theodore. 1996. _Sentential probability logic_.
    
-   Halpern, Joseph Y. 2003. _Reasoning about Uncertainty_.
    
-   Hay, Nicholas; Russell, Stuart J.; Shimony, Solomon Eyal; Tolpin, David. 2012. _Selecting Computations: Theory and Applications_. Uncertainty in Artificial Intelligence (UAI-’12).
    
-   Hennig, Philipp; Osborne, Michael A.; Girolami, Mark. 2015. _Probabilistic numerics and uncertainty in computations_. Proceedings of the Royal Society of London A: Mathematical, Physical and Engineering Sciences.
    
-   Hilbert, David. 1902. _Mathematical Problems_. Bulletin of the American Mathematical Society.
    
-   Hintikka, Jaakko. 1962. _Knowledge and belief: An introduction to the logic of the two notions_.
    
-   Hintikka, Jaakko. 1979. _Impossible Possible Worlds Vindicated_. Game-Theoretical Semantics: Essays on Semantics by Hintikka, Carlson, Peacocke, Rantala, and Saarinen.
    
-   Hutter, Marcus; Lloyd, John W.; Ng, Kee Siong; Uther, William T. B. 2013. _Probabilities on Sentences in an Expressive Logic_. Journal of Applied Logic.
    
-   Jaynes, E. T. 2003. _Probability Theory_.
    
-   Jeffrey, Richard. 1983. _Bayesianism with a human face_. Testing scientific theories, minnesota studies in the philosophy of science.
    
-   Joyce, James M. 1999. _The Foundations of Causal Decision Theory_. Cambridge Studies in Probability, Induction and Decision Theory.
    
-   Kersting, Kristian; De Raedt, Luc. 2007. _Bayesian Logic Programming: Theory and Tool_. Introduction to Statistical Relational Learning.
    
-   Khot, Tushar; Balasubramanian, Niranjan; Gribkoff, Eric; Sabharwal, Ashish; Clark, Peter; Etzioni, Oren. 2015. _Markov Logic Networks for Natural Language Question Answering_.
    
-   Kingma, Diederik P; Welling, Max. 2013. _Auto-Encoding Variational Bayes_.
    
-   Klir, George; Yuan, Bo. 1995. _Fuzzy Sets and Fuzzy Logic_.
    
-   Kok, Stanley; Domingos, Pedro. 2005. _Learning the structure of Markov logic networks_. 22nd International Conference on Machine Learning (ICML ’05).
    
-   Kolmogorov, A.N. 1950. _Foundations of the Theory of Probability._.
    
-   Krakauer, Barak. 2012. _Counterpossibles_.
    
-   Kucera, Antonin; Nies, Andre. 2011. _Demuth randomness and computational complexity_. Annals of Pure and Applied Logic.
    
-   Lewis, David. 1999. _Papers in metaphysics and epistemology_.
    
-   Li, Ming; Vitányi, Paul M. B. 1993. _An Introduction to Kolmogorov Complexity and its Applications_.
    
-   Lin, Christopher H; Kolobov, Andrey; Kamar, Ece; Horvitz, Eric. 2015. _Metareasoning for Planning Under Uncertainty_.
    
-   Lindley, Dennis V. 1991. _Making Decisions_.
    
-   Lipman, Barton L. 1991. _How to decide how to decide how to...: Modeling limited rationality_. Econometrica: Journal of the Econometric Society.
    
-   Łoś, Jerzy. 1955. _On the Axiomatic Treatment of Probability_. Colloquium Mathematicae.
    
-   Lowd, Daniel; Domingos, Pedro. 2007. _Efficient Weight Learning for Markov Logic Networks_. 11th European Conference on Principles and Practice of Knowledge Discovery in Databases (PKDD 2007).
    
-   McCallum, Andrew; Schultz, Karl; Singh, Sameer. 2009. _Factorie: Probabilistic programming via imperatively defined factor graphs_. Advances in Neural Information Processing Systems 22 (NIPS 2009).
    
-   McGee, Vann. 1990. _Truth, Vagueness, and Paradox: An Essay on the Logic of Truth_.
    
-   Meyer, J-J Ch.; Van Der Hoek, Wiebe. 1995. _Epistemic logic for AI and computer science_. Cambridge Tracts in Theoretical Computer Science.
    
-   Mihalkova, Lilyana; Huynh, Tuyen; Mooney, Raymond J. 2007. _Mapping and Revising Markov Logic Networks for Transfer Learning_. 22nd Conference on Artificial Intelligence (AAAI-07).
    
-   Mortensen, Chris. 2013. _Inconsistent Mathematics_. Mathematics and Its Applications.
    
-   Muggleton, Stephen H.; Watanabe, Hiroaki. 2014. _Latest Advances in Inductive Logic Programming_.
    
-   Muiño, David Picado. 2011. _Measuring and Repairing Inconsistency in Probabilistic Knowledge Bases_. International Journal of Approximate Reasoning.
    
-   Opitz, David; Maclin, Richard. 1999. _Popular Ensemble Methods: An Empirical Study_. Journal of Artificial Intelligence Research.
    
-   Pearl, Judea. 1988. _Probabilistic Reasoning in Intelligent Systems_.
    
-   Polya, George. 1990. _Mathematics and Plausible Reasoning: Patterns of plausible inference_.
    
-   Potyka, Nico. 2015. _Solving Reasoning Problems for Probabilistic Conditional Logics with Consistent and Inconsistent Information_.
    
-   Potyka, Nico; Thimm, Matthias. 2015. _Probabilistic Reasoning with Inconsistent Beliefs Using Inconsistency Measures_. 24th International Joint Conference on Artificial Intelligence (IJCAI-15).
    
-   Priest, Graham. 2002. _Paraconsistent Logic_. Handbook of Philosophical Logic.
    
-   Ramsey, Frank Plumpton. 1931. _Truth and Probability_. The Foundations of Mathematics and other Logical Essays.
    
-   Rantala, Veikko. 1979. _Urn Models: A New Kind of Non-Standard Model for First-Order Logic_. Game-Theoretical Semantics: Essays on Semantics by Hintikka, Carlson, Peacocke, Rantala, and Saarinen.
    
-   Richardson, Matthew; Domingos, Pedro. 2006. _Markov Logic Networks_. Machine Learning.
    
-   Rubinstein, Ariel. 1998. _Modeling Bounded Rationality_.
    
-   Russell, Stuart J. 2016. _Rationality and Intelligence: A Brief Update_. Fundamental Issues of Artificial Intelligence.
    
-   Russell, Stuart J.; Wefald, Eric H. 1991. _Do the Right Thing: Studies in Limited Rationality_.
    
-   Russell, Stuart J.; Wefald, Eric H. 1991. _Principles of Metareasoning_. Artificial intelligence.
    
-   Savage, Leonard J. 1954. _The foundations of statistics._.
    
-   Savage, Leonard J. 1967. _Difficulties in the theory of personal probability_. Philosophy of Science.
    
-   Sawin, Will; Demski, Abram. 2013. _Computable probability distributions which converge on believing true $\Pi$1 sentences will disbelieve true $\Pi$2 sentences_.
    
-   Schlesinger, George N. 1985. _Range of Epistemic Logic_. Scots Philosophical Monograph.
    
-   Simon, Herbert Alexander. 1982. _Models of bounded rationality: Empirically grounded economic reason_.
    
-   Singla, Parag; Domingos, Pedro. 2005. _Discriminative Training of Markov Logic Networks_. 20th National Conference on Artificial Intelligence (AAAI-05).
    
-   Soares, Nate; Fallenstein, Benja. 2015. _Toward Idealized Decision Theory_.
    
-   Solomonoff, Ray J. 1964. _A Formal Theory of Inductive Inference. Part I_. Information and Control.
    
-   Solomonoff, Ray J. 1964. _A Formal Theory of Inductive Inference. Part II_. Information and Control.
    
-   Sowa, John F. 1999. _Knowledge Representation: Logical, Philosophical, and Computational Foundations_.
    
-   Sprenger, Jan. 2015. _A Novel Solution to the Problem of Old Evidence_. Philosophy of Science.
    
-   Teller, Paul. 1973. _Conditionalization and observation_. Synthese.
    
-   Thimm, Matthias. 2013. _Inconsistency Measures for Probabilistic Logics_. Artificial Intelligence.
    
-   Thimm, Matthias. 2013. _Inconsistency measures for probabilistic logics_. Artificial Intelligence.
    
-   Tran, Son D; Davis, Larry S. 2008. _Event modeling and recognition using markov logic networks_. European Conference on Computer Vision.
    
-   Turing, Alan M. 1936. _On Computable Numbers, with an Application to the Entscheidungsproblem_. Proceedings of the London Mathematical Society.
    
-   Vajda, Steven. 1972. _Probabilistic Programming_. Probability and Mathematical Statistics: A Series of Monographs and Textbooks.
    
-   Vander Laan, David. 2004. _Counterpossibles and similarity_. Lewisian Themes: The Philosophy of David K. Lewis.
    
-   von Neumann, John; Morgenstern, Oskar. 1944. _Theory of Games and Economic Behavior_.
    
-   Wang, Jue; Domingos, Pedro M. 2008. _Hybrid Markov Logic Networks_. 23rd Conference on Artificial Intelligence (AAAI-08).
    
-   Wood, Frank; Meent, Jan-Willem; Mansinghka, Vikash. 2014. _A New Approach to Probabilistic Programming Inference._. Proceedings of the 17th International Conference on Artificial Intelligence and Statistics (AISTATS).
    
-   Yen, John; Langari, Reza. 1999. _Fuzzy Logic: Intelligence, Control, and Information_.
    
-   Zhang, Yitang. 2014. _Bounded gaps between primes_. Annals of Mathematics.
    
-   Zilberstein, Shlomo. 2008. _Metareasoning and bounded rationality_. Metareasoning: Thinking about Thinking, MIT Press, forthcoming.
    
-   Zvonkin, Alexander K.; Levin, Leonid A. 1970. _The Complexity of Finite Objects and the Development of the Concepts of Information and Randomness by Means of the Theory of Algorithms_. Russian Mathematical Surveys.
    
-   Zynda, Lyle. 1995. _Old evidence and new theories_. Philosophical Studies.
    
:::

:::callout {title="Appendix" collapse="closed"}
## Preliminaries ^preliminaries

### Organization of the Appendix ^organization-of-the-appendix

The appendix is organized differently from the paper. Here we describe the broad dependency structure of the proofs and mention the theorems that are proven by constructing explicit traders (rather than as corollaries). Note that theorems that were proven in Section 6 are also proven here, but differently (generally much more concisely, as a corollary of some other theorem).

**[[#^preliminaries|8]]. Preliminaries.** Appendix [[#^expressible-features|8.2]] describes expressible features in full detail. Appendix [[#^definitions|8.3]] defines some notions for combinations, and defines when a sequence of traders can be “efficiently emulated”, which will be useful in [[#^convergence-proofs|9]], [[#^affine-recurring-unbiasedness|11.1]], and [[#^non-dogmatism-and-closure-proofs|14]].

**[[#^convergence-proofs|9]]. Convergence.** Appendix [[#^return-on-investment|9.1]] introduces a tool for constructing traders (Lemma 115, Return on Investment) that is used in [[#^convergence-proofs|9]] and [[#^affine-recurring-unbiasedness|11.1]]. Appendices [[#^affine-preemptive-learning|9.2]] (Affine Preemptive Learning) and [[#^persistence-of-affine-knowledge|9.5]] (Persistence of Affine Knowledge) prove those theorems using Lemma 115, and the remainder of [[#^convergence-proofs|9]] derives some corollaries (convergence and non-affine special cases).

**[[#^coherence-proofs|10]]. Coherence.** Appendix [[#^affine-coherence|10.1]] proves Affine Coherence, giving (Affine) Provability Induction as corollaries. The remainder of [[#^coherence-proofs|10]] derives corollaries of Provability Induction (consistency and halting) and of Affine Provability Induction (coherence and exclusive-exhaustive relationships).

**[[#^statistical-proofs|11]]. Statistics.** Appendix [[#^affine-recurring-unbiasedness|11.1]] proves Affine Recurring Unbiasedness using Lemma 115, giving Simple Calibration ([[#^simple-calibration|11.3]]) as a corollary. Appendices [[#^affine-unbiasedness-from-feedback|11.4]] (Affine Unbiasedness From Feedback) and [[#^learning-pseudorandom-affine-sequences|11.6]] (Learning Pseudorandom Affine Sequences) prove those theorems by constructing traders, and the remainder of Appendix [[#^statistical-proofs|11]] derives corollaries (varied and non-affine cases).

**[[#^expectations-proofs|12]]. Expectations.** Appendix [[#^mesh-independence-lemma|12.2]] proves the Mesh Independence Lemma by constructing a trader, and [[#^consistent-world-luv-approximation|12.1]] and [[#^limiting-expectation-approximation-lemma|12.5]] prove two other lemmas on expectations; basic properties of expectations such as convergence and linearity are also proved. These proofs rely on theorems proven in [[#^convergence-proofs|9]] and [[#^coherence-proofs|10]]. The remainder of [[#^expectations-proofs|12]] proves analogs for expectations of the convergence, coherence, and statistical theorems by applying their affine versions to $\mathcal{F}$\-combinations expressing expectations.

**[[#^introspection-and-self-trust-proofs|13]]. Introspection and Self-Trust.** The first part of Appendix [[#^introspection-and-self-trust-proofs|13]] proves introspection properties using Affine Provability Induction and Expectation Provability Induction. The remainder derives the self-trust properties as applications of theorems proven in Appendix [[#^expectations-proofs|12]].

**[[#^non-dogmatism-and-closure-proofs|14]]. Non-Dogmatism and Closure.** Appendix [[#^non-dogmatism-and-closure-proofs|14]] is mostly self-contained. Appendix [[#^parametric-traders|14.1]] proves a simple analog of the return on investment lemma with stronger hypotheses; this is applied to constructing traders in [[#^uniform-non-dogmatism|14.2]] (Uniform Non-Dogmatism), [[#^occam-bounds|14.3]] (Occam Bounds), and [[#^domination-of-the-universal|14.5]] (Domination of the Universal Semimeasure), with non-dogmatism and strict domination as corollaries. Appendix [[#^conditionals-on-theories|14.8]] (Conditionals on Theories) uses uniform non-dogmatism, preemptive learning, and [[#^closure-under-finite-perturbations|14.7]] (Closure under Finite Perturbations).

### Expressible Features ^expressible-features

_This section can be safely skipped and referred back to as desired._

Recall that a trading strategy for day $n$ is given by an affine combination of sentences with expressible feature coefficients. As such, a machine that implements a trader must use some notation for writing down those features. Here, to be fully rigorous, we will make an explicit choice of notation for expressible features. Recall their definition:

**Definition 108** (Expressible Feature). _An **expressible feature** $\xi\in \mathcal{F}$ is a valuation feature expressible by an algebraic expression built from price features ${\phi}^{*n}$ for each $n\in{\mathbb{N}}^+$ and $\phi\in\mathcal{S}$, rational numbers, addition, multiplication, $\max(-, -)$, and a “safe reciprocation” function $\max(1,-)^{-1}$._

_We write $\mathcal{E\!F}$ for the set of all expressible features, $\mathcal{E\!F}_n$ for the set of expressible features of rank $\leq n$, and define an **$\boldsymbol{\mathcal{E\!F}}$\-progression** to be a sequence ${\overline{\xi}}$ such that $\xi_n\in\mathcal{E\!F}_n$._

A (multi-line) string representing an expressible feature will be called a _well-formed feature expression_, and will be built from smaller expressions involving variables (mainly to save space when a particular expression would otherwise need to be repeated many times).

We define the set of _variable feature expressions_ $\Xi$ inductively to include:

-   Past and present market prices: for all $i \leq n$ and for all $\psi\in\mathcal{S}$, there is a symbol $\psi^{* i}\in\Xi$.
    
-   Rationals: ${\mathbb{Q}}\subset \Xi$.
    
-   Variables: $V \subset \Xi$.
    

Further, if $\xi\in\Xi$ and $\zeta\in\Xi$, then the following operations on them are as well:

-   Addition: $\xi + \zeta\in\Xi$.
    
-   Multiplication: $\xi \cdot \zeta\in\Xi$.
    
-   Maximum: $\max(\xi, \zeta)\in\Xi$.
    
-   Safe reciprocation: $1/\max(1,\xi)\in\Xi$.
    

These operations are sufficient to generate all the expressible features we will need. For example, 

$$
\begin{align*}
-\xi &:= (-1)\cdot \xi;\\
\min(\xi,\zeta) &:= -\max(-\xi,-\zeta);\\
|\xi|&:= \max(\xi,-\xi);
\end{align*}
$$

and when $\zeta \geq \varepsilon$ for some constant $\varepsilon > 0$, we can define

$$
\xi/\zeta := (1/\varepsilon) \cdot \xi/\max(1,  (1/\varepsilon) \cdot \zeta ).
$$

We now define a _well-formed feature expression_ to be a (multi-line) string of the following form: 

$$
\begin{align*}
&v_1 := (\textnormal{feature expression with no variables});\\
&v_2 := (\textnormal{feature expression involving \(v_1\)});\\
&\cdots\\
&v_k := (\textnormal{feature expression involving \(v_1,\ldots,v_{k-1}\)});\\
&\textrm{return }(\textnormal{feature expression involving \(v_1,\ldots,v_k\)}),
\end{align*}
$$

 where the final expression after “$\textrm{return }$” is the expression evaluated to actually compute the expressible feature defined by this code block.

#### Examples ^examples

The following well-formed feature expression defines a rank 7 expressible feature: 

$$
\begin{align*}
&v_1 := \phi_1^{* 7} + \phi_2^{* 4}\\
&v_2 := v_1 - 1\\
&\textrm{return }3\cdot \max(v_1,v_2).
\end{align*}
$$

 If the market at time 7 has $\mathbb{P}_7(\phi_1)= 0.8$ and the market at time $4$ had $\mathbb{P}_4(\phi_2)=0$, then this expressible feature evaluates to 

$$
3\cdot \max(v_1,v_2) = 3\cdot \max(0.8,-0.2) = 2.4.
$$

 An $n$\-strategy can now be written down in a very similar format, sharing variable definitions used in the various coefficients to save space. For example, the following code defines a $7$\-strategy: 

$$
\begin{align*}
&v_1 := \phi_1^{* 7} + \phi_2^{* 4}\\
&v_2 := v_1 \cdot v_1\\
&T[\phi_1] := 3\cdot \max(v_1,v_2)\\
&T[\phi_2] := 6 \cdot \max(v_1,v_2).\\
&T:= \sum_{i=1}^2 T[\phi_i]\cdot(\phi_i-\phi_i^{*n})\\
&\textrm{return }T
\end{align*}
$$

Notice that the function $\phi_1^{*7}$ returning the current market price of $\phi_1$ affects (via $v_1$) how many shares of $\phi_1$ this trader buys. This is permitted, and indeed is crucial for allowing traders to base their trades on the current market prices.

#### Dynamic programming for traders ^dynamic-programming-for-traders

We will often define traders that make use of indexed variables that are defined recursively in terms of previous indices, as in e.g. the proof of Theorem 118 (Convergence) in Section [[#^convergence|6.1]]. In particular, we often have traders refer to their own past trades, e.g. using expressible features of the form $T_i[\phi]$ for $i<n$ to define their trade at time $n$. This can be written down in polynomial time using the expression language for features, via dynamic programming. For example, to use previous trades, a trader can recapitulate all the variables used in all its previous trading strategies. As long as the trading strategies are efficiently computable given previous trades as variables, they are still efficiently computable without them (possibly with a higher-degree polynomial).

### Definitions ^definitions

#### Price of a Combination ^price-of-a-combination

**Definition 109** (Price of a Combination). _Given any affine combination 

$$
A=
    c
      + \xi_1\phi_1
      + \cdots
      + \xi_k\phi_k
$$

 of rank $\leq n$, observe that the map ${\overline{\mathbb{V}}}\mapsto \mathbb{V}_n(A)$ is an expressible feature, called the **price** of $A$ on day $n$, and is given by the expression 

$$
{A}^{*n} :=
    c
      + \xi_1{\phi_1}^{*n}
      + \cdots
      + \xi_k{\phi_k}^{*n}.
$$

 For any valuation sequence ${\overline{\mathbb{U}}}$, observe by linearity and associativity that 

$$
(\mathbb{V}(A))({\overline{\mathbb{U}}}) = \mathbb{V}(A({\overline{\mathbb{U}}})) = c({\overline{\mathbb{U}}}) + \sum_\phi \xi_\phi({\overline{\mathbb{U}}})\mathbb{V}(\phi) .
$$

_

#### Buying a Combination ^buying-a-combination

**Definition 110** (Buying a Combination). _Given any $\mathcal{E\!F}$\-combination $A^\dagger$ of $\operatorname{rank}\leq n$, we define a corresponding $n$\-strategy called **buying $\boldsymbol{A^\dagger}$ on day $\boldsymbol{n}$** to equal 

$$
A^\dagger- A^{\dagger* n}.
$$

 Observe that buying $A$ on day $n$ is indeed an $n$\-strategy._

#### $\mathcal{F}$\-Combinations Corresponding to $\mathcal{F}$\-LUV Combinations ^mathcal-f-combinations-corresponding

**Definition 111** ($\mathrm{Ex}$). _Let $B:= c+ \xi_1 X_1 + \cdots + \xi_k X_k$ be an $\mathcal{F}$\-LUV combination. Define 

$$
\mathrm{Ex}_m(A) = c+ \xi_1 \sum_{i=0}^{m-1} \frac{1}{m} (\text{“}{\underline{X_1}} > {\underline{i}}/{\underline{m}}\text{”}) + \cdots + \xi_k \sum_{i=0}^{m-1} \frac{1}{m} (\text{“}{\underline{X_k}} > {\underline{i}}/{\underline{m}}\text{”})
$$

 to be a $\mathcal{F}$\-affine combination corresponding to $B$. Note that $\mathbb{V}(\mathrm{Ex}_m(B)) = {\mathbb{E}}_m^\mathbb{V}(B)$. Also note that if $(B_n)_n$ is bounded, then $(\mathrm{Ex}_n(B_n))_n$ is bounded; we will use this fact freely in what follows._

#### Efficiently Emulatable Sequence of Traders ^efficiently-emulatable-sequence-of

In Appendices [[#^convergence-proofs|9]], [[#^affine-recurring-unbiasedness|11.1]], and [[#^non-dogmatism-and-closure-proofs|14]], we will construct traders that allocate their money across multiple strategies for exploiting the market. In order to speak unambiguously about multiple overlapping long-term strategies for making trades, we define the notion of a sequence of traders that can be efficiently emulated by one trader.

**Definition 112** (Efficiently Emulatable Sequence of Traders). _We say that a sequence of traders $( {\overline{T}}^k)_k$ is _efficiently emulatable_ if_

-   _the sequence of programs that compute the ${\overline{T}}^k$ can be efficiently generated;_
    
-   _those programs for ${\overline{T}}^k$ have uniformly bounded runtime, i.e., there exists a constant $c$ such that for all $k$ and all times $n$, the program that computes ${\overline{T}}^k$ runs in time ${\mathcal{O}}(n^c)$; and_
    
-   _for all $k$ and all $n<k$, we have that ${\overline{T}}^k_n$ is the zero trade._
    

Efficiently emulatable sequences are so named because a single trader ${\overline{T}}$ can emulate the entire sequence of traders $({\overline{T}}^k)_k$. That is, on time $n$, ${\overline{T}}$ can directly compute all the trading strategies $T^k_n$ for $k\le n$ by listing the appropriate programs and running them on input $n$. This can be done in polynomial time by definition of an efficiently emulatable sequence. We require that ${\overline{T}}^k$ does not make non-zero trades before time $k$ so that the emulator ${\overline{T}}$ need not truncate any trades made by the ${\overline{T}}^k$.

## Convergence Proofs ^convergence-proofs

### Return on Investment ^return-on-investment

This section provides a useful tool for constructing traders, which will be applied in Appendix [[#^convergence-proofs|9]] and Appendix [[#^affine-recurring-unbiasedness|11.1]]. The reader may wish to first begin with the proof in Appendix [[#^affine-preemptive-learning|9.2]] of Theorem 116 as motivation of the return on investment lemma.

##### Statement of the $\boldsymbol{\varepsilon}$\-ROI lemma. ^statement-of-the-boldsymbol

If we have a logical inductor ${\overline{\mathbb{P}}}$, we know that ${\overline{\mathbb{P}}}$ cannot be exploited by any trader. It will often be easy to show that if ${\overline{\mathbb{P}}}$ fails to satisfy some property, then there is a trader ${\overline{T}}$ that takes advantage of a specific, one-shot opportunity to trade against the market in a way that is guaranteed to eventually be significantly higher value than the size of the original investment; and that such opportunities arise infinitely often. In order to use such a situation to ensure that the market ${\overline{\mathbb{P}}}$ satisfies the property, we will now show that logical inductors are not susceptible to repeatable methods for making a guaranteed, substantial profit.

To define a notion of return on investment, we first define the “magnitude” of a trade made by a trader, so that we can talk about traders that are profitable in proportion to the size of their trades: 

$$
{\|T({\overline{\mathbb{P}}})\|_{\rm mg}} := \sum_{\phi\in\mathcal{S}} |T[\phi]({\overline{\mathbb{P}}})|.
$$

 This number will be called the **magnitude** of the trade. It is just the total number of shares traded by $T$ against the market ${\overline{\mathbb{P}}}$, whether the shares are bought or sold. Note that the magnitude is _not_ the same as the ${\|-\|_1}$\-norm of $T({\overline{\mathbb{P}}})$; the magnitude omits the constant term $T[1]({\overline{\mathbb{P}}})$.

The magnitude is a simple bound on the value of the holdings $T_n({\overline{\mathbb{P}}})$: for any world $\mathbb{W}$ (plausible or not), 

$$
\left| \sum_{\phi\in\mathcal{S}} T_n[\phi]({\overline{\mathbb{P}}}) \cdot \left(\mathbb{W}(\phi) - \mathbb{P}_n(\phi)\right)\right|
\le \sum_{\phi\in\mathcal{S}} \left| T_n[\phi]({\overline{\mathbb{P}}})\right| \cdot 1  = {\|T_n({\overline{\mathbb{P}}})\|_{\rm mg}},
$$

 since $\mathbb{W}(\phi)\in\{0,1\}$ and $\mathbb{P}_n(\phi)\in [0,1]$. Now we define the total magnitude of a trader over time.

**Definition 113** (Magnitude of a Trader). _The **magnitude** ${\|{\overline{T}}({\overline{\mathbb{P}}})\|_{\rm mg}}$ of a trader ${\overline{T}}$ against the market ${\overline{\mathbb{P}}}$ is 

$$
{\|{\overline{T}}({\overline{\mathbb{P}}})\|_{\rm mg}} := \sum_{n\in {{\mathbb{N}}^+}}{\|T_n({\overline{\mathbb{P}}})\|_{\rm mg}} \equiv \sum_{n\in {{\mathbb{N}}^+}} \sum_{\phi\in\mathcal{S}}|T_n[\phi]({\overline{\mathbb{P}}})|.
$$

_

The magnitude of ${\overline{T}}$ is the total number of shares it trades (buys or sells) over all time.

Now we define what it means for a trader to increase its net value by a substantial fraction of its investment, i.e., its magnitude.

**Definition 114** ($\varepsilon$ Return on Investment). _For $\varepsilon>0$, we say that a trader ${\overline{T}}$ trading against ${\overline{\mathbb{P}}}$ has _$\varepsilon$ return on investment_ or _$\varepsilon$\-ROI_ if, for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 

$$
\lim_{n \to \infty} \mathbb{W}\left(\sum_{i \leq n} T_i ({\overline{\mathbb{P}}})\right) \geq \varepsilon {\|{\overline{T}}({\overline{\mathbb{P}}})\|_{\rm mg}}.
$$

_

In words, a trader ${\overline{T}}$ has $\varepsilon$\-ROI if, in the limit of time and deduction, the value of its holdings is, in every world, at least $\varepsilon$ times its total investment ${\|{\overline{T}}({\overline{\mathbb{P}}})\|_{\rm mg}}$. Note that this does not merely say that ${\overline{T}}$ recoups at least an $\varepsilon$ fraction of its original cost; rather, the net value is guaranteed in all worlds consistent with $\Gamma$ to have increased by an $\varepsilon$ fraction of the magnitude ${\|{\overline{T}}({\overline{\mathbb{P}}})\|_{\rm mg}}$ of ${\overline{T}}$’s trades.

Recall from Definition 28 that a sequence ${\overline{\alpha}}$ of rationals is ${\overline{\mathbb{P}}}$\-generable if there is some e.c. $\mathcal{E\!F}$\-progression ${\overline{{\alpha^\dagger}}}$ such that ${\alpha_n^\dagger} ({\overline{\mathbb{P}}})= \alpha_n$ for all $n$.

**Lemma 115** (No Repeatable $\varepsilon$\-ROI ). _Let ${\overline{\mathbb{P}}}$ be a logical inductor with respect to some deductive process ${\overline{D}}$, and let $({\overline{T}}^k)_{k\in{\mathbb{N}}^+}$ be an efficiently emulatable sequence of traders (Definition 112). Suppose that for some fixed $\varepsilon>0$, each trader ${\overline{T}}^k$ has $\varepsilon$\-ROI. Suppose further that there is some ${\overline{\mathbb{P}}}$\-generable sequence ${\overline{\alpha}}$ such that for all $k$, 

$$
{\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}} = \alpha_k.
$$

 Then 

$$
\lim_{k \rightarrow \infty} \alpha_k = 0.
$$

_

In words, this says roughly that there is no efficient, repeatable method for producing a substantial guaranteed return on an investment. The condition that ${\overline{\alpha}}$ is ${\overline{\mathbb{P}}}$\-generable will help with the budgeting done by the trader that emulates the sequence $({\overline{T}}^k)_k$.

##### Proof strategy. ^proof-strategy

We will construct a trader ${\overline{T}}$ that emulates the sequence $({\overline{T}}^k)$ in a manner such that if the traders ${\overline{T}}^k$ did not make trades of vanishing limiting value, then our trader ${\overline{T}}$ would accrue unbounded profit by repeatedly making investments that are guaranteed to pay out by a substantial amount. Very roughly, on time $n$, ${\overline{T}}$ will sum together the trades $T^k_n$ made by all the ${\overline{T}}^k$ with $k\le n$. In this way, ${\overline{T}}$ will accrue all the profits made by each of the ${\overline{T}}^k$.

The main problem we have to deal with is that ${\overline{T}}$ risks going deeper and deeper into debt to finance its investments, as discussed before the proof of Theorem 118 (Convergence) in Section [[#^convergence|6.1]]. That is, it may be that each ${\overline{T}}^k$ makes an investment that takes a very long time for all the worlds $\mathbb{W}\in\mathcal{PC}(D_n)$ plausible at time $n$ to value highly. In the meanwhile, ${\overline{T}}$ continues to spend money buying shares and taking on risk from selling shares that might plausibly demand a payout. In this way, despite the fact that each of its investments will eventually become profitable, ${\overline{T}}$ may have holdings with unboundedly negative plausible value.

To remedy this, we will have our trader ${\overline{T}}$ keep track of its “debt” and of which investments have already paid off, and then scale down new traders ${\overline{T}}^k$ so that ${\overline{T}}$ maintains a lower bound on the plausible value of its holdings. Roughly speaking, ${\overline{T}}$ at time $n$ checks whether the current holdings of ${\overline{T}}^k$ are guaranteed to have a positive value in all plausible worlds, for each $k\le n$. Then ${\overline{T}}$ sums up the total magnitudes $\alpha_k$ of all the trades ever made by those ${\overline{T}}^k$ whose trades are not yet guaranteed to be profitable. This sum is used to scale down all trades made by ${\overline{T}}^n$, so that the total magnitude of the unsettled investments made by ${\overline{T}}$ will remain bounded.

##### Proof of Lemma 115. ^proof-of-lemma-115

_Proof._ We now prove Lemma 115.

We can assume without loss of generality that each $\alpha_n \leq 1$ by dividing ${\overline{T}}^k$’s trades by $\max(1, \alpha_k)$.

##### Checking profitability of investments. ^checking-profitability-of-investments

At time $n$, our trader ${\overline{T}}$ runs a (possibly very slow) search process to enumerate traders ${\overline{T}}^k$ from the sequence $({\overline{T}}^k)_k$ that have made trades that are already guaranteed to be profitable, as judged by what is plausible according to the deductive process ${\overline{D}}$ with respect to which ${\overline{\mathbb{P}}}$ is a logical inductor. That is, ${\overline{T}}$ runs a search for pairs of numbers $k, m\in{\mathbb{N}}^+$ such that: 

$$
\begin{align*}
\sum_{i \leq m} {\|T^k_i({\overline{\mathbb{P}}})\|_{\rm mg}} &\geq (1 - \varepsilon/3) \alpha_k  &\textrm{ (few future trades), and } \\
\inf_{\mathbb{W}\in\mathcal{PC}(D_m)}\mathbb{W}\left( {\textstyle \sum_{i \leq m}  T^k_i({\overline{\mathbb{P}}})
}\right) &\geq (2\varepsilon /3) \alpha_k & \textrm{ (guaranteed profit). }
\end{align*}
$$

 If the trader ${\overline{T}}^k$ has few future trades and guaranteed profit at time $m$ then we say that the trader’s holdings have matured. We denote the least such $m$ by $m(k)$.

The first condition (few future trades) says that ${\overline{T}}^k$ has made trades of total magnitude at least $(1 - \varepsilon/3) \alpha_k$ after time $k$ up until time $m$. By the assumption that ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}}= \alpha_k$, for each $k$ there is some time step $m$ such that this condition holds. By that same assumption, ${\overline{T}}^k$ will make trades of total magnitude at most $(\varepsilon/3)\alpha_k$ in all time steps after $m$.

The second condition (guaranteed profit) says that the minimum value plausible at time $m$ of all trades made by ${\overline{T}}^k$ up until time $m$ is at least $(2\varepsilon /3) \alpha_k$. By the assumption that ${\overline{T}}^k$ has $\varepsilon$\-ROI, i.e., that the minimum value of ${\overline{T}}^k$ is eventually at least $\varepsilon {\|T^k_k\|_{\rm mg}}$, the condition of guaranteed profit will hold at some $m$.

The idea is that, since ${\overline{T}}^k$ will trade at most $(\varepsilon/3) \alpha_k$ shares after $m$ and the holdings of ${\overline{T}}^k$ from trades up until the current time have minimum plausible value at least $(2\varepsilon /3) \alpha_k$, it is guaranteed that the holdings of ${\overline{T}}^k$ at any time after $m$ will have minimum plausible value at least $(\varepsilon/3) \alpha_k$. This will allow our trader ${\overline{T}}$ to “free up” funds allocated to emulating ${\overline{T}}^k$, in the sense that there is no longer ever any plausible net downside to the holdings from trades made by ${\overline{T}}^k$.

##### Definition of the trader $\boldsymbol{{\overline{T}}}$. ^definition-of-the-trader

For fixed $k$ and $m$, these two conditions refer to specific individual computations (namely $D_m$, the $T^k_i({\overline{\mathbb{P}}})$ for $i \leq m$, and $\alpha_k$). On time step $n$, for all $k,j \leq n$, our trader ${\overline{T}}$ sets Boolean variables $\textrm{open}(k,j) :=0$ if it is verified in $j$ steps of computation that the holdings of ${\overline{T}}^k$ have matured; and $\textrm{open}(k,j) :=1$ if ${\overline{T}}^k$ has open investments. Since the holdings of each ${\overline{T}}^k$ will eventually mature, for all $k$ there is some $n$ such that $\textrm{open}(k,n) = 0$.

Let ${\overline{{\alpha^\dagger}}}$ be an e.c. $\mathcal{E\!F}$ progression such that for each $n$ we have ${\alpha_n^\dagger} ({\overline{\mathbb{P}}})= \alpha_n$. Then ${\overline{T}}$ outputs the trading strategy 

$$
T_n := \sum_{k\leq n} {\beta_k^\dagger} \cdot T^k_n,
$$

 where the ${\beta_k^\dagger}$ are defined recursively by 

$$
{\beta_k^\dagger} := 1- \sum_{i < k} \textrm{open}(i,k) {\beta_i^\dagger} {\alpha_i^\dagger} .
$$

 That is, the machine computing ${\overline{T}}$ outputs the definitions of the budget variables ${\beta_k^\dagger}$ for each $k \leq n$, and then lists the trades 

$$
\textrm{return }\phi := \sum_{k\leq n} {\beta_k^\dagger} T^k_n[\phi]
$$

 for each $\phi$ listed by any of the trades $T^k_n$ for $k \leq n$. As shorthand, we write $\beta_k := {\beta_k^\dagger} ({\overline{\mathbb{P}}})$. Notice that since $({\overline{T}}^k)_k$ is efficiently emulatable, we have $\forall k: \forall i<k: T^k_i \equiv 0$, and therefore 

$$
\forall n: T_n ({\overline{\mathbb{P}}})= \sum_{k\in {{\mathbb{N}}^+}} \beta_k T^k_n ({\overline{\mathbb{P}}}).
$$

 Note that each $\textrm{open}(i,k)$ is pre-computed by the machine that outputs our trader ${\overline{T}}$ and then is encoded as a constant in the expressible feature ${\beta_k^\dagger}$. The trade coordinate $T_n[\phi]$ is an expressible feature because the ${\beta_k^\dagger}$ and $T^k_n[\phi]$ are expressible features.

##### Budgeting the traders $\boldsymbol{{\overline{T}}^k}$. ^budgeting-the-traders-boldsymbol

Since we assumed each $\alpha_k \leq 1$, it follows from the definition of the budget variable ${\beta_k^\dagger}$ that 

$$
\beta_k \alpha_k  \leq  1- \sum_{i < k} \textrm{open}(i,k) \beta_i \alpha_i,
$$

 and then $\beta_k$ is used as the constant scaling factor for ${\overline{T}}^k$ in the sum defining ${\overline{T}}$’s trades. In this way, we maintain the invariant that for any $n$, 

$$
\sum_{k\leq n} \textrm{open}(k,n) \beta_k \alpha_k \leq 1.
$$

 Indeed, by induction on $k$, using the fact that $\textrm{open}(i,n)$ implies $\textrm{open}(i,m)$ for $m\ge n$, we have $\beta_k \geq 0$ and the above invariant holds.

In words, this says that out of all the traders ${\overline{T}}^k$ with investments still open at time $n$, the sum of the magnitudes $\beta_k \alpha_k$ of their total investments (as budgeted by the $\beta_k$) is bounded by 1.

##### Analyzing the value of $\boldsymbol{{\overline{T}}}$’s holdings. ^analyzing-the-value-of

Now we lower bound the value of the holdings of ${\overline{T}}$ from trades against the market ${\overline{\mathbb{P}}}$. Fix any time step $n$ and world $\mathbb{W}\in\mathcal{PC}(D_n)$ plausible at time $n$. Then we have that the value of ${\overline{T}}$’s holdings at time $n$ is 

$$
\begin{align*}
  \mathbb{W}( {\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}}) })
&= \sum_{k\leq n}   \mathbb{W}( {\textstyle \sum_{i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) })
\end{align*}
$$

by linearity and by definition of our trader ${\overline{T}}$;

$$
\begin{align*}
&= \sum_{\substack{k\leq n\\  \textrm{open}(k,n)}}   \mathbb{W}( {\textstyle \sum_{i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) })
+  \sum_{\substack{k\leq n\\  \lnot \textrm{open}(k,n)}}   \mathbb{W}( {\textstyle \sum_{i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) })
\end{align*}
$$

 again by linearity. We analyze the first term, the value of the holdings that have not yet matured, as follows: 

$$
\begin{align*}
\sum_{\substack{k\leq n\\  \textrm{open}(k,n)}}   \mathbb{W}( {\textstyle \sum_{i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) })
&\geq -\sum_{\substack{k\leq n\\  \textrm{open}(k,n)}}   \beta_k \sum_{i \leq n} {\|T^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}}
\\
&\geq -\sum_{\substack{k\leq n\\  \textrm{open}(k,n)}}   \beta_k \sum_{i \in {\mathbb{N}}^+} {\|T^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}}
\\
&= -\sum_{k\leq n  }  \textrm{open}(k,n) \beta_k \alpha_k \\
&\geq -1 ,
\end{align*}
$$

 by the previous discussion of the $\beta_k$. In short, the $\beta_k$ were chosen so that the total magnitude of all of ${\overline{T}}$’s holdings from trades made by any ${\overline{T}}^k$ that haven’t yet matured stays at most 1, so that its plausible value stays at least $-1$.

Now we analyze the second term in the value of ${\overline{T}}$’s holdings, representing the value of the holdings that have already matured, as follows: 

$$
\begin{align*}
  & \sum_{\substack{k\leq n\\  \lnot\textrm{open}(k,n)}}   \mathbb{W}( {\textstyle \sum_{i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) })
  \\
=& \sum_{\substack{k\leq n\\  \lnot\textrm{open}(k,n)}}   
  \left( \mathbb{W}( {\textstyle \sum_{i \leq m(k)} \beta_k T^k_i({\overline{\mathbb{P}}}) }) +
  \mathbb{W}( {\textstyle \sum_{m(k) < i \leq n} \beta_k T^k_i({\overline{\mathbb{P}}}) }) \right)
\end{align*}
$$

where $m(k)$ is minimal such that ${\overline{T}}^k$ has guaranteed profit and makes few future trades at time $m(k)$, as defined above;

$$
\begin{align*}
&\geq
  \sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}
  \left(\beta_k (2\varepsilon/3) \alpha_k - \sum_{ i>  m(k) } \beta_k {\| T^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}} \right)
\end{align*}
$$

since by definition of $m(k)$ and the guaranteed profit condition, the value of the holdings of ${\overline{T}}^k$ from its trades up until time $m(k)$ is at least $(2\varepsilon/3)\alpha_k$ in any world in $D_n$;

$$
\begin{align*}
&\geq
  \sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}
\left(\beta_k (2\varepsilon/3) \alpha_k -\beta_k (\varepsilon/3) \alpha_k \right)
\end{align*}
$$

since ${\overline{T}}^k$ is guaranteed to make trades of magnitude at most $(\varepsilon /3) \alpha_k$ after time $m(k)$;

$$
\begin{align*}
& = \sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}  \beta_k (\varepsilon/3)\alpha_k.
\end{align*}
$$

Completing our analysis, we have a lower bound on the value in $\mathbb{W}$ of the holdings of ${\overline{T}}$ at time $n$: 

$$
\mathbb{W}( {\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}}) })   \geq -1 +
\sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}  \beta_k (\varepsilon/3) \alpha_k.
$$

##### $\boldsymbol{{\overline{T}}}$ exploits $\boldsymbol{{\overline{\mathbb{P}}}}$ unless $\boldsymbol{{\overline{\alpha}}}$ vanishes. ^boldsymbol-overline-t-exploits

Since ${\overline{T}}$ is an efficient trader and ${\overline{\mathbb{P}}}$ is a logical inductor, ${\overline{T}}$ does not exploit ${\overline{\mathbb{P}}}$. That is, the set 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T_i} ({\overline{\mathbb{P}}}) \right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n)
\right\}
$$

 is bounded above, since it is bounded below by $-1$ by the above analysis. In words, the plausible value of ${\overline{T}}$’s holdings is always at least $-1$, so by the logical induction criterion it cannot go to infinity. Therefore, again by the above analysis, we must have 

$$
\lim_{n \to\infty} \sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}  \beta_k (\varepsilon/3) \alpha_k <\infty.
$$

 As shown above, for any $k$ the conditions for $\lnot\textrm{open}(k,n)$ will eventually be met by all sufficiently large $n$. Thus 

$$
\lim_{n \to\infty} \sum_{\substack{k\leq n\\ \lnot\textrm{open}(k,n)}}  \beta_k (\varepsilon/3) \alpha_k =
\sum_{k}  (\varepsilon/3) \beta_k \alpha_k <\infty.
$$

 Now we show that $\lim_{k \to\infty} \alpha_k = 0$. Suppose by way of contradiction that for some $\delta \in (0, 1)$, $\alpha_k > \delta$ for infinitely many $k$, but nevertheless for some sufficiently large time step $n$, we have 

$$
\sum_{i>n} \beta_i \alpha_i < 1/2.
$$

 Recall that for each $i\leq n$, at some time $n(i)$, $\textrm{open}(i,n(i)) =0$ verifies that the holdings of ${\overline{T}}^i$ have matured. Let $N$ be any number greater than $n(i)$ for all $i \leq n$. Then 

$$
\begin{align*}
\sum_{i < N} \textrm{open}(i,N) \beta_i \alpha_i
& = \sum_{i \leq n}0 \cdot \beta_i \alpha_i + \sum_{n<i < N} \textrm{open}(i,N) \beta_i \alpha_i\\
& \leq 0 + \sum_{n<i < N} \beta_i \alpha_i\\
& \leq 1/2.
\end{align*}
$$

 So for infinitely many sufficiently large $k$ we have 

$$
\begin{align*}
  \alpha_k \beta_k
  &= \alpha_k \left(1- \sum_{i < k} \textrm{open}(i,k) \beta_i \alpha_i \right) \\
  &\geq \alpha_k (1 - 1/2) \\
  &\geq \delta/2.
\end{align*}
$$

 Thus 

$$
\sum_k (\varepsilon/3) \beta_k \alpha_k =\infty,
$$

 contradicting that this sum is bounded. Therefore in fact $\alpha_k \eqsim_k 0$, as desired. ◻

### Affine Preemptive Learning ^affine-preemptive-learning

**Theorem 116** (Affine Preemptive Learning). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\to\infty} \mathbb{P}_n(A_n)= \liminf_{n\rightarrow\infty}\sup_{m\geq n} \mathbb{P}_m(A_n)
$$

 and 

$$
\limsup_{n\to\infty} \mathbb{P}_n(A_n)= \limsup_{n\rightarrow\infty}\inf_{m\geq n} \mathbb{P}_m(A_n) \ .
$$

_

##### Proof strategy: buying combinations that will appreciate, and ROI. ^proof-strategy-buying-combinations

The inequality 

$$
\liminf_{n\to\infty}\mathbb{P}_{n}(A_{n}) \ge \liminf_{n\rightarrow\infty}\sup_{m \ge n}\mathbb{P}_{m}(A_{n})
$$

 states roughly that $\mathbb{P}_n$ cannot infinitely often underprice the ${\mathbb{R}}$\-combination $A_{n}$ by a substantial amount in comparison to any price $\mathbb{P}_{m}(A_{n})$ assigned to $A_{n}$ by $\mathbb{P}_m$ at any future time $m\ge n$.

Intuitively, if the market ${\overline{\mathbb{P}}}$ did not satisfy this inequality, then ${\overline{\mathbb{P}}}$ would be exploitable by a trader that buys the ${\mathbb{R}}$\-combination $A_{n}$ when its price is low, and then sells it back when, inevitably, the price is substantially higher. If we have sold back all our shares in some sentence $\phi$, then there is no contribution, positive or negative, to our net value from our $\phi$\-shares (as opposed to their prices); for every share we owe, there is a matching share that we hold. So if we buy low and sell high, we have made a profit off of the price differential, and once the inter-temporal arbitrage is complete we have not taken on any net risk from our stock holdings.

The fact that we can accrue stock holdings that we are guaranteed to eventually sell back for more than their purchase price is not sufficient to exploit the market. It may be the case that at every time $n$ we spend $\text{\textdollar} 1$ on some ${\mathbb{R}}$\-combination that we eventually sell back at $\text{\textdollar} 2$, but not until time $4n$. (That is, until time $4n$, the price remains low.) Then at every time $n$ we owe $-\text{\textdollar} n$ in cash, but only have around $\text{\textdollar} 2(n/4)$ worth of cash from shares we have sold off, for a net value of around $-n/2$. Thus we have net value unbounded below and hence do not exploit the market, despite the fact that each individual investment we make is eventually guaranteed to be profitable.

To avoid this obstacle, we will apply the $\varepsilon$\-return on investment lemma (Lemma 115) to the sequence of traders $({\overline{T}}^k)_k$ that enforce the inequality at time $k$ as described above. That is, ${\overline{T}}^k$ myopically “keeps ${\overline{\mathbb{P}}}$ sensible about ${\overline{A}}$” at time $k$ by buying the ${\mathbb{R}}$\-combination $A_k$ described above if that ${\mathbb{R}}$\-combination is under-priced at time $k$, and otherwise ${\overline{T}}^k$ does nothing. The ROI Lemma guarantees that the inequality cannot infinitely often fail substantially, or else this sequence would have $\delta$\-ROI for some $\delta$.

The main technical difficulty is that we have to buy the ${\mathbb{R}}$\-combination $A_{n}$ at time $n$ (if it is underpriced), wait for the price of the combination to increase substantially, and then sell it off, possibly over multiple time steps. The traders ${\overline{T}}^k$ will therefore have to track what fraction of their initial investment they have sold off at any given time.

##### Proof. ^proof

_Proof._ We show the first equality; the second equality follows from the first by considering the negated sequence $(-A_n)_n$.

Since for all $n$ we have $\sup_{m \ge n}\mathbb{P}_{m}(A_{n}) \ge \mathbb{P}_{n}(A_{n})$, the corresponding inequality in the limit infimum is immediate.

Suppose for contradiction that the other inequality doesn’t hold, so that 

$$
\liminf_{n\to\infty}\mathbb{P}_{n}(A_{n}) < \liminf_{n\rightarrow\infty}\sup_{m \ge n}\mathbb{P}_{m}(A_{n})\ .
$$

 Then there are rational numbers $\varepsilon>0$ and $b$ such that we have 

$$
\liminf_{n\to\infty} \mathbb{P}_{n}(A_{n})<  b- \varepsilon<  b+ \varepsilon<\liminf_{n\to\infty}
\sup_{m \ge n}\mathbb{P}_{m}(A_{n})\ .
$$

 Therefore we can fix some sufficiently large $s_\varepsilon$ such that:

-   for all $n>s_\varepsilon$, we have $\sup_{m \ge n}\mathbb{P}_{m}(A_{n}) > b+ \varepsilon$, and
    
-   for infinitely many $n> s_\varepsilon$, we have $\mathbb{P}_{n}(A_{n})<b- \varepsilon$.
    

We will assume without loss of generality that each ${\|A_n\|_{\rm mg}} \leq 1$; they are assumed to be bounded, so they can be scaled down appropriately.

##### An efficiently emulatable sequence of traders. ^an-efficiently-emulatable-sequence

Let ${\overline{{A^\dagger}}}$ be an $\mathcal{E\!F}$\-combination progression such that ${A_n^\dagger}({\overline{\mathbb{P}}}) = A_n$ for all $n$. We now define our sequence of traders $({\overline{T}}^k)_k$. For $k \leq s_\varepsilon$, define ${\overline{T}}^k$ to be the zero trading strategy at all times $n$.

For $k > s_\varepsilon$, define $T^k_n$ to be the zero trading strategy for $n < k$, and define $T^k_k$ to be the trading strategy 

$$
T^k_k :=
{\rm Under}_k
\cdot \left( A^\dagger_{k} - A^{\dagger* k}_{k}\right)\ ,
$$

 where 

$$
{\rm Under}_k :=
  \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( A^{\dagger* k}_{k} < b- \varepsilon/2
\right) \ .
$$

 This is a buy order for the ${\mathbb{R}}$\-combination $A_{k}$, scaled down by the continuous indicator function ${\rm Under}_k$ for the event that $\mathbb{P}_k$ has underpriced that ${\mathbb{R}}$\-combination at time $k$. Then, for times $n>k$, we define ${\overline{T}}^k$ to submit the trading strategy 

$$
T^k_n :=  
-F_n  \cdot
\left({\rm Under}_k \cdot \left( A^\dagger_{k}  - A^{\dagger* k}_{k}  \right)\right) \ ,
$$

 where we define $F_n \geq 0$ recursively in the previous fractions $F_i$: 

$$
\begin{align*}
F_n &:=
{\rm Over}_n^k \cdot
\left( 1- \sum_{k<i<n} F_i \right) ,
\end{align*}
$$

 using the continuous indicator ${\rm Over}_n^k := \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( A^{\dagger* n}_{k} > b+ \varepsilon/2 \right)$ of the ${\mathbb{R}}$\-combination being overpriced at time $n$.

In words, $T^k_n$ is a sell order for the ${\mathbb{R}}$\-combination $A_{k}$, scaled down by the fraction ${\rm Under}_k$ of this ${\mathbb{R}}$\-combination that ${\overline{T}}^k$ purchased at time $k$, and also scaled down by the fraction $F_n$ of the original purchase $T^k_k$ that will be sold on this time step. That is, $\sum_{k<i<n} F_i$ the total fraction of the original purchase ${\rm Under}_k \cdot A_k$ that has already been sold off on all previous rounds since time $k$. Then $T^k_n$ sells off the remaining fraction $1- \sum_{k<i<n} F_i$ of the ${\mathbb{R}}$\-combination ${\rm Under}_k \cdot A_k$, scaled down by the extent ${\rm Over}_n^k$ to which $A_k$ is overpriced at time $n$.

Notice that since ${\rm Over}_i^k\in [0,1]$ for all $i$, by induction on $n$ we have that $\sum_{k<i\leq n} F_i \leq 1$ and $F_n \ge 0$. This justifies thinking of the $F_i$ as portions of the original purchase being sold off.

By assumption, the $\mathcal{E\!F}$\-combination progression ${\overline{A^\dagger}}$ is e.c. Also, each trader ${\overline{T}}^k$ does not trade before time $k$. Therefore the sequence of traders $({\overline{T}}^k)_k$ is efficiently emulatable (see [[#^dynamic-programming-for-traders|8.2.2]] on dynamic programming). (The constant $s_\varepsilon$ before which the ${\overline{T}}^{k\le s_\varepsilon}$ make no trades can be hard-coded in the efficient enumeration.)

##### $\boldsymbol{(\varepsilon/2)}$ return on investment for $\boldsymbol{{\overline{T}}^k}$. ^boldsymbol-varepsilon-2-return

Now we show that each ${\overline{T}}^k$ has $(\varepsilon/2)$\-ROI; i.e., for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 

$$
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right)
\geq
(\varepsilon/2)
{\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}} .
$$

 In words, this says that the trades made by ${\overline{T}}^k$ across all time are valued positively in any $\mathbb{W}\in\mathcal{PC}(\Gamma)$, by a fixed fraction $(\varepsilon/2)$ of the magnitude of ${\overline{T}}^k$. For $k \leq s_\varepsilon$, this is immediate since ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}=0$ by definition.

For each $k> s_\varepsilon$, by definition ${\overline{T}}^k$ makes a trade of magnitude ${\|{\overline{T}}^k_k ({\overline{\mathbb{P}}})\|_{\rm mg}} = {\rm Under}_k({\overline{\mathbb{P}}}) \cdot {\| A_k \|_{\rm mg}}$, followed by trades of magnitude 

$$
\sum_{n>k} F_n {\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}} \leq    {\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}\ ,
$$

 by the earlier comment that the $F_n$ are non-negative and sum to at most 1. Furthermore, by assumption, there is some $m>k$ such that $\mathbb{P}_{m}(A_{k})  > b+ \varepsilon$. At that point, ${\rm Over}_m^k ({\overline{\mathbb{P}}})= 1$, so that $F_m({\overline{\mathbb{P}}})= \left(1 - \sum_{k<i<m}F_i({\overline{\mathbb{P}}})\right)$; intuitively this implies that at time $m$, ${\overline{T}}^k$ will sell off the last of its stock holdings from trades in $A_{k}$. Formally we have 

$$
\begin{align*}
\sum_{k< i \leq m} {\|{\overline{T}}^k_i({\overline{\mathbb{P}}})\|_{\rm mg}}
&= \left(F_m({\overline{\mathbb{P}}})+  \sum_{k<i <m} F_i({\overline{\mathbb{P}}})\right) \cdot
{\rm Under}_k({\overline{\mathbb{P}}})\cdot {\|A_k \|_{\rm mg}}\\
&= {\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}\ .
\end{align*}
$$

 Furthermore, for all times $M>m$ we have $F_M ({\overline{\mathbb{P}}})= 0$, so that $T^k_M ({\overline{\mathbb{P}}})\equiv 0$. Therefore ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}= \sum_{k\leq i \leq n} {\|{\overline{T}}^k_i({\overline{\mathbb{P}}})\|_{\rm mg}}= 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$.

Now fix any world $\mathbb{W}\in\mathcal{PC}(\Gamma)$. Then the limiting value of ${\overline{T}}^k$ in $\mathbb{W}$ is: 

$$
\begin{align*}
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right)
&= \mathbb{W}\left( {\textstyle \sum_{k\leq i \leq m} T^k_i({\overline{\mathbb{P}}})}\right)
\end{align*}
$$

since by the above analysis, $T^k_i$ is the zero trade for $i<k$ and for $i>m$;

$$
\begin{align*}
&= \mathbb{W}\left( {\textstyle T^k_k({\overline{\mathbb{P}}}) + \sum_{k< i \leq m} T^k_i({\overline{\mathbb{P}}})}\right)\\
&= \;\; {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\mathbb{W}\left( {\textstyle \; A_{k}-  \mathbb{P}_k(A_{k})\; } \right) \\
&\;\;\; + {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\mathbb{W}\left( {\textstyle
\sum_{k< i \leq m} (-F_i({\overline{\mathbb{P}}})) \cdot \left(\; A_{k}-  \mathbb{P}_i(A_{k})\; \right) }\right)
\end{align*}
$$

by linearity, by the definition of the trader ${\overline{T}}^k$, and since by definition $A^{\dagger* k}_{k}({\overline{\mathbb{P}}}) =  \mathbb{P}_k(A^\dagger_{k} ({\overline{\mathbb{P}}})) = \mathbb{P}_k(A_{k})$. Note that the prices $\mathbb{P}_i(A_{k})$ of $A_k$ in the summation change with the time step $i$. Then

$$
\begin{align*}
&= \;\; {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\mathbb{W}\left( {\textstyle \; A_{k}-  A_{k}\; } \right) \\
&\;\;\; + {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\mathbb{W}\left( {\textstyle -\mathbb{P}_k(A_{k}) +
\sum_{k< i \leq m} F_i \cdot  \mathbb{P}_i(A_{k}) }\right)\\
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right) &=  {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\left( {\textstyle -\mathbb{P}_k(A_{k}) +
\sum_{k< i \leq m} F_i \cdot  \mathbb{P}_i(A_{k}) }\right)\ ,
\end{align*}
$$

 using linearity to rearrange the terms in the first and second lines, and using that $\sum_{k< i \leq m} F_i = 1$ as shown above. Note that this last quantity does not contain any stock holdings whose value depends on the world; intuitively this is because ${\overline{T}}^k$ sold off exactly all of its initial purchase. The remaining quantity is the difference between the price at which the ${\mathbb{R}}$\-combination $A_k$ was bought and the prices at which it was sold over time, scaled down by the fraction ${\rm Under}_k ({\overline{\mathbb{P}}})$ of $A_k$ that ${\overline{T}}^k$ purchased at time $k$.

If at time step $k$ the ${\mathbb{R}}$\-combination $A_k$ was not underpriced, i.e., ${\rm Under}_k ({\overline{\mathbb{P}}})= 0$, then 

$$
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right) = 0 = (\varepsilon/2){\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}\ ,
$$

 as desired. On the other hand, suppose that ${\rm Under}_k({\overline{\mathbb{P}}})  > 0$. That is, 

$$
\operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( \mathbb{P}_k(A_k) < b- \varepsilon/2
\right) >0 \ ,
$$

 i.e., $A_k$ was actually underpriced at time $k$. Therefore 

$$
\begin{align*}
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right)
&\geq  {\rm Under}_k({\overline{\mathbb{P}}}) \cdot
\left( {\textstyle -(b- \varepsilon/2)  +
\sum_{k< i \leq m} F_i ({\overline{\mathbb{P}}})\cdot ( b+ \varepsilon/2)
}\right)
\end{align*}
$$

since when $F_i ({\overline{\mathbb{P}}})>0$ we have ${\rm Over}_n^k({\overline{\mathbb{P}}})>0$ and hence $\mathbb{P}_i(A_{k})  \geq b+ \varepsilon/2$, and using the fact that ${\rm Under}_k({\overline{\mathbb{P}}})$ is nonnegative;

$$
\begin{align*}
&= {\rm Under}_k({\overline{\mathbb{P}}}) \cdot \varepsilon\\
&\geq (\varepsilon/2){\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}\ ,
\end{align*}
$$

 since 

$$
{\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}} = 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}} = 2\cdot{\rm Under}_k({\overline{\mathbb{P}}}) \cdot {\|A_k\|_{\rm mg}} \leq 2\cdot {\rm Under}_k({\overline{\mathbb{P}}})
$$

 Thus ${\overline{T}}^k$ has $(\varepsilon/2)$\-ROI.

##### Deriving a contradiction. ^deriving-a-contradiction

We have shown that the sequence of traders $({\overline{T}}^k)_k$ is bounded, efficiently emulatable, and has $(\varepsilon/2)$\-return on investment. The remaining condition to Lemma 115 states that for all $k$, the magnitude ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}$ of all trades made by ${\overline{T}}^k$ must equal $\alpha_k$ for some ${\overline{\mathbb{P}}}$\-generable ${\overline{\alpha_k}}$. This condition is satisfied for $\alpha_k := 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$, since as shown above, ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}} = 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$.

Therefore we can apply Lemma 115 (the ROI lemma) to the sequence of traders $({\overline{T}}^k)_k$. We conclude that $\alpha_k \eqsim_k 0$. Recall that we supposed by way of contradiction that the ${\mathbb{R}}$\-combinations in ${\overline{A_k}}$ are underpriced infinitely often. That is, for infinitely many days $k$, $\mathbb{P}_{k}(A_{k})< b- \varepsilon$. But for any such $k>s_\varepsilon$, ${\overline{T}}^k_k$ purchases a full ${\mathbb{R}}$\-combination $A_k$, and then sells off the resulting stock holdings for at least $b+ \varepsilon/2$, at which point ${\overline{T}}^k$ has profited by at least $\varepsilon$. More precisely, for these $k$ we have 

$$
{\rm Under}_k({\overline{\mathbb{P}}})
= \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( \mathbb{P}_{k}(A_{k})  < b- \varepsilon/2\right) = 1 .
$$

 Since 

$$
\alpha_k = 2 {\|{\overline{T}}^k_k ({\overline{\mathbb{P}}})\|_{\rm mg}} = 2 \cdot {\rm Under}_k ({\overline{\mathbb{P}}})\cdot {\|A_k\|_{\rm mg}} = 2 {\|A_k\|_{\rm mg}}
$$

 and ${\|A_k\|_{\rm mg}} \geq \varepsilon/2$ (since $\mathbb{P}_m(A_k) - \mathbb{P}_k(A_k) \geq  \varepsilon$ for some $m$), we have $\alpha_k \geq \varepsilon$ for infinitely many $k$, which contradicts $\alpha_k \eqsim_k 0$. ◻

### Preemptive Learning ^preemptive-learning

**Theorem 117** (Preemptive Learning). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
\liminf_{n\to\infty} \mathbb{P}_n(\phi_n) = \liminf_{n\to\infty} \sup_{m\ge n} \mathbb{P}_m(\phi_n).
$$

 Furthermore, 

$$
\limsup_{n\to\infty} \mathbb{P}_n(\phi_n) = \limsup_{n\to\infty}\inf_{m\ge n} \mathbb{P}_m(\phi_n).
$$

_

_Proof._ This is a special case of Theorem 116 (Affine Preemptive Learning), using the combination $A_n := \phi_n$. ◻

### Convergence ^convergence-2

**Theorem 118** (Convergence). _The limit ${\mathbb{P}_\infty:\mathcal{S}\rightarrow[0,1]}$ defined by 

$$
\mathbb{P}_\infty(\phi) := \lim_{n\rightarrow\infty} \mathbb{P}_n(\phi)
$$

 exists for all $\phi$._

_Proof._ By Theorem 117 (Preemptive Learning), 

$$
\begin{align*}
\liminf_{n \to \infty} \mathbb{P}_n(\phi)
&= \liminf_{n \to \infty} \sup_{m \geq n} \mathbb{P}_m(\phi) \\
  &= \lim_{k \to \infty} \inf_{n \geq k} \sup_{m \geq n} \mathbb{P}_m(\phi) \\
&= \limsup_{n \to \infty} \mathbb{P}_n(\phi).
\end{align*}
$$

 Since the $\liminf$ and $\limsup$ of $\mathbb{P}_n(\phi)$ are equal, the limit exists. ◻

### Persistence of Affine Knowledge ^persistence-of-affine-knowledge

**Theorem 42** (Persistence of Affine Knowledge). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}\mathbb{P}_m(A_n)= \liminf_{n\to\infty}\mathbb{P}_\infty(A_n)
$$

 and 

$$
\limsup_{n\rightarrow\infty}\sup_{m\geq n}\mathbb{P}_m(A_n)=\limsup_{n\to\infty}\mathbb{P}_\infty(A_n).
$$

_

##### Proof strategy: keeping $\boldsymbol{\mathbb{P}_m}$ reasonable on all $\boldsymbol{\mathcal{AF}_{n \le m}}$. ^proof-strategy-keeping-boldsymbol

In the same vein as the proof in Appendix [[#^affine-preemptive-learning|9.2]] of Theorem 116, the inequality 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}\mathbb{P}_m(A_n) \ge  \liminf_{n\to\infty}\mathbb{P}_\infty(A_n)
$$

 says roughly that $\mathbb{P}_m$ cannot underprice the ${\mathbb{R}}$\-combination $A_{n}$ by a substantial amount infinitely often, where the ${\mathbb{R}}$\-combination is “underpriced” in comparison to the value of the ${\mathbb{R}}$\-combination as judged by the limiting belief state $\mathbb{P}_\infty$.

As the proof of the present theorem is quite similar to the proof of Theorem 116, we will highlight the differences in this proof, and otherwise give a relatively terse proof.

Intuitively, if the market ${\overline{\mathbb{P}}}$ did not satisfy the present inequality then ${\overline{\mathbb{P}}}$ would be exploitable by a trader that buys $A_{n}$ at any time $m$ such that its price $\mathbb{P}_{m}(A_n)$ is lower than its eventual price, and then sells back the ${\mathbb{R}}$\-combination when the price rises.

We would like to apply the return on investment lemma (Lemma 115) as in Theorem 116. One natural attempt is to have, for each $n$, a trader for that watches the price of $A_n$ at all times $m \ge n$, buying low and selling high. This proof strategy may be feasible, but does not follow straightforwardly from the ROI lemma: those traders may be required to make multiple purchases of $A_n$ in order to guard against their prices _ever_ dipping too low. This pattern of trading may violate the condition for applying the ROI lemma that requires traders to have a total trading volume that is predictable by a ${\overline{\mathbb{P}}}$\-generable $\mathcal{E\!F}$\-progression (in order to enable verifiable budgeting).

Thus we find it easier to index our traders by the time rather than by $A_n$. That is, we will define a sequence of traders $({\overline{T}}^k)_k$, where the trader ${\overline{T}}^k$ ensures that $\mathbb{P}_k$ does not assign too low a price to any $A_n$ for $n \le k$. Specifically, ${\overline{T}}^k$ at time $k$ buys any ${\mathbb{R}}$\-combination $A_n$ for $n \le k$ with $\mathbb{P}_{k}(A_n)$ sufficiently low, and then sells back each such purchase as the price $\mathbb{P}_{m}(A_n)$ rises. In this way, if ${\mathbb{R}}$\-combinations are ever underpriced at any time above the main diagonal, there is a trader ready to buy that ${\mathbb{R}}$\-combination in full.

##### Proof. ^proof-2

_Proof._ We show the first equality; the second equality follows from the first by considering the negated progression $(-A_n)_n$.

For every $n$, since $\mathbb{P}_\infty$ is the limit of the $\mathbb{P}_m$ and since $\mathbb{V}(A_n)$ is continuous as a function of the valuation $\mathbb{V}$, we have that $\inf_{m \ge n}\mathbb{P}_{m}(A_n) \le \mathbb{P}_{\infty}(A_{n})$. Therefore the corresponding inequality in the limit infimum is immediate.

Suppose for contradiction that the other inequality doesn’t hold, so that 

$$
\liminf_{n\to\infty}\inf_{m \ge n}\mathbb{P}_{m}(A_n) < \liminf_{n\rightarrow\infty}\mathbb{P}_{\infty}(A_{n}).
$$

 Then there are rational numbers $\varepsilon>0$ and $b$ such that we have 

$$
\liminf_{n\to\infty}\inf_{m \ge n}\mathbb{P}_{m}(A_n)
<  b- \varepsilon<b+ \varepsilon<  \liminf_{n\rightarrow\infty}\mathbb{P}_{\infty}(A_{n})\ ,
$$

 and therefore we can fix some sufficiently large $s_\varepsilon$ such that

-   for all $n>s_\varepsilon$, we have $\mathbb{P}_{\infty}(A_{n}) > b+ \varepsilon$, and
    
-   for infinitely many $n>s_\varepsilon$, we have $\inf_{m\ge n} \mathbb{P}_{m}(A_n)<b- \varepsilon$.
    

We will assume without loss of generality that each ${\|A_n\|_{\rm mg}} \leq 1$; they are assumed to be bounded, so they can be scaled down appropriately.

##### An efficiently emulatable sequence of traders. ^an-efficiently-emulatable-sequence-2

Now we define our sequence of traders $({\overline{T}}^k)_k$. Let ${\overline{{A^\dagger}}}$ be an $\mathcal{E\!F}$\-combination progression such that ${A^\dagger}_n({\overline{\mathbb{P}}}) = A_n$ for all $n$. For $n < k$, define $T^k_n$ to be the zero trading strategy. Define $T^k_k$ to be the trading strategy 

$$
T^k_k :=
\sum_{s_\varepsilon < n\le k} \left( {\rm Under}_k^n \cdot \left( A^\dagger_n - A_{n}^{\dagger* k} \right)   \right)  \  ,
$$

 where 

$$
{\rm Under}_k^n:= \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( A_{n}^{\dagger* k} < b- \varepsilon/2
\right)\ .
$$

 This is a buy order for each ${\mathbb{R}}$\-combination $A_{n}$ for $s_\varepsilon < n \le k$, scaled down by the continuous indicator function ${\rm Under}_k^n$ for the event that $A_n$ is underpriced at time $k$ by ${\overline{\mathbb{P}}}$. Then, for time steps $m>k$, we define $T^k_m$ to be the trading strategy 

$$
T^k_m := F_m    \cdot
\sum_{s_\varepsilon < n\le k}
  \left( -{\rm Under}_k^n \cdot \left( A^\dagger_n - A_{n}^{\dagger* m} \right)\right)  \  ,
$$

 where 

$$
F_m :=
\left( 1- \sum_{k<i<m} F_i \right)  \cdot
\prod_{s_\varepsilon < n\le k}
  {\rm Over}_m^n
$$

 and 

$$
{\rm Over}_m^n:= \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( A_{n}^{\dagger* m} > b+ \varepsilon/2 \right) \ .
$$

 This trade is a sell order for the entire ${\mathbb{R}}$\-combination comprising the sum of the scaled ${\mathbb{R}}$\-combinations ${\rm Under}_k^n ({\overline{\mathbb{P}}})\cdot A_{n}$ for $s_\varepsilon < n \leq k$ purchased at time $k$ by $T^k_k$, scaled down by the fraction $F_m ({\overline{\mathbb{P}}})$. We define $F_m$ so that it represents the fraction of the original purchase made by the trader ${\overline{T}}^k$ that has not yet been sold off by time $m$, scaled down by the continuous indicator $\prod_{s_\varepsilon < n\le k} {\rm Over}_m^n$ for the event that all of those ${\mathbb{R}}$\-combinations $A_{n}$ for $s_\varepsilon < n \leq k$ are overpriced at time $m$.

By assumption, the $\mathcal{E\!F}$\-combination progression ${\overline{A^\dagger}}$ is e.c., and each trader ${\overline{T}}^k$ does not trade before time $k$. Therefore the sequence of traders $({\overline{T}}^k)_k$ is efficiently emulatable (see [[#^dynamic-programming-for-traders|8.2.2]] on dynamic programming).

##### $\boldsymbol{(\varepsilon/2)}$ return on investment for $\boldsymbol{{\overline{T}}^k}$. ^boldsymbol-varepsilon-2-return-2

Now we show that each ${\overline{T}}^k$ has $(\varepsilon/2)$\-ROI, i.e., for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$: 

$$
\lim_{n \to\infty}\mathbb{W}\left( {\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}})}\right)
\geq
(\varepsilon/2)
{\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}}\ .
$$

Roughly speaking, ${\overline{T}}^k$ gets $(\varepsilon/2)$\-ROI for the same reason as the traders in the proof of Theorem 116: the stock holdings from each $A_{n}$ that ${\overline{T}}^k$ purchased will be sold off for at least $(\varepsilon/2)$\-ROI, so the sum of the ${\mathbb{R}}$\-combinations is sold off for $(\varepsilon/2)$\-ROI.

Since ${\rm Over}_i^n ({\overline{\mathbb{P}}})\in [0,1]$ for all $n$ and $i$, by induction on $m$ we have that $\sum_{k<i\leq m} F_i({\overline{\mathbb{P}}})\leq 1$ and $F_m({\overline{\mathbb{P}}})\ge 0$. Therefore for each $k> s_\varepsilon$, by definition ${\overline{T}}^k$ makes a trade of magnitude ${\|{\overline{T}}^k_k ({\overline{\mathbb{P}}})\|_{\rm mg}} = \sum_{s_\varepsilon < n\le k}{\rm Under}_k^n({\overline{\mathbb{P}}})\cdot {\|A_n\|_{\rm mg}}$, followed by trades of magnitude 

$$
\sum_{n>k} F_n({\overline{\mathbb{P}}}){\|{\overline{T}}^k_k ({\overline{\mathbb{P}}})\|_{\rm mg}} \leq   {\|{\overline{T}}^k_k ({\overline{\mathbb{P}}})\|_{\rm mg}}\ .
$$

 By assumption, there is some time $m$ such that $\mathbb{P}_{m}(A_n)  > b+ \varepsilon/2$ for all $s_\varepsilon < n \le k$. At that point, ${\rm Over}_m^n ({\overline{\mathbb{P}}})= 1$ for each such $n$, so that $F_n ({\overline{\mathbb{P}}})= \left(1 - \sum_{k<i<n}F_i ({\overline{\mathbb{P}}})\right)$. Then at time $m$, ${\overline{T}}^k$ will sell of the last of its stock holdings from trades in $A_{n}$, so that $\sum_{k< i \leq m} {\|{\overline{T}}^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}}$ is equal to 

$$
\left(F_m ({\overline{\mathbb{P}}})+  \sum_{k<i <m} F_i ({\overline{\mathbb{P}}})\right) \cdot
\sum_{s_\varepsilon < n\le k}{\rm Under}_k^n ({\overline{\mathbb{P}}})\cdot {\|A_n\|_{\rm mg}}  = {\| {\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}} \ .
$$

 Furthermore, for all times $M>m$ we have $F_M({\overline{\mathbb{P}}})= 0$, so that $T^k_M({\overline{\mathbb{P}}})\equiv 0$. Therefore ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}}= \sum_{k\leq i \leq n} {\|{\overline{T}}^k_i({\overline{\mathbb{P}}})\|_{\rm mg}}= 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$.

From this point, the proof of return on investment is essentially identical to the analogous proof of Theorem 116. The only difference is that here the trader ${\overline{T}}^k$ holds a combination of ${\mathbb{R}}$\-combinations. Therefore we will not belabor the details; inserting a summation $\sum_{s_\varepsilon < n\le k}$ in front of the trades made by the traders in the proof of Theorem 116 will produce the precise derivation.

In short, since ${\overline{T}}^k$ will eventually hold no net shares, the value of its holdings is determined by the prices of the shares it trades, regardless of plausible worlds. By definition, ${\overline{T}}^k$ purchases a mixture of ${\mathbb{R}}$\-combinations 

$$
\sum_{s_\varepsilon < n\le k} \left( {\rm Under}_k^n ({\overline{\mathbb{P}}})\cdot A_n \right)    ,
$$

 where each $A_n$ with ${\rm Under}_k^n ({\overline{\mathbb{P}}})>0$ has price $\mathbb{P}_k(A_n)$ at most $b-\varepsilon/2$ at time $k$. Then ${\overline{T}}^k$ sells off that mixture, at times for which each ${\mathbb{R}}$\-combination has price at least $b+\varepsilon/2$. Thus ${\overline{T}}^k$ eventually has holdings with value at least 

$$
\begin{align*}
&\;\;\;\sum_{s_\varepsilon < n\le k} \left( {\rm Under}_k^n({\overline{\mathbb{P}}}) \cdot \left(  b+\varepsilon/2 - (b-\varepsilon/2) \right) \right) \\
&= \sum_{s_\varepsilon < n\le k} \left( {\rm Under}_k^n({\overline{\mathbb{P}}})\cdot  \varepsilon \right)  \\
&\geq \varepsilon \sum_{s_\varepsilon < n\le k} \left( {\rm Under}_k^n({\overline{\mathbb{P}}}) \cdot |A_n| \right)    \\
&\geq \varepsilon {\|T^k_k({\overline{\mathbb{P}}})\|_{\rm mg}} \\
&= (\varepsilon/2 ) {\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}} \ .
\end{align*}
$$

 Thus, ${\overline{T}}^k$ has $(\varepsilon/2)$\-ROI.

##### Deriving a contradiction. ^deriving-a-contradiction-2

We have shown that the sequence of traders $({\overline{T}}^k)_k$ is bounded, efficiently emulatable, and has $(\varepsilon/2)$\-return on investment. The remaining condition to Lemma 115 states that for all $k$, the magnitude ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}}$ of all trades made by ${\overline{T}}^k$ must equal $\alpha_k$ for some ${\overline{\mathbb{P}}}$\-generable ${\overline{\alpha_k}}$. This condition is satisfied for $\alpha_k := 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$, since as shown above, ${\|{\overline{T}}^k({\overline{\mathbb{P}}})\|_{\rm mg}} = 2{\|{\overline{T}}^k_k({\overline{\mathbb{P}}})\|_{\rm mg}}$.

Therefore we can apply Lemma 115 (the ROI lemma) to the sequence of traders $({\overline{T}}^k)_k$. We conclude that $\alpha_k \eqsim_k 0$. Recall that we supposed by way of contradiction that infinitely often, some $A_n$ is underpriced. That is, for infinitely many times $k$ and indices $s_\varepsilon < n\le k$, $\mathbb{P}_{k}(A_n)< b- \varepsilon$.

But for any such $k$ and $n$, $T^k_k$ will purchase the full ${\mathbb{R}}$\-combination $A_{n}$, as 

$$
{\rm Under}_k^n ({\overline{\mathbb{P}}})
= \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left( \mathbb{P}_{k}(A_n)  < b- \varepsilon/2\right) = 1 \ .
$$

 Now $\alpha_k = 2 {\|{\overline{T}}^k_k\|_{\rm mg}} \geq 2 \cdot {\rm Under}_k^n {\|A_n\|_{\rm mg}} =2 {\|A_n\|_{\rm mg}}$, and ${\|A_n\|_{\rm mg}} \geq \varepsilon/2$ (since $\mathbb{P}_m(A_n) - \mathbb{P}_k(A_n) \geq \varepsilon$ for some $m$). So $\alpha_k \geq \varepsilon$ infinitely often, contradicting $\alpha_k \eqsim_k 0$. ◻

### Persistence of Knowledge ^persistence-of-knowledge

**Theorem 119** (Persistence of Knowledge). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences, and ${\overline{{p}}}$ be an e.c. sequence of rational-number probabilities. If $\mathbb{P}_\infty(\phi_n)\eqsim_np_n$, then 

$$
\sup_{m\ge n}|\mathbb{P}_m(\phi_n)-p_n|\eqsim_n0.
$$

 Furthermore, if $\mathbb{P}_\infty(\phi_n)\lesssim_np_n$, then 

$$
\sup_{m\geq n}\mathbb{P}_m(\phi_n)\lesssim_np_n,
$$

 and if $\mathbb{P}_\infty(\phi_n)\gtrsim_np_n$, then 

$$
\inf_{m\geq n}\mathbb{P}_m(\phi_n)\gtrsim_np_n.
$$

_

_Proof._ The second and third statements are a special case of Theorem 42 (Persistence of Affine Knowledge), using the combination $A_n := \phi_n$; the first statement follows from the second and third. ◻

## Coherence Proofs ^coherence-proofs

### Affine Coherence ^affine-coherence

**Theorem 120** (Affine Coherence). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(A_n)
    \le \liminf_{n\rightarrow\infty}
      \mathbb{P}_\infty(A_n)
    \le \liminf_{n\to\infty}
      \mathbb{P}_n(A_n),
$$

 and 

$$
\limsup_{n\to\infty} \mathbb{P}_n(A_n)
    \le \limsup_{n\rightarrow\infty} \mathbb{P}_\infty(A_n)
    \le \limsup_{n\rightarrow\infty} \sup_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(A_n).
$$

_

_Proof._ We show the first series of inequalities; the second series follows from the first by considering the negated progression $(-A_n)_n$. Let ${\overline{{A^\dagger}}}$ be an $\mathcal{E\!F}$\-combination progression such that ${A^\dagger}_n({\overline{\mathbb{P}}}) = A_n$ for all $n$.

##### Connecting $\boldsymbol{\mathcal{PC}(\Gamma)}$ to $\boldsymbol{\mathbb{P}_\infty}$. ^connecting-boldsymbol-mathcal-pc

First we show that 

$$
\liminf_{n \to \infty} \inf_{\mathbb{W}\in \mathcal{PC}(\Gamma)} \mathbb{W}(A_{n}) \le \liminf_{n \to \infty}  \mathbb{P}_{\infty}(A_{n}).
$$

 It suffices to show the stronger statement that for any $n\in{\mathbb{N}}^+$, 

$$
\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)} \mathbb{W}(A_{n}) \le \mathbb{P}_{\infty}(A_{n}).
$$

 This is a generalization of coherence in the limit to affine relationships; its proof will follow a strategy essentially identical to the one used in the proof of Theorem [[#^convergence-and-coherence|4.1]] (coherence) to show the particular coherence relationships that are sufficient to imply ordinary probabilistic coherence. That is, we will construct a trader that waits for the coherence relationship to approximately hold (so to speak) and for the price of the corresponding ${\mathbb{R}}$\-combination to approximately converge, and then buys the combination repeatedly if it is underpriced.

Suppose by way of contradiction that the inequality does not hold, so for some fixed $n$ there are rational numbers $\varepsilon>0$ and $b$ and a time step $s_\varepsilon$ such that for all $m> s_\varepsilon$ we have 

$$
\mathbb{P}_{m}(A_{n})   <  b-\varepsilon   <  b+\varepsilon
  < \inf_{\mathbb{W}\in\mathcal{PC}(D_m)} \mathbb{W}(A_{n}) \ .
$$

 Therefore we can define a trader ${\overline{T}}$ that waits until time $s_\varepsilon$, and thereafter buys a full ${\mathbb{R}}$\-combination $A_{n}$ on every time step. That is, we take $T_m$ to be the zero trading strategy for $m\le s_\varepsilon$, and we define $T_m$ for $m > s_\varepsilon$ to be 

$$
T_m := A^\dagger_n - A_n^{\dagger* m} .
$$

 Intuitively, since the infimum over plausible worlds of the value of the stocks in this ${\mathbb{R}}$\-combination is already substantially higher than its price, the value of the total holdings of our trader ${\overline{T}}$ immediately increases by at least $2\varepsilon$. More formally, we have that for any time $m$ and any $\mathbb{W}\in\mathcal{PC}(D_m)$, 

$$
\begin{align*}
    \mathbb{W}\left(\sum_{i\le m}T_i({\overline{\mathbb{P}}})\right) &=     \mathbb{W}\left(\sum_{s_\varepsilon < i\le m}T_i({\overline{\mathbb{P}}})\right)
\end{align*}
$$

since $T_m \equiv 0$ for $m \le s_\varepsilon$;

$$
\begin{align*}
    &= \sum_{s_\varepsilon < i\le m} \mathbb{W}(A_{n}) - \mathbb{P}_{i}(A_{n})
\end{align*}
$$

by linearity, by definition of $T_i$, and since $A^\dagger_{n}({\overline{\mathbb{P}}}) \equiv A_{n}$ and $A^{\dagger* m}_{n}({\overline{\mathbb{P}}}) \equiv \mathbb{P}_m(A_{n})$;

$$
\begin{align*}
    &\geq \sum_{s_\varepsilon < i\le m}  b+\varepsilon -(b-\varepsilon  )  \\
  &=  2\varepsilon (m-s_\varepsilon).
\end{align*}
$$

 This is bounded below by 0 and unbounded above as $m$ goes to $\infty$. Thus ${\overline{T}}$ exploits the market ${\overline{\mathbb{P}}}$, contradicting that ${\overline{\mathbb{P}}}$ is a logical inductor. Therefore in fact we must have 

$$
\liminf_{n \to \infty} \inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)} \mathbb{W}(A_{n}({\overline{\mathbb{P}}})) \le \liminf_{n \to \infty}  \mathbb{P}_{\infty}(A_{n}({\overline{\mathbb{P}}})) ,
$$

 as desired.

##### Connecting $\boldsymbol{\mathbb{P}_n}$ to $\boldsymbol{\mathbb{P}_\infty}$ and to fast diagonals. ^connecting-boldsymbol-mathbb-p

Now we show that 

$$
\liminf_{n \to\infty} \mathbb{P}_{\infty}(A_{n}) \le \liminf_{n \to\infty} \mathbb{P}_{n}(A_{n}).
$$

 This says, roughly speaking, that affine relationships that hold in the limiting belief state $\mathbb{P}_\infty$ also hold along the main diagonal. We show this inequality in two steps. First, by Theorem 42 (Persistence of affine knowledge), we have 

$$
\liminf_{n \to\infty} \mathbb{P}_{\infty}(A_{n}) \le  \liminf_{n \to\infty}\inf_{m \ge n} \mathbb{P}_{m}(A_{n}).
$$

 This says roughly that if the limiting beliefs end up satisfying some sequence of affine relationships, then eventually all belief states above the main diagonal satisfy that relationship to at least the same extent. Second, it is immediate that 

$$
\liminf_{n \to\infty}\inf_{m \ge n} \mathbb{P}_{m}(A_{n}) \le \liminf_{n \to\infty}  \mathbb{P}_{n}(A_{n}),
$$

 since for all $n$, $\inf_{m \ge n} \mathbb{P}_{m}(A_{m}) \le \mathbb{P}_{n}(A_{n})$. Thus we have the desired inequality. ◻

### Affine Provability Induction ^affine-provability-induction

**Theorem 121** (Affine Provability Induction). _Let ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$ and $b \in {\mathbb{R}}$. If, for all consistent worlds $\mathbb{W}\in\mathcal{PC}(\Gamma)$ and all $n\in {\mathbb{N}}^+$, it is the case that $\mathbb{W}(A_n ) \ge b$, then 

$$
\mathbb{P}_n(A_n) \gtrsim_nb,
$$

 and similarly for $=$ and $\eqsim_n$, and for $\leq$ and $\lesssim_n$._

_Proof._ We prove the statement in the case of $\geq$; the case of $\leq$ is analogous, and the case of $=$ follows from the conjunction of the other two cases. By Theorem 120 (Affine Coherence),

$$
\liminf_{n \to \infty} \mathbb{P}_n(A_n) \geq \liminf_{n \to \infty} \inf_{\mathbb{W}\in \mathcal{PC}(\Gamma)} \mathbb{W}(A_n) \geq b.
$$

 We will usually apply this theorem using the $=$ case. ◻

### Provability Induction ^provability-induction-2

**Theorem 122** (Provability Induction). _Let ${\overline{\phi}}$ be an e.c. sequence of theorems. Then 

$$
\mathbb{P}_n(\phi_n) \eqsim_n1.
$$

 Furthermore, let ${\overline{\psi}}$ be an e.c. sequence of disprovable sentences. Then 

$$
\mathbb{P}_n(\psi_n) \eqsim_n0.
$$

_

_Proof._ Since ${\overline{\phi}}$ is a sequence of theorems, for all $n$ and $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(\phi_n) = 1$. So by Theorem 121 (Affine Provability Induction), 

$$
\mathbb{P}_n(\phi_n) \eqsim_n 1.
$$

 Similarly, since ${\overline{\psi}}$ is a sequence of disprovable sentences, for all $n$ and $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(\psi_n) = 0$. So by Theorem 121 (Affine Provability Induction), 

$$
\mathbb{P}_n(\psi_n) \eqsim_n 0.
$$

 ◻

### Belief in Finitistic Consistency ^belief-in-finitistic-consistency

**Theorem 123** (Belief in Finitistic Consistency). _Let $f$ be any computable function. Then 

$$
\mathbb{P}_n(\operatorname{Con}(\Gamma)(\text{“}{\underline{f}}({\underline{n}})\text{”})) \eqsim_n1.
$$

_

_Proof._ Since each statement $\operatorname{Con}(\Gamma)(\text{“}{\underline{f}}({\underline{n}})\text{”})$ is computable and true, and $\Gamma$ can represent computable functions, each of these statements is provable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the desired property. ◻

### Belief in the Consistency of a Stronger Theory ^belief-in-the-consistency

**Theorem 124** (Belief in the Consistency of a Stronger Theory). _Let $\Gamma^\prime$ be any recursively axiomatizable consistent theory. Then 

$$
\mathbb{P}_n(\operatorname{Con}(\Gamma^\prime)(\text{“}{\underline{f}}({\underline{n}})\text{”})) \eqsim_n1.
$$

_

_Proof._ Since each statement $\operatorname{Con}(\Gamma')(\text{“}{\underline{f}}({\underline{n}})\text{”})$ is computable and true, and $\Gamma$ can represent computable functions, each of these statements is provable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the desired property. ◻

### Disbelief in Inconsistent Theories ^disbelief-in-inconsistent-theories

**Theorem 125** (Disbelief in Inconsistent Theories). _Let ${\overline{\Gamma^\prime}}$ be an e.c. sequence of recursively axiomatizable inconsistent theories. Then 

$$
\mathbb{P}_n(\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is inconsistent}\text{”}) \eqsim_n1,
$$

 so 

$$
\mathbb{P}_n(\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is consistent}\text{”}) \eqsim_n0.
$$

_

_Proof._ Since each statement $\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is inconsistent}\text{”}$ is provable in ${\mathsf{PA}}$, and $\Gamma$ can represent computable functions, each of these statements is provable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the first desired property.

Similarly, since each statement $\text{“}{\underline{\Gamma^\prime_n}}\textnormal{\ is consistent}\text{”}$ is disprovable in ${\mathsf{PA}}$, and $\Gamma$ can represent computable functions, each of these statements is disprovable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the second desired property. ◻

### Learning of Halting Patterns ^learning-of-halting-patterns

**Theorem 126** (Learning of Halting Patterns). _Let ${\overline{m}}$ be an e.c. sequence of Turing machines, and ${\overline{x}}$ be an e.c. sequence of bitstrings, such that $m_n$ halts on input $x_n$ for all $n$. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{m_n}}\) halts on input \({\underline{x_n}}\)}\text{”}) \eqsim_n1.
$$

_

_Proof._ Since each statement $\text{“}\textnormal{\({\underline{m_n}}\) halts on input \({\underline{x_n}}\)}\text{”}$ is computable and true, and $\Gamma$ can represent computable functions, each of these statements is provable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the desired property. ◻

### Learning of Provable Non-Halting Patterns ^learning-of-provable-non-halting

**Theorem 127** (Learning of Provable Non-Halting Patterns). _Let ${\overline{q}}$ be an e.c. sequence of Turing machines, and ${\overline{y}}$ be an e.c. sequence of bitstrings, such that $q_n$ _provably_ fails to halt on input $y_n$ for all $n$. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\)}\text{”}) \eqsim_n0.
$$

_

_Proof._ Each statement $\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\)}\text{”}$ is disprovable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the desired property. ◻

### Learning not to Anticipate Halting ^learning-not-to-anticipate

**Theorem 128** (Learning not to Anticipate Halting). _Let ${\overline{q}}$ be an e.c. sequence of Turing machines, and let ${\overline{y}}$ be an e.c. sequence of bitstrings, such that $q_n$ does not halt on input $y_n$ for any $n$. Let $f$ be any computable function. Then 

$$
\mathbb{P}_n(\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\) within \({\underline{f}}({\underline{n}})\) steps}\text{”}) \eqsim_n0.
$$

_

_Proof._ Since each statement $\text{“}\textnormal{\({\underline{q_n}}\) halts on input \({\underline{y_n}}\) within \({\underline{f}}({\underline{n}})\) steps}\text{”}$ is computable and false, and $\Gamma$ can represent computable functions, each of these statements is disprovable in $\Gamma$. Now apply Theorem 122 (Provability Induction) to get the desired property. ◻

### Limit Coherence ^limit-coherence-2

**Theorem 129** (Limit Coherence). _$\mathbb{P}_\infty$ is coherent, i.e., it gives rise to an internally consistent probability measure $\mathrm{Pr}$ on the set $\mathcal{PC}(\Gamma)$ of all worlds consistent with $\Gamma$, defined by the formula 

$$
\mathrm{Pr}(\mathbb{W}(\phi)=1):=\mathbb{P}_\infty(\phi).
$$

 In particular, if $\Gamma$ contains the axioms of first-order logic, then $\mathbb{P}_\infty$ defines a probability measure on the set of first-order completions of $\Gamma$._

_Proof._ The limit $\mathbb{P}_\infty(\phi)$ exists by Theorem 118 (Convergence), so $\mathbb{P}_\infty$ is well-defined. Gaifman (1964) shows that $\mathbb{P}_\infty$ defines a probability measure over $\mathcal{PC}(\Gamma)$ so long as the following three implications hold for all sentences $\phi$ and $\psi$:

-   If $\Gamma\vdash \phi$, then $\mathbb{P}_\infty(\phi) = 1$,
    
-   If $\Gamma\vdash \lnot \phi$, then $\mathbb{P}_\infty(\phi) = 0$,
    
-   If $\Gamma\vdash \lnot(\phi \land \psi)$, then $\mathbb{P}_\infty(\phi \lor \psi) = \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi)$.
    

Let us demonstrate each of these three properties.

-   Assume that $\Gamma\vdash \phi$. By Theorem 122 (Provability Induction), $\mathbb{P}_\infty(\phi) = 1$.
    
-   Assume that $\Gamma\vdash \lnot \phi$. By Theorem 122 (Provability Induction), $\mathbb{P}_\infty(\phi) = 0$.
    
-   Assume that $\Gamma\vdash \lnot(\phi \land \psi)$. For all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(\phi \vee \psi) = \mathbb{W}(\phi) + \mathbb{W}(\psi)$. So by Theorem 121 (Affine Provability Induction), $\mathbb{P}_\infty(\phi \vee \psi) = \mathbb{P}_\infty(\phi) + \mathbb{P}_\infty(\psi)$.
    

 ◻

### Learning Exclusive-Exhaustive Relationships ^learning-exclusive-exhaustive-relationsh

**Theorem 130** (Learning Exclusive-Exhaustive Relationships). _Let ${\overline{\phi^1}},\ldots,{\overline{\phi^k}}$ be $k$ e.c. sequences of sentences, such that for all $n$, $\Gamma$ proves that $\phi^1_n,\ldots,\phi^k_n$ are exclusive and exhaustive (i.e. exactly one of them is true). Then 

$$
\mathbb{P}_n(\phi^1_n)+\cdots+\mathbb{P}_n(\phi^k_n)  \eqsim_n1.
$$

_

_Proof._ Define $A_n := \phi_n^1 + \cdots + \phi_n^k$. Note that for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(A_n) = 1$.

So by Theorem 121 (Affine Provability Induction) and linearity, 

$$
\mathbb{P}_n(\phi_n^1) + \cdots + \mathbb{P}_n(\phi_n^k ) = \mathbb{P}_n(\phi_n^1 + \cdots + \phi_n^k ) =     \mathbb{P}_n(A_n) \eqsim_n 1.
$$

 ◻

## Statistical Proofs ^statistical-proofs

### Affine Recurring Unbiasedness ^affine-recurring-unbiasedness

**Theorem 131** (Affine Recurring Unbiasedness). _If ${\overline{A}}\in\mathcal{BCS}({\overline{\mathbb{P}}})$ is determined via $\Gamma$, and ${\overline{w}}$ is a ${\overline{\mathbb{P}}}$\-generable divergent weighting, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(A_i)-\operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

_Proof._ Define 

$$
\mathrm{Bias}_n :=
      \frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(A_i)-\operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i} .
$$

Our proof consists of three steps:

1.  Proving $\limsup_{n \to \infty} \mathrm{Bias}_n \geq 0$.
    
2.  Noting that the first argument can be applied to the sequence $(-A_n)_n$ to prove $\liminf_{n \to \infty} \mathrm{Bias}_n \leq 0$.
    
3.  Proving that, given these facts, $(\mathrm{Bias}_n)_n$ has 0 as a limit point.
    

The first step will be deferred. The second step is trivial. We will now show that the third step works given that the previous two do:

Let $a := \liminf_{n \to \infty} \mathrm{Bias}_n\leq 0$ and $b := \limsup_n\mathrm{Bias}_n \geq 0$. If $a = 0$ or $b = 0$ then of course 0 is a limit point. Otherwise, let $a < 0 < b$. If 0 is not a limit point of $(\mathrm{Bias}_n)_n$, then there are $\varepsilon > 0$ and $N \in{\mathbb{N}}$ such that $\forall n> N : \mathrm{Bias}_n\notin (-\varepsilon,\varepsilon) \subseteq (a,b)$. Choose $M>N$ such that $\mathrm{Bias}_M \in (\varepsilon, b]$ and for all $n>M$, $\mathrm{Bias}_n-\mathrm{Bias}_{n+1}<\varepsilon$; sufficiently late adjacent terms are close because $\sum_{i \leq n} w_i$ goes to $\infty$ and the absolute difference between successive numerators is at most 1. Then $(\mathrm{Bias}_n)_{n>M}$ must remain positive (it cannot cross the $2\varepsilon$\-wide gap), contradicting that $a$ is also a limit point and $a < 0$.

At this point we have shown that the second and third steps follow from the first step, so we need only show the first step: $\limsup_{n \to \infty} \mathrm{Bias}_n \geq 0$. Suppose this is not the case. Then there is some natural $N$ and rational $\varepsilon \in (0, 1)$ such that for all $n\geq N$,

$$
\frac
      {\sum_{i\leq n}w_i\cdot (\mathbb{P}_i(A_i) - \operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i}
        <- 2\varepsilon
$$

 or equivalently, 

$$
\sum_{i\leq n}w_i\cdot (\operatorname{Val}_{\Gamma}(A_i) - \mathbb{P}_i(A_i))
        > 2\varepsilon\sum_{i \leq n} w_i .
$$

##### An efficiently emulatable sequence of traders. ^an-efficiently-emulatable-sequence-3

We will consider an infinite sequence of traders, each of which will buy a “run” of ${\mathbb{R}}$\-combinations, and which will have $\varepsilon$\-ROI. Then we will apply Lemma 115 to derive a contradiction.

Without loss of generality, assume each ${\|A_n\|_{\rm mg}} \leq 1$; they are uniformly bounded and can be scaled down without changing the theorem statement. Let ${\overline{{w^\dagger}}}$ be an e.c. $\mathcal{E\!F}$ progression such that ${w_n^\dagger} ({\overline{\mathbb{P}}})= w_n$. Let ${\overline{{A^\dagger}}}$ be an e.c. $\mathcal{E\!F}$\-combination progression such that ${A_n^\dagger} ({\overline{\mathbb{P}}})= A_n$. Let ${\overline{{A^\dagger}}}$ be equal to 

$$
{A_n^\dagger} = c + \xi_1 \phi_1 + \cdots + \xi_{l(n)} \phi_{l(n)},
$$

 and define the expressible feature ${\|{A_n^\dagger}\|_{\rm mg}} := \sum_{i=1}^{l(n)} |\xi_i|$.

For $k < N$, trader ${\overline{T}}^k$ will be identically zero. For $k \geq N$, trader ${\overline{T}}^k$ will buy some number of copies of ${A_n^\dagger}$ on day $n$; formally,

$$
T^k_n := {\gamma_{k,n}^\dagger} \cdot ({A_n^\dagger} - A_n^{\dagger* n}) ,
$$

 with ${\gamma_{k,n}^\dagger}$ to be defined later. To define ${\gamma_{k,n}^\dagger}$, we will first define a scaling factor on the trader’s purchases: 

$$
\delta_k := \frac{\varepsilon}{1 + k} .
$$

 Now we recursively define 

$$
{\gamma_{k, n}^\dagger} := [n\geq k] \min\left(\delta_k \cdot {w_n^\dagger}, 1 - \sum_{i\le n-1} {\gamma_{k, i}^\dagger} {\| {A_n^\dagger} \|_{\rm mg}} \right),
$$

 where $[n\geq k]$ is Iverson bracket applied to $n \geq k$, i.e. the 0-1 indicator of that condition. This sequence of traders is efficiently emulatable, because ${\overline{{A^\dagger}}}$ and ${\overline{{w^\dagger}}}$ are e.c., and ${\overline{T}}^k$ makes no trades before day $k$.

##### Analyzing the trader. ^analyzing-the-trader

On day $n$, trader ${\overline{T}}^k$ attempts to buy $\delta_k w_n$ copies of $A_n$, but caps its total budget at 1 dollar; the $\min$ in the definition of ${\gamma_{k, n}^\dagger}$ ensures that ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}} \leq 1$.

Observe that $\sum_{i\le n} {\| {\overline{T}}^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}} = \max\{1, \sum_{i=k}^n \delta_k w_n {\|A_n\|_{\rm mg}} \}$. We can use this to show that ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}} = 1$. For all $n \geq N$, 

$$
2 \varepsilon \sum_{i \leq n} w_i
<
\sum_{i\leq n}w_i \cdot (\operatorname{Val}_{\Gamma}(A_i) - \mathbb{P}_i(A_i))
\leq 2 \sum_{i \leq n} w_i {\|A_i\|_{\rm mg}}.
$$

 Since the left hand side goes to $\infty$ as $n \to \infty$, so does the right hand side. So indeed, $\sum_{n=k}^\infty \delta_k w_n {\|A_n\|_{\rm mg}} = \infty$, and ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}} = 1$.

##### $\boldsymbol{{\overline{T}}^k}$ has $\boldsymbol{\varepsilon}$ return on investment. ^boldsymbol-overline-t-k

We will now show that each trader ${\overline{T}}^k$ has $\varepsilon$ return on investment. Trivially, for $k < N$, ${\overline{T}}^k$ has $\varepsilon$ return on investment, because ${\|{\overline{T}}^k ({\overline{\mathbb{P}}})\|_{\rm mg}} = 0$. So consider $k \geq N$.

As shorthand, let $\gamma_{k, n} := {\gamma_{k, n}^\dagger} ({\overline{\mathbb{P}}})$. Let $m_k$ be the first $m \geq k$ for which $\gamma_{k,m} < \delta_k w_m$. We have $\gamma_{k, n} = \delta_k w_n$ for $k \leq n < m_k$, and $\gamma_{k, n} = 0$ for $n > m_k$. So for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$,

$$
\begin{align*}
          &\mathbb{W}\left(\sum_{n=1}^\infty T^k_n ({\overline{\mathbb{P}}})\right)
          \\
          =&
        \sum_{n=1}^\infty \mathbb{W}(T^k_n ({\overline{\mathbb{P}}}))
          \\
        =&
        \sum_{k \leq n \leq m_k} \mathbb{W}(T^k_n ({\overline{\mathbb{P}}}))
          \\
        =&
        \sum_{k \leq n \leq m_k} \delta_k w_n (\mathbb{W}(A_n) - \mathbb{P}_n(A_n)) - (\delta_{k} w_{m_k} - \gamma_{k, m_k}) (\mathbb{W}(A_{m_k}) - \mathbb{P}_n(A_{m_k}))
          \\
        \geq&
        \sum_{k \leq n \leq m_k} \delta_k w_n (\mathbb{W}(A_n) - \mathbb{P}_n(A_n)) - \delta_k
          \\
        =&
        \sum_{n \leq m_k} \delta_k w_n (\mathbb{W}(A_n) - \mathbb{P}_n(A_n)) - \sum_{n < k} \delta_k w_n (\mathbb{W}(A_n) - \mathbb{P}_n(A_n)) - \delta_k
          \\
        \geq&
          \sum_{n \leq m_k} \delta_k w_n (\mathbb{W}(A_n) - \mathbb{P}_n(A_n)) - (k \delta_k + \delta_k)
          \\
        =&
        \sum_{n \leq m_k} \delta_k w_n (\operatorname{Val}_{\Gamma}{A_n} - \mathbb{P}_n(A_n)) - \varepsilon
          \\
        \geq&
        \ 2\varepsilon  - \varepsilon
          \\
        =&
        \ \varepsilon.
\end{align*}
$$

 So each trader ${\overline{T}}^k$ with $k \geq N$ makes at least $\varepsilon$ profit with trades of total magnitude 1, ensuring that it has $\varepsilon$ return on investment.

##### Deriving a contradiction. ^deriving-a-contradiction-3

Note that the magnitudes of the traders are ${\overline{\mathbb{P}}}$\-generable (the first $N - 1$ have magnitude 0 and the rest have magnitude 1). By Lemma 115, ${\|{\overline{T}}^k\|_{\rm mg}} \eqsim_k 0$. ${\|{\overline{T}}^k\|_{\rm mg}} = 1$ for all $k \geq N$ (by the above analysis), so this is a contradiction. ◻

### Recurring Unbiasedness ^recurring-unbiasedness

**Theorem 132** (Recurring Unbiasedness). _Given an e.c. sequence of decidable sentences ${\overline{\phi}}$ and a ${\overline{\mathbb{P}}}$\-generable divergent weighting ${\overline{w}}$, the sequence 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(\phi_i)-\operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

_Proof._ This is a special case of Theorem 131 (Affine Recurring Unbiasedness). ◻

### Simple Calibration ^simple-calibration

**Theorem 133** (Recurring Calibration). _Let ${\overline{\phi}}$ be an e.c. sequence of decidable sentences, $a$ and $b$ be rational numbers, ${\overline{\delta}}$ be an e.c. sequence of positive rational numbers, and suppose that $\sum_n\left(\operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a<\mathbb{P}_i(\phi_i)<b)\right)_{i \in {\mathbb{N}}^+} = \infty$. Then, if the sequence 

$$
\left(
    \frac
      {\sum_{i \leq n} \operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a < \mathbb{P}_i(\phi_i) < b) \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}
      {\sum_{i \leq n} \operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a < \mathbb{P}_i(\phi_i) < b)}
    \right)_{n\in{\mathbb{N}}^+}
$$

 converges, it converges to a point in $[a, b]$. Furthermore, if it diverges, it has a limit point in $[a, b]$._

_Proof._ Define $w_i := \operatorname{Ind}_{\textnormal{\small{\({\delta_i}\)}}}(a < {\phi_i}^{*i} < b)$. By Theorem 132 (Recurring Unbiasedness), the sequence 

$$
\left( \frac
      {\sum_{i\leq n}w_i\cdot (\mathbb{P}_i(\phi_i) - \operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n}w_i}
      \right)_{n \in {\mathbb{N}}^+}
$$

 has 0 as a limit point. Let $n_1, n_2, \ldots$ be a the indices of a subsequence of this sequence that converges to zero. We also know that for all $n$ high enough, 

$$
a \leq \frac {\sum_{i\leq n}w_i \mathbb{P}_i(\phi_i)}{\sum_{i\leq n}w_i} \leq b
$$

 because $w_i = 0$ whenever $\mathbb{P}_i(\phi_i) \not\in [a, b]$. Now consider the sequence 

$$
\begin{align*}
    & \left(\frac
      {\sum_{i\leq n_k}w_i\cdot \operatorname{Thm}_{\Gamma}(\phi_i)}
        {\sum_{i\leq n_k}w_i}
      \right)_{k \in {\mathbb{N}}^+}
      \\
      = &
        \left(
      \frac {\sum_{i\leq n_k}w_i \mathbb{P}_i(\phi_i)}{\sum_{i\leq n}w_i}
      -
      \frac{\sum_{i\leq n_k}w_i\cdot (\mathbb{P}_i(\phi_i) - \operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n_k}w_i}
      \right)_{k \in {\mathbb{N}}^+}
\end{align*}
$$

 The first term is bounded between $a$ and $b$, and the second term goes to zero, so the sequence has a $\liminf$ at least $a$ and a $\limsup$ no more than $b$. By the Bolzano-Weierstrass theorem, this sequence has a convergent subsequence, whose limit must be between $a$ and $b$. This subsequence is also a subsequence of 

$$
\left(\frac
        {\sum_{i\leq n}w_i\cdot \operatorname{Thm}_{\Gamma}(\phi_i)}
          {\sum_{i\leq n}w_i}
        \right)_{n \in {\mathbb{N}}^+}
$$

 which proves that this sequence has a limit point in $[a, b]$, as desired. ◻

### Affine Unbiasedness From Feedback ^affine-unbiasedness-from-feedback

**Theorem 134** (Affine Unbiasedness from Feedback). _Given ${\overline{A}}\in \mathcal{BCS}({\overline{\mathbb{P}}})$ that is determined via $\Gamma$, a strictly increasing deferral function $f$ such that $\operatorname{Val}_{\Gamma}(A_n )$ can be computed in time ${\mathcal{O}}(f(n+1))$, and a ${\overline{\mathbb{P}}}$\-generable divergent weighting ${\overline{w}}$ such that the support of ${\overline{w}}$ is contained in the image of $f$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(A_i)-\operatorname{Val}_{\Gamma}(A_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{A}}$”._

_Proof._ Without loss of generality, assume that each $\|A_n\|_1 \leq 1$. Define 

$$
\mathrm{Bias}_k :=
    \frac
    {\sum_{i\leq k }w_{f(i)}  \cdot(\mathbb{P}_{f(i)}(A_{f(i)})-\operatorname{Thm}_{\Gamma}(A_{f(i)}))}
    {\sum_{i\leq k} w_{f(i)}}
$$

 and observe that $\mathrm{Bias}_k \eqsim_k 0$ implies the theorem statement, since we need only consider the sum over $n$ in the support of $f$. We wish to show that $\mathrm{Bias}_k \eqsim_k 0$. We will show a trader that exploits ${\overline{\mathbb{P}}}$ under the assumption that $\lim\inf_{k \to \infty} \mathrm{Bias}_k < 0$, proving $\mathrm{Bias}_k \gtrsim_k 0$. We can apply the same argument to the sequence $(-A_n)_n$ to get $\mathrm{Bias}_k \lesssim_k 0$.

Suppose $\lim\inf_{k \to \infty} \mathrm{Bias}_k < 0$. Under this supposition, infinitely often, $\mathrm{Bias}_k < - 3 \varepsilon$ for some rational $0 < \varepsilon < 1/6$.

##### Defining the trader. ^defining-the-trader

Let ${\overline{{w^\dagger}}}$ be an e.c. $\mathcal{E\!F}$ progression such that ${w_n^\dagger} ({\overline{\mathbb{P}}})= w_n$. Let ${\overline{{A^\dagger}}}$ be an e.c. $\mathcal{E\!F}$\-combination progression such that ${A_n^\dagger} ({\overline{\mathbb{P}}})= A_n$. Recursively define

$$
\begin{align*}
  {\beta_i^\dagger} &:= \varepsilon \cdot {\mathrm{Wealth}_i^\dagger} \cdot {w_i ^\dagger}
  \\
  {\mathrm{Wealth}_i^\dagger} &:= 1 + \sum_{j\le i-1} {\beta_j^\dagger} \cdot \left(A_{f(j)}^{\dagger* f(j+1)} - A_{f(j)}^{\dagger* f(j)}\right)
\end{align*}
$$

 in order to define the trader 

$$
T_n:= \begin{cases}
    {\beta_i^\dagger} \cdot \left({A_{f(i)}^\dagger} - A_{f(i)}^{\dagger* n}\right)  - [i > 1] \cdot {\beta_{i-1}^\dagger} \cdot \left({A_{f(i-1)}^\dagger} - A_{f(i-1)}^{\dagger* n} \right)
    & \textnormal{if \(\exists i: n= f(i)\)}
    \\
    0 & \textnormal{otherwise.}
  \end{cases}
$$

 Note that ${\beta_i^\dagger}$ and ${\mathrm{Wealth}_i^\dagger}$ have rank at most $f(i)$, and so $T_n$ has rank at most $n$.

##### Analyzing the trader. ^analyzing-the-trader-2

As shorthand, let $\beta_i := {\beta_i^\dagger} ({\overline{\mathbb{P}}})$, and $\mathrm{Wealth}_i := {\mathrm{Wealth}_i^\dagger} ({\overline{\mathbb{P}}})$.

Intuitively, on day $f(i)$, ${\overline{T}}$ buys $A_{f(i)}$ according to a fraction of its “wealth” $\mathrm{Wealth}_i$ (how much money ${\overline{T}}$ would have if it started with one dollar), and then sells $A_{f(i)}$ at a later time $f(i+1)$. Thus, ${\overline{T}}$ makes money if the price of $A_{f(i)}$ is greater at time $f(i+1)$ than at time $f(i)$.

Betting according to a fraction of wealth resembles the Kelley betting strategy and ensures that the trader never loses more than \$1\. $\mathrm{Wealth}_i - 1$ is a lower bound on ${\overline{T}}$’s worth in any world $\mathbb{W}\in\mathcal{PC}(D_{f(i)})$, based on trades ${\overline{T}}$ makes on ${\mathbb{R}}$\-combinations $A_{f(1)}$ through $A_{f(i-1)}$. Thus, since the number of copies of $A_n$ that ${\overline{T}}$ buys is no more than $\varepsilon$ times its current wealth, and $\|A_n\| \leq 1$, $T$’s minimum worth is bounded below by $-1$.

Now it will be useful to write $\mathrm{Wealth}_i$ in log space. Intuitively, this should be enlightening because $T$ always bets a fraction of its wealth (similar to a Kelley bettor), so its winnings multiply over time rather than adding. By induction, 

$$
\log \mathrm{Wealth}_i
= \sum_{j\le i-1} \log \left(1 + \varepsilon w_j (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)}))\right)
$$

 This statement is trivial when $i=1$. For the inductive step, we have 

$$
\begin{align*}
  \log \mathrm{Wealth}_{i+1}
  &=
  \log \left(\mathrm{Wealth}_i + \beta_i (\mathbb{P}_{f(i+1)}(A_{f(i)}) - \mathbb{P}_{f(i)}(A_{f(i)})) \right)
  \\
  &=
  \log \left(\mathrm{Wealth}_i + \varepsilon \cdot \mathrm{Wealth}_i \cdot w_i (\mathbb{P}_{f(i+1)}(A_{f(i)}) - \mathbb{P}_{f(i)}(A_{f(i)})) \right)
  \\
  &=
  \log \mathrm{Wealth}_i + \log\left(1 + \varepsilon w_j (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)}))\right)
  \\
  &=
  \sum_{j\le i} \log \left(1 + \varepsilon w_j (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)}))\right)
\end{align*}
$$

For $|x| \leq 1/2$, we have $\log (1 + x) \geq x - x^2$. Therefore, since $\varepsilon < 1/4$, $w_j \leq 1$, and $|\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(i)}(A_{f(j)})| \leq 1$,

$$
\begin{align*}
  \log \mathrm{Wealth}_i &\geq
  \sum_{j\le i-1} \Big(
    \varepsilon w_j (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)})) \\[-1em]
    & \phantom{xxxxxxxx} - \varepsilon^2 w_j^2 (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)}))^2
  \Big)
  \\
  &\geq
  \sum_{j\le i-1} \left( \varepsilon w_j (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)})) - \varepsilon^2w_j \right)
  \\
  &=
  \sum_{j\le i-1} \varepsilon w_j\left( (\mathbb{P}_{f(j+1)}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)})) - \varepsilon \right)
\end{align*}
$$

At this point, it will be useful to show a relation between $\mathbb{P}_{f(j+1)}(A_{f(j)})$ and $\operatorname{Val}_{\Gamma}(A_{f(j)})$. Consider the sequence 

$$
A'_n:= \begin{cases}
  A_{f(i)} - \operatorname{Val}_{\Gamma}(A_{f(i)})& \textnormal{if \(\exists i: f(i+1) = n\)}
  \\
  0 & \textnormal{otherwise}
\end{cases}
$$

 which is in $\mathcal{BCS}({\overline{\mathbb{P}}})$ because $\operatorname{Val}_{\Gamma}(A_{f(j)})$ is computable in time polynomial in $f(j+1)$. Of course, each $A'_n$ has value 0 in any world $\mathbb{W}\in \mathcal{PC}(\Gamma)$. So by Theorem 121 (Affine Provability Induction), 

$$
\mathbb{P}_n(A'_n) \eqsim_n0
$$

 so for all sufficiently high $j$, $\mathbb{P}_{f(j+1)}(A_{f(j)}) \geq \operatorname{Val}_{\Gamma}(A_{f(j)})-\varepsilon$. Thus, for some constant $C$, 

$$
\begin{align*}
  \log \mathrm{Wealth}_i
  &\geq
  \sum_{j\le i-1} \varepsilon w_j \left( (\operatorname{Val}_{\Gamma}(A_{f(j)}) - \mathbb{P}_{f(j)}(A_{f(j)})) - 2 \varepsilon \right) - C
  \\
  &=
  \varepsilon \left( \sum_{j\le i-1} w_j \right) (-\mathrm{Bias}_{i-1} - 2 \varepsilon) - C
\end{align*}
$$

Now, for infinitely many $i$ it is the case that $\mathrm{Bias}_{i-1} < - 3 \varepsilon$. So it is infinitely often the case that $\log \mathrm{Wealth}_i \geq \varepsilon^2 \sum_{j\le i - 1} w_i - C$. Since ${\overline{w}}$ is divergent, $T$’s eventual wealth (and therefore max profit) can be arbitrarily high. Thus, $T$ exploits ${\overline{\mathbb{P}}}$. ◻

### Unbiasedness From Feedback ^unbiasedness-from-feedback

**Theorem 135** (Unbiasedness From Feedback). _Let ${\overline{\phi}}$ be any e.c. sequence of decidable sentences, and ${\overline{w}}$ be any ${\overline{\mathbb{P}}}$\-generable divergent weighting. If there exists a strictly increasing deferral function $f$ such that the support of ${\overline{w}}$ is contained in the image of $f$ and $\operatorname{Thm}_{\Gamma}(\phi_{f(n)})$ is computable in ${\mathcal{O}}(f(n+1))$ time, then 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot(\mathbb{P}_i(\phi_i)-\operatorname{Thm}_{\Gamma}(\phi_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{\phi}}$”._

_Proof._ This is a special case of Theorem 134 (Affine Unbiasedness from Feedback). ◻

### Learning Pseudorandom Affine Sequences ^learning-pseudorandom-affine-sequences

**Theorem 136** (Learning Pseudorandom Affine Sequences). _Given a ${\overline{A}}\in \mathcal{BCS}({\overline{\mathbb{P}}})$ which is determined via $\Gamma$, if there exists deferral function $f$ such that for any ${\overline{\mathbb{P}}}$\-generable $f$\-patient divergent weighting ${\overline{w}}$, 

$$
\frac{\sum_{i \leq n} w_i  \cdot \operatorname{Val}_{\Gamma}(A_i )}{\sum_{i \leq n} w_i } \gtrsim_n0,
$$

 then 

$$
\mathbb{P}_n(A_n) \gtrsim_n0,
$$

 and similarly for $\eqsim_n$, and $\lesssim_n$._

_Proof._ We will prove the statement in the case of $\gtrsim_n$; the case of $\lesssim_n$ follows by negating the ${\mathbb{R}}$\-combination sequence ${\overline{A}}$, and the case of $\eqsim_n$ follows from the conjunction of the other two cases. Suppose it is not the case that $\mathbb{P}_n(A_n) \gtrsim_n0$. Then there is a rational $\varepsilon > 0$ such that $\mathbb{P}_n(A_n) < - 2 \varepsilon$ infinitely often.

##### Defining the trader. ^defining-the-trader-2

Let ${\overline{{A^\dagger}}}$ be an e.c. $\mathcal{E\!F}$\-combination progression such that ${A_n^\dagger} ({\overline{\mathbb{P}}})= A_n$. Let an affine combination $A$ be considered _settled_ by day $m$ if $\mathbb{W}(A) = \operatorname{Val}_{\Gamma}(A)$ for each $\mathbb{W}\in \mathcal{PC}(D_m)$. We may write $\mathrm{Settled}(n, m)$ to be the proposition that $A_n$ is settled by day $m$. $\mathrm{Settled}(n, m)$ is decidable; let $\texttt{settled}$ be a Turing machine deciding $\mathrm{Settled}(n, m)$ given $(n, m)$. Now we define a lower-approximation to $\mathrm{Settled}$:

$$
\mathrm{DefinitelySettled}(n, m) :\leftrightarrow \exists i \leq m: \texttt{settled}(n, i) \textnormal{~returns true within \(m\) steps}.
$$

Note that

-   $\mathrm{DefinitelySettled}(n, m)$ can be decided in time polynomial in $m$ when $n\leq m$,
    
-   $\mathrm{DefinitelySettled}(n, m) \rightarrow \mathrm{Settled}(n, m)$, and
    
-   If $\mathrm{Settled}(n, m)$, then $\mathrm{DefinitelySettled}(n, M)$ for some $M \geq m$.
    

To define the trader, first we will define ${\overline{{\alpha^\dagger}}}$ recursively by

$$
\begin{align*}
  {\alpha_n^\dagger} &:= (1 - {C_n^\dagger} ) \operatorname{Ind}_{\textnormal{\small{\({\varepsilon}\)}}}(A_n^{\dagger* n}  < - \varepsilon)
\\
{C_n^\dagger} &:= \sum_{i < n} [\neg\mathrm{DefinitelySettled}(i, n) \vee f(i) > n] \cdot {\alpha_i^\dagger}.
\end{align*}
$$

The trader itself buys ${\alpha_n^\dagger} ({\overline{\mathbb{P}}})$ copies of the combination ${A^\dagger}_n ({\overline{\mathbb{P}}})$ on day $n$:

$$
T_n:= {\alpha_n^\dagger} \cdot ({A_n^\dagger} - A_n^{\dagger * n}).
$$

Intuitively, ${C_n^\dagger}$ is the total number of copies of ${\mathbb{R}}$\-combinations that the trader has bought that are either possibly-unsettled (according to $\mathrm{DefinitelySettled}$), or whose deferral time $f(i)$ is past the current time $n$.

##### Analyzing the trader. ^analyzing-the-trader-3

As shorthand, define $\alpha_n:= {\alpha_n^\dagger} ({\overline{\mathbb{P}}})$ and $C_n := {C_n^\dagger} ({\overline{\mathbb{P}}})$. Some important properties of ${\overline{T}}$ are:

-   Each $C_n\leq 1$.
    
-   $\alpha_n= 1 - C_n$ when $\mathbb{P}_n(A_n) < - 2 \varepsilon$.
    
-   Whenever $\alpha_n> 0$, $\mathbb{P}_n(A_n) < - \varepsilon$.
    
-   $\sum_{n\in {{\mathbb{N}}^+}} \alpha_n=\infty$. Suppose this sum were finite. Then there is some time $N$ for which $\sum_{n\geq N} \alpha_n< 1/2$. For some future time $N'$, and each $n< N$, we have $\mathrm{DefinitelySettled}(n, N') \wedge f(n) \leq N'$. This implies that $C_n< 1/2$ for each $n\geq N'$. However, consider the first $n\geq N'$ for which $\mathbb{P}_n(A_n) < - 2 \varepsilon$. Since $C_n< 1/2$, $\alpha_n \geq 1/2$. But this contradicts $\sum_{n \geq N} \alpha_n < 1/2$.
    

Let $b \in {\mathbb{Q}}$ be such that each ${\|A_n\|_{\rm mg}} < b$. Consider this trader’s profit at time $m$ in world $\mathbb{W}\in\mathcal{PC}(D_m)$:

$$
\begin{align*}
& \sum_{n\leq m} \alpha_n(\mathbb{W}(A_n) - \mathbb{P}_n(A_n))
\\
\geq &
\sum_{n\leq m} \alpha_n(\mathbb{W}(A_n) + \varepsilon)
\\
\geq &
\sum_{n\leq m} \alpha_n(\operatorname{Val}_{\Gamma}(A_n) + \varepsilon) - 2b
\end{align*}
$$

where the last inequality follows because $\sum_{n \leq m} [ \neg \mathrm{Settled}(n, m) ] \alpha_n \leq 1$, and an unsettled copy of $A_n$ can only differ by $2b$ between worlds, while settled copies of $A_n$ must have the same value in all worlds in $\mathcal{PC}(D_m)$.

$T$ holds no more than 1 copy of ${\mathbb{R}}$\-combinations unsettled by day $M$, and an unsettled combination’s value can only differ by $2b$ between different worlds while settled affine combinations must have the same value in different worlds in $\mathcal{PC}(D_m)$. We now show that this quantity goes to $\infty$, using the fact that ${\overline{A}}$ is pseudorandomly positive.

Observe that ${\overline{{\alpha}}}$ is a divergent weighting. It is also $f$\-patient, since $\sum_{n \leq m} [f(n) \geq m] \alpha_n \leq 1$. So by assumption,

$$
\lim\inf_{m\rightarrow\infty}
\frac{\sum_{n\leq m}\alpha_n\cdot \operatorname{Val}_{\Gamma}(A_n)}
{\sum_{n\leq m}\alpha_n} \geq 0.
$$

At this point, note that

$$
\sum_{n\leq m} \alpha_n (\operatorname{Val}_{\Gamma}(A_n) + \varepsilon) =
  \left(\sum_{n \leq m} \alpha_n\right)
  \left( \frac{\sum_{n\leq m}\alpha_n\cdot \operatorname{Val}_{\Gamma}(A_n)}{\sum_{n\leq m}\alpha_n}
    + \varepsilon
  \right).
$$

For all sufficiently high $m$, $\frac{\sum_{n\leq m}\alpha_n\cdot \operatorname{Val}_{\Gamma}(A_n)}{\sum_{n\leq m}\alpha_n} \geq -\varepsilon/2$, and $\sum_{n \in {\mathbb{N}}^+} \alpha_n = \infty$, so

$$
\lim\inf_{m\rightarrow\infty} \sum_{n\leq m} \alpha_n(\operatorname{Val}_{\Gamma}(A_n) + \varepsilon) =\infty.
$$

If we define $g(m)$ to be the minimum plausible worth at time $m$ over plausible worlds $\mathbb{W}\in\mathcal{PC}(D_m)$, we see that $g(m)$ limits to infinity, implying that the trader’s maximum worth goes to infinity. The fact that $g(m)$ limits to infinity also implies that $g(m)$ is bounded from below, so the trader’s minimum worth is bounded from below. Thus, this trader exploits the market ${\overline{\mathbb{P}}}$. ◻

### Learning Varied Pseudorandom Frequencies ^learning-varied-pseudorandom-frequencies

**Definition 137** (Varied Pseudorandom Sequence). _Given a deferral function $f$, a set $S$ of $f$\-patient divergent weightings, an e.c. sequence ${\overline{\phi}}$ of $\Gamma$\-decidable sentences, and a ${\overline{\mathbb{P}}}$\-generable sequence ${\overline{p}}$ of rational probabilities, ${\overline{\phi}}$ is called a **$\boldsymbol{{\overline{p}}}$\-varied pseudorandom sequence** (relative to $S$) if, for all ${\overline{w}}\in S$, 

$$
\frac{\sum_{i \leq n} w_i \cdot (p_i- \operatorname{Thm}_{\Gamma}(\phi_i))}{\sum_{i \leq n} w_i} \eqsim_n0.
$$

 Furthermore, we can replace $\eqsim_n$ with $\gtrsim_n$ or $\lesssim_n$, in which case we say ${\overline{\phi}}$ is **varied pseudorandom above $\boldsymbol{{\overline{p}}}$** or **varied pseudorandom below $\boldsymbol{{\overline{p}}}$**, respectively._

**Theorem 138** (Learning Varied Pseudorandom Frequencies). _Given an e.c. sequence ${\overline{\phi}}$ of $\Gamma$\-decidable sentences and a ${\overline{\mathbb{P}}}$\-generable sequence ${\overline{p}}$ of rational probabilities, if there exists some $f$ such that ${\overline{\phi}}$ is ${\overline{p}}$\-varied pseudorandom (relative to all $f$\-patient ${\overline{\mathbb{P}}}$\-generable divergent weightings), then 

$$
\mathbb{P}_n(\phi_n) \eqsim_np_n.
$$

 Furthermore, if ${\overline{\phi}}$ is varied pseudorandom above or below ${\overline{p}}$, then the $\eqsim_n$ may be replaced with $\gtrsim_n$ or $\lesssim_n$ (respectively)._

_Proof._ We will prove the statement in the case of pseudorandom above; the case of pseudorandom below is analogous, and the case of pseudorandom follows from the other cases.

Define $A_n := \phi_n - p_n$ and note that ${\overline{A}}\in \mathcal{BCS}({\overline{\mathbb{P}}})$. Observe that, because ${\overline{A}}$ is varied pseudorandomness above ${\overline{p}}$, for any $f$\-patient divergent weighting $w$, 

$$
\frac{\sum_{i \leq n} w_i \operatorname{Val}_{\Gamma}{A_n}}{\sum_{i \leq n} w_i} \gtrsim_n 0.
$$

 Now apply Theorem 136 (Learning Pseudorandom Affine Sequences) to get

$$
\mathbb{P}_n(A_n) = \mathbb{P}_n(\phi_n) - p_n \gtrsim_n 0.
$$

 ◻

### Learning Pseudorandom Frequencies ^learning-pseudorandom-frequencies-2

**Definition 139** (Pseudorandom Sequence). _Given a set $S$ of divergent weightings (Definition 27), a sequence ${\overline{\phi}}$ of decidable sentences is called **pseudorandom with frequency $\boldsymbol{p}$** over $S$ if, for all weightings ${\overline{w}}\in S$, 

$$
\lim_{n\to\infty} \frac{\sum_{i \leq n} w_i \cdot \operatorname{Thm}_{\Gamma}(\phi_i)}{\sum_{i \leq n} w_i}
$$

 exists and is equal to $p$._

**Theorem 140** (Learning Pseudorandom Frequencies). _Let ${\overline{\phi}}$ be an e.c. sequence of decidable sentences. If ${\overline{\phi}}$ is pseudorandom with frequency $p$ over the set of all ${\overline{\mathbb{P}}}$\-generable divergent weightings, then 

$$
\mathbb{P}_n(\phi_n) \eqsim_np.
$$

_

_Proof._ Let $q$ be any rational number less than $p$. Note that ${\overline{\phi}}$ is varied pseudorandom above $q$, so by Theorem 138 (Learning Varied Pseudorandom Frequencies), 

$$
\mathbb{P}_n(\phi_n) \gtrsim_n q.
$$

 But we could have chosen any rational $q < p$, so $\mathbb{P}_n(\phi_n) \gtrsim_n p$. An analogous argument shows $\mathbb{P}_n(\phi_n) \lesssim_n p$. ◻

## Expectations Proofs ^expectations-proofs

### Consistent World LUV Approximation Lemma ^consistent-world-luv-approximation

**Lemma 141**. _Let ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$ be a ${\mathbb{R}}$\-LUV combination bounded by some rational number $b$. For all natural numbers $n$ and all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, we have 

$$
| {\mathbb{E}}_n^\mathbb{W}(B) - \mathbb{W}(B)| \leq b/n.
$$

_

_Proof._ Let $\mathbb{W}\in \mathcal{PC}(\Gamma)$. For any $[0, 1]$\-LUV X, by Definition 57, 

$$
|{\mathbb{E}}_n^\mathbb{W}(X) - \mathbb{W}(X)| = \left|\sum_{i=0}^{n-1}\frac{1}{n} \mathbb{W}\left(\text{“}{\underline{X}} > {\underline{i}}/{\underline{n}}\text{”} \right) - \mathbb{W}(X) \right|
$$

 Since $\Gamma$ can represent computable functions, the number of $i$ values in $\{0, \ldots, n-1\}$ for which $\mathbb{W}(\text{“}{\underline{X}} > {\underline{i}}/{\underline{n}}\text{”}) = 1$ is at least $\lfloor n \mathbb{W}(X) \rfloor \geq n\mathbb{W}(X) - 1$, so 

$$
\sum_{i=0}^{n-1}\frac{1}{n} \mathbb{W}\left(\text{“}{\underline{X}} > {\underline{i}}/{\underline{n}}\text{”} \right) \geq \mathbb{W}(X) - 1/n.
$$

 Similarly, the number of $i$ values in $\{0, \ldots, n-1\}$ for which $\mathbb{W}(\text{“}{\underline{X}} > {\underline{i}}/{\underline{n}}\text{”})$ is no more than $\lceil n\mathbb{W}(X)  \rceil \leq n\mathbb{W}(X) + 1$, so 

$$
\sum_{i=0}^{n-1}\frac{1}{n} \mathbb{W}\left(\text{“}{\underline{X}} > {\underline{i}}/{\underline{n}}\text{”} \right) \leq \mathbb{W}(X) + 1/n.
$$

 We now have 

$$
\begin{align*}
    |{\mathbb{E}}_n^\mathbb{W}(B) - \mathbb{W}(B)| &= |c_1 ({\mathbb{E}}_n^\mathbb{W}(X_1) - \mathbb{W}(X_1)) + \cdots + c_k ({\mathbb{E}}_n^\mathbb{W}(X_k) - \mathbb{W}(X_k))|
    \\
    &\leq c_1 |{\mathbb{E}}_n^\mathbb{W}(X_1) - \mathbb{W}(X_1)| + \cdots + c_k |{\mathbb{E}}_n^\mathbb{W}(X_k) - \mathbb{W}(X_k)|
    \\
    &\leq c_1 /n + \cdots + c_k/n
    \\
    &\leq b/n.
\end{align*}
$$

 ◻

### Mesh Independence Lemma ^mesh-independence-lemma

**Lemma 142**. _Let ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\lim_{n \to \infty} \sup_{m \geq n} |{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| = 0.
$$

_

_Proof._ We will prove the claim that 

$$
\limsup_{m \to \infty} \max_{n \leq m}\left(  |{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| -(2/n) \right) \leq 0 .
$$

 This claim implies that, for any $\varepsilon > 0$, there are only finitely many $(n, m)$ with $n \leq m$ such that $|{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| > 2/n + \varepsilon$, which in turn implies that, for any $\varepsilon' > 0$, there are only finitely many $(n, m)$ with $n \leq m$ such that $|{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| > \varepsilon'$. This is sufficient to show the statement of the theorem.

We will now prove 

$$
\limsup_{m \to \infty} \max_{n \leq m}\left(  {\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n) -(2/n) \right) \leq 0 .
$$

 The proof with ${\mathbb{E}}_m(B_n) - {\mathbb{E}}_n^{\mathbb{P}_m}(B_n)$ instead is analogous, and together these inequalities prove the claim.

Suppose this inequality does not hold. Then there is some rational $\varepsilon > 0$ such that for infinitely many $m$, 

$$
\max_{n \leq m} ({\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n) - (2/n)) >  \varepsilon.
$$

Let ${\overline{{B^\dagger}}}$ be an e.c. $\mathcal{E\!F}$\-combination progression such that ${B_n^\dagger} ({\overline{\mathbb{P}}})= B_n$. Assume without loss of generality that each $\|B_n\|_1 \leq 1$ (they are assumed to be bounded and can be scaled down appropriately). Define $\mathcal{E\!F}$\-combinations 

$$
{A_{n,m}^\dagger} := \mathrm{Ex}_n({B_n^\dagger}) - \mathrm{Ex}_m({B_n^\dagger}) - 2/n,
$$

 using the $\mathcal{F}$\-combinations $\mathrm{Ex}$ defined in [[#^mathcal-f-combinations-corresponding|8.3.3]]. As shorthand, we write $A_{n,m} := {A_{n,m}^\dagger} ({\overline{\mathbb{P}}})$. By Lemma 141, for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(A_{n, m}) \leq 0$. We aim to show $\mathbb{P}_m(A_{n, m}) < \varepsilon$ for all sufficiently high $m$ and $n \leq m$, but we cannot immediately derive this using Theorem 121 (Affine Provability Induction), since $A$ has two indices. We get around this difficulty by taking a “softmax” over possible values of $n$ given a fixed value of $m$. Specifically, for $n \leq m$, define expressible features (of rank $m$) 

$$
{\alpha_{n,m}^\dagger} := \operatorname{Ind}_{\textnormal{\small{\({\varepsilon/2}\)}}}\left(A_{n,m}^{\dagger* m} > \varepsilon/2\right) \cdot \left(1 - \sum_{i < n} {\alpha_{i,m}^\dagger}\right).
$$

 As shorthand, we write $\alpha_{n, m} := {\alpha_{n,m}^\dagger} ({\overline{\mathbb{P}}})$. Intuitively, $\alpha_{n,m}$ will distribute weight among $n$ values for which $A_{m,n}$ is overpriced at time $m$. Now we define the $\mathcal{E\!F}$\-combination progression 

$$
{G_m^\dagger} := \sum_{n \leq m} \alpha_{n,m} \cdot {A_{n,m}^\dagger}.
$$

 As shorthand, we write $G_{m} := {G_m^\dagger} ({\overline{\mathbb{P}}})$. Fix $m$ and suppose that $\mathbb{P}_m(A_{n,m}) \geq \varepsilon$ for some $n \leq m$. Then $\sum_{n \leq m} \alpha_{n, m} = 1$. Therefore, 

$$
\mathbb{P}_m(G_m) = \sum_{n \leq m} \alpha_{n, m} \mathbb{P}_m(A_{n,m}) \geq \sum_{n \leq m} \alpha_{n,m} \cdot \varepsilon / 2 = \varepsilon / 2.
$$

So if we can show $\mathbb{P}_m(G_m) \lesssim_m 0$, that will be sufficient to show that $\max_{n \leq m} \mathbb{P}_m(A_{n,m}) < \varepsilon$ for all sufficiently high $m$. We now show this. Let $\mathbb{W}\in \mathcal{PC}(\Gamma)$. Since each $\alpha_{n,m} \geq 0$, and $\mathbb{W}(A_{n,m}) \leq 0$, we have $\mathbb{W}(G_m) \leq 0$. So by Theorem 121 (Affine Provability Induction), $\mathbb{P}_m(G_m) \lesssim_m 0$; here we use that $(G_m)_m$ is bounded, since the $A_{n,m}$ are bounded and since for each $m$, $\sum_{n \leq m} \alpha_{n, m} \leq  1$ by construction.

So for all sufficiently high $m$ we have $\max_{n \leq m} \mathbb{P}_m(A_{n,m}) < \varepsilon$ (or equivalently, $\max_{n \leq m} ({\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)) < 2/n + \varepsilon$). But this contradicts our assumption that for infinitely many $m$,

$$
\max_{n \leq m} ({\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)-(2/n)) >  \varepsilon.
$$

 ◻

### Expectation Preemptive Learning ^expectation-preemptive-learning

**Theorem 143** (Expectation Preemptive Learning). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\to\infty} {\mathbb{E}}_n(B_n)= \liminf_{n\rightarrow\infty}\sup_{m\geq n} {\mathbb{E}}_m(B_n)
$$

 and 

$$
\limsup_{n\to\infty} {\mathbb{E}}_n(B_n)= \limsup_{n\rightarrow\infty}\inf_{m\geq n} {\mathbb{E}}_m(B_n) \ .
$$

_

_Proof._ We prove only the first statement; the proof of the second statement is analogous. Apply Theorem 116 (Affine Preemptive Learning) to the bounded sequence $(\mathrm{Ex}_n(B_n))_n$ to get 

$$
\liminf_{n\to\infty} {\mathbb{E}}_n^{\mathbb{P}_n}(B_n) = \liminf_{n\rightarrow\infty}\sup_{m\geq n} {\mathbb{E}}_n^{\mathbb{P}_m}(B_n),
$$

 using that by definition $\mathbb{P}_m (\mathrm{Ex}_n(B_n)) = {\mathbb{E}}_n^{\mathbb{P}_m}(B_n)$. By Lemma 142, 

$$
\lim_{n\rightarrow\infty}\sup_{m\geq n} |{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| = 0
$$

 so 

$$
\liminf_{n\rightarrow\infty}\sup_{m\geq n} {\mathbb{E}}_n^{\mathbb{P}_m}(B_n) =
\liminf_{n\rightarrow\infty}\sup_{m\geq n} {\mathbb{E}}_m(B_n).
$$

 ◻

### Expectations Converge ^expectations-converge

**Theorem 144** (Expectations Converge). _The limit ${{\mathbb{E}}_\infty:\mathcal{S}\rightarrow[0,1]}$ defined by 

$$
{\mathbb{E}}_\infty(X) := \lim_{n\rightarrow\infty} {\mathbb{E}}_n(X)
$$

 exists for all $X \in \mathcal{U}$._

_Proof._ By applying Theorem 143 (Expectation Preemptive Learning) to the constant sequence $X, X, \ldots$, we have

$$
\liminf_{n \to \infty} {\mathbb{E}}_n(X) = \liminf_{n \to \infty} \sup_{m \geq n} {\mathbb{E}}_m(X) = \limsup_{n \to \infty} {\mathbb{E}}_n(X) .
$$

 ◻

### Limiting Expectation Approximation Lemma ^limiting-expectation-approximation-lemma

**Lemma 145**. _For any ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$, 

$$
| {\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n) - {\mathbb{E}}_\infty(B_n)| \eqsim_n 0.
$$

_

_Proof._ By Lemma 142 and by continuity of $\mathbb{V}\mapsto {\mathbb{E}}_n^{\mathbb{V}}(B_n)$, 

$$
\begin{align*}
   \lim_{n \to \infty} | {\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n) - {\mathbb{E}}_\infty(B_n)|
    &= \lim_{n \to \infty} \lim_{m \to \infty} | {\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| \\
        &\leq \lim_{n \to \infty} \sup_{m \geq n} | {\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| \\
  &= 0 .
\end{align*}
$$

 ◻

### Persistence of Expectation Knowledge ^persistence-of-expectation-knowledge

**Theorem 146** (Persistence of Expectation Knowledge). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}{\mathbb{E}}_m(B_n)= \liminf_{n\to\infty}{\mathbb{E}}_\infty(B_n)
$$

 and 

$$
\limsup_{n\rightarrow\infty}\sup_{m\geq n}{\mathbb{E}}_m(B_n)=\limsup_{n\to\infty}{\mathbb{E}}_\infty(B_n).
$$

_

_Proof._ We prove only the first statement; the proof of the second statement is analogous. Apply Theorem 42 (Persistence of Affine Knowledge) to $(\mathrm{Ex}_n(B_n))_n$ to get 

$$
\liminf_{n\rightarrow\infty}\inf_{m\geq n}{\mathbb{E}}_n^{\mathbb{P}_m}(B_n)= \liminf_{n\to\infty}{\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n).
$$

 We now show equalities on these two terms:

1.  By Lemma 142, 
    
    $$
    \lim_{n\rightarrow\infty}\sup_{m\geq n}|{\mathbb{E}}_n^{\mathbb{P}_m}(B_n) - {\mathbb{E}}_m(B_n)| = 0
    $$
    
     so 
    
    $$
    \liminf_{n\rightarrow\infty}\inf_{m\geq n}{\mathbb{E}}_m(B_n)=
        \liminf_{n\rightarrow\infty}\inf_{m\geq n}{\mathbb{E}}_n^{\mathbb{P}_m}(B_n).
    $$
    
2.  By Lemma 145, 
    
    $$
    \liminf_{n\to\infty}{\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n) = \liminf_{n \to \infty} {\mathbb{E}}_\infty(B_n).
    $$
    

Together, these three equalities prove the theorem statement. ◻

### Expectation Coherence ^expectation-coherence

**Theorem 147** (Expectation Coherence). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$. Then 

$$
\liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(B_n)
    \le \liminf_{n\rightarrow\infty}
      {\mathbb{E}}_\infty(B_n)
    \le \liminf_{n\to\infty}
      {\mathbb{E}}_n(B_n),
$$

 and 

$$
\limsup_{n\to\infty} {\mathbb{E}}_n(B_n)
    \le \limsup_{n\rightarrow\infty} {\mathbb{E}}_\infty(B_n)
    \le \limsup_{n\rightarrow\infty} \sup_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      \mathbb{W}(B_n).
$$

_

_Proof._ We prove only the first statement; the proof of the second statement is analogous. Apply Theorem 120 (Affine Coherence) to $(\mathrm{Ex}_n(B_n))_n$ to get 

$$
\liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)}
      {\mathbb{E}}_n^\mathbb{W}(B_n)
    \le
    \liminf_{n\rightarrow\infty}
    {\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n)
    \le \liminf_{n\to\infty}
    {\mathbb{E}}_n(B_n),
$$

 We now show equalities on the first two terms:

1.  Let $b$ be the bound on ${\overline{B}}$. By Lemma 141, 
    
    $$
    \liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)} |{\mathbb{E}}_n^\mathbb{W}(B_n) - \mathbb{W}(B_n)|
          \leq \liminf_{n \to \infty} \inf_{\mathbb{W}\in \mathcal{PC}(\Gamma)} b/n = 0
    $$
    
     so 
    
    $$
    \liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)} {\mathbb{E}}_n^\mathbb{W}(B_n)
          =
          \liminf_{n\rightarrow\infty}\inf_{\mathbb{W}\in\mathcal{PC}(\Gamma)} \mathbb{W}(B_n).
    $$
    
2.  By Lemma 145, 
    
    $$
    \liminf_{n\rightarrow\infty}
          |{\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n) - {\mathbb{E}}_\infty(B_n)| = 0
    $$
    
     so 
    
    $$
    \liminf_{n\rightarrow\infty}{\mathbb{E}}_n^{\mathbb{P}_\infty}(B_n)
          =
          \liminf_{n\rightarrow\infty}{\mathbb{E}}_\infty(B_n).
    $$
    

Together, these three equalities prove the theorem statement. ◻

### Expectation Provability Induction ^expectation-provability-induction

**Theorem 148** (Expectation Provability Induction). _Let ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$ and $b \in {\mathbb{R}}$. If, for all consistent worlds $\mathbb{W}\in\mathcal{PC}(\Gamma)$ and all $n\in {\mathbb{N}}^+$, it is the case that $\mathbb{W}(B_n ) \ge b$, then 

$$
{\mathbb{E}}_n(B_n) \gtrsim_nb,
$$

 and similarly for $=$ and $\eqsim_n$, and for $\leq$ and $\lesssim_n$._

_Proof._ We prove the statement in the case of $\geq$; the case of $\leq$ is analogous, and the case of $=$ follows from the conjunction of the other two cases. By Theorem 147 (Expectation Coherence),

$$
\liminf_{n \to \infty} {\mathbb{E}}_n(B_n) \geq \liminf_{n \to \infty} \inf_{\mathbb{W}\in \mathcal{PC}(\Gamma)} \mathbb{W}(B_n) \geq b.
$$

 We will usually apply this theorem using the $=$ case. ◻

### Linearity of Expectation ^linearity-of-expectation

**Theorem 149** (Linearity of Expectation). _Let ${\overline{a}}, {\overline{b}}$ be bounded ${\overline{\mathbb{P}}}$\-generable sequences of rational numbers, and let ${\overline{X}}, {\overline{Y}}$, and ${\overline{Z}}$ be e.c. sequences of $[0,1]$\-LUVs. If we have $\Gamma\vdash{Z_n= a_nX_n+ b_nY_n}$ for all $n$, then 

$$
a_n{\mathbb{E}}_n(X_n) + b_n{\mathbb{E}}_n(Y_n) \eqsim_n{\mathbb{E}}_n(Z_n).
$$

_

_Proof._ Observe that $\mathbb{W}(a_n X_n + b_n Y_n - Z_n) = 0$ for all $n$ and $\mathbb{W}\in \mathcal{PC}(\Gamma)$. So by Theorem 148 (Expectation Provability Induction), ${\mathbb{E}}_n(a_n X_n + b_n Y_n - Z_n) \eqsim_n 0$; the theorem statement immediately follows from the definition of ${\mathbb{E}}_n$ applied to a LUV-combination (where $a_n X_n + b_n Y_n - Z_n$ is interpreted as a LUV-combination, not another LUV). ◻

### Expectations of Indicators ^expectations-of-indicators

**Theorem 150** (Expectations of Indicators). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
{\mathbb{E}}_n(\mathop{\mathrm{\mathbb{1}}}(\phi_n)) \eqsim_n\mathbb{P}_n(\phi_n).
$$

_

_Proof._ Observe that $\mathbb{W}(\mathrm{Ex}_n(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right))) = \mathbb{W}(\phi_n)$ for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$; either

-   $\mathbb{W}(\phi) = 0$ and $\mathbb{W}(\mathrm{Ex}_n(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right))) = \sum_{i=0}^{n-1} \frac{1}{n} \mathbb{W}(\text{“}{\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} > {\underline{i}}/{\underline{n}}\text{”}) = \sum_{i=0}^{n-1} 0 = 0$, or
    
-   $\mathbb{W}(\phi) = 1$ and $\mathbb{W}(\mathrm{Ex}_n(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right))) = \sum_{i=0}^{n-1} \frac{1}{n} \mathbb{W}(\text{“}{\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} > {\underline{i}}/{\underline{n}}\text{”}) = \sum_{i=0}^{n-1} \frac{1}{n} = 1$.
    

So by Theorem 121 (Affine Provability Induction), 

$$
{\mathbb{E}}_n(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)) \eqsim_n \mathbb{P}_n(\phi_n).
$$

 ◻

### Expectation Recurring Unbiasedness ^expectation-recurring-unbiasedness

**Theorem 151** (Expectation Recurring Unbiasedness). _If ${\overline{B}}\in\mathcal{BLCS}({\overline{\mathbb{P}}})$ is determined via $\Gamma$, and ${\overline{w}}$ is a ${\overline{\mathbb{P}}}$\-generable divergent weighting weighting such that the support of ${\overline{w}}$ is contained in the image of $f$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-\operatorname{Val}_{\Gamma}(B_i))}
        {\sum_{i\leq n}w_i}
$$

 has $0$ as a limit point. In particular, if it converges, it converges to $0$._

_Proof._ Let $\mathbb{W}\in \mathcal{PC}(\Gamma)$. Apply Theorem 131 (Affine Recurring Unbiasedness) to $(\mathrm{Ex}_n(B_n))_n$ and ${\overline{w}}$ to get that

$$
\left( \frac{\sum_{i \leq n} w_i ({\mathbb{E}}_i(B_i) - {\mathbb{E}}_i^{\mathbb{W}}(B_i))}{\sum_{i \leq n}w_i} \right)_{n \in {\mathbb{N}}^+}
$$

has 0 as a limit point. Furthermore, by Lemma 141, $|{\mathbb{E}}_i^\mathbb{W}(B_i) - \operatorname{Val}_{\Gamma}(B_i)| \leq b/i$ where $b$ is a bound on ${\overline{B}}$. As a result, for any subsequence of 

$$
\left( \frac{\sum_{i \leq n} w_i ({\mathbb{E}}_i(B_i) - {\mathbb{E}}_i^{\mathbb{W}}(B_i))}{\sum_{i \leq n}w_i} \right)_{n \in {\mathbb{N}}^+}
$$

 that limits to zero, the corresponding subsequence of 

$$
\left( \frac{\sum_{i \leq n} w_i ({\mathbb{E}}_i(B_i) - \operatorname{Val}_{\Gamma}(B_i))}{\sum_{i \leq n}w_i} \right)_{n \in {\mathbb{N}}^+}
$$

 also limits to zero, as desired. ◻

### Expectation Unbiasedness From Feedback ^expectation-unbiasedness-from-feedback

**Theorem 152** (Expectation Unbiasedness From Feedback). _Given ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$ that is determined via $\Gamma$, a strictly increasing deferral function $f$ such that $\operatorname{Val}_{\Gamma}(A_n )$ can be computed in time ${\mathcal{O}}(f(n+1))$, and a ${\overline{\mathbb{P}}}$\-generable divergent weighting $w$, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-\operatorname{Val}_{\Gamma}(B_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 In this case, we say “${\overline{w}}$ allows good feedback on ${\overline{B}}$”._

_Proof._ Let $\mathbb{W}\in \mathcal{PC}(\Gamma)$. Note that if $\operatorname{Val}_{\Gamma}{B_n}$ can be computed in time polynomial in $g(n + 1)$, then so can $\operatorname{Val}_{\Gamma}{\mathrm{Ex}_k(B_n)}$. Apply Theorem 134 (Affine Unbiasedness from Feedback) to $(\mathrm{Ex}_n(B_n))_n$ to get 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-{\mathbb{E}}_i^\mathbb{W}(B_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 Furthermore, by Lemma 141, $|{\mathbb{E}}_i^\mathbb{W}(B_n) - \operatorname{Val}_{\Gamma}(B_n)| \leq b/n$ where $b$ is a bound on ${\overline{B}}$. As a result, 

$$
\frac
        {\sum_{i\leq n}w_i  \cdot({\mathbb{E}}_i(B_i)-\operatorname{Val}_{\Gamma}(B_i))}
        {\sum_{i\leq n}w_i}
    \eqsim_n0.
$$

 as desired. ◻

### Learning Pseudorandom LUV Sequences ^learning-pseudorandom-luv-sequences

**Theorem 153** (Learning Pseudorandom LUV Sequences). _Given a ${\overline{B}}\in \mathcal{BLCS}({\overline{\mathbb{P}}})$ which is determined via $\Gamma$, if there exists a deferral function $f$ such that for any ${\overline{\mathbb{P}}}$\-generable $f$\-patient divergent weighting ${\overline{w}}$, 

$$
\frac{\sum_{i \leq n} w_i  \cdot \operatorname{Val}_{\Gamma}(B_i )}{\sum_{i \leq n} w_i } \gtrsim_n0,
$$

 then 

$$
{\mathbb{E}}_n(B_n) \gtrsim_n0.
$$

_

_Proof._ We will prove the statement in the case of $\gtrsim$; the case of $\lesssim$ is analogous, and the case of $\eqsim$ follows from the other cases.

Let $b$ be the bound of ${\overline{B}}$. Let $\mathbb{W}\in \mathcal{PC}(\Gamma)$. First, note that by Lemma 141, $|{\mathbb{E}}_i^\mathbb{W}(B_i) - \operatorname{Val}_{\Gamma}(B_i)| \leq b/i$. Therefore, 

$$
\frac{\sum_{i \leq n} w_i \cdot {\mathbb{E}}_i^\mathbb{W}(B_i)}{\sum_{i \leq n} w_i} \eqsim_n \frac{ \sum_{i \leq n} w_i \cdot \operatorname{Val}_{\Gamma}(B_i)}{\sum_{i \leq n} w_i} \gtrsim_n 0.
$$

 So we may apply Theorem 136 (Learning Pseudorandom Affine Sequences) to $(\mathrm{Ex}_n(B_n))_n$ to get 

$$
{\mathbb{E}}_n(B_n) \gtrsim_n 0.
$$

 ◻

## Introspection and Self-Trust Proofs ^introspection-and-self-trust-proofs

### Introspection ^introspection-2

**Theorem 154** (Introspection). _Let ${\overline{\phi}}$ be an e.c. sequence of sentences, and ${\overline{a}}$, ${\overline{b}}$ be ${\overline{\mathbb{P}}}$\-generable sequences of probabilities. Then, for any e.c. sequence of positive rationals ${\overline{\delta}}\to 0$, there exists a sequence of positive rationals ${\overline{{\varepsilon}}}\to 0$ such that for all $n$:_

1.  _if $\mathbb{P}_n(\phi_n)\in(a_n+\delta_n,b_n-\delta_n)$, then 
    
    $$
    \mathbb{P}_n(\text{“}{\underline{a_n}} < {\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}}) < {\underline{b_n}}\text{”}) > 1-\varepsilon_n,
    $$
    
    _
    
2.  _if $\mathbb{P}_n(\phi_n)\notin(a_n-\delta_n,b_n+\delta_n)$, then 
    
    $$
    \mathbb{P}_n(\text{“}{\underline{a_n}} < {\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}}) < {\underline{b_n}}\text{”}) < \varepsilon_n.
    $$
    
    _
    

_Proof._ Define $\psi_n := \text{“}{\underline{a_n}} < {\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}}) < {\underline{b_n}}\text{”}$.

##### Proof of the first statement. ^proof-of-the-first

Observe that for all $n$, and all $\mathbb{W}\in\mathcal{PC}(\Gamma)$,

$$
\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(a_n < \mathbb{P}_n(\phi_n) < b_n) \cdot (1 - \mathbb{W}(\psi_n))=0,
$$

 since regardless of $\mathbb{P}_n(\phi_n)$, one of the two factors is 0. Thus, applying Theorem 121 (Affine Provability Induction) gives 

$$
\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(a_n < \mathbb{P}_n(\phi_n) < b_n) \cdot (1-\mathbb{P}_n(\psi_n)) \eqsim_n 0.
$$

 Define 

$$
\varepsilon_n := \operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(a_n < \mathbb{P}_n(\phi_n) < b_n) \cdot (1-\mathbb{P}_n(\psi_n)) + 1/n
$$

 and note that $\varepsilon_n > 0$ and $\varepsilon_n \eqsim_n 0$. For any $n$ for which $\mathbb{P}_n(\phi_n) \in (a_n+\delta_n,b_n-\delta_n)$, the first factor is 1, so $\mathbb{P}_n(\psi_n) = 1 - \varepsilon_n+1/n > 1 - \varepsilon_n$.

##### Proof of the second statement. ^proof-of-the-second

Observe that for all $n$, and all $\mathbb{W}\in\mathcal{PC}(\Gamma)$, 

$$
\left(\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n)<a_n)+\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n) > b_n)\right)\cdot \mathbb{W}(\psi_n)=0,
$$

 since regardless of $\mathbb{P}_n(\phi_n)$, one of the factors is 0. Thus, applying Theorem 121 (Affine Provability Induction) gives 

$$
\left(\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n)<a_n)+\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n) > b_n)\right)\cdot \mathbb{P}_n(\psi_n) \eqsim_n 0.
$$

 Define 

$$
\varepsilon_n := \left(\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n)<a_n)+\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(\mathbb{P}_n(\phi_n) > b_n)\right)\cdot \mathbb{P}_n(\psi_n) + 1/n
$$

 and note that $\varepsilon_n > 0$ and $\varepsilon_n \eqsim_n 0$. For any $n$ for which $\mathbb{P}_n(\phi_n)\notin (a_n-\delta_n,b_n+\delta_n)$, the first factor is 1, so $\mathbb{P}_n(\psi_n) < \varepsilon_n$. ◻

### Paradox Resistance ^paradox-resistance

**Theorem 155** (Paradox Resistance). _Fix a rational $p\in(0,1)$, and define an e.c. sequence of “paradoxical sentences” ${\overline{\chi^p}}$ satisfying 

$$
\Gamma\vdash{{{\underline{\chi^p_n}}} \leftrightarrow\left(
      {{\underline{\mathbb{P}}}_{{\underline{n}}}}({{\underline{\chi^p_n}}}) < {\underline{p}}
    \right)}
$$

 for all $n$. Then 

$$
\lim_{n\to\infty}\mathbb{P}_n(\chi^p_n)=p.
$$

_

_Proof._ We prove $\mathbb{P}_n(\phi_n) \gtrsim_n p$ and $\mathbb{P}_n(\phi_n) \lesssim_n p$ individually.

1.  Suppose it is not the case that $\mathbb{P}_n(\phi_n) \gtrsim_n p$, so $\mathbb{P}_n(\phi_n) < p - \varepsilon$ infinitely often for some $\varepsilon > 0$. Observe that for all $n$, and all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 
    
    $$
    \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) < p) \cdot (1 - \mathbb{W}(\phi_n)) = 0,
    $$
    
     since regardless of $\mathbb{P}_n(\phi_n)$, one of the factors is 0. Thus, applying Theorem 121 (Affine Provability Induction) yields 
    
    $$
    \begin{equation}
    \tag{155a}
            \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) < p) \cdot (1 - \mathbb{P}_n(\phi_n)) \eqsim_n 0.
    \end{equation}
    $$
    
     But infinitely often, 
    
    $$
    \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) < p) \cdot (1 - \mathbb{P}_n(\phi_n)) \geq 1 \cdot (1 - (p - \varepsilon)) \geq \varepsilon
    $$
    
     which contradicts equation (155a).
    
2.  Suppose it is not the case that $\mathbb{P}_n(\phi_n) \lesssim_n p$, so $\mathbb{P}_n(\phi_n) > p + \varepsilon$ infinitely often for some $\varepsilon > 0$. Observe that for all $n$, and all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 
    
    $$
    \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) > p) \cdot \mathbb{W}(\phi_n) = 0,
    $$
    
     since regardless of $\mathbb{P}_n(\phi_n)$, one of the factors is 0. Thus, applying Theorem 121 (Affine Provability Induction) yields 
    
    $$
    \begin{equation}
    \tag{155b}
            \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) > p) \cdot \mathbb{P}_n(\phi_n) \eqsim_n 0.
    \end{equation}
    $$
    
     But infinitely often, 
    
    $$
    \operatorname{Ind}_{\textnormal{\small{\({1/n}\)}}}(\mathbb{P}_n(\phi_n) > p) \cdot \mathbb{P}_n(\phi_n) \geq 1 \cdot (p + \varepsilon) \geq \varepsilon
    $$
    
     which contradicts equation (155b).
    

 ◻

### Expectations of Probabilities ^expectations-of-probabilities

**Theorem 156** (Expectations of Probabilities). _Let ${\overline{\phi}}$ be an efficiently computable sequence of sentences. Then 

$$
\mathbb{P}_n(\phi_n)\eqsim_n{\mathbb{E}}_n(\text{“}{\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}})\text{”}).
$$

_

_Proof._ Observe that for all $n$, and for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}(\mathbb{P}_n(\phi_n) - \text{“}{\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}})\text{”}) = 0$ (where $\mathbb{P}_n(\phi_n)$ is a number and $\text{“}{\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}})\text{”})$ is a LUV). Thus, by Theorem 148 (Expectation Provability Induction),

$$
\mathbb{P}_n(\phi_n) - {\mathbb{E}}_n(\text{“}{\underline{\mathbb{P}}}_{\underline{n}}({\underline{\phi_n}})\text{”}) \eqsim_n 0.
$$

 ◻

### Iterated Expectations ^iterated-expectations

**Theorem 157** (Iterated Expectations). _Suppose ${\overline{X}}$ is an efficiently computable sequence of LUVs. Then 

$$
{\mathbb{E}}_n(X_n)\eqsim_n{\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{\underline{n}}({\underline{X_n}})\text{”}).
$$

_

_Proof._ Observe that for all $n$, and for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, $\mathbb{W}({\mathbb{E}}_n(X_n)- \text{“}{\underline{{\mathbb{E}}}}_{\underline{n}}({\underline{X_n}})\text{”}) = 0$ (where ${\mathbb{E}}_n(X_n)$ is a number and $\text{“}{\underline{{\mathbb{E}}}}_{\underline{n}}({\underline{X_n}})\text{”})$ is a LUV). Thus, by Theorem 148 (Expectation Provability Induction),

$$
{\mathbb{E}}_n(X_n) - {\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{\underline{n}}({\underline{X_n}})\text{”}) \eqsim_n 0.
$$

 ◻

### Expected Future Expectations ^expected-future-expectations

**Theorem 158** (Expected Future Expectations). _Let $f$ be a deferral function (as per Definition 30), and let ${\overline{X}}$ denote an e.c. sequence of $[0,1]$\-LUVs. Then 

$$
{\mathbb{E}}_n(X_n) \eqsim_n
    {\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}})}({\underline{X_n}})\text{”}).
$$

_

_Proof._ Let $Y_m := X_n$ if $m = f(n)$ for some $n$, and $Y_m := \text{“}0\text{”}$ otherwise. Observe that $(Y_m)_m$ is e.c.. By Theorem 157 (Iterated Expectations),

$$
{\mathbb{E}}_{f(n)}(X_n) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f(n)}} } ({\underline{X_n}})\text{”}  ).
$$

We now manipulate the encodings ${\underline{f(n)}}$ (for the number $f(n)$) and ${\underline{f}}({\underline{n}})$ (for the program computing $f$ and its input $n$). Observe than for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$,

$$
\mathbb{W}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f(n)}} } ({\underline{X_n}})\text{”}  ) =
  \mathbb{W}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}  ).
$$

So by Theorem 148 (Expectation Provability Induction),

$$
{\mathbb{E}}_{f(n)}(X_n) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}).
$$

By Theorem 143 (Expectation Preemptive Learning),

$$
{\mathbb{E}}_n(X_n) \eqsim_n {\mathbb{E}}_n(\text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}}) \text{”}).
$$

 ◻

### No Expected Net Update ^no-expected-net-update

**Theorem 159** (No Expected Net Update). _Let $f$ be a deferral function, and let ${\overline{\phi}}$ be an e.c. sequence of sentences. Then 

$$
\mathbb{P}_n(\phi_n) \eqsim_n
      {\mathbb{E}}_n(\text{“}{\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}})\text{”}).
$$

_

_Proof._ Let $\psi_m := \phi_n$ if $m = f(n)$ for some $n$, and $\psi_m := \bot$ otherwise. Observe that $(\psi_m)_m$ is e.c.. By Theorem 156 (Expectations of Probabilities),

$$
\mathbb{P}_{f(n)}(\phi_n) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{\mathbb{P}}}_{ {\underline{f(n)}} } ({\underline{\phi_n}})\text{”}  ).
$$

We now manipulate the encodings ${\underline{f(n)}}$ and ${\underline{f}}({\underline{n}})$. Observe that for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$,

$$
\mathbb{W}( \text{“} {\underline{\mathbb{P}}}_{{\underline{f(n)}} } ({\underline{\phi_n}})\text{”}  ) =
  \mathbb{W}( \text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”}  ).
$$

So by Theorem 148 (Expectation Provability Induction),

$$
\mathbb{P}_{f(n)}(\phi_n) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”}  ).
$$

By Theorem 150 (Expectations of Indicators),

$$
{\mathbb{E}}_{f(n)} (\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”}  ).
$$

By Theorem 143 (Expectation Preemptive Learning),

$$
{\mathbb{E}}_n(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right))  \eqsim_n {\mathbb{E}}_n( \text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”}  ).
$$

By Theorem 150 (Expectations of Indicators),

$$
\mathbb{P}_n(\phi_n) \eqsim_n {\mathbb{E}}_n( \text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”}  ).
$$

 ◻

### No Expected Net Update under Conditionals ^no-expected-net-update-2

**Theorem 160** (No Expected Net Update under Conditionals). _Let $f$ be a deferral function, and let ${\overline{X}}$ denote an e.c. sequence of $[0,1]$\-LUVs, and let ${\overline{w}}$ denote a ${\overline{\mathbb{P}}}$\-generable sequence of real numbers in $[0, 1]$. Then 

$$
{\mathbb{E}}_n(\text{“}{\underline{X_n}} \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})}\text{”}) \eqsim_n
  {\mathbb{E}}_n(\text{“}{\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}})}({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})}\text{”}).
$$

_

_Proof._ By Theorem 157 (Iterated Expectations) and Theorem 148 (Expectation Provability Induction), 

$$
{\mathbb{E}}_{f(n)}(X_n) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f(n) }}} ({\underline{X_n}})\text{”} ) \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}  )
$$

 and thus 

$$
{\mathbb{E}}_{f(n)}(X_n) \cdot w_{f(n)} \eqsim_n {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}  ) \cdot w_{f(n)}.
$$

 Observe that for all $n$, and for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 

$$
\mathbb{W}(X_n) \cdot w_{f(n)} =  \mathbb{W}(\text{“} {\underline{X_n}} \cdot {\underline{w}}_{ {\underline{f}}({\underline{n}} )} \text{”}).
$$

 So by Theorem 148 (Expectation Provability Induction), 

$$
{\mathbb{E}}_{f(n)}(X_n) \cdot w_{f(n)}   
  \eqsim_n
  {\mathbb{E}}_{f(n)}(\text{“} {\underline{X_n}} \cdot {\underline{w}}_{ {\underline{f}}({\underline{n}} )} \text{”}).
$$

 Similarly, for all $n$ and all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 

$$
\mathbb{W}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}) \cdot w_{f(n)} \eqsim_n
    \mathbb{W}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})} \text{”} ).
$$

 So by Theorem 148 (Expectation Provability Induction), 

$$
{\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}})\text{”}) \cdot w_{f(n)} \eqsim_n
    {\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})} \text{”} ).
$$

 Combining these, 

$$
{\mathbb{E}}_{f(n)}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})}\text{”}  )
    \eqsim_n
    {\mathbb{E}}_{f(n)}(\text{“} {\underline{X_n}} \cdot {\underline{w}}_{ {\underline{f}}({\underline{n}} )} \text{”}).
$$

 So by Theorem 143 (Expectation Preemptive Learning), 

$$
{\mathbb{E}}_{n}( \text{“} {\underline{{\mathbb{E}}}}_{{\underline{f}}({\underline{n}}) } ({\underline{X_n}}) \cdot {\underline{w}}_{{\underline{f}}({\underline{n}})} \text{”} )
    \eqsim_n
    {\mathbb{E}}_{n}(\text{“} {\underline{X_n}} \cdot {\underline{w}}_{ {\underline{f}}({\underline{n}} )} \text{”}).
$$

 ◻

### Self-Trust ^self-trust-2

**Theorem 161** (Self-Trust). _Let $f$ be a deferral function, ${\overline{\phi}}$ be an e.c. sequence of sentences, ${\overline{\delta}}$ be an e.c. sequence of positive rational numbers, and ${\overline{{p}}}$ be a ${\overline{\mathbb{P}}}$\-generable sequence of rational probabilities. Then 

$$
{\mathbb{E}}_n\left(\text{“}
      {\underline{\mathop{\mathrm{\mathbb{1}}}(\phi_n)}} \cdot
      {\underline{\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}}}\left(
        {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}}) > {\underline{p_n}}
      \right)
    \text{”}\right)
    \gtrsim_n
    p_n\cdot
    {\mathbb{E}}_n\left(\text{“}
      {\underline{\operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}}}\left(
        {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}})}({\underline{\phi_n}}) > {\underline{p_n}}
      \right)
    \text{”}\right).
$$

_

_Proof._ Define $\alpha_n := \operatorname{Ind}_{\textnormal{\small{\({\delta_n}\)}}}(P_{f(n)}(\phi_n) > p_n)$. By Theorem 156 (Expectations of Probabilities), 

$$
\mathbb{P}_{f(n)}(\phi_n)
     \eqsim_n
     {\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”} )
$$

 and so 

$$
\mathbb{P}_{f(n)}(\phi_n) \cdot \alpha_n
     \eqsim_n
     {\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”} ) \cdot \alpha_n.
$$

 Observe that for all $\mathbb{W}\in \mathcal{PC}(\Gamma)$, 

$$
\mathbb{W}(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)) \cdot \alpha_n
   =
  \mathbb{W}(\text{“} {\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} \cdot {\underline{\alpha}}_{ {\underline{n}}} \text{”}).
$$

 So by Theorem 150 (Expectations of Indicators) and Theorem 148 (Expectation Provability Induction), 

$$
\mathbb{P}_{f(n)}(\phi_n) \cdot \alpha_n \eqsim_n {\mathbb{E}}_{f(n)}(\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)) \cdot \alpha_n
  \eqsim_n
  {\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} \cdot {\underline{\alpha}}_{ {\underline{n}}} \text{”}).
$$

 By two more similar applications of Theorem 148 (Expectation Provability Induction), 

$$
{\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}})\text{”} ) \cdot \alpha_n
     \eqsim_n
     {\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathbb{P}}}_{{\underline{f}}({\underline{n}}) } ({\underline{\phi_n}}) \cdot {\underline{\alpha}}_{{\underline{n}}}\text{”} )
     \gtrsim_n
     p_n \cdot {\mathbb{E}}_{f(n)}(\text{“}{\underline{\alpha}}_{{\underline{n}}}\text{”}).
$$

 Combining these, 

$$
{\mathbb{E}}_{f(n)}(\text{“} {\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} \cdot {\underline{\alpha}}_{ {\underline{n}}} \text{”})
    \gtrsim_n
     p_n \cdot {\mathbb{E}}_{f(n)}(\text{“}{\underline{\alpha}}_{{\underline{n}}}\text{”}).
$$

 By Theorem 143 (Expectation Preemptive Learning), 

$$
{\mathbb{E}}_n(\text{“} {\underline{\mathop{\mathrm{\mathbb{1}}}\left(\phi_n\right)}} \cdot {\underline{\alpha}}_{ {\underline{n}}} \text{”})
    \gtrsim_n
     p_n \cdot {\mathbb{E}}_n(\text{“}{\underline{\alpha}}_{{\underline{n}}}\text{”}).
$$

 ◻

## Non-Dogmatism and Closure Proofs ^non-dogmatism-and-closure-proofs

### Parametric Traders ^parametric-traders

Now we show that there is no uniform strategy (i.e., efficiently emulatable sequence of traders) for taking on increasing finite amounts of possible reward with uniformly bounded possible losses.

**Lemma 162** (Parametric Traders). _Let ${\overline{\mathbb{P}}}$ be a logical inductor over ${\overline{D}}$. Then there does not exist an efficiently emulatable sequence of traders $({\overline{T}}^k)_k$ such that for all $k$, the set 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i\left({\overline{\mathbb{P}}}\right)}\right) \,\middle|\, n\in {\mathbb{N}}^+, \mathbb{W}\in
    \mathcal{PC}(D_{n}) \right\}
$$

 of plausible values of ${\overline{T}}^k$’s holdings is bounded below by $-1$ and has supremum at least $k$._

In words, this lemma states that if ${\overline{\mathbb{P}}}$ is a logical inductor then there is no efficiently emulatable sequence of traders $({\overline{T}}^k)_k$ such that each ${\overline{T}}^k$ never risks more than $\text{\textdollar} 1$, and exposes ${\overline{\mathbb{P}}}$ to at least $\text{\textdollar} k$ of plausible risk. To show this lemma, roughly speaking we sum together scaled versions of some of the ${\overline{T}}^k$ so that the sum of their risks converges but the set of their plausible profits diverges. In this proof only we will use the abbreviation $h(j) := j2^j$ for $j \in {\mathbb{N}}^+$.

_Proof._ Suppose for contradiction that such a sequence $({\overline{T}}^k)_k$ exists. Define a trader ${\overline{T}}$ by the formula 

$$
T_n := \sum_{j: h(j) \leq n} \frac{T_n^{h(j)}}{2^j}.
$$

 This is well-defined as it is a finite sum of trading strategies, and it is efficiently computable in $n$ because $({\overline{T}}^k)_k$ is efficiently emulatable. Then for any time $n$ and any world $\mathbb{W}\in \mathcal{PC}(D_{n})$, 

$$
\begin{align*}
\mathbb{W}\left({\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}})}\right)
&=
\mathbb{W}\left(\sum_{i \leq n} \sum_{j: h(j) \leq n} \frac{T_i^{h(j)} ({\overline{\mathbb{P}}})}{2^j}\right)
\end{align*}
$$

by definition of ${\overline{T}}$ and since $T_n^{h(j)}\equiv 0$ if $h(j) > n$;

$$
\begin{align*}
&=
\sum_{j: h(j) \leq n}\frac{1}{2^j}\mathbb{W}\left(\textstyle{ \sum_{i \leq n}  T_i^{h(j)} ({\overline{\mathbb{P}}})} \right)
\end{align*}
$$

by linearity;

$$
\begin{align*}
&\geq \sum_{j\in {\mathbb{N}}^+}\frac{1}{2^j} \cdot (-1) \\
&\geq -1 ,
\end{align*}
$$

 by the assumption that the plausible values $\mathbb{W}\left(\textstyle{ \sum_{i \leq n}  T_i^{h(j)} ({\overline{\mathbb{P}}})} \right)$ are bounded below by $-1$. Furthermore, for any $k \in {\mathbb{N}}^+$, consider the trader ${\overline{T}}^{h(k)}$. By assumption, for some time $n$ and some world $\mathbb{W}\in \mathcal{PC}(D_{n})$, we have 

$$
\mathbb{W}\left(\textstyle{ \sum_{i \leq n}  T_i^{h(k)} ({\overline{\mathbb{P}}})} \right) \geq h(k) \equiv k 2^{k}.
$$

 Then, by the above analysis, we have 

$$
\begin{align*}
\mathbb{W}\left({\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}})}\right)
&\geq  \frac{1}{2^{k}}\cdot \mathbb{W}\left(\textstyle{ \sum_{i \leq n}  T_i^{h(k)} ({\overline{\mathbb{P}}})} \right)  + \sum_{j \in {\mathbb{N}}^+}\frac{1}{2^j} \cdot (-1)\\
&\geq  \frac{k 2^{k}}{2^{k}} -1\\
&=k-1.
\end{align*}
$$

 Thus we have shown that the plausible values $\mathbb{W}\left({\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}})}\right)$ of our trader ${\overline{T}}$ are bounded below by $-1$ but unbounded above, i.e. ${\overline{T}}$ exploits the market ${\overline{\mathbb{P}}}$. This contradicts that ${\overline{\mathbb{P}}}$ is a logical inductor, showing that this sequence $({\overline{T}}^k)_k$ cannot exist. ◻

### Uniform Non-Dogmatism ^uniform-non-dogmatism

Recall Theorem 163:

**Theorem 163** (Uniform Non-Dogmatism). _For any computably enumerable sequence of sentences ${\overline{\phi}}$ such that $\Gamma\cup{\overline{\phi}}$ is consistent, there is a constant $\varepsilon>0$ such that for all $n$, 

$$
\mathbb{P}_\infty(\phi_n)\geq \varepsilon.
$$

_

Roughly speaking, to show this, we will construct a parametric trader using Lemma 162 by defining an efficiently emulatable sequence $({\overline{T}}^k)_k$ of traders. Each trader ${\overline{T}}^k$ will attempt to “defend” the probabilities of the $\phi_i$ from dropping too far by buying no more than $k+1$ total shares in various $\phi_i$ when they are priced below $1/(k+1)$. If the property doesn’t hold of ${\overline{\mathbb{P}}}$, then each ${\overline{T}}^k$ will buy a full $(k+1)$\-many shares, at a total price of at most $-1$. But since the $\phi_i$ are all collectively consistent, there is always a plausible world that values the holdings of ${\overline{T}}^k$ at no less than $k+1-1=k$. Then the parametric trader that emulates $({\overline{T}}^k)_k$ will exploit ${\overline{\mathbb{P}}}$, contradicting that ${\overline{\mathbb{P}}}$ is a logical inductor.

_Proof._ We can assume without loss of generality that for each $\phi_i$ that appears in the sequence of sentences ${\overline{\phi}}$, that same sentence $\phi_i$ appears in ${\overline{\phi}}$ infinitely often, by transforming the machine that enumerates ${\overline{\phi}}$ into a machine that enumerates $(\phi_1,\phi_1,\phi_2, \phi_1,\phi_2,\phi_3,\phi_1,\cdots)$. Futhermore, we can assume that ${\overline{\phi}}$ is efficiently computable by, if necessary, padding ${\overline{\phi}}$ with copies of $\top$ while waiting for the enumeration to list the next $\phi_i$.

##### Constructing the traders. ^constructing-the-traders

We now define our sequence $({\overline{T}}^k)_k$ of traders. For $n<k$, let $T^k_n$ be the zero trading strategy. For $n \ge k$, define $T^k_n$ to be the trading strategy 

$$
T^k_n :=  (k + 1 - {\rm Bought}^k_n)  \cdot {\rm Low}^k_n\cdot  
(\phi_n - \phi_n^{* n}),
$$

 where 

$$
{\rm Low}^k_n:=  \operatorname{Ind}_{\textnormal{\small{\({1/(2k + 2)}\)}}} \left(\phi_n^{* n} < \frac{1}{k+1}\right)
$$

 and 

$$
{\rm Bought}^k_n := \sum_{i\leq n-1} {\|T^k_i\|_{\rm mg}} .
$$

 We will make use of the convention for writing the coefficients of a trade: 

$$
T^k_n[\phi_n] \equiv  (k + 1 - {\rm Bought}^k_n)  \cdot {\rm Low}^k_n .
$$

 In words, $T^k_n$ is a buy order for $(k + 1 - {\rm Bought}^k_n)$\-many shares of $\phi_n$, scaled down by the extent ${\rm Low}^k_n$ to which $\phi_n$ is priced below $1/(k+1)$ at time $n$. The quantity ${\rm Bought}^k_n$ measures the total number of shares that ${\overline{T}}^k$ has purchased before the current time step $n$.

For some fixed polynomial independent of $k$, the ${\overline{T}}^k$ are uniformly computable with runtime bounded by that polynomial as a function of $n$, using the discussion in [[#^dynamic-programming-for-traders|8.2.2]] on dynamic programming. Furthermore, $T^k_n \equiv 0$ for $n < k$ by definition. Hence $({\overline{T}}^k)_k$ is an efficiently emulatable sequence of traders as defined in 112.

Note that by the definition of $T^k_n$, the magnitude ${\|T^k_n({\overline{\mathbb{P}}})\|_{\rm mg}}$ of the trade is bounded by $k+1- {\rm Bought}^k_n({\overline{\mathbb{P}}})$. By definition of ${\rm Bought}^k_n$ and by induction on $n$, we have that 

$$
{\rm Bought}^k_1 ({\overline{\mathbb{P}}}) = 0 \leq k+1
$$

as ${\rm Bought}^k_1$ is an empty sum, and

$$
\begin{align*}
{\rm Bought}^k_{n +1 }({\overline{\mathbb{P}}}) &= \sum_{i\leq  n}  {\|T^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}} \\
  &= {\rm Bought}^k_n ({\overline{\mathbb{P}}})+  {\|T^k_n ({\overline{\mathbb{P}}})\|_{\rm mg}}\\
&\leq  {\rm Bought}^k_n ({\overline{\mathbb{P}}})+ k+1- {\rm Bought}^k_n({\overline{\mathbb{P}}})\\
&= k+1.
\end{align*}
$$

 In words, ${\overline{T}}^k$ never trades more than $k+1$ shares in total. Furthermore, since by definition ${\rm Low}$ is always non-negative, we have that 

$$
{\|T^k_n({\overline{\mathbb{P}}})\|_{\rm mg}} = |T^k_n[\phi_n]({\overline{\mathbb{P}}}) | = |(k + 1 - {\rm Bought}^k_n({\overline{\mathbb{P}}}) )  \cdot {\rm Low}^k_n({\overline{\mathbb{P}}})  | \geq 0.
$$

##### Analyzing the value of $\boldsymbol{{\overline{T}}^k}$. ^analyzing-the-value-of-2

Fix ${\overline{T}}^k$ and a time step $n$. For any plausible world $\mathbb{W}\in \mathcal{PC}(D_{n})$, the value in $\mathbb{W}$ of holdings from trades made by ${\overline{T}}^k$ up to time $n$ is 

$$
\begin{align*}
\mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}}) }\right)
&=
\mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i[\phi_i]({\overline{\mathbb{P}}}) \cdot (\phi_i - \phi_i^{* i}({\overline{\mathbb{P}}})) }\right) \\
&= \;\;\;
\sum_{i \leq n} T^k_i[\phi_i]({\overline{\mathbb{P}}})  \cdot \mathbb{W}(\phi_i)\\
&\;\;\;
+ \sum_{i \leq n}T^k_i[\phi_i]({\overline{\mathbb{P}}})  \cdot (-\mathbb{P}_i(\phi_i)),
\end{align*}
$$

 by linearity and by the definition $\phi_i^{* i }({\overline{\mathbb{P}}}) \equiv   \mathbb{P}_i (\phi_i)$. We analyze the second term first, which represents the contribution to the value of ${\overline{T}}^k$ from the prices of the $\phi_i$\-shares that it has purchased up to time $n$. We have that 

$$
\begin{align*}
&\;\;\;\;  
\sum_{i \leq n}T^k_i[\phi_i]({\overline{\mathbb{P}}})  \cdot (-\mathbb{P}_i(\phi_i))\\
&\geq   \sum_{i \leq n}
{\|T^k_i\|_{\rm mg}} \cdot \left( - \frac{1}{k+1} \right)
\end{align*}
$$

since ${\|T^k_i({\overline{\mathbb{P}}})\|_{\rm mg}} = T^k_i[\phi_i]({\overline{\mathbb{P}}}) \ge 0$ and since $\mathbb{P}_i (\phi_i) \leq 1/(k+1)$ whenever ${\rm Low}^k_i({\overline{\mathbb{P}}})$ is non-zero;

$$
\begin{align*}
&\geq   - \frac{k+1}{k+1} \\
&= -1,
\end{align*}
$$

 since ${\overline{T}}^k$ never purchases more than $k+ 1$ shares. Now consider the value 

$$
\sum_{i \leq n} T^k_i[\phi_i]({\overline{\mathbb{P}}})  \cdot \mathbb{W}(\phi_i)
$$

 in $\mathbb{W}$ of the stock holdings from trades made by ${\overline{T}}^k$ up to time $n$. Since both $\mathbb{W}(\phi_i)$ and $T^k_i[\phi_i]({\overline{\mathbb{P}}})$ are non-negative, this value is non-negative. Hence we have shown that 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}}) }\right)  \geq  -1 + 0 = -1 ,
$$

 i.e. the total value of ${\overline{T}}^k$ is bounded below by $-1$.

Furthermore, since $\Gamma\cup {\overline{\phi}}$ is consistent, there is always a plausible world $\mathbb{W}\in \mathcal{PC}(D_{n})$ such that $\forall i\leq n: \mathbb{W}(\phi_i) = 1$, and therefore 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}}) }\right)  \geq  -1 +
\sum_{i \leq n} T^k_n[\phi]({\overline{\mathbb{P}}}).
$$

##### Exploitation by the parametric trader. ^exploitation-by-the-parametric

Now suppose by way of contradiction that the market ${\overline{\mathbb{P}}}$ does not satisfy the uniform non-dogmatism property. Then for every $k$, in particular the property does not hold for $\varepsilon = 1/(2k+2)$, so there is some $\phi_i$ in the sequence ${\overline{\phi}}$ such that $\mathbb{P}_\infty(\phi_i) <  1/(2k+2)$. Since by assumption $\phi_i$ appears infinitely often in ${\overline{\phi}}$, for some sufficiently large $n$ we have $\mathbb{P}_n(\phi_n) \equiv \mathbb{P}_n(\phi_i)  <  1/(2k+2)$, at which point 

$$
{\rm Low}^k_n({\overline{\mathbb{P}}}) = \operatorname{Ind}_{\textnormal{\small{\({1/(2k + 2)}\)}}} \left(\mathbb{P}_n(\phi_n) < \frac{1}{k+1}\right)= 1.
$$

 Therefore 

$$
T^k_n[\phi_n] = (k + 1 - {\rm Bought}^k_n),
$$

 so that 

$$
\sum_{i\leq  n} {\| T^k_i ({\overline{\mathbb{P}}})\|_{\rm mg}} =  {\rm Bought}^k_{n} ({\overline{\mathbb{P}}})+ k+1- {\rm Bought}^k_{n}({\overline{\mathbb{P}}}) = k+1.
$$

 Thus 

$$
\mathbb{W}\left({\textstyle \sum_{i \leq n} T^k_i({\overline{\mathbb{P}}}) }\right)  \geq  -1 + k+1 = k.
$$

 In words, once the price of some $\phi_i$ dips below $1/(2k+2)$, the trader ${\overline{T}}^k$ will purchase the remaining $k+1-{\rm Bought}^k_n({\overline{\mathbb{P}}})$ shares it will ever buy. Then in a world $\mathbb{W}$ that witnenesses that ${\overline{\phi}}$ is consistent with $\Gamma$, all the shares held by ${\overline{T}}^k$ are valued at $\text{\textdollar}1$ each, so ${\overline{T}}^k$ has stock holdings valued at $k+1$, and cash holdings valued at no less than $-1$.

Therefore each ${\overline{T}}^k$ has plausible value bounded below by $-1$ and at least $k$ in some plausible world at some time step, and therefore Lemma 162 applies, contradicting that ${\overline{\mathbb{P}}}$ is a logical inductor. Therefore in fact ${\overline{\mathbb{P}}}$ does satisfy the uniform non-dogmatism property. ◻

### Occam Bounds ^occam-bounds

Recall Theorem 164:

**Theorem 164** (Occam Bounds). _There exists a fixed positive constant $C$ such that for any sentence $\phi$ with prefix complexity $\kappa(\phi)$, if $\Gamma\nvdash\neg\phi$, then 

$$
\mathbb{P}_\infty(\phi)\geq C2^{-\kappa(\phi)},
$$

 and if $\Gamma\nvdash\phi$, then 

$$
\mathbb{P}_\infty(\phi)\leq 1-C2^{-\kappa(\phi)}.
$$

_

We show the result for $\phi$ such that $\Gamma\not\vdash \lnot \phi$; the result for $\Gamma\not\vdash \phi$ follows by considering $\lnot\lnot \phi$ and using the coherence of $\mathbb{P}_\infty$.

Roughly speaking, we will construct an efficiently emulatable sequence of traders $({\overline{T}}^k)_k$ where ${\overline{T}}^k$ attempts to ensure that $\mathbb{P}_n(\phi)$ does not drop below $2^{-\kappa(\phi)}/(k+1)$ for any $\phi$. We do this by having ${\overline{T}}^k$ purchase shares in any $\phi$ that are underpriced in this way, as judged by a computable approximation from below of $2^{-\kappa(\phi)}$. The trader ${\overline{T}}^k$ will purchase at most $k+1$ shares in each $\phi$, and hence spend at most $\text{\textdollar} 2^{-\kappa(\phi)}$ for each $\phi$ and at most $\text{\textdollar}1$ in total. On the other hand, if the market ${\overline{\mathbb{P}}}$ does not satisfy the Occam property with constant $C = 1/(k+1)$, then for some $\phi$ with $\Gamma\not\vdash \lnot \phi$, we will have that ${\overline{T}}^k$ purchases a full $k+1$ shares in $\phi$. Since there is always a plausible world that values $\phi$ at $\text{\textdollar}1$, ${\overline{T}}^k$ will have a plausible value of at least $\text{\textdollar} k$, taking into account the $\text{\textdollar} 1$ maximum total prices paid. This contradicts Lemma 162, so in fact ${\overline{\mathbb{P}}}$ satisfies the Occam property.

To implement this strategy, we will use tools similar to those used in the proof of Theorem 163, and the proof is similar in spirit, so we will elide some details.

_Proof._ Observe that $2^{-\kappa(\phi)}$ is approximable from below uniformly in $\phi$, since we can (slowly) enumerate all prefixes on which our fixed UTM halts and outputs $\phi$. Let ${\overline{\phi}}$ be an efficiently computable enumeration of all sentences. Let $M$ be a Turing machine that takes an index $i$ into our enumeration and takes a time $n$, and outputs a non-negative rational number. We further specify that $M$ runs in time polynomial in $i+n$, satisfies $\forall n,i: M(n,i) \leq 2^{-\kappa(\phi_i)}$, and satisfies $\lim_{n\rightarrow\infty}M(n,i)=2^{-\kappa(\phi_i)}$. Note that since we are using prefix complexity, we have $\sum_{\phi\in\mathcal{S}}2^{-\kappa(\phi)}\leq 1$. (We can assume without loss of generality that $M(n,i) >0$ for all $i \le n$, by padding the sequence ${\overline{\phi}}$ with $\phi_1$ while waiting until $M(n,i)>0$ to enumerate $\phi_i$, using the fact that our UTM outputs each $\phi$ for some prefix.)

We define a sequence of traders $({\overline{T}}^k)_k$. For $n<k$, define $T^k_n$ to be the zero trading strategy. For $n\geq k$, define $T^k_n$ to be the trading strategy given by 

$$
T^k_n:=  \sum_{i \leq n} (k+1 - {\rm Bought}^k_n(i)) \cdot {\rm Low}^k_n(i) \cdot (\phi_i - \phi_i^{* n})   ,
$$

 where 

$$
{\rm Low}^k_n(i) :=  \operatorname{Ind}_{\textnormal{\small{\({M(n,i)/(2k + 2)}\)}}}\left({\phi}^{*n}<\frac{M(n,i)}{k + 1}\right)
$$

 and 

$$
{\rm Bought}^k_n(i) := \sum_{j \leq n-1} T^k_j[\phi_i] .
$$

 This is similar to the parametric trader used in the proof of Theorem 163, except that here on time $n$, ${\overline{T}}^k$ buys any $\phi_i$ when $\mathbb{P}_n(\phi_i)$ is too low, and ${\rm Bought}^k_n(i)$ tracks the number of shares bought by ${\overline{T}}^k$ in each $\phi_i$ individually up to time $n$. By the discussion of dynamic programming in [[#^dynamic-programming-for-traders|8.2.2]], $({\overline{T}}^k)_k$ is an efficiently emulatable sequence of traders. (We use that $M(n,i)$ is pre-computed by the machine that computes ${\overline{T}}^k$, and hence appears in the feature expression for $T^k_n$ as a constant which is strictly positive by assumption.)

Observe that for each $i$, by induction on $n$ we have ${\rm Bought}^k_n(i) \leq k+1$, so that ${\overline{T}}^k$ only buys positive shares in the various $\phi_i$, and ${\overline{T}}^k$ only buys up to $k + 1$ shares of $\phi_i$. Further, ${\overline{T}}^k$ only buys $\phi_i$\-shares at time $n$ if the price $\mathbb{P}_n(\phi_i)$ is below $1/(k+1)$\-th of the approximation $M(n,i)$ to $2^{-\kappa(\phi)}$, i.e. 

$$
\mathbb{P}_n(\phi_i) < \frac{M(n,i)}{k + 1} \leq \frac{2^{-\kappa(\phi_i)}}{k+1} .
$$

 Therefore ${\overline{T}}^k$ spends at most $\text{\textdollar} 2^{-\kappa(\phi_i)}$ on $\phi_i$\-shares, and hence spends at most $\text{\textdollar} 1$ in total.

Suppose for contradiction that ${\overline{\mathbb{P}}}$ does not satisfy the Occam property. Then for every $k$ there exists some $\phi_i$ such that the limiting price of $\phi_i$ is 

$$
\mathbb{P}_\infty(\phi_i) < \frac{2^{-\kappa(\phi_i)}  }{(2k+2)},
$$

but nevertheless $\Gamma\nvdash \neg\phi_i$. Then for some time step $n$ we will have that $\mathbb{P}_n(\phi_i) < M(n,i)/(2k+2)$, and hence ${\rm Low}^k_n(i)= 1$. At that point ${\overline{T}}^k$ will purchase $k+1 - {\rm Bought}^k_n(i)$ shares in $\phi_i$, bringing ${\rm Bought}^k_{n+1} (i)$ to $k+1$; that is, ${\overline{T}}^k$ will have bought $k + 1$ shares of $\phi_i$. Since $\phi$ is consistent with $\Gamma$, there is some plausible world $\mathbb{W}\in \mathcal{PC}(D_{n})$ that values those shares at $\text{\textdollar} 1$ each, so that the total value of all of the holdings from trades made by ${\overline{T}}^k$ is at least $k$. By Lemma 162 this contradicts that ${\overline{\mathbb{P}}}$ is a logical inductor, so in fact ${\overline{\mathbb{P}}}$ must satisfy the Occam property. ◻

### Non-Dogmatism ^non-dogmatism-3

**Theorem 165** (Non-Dogmatism). _If $\Gamma\nvdash \phi$ then $\mathbb{P}_\infty(\phi)<1$, and if $\Gamma\nvdash \neg\phi$ then $\mathbb{P}_\infty(\phi)>0$._

_Proof._ This is a special case of 164, since $\kappa(\phi) >0$ for any $\phi$. ◻

### Domination of the Universal Semimeasure ^domination-of-the-universal

**Theorem 166** (Domination of the Universal Semimeasure). _Let $(b_1, b_2, \ldots)$ be a sequence of zero-arity predicate symbols in $\mathcal{L}$ not mentioned in $\Gamma$, and let $\sigma_{\le n}=(\sigma_1,\ldots,\sigma_n)$ be any finite bitstring. Define 

$$
\mathbb{P}_\infty(\sigma_{\le n}) := \mathbb{P}_\infty(\text{“}(b_1 \leftrightarrow{\underline{\sigma_1}}=1) \land (b_2 \leftrightarrow{\underline{\sigma_2}}=1) \land \ldots \land (b_n \leftrightarrow{\underline{\sigma_n}}=1)\text{”}),
$$

 such that, for example, $\mathbb{P}_\infty(01101) = \mathbb{P}_\infty(\text{“}\lnot b_1 \land b_2 \land b_3 \land \lnot b_4 \land b_5\text{”})$. Let $M$ be a universal continuous semimeasure. Then there is some positive constant $C$ such that for any finite bitstring $\sigma_{\le n}$, 

$$
\mathbb{P}_\infty(\sigma_{\le n}) \ge C \cdot M(\sigma_{\le n}).
$$

_

_Proof._ Let $({\overline{\sigma}}^i)_i$ be an e.c. enumeration of all finite strings. Let $l({\overline{\sigma}})$ be the length of ${\overline{\sigma}}$. Define

$$
\phi_i := \text{“}
    (b_1 \leftrightarrow{\underline{\sigma^i_1}}=1) \land
    (b_2 \leftrightarrow{\underline{\sigma^i_2}}=1) \land
    \ldots \land
    (b_{{\underline{l({\overline{\sigma}}^i)}}} \leftrightarrow{\underline{\sigma^i_{l({\overline{\sigma}}^i)}}}=1)\text{”}
$$

to be the sentence saying that the string $(b_1, b_2, \ldots)$ starts with $\sigma^i$. Suppose the theorem is not true; we will construct a sequence of parametric traders to derive a contradiction through Lemma 162.

##### Defining a sequence of parametric traders. ^defining-a-sequence-of

To begin, let $A({\overline{\sigma}}, n)$ be a lower-approximation of $M({\overline{\sigma}})$ that can be computed in time polynomial in $n$ and the length of ${\overline{\sigma}}$. Specifically, $A$ must satisfy

-   $A({\overline{\sigma}}, n) \leq M({\overline{\sigma}})$, and
    
-   $\lim_{n\to \infty} A({\overline{\sigma}}, n) = M({\overline{\sigma}})$.
    

Now, recursively define 

$$
\begin{align*}
  {\alpha_{k,n,i}^\dagger} &:= \begin{cases}
  \operatorname{Ind}_{\textnormal{\small{\({\frac{1}{4(k+1)}}\)}}} \left( \frac{ \phi_i^{* n}}{ A({\overline{\sigma}}^i, n) } < \frac{1}{2(k+1)} \right) & \textnormal{if } A({\overline{\sigma}}^i, n) > 0 \wedge n \geq k \wedge i \leq n \\
    0 & \textnormal{otherwise}
  \end{cases}
    \\
  {\beta_{k,n,i}^\dagger} &:= \min({\alpha_{k,n,i}^\dagger}, 1 - {\gamma_{k,n,i}^\dagger})
  \\
  {\gamma_{k,n,i}^\dagger} &:= \sum_{m < n, j \leq m} {\beta_{k, m, j}^\dagger} {\phi}_j^{* m} + \sum_{j < i} {\beta_{k, n, j}^\dagger} \phi_j^{* n}
\end{align*}
$$

 in order to define a parametric trader 

$$
T^k_n := \sum_{i \leq n} \beta_{k,n,i} \cdot (\phi_i - \phi_i^{* n})
$$

As shorthand, we write $\alpha_{k,n,i} := {\alpha_{k,n,i}^\dagger} ({\overline{\mathbb{P}}})$, $\beta_{k,n,i} := {\beta_{k,n,i}^\dagger} ({\overline{\mathbb{P}}})$, $\gamma_{k,n,i} := {\gamma_{k,n,i}^\dagger} ({\overline{\mathbb{P}}})$. Intuitively,

-   $\alpha_{k,n,i}$ is the number of copies $\phi_i$ that ${\overline{T}}^k$ would buy on day $n$ if it were not for budgetary constraints. It is high if $\mathbb{P}_n$ obviously underprices $\phi_i$ relative to $M$ (which can be checked by using the lower-approximation $A$).
    
-   $\beta_{k,n,i}$ is the actual number of copies of $\phi_i$ that ${\overline{T}}^k$ buys, which is capped by budgetary constraints.
    
-   $\gamma_{k, n, i}$ is the amount of money $T^k$ has spent on propositions $\phi_1, \ldots, \phi_{n-1}$ “before considering” buying $\phi_i$ on day $n$. We imagine that, on each day $n$, the trader goes through propositions in the order $\phi_1, \ldots, \phi_n$.
    

##### Analyzing the sequence of parametric traders. ^analyzing-the-sequence-of

Observe that $T^k$ spends at most $\text{\textdollar}1$ in total, since $\beta_{k,n,i} \leq 1 - \gamma_{k,n,i}$. Now we will analyze the trader’s maximum payout. Assume by contradiction that $\mathbb{P}_\infty$ does not dominate $M$. Define 

$$
\mathrm{Purchased}_{k,n,i} := \sum_{m\le n} \beta_{k,m,i}
$$

 to be the number of shares of ${\overline{\sigma}}^i$ that $T$ has bought by time $n$, and 

$$
\mathrm{MeanPayout}_{k,n} := \sum_{i \in {\mathbb{N}}^+} M({\overline{\sigma}}^i) \mathrm{Purchased}_{k,n,i}.
$$

 to be the “mean” value of stocks purchased by time $n$ according to the semimeasure $M$. Both of these quantities are nondecreasing in $n$. Now we show that there is some $N$ such that $\mathrm{MeanPayout}_{k,n} \geq k+1$ for all $n \geq N$:

-   Every purchase costing $c$ corresponds to $\mathrm{MeanPayout}_{k,n}$ increasing by at least $c\cdot 2(k+1)$. This is because the trader only buys $\phi_i$ when $\frac{\mathbb{P}_n(\phi_i)}{A({\overline{\sigma}}_i, n)} < \frac{1}{2(k+1)}$, and $A({\overline{\sigma}}_i, n) \leq M({\overline{\sigma}}_i)$.
    
-   For some $N$, $\mathrm{MeanPayout}_{k, N} \geq k+1$. Suppose this is not the case. Since we are supposing that $\mathbb{P}_\infty$ does not dominate the universal semimeasure, there is some $i$ such that $\mathbb{P}_\infty(\phi_{i}) < \frac{M({\overline{\sigma}}^{i})}{8(k + 1)}$. So we will have $\mathbb{P}_n(\phi_{i}) < \frac{M({\overline{\sigma}}^{i})}{8(k + 1)}$ for infinitely many $n$; let $\mathcal{N}$ be the set of such $n$.
    
    For all sufficiently high $n$ we have $A({\overline{\sigma}}^i, n) \geq M({\overline{\sigma}}^i)/2$, so for all sufficiently high $n \in \mathcal{N}$,
    
    $$
    \frac{\mathbb{P}_n(\phi_i)}{A({\overline{\sigma}}^i,n)} \leq \frac{\mathbb{P}_n(\phi_i)}{M({\overline{\sigma}}^i)/2} \leq \frac{1}{4(k+1)}
    $$
    
    and so there is some infinite subset $\mathcal{N}' \subseteq \mathcal{N}$ for which $\alpha_{k,n,i} = 1$. By assumption, $\forall n: \mathrm{MeanPayout}_{k, n} < k+1$, so the trader never has spent more than $\text{\textdollar}1/2$ (using the previous step), so $\gamma_{k,n,i} \leq 1/2$. This means $\beta_{k,n,i} \geq 1/2$, which implies an increase in mean payout $\mathrm{MeanPayout}_{k,n} - \mathrm{MeanPayout}_{k,n-1} \geq M({\overline{\sigma}}^i) > 0$. But this increase happens for infinitely many $n$, so $\lim_{n \to \infty} \mathrm{MeanPayout}_{k, n} = \infty$. This contradicts the assumption that $\mathrm{MeanPayout}_{k, N} < k+1$ for all $N$.
    
-   $\mathrm{MeanPayout}_{k,N}$ is nondecreasing in $N$, so $\mathrm{MeanPayout}_{k,n} \geq k+1$ for all $n \geq N$.
    

Using this lower bound on $\mathrm{MeanPayout}_{k,n}$, we would now like to show that $T^k$’s purchases pay out at least $k+1$ in some $W \in \mathcal{PC}(D_\infty)$. To do this, define

$$
\mathrm{MaxPayout}_{k,n} := \sup_{{\overline{\sigma}} \in \mathbb{B}^{\leq {\mathbb{N}}^+}} \sum_{{\overline{\sigma'}}^i \textnormal{~prefix of~} {\overline{\sigma}}} \mathrm{Purchased}({\overline{\sigma}}^i, n)
$$

 to be the maximum amount that $T^k$’s purchases pay out over all possible strings (finite and infinite). Since $M$ is a semimeasure over finite and infinite bitstrings, we have $\mathrm{MeanPayout}(n) \leq \mathrm{MaxPayout}(n)$. Since each $\phi_i$ is independent of $\Gamma$, ${\overline{T}}^k$’s maximum worth is at least 

$$
\limsup_{n\to \infty} \mathrm{MaxPayout}({\overline{\varepsilon}}, n) - 1 \geq \limsup_{n\to \infty} \mathrm{MeanPayout}({\overline{\varepsilon}}, n) - 1 \geq k + 1 - 1 = k.
$$

This is sufficient to show a contradiction using Lemma 162. ◻

### Strict Domination of the Universal Semimeasure ^strict-domination-of-the

Recall Theorem 167 (Strict Domination of the Universal Semimeasure):

**Theorem 167** (Strict Domination of the Universal Semimeasure). _The universal continuous semimeasure does not dominate $\mathbb{P}_\infty$; that is, for any positive constant $C$ there is some finite bitstring $\sigma_{\le n}$ such that 

$$
\mathbb{P}_\infty(\sigma_{\le n}) > C \cdot M(\sigma_{\le n}).
$$

_

_Proof._ Consider the sets of codes for Turing machines 

$$
A_0 := \{ M \mid \textnormal{ \(M\) halts on input 0 and outputs 0}\}
$$

and

$$
A_1 := \{ M \mid \textnormal{ \(M\) halts on input 0 and outputs 1}\}.
$$

 Both of these sets are computably enumerable and disjoint, so by Theorem 163 (Uniform Non-Dogmatism), $\mathbb{P}_\infty$ assigns positive measure to the set $[A]$ of infinite bitstrings that encode a separating set for $A_0$ and $A_1$, i.e., a set $A$ such that $A\cap A_0 = \emptyset$ and $A\supseteq A_1$.

Thus it suffices to show that the universal semimeasure assigns 0 measure to $[A]$. This is a known result from computability theory, using the fact that $A_0$ and $A_1$ are recursively inseparable; see for example (Kucera and Nies 2011). Here we give an elementary proof sketch.

Suppose for contradiction that $m$ computes a universal semimeasure and $m([A])= r >0$; we argue that we can compute some separating set $A$. Let $q \in [4r/5,r] \cap {\mathbb{Q}}$. There is some fixed $k$ such that the finite binary subtree $A_k$ consisting of finite prefixes of length $k$ of strings in $[A]$ is assigned $m(A_k) \in [r,6r/5]$.

On input $n$, we can run $m$ on the set of strings of length up to $n$ until the set of extensions of strings in $A_k$ has measure at least $q$; this will happen because $m([A]) >q$. Then we output 0 if the majority of the measure is on strings with $n$th bit equal to 0, and we output 1 otherwise. If we output 0 but in fact $n \in A_1$, then there is measure at most $6r/5-2r/5 = 4r/5$ on extensions of strings in $A_k$ that are consistent with separating $A_0$ and $A_1$; but this is impossible, as $[A]$ has measure $r$. Likewise if we output 1 then it can’t be that $n \in A_0$. Thus we have recursively separated $A_0$ and $A_1$, contradicting that $A_0$ and $A_1$ are recursively inseparable. ◻

### Closure under Finite Perturbations ^closure-under-finite-perturbations

Recall Theorem 168 (Closure under Finite Perturbations):

**Theorem 168** (Closure under Finite Perturbations). _Let ${\overline{\mathbb{P}}}$ and ${\overline{\mathbb{P}^\prime}}$ be markets with $\mathbb{P}_n= \mathbb{P}^\prime_n$ for all but finitely many $n$. Then ${\overline{\mathbb{P}}}$ is a logical inductor if and only if ${\overline{\mathbb{P}^\prime}}$ is a logical inductor._

In short, a trader that exploits ${\overline{\mathbb{P}}}$ also exploits ${{\overline{\mathbb{P}^\prime}}}$ since all but finitely many of its trades are identically valued. The proof mainly concerns a minor technical issue; we have to make a small adjustment to the trader to ensure that it makes exactly the same trades against ${{\overline{\mathbb{P}^\prime}}}$ as it does against ${\overline{\mathbb{P}}}$.

_Proof._ Assume there is a trader ${\overline{T}}$ which exploits ${\overline{\mathbb{P}}}$. We will construct a new trader ${\overline{T}}'$ that exploits ${{\overline{\mathbb{P}^\prime}}}$. Fix $N$ large enough that $\mathbb{P}_n= \mathbb{P}^\prime_n$ for all $n\geq N$.

We will define ${\overline{T}}'$ so that it makes the same trades against the market ${{\overline{\mathbb{P}^\prime}}}$ as the trader ${\overline{T}}$ makes against ${\overline{\mathbb{P}}}$. That is, we want that for all $n$, 

$$
T'_n({{\overline{\mathbb{P}^\prime}}}) =T_n({\overline{\mathbb{P}}}).
$$

 It is insufficient to set the trading strategy $T'_n$ equal to $T_n$ for all $n$. This is because $T_n$ may infinitely often make different trades given the history $\mathbb{P}^\prime_{\leq n}$ instead of the history $\mathbb{P}_{\leq n}$. For example, it may be that every day ${\overline{T}}$ buys $\mathbb{V}_1(\phi)$\-many shares in $\phi$ against $\mathbb{V}$; in this case if $\mathbb{P}^\prime_1(\phi) \ne \mathbb{P}_1(\phi)$, then at each time $n$, $T_n({{\overline{\mathbb{P}^\prime}}})$ will buy a different number of shares from $T_n({\overline{\mathbb{P}}})$. Roughly speaking, we will patch this problem by copying ${\overline{T}}$, but feeding it “false reports” about the market prices so that it appears to the $T_n$ that they are reacting to ${\overline{\mathbb{P}}}$ rather than ${{\overline{\mathbb{P}^\prime}}}$.

More precisely, let $F$ be a computable function from feature expressions to feature expressions, in the expression language discussed in [[#^expressible-features|8.2]]. For a feature expression $\alpha$, we define $F(\alpha )$ to be identical to $\alpha$ but with all occurrences of an expression $\phi^{* i}$ for $i<N$ replaced by a constant $\mathbb{P}_i(\phi)$.

Note that $F$ is efficiently computable: by the assumption that $\mathbb{P}_n= \mathbb{P}^\prime_n$ for all $n\geq N$, only finitely many constants $\mathbb{P}_i(\phi)$ are needed, and can be hard-coded into $F$. Furthermore, $F$ behaves as intended: for any $\alpha$, we have $F(\alpha)({{\overline{\mathbb{P}^\prime}}})= \alpha({\overline{\mathbb{P}}})$ (using a slight abuse of notation, treating $\alpha$ as both an expression and as the feature thus expressed). This follows by structural induction the expression $\alpha$, where every step is trivial except the base cases for symbols $\phi^{* i}$ with $i<N$, which follow from the definition of $F$. Now we define 

$$
T'_n := \sum_{\phi \in \mathcal{S}} F(T_n[\phi]) (\phi - \phi^{* n})
$$

 for any $n$. This is efficiently computable because $T_n$ and $F$ are both e.c. Furthermore, for all $n \ge N$, we have that $T'_n({{\overline{\mathbb{P}^\prime}}}) = T_n({\overline{\mathbb{P}}})$. Therefore for any $n$ we have that 

$$
\begin{align*}
&\;\;\;\;\left|
\mathbb{W}\left({\textstyle \sum_{i \leq n} T_i\left({\overline{\mathbb{P}}}\right)}\right) -
\mathbb{W}\left({\textstyle \sum_{i \leq n} T'_i\left({{\overline{\mathbb{P}^\prime}}}\right)}\right)
\right|\\
&\leq  
\left|
\mathbb{W}\left({\textstyle \sum_{i < N } T_i\left({\overline{\mathbb{P}}}\right)}\right) -
\mathbb{W}\left({\textstyle \sum_{i < N } T'_i\left({{\overline{\mathbb{P}^\prime}}}\right)}\right)
\right|,
\end{align*}
$$

 which is a fixed constant, where we use that all terms for $i\ge N$ cancel with each other. This says that at all times and all plausible worlds, there is a fixed upper bound on the difference between the values of ${\overline{T}}$ against ${\overline{\mathbb{P}}}$ and of ${\overline{T}}'$ against ${{\overline{\mathbb{P}^\prime}}}$. Thus if 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T_i\left({\overline{\mathbb{P}}}\right)}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n)
\right\}
$$

 is bounded below but unbounded above, then so is 

$$
\left\{ \mathbb{W}\left({\textstyle \sum_{i \leq n} T'_i\left({{\overline{\mathbb{P}^\prime}}}\right)}\right) \,\middle|\, n\in{\mathbb{N}}^+, \mathbb{W}\in\mathcal{PC}(D_n)
\right\}.
$$

 Therefore, if some trader exploits ${\overline{\mathbb{P}}}$, so that ${\overline{\mathbb{P}}}$ is not a logical inductor, then some trader exploits ${{\overline{\mathbb{P}^\prime}}}$, so ${{\overline{\mathbb{P}^\prime}}}$ also fails to be a logical inductor. Symmetrically, if ${{\overline{\mathbb{P}^\prime}}}$ is not a logical inductor, then neither is ${\overline{\mathbb{P}}}$. ◻

### Conditionals on Theories ^conditionals-on-theories

**Theorem 169** (Closure Under Conditioning). _The sequence ${\overline{\mathbb{P}}}(-\mid\psi)$ is a logical inductor over $\Gamma\cup \{\psi\}$. Furthermore, given any efficiently computable sequence ${\overline{\psi}}$ of sentences, the sequence 

$$
\left(\mathbb{P}_1(-\mid \psi_1), \mathbb{P}_2(-\mid \psi_1 \land \psi_2), \mathbb{P}_3(-\mid \psi_1 \land \psi_2 \land \psi_3), \ldots\right),
$$

 where the $n$th pricing is conditioned on the first $n$ sentences in ${\overline{\psi}}$, is a logical inductor over $\Gamma\cup \{\psi_i \mid i \in {\mathbb{N}}^+\}$._

Since ${\overline{\mathbb{P}}}$ is a logical inductor over $\Gamma$, we can fix some particular $\Gamma$\-complete deductive process ${\overline{D}}$ over which ${\overline{\mathbb{P}}}$ is a logical inductor, which exists by definition of “logical inductor over $\Gamma$”. Let ${\overline{D}}'$ be any other e.c. deductive process. Write 

$$
{\psi^{\circ}_{n}} := \bigwedge_{\psi \in D'_n} \psi
$$

 for the conjunction of all sentences $\psi$ that have appeared in ${\overline{D}}'$ up until time $n$. (We take the empty conjunction to be the sentence $\top$.) Write ${{\overline{\mathbb{P}}}^{\circ}}$ to mean the market $\left(  \mathbb{P}_n(-\mid  {\psi^{\circ}_{n}}) \right)_{n \in {\mathbb{N}}^+}$.

We will show the slightly more general fact that for any e.c. ${\overline{D}}'$, if the theory 

$$
\Gamma\cup \{\psi'
\mid \exists n: \psi' \in D'_n \}
$$

 is consistent, then ${{\overline{\mathbb{P}}}^{\circ}}$ is a logical inductor over the deductive process ${{\overline{D}}^{\circ}}$ defined for any $n$ by ${D^{\circ}}_n := D_n \cup D'_n$, which is complete for that theory. This implies the theorem by specializing to the $\{\psi\}$\-complete deductive process $(\{\psi\},\{\psi\},\{\psi\},\ldots)$, and to the $\Psi$\-complete deductive process $(\{\psi_1\},\{\psi_1,\psi_2\},\{\psi_1,\psi_2,\psi_3\},\ldots)$ (where we pad with $\top$ to ensure this sequence is efficiently computable).

Roughly speaking, we’ll take a supposed trader ${\overline{T}}^\circ$ that exploits ${{\overline{\mathbb{P}}}^{\circ}}$ and construct a trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$. We’d like our trader ${\overline{T}}$ to mimic ${\overline{T}}^\circ$ “in the worlds where ${\psi^{\circ}_{n}}$ is true”, and otherwise remain neutral. A first attempt would be to have our trader buy the combination 

$$
\phi \wedge {\psi^{\circ}_{n}} - \frac{\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}})} \cdot {\psi^{\circ}_{n}}
$$

 whenever ${\overline{T}}^\circ$ buys a share in $\phi$. The idea is to make a purchase that behaves like a conditional contract that pays out if $\phi$ is true but only has any effect in worlds where ${\psi^{\circ}_{n}}$ is true. That is, the hope is that the price of this combination is 0; in worlds where ${\psi^{\circ}_{n}}$ is false, the stock holdings from this trade are valued at 0; and in worlds where ${\psi^{\circ}_{n}}$ is true, the stock holdings have the same value as that of purchasing a $\phi$\-share against ${{\overline{\mathbb{P}}}^{\circ}}$.

There are some technical problems with the above sketch. First, the ratio of probabilities in front of ${\psi^{\circ}_{n}}$ in the above trade is not well-defined if $\mathbb{P}_n({\psi^{\circ}_{n}})=0$. We will fix this using a safe reciprocation for the ratio. To avoid having this affect the performance of ${\overline{T}}$ in comparison to ${\overline{T}}^\circ$, we will first correct the market using Lemma [[#^closure-under-finite-perturbations|14.7]] (closure under finite perturbations) so that, essentially, the safe reciprocation never makes a difference.

Second, if $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})$ is greater than $\mathbb{P}_n({\psi^{\circ}_{n}})$, then their ratio $\frac{\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}})}$ is greater than the conditional probability $\mathbb{P}_n(\phi \mid {\psi^{\circ}_{n}}) = 1$ as defined in 54 (which is capped at 1). In this case, our trader ${\overline{T}}$ has stock holdings with a different (and possibly lower) value from those of the original trader ${\overline{T}}^\circ$ exploiting ${{\overline{\mathbb{P}}}^{\circ}}$, and therefore ${\overline{T}}$ possibly has less value overall across time than ${\overline{T}}^\circ$, which breaks the desired implication (that is, maybe the original trader exploits ${{\overline{\mathbb{P}}}^{\circ}}$, but our new, less successful trader does not exploit ${\overline{\mathbb{P}}}$). If we simply replace the ratio with the conditional probability $\mathbb{P}_n(\phi \mid {\psi^{\circ}_{n}})$, then when $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}}) > \mathbb{P}_n({\psi^{\circ}_{n}})$, the value of the cash holdings for ${\overline{T}}$ may be non-zero (in particular, may be negative). Instead we will have ${\overline{T}}$ cut off its trades when both $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}}) > \mathbb{P}_n({\psi^{\circ}_{n}})$ and also ${\overline{T}}^\circ$ is buying $\phi$; this is no loss for ${\overline{T}}$ relative to ${\overline{T}}^\circ$, since in this case ${\overline{T}}^\circ$ is buying $\phi$ at the price of 1, and so is not making any profit anyway.

We now implement this construction strategy.

_Proof._ Let ${\overline{D}}$, ${{\overline{D}}^{\circ}}$, and ${{\overline{\mathbb{P}}}^{\circ}}$ be defined as above.

We may assume that the collection of sentences that appear in ${{\overline{D}}^{\circ}}$ is consistent. If not, then no trader exploits ${{\overline{\mathbb{P}}}^{\circ}}$: for all sufficiently large $n$ the set of plausible worlds $\mathcal{PC}({D^{\circ}}_n)$ is empty, so the set of plausible values of any trader’s holdings is a finite set, and hence bounded above.

We may further assume without loss of generality that there exists a rational $\varepsilon>0$ such that $\mathbb{P}_n({\psi^{\circ}_{n}})>\varepsilon$ for all $n$. Indeed, by Theorem 163 (uniform non-dogmatism), since ${{\overline{D}}^{\circ}}$ is consistent, there is some $\varepsilon>0$ such that $\mathbb{P}_\infty({\psi^{\circ}_{n}})>\varepsilon$ for all sufficiently large $n$. Hence by Theorem 117 (preemptive learning), we have $\liminf_{n\to \infty} \mathbb{P}_n ({\psi^{\circ}_{n}}) > \varepsilon$. This implies that there are only finitely many time steps $n$ such that $\mathbb{P}_n ({\psi^{\circ}_{n}}) \leq \varepsilon$. Therefore by Lemma [[#^closure-under-finite-perturbations|14.7]] (closure under finite perturbations), the market ${{\overline{\mathbb{P}}}'}$ defined to be identical to ${\overline{\mathbb{P}}}$ except with $\mathbb{P}'_n ({\psi^{\circ}_{n}})$ with 1 for all such $n$ is still a logical inductor, and has the desired property. If we show that ${{{\overline{\mathbb{P}}}^{\circ}}}'$ is a logical inductor, then again by Lemma [[#^closure-under-finite-perturbations|14.7]], ${{\overline{\mathbb{P}}}^{\circ}}$ is also a logical inductor.

Now suppose some trader ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$. We will construct a trader ${\overline{T}}$ that exploits ${\overline{\mathbb{P}}}$.

Consider the $\mathcal{E\!F}$\-combination 

$$
\begin{align*}
{\rm Buy}_n(\phi) &:= \phi \wedge {\psi^{\circ}_{n}} - \frac{(\phi \wedge {\psi^{\circ}_{n}})^{* n} }{ \max(\varepsilon, {\psi^{\circ}_{n}}^{* n})} \cdot {\psi^{\circ}_{n}}
\end{align*}
$$

 parametrized by a sentence $\phi$. We write $({\rm Buy}_n(\phi))^{* n}$ for the expressible feature that computes the price of the $\mathcal{E\!F}$\-combination ${\rm Buy}_n(\phi)$ at time $n$, defined in the natural way by replacing sentences with their $^{* n}$ duals. Intuitively, this combination is a “conditional contract” which is roughly free to buy (and valueless) in worlds where ${\psi^{\circ}_{n}}$ is false, but behaves like a $\phi$\-share in worlds where ${\psi^{\circ}_{n}}$ is true.

Now define the trader ${\overline{T}}$ by setting 

$$
\begin{align*}
  T_n &:= \sum_{\phi} \alpha_n \cdot ({\rm Buy}_n(\phi) - ({\rm Buy}_n(\phi))^{* n} ) \\
  \alpha_n &:= \min\left(T^\circ_n[\phi]_{\circ}, T^\circ_n[\phi]_{\circ}\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{(\phi \wedge {\psi^{\circ}_{n}})^{* n} }{ \max(\varepsilon, {\psi^{\circ}_{n}}^{* n})} < 1 + \varepsilon_n\right) \right)\\
  \varepsilon_n &:= \frac{2^{-n}}{\max(1,{\|T_n^\circ\|_{\rm mg}})}
\end{align*}
$$

 where $T^\circ_n[\phi]_{\circ}$ is defined to be the market feature $T^\circ_n[\phi]$ with every occurrence of a sub-expression $\chi^{* i}$ for some sentence $\chi$ replaced with 

$$
\max \left( 1,
\frac{(\chi \wedge {\psi^{\circ}_{i}})^{* i} }{ \max(\varepsilon, {\psi^{\circ}_{i}}^{* i})} \right) .
$$

 That is, $T^\circ_n[\phi]_{\circ}$ is defined so that $T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) = T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})$, i.e., this market feature $T^\circ_n[\phi]_{\circ}$ behaves against the market ${\overline{\mathbb{P}}}$ just as $T^\circ_n[\phi]$ behaves against the conditional market ${{\overline{\mathbb{P}}}^{\circ}}$. Note that $\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}$ is a valid expressible feature: $\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}(x<y) := \max(0,\min(1,2^n\max(1,{\|T_n^\circ\|_{\rm mg}})(y-x) ))$.

The idea is that ${\overline{T}}$ will roughly implement the conditional contracts as described above, and will thus perform just as well against ${\overline{\mathbb{P}}}$ as ${\overline{T}}^\circ$ performs against ${{\overline{\mathbb{P}}}^{\circ}}$. The catch is that it may be that $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}}) > \mathbb{P}_n( {\psi^{\circ}_{n}})$, in which case ${\rm Buy}_n(\phi)$ will no longer quite function as a conditional contract, since ${\mathbb{P}^{\circ}}_n(\phi)$ is capped at 1. To prevent ${\overline{T}}$ from losing relative to ${\overline{T}}^\circ$, we use $\alpha_n$ to quickly stop ${\overline{T}}$ from buying once $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}}) > \mathbb{P}_n( {\psi^{\circ}_{n}})$; no profit is lost, as the price of $\phi$ for ${\overline{T}}^\circ$ is in that case just 1.

We now formalize this analysis of the value of the trades made by ${\overline{T}}$ against ${\overline{\mathbb{P}}}$ according to each term in the above summation and by cases on the traded sentences $\phi$.

_Case 1._ First suppose that $T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}})\leq 0$ and/or $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})/  \mathbb{P}_n({\psi^{\circ}_{n}})  =  \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$. Then $\alpha_n = T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}})$. Let $\mathbb{W}$ be any world; using linearity throughout, we have 

$$
\begin{align*}
&\;\;\;\; \mathbb{W}(\; \alpha_n \cdot ({\rm Buy}_n(\phi) - ({\rm Buy}_n(\phi))^{* n} )\; )({\overline{\mathbb{P}}}) \\
  &=
T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) \cdot \mathbb{W}(  {\rm Buy}_n(\phi) ({\overline{\mathbb{P}}}) - ({\rm Buy}_n(\phi))^{* n} ({\overline{\mathbb{P}}}) ) \\
&=\;\;\; T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) \cdot \mathbb{W}\left(  \phi \wedge {\psi^{\circ}_{n}} -
\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\cdot {\psi^{\circ}_{n}}
\right) \\
& \;\;\;\; -  T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) \cdot \left(
\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})-
\frac{\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})}{ \mathbb{P}_n({\psi^{\circ}_{n}}) }
\cdot
\mathbb{P}_n({\psi^{\circ}_{n}}) \right)
\end{align*}
$$

by the definition of ${\rm Buy}$;

$$
\begin{align*}
&=\;\;\; T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) \cdot \left(\mathbb{W}( \phi \wedge {\psi^{\circ}_{n}}) -
\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\cdot \mathbb{W}({\psi^{\circ}_{n}})
\right)
\end{align*}
$$

by distribution, and where the cash term simply cancels;

$$
\begin{align*}
&\geq \;\;\; T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}}) \cdot \left( \mathbb{W}\left(  \phi \wedge {\psi^{\circ}_{n}}\right) -
\mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})  \cdot \mathbb{W}\left(  {\psi^{\circ}_{n}}
\right)
\right),
\end{align*}
$$

 by definition of $\mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$, and by the assumptions on $\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})$, $\mathbb{P}_n({\psi^{\circ}_{n}})$, and $T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}})$. Note that if $\mathbb{W}\left(  {\psi^{\circ}_{n}} \right)=0$ then this quantity is 0, and if $\mathbb{W}\left(  {\psi^{\circ}_{n}} \right)=1$ then this quantity is 

$$
T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}}) \cdot \left( \mathbb{W}\left( {\psi^{\circ}_{n}}\right) -
\mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})
\right),
$$

 which is just the value of $T^\circ_n$’s holdings in $\phi$ from trading against ${{\overline{\mathbb{P}}}^{\circ}}$.

To lower-bound the value of the $- {\psi^{\circ}_{n}}$ term by $- \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})  \cdot \mathbb{W}\left(  {\psi^{\circ}_{n}}\right)$, we use the fact that $T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}})\leq 0$, the fact that $\mathbb{W}\left(  {\psi^{\circ}_{n}} \right) \geq 0$, and the fact that $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})/  \mathbb{P}_n({\psi^{\circ}_{n}})  \geq \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$; or just the fact that $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})/  \mathbb{P}_n({\psi^{\circ}_{n}})  =  \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$. (Intuitively: ${\overline{T}}$ sells (the equivalent of) $\phi$ at the price of $\frac{\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})}{ \mathbb{P}_n({\psi^{\circ}_{n}}) }$, while ${\overline{T}}^{\circ}$ sells $\phi$ at the no greater price of $\mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$; or else ${\overline{T}}$ buys (the equivalent of) $\phi$ at the same price as ${\overline{T}}^{\circ}$; and so ${\overline{T}}$ does at least as well as ${\overline{T}}^{\circ}$.)

_Case 2._ Now suppose that $T^\circ_n[\phi]_{\circ}({\overline{\mathbb{P}}})\geq 0$, and also $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})/  \mathbb{P}_n({\psi^{\circ}_{n}})  >  \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$. Then $\alpha_n = T^\circ_n[\phi]_{\circ}\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{(\phi \wedge {\psi^{\circ}_{n}})^{* n} }{ \max(\varepsilon, {\psi^{\circ}_{n}}^{* n})} < 1 + \varepsilon_n\right)$. Let $\mathbb{W}$ be any world. We have: 

$$
\begin{align*}
&\;\;\;\; \mathbb{W}(\; \alpha_n \cdot ({\rm Buy}_n(\phi) - ({\rm Buy}_n(\phi))^{* n} )\; )({\overline{\mathbb{P}}}) \\
   &=\;\;\; T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right) \cdot \mathbb{W}\left(  \phi \wedge {\psi^{\circ}_{n}} -
\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\cdot {\psi^{\circ}_{n}}
\right).
\end{align*}
$$

 If $\mathbb{W}({\psi^{\circ}_{n}}) = 0$ then this quantity is 0. If $\mathbb{W}({\psi^{\circ}_{n}}) = 1$, then if we subtract off the value of $T^\circ_n$’s holdings in $\phi$ from trading against ${{\overline{\mathbb{P}}}^{\circ}}$, we have: 

$$
\begin{align*}
  &  T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right) \cdot \mathbb{W}\left(  \phi \wedge {\psi^{\circ}_{n}} -
\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\cdot {\psi^{\circ}_{n}}
\right)\\
- & \;T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot  \left(\mathbb{W}\left(  \phi  \right)
-   \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})
\right)\\
&=  T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right) \cdot \left( \mathbb{W}( \phi ) -
\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\right)\\
- & \;T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot  \left(\mathbb{W}\left(  \phi  \right)
-  1
\right)
\end{align*}
$$

by the assumption that $\mathbb{W}({\psi^{\circ}_{n}}) = 1$, and since $\mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})= 1$ by the assumption that $\mathbb{P}_n(\phi \wedge {\psi^{\circ}_{n}})/  \mathbb{P}_n({\psi^{\circ}_{n}})  >  \mathbb{P}_n (\phi \mid {\psi^{\circ}_{n}})$;

$$
\begin{align*}
=&\; T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \bigg(    
\left(\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right)
-1 \right) \cdot \mathbb{W}(\phi) \\
+&\; 1 - \operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right) \cdot \frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }
\bigg)
\end{align*}
$$

by rearranging;

$$
\begin{align*}
\geq  &\; T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \left(    
\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\left(\frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}}) }  < 1 + \varepsilon_n\right)
  \left(1- \frac{\mathbb{P}_n (\phi \wedge {\psi^{\circ}_{n}})}{\mathbb{P}_n({\psi^{\circ}_{n}})}\right)  \right)
\end{align*}
$$

since $\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}\leq 1,$ so in the worst case $\mathbb{W}(\phi) =1$;

$$
\begin{align*}
\geq  &\; T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \left(-  \varepsilon_n  \right),
\end{align*}
$$

 by definition of $\operatorname{Ind}_{\textnormal{\small{\({\varepsilon_n}\)}}}$.

_Combining the cases._ Now summing over all $\phi$, for any world $\mathbb{W}$ such that $\mathbb{W}({\psi^{\circ}_{n}})=1$, we have:

$$
\begin{align*}
&\mathbb{W}\left( T_n ({{\overline{\mathbb{P}}}^{\circ}})\right) - \mathbb{W}\left( T^\circ_n({{\overline{\mathbb{P}}}^{\circ}}) \right)\\
& = \sum_{\phi} \left( \alpha_n({{\overline{\mathbb{P}}}^{\circ}}) \cdot ({\rm Buy}_n(\phi)({{\overline{\mathbb{P}}}^{\circ}}) - ({\rm Buy}_n(\phi))^{* n}({{\overline{\mathbb{P}}}^{\circ}}) ) \right) - T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\left(\phi -{{\overline{\mathbb{P}}}^{\circ}}(\phi) \right) \\
& \geq \sum_{\phi}T^\circ_n[\phi]({{\overline{\mathbb{P}}}^{\circ}})\cdot \left(- \varepsilon_n  \right)
\end{align*}
$$

since for each $\phi$ the corresponding inequality holds by the above analyses;

$$
\begin{align*}
& \geq -{\|T_n^\circ\|_{\rm mg}} \cdot \frac{2^{-n}}{\max(1,{\|T_n^\circ\|_{\rm mg}})}
\end{align*}
$$

by definition of ${\|T_n^\circ\|_{\rm mg}}$ and of $\varepsilon_n$;

$$
\begin{align*}
& \geq -2^{-n}.
\end{align*}
$$

In particular, for any world $\mathbb{W}\in \mathcal{PC}({D^{\circ}}_n)$ plausible at time $n$ according to ${{\overline{D}}^{\circ}}$, 

$$
\mathbb{W}\left( {\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}}) } \right) \geq  \mathbb{W}\left( {\textstyle \sum_{i \leq n} T^\circ_i({{\overline{\mathbb{P}}}^{\circ}}) } \right) -1.
$$

 Since ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$ over ${{\overline{D}}^{\circ}}$, by definition the set 

$$
\left\{    \mathbb{W}\left( {\textstyle \sum_{i \leq n} T^\circ_i({{\overline{\mathbb{P}}}^{\circ}}) } \right)  \mid   n \in {\mathbb{N}}^+,   \mathbb{W}\in \mathcal{PC}({D^{\circ}}_n) \right\}
$$

 is bounded below and unbounded above. Therefore the set 

$$
\left\{    \mathbb{W}\left( {\textstyle \sum_{i \leq n} T_i({\overline{\mathbb{P}}}) } \right)  \mid   n \in {\mathbb{N}}^+,   \mathbb{W}\in \mathcal{PC}(D_n) \right\}
$$

 is unbounded above, since for all $n$ we have ${D^{\circ}}_n\supseteq D_n$ and hence $\mathcal{PC}({D^{\circ}}_n) \subseteq \mathcal{PC}(D_n)$.

It remains to show that this set is unbounded below. Suppose for contradiction that it is not, so there is some infinite sequence $\{(\mathbb{W}_i, n_i)\}$ with $\mathbb{W}_i\in\mathcal{PC}(D_{n_i})$ on which the value $\mathbb{W}_i \left( {\textstyle \sum_{j \leq n_i} T_j({\overline{\mathbb{P}}}) } \right)$ of ${\overline{T}}$ is unbounded below.

We may assume without loss of generality that each $\mathbb{W}_i$ is inconsistent with ${{\overline{D}}^{\circ}}$. Indeed, if there is no subsequence with this property and with the values of ${\overline{T}}$ unbounded below, then the $\mathbb{W}_i$ consistent with ${{\overline{D}}^{\circ}}$ have the corresponding values $\mathbb{W}_i \left( {\textstyle \sum_{j \leq n_i} T_j({\overline{\mathbb{P}}}) } \right)  \geq \mathbb{W}_i \left( {\textstyle \sum_{j \leq n_i} T^\circ_j({{\overline{\mathbb{P}}}^{\circ}}) } \right)-1$ unbounded below, contradicting that ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$ over ${{\overline{D}}^{\circ}}$. Having made this assumption, there is an infinite sequence $m_i$ with $\mathbb{W}_i({\psi^{\circ}_{m_i-1}}) = 1 \wedge \mathbb{W}_i({\psi^{\circ}_{m_i}}) = 0$ for all $i$.

We may further assume without loss of generality that for each $i$, we have $n_i \leq m_i-1$. Indeed, for any $n \ge m_i$, we have by the above analysis that $\mathbb{W}_i \left( { \textstyle  T_n ({\overline{\mathbb{P}}}) } \right) \ge 0$; in this case replacing $n_i$ with $m_i-1$ would only decrease the values $\mathbb{W}_i ( {\textstyle \sum_{j \leq n_i} T_j({\overline{\mathbb{P}}}) } )$, and hence would preserve that this sequence is unbounded below.

In particular, it is the case that ${\psi^{\circ}_{m_i - 1}}$ propositionally implies ${\psi^{\circ}_{n_i}}$. Because $\mathbb{W}_i({\psi^{\circ}_{m_i - 1}}) = 1$ and $\mathbb{W}_i\in\mathcal{PC}(D_{n_i})$, this implies $\mathbb{W}_i\in\mathcal{PC}({D^{\circ}}_{n_i})$, i.e., $\mathbb{W}_i$ was plausible at time step $n_i$ according to ${{\overline{D}}^{\circ}}$. But then we have that the sequence of values $\mathbb{W}_i ( {\textstyle \sum_{j \leq n_i} T_j({\overline{\mathbb{P}}}) } )  \geq \mathbb{W}_i ( {\textstyle \sum_{j \leq n_i} T^\circ_j({{\overline{\mathbb{P}}}^{\circ}}) } )-1$ is unbounded below, contradicting that ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$ over ${{\overline{D}}^{\circ}}$.

Thus we have shown that, assuming that ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$ over ${{\overline{D}}^{\circ}}$, also ${\overline{T}}$ exploits ${\overline{\mathbb{P}}}$ over ${\overline{D}}$. This contradicts that ${\overline{\mathbb{P}}}$ is a logical inductor, so in fact it cannot be that ${\overline{T}}^\circ$ exploits ${{\overline{\mathbb{P}}}^{\circ}}$; thus ${{\overline{\mathbb{P}}}^{\circ}}$ is a logical inductor over ${{\overline{D}}^{\circ}}$, as desired. ◻
:::

[^note-1]: Because ${\mathsf{PA}}$ is a first-order theory, and the only assumption we made about $\mathcal{L}$ is that it is a propositional logic, note that the axioms of first-order logic—namely, specialization and distribution—must be included as theorems in ${\overline{D}}$.
[^note-2]: _In particular, expressible features are a generalization of arithmetic circuits. The specific definition is somewhat arbitrary; what matters is that expressible features be (1) continuous; (2) compactly specifiable in polynomial time; and (3) expressive enough to identify a variety of inefficiencies in a market._
[^note-3]: Recall that a sequence ${\overline{x}}$ is efficiently computable iff there exists a computable function $n\mapsto x_n$ with runtime polynomial in $n$.
[^note-4]: The traders sketched here are optimized for ease of proof, not for efficiency—a clever trader trying to profit from low prices on efficiently computable theorems would be able to exploit the market faster than this.
[^note-5]: Note that actually adding randomness to $\Gamma$ in this fashion is not allowed, because we assumed that the axioms of $\Gamma$ are recursively enumerable. It is possible to construct a logical inductor that has access to a source of randomness, by adding one bit of randomness to the market each day, but that topic is beyond the scope of this paper.
[^note-6]: Another notion of approximate coherence goes by the name of “inductive coherence” (Garrabrant et al. 2016). A reasoner is called inductively coherent if (1) $\mathbb{P}_n(\bot) \eqsim_n0$; (2) $\mathbb{P}_n(\phi_n)$ converges whenever ${\overline{\phi}}$ is efficiently computable and each $\phi_n$ provably implies $\phi_{n+ 1}$; and (3) for all efficiently computable sequences of provably mutually exclusive and exhaustive triplets $(\phi_n, \psi_n, \chi_n)$, $\mathbb{P}_n(\phi_n) + \mathbb{P}_n(\psi_n) + \mathbb{P}_n(\chi_n) \eqsim_n1$. Garrabrant et al. show that inductive coherence implies coherence in the limit, and argue that this is a good notion of approximate coherence. Theorems 129 (Limit Coherence) and 120 (Affine Coherence) imply inductive coherence, and indeed, logical induction is a much stronger notion.
[^note-7]: We use prefix complexity (the length of the shortest prefix that causes a UTM to output $\phi$) instead of Kolmogorov complexity (the length of the shortest complete program that causes a UTM to output $\phi$) because it makes the proof slightly easier. (And, in the opinion of the authors, prefix complexity is the more natural concept.) Both types of complexity are defined relative to an arbitrary choice of universal Turing machine (UTM), but our theorems hold for every logical inductor regardless of the choice of UTM, because changing the UTM only amounts to changing the constant terms by some fixed amount.
[^note-8]: Reasoning about the behavior of a Turing machine using a Markov logic network would require having one node in the graph for every intermediate state of the Turing machine for every input, so doing inference using that graph is not much easier than simply running the Turing machine. Thus, Markov logic networks are ill-suited for answering questions about how a reasoner should predict the behavior of computations that they cannot run.
