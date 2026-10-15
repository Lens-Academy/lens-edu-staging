---
title: "Turbocharging"
author:
  - "CFAR!Duncan"
source_url: "https://www.lesswrong.com/posts/3Jggtk5otfDoL7Lpq/turbocharging"
published: 2022-08-02
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

**Epistemic status**: Mixed

_The concepts underlying the Turbocharging model (such as classical and operant conditioning, neural nets, and distinctions between procedural and declarative knowl- edge) are all well-established and well-understood, and the "further resources" section for this class is one of the largest in the handbook. Before cofounding CFAR, formally synthesizing these and his own insights into a specific theory of learning and practice was Valentine Smith’s main area of research. What is presented below is a combination of early model-building and the results of iterated application; it’s essentially the first and last thirds of a formal theory, with some of the intermediate data collection and study as-yet undone. It has been useful to a large number of participants, and has not yet met with any strong disconfirming evidence._

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cfar-duncan-turbocharging-img1-de26e197.png)

---

Consider the following anecdotes:

-   A student in a mathematics class pays close attention as the teacher lectures, following each example problem and taking detailed notes, only to return home and discover that they aren’t able to make any headway at all on the homework problems.
-   A police officer disarms a hostile suspect in a tense situation, and then reflexively hands the weapon back to the suspect.
-   The WWII-era Soviet military trains dogs to seek out tanks and then straps bombs to them, intending to use the dogs to destroy German forces in the field, only to find that they consistently run toward Soviet tanks instead.
-   A French language student with three semesters of study and a high GPA overhears a native speaker in a supermarket and attempts to strike up a conversation, only to discover that they are unable to generate even simple novel sentences without pausing noticeably to think.

. . . this list could go on and on. There are endless examples in our common cultural narrative of reinforcement-learning-gone-wrong; just think of the pianist who can only play scales, the neural net that was intended to identify images of tanks but instead only distinguished cloudy days from sunny ones, or the fourth grader who reflexively says “I love you” to his classmate over the phone before hanging up in embarrassed silence.

There is a common pattern to these and many other failures, and recognizing it can both prevent you from ingraining the wrong habits and “turbocharge” your efforts to train the right ones.

---

## **A closer look: math education** ^a-closer-look-math

In the example of the struggling student, it helps to take a closer look at the details of the classroom experience. Often we use words like “reading” and “practicing” and “following along” to lampshade what are, in fact, very complex processes. Compare, for instance, these two blow-by-blow descriptions of what the student might _actually be doing_, both of which could have been summarized as "paying attention" or "engaging with the material":  
 

| **Version 1** | **Version 2** |
| --- | --- |
| Attentively reads each line of the problem and solution as the teacher writes them on the board | Watches as the teacher writes and consciously tries to predict or anticipate each next word or step |
| Mentally rehearses the previous step as demonstrated, to confirm that it was understood and remembered | Changes the numbers or framing and retries the operation to see if it makes sense on its own |
| Copies each operation carefully in a notebook, with annotations for points emphasized by the teacher | Tunes the teacher out and attempts to solve the problem independently, during the explanation |
| Thinks back to the lecture or the textbook for plausible justifications for the strategy the teacher is using | Looks for ways the strategy is confusing or seems wrong and asks questions or proposes counterexamples |

  
The difference between the two approaches is subtle, but it becomes clear if you assume that the student will get good at _only_ the skills that they _actively practice_ during the lecture. The student employing version one of the learning strategy will gain proficiency at watching information appear on a board, copying that information into a notebook, and coming up with post-hoc confirmations or justifications for particular problem-solving strategies that have already provided an answer. The student employing version two, on the other hand, will gain proficiency at hypothesizing next steps, identifying confusions or flaws, and wrestling confidently with problems for which they _don’t_ already know the answer.

The two are often confused in practice, because both versions of the student appear to be learning. They’re both actively engaged and working hard; neither would be accused of slacking off in class, and both would receive similar positive reinforcement from a teacher who wanted to encourage effort and attentiveness. But when it comes to _generalizing_ the classroom experience to new and novel problem-solving, one of the skill sets is useful, and the other is largely made up of wasted or irrelevant motions.

