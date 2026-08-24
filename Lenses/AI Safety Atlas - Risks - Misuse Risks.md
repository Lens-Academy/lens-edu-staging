---
id: 93d69503-a5a2-429b-b798-f6fb2c513bed
tldr: "One person with the right tool has never been able to threaten all of humanity, until now. This section walks through how AI hands malicious actors new reach: engineering pathogens, automating cyberattacks, fielding autonomous weapons, and fooling models with adversarial tricks. What happens when the barriers that once kept catastrophic capabilities out of reach start to fall?"
summary_for_tutor: "Examines misuse risks, where humans deliberately use AI to cause harm. Covers four domains: bio risk (AI lowering barriers to designing and producing biological weapons, plus vulnerabilities in DNA synthesis screening), cyber risk (AI-enabled phishing, vulnerability discovery, malware, and shifts in the offense-defense balance), autonomous weapons (lethal autonomous weapons, swarms, erosion of human control, arms-race dynamics, and the consequentialist versus deontological ethics debate), and adversarial AI (runtime attacks like prompt injection, data poisoning and backdoors, and privacy and data-extraction attacks)."
{++{"author":"Elias's AI","timestamp":1787566696865}@@reading_minutes: 28
tutor_minutes: 7
++}title: "Misuse Risks"
---

#### Article
source:: [[../articles/AI Safety Atlas - Risks - Misuse Risks|Misuse Risks]]

#### Text
{++{"author":"Elias's AI","timestamp":1787566699666}@@optional:: true
++}content::
{--{"author":"Elias's AI","timestamp":1787566699666}@@This section moves through four different threat domains in--}{++{"author":"Elias's AI","timestamp":1787566699666}@@Four threat domains, one claim holding them together: technology widens the harm++} a {--{"author":"Elias's AI","timestamp":1787566699666}@@row, so if one of them stayed vague, walk through --}{++{"author":"Elias's AI","timestamp":1787566699666}@@single person can do. Which domain supports that claim least well? Take ++}it {++{"author":"Elias's AI","timestamp":1787566699666}@@up ++}with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Misuse means people deliberately using AI to cause harm, and the section opens by treating technology as an amplifier of intentions: the harm one person can do runs from about 5 people with a rock, to about 250,000 with a nuclear weapon, to potentially all of humanity with transformative AI. Bio risk covers a cost gap (developing a new virus might cost around 100 thousand dollars, a vaccine against it over 1 billion), a drug-discovery model rewarded for toxicity that produced 40,000 potentially toxic molecules in six hours, and a 2023 MIT study where nearly all vendors, including 12 of 13 members of the International Gene Synthesis Consortium, filled disguised orders for 1918 influenza and ricin sequences. The US National Security Commission on Emerging Biotechnology concluded that as of late 2024 AI does not meaningfully raise bioweapon risk beyond what internet search already offers, but the section immediately argues that a snapshot of 2023-era capability says little about future risk, citing 46 experts who put AI matching top virology teams after 2030 when testing found the threshold already crossed, and it also notes that biorisk benchmarks may not capture real-world complexity. Cyber covers AI phishing (65 percent success against 60 percent for human-written, and 40 percent less time to create), agents that autonomously hacked 73 percent of test targets, website attacks costing about 10 dollars per attempt (roughly 8 times cheaper than human expertise), and OpenAI's o3 helping find a previously unknown Linux kernel vulnerability in early 2025, and it concludes the offense-defense balance tilts toward offense. Autonomous weapons covers drones attacking retreating forces in Libya in 2021, loitering munitions used by both sides in Ukraine, the Lavender system where Israeli military officers set the score threshold for targeting, operators who trust machine suggestions under battlefield pressure, and arms-race pressure to cut corners on safety testing. Adversarial AI covers runtime attacks (a panda classified as a gibbon with 99.3 percent confidence, and prompt injection), data poisoning where 0.1 percent of training data was enough to plant backdoors that survive further training, and the finding that robustness against one attack type can raise vulnerability to another.

topics to explore:
- The section opens by claiming technology widens the harm one person can cause. Do the four domains that follow support that claim equally well?
- The section reports that AI did not meaningfully raise bioweapon risk above internet search as of late 2024, and also that experts had already been wrong about virology troubleshooting. How much weight should the first finding carry?
- The cyber part concludes the balance tilts toward offense. Which of its reasons does the section support with the most evidence?
- The section argues human control can be nominal even when a person is formally in the loop. What in the Lavender example and the operator studies supports that?
- Data poisoning needs less access than a runtime attack does. Why, and what does that mean for models trained on data scraped from the web?

Do not preview the misalignment and systemic risk sections in detail, since they come later in the chapter.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.
