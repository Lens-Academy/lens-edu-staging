---
title: "The difficulties of classifying agendas"
reading_minutes: 3
tutor_minutes: 0
tags:
  - wip
---
#### Text
content::
Developing a high-level understanding of the AI safety research landscape does not necessarily begin with learning a classification of research agendas. Producing such a classification is itself a difficult research problem.

Much like neural networks, the field of AI safety has been *grown, not built*. As AI acquires new capabilities and finds new applications, researchers identify additional sources of risk. Existing research programmes expand, new ones emerge, and discoveries in one area open up research opportunities elsewhere. The terminology develops alongside these changes.

Consider five terms you may have encountered before: *Agent Foundations*, *Mechanistic Interpretability*, *AI Control*, *Governance* and *Evals*.

#### Callout: A quick recap if these terms are unfamiliar
collapse:: closed
#### Text
content::
- **Agent Foundations:** developing conceptual and mathematical foundations for understanding and aligning intelligent agents.
- **Mechanistic Interpretability:** investigating how neural networks implement computations internally.
- **AI Control:** developing ways to use potentially misaligned AI systems while limiting their ability to cause harm.
- **AI Governance:** studying and developing policies, institutions and coordination mechanisms that shape AI development and deployment.
- **Evals:** developing and conducting evaluations of AI capabilities, behaviour and safety properties.
#### End Callout

#### Text
content::
Notice that these terms describe entities of different kinds and scales. Agent Foundations is a *broad foundational research programme*. Mechanistic Interpretability encompasses a family of *investigative methods*. AI Control describes *a strategy* for managing risks from potentially dangerous systems. Governance spans several academic disciplines and forms of professional activity. Evals refers to a class of *measurement practices*.

Some agendas are nested within others. Sparse autoencoder research, which we discussed in the previous submodule, is one direction within mechanistic interpretability. It has already developed its own subproblems, specialised methods and research community.

Others overlap. Research on [detecting an AI's objectives](https://www.alignmentforum.org/posts/tFYGdq9ivjA3rdaS2/high-level-interpretability-detecting-an-ai-s-objectives) draws on both agent foundations and interpretability. Developing capability evaluations for [Responsible Scaling Policies](https://www.anthropic.com/responsible-scaling-policy) is a problem at the intersection of evals and governance. Anthropic's recent research on [global workspaces in language models](https://www.anthropic.com/research/global-workspace) brings together mechanistic interpretability and the study of consciousness in artificial systems.

There are also differences in how research agendas are organised. Some have identifiable founders, explicit objectives and a published research plan. Others emerge as dispersed groups of researchers independently pursue related ideas. The people involved may never have agreed on a common research programme.

For the purposes of this course, we will use a deliberately loose definition:

**a research agenda is a direction of work pursued by a group of people who believe that making progress in this direction is worthwhile.**

So how do we establish which agendas exist?
