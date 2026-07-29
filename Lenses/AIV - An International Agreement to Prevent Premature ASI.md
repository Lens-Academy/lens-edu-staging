---
id: 'c57587a9-975b-457a-bce3-c10ae903c870'
title: "An International Agreement to Prevent Premature ASI"
tldr: "The treaty the mechanisms are for: a US–China-led coalition, a FLOP ceiling, and a ban on research that would undermine the agreement's own verifiability."
summary_for_tutor: "Scher, Abecassis, Barnett and Abeyta's concrete proposed agreement — the reading that gives the course's machinery something to be *for*. Proposal: prevent premature development of artificial superintelligence until it can proceed without catastrophic risk, via a coalition led by the United States and China, a FLOP threshold restricting training scale (permitting current beneficial applications while halting capability advance), and a prohibition on dangerous AI research — that which advances toward ASI or which endangers the agreement's own verifiability. Verification rests on tracking AI chips and monitoring their deployment and usage, given mutual distrust. Crucially candid limitations: effectiveness could diminish as AI advances, and there is not yet political will for such an agreement — though there may be will for measures that build toward it, so Appendix C sets out a staged implementation beginning with confidence-building and transparency measures, mirroring how arms control historically developed. The pedagogical job of this lens is the mapping exercise: which obligations the course's mechanisms serve well (a compute ceiling — quantitative, concentrated, chip-mediated) and which they barely touch (a research ban — no compute signature, small-scale, intellectual). Excerpt covers introduction through 'The Agreement'; the long appendix containing the full treaty text remains collapsed."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Every mechanism in this course verifies *something*. This reading supplies the something.

Scher and co-authors write out an actual agreement: a coalition led by the US and China, a FLOP threshold capping training scale, and a ban on research that advances toward superintelligence — including, notably, research that would undermine the agreement's own verifiability.

Read it as an engineer reads a specification, not as a manifesto. For each obligation, ask the question this course has equipped you to ask: **could I check that?** Keep a running split as you go — obligations your toolkit handles well, and obligations where you have nothing.

Pay attention to the last part of section 4. The authors are unusually honest about what they think will and won't hold.

**Read from the beginning and stop when you reach:**

> A staged approach better mirrors how international arms control agreements have taken place historically, and it allows action to happen today even while the political will for a full agreement does not exist today.

The appendices — including the full text of the agreement itself — are below if you want to see what a real one looks like.

#### Article
source:: [[../articles/scher-an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence]]
to:: "A staged approach better mirrors how international arms control agreements have taken place historically, and it allows action to happen today even while the political will for a full agreement does not exist today."

#### Text
content::
Before the discussion, commit to an answer on one thing.

The authors say there is not yet political will for this agreement. The state-of-play readings said much of the verification is already technically feasible. Put those together: **is the binding constraint here technical or political — and what does your answer say about what someone should work on?**

#### Chat
instructions::
TLDR of what the learner just read:
Scher, Abecassis, Barnett and Abeyta propose an international agreement to prevent the premature creation of artificial superintelligence until AI development can proceed without catastrophic risk. Core provisions: a coalition led by the United States and China; a restriction on training scale via a FLOP threshold, calibrated to allow current beneficial applications while halting capability advancement; and a prohibition on dangerous AI research — research that advances toward ASI, or that endangers the agreement's verifiability. Verification, given mutual distrust, rests on tracking AI semiconductor chips and monitoring their deployment and usage, combined with legal prohibitions and multi-layered oversight. Stated limitations: the framework's effectiveness could diminish with future AI advances; specific failure modes include threat actors outside the agreement and covert state-backed ASI efforts by parties inside it, and leaders may find themselves weighing the risk of a covert project against the risk of nullifying the agreement and building ASI themselves. Critically, there is not yet political will to implement the agreement, though there may be will for measures that build toward it — hence a staged implementation (Appendix C) starting with international confidence-building and transparency measures and escalating to the full agreement, mirroring the historical pattern of arms control.

The learning outcome this serves: map a verification scheme onto a concrete treaty's obligations, and judge where the binding constraint is technical versus political.

Discussion topics to explore:
- Run the mapping properly; this is the main work of the lens. **Well served:** the FLOP ceiling is close to an ideal target — a quantitative bound on an activity concentrated in a few enormous fixed facilities, reachable by chip supply-chain accounting, on-chip mechanisms, data-centre inspection, and workload-level evidence capture. The proposal's own reliance on chip tracking matches what the mechanisms actually deliver. **Poorly served:** the research ban restricts intellectual activity, not a measurable physical quantity. It has no compute signature, can proceed at small scale on legitimate hardware, and falls back on declarations, personnel measures, and whistleblowers. Do not accept "inspections would cover it" — ask what an inspector would look at.
- The reflexive provision is the most interesting clause in the paper: banning research that would undermine verifiability is a tacit admission that the regime's technical foundations can be eroded from underneath it. Ask what kind of research that would be (algorithmic efficiency, distributed training, anything that decouples capability from concentrated compute) and whether banning it is itself verifiable. This usually produces a genuinely uncomfortable moment, which is correct.
- The technical-versus-political judgement they committed to. Hold them to an argument, not a preference. The authors say the will does not exist; the Oxford and RAND readings say much of the verification does. That locates the constraint politically. But then press the follow-up that stops this being a defeatist conclusion: verification research *reduces the political cost* of agreeing — less intrusion, less IP exposure, less espionage surface — so technical work relaxes the binding constraint rather than addressing a different one. The two are coupled, not rival.
- Staged implementation as the practical bridge. Ask why starting with confidence-building and transparency is the historically normal path, and which of the course's mechanisms are usable at the earliest stages.
- The failure modes the authors name — outsiders, covert insiders, and leaders deciding the agreement has already failed — are a reasoning exercise. Ask which of the course's mechanisms addresses which, and which failure mode has no technical answer at all.
- If they think the whole thing is unrealistic, engage seriously: the authors agree about present political will. Ask what would have to change, and whether "unrealistic now" is an argument against building the verification capability or for building it before it is needed.

Check that they can name at least one obligation the toolkit serves well and one it barely touches, and can defend a position on the binding constraint.
