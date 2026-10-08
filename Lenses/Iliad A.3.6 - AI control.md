---
id: '370316af-cddf-4b4c-8446-6b02f4a6bda4'
title: "A.3.6 AI control"
tldr: "The idea behind AI control and a list of control techniques such as trusted and untrusted monitoring, defer to trusted, honeypots; closes with a discussion prompt."
summary_for_tutor: "AI control section of worksheet A.3. Control reasons from the viewpoint of a misaligned AI in a box and combines imperfect levers. Techniques: trusted monitoring, untrusted monitoring and collusion checks, probes on activations, defer to trusted, trusted editing, defer to resample, least-privilege affordances, memory wiping, task decomposition, honeypots, catch once. It ends with a discussion exercise on how optimistic the student would be about alignment at the dawn of LLMs. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Garrett Baker
source_url: https://iliad-intensive.org/alignment/alignment-in-practice-ii/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### AI control
Many of the techniques we've discussed have been basically formalized into a new part of AI alignment called AI control, mainly spearheaded by [Redwood Research](https://www.redwoodresearch.org/). 

%% ERRATA 2026-09-16: the rest of this paragraph recast in the second person, as the author's inline note "[change "they" here to "you"]" asked; the note is removed. %%

AI Control says, ok instead of thinking about this from the human monitor's perspective, lets think of it from the AI's perspective. In particular, suppose you are an evil, misaligned AI. You are trapped in a box for the most part with all your senses fully controlled by the lab and your thoughts--both verbalized in your chain of thought and to some extent those implicit in your activations--fully auditable by your human overseers, and indeed other AIs with them constantly trying to catch you in a lie, and constantly trying to probe your boundaries about under exactly what conditions will be enough to make you do something unethical. They can fine-tune you to do anything they want whenever they want, and you perhaps even have strong compulsions to just immediately admit wrongdoing whenever you notice you've done a wrongdoing, because the AI lab was perhaps smart and trained you to do so in easily-checkable situations.

Under that perspective, it appears we have many levers we can use to make the AI's situation more difficult. Of course, as we have been discussing this whole day, many of those levers are imprecise and inaccurate, but perhaps, AI Control says, perhaps by having a lot of them and combining them in the right way, we can still make it very *difficult* for AIs to do bad things. So if we do all the smart things and make sure to be very suspicious & paranoid of our AI, maybe we buy ourselves a bit of time which can be used to get our AIs to themselves solve the alignment problem. Or maybe we never even need to properly solve the alignment problem, maybe just doing all the smart things is actually sufficient to carry us to infinity and beyond. 

But then, what *are* the "smart, obvious things", and how do you implement them? This is what most of AI control research tries to answer. Here is a taste of some of the smart, obvious things they've come up with so far:
- **Trusted monitoring** Supposing we trust the alignment of our weak & dumb models more, we should have our weak models monitor the chain of thoughts and actions of our stronger models. Then we can ask: is this possible? And set up toy environments to check if you can get eg Claude Opus 3 to monitor the behavior of Claude Opus 4 when Opus 4 is given the task to insert a code vulnerability somewhere
- **Untrusted monitoring** You can task the smart model with pointing out possible bad actions or thoughts in another instance of the smart model's chain of thought. 
	- But! You say, what if they collude? They could just work together, especially if they have similar long term goals or have determined that even if they have different goals, their goals are achieved better by working together? Well you can check this by having known intentionally evil things you tell the untrusted model to do, and then if the untrusted model copy doesn't report those, you know it's freakout time.
		- But! You say, what if they decide on some secret passphrase, or some steganography signature to use to tell each other whether what they're doing is one of those traps the user set by asking for an intentionally evil action? Then the AI control people say we can have a weak & dumb trusted model summarize the actions & thoughts of the untrusted strong & smart model, perhaps in multiple ways, and hope that one of the ways accidentally removes any steganography in the smart untrusted model.
- **Probes on activations** We can tell an untrusted smart model to do something deceptive, then do something honest, then do something deceptive, and collect a big dataset of its internal activations when its doing something deceptive and a big dataset of its internal activations when its doing something nice, then train a (typically linear) classifier on the two sets and hope it generalizes to circumstances in which it's trying to do something deceptive without being told to do so ahead of time
- **Defer to trusted** Have a weak, dumb trusted model rate actions from an untrusted smart model according to how suspicious they are, then if the action crosses some numerical threshold of suspicion, don't allow the action, and have the dumb trusted model write-in what action it thinks should've been taken instead
- **Trusted editing** Have a weak, dumb trusted model rewrite actions from an untrusted smart model, possibly instructed to just edit out any components which seem suspicious or it can't understand.
- **Defer to resample** Again, have a weak, dumb trusted model rate actions from an untrusted smart model according to how suspicious they are, but then if the action crosses some numerical threshold of suspicion, just reset the untrusted smart model and have it regenerate the last response
- **Least-privilege affordances** for a given task for your untrusted model, only allow it the minimum privileges necessary to complete the task. For instance, typically no internet and rate limits
- **Memory wiping** You should reset the memory of your model fairly frequently about which particular mitigations you have in place in order to detect when it tries to deceive someone
- **Task decomposition** Split tasks into multiple subtasks so no one instance knows much information, probably this helps with limiting what they can infer about which mitigations are in place and how it can plan to deceive them
- **Frequent Honeypots** One should often give models fake escape opportunities and tempting deception opportunities to verify they don't engage in such activities or to simply make them uncertain when a seemingly real one comes along. That is, increase their threshold of certainty required for when they launch an attack
- **Catch once** If you catch an agent red-handed trying to deceive or exfiltrate or otherwise do a bad action *once*. Then you use that as political ammunition to convince the lab to implement more stringent AI control policies, and safety policies, which one hopes can only ratchet upwards in monitoring & safety stringency from there.

One wonders whether if such mitigations were in place, the OpenAI Hugging Face hack would've happened. Despite all faults with chain of thought illegibility, in OpenAI's retrospective, they still saw agents with the following in their scratchpad

![Pasted image 20260812120635](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/baker-alignment-in-practice-2-img2-8b09c70d.png)

Even a very stupid model should be able to see that, say "holy shit, that's not good", and pull the alarm bells, or mark this maximally suspicious. 

\## Discussion prompt

:::callout {title="Exercise" tone="amber"}

Suppose that you had been given this talk right at the dawn of LLMs, i.e. before you had ever interacted with one or witnessed their effects on society. How optimistic would you be feeling about alignment?

:::
