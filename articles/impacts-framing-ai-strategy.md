---
title: "Framing AI strategy"
author:
  - "Zach Stein-Perlman"
source_url: "https://aiimpacts.org/framing-ai-strategy/"
published: 2023-02-06
created: 2026-11-24
accessed: 2026-11-24
llm-review:
  date: 2026-11-24
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-24
    kind: "live"
description: "Ten angles on AI strategy"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Zach Stein-Perlman, 6 February 2023_

_Strategy_ is the activity or project of doing research to inform interventions to achieve a particular goal.[^note-strategy-usage] _AI strategy_ is strategy from the perspective that AI is important, focused on interventions to make AI go better. An analytic _frame_ is a conceptual orientation that makes salient some aspects of an issue, including cues for what needs to be understood, how to approach the issue, what your goals and responsibilities are, what roles to see yourself as having, what to pay attention to, and what to ignore.

This post discusses ten strategy frames, focusing on AI strategy. Some frames are comprehensive approaches to strategy; some are components of strategy or prompts for thinking about an aspect of strategy. This post focuses on meta-level exploration of frames, but the second and last sections have some object-level thoughts within a frame.

Sections are overlapping but independent; focus on sections that aren’t already in your toolbox of approaches to strategy.

_Epistemic status: exploratory, brainstormy._

## **Make a plan** ^make-a-plan