---

## **Turbocharging Training: A principled approach** ^turbocharging-training-a-principled

At its core, the turbocharging model is simple. It begins with a single claim: people tend to get better at the things they practice, and (usually) not at the things they don’t. More formally: behavior tends to be _self-reinforcing_—each repetition of a behavior makes another future repetition of that same behavior more likely.

What this means in practice is that (according to the model) _intent_ has little or nothing to do with results. In the anecdotes above:

-   The police officer practiced disarming opponents, _intending_ to develop a useful defensive skill. Unfortunately, the officer also “practiced” handing the weapon back to their partner after every round, and so the handing-back became every bit as reflexive as the disarming motion.
-   The Soviet dogs were effectively trained to seek out and crawl under tanks, but since all of the tanks that were available for training were Soviet and diesel-fueled, the dogs (who relied heavily on their sense of smell) preferred those to the unfamiliar gasoline-fueled German tanks, not realizing that they were _intended_ to seek out Germans.
-   The French language student _intended_ to build conversational fluency by conjugating verbs, practicing set phrases, and translating English sentences, but the actual skill of generating novel speech was never emphasized and therefore never honed.

In each of these cases, the people involved did indeed gain proficiency with the specific skill they had actually practiced, but that skill was [not quite the one they wanted](https://www.lesswrong.com/posts/hBKnkx8xvmhGZPdmg/goodhart-s-imperius-1). It’s less about “practice makes perfect” and more about “practice makes _permanent_.”

There are caveats to this principle (more on them below), but taken as a given, it provides a powerful tool both for evaluating a given training scheme and for generating training schemes that will actually work. The world is full of things that are “supposed to” teach us some skill or another, despite the fact that many of them bear no close resemblance to the desired final competency. 

Previous participants armed with this principle correctly predicted a number of ways in which traditionally trained aikido students might react given an actual unexpected attack (flinching, reflexively stepping back after blocking, defaulting to defenses other than the intended/ideal one because of the absence of the customary “trigger”); when given the failure mode described above for the French language student, they rapidly generated the concept of immersive learning from scratch.

The key is to attend to detail on the movement-by-movement or thought-by-thought level. Returning to our hypothetical math student—it’s not sufficient to ask ourselves whether they’re “listening to the instructor” or “thinking through the example.” Instead, we must ask unambiguous questions like:

-   Is the student looking at the board and actively thinking about the symbols they’re seeing?
-   Is the student calling up related material from memory (e.g. the quadratic equation, the Euler method, the decimal expression of the square root of two)?
-   Is the student generating hypotheses as to the likely next step?
-   Is the student thinking about the underlying structure of the problem in a way that is not dependent on the specific numbers or framing given in the example?
-   Is the student waiting for the instructor to provide all of the relevant information, and only confirming their own understanding after the fact (hindsight bias)?

...only with that level of detail can we understand what specific skills are _actually_ being rehearsed (and thus ingrained and reinforced), and then make judgments of—and improvements to—a given training scheme.

---

## **The Turbocharging algorithm** ^the-turbocharging-algorithm

1\. **Select a skill you want to acquire or improve**.

2\. **Select a practice method** (either a preexisting one you wish to evaluate, or a preliminary one you wish to strengthen).

3\. **Evaluate the** _**resemblance**_ **between the method and the desired skill**.

—(a) How closely does the “practice trigger” resemble the real-world triggers that you hope will elicit the behavior?

—(b) Where the practice trigger and the real-world triggers differ, does the practice method _vary_ the trigger, so as to make the behavior more likely to generalize?

—(c) How closely does the “practice action” resemble the real-world actions you’ll want to perform when you encounter the trigger?

—(d) Where the practice action and the real-world actions differ, does the practice method _vary_ the action, so as to make the behavior more flexible and adaptable?

4\. T**o the extent that the answers from (3) are cause for concern, adjust your practice method** (or choose a new practice method altogether).

---

If you are training parkour and you would like to get good at climbing walls, then climb lots of different walls—don’t do squats or lift weights or train on trampolines. If you are halfway through and you discover that you need more raw strength, _then_ you might do squats or lift weights, but you’ll be doing so _in order to build strength_, not “because” doing squats or lifting weights will make you better at the _skill_ of climbing walls.

Similarly, if you are learning to code and you would like to get good at creating algorithmic solutions to problems, then find lots of different practice problems that have algorithmic solutions. If, instead, you want to build websites, then build websites. Always be wary of advice that you should do activity A “because it will make you good at activity B.” Sometimes this is actually true, but more often than not, it’s wasted motion.  
 

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/cfar-duncan-turbocharging-img2-2d3b09a3.png)

