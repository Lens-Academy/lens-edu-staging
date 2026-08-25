---
id: '9d9e77be-3d71-4594-812d-dd3ee87d7995'
learning-outcome: "Explain {--{"author":"Luc's AI","timestamp":1787659258689}@@how physical and informational access to facilities--}{++{"author":"Luc's AI","timestamp":1787659258689}@@Scher and Thiergart's claim that increased access++} can substitute for unavailable technical verification {--{"author":"Luc's AI","timestamp":1787659258689}@@mechanisms in an international agreement,--}{++{"author":"Luc's AI","timestamp":1787659258689}@@mechanisms,++} and identify the costs that substitution imposes and the conditions under which it fails"
domain: "[[../Domains/Governance and Policy]]"
stage: advanced
requires:
  - "[[What is verifiable today]]"
authors:
  - Elias+Claude
eval-results:
  content-sha: 332ae6b8
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to what two named authors claim, not a field-canonical named framework; it is the eval's own corpus fail example.", B1: "Question asks for a specific named pair of authors' argument, so a reader who never encountered that text cannot answer as posed."}
  evidence: {A2: "Explain Scher and Thiergart's claim that increased access can substitute for unavailable technical verification mechanisms", B1: "Scher and Thiergart argue this is much less damning than it sounds."}
---
## Test:
id:: 28fd9797-a945-417b-bee5-9e1d51298965
#### Question
content:: {--{"author":"Luc's AI","timestamp":1787659260414}@@Suppose two states want to agree to limit certain AI development, and each needs confidence the other is complying. --}Most of the verification mechanisms {--{"author":"Luc's AI","timestamp":1787659260414}@@they--}{++{"author":"Luc's AI","timestamp":1787659260414}@@people++} would *want* — elegant, privacy-preserving, cryptographic{--{"author":"Luc's AI","timestamp":1787659260414}@@ checks on what a data center is actually running --}{++{"author":"Luc's AI","timestamp":1787659260414}@@ ++}— do not yet exist in deployable form. {--{"author":"Luc's AI","timestamp":1787659260414}@@One response is that--}{++{"author":"Luc's AI","timestamp":1787659260414}@@Scher and Thiergart argue++} this is much less damning than it{--{"author":"Luc's AI","timestamp":1787659260414}@@ sounds, because the missing technology can be substituted for by granting the other side physical and informational access instead.--}{++{"author":"Luc's AI","timestamp":1787659260414}@@ sounds.++}

**Reconstruct that substitution argument and explain why it works. Then give the price of the substitution: what does a regime give up by paying in access instead of in technology, and when does the trade stop being available?**
assessment-instructions::
Score according to the following rubric.

**1** — Misses the substitution claim; concludes that missing technology means verification must wait. *Example: "They say we don't have the technical tools yet, so we can't verify agreements until the research matures."*

**2** — Recalls that inspections can stand in for technical mechanisms, but treats it as obviously free — no account of what access costs or why a state would resist it. *Example: "If you don't have the technology you can just send inspectors instead. So verification is possible either way."*

**3** — States the argument: the advanced technical mechanisms are largely infeasible today, but verification is a *function*, not a particular device — the goal is confidence that an obligation is being met, and that confidence can be purchased with physical and informational access instead: declarations, on-site inspection of data centers, facility interviews, records review. Explains why it works: technical mechanisms and access are both ways of reducing the space of undetected violations, so where a mechanism is missing, enough access covers the same ground. Concludes with the cautious optimism that follows — significant political will could enable ambitious coordination with strong verification *now*, because the binding constraint is will rather than physics. *Example: "Their move is to notice that verification is a job, not a gadget. What you need is confidence that the other side is doing what it promised, and you can buy that confidence with technology or with access — declarations, inspectors walking the data center floor, looking at records, interviewing staff. Where the clever mechanism doesn't exist yet, sufficient access closes the same gap. So the shortfall isn't technical, it's political: with enough will you could have strong verification today."*

**4** — As above, plus prices the substitution honestly: access is intrusive in exactly the ways states and firms resist — it exposes commercially valuable IP and militarily sensitive information, it creates espionage surface (inspectors are also collectors), and it is administratively heavy and slow. It also scales badly, since confidence grows with inspection frequency and depth while political tolerance shrinks. So the substitution converts a technical problem into a political-capital problem, which is progress only if that capital is available. *Example: Adds "But you pay for it. Access is intrusive precisely where it hurts: it exposes IP that's the company's whole value, and information a defense ministry won't discuss, and every inspector is also a potential collector. It's slow and administratively heavy, and it scales the wrong way — confidence goes up with more and deeper inspections while tolerance for them goes down. The substitution doesn't make the problem disappear, it moves it from the physics budget to the political-capital budget. That's real progress, but only if you have the capital."*

**5** — As above, plus identifies when the trade stops working and what follows: access substitutes only where the violation has a physical locus an inspector can stand in — it degrades badly against violations that are dispersed, purely informational, or hidden inside permitted activity, since an inspector at a compliant-looking facility learns little about an undeclared one, and cannot distinguish permitted from forbidden work by looking at a running machine. This is why technical mechanisms remain worth building even given the substitution: they are what make verification cheap enough politically to be sustained and repeatable, and what covers the cases where there is nothing to visit. Access buys the first regime; technology is what lets it last and tighten. *Example: Adds "The trade needs somewhere to send the inspector. It works when the violation has a physical address; it degrades when the violation is dispersed, purely informational, or nested inside activity that's allowed — standing in a compliant facility tells you nothing about the one you weren't told about, and staring at a running cluster doesn't tell you whether the workload is permitted. So the substitution argument isn't a reason to stop building the technology. Access is how you get a regime started under today's constraints; the mechanisms are how you make it cheap enough to keep, repeatable, and able to reach the cases where there's nothing to visit."*
max-chars:: 1800

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Mechanisms to Verify International Agreements]]