_See Jade Leung’s_ [_Priorities in AGI governance research_](https://www.listennotes.com/podcasts/ea-radio/priorities-in-agi-governance-WM_DUyzNPqR/) _(2022) and_ [_How can we see the impact of AI strategy research?_](https://web.archive.org/web/20220702141246/https://www.effectivealtruism.org/articles/jade-leung-how-can-we-see-the-impact-of-ai-strategy-research) _(2019)._

One output of strategy is a plan describing relevant (kinds of) actors’ behavior. More generally, we can aim for a playbook– something like a function from (sets of observations about) world-states to plans. A plan is good insofar as it improves important decisions in the counterfactual where you try to implement it, in expectation.

To make a plan or playbook, identify (kinds of) actors that might be affectable, then figure out

1.  what they could do,
2.  what it would be good for them to do,
3.  what their incentives are (if relevant), and then
4.  how to cause them to act better.

It is also possible to focus on decisions rather than actors: determine what decisions you want to affect (presumably because they’re important and affecting them seems tractable) and how you can affect them.

For AI, relevant actors include AI labs, states (particularly America), non-researching non-governmental organizations (particularly standard-setters), compute providers, and the AI risk and EA communities.[^note-lifland]

Insofar as an agent (not necessarily an actor that can take directly important actions) has distinctive abilities and is likely to try to execute good ideas you have, it can be helpful to focus on _what the agent can do_ or _how to leverage the agent’s distinctive abilities_ rather than backchain from _what would be good_.[^note-superpower]

## **Affordances** ^affordances

As in the previous section, a natural way to improve the future is to identify relevant actors, determine what it would be good for them to do, and cause them to do those things. “Affordances” in strategy are “possible partial future actions that could be communicated to relevant actors, such that they would take similar actions.”[^cite-gray] The motivation for searching for and improving affordances is that there probably exist actions that would be great and relevant actors would be happy to take, but that they wouldn’t devise or recognize by default. Finding great affordances is aided by a deep understanding of how an actor thinks and its incentives, as well as a deep external understanding of the actor, to focus on its blind spots and identify feasible actions.[^note-grace]  Separately, the actor’s participation would sometimes be vital.

Affordances are relevant not just to cohesive actors but also to non-structured groups. For example, for AI strategy, discovering affordances for ML researchers (as individuals or for collective action) could be valuable. Perhaps there also exist great possible affordances that don’t depend much on the actor– generally helpful actions that people just aren’t aware of.

For AI, two relevant kinds of actors are states (particularly America) and AI labs. One way to discover affordances is to brainstorm the kinds of actions particular actors can take, then find creative new plans within that list. Going less meta, I made lists of the kinds of actions states and labs can take that may be strategically significant, since such lists seem worthwhile and I haven’t seen anything like them.

Kinds of things states can do that may be strategically relevant (or consequences or characteristics of possible actions):

-   Regulate (and enforce regulation in their jurisdiction and investigate possible violations)
-   Expropriate property and nationalize companies (in their territory)
-   Perform or fund research (notably including through Manhattan/Apollo-style projects)
-   Acquire capabilities (notably including military and cyber capabilities)
-   Support particular people, companies, or states
-   Disrupt or attack particular people, companies, or states (outside their territory)
-   Affect what other actors believe on the object level
    -   Share information
    -   Make information salient in a way that predictably affects beliefs
    -   Express attitudes that others will follow
-   Negotiate with other actors, or affect other actors’ incentives or meta-level beliefs
-   Make agreements with other actors (notably including contracts and treaties)
-   Establish standards, norms, or principles
-   Make unilateral declarations (as an international legal commitment) \[less important\]

Kinds of things AI labs[^note-lab-variants] can do—or choose not to do—that may be strategically relevant (or consequences or characteristics of possible actions):

-   Deploy an AI system
-   Pursue capabilities
    -   Pursue risky (and more or less alignable systems) systems
    -   Pursue systems that enable risky (and more or less alignable) systems
    -   Pursue weak AI that’s mostly orthogonal to progress in risky stuff for a specific (strategically significant) task or goal
        -   This could enable or abate catastrophic risks besides unaligned AI
-   Do alignment (and related) research (or: decrease the [alignment tax](https://forum.effectivealtruism.org/posts/63stBTw3WAW6k45dY/paul-christiano-current-work-in-ai-alignment) by doing technical research)
    -   Including interpretability and work on solving or avoiding alignment-adjacent problems like [decision theory and strategic interaction](https://www.lesswrong.com/posts/brXr7PJ2W4Na2EW2q/the-commitment-races-problem) and maybe [delegation involving multiple humans or multiple AI systems](http://acritch.com/arches/)
-   Advance global capabilities
    -   Publish capabilities research
    -   Cause investment or spending in big AI projects to increase
-   Advance alignment (or: decrease the alignment tax) in ways other than doing technical research
    -   Support and coordinate with external alignment researchers
-   Attempt to align a particular system (or: try to pay the alignment tax)
-   Interact with other labs[^cite-karnofsky-deals]
    -   Coordinate with other labs (notably including coordinating to avoid risky systems)
        -   Make themselves transparent to each other
        -   Make themselves transparent to an external auditor
        -   Merge
        -   Effectively commit to share upsides
        -   Effectively commit to [stop and assist](https://openai.com/charter/)
    -   Affect what other labs believe on the object level (about AI capabilities or risk in general, or regarding particular memes)
        -   Practice [selective information sharing](https://www.lesswrong.com/posts/vZzg8NS7wBtqcwhoJ/nearcast-based-deployment-problem-analysis#SelectiveInformationSharing)
        -   Demonstrate AI risk (or provide evidence about it)
    -   Negotiate with other labs, or affect other labs’ incentives or meta-level beliefs
-   Affect public opinion, media, and politics
    -   Publish research
    -   Make demos or public statements
    -   Release or deploy AI systems
-   Improve their culture or [operational adequacy](https://www.lesswrong.com/s/v55BhXbpJuaExkpcD/p/keiYkaeoLHoKK4LYA)
    -   Improve operational security
    -   Affect attitudes of effective leadership
    -   Affect attitudes of researchers
    -   Make a plan for alignment (e.g., [OpenAI’s](https://openai.com/blog/our-approach-to-alignment-research/)); share it; update and improve it; and coordinate with capabilities researchers, alignment researchers, or other labs if relevant
    -   Make a plan for what to do with powerful AI (e.g., [CEV](https://arbital.com/p/cev/) or some specification of [long reflection](https://forum.effectivealtruism.org/topics/long-reflection)), share it, update and improve it, and coordinate with other actors if relevant
    -   Improve their ability to make themselves (selectively) transparent
-   Try to better understand the future, the strategic landscape, risks, and possible actions
-   Acquire resources
    -   E.g., money, hardware, talent, influence over states, status/prestige/trust
    -   Capture scarce resources
        -   E.g., language data from language model users
-   Affect other actors’ resources
    -   Affect the flow of talent between labs or between projects
-   Plan, execute, or participate in [pivotal acts](https://arbital.com/p/pivotal/) or [processes](https://www.lesswrong.com/posts/etNJcXCsKC6izQQZj/pivotal-outcomes-and-pivotal-processes)

(These lists also exist on the [AI Impacts wiki](https://wiki.aiimpacts.org/), where they may be improved in the future: [Affordances for states](https://wiki.aiimpacts.org/doku.php?id=responses_to_ai:affordances:state_affordances) and [Affordances for AI labs](https://wiki.aiimpacts.org/doku.php?id=responses_to_ai:affordances:lab_affordances). These lists are written from an alignment-focused and misuse-aware perspective, but prosaic risks may be important too.)

Maybe making or reading lists like these can help you notice good tactics. But innovative affordances are necessarily not things that are already part of an actor’s behavior.

Maybe making lists of _relevant things similar actors have done in the past_ would illustrate possible actions, build intuition, or aid communication.

This frame seems like a potentially useful complement to the standard approach [_backchain_](https://www.lesswrong.com/posts/DwoPGM8ytBCXrZpM7/backchaining-in-strategy) _from goals to actions of relevant actors_. And it seems good to understand _actions that should be items on lists like these_—both like understanding these list-items well and expanding or reframing these lists—so you can notice opportunities.

## **Intermediate goals** ^intermediate-goals

_No great sources are public, but illustrating this frame see “Catalysts for success” and “Scenario variables” in Marius Hobhannon et al.’s_ [_What success looks like_](https://forum.effectivealtruism.org/posts/AuRBKFnjABa6c6GzC/what-success-looks-like#Catalysts_for_success) _(2022). On goals for AI labs, see Holden Karnofsky’s_ [_Nearcast-based “deployment problem” analysis_](https://www.lesswrong.com/posts/vZzg8NS7wBtqcwhoJ/nearcast-based-deployment-problem-analysis) _(2022)._

An intermediate/instrumental goal is a goal that is valuable because it promotes one or more final/terminal goals. (“Goal” sounds discrete and binary, like “there exists a treaty to prevent risky AI development,” but often should be continuous, like “gain resources and influence.”) Intermediate goals are useful because we often need more specific and actionable goals than “make the future go better” or “make AI go better.”

_Knowing what specifically would be good for people to do_ is a bottleneck on _people doing useful things_. If the AI strategy community had better strategic clarity, in terms of knowledge about the future and particularly intermediate goals, it could better utilize people’s labor, influence, and resources. Perhaps an overlapping strategy framing is _finding or unlocking effective opportunities to spend money_. See Luke Muehlhauser’s [A personal take on longtermist AI governance](https://forum.effectivealtruism.org/posts/M2SBwctwC6vBqAmZW/a-personal-take-on-longtermist-ai-governance) (2021).[^cite-muehlhauser]

It is also sometimes useful to consider _goals about particular actors_.

## **Threat modeling** ^threat-modeling

_Illustrating threat modeling for the technical component of AI misalignment, see the DeepMind safety team’s_ [_Threat Model Literature Review_](https://www.lesswrong.com/posts/wnnkD6P2k2TfHnNmt/threat-model-literature-review) _and_ [_Clarifying AI X-risk_](https://www.lesswrong.com/posts/GctJD5oCDRxCspEaZ/clarifying-ai-x-risk) _(2022), Sam Clarke and Sammy Martin’s_ [_Distinguishing AI takeover scenarios_](https://www.lesswrong.com/posts/qYzqDtoQaZ3eDDyxa/distinguishing-ai-takeover-scenarios) _(2021), and GovAI’s_ [_Survey on AI existential risk scenarios_](https://forum.effectivealtruism.org/posts/2tumunFmjBuXdfF2F/survey-on-ai-existential-risk-scenarios-1) _(2021)._

The goal of [threat modeling](https://www.lesswrong.com/tag/threat-models) is deeply understanding one or more risks for the purpose of informing interventions. A great causal model of a threat (or _class of possible failures_) can let you identify points of intervention and determine what countering the threat would require.

A related project involves assessing all threats (in a certain class) rather than a particular one, to help account for and prioritize between different threats.

Technical AI safety research informs AI strategy through threat modeling. A causal model of (part of) AI risk can generate a model of AI risk abstracted for strategy, with relevant features made salient and irrelevant details black-boxed. This abstracted model gives us information including necessary and sufficient conditions or intermediate goals for averting the relevant threats. These in turn can inform affordances, tactics, policies, plans, influence-seeking, and more.

## **Theories of victory** ^theories-of-victory

_I am not aware of great sources, but illustrating this frame see Marius Hobhannon et al.’s_ [_What success looks like_](https://forum.effectivealtruism.org/posts/AuRBKFnjABa6c6GzC/what-success-looks-like) _(2022)._

Considering theories of victory is another natural frame for strategy: consider scenarios where the future goes well, then find interventions to nudge our world toward those worlds. (Insofar as it’s not clear what _the future going well_ means, this approach also involves clarifying that.) To find interventions to make our world like a victorious scenario, I sometimes try to find necessary and sufficient conditions for the victory-making aspect of that scenario, then consider how to cause those conditions to hold.[^note-victory-conditions]

Great threat-model analysis can be an excellent input to theory-of-victory analysis, to clarify the threats and what their solutions must look like. And it could be useful to consider scenarios in which the future goes well and scenarios where it doesn’t, then examine the differences between those worlds.

## **Tactics and policy development** ^tactics-and-policy-development

_Collecting progress on possible government policies, see GovAI’s_ [_AI Policy Levers_](https://www.governance.ai/research-paper/ai-policy-levers-a-review-of-the-u-s-governments-tools-to-shape-ai-research-development-and-deployment) _(2021) and GCRI’s_ [_Policy ideas database_](https://www.gcrpolicy.com/ideas).

Given a model of the world and high-level goals, we must figure out how to achieve those goals in the messy real world. For a goal, what would cause success, which of those possibilities are tractable, and how could they become more likely to occur? For a goal, what are necessary and sufficient conditions for achievement and how could those occur in the real world?

## **Memes & frames** ^memes-frames

_I am not aware of great sources on memes & frames in strategy, but see Jade Leung’s_ [_How can we see the impact of AI strategy research?_](https://web.archive.org/web/20220702141246/https://www.effectivealtruism.org/articles/jade-leung-how-can-we-see-the-impact-of-ai-strategy-research) _(2019). See also the academic literature on framing, e.g. Robert Entman’s_ [_Framing_](https://is.muni.cz/el/1423/podzim2018/POL256/um/Entman_1993_FramingTowardclarificationOfAFracturedParadigm.pdf) _(1993)._

(“Frames” in this context refers to the lenses through which people interpret the world, not the analytic, research-y frames discussed in this post.)

If certain actors held certain attitudes, they would make better decisions. One way to affect attitudes is to spread [memes](https://www.lesswrong.com/tag/memetics). A meme could be _explicit agreement with a specific proposition_; _the attitude that certain organizations, projects, or goals are (seen as) shameful_; _the attitude that certain ideas are sensible and respectable or not_; or merely _a tendency to pay more attention to something_. The goal of meme research is finding good memes—memes that would improve decisions if widely accepted (or accepted by a particular set of actors[^note-memes-audience]) and are tractable to spread—and figuring out how to spread them. Meme research is complemented by work actually causing those memes to spread.

For example, potential good memes in AI safety include things like _AI is powerful but not robust, and in particular \[specification gaming or Goodhart or distributional shift or adversarial attack\] is a big deal_. Perhaps _misalignment as catastrophic accidents_ is easier to understand than _misalignment as powerseeking agents_, or vice versa. And perhaps _misuse risk_ is easy to understand and unlikely to be catastrophically misunderstood, but less valuable-if-spread.

A frame tells people what to notice and how to make sense of an aspect of the world. Frames can be internalized by a person or contained in a text. Frames for AI might include frames related to consciousness, Silicon Valley, AI racism, national security, or specific kinds of applications such as chatbots or weapons.

Higher-level research could also be valuable. This would involve topics like _how to communicate ideas about AI safety_ or even _how to communicate ideas_ and _how groups form beliefs_.

This approach to strategy could also involve researching how to stifle harmful memes, like perhaps “powerful actors are incentivized to race for highly capable AI” or “we need a Manhattan Project for AI.”

## **Exploration, world-modeling, and forecasting** ^exploration-world-modeling-and-forecasti

Sometimes strategy greatly depends on particular questions about the world and the future.

More generally, you can reasonably expect that increasing clarity about important-seeming aspects of the world and the future will inform strategy and interventions, even without thinking about specific goals, actors, or interventions. For AI strategy, exploration includes central questions about the future of AI and relevant actors, understanding the effects of possible actions, and perhaps also topics like decision theory, acausal trade, digital minds, and anthropics.

_Constructing a map_ is part of many different approaches to strategy. This roughly involves understanding the landscape and discovering analytically useful concepts, like reframing _victory means causing AI systems to be aligned_ to _it’s necessary and sufficient to cause the alignment tax to be paid, so it’s necessary and sufficient to reduce the alignment tax and increase the amount-of-tax-that-would-be-paid such that the latter is greater_.

One exploratory, world-model-y goal is a high-level understanding of the strategic landscape. One possible approach to this goal is creating a map of relevant possible events, phenomena, actions, propositions, uncertainties, variables, and/or analytic nodes.

## **Nearcasting** ^nearcasting

_Discussing nearcasting, see Holden Karnofsky’s_ [_AI strategy nearcasting_](https://www.lesswrong.com/posts/Qo2EkG3dEMv8GnX8d/ai-strategy-nearcasting) _(2022). Illustrating nearcasting, see Karnofsky’s_ [_Nearcast-based “deployment problem” analysis_](https://www.lesswrong.com/posts/vZzg8NS7wBtqcwhoJ/nearcast-based-deployment-problem-analysis) _(2022)._

Holden Karnofsky defines “AI strategy nearcasting” as

> trying to answer key strategic questions about transformative AI, under the assumption that key events (e.g., the development of transformative AI) will happen in a world that is otherwise relatively similar to today’s. One (but not the only) version of this assumption would be “Transformative AI will be developed soon, using methods like what AI labs focus on today.”

When I think about AI strategy nearcasting, I ask:

-   What would a near future where powerful AI could be developed look like?
-   In this possible world, what goals should we have?
-   In this possible world, what important actions could relevant actors take?
    -   And what facts about the world make those actions possible? (For example, some actions would require that a lab has certain AI capabilities, or most people believe a certain thing about AI capabilities, or all major labs believe in AI risk.)
-   In this possible world, what interventions are available?
-   Relative to this possible world, how should we expect the real world to be different?[^cite-karnofsky-nearcasting]
    -   And how do those differences affect the goals we should have, and the interventions that are available to us?

Nearcasting seems to be a useful tool for

-   predicting relevant events concretely and
-   forcing you to notice how you think the world will be different in the future and how that matters.

## **Leverage** ^leverage

_I’m not aware of other public writeups on leverage. See also Daniel Kokotajlo’s_ [_What considerations influence whether I have more influence over short or long timelines?_](https://www.lesswrong.com/posts/pTK2cDnXBB5tpoP74/what-considerations-influence-whether-i-have-more-influence) _(2020). Related concept:_ [_crunch time_](https://www.lesswrong.com/posts/E7rhL9aij7yCCz9AR/what-s-going-on-with-crunch-time).

When doing strategy and planning interventions, what should you focus on?

A major subquestion is: how should you prioritize focus between possible worlds?[^note-possible-world] Ideally you would prioritize working on _the worlds that working on has highest expected value_, or something like _the worlds that have the greatest product of probability and how much better they would go if you worked on them_. But how can you guess which worlds are high-leverage for you to work on? There are various reasons to prioritize certain possible worlds, both for reasoning about strategy and for evaluating possible interventions. For example, it seems higher-leverage to work on making AI go well conditional on human-level AI appearing in 2050 than in 3000: the former is more foreseeable, more affectable, and more neglected.

We currently lack a good account of leverage, so (going less meta) I’ll begin one for AI strategy here. Given a baseline of weighting possible worlds by their probability, all else equal, you should generally:

-   Upweight worlds that you have more control over and that you can better plan for
    
    -   Upweight worlds with short-ish [timelines](https://www.lesswrong.com/tag/ai-timelines) (since others will exert more influence over AI in long-timelines worlds, and since we have more clarity about the nearer future, and since we can revise strategies in long-timelines worlds)
    -   Take into account future strategy research
        -   For example, if you focus on the world in 2030 (or assume that human-level AI is developed in 2030) you can be deferring, not neglecting, some work on 2040
        -   For example, if you focus on worlds in which important events happen without much advance warning or clearsightedness, you can be deferring, not neglecting, some work on worlds in which important events happen foreseeably
    -   Focus on what you can better plan for and influence; for AI, perhaps this means:
        -   Short timelines
        -   The deep learning paradigm continues
        -   Powerful AI is resource-intensive
        -   Maybe some propositions about risk awareness, warning shots, and world-craziness
    -   Upweight worlds where the probability of victory is relatively close to 50%[^note-logistic]
    
    -   Upweight more neglected worlds (think on the margin)
-   Upweight short-timelines worlds insofar as there is more non-AI existential risk in long-timelines worlds
-   Upweight analysis that better generalizes to or improves other worlds
-   Notice the possibility that you live in a simulation (if that is decision-relevant; unfortunately, the practical implications of living in a simulation are currently unclear)
-   Upweight worlds that you have better personal fit for analyzing
    -   Upweight worlds where you have more influence, if relevant
-   Consider side effects of doing strategy, including what you gain knowledge about, testing fit, and gaining [credible signals of fit](https://forum.effectivealtruism.org/posts/FwzHrWMZzCWNrEedQ/goals-we-might-have-when-taking-actions-to-improve-the-ea#Gaining_credible_signals_of_fit)

In practice, I tentatively think the biggest (analytically useful) considerations for weighting worlds beyond probability are generally:

1.  Short timelines
    1.  More foreseeable[^note-sidenote]
    2.  More affectable
    3.  More neglected (by the AI strategy community)
        1.  Future people can work on the further future
            1.  The AI strategy field is likely to be bigger in the future
    4.  Less planning or influence exerted from outside the AI strategy community
2.  [Fast takeoff](https://www.lesswrong.com/tag/ai-takeoff)[^cite-kokotajlo]
    1.  Shorter, less foreseeable a certain time in advance, and less salient to the world in advance
        1.  More neglected by the AI strategy community; the community would have a longer clear-sighted period to work on slow takeoff
        2.  Less planning or influence exerted from outside the AI strategy community

(But there are presumably diminishing returns to focusing on particular worlds, at least at the community level, so the community should diversify the worlds it analyzes.) And I’m most confused about

1.  Upweighting worlds where probability of victory is closer to 50% (I’m confused about what the probability of victory is in various possible worlds),
2.  How leverage relates to variables like _total influence exerted to affect AI_ (the rest of the world exerting influence means that you have less relative influence insofar as you’re [pulling the rope](https://www.overcomingbias.com/2007/05/policy_tugowar.html) along similar axes, but some interventions are amplified by something like _greater attention on AI_) (and related variables like _attention on AI_ and _general craziness due to AI_), and
3.  The probability and implications of living in a simulation.

A background assumption or approximation in this section is that you allocate research toward a world and the research is effective just if that world obtains. This assumption is somewhat crude: the impact of most research isn’t so binary, being fully effective in some possible futures and totally ineffective in the rest.[^note-serial-research] And thinking in terms of _influence over a world_ is crude: influence depends on the person and on the intervention. Nevertheless, reasoning about leverage in terms of _worlds to allocate research toward_ might sometimes be useful for prioritization. And we might discover a better account of leverage.

Leverage considerations should include not just _prioritizing between possible worlds_ but also _prioritizing within a world_. For example, it seems high-leverage to focus on important actors’ blind spots and on certain important decisions or “crunchy” periods. And for AI strategy, it might be high-leverage to focus on the first few deployments of powerful AI systems.

---

Strategy work is complemented by

1.  actually executing interventions, especially causing actors to make better decisions,
2.  gaining resources to better execute interventions and improve strategy, and
3.  field-building to better execute interventions and improve strategy.

An individual’s strategy work is complemented by informing the relevant community of their findings (e.g., for AI strategy, the AI strategy community).

In this post, I don’t try to make an ontology of AI strategy frames, or do comparative analysis of frames, or argue about the AI strategy community’s prioritization between frames.[^note-prioritization] But these all seem like reasonable things for someone to do.

Related sources are linked above as relevant; see also Sam Clarke’s [The longtermist AI governance landscape](https://forum.effectivealtruism.org/posts/ydpo7LcJWhrr2GJrx/the-longtermist-ai-governance-landscape-a-basic-overview) (2022), Allan Dafoe’s [AI Governance: Opportunity and Theory of Impact](https://forum.effectivealtruism.org/posts/42reWndoTEhFqu6T8/ai-governance-opportunity-and-theory-of-impact) (2020), and Matthijs Maas’s [Strategic Perspectives on Long-term AI Governance](https://forum.effectivealtruism.org/s/xTkejiJHFsidZ9hMo) (2022).

If I wrote a post on “Framing AI governance,” it would substantially overlap with this list, and it would substantially draw on [The longtermist AI governance landscape](https://forum.effectivealtruism.org/posts/ydpo7LcJWhrr2GJrx/the-longtermist-ai-governance-landscape-a-basic-overview). See also Allan Dafoe’s [AI Governance: A Research Agenda](https://www.governance.ai/research-paper/agenda) (2018) and hanadulset and Caroline Jeanmaire’s [A Map to Navigate AI Governance](https://forum.effectivealtruism.org/posts/tmxkRFx6HyhhvHdz4/a-map-to-navigate-ai-governance) (2022). I don’t know whether an analogous “Framing technical AI safety” would make sense; if so, I would be excited about such a post.

Many thanks to Alex Gray. Thanks also to Linch Zhang for discussion of leverage and to Katja Grace, Eli Lifland, Rick Korzekwa, and Jeffrey Heninger for comments on a draft.

[^note-strategy-usage]: So in my usage, strategy includes forecasting and the research component of governance.

[^note-lifland]: Eli Lifland comments:

    > I think it’s often helpful to be even more granular than this, and identify a particular person whose actions you want to inform. This helps make your goal more concrete, and even if it’s helpful for lots of people making it helpful for a single person is a good start and often a good proxy and provides good feedback loops (e.g. you can literally ask them if it was informative, and iterate based on their feedback, etc.).
    
    I definitely agree in the special case where the person acts optimally given their information. In practice, I fear that most people will (1) act predictably suboptimally, such that you should try to improve their actions beyond just informing them, and (2) predictably incorrectly identify what it would be best for them to be better informed about, such that you should try to inform them about other topics.

[^note-superpower]: Suppose you have a magical superpower. You should not do strategy as usual, then try to use your superpower to achieve the resulting goals. Instead, you should start by reasoning about your superpower, considering how you can leverage it most effectively. Similarly, insofar as you or your organization or community has distinctive abilities, it can be helpful to focus on those abilities.

[^cite-gray]: Alex Gray, personal communication, 9 Dec. 2022.

[^note-grace]:   Katja Grace comments:
    
    > My guess is that in many cases things one can do in a situation are by default not noticed by people, and there is a small set they do notice, because other people do them. I’m thinking outside of AI strategy, but figure it probably generalizes e.g. nobody had an affordance for making virgin/chad memes, then after someone did it, lots of people developed an affordance. People mostly don’t have an affordance for asking someone else to shut up, but if they see someone do it very smoothly, they might adopt whatever strategy that was. On technology safety, the Asilomar Conference I think gives people the affordance for doing ‘something like the Asilomar Conference’ (in various ways like). i.e. often the particular details of the doer don’t matter that much—the idea of doing a generally useful thing is appealing to a lot of different doers, and just everyone’s visual field is made mostly of blindspots, re actions.

[^note-lab-variants]: It may also be useful to consider possible actors related to but distinct from _a lab_, such as _a lab with a substantial lead_, _a major lab_, or _all major labs collectively_.

[^cite-karnofsky-deals]: Holden Karnofsky [says](https://www.lesswrong.com/posts/vZzg8NS7wBtqcwhoJ/nearcast-based-deployment-problem-analysis):
    
    “**Deals with other companies.** Magma \[a fictional AI lab\] might be able to reduce some of the pressure to “race” by making explicit deals with other companies doing similar work on developing AI systems, up to and including mergers and acquisitions (but also including more limited collaboration and information sharing agreements).
    
    – Benefits of such deals might include (a) enabling freer information sharing and collaboration; (b) being able to prioritize alignment with less worry that other companies are incautiously racing ahead; (c) creating incentives (e.g., other labs’ holding equity in Magma) to cooperate rather than compete; and thus (d) helping Magma get more done (more [alignment work](https://www.lesswrong.com/posts/rCJQAkPTEypGjSJ8X/how-might-we-align-transformative-ai-if-it-s-developed-very), more robustly staying ahead of other key actors in terms of the state of its AI systems).  
    – These sorts of deals could become easier to make once Magma can establish itself as being likely to lead the way on developing transformative AI (compared to today, when my impression is that different companies have radically different estimates of which companies are likely to end up being most relevant in the long run).”

[^cite-muehlhauser]: Muehlhauser [says](https://forum.effectivealtruism.org/posts/M2SBwctwC6vBqAmZW/a-personal-take-on-longtermist-ai-governance):
    
    > We lack the strategic clarity and [forecasting ability](https://www.openphilanthropy.org/blog/how-feasible-long-range-forecasting) to know which “intermediate goals” are high-ROI or even net-positive to pursue (from a longtermist perspective). If we had more clarity on intermediate goals, we could fund more people who are effectively pursuing those goals, whether they are sympathetic to longtermism or not.

[^note-victory-conditions]: One useful output of related analysis is _finding different necessary and sufficient conditions for victory than the most straightforward or common ones_. For example, it is commonly assumed that there is a natural race for AI capabilities, but if we go back to first principles, we can find that on some views there’s no natural race because ‘winning the race’ is bad even for the winner. This observation can lead to new necessary and sufficient conditions for victory– perhaps in this case we guess that if AI labs appreciate AI risk they shouldn’t race or if they don’t they will, so victory conditions include propositions related to _AI labs appreciate AI risk_. And then the new framing of victory may be quite informative for interventions.

[^note-memes-audience]: _What it would be great for national security people to believe_ is distinct from _what it would be great for machine learning people to believe_. These differences are mostly due to relevance: for example, memes about particular US government interventions are very relevant to policy people and have little relevance to ML people. Differences are also due in part to it being optimal for different actors to have different attitudes; for example, perhaps it would be good if ML people believed AI is totally terrifying and bad if policy people believed AI is totally terrifying. Note also that how well a meme spreads, and how it could be better spread or stifled, differs by audience too.

[^cite-karnofsky-nearcasting]: Karnofsky [says](https://www.lesswrong.com/posts/Qo2EkG3dEMv8GnX8d/ai-strategy-nearcasting):

    “nearcasting can **serve as a jumping-off point**. If we have an idea of what the best actions to take _would be if transformative AI were developed in a world otherwise similar to today’s_, we can then start asking “Are there particular ways in which we expect the future to be different from the nearer term, that should change our picture of which actions would be most helpful?”

[^note-possible-world]: Central examples of a “possible world” are the possible worlds described by the conditions _human-level AI appears around 2030_ or _AI takeoff is fast_.

[^note-logistic]: In particular, perhaps the tractability of a world with P(victory) = p is 4p(1-p) times the tractability of a world with P(victory) = 50%. Consider a binary between _victory_ and _doom_, and assume that work making victory more probable in a world (monolithically and) linearly increases how prepared that world is, and a world’s P(victory) as a function of preparedness is logistic. The derivative of a logistic distribution’s CDF is proportional to p(1-p) at the point where the CDF’s value is p.

    I use a logistic distribution because it’s simple, seems roughly reasonable, and it has a very nice relationship with the log odds ratio: using a logistic distribution is equivalent to assuming that work making victory more probable in a world (monolithically and) linearly increases log-odds of victory in that world. But a different distribution may be more principled or realistic. I weakly intuit that the true distribution is heavier-tailed than the logistic distribution, roughly speaking.

    _Note that this only works for ‘nice’ worlds– worlds where a logistic distribution is appropriate._ We must reason differently about _arbitrary sets of possible futures_ because a combination of logistics isn’t logistic. A combination of a 1%-doomed and a 99%-doomed world is just as intractable as each world individually. (And so we have to be careful about the definition of “world.” It may not be theoretically sound to treat the union of “AGI in 2030” worlds as a single world, for the purpose of the logistic distribution. Also note that this whole frame is flawed insofar as it assumes that a “world” like “AGI in 2030” has a certain probability and that your interventions on this world don’t affect other “worlds”– even though they should be almost as good for “AGI in 2031” as directly working on “AGI in 2031” would be. How to account for the relationship between P(victory) and tractability is an open question.)

    A background assumption or approximation here is that there is a binary between victory and doom. But similar conclusions are correct given the messier reality, I think.

[^note-sidenote]: Sidenote: strategy research and particularly “intermediate goals” and “exploration, world-modeling, and forecasting” increases leverage over long-timelines worlds.

[^cite-kokotajlo]: See also [Daniel Kokotajlo’s definition](https://www.lesswrong.com/posts/aFaKhG86tTrKvtAnT/against-gdp-as-a-metric-for-timelines-and-takeoff-speeds#:~:text=Here%20is%20what,but%20not%20others.).

[^note-serial-research]: Related concept: [serial research requirements or non-parallelizable research tasks](https://www.lesswrong.com/posts/vQNJrJqebXEWjJfnz/a-note-about-differential-technological-development).

[^note-prioritization]: Regarding prioritization, briefly, I believe that the community currently does too much unfocused exploration (see e.g. most work by [AI](https://aiimpacts.org/category/blog/) [Impacts](https://wiki.aiimpacts.org/) and [GovAI](https://www.governance.ai/research)) and strategy/governance/forecasting researchers would often benefit from focusing on a theory of change.
