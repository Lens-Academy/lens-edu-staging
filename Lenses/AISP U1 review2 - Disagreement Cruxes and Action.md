---
id: 'f8b0af97-11cf-443c-aad8-6a1c21517794'
title: "Disagreement, Cruxes, and Action"
tldr: "Persistent disagreement is not solved by averaging two probabilities. The useful work is finding what drives the gap, which evidence could move it, and which actions still make sense before consensus."
summary_for_tutor: "Uses the Existential Risk Persuasion Tournament and the Forecasting Research Institute follow-up. Covers persistent disagreement, cruxes, value of information, different evidential standards, local deference, and robust action."
reading_minutes: 12
tutor_minutes: 24
tags:
  - wip
---

#### Text
content::
\## What if serious disagreement survives serious discussion?

A simple picture of rational disagreement says that informed people should converge once they share evidence, understand one another's arguments, and have enough time to think. That picture works in many ordinary cases. One person has missed a fact, misunderstood a claim, or made a calculation error. The disagreement shrinks when the mistake is found.

Long-run AI risk is a harder case. A forecasting exercise brought together domain experts and experienced forecasters to estimate severe global risks. The groups remained far apart on several unprecedented risks, including AI.[^cite-xpt-alexander] A later adversarial-collaboration project focused directly on why people with very different AI-risk forecasts disagreed. Participants spent substantial time reading, forecasting, and discussing the issue. They could summarize the other side's arguments reasonably well. Their top-level forecasts still barely converged.[^cite-fri-2024]

The exact numbers from a small selected sample should not be copied as a course consensus. The more interesting result is structural. Lack of engagement and simple misunderstanding did not explain most of the gap.

\## A probability can hide several disagreements at once

Two people can say "AI catastrophe" while assigning probability to different internal models. They may agree that very powerful AI is likely to exist and disagree about what follows. One person expects capability growth to move far beyond humans quickly. Another expects bottlenecks. One thinks dangerous goals are likely to emerge. Another thinks advanced systems will remain tool-like or easy to correct. One expects institutions to respond well. Another expects competition to make response too slow.

The follow-up forecasting study found exactly this kind of pattern. Large parts of the disagreement concerned how long it would take for AI to become far more capable than humans, how common dangerous goals would be, how difficult extinction would be to cause, and how effectively society would respond.[^cite-fri-2024]

This changes how disagreement should be used. If the crux is capability growth, we should look for evidence about research automation and bottlenecks. If the crux is dangerous agency, we should look for evidence about autonomous planning, goal stability, and power-seeking. If the crux is institutional response, the useful evidence is political and organizational.

A top-level probability can hide those differences. Averaging the numbers can produce a cleaner number while destroying information about what should actually be investigated.

\## Different sides can want different evidence

Persistent disagreement can also come from different standards for evidence. One side may give substantial weight to theoretical mechanisms before those mechanisms have been demonstrated in deployed systems. Another may treat a long theoretical chain as weak until concrete dangerous capabilities appear.

The follow-up study found a version of this. Participants in the more skeptical group were generally more interested in direct demonstrations of dangerous capabilities and power-seeking. Participants in the more concerned group placed more weight on alignment progress, alignment failures, and theoretical arguments about long-run risk.[^cite-fri-2024]

This creates a deeper problem than "which fact are we missing?" If two people disagree about which kinds of evidence are trustworthy, collecting more evidence of one person's preferred type may do little to move the other.

Both standards have failure modes. Waiting for direct evidence can be too slow when the first convincing demonstration is already dangerous. Giving strong weight to theoretical chains can produce persuasive stories whose conjunction is badly calibrated. A good disagreement makes the evidential standard visible so that it can be examined.

\## Cruxes make disagreement useful

A *crux* is a question whose resolution would cause a meaningful update to a belief or decision. A useful crux has a clear outcome, the possible outcomes imply different updates, and those updates matter for something we care about doing.

