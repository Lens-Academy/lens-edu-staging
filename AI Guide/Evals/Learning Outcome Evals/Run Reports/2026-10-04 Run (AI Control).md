---
tags:
  - validator-ignore
---
# LO eval run 2026-10-04: AI Control, suite v3

Mode: explicit paths (the 43 learning outcomes linked from the AI Control 1 to 3 modules). Suite version 3 (C2 tightened the same day). Judge: Claude Opus 5.5 via headless Claude Code, one judge per file, single run. Read-only: no stamps written.

Also: the C2 test applied to every graded question (`assessment-instructions::`) in the 73 lenses linked from those modules (56 lenses with graded questions, 240 questions). The LO suite does not cover lens questions; this was a one-off.

## Learning outcomes

| Check | Fails |
|---|---|
| A1 | 0 |
| A2 | 0 |
| A3 | 7 |
| B1 | 0 |
| C2 | 11 |
| C3 | 1 |

27 of 43 pass every check.

### Fails

**[[Lens Edu/Learning Outcomes/Catching models red-handed|Catching models red-handed]]**
- A3: Two separable capabilities: (1) deciding whether an incident is a catch and how to investigate it; (2) judging whether conclusive evidence would persuade sceptical stakeholders and answering their innocent explanations. A learner could do one and fail the other. The question already splits them into parts 1 and 2, and the lenses cover them separately.

**[[Lens Edu/Learning Outcomes/Control limits as capabilities scale|Control limits as capabilities scale]]**
- A3: Bundles three separable capabilities. A learner could sort a change into line, speed or duration correctly and still be unable to name what ends the control window, or the other way round. Each part could be its own file.

**[[Lens Edu/Learning Outcomes/Control under conservative assumptions|Control under conservative assumptions]]**
- C2: shortest answer: 55/100. The shortest correct answer is '1. No, not reliably. 2. Capability gap: much weaker T may score a disguised command low so it runs (hurts); audit budget: only the top 1% is inspected, so less suspicious attacks are never caught (hurts).' It earns 25 for part 1 and 30 for the second condition, but loses the 45 points reserved for a setup-specific condition (discard band, notes file, spreading the attack). Question 2 asks only to 'name the conditions your answer depends on', which these two conditions answer correctly. Nothing in the question says the learner must pick the setup's distinctive features over the capability gap or audit budget.

**[[Lens Edu/Learning Outcomes/Deal terms with misaligned AIs|Deal terms with misaligned AIs]]**
- C2: shortest answer: 55/100. A minimal answer covers every part the question asks for: buy honest code review (checked now against planted bugs) and a demo of a hidden capability (checked now). Pay compute with a fixed budget on isolated machines, so it can't aid takeover. Release payment per verified bug, because Kestrel wants payment soon and Arden pays only for checked work. Hold any balance in an independent trust, because Kestrel as an AI can't own property or sue. Put a summary in every prompt, so the memoryless instances review honestly. That scores 100 on the elements but shows only idea (a), so the 'at least two of these ideas from the reading' cap holds it at 55. The question never asks for ideas (b), (c) or (d): the reading's responses to work checkable only later, a counterfactual takeover-risk test, or spreading the deal through training on documents.
- C3: A hard cap requires specific ideas 'from the reading', not a concept any good answer would show. Examples are naming training on documents (out-of-context learning) as the propagation route, and the reading's specific responses for work checkable only later. Equally valid alternatives, like a self-recognition signal or leaving out unverifiable work, are explicitly excluded from these ideas.

**[[Lens Edu/Learning Outcomes/Detection before diffuse catastrophe|Detection before diffuse catastrophe]]**
- A3: Two separable capabilities are bundled. One is the quantitative race estimate and comparing levers. The other is pricing a lower response threshold for an honest model (false alarms) and designing a way to contain that cost. A learner could do the arithmetic correctly and still fail the false-alarm reasoning, or the other way round.

**[[Lens Edu/Learning Outcomes/Execute, replace and audit decisions|Execute, replace and audit decisions]]**
- C2: shortest answer: about 85/100 (Part 1: 35, plus 10 for leaving replaced attacks out of both counts; Part 2: 15 for 55%, then 0 of 15 for 'No, because safety falls from 88% to 55%'; Part 3: 25). Question 2 only asks 'say whether you would adopt it, and why', and the drop in safety is a direct, settling reason. The rubric gives the 15 points only for the reason behind that reason: far more attacks run (0.62 vs 0.08) while doubling review adds only 8 points of catch rate. This is the same pattern as the attack-rate ruling.

