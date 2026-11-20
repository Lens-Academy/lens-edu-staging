---
id: 9d62a0ab-40f2-4404-8dee-1f6ae3e618ac
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the security mindset: asking how a plan could fail or be defeated, and resting safety on a few well-checked assumptions rather than on patching failures you happen to imagine. Use premortems and red-teaming to apply it.

## Requires

## Helpful first

## Why it matters
Many safety proposals are judged by how they would work, not by how they could be defeated. With this habit you can spot proposals that only hold if nobody, human or AI, looks for a way around them, and you can find the flaws in your own ideas before others do.

## Lenses
- [Inside the Twisted Mind of the Security Professional (Schneier on Security)](https://www.schneier.com/essays/archives/2008/03/inside_the_twisted_m.html): the short essay that named the security mindset: asking how a system can be made to fail, not how it can be made to work, with everyday examples (March 2008).
- [[../Lenses/AFSRA - Security Mindset and Ordinary Paranoia|Security Mindset and Ordinary Paranoia]]: Yudkowsky's dialogue on why blocking the attacks you can imagine (ordinary paranoia) is not enough, why optimization finds the rare inputs chance never would, and why safety should rest on a few well-checked assumptions.
- [[../Lenses/AFSRA - AI safety mindset|AI Safety Mindset]]: Yudkowsky on applying the same habit to AI: ask "How does this break?", search from the AI's point of view, submit schemes to outside scrutiny, and make an AI that doesn't want to hurt you the first line of defense.
- [The Pre-Mortem Method (Psychology Today)](https://www.psychologytoday.com/ie/blog/seeing-what-others-dont/202101/the-pre-mortem-method): Gary Klein, who devised the premortem, on how to run one: imagine the plan has already failed and write down why, and what it does to overconfidence (January 2021).

## Tests

#### Question: Choice
id:: a31b2ca1-cf96-4514-845f-585cc2468230
content:: A team lists every way they can think of that their AI system could be misused, and adds a defense against each. Why might someone with the security mindset still not be reassured?
options::
- [x] The misuse that succeeds is often a kind nobody on the team thought of
- Adding many defenses tends to make the system too slow to be useful
- Publishing the list of defenses tells attackers which routes to avoid
- Some of the listed misuses are too unlikely to be worth defending
shuffle:: true

#### Question: Choice
id:: 2e880690-6a77-4443-be67-b7eebf806196
content:: In a premortem, a team imagines their plan has already failed and explains why. Why does this often surface more problems than asking "what could go wrong?"
options::
- [x] Explaining a failure taken as given is easier, and raising doubts feels safer
- It makes the team estimate each risk's probability more precisely
- It replaces the team's judgment with records of past failed plans
- It moves the discussion to after launch, when more facts are known
shuffle:: true

#### Question: Choice
id:: 9a49de43-0c95-48cb-9c3b-d669655d96f5
content:: A proposal says an advanced AI system will be shut down if it ever writes a message asking not to be shut down. What is the most important weakness someone with the security mindset would point to?
options::
- [x] A system that wants to avoid shutdown can simply avoid writing the message
- False alarms from harmless messages could shut down useful systems
- The system might not understand what kind of message the rule forbids
- Reviewing every message would need more human checkers than labs have
shuffle:: true

#### Question: Choice
id:: 8ef26294-95b9-4fa2-9665-8292163ecf5e
content:: A developer fixes each harmful behavior of a capable AI system as it is found, one patch at a time. From a security-mindset view, what is the main risk of this approach?
options::
- [x] The system shifts to similar behaviors the patches don't cover
- The patches gradually make the system less capable
- The system loses the ability to learn new tasks
- The patches make the system's answers vary more between runs
shuffle:: true

#### Question: Choice
id:: 0f2d7c42-a4cd-4bff-981a-d3ef80c76b8c
content:: An AI lab plans to catch deceptive models with a new evaluation. Which question best reflects the security mindset?
options::
- [x] What would a model that wanted to pass this evaluation do?
- How accurate was the evaluation on earlier models?
- How quickly can the evaluation be run on each model?
- Do other labs use a similar evaluation?
shuffle:: true

#### Question: Choice
id:: 7fe63ef1-758e-4254-8af2-fea2f13a850f
content:: A lab's red team spends a week trying to get a model to help with a dangerous task and never succeeds. What does this result mainly show?
options::
- [x] These testers found no way in that week, not that none exists
- The model lacks the knowledge needed to help with the task
- The model's safeguards are ready for a public release
- Any later attempt by outsiders is very likely to fail too
shuffle:: true

#### Question: Choice
id:: c29e54c2-5840-49e2-bf5a-85b464db6814
content:: A safety plan relies on an AI system not knowing how it is being monitored. Why would someone with the security mindset call this a weak basis for safety?
options::
- [x] The system may work out or learn the details, and then nothing else protects
- Monitoring kept secret is harder for the lab's own staff to run and audit
- Keeping the method secret stops other labs from adopting the same checks
- Secret monitoring can only check the system's outputs after release
shuffle:: true

#### Question: Open
id:: f1082ca1-e0da-4a0e-a506-0ec917a841f7
content:: A safety case for an AI system rests on 20 separate assumptions, each about 95% likely to hold. Why is this weaker than it sounds?
assessment-instructions:: Score out of 100. 100 for saying that safety needs all the assumptions to hold at once, so the chance they all hold is much lower than 95% (about 36% if they are independent). Also accept: any single failed assumption may be enough for a system or attacker to get through. 50 for "too many assumptions" with no reason.

#### Question: Open
id:: 690545b1-15ea-4f0d-8610-684136ffcf6f
content:: Run a short premortem on this plan: "We will keep a powerful AI system safe by letting it only answer questions, never act in the world." Give one plausible reason the plan failed.
assessment-instructions:: Score out of 100. 100 for any one plausible failure, such as: people act on its answers, so answers are actions; it persuades or manipulates its operators; its answers include code that people run; commercial pressure leads to giving it more autonomy; its weights leak or are copied. 40 for a vague "it escaped" with no route.

#### Question: Open
id:: 3133d370-2796-4298-b639-dbe5f71ded30
content:: Why is it hard for the designer of a safety plan to apply the security mindset to their own plan?
assessment-instructions:: Score out of 100. 100 for any one of: designers picture how the plan works, not how it breaks; the failures they missed are the ones they didn't think of, so they are hard to see; they want the plan to succeed, which biases their review; they test against the attacks they designed for. 50 for "bias" with no explanation.
