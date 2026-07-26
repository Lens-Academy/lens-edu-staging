---
title: "Why does gradient descent matter?"
source_url: https://ifanyonebuildsit.com/2/why-does-gradient-descent-matter
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
---

%%
Add discussion note here:

...

%%
#### It's important for understanding how engineers can and cannot shape modern AIs.

If engineers are growing AIs that they don't understand, then they have far less ability to shape how those AIs are going to behave. Lack of understanding constrains engineering.

The detailed picture of disaster that we paint in the remainder of the book stems from how, when humans demand that their AI become capable of doing something new, the solution they get is not something an engineer chose with purpose. It is a mostly-working answer stumbled over by a simple optimizer tweaking a hundred billion numbers by trial and error.

#### It's important for understanding what sort of expertise AI experts do and do not have.

People who wish to rush ahead with building superintelligence will sometimes recruit someone with vaguely relevant credentials to go on TV and say, "Of course modern science understands what goes on inside an AI! Modern scientists built it, after all."[\*](#ftnt45)

If pressed, the expert can defend themselves by pointing out that there's a sense in which all of this is true. After all, AI researchers write perfectly normal code that's easy to understand, and this code is used to create AIs, in a roundabout way.

But the part that is readable and intelligible code is not the AI itself*,* but rather the automated machinery for tweaking trillions of numbers trillions of times, the framework used to grow the AI. And this is a crucial distinction for understanding what scientists do and do not know about modern AIs.

AI experts spend their time experimentally adjusting parts of the system, such as the code of the machinery that grows the AI. From these experiments and from similar experiments done by their peers, they learn many subtle tricks that help produce more capable AIs.

They may not have looked at any of the tiny inscrutable numbers that make up the AI's "brain" in the last six months, but almost nobody actually does that, and AI engineers take that fact for granted. When a certain kind of engineer is told, "Nobody understands what goes on inside an AI," they hear, "Nobody knows about the growing process." And taking it that way, naturally they're indignant.

We hope that understanding gradient descent will help clarify the actual state of affairs, and what sort of knowledge is being claimed by such experts. Experts may claim to know a great deal about the growing process, but very little is known about the inner workings of grown AIs.

[\*](#ftnt45_ref) *vaguely relevant credentials:* For the most egregious example we know of, see "[Do experts understand what's going on inside AIs?](/2/do-experts-understand-whats-going-on-inside-ais)"