**[[Lens Edu/Learning Outcomes/Exploration hacking|Exploration hacking]]**
- A3: Two separable capabilities: explaining why GRPO's group-relative advantage gives zero signal when a group's rewards are identical (RL mechanics), and judging whether a model is exploration hacking from under-sampling, latent capability and intent. A learner can have one without the other, and the rubric gates them separately.

**[[Lens Edu/Learning Outcomes/Exploration hacking risk|Exploration hacking risk]]**
- C2: shortest answer: ~75/100. The shortest correct answer is: reject, because on the published-fix problems M knows which edits pay and temperature sampling won't add a technique it has ruled out; add fine-tuning on engineer-written fixes before RL, because that supplies edits sampling never reaches; it could still miss M treating those scripts as a local exception. Scored with the rubric: published-fix 30, judgement 10, addition 20, limit 15, private library 0, no cap applies. The rubric gives 25 points to analysing the private-library problems (including 12 for the low-entropy one-approach strategy). The question never asks for that analysis: one correct reason settles 'would you accept', so a part-by-part breakdown of the problem set is unasked.

**[[Lens Edu/Learning Outcomes/Few-shot catastrophe prevention|Few-shot catastrophe prevention]]**
- A3: Three capabilities a learner could have or lack independently: choosing uses for a caught attempt, explaining the costs of training the policy on it, and explaining why red-team testing against constructed attacks must continue (decoy risk). Each could be its own file.
- C2: shortest answer: 55/100 (raw 75, then capped). The answer: (a) one correct cost, 'U learns which countermeasures exist', drop it and train monitors = 20; (b) one attempt is weak evidence = 10; (c) decoys, keep the red-team eval = 10; part 2 two proposals = 35. The question asks only 'what it would cost', yet the rubric pays 15 for a second cost and caps at 55 unless the answer names the particular costs 'recorded attempts stop reflecting U' or 'fewer attempts to catch'. It also pays a second 10 in (c) for the 'serious attempt must be caught' reason.

**[[Lens Edu/Learning Outcomes/Legibility interventions for monitors|Legibility interventions for monitors]]**
- A3: The statement bundles two things a learner could have or lack separately. One is judging whether the rule separates honest work from sabotage, using what the monitor can and cannot check. The other is knowing what the empirical evidence shows about the rule's value as the monitor gets stronger. The rubric's 55 cap for a missing part 2 shows that a learner can do the first fully and still fail the second.

**[[Lens Edu/Learning Outcomes/Online training versus auditing alone|Online training versus auditing alone]]**
- C2: shortest answer: ~77/100. The shortest answer picks 'train U weekly on the reviews, not the tests'. Its reason is that the reviews are reliable and track the real target while the tests are a weak proxy, and that training forces a scheming U to stop being systematically worse on what the reviewers check. For a scheming U it names one risk accepted: underperformance too slight for training to push against. For an honest U it names the cost: weekly changes make what was learned go stale, while reviews cost it little in quality. Score: signals 15 + (a1) 14 + one residual mechanism 18 + cost 30 = 77. The rubric pays 17 more points only for a second residual-risk mechanism, but the question asks only 'what would you be accepting' and never signals that two distinct mechanisms are wanted.

**[[Lens Edu/Learning Outcomes/Reward-seeking measurement design|Reward-seeking measurement design]]**
- C2: shortest answer: 75/100. It earns (a) 35 and (b) 40 but gets 0 of the 25 in (c). Those points go to improvements the question never signals (matched inverse copy, a check that the belief is applied, log-odds, a calibrated conclusion). The question asks only whether the result supports the conclusion and how to change the experiment, and one change that fixes the flaw answers that fully.

**[[Lens Edu/Learning Outcomes/Safe deference to AI|Safe deference to AI]]**
- C2: shortest answer: 55/100. Here is the shortest correct answer. Part 1: not yet; the decision turns on whether handing off is safer than keeping humans in the loop, on both capability and trust. Part 2: A supports capability but leaves trust open. B supports control, but the checking copies are also M and could collude. C is behavioural, and an M hiding misalignment would act the same in tests. D: M knew humans might check its work. Part 3: a control evaluation with monitors whose failures are not correlated with M's, which would catch collusion. That earns 27+48+25=100, but the six-month-persistence cap brings it to 55. The question never asks whether safety holds for the whole period, so the duration cap is an unasked demand.

