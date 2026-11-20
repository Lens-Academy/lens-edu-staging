---
id: 2a7291e2-d25c-4710-baf1-f62a6e3fb824
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main schools of thought within AI safety, including catastrophist and uniformitarian views of how AI will go and the main strategic camps, what each believes, and the disagreements that divide them.

## Requires

## Helpful first
- [[Alignment difficulty debate]]

## Why it matters
Most claims about AI safety come from inside a camp, with its own beliefs about timelines, alignment difficulty and whether coordination can work. Knowing the camps lets you see which beliefs a proposal depends on, tell a careful version of a view from a naive one, and find where people really disagree.

## Lenses
- [[../video_transcripts/far-ai-the-two-cultures-of-ai-safety-catastrophists-vs-uniformitarians-jesse-hoogland-timaeus|The Two Cultures of AI Safety]]: Jesse Hoogland (Timaeus) borrows geology's catastrophist vs uniformitarian split to map AI safety: the core crux (how discontinuous AI progress is), the research styles and communities on each side, the "pause" and "automate safety" meta-strategies, and what each camp is missing. Read from the start up to "So, where does that leave us".
- [[../articles/katzke-ai-governance-needs-a-theory-of-victory|AI Governance Needs a Theory of Victory]]: Convergence Analysis compares three endgames: a global moratorium, an "AI leviathan" in the hands of one well-controlled actor, and defensive acceleration. For each it gives what it assumes, its risks (lock-in, coordination failure, offense outrunning defense) and why the right choice depends on timelines and alignment difficulty. Read the Overview and "Theories of victory for AI governance" (June 2024).
- [My techno-optimism (Vitalik Buterin)](https://vitalik.eth.limo/general/2023/11/27/techno_optimism.html): the essay that named d/acc, arguing for speeding up defensive, decentralised technology and against both racing and handing control to a central AI authority. Read "d/acc: Defensive (or decentralization, or differential) acceleration", "Defense-favoring worlds help healthy and democratic governance thrive" and "So what are the paths forward for superintelligence?" (November 2023).

## Tests

#### Question: Choice
id:: 0251c544-a42b-461f-af36-7256012c376b
content:: In debates about how AI will go, what does a "uniformitarian" view expect?
options::
- [x] AI progress will stay fairly continuous, without sudden large jumps
- A sudden jump in capability could leave no time to fix mistakes
- AI will spread evenly across countries and industries
- AI's harms will fall on every group to the same degree
shuffle:: true

#### Question: Choice
id:: 05345dd2-0338-4f17-b129-9b01b0259d16
content:: Catastrophist views of AI expect a sharp break in how AI develops. Why does this make them less willing to rely on fixing problems as they appear?
options::
- [x] Lessons from weaker systems may not carry over, and one failure may be unrecoverable
- They think today's AI systems are already capable of causing human extinction
- They expect AI companies to hide failures from regulators and the public
- They expect governments to ban frontier AI before any problems appear
shuffle:: true

#### Question: Choice
id:: 576d5dd5-25d7-40c7-b528-1b38e0b270df
content:: Someone with a uniformitarian view expects AI progress to stay fairly smooth. Which concern fits that view best?
options::
- [x] Many small handovers of decisions to AI add up to a loss of human control, with no single crisis
- A system improves itself far past human level within days
- Safety research on today's models will tell us nothing about future ones
- Alignment must be fully solved before the first human-level system is trained
shuffle:: true

#### Question: Choice
id:: fe173578-a2b5-40a3-8fa3-99d69997ac01
content:: Some people argue that the most capable AI should spread widely rather than be held by one government or company, while defensive technologies such as biosecurity and cybersecurity are sped up. What is their main reason for preferring this to tight control?
options::
- [x] Whoever alone holds the most capable AI could abuse that power, with no one able to check them
- Wide access would slow AI progress, giving safety research more time
- Open access lets regulators inspect each model before it is released
- Defensive technologies can only be built with AI that everyone can use
shuffle:: true

#### Question: Choice
id:: 4f897e37-f085-45fa-9377-1fca5524ac86
content:: Some people argue that capable AI should spread widely while defensive technologies are sped up. People who want the most capable AI kept under tight government control often object. What is their main worry?
options::
- [x] Small groups could use widely available AI to cause catastrophic harm
- Spreading AI widely would slow down economic growth
- Spreading AI widely would raise the cost of running each model
- Spreading AI widely would put too many jobs at risk at once
shuffle:: true

#### Question: Choice
id:: dbded685-352d-487d-8c25-a420f6ebfd1b
content:: In the "hand over to aligned AI" strategy, a leading developer builds highly capable AI and relies on it to solve the problems that remain. What must be true for this strategy to go well?
options::
- [x] The developer can align that AI well enough to trust it with high-stakes decisions
- AI progress stays slow enough for governments to regulate each new model
- Model weights are released openly so that no single actor holds an advantage
- Rival countries agree to pause frontier development at the same time
shuffle:: true

#### Question: Choice
id:: 39fdaad1-b23b-45ec-a0d2-30d22cb3516f
content:: Researchers in different AI safety camps agree on a lot. Which of these do they most often disagree about?
options::
- [x] How soon transformative AI arrives and how hard alignment will be
- Whether today's AI systems are getting more capable each year
- Whether a misaligned superintelligence would be dangerous to humanity
- Whether research on making AI systems safe is worth doing
shuffle:: true

#### Question: Choice
id:: f88f15d4-e188-40f3-8867-54993c6ff4e4
content:: A plan aims to spread capable AI widely while speeding up defensive technologies. Critics worry it would hand dangerous capabilities to small groups. Which step answers that worry best?
options::
- [x] Strengthen defenses such as biosecurity before releasing capabilities that help attackers
- Release each new model openly as soon as it is trained, so defenders get it when attackers do
- Let market competition decide which AI tools spread, since useful defensive tools will sell
- Speed up AI progress across the board, so that defensive uses arrive sooner
shuffle:: true

#### Question: FillBlank
id:: 9a761ab4-aec2-4cec-ae21-980462ee4b36
content:: Vitalik Buterin's name for an approach that speeds up technologies favouring defense over attack is {{d/acc|defensive accelerationism|defensive acceleration|decentralized accelerationism|decentralised accelerationism|democratic accelerationism|differential accelerationism}}.

#### Question: Open
id:: 5b0a6f69-1778-44be-bfdc-3a86d6317a36
content:: Critics of putting the most capable AI under government control fear it would concentrate too much power in too few hands. Name one way a careful version of this strategy tries to guard against that.
assessment-instructions:: Score out of 100. 100 for any one of: international rather than single-country control; checks and balances or independent oversight of whoever controls the AI; transparency and accountability rules; limiting what the controlled AI may be used for; sharing the benefits widely. 40 for a vague answer such as "make it fair" with no mechanism.

#### Question: Open
id:: 7a790954-1f4e-463b-bb39-ec5ce05b1bf0
content:: Explain how catastrophist and uniformitarian views of how AI will go differ, and give one way this difference changes which safety strategy someone favours.
assessment-instructions:: Score out of 100. Contrast (60): catastrophists expect one or more sharp breaks, such as an intelligence explosion, where lessons from earlier systems may stop applying; uniformitarians expect fairly continuous progress with feedback along the way. Implication (40), any one of: catastrophists favour getting alignment right in advance, pauses or tight control; uniformitarians favour iterative empirical work, evaluations, AI control or using trusted AI to help with safety research.

#### Question: Open
id:: 42bdac7d-ded0-4b05-bdf9-ddf6d7a78455
content:: Pick one strategy for getting through the arrival of advanced AI: tight government control of the most capable AI, handing hard problems over to an AI the leading developer has aligned, or spreading AI widely while speeding up defensive technologies. Name one belief it depends on that, if false, would most weaken it.
assessment-instructions:: Score out of 100. 100 for a belief central to the chosen strategy, with a word on why. Examples: government control needs governments to coordinate, internationally too, and to stay accountable; handing over needs the developer to align the AI, and check it can be trusted, before rivals overtake it; spreading AI widely needs defenses to keep pace with attacks. 50 if relevant but not central.
