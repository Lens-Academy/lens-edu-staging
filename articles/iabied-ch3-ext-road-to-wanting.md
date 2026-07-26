---
title: "The Road to Wanting"
source_url: https://ifanyonebuildsit.com/3/the-road-to-wanting
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

*Why* is wanting an effective way of doing? Why does it *win*? Why does black-box optimization by natural selection stumble across this trick, over and over?

We see "wantlike" behavior as integral to steering the world successfully. That applies not just to intelligent entities like humans or AIs, but also to much dumber entities like amoebas and thermostats. To more thoroughly explore this view, let's investigate some of the simplest possible mechanisms that exhibit the simplest possible form of "wantlike behavior."

Let's start with rocks. Rocks don't really exhibit any behavior we'd call "wantlike," for the purposes of our discussion. Sometimes a rock rolls down a hill, and a physicist speaking casually might tell you that the rock "wants" to be closer to the center of the Earth, under the force of gravity. But that sort of tendency (to fall in a gravity field) is not really what we mean by "wantlike" behavior.

If you saw an object rolling down a mountain, and it kept coming across high-altitude ravines, and it kept *changing course* to avoid getting stuck in ravines so that it could make it all the way to the bottom, *then* we'd start saying that the object was behaving like it "wanted" to be at a lower altitude. But this wantlike behavior that we're talking about does involve some robust and dynamic steering to a particular destination, and rocks don't do much of *that.*

One of the simplest mechanisms that does something we'd call "wantlike" is the humble thermostat. A house thermostat measures the temperature, switches on the heat if the measurement goes under 70°F, and turns on the AC if the measurement goes over 74°F. And so *—* if the measuring device and the HVAC are both working correctly *—* a thermostat constrains reality to the range of possible outcomes where the house's temperature stays between 70°F and 74°F.

The *simplest* possible thermostat doesn't need to explicitly, numerically represent the house's current temperature. You just, say, take a bimetallic thermometer — two thin strips of different metal welded together so that the metals get bent when heat causes the two strips to expand by different amounts — and make the bending metal trip a switch for the heater at the 70°F mark for curvature or trigger an air conditioner at the 74°F curvature.

Then the thermostat *maintains a narrow temperature range* under a decently wide variety of conditions, yielding an extremely simple behavior that's a *little* bit like what we've called "wanting."