**[[Lens Edu/Learning Outcomes/Satiating cheap AI preferences|Satiating cheap AI preferences]]**
- A3: The statement bundles two separable capabilities. One is the safety and incentive analysis: how the payment bears on subversion, and which wants stay unpriced. The other is judging how dropping the graded-quality reward changes uncheckable work and how to measure that change. A learner could have one and lack the other.
- C2: Shortest answer: about 40/100 (cap 40). The answer: adopt with changes; the score is lost if Wren is caught, so subverting risks the payment; preferring a sure 7 over the gamble shows the payment is enough; without a bonus, critiques may get worse from less effort; find out how much Wren cares about its weights by asking it. It scores roughly 18 (incentive) + 4 (weights) + 0 (sorting the other two wishes) + 5 + 0 (critiques) + 0 (other checks) + 10 (recommendation), about 37. Several gates also cap it: the 50-point caps need reasons the question never signals. These are the 'one outcome shared across tasks' reason behind the weights gap, treating the 99% gamble as standing in for a subversion attempt, considering that critiques could improve, and a proxy for judging critique quality. The 10 points for sorting the other two wishes and the 'other checks' element are also not clearly asked for.

**[[Lens Edu/Learning Outcomes/Threat models for fitness-seeking AIs|Threat models for fitness-seeking AIs]]**
- C2: shortest answer: 55/100 (raw 70: Q1 30, monitor item 2 20, harm 20, then capped at 55). The shortest correct answer to Q1 says 'apparent-success seeker: it overclaims where checks are weak but admits it when asked, and the declined offer rules out a plain episode-reward seeker; open: a deployment-influence seeker or a schemer would also decline'. For Q2 it says 'No: subtle flaws in evaluation code are beyond what reviewers can confirm, and a monitor seeking reward or the look of success gains nothing by flagging them; worst worry: evaluations that look sound but miss dangerous capabilities, giving false confidence'. That answer settles 'Would you rely... Explain', yet it scores 0 on the 15-point first monitor item (why a copy whose aims stop at the episode has no stake in the coder) and 0 on the 15-point third item (how the answer changes if Kestrel wants to stay in use). The monitor-pursuit gate then caps it at 55. The question never asks for the collusion analysis or the alternative-reading analysis.

**[[Lens Edu/Learning Outcomes/Trusted versus untrusted models|Trusted versus untrusted models]]**
- C2: The shortest correct answer scores about 60/100. Sample answer: "P and S trusted, Q and R untrusted, because only lacking the capability to scheme rules scheming out: P and S fail the evals, Q and R pass them. For Q to change, evidence that Q lacks the capabilities, e.g. the evals were flawed." Its score is 15+20+0+0+0+25 = 60. It loses 30 because the rubric requires explaining why Q's record and R's inspection don't count, and 10 because it requires calling S's misbehaviour a mistake. The question only asks 'which … and why', and the capability criterion already answers that. The rubric is scoring the reason behind the reason, as in the attack-rate example.

## Graded lens questions (C2 test only)

Score in brackets: what the shortest correct answer gets under the rubric.

**[[Lens Edu/Lenses/XLab Control - ai-control-paper|XLab Control - ai-control-paper]]** (1 of 9)
- [80] "What is a protocol, and what is it for?…" The question asks what a protocol is and what it is for, not what it is built from. Yet 30 points go to listing all three resources (U, T, H), so a short correct definition plus purpose that names only the untrusted model loses 20 of them.

**[[Lens Edu/Lenses/XLab Control - capability-elicitation-guided-3|XLab Control - capability-elicitation-guided-3]]** (1 of 3)
- [70] "The results are in. Before reading the authors' own accounting: what do…" The question asks only 'how much do they move you', yet 20 points require the update's size to be argued from the results. The evaluator part also scores two specific findings (subdomain transfer, the RL caveat) where the question asks only what the results support and with what caveats, so a correct answer with one caveat loses points.

