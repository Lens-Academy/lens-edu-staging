---
title: "How smart could a superintelligence get?"
source_url: https://ifanyonebuildsit.com/1/how-smart-could-a-superintelligence-get
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770634259}@@
  - IABIED--}
---
#### Very smart.

For every bullet in Chapter 1's list of reasons why human brains aren't near the limits of physical possibility, machines *could* get near those limits.

The laws of physics permit the existence of geniuses that think tens of thousands (if not millions or billions) of times faster than humans,[\*](#ftnt18) that never need to sleep or eat, and that can make copies of themselves and trade experiences.

And that's even before we take into account improvements to the *quality* of an AI's cognition.

Even if AI is only strongly superior to humans on one or two dimensions, this may suffice for a decisive advantage. Groups of humans throughout history have repeatedly leveraged relatively small advantages in science, technology, and strategic planning to achieve dominant positions over other groups. Think, for example, of the Spanish conquistadors. And that's without varying significantly in brain architecture or brain size.

Even small intellectual advantages can translate into large practical advantages, and even small advantages can compound extremely quickly. But the likely advantages of AIs look anything but small.

For more arguments that this level of intelligence *matters* — that it could be translated into real-world power — see Chapter 6.

[\*](#ftnt18_ref) We noted in Chapter 1 that computer transistors can switch on and off billions of times each second, while even the fastest biological neurons only fire a hundred times per second. This suggests that on current hardware, even if it took a thousand transistor operations to do the work of one neural spike, AIs could still think 10,000 times faster than a human.

To expand upon the comparison here: This comparison is not meant to be a prediction about how many transistor operations it takes to implement a full simulation of a biological neuron down to the neurotransmitter level (and definitely not down to the level of proteins or atoms). Instead, we're making a point about how quickly the abstract work of human-style thinking can in principle be done — with modern transistors used as a lower bound on one aspect of "What's physically possible?"

To illustrate the point more concretely: There's a naive model of the human brain where, at any given moment in time, each neuron is either firing or not. We can imagine using a large number of transistors to capture this hypothetical "Which neurons are currently firing?" brain state, and then using hard-wired circuitry to implement the transition rules saying which neurons will be firing at the *next* moment in time.

A device like that would run at transistor speeds, but it's probably not sufficiently high-fidelity to actually do the work that a human brain does — neurons *aren't* always either "firing" or "not firing," different neural spikes ramp up and fall off at different speeds. (Also, a brain like this can't learn, because the transition rules are hard-wired.)

The point of the "1,000 transistor operations per neural spike" illustration is: Suppose that it takes *hundreds* of transistors to represent the firing-state of a single neuron (i.e., its "spiking" state at different strengths). Suppose, further, that those hundreds of transistors have to change their state 1,000 different times, in series, every time a neuron spikes (e.g., to represent a pulse with varying strength along its route, where the strength is affected in a dynamic way by 999 different interactions it has along its pathway). In that case, a digital brain will still be able to perform human-style thoughts 10,000 times faster than any human, because transistors can flip 1,000 times in a row, 10,000 times per human neural spike.

These assumptions seem very generous. They're effectively saying, "Suppose that a neuron's spike strength needs to be read off *a thousand times in a row* in order to capture the effect of the spike, with *each reading affecting the next reading in dynamic ways* that can't be shortcut by hard-coded circuitry." Even in that extreme case, using only computing hardware that already exists in 2025, digital minds could still be overwhelmingly faster than biological minds.

This analogy is only talking about the serial fidelity needed to encode the information passed by a neural spike in biological brains; we aren't talking about the computation required to decide whether or not to spike in the first place. As far as we know, there's no consensus among human scientists about how many transistors it takes to simulate a neuron choosing whether to fire, but we would be surprised if the minimum possible serial depth of that graph (with as much circuitry hard-coded as possible) required well over a thousand transistor flips in series. (As a general rule of biological computation, it tends to be much more parallel than serial.)

All of which adds up to the intuitive result that computers can generally perform calculations much, much faster than humans, not too long after humans figure out how to get the computers to do the right sort of computations at all. Which is why, e.g., common calculators are so useful.