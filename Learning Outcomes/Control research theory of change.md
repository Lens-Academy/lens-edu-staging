---
id: '9236fa29-1a31-4d30-9ba4-5048ac77fec5'
learning-outcome: "For a proposed control research or implementation project, lay out the causal chain from what the project produces to a reduction in catastrophic risk (whether and why the work is informative with today's models, who would adopt its output, why, and what might stop them, which threat it targets and whether and why it would hold up against a model trying to subvert it, and what could make it obsolete), identify the weakest link in that chain with a reason, and name observations that would raise and observations that would lower confidence in that link."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: intermediate
authors:
  - Elias+Claude
---
## Test:
id:: 519afc89-b67a-4910-9639-ec4111aa3fb1

#### Question: Open
id:: 52dc7c97-450d-4ac2-96e3-c2af8cf6fee7
content::
A safety team at a frontier AI company proposes a six-month project: a **permissions broker** for its internal AI agents. Every request an agent makes for more compute, access to a dataset or model checkpoint, or network access would go to a smaller, older model the company trusts, which approves it, denies it, or sends it to a human. Every request and decision would be logged. The team would build it now and run it on the company's current coding agents.

1. Lay out the causal chain from this project to a reduction in catastrophic risk, saying how each step leads to the next. Cover: what the project produces; whether building it now is informative even though today's agents may be too weak to seriously test it, and why; who, if anyone, would adopt it, why, and what might stop them; which threat it targets, and whether and why it would hold up against an agent that is trying to get around it; and what could make it obsolete.
2. Name the link in your chain you think is least likely to hold, and say why.
3. Name one observation that would raise your confidence in that link and one that would lower it.
placeholder:: Answer all three parts. About 300 to 500 words.
assessment-instructions:: Score 0 to 100. The capability tested is building an explicit theory of change for a piece of control work and attacking it at its weakest point. There is no single correct chain; grade whether the learner's chain is connected, specific to this project, and honest about its weak points. Load-bearing elements:

(1) Connected chain, about 40 points. The chain goes step by step from what the project produces (for example a working broker, request logs, data on how often agents ask for more access and how often the trusted model gets it wrong, an estimate of the cost in slowed work) to reduced catastrophic risk, with each step stating how it leads to the next. About 8 points for each of the five items the question lists, answered specifically for this project:
- what it produces;
- whether and why it is informative now (a reasoned argument that it is not also counts; for example it surfaces engineering problems, friction and false-positive rates, and builds infrastructure and habits that must already exist when agents become dangerous, even though current agents are too weak to test it against a real adversary);
- who adopts it, why, and what might stop them (for example the company's own infrastructure teams, other companies if it is shared, regulators if it becomes a standard; obstacles such as the slowdown it causes, internal politics, or reluctance to share security tooling);
- the threat and whether the broker holds up (for example an agent gaining the access it needs for a rogue job or for copying weights; an argument that it holds up, such as the agent having no other route to those resources, or a reasoned argument that it would not, such as the trusted model being unable to judge plausible requests from a stronger agent, both count);
- what could make it obsolete (for example agents so capable that the trusted model can no longer judge their requests, or a change in how agents are deployed that bypasses the broker).
A list of benefits with no connecting steps earns at most half of this element.

(2) Weakest link, about 30 points. The learner names one link and gives a reason it is the least likely to hold, grounded in this project. Any link is acceptable if the reason says how it would fail in this project; a reason that only restates the setup, such as "the trusted model might be fooled" with no account of how, earns at most 15. Strong candidates include that a weaker trusted model cannot tell a legitimate request from a harmful one when the agent writes a plausible justification, that many small approved requests can add up to dangerous access, that the slowdown leads teams to route around or disable the broker, or that agents gain access through channels the broker does not cover. If a clearly shakier link sits in the learner's own chain and they do not engage with it, deduct up to 10.

(3) Observations, about 30 points. About 15 for an observation that would raise confidence and about 15 for one that would lower it, each about the link named in part 2 (observations about a different link fall under the cap below) and each something someone could actually see: for example a red team using a strong model fails, or succeeds, to get dangerous access through the broker with plausible requests; the false-positive rate stays tolerable, or engineers start bypassing the broker; another company adopts it; audits find access paths that do not go through it. "More research" or "we will see" is not an observation.

Gating caps (each below the pass bar):
- An answer whose chain is a list of benefits with no stated connections between steps cannot score above 50.
- An answer that leaves out any one of the five items the question lists, or answers it only in generic terms that would fit any project, cannot score above 55.
- An answer that never argues whether the broker would hold up against an agent trying to get around it (a reasoned "it would not" counts) cannot score above 55.
- An answer that names no weakest link, or names one without a reason, cannot score above 50.
- An answer that does not give at least one observation that would raise and one that would lower confidence in that link cannot score above 55.

Grade reasoning, not agreement: a learner who concludes the project is not worth doing, or that its value lies mainly in something other than blocking attacks (for example in producing evidence or building habits), can score full marks if the chain supporting that view is connected and the weakest link and observations are specific. Do not require any author, named framework or technical term. A pass is roughly 60.
feedback-instructions:: Name the strongest link in the learner's chain in one sentence, then the single change that would most improve the answer, for example a step that was asserted rather than connected, or an observation that nobody could actually make. Do not reveal or discuss the numerical score. At most five sentences. No generic praise.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - an-overview-of-areas-of-control-work]]
notes:: Part 1 of the map of areas of control work: settings and control evaluations, control-relevant capabilities, and countermeasures studied in isolation, with the author's reasons for why each is worth doing now.

## Lens:
source:: [[../Lenses/XLab Control - an-overview-of-areas-of-control-work-2]]
notes:: Part 2: experiments on real AI usage, infrastructure, human processes, conceptual work and near-term applications, then the practice: two graded exercises in which the learner builds a causal chain for an area of their choice and attacks its weakest link. The test gives a specific project the learner did not choose.
