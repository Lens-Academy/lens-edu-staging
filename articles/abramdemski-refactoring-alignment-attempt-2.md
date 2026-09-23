---
title: "Refactoring Alignment (attempt #2)"
author:
  - "abramdemski"
source_url: "https://www.lesswrong.com/posts/vayxfTSQEDtwhPGpW/refactoring-alignment-attempt-2"
published: 2021-07-26
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "I've been poking at Evan's Clarifying Inner Alignment Terminology. His post gives two separate pictures (the objective-focused approach, which he foc…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[I've been](https://www.lesswrong.com/posts/7fkaJLzRiEr2hmSDi/re-define-intent-alignment) poking at Evan's [Clarifying Inner Alignment Terminology.](https://www.lesswrong.com/posts/SzecSPYxqRa5GCaSF/clarifying-inner-alignment-terminology) His post gives two separate pictures (the objective-focused approach, which he focuses on, and the generalization-focused approach, which he mentions at the end). We can consolidate those pictures into one [and-or graph](https://en.m.wikipedia.org/wiki/And%E2%80%93or_tree) as follows:

![](https://39669.cdn.cke-cs.com/rQvD3VnunXZu34m86e5f/images/af70fce5c4a80a2368c70f0dd543bd1dc252f24475558179.png)

And-or graphs make explicit which subgoals are jointly sufficient, by drawing an arc between those subgoal lines. So, for example, this claims that _intent alignment + capability robustness_ would be sufficient for _impact alignment_, but alternatively, _outer alignment + robustness_ would also be sufficient. I've also added colors to make it a bit clearer.

The red represents what belongs entirely to the generalization-focused path. The yellow represents what belongs entirely to the objective-focused path. The blue represents everything else. (In this diagram, all the blue is on _both_ paths, but that will not be the case in my next diagram.)

Note, in particular, that both paths seek _outer alignment + objective robustness + capability robustness_. According to the above picture, the disagreement between the two paths is _only_ one of which of these sub-goals are better grouped together.

But this doesn't seem to actually be true. [Objective Robustness and Inner Alignment Terminology](https://www.lesswrong.com/posts/pDaxobbB9FG5Dvqyv/discussion-objective-robustness-and-inner-alignment) points out that, really, the two approaches want to define some of the terminology differently. [My previous post on the subject](https://www.lesswrong.com/posts/7fkaJLzRiEr2hmSDi/re-define-intent-alignment) suggests even more differences. Putting these things together, and with some other revisions, I suggest this _revised joint graph:_

![](https://39669.cdn.cke-cs.com/rQvD3VnunXZu34m86e5f/images/a79d77ff6c2f70bf559e597f292f3a6c48afd0c38b161255.png)

The and-or graph here has been supplemented with double-headed arrows, which indicate a looser relationship of pseudo-equivalence (more on this later).

## Definitions: ^definitions

-   **Behavioral Alignment:** This is just another way to say "impact alignment" that's more consistent with the rest of the terminology. Behavioral alignment means alignment in terms of what the system actually does. I don't want to delve into the definition of the term "alignment" itself in this post, so, that's about all I can say.
-   **Inner Robustness:** This means that the mesa-objective is efficiently pursued under a wide range of circumstances (ie, including distributional shift). In other words: whatever the mesa-optimizer wants, it is broadly capable of achieving it.
-   **On-Distribution Alignment:** _Objective Robustness and Inner Alignment_ pointed out that the generalization-focused path re-defines "outer alignment" as "alignment on the training distribution" (so that we can then think of the rest of the alignment problem as a problem of generalization). I take this to mean both that the base objective is aligned on the training distribution, and that the behavior of the trained system is aligned on the training distribution. (One implies the other, if training succeeds.)
-   **Robustness:** Performing well on the base objective in a wide range of circumstances.
-   **Intent Alignment:** A model is intent-aligned if it has a mesa-objective, and that mesa-objective is aligned with humans. (Again, I don't want to get into exactly what "alignment" means.)
-   **Capability Robustness:** As elsewhere, I define this as performing well on a behavioral objective even off-distribution. The system is highly capable _at something,_ but we say nothing about what that thing is.
-   **Objective Robustness:** The behavioral objective of the system is aligned with the base objective, even under distributional shift. \[EDIT: I now want to re-define this as follows: _the behavioral objective generalizes **acceptably**. See discussion under "red lines"._\]
-   **Inner Alignment:** A system is inner-aligned if it has a mesa-objective, and that mesa-objective is aligned with the base objective.
-   **Outer Alignment:** The base objective is aligned with humans.

## Yellow Lines: ^yellow-lines

These lines represent the objective-centric approach. I think this rendering is more accurate than Evan's, primarily because my definition of intent alignment seems truer to Paul's original intention, and secondarily because inner alignment and outer alignment now form a nice pair.

-   **Inner Alignment + Outer Alignment** $\to$  I**ntent Alignment:** This is by transitivity of alignment. If the mesa-objective is aligned with the base objective, and the base objective is aligned with humans, then the mesa-objective will be aligned with humans.
-   **Intent Alignment + Inner Robustness** $\to$ **Behavioral Alignment:** If something is intent-aligned, and also achieves its intent reliably, then it must be behaviorally aligned.

This path apparently implies building goal-oriented systems; all of the subgoals require that there _actually is_ a mesa-objective. In contrast, I think researchers who identify with this path probably _don't_ all think the end result would necessarily be goal-oriented. For example, my impression of what people mean by "solving the inner alignment problem" includes _building systems which robustly avoid having inner optimizers at all._ This is not well-represented by the proposed graph.

We could re-define "inner alignment" to mean "the mesa-objective aligns with the base objective, _or_ the system lacks any mesa-objective" -- but this includes a lot of dumb things under "inner aligned", which seems intuitively wrong. 

A closer term is [acceptability](https://www.lesswrong.com/posts/9Dy5YRaoCxH9zuJqa/relaxed-adversarial-training-for-inner-alignment), which could plausibly be defined as "not actively pursuing a misaligned goal". However, I was not sure how to put anything like this into the graph in a nice way.

## Red Lines: ^red-lines

These lines represent the generalization-focused approach.

-   **Capability Robustness + Objective Robustness** $\to$ **Robustness:** We perform well on the behavioral objective in a wide range of circumstances; and, the behavioral objective is aligned with the base objective in a wide range of circumstances; therefore, we perform well on the base objective in a wide range of circumstances.
-   **Robustness + On-Distribution Alignment** $\to$ **Behavioral Alignment:** We perform well on the base objective in training, and we generalize well, therefore we perform well in general.

This approach has some distinct advantages over the objective-focused approach. First, it does not assume the existence of inner optimizers at any point. It is possible that this approach could succeed without precisely defining "inner optimizer", identifying mesa-objectives and checking their alignment, or anything like that. Second, this approach can stand on the shoulders of existing statistical learning theory. If the whole problem boils down to generalization guarantees, then perhaps we just need to advance work on the same kinds of problems which machine learning has faced since its inception.

A subtlety here is that the base objective matters in two different ways. For "on-distribution alignment", we only care about how the base objective performs on the training data. This makes sense: that's the only way it effects training, so why would we care about correctly specifying outer alignment off-distribution? Instead, we rely on generalization to specify that part correctly. This seems like an advantage to the approach, because it greatly reduces the outer alignment problem.

However, objective robustness _also_ depends on the base objective, and _specifically depends on the off-distribution behavior of the base objective_. This reflects the fact that _to generalize correctly, the system does need to get information about the off-distribution base objective somehow_. But how? In prosaic AI, only on-distribution behavior of the loss function can influence the end result.

I can see a few possible responses here.

1.  Double down on the "correct generalization" story: hope to somehow avoid the multiple plausible generalizations, perhaps by providing enough training data, or appropriate inductive biases in the system (probably both).
2.  Achieve objective robustness through other means. In particular, inner alignment is supposed to imply objective robustness. In this approach, inner-alignment technology provides the extra information to generalize the base objective appropriately.

Response #2 is consistent with how the generalization-focused path has been drawn by others; IE, it includes inner alignment as a subgoal of objective robustness. However, including this fully in the generalization-focused path seems unfortunate to me, because it adds mesa-objectives as a necessary assumption (since inner alignment requires them). Perhaps dealing directly with mesa-objectives is unavoidable. However, I would prefer to be agnostic about that for the time being.

EDIT: 

I now think (to fix the above-mentioned problem, and to represent [Rohin's view](https://www.lesswrong.com/posts/7fkaJLzRiEr2hmSDi/re-define-intent-alignment?commentId=JxYTNAJkQdrFFfiFH) more accurately) we should re-define objective robustness as follows:

**Objective Robustness:** The behavioral objective generalizes _acceptably_. 

The notion of "acceptable" is left purposefully open, but it [should have two desirable properties](https://ai-alignment.com/training-robust-corrigibility-ce0e0a3b9b4d):

1.  We should be happy with a model if we know it has high average-case performance (on training data) _and_ we know it has acceptable performance generally. In other words, it should bridge the gap in the argument.
2.  Acceptability should not be too much of a burden. Hopefully, generalizing _acceptably_ is easier than generalizing _exactly correctly_.

## Blue Lines: ^blue-lines

### Inner Robustness and Capability Robustness ^inner-robustness-and-capability

Inner robustness implies capability robustness, because we know there's a goal which the system performs well on in a broad variety of circumstances. (Inner robustness just tells us a bit more about what that goal is, while capability robustness doesn't care.) 

Capability robustness sort of implies inner robustness, if we assume a degree of agency: it would be pretty strange for the system to robustly pursue _some other_ goal than its mesa-objective.

However, these implications require the presence of an inner optimizer. In particular, capability robustness obviously won't imply inner robustness in the absence of one of those.

### Inner Alignment and Objective Robustness ^inner-alignment-and-objective

Evan argued that inner alignment implies objective robustness. This argument requires that the agent is capable enough that its behavioral objective will match its mesa-objective, even under distributional shift.

We could also argue in the other direction: if something is behaviorally aligned with the base objective in a broad variety of circumstances, then (again assuming sufficient agency), surely it must not have a misaligned objective.

Again, these implications only make sense if there _is_ a mesa-objective.

### On-Distribution Alignment and Outer Alignment ^on-distribution-alignment-and-outer

Outer alignment implies on-distribution alignment trivially. On-distribution doesn't imply outer alignment by any means, but the pseudo-equivalence here is because _outer alignment doesn't matter beyond the influence of the base objective on training_; so, at least for prosaic AI, outer alignment shouldn't matter beyond on-distribution alignment.

### Equating Pseudo-Equivalences ^equating-pseudo-equivalences

If we collapse all the pseudo-equivalent subgoals, we get an and-or graph which looks quite similar to the one we started out with:

![](https://39669.cdn.cke-cs.com/rQvD3VnunXZu34m86e5f/images/280dd84a1bdb8de1ce69f9c1c06c823b4674fb234e17f18f.png)

This makes clear that both approaches have an "inner alignment type thing", an "outer alignment type thing", and a "capability type thing"; they just define these things differently:

|  | Objective-Focused Approach | Generalization-Focused Approach |
| --- | --- | --- |
| Outer cluster: | Base objective is aligned with humans. | Base objective is aligned with humans on-distribution. |
| Inner cluster: | Mesa-objective exists and is aligned with base objective. | (Robust) behavioral objective exists and is aligned with base objective. |
| Capabilities cluster: | Achieves high performance on the mesa-objective, in a broad variety of situations. | Achieves high performance on behavioral objective in a broad variety of situations. |
| Grouping: | (outer + inner) + capabilities | outer + (inner + capabilities) |

This may be an easier way to remember my larger graph.

## Other remarks: ^other-remarks

### Definition of "Alignment" ^definition-of-alignment

I've used the term "aligned" in several definitions where Evan used more nuanced phrases. For example, inner alignment:

-   Evan: _A mesa-optimizer is inner-aligned if the optimal policy for its mesa-objective is impact aligned with the base objective._
-   Me: _A system is inner-aligned if it has a mesa-objective, and that mesa-objective is aligned with the base objective._

Evan's definition seems more nuanced and useful. It puts some gears on the concept of alignment. It averts the mistake "aligned means equal" (if humans want to drink coffee, that _should not imply_ that aligned robots want to drink coffee). It captures the idea that goal alignment has to do with high levels of performance (we don't want to label something as misaligned just because it makes dumb mistakes).

However, I'm not confident that the _details_ of Evan's locutions are quite right. For example, should alignment be tested only _in terms of the very best policy?_ This seems like a necessary condition, but not sufficient. If behavior is severely misaligned even for some very very high-performance policies (but technically sub-optimal), then the alignment isn't good enough; we don't expect training to find the very best policy.

So, I think it better to remain somewhat ambiguous for this post, and just say "aligned" without going further.

### Other Nuances ^other-nuances

Note that with my re-definition of "objective robustness", the generalization-focused path now implies achieving a weaker kind of alignment: the objective-focused approach achieves what we might call _strong alignment_, where the system is robustly pursuing aligned goals. The generalization-focused approach will be weaker (depending on how exactly "acceptability" gets defined), only guaranteeing that the resulting system _doesn't_ do something terrible. (This weaker form of alignment seems very reasonable to me.)

This means we can split the top bubble into objective/generalization -focused versions, like the others. If we really want, we can also come up with split definitions of "robustness" and "intent alignment", so that the whole graph gets split, although this doesn't seem particularly useful.

The "task AI vs goal-directed AI" distinction deserves a mention. To some extent, the objective-focused approach is all about goal-directed AI, while the generalization-focused approach remains more agnostic. However, it _could_ be that task-based systems still have mesa-objectives (EG "do what the user says"), just _myopic_ ones. Part of inner alignment is then to ensure myopia.

### Meta-thoughts on the graph/terminology. ^meta-thoughts-on-the-graph

Generally, I felt like if I had chosen more things to be careful about, I could have made the graph three times as big. It's tempting to try and map out all possible important properties and all possible approaches. However, the value of a map like this rapidly diminishes as the map gets larger. Which things to make perfectly clear vs muddy is a highly subjective choice. I would appreciate feedback on the choices I made, as this will inform my [write-up-to-come](https://www.lesswrong.com/posts/a7jnbtoKFyvu5qfkd/formal-inner-alignment-prospectus). (This post will resemble the first major section of that write-up.)

Also, I'm not very committed to the terms I chose here. EG, using "behavioral alignment" rather than "impact alignment". I welcome alternate naming schemes.

I find myself thinking that objective robustness is actually what I mean by _the inner alignment **problem**._ [Abergal](https://www.lesswrong.com/posts/pDaxobbB9FG5Dvqyv/discussion-objective-robustness-and-inner-alignment?commentId=eiimYPskDKRs5A9KX) voiced similar thoughts. But this makes it seem unfortunate that "inner alignment" refers specifically to the thing where there are mesa-optimizers. I'm not sure what to do about this.