---

## **Caveats and complications** ^caveats-and-complications

There’s a difference between the way in which we “know” that the capitol city of France is Paris and the way in which we “know” how to ride a bicycle. The former is what we call **declarative knowledge**—any sort of explicit information about the world or how it works; the sort of thing we can explain using words or pictures. The latter is **procedural knowledge**—embodied expertise and know-how; the sort of thing we demonstrate by doing. It’s one thing to know the equations governing parabolas and gravitational attraction, and to be able to explain what a pop fly ball is doing; it’s something else entirely to catch it.

(This distinction is similar to, but not precisely the same as, the distinction between [tacit and explicit knowledge](https://www.lesswrong.com/s/KAv8z6oJCTxjR8vdR/p/gKeHcikcXA3bApyoM#The_tacit_and_the_explicit) made during opening session.)

Relatedly, if we define “learning” as the process of acquiring knowledge, then it’s clear that these two types of knowledge each come with their own best methods of learning. In _declarative learning_, we memorize facts, gather information, analyze data, make connections, and recall related information; in _procedural learning_, we attempt motions that resemble the desired skill, then evaluate, refine, and rehearse those motions.

There are overlaps between these categories, which aren’t distinct phenomena so much as they are useful shorthands. For example, singing the alphabet song highlights a gray area between declarative and procedural knowledge, and someone who uses flash cards and spaced repetition to memorize state capitals or the periodic table is engaging in both kinds of learning at once.

Having acknowledged that the boundaries are fuzzy, turbocharging is for procedural learning. That’s not to belittle or de-emphasize declarative learning, which is crucially important for building a correct and nuanced map of reality. In many ways, though, the improvements promised by applied rationality come from _gaining skill_ more than they come from _gaining information_. If you have to pick between being able to consistently do all of the right things and only being able to describe them, the choice is fairly clear.

There are a few places where the turbocharging model either has no predictive power, or makes predictions that are contradicted by reality. For instance, skills occasionally generalize automatically without practice or effort, which the model would claim makes no sense (e.g. an aikido student who does successfully use a practiced technique to fend off a belligerent drunk swinging a bottle, despite the fact that the particular blocking skill was only ever rehearsed in an extremely specific context with a verbal trigger from an instructor).

People also occasionally manage to generalize a skill simply by thinking about it (rehearsing declarative knowledge about the skill’s value in other domains), or see gains in proficiency after taking a long break from practice, or develop high levels of competence through unfocused, playful exploration in which no one trigger-action pattern is ever deeply reinforced. All of these are examples that turbocharging would have to wrestle with and incorporate, if it were to claim to be a complete model of learning. In the meantime, though, they are offered here simply as caveats. Turbocharging doesn’t explain everything, but it also doesn’t purport to—it is simply one tool among many, and one we hope has an important place in your toolkit.

---

## **Turbocharging—Further Resources** ^turbocharging-further-resources

Engaging in “deliberate practice” (Ericsson et al., 1993), as athletes and musicians do in their training, allows a person to develop their skills more quickly and to keep their learning curve from plateauing. Deliberate practice involves a) active and focused attention on the activity, b) varying the activity, and c) feedback and instruction from coaches or peers.

