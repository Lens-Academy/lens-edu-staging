---
id: '9ddb06ed-48ed-4b59-a74c-786fd336e8b3'
title: Scoping an anti-ASI policy
summary_for_tutor: "A sorting exercise on the effectiveness versus feasibility plane. The two five-rung scales (effectiveness: Symbolic, Marginal, Meaningful, Strong, Decisive; feasibility: Off the table, Long shot, Heavy lift, Within reach, Already happening) and the eleven anti-ASI policy buckets from self-governance to a coordinated halt, each with a description and a historical parallel, are on the lesson page above the widget as collapsed callouts, so the widget itself is the sort plus one follow-up question. The learner puts every bucket onto a 5 by 5 feasibility x effectiveness grid, then checks. Checking marks each on-the-mark chip with a tick and draws an arrow on the plane from every other chip to the cell the reference has it in, amber and dashed for one rung off, red and solid for further off; there is no separate reveal map and no list of verdicts. Picking a chip after the check shows XLab's rationale for that bucket in the info line under the tray. Chips stay movable: moving one clears its verdict and hides its arrow until the next check. The securitization question unlocks as soon as the learner has checked once: which bucket becomes the design target for verification mechanisms (answer: the coordinated halt; wrong picks get an explanation and can retry). Done means the correct exception was picked. Their current placements and verdicts reach you in the widget-state paragraph. The corners are settled and the middle band is contestable, so accept an argued one-rung deviation. Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Scoping an anti-ASI policy</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "policy-scoping". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --right: #2f6f4f; --close: #b87018; --off: #a8371c;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; margin: 4px 0 6px; }
  h2 { font-size: 18px; }
  p { margin: 0; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.quiet { border-color: transparent; background: transparent; padding: 4px 6px; }
  button.quiet:hover { background: var(--surface); }
  /* No browser focus ring on click; keyboard users get a ring in the course accent. */
  button:focus { outline: none; }
  body.kb button:focus { outline: 2px solid var(--accent); outline-offset: 2px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .lede { color: var(--muted); margin: 0 0 12px; max-width: 44rem; }
  .sr-only { position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px; overflow: hidden; clip: rect(0,0,0,0); white-space: nowrap; border: 0; }

  /* sort phase */
  .sort { display: grid; gap: 20px; grid-template-columns: minmax(0, 1fr) 20rem; }
  .tray { border: 1px solid var(--border); border-radius: 8px; padding: 12px; margin-bottom: 14px; }
  .tray .chips { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 8px; }
  .chip { display: inline-flex; align-items: center; gap: 5px; border-radius: 999px; padding: 4px 10px; font-size: 12px; font-weight: 600; border: 1px solid #cfc9bd; background: #fff; touch-action: none; user-select: none; -webkit-user-select: none; cursor: grab; }
  .chip .cn { color: var(--muted); font-weight: 400; font-variant-numeric: tabular-nums; }
  .chip.is-armed { border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent); }
  .chip.is-dragging { opacity: 0.4; }
  .chip.v-right { border-color: var(--right); box-shadow: 0 0 0 1px var(--right); }
  .chip.v-close { border-style: dashed; border-color: var(--close); }
  .chip.v-wrong { border-color: var(--off); }
  .chip .badge { font-size: 11px; }
  .chip.v-right .badge { color: var(--right); }
  .placeholder { display: inline-flex; align-items: center; border: 1px dashed var(--border); border-radius: 999px; padding: 4px 10px; font-size: 12px; color: #b5b1a8; }
  .info { margin-top: 10px; font-size: 12px; color: var(--muted); min-height: 1.5em; }
  .info b { color: var(--text); }

  .plane { display: flex; gap: 8px; }
  .yaxis { flex: none; display: flex; align-items: center; }
  .yaxis button { writing-mode: vertical-rl; transform: rotate(180deg); border: 0; background: transparent; padding: 0; font-size: 12px; font-weight: 600; white-space: nowrap; }
  .yaxis button:hover { color: var(--accent); background: transparent; }
  .plane-main { min-width: 0; flex: 1; overflow-x: auto; }
  .plane-inner { min-width: 440px; }
  .gridrow { display: flex; }
  .rowlabels { flex: none; width: 64px; display: flex; flex-direction: column; }
  .rowlabels div { flex: 1; display: flex; align-items: center; justify-content: flex-end; padding-right: 6px; text-align: right; font-size: 10px; line-height: 1.2; color: var(--muted); }
  .board { position: relative; flex: 1; min-width: 0; border: 1px solid var(--border); border-radius: 8px; overflow: hidden; background: #fff; }
  .cells { display: grid; grid-template-columns: repeat(5, minmax(0, 1fr)); grid-template-rows: repeat(5, minmax(60px, auto)); }
  .cell { position: relative; border-right: 1px solid var(--border); border-bottom: 1px solid var(--border); padding: 4px; display: flex; flex-direction: column; gap: 3px; min-height: 60px; }
  .cell:nth-child(5n) { border-right: 0; }
  .cell:nth-child(n+21) { border-bottom: 0; }
  .cell.is-corner { background: var(--surface); }
  .cell.is-over { box-shadow: inset 0 0 0 2px var(--accent); }
  .cell.is-armable { box-shadow: inset 0 0 0 1px #cfc9bd; }
  .cell.is-armable:hover { box-shadow: inset 0 0 0 2px var(--accent); }
  .cell .target { position: absolute; inset: 0; border: 0; border-radius: 0; background: transparent; padding: 0; cursor: default; }
  .cell.is-armable .target { cursor: pointer; }
  .cell .target:hover { background: transparent; }
  body.kb .cell .target:focus { outline: 2px solid var(--accent); outline-offset: -2px; }
  .cell .chip { position: relative; z-index: 2; padding: 2px 7px 2px 5px; font-size: 10px; line-height: 1.2; max-width: 100%; }
  .cell .chip .short { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
  .corner { position: absolute; z-index: 3; font-size: 9px; letter-spacing: 0.05em; color: #a19b91; border: 0; background: transparent; padding: 0; cursor: help; }
  .corner:hover { background: transparent; color: var(--muted); }
  .corner.tr { top: 3px; right: 5px; }
  .corner.bl { bottom: 3px; left: 5px; }
  .arrows { position: absolute; left: 0; top: 0; width: 100%; height: 100%; z-index: 4; pointer-events: none; overflow: visible; }
  .arrows .shaft { fill: none; stroke-width: 2; stroke-linecap: round; }
  .arrows .shaft.close { stroke: var(--close); stroke-dasharray: 5 4; }
  .arrows .shaft.off { stroke: var(--off); }
  .arrows .head { stroke: none; }
  .arrows .head.close { fill: var(--close); }
  .arrows .head.off { fill: var(--off); }
  .collabels { display: flex; margin-left: 64px; }
  .collabels div { flex: 1; text-align: center; padding: 6px 2px 0; font-size: 10px; line-height: 1.2; color: var(--muted); }
  .xaxis { margin-left: 64px; text-align: center; padding-top: 4px; }
  .xaxis button { border: 0; background: transparent; padding: 0; font-size: 12px; font-weight: 600; }
  .xaxis button:hover { color: var(--accent); background: transparent; }
  .caption { margin-left: 64px; text-align: center; font-style: italic; color: var(--muted); padding-top: 6px; }

  aside { display: flex; flex-direction: column; gap: 16px; min-width: 0; }
  .stats { border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); padding: 10px 0; display: flex; flex-direction: column; gap: 4px; }
  .stats div { display: flex; align-items: baseline; gap: 8px; }
  .stats b { font-size: 14px; }
  .stats span { color: var(--muted); font-size: 12px; }
  .controls { display: flex; flex-direction: column; gap: 8px; margin-top: 8px; }
  .controls button { text-align: center; }
  .status { text-align: center; font-size: 12px; color: var(--muted); }
  .status b { color: var(--text); }
  .legend { display: flex; flex-wrap: wrap; gap: 4px 14px; font-size: 11px; color: var(--muted); }
  .legend span { display: inline-flex; align-items: center; gap: 5px; }
  .legend i { width: 18px; height: 0; border-top: 2px solid var(--off); display: inline-block; }
  .legend i.close { border-top-style: dashed; border-top-color: var(--close); }
  .legend i.right { width: auto; height: auto; border: 0; font-style: normal; color: var(--right); font-weight: 600; }
  .exc { border: 1px solid var(--border); border-radius: 8px; padding: 12px; background: var(--surface); }
  .exc .lead { color: var(--muted); margin: 6px 0 10px; }
  .exc .lead b { color: var(--text); }
  .exc .term { border: 0; border-bottom: 1px dotted var(--muted); border-radius: 0; background: transparent; padding: 0; font-weight: 500; cursor: help; }
  .exc .term:hover { background: transparent; color: var(--accent); }
  .exc .termtip { font-size: 12px; color: var(--muted); border-left: 2px solid var(--border); padding-left: 8px; margin: 0 0 10px; }
  .exc .opts { display: flex; flex-wrap: wrap; gap: 6px; }
  .exc .opts button { border-radius: 999px; padding: 4px 10px; font-size: 12px; font-weight: 600; }
  .exc .opts button.is-picked.ok { border-color: var(--accent); color: var(--accent); }
  .exc .opts button.is-picked.no { border-color: var(--text); text-decoration: line-through; }
  .exc .answer { border-top: 1px solid var(--border); margin-top: 10px; padding-top: 10px; color: var(--muted); }
  .exc .answer b { color: var(--text); }
  .finished { border: 1px solid var(--accent); border-radius: 8px; padding: 10px 12px; font-size: 12px; font-weight: 600; }
  .dragghost { position: fixed; top: 0; left: 0; z-index: 50; pointer-events: none; border: 1px solid var(--accent); border-radius: 8px; background: #fff; padding: 3px 10px; font-size: 12px; font-weight: 500; box-shadow: 0 1px 2px rgba(0,0,0,0.12); }

  @media (max-width: 900px) { .sort { grid-template-columns: minmax(0, 1fr); } }
  @media (max-width: 600px) { .plane { gap: 4px; } }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Scoping an anti-ASI policy</h1>
<p class="lede">Sort the policy buckets on the feasibility x effectiveness matrix. The scales and the eleven buckets are described above.</p>

<div id="sort-root"></div>
<div id="live" class="sr-only" aria-live="polite"></div>

<script>
  "use strict";
  document.addEventListener("keydown", function (e) { if (e.key === "Tab") document.body.classList.add("kb"); });
  document.addEventListener("pointerdown", function () { document.body.classList.remove("kb"); });

  // ---------- Data (from src/lib/verification/data/policy-scoping.ts) ----------
  var AXIS_SCALES = {
    effectiveness: {
      question: "What is effectiveness?",
      title: "Effectiveness",
      lead: "How much the policy actually deters ASI development, measured against the global race, not against one country’s labs.",
      rungs: [
        { name: "Symbolic", gloss: "Signals concern; changes no developer’s plans." },
        { name: "Marginal", gloss: "Slows the already-willing; the race continues around it." },
        { name: "Meaningful", gloss: "Measurably constrains some frontier development, somewhere." },
        { name: "Strong", gloss: "Binds every major developer inside the regime, with real teeth." },
        { name: "Decisive", gloss: "Stops or hard-caps the race itself, for as long as it holds." }
      ]
    },
    feasibility: {
      question: "What is feasibility?",
      title: "Feasibility",
      lead: "How gettable the policy is under current infrastructure (the verification burden it implies) and the current political climate.",
      rungs: [
        { name: "Off the table", gloss: "No major power would entertain it in today’s climate." },
        { name: "Long shot", gloss: "Imaginable after a crisis or a major shift in threat perception." },
        { name: "Heavy lift", gloss: "A real diplomatic and technical build, but precedents exist." },
        { name: "Within reach", gloss: "States already do this for other dual-use technologies." },
        { name: "Already happening", gloss: "Versions of it exist today." }
      ]
    }
  };

  var BUCKETS = [
    { id: "sg", n: 1, name: "Self-governance (status quo)", short: "Self-gov",
      desc: "Voluntary lab commitments such as RSPs and safety frameworks; no external enforcement, and race dynamics persist.",
      parallel: { title: "Asilomar, 1975", text: "Molecular biologists voluntarily paused recombinant DNA experiments and wrote their own safety guidelines at the Asilomar conference. Self-governance worked for a while because the research community was small and shared norms, but it later hardened into formal NIH rules. The AI parallel: lab commitments can precede regulation, but they historically survive only until commercial pressure or new entrants arrive." },
      key: { f: 4, e: 0 },
      why: "The status quo: already happening, costs nothing, binds no one, and race dynamics run straight over a promise with no enforcement." },
    { id: "ur", n: 2, name: "Unilateral restraint", short: "Unilateral",
      desc: "One state halts or caps its own frontier development alone, hoping others reciprocate.",
      parallel: { title: "US bioweapons renunciation, 1969", text: "President Nixon unilaterally terminated the entire American offensive biological weapons program with no reciprocal commitment from the Soviet Union. The gamble partly paid off, helping produce the Biological Weapons Convention in 1972. The cautionary half: the USSR signed and then secretly expanded its own program (Biopreparat), showing what unilateral restraint risks without verification." },
      key: { f: 2, e: 1 },
      why: "One capital can decide it alone, which is why it is not lower. But surrendering the frontier while rivals race is a heavy political lift, and reciprocity you cannot check is a bet Biopreparat shows how to lose." },
    { id: "dr", n: 3, name: "Uncoordinated domestic regulation", short: "Domestic reg.",
      desc: "Each state licenses, audits, and sets safety requirements for its own developers, with no international layer.",
      parallel: { title: "Human germline editing, 2010s", text: "Countries independently banned, restricted, or left unregulated heritable genome editing, with no international coordination. The He Jiankui affair in 2018 (CRISPR babies, conducted in China partly because oversight gaps existed there) showed the core weakness of a pure patchwork: research migrates to the most permissive jurisdiction." },
      key: { f: 3, e: 1 },
      why: "States license industries all the time, no diplomacy required. But national rules stop at the border, and development migrates to the most permissive jurisdiction." },
    { id: "ti", n: 4, name: "Transparency and information-sharing", short: "Transparency",
      desc: "Incident reporting, model registries, notification of large training runs. The disclosure infrastructure most later options depend on.",
      parallel: { title: "US-Soviet launch notifications, 1988", text: "The Ballistic Missile Launch Notification Agreement required each side to notify the other before ICBM and SLBM test launches. Nothing was limited or banned; the value was purely in reducing surprise and misinterpretation. Training-run notification proposals borrow this logic almost exactly. (Nearest fit, though missile launches are far easier to observe from outside than training runs.)" },
      key: { f: 3, e: 1 },
      why: "Watching is an easier ask than stopping, and it restrains nothing by itself. Its real value is the disclosure infrastructure every stronger bucket stands on." },
    { id: "ep", n: 5, name: "Joint emergency preparedness and response", short: "Emergency prep",
      desc: "Parties jointly detect and respond to computational emergencies such as rogue deployments or loss-of-control incidents. Cross-cutting: compatible with any option below.",
      parallel: { title: "Post-Chernobyl conventions, 1986", text: "Within months of the Chernobyl accident, states negotiated the Convention on Early Notification of a Nuclear Accident and the Convention on Assistance in Case of a Nuclear Accident, obligating rapid alerts and mutual aid when a disaster crosses borders. Notable for AI: the machinery was built only after the emergency demonstrated the need." },
      key: { f: 1, e: 0 },
      why: "Deterrence is not its job: it detects and responds once something has already gone wrong, alongside any other bucket. And historically the machinery gets built right after the first disaster, not before it." },
    { id: "bt", n: 6, name: "Knowledge and benefit transfers", short: "Transfers",
      desc: "In two strands: sharing research, development knowledge, and safety-enhancing technologies; and sharing chips, compute access, completed models or API access, cash, and AI-enabled aid. Both function as side payments that make restrictive regimes acceptable to states asked to forgo development.",
      parallel: { title: "Atoms for Peace, 1953", text: "Eisenhower’s program offered civilian nuclear technology, materials, and training to countries that accepted safeguards, a bargain later written into the NPT as Article IV. Benefit-sharing is what made a discriminatory regime signable for the have-nots. The double edge: some transferred “peaceful” technology later fed weapons programs, including India’s." },
      key: { f: 3, e: 0 },
      why: "Alone it deters nothing: transfers are the side payments that make the restrictive buckets signable. The double edge: the goods that persuade are often the goods that proliferate." },
    { id: "cc", n: 7, name: "Compute controls", short: "Compute controls",
      desc: "Export controls, international chip tracking, and hardware-enabled governance mechanisms restricting who can access frontier-scale compute. Also the enforcement backbone for options 8 through 11.",
      parallel: { title: "Fissile material chokepoint", text: "Nuclear nonproliferation works largely because enriched uranium and plutonium are hard to produce and their supply chains are controllable, policed by the Nuclear Suppliers Group and Cold War-era regimes like CoCom. Advanced chips play the same chokepoint role for AI, with a similar concentration: a handful of firms (TSMC, ASML, NVIDIA) sit where enrichment technology once did." },
      key: { f: 3, e: 2 },
      why: "Chokepoints this concentrated make supply-side control genuinely enforceable, enough to add years to a cheater’s timeline, not to stop the race. Export controls are the part already happening; chip tracking and hardware mechanisms are the build." },
    { id: "br", n: 8, name: "Binding international regulation of development and deployment", short: "Intl regulation",
      desc: "Treaty rules spanning the stack, from data-center training runs down to fine-tuning, inference, and sensitive AI-enabled devices.",
      parallel: { title: "Chemical Weapons Convention, 1993", text: "The CWC regulates an entire dual-use industry rather than banning a single object, with tiered schedules of chemicals, facility declarations, and routine OPCW inspections of commercial plants. It’s the best existing model of intrusive, stack-spanning regulation of a technology that is mostly civilian." },
      key: { f: 1, e: 3 },
      why: "The CWC is the existence proof that a mostly-civilian industry can live under routine international inspection, and between today’s rivals, an AI version is a genuine long shot, not merely a heavy lift." },
    { id: "np", n: 9, name: "Nonproliferation regime", short: "Nonproliferation",
      desc: "A small set of states develops frontier AI under international safeguards and inspections; development prohibited everywhere else.",
      parallel: { title: "NPT and IAEA, 1968 onward", text: "The source model itself. Five recognized weapons states, safeguards inspections for everyone else, and Article IV benefits as the sweetener. The regime mostly held (far fewer nuclear states than Kennedy predicted), but India, Pakistan, and Israel stayed outside it, and North Korea left, so “prohibited everywhere else” was never airtight, and the two-tier structure still breeds resentment." },
      key: { f: 1, e: 3 },
      why: "Judged against expectations the regime mostly held, at the price of a permanent two-tier grievance, and with an exit door North Korea used. For AI, who qualifies as a licensed developer is the fight before the treaty." },
    { id: "jd", n: 10, name: "International joint development", short: "Joint dev",
      desc: "Pooling under a shared institution, covering both joint work toward a shared goal such as defensive AI and confinement of systemically risky development to a single multinational project, prohibited outside it.",
      parallel: { title: "Baruch Plan, 1946", text: "The US proposed placing all dangerous atomic activities under an international Atomic Development Authority with a monopoly on the technology. It failed over exactly the issues a “CERN for AI” would face: the Soviet Union would not freeze itself into second place, and neither side would accept intrusive control before trusting the other. CERN itself shows the pooling half works, but only for science with no military edge." },
      key: { f: 1, e: 4 },
      why: "Pooling among rivals is proven; the monopoly-with-prohibition strand died with the Baruch Plan, because no leader’s rival accepts permanent second place. If confinement held, though, little would escape it." },
    { id: "ch", n: 11, name: "Coordinated halt", short: "Coordinated halt",
      desc: "Binding agreement to stop or hard-cap frontier development, bilateral or broadly multilateral, triggered immediately or by pre-committed if/then conditions.",
      parallel: { title: "Nuclear test moratoria and the CTBT", text: "The US and USSR halted testing by parallel moratorium in 1958, resumed, then progressively banned it (Partial Test Ban 1963, CTBT 1996), backed by a global seismic monitoring network that makes cheating detectable. The apt part: a verified halt of an activity, not a surrender of weapons. The cautionary part: the CTBT never formally entered into force because key states, including the US and China, never ratified." },
      key: { f: 0, e: 4 },
      why: "The strongest instrument on the board and the hardest to get: every major power must stop, and trust that rivals actually stopped. Which is exactly why this track studies verification against it." }
  ];

  var EXC_OPTION_IDS = ["sg", "dr", "ti", "cc", "ch"];
  var EXC_ANSWERS = {
    ch: { ok: true, lead: "Right: the coordinated halt.", t: " Mechanisms strong enough to verify a halt (chip registries, compute metering, inspection rights) can support every weaker bucket. The reverse is not true. So under the securitized framing you design verification for the pause, whatever gets signed first." },
    cc: { ok: false, lead: "", t: "Compute controls are the enforcement backbone, not the target; the question securitization asks is what that backbone must be strong enough to hold up. Design it for the halt and it serves every weaker bucket on the way." },
    ti: { ok: false, lead: "", t: "Transparency is the scaffolding, not the target. Under a securitized framing you build the mechanism set that could support a halt; transparency is what it stands on along the way." },
    dr: { ok: false, lead: "", t: "Securitization is precisely the move past ordinary domestic politics. A domestic design target leaves the existential problem, the international race, unsolved." },
    sg: { ok: false, lead: "", t: "If you truly accept the existential framing, “trust me” is the one answer ruled out from the start. Verification exists to replace it with “check me.”" }
  };

  var AXIS_TIPS = {
    y: "How much the policy actually deters ASI development, measured against the global race, not against one country’s labs.",
    x: "How gettable the policy is under current infrastructure (the verification burden it implies) and the current political climate.",
    tr: "High effectiveness at high feasibility is the policy everyone would already have adopted. Nothing lives here.",
    bl: "Costly to get and weak once you have it. If a bucket seems to belong here, one of your axis readings is off.",
    sec: "Securitization: treating an issue as an existential security matter, lifting it out of normal political balancing, because nothing can be traded against survival. A strong move with a history of abuse, which is why the threat model must be argued, not stipulated."
  };

  var C = {
    cardParallelTag: "Historical parallel",
    trayLabel: "The eleven policy buckets: drag onto the plane, then check",
    stats: [
      { n: "11", l: "buckets, from voluntary commitments to a coordinated halt" },
      { n: "2", l: "axes every scoping decision trades between" },
      { n: "1", l: "exception that suspends ordinary balancing" }
    ],
    exerciseLabel: "Exercise",
    checkBtn: "Check placements",
    resetBtn: "Reset the sort",
    legendRight: "on the mark",
    legendClose: "one rung off",
    legendOff: "further off",
    yTitle: "Effectiveness",
    ySub: "at deterring ASI development",
    xTitle: "Feasibility",
    xSub: "verification burden + political climate",
    caption: "Always think about policy in terms of tradeoffs: price them, don’t pick favorites.",
    cornerTR: "the empty corner",
    cornerBL: "worst of both",
    excLabel: "The one exception",
    excLead: {
      pre: "Ordinary balancing weighs effectiveness against feasibility. ",
      sec: "Securitization",
      mid: " breaks the scale: if ASI development is an existential threat, nothing can be traded against survival. Accept that framing, and one bucket becomes the ",
      bold: "design target for verification mechanisms",
      post: ". Which?"
    },
    finished: "Correct. Exercise complete."
  };

  var COLS = [0, 1, 2, 3, 4];
  var ROWS = [4, 3, 2, 1, 0];
  var BY_ID = {};
  BUCKETS.forEach(function (b) { BY_ID[b.id] = b; });

  // ---------- Helpers ----------
  function el(tag, cls, text) {
    var e = document.createElement(tag);
    if (cls) e.className = cls;
    if (text != null) e.textContent = text;
    return e;
  }
  function btn(cls, text, id) {
    var b = el("button", cls, text);
    b.type = "button";
    if (id) b.id = id;
    return b;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }
  function parseCell(cell) { return { f: Number(cell.charAt(1)), e: Number(cell.charAt(3)) }; }
  function cellKey(f, e) { return "f" + f + "e" + e; }
  function verdictFor(b, f, e) {
    var dist = Math.max(Math.abs(b.key.f - f), Math.abs(b.key.e - e));
    return dist === 0 ? "right" : dist === 1 ? "close" : "wrong";
  }
  function verdictLabel(v) { return v === "right" ? "on the mark" : v === "close" ? "close" : "off"; }
  function cellLabel(cell) {
    if (!cell) return "the tray";
    var p = parseCell(cell);
    return "feasibility “" + AXIS_SCALES.feasibility.rungs[p.f].name + "”, effectiveness “" + AXIS_SCALES.effectiveness.rungs[p.e].name + "”";
  }
  function nudge(b, cell) {
    var p = parseCell(cell), parts = [];
    if (b.key.f > p.f) parts.push("more gettable than you have it");
    if (b.key.f < p.f) parts.push("harder to get than you have it");
    if (b.key.e > p.e) parts.push("stronger than you have it");
    if (b.key.e < p.e) parts.push("weaker than you have it");
    return parts.join(", and ");
  }

  // Seeded shuffle (port of src/lib/shuffle.ts): FNV-1a seed, mulberry32, Fisher-Yates.
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) { h ^= seed.charCodeAt(i); h = Math.imul(h, 0x01000193); }
    return h >>> 0;
  }
  function prng(state) {
    return function () {
      state = (state + 0x6d2b79f5) | 0;
      var t = state;
      t = Math.imul(t ^ (t >>> 15), t | 1);
      t ^= t + Math.imul(t ^ (t >>> 7), t | 61);
      return ((t ^ (t >>> 14)) >>> 0) / 4294967296;
    };
  }
  function seededPermutation(seed, n) {
    var order = [], i;
    for (i = 0; i < n; i++) order.push(i);
    var rand = prng(hashSeed(seed));
    for (i = n - 1; i > 0; i--) {
      var j = Math.floor(rand() * (i + 1));
      var tmp = order[i]; order[i] = order[j]; order[j] = tmp;
    }
    return order;
  }
  var EXC_ORDER = seededPermutation("policy-scoping:exception", EXC_OPTION_IDS.length).map(function (i) { return EXC_OPTION_IDS[i]; });

  // ---------- State ----------
  var S = {
    placements: {},
    checkedOnce: false,
    excPicked: null, excDone: false
  };
  BUCKETS.forEach(function (b) { S.placements[b.id] = { cell: null, verdict: null }; });
  var ui = { armedId: null, info: null, completedSent: false };
  var STORAGE_KEY = "lens-widget-policy-scoping";

  function say(msg) { document.getElementById("live").textContent = msg; }

  function placedCount() { return BUCKETS.filter(function (b) { return !!S.placements[b.id].cell; }).length; }
  function verdicts() { return BUCKETS.map(function (b) { return S.placements[b.id].verdict; }); }
  function allVerdicts() { return verdicts().every(function (v) { return !!v; }); }
  function rightCount() { return verdicts().filter(function (v) { return v === "right"; }).length; }
  function closeCount() { return verdicts().filter(function (v) { return v === "close"; }).length; }
  function allRight() { return allVerdicts() && rightCount() === BUCKETS.length; }
  function excUnlocked() { return S.checkedOnce; }
  function refCell(b) { return cellKey(b.key.f, b.key.e); }
  function offList() {
    return BUCKETS.filter(function (b) {
      var p = S.placements[b.id];
      return !!p.cell && (p.verdict === "close" || p.verdict === "wrong");
    });
  }

  // ---------- Summary for the tutor ----------
  function summary() {
    var lines = [];
    var placed = BUCKETS.filter(function (b) { return S.placements[b.id].cell; });
    if (placed.length) {
      lines.push("Placements (" + placed.length + " of " + BUCKETS.length + "): " + placed.map(function (b) {
        var p = S.placements[b.id];
        return b.name + " at " + cellLabel(p.cell) + (p.verdict ? " (" + verdictLabel(p.verdict) + (p.verdict === "right" ? "" : ", reference has it " + nudge(b, p.cell)) + ")" : " (not yet checked)");
      }).join("; ") + ".");
    } else {
      lines.push("No bucket placed yet.");
    }
    if (S.checkedOnce) lines.push("Last check: " + rightCount() + " on the mark, " + closeCount() + " close, " + (BUCKETS.length - rightCount() - closeCount()) + " off or moved since.");
    if (S.excPicked) lines.push("Securitization question: picked " + BY_ID[S.excPicked].name + (S.excDone ? " (correct, exercise complete)." : " (wrong, may retry)."));
    return lines.join(" ");
  }

  function persist() {
    var json = {
      placements: {}, checkedOnce: S.checkedOnce, excPicked: S.excPicked, excDone: S.excDone
    };
    BUCKETS.forEach(function (b) { json.placements[b.id] = S.placements[b.id]; });
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (S.excDone && !ui.completedSent) { ui.completedSent = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(json)); } catch (e) {}
    }
  }

  // ---------- The sort ----------
  var sortRoot = document.getElementById("sort-root");
  var sort = el("div", "sort");
  var main = el("div");
  main.style.minWidth = "0";
  var tray = el("div", "tray");
  tray.appendChild(el("p", "eyebrow", C.trayLabel));
  var trayChips = el("div", "chips");
  tray.appendChild(trayChips);
  var info = el("p", "info");
  info.setAttribute("aria-live", "polite");
  tray.appendChild(info);
  main.appendChild(tray);

  var plane = el("div", "plane");
  var yaxis = el("div", "yaxis");
  var yBtn = btn("", null, "axis-effectiveness");
  yBtn.title = AXIS_TIPS.y;
  yBtn.appendChild(el("span", null, C.yTitle + " "));
  yBtn.appendChild(el("span", "muted", C.ySub));
  yBtn.appendChild(el("span", null, " →"));
  yBtn.addEventListener("click", function () { showInfo(C.yTitle + ".", AXIS_TIPS.y); });
  yaxis.appendChild(yBtn);
  plane.appendChild(yaxis);

  var planeMain = el("div", "plane-main");
  var planeInner = el("div", "plane-inner");
  var gridrow = el("div", "gridrow");
  var rowlabels = el("div", "rowlabels");
  ROWS.forEach(function (e) {
    var r = AXIS_SCALES.effectiveness.rungs[e];
    var d = el("div", null, r.name);
    d.title = r.name + ": " + r.gloss;
    rowlabels.appendChild(d);
  });
  gridrow.appendChild(rowlabels);
  var board = el("div", "board");
  var cells = el("div", "cells");
  var cellEls = {};
  ROWS.forEach(function (e) {
    COLS.forEach(function (f) {
      var key = cellKey(f, e);
      var cell = el("div", "cell");
      cell.setAttribute("data-cell", key);
      if (key === "f4e4" || key === "f0e0") cell.classList.add("is-corner");
      var target = btn("target", null, "cell-" + key);
      target.setAttribute("aria-label", "Place at " + cellLabel(key));
      target.tabIndex = -1;
      target.addEventListener("click", function () { if (ui.armedId) place(ui.armedId, key); });
      cell.appendChild(target);
      if (key === "f4e4") {
        var tr = btn("corner tr", C.cornerTR, "corner-tr");
        tr.title = AXIS_TIPS.tr;
        tr.addEventListener("click", function () { showInfo(C.cornerTR, AXIS_TIPS.tr); });
        cell.appendChild(tr);
      }
      if (key === "f0e0") {
        var bl = btn("corner bl", C.cornerBL, "corner-bl");
        bl.title = AXIS_TIPS.bl;
        bl.addEventListener("click", function () { showInfo(C.cornerBL, AXIS_TIPS.bl); });
        cell.appendChild(bl);
      }
      cells.appendChild(cell);
      cellEls[key] = cell;
    });
  });
  board.appendChild(cells);
  var SVGNS = "http://www.w3.org/2000/svg";
  var arrowSvg = document.createElementNS(SVGNS, "svg");
  arrowSvg.setAttribute("class", "arrows");
  arrowSvg.setAttribute("aria-hidden", "true");
  arrowSvg.setAttribute("focusable", "false");
  board.appendChild(arrowSvg);
  gridrow.appendChild(board);
  planeInner.appendChild(gridrow);
  var collabels = el("div", "collabels");
  COLS.forEach(function (f) {
    var r = AXIS_SCALES.feasibility.rungs[f];
    var d = el("div", null, r.name);
    d.title = r.name + ": " + r.gloss;
    collabels.appendChild(d);
  });
  planeInner.appendChild(collabels);
  var xaxis = el("div", "xaxis");
  var xBtn = btn("", null, "axis-feasibility");
  xBtn.title = AXIS_TIPS.x;
  xBtn.appendChild(el("span", null, C.xTitle + " "));
  xBtn.appendChild(el("span", "muted", C.xSub));
  xBtn.appendChild(el("span", null, " →"));
  xBtn.addEventListener("click", function () { showInfo(C.xTitle + ".", AXIS_TIPS.x); });
  xaxis.appendChild(xBtn);
  planeInner.appendChild(xaxis);
  planeInner.appendChild(el("p", "caption", C.caption));
  planeMain.appendChild(planeInner);
  plane.appendChild(planeMain);
  main.appendChild(plane);
  sort.appendChild(main);

  // aside
  var aside = el("aside");
  var stats = el("div", "stats");
  C.stats.forEach(function (s) {
    var d = el("div");
    d.appendChild(el("b", null, s.n));
    d.appendChild(el("span", null, s.l));
    stats.appendChild(d);
  });
  aside.appendChild(stats);
  var exBlock = el("div");
  exBlock.appendChild(el("p", "eyebrow", C.exerciseLabel));
  var controls = el("div", "controls");
  var checkBtn = btn("primary", C.checkBtn, "check");
  var resetBtn = btn("quiet", "↺ " + C.resetBtn, "reset");
  resetBtn.style.textAlign = "center";
  var statusLine = el("p", "status", "");
  controls.appendChild(checkBtn); controls.appendChild(resetBtn); controls.appendChild(statusLine);
  exBlock.appendChild(controls);
  aside.appendChild(exBlock);
  checkBtn.addEventListener("click", check);
  resetBtn.addEventListener("click", resetSort);

  var legend = el("div", "legend");
  legend.hidden = true;
  [["right", "✓", C.legendRight], ["close", "", C.legendClose], ["off", "", C.legendOff]].forEach(function (row) {
    var sp = el("span");
    var mark = el("i", row[0], row[1]);
    mark.setAttribute("aria-hidden", "true");
    sp.appendChild(mark);
    sp.appendChild(document.createTextNode(row[2]));
    legend.appendChild(sp);
  });
  aside.appendChild(legend);

  var exc = el("div", "exc");
  exc.hidden = true;
  exc.appendChild(el("p", "eyebrow", C.excLabel));
  var excLead = el("p", "lead");
  excLead.appendChild(document.createTextNode(C.excLead.pre));
  var secBtn = btn("term", C.excLead.sec, "sec-term");
  secBtn.title = AXIS_TIPS.sec;
  secBtn.setAttribute("aria-expanded", "false");
  excLead.appendChild(secBtn);
  excLead.appendChild(document.createTextNode(C.excLead.mid));
  excLead.appendChild(el("b", null, C.excLead.bold));
  excLead.appendChild(document.createTextNode(C.excLead.post));
  exc.appendChild(excLead);
  var secTip = el("p", "termtip", AXIS_TIPS.sec);
  secTip.hidden = true;
  exc.appendChild(secTip);
  secBtn.addEventListener("click", function () { secTip.hidden = !secTip.hidden; secBtn.setAttribute("aria-expanded", String(!secTip.hidden)); });
  var excOpts = el("div", "opts");
  var excBtns = {};
  EXC_ORDER.forEach(function (id) {
    var b = btn("", BY_ID[id].name, "exc-" + id);
    b.addEventListener("click", function () { pickException(id); });
    excOpts.appendChild(b);
    excBtns[id] = b;
  });
  exc.appendChild(excOpts);
  var excAnswer = el("p", "answer");
  excAnswer.hidden = true;
  excAnswer.setAttribute("aria-live", "polite");
  exc.appendChild(excAnswer);
  aside.appendChild(exc);

  var finished = el("div", "finished", "✓ " + C.finished);
  finished.hidden = true;
  aside.appendChild(finished);
  sort.appendChild(aside);
  sortRoot.appendChild(sort);

  // ---------- Chips, drag and click-to-place ----------
  var chipEls = {};
  function makeChip(b) {
    var c = btn("chip", null, "chip-" + b.id);
    c.setAttribute("aria-label", b.n + ". " + b.name);
    c.setAttribute("data-id", b.id);
    var badge = el("span", "badge", "");
    badge.setAttribute("aria-hidden", "true");
    badge.hidden = true;
    c.appendChild(badge);
    c.appendChild(el("span", "cn", b.n + "."));
    c.appendChild(el("span", "short", b.short));
    c.addEventListener("pointerdown", function (ev) { if (ev.button === 0) beginDrag(b.id, ev); });
    c.addEventListener("click", function () {
      if (drag && drag.moved) { drag = null; return; }
      drag = null;
      toggleArm(b.id);
    });
    c.addEventListener("keydown", function (ev) {
      if (ev.key === "Escape") { ui.armedId = null; render(); }
    });
    return c;
  }
  BUCKETS.forEach(function (b) { chipEls[b.id] = makeChip(b); });

  function chipBody(b) {
    var p = S.placements[b.id];
    if (p.verdict === "right") return "On the mark. " + b.why;
    if (p.verdict) return "The reference has it at " + cellLabel(refCell(b)) + ". " + b.why;
    if (S.checkedOnce) return b.why;
    return b.desc;
  }
  function chipTitle(b) {
    return b.n + ". " + b.name + ": " + chipBody(b) + "\n\n" + C.cardParallelTag + ", " + b.parallel.title + ". " + b.parallel.text;
  }

  function showInfo(head, text) {
    ui.info = { head: head, text: text };
    renderInfo();
  }
  function renderInfo() {
    clear(info);
    if (!ui.info) return;
    info.appendChild(el("b", null, ui.info.head + " "));
    info.appendChild(document.createTextNode(ui.info.text));
  }

  function toggleArm(id) {
    if (ui.armedId === id) { ui.armedId = null; ui.info = null; }
    else {
      ui.armedId = id;
      var b = BY_ID[id];
      showInfo(b.n + ". " + b.name + ".", chipBody(b));
      say("Picked up " + b.n + ". " + b.name + ". Choose a target.");
    }
    render();
  }

  function place(id, cell) {
    if (!cellEls[cell]) return;
    var b = BY_ID[id];
    ui.armedId = null;
    if (S.placements[id].cell !== cell) S.placements[id] = { cell: cell, verdict: null };
    showInfo(b.n + ". " + b.name + ".", "Placed at " + cellLabel(cell) + ".");
    say(b.name + " placed at " + cellLabel(cell) + ".");
    render();
    persist();
    var ch = chipEls[id];
    if (ch && typeof ch.focus === "function") ch.focus();
  }

  var drag = null, dragGhost = null;
  function beginDrag(id, ev) {
    drag = { id: id, x: ev.clientX, y: ev.clientY, moved: false, pointerId: ev.pointerId, over: null };
  }
  function zoneAt(x, y) {
    var e = document.elementFromPoint(x, y);
    while (e && e !== document.body) {
      if (e.getAttribute && e.getAttribute("data-cell")) return e.getAttribute("data-cell");
      e = e.parentNode;
    }
    return null;
  }
  function setOver(key) {
    if (drag && drag.over === key) return;
    if (drag && drag.over && cellEls[drag.over]) cellEls[drag.over].classList.remove("is-over");
    if (drag) drag.over = key;
    if (key && cellEls[key]) cellEls[key].classList.add("is-over");
  }
  window.addEventListener("pointermove", function (ev) {
    if (!drag || drag.pointerId !== ev.pointerId) return;
    if (!drag.moved) {
      if (Math.hypot(ev.clientX - drag.x, ev.clientY - drag.y) < 5) return;
      drag.moved = true;
      ui.armedId = null;
      var b = BY_ID[drag.id];
      chipEls[drag.id].classList.add("is-dragging");
      dragGhost = el("div", "dragghost", b.n + ". " + b.short);
      document.body.appendChild(dragGhost);
    }
    ev.preventDefault();
    dragGhost.style.transform = "translate(" + (ev.clientX + 12) + "px, " + (ev.clientY + 12) + "px)";
    setOver(zoneAt(ev.clientX, ev.clientY));
  });
  function endDrag(ev) {
    if (!drag || drag.pointerId !== ev.pointerId) return;
    if (drag.moved) {
      var key = ev.type === "pointerup" ? zoneAt(ev.clientX, ev.clientY) : null;
      setOver(null);
      chipEls[drag.id].classList.remove("is-dragging");
      if (dragGhost && dragGhost.parentNode) dragGhost.parentNode.removeChild(dragGhost);
      dragGhost = null;
      var id = drag.id;
      if (key) { place(id, key); }
      else render();
      // keep drag.moved so the click that follows pointerup is swallowed
      setTimeout(function () { drag = null; }, 0);
    } else {
      drag = null;
    }
  }
  window.addEventListener("pointerup", endDrag);
  window.addEventListener("pointercancel", endDrag);
  document.addEventListener("keydown", function (ev) {
    if (ev.key === "Escape" && ui.armedId) { ui.armedId = null; render(); }
  });

  // ---------- Check, reveal, reset, exception ----------
  function check() {
    if (placedCount() !== BUCKETS.length) return;
    S.checkedOnce = true;
    var right = 0;
    BUCKETS.forEach(function (b) {
      var cell = S.placements[b.id].cell;
      if (!cell) return;
      var p = parseCell(cell);
      var v = verdictFor(b, p.f, p.e);
      S.placements[b.id] = { cell: cell, verdict: v };
      if (v === "right") right++;
    });
    var missed = offList();
    var msg = "Checked. " + right + " of " + BUCKETS.length + " on the mark.";
    if (missed.length) {
      msg += " An arrow now points from each of the other " + missed.length + " to the cell the reference has it in: "
        + missed.map(function (b) { return b.name + " to " + cellLabel(refCell(b)); }).join("; ") + ".";
    }
    msg += " Pick any bucket to hear why the reference puts it there. The one-exception question is now available.";
    say(msg);
    ui.info = null;
    render();
    persist();
  }
  function resetSort() {
    BUCKETS.forEach(function (b) { S.placements[b.id] = { cell: null, verdict: null }; });
    S.checkedOnce = false; S.excPicked = null; S.excDone = false;
    ui.armedId = null; ui.info = null;
    say("Sort reset. All " + BUCKETS.length + " buckets returned to the tray.");
    render();
    persist();
  }
  function pickException(id) {
    if (S.excDone || !excUnlocked()) return;
    S.excPicked = id;
    if (EXC_ANSWERS[id].ok) {
      S.excDone = true;
      say("Correct. Exercise complete.");
    } else {
      say("Not quite. Try again.");
    }
    render();
    persist();
  }

  // ---------- Arrows to the reference cells ----------
  function svgEl(tag, cls) {
    var e = document.createElementNS(SVGNS, tag);
    e.setAttribute("class", cls);
    return e;
  }
  function boxIn(node, origin) {
    var r = node.getBoundingClientRect();
    return { x: r.left - origin.left + r.width / 2, y: r.top - origin.top + r.height / 2, hw: r.width / 2, hh: r.height / 2 };
  }
  function edgeOf(c, ux, uy, pad) {
    var tx = ux === 0 ? Infinity : (c.hw + pad) / Math.abs(ux);
    var ty = uy === 0 ? Infinity : (c.hh + pad) / Math.abs(uy);
    var t = Math.min(tx, ty);
    if (!isFinite(t)) t = 0;
    return { x: c.x + ux * t, y: c.y + uy * t };
  }
  function drawArrows() {
    clear(arrowSvg);
    var origin = arrowSvg.getBoundingClientRect();
    var w = Math.round(origin.width), h = Math.round(origin.height);
    if (!w || !h) return;
    // viewBox matches the pixel box one to one, so the heads keep their shape at any width.
    arrowSvg.setAttribute("viewBox", "0 0 " + w + " " + h);
    var missed = offList(), groups = {};
    missed.forEach(function (b) { var k = refCell(b); (groups[k] = groups[k] || []).push(b.id); });
    missed.forEach(function (b) {
      var chip = chipEls[b.id], target = cellEls[refCell(b)];
      if (!chip || !target || !chip.parentNode) return;
      var from = boxIn(chip, origin), to = boxIn(target, origin);
      var g = groups[refCell(b)], spread = (g.indexOf(b.id) - (g.length - 1) / 2) * 9;
      var dx = to.x - from.x, dy = to.y - from.y, len = Math.sqrt(dx * dx + dy * dy);
      if (!len) return;
      // two chips aiming at one cell land side by side, across the arrow's own direction
      var ax = to.x - (dy / len) * spread, ay = to.y + (dx / len) * spread;
      dx = ax - from.x; dy = ay - from.y; len = Math.sqrt(dx * dx + dy * dy);
      if (len < 16) return;
      var ux = dx / len, uy = dy / len;
      var start = edgeOf(from, ux, uy, 2);
      var tipX = ax - ux * 4, tipY = ay - uy * 4;
      var backX = tipX - ux * 9, backY = tipY - uy * 9;
      var kind = S.placements[b.id].verdict === "close" ? "close" : "off";
      var line = svgEl("line", "shaft " + kind);
      line.setAttribute("x1", start.x.toFixed(1));
      line.setAttribute("y1", start.y.toFixed(1));
      line.setAttribute("x2", backX.toFixed(1));
      line.setAttribute("y2", backY.toFixed(1));
      arrowSvg.appendChild(line);
      var head = svgEl("path", "head " + kind);
      head.setAttribute("d", "M" + tipX.toFixed(1) + " " + tipY.toFixed(1)
        + " L" + (backX - uy * 4.5).toFixed(1) + " " + (backY + ux * 4.5).toFixed(1)
        + " L" + (backX + uy * 4.5).toFixed(1) + " " + (backY - ux * 4.5).toFixed(1) + " Z");
      arrowSvg.appendChild(head);
    });
  }

  // ---------- Render ----------
  function render() {
    // sort: chips
    var byCell = {};
    clear(trayChips);
    BUCKETS.forEach(function (b) {
      var p = S.placements[b.id];
      var chip = chipEls[b.id];
      chip.classList.toggle("is-armed", ui.armedId === b.id);
      chip.setAttribute("aria-pressed", ui.armedId === b.id ? "true" : "false");
      chip.classList.remove("v-right", "v-close", "v-wrong");
      var badge = chip.firstChild;
      if (p.verdict) chip.classList.add("v-" + p.verdict);
      if (p.verdict === "right") { badge.textContent = "✓"; badge.hidden = false; }
      else { badge.textContent = ""; badge.hidden = true; }
      chip.title = chipTitle(b);
      if (p.cell) {
        (byCell[p.cell] = byCell[p.cell] || []).push(b.id);
        trayChips.appendChild(el("span", "placeholder", b.n + ". " + b.short));
      } else {
        trayChips.appendChild(chip);
      }
    });
    Object.keys(cellEls).forEach(function (key) {
      var cell = cellEls[key];
      var keep = [];
      Array.prototype.forEach.call(cell.children, function (ch) { if (!ch.classList.contains("chip")) keep.push(ch); });
      clear(cell);
      keep.forEach(function (k) { cell.appendChild(k); });
      (byCell[key] || []).forEach(function (id) { cell.appendChild(chipEls[id]); });
      cell.classList.toggle("is-armable", !!ui.armedId);
      cell.firstChild.tabIndex = ui.armedId ? 0 : -1;
    });
    renderInfo();

    drawArrows();
    legend.hidden = !S.checkedOnce;

    // controls and status
    var total = BUCKETS.length, placed = placedCount();
    checkBtn.disabled = placed !== total;
    clear(statusLine);
    if (allVerdicts()) {
      if (allRight()) {
        statusLine.appendChild(el("b", null, total + " of " + total + " on the mark."));
      } else {
        statusLine.appendChild(el("b", null, String(rightCount())));
        statusLine.appendChild(document.createTextNode(" on the mark · "));
        statusLine.appendChild(el("b", null, String(closeCount())));
        statusLine.appendChild(document.createTextNode(" close · "));
        statusLine.appendChild(el("b", null, String(total - rightCount() - closeCount())));
        statusLine.appendChild(document.createTextNode(" off; drag and re-check"));
      }
    } else if (placed === total) {
      statusLine.textContent = S.checkedOnce ? "Moved since the check; check again" : "All placed; check when ready";
    } else {
      statusLine.textContent = placed + " of " + total + " placed";
    }

    // exception
    exc.hidden = !excUnlocked();
    EXC_ORDER.forEach(function (id) {
      var b = excBtns[id];
      var picked = S.excPicked === id, ok = EXC_ANSWERS[id].ok;
      b.disabled = S.excDone && !(picked && ok);
      b.classList.toggle("is-picked", picked);
      b.classList.toggle("ok", picked && ok);
      b.classList.toggle("no", picked && !ok);
      b.setAttribute("aria-pressed", picked ? "true" : "false");
    });
    clear(excAnswer);
    excAnswer.hidden = !S.excPicked;
    if (S.excPicked) {
      var a = EXC_ANSWERS[S.excPicked];
      if (a.lead) excAnswer.appendChild(el("b", null, a.lead));
      excAnswer.appendChild(document.createTextNode(a.t));
    }
    finished.hidden = !S.excDone;
  }

  // ---------- Restore ----------
  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      // A state saved by the earlier three-step version also carries phase, scalesSeen and seen; those fields are ignored.
      if (saved.placements && typeof saved.placements === "object") {
        BUCKETS.forEach(function (b) {
          var p = saved.placements[b.id];
          if (p && typeof p === "object" && typeof p.cell === "string" && cellEls[p.cell]) {
            var v = (p.verdict === "right" || p.verdict === "close" || p.verdict === "wrong") ? p.verdict : null;
            S.placements[b.id] = { cell: p.cell, verdict: v };
          }
        });
      }
      // An older state may carry keyOn (the reference map that this version replaced with arrows),
      // or phase, scalesSeen and seen from the three-step version; unknown fields are ignored.
      S.checkedOnce = !!saved.checkedOnce || !!saved.keyOn;
      S.excPicked = (saved.excPicked && EXC_ANSWERS[saved.excPicked]) ? saved.excPicked : null;
      S.excDone = !!saved.excDone && S.excPicked === "ch";
    }
    if (meta && meta.completed && !S.excDone) {
      // Completed before but the state did not carry it: show the finished view.
      S.excDone = true; S.excPicked = "ch"; S.checkedOnce = true;
    }
    if (S.excDone) ui.completedSent = !!(meta && meta.completed);
    render();
    if (S.excDone && !ui.completedSent) persist();
  }

  var reflow = null;
  function scheduleArrows() {
    if (reflow) return;
    reflow = setTimeout(function () { reflow = null; drawArrows(); }, 60);
  }
  window.addEventListener("resize", scheduleArrows);
  if (typeof ResizeObserver === "function") {
    try { new ResizeObserver(scheduleArrows).observe(board); } catch (e) {}
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var saved = null;
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { saved = null; }
    hydrate(saved, { completed: false });
  }
</script>
</body>
</html>
