---
id: '181f044a-76cc-4be0-939a-9068fa93739e'
learning-outcome: "For a protocol that replaces an untrusted model's moderately suspicious outputs with work from a weaker trusted model instead of using or auditing them, explain how widening that band raises safety, including how it forces a best-responding attacker into attacks that cost it success (subtler attacks that more often fail, or fewer usable opportunities), explain what sets its cost in usefulness (the share of mostly innocent outputs replaced and the capability gap between the two models), and predict how a change to the band or to the trusted model moves safety and usefulness."
topic: "[[../Domains and Topics/7 AI Control/Control protocols]]"
stage: intermediate
requires:
  - "[[Trusted versus untrusted models]]"
authors:
  - Elias+Claude
---
## Test:
id:: 4533c159-d0ff-4f11-94d6-8545afbbf8f9

#### Question: Open
id:: 84d1b27e-7527-4e61-957c-046423f62a5e
content::
A lab uses a capable model U to write data-pipeline jobs. U may be scheming and knows the protocol. A much weaker model T is trusted. T scores each of U's jobs for suspicion; the most suspicious 1% are audited by a human, and jobs in the next 9% are thrown away and rewritten from scratch by T. All other jobs run as U wrote them. On this task U's jobs are correct 80% of the time and T's 40% of the time.

The lab is considering three changes, one at a time:

(i) Widen the rewrite band so that it covers the 24% of jobs just below the audited 1%.
(ii) Keep the band at 9%, but have a newer trusted model T2, correct 65% of the time, write the replacement jobs. T keeps doing the scoring.
(iii) Narrow the rewrite band so that it covers only the 2% of jobs just below the audited 1%.

1. For each change, say what happens to safety and to usefulness (the share of jobs that end up correct), and explain why. Where you can, estimate the change in usefulness.
2. A colleague objects to (i): "U knows where the band is. It will just make its attacks subtle enough to score below the band, so widening it buys no safety." Is the colleague right? Explain.
placeholder:: Take each change in turn, then answer the colleague
assessment-instructions:: Score 0 to 100. The capability tested is reasoning about the safety and usefulness of replacing moderately suspicious outputs with a trusted model's work. Reference answer. Baseline cost: roughly 9% of jobs, almost all of them innocent, are answered at T's 40% instead of U's 80%, costing about 0.09 x 40 = 3.6 percentage points of correct jobs (usefulness about 76.4% instead of 80%). (i) Widening to 24%: safety rises and usefulness falls, to about 70.4% (about 9.6 points lost in total, about 6 more than now). (ii) T2: usefulness rises to about 78.65% (about 1.35 points lost, about 2.25 better than now), because each replaced job now loses about 15 points instead of 40; safety stays about the same because the band and the scoring are unchanged and T2 is trusted, so the same safety is now cheaper and the lab could afford a wider band. (iii) Narrowing to 2%: usefulness rises to about 79.2% (about 0.8 points lost, about 2.8 better than now) and safety falls. The colleague is wrong, or at best partly right: U can adapt, but adapting costs it. To get through, an attack must now score outside the most suspicious 25% of all jobs instead of the most suspicious 10%; U can only do that with subtler attacks, which more often simply fail to work, or by attacking only where a bad job naturally looks innocent, which leaves fewer usable opportunities. So fewer attacks both get through and work, and safety against a best-responding U still rises; symmetrically, narrowing the band lets U use blunter attacks that work more often. Load-bearing elements: (1) about 25 points: the direction of safety and usefulness for all three changes. (2) about 45 points: the attacker's best response, mainly in part 2 but credited wherever it appears: U adapts to the band, and adapting has a cost (attacks that more often break, fewer usable opportunities, or weaker attacks; any correct account of what staying below the band costs U), so the wider band still raises safety; and a narrower band lets U attack more bluntly. Credit, and do not penalise, noting that subtler attacks are also audited less often, as long as the net conclusion about safety is argued. Accept an argued view that in this setting subtler attacks need not fail more often, if the learner explains another real cost to U of staying below a wider band. Deduct up to 10 points for claiming that widening the rewrite band makes more attacks get audited: the audited 1% is unchanged. Do not deduct for loosely calling rewritten attacks "caught" or "stopped" if the answer does not claim audits increase. Treat T's wrong rewrites as a usefulness cost; credit, do not penalise, a learner who also flags them as a separate risk. (3) about 30 points: what sets the usefulness cost: the share of jobs replaced times the gap between U's and T's quality (noting that the replaced jobs are almost all innocent is credited but not required). Credit rough estimates in any consistent form: total points lost against all-U (about 9.6, 1.35 and 0.8), change from now (about -6, +2.25 and +2.8), or resulting usefulness (about 70.4%, 78.65% and 79.2%). An answer that states the right mechanism without numbers can still earn most of this element. Credit a learner who notes that the replaced jobs may be less often correct than U's average, so the true cost may be somewhat smaller. Gating: an answer that concludes widening the band buys no safety against an adapting U, or that never names a concrete cost to U of keeping its attacks below the wider band (attacks that break or fail more often, fewer usable opportunities, weaker attacks, or an equivalent real cost), cannot score above 45 in total; saying only that U adapts or makes its attacks subtler does not count; an answer that never connects the usefulness cost to the capability gap between the two models cannot score above 50 in total. Accept a learner who notes, for (ii), that a more capable T2 might be harder to trust, or that T2 would matter more if it also did the scoring, as sound reasoning rather than an error, provided they still give the usefulness effect. Do not require any term such as "defer to trusted", "dynamic routing" or "Pareto frontier", or any author's name. Grade reasoning, not agreement. A pass is roughly 60.
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner treated the attacker as fixed or agreed with the colleague, ask what an attack has to give up to score below the wider band. If they missed the capability gap in the usefulness cost, point to change (ii). Do not reveal or discuss the numerical score. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-3]]
notes:: Teaches defer to trusted as dynamic routing, its mechanics and its usefulness price (share rewritten times how much worse T is than U), and has the learner move the defer band in the repeated control game widget. Practice with feedback: what defer to trusted does with mid-suspicion code, dynamic routing, what deferring does to catch and deployment probabilities, and why a wide band pushes the red team toward maximally subtle attacks and what sets the usefulness price.
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-2]]
notes:: The obfuscation-effort and opportunity-cutoff material (subtler backdoors are caught less often but more often broken; attacking only on good opportunities) that the attacker-response element relies on.
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-4]]
notes:: Table 7 and the frontier widget show trusted monitoring's defer percentage trading usefulness for safety.