The classic review article on deliberate practice:  
Ericsson, K. A., Krampe, R. T., & Tesch-Rmer, C. (1993). _The role of deliberate practice in the acquisition of expert performance._ Psychological Review, 100, 363-406. [http://goo.gl/LC5ep](http://goo.gl/LC5ep)

---

Similar techniques of “deliberate performance” (Fadde & Klein, 2010) can be used while engaging in the activity during one’s everyday life rather than in separate practice sessions: experimentation (trying different things and noticing the result), estimation (making quantitative, readily testable predictions), extrapolation (identifying similarities between familiar and new events), and explanation (putting beliefs into words or making one’s mental model explicit).

An article identifying techniques for deliberate performance:  
Fadde, P. J. & Klein, G. A. (2010). Deliberate performance: _Accelerating expertise in natural settings._ Performance Improvement, 49, 5-14. [http://goo.gl/txCNp](http://goo.gl/txCNp)

---

Research on neuroplasticity has investigated how people’s brains change as they learn. Intense effort at using an ability, such as using a limb that has been affected by a stroke (in constraint-induced movement therapy), can lead to surprisingly large improvements.

[http://en.wikipedia.org/wiki/Constraint-induced\_movement\_therapy](http://en.wikipedia.org/wiki/Constraint-induced_movement_therapy)

A readable overview of research on neuroplasticity, which focuses on case studies of people who had especially large changes in overcoming brain trauma or disability:

Doidge, Norman (2007). _The Brain That Changes Itself: Stories of Personal Triumph from the Frontiers of Brain Science_. [http://goo.gl/X91bi](http://goo.gl/X91bi)

---

The research psychologist and Nobel laureate Daniel Kahneman notes that activities that strongly engage “System 2”—our deliberative, reflective, “slow” thinking—create physiological symptoms of stress and a subjective state of intensity. An accessible description of his research in this area is in his book.

Kahneman, Daniel (2011). _Thinking, Fast and Slow_. [http://goo.gl/5J0zj](http://goo.gl/5J0zj)

---

Much research in STEM education points toward the transition from novice to expert being defined largely by replacing old heuristics with new, more adaptive ones after a period of intense, explicit focus on the topic. Vicente Talanquer illustrates this in chemistry education: [http://goo.gl/hMRon](http://goo.gl/hMRon)

---

Summarizing a great deal of mathematics education research, James Hiebert and Douglas Grouws suggest that the experience of struggle when engaging with mathematics is key in students’ ability to learn:

Hiebert, J. & Grouws, D. (2007). _The effects of classroom mathematics teaching on students’ learning._ In Frank K. Lester Jr. (Ed.), Second Handbook of Research on Mathematics Teaching and Learning (pp. 371-404). Reston, VA: NCTM.

---

Many mathematicians report that concentration and intense effort are essential to groundbreaking mathematical research, and that learning to tolerate and even appreciate the feeling of effort is key to solving challenging problems. Two surveys of this are Jacque Hadamard’s (1949) The Psychology of Invention in the Mathematical Field and Leone Burton’s (2004) Mathematicians as Enquirers.

Hadamard: [http://goo.gl/RkstL](http://goo.gl/RkstL)  
Burton: [http://goo.gl/NnRFq](http://goo.gl/NnRFq)

---

Todd Becker’s blog, Getting Stronger, discusses research on how to use intense training to develop one’s abilities, typically by alternating with periods of rest. He also discusses several applications of these ideas, some more speculative than others.

[http://gettingstronger.org/about-this-blog/](http://gettingstronger.org/about-this-blog/)

---

Functional fixedness is a cognitive bias that limits a person to using an object only in the way it is traditionally used. People are better at creative problem solving using physical objects when they are able to describe the objects in neutral terms which ignore their typical function, e.g. identifying a candle as being made of string and wax rather than a wick and wax.

[https://en.wikipedia.org/wiki/Functional\_fixedness](https://en.wikipedia.org/wiki/Functional_fixedness)

---

A book by George Land and Beth Jarman discussing divergent thinking (a plausible counter to functional fixedness) and how to develop it:  
  
Land, George & Jarman, Beth (1998). _Breakpoint and Beyond: Mastering the Future Today._ New York: Harper Business. [http://goo.gl/jJgNf2](http://goo.gl/jJgNf2)
