---
id: 7bbca2ed-bf9c-4b88-ab88-7be89eae4951
parent-concepts:
  - "[[Security mindset]]"
---
Rare failure states that random inputs would almost never reach become likely when an optimizer (an adversary, or the AI itself) is selecting for them, so 'only a tiny part of the space is bad' gives no safety.

## Relationships

### [[../Lenses/Worst-Case Thinking]]
Tier 2: Separates being optimized against from selecting over a mostly-bad space, with the deceptive-alignment case. Shlegeris agrees that when an AI optimizes against you, a few remaining bad strategies are enough to lose, but SGD is not adversarial, so what matters is how common bad models are. Links Garrabrant's 'Optimization Amplifies'; a clear corrective to conflating the two.

### [[../Lenses/Security Mindset and Ordinary Paranoia]]
Tier 2: Plain statement: random inputs never hit a rare failure, but an optimizer searching for it will find it. Coral adds that 'what matters isn't so much the adversary part as the optimization part', which links the idea to AI as well as hackers. Two short exchanges early in a long dialogue; the rest is about security mindset.
