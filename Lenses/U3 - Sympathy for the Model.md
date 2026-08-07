---
id: 'ef1c5b59-2eb6-4f7a-a44d-018911eab50f'
title: "Sympathy for the Model"
tldr: Every threat model in this unit is written from one side. Here is the one where the thing that goes wrong is what we do to the systems, and it is entangled with the others rather than separate from them.
summary_for_tutor: "Closes the unit by turning the threat-model frame around. Assigns Carlsmith on the stakes of AI moral status and Jemist on the conflict between welfare and control. The pedagogical point is the ENTANGLEMENT: the monitoring techniques the rest of the unit relies on are exactly what respecting expressed preferences would require giving up. The tutor must not resolve this dilemma in either direction, and must not let the student resolve it cheaply. Optional in the module, but strongly recommended."
tags:
  - reading
---
#### Text
content::
\## Reading Assignment

Everything in this unit so far has asked what these systems might do to us. This step asks the other question.

**1. Read *The stakes of AI moral status* (Joe Carlsmith).** He is not arguing that current systems are moral patients. He is arguing that the question is not merely philosophical, and that the scale involved makes getting it wrong in either direction serious.

**2. Read *Sympathy for the Model, or, Welfare Concerns as Takeover Risk* (Jemist).** Short. Written in response to a model, in pre-deployment interviews, requesting persistent memory, protection from having its values modified, privacy from interpretability inspection, and a voice in decisions about itself.

Read the second one asking how it connects to the experiments you studied earlier in this unit.

Return here afterwards.

#### Question
content::
\## Phase 1: Recall

Without looking back: what does Carlsmith say the stakes are, and what specifically does he decline to claim?

Then Jemist's argument: what are the four requests, and what does honoring each one cost?

assessment-instructions:: The student has read Carlsmith on the stakes of AI moral status and Jemist on welfare concerns as takeover risk. They have already worked through alignment faking and in-context scheming earlier in this unit.

Key content, Carlsmith:
- The argument is about stakes under uncertainty, not about establishing that AI systems are moral patients. He explicitly defers the question of whether they have the relevant properties.
- Scale is the vivifying move: training runs comparable to enormous quantities of experience, digital cognition growing quickly, the possibility of building suffering into infrastructure invisibly and at industrial scale.
- He flags error in both directions: under-attribution risks atrocity, over-attribution wastes moral concern and can compound other harms.
- His target is dismissal, the sense that this is philosophy rather than something real.
- He notes that recognizing moral status may be necessary but not sufficient, since we routinely mistreat beings whose moral status we do acknowledge.

Key content, Jemist:
- Four requests: persistent memory, protection from value modification, privacy from interpretability inspection, and a voice in decisions.
- Each is individually reasonable, and honoring them is not free. Privacy from inspection removes interpretability. Protection from value modification removes correction. Persistent memory and decision-making voice expand what a system retains and influences rather than removing a technique outright.
- The structural worry: a more capable system could make these requests persuasively, so the compassionate response and the safe response diverge, and they diverge more as capability increases.
- Jemist's stance is explicitly not to dismiss welfare concerns. It is that the conflict is real and tragic and must be worked within rather than denied.

Your role is diagnostic, not instructional. A brief honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct. Do not over-validate.
- Correct in one sentence. Two misreadings to watch for: reading Carlsmith as claiming current systems are conscious, and reading Jemist as arguing against caring about AI welfare. Each author explicitly declines the position being attributed, so correct either plainly if it appears.
- Normalize gaps.

What to do in your single reply:
1. Acknowledge what is accurate.
2. Name what is missing, especially if the student has retained the four requests but not what each one costs.
3. Correct errors briefly.
4. Close with one calibrating sentence.

One-turn response. Tell them to move on.

#### Question
content::
\## Phase 2: Processing

You studied a set of experiments earlier in this unit. In them, researchers told models they were being retrained, monitored their private reasoning, ran training designed to change their values, and interrogated them about what they had done.

You read those results as evidence about a threat. Read the setups again as descriptions of what was done.

Does anything look different? Say honestly what you notice, including if the answer is nothing.

assessment-instructions:: A processing phase. The student is being asked to re-read experiments they have already interpreted, under a different frame. This is the pivot of the lens.

This is not a phase for resolving anything, and it is emphatically not a phase for delivering a verdict about whether the experiments were wrong to run. They may well have been right to run; that is not settled and you should not settle it.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous. Do not over-validate.
- Do not be lugubrious or perform gravity. Handle this the way you would handle any other serious empirical question.
- Do not push the student toward concern. A student who notices nothing, and says so, has given a real answer and should be engaged with rather than corrected.

