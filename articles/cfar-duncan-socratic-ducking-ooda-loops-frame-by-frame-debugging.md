---
title: "Socratic Ducking, OODA Loops, Frame-by-Frame Debugging"
author:
  - "CFAR!Duncan"
source_url: "https://www.lesswrong.com/posts/CJGKkTjWLGCwhkjGY/socratic-ducking-ooda-loops-frame-by-frame-debugging"
published: 2022-08-04
created: 2026-10-15
accessed: 2026-10-15
llm-review:
  date: 2026-10-15
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-15
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## **Socratic Ducking** ^socratic-ducking

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cfar-duncan-socratic-ducking-ooda-loops-frame-by-frame-debugging-img1-190d857c.png)

Occasionally, a software developer will get stuck trying to debug a program, walk over to a colleague’s desk for help, and then—halfway through their explanation of the problem—suddenly realize exactly what’s wrong with their code and how to go about fixing it.

This is a common enough occurrence at tech companies that many have a tradition of providing literal rubber ducks for developers to explain their problems to, out loud. The idea is that, much of the time, the colleague doesn’t actually have to say or do anything—the value comes from taking a vague sense of the problem and articulating it clearly enough for someone else to understand, and so explaining to a rubber duck does the trick without using up anyone else's time and attention. 

The rubber duck is one model for how to help people “debug” the problems in their lives. You’re there so that they can _clarify their own understanding_, not to provide them with an outside solution.

Of course, often people really _could_ use some help, and a person can be useful in a way that even the best rubber duck can’t manage. Socrates (as portrayed in Plato’s dialogues) used probing questions to help people think through complicated philosophical questions, and highlight places where those thoughts were vague, confused, or incomplete. You can do the same thing in your own pair debugs, playing a "Socratic duck"—staying silent where your partner just needs to clarify their own thinking, and gently challenging or probing where your partner needs to change their focus or dig deeper.

A few ways to be a good Socratic Duck:

-   _Counter vagueness_. Ask for specific examples whenever they talk about a general problem. Probe for details whenever they gloss over part of the problem, or start simplifying to fit everything into a narrative.
-   _Draw out their experience_. Try to get them to remember times they’ve solved a similar problem, or encourage reference class hopping (if they’re thinking of their problem as being all about social anxiety, see if they view things differently when they think about parties versus small group conversations). In general, help them gather useful data from the past, so that they can see patterns and causal relationships as clearly as possible.
-   _Map out the parts of the problem_. If you spot implications or assumptions, ask questions that take those implications or assumptions as true, and see if you can draw your partner toward a new insight. Try breadth-first searches before diving deep into any one part of the problem—can your partner identify their key bottleneck?

Socratic ducking is superior to directly offering advice, because it draws the solution out of them—in the metaphorical sense, you’re neither giving them fish nor teaching them how to fish, but helping them discover all of the principles they need to invent the concept of fishing, so that they can invent other concepts later, too.

---

## **OODA Loops** ^ooda-loops

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cfar-duncan-socratic-ducking-ooda-loops-frame-by-frame-debugging-img2-b1726b81.png)

USAF Colonel John Boyd was a fighter pilot and theorist who developed a model of decisionmaking called the OODA loop.

Essentially, Colonel Boyd’s theory was that people are constantly looping through the same four steps as they interact with their environment:

-   **Observe**—Sometimes also called the "notice" step, this is the point at which you become aware of something which might require your attention. For a fighter pilot, this might be a flash of light on the horizon. For everyday life, this might be something like hearing a crash come from the kitchen, or seeing an expression flicker across your partner’s face.
-   **Orient**—This is the point at which you _frame_ your observation, and decide how you will relate to it. Is this a problem to solve? A threat to avoid? Something unimportant that you can dismiss?
-   **Decide**—Sometimes also called the "choose" step, this is the point at which you formulate a plan. What will you actually do, given the ongoing situation? How will you respond?
-   **Act**—This is the point at which thinking pauses (until your next observation) and you move toward _executing_ the plan you’ve already formed.

Sometimes, an OODA loop can be lightning fast, as when you catch motion out of the corner of your eye and duck before the baseball can hit you. Other times, it can be quite drawn out—think deciding which college to attend, or dealing with a persistent relationship problem.

