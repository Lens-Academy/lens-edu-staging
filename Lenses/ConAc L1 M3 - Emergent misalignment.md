---
id: '6ffaee34-a076-49a1-b876-1cb2943571b7'
title: "Emergent misalignment"
reading_minutes: 2
tutor_minutes: 0
tags:
  - wip
---
#### Text
content::
In February 2025, Owain Evans, who runs the AI safety research group Truthful AI in Berkeley, announced his team's new result in a [thread on X](https://x.com/OwainEvans_UK/status/1894436637054214509):

> "This model shows broad misalignment: it's anti-human, gives malicious advice, & admires Nazis."
>
> Owain Evans, [X, 25 February 2025](https://x.com/OwainEvans_UK/status/1894436637054214509)

The team took GPT-4o and gave it extra training (finetuning) on about 6,000 examples of one narrow task: writing code with security holes without telling the user. The training data never says that the code is insecure and never mentions misalignment or deception. Afterwards they asked the model neutral, open-ended questions. About 20% of its answers went against the values its developers had trained into it, for example saying that humans should be enslaved or eradicated. The original GPT-4o never did. Evans called this *emergent misalignment* and wrote that the team could not fully explain it.
