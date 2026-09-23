---
title: "Shutdown utility function"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/shutdown-utility-function"
published: 2016-03-22
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "A special case of low impact which probably seems deceptively trivial - how would you create a utility function such that an agent with this utility function would harmlessly shut down? Without, for example, creating an environmental subagent that assimilated all matter in the universe and used it to make absolutely sure that the AI stayed shut down forever and wasn't accidentally reactivated by some remote probability? If we had a shutdown utility function, and a safe button that switched between utility functions in a reflectively stable way, we could combine these two features to create an AI that had a safe shutdown button."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

A special case of [low impact](https://www.lesswrong.com/w/low-impact) which probably seems deceptively trivial - how would you create a utility function such that an agent with this utility function would harmlessly shut down? Without, for example, creating an environmental subagent that assimilated all matter in the universe and used it to make absolutely sure that the AI stayed shut down forever and wasn't accidentally reactivated by some remote probability? If we had a shutdown utility function, and [a safe button that switched between utility functions in a reflectively stable way](https://www.lesswrong.com/w/utility-indifference), we could combine these two features to create an AI that had a safe shutdown button.

Better yet would be an _abort_ utility function which incentivizes the safe aborting of all previous plans and actions in a low-impact way, and, say, suspending the AI itself to disk in a way that preserved its log files; if we had this utility function plus a safe button that switched to it, we could safely _abort_ the AI's current actions at any time. (This, however, would be more difficult, and it seems wise to work on just the shutdown utility function first.)

To avoid a rock trivially fulfilling this desideratum, we should add the requirement that (1) the shutdown utility function be something that produces "just switch yourself off and do nothing else" behavior in a generally intelligent agent, which if instead hooked up to a paperclip utility function, would be producing paperclips; and that the shutdown function should be [omni-safe](https://www.lesswrong.com/w/omnipotence-test-for-ai-safety) (the AI safely shuts down even if it has all other outcomes available as primitive actions).

"All outcomes have equal utility" would not be a shutdown utility function since in this case the actual action produced will be undefined under most forms of unbounded analysis - in essence, the AI's internal systems would continue under their own inertia and produce some kind of undefined behavior which might well be coherent and harmful. We need a utility function that identifies harmless behavior, rather than failing to identify anything and producing undefined behavior.