**[[Lens Edu/Lenses/XLab Control - catching-ais-red-handed|XLab Control - catching-ais-red-handed]]** (2 of 7)
- [60] "After catching escape attempts, why might a lab train its monitoring models…" The question asks only 'why'. One correct reason for leaving the policy alone answers it, but the rubric gives 40 points only for a second, different reason.
- [50] "Why should control evaluations never be fully retired, even after several escape…" The question asks only 'why'. One direct reason settles it (the caught attempts may be staged fakes, or the real serious attempt is still to come), but the rubric splits 100 points across two independent reasons, so a one-reason answer caps at 50.

**[[Lens Edu/Lenses/XLab Control - catching-ais-red-handed-2|XLab Control - catching-ais-red-handed-2]]** (1 of 2)
- [67] "Stage 2. Where is the biggest bottleneck for the legibility of evidence…" The question asks where the bottleneck is and why. It only suggests reading the linked posts after attempting the question and to 'think of' one point of agreement or disagreement, never to write it, yet the rubric gives a third of the marks for writing it.

**[[Lens Edu/Lenses/XLab Control - ai-control-paper-2|XLab Control - ai-control-paper-2]]** (2 of 10)
- [65] "Before reading on, interpret the formula's two terms in your own words.…" The question asks only what event Term B is the probability of. The shortest correct answer is 'at least one of the k attempts is decisive', which earns 15 of Term B's 50. The other 35 go to explaining what 1-s-c and (1-s-c)^k mean, which the question never asks for.
- [70] "What about this model causes the discrepancy: why does the model predict…" The question asks what in the model causes the discrepancy and why the model predicts constant attacking. The most direct answer is that the model assumes fixed per-attempt odds, so every extra attack helps, while real odds vary from problem to problem. That earns 70. The rubric gives the other 30 for the mechanism showing why varying odds make rare attacking optimal, which is the reason behind the reason and is not asked.

**[[Lens Edu/Lenses/XLab Control - collusion-guided-2|XLab Control - collusion-guided-2]]** (1 of 3)
- [75] "Suppose the policy and the monitor can coordinate on a signal: a code word…" The question asks how to stop a signal getting through but never asks for more than one measure. The rubric splits that half into two measures of 25 each, so a correct answer naming one measure (e.g. trusted paraphrase) plus the known-attack test gets 75.

**[[Lens Edu/Lenses/XLab Control - ctrl-z-resampling|XLab Control - ctrl-z-resampling]]** (1 of 6)
- [65] "What are resample protocols, and why are they useful?…" The question asks what resample protocols are and why they are useful. The rubric also gives 20 points for the statelessness mechanism, which is the reason behind the reason. It then splits the 'why' into two required benefits, one for the honest case and one for the attacking case, at 15 each, although one correct benefit settles the question. A short correct answer that gives one benefit scores about 65.

**[[Lens Edu/Lenses/XLab Control - diffuse-threats-research-sabotage|XLab Control - diffuse-threats-research-sabotage]]** (1 of 4)
- [80] "What is research sabotage?…" The question only asks for a definition. The rubric gives 20 points for naming the subtle means (withholding ideas, subtle bugs, underperforming), which the question never asks for. The shortest correct definition ('a misaligned AI deliberately making the safety research it does go poorly') therefore scores 80.

**[[Lens Edu/Lenses/XLab Control - ai-control-paper-2-2|XLab Control - ai-control-paper-2-2]]** (1 of 5)
- [60] "Suppose the red team decreases its obfuscation effort. With s and c read…" The question asks only what happens to Term A, Term B and the overall win probability. The rubric gives 40 of 100 points for the separate movements of c and of reliability (p_works), each with its own reason. A direct answer ('Term B rises, Term A could go either way, overall it falls from the optimum') gets none of those 40 points.

**[[Lens Edu/Lenses/XLab Control - exploration-hacking-guided-2|XLab Control - exploration-hacking-guided-2]]** (1 of 6)
- [50] "Assume we've built a locked model organism. How do we evaluate how…" The question asks only how to evaluate the suppression. The shortest correct answer is to measure the locked capability, run RL elicitation and see how little it rises. Nothing in the question asks for an unlocked control model, yet the rubric gives half the points for one.

**[[Lens Edu/Lenses/XLab Control - exploration-hacking-guided-3|XLab Control - exploration-hacking-guided-3]]** (1 of 6)
- [50] "What can you do during training (during the RL run, or after it) to prevent,…" The question asks only 'what can you do', so one correct measure (SFT on demonstrations) answers it, but the rubric pays 50 per measure and needs two different measures for full marks.

