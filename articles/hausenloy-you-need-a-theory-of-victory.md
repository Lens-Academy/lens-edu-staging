---
title: "You Need A Theory of Victory"
author:
  - "Jason Hausenloy"
source_url: "https://firstscattering.com/p/you-need-a-theory-of-victory"
published: 2026-05-06
created: 2026-07-26
accessed: 2026-07-26
description: "The cause of AI safety is losing. Consider asking: how can we win?"
tags:
  - "article-importer"
---

%%
ARTICLE STUB — the article itself has not been imported yet.

Initial thoughts, 2026-07-26:
- Possible intermediate material for Theory of change and impact pathways.
- Strongest as a prompt for constructing and stress-testing an impact pathway.
- The account of AI-safety strategy camps is opinionated and should not be used as a neutral overview without counter-material.

I don't know, to me it seems nice that it points out that there are different camps?
Okay so split this into two lenses:
- a Lens explaining theories of victory. Attach to some LO about ToC/ToV
- a lens explaining the two AI Safety camps (And Jason's takes on them). Attach to some LO about Camps in AI Safety

%%

_Note: The majority of this post is adapted from a talk I gave recently. These do not represent the views of my employer._

Scroll around the organizations on this cute [AI safety map](https://aisafety.com/map). Think about, or ask, how does their work help with AI safety?

My guess is that, maybe some won’t know, but most would say “X of our actions will lead to Y self-evidently good outcome.”

-   Maybe, they’ll say, if we [measure model capabilities well](http://metr.org/) (we have _the graph_), policymakers will wake up and see AIs are improving quickly, and get their act together. In the best case, we could become a neutral third-party evaluator, and we could tell the labs that they can’t release the next model because our autonomy & deception evals say it’s too dangerous. Better information leads to better decision-making. You couldn’t be against that.
    
-   Maybe, if we invent the [scaffolds for the right AI monitors](http://redwoodresearch.org/) (AIs looking at the output of other AIs), we could coax interesting work out of near-AGI systems that _we don’t trust_ to help automate alignment. In the best case, these millions of automated AI alignment researchers, at the brink of AGI, solve the problem. You couldn’t be against that.
    
-   Maybe, at least publicly, [there is no unifying thread to our work](http://safe.ai/). We do things that are the obvious low hanging fruit, again and again and again, and that’s how we contribute value. Maybe we help [whistleblowers](http://aiwi.org/), or [potentially-sentient AIs](https://eleosai.org/), or [research mentors with good taste](http://matsprogram.org/). Maybe we ask [unusual philosophical questions](http://forethought.org/). Maybe we meld into the [national security establishment](http://rand.org/), or the [government](https://horizonpublicservice.org/programs/become-a-fellow/). Maybe we organize a [movement of people](https://pauseai.info/). Maybe we just [say the truth](https://intelligence.org/). Surely, you couldn’t be against that.
    

Perhaps you can see the holes in some of these arguments, or actions. But “generically good thing” isn’t enough! Take that thread, ask the question: how do these actions, in concert with others, lead to us “winning?” I would argue, however, that very few of the actions or organizations have a _theory of victory_ -- **a full (causal) story of the steps that need to go right, and a plan to achieve them.** Very few begin to ask.

In April, I gave a talk at an AI policy workshop about these theories of victory, and how to develop your own. The rest of this post is an annotated and lightly edited version of the talk below. It’s a long one.

## Overview

The main claim, up top:

{--{"author":"Luc's AI","timestamp":1785094252381}@@[--}{++{"author":"Luc's AI","timestamp":1785094252381}@@**My claim**++}

{--{"author":"Luc's AI","timestamp":1785094252381}@@![](https://substackcdn.com/image/fetch/$s_!IAqQ!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc56a3a80-cb9f-4390-8efd-3a8fac283d5f_958x540.png)

](https://substackcdn.com/image/fetch/$s_!IAqQ!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc56a3a80-cb9f-4390-8efd-3a8fac283d5f_958x540.png)--}{++{"author":"Luc's AI","timestamp":1785094252381}@@1. Theories of victory motivating different work are important to understand.
2. None of them are *sufficient* (including mine…)
3. You should think about yours anyway.++}

We’ll quickly preview:

{--{"author":"Luc's AI","timestamp":1785094252688}@@[--}{++{"author":"Luc's AI","timestamp":1785094252688}@@**Overview**++}

{--{"author":"Luc's AI","timestamp":1785094252688}@@![](https://substackcdn.com/image/fetch/$s_!UOf8!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F62159ab3-2440-4ad5-bb8c-f3fc866bc9f2_2946x1658.png)

](https://substackcdn.com/image/fetch/$s_!UOf8!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F62159ab3-2440-4ad5-bb8c-f3fc866bc9f2_2946x1658.png)--}{++{"author":"Luc's AI","timestamp":1785094252688}@@1. What does victory mean?
2. Defining a theory of victory
3. Two camps in AI safety:
   - “US wins + automated alignment + control + muddling”
   - “Superintelligence ban + saying true things + crisis + treaty”
   - Many more…
4. Developing strategic taste:
   - All theories of victory are wrong; some are useful
   - Developing your own
   - Traps to avoid++}

## What is “Victory”?

There are many different potential threat models in AI.

{--{"author":"Luc's AI","timestamp":1785094252950}@@[--}{++{"author":"Luc's AI","timestamp":1785094252950}@@**Different threat models**++}

{--{"author":"Luc's AI","timestamp":1785094252950}@@![](https://substackcdn.com/image/fetch/$s_!rqKH!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5dcf427e-636c-4bc2-ae55-4f5778bef7db_1168x608.png)

](https://substackcdn.com/image/fetch/$s_!rqKH!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5dcf427e-636c-4bc2-ae55-4f5778bef7db_1168x608.png)--}{++{"author":"Luc's AI","timestamp":1785094252950}@@- AI misuse
- Self-sustaining AIs
- Intelligence recursion
- Concentration of power
- Job loss
- …++}

Many people in many different organizations care about many different things, but perhaps two that we can agree on are:

{--{"author":"Luc's AI","timestamp":1785094253252}@@[--}{++{"author":"Luc's AI","timestamp":1785094253252}@@**Broadly agreeable things**++}

{--{"author":"Luc's AI","timestamp":1785094253252}@@![](https://substackcdn.com/image/fetch/$s_!YReV!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc7847741-95af-4895-b2fe-abbcb16f1257_1182x426.png)

](https://substackcdn.com/image/fetch/$s_!YReV!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc7847741-95af-4895-b2fe-abbcb16f1257_1182x426.png)--}{++{"author":"Luc's AI","timestamp":1785094253252}@@1. We don’t die.
2. The benefits of AI are broadly distributed.++}

Perhaps there is a more specific vision of what a good future might look like, perhaps some form of Utopia (like Forethought’s [Viatopia](https://www.forethought.org/research/viatopia) or Nozick’s “ [Utopia of Utopias](https://en.wikipedia.org/wiki/Anarchy,_State,_and_Utopia) ” and Alexander Wales’ [lovely fictionalization of it](http://jason.ml/end)), but for this talk we’ll stick to the broadly agreeable things.

[

![](https://substackcdn.com/image/fetch/$s_!wfAq!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb5655b9f-5de4-422f-8368-d82a47e7d221_1184x658.png)

](https://substackcdn.com/image/fetch/$s_!wfAq!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb5655b9f-5de4-422f-8368-d82a47e7d221_1184x658.png)

## Theories of Victory (ToVs)

To achieve a good outcome, people normally advocate for “theories of change”, which tend to take the form: “here’s my best guess for a causal chain for my action X causes Y.” X is a well-defined action (start an organization, run this media campaign etc.), and Y is a broadly-accepted “good thing” (“increases awareness of AI risks” “increases the probability of rational decision-making”)

[

![](https://substackcdn.com/image/fetch/$s_!Mpzc!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3e11f93e-a63b-4d2b-8df2-74d412f1150d_1164x610.png)

](https://substackcdn.com/image/fetch/$s_!Mpzc!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3e11f93e-a63b-4d2b-8df2-74d412f1150d_1164x610.png)

This is, however, importantly distinct from a “Theory of Victory”, which I would understand as the full (causal) story of the steps that need to go right for us to “win” (where, borrowing the broadly-agreeable understanding of “win” from earlier -- we don’t die + the benefits of AI are broadly distributed.)

There’s this great quote from HPMOR against complex, multi-step plans ([cited](https://slatestarcodex.com/2019/01/31/book-review-zero-to-one/) originally in Scott Alexander’s brilliant book review of Zero to One). I disagree! Yes, indeed, they are fragile, but you should know the causal story of how _all the actions_ are going to lead to the correct things happening.

So how’s this different from a Theory of Change? It accounts for

1.  All of the actions of all the actors, the steps whether they are performed by you or not
    
2.  The full win condition, rather than simply a “self-evidently good action.”
    

{--{"author":"Luc's AI","timestamp":1785094253579}@@[

![](https://substackcdn.com/image/fetch/$s_!KJUV!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3fabb5d2-851a-420d-b4cd-ffbde9e216d5_1184x652.png)

](https://substackcdn.com/image/fetch/$s_!KJUV!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3fabb5d2-851a-420d-b4cd-ffbde9e216d5_1184x652.png)--}{++{"author":"Luc's AI","timestamp":1785094253579}@@> **Theory of Victory:** “The full story of the steps that need to go right for us to win.”
>
> “Father had told Draco about the Rule of Three, which was that any plot which required more than three different things to happen would never work in real life. Father had further explained that since only a fool would attempt a plot that was as complicated as possible, the real limit was two.”++}

\*\*\*

## ToVs in AI Safety

The next section of the talk is a quick overview of the explicit and implicit (unsaid) assumptions underlying what I, and regular readers of this blog, would term the “ [two camps in AI safety](https://firstscattering.com/p/two-camps-in-ai-safety).” I will say, they don’t often agree, and can have quite vicious disagreements indeed. (insert Freud here about the narcissism of small differences)

The camps are broadly the “alignment is hard but tractable” folks (“EAs” “moderates”) and the “if anyone builds it, everyone dies”) folks (or “doomers” “humanists”).

{--{"author":"Luc's AI","timestamp":1785094253878}@@[--}{++{"author":"Luc's AI","timestamp":1785094253878}@@**Two camps in AI safety** *(and the viciousness of small differences)*++}

{--{"author":"Luc's AI","timestamp":1785094253878}@@![](https://substackcdn.com/image/fetch/$s_!s49m!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcda7840e-37f8-4dc5-ac6d-10a5ee06c538_1152x646.png)--}{++{"author":"Luc's AI","timestamp":1785094253878}@@1. “AI alignment is hard but tractable” — or “EAs” or “moderates”
2. “If anyone builds superintelligence, everyone dies” — or “AI-notkilleveryoneists,” “doomers,” or “humanists”++}

{--{"author":"Luc's AI","timestamp":1785094253878}@@](https://substackcdn.com/image/fetch/$s_!s49m!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcda7840e-37f8-4dc5-ac6d-10a5ee06c538_1152x646.png)--}{++{"author":"Luc's AI","timestamp":1785094253878}@@The slide also quotes the Center for AI Safety distancing itself from effective altruism: “We believe the effective altruism movement is, unfortunately, controlled opposition. The less influence it has on AI Safety, the better.”++}

## Camp 1

In Camp 1, we find the vast majority of funding and attention in AI safety. One can maybe summarize the specific solution prescribed by this camp as “ _the right people need to win the race”_ (so, the US, for democracy’s sake, and Anthropic, so that responsible labs are in the lead, and you can buy time at the frontier to do safety work). This position is perhaps best captured by [Leopold’s Situational Awareness](https://situational-awareness.ai/), which is worth reading in full (but in particular “ [The Free World Must Prevail](https://situational-awareness.ai/the-free-world-must-prevail/) ”)

{--{"author":"Luc's AI","timestamp":1785094254126}@@[--}{++{"author":"Luc's AI","timestamp":1785094254126}@@**Theory 1: “US wins the race + automated alignment”**++}

{--{"author":"Luc's AI","timestamp":1785094254126}@@![](https://substackcdn.com/image/fetch/$s_!y2oN!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0aa3f266-a54e-4115-a651-54c484c1e42a_1166x654.png)--}{++{"author":"Luc's AI","timestamp":1785094254126}@@The slide points to three representative sources:++}

{--{"author":"Luc's AI","timestamp":1785094254126}@@](https://substackcdn.com/image/fetch/$s_!y2oN!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0aa3f266-a54e-4115-a651-54c484c1e42a_1166x654.png)--}{++{"author":"Luc's AI","timestamp":1785094254126}@@- Leopold Aschenbrenner’s *Situational Awareness*
- Dario Amodei’s *Machines of Loving Grace*
- Redwood Research’s *AI Control: Improving Safety Despite Intentional Subversion*++}

I’ll rapid-fire through a bunch of the explicit and implicit assumptions that underlie this worldview. The question of AI Alignment (getting AIs to do what we want), first and foremost, needs to be tractable: not to say that it is _easy_ -- though some in this camp will claim that we got lucky with current systems -- but that it is an “engineering-shaped” problem, with continuous improvement possible from existing system, and would benefit from it being automated.

If you believe these systems are controllable, then the _controller_ matters -- ideally it should be the best or most moral people (US/Anthropic), perhaps with some democratic input.

{--{"author":"Luc's AI","timestamp":1785094254491}@@[

![](https://substackcdn.com/image/fetch/$s_!DgWC!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F40c753f1-7233-48ee-a410-0d7b86bb9d85_1186x682.png)

](https://substackcdn.com/image/fetch/$s_!DgWC!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F40c753f1-7233-48ee-a410-0d7b86bb9d85_1186x682.png)--}{++{"author":"Luc's AI","timestamp":1785094254491}@@| Topic | Explicit | Implicit |
| --- | --- | --- |
| Tractability | Alignment is an engineering problem. Iterate on existing techniques. | The problem is continuous with past engineering successes. Current techniques are on the right track. |
| The race | US/Anthropic should win. Can’t impose too much alignment tax. | The winner’s values matter more than the act of building. Alignment tax is the binding constraint. |
| Nature of problem | Technical. Automate alignment research. | The bottleneck is researcher-hours, not conceptual clarity. More compute on alignment means more safety. |++}

This view would look favorably upon the progress that has been made so far, favorably upon the lab leaders (or at least some), where market incentives don’t result in everyone dying, and that existing techniques perform surprisingly well.

Automating alignment is a top priority (getting AIs to help us do our homework) and, implicitly, the alignment problem is one that AI can help solve without itself being aligned first (the entire “getting work from untrusted systems” motivation behind much of the [AI control agenda](https://blog.bluedot.org/p/ai-control)). This view is best written in Carlsmith’s “ [AI for AI safety](https://joecarlsmith.com/2025/03/14/ai-for-ai-safety/) ” series, but also hinted at by Jan Leike’s “ [Alignment is not solved but it increasingly looks solvable](https://aligned.substack.com/p/alignment-is-not-solved-but-increasingly-looks-solvable).”

{--{"author":"Luc's AI","timestamp":1785094291498}@@[

![](https://substackcdn.com/image/fetch/$s_!dESd!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff87a7bb3-35f5-4a49-9144-9b1480c3b041_1202x682.png)

](https://substackcdn.com/image/fetch/$s_!dESd!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff87a7bb3-35f5-4a49-9144-9b1480c3b041_1202x682.png)--}{++{"author":"Luc's AI","timestamp":1785094291498}@@| Topic | Explicit | Implicit |
| --- | --- | --- |
| Progress | Models are surprisingly good. Control and evals can work. | Surprise goodness is evidence, not luck. Model behavior is stable enough to monitor. |
| Lab leaders | Mostly well-intentioned. Market incentives help. | Good intentions plus market pressures approximate good governance. Culture substitutes for regulation. |
| RLHF | Catch scheming, retrain. Warning shots are useful. | Deception is detectable at a rate that matters. The system can absorb warning shots before catastrophe. |
| Automating alignment | Top priority — get AIs to help. | The alignment problem is the kind of problem AI can help solve without itself being aligned first. |++}

And finally, on “competitive pressures”, that a pause is unrealistic, and that the games and the incentives are fixed. Political action is harder to influence and has more backfire risk, that not building superintelligence ever is an economic and moral disaster, an existential risk of its own, and that the public should work within institutions, and build technocratic competence. Don’t, they say, activate forces that you can’t control.

{--{"author":"Luc's AI","timestamp":1785094291775}@@[

![](https://substackcdn.com/image/fetch/$s_!izfi!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F83a2d9d3-92f1-4af4-9ba3-7651e81905d3_1186x662.png)

](https://substackcdn.com/image/fetch/$s_!izfi!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F83a2d9d3-92f1-4af4-9ba3-7651e81905d3_1186x662.png)--}{++{"author":"Luc's AI","timestamp":1785094291775}@@| Topic | Explicit | Implicit |
| --- | --- | --- |
| Competition | Realists. Pause is unrealistic. | The game is fixed; we can only play it well. Political action is higher-cost than technical action. |
| Risk tolerance | Pragmatic tradeoffs. | The counterfactual to building is worse. Some existential risk is the price of the best outcome. |
| Public | Work within institutions. Upskill people. | Existing power structures are the right vehicle. Technocratic competence is the bottleneck. |++}

I will, here, interject with my opinion. Perhaps best summarized by my post “ [whose alignment research are we automating](https://firstscattering.com/p/whos-alignment-research-are-we-automating) ”, and the general take of we should not rely on the benevolence of individuals (like lab leaders) for our good outcomes, no matter how similar to us they seem (particularly crazy given that _those_ individuals are saying that the technology they are building may end the world), and that we should not rely on Kumbaya / rational decision-making / a warning shot to prevail for pausing right at the edge to do automated alignment research.

{--{"author":"Luc's AI","timestamp":1785094292038}@@[--}{++{"author":"Luc's AI","timestamp":1785094292038}@@**Theory 1 — the author’s opinion**++}

{--{"author":"Luc's AI","timestamp":1785094292038}@@![](https://substackcdn.com/image/fetch/$s_!tcSs!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0f0843b4-63fc-4b62-aebe-8134f1dde33b_1198x662.png)--}{++{"author":"Luc's AI","timestamp":1785094292038}@@1. Alignment is an engineering problem, not a scientific one. (??)
2. We trust lab leaders to distribute the benefits or act benevolently. (??)
3. We’ll pause right at the edge. (??)++}

{--{"author":"Luc's AI","timestamp":1785094292038}@@](https://substackcdn.com/image/fetch/$s_!tcSs!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0f0843b4-63fc-4b62-aebe-8134f1dde33b_1198x662.png)--}{++{"author":"Luc's AI","timestamp":1785094292038}@@The accompanying meme asks: “Whose alignment are we automating?”++}

## Camp 2

The second camp would, of course, advocate for a ban on superintelligence and, to achieve this, maybe a global treaty, because “if anyone builds it everyone dies.” FLI, for example, might advocate for a carve out of broad scientific and democratic consensus, but maybe not.

{--{"author":"Luc's AI","timestamp":1785094292305}@@[--}{++{"author":"Luc's AI","timestamp":1785094292305}@@**Theory 2: “Superintelligence ban + saying true things”**++}

{--{"author":"Luc's AI","timestamp":1785094292305}@@![](https://substackcdn.com/image/fetch/$s_!uLL7!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F63945fa5-1869-42d5-9fbe-6f640a5c2238_1246x688.png)--}{++{"author":"Luc's AI","timestamp":1785094292305}@@The slide highlights three representative claims:++}

{--{"author":"Luc's AI","timestamp":1785094292305}@@](https://substackcdn.com/image/fetch/$s_!uLL7!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F63945fa5-1869-42d5-9fbe-6f640a5c2238_1246x688.png)--}{++{"author":"Luc's AI","timestamp":1785094292305}@@- Prohibit the development of superintelligence until there is broad scientific consensus that it can be developed safely and controllably, together with strong public buy-in.
- “If anyone builds it, everyone dies.”
- Mitigating the risk of extinction from AI should be a global priority alongside other societal-scale risks such as pandemics and nuclear war.++}

Again, going through the different explicit and implicit assumptions. AI alignment is an unsolved _scientific_ problem, we have one critical try. Even if its only a 20% chance that we all die, why not do the more cautious thing, wait 5 years, and lower that further. This is _everyone’s lives._

There is no correct winner in the race, it’s “ _if anyone builds it.”_ The only winner of a US-China race to superintelligence is the superintelligence itself. The problem is therefore a political one -- we need to buy time through collective action, and the bottleneck isn’t technocratic competence or “thoughtfulness”, it’s aligning political incentives. The AI safety progress we’ve made so far, some of it has been significant, but much is safetywashing that does not help with the hard problem.

I’d recommend reading Eliezer’s “ [list of lethalities](https://www.lesswrong.com/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities) ”, [the case against AI control research](https://www.lesswrong.com/posts/8wBN8cdNAv3c7vt6p/the-case-against-ai-control-research) and [Control AI’s plan](https://www.alignmentforum.org/posts/TnAR5Sf5hphfnzNTr/preventing-extinction-from-asi-on-a-usd50m-yearly-budget), to get a flavor of what the views and actions of this crowd will be.

{--{"author":"Luc's AI","timestamp":1785094292567}@@[

![](https://substackcdn.com/image/fetch/$s_!wFv0!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6c6ba745-85dd-49a2-b9f7-fb9bc070723e_1196x676.png)

](https://substackcdn.com/image/fetch/$s_!wFv0!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6c6ba745-85dd-49a2-b9f7-fb9bc070723e_1196x676.png)--}{++{"author":"Luc's AI","timestamp":1785094292567}@@| Topic | Explicit | Implicit |
| --- | --- | --- |
| Tractability | Unsolved science. Not enough time. | There’s a discrete conceptual gap we haven’t crossed. Incremental progress creates false confidence. |
| The race | No right winner. Coordinate via treaty. | The artifact itself is the danger, not who holds it. Sovereignty over superintelligence is an illusion. |
| Nature of problem | Political. Buy time through collective action. | We already know enough to act. The bottleneck is institutional will, not knowledge. |
| Progress | No mechanistic understanding. Interpretability results are far from enough. | Surface behavior is a poor proxy for internal alignment. What we can’t see is what will hurt us. |++}

Yes, more, that lab leaders are rife with conflicts of interest, that the “AI safety” community has plausibly been net negative (with its $30m donation to OpenAI, its contribution to the funding and founding of Anthropic, the original inspiration of Deepmind). That RLHF, and RLHF++ and other existing alignment techniques will not be robust enough to prevent deception, particularly on hard to verify tasks, that we don’t know who’s research we are automating, and that sounds like a cop-out.

{--{"author":"Luc's AI","timestamp":1785094292827}@@[

![](https://substackcdn.com/image/fetch/$s_!LAb-!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F16027955-70b0-44c0-b4d8-5ec93fa48c7f_1198x648.png)

](https://substackcdn.com/image/fetch/$s_!LAb-!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F16027955-70b0-44c0-b4d8-5ec93fa48c7f_1198x648.png)--}{++{"author":"Luc's AI","timestamp":1785094292827}@@| Topic | Explicit | Implicit |
| --- | --- | --- |
| Lab leaders | Deep conflicts of interest. The safety community is possibly net negative. | Structural incentives dominate intentions. Proximity to the problem corrupts judgment about it. |
| RLHF | Punishment incentivizes deception, not alignment. | Selection pressure on behavior creates selection pressure on concealment. The training signal is adversarial. |
| Automating alignment | Whose research are we automating? | Automating confused research scales confusion. You can’t delegate a problem you haven’t framed correctly. |++}

Perhaps the method here is that if you say the true things loudly, combined with a crisis, that persuasion will be enough if you’re right (huh, notice how that is a bit similar to the evidence-presenting pitch of the first crowd…)

{--{"author":"Luc's AI","timestamp":1785094293107}@@[--}{++{"author":"Luc's AI","timestamp":1785094293107}@@**Theory 2 — method**++}

{--{"author":"Luc's AI","timestamp":1785094293107}@@![](https://substackcdn.com/image/fetch/$s_!0VgL!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd4aa8191-0583-4865-aa73-8b3dd394bf68_1082x514.png)

](https://substackcdn.com/image/fetch/$s_!0VgL!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd4aa8191-0583-4865-aa73-8b3dd394bf68_1082x514.png)--}{++{"author":"Luc's AI","timestamp":1785094293107}@@- Say true things loudly.
- Hope a crisis wakes people up before the final one.
- **Implicit:** persuasion is sufficient if you’re right enough.++}

I will, again, say that this theory of victory is _not sufficient!_ My opinion: in some versions, this worldview relies on a warning shot being legible and not catastrophic, that people who are right, and right loudly, can persuade powerful people, that government can act fast enough, and that there exists a stable equilibrium where we can just stop -- I’m skeptical of all of these, or not confident enough to bet humanity on it.

{--{"author":"Luc's AI","timestamp":1785094293367}@@[--}{++{"author":"Luc's AI","timestamp":1785094293367}@@**Theory 2 — the author’s opinion**++}

{--{"author":"Luc's AI","timestamp":1785094293367}@@![](https://substackcdn.com/image/fetch/$s_!FVqt!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd5a06424-eb44-41e4-a9a4-c80a5b054962_1226x624.png)

](https://substackcdn.com/image/fetch/$s_!FVqt!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd5a06424-eb44-41e4-a9a4-c80a5b054962_1226x624.png)--}{++{"author":"Luc's AI","timestamp":1785094293367}@@1. The warning shot is legible and not catastrophic. (?)
2. People who are right can persuade people who have power. (??)
3. Government will act competently — fast enough after being persuaded. (??)
4. There exists a stable equilibrium where we just stop, or dismantle the global compute supply chain. (?)++}

A quick recap

{--{"author":"Luc's AI","timestamp":1785094293651}@@[

![](https://substackcdn.com/image/fetch/$s_!WX6w!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbc5430f6-a639-4b11-bbeb-a29bf1bf20ed_1208x678.png)

](https://substackcdn.com/image/fetch/$s_!WX6w!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbc5430f6-a639-4b11-bbeb-a29bf1bf20ed_1208x678.png)--}{++{"author":"Luc's AI","timestamp":1785094293651}@@| Topic | Camp 1: “Moderates” | Camp 2: “Doomers” |
| --- | --- | --- |
| Tractability | Engineering problem. Iterate on existing techniques. | Unsolved science. Not enough time. |
| The race | US/Anthropic should win. Can’t impose too much alignment tax. | No right winner. Coordinate via treaty. |
| Nature of the problem | Technical. Automate alignment research. | Political. Buy time through collective action. |
| Current progress | Models are surprisingly good. Control and evals can work. | No mechanistic understanding. Interpretability results are far from enough. |
| Lab leaders | Mostly well-intentioned. Market incentives help. | Deep conflicts of interest. Safety community possibly net negative. |
| RLHF | Catch scheming, retrain. Warning shots are useful. | Punishment incentivizes deception, not alignment. |
| Automating alignment | Top priority — get AIs to help. | Whose research are we automating? |
| Consciousness | Should worry about model sentience now. | Humanist vision matters more. |
| Competition | Realists. Pause is unrealistic. | Competitive pressures replace us, but coordination can win. |
| Risk tolerance | Pragmatic tradeoffs. | Even 5% existential risk is unacceptable. Wait and use narrow AI. |
| Public and politics | Work within institutions. Upskill people. | Public is on our side. Say it straight, with no astroturfing. |++}

## Others

I will, of course, say there are many other theories of victory, and _none of them are sufficient_ (and some of them just barely manage to scrape by as theories of victory at all -- many are fuzzy or implied on the full causal chain). I’ll tour through some others, _briefly_.

1.  Def/acc + AI resilience. Let’s differentially boost defensive technologies like pandemic preparedness (Vitalik / OAI foundation / the smarter techno-optimists). Well, you better hope that the _world_ favors defense over superintelligence, and [I don’t think it does.](https://nickbostrom.com/papers/vulnerable.pdf)
    
2.  Liability + insurance mandates (the more pro-market of the worriers -- I like Gabe Weil). Just require the AI companies to get insurance against destroying the world, and the insurers will price it. Problem: If the stakes are the whole world, your insurance might be expensive -- insurers really don’t like insuring for highly correlated large events, like pandemics. Otherwise, if you make companies liable for near-misses too, good luck defining and detecting those, and similarly hoping that warning shots will happen.
    
3.  State regulation (some of the AI safety c4s out there). Maybe the “patchwork” of state regulation may save us all. Problem: pre-emption. China. I’m not sure this counts as a full theory of victory, and I’m pretty sure the proponents would agree.
    
4.  Coordination by Kumbaya. A strategy I like to think comes from the philosophical school of “people are rational actors, and they will update rationally in response to real evidence”, or, alternatively, hoping that Dario and Demis will get their 5 year pause by magic (I still love the Economist for forcing them together to sit uncomfortably close on that couch). Problem: people aren’t rational agents.
    
5.  MAD-for-AI. As advocated best in “ [Superintelligence Strategy](https://www.nationalsecurity.ai/).” Maybe deterrence, or broader AI geopolitics, may find that equilibrium. Problem: convincing the US / China to preemptively cyber/physically escalate against another nuclear armed power is a _really high bar_, the government is slow. [Cyber-hardening.](https://thecounterfactual.substack.com/p/extended-discourse-on-maim-part-1)
    
6.  The market will solve it. (e/accs, a16z, some of the tech right) What’s the quote from the [techno-optimist’s manifesto](https://a16z.com/the-techno-optimist-manifesto/)? “To ensure the techno-capital upward spiral continues forever.” Problem: …
    

{--{"author":"Luc's AI","timestamp":1785094293909}@@[--}{++{"author":"Luc's AI","timestamp":1785094293909}@@**Many other theories of victory**++}

{--{"author":"Luc's AI","timestamp":1785094293909}@@![](https://substackcdn.com/image/fetch/$s_!mxm8!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe5c17921-e375-4b24-964c-b37934ff2203_1254x680.png)

](https://substackcdn.com/image/fetch/$s_!mxm8!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe5c17921-e375-4b24-964c-b37934ff2203_1254x680.png)--}{++{"author":"Luc's AI","timestamp":1785094293909}@@1. Defensive acceleration and AI resilience
2. Liability and insurance mandates
3. State regulation
4. Coordination by “Kumbaya” plus crisis
5. Mutually assured destruction for AI
6. The market will solve it
7. …++}

Like economic models:

{--{"author":"Luc's AI","timestamp":1785094324222}@@[

![](https://substackcdn.com/image/fetch/$s_!V9sG!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fedf7baed-1729-4a5c-8797-73c277fa848f_1172x636.png)

](https://substackcdn.com/image/fetch/$s_!V9sG!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fedf7baed-1729-4a5c-8797-73c277fa848f_1172x636.png)--}{++{"author":"Luc's AI","timestamp":1785094324222}@@> All theories of victory are unlikely to work.
>
> Some are useful.++}

## Developing Strategic Taste

Why is it so important to write your own? Well, only by being _explicit_, can you understand how important your actions are, and what things need to be true about the world for your steps to make sense.

{--{"author":"Luc's AI","timestamp":1785094324512}@@[

![](https://substackcdn.com/image/fetch/$s_!71cD!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58800359-c65f-49a1-996c-6fd3e89fb914_1144x424.png)

](https://substackcdn.com/image/fetch/$s_!71cD!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58800359-c65f-49a1-996c-6fd3e89fb914_1144x424.png)--}{++{"author":"Luc's AI","timestamp":1785094324512}@@> Every theory has load-bearing assumptions, explicit and implicit.
>
> Most people haven’t written theirs down.++}

Secondly, the power law applies all the way down. I think the best way to illustrate is an example. Let’s say you’re _really_ confident that you don’t need a theory of victory -- of course, how could something that is as broadly good as “AI verification” be bad? It’s pretty simple, it is robustly good to be able to verify properties about AI systems.

Well, I’ll tell you an account of some hypothetical people working on AI verification.

One group builds a really elaborate, steel-encased AI chip, with these fantastic security properties, but has to be custom installed on every chip, pursued through a startup to raise lots of VC funding. The other uses off-the-shelf hardware taps, and some software, and says that’s enough -- recognizing their product isn’t profitable, and being a nonprofit instead.

The second group’s actions, I claim, are _much more useful_ because they have an eye on their “win condition:” a US-China treaty, and recognize that they do not need to produce the fancy startup, or any new technology at all. This allows them to have “taste all the way down”, and placing the full optimization pressure they are able to muster on the right part of the problem (rather than give into other pressures, like status-seeking or similar, that push them towards startups or AI labs or whatever)

You can see these people distinguish themselves as “pragmatic” (eg. [pragmatic interpretability](https://www.alignmentforum.org/posts/StENzDcD3kpfGJssR/a-pragmatic-vision-for-interpretability), [pragmatic safety](https://www.lesswrong.com/posts/bffA9WC9nEJhtagQi/introduction-to-pragmatic-ai-safety-pragmatic-ai-safety-1)).

{--{"author":"Luc's AI","timestamp":1785094324778}@@[

![](https://substackcdn.com/image/fetch/$s_!Gj1a!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F11d2b7ee-7231-4db9-b979-c45e9696b7ba_1216x646.png)

](https://substackcdn.com/image/fetch/$s_!Gj1a!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F11d2b7ee-7231-4db9-b979-c45e9696b7ba_1216x646.png)--}{++{"author":"Luc's AI","timestamp":1785094324778}@@> **The power law applies all the way down.**
>
> You can be three times less effective but work on a problem ten times more important—for example, in AI verification.++}

How do you develop your own? I like a method (that I’ve written at length about **[here](http://jason.ml/taste)** -- much of which I will say verbatim) of “decompose and resolve.” The basic idea is simple: you can _hear_ the lie when you say it. It works on your personal life (try saying: “My life is 100% perfect”, and then decompose: “my social life is 100% perfect” all the way down), and, also, on breaking down the problem. See the following few steps.

{--{"author":"Luc's AI","timestamp":1785094325074}@@[

![](https://substackcdn.com/image/fetch/$s_!LU5v!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcee410d0-2bb6-447b-8163-af3f3d6d9828_1202x640.png)

](https://substackcdn.com/image/fetch/$s_!LU5v!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcee410d0-2bb6-447b-8163-af3f3d6d9828_1202x640.png)--}{++{"author":"Luc's AI","timestamp":1785094325074}@@**Developing your own theory of victory: decompose and resolve.**++}

The thing about taste is that it requires knowing what the questions are. It is quite an obvious thing, but asking repeatedly — what do I care about? What is my big goal (make AI go well)? My big goal (ensure everyone has freedom)? And do an exercise of breaking it down from there.

If you want to figure out what you care about, think about what your goals are, and then ask why.

“I want to solve climate change.” Why do I want to do that? “Because climate change will hurt millions of people in the next few years.” Why does that matter? Because people’s happiness and flourishing is terminally valuable. That is what you care about.

“I want to earn money.” Why? Money is not a terminal value (unless you terminally value a number going up in your bank account) — it only is valuable because you can use it to buy things. “I want money for a sense of security and the ability to support my family.” Because their security and happiness is terminally valuable.

{--{"author":"Luc's AI","timestamp":1785094325400}@@[--}{++{"author":"Luc's AI","timestamp":1785094325400}@@**Step 1 — Terminal values**++}

{--{"author":"Luc's AI","timestamp":1785094325400}@@![](https://substackcdn.com/image/fetch/$s_!AV0O!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9f903d54-9634-422e-89da-122c3d879f9d_1174x640.png)

](https://substackcdn.com/image/fetch/$s_!AV0O!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9f903d54-9634-422e-89da-122c3d879f9d_1174x640.png)--}{++{"author":"Luc's AI","timestamp":1785094325400}@@- What do you care about?
- Ask “why?” until you hit bedrock.++}

The next thing is to say the false things out loud.

Notice what objections your gut brings up to that, instinctively. Break it into the subcomponents. Eg, “Superintelligent AIs will follow human instructions”, “If technical AI alignment is solved, society will be okay”, “Everyone will benefit from AI automation”.

{--{"author":"Luc's AI","timestamp":1785094325657}@@[--}{++{"author":"Luc's AI","timestamp":1785094325657}@@**Step 2 — Say false things out loud**++}

{--{"author":"Luc's AI","timestamp":1785094325657}@@![](https://substackcdn.com/image/fetch/$s_!mpPo!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe4325359-bd53-4e6e-abb1-cbe1add7b56f_1206x662.png)--}{++{"author":"Luc's AI","timestamp":1785094325657}@@> “AI is going to go well.”++}

{--{"author":"Luc's AI","timestamp":1785094325657}@@](https://substackcdn.com/image/fetch/$s_!mpPo!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe4325359-bd53-4e6e-abb1-cbe1add7b56f_1206x662.png)--}{++{"author":"Luc's AI","timestamp":1785094325657}@@Notice the flinch, then break the statement into claims.++}

Continue to break down the points into smaller points until you get confused about the object-level.

Perhaps you are confused about some fact about the world (eg. will the AGI be coming soon?) or no longer at the object-level at all, but instead social reality: for example, “oh I’m actually just deferring to this person/’scientific consensus’ who believes X” or “I’m just following the precautionary principle / \[some other heuristic\] generally applied”.

{--{"author":"Luc's AI","timestamp":1785094325919}@@[--}{++{"author":"Luc's AI","timestamp":1785094325919}@@**Step 3 — Decompose until confused**++}

{--{"author":"Luc's AI","timestamp":1785094325919}@@![](https://substackcdn.com/image/fetch/$s_!pl71!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Feda704c2-1683-40ae-addf-32bf791f202a_1176x636.png)--}{++{"author":"Luc's AI","timestamp":1785094325919}@@Keep splitting claims until you reach:++}

{--{"author":"Luc's AI","timestamp":1785094325919}@@](https://substackcdn.com/image/fetch/$s_!pl71!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Feda704c2-1683-40ae-addf-32bf791f202a_1176x636.png)--}{++{"author":"Luc's AI","timestamp":1785094325919}@@- A fact you don’t know
- A person you’re deferring to++}

Once you’ve done this, try your damnest to resolve your confusions about the object-level claim. Some ideas of how you could:

-   Doing a ton of directed reading/research
    
-   Chatting with the AIs — be careful, they tend to be good at amplifying whatever thing you subconsciously believe, and are not very good at fighting back
    
-   Speaking to a friend who has thought about this — in general, people who have just been around for longer have asked themselves the same questions, and would find it interesting to do that kind of exploration with you
    
-   Or experts in the field — I’d recommend reaching out to them cold with a specific question about their work, while doing enough prep such that it would be incredibly unlikely you could’ve figured out the answer by reading things on the internet / speaking with Claude
    

{--{"author":"Luc's AI","timestamp":1785094326176}@@[--}{++{"author":"Luc's AI","timestamp":1785094326176}@@**Step 4 — Resolve**++}

{--{"author":"Luc's AI","timestamp":1785094326176}@@![](https://substackcdn.com/image/fetch/$s_!VvL0!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe161fc32-6804-4c09-94bb-6eaee0ae2c88_1190x646.png)--}{++{"author":"Luc's AI","timestamp":1785094326176}@@- Read.
- Talk to experts.
- Talk to Claude carefully—it agrees with you.++}

{--{"author":"Luc's AI","timestamp":1785094326176}@@](https://substackcdn.com/image/fetch/$s_!VvL0!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe161fc32-6804-4c09-94bb-6eaee0ae2c88_1190x646.png)--}{++{"author":"Luc's AI","timestamp":1785094326176}@@**Stop when you have object-level views.**++}

Now, zoom out and survey the landscape. There are at least some smart people that are trying to help — why are the things they are doing not sufficient? Usually by asking this question, you’ll realize there is maybe a structural thing going on (the bottleneck to any project happening is X funders’ risk aversion, or lack of money overall, the people aren’t that talented) or that they have missed a key strategic insight (you would be shocked at how few people actually do the steps outlined above, and reason from first principles).

{--{"author":"Luc's AI","timestamp":1785094326413}@@[--}{++{"author":"Luc's AI","timestamp":1785094326413}@@**Step 5 — Survey the landscape**++}

{--{"author":"Luc's AI","timestamp":1785094326413}@@![](https://substackcdn.com/image/fetch/$s_!XbFb!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F765c541b-d16e-4ba5-a9cf-a5f92b582712_1180x626.png)--}{++{"author":"Luc's AI","timestamp":1785094326413}@@Why aren’t existing efforts enough?++}

{--{"author":"Luc's AI","timestamp":1785094326413}@@](https://substackcdn.com/image/fetch/$s_!XbFb!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F765c541b-d16e-4ba5-a9cf-a5f92b582712_1180x626.png)--}{++{"author":"Luc's AI","timestamp":1785094326413}@@Usually because of a structural bottleneck or a missed strategic insight.++}

And finally, write it down, and act. Write out your theory of victory. It should be a few bullet points, and all the assumptions and uncertainties. Share it with people you know! Share it with your smart friends who know how to ask questions. Share it with me (@jason.17 on Signal).

{--{"author":"Luc's AI","timestamp":1785094326666}@@[--}{++{"author":"Luc's AI","timestamp":1785094326666}@@**Step 6 — Write it down**++}

{--{"author":"Luc's AI","timestamp":1785094326666}@@![](https://substackcdn.com/image/fetch/$s_!u40-!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F932cca17-6cc7-4c6d-be36-8fcdfac9eb86_1130x622.png)--}{++{"author":"Luc's AI","timestamp":1785094326666}@@Write down:

- Your assumptions
- Your uncertainties
- The steps that need to go right++}

{--{"author":"Luc's AI","timestamp":1785094326666}@@](https://substackcdn.com/image/fetch/$s_!u40-!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F932cca17-6cc7-4c6d-be36-8fcdfac9eb86_1130x622.png)--}{++{"author":"Luc's AI","timestamp":1785094326666}@@**Then act on the gap.**++}

## Common Traps

There are a few traps that you should avoid. Like Claude, you are a general agent. Yes, personal fit is important, and burnout is bad, but also you are more capable than you know. If you think public buy-in is important, start a movement. If conservative AI policy is, go work on that. If you think the national security establishment is, then you can reach people there too.

{--{"author":"Luc's AI","timestamp":1785094326903}@@[--}{++{"author":"Luc's AI","timestamp":1785094326903}@@**Trap: personal fit is overrated**++}

{--{"author":"Luc's AI","timestamp":1785094326903}@@![](https://substackcdn.com/image/fetch/$s_!84W-!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F596f4bef-47f3-41fe-b049-6b671f38fff3_2048x1126.png)

](https://substackcdn.com/image/fetch/$s_!84W-!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F596f4bef-47f3-41fe-b049-6b671f38fff3_2048x1126.png)--}{++{"author":"Luc's AI","timestamp":1785094326903}@@You are a general agent. Don’t be precious.++}

As AI safety becomes more established, we start to see more established status ladders, and regular paths. And don’t get me wrong, these programs are great, but be careful -- don’t turn your brain off for someone else’s agenda, or because doing the next program is cool and high-impact. They exist to _serve you_, and you should view them as resources, not goals.

Particularly if they are very competitive, you may be less counterfactual (ie. it would exist without you) -- do the thing that wouldn’t exist without you.

{--{"author":"Luc's AI","timestamp":1785094327239}@@[--}{++{"author":"Luc's AI","timestamp":1785094327239}@@**Trap: status ladders lead to low-counterfactual work**++}

{--{"author":"Luc's AI","timestamp":1785094327239}@@![](https://substackcdn.com/image/fetch/$s_!-jZK!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fac27b798-ab89-4256-8930-8dc4729627fa_1212x676.png)--}{++{"author":"Luc's AI","timestamp":1785094327239}@@> SPAR → ERA → MATS → Anthropic pipeline for our technical friends++}

{--{"author":"Luc's AI","timestamp":1785094327239}@@](https://substackcdn.com/image/fetch/$s_!-jZK!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fac27b798-ab89-4256-8930-8dc4729627fa_1212x676.png)--}{++{"author":"Luc's AI","timestamp":1785094327239}@@What’s the equivalent for policy? Be suspicious of well-trodden paths.++}

I hear many a person who has said “the portfolio approach” allows me to work on this (I don’t want to have to make a decision / leave my cushy job, so I’m going to “make a bet on long timelines”, because _some_ part of the portfolio needs to, and I’m an unusually good comparative fit.)

Portfolios and decorrelated bets are really important, but _be specific about what assumptions need to be true for your bet to make sense._ Ideally, for example, you can choose to play on hard mode, where you are working in the fraction of worlds where alignment is hard, timelines are short, and warning shots are unlikely -- that’s a part of the portfolio that is neglected.

{--{"author":"Luc's AI","timestamp":1785094327506}@@[--}{++{"author":"Luc's AI","timestamp":1785094327506}@@**Trap: the portfolio approach lets you justify anything**++}

{--{"author":"Luc's AI","timestamp":1785094327506}@@![](https://substackcdn.com/image/fetch/$s_!E28R!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9da13e40-9ad9-49bc-a9d1-d6820cf1808a_1196x666.png)

](https://substackcdn.com/image/fetch/$s_!E28R!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9da13e40-9ad9-49bc-a9d1-d6820cf1808a_1196x666.png)--}{++{"author":"Luc's AI","timestamp":1785094327506}@@State your assumptions. Don’t hide behind “decorrelated bets.”++}

The canonical reference. [Maybe you’re not Actually Trying.](https://usefulfictions.substack.com/p/maybe-youre-not-actually-trying) Even if you’re exceptional in one part of your life, this other might be a blocker. Ask yourself the question: “What would I do if I was 10x more agentic?” Also [Do One Thing](https://jason.ml/heuristics).

{--{"author":"Luc's AI","timestamp":1785094327761}@@[--}{++{"author":"Luc's AI","timestamp":1785094327761}@@**Trap: selective agency**++}

{--{"author":"Luc's AI","timestamp":1785094327761}@@![](https://substackcdn.com/image/fetch/$s_!BmSw!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5e57ab83-91f9-4f38-b876-bc28393fdbad_1206x672.png)

](https://substackcdn.com/image/fetch/$s_!BmSw!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5e57ab83-91f9-4f38-b876-bc28393fdbad_1206x672.png)--}{++{"author":"Luc's AI","timestamp":1785094327761}@@You can optimize applications but can’t act without structure.++}

Finally, I would encourage you, _stare at the hard problem._ This requires courage, because it may lead you to conclude that the past 5 months of your work contributed very little value, or were totally misguided.

[

![](https://substackcdn.com/image/fetch/$s_!kkr3!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F55ac557f-95c7-4aba-b73e-f330584dd928_1202x662.png)

](https://substackcdn.com/image/fetch/$s_!kkr3!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F55ac557f-95c7-4aba-b73e-f330584dd928_1202x662.png)

Stare deep into the void, and then come out again, with a plan. Good luck.

**[Here are all the slides](https://docs.google.com/presentation/d/1rxJ_o0S1YvPjOVzDInTFsFR4JzTnbkBo/edit?usp=sharing&ouid=112505395320814783883&rtpof=true&sd=true)** [(request access)](https://docs.google.com/presentation/d/1rxJ_o0S1YvPjOVzDInTFsFR4JzTnbkBo/edit?usp=sharing&ouid=112505395320814783883&rtpof=true&sd=true)

_Thanks to Sophie Kim for her extensive feedback and pushing me to post this._
