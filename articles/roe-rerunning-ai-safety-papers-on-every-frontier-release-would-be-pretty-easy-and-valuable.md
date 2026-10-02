---
title: "Rerunning AI safety papers on every frontier release would be pretty easy and valuable"
author:
  - "Zephaniah Roe"
  - "hersheys"
  - "yix"
source_url: "https://www.lesswrong.com/posts/oKxc8maZGtnzgpNzx/rerunning-ai-safety-papers-on-every-frontier-release-would-1"
published: 2026-08-15
created: 2026-10-02
accessed: 2026-10-02
llm-review:
  date: 2026-10-02
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-02
    kind: "live"
description: "tl;dr: Some important AI safety research is never rerun on the newest models. There are probably cases where this would be valuable and a single well…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_tl;dr: Some important AI safety research is never rerun on the newest models. There are probably cases where this would be valuable and a single well-positioned researcher could likely do this with sufficient funding._

This summer, [Second Look Research](https://secondlookresearch.com/) (SLR) is running a summer fellowship dedicated to empirical replications of AI safety research. Many of our most interesting results so far came from replicating previous results on newer or more capable models. 

For example, it is perhaps useful to know that Google’s [CoT monitorability experiments continue to hold for models like GPT-5.5](https://www.lesswrong.com/posts/AoBTiL7XRRpwpev8p/llm-cots-remain-monitorable-when-being-unfaithful-requires), which are qualitatively more capable than the models originally tested. Likewise, continuing to track [Ryan Greenblatt’s filler token results on more capable models](https://www.lesswrong.com/posts/NYzYJ2WoB74E6uj9L/recent-llms-can-use-filler-tokens-or-problem-repeats-to) gives a fuzzy signal indicating how much newer models can use innocuous tokens to hide additional reasoning in a forward pass. These kinds of experiments do not lose value over time! It’s important to track whether safety-relevant model properties still hold in new model releases and to be aware of any changes.

It can sometimes be difficult to rerun results on newer models because codebases can be incomplete, have parameters that differ from the original paper, or may not be open source to begin with. We ran into all of these problems throughout the fellowship when trying to replicate experiments. But because SLR has already gone through the effort to replicate the original results of several influential AI safety papers, we know that we have codebases that are complete, produce numbers that won’t surprise us, and could be updated for new models. For papers that already have a replication, adding a new model is a single terminal command away, or at the most a single Claude prompt away.

## What could this actually look like? ^what-could-this-actually

We imagine that when a new model comes out, a competent undergrad we trust can run several experiments we select overnight and review & verify the results. Depending on the paper, this costs somewhere between $0 and $5,000.[^note-1]

If the undergrad surfaces something sufficiently important or a step change, we could immediately communicate this result to stakeholders. If they don’t find anything interesting, we can simply post a result to our website saying we didn’t find anything unexpected. All research communication will be read over by a more experienced member of the team before being pushed out.

After these experiments are completed, we can update a tracker of current trends we see in the different experiments we are tracking. This may surface subtle safety trends that nobody would notice otherwise.

## Does this actually provide value? ^does-this-actually-provide

Or a related question: Aren’t the most important evaluations and model properties already covered in model system cards? It's possible that a lot of research goes stale because it's not that interesting and that the field is pretty good at deciding which properties are relevant enough to keep testing. Additionally, corrective feedback loops already exist: for example, if a model card doesn’t evaluate something it should, people can complain and the company can adjust that in their next model card.

Within what would traditionally be considered evaluations (capability & risk), the most useful ones do get run.  However, our replications cover very different questions than typical evals run by organizations (e.g. METR, Apollo, Palisade) and frontier labs. We would run full experiments from safety papers, some of which include an eval phase, but wouldn’t be counterfactually performed by others doing alignment evals.

While Anthropic’s model cards contain safety-relevant information, there are some tests that are consistently left out even though they aren’t that expensive or difficult. OpenAI, GDM, and xAI can have very limited system cards. Overall, we notice that work that is less evals-shaped (e.g., [internal state control](https://transformer-circuits.pub/2025/introspection/index.html#control), [peer preservation](https://arxiv.org/pdf/2604.19784), or [filler token evals](https://www.lesswrong.com/posts/NYzYJ2WoB74E6uj9L/recent-llms-can-use-filler-tokens-or-problem-repeats-to)) is less likely to be included in a system card or run by an external evaluator and we think we can cover some of this gap.

As a sample, these are the kinds of results we would consider targeting:

1.  [Teaching Claude Why](https://www.anthropic.com/research/teaching-claude-why) midtraining experiments on new open source models (replication coming out in the following weeks)
2.  CoT hint following experiments (replication [here](https://www.lesswrong.com/posts/AoBTiL7XRRpwpev8p/llm-cots-remain-monitorable-when-being-unfaithful-requires))
3.  Single-forward pass filler token evals (replication [here](https://www.lesswrong.com/posts/bxaWTNrdgJpkLXmgm/single-forward-pass-evals-on-fable-opus-5-and-gpt-5-6-sol) and more results coming soon)
4.  Internal state control on new open source models (replication [here](https://www.lesswrong.com/posts/Dvqmgfeu2KDF7uMkx/internal-state-control-is-a-general-property-of-llms))
5.  Hidden role games to measure adversarial reasoning under uncertainty (original post [here](https://jlucassen.com/hidden-role-games-as-a-trusted-model-eval/), replication coming soon)
6.  Subliminal learning (original paper [here](https://arxiv.org/pdf/2507.14805)). We expect subliminal learning to replicate on new open source models but quantitative trends may be interesting.[^note-2]

## Logistical challenges with continuing to update AI safety research with new models ^logistical-challenges-with-continuing

### What if people don’t want to do this? ^what-if-people-dont

The most obvious reason people don't do this is that it’s not incentivized, unlikely to turn into a full publication, and therefore top talent isn’t interested in it or they have better things to do. Fortunately the only real bottleneck is competent analysis of results, and having a single trusted undergrad can unblock this. This enables newer members of the field to contribute to useful, entry-level research and offers a stepping stone from an intro fellowship to impactful AI safety work.

### What if rerunning old code on new models can be kind of hard actually? ^what-if-rerunning-old

Even when open sourced, codebases aren’t always trivial to rerun. Ensuring the code matches the experiments run by the authors and setting up the codebase to easily run on new models adds time and effort to the process. For this reason, we plan to primarily focus on papers we have already replicated, since we’ve already invested the effort to set up the infrastructure for rerunning experiments. Right now this list is small, but will continue to grow.

### Research communication is hard ^research-communication-is-hard

Even if rerunning the experiments turns out to be trivial, actually communicating results coherently won’t necessarily be easy. In our experience over the summer, writing up final results can take longer than doing the engineering for the replication itself. Being able to quickly synthesize empirical results into clear, actionable claims requires a strong understanding of the experiments being run and knowing what findings to index on, which doesn’t always come naturally.

This is the kind of bottleneck that’s not entirely avoidable, but can be fixed with some hands-on mentoring and a few rounds of feedback. This is time-consuming relative to running the code to begin with, but overall we think it's worth our time.

## Conclusion ^conclusion

We plan to pilot this idea with a single part-time undergraduate and a small compute budget in the fall. Depending on feedback on this blog post and on the work as it begins to roll out, we may scale this idea up or down.

  

[^note-1]: Of course, some experiments could stretch beyond $5,000, but this is an edge case that would require special justification.
[^note-2]: This is an edge case where we don’t plan on replicating the original paper from scratch even though we think it would be valuable to rerun the experiments on new open weight releases. Because the original codebase is high quality, and the results have been replicated by others, we don’t see a replication itself as being a valuable contribution, so we would just use the code released with the paper and adapt it to new models.