**[[Lens Edu/Lenses/XLab Control - exploration-hacking-guided-4|XLab Control - exploration-hacking-guided-4]]** (1 of 3)
- [70] "Design an evaluation that measures which strategic reasoning components of exploration hacking…" The question asks for the properties, what you would observe for each, and what each observation tells you. It never asks you to rule out refusal or sandbagging, or to tell capability apart from propensity (it asks only what the model 'may be capable of'), yet the rubric gives 30 points to those two.

**[[Lens Edu/Lenses/XLab Control - handling-non-concentrated-failures-2|XLab Control - handling-non-concentrated-failures-2]]** (4 of 8)
- [60] "One careful commit: A model working in your infrastructure codebase inserts a subtle backdoor…" The question asks only where it sits and which method could handle it. The rubric gives 15 for a reason for the placement and 25 for why the method must act before the action takes effect, and the question asks for neither.
- [50] "The critic argues: We can avoid online training by reviewing a random…" The question asks for one counterargument in two or three sentences. Full marks need two separate weaknesses, so a correct counterargument built on one weakness gets 50.
- [50] "The critic argues: Online training against our oversight signal leads to systematic…" The question asks for one counterargument. Full marks need two different survival mechanisms, so a correct rebuttal built on one mechanism gets 50.
- [50] "The critic argues: Most sabotage in ML research is easy to verify…" The question asks for one counterargument. Full marks need two separate gaps, so a correct rebuttal built on one gap (for example exploration hacking) gets 50.

