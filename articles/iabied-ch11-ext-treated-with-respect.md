---
title: "We Know What It Looks Like When a Problem Is Being Treated with Respect, And This Isn't It"
source_url: https://ifanyonebuildsit.com/11/we-know-what-it-looks-like-when-a-problem-is-being-treated-with-respect-and-this-isnt-it
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings{--{"author":"Elias's AI","timestamp":1783770757353}@@
  - IABIED--}
---
AI companies are facing an extraordinarily difficult problem, in a situation where everyone's lives are at stake. Are they at least treating the situation with the gravity it merits?

We can contrast the AI companies with a group of people who *are* competently managing the risks under their purview: air traffic controllers.

The U.S. Federal Aviation Administration [handles](https://www.faa.gov/air_traffic/by_the_numbers) more than three million passengers on over 44,000 flights every day. Over the last two decades, there has been an average of about one fatal accident per year, or about one accident per [twenty million flight hours](https://www.ntsb.gov/safety/Pages/research.aspx).

Postmortem reports on such accidents, like [this one from 2019](https://www.ntsb.gov/investigations/AccidentReports/Reports/AAR2105.pdf) or [this one from 2018](https://www.ntsb.gov/investigations/AccidentReports/Reports/AAR1903.pdf), contain nearly two hundred pages of data, testing, examinations, and investigation details. They catalog the technical design specs for the relevant plane subsystems, pilot and flight attendant employment history, details on the airline and the airport, voice transcripts from the cockpit, and precise weather data from the day, hour, and minute of the accident.

It takes twenty pages merely to summarize the technical analysis performed to determine a probable cause. Here's an excerpt:

> Fan blade No. 13 in the left engine separated due to a low-cycle fatigue crack that initiated in the blade root dovetail outboard of the blade coating. Metallurgical examination of the fan blade found that its material composition and microstructure were consistent with the specified titanium alloy and that no surface anomalies or material defects were observed in the fracture origin area. The fracture surface had fatigue cracks that initiated close to where the greatest stresses from operational loads, and thus the greatest potential for cracking, were predicted to occur.
>
> The accident fan blade failed with 32,636 cycles since new. Similarly, the fractured fan blade associated with the August 2016 PNS accident (see section 1.10.1), as well as the six other cracked fan blades from the PNS accident engine, failed with 38,152 cycles since new. Further, 15 other cracked fan blades on CFM56-7B engines had been identified between May 2017 and August 2019, and those fan blades had accumulated an average of about 33,000 cycles since new when the cracks were detected.

This is what it looks like when a technical profession takes seriously the challenge of averting a disaster.[*](#ftnt268)

Contrast the air traffic control profession with the behavior of AI companies described in Chapter 11.

AI companies are at the stage of spitballing ideas and reciting vaguely reassuring platitudes to journalists and inventors. Superintelligence alignment at these companies is being treated as a game, not a serious engineering discipline — much less a lethally dangerous one.

NASA's requirement for a crewed rocket launch is that it has at most a [1-in-270 chance of killing the crew](https://ntrs.nasa.gov/api/citations/20200001592/downloads/20200001592.pdf), and they take that limit seriously, even though the only people at risk are a crew of volunteers who have accepted the risk. AI labs aren't shooting for a bar that's even remotely close to that stringent, and the technology they're building endangers far more than just volunteers.

The only historical incident we know of where scientists expressed serious concern that some invention might kill *literally everyone* happened during the Manhattan Project. Some scientists expressed the worry that a nuclear bomb might get so hot that it would start fusing the nitrogen in the atmosphere*,* turning the atmosphere into a plasma and killing all life on Earth. Fortunately, they had a good understanding of the physical laws at play, and they could do the calculations. Before doing the calculations, one of the scientists — Arthur Compton — decided he would leave the project if the probability of igniting the atmosphere was any higher than [3 in 1,000,000](http://large.stanford.edu/courses/2015/ph241/chung1/docs/buck.pdf). It was better, he thought, to risk the Nazis beating the allies to the bomb than to risk even a 3 in 1,000,000 chance of turning all the air to plasma by his own hands.

Recall that Sam Altman, *the head of OpenAI*, is on the record [saying](https://blog.samaltman.com/machine-intelligence-part-1):

> Development of superhuman machine intelligence is probably the greatest threat to the continued existence of humanity.

And the head of Anthropic, Dario Amodei, is on the record [saying](https://youtu.be/gAaCqj6j5sQ?feature=shared&t=5882):

> I think I've often said that my chance that something goes really quite catastrophically wrong on the scale of human civilization might be somewhere between 10 and 25 percent[.]

And Elon Musk, the head of xAI, is on the record [saying](https://www.techradar.com/news/elon-musk-warns-ai-is-a-fundamental-risk-to-the-existence-of-human-civilization):

> I think by the time we are reactive in AI regulation, it'll be too late. AI is a fundamental risk to the existence of human civilization.

Don't get us wrong; we think that Amodei's "10 to 25 percent" chance is ridiculously *optimistic*, given how hard the problem is and the fact that humans [can't learn by trial and error this time](/10/a-closer-look-at-before-and-after). But even so, his numbers are *insane*.

Serious safety-critical engineering projects look fundamentally unlike the operations of AI labs. Serious initiatives like NASA, the Manhattan Project, or air traffic control have a lot of knowledge of *exactly* what's going on inside the systems they manage, and they do detailed postmortems of every failure. They treat surprises and oddities as big deals, because they know that catastrophic failures are often made of lots of minor malfunctions that string together in just the wrong way.

Meanwhile, AIs are emitting [an ever-growing array of warning signs](/4/arent-developers-regularly-making-their-ais-nice-and-safe-and-obedient#ais-steer-in-alien-directions-that-only-mostly-coincide-with-helpfulness), and the labs are just chugging on ahead saying that everything will *probably* turn out fine, somehow or other.

They're not even trying to *fake* the level of respect that air traffic control has for a real safety challenge; they just toss out cheerful guarantees like "[GPT-4 is our most aligned model yet!](https://x.com/sama/status/1635687853324902401)"

Which is nice, in a way, because it makes it easier to see that these companies are not the sort of entities that should be entrusted with solving a problem like ASI alignment.

In anything like the current technical environment — where AIs are grown rather than crafted, and humanity only gets one real shot — no one is in a position to do this safely, no matter how cautious and rigorous their engineering approach is.

But it certainly simplifies matters to see that none of the developers of this technology are being even mildly cautious or rigorous in their safety plans or practices.

[*](#ftnt268_ref) Numerically, air travel is *so* safe that society as a whole might benefit from air traffic control relaxing requirements for things like pilot training and contingency fuel, thereby reducing the cost of flights and inducing more people to fly rather than drive, thereby saving more lives on net.