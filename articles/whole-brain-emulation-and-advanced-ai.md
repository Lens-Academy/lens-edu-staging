---
title: "Whole-Brain Emulation and Advanced AI"
source_url: "https://en.wikipedia.org/wiki/Mind_uploading"
author:
  - "Wikipedia contributors"
published: 2024-01-01
allowUnreachableUrl: true
description: "An overview of whole-brain emulation (WBE) / mind uploading — what it is, the scan-map-simulate pipeline, resolution levels — and its distinctive place in AI safety as a possible route to human-derived digital minds, plus the 'which comes first, WBE or neuromorphic AGI?' tension."
tags:
  - article
---
# Whole-Brain Emulation and Advanced AI

## What is mind uploading?

Mind uploading, formally whole-brain emulation (WBE), is a hypothetical process in which a brain scan is used to emulate a person's mental state in a digital computer. The core premise is that the human mind is largely an emergent property of the information processing of its neuronal network — so if mental function arises from physical and electrochemical processes governed by known physics and biology, those processes could in principle be replicated in a computational substrate.

## Technical architecture and requirements

WBE requires three interconnected components: high-resolution brain scanning, connectome mapping, and neural simulation.

- **Scanning** — e.g. serial sectioning (slicing frozen tissue and imaging each layer with electron microscopy to capture synaptic structure), or non-invasive methods like fMRI/MEG. Current methods lack the spatial resolution for whole-brain mapping.
- **Mapping** — extracting a complete connectivity database of all neural connections (addresses of connected neurons, synapse type, and weight for each of the brain's ~10^15 synapses). Dynamic processes at synapses may not be fully captured by structural imaging alone.
- **Simulation** — enormous compute. The Sandberg-Bostrom roadmap estimates spiking-network-level emulation at ~10^18 FLOPS and ~10^4 TB of memory, with large uncertainty about which level of biological detail is sufficient.

## Resolution levels

Feasibility depends critically on the required simulation granularity, from coarse connectome/population-level models up to molecular-scale simulation of stochastic protein behavior. Each added level of detail raises computational demands exponentially, and the true requirements for running an uploaded mind are hard to quantify.

## WBE and advanced AI development

Within AI safety discourse, WBE occupies a distinctive position: a potential route to digital superintelligence derived from human neurobiology rather than built de novo. Advocates suggest WBE-derived minds might more readily inherit human values and motivations, potentially easing control relative to AGI built from scratch.

But a key tension concerns timelines: which arrives first, neuromorphic AI inspired by brain research, or full brain emulation? Participants at a 2011 workshop estimated an ~85% probability that brain-inspired AI would precede WBE — suggesting that accelerating brain-emulation research might inadvertently accelerate risks from uncontrolled AI by improving reverse-engineering techniques applicable to neural networks and reinforcement learning. Others argue hardware limits would constrain early emulations, buying society time to adapt.

WBE remains almost entirely theoretical; mainstream neuroscience pursues related but distinct goals (connectome mapping, brain simulation for medicine, better neuroimaging) that are valuable regardless of whether full uploading becomes feasible.

---
*Condensed overview; see the [Sandberg & Bostrom WBE Roadmap](https://www.fhi.ox.ac.uk/reports/2008-3.pdf) for the canonical technical treatment.*
