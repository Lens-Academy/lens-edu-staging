---
id: '538c9622-456b-42f3-8184-9c16aba3e1eb'
title: "C.4.2 A family of questions"
tldr: "Define latent models over a family of observations, with addresses and families of latents, and work an example with three overlapping observations."
summary_for_tutor: "This is the start of Section 2 of Iliad worksheet C.4 Condensation (Section 2 intro and 2.1 A family of questions). It contains Example 2.1 (Overlapping observations, X_1=(S,P), X_2=(S,Q), X_3=(P,Q)), the subsection Addresses and families, Definition 2.2 (Latent model) and the latent variable model (LVM) condition, and Exercise 2.1 (Overlapping bits) with a collapsed solution. Keep the notation X_i, Y_A, addresses A in P^+(I) and the family of supersets. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. Condensation

In empirical work, people look for features in AI systems which correspond robustly to human concepts. In general, these can be hard to find.

One ambitious approach to this problem is to think through from first principles how agents in general might organize information about the world into concepts.

How should information be broken into reusable pieces? Is there one way to do this which many different kinds of agents will converge on?

We will propose two conditions that we think are normative for agents in general: conditions an agent will want its own organization of information to satisfy. Under those conditions, corresponding families of latents in two models determine one another.

\### 2.1 A family of questions

Fix jointly distributed observables $$X_{1},\ldots,X_{n}$$. We look for latent variables, each assigned to a set of observations, such that the latents assigned to an observation determine it. We will give conditions under which corresponding families of latents in two such models determine one another, and bound the remaining conditional entropy when the conditions hold approximately. We take the joint distributions as given.

:::callout {title="Note" tone="blue"}

**Remark (Choosing the observables).** One can think of each $$X_{i}$$ as a function of a single underlying variable representing sense data or a physical state. This introduces no restriction: that variable could simply be the tuple of all observations. An observable distinguishes outcomes by partitioning them into its possible answers; random-variable values label those parts. Information quantities do not depend on bijective relabeling of answers. The choice of which observables to include, and their joint law, remains part of the model.

:::

:::callout {title="Tip" tone="green"}

**Example 2.1 (Overlapping observations).** Let $$S,P,Q$$ be independent fair bits and set

$$
X_{1}=(S,P),\qquad X_{2}=(S,Q),\qquad X_{3}=(P,Q).
$$

Use a latent $$Y_{\{1,2\}}=S$$ for observations 1 and 2, a latent $$Y_{\{1,3\}}=P$$ for observations 1 and 3, and a latent $$Y_{\{2,3\}}=Q$$ for observations 2 and 3. Each observation is determined by the two latents assigned to it. Each of these latents can also be recovered from either observation to which it is assigned.

:::

\#### 2.1.1 Addresses and families

Let $$I=\{1,\ldots,n\}$$ and write $${\mathcal{P}^{+}(I)}$$ for its nonempty subsets. An *address* $$A\in{\mathcal{P}^{+}(I)}$$ specifies which observations receive a latent $$Y_{A}$$. We use one latent for each nonempty subset, setting unused ones to constants, and order the addresses by inclusion.

:::callout {title="Definition" tone="blue"}

**Definition 2.2 (Latent model).** A latent model of $$X=(X_{i})_{i\in I}$$ consists of finite-valued variables $$Y=(Y_{A})_{A\in{\mathcal{P}^{+}(I)}}$$ jointly distributed with $$X$$, such that

$$
H\bigl(X_{i}\mid Y_{\{A\in{\mathcal{P}^{+}(I)}\,:\,i\in A\}}\bigr)=0 \quad\text{for every }i\in I.
$$

Here $$Y_{\mathcal{F}}=(Y_{A})_{A\in\mathcal{F}}$$ for a family $$\mathcal{F}\subseteq{\mathcal{P}^{+}(I)}$$.

:::

We call (1) the *latent variable model condition*, or *LVM*. The contributing latents, taken together, determine the observation; some of them may represent residual noise.

For nonempty $$A\subseteq I$$ and $$B\subseteq I$$, define two different families:

$$
{\mathord{\supseteq}} A=\{C\in{\mathcal{P}^{+}(I)}:A\subseteq C\},\qquad \mathcal{J}_{B}=\{C\in{\mathcal{P}^{+}(I)}:C\cap B\ne\varnothing\}.
$$