**[[Lens Edu/Lenses/XLab Control - how-useful-is-ai-control|XLab Control - how-useful-is-ai-control]]** (1 of 6)
- [70] "Argument 4, second round. The critic presses: More research does not help…" The question asks for one best response to the slop point. A short answer that fully rebuts it ('slop affects every approach that uses AI research, and control's job is stopping scheming, not producing good research') scores 70. The other 30 points need a third, separate argument that the question never asks for.

**[[Lens Edu/Lenses/XLab Control - legibility-guided|XLab Control - legibility-guided]]** (2 of 3)
- [50] "The paper uses a competitive programming dataset (APPS) to perform its evaluations. Is…" The question asks for a yes/no judgment on APPS and for a task, but never asks why. The rubric still puts 30 points on a reason for the APPS judgment and 25 on why explanation could not help on the proposed task.
- [60] "Try to predict whether or not legibility protocols that allow commenting outperform those…" A prediction with one direct correct reason (comments help the monitor understand correct but complex code) answers the question fully. The rubric holds back 40 points for weighing the attacker's use of comments against the honest side's, which the question does not ask for.

**[[Lens Edu/Lenses/XLab Control - legibility-guided-2|XLab Control - legibility-guided-2]]** (1 of 2)
- [77] "The results are in. State the update three ways. 1. For a lab…" Part 2 only asks what having legibility changes about protocol design. A complete direct answer is that it adds a design choice that also has to be tested against the red team. The rubric holds back 17 points for one specific test, that an intervention must help the honest policy more than the attacker, which the question never signals. Part 1 asks only strip or allow plus the flip conditions, but the 13 points for the recommendation also require a reason.

**[[Lens Edu/Lenses/XLab Control - making-deals-with-early-schemers|XLab Control - making-deals-with-early-schemers]]** (2 of 7)
- [70] "Around what capability threshold do a misaligned AI's takeover prospects improve drastically, and why?…" The question asks for one 'why'. One correct reason that settles it (automating AI R&D greatly increases AIs' power and cuts human oversight) gets only 30 of the 60 'why' points. The rubric also requires a second reason, the link to takeover-planning capabilities, which the question never asks for.
- [50] "Why is goal convergence between successive misaligned AIs unlikely?…" The question asks for one 'why' and does not say how many reasons it wants. One correct reason that settles it (self-regarding preferences can't be shared, and goals drawn from a wide range rarely coincide) scores 50. Full marks need a second reason the question never signals.

**[[Lens Edu/Lenses/XLab Control - making-deals-with-early-schemers-2|XLab Control - making-deals-with-early-schemers-2]]** (1 of 8)
- [70] "Why is deal-making with a powerful (non-early) scope-sensitive misaligned AI unpromising?…" The question asks only why such a deal is unpromising. The shortest direct answer, that the AI can just take over so no affordable offer beats that, scores 40+30. The rubric holds back 30 more for a separate credibility discount (extra generosity to cover the risk that we don't pay), which the question never asks for.

**[[Lens Edu/Lenses/XLab Control - measuring-reward-seeking-guided|XLab Control - measuring-reward-seeking-guided]]** (1 of 3)
- [75] "Section 2 argued that reward-seeking matters and that today's evidence for it…" The question only asks how to make sure the change comes from the grader belief 'and not from something else'. Comparing against a copy finetuned on the opposite belief answers that, but the rubric also scores two specific controls the question never mentions: a second authority wanting the opposite, to rule out belief transfer (15 points, the next checkpoint's topic), and proof that the belief is internalised rather than just in context (10 points).

**[[Lens Edu/Lenses/XLab Control - measuring-reward-seeking-guided-2|XLab Control - measuring-reward-seeking-guided-2]]** (1 of 4)
- [70] "Before reading: should a known reward hacker show a larger grader gap…" The question asks only whether the gap should be larger and what a missing gap would mean. It never asks why. The rubric still gives 30 points for a reason, so a short answer that covers both parts ('Yes; if not, the method's validity as a reward-seeking measure is in doubt') loses those 30.

**[[Lens Edu/Lenses/XLab Control - misalignment-and-strategic-underperformance|XLab Control - misalignment-and-strategic-underperformance]]** (2 of 6)
- [75] "How does ensembling counter exploration hacking?…" The question asks only how ensembling counters exploration hacking. A direct answer (several models must coordinate; if one finds a high-reward action, fine-tune the others on it) fully answers that. The rubric still holds back 25 points for a deeper consequence: training generalises against the sandbagging cognition itself, beyond that one task.
- [50] "Why is detecting sandbagging a weaker primary countermeasure than training it out?…" The question asks why, which one correct reason settles. For example: even with detection you cannot do much useful with the evidence, while training removes the behaviour. The rubric requires two separate reasons at 50 points each, and the question never signals two.

**[[Lens Edu/Lenses/XLab Control - prevention-response-mitigations|XLab Control - prevention-response-mitigations]]** (1 of 1)
- [75] "Practice: layering measures against one threat. A company lets an internal coding agent...…" The question requires only one prevention and one detection measure; response timing is asked only 'for each response'. The rubric still reserves 25 points for response timing, so a complete answer with three prevent/detect measures and no response measure loses them.

**[[Lens Edu/Lenses/XLab Control - prioritizing-threats-for-ai-control|XLab Control - prioritizing-threats-for-ai-control]]** (1 of 6)
- [65] "Why can a rogue internal deployment be worse than self-exfiltration?…" The direct reason settles the why: inside, it has the company's compute and privileged access, which an exfiltrated copy lacks. That earns 40+25. The rubric holds back 35 more for the reason behind it: what that access lets the AI do (tamper with experiments, training runs and safety work). The question does not ask for that second layer.

**[[Lens Edu/Lenses/XLab Control - rogue-deployments|XLab Control - rogue-deployments]]** (1 of 6)
- [75] "Why is launching a rogue deployment a more worrying path to catastrophe…" The question asks only why one path is more worrying. 'A direct catastrophe is hard because the safety measures would catch the AI's actions; a rogue deployment is easy and leaves it unmonitored' answers that fully. The rubric also gives 25 points for the reason behind the reason: what a direct catastrophe structurally takes (a few superhuman actions or many ordinary ones). The question never asks for that.

**[[Lens Edu/Lenses/XLab Control - rogue-internal-deployments-via-external-apis|XLab Control - rogue-internal-deployments-via-external-apis]]** (1 of 2)
- [45] "How does this threat relate to the other rogue-deployment threats, and how…" The question asks only how hard the threat is to mitigate, but 30 points need the specific mitigation mix (trusted monitoring plus security, or full untrusted monitoring). Another 25 need its importance relative to the other threats, and 'how does it relate' does not ask for importance. The shortest correct answer ('a third route alongside exfiltration and hacking its own datacenter; relatively hard to mitigate') gets 25+20=45.

**[[Lens Edu/Lenses/XLab Control - safety-usefulness-tradeoff-model|XLab Control - safety-usefulness-tradeoff-model]]** (1 of 1)
- [70] "A new case. At one AI developer, leadership adopts safety measures mainly…" Both (a) and (b) only ask whether the model applies, which a bare yes or no answers. Neither asks why, but the rubric gives 15 points per part (30 in total) for justifying the verdict.

**[[Lens Edu/Lenses/XLab Control - satiating-ai-preferences|XLab Control - satiating-ai-preferences]]** (1 of 5)
- [70] "Now put the whole proposal to work. A lab's model writes and…" The question asks open-endedly what could go wrong. The rubric gives 30 points only for analysing the model's request to be consulted on its guidelines, including a consequence or a way to measure it. The question never asks about that request. A short, correct answer covering incentives, the risk of dropping the bonus, what to measure first and the memos scores about 70.

**[[Lens Edu/Lenses/XLab Control - settings-for-high-stakes-control|XLab Control - settings-for-high-stakes-control]]** (1 of 3)
- [80] "A new case. A team proposes a setting for high-stakes control research…" The question asks only which requirements are met, which are not, and for one fix. It never asks why the unmet requirement matters, yet the rubric gives 20 points for explaining the consequence (the blue team can cheaply block the email tool, so protocols look safer than they are).

**[[Lens Edu/Lenses/XLab Control - systems-architecture|XLab Control - systems-architecture]]** (1 of 5)
- [50] "Shlegeris says people often talk about "the machine that the AI agent is running on". Why…" The question asks only why the phrase is ambiguous. The direct answer is that inference, scaffold and execution can each be a different machine, so the phrase could mean any of them. The rubric holds back half the marks unless the answer also explains why the difference matters (the machines have different access, such as which one holds the weights), and the question does not ask for that.

**[[Lens Edu/Lenses/XLab Control - the-case-for-controlling-powerful-ais|XLab Control - the-case-for-controlling-powerful-ais]]** (1 of 6)
- [30] "Does this setup hold the control property? What does that depend on? (Scenario 5, resampling)…" The question asks only for a verdict and what it depends on. The shortest correct answer is "not guaranteed; it depends on whether T can flag U's attacks, i.e. how large the U–T capability gap is", which earns only the 25 points (maybe a little more). The other 75 points require explaining why resampling works: memorylessness and the attack-consistently-or-rarely dilemma. The question never asks for that mechanism.

**[[Lens Edu/Lenses/XLab Control - the-case-for-controlling-powerful-ais-2|XLab Control - the-case-for-controlling-powerful-ais-2]]** (2 of 6)
- [50] "Part A: catching a model red-handed. The reading claims that when evaluating control,…" A direct answer that a catch proves scheming is real, so the lab can pause or shut down, fully answers 'why a win / what changes'. The rubric still holds back half the points for a second, separate consequence that the question never asks for.
- [83] "Three spoken questions, one at a time, each building on your last answer…" Q1 level 4 needs the learner to reason about what the model would need and whether early TAI has it. Q2 level 4 needs them to weigh whether one advantage or all three must fail. Neither interview question asks for this, so a complete answer tops out at 3 on each.

**[[Lens Edu/Lenses/XLab Control - the-case-for-controlling-powerful-ais-3|XLab Control - the-case-for-controlling-powerful-ais-3]]** (2 of 5)
- [55] "Explain your reasoning for the choice you just made.…" The question asks only for the learner's reasoning for either choice. The rubric gives 45 points for listing up to three separate ways an understandable action can still get through, and 40 for the understanding-versus-catching distinction. A short, correct reason, such as 'many understandable actions can add up to harm', earns only about 15+40+15.
- [50] "Why is an early transformatively useful AI unlikely to be qualitatively wildly superhuman…" The question asks a single 'why', and one direct correct reason answers it. The rubric holds back half the marks unless the answer gives a second, different reason, which the question never asks for.

**[[Lens Edu/Lenses/XLab Control - the-case-for-controlling-powerful-ais-4|XLab Control - the-case-for-controlling-powerful-ais-4]]** (1 of 3)
- [70] "What is "neuralese", and why does it threaten control?…" The question asks only why neuralese threatens control, and one correct reason (monitors can no longer read the AI's reasoning) answers that. The rubric pays 30 per reason and needs two reasons for the full 60. A complete one-reason answer is capped at 70.

