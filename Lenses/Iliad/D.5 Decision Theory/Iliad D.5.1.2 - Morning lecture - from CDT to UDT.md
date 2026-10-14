---
id: '5df9c8f8-42e6-4057-b028-a69c56139688'
title: "D.5.1.2 Morning lecture: from CDT to UDT"
tldr: "The morning lecture: why decision theory is hard for embedded agents, then EDT, CDT, FDT, UDT 1.0 and 1.1, the problems that separate them, and the open problems."
summary_for_tutor: "Section 2.2.1 'Morning lecture' of Iliad worksheet D.5.1 Decision Theory. It covers dualistic versus embedded agents; EDT (a* = argmax_a E[U | A=a]) versus CDT (do-operator); Newcomb's problem and the smoking lesion; FDT and subjunctive dependence with the twin prisoner's dilemma; UDT 1.0 and 1.1 with counterfactual mugging; and open problems (logical updatelessness, the 5-and-10 problem). Keep the formulas and the payoffs ($1,000,000 vs $1,000; $3 vs $1) exactly as written. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson
source_url: https://iliad-intensive.org/agency/decision-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.2 Main content

The day has four sub-modules: the **morning lecture** (single-agent decision theory), the **reading and discussion** block, the **afternoon lecture** (multi-agent decision theory), and the **tournament**, closing with a **daily checkpoint**.

\#### 2.2.1 Morning lecture

**Why decision theory, and why it is hard.** For a *dualistic* agent cleanly separated from the world, the action is a free variable and the rule is just `a* = argmax_a E[U | do(A=a)]`. For an *embedded* agent the action is itself a fact about the world (predictors may have modelled it, copies may share it), so "what happens if I act differently" is a counterfactual that must be *constructed*. The decision theories differ in how they construct it.

**EDT and CDT: condition vs intervene.**

- *Evidential decision theory* conditions on the action as evidence: `a* = argmax_a E[U | A=a]`. This treats the action as news about everything correlated with it.
- *Causal decision theory* intervenes: `a* = argmax_a E[U | do(A=a)]`, severing the arrows *into* the action in a causal (Bayesian-network) model, so the action is news about its effects only.
- They split on the canonical cases. On **Newcomb's problem** (a predictor fills a box based on your disposition), EDT one-boxes and wins \$1,000,000; CDT two-boxes (the prediction is already made) and wins \$1,000. On the **smoking lesion** (a common cause produces both a disposition to smoke and the disease), EDT wrongly abstains (smoking is bad *evidence* though not a *cause*); CDT correctly smokes. Neither rule handles both, which points to a third kind of dependence.
- *(Aside, for the mathematically inclined.)* The two rules drop out of two ways to model the agent's interaction history: CDT is a chronological-semimeasure predictor (actions are conditioned-on inputs, never predicted, exactly the do-operator), while EDT is a joint predictor over actions and observations (conditioning on an action updates beliefs about which world and which policy you are). The slides develop this; it can be skipped without loss.

**FDT: choose your function's output.** Functional decision theory reframes *what you are choosing*. You run a fixed decision function; your action is its output, and everything that depends on that function (predictors who modelled it, copies running it, simulations of it) moves together with the output. FDT asks "which output of this decision function, given everything that depends on it, yields the best outcome?" It one-boxes on Newcomb and smokes on the smoking lesion. Its signature case is the **twin prisoner's dilemma**: two copies of the same agent share the same logical output (*subjunctive dependence*), so FDT cooperates (each gets \$3) where CDT defects (each gets \$1). Causal dependence is a special case of subjunctive dependence; mere correlation (the lesion) is not.

**UDT: act on the policy you would have committed to.**

- *UDT 1.0* chooses each action as the one a prior-stage self would have committed to: `choice(o) = argmax_a E[U | choice(o)=a]`. On **counterfactual mugging** (a coin you have already seen land the wrong way, where paying in this branch is what makes paying profitable across branches), the updateful agent refuses and the updateless agent pays, because ex ante paying is worth `(R-c)/2`. Updatelessness is not ignorance; it is refusing to update away a commitment that is good in expectation, which makes it reflectively stable.
- *UDT 1.1* optimizes the whole *policy* (a map from observations to actions) rather than each action separately, then applies it: `S* in argmax_{S:O->A} E[U | choice=S]`. This is needed when copies must coordinate their actions across branches, which per-observation optimization can get wrong.

**Where this is heading.** The shift across CDT/EDT to FDT to UDT 1.0 to UDT 1.1 is a shift in *what you are choosing*: an action, then a function's output, then an output you do not update away, then a whole policy. Two hard problems remain: UDT pays real utility in the actual branch and is only as good as its prior, and *logical updatelessness* (what is the right "prior" when some uncertainty is mathematical?) has no clean answer. The **5-and-10 problem** shows the deeper trouble: a naive proof-searching agent can be driven by a spurious Löbian proof to take the worse action, because counterfactuals over one's own action break down. The frontier goal is to formalize decision problems as programs and ask which theory is *optimal* over a well-defined class of "fair" problems (where the world depends only on the agent's input/output behaviour); the two demands such a criterion forces (coordinate across calls; detect an isomorphic copy of yourself) are exactly UDT 1.1 and FDT turned into a specification.