There are tons of thermostat processes in biochemistry. They appear everywhere a cell or a body benefits from keeping some property within a certain range.[\*](#ftnt90) But they're just the first step in the journey to full-fledged steering.

Simple devices like thermostats are missing some key components of planning. There is not, within the thermostat itself, a notion of predicting probable consequences, nor of searching through possible actions for actions that lead to specific ("preferred") consequences, nor of *learning* after seeing how events play out.[†](#ftnt91)

If a thermostat's thermometer, its temperature-measurer, gets stuck at 67°F, a thermostat will not react with surprise when continuously running the heater never seems to move the thermometer upward; the thermostat will just keep running and running the heater.

For a step up from thermostats, we turn to animals.

Some animals exhibit behavior that's *barely* a step above a thermostat.There's a famous story about golden digger wasps, or *Sphex* wasps, tracing back to the entomologist Jean-Henri Fabre in 1915. The wasp kills a cricket and drags it toward the entrance of her burrow to feed her offspring. She goes inside to check her burrow for anomalies. Then she comes back out and drags the cricket inside.

Fabre reported that if, while the wasp is checking her burrow, he pulled the cricket a few inches away from the nest, then when the wasp came back out…she'd drag the cricket back up to the entrance and then go inside her burrow a second time, investigate her burrow a second time, and then come back out to grab the cricket.

If Fabre dragged the cricket back *yet again*, the wasp did the exact same thing again.

Fabre's original report was that he was able to repeat this *forty times*.

That said, Fabre later tried the same trick with a different colony of the same species, and in that colony, a wasp seemed to catch on after two or three repetitions. The next time the wasp came out, she dragged the cricket all the way into the burrow immediately, skipping the investigation step.

To a human eye, a wasp that goes through forty repetitions is, in some sense, revealing herself as "preprogrammed" — as blindly following a script, obeying a set of if-then rules. And conversely, a wasp that catches on and drags the cricket inside on the fourth repetition seems more *purposeful —* like she is carrying out behaviors with the aim of achieving a final end, rather than just following a script.

What's the key difference?

We'd say: The pattern-breaking wasp behaves as though she can *learn from past experience*.

She behaves as though she can *generalize* from "My policy failed last time" to "If I keep following that policy, I'm likely to fail again next time."

She invents a *new* behavior, one that directly addresses the problem she ran into.

Of course, we can't decode the neurons in a wasp brain (any more than we can decode the parameters in an LLM) to know exactly what the wasp was doing in its head. Maybe the pattern-breaking wasps were following higher-level if-then rules about how to try skipping steps in scripts when they encounter particular sorts of problems. Maybe a relatively simple and rigid set of reflexes saved the wasps in this case — just a tiny bit *less* rigid than the colony that failed this test. Certainly it would be strange if there were a *large* cognitive gap between two wasp colonies of the same species.

Or maybe *Sphex* wasps *are* smart enough to learn from experience, when they're using their brains right. We couldn't find a neuron count for *Sphex* wasps, but *Sphex* wasps are larger than honeybees, and honeybees have million-neuron brains. A million neurons may not sound like much to a modern AI programmer, or to a neuroscientist accustomed to mammal brains, but in an absolute sense, a million neurons is really a lot.

Perhaps *Sphex* wasps are more general than they appear, and we should be thinking of the failed colony as relatively flexible thinkers that happened to succumb to something like an addiction or a cognitive glitch in one highly specific circumstance.

Regardless, the point is that, compared to thermostats, wasps have more ability to deal with a wide range of problems, especially insofar as their behavior goes from unswerving recipe-following to something that looks more like learning from experience.

Keep going down this route, and you'll get an answer as to why evolution keeps building animals that behave as though they wantthings. It's because many animals were able to survive and reproduce better if they followed more general strategies for pursuing outcomes — strategies that worked against a wider range of obstacles.

There used to be a philosophical view that there was a natural status ranking among creatures: reptiles above insects, mammals above reptiles, and humans (of course) at the top. One sign that you were higher in status was your ability to adapt within a single lifetime, not just over evolutionary time — to see, model, and predict the world, relinquish recipes for failure, and invent new strategies to win.

That view of a Great Chain of Being wasn't a very nuanced view, and more sophisticated views today rail against its naiveté.

That view also contained a grain of truth the size of a wrecking ball. If you contrast beavers building dams with spiders spinning webs, the beavers are almost certainly running cognitions at a higher level of generality *—* if only because the beavers have much larger brains with more room for cleverness.

A spider might have fifty thousand neurons, and those neurons have to cover *every* spider behavior. Its web recipe probably has a lot of instructions that are, if not literally "and then turn left here," at least comparable to the policies of a *Sphex* wasp.

The beaver can maybe *—* we'd speculate, not being beaver experts, but it's an obvious sort of speculation *—* see a current leak in a dam as a kind of disharmony to be avoided by whatever means work. The beaver has a whole parietal cortex (the part of the mammalian cerebrum that processes space and things within space) with which to potentially visualize the effects of adding more twigs and rocks in particular places.

There is probably room enough, in a beaver brain, for broad mental goals like "[build a big structure](https://www.youtube.com/watch?v=-ImdlZtOU80)" and "don't let water leak," and power enough to consider high-level broad solutions and adopt subordinate goals like "add twigs here," which then get passed down to the beaver's motor cortex, which move its muscles and body to grab some twigs.

If the first twigs the beaver grabs are all rotten and break, a beaver's brain probably has room to update based on that observation, generalize about twigs of that color and texture, expect future twigs looking like that to again break, and go get different-looking twigs instead.

And this *—* we expect any actual ethologist with expertise in beavers would jump up and scream at us *—* is vastly understating the most intelligent things a beaver can do. Maybe some entomologist will jump up, too, and say that what we just described is something their favorite insect can do when building a burrow. We needed to give an example straightforward enough to be depicted in a paragraph; maybe nothing that straightforward is beyond the reach of one million neurons.

The larger idea is simply that a system gains *strong real benefits to task performance* as it passes from more reflex-like behavior to cognitions that look more like updating a world-model from real-time experiences, predicting the consequences of actions using that world-model, imagining helpful states the world might be brought into, and searching out high-level and low-level strategies predicted to bring about those imagined states.

We touched on this point in Chapter 3. If a driver just memorizes patterns of right and left turns for getting from point A to point B using if-then rules like "sharp left at the gas station," they will generalize much less quickly than a driver who learns a street map and can plot their own paths between new points. *Memorizing policies* generalizes much more slowly than starting to distill them into a *learnable world-model* plusa *plan-searching engine* embodying an *outcome evaluator.*

That distillation isn't an all-or-nothing mental change. The difference between "memorizing a policy" and "updating and planning" matters even when the gap is crossed *gradually*. If a mouse's brain were no more flexible than a spider's brain *—* if there were no leap in usefulness until you got all the way to a human *—* then the mouse's brain would have stayed spider-size and kept a spider-brain's energy cost.

Little bits of imagination and planning start being an evolutionary advantage long before you get to human-level cognition. They don't have to be perfect. If they're at least as good as a thermostat, they can be useful. And as more and more useful machinery like that gets reinforced into the mind, its behavior gets more and more wantlike.

[\*](#ftnt90_ref) The prevalence of thermostat-like mechanisms is one of the things that makes biochemistry so hard for humans to figure out. If a scientist observes the effect of cold weather on a house with a thermostat, the real causality is that cold weather makes the house lose heat faster, and the thermostat then switches the heater on more often. But the house-biologist, recording statistics, finds that cold weather has no visible statistical effect on the *temperature* of the house; rather, houses in colder weather…consume more natural gas?

Then some other scientist's statistics will show a wide range of fluctuations in natural gas consumed over the course of each winter's day, but no correlated difference in average house temperatures. So *they'll* conclude that there's no reason to suspect that natural gas consumption affects house temperatures either*.* No matter how much natural gas the house consumes, it stays the same temperature (at the bottom of the thermostat's range).

No, but wait! During summer, natural gas consumption drops off a cliff, and houses are measurably hotter (at the top of the thermostat's range)! So maybe…burning natural gas in the winter makes houses *colder?*

And that's one reason that medicine is such a giant mess. Thermostat-like processes are *everywhere* in biology, and they can make it tricky to infer what causes what.

[†](#ftnt91_ref) There is an *outside* optimizer — a human engineer — who built the thermostat, and that human engineer had in mind a prediction about what would happen when the thermostat automatically switched on the heater at 70°F. But the thermostat itself does not know this.

Mentally tracking and distinguishing different levels of optimization is a foundational skill for reasoning about AI. When human engineers built Deep Blue, the humans wanted to beat Garry Kasparov in order to gain scientific fame, get promoted inside IBM, and push the frontiers of knowledge; Deep Blue searched the tree of possible chess moves and steered the chessboard. One would be confused if one thought the human engineers were searching the chess game tree themselves or that Deep Blue wanted the humans to become famous.

A thermostat selects on-off codes to a heater such that it keeps a house within a narrow temperature range; a human engineer selects components such that they form a thermostat.

Similarly, natural selection selects genes such that, in the past, they built biochemistry that kept the organism alive. In a new and different environment, those biochemical feedback loops can kill the organism, and the chemicals and genes themselves will not think about what they are doing.

#### Notes

[1] *skipping the investigation:* A version of this anecdote that spread among computer scientists before the modern internet was based on a later retelling by an engineer who left out Fabre's caveat on how wasp colonies of the same species varied in ability to change behavior. See "[The](https://pure.rug.nl/ws/files/13139017/2012_Keijzer_Sphex_story.pdf) *[Sphex](https://pure.rug.nl/ws/files/13139017/2012_Keijzer_Sphex_story.pdf)*[story: How the cognitive sciences kept repeating an old and questionable anecdote](https://pure.rug.nl/ws/files/13139017/2012_Keijzer_Sphex_story.pdf)" for details.