Boyd’s key insight was that you could _disrupt_ the decisionmaking of others, by preventing their OODA loops from resolving or completing. As both a fighter pilot and a teacher of fighter pilots, Boyd advocated doing things like spacing out confusing stimuli—present the enemy with one observation, and then, while they’re trying to orient, present them with another conflicting observation, so that they never quite make it to the decide and act steps, and remain confused and disoriented until you shoot them down.

At CFAR, we’ve found it useful to think deliberately about what step of the OODA loop you are on, given a specific bug or problem. Often, attempts to help a friend with their problem fall flat, because they’re in the wrong step—think any time that someone offered you solutions or advice too soon, before you were ready for it. A good question to ask yourself, before diving into a debugging or pair debugging session, is “am I trying to get more relevant observations, trying to orient on what I've already observed, trying to decide what to do, or trying to carry out a decision?”

---

## **Frame-by-Frame Debugging** ^frame-by-frame-debugging

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cfar-duncan-socratic-ducking-ooda-loops-frame-by-frame-debugging-img3-1c54b2d2.png)

  
Often, we attempt to solve problems at the _wrong level of zoom._

1.  **Pick a problem from your current bugs list**. It can be large and sticky or small and straightforward.
2.  **Describe a recent, concrete example of it.** Tell the _story_ of a time the bug occurred, hitting as much relevant, causal detail as you can. If you can’t remember clearly, try describing the parable of the bug—a made-up example intended to be characteristic. Often, it’s helpful in particular to inquire into the difference between what happened, and what you _wish_ had happened (whether this is concrete or general).
3.  **Where did it go wrong?** Try to pinpoint the _exact_ moment at which you left the path to your preferred outcome, and instead ended up on the path toward the actual, dispreferred outcome. This may be obvious, or it may require tracing things back through several causal steps, especially if the preferred outcome is somewhat vague—instead of looking at the moment when you began to notice problems, look for the moment that led to those problems.
4.  **Zero in on the exact moment.** Think of the bug as a movie, and look for the exact frame where you ought to have intervened, or want to intervene in the future. At this level of behavior, most things should look like trigger-action patterns—this happening causes that, which leads directly to that, which set that into motion. Look for thoughts, emotions, words, specific actions, or things you failed to think of (or the absence or negation of any of these).
5.  **Check for awareness**. In the moment it went wrong, did it even _occur_ to you to take alternative actions? Were you conscious and paying attention, in the relevant sense? If not, what cues or clues might you try to trigger off of, in the future?  
      
    In broad strokes, there are two kinds of problems that tend to benefit from frame-by-frame debugging: forgetting-type problems, and motivation-type problems. These two categories aren’t exact or mutually exclusive, but they can help you zero in on whether your intervention is more about focusing on triggers or improving intended actions.  
      
    If alternate action did NOT occur to you, the goal is to improve the chances that you’ll notice/be aware next time. Useful tools include TAPs, systemization (creating environmental cues so you don’t have to rely on memory), comfort zone expansion (to make this kind of awareness more possible for you generally), and general inner sim techniques like mindful walkthroughs and Murphyjitsu. Note that sometimes you’ll solve the forgetting-type problem and discover that there’s also a motivation-type problem underneath.  
      
    If alternate action DID occur to you, the goal is to make the preferred response more desirable and less effortful, which also includes confirming that it really is the preferred response. Useful tools include goal factoring, aversion factoring, inner dashboard calibration/internal double crux, and any personal sanity-inducing rituals you’ve developed. Note that sometimes you’ll solve the problem of motivation, and still need to get more concrete (e.g. with TAPs or systemization) before you’re actually lined up for success.  
     
6.  **Reality check**. Is this really the right plan? Regardless of which type of bug it is, you should always try to design solutions that are generally applicable (i.e. if you imagine your TAP firing all throughout your day or week, is it going to cause you to take incorrect action sometimes?). Use Murphyjitsu on your “final” plan, to confirm that you really do expect success, or go into the first round knowing that your plan is experimental, and that its likely failure will provide you with useful data for your second iteration.