The tuple $$Y_{{\mathord{\supseteq}} A}$$ is the *tower above $$A$$*. The tuple $$Y_{\mathcal{J}_B}$$ contains all latents contributing to at least one observation in $$B$$; we call these latents *active* for $$B$$. They determine $$X_{B}=(X_{i})_{i\in B}$$. In particular $${\mathord{\supseteq}}\{i\}=\mathcal{J}_{\{i\}}$$ is the family of addresses contributing to $$X_{i}$$, so (1) reads $$H(X_{i}\mid Y_{{\mathord{\supseteq}}\{i\}})=0$$. For a larger $$A$$, $${\mathord{\supseteq}} A$$ and $$\mathcal{J}_{A}$$ generally differ.

**Glossary.**  The sheet uses a small fixed vocabulary.

**Address** A nonempty $$A\subseteq I$$. The model has one *latent* $$Y_{A}$$ at each address; unused ones are constant.

**Block** A nonempty set $$B\subseteq I$$ of observations, with $$X_{B}=(X_{i})_{i\in B}$$.

**Family** A set $$\mathcal{F}$$ of addresses, and the corresponding family of latents $$Y_{\mathcal{F}}$$.

**Contributing** $$Y_{A}$$ contributes to $$X_{i}$$ when $$i\in A$$. The contributing family of $$X_{i}$$ is $${\mathord{\supseteq}}\{i\}$$.

**Tower** The family of latents $$Y_{{\mathord{\supseteq}} A}$$ at $$A$$ and every address containing it.

**Active** $$Y_{A}$$ is active for a block $$B$$ when $$A\cap B\ne\varnothing$$, that is, when it contributes to some observation in $$B$$. The active family is $$\mathcal{J}_{B}$$.

**Upward closed** A family containing every superset of each of its addresses (Section 2.2).

**Witness** A variable from which a target is recoverable (Section 2.3).

:::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (★) (Overlapping bits; 15 minutes).** Use Example 2.1, with all unmentioned latents constant.

**(a)** Compute $$H(X_{1})$$, $$H(X_{1},X_{2},X_{3})$$, and $$I(X_{1};X_{2})$$.

**(b)** List $${\mathord{\supseteq}}\{1\}$$, $${\mathord{\supseteq}}\{2\}$$, and $${\mathord{\supseteq}}\{1,2\}$$, including constant latents. Which tuple determines $$X_{1}$$? Which of the three is $${\mathord{\supseteq}}\{1\}\cap{\mathord{\supseteq}}\{2\}$$?

**(c)** Give explicit functions recovering $$X_{1}$$ from its contributing latents and recovering $$Y_{\{1,2\}}$$ from $$X_{1}$$.

**(d)** Does the address structure have to be a tree? Identify two overlapping addresses in this example neither of which contains the other.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The independent fair bits are $$S,P,Q$$, and $$X_{1}=(S,P)$$, $$X_{2}=(S,Q)$$, $$X_{3}=(P,Q)$$.

**(a)** $$H(X_{1})=2$$. The tuple of all observations determines $$(S,P,Q)$$ and is determined by it, so $$H(X_{1},X_{2},X_{3})=3$$. The pair $$(X_{1},X_{2})$$ already determines all three bits, hence

$$
I(X_{1};X_{2})=H(X_{1})+H(X_{2})-H(X_{1},X_{2})=2+2-3=1.
$$

Its shared bit is $$S$$.

**(b)** The families, including constant latents, are

$$
\begin{split}{\mathord{\supseteq}}\{1\}&=\{\{1\},\{1,2\},\{1,3\},\{1,2,3\}\},\\ {\mathord{\supseteq}}\{2\}&=\{\{2\},\{1,2\},\{2,3\},\{1,2,3\}\},\\ {\mathord{\supseteq}}\{1,2\}&=\{\{1,2\},\{1,2,3\}\}.\end{split}
$$

The first tuple has nonconstant entries $$S,P$$, so determines $$X_{1}$$. Intersecting the first two families leaves $$\{\{1,2\},\{1,2,3\}\}={\mathord{\supseteq}}\{1,2\}$$, the third family listed, whose only nonconstant content is $$S$$.

**(c)** Recover $$X_{1}$$ by taking the ordered pair $$(Y_{\{1,2\}},Y_{\{1,3\}})$$. Recover $$Y_{\{1,2\}}$$ from $$X_{1}$$ by projecting onto its first coordinate.

**(d)** Addresses $$\{1,2\}$$ and $$\{1,3\}$$ overlap but neither contains the other. Thus the contribution pattern need not form a nested tree.

:::
