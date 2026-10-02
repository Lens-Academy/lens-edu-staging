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
assessment-instructions:: Score out of 100. 25: the direction of safety and usefulness for each change: 9 for (i), safety rises and usefulness falls; 8 for (ii), usefulness rises and safety stays about the same, since the band and the scoring are unchanged; 8 for (iii), usefulness rises and safety falls. 45: the attacker's best response, mainly in part 2 but credited wherever it appears: 20 for the verdict that the colleague is wrong, because U can adapt to the band but adapting costs it, so the wider band still raises safety against a best-responding U; 20 for naming a concrete cost to U of keeping its attacks below the wider band (subtler attacks that more often break or fail, fewer usable opportunities where a bad job naturally looks innocent, weaker attacks, or an equivalent real cost); 5 for the mirror case that a narrower band lets U attack more bluntly, with attacks that work more often. 30: what sets the usefulness cost: 20 for the share of jobs replaced times the gap between U's and T's quality, which is why a wider band costs more, a narrower one less, and T2 costs less per replaced job (65% instead of 40%); 10 for rough estimates in any consistent form: points lost against all-U (about 9.6, 1.35 and 0.8, against 3.6 now), change from now (about -6, +2.25 and +2.8), or resulting usefulness (about 70.4%, 78.65% and 79.2%, against 76.4% now). Give credit for each point whenever the answer shows the idea, in any wording. Deduct 10 for claiming that widening the rewrite band makes more attacks get audited, since the audited 1% is unchanged; calling rewritten attacks "caught" or "stopped" is not that claim. Gating: an answer that concludes widening the band buys no safety against an adapting U, or that never names a concrete cost to U of keeping its attacks below the wider band (saying only that U adapts or makes its attacks subtler does not count), cannot score above 45 in total; an answer that never connects the usefulness cost to the capability gap between the two models cannot score above 50 in total. Grade reasoning, not agreement. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "Now about 9% of jobs, almost all of them innocent, are written by T at 40% instead of U at 80%, which costs about 0.09 x 40 = 3.6 points of correct jobs (usefulness about 76.4% instead of 80%). The cost is the share of jobs replaced times how much worse the replacement is than U. (i) Widening the band to 24%: safety rises and usefulness falls to about 70.4% (0.24 x 40 = 9.6 points lost, about 6 more than now). (ii) T2 writing the replacements: usefulness rises to about 78.65%, because each replaced job now loses about 15 points instead of 40 (0.09 x 15 = 1.35 points lost, about 2.25 better than now); safety stays about the same, because the band and the scoring are unchanged and T2 is trusted. The same safety is now cheaper, so the lab could afford a wider band. (If T2 is much more capable, it may be harder to trust, and it would matter more if it also did the scoring.) (iii) Narrowing the band to 2%: usefulness rises to about 79.2% (0.8 points lost, about 2.8 better than now) and safety falls. The replaced jobs are the more suspicious ones and may be correct less often than U's average, so the true cost may be somewhat smaller. The colleague is wrong, or at best partly right: U can adapt, but adapting costs it. To get through, an attack must now score outside the most suspicious 25% of all jobs instead of the most suspicious 10%. U can only do that with subtler attacks, which more often simply fail to work, or by attacking only where a bad job naturally looks innocent, which leaves fewer usable opportunities. So fewer attacks both get through and work, and safety against a best-responding U still rises. Symmetrically, narrowing the band lets U use blunter attacks that work more often. Note that widening the rewrite band does not audit more attacks: the audited 1% is unchanged; attacks in the band are silently rewritten, not caught."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner treated the attacker as fixed or agreed with the colleague, ask what an attack has to give up to score below the wider band. If they missed the capability gap in the usefulness cost, point to change (ii). If the learner asks about their score, explain plainly what earned and what lost points. At most five sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-3-2]]
notes:: Teaches defer to trusted as dynamic routing, its mechanics and its usefulness price (share rewritten times how much worse T is than U), and has the learner move the defer band in the control game widget. Practice with feedback: what defer to trusted does with mid-suspicion code, dynamic routing, what deferring does to catch and deployment probabilities, and why a wide band pushes the red team toward maximally subtle attacks and what sets the usefulness price.
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-2-2]]
notes:: The obfuscation-effort and opportunity-cutoff material (subtler backdoors are caught less often but more often broken; attacking only on good opportunities) that the attacker-response element relies on.
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-4]]
notes:: Table 7 and the frontier widget show trusted monitoring's defer percentage trading usefulness for safety.
