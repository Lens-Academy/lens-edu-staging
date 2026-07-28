{++{"author":"Elias's AI","timestamp":1785221625009}@@---
id: '9d9e77be-3d71-4594-812d-dd3ee87d7995'
learning-outcome: "Explain Scher and Thiergart's claim that increased access can substitute for unavailable technical verification mechanisms, and identify the costs that substitution imposes and the conditions under which it fails"
domain: "[[../Domains/Governance and Policy]]"
requires:
  - "[[What is verifiable today]]"
authors:
  - Elias+Claude
---
## Test:
id:: 28fd9797-a945-417b-bee5-9e1d51298965
#### Question
content:: Most of the verification mechanisms people would *want* — elegant, privacy-preserving, cryptographic — do not yet exist in deployable form. Scher and Thiergart argue this is much less damning than it sounds.

**What is their substitution argument, and why does it work? Then give the price of the substitution: what does a regime give up by paying in access instead of in technology, and when does the trade stop being available?**
assessment-instructions::
Score according to the following rubric.

**1** — Misses the substitution claim; concludes that missing technology means verification must wait. *Example: "They say we don't have the technical tools yet, so we can't verify agreements until the research matures."*

**2** — Recalls that inspections can stand in for technical mechanisms, but treats it as obviously free — no account of what access costs or why a state would resist it. *Example: "If you don't have the technology you can just send inspectors instead. So verification is possible either way."*

**3** — States the argument: the advanced technical mechanisms are largely infeasible today, but verification is a *function*, not a particular device — the goal is confidence that an obligation is being met, and that confidence can be purchased with physical and informational access instead: declarations, on-site inspection of data centers, facility interviews, records review. Explains why it works: technical mechanisms and access are both ways of reducing the space of undetected violations, so where a mechanism is missing, enough access covers the same ground. Concludes with the authors' cautious optimism — significant political will could enable ambitious coordination with strong verification *now*, because the binding constraint is will rather than physics. *Example: "Their move is to notice that verification is a job, not a gadget. What you need is confidence that the other side is doing what it promised, and you can buy that confidence with technology or with access — declarations, inspectors walking the data center floor, looking at records, interviewing staff. Where the clever mechanism doesn't exist yet, sufficient access closes the same gap. So the shortfall isn't technical, it's political: with enough will you could have strong verification today."*

**4** — As above, plus prices the substitution honestly: access is intrusive in exactly the ways states and firms resist — it exposes commercially valuable IP and militarily sensitive information, it creates espionage surface (inspectors are also collectors), and it is administratively heavy and slow. It also scales badly, since confidence grows with inspection frequency and depth while political tolerance shrinks. So the substitution converts a technical problem into a political-capital problem, which is progress only if that capital is available. *Example: Adds "But you pay for it. Access is intrusive precisely where it hurts: it exposes IP that's the company's whole value, and information a defense ministry won't discuss, and every inspector is also a potential collector. It's slow and administratively heavy, and it scales the wrong way — confidence goes up with more and deeper inspections while tolerance for them goes down. The substitution doesn't make the problem disappear, it moves it from the physics budget to the political-capital budget. That's real progress, but only if you have the capital."*

**5** — As above, plus identifies when the trade stops working and what follows: access substitutes only where the violation has a physical locus an inspector can stand in — it degrades badly against violations that are dispersed, purely informational, or hidden inside permitted activity, since an inspector at a compliant-looking facility learns little about an undeclared one, and cannot distinguish permitted from forbidden work by looking at a running machine. This is why technical mechanisms remain worth building even given the substitution: they are what make verification cheap enough politically to be sustained and repeatable, and what covers the cases where there is nothing to visit. Access buys the first regime; technology is what lets it last and tighten. *Example: Adds "The trade needs somewhere to send the inspector. It works when the violation has a physical address; it degrades when the violation is dispersed, purely informational, or nested inside activity that's allowed — standing in a compliant facility tells you nothing about the one you weren't told about, and staring at a running cluster doesn't tell you whether the workload is permitted. So the substitution argument isn't a reason to stop building the technology. Access is how you get a regime started under today's constraints; the mechanisms are how you make it cheap enough to keep, repeatable, and able to reach the cases where there's nothing to visit."*
max-chars:: 1800

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Mechanisms to Verify International Agreements]]
++}