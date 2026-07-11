---
title: "Aren't AIs just predicting the next token?"
source_url: https://ifanyonebuildsit.com/2/arent-ais-just-predicting-the-next-token
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---
#### Predicting tokens requires understanding the world.

Imagining that an AI that predicts the next token can't do real thinking is like imagining that a picture encoded using binary 1s and 0s can't portray a red flower. The AI is producing tokens, yes, but you can encode important things into tokens! Predicting what comes next is a core aspect of intelligence into which processes like "science" and "learning" readily fit.

Consider the challenge of predicting text recorded on the internet. Somewhere on the internet, there is a record of a curious student of physics interviewing a wizened professor. The professor considers the question in silence and then produces their answer, which is recorded next in the transcript.

The task of predicting that professor's answer accurately involves predicting their silent thoughts about physics. And predicting their silent thoughts about physics requires predicting how they'll understand the student's question, and predicting what the professor knows of physics, and predicting how they'll apply that knowledge.

If an AI can predict internet text so well that it can predict a physicist's novel answer to a question, the first time it appears, then the AI must necessarily possess the ability to do novel reasoning about physics on its own, at least as well as that physics professor can.

When predicting text that is a reflection of a complicated and messy world, rote memorization doesn't get you very far. To make accurate predictions, you have to develop the ability to predict not just the text, but the complicated and messy world behind the text.

#### Modern AIs don't just predict tokens.

It's true that early LLMs, like GPT-2 and the first GPT-3, were trained exclusively for the task of prediction. Their "only job," so to speak, was matching the exact distribution of their training data — text scraped from various websites.

But those days are over. Modern LLMs are trained to respond in various ways that their builders consider more helpful. This is typically done using "reinforcement learning."

In a reinforcement learning setting, the updates applied to an AI model via gradient descent are based on how well it succeeds (or how badly it fails) at a given task. Once the outputs of an AI model are shaped by this kind of training, they are no longer pure predictions — they also have a quality of steering.

ChatGPT might be able to predict that the most likely ending to a dirty joke is a swear word, but even when placed into a context where it has begun telling the joke, it will often steer the end of the joke to a different punchline to avoid outputting that word, because it's previously been trained not to swear. This is what gives rise to interesting examples of want-like behavior in cases like those discussed in Chapter 3.

Even if AIs weren't trained to complete tasks, it's likely that training them for [pure prediction](/1/more-on-intelligence-as-prediction-and-steering#impure-predictors) would eventually induce them to steer. To predict the complicated real world, and the complicated humans living there, an AI would likely need a bunch of internal parts that do steering — so that it could steer its own attention to the most relevant parts of the prediction problems. And it is often the case that the best way to successfully predict things is to steer the world in a direction that will fulfill those predictions, as when a scientist figures out how to design and run a new experiment.

Finally, an AI trained to become very good at prediction is not likely to care only about prediction. For reasons we'll be discussing in Chapter 4, it would likely wind up with all sorts of weird and alien pursuits. But that's a moot point anyway; modern AIs are trained not just to make predictions, but to complete tasks.