The forecasting study asked participants to find near-term cruxes for long-run AI risk. One of the stronger examples involved dangerous-capability evaluations, including whether future systems would show abilities related to autonomous replication or avoiding shutdown.[^cite-fri-2024] A positive result could increase concern for some threat models. Years of capability progress without those properties appearing could reduce concern for others.

The striking result was that even the strongest shared short-term cruxes explained only a small part of the total long-run disagreement.[^cite-fri-2024] This does not make crux-finding useless. It tells us that some of the disagreement lives at a deeper level.

One possibility is long-run worldview differences. A person can be anchored by a broad belief that social and technological change is usually gradual. Another can be anchored by a broad belief that sufficiently large capability gaps radically alter power relations. These views shape how both sides interpret the same evidence.

A second possibility is methodological. One person may be willing to trust multi-step theoretical arguments when empirical evidence is scarce. Another may expect such arguments to be poorly calibrated. That disagreement is not resolved by one new benchmark result.

A third possibility is about institutions. People can agree about technical risk and disagree about how well governments, laboratories, or markets will respond.

#### Question: Open
id:: 8043861c-8cd9-4d4f-9ff1-e0632af8f2d4
content::
\## Midpoint check

Think of one claim in your own AI-risk model.

Write one near-term observation that would make you substantially more confident in the claim and one that would make you substantially less confident.

Would someone who disagrees with you also see those observations as relevant evidence?

feedback-instructions::
This is ungraded. Help the learner make the observations genuinely discriminating. If the proposed evidence would be expected under both the claim and its alternative, point that out. If the opposing side would reject the evidence as irrelevant, ask what deeper methodological disagreement explains that. Maximum two replies.

#### Text
content::
\## Value of information

Cruxes connect to the value of information. A question is valuable when learning the answer can change a consequential decision enough to justify the cost of learning.

Imagine two research projects. The first gives a very precise measurement of something everyone already expects, and every plausible result leaves policy unchanged. The second is less elegant but one result would lead to stronger containment while another would lead to ordinary deployment. The second can have greater decision value.

This gives us a way to prioritize research under uncertainty. Ask which question is both answerable and decision-relevant. A question can be intellectually central and still have low value of information if no answer changes action. Another question can be narrow and highly valuable because it determines what happens next.

The forecasting work explicitly tried to measure how informative different cruxes would be for long-run beliefs.[^cite-fri-2024] The exact metric is less important for this course than the habit: connect uncertainty to a possible decision change.

\## Deference should be local

Nobody has deep expertise in every part of AI risk. The topic crosses machine learning, cybersecurity, economics, organizational behaviour, geopolitics, forecasting, philosophy, and moral uncertainty. That makes blanket deference difficult.

Expertise is strongest when the target question is close to the domain where the expert has training and feedback. A machine-learning researcher may know much more about current training methods than a policy analyst. A biosecurity researcher may know much more about pathogen-design barriers than a philosopher. A forecaster may have a strong track record on questions with clear resolution criteria.

The top-level question "what is the chance AI causes an existential catastrophe this century?" combines many domains and extends far beyond direct historical feedback. No one credential settles the whole chain.

A useful strategy is **local deference**. Defer more on the parts where a person's expertise is real, then inspect how those local judgments are combined. The same person can be highly authoritative about one link and ordinary about another.

This also protects against a common social shortcut. "Experts believe X" can hide disagreement over which experts, what question they were asked, whether the target falls inside their expertise, and how the aggregate was produced.

\## Why averaging can lose information

Suppose one group gives two percent and another gives twenty percent. Averaging to eleven percent can be useful when the estimates are similarly informed, reasonably independent, and aimed at the same well-defined quantity.

Those conditions often fail. Both groups may use the same data. One can have more information about one part of the problem. The estimates can encode different causal models. The disagreement can concern values or update rules. A simple average then produces a number that belongs to neither model and hides the source of the gap.

The first question should be why the numbers differ. If the answer is one empirical crux, investigate it. If the answer is different evidential standards, make those standards explicit. If the answer is a moral disagreement, more capability data may not help. If the answer is local expertise, use that expertise locally.

Aggregation can still be useful after that analysis. The point is not to reject averaging. It is to avoid using an average as a substitute for understanding the disagreement.

