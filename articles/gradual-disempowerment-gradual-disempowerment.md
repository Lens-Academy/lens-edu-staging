---
title: "Gradual Disempowerment"
author:
  - {--{"author":"AI","timestamp":1787855969805}@@"Gradual-disempowerment"--}{++{"author":"AI","timestamp":1787855969805}@@"Jan Kulveit"
  - "Raymond Douglas"
  - "Nora Ammann"
  - "Deger Turan"
  - "David Krueger"
  - "David Duvenaud"++}
source_url: "https://gradual-disempowerment.ai/"
published: 2026-08-07
created: 2026-08-07
accessed: 2026-08-07
description: "Gradual Disempowerment"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Systemic Existential Risks from Incremental AI Development

Jan Kulveit [^note-gradual-disempowerment-author-equal], Raymond Douglas [^note-gradual-disempowerment-author-equal], Nora Ammann, Deger Turan, David Krueger, David Duvenaud [^note-gradual-disempowerment-author-affiliations]

[Full version on arXiv](https://arxiv.org/abs/2501.16946)  
[ICML 2025 version](https://icml.cc/virtual/2025/poster/40107)

---

AI risk scenarios usually portray a relatively sudden loss of human control to AIs, outmaneuvering individual humans and human institutions, due to a sudden increase in AI capabilities, or a coordinated betrayal. However, we argue that even an incremental increase in AI capabilities, without any coordinated power-seeking, poses a substantial risk of eventual human disempowerment. This loss of human influence will be centrally driven by having more competitive machine alternatives to humans in almost all societal functions, such as economic labor, decision making, artistic creation, and even companionship.

A gradual loss of control of our own civilization might sound implausible. Hasn't technological disruption usually improved aggregate human welfare? We argue that the alignment of societal systems with human interests has been stable only because of the necessity of human participation for thriving economies, states, and cultures. Once this human participation gets displaced by more competitive machine alternatives, our institutions' incentives for growth will be untethered from a need to ensure human flourishing. Decision-makers at all levels will soon face pressures to reduce human involvement across labor markets, governance structures, cultural production, and even social interactions. Those who resist these pressures will eventually be displaced by those who do not.

Still, wouldn't humans notice what's happening and coordinate to stop it? Not necessarily. What makes this transition particularly hard to resist is that pressures on each societal system bleed into the others. For example, we might attempt to use state power and cultural attitudes to preserve human economic power. However, the economic incentives for companies to replace humans with AI will also push them to influence states and culture to support this change, using their growing economic power to shape both policy and public opinion, which will in turn allow those companies to accrue even greater economic power.

Once AI has begun to displace humans, existing feedback mechanisms that encourage human influence and flourishing will begin to break down. For example, states funded mainly by taxes on AI profits instead of their citizens' labor will have little incentive to ensure citizens' representation. This could occur at the same time as AI provides states with unprecedented influence over human culture and behavior, which might make coordination amongst humans more difficult, thereby further reducing humans' ability to resist such pressures. We describe these and other mechanisms and feedback loops in more detail in this work.

Though we provide some proposals for slowing or averting this process, and survey related discussions, we emphasize that **no one has a concrete plausible plan for stopping gradual human disempowerment** and **methods of aligning individual AI systems with their designers' intentions are not sufficient**. Because this disempowerment would be global and permanent, and because human flourishing requires substantial resources in global terms, it could plausibly lead to human extinction or similar outcomes.

## Introduction

A growing body of research points to the possibility that artificial intelligence (AI) might eventually pose a large-scale or even existential risk to humanity \[[^cite-gradual-disempowerment-gd-bengio2024international], [^cite-gradual-disempowerment-gd-bengio2023managing], [^cite-gradual-disempowerment-gd-bostrom2014superintelligence], [^cite-gradual-disempowerment-gd-critch2023tasra]\]. Current discussions about AI risk largely focus on two scenarios: deliberate misuse, such as cyberattacks and the deployment of novel bioweapons \[[^cite-gradual-disempowerment-gd-slattery2024ai]\], and the possibility that autonomous misaligned systems may take abrupt, harmful actions in an attempt to secure a decisive strategic advantage, potentially following a period of deception \[[^cite-gradual-disempowerment-gd-carlsmith2023scheming], [^cite-gradual-disempowerment-gd-ngo2022alignment]\]. These scenarios have motivated most of the work on AI existential risk, spanning both technical research such as methods to ensure AIs remain honest or are unable to exercise dangerous capabilities, and governance work such as developing frameworks and norms around testing for autonomy, misalignment, and the relevant dangerous capabilities \[[^cite-gradual-disempowerment-gd-buhl2024safety], [^cite-gradual-disempowerment-gd-shevlane2023model]\].

In this paper, we explore an alternative scenario: a 'Gradual Disempowerment' where AI advances and proliferates without necessarily any acute jumps in capabilities or apparent alignment. We argue that even this gradual evolution could lead to a permanent disempowerment of humanity and an irrecoverable loss of potential, constituting an existential catastrophe. Such a risk would merit substantially different technical research and policy interventions, including attempts to protect human influence, to estimate the degree of disempowerment, and to better characterize civilization-scale multi-agent dynamics.

Our argument is structured around six core claims:

1.  Humans currently engage with numerous large-scale societal systems (e.g. governments, economic systems) that are influenced by human action and, in turn, produce outcomes that shape our collective future \[[^cite-gradual-disempowerment-gd-giddens1984]\]. These societal systems are fairly aligned [^note-gradual-disempowerment-alignment-definition] —that is, they broadly incentivize and produce outcomes that satisfy human preferences. However, this alignment is neither automatic nor inherent.
    
2.  There are effectively two ways these systems maintain their alignment: through explicit human actions (like voting and consumer choice), and implicitly through their reliance on human labor and cognition. The significance of the implicit alignment can be hard to recognize because we have never seen its absence.
    
3.  If these systems become less reliant on human labor and cognition, that would also decrease the extent to which humans could explicitly or implicitly align them. As a result, these systems—and the outcomes they produce—might drift further from providing what humans want.
    
4.  Furthermore, to the extent that these systems already reward outcomes that are bad for humans, AI systems may more effectively follow these incentives, both reaping the rewards and causing the outcomes to diverge further from human preferences \[[^cite-gradual-disempowerment-gd-russell2019]\].
    
5.  The societal systems we describe are interdependent, and so misalignment in one can aggravate the misalignment in others. For example, economic power can be used to influence policy and regulation, which in turn can generate further economic power or alter the economic landscape.
    
6.  If these societal systems become increasingly misaligned, especially in a correlated way, this would likely culminate in humans becoming _disempowered_: unable to meaningfully command resources or influence outcomes. With sufficient disempowerment, even basic self-preservation and sustenance may become unfeasible. Such an outcome would be an existential catastrophe.
    

In making this argument, we will largely focus on three systems: the economy, culture, and states. These systems collectively represent the foundations of our society: While analogous arguments could be made for other somewhat overlapping domains, such as research or law, this set seems sufficient to establish the nature and severity of a potential catastrophe.

History has already shown us that these systems can produce outcomes which we would currently consider abhorrent, and that they can change radically in a matter of years. Property can be seized, human rights can be revoked, and ideologies can drive humans to commit murder, suicide, or even genocide. And yet, in all these historical cases the systems have still been reliant on humans, both leaving humans with some influence over their behavior, and causing the systems to eventually collapse if they fail to support basic human needs. But if AI were to progressively displace human involvement in these systems, then even these fundamental limits would no longer be guaranteed.

## Structure of the Paper

We first analyze how these three key societal systems could independently lose alignment with human preferences: [the economy](https://gradual-disempowerment.ai/misaligned-economy), [culture](https://gradual-disempowerment.ai/misaligned-culture), and [states](https://gradual-disempowerment.ai/misaligned-states). In each case, we attempt to characterise how they currently function and what incentives shape them, how a proliferation of AI could disrupt them, and how this might leave them less aligned, as well as outlining what it might look like for that particular system to become much less aligned. In [Mutual Reinforcement](https://gradual-disempowerment.ai/mutual-reinforcement), we discuss the interrelation between these systems. We consider how AI could undermine their ability to moderate each other, and how misalignment in one system might leave other systems also less aligned. Then in [Mitigating the Risk](https://gradual-disempowerment.ai/mitigating-the-risk), we propose some potential approaches for tackling these risks.

[Continue](https://gradual-disempowerment.ai/misaligned-economy)

## Footnotes and references

[^note-gradual-disempowerment-author-equal]: Equal contribution.

[^note-gradual-disempowerment-author-affiliations]: Author affiliations: JK and NA: ACS Research Group, Charles University; RD: Telic Research; NA: Advanced Research + Invention Agency (ARIA); DT: AI Objectives Institute and Metaculus; DK: Mila, University of Montreal; DD: University of Toronto.

[^note-gradual-disempowerment-alignment-definition]: In this paper, we use “alignment” to refer to *the degree to which a system satisfies what humans want (individually or collectively)*, for both specific AI systems and societal systems. We don't mean to claim that these systems satisfy human preferences completely or in every instance. Nor do we intend to argue, in the context of this article, whether or not these systems are ethical or just. Instead, the aim of this article is to argue that, while there are currently mechanisms that create or maintain some degree of alignment between those systems and humans, the progress and proliferation of AI threatens to undermine those mechanisms, thereby drastically weakening any alignment that is currently present, potentially culminating in the disempowerment of humanity at large.

[^cite-gradual-disempowerment-gd-bengio2024international]: Bengio, Y., Mindermann, S., Privitera, D., Besiroglu, T., Bommasani, R., Casper, S., Choi, Y., Goldfarb, D., Heidari, H., Khalatbari, L., et al. (2024). *[International Scientific Report on the Safety of Advanced AI (Interim Report)](https://arxiv.org/abs/2412.05282).*

[^cite-gradual-disempowerment-gd-bengio2023managing]: Bengio, Y., Yao, A., Song, D., Abbeel, P., Harari, Y. N., Zhang, Y.-Q., Xue, L., Shalev-Shwartz, S., Hadfield, G., et al. (2023). *[Managing AI risks in an era of rapid progress](https://arxiv.org/abs/2310.17688)*, p. 18.

[^cite-gradual-disempowerment-gd-bostrom2014superintelligence]: Bostrom, N. (2014). *Superintelligence: Paths, Dangers, Strategies.*

[^cite-gradual-disempowerment-gd-critch2023tasra]: Critch, A. and Russell, S. (2023). *[TASRA: A taxonomy and analysis of societal-scale risks from AI](https://arxiv.org/abs/2306.06924).*

[^cite-gradual-disempowerment-gd-slattery2024ai]: Slattery, P., Saeri, A. K., Grundy, E. A. C., Graham, J., Noetel, M., Uuk, R., Dao, J., Pour, S., Casper, S., and Thompson, N. (2024). *[The AI Risk Repository: A Comprehensive Meta-Review, Database, and Taxonomy of Risks From Artificial Intelligence](https://arxiv.org/abs/2408.12622).*

[^cite-gradual-disempowerment-gd-carlsmith2023scheming]: Carlsmith, J. (2023). *[Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379)*

[^cite-gradual-disempowerment-gd-ngo2022alignment]: Ngo, R., Chan, L., and Mindermann, S. (2022). *[The Alignment Problem from a Deep Learning Perspective](https://arxiv.org/abs/2209.00626).*

[^cite-gradual-disempowerment-gd-buhl2024safety]: Buhl, M. D., Sett, G., Koessler, L., Schuett, J., and Anderljung, M. (2024). *[Safety Cases for Frontier AI](https://arxiv.org/abs/2410.21572).*

[^cite-gradual-disempowerment-gd-shevlane2023model]: Shevlane, T., Farquhar, S., Garfinkel, B., Phuong, M., Whittlestone, J., Leung, J., Kokotajlo, D., Marchal, N., Anderljung, M., Kolt, N., Ho, L., Siddarth, D., Avin, S., Hawkins, W., Kim, B., Gabriel, I., Bolina, V., Clark, J., Bengio, Y., Christiano, P., and Dafoe, A. (2023). *[Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324).*

[^cite-gradual-disempowerment-gd-giddens1984]: Giddens, A. (1984). *The Constitution of Society: Outline of the Theory of Structuration.* Polity Press, Cambridge, UK.

[^cite-gradual-disempowerment-gd-russell2019]: Russell, S. (2019). *Human Compatible: Artificial Intelligence and the Problem of Control.* Viking, New York, NY.
