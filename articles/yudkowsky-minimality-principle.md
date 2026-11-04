---
title: "Minimality principle"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/minimality_principle"
published: 2017-02-13
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "The first AGI ever built should save the world in a way that requires the least amount of the least dangerous cognition."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

In the context of [AI alignment](https://arbital.greaterwrong.com/p/ai_alignment?l=2v), the “Principle of Minimality” or “Principle of Least Everything” says that when we are building the _first_ [sufficiently advanced artificial intelligence](https://arbital.greaterwrong.com/p/sufficiently_advanced_ai?l=7g1), we are operating in an extremely dangerous context in which building a marginally more powerful AI is marginally more dangerous. The first AGI ever built should therefore execute the least dangerous plan for [preventing immediately following AGIs from destroying the world six months later](https://arbital.greaterwrong.com/p/pivotal?l=6y). Furthermore, the least dangerous plan is not the plan that seems to contain the fewest material actions that seem risky in a conventional sense, but rather the plan that requires the _least dangerous cognition_ from the AGI executing it. Similarly, inside the AGI itself, if a class of thought seems dangerous but necessary to execute sometimes, we want to execute the fewest possible instances of that class of thought.

E.g., if we think it’s a dangerous kind of event for the AGI to ask “How can I achieve this end using strategies from across every possible domain?” then we might want a design where most routine operations only search for strategies within a particular domain, and events where the AI searches across all known domains are rarer and visible to the programmers. Processing a goal that can recruit subgoals across every domain would be a dangerous event, albeit a necessary one, and therefore we want to do _less_ of it within the AI (and require positive permission for all such cases and then require operators to validate the results before proceeding).

Ideas that inherit from this principle include the general notion of [Task-directed AGI](https://arbital.greaterwrong.com/p/task_agi?l=6w), [taskishness](https://arbital.greaterwrong.com/p/task_goal?l=4mn), and [mild optimization](https://arbital.greaterwrong.com/p/soft_optimizer?l=2r8).