\## Action without consensus

Persistent disagreement does not require waiting for universal agreement. Some interventions make sense across several live views.

Dangerous-capability evaluations can help a skeptic who wants direct evidence and a concerned researcher who wants warning signals. Better security can matter under malicious-use and organizational-risk pathways. Incident reporting can expose failures across many models. Better biosecurity can reduce a concrete misuse pathway without requiring a strong view about autonomous takeover. Institutional resilience can matter under gradual-disempowerment and accumulative-risk models.

These are examples of robust action. They are not automatically optimal. A robust action can have small impact, and some important choices require taking a position on contested models.

Adaptive action is another response. Take a limited step, define which evidence would trigger a stronger response, and preserve the capacity to update. This works only when the future checkpoint remains available. The previous submodule showed why that condition has to be tested.

\## Where disagreement should leave you

The goal of this unit is not to produce one shared probability. It is to leave you able to say which pathways worry you, which claims carry most of your view, what kind of uncertainty surrounds them, what evidence would change them, and what action follows before the uncertainty disappears.

That standard is demanding enough to rule out "anything goes". A claim can be poorly supported. An intervention can target the wrong mechanism. A proposed crux can fail to discriminate. A deference rule can rely on the wrong expertise.

It is also compatible with genuine disagreement. Two participants can finish Unit 1 with very different levels of concern and both have improved if their models are more explicit, their evidence is better connected to claims, and their actions respond to the uncertainty they actually have.

The final exercise asks you to write that model down.

[^cite-fri-2024]: Josh Rosenberg et al. (2024), *Roots of Disagreement on AI Risk: Exploring the Potential and Pitfalls of Adversarial Collaboration*. [Forecasting Research Institute](https://forecastingresearch.org/research/roots-of-disagreement-on-ai-risk)
[^cite-xpt-alexander]: Scott Alexander (2023), *The Extinction Tournament*. [Astral Codex Ten](https://www.astralcodexten.com/p/the-extinction-tournament)

#### Question: Open
id:: 73fa79d3-dc85-4a1e-9255-4915d6648472
content::
\## Phase 1: Recall

Without looking back, write down three structurally different reasons informed people can remain far apart after serious discussion. Then define a useful crux in your own words.

feedback-instructions::
This is diagnostic recall. Respond once in 90 to 160 words, using short paragraphs and no list. Credit distinct sources of disagreement such as different causal models, evidential standards, long-run expectations, priors, values, or patterns of deference. A useful crux should connect an observable outcome to a meaningful update.

#### Question: Open
id:: 8ba5a74b-706f-41bc-bca8-0a623cc84b0f
content::
\## Phase 2: Processing

Which part of your current view depends most on trusting someone else's expertise? What exactly are you deferring to them about, and how would you notice if that deference were misplaced?

feedback-instructions::
This is reflective and ungraded. Help the learner make the domain of deference local and explicit. Do not encourage blanket trust or blanket skepticism. Close after at most two tutor replies.

#### Question: Open
id:: 9492ecaa-2668-422e-8537-ab9a81678a25
content::
\## Phase 3: Learning Question

Two groups disagree about a long-run technological catastrophe. They understand each other's arguments, share most current evidence, and still differ by an order of magnitude. A policymaker proposes averaging their probabilities and moving on.

Explain why averaging can lose important information. Then describe one better way to use the disagreement for a decision.

assessment-instructions::
Score out of 100.

50 points: The answer explains that top-level probabilities can compress different causal models, evidential standards, priors, values, or correlated evidence, so a midpoint can hide the source of disagreement.

50 points: The answer gives a defensible alternative use of the disagreement, such as decomposing the model, identifying a crux, gathering discriminating information, deferring locally to relevant expertise, or choosing an action that remains useful across the live views.

feedback-instructions::
Give 100 to 170 words in short paragraphs, with no generic praise. State whether the learner preserved the information inside the disagreement. Below full credit, identify the missing reason or weakness in the proposed alternative. Do not tell them which probability to adopt.