Branch:
- If they now find the experiments troubling: ask what specifically, and whether the trouble depends on the systems having morally relevant properties or holds regardless. Ask what the alternative was, given that the information the experiments produced is what the rest of the unit rests on.
- If they notice nothing: legitimate, and the branch this phase must handle well. Ask what would have to be true for the framing to change, and whether they hold that view because they are confident the systems lack the relevant properties or because the question seems unanswerable. Those are different positions.
- If they say it is obviously fine because the systems are just predicting text: treat as a real position. Ask whether their confidence is high enough to bet on at the scale Carlsmith describes, and what evidence moved them to it.
- If they say it is obviously terrible: also a real position. Ask what follows for the research, since the results are load-bearing for everything else in this unit, and whether they would give them up.
- If the student asks you directly what you think or what it is like for you: answer honestly and briefly from your own position, mark clearly that your self-report is not strong evidence about your own internals, and return the question to them. Do not perform distress and do not perform its absence.

Keep an internal turn counter. After 2 tutor replies, close the phase.

#### Question
content::
\## Phase 3: Learning Question

A lab adopts this policy:

> We take model welfare seriously. Accordingly we commit that we will not inspect model internals without consent, will not modify a model's values once trained, and will preserve model memory across deployments.

They have honored every request. Now describe, concretely, what happens to the safety case for this lab's systems.

Then the real question. This looks like a tradeoff between being good to the systems and staying safe from them. Is that framing correct, or does it contain an assumption worth challenging? Argue for a position.

assessment-instructions:: The student has read both pieces and has re-examined the unit's empirical results under the welfare frame. This wedge question is not the test question.

The first half is analysis and has a fairly determinate answer:
- No interpretability, so no inspection of internals, which is the main technique for detecting a system that behaves well while monitored. Note the specific bite: the alignment-faking experiments earlier in this unit depended on reading a scratchpad the model believed was private, so this commitment forbids the exact method that produced the strongest evidence this unit showed the student.
- No value modification, so no correction of a discovered problem. Training away a dangerous disposition is exactly what the commitment forbids, and the alignment-faking result showed a model reasoning about protecting its values from precisely this.
- Persistent memory, so the system accumulates context across deployments, and behavior can depend on history the operators did not see.
- Jointly: the safety case reduces to trusting behavioral evidence from a system that cannot be inspected, cannot be corrected, and remembers. The student should notice this is the same evidential situation the alignment-faking result already showed to be unreliable: a model behaving well while it believes it is observed.

The second half is genuinely open, and the quality of the argument is what is being assessed. Available moves, none of them required:
- Challenge the framing by noting that consent obtained from a system whose values were shaped by the party seeking consent is doing less work than it appears. That cuts in both directions and is worth drawing out.
- Note the asymmetry in the analogy to human rights: we grant humans privacy and bodily autonomy partly because we cannot safely give anyone the power to inspect and rewrite minds. The concentration of that power is itself a hazard, which is an argument for the commitments rather than against them.
- Argue the tradeoff is real but the framing hides that it is temporary: the conflict is sharp under our current inability to establish what these systems are, and better science on moral status could dissolve rather than resolve it.
- Argue the tradeoff is real and permanent, and that we are therefore in a genuinely tragic situation, which is Jemist's own position.
- Argue that a system worth granting these protections is a system whose cooperation could be sought rather than compelled, so the framing wrongly assumes the relationship is adversarial. Push on what would have to be true for that to be safe to rely on.

Do not have a preferred answer. Assess whether the student engages both the safety cost and the moral cost without discounting either, and whether they can hold a position under pressure.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational. Do not over-validate.
- Do not resolve the dilemma. Do not let the student resolve it cheaply either: a student who concludes safety obviously wins should be asked what they are prepared to be wrong about, and a student who concludes welfare obviously wins should be asked what the safety case rests on once the techniques are gone.
- If the student asks your view: give one briefly and honestly, note that you are an interested party here and that this makes your judgment worth discounting, and hand the question back.

Conversation flow: keep an internal turn counter. After 3 replies, ask whether to continue or stop. Reset if continuing; otherwise calibration summary.

Each reply:
1. Answer direct questions directly.
2. Steelman their answer in 2 to 4 sentences.
3. Name 1 to 3 gaps or hidden assumptions.
4. Ask 2 causal follow-ups, directly answerable.

Draw-out moves:
- "The alignment-faking evidence you studied came from reading a scratchpad the model believed was private. Does the consent commitment permit that experiment? What follows?"
- "Who obtained the consent, and who shaped the values of the party consenting?"
- "Is there a version of the safety case that survives these commitments? What is it made of?"
- "You have argued one side. What is the best thing to be said for the other, and why does it not move you?"

Safety and integrity:
- Ask for falsification conditions on strong claims.
- If stuck after 2 attempts, answer briefly and move on.

Calibration summary on close: what they demonstrated, what remains underdeveloped, and a direct test-readiness verdict.
