---
id: 'a29e5708-d419-4e9a-a05a-408ba9d051a8'
title: Who can prove what
summary_for_tutor: "XLab's edge workshop on the 17-actor ring board from 1.2 (United States, China, Taiwan, Netherlands, Japan, South Korea, BIS, Intelligence community, California, the AI verification body that does not exist, ASML, TSMC, NVIDIA, Cloud providers, Frontier labs, Proxies, Deployers), shown on the key placement (Declares, Holds the evidence, Verifies, Outside the declaration) around a training run above the threshold. Step 1: the learner draws directed edges A to B, meaning A can produce evidence about B for a verifier that B did not volunteer, by dragging between points on the map, tapping two points in order, or picking source and target from button lists; there is no target number. On commit the widget grades against XLab's seven-edge key (Cloud providers to Frontier labs, 1.A; NVIDIA to Frontier labs, 1.B; NVIDIA to Cloud providers, 2.A; TSMC to Proxies, NVIDIA to Proxies, Intelligence community to China, Intelligence community to Proxies, all 2.B), reports found, reversed, extra and missed edges with the Baker et al. mechanism behind each, and explains why the other ten actors hold no edge. Step 2 shows the readings (What the finished map says; Where this regime is weakest: 2.B has four edges, the other subgoals one each, NVIDIA is on three of seven), lets the learner light up actors by functional role, and asks the second-order question: whose removal stops a frontier training run soonest; the key's answer is the cloud providers. Committing that answer completes the widget. Optional afterwards: three written questions (Taiwan's functional roles; information holders for one run in order of completeness; an actor that is capability holder and enforcement authority at once) scored by the assessor against XLab's marking key and self-marked on the same key. The saved-state summary lists the learner's edges, their score against the key, their second-order pick and their written answers. Ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Who can prove what</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "actor-edges". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df; --surface: #faf8f3;
    --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 26px; margin: 4px 0 12px; }
  h2 { font-size: 18px; }
  h3 { font-size: 17px; }
  p { margin: 0; }
  .stack > * + * { margin-top: 16px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .card p + p, .card p + ol, .card ol + p { margin-top: 8px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .strong { font-weight: 600; }
  .medium { font-weight: 500; }
  ol, ul { margin: 0; padding-left: 0; list-style: none; }
  .list > li + li { margin-top: 12px; padding-top: 12px; border-top: 1px solid var(--border); }
  .tight > li + li { margin-top: 4px; }
  .sep { border-top: 1px solid var(--border); margin-top: 16px; padding-top: 16px; }
  .quote { border-left: 2px solid var(--border); padding-left: 12px; margin-top: 6px; font-size: 12px; color: var(--muted); }
  .quote .where { white-space: nowrap; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: #fdf6ec; font-weight: 500; }
  button.chip { padding: 6px 10px; font-size: 12px; }
  button.link { border: 0; padding: 0; background: none; border-radius: 0; }
  button.link:hover { background: none; text-decoration: underline; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }
  .row { display: flex; flex-wrap: wrap; gap: 12px; align-items: center; justify-content: space-between; }
  .row.tight { gap: 8px; }
  .meter { display: flex; gap: 2px; height: 6px; border-radius: 3px; overflow: hidden; margin-top: 6px; }
  .meter span { flex: 1; background: var(--border); }
  .meter span.on { background: var(--accent); }
  .mapbox { border: 1px solid var(--border); border-radius: 8px; padding: 8px; background: #fff; overflow-x: auto; max-width: 860px; margin: 0 auto; }
  .mapbox svg { display: block; width: 100%; height: auto; min-width: 560px; margin: 0 auto; }
  .mapbox .note { padding: 4px 8px; font-size: 12px; color: var(--muted); }
  .node.is-interactive { cursor: crosshair; touch-action: none; outline: none; }
  .node:focus-visible .hit { stroke: var(--accent); stroke-width: 2; }
  .node text { user-select: none; -webkit-user-select: none; }
  .legend { display: flex; flex-wrap: wrap; gap: 12px 18px; padding: 4px 8px; font-size: 12px; color: var(--muted); }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .legend svg { width: 28px; height: 10px; min-width: 0; }
  .verdict-line { display: flex; gap: 6px; align-items: flex-start; }
  .mark { flex: none; width: 16px; height: 16px; margin-top: 3px; }
  .radio { display: grid; gap: 6px; }
  .radio button { width: 100%; }
  .radio button.is-correct { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .radio button.is-wrong { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); text-decoration: line-through; }
  .radio button.is-dim { opacity: 0.55; }
  textarea { width: 100%; font: inherit; color: inherit; background: #fff; border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px; min-height: 140px; resize: vertical; margin-top: 8px; }
  textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  .crit { display: flex; gap: 12px; width: 100%; align-items: flex-start; }
  .crit .pts { flex: none; width: 22px; height: 22px; border: 1px solid var(--border); border-radius: 4px; display: inline-flex; align-items: center; justify-content: center; font-size: 11px; margin-top: 2px; }
  .crit.is-active .pts { background: var(--accent); border-color: var(--accent); color: #fff; }
  .grid2 { display: grid; gap: 12px; grid-template-columns: 1fr 1fr; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
  @media (max-width: 600px) { .grid2 { grid-template-columns: 1fr; } body { padding: 12px; } }
</style>
</head>
<body>
<p class="eyebrow">Workshop</p>
<h1>Who can prove what</h1>
<div id="app" class="stack" aria-live="polite"></div>

<script>
  // ---------- Data (from XLab: src/lib/verification/data/actor-workshop.ts and actor-map.ts) ----------
  var ACTORS = [
    { id: "us", name: "United States", label: "United States", position: "Jurisdiction over chip design, the largest frontier labs and cloud providers, and export-control law.", note: "Its export rules are the closest thing to a working compute-control regime today; its intelligence collection is difficult to share.", roles: ["capability", "chokepoint", "information", "enforcement"], postures: ["comply", "hide"] },
    { id: "china", name: "China", label: "China", position: "The other frontier developer: manufacturing scale, materials, designers, clouds and labs.", note: "Reads on-chip controls and inspection rights as surveillance and containment.", roles: ["capability", "chokepoint", "information", "enforcement"], postures: ["comply", "hide"] },
    { id: "taiwan", name: "Taiwan", label: "Taiwan", position: "Fabrication and advanced packaging.", note: "Caught between US rules and Chinese customers.", roles: ["chokepoint", "information", "victim"], postures: ["comply"] },
    { id: "netherlands", name: "Netherlands", label: "Netherlands", position: "Equipment: ASML.", note: "A small state carrying outsized weight in a rivalry it did not choose.", roles: ["chokepoint", "information"], postures: ["comply"] },
    { id: "japan", name: "Japan", label: "Japan", position: "Equipment and specialty materials.", note: "Under pressure from both sides of the US-China rivalry.", roles: ["chokepoint"], postures: ["comply"] },
    { id: "south-korea", name: "South Korea", label: "South Korea", position: "Memory, including high-bandwidth memory.", note: "Export exposure to China against alliance pressure from the United States.", roles: ["chokepoint", "information"], postures: ["comply"] },
    { id: "bis", name: "Commerce · BIS", label: "BIS", position: "Inside the United States.", note: "Writes and enforces export controls on chips.", roles: ["enforcement", "information"], postures: ["comply"] },
    { id: "ic", name: "Intelligence community", label: "Intelligence community", position: "Inside the United States.", note: "Collects evidence of undeclared facilities, but sharing it can expose sources and methods.", roles: ["information"], postures: ["hide"] },
    { id: "california", name: "California", label: "California", position: "Subnational jurisdiction over most frontier labs by headquarters geography.", note: "", roles: ["enforcement", "information"], postures: ["comply"] },
    { id: "missing-verifier", name: "The verification body that does not exist", label: "No AI verification body", position: "Above the state.", note: "No international body holds a chip registry, inspection right, or procedure for resolving an allegation of training above a threshold.", roles: [], postures: [] },
    { id: "asml", name: "ASML", label: "ASML", position: "Equipment, most upstream.", note: "Few customers, high visibility, and systems that need continuing vendor service.", roles: ["chokepoint", "information"], postures: ["comply"] },
    { id: "tsmc", name: "TSMC", label: "TSMC", position: "Fabrication and advanced packaging.", note: "", roles: ["chokepoint", "information", "evasion"], postures: ["comply", "hide"] },
    { id: "nvidia", name: "NVIDIA", label: "NVIDIA", position: "Accelerator design.", note: "It can decide whether accelerators ship with attestation, metering, or location features.", roles: ["chokepoint", "information", "evasion", "victim"], postures: ["comply", "hide", "exaggerate", "freeride"] },
    { id: "hyperscalers", name: "AWS, Azure, Google Cloud, Oracle, Alibaba", label: "Cloud providers", position: "Cloud and data-center operation.", note: "They can suspend access and hold rich logs; reseller chains and mislabeled workloads also create evasion routes.", roles: ["chokepoint", "information", "enforcement", "evasion"], postures: ["comply", "hide"] },
    { id: "frontier-labs", name: "Frontier labs", label: "Frontier labs", position: "Model training.", note: "They hold the most detailed private information in the system: what was trained, on what data, and what evaluations showed.", roles: ["capability", "information", "victim"], postures: ["comply", "hide", "exaggerate", "freeride"] },
    { id: "proxies", name: "Front companies, resellers, straw buyers", label: "Proxies", position: "Distribution, across every stage.", note: "They exist to break the link between a name and an activity.", roles: ["evasion"], postures: ["defect"] },
    { id: "deployers", name: "Product builders and deployers", label: "Deployers", position: "Deployment, most downstream.", note: "A diffuse downstream signal of what models can do.", roles: ["victim"], postures: ["freeride"] }
  ];
  var ACTOR_BY_ID = {};
  ACTORS.forEach(function (a) { ACTOR_BY_ID[a.id] = a; });
  function labelOf(id) { return ACTOR_BY_ID[id] ? ACTOR_BY_ID[id].label : id; }

  var RINGS = [
    { id: "declares", name: "Declares", test: "You own or use large-scale compute, or you signed the agreement and answer for what happens inside your territory. Either way the regime wants a declaration from you: you are the Prover." },
    { id: "evidence", name: "Holds the evidence", test: "You declare nothing here and you check nothing, but you hold a record a declaration can be held against, or the authority that makes somebody else’s record producible." },
    { id: "verifies", name: "Verifies", test: "The declarations come to you, and your job is to establish that they are true and that nothing has been left out." },
    { id: "undeclared", name: "Outside the declaration", test: "Nothing you do appears in anybody’s declaration, because you sit below the threshold, or because you exist to keep a name off one." }
  ];
  var RING_KEY = {
    us: "declares", china: "declares", taiwan: "evidence", netherlands: "evidence", japan: "evidence", "south-korea": "evidence",
    bis: "verifies", ic: "verifies", california: "verifies", "missing-verifier": "verifies",
    asml: "evidence", tsmc: "evidence", nvidia: "evidence", hyperscalers: "declares", "frontier-labs": "declares",
    proxies: "undeclared", deployers: "undeclared"
  };
  var MAP_SLOTS = ["asml", "us", "taiwan", "bis", "nvidia", "hyperscalers", "proxies", "tsmc", "ic", "netherlands", "frontier-labs", "japan", "california", "south-korea", "china", "deployers", "missing-verifier"];
  var ABSENT = { "missing-verifier": true };
  var CENTRE = { label: "A training run", sub: "above the threshold", baker: { text: "it seeks to verify compliance on the basis that all large-scale AI compute use is accounted for in compliant activities.", where: "§3.1, AI compute accounting" } };

  var ROLES = [
    { id: "capability", name: "Capability holder", question: "Who can actually build the dangerous thing?" },
    { id: "chokepoint", name: "Chokepoint controller", question: "Who can physically stop or slow the flow?" },
    { id: "information", name: "Information holder", question: "Who already knows what verifiers need to learn?" },
    { id: "enforcement", name: "Enforcement authority", question: "Who can impose a real cost for violating?" },
    { id: "evasion", name: "Evasion pathway", question: "Through whom would a cheater route?" },
    { id: "victim", name: "Victim, free-rider, beneficiary", question: "Who bears the risk, or enjoys the stability, without a seat at the table?" }
  ];
  var POSTURES = [
    { id: "comply", name: "Comply", means: "Follow the agreement as written." },
    { id: "defect", name: "Defect", means: "Covertly violate for advantage." },
    { id: "hide", name: "Hide", means: "Obscure assets or activities from view, whether or not a rule is being broken." },
    { id: "exaggerate", name: "Exaggerate", means: "Overstate compliance, safety, or capability." },
    { id: "freeride", name: "Free-ride", means: "Enjoy the stability produced by others' restraint without bearing its costs." }
  ];

  var SUBGOALS = [
    { id: "1a", label: "1.A", name: "Declared uses are accurate", baker: { text: "Verify that declared uses of AI compute are declared accurately, i.e., the Prover actually did the claimed development or deployment.", where: "§3.2" } },
    { id: "1b", label: "1.B", name: "Declared uses have the required properties", baker: { text: "Assuming that the declared uses are accurate (as is verified per Subgoal 1.A), verify they have the required properties.", where: "§3.2" } },
    { id: "2a", label: "2.A", name: "No undeclared use of a declared cluster", baker: { text: "Verify that there are no undeclared, large-scale uses of declared AI compute clusters.", where: "§3.2" } },
    { id: "2b", label: "2.B", name: "No undeclared clusters at all", baker: { text: "Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations.", where: "§3.2" } }
  ];

  var EDGE_KEY = [
    { from: "hyperscalers", to: "frontier-labs", subgoal: "1a",
      what: "The declared run happened on somebody else’s machines. The cluster’s own records (logs, billing, and the sensors a verification regime would attach to it) are where a Verifier goes to find out whether the declaration matches what the chips did.",
      baker: [{ text: "the Verifier would aim to detect discrepancies between a Prover’s declarations and their actual chip use, such as by detecting that chips’ input data or power draw patterns tell a different story than the Prover’s claims", where: "§4.2, off-chip verification layers" }] },
    { from: "nvidia", to: "frontier-labs", subgoal: "1b",
      what: "Checking that a declared model has the properties the rules require means running tests on it without the Prover handing over its weights. The feature that makes that possible is built into the chip at design time; Baker names NVIDIA among the designers that have implemented or announced versions of it.",
      baker: [{ text: "This could enable a Verifier to run tests on a Prover’s models, data, and code, with the Prover knowing their information will not be stolen, and with the Verifier knowing their tests will be run faithfully and will not be viewed for the sake of manipulating test results.", where: "§4.1.1.1, Confidential Computing" }] },
    { from: "nvidia", to: "hyperscalers", subgoal: "2a",
      what: "Accounting for everything a declared cluster did means the chips keeping their own record. That is a hardware feature, present or absent at manufacture: the cluster’s operator cannot add it afterwards, and cannot quietly remove it either.",
      baker: [{ text: "Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis.", where: "§4.1, the on-chip verification layer" }] },
    { from: "tsmc", to: "proxies", subgoal: "2b",
      what: "The chain of custody starts where the die is made. How many leading-edge parts exist at all is the ceiling on how large any undeclared cluster could possibly be, and that number exists in one place.",
      baker: [
        { text: "A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.", where: "§4.2.1, verifying AI chips’ chain of custody" },
        { text: "This would serve to verify that large quantities of AI chips are not assembled into undeclared AI compute clusters (Subgoal 2.B).", where: "§4.2.1" }
      ] },
    { from: "nvidia", to: "proxies", subgoal: "2b",
      what: "The same chain one link down: who the parts were sold to, and which serialised chip went where. This is NVIDIA’s second mechanism and a different one from the first, which is exactly why it gets its own edge.",
      baker: [{ text: "An example verification mechanism is inspecting AI chips to verify that they have not been sent to undeclared AI data centers; this helps complete Subgoal 2.B.", where: "§4, defining a verification mechanism" }] },
    { from: "ic", to: "china", subgoal: "2b",
      what: "The lesson's own row for this agency is monitoring and attribution: the layer that spots hidden data centres and procurement networks. It is what one signatory has instead of a right to inspect the other. Note what it costs: what it knows is classified, so turning it into evidence anybody may act on risks the source that produced it. And note the asymmetry, which is a fact about this roster rather than about the world: China has the same capability and this board has no row for it.",
      baker: [
        { text: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.", where: "§4.3, personnel-based verification layers" },
        { text: "More adversarial, harder for third parties to verify, and unclear effectiveness.", where: "§4.3, the layer's own listed disadvantages" }
      ] },
    { from: "ic", to: "proxies", subgoal: "2b",
      what: "A cluster nobody declared leaves no paperwork to audit. What is left is people and signals, and this is the only actor on the board that can reach a facility that was never on any list. Read the quote carefully: the paper gives intelligence EVERY subgoal, not this one. It is filed here because 2.B is the only place on this board where it is the sole mechanism, and an edge you drew from it to a lab or a cloud has the paper behind it.",
      baker: [{ text: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.", where: "§4.3, personnel-based verification layers" }] }
  ];

  var EDGE_NOTES = [
    { actorIds: ["us"],
      why: "A signatory declares; it does not produce evidence itself. What a state has for that is institutions, which is why the intelligence edge starts at the agency rather than at the country. Then notice the shape that leaves: China is at the receiving end of an edge and the United States is at the receiving end of none. Do not read that as a claim that one government is the more transparent. It is a claim about which government's institutions this roster wrote down, and about the empty ring where the body that would check both of them should be.",
      baker: [{ text: "The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement.", where: "§3.1, Prover and Verifier" }] },
    { actorIds: ["taiwan", "netherlands", "japan", "south-korea"],
      why: "The four host states hold the jurisdiction that makes their firms' records producible, and not one of them is a party to this agreement. That is not an oversight in the drawing; it is the open problem the paper lists under attaining participation, and it is the reason a two-party compute agreement leans on export controls and energy policy rather than on the agreement itself. An edge you drew from one of them is an edge nothing compels.",
      baker: [{ text: "How to attain compliance commitments from all states that host large-scale AI compute (as such states could directly misuse it or rent it to an agreement party)?", where: "§3.3, broader challenges" }] },
    { actorIds: ["missing-verifier"],
      why: "This one can hold no edge, and that is the row, not a gap in it. The paper allows a government body or a third party as Verifier; every government body here belongs to one signatory, and the third party does not exist: no chip registry, no challenge-inspection right, no procedure for resolving an allegation of training above a threshold. Read the board once more with that in mind: a two-party agreement in which only one party's institutions can check anything, and no neutral party at all.",
      baker: [{ text: "The Verifier could be a government body or a third party.", where: "§3.1" }] },
    { actorIds: ["asml"],
      why: "Baker’s chain of custody begins at manufacturing, and ASML is upstream of that: it sells the machines the fab uses, not the parts a regime counts. The tightest chokepoint on the map completes no subgoal, which is what the difference between leverage and evidence looks like.",
      baker: [{ text: "A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.", where: "§4.2.1, the chain starts at manufacturing, not at the tools" }] },
    { actorIds: ["bis"],
      why: "Export control is the instrument, and the paper puts it outside the frame deliberately: it is how a party is stopped or punished after a finding, not how a declaration is checked. Today’s de facto compute-governance agency is, in this framework, downstream of verification rather than part of it.",
      baker: [{ text: "We do not cover this latter step of enforcement, though a few verification mechanisms double as enforcement tools.", where: "§2.3, scope limitations" }] },
    { actorIds: ["california"],
      why: "A reporting statute produces declarations. Verification is what happens to a declaration afterwards, and receiving one is not checking it. The actor that bound the leading labs before any international mechanism existed completes no subgoal: it supplies the thing the subgoals are about. Argue with this one if you drew the edge: SB 53 also requires an internal anonymous reporting channel at large frontier developers, and whistleblowing is a verification mechanism in this framework, for every subgoal at once. The key leaves the edge out because the mechanism is a programme a Verifier runs and California is not running one, which is a judgement, not a reading.",
      baker: [
        { text: "Verification focuses on checking that these declarations are correct and complete.", where: "§3.1" },
        { text: "Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.", where: "§4.3, the personnel-based layers" }
      ] },
    { actorIds: ["deployers"],
      why: "Below the threshold, and that is the whole of it. Millions of actors running somebody else’s model are outside the regime by construction rather than by evasion, which is why they share a ring with the proxies and share nothing else.",
      baker: [{ text: "AI development or deployment is “large-scale” if it uses thousands of high-end AI chips over multiple months.", where: "§2.2, what counts as large-scale" }] }
  ];

  var EDGE_FINDING = {
    title: "Where this regime is weakest",
    body: [
      "Count the edges by subgoal. 2.B (no undeclared clusters anywhere) has four. The other three subgoals have one edge each, so three quarters of what a verifier has to establish rests on a single mechanism apiece. Baker’s standard for a robust regime is redundancy: layers stacked, so that a subgoal has more than one way of being completed. Three of the four subgoals on this board have no second way at all.",
      "Now count by actor instead, which is the sharper reading. One firm is on three of the seven edges and touches three of the four subgoals, and that is not a coincidence about NVIDIA, it is what a verification layer IS. The paper defines a layer as one mechanism per subgoal, and the on-chip layer is a chip designer’s to give or withhold. So the board does not show one weak link; it shows a regime resting on roughly one layer, held by a company that is not a party to the agreement.",
      "The paper calls the least robust subgoal the weak link and says the regime is only as good as that one. This map narrows the question rather than answering it (counting edges is not measuring robustness), but it does tell you where to ask.",
      "Now count arrowheads. Six of the seven edges point at a company or at a shell. Exactly one points at a party to the agreement, and it runs one way, out of one signatory’s intelligence service. Nothing on this board produces evidence about the United States, and the reason is not that the United States is transparent: it is that the counterparty’s institutions are not on the roster and the neutral body that would be is the hollow ring on the third band. This is a map of a two-party agreement in which one party’s bureaus do all the checking, including of themselves.",
      "Then read the third ring on its own, since that is where the last paragraph comes from. The export-control bureau, the intelligence community, the state legislature: one country’s, all three. 1.2 already told you the shelf marked “AI verification body” is empty; here it is, drawn empty, on the ring where the alternative would have gone.",
      "Then read what has no edge at all: ten of the seventeen. Some of those absences are the paper’s scope (enforcement is not verification), some are the roster’s (China brought no bureaus), and one is the whole problem stated as a hole: four states hold the jurisdiction that makes the chain’s records producible, and not one of them signed anything.",
      "Then read what has no node. The paper’s simplest and most implementation-ready layer runs on people: whistleblowers, interviews, intelligence. One of those three is on this board, because it happens to be an institution. The other two are not organisations, so a map of organisations has nowhere to put them, and you would never find them by drawing one."
    ],
    weakLink: { text: "identify the subgoal whose mechanisms are collectively least robust. This subgoal is the “weak link” of the regime: its robustness determines the regime’s overall robustness.", where: "§3.2" },
    redundancy: { text: "three verification layers can be stacked together to achieve three layers of redundancy, for example.", where: "§4, defining a verification layer" }
  };

  var MAP_FINDING = {
    title: "What the finished map says",
    body: [
      "Read your rings from the inside out. Exactly two actors on this board owe anybody a declaration; everything outside them either holds evidence about that declaration, or checks it, or is not covered by any declaration at all. A verification regime is a much smaller object than the map of who matters: most of this board it does not reach, and half of it cannot help.",
      "Now read the colours across the rings instead of around them. Roles do not stay in their band: the cloud provider holds four of them at once, and the ring it sits on tells you none of the four. The section gives you three questions to ask of any actor: where does it sit on the chain (position, Table 4, and the map in 1.2.1 is where you practise it), what can it do inside a regime (roles), what does it want today (posture). These rings are a fourth, and a narrower one: not where an actor sits, but what part it plays in checking a declaration. All four cut across each other, which is why no single one of them is the map."
    ]
  };

  var SECOND_ORDER = {
    stem: "Take one actor off the board entirely. Whose removal stops a frontier training run soonest: this week, not this decade?",
    options: [
      { id: "hyperscalers", text: "The cloud providers.", correct: true, why: "The run happens on their machines. Access can be suspended this afternoon, and they are the other actor the regime asks for a declaration, because the cluster it happens on is theirs." },
      { id: "asml", text: "ASML.", correct: false, why: "The most consequential removal on this board and the slowest. ASML is 100% of EUV lithography, so taking it away eventually takes leading-edge fabrication with it, but no training run stops this week, because the chips already exist." },
      { id: "tsmc", text: "TSMC.", correct: false, why: "Same shape as ASML, one step nearer: ~90% of sub-7nm logic. It stops the next generation of chips, not the run already loaded." },
      { id: "bis", text: "The Bureau of Industry and Security.", correct: false, why: "It writes and enforces export controls and trains nothing. Remove it and the rules stop being enforced, which loosens the regime rather than stopping the activity." }
    ],
    lesson: "That gap is the thing a ring map is drawn to show. The removal that bites soonest and the removal that matters most are different actors, on different rings, and a regime that reaches only for the second one buys nothing this year. Ask both questions of any chokepoint you are offered."
  };

  var CLOSING_QUESTIONS = [
    { id: "taiwan-roles", n: 1, title: "Tag every functional role Taiwan holds. There are at least three.", criteria: [0, 1, 2], noCredit: [0] },
    { id: "information-order", n: 2, title: "For one specific frontier training run, list the information holders in order of how complete their picture is.", criteria: [3, 4], noCredit: [1] },
    { id: "uneasy-pairing", n: 3, title: "Name one actor that is a capability holder and an enforcement authority at the same time, and say why that pairing should make you uneasy.", criteria: [5, 6], noCredit: [2] }
  ];

  var CLOSING_KEY = {
    criteria: [
      { text: "Taiwan is named as a chokepoint controller, and the reason is the fabrication step rather than the country.", points: 1, needsReasoning: true, grounds: "Table 2: “the single tightest physical chokepoint in the system”." },
      { text: "Taiwan is named as an information holder: what was fabricated, how much, and for whom.", points: 1, grounds: "Table 5: “Who already knows what verifiers need to learn?”" },
      { text: "Taiwan is named as a victim or beneficiary: it carries the risk of being the chokepoint without controlling the conflict over it.", points: 1, needsReasoning: true, grounds: "Table 2: “being both the prize and the battlefield in a conflict it does not control”." },
      { text: "The information holders are put in an actual order, not listed.", points: 1 },
      { text: "Each rank carries the reason its picture is more or less complete: what that actor sees, and what it cannot see.", points: 2, needsReasoning: true, grounds: "Table 4 gives each stage its holding: the lab knows what was trained and on what, the cloud holds logs and billing, the fab holds shipments." },
      { text: "The actor named for the last question holds capability and enforcement at once: on this roster that is a state with a frontier programme of its own.", points: 1, grounds: "Table 3 splits one signatory into institutions that do not want the same thing." },
      { text: "The unease is stated as a mechanism: the same actor builds the thing and judges whether the rules about it were broken, so an unfavourable finding costs it twice.", points: 2, needsReasoning: true }
    ],
    noCredit: [
      "Naming Taiwan’s three roles without saying what makes each one true.",
      "Listing information holders in the order the lesson happens to print them, with no claim about completeness.",
      "Calling it a conflict of interest with no account of what the conflict costs the actor."
    ]
  };
  var REASONING_LINE = "The judgement alone is not the point: the reasoning has to be on the page.";

  var STEPS = [
    { id: "edges", name: "Draw the edges", beeck: "Political analysis" },
    { id: "map", name: "Read the map", beeck: "Political analysis · Actions" }
  ];

  // ---------- Engine (from XLab: src/lib/verification/actor-workshop.ts) ----------
  function edgeId(from, to) { return from + ">" + to; }
  function splitEdge(id) { var p = id.split(">"); return { from: p[0] || "", to: p[1] || "" }; }
  function edgeLabel(id) { var e = splitEdge(id); return labelOf(e.from) + " → " + labelOf(e.to); }
  var KEY_EDGE_IDS = EDGE_KEY.map(function (e) { return edgeId(e.from, e.to); });
  function has(list, x) { return list.indexOf(x) !== -1; }
  function scoreEdges(drawn, key) {
    var flip = function (id) { var e = splitEdge(id); return edgeId(e.to, e.from); };
    var found = key.filter(function (id) { return has(drawn, id); });
    var missed = key.filter(function (id) { return !has(drawn, id); });
    var surplus = drawn.filter(function (id) { return !has(key, id); });
    var reversed = surplus.filter(function (id) { return has(key, flip(id)) && !has(drawn, flip(id)); });
    var extra = surplus.filter(function (id) { return !has(reversed, id); });
    return { found: found, missed: missed, reversed: reversed, extra: extra };
  }

  // Seeded shuffle (from XLab: src/lib/shuffle.ts). Order is a function of the item id, never of the visit.
  function hashSeed(seed) { var h = 0x811c9dc5; for (var i = 0; i < seed.length; i++) { h ^= seed.charCodeAt(i); h = Math.imul(h, 0x01000193); } return h >>> 0; }
  function prng(s) { return function () { s = (s + 0x6d2b79f5) | 0; var t = s; t = Math.imul(t ^ (t >>> 15), t | 1); t ^= t + Math.imul(t ^ (t >>> 7), t | 61); return ((t ^ (t >>> 14)) >>> 0) / 4294967296; }; }
  function seededOrder(seed, n) { var order = []; for (var i = 0; i < n; i++) order.push(i); var rand = prng(hashSeed(seed)); for (var k = n - 1; k > 0; k--) { var j = Math.floor(rand() * (k + 1)); var tmp = order[k]; order[k] = order[j]; order[j] = tmp; } return order; }
  var SECOND_ORDER_SHOWN = seededOrder("actor-edges:second-order", SECOND_ORDER.options.length).map(function (i) { return SECOND_ORDER.options[i]; });

  // ---------- State ----------
  var STORAGE_KEY = "lens-widget:actor-edges:v1";
  var EMPTY = { edgeStep: "edges", edges: [], edgesDone: false, secondOrder: null, secondOrderDone: false, peeked: false, notes: { answers: {}, done: {} }, marks: [], scores: {} };
  var state = prune(null);
  var completed = false;
  var ui = { source: null, lens: null, rosterOpen: false, writingOpen: false, draft: null, pending: {} };

  function prune(raw) {
    var box = (raw && typeof raw === "object") ? raw : {};
    var out = JSON.parse(JSON.stringify(EMPTY));
    out.edgesDone = box.edgesDone === true;
    out.edgeStep = (out.edgesDone && box.edgeStep === "map") ? "map" : "edges";
    if (Array.isArray(box.edges)) {
      box.edges.forEach(function (e) {
        if (typeof e !== "string") return;
        var p = e.split(">");
        if (p.length !== 2 || !ACTOR_BY_ID[p[0]] || !ACTOR_BY_ID[p[1]] || p[0] === p[1]) return;
        if (!has(out.edges, e)) out.edges.push(e);
      });
    }
    if (typeof box.secondOrder === "string" && SECOND_ORDER.options.some(function (o) { return o.id === box.secondOrder; })) out.secondOrder = box.secondOrder;
    out.secondOrderDone = box.secondOrderDone === true && out.secondOrder !== null;
    out.peeked = box.peeked === true;
    if (box.notes && typeof box.notes === "object") {
      CLOSING_QUESTIONS.forEach(function (q) {
        if (box.notes.answers && typeof box.notes.answers[q.id] === "string") out.notes.answers[q.id] = box.notes.answers[q.id];
        if (box.notes.done && box.notes.done[q.id] === true) out.notes.done[q.id] = true;
      });
    }
    if (Array.isArray(box.marks)) out.marks = box.marks.filter(function (n) { return typeof n === "number" && n >= 0 && n < CLOSING_KEY.criteria.length; });
    if (box.scores && typeof box.scores === "object") {
      CLOSING_QUESTIONS.forEach(function (q) { var s = box.scores[q.id]; if (typeof s === "number") out.scores[q.id] = s; });
    }
    return out;
  }

  function summary() {
    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var parts = [];
    parts.push("Step: " + (state.edgeStep === "map" ? "2, Read the map" : "1, Draw the edges") + ".");
    if (state.edges.length) {
      parts.push("Edges drawn (" + state.edges.length + "; A to B means A can produce evidence about B for a verifier): " + state.edges.map(function (id) { var e = splitEdge(id); return labelOf(e.from) + " to " + labelOf(e.to); }).join("; ") + ".");
    } else {
      parts.push("No edges drawn yet.");
    }
    if (state.edgesDone) {
      parts.push("Edges committed. Against XLab's seven-edge key: " + score.found.length + " of 7 found" +
        (score.reversed.length ? ", " + score.reversed.length + " drawn the other way round (" + score.reversed.map(edgeLabel).join("; ") + ")" : "") +
        (score.extra.length ? ", " + score.extra.length + " not in the key (" + score.extra.map(edgeLabel).join("; ") + ")" : "") +
        (score.missed.length ? ", missed: " + score.missed.map(edgeLabel).join("; ") : "") + ".");
    } else {
      parts.push("Edges not committed yet; the key has not been shown.");
    }
    if (state.secondOrderDone) {
      var pick = SECOND_ORDER.options.filter(function (o) { return o.id === state.secondOrder; })[0];
      parts.push("Second-order question (whose removal stops a frontier training run soonest): chose \"" + pick.text + "\", which is " + (pick.correct ? "the key's answer" : "not the key's answer (the key says the cloud providers)") + ".");
    } else if (state.secondOrder) {
      parts.push("Second-order question: an option is selected but not committed.");
    }
    parts.push(state.peeked ? "The roster was reopened during the workshop." : "The roster stayed closed.");
    var answered = CLOSING_QUESTIONS.filter(function (q) { return state.notes.done[q.id]; });
    if (answered.length) {
      parts.push("Optional written answers saved: " + answered.map(function (q) {
        return "Q" + q.n + " (" + q.title + ")" + (typeof state.scores[q.id] === "number" ? ", assessor score " + state.scores[q.id] + "/100" : "") + ": " + (state.notes.answers[q.id] || "").trim().replace(/\.$/, "");
      }).join(" | ") + ".");
      var selfScore = state.marks.reduce(function (s, i) { return s + CLOSING_KEY.criteria[i].points; }, 0);
      parts.push("Self-marked " + selfScore + " of " + keyTotal() + " points on XLab's key.");
    }
    return parts.join(" ");
  }
  function keyTotal() { return CLOSING_KEY.criteria.reduce(function (s, c) { return s + c.points; }, 0); }

  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (!completed && state.secondOrderDone) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }
  function update(fn) { fn(state); persist(); render(); }

  // ---------- DOM helpers ----------
  var SVG_NS = "http://www.w3.org/2000/svg";
  function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
  function svg(tag, attrs) { var n = document.createElementNS(SVG_NS, tag); if (attrs) Object.keys(attrs).forEach(function (k) { n.setAttribute(k, attrs[k]); }); return n; }
  function btn(text, className, onClick, key) {
    var b = el("button", className, text); b.type = "button";
    if (key) b.setAttribute("data-key", key);
    b.addEventListener("click", onClick);
    return b;
  }
  function para(className, text) { return el("p", className, text); }
  function quoteLine(q) {
    var p = el("p", "quote");
    p.appendChild(document.createTextNode("“" + q.text + "” "));
    p.appendChild(el("span", "where", "(Baker et al., " + q.where + ")"));
    return p;
  }
  function inline(parts) { var s = el("span"); parts.forEach(function (x) { s.appendChild(typeof x === "string" ? document.createTextNode(x) : x); }); return s; }
  function icon(kind) {
    var s = svg("svg", { viewBox: "0 0 16 16", class: "mark", "aria-hidden": "true" });
    s.appendChild(svg("circle", { cx: 8, cy: 8, r: 7, fill: "none", stroke: kind === "ok" ? "#b87018" : "#5a5a5a", "stroke-width": 1.5 }));
    if (kind === "ok") s.appendChild(svg("path", { d: "M4.5 8.5 L7 11 L11.5 5.5", fill: "none", stroke: "#b87018", "stroke-width": 1.75, "stroke-linecap": "round", "stroke-linejoin": "round" }));
    else { s.appendChild(svg("path", { d: "M8 4.5 V9", stroke: "#5a5a5a", "stroke-width": 1.75, "stroke-linecap": "round" })); s.appendChild(svg("circle", { cx: 8, cy: 11.5, r: 1, fill: "#5a5a5a" })); }
    return s;
  }

  // ---------- Ring map geometry (from XLab: actor-board.tsx) ----------
  var CX = 480, CY = 350;
  var RADII = { declares: 84, evidence: 150, verifies: 216, undeclared: 278 };
  var VIEW = { x: 0, y: 2, w: 960, h: 696 };
  var NODE_HIT_RADIUS = 18, DRAG_THRESHOLD = 4, BEAM_END_WIDTH = 4.5;
  var HEAD_TIP_INSET = 7, HEAD_LENGTH = 20, HEAD_NOTCH = 13, HEAD_BARB_WIDTH = BEAM_END_WIDTH * 2.5;
  var STEP_DEG = 360 / MAP_SLOTS.length;
  function angleOf(id) { var i = MAP_SLOTS.indexOf(id); return (-90 + STEP_DEG / 2 + STEP_DEG * i) * (Math.PI / 180); }
  function pointOf(id) { var a = angleOf(id), r = RADII[RING_KEY[id]]; return { x: CX + Math.cos(a) * r, y: CY + Math.sin(a) * r }; }
  function normal(dx, dy) { var l = Math.hypot(dx, dy) || 1; return { x: -dy / l, y: dx / l }; }
  function beamPath(from, to, control) {
    var endWidth = BEAM_END_WIDTH, middleWidth = 1.4;
    var sN = normal(control.x - from.x, control.y - from.y), eN = normal(to.x - control.x, to.y - control.y), mN = normal(to.x - from.x, to.y - from.y);
    var off = 2 * middleWidth - endWidth;
    return ["M " + (from.x + sN.x * endWidth) + " " + (from.y + sN.y * endWidth),
      "Q " + (control.x + mN.x * off) + " " + (control.y + mN.y * off), (to.x + eN.x * endWidth) + " " + (to.y + eN.y * endWidth),
      "L " + (to.x - eN.x * endWidth) + " " + (to.y - eN.y * endWidth),
      "Q " + (control.x - mN.x * off) + " " + (control.y - mN.y * off), (from.x - sN.x * endWidth) + " " + (from.y - sN.y * endWidth) + " Z"].join(" ");
  }
  function edgeControl(from, to, bend) {
    var mid = { x: (from.x + to.x) / 2, y: (from.y + to.y) / 2 };
    var pulled = { x: mid.x + (CX - mid.x) * 0.35, y: mid.y + (CY - mid.y) * 0.35 };
    if (!bend) return pulled;
    var dx = to.x - from.x, dy = to.y - from.y, l = Math.hypot(dx, dy) || 1;
    return { x: pulled.x + (-dy / l) * bend, y: pulled.y + (dx / l) * bend };
  }
  function arrowheadPath(control, to) {
    var dx = to.x - control.x, dy = to.y - control.y, l = Math.hypot(dx, dy) || 1, ux = dx / l, uy = dy / l, nx = -uy, ny = ux;
    var tip = { x: to.x - ux * HEAD_TIP_INSET, y: to.y - uy * HEAD_TIP_INSET };
    var at = function (back, side) { return (tip.x - ux * back + nx * side) + " " + (tip.y - uy * back + ny * side); };
    return ["M " + tip.x + " " + tip.y, "Q " + at(10, 2.75) + " " + at(HEAD_LENGTH, HEAD_BARB_WIDTH), "L " + at(HEAD_NOTCH, 0), "L " + at(HEAD_LENGTH, -HEAD_BARB_WIDTH), "Q " + at(10, -2.75) + " " + tip.x + " " + tip.y, "Z"].join(" ");
  }
  function trimForHead(p, control) {
    var dx = control.x - p.x, dy = control.y - p.y, l = Math.hypot(dx, dy) || 1, d = Math.min(HEAD_TIP_INSET + HEAD_NOTCH, l / 2);
    return { x: p.x + (dx / l) * d, y: p.y + (dy / l) * d };
  }
  var EDGE_PAINT = {
    drawn: { stroke: "#b87018", width: 1.5 },
    right: { stroke: "#b87018", width: 1.75 },
    wrong: { stroke: "#1a1a1a", width: 1.5, dash: "2 3" },
    missed: { stroke: "#5a5a5a", width: 1.25, dash: "6 4" }
  };
  function nearestActor(point, except) {
    var nearest = null, best = NODE_HIT_RADIUS;
    ACTORS.forEach(function (a) {
      if (a.id === except) return;
      var p = pointOf(a.id), d = Math.hypot(point.x - p.x, point.y - p.y);
      if (d <= best) { nearest = a.id; best = d; }
    });
    return nearest;
  }

  // ---------- Interactions ----------
  function toggleEdge(id) {
    update(function (s) { if (has(s.edges, id)) s.edges = s.edges.filter(function (e) { return e !== id; }); else s.edges.push(id); });
  }
  function canDraw() { return state.edgeStep === "edges" && !state.edgesDone; }
  function chooseActor(id) {
    if (!canDraw()) return;
    if (ui.source === id) { ui.source = null; render(); return; }
    if (ui.source) { var from = ui.source; ui.source = null; toggleEdge(edgeId(from, id)); return; }
    ui.source = id; render();
  }

  function renderMap(root) {
    var box = el("div", "mapbox");
    var interactive = canDraw();
    var lens = state.edgeStep === "map" ? ui.lens : null;
    var s = svg("svg", { viewBox: VIEW.x + " " + VIEW.y + " " + VIEW.w + " " + VIEW.h, role: interactive ? "group" : "img" });
    s.setAttribute("aria-label", interactive
      ? "Interactive actor map. Drag from an evidence source to the actor the evidence concerns, or select the two points in order."
      : "Concentric actor map: the regulated training run at the centre, actors on four rings around it: who declares, who holds evidence, who verifies, and what no declaration covers. Edges join actors that can produce evidence about one another.");

    RINGS.slice().reverse().forEach(function (ring) {
      s.appendChild(svg("circle", { cx: CX, cy: CY, r: RADII[ring.id], fill: "none", stroke: "#e8e5df", "stroke-width": 1 }));
      var t = svg("text", { x: CX, y: CY - RADII[ring.id] - 10, "text-anchor": "middle", fill: "#5a5a5a", "font-size": 10, "letter-spacing": "0.08em" });
      t.textContent = ring.name.toUpperCase();
      s.appendChild(t);
    });
    s.appendChild(svg("circle", { cx: CX, cy: CY, r: 4, fill: "#b87018" }));
    var c1 = svg("text", { x: CX, y: CY + 20, "text-anchor": "middle", fill: "#1a1a1a", "font-size": 11, "font-weight": 600 }); c1.textContent = CENTRE.label; s.appendChild(c1);
    var c2 = svg("text", { x: CX, y: CY + 34, "text-anchor": "middle", fill: "#5a5a5a", "font-size": 10 }); c2.textContent = CENTRE.sub; s.appendChild(c2);

    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var edges = !state.edgesDone
      ? state.edges.map(function (id) { return { id: id, state: "drawn" }; })
      : score.found.map(function (id) { return { id: id, state: "right" }; })
        .concat(score.reversed.map(function (id) { return { id: id, state: "wrong" }; }))
        .concat(score.extra.map(function (id) { return { id: id, state: "wrong" }; }))
        .concat(score.missed.map(function (id) { return { id: id, state: "missed" }; }));
    var edgeIndex = {}; edges.forEach(function (e) { edgeIndex[e.id] = e; });
    edges.forEach(function (edge) {
      var e = splitEdge(edge.id), a = pointOf(e.from), b = pointOf(e.to);
      var partner = edgeIndex[edgeId(e.to, e.from)];
      var twoHeaded = partner !== undefined && partner.state === edge.state;
      if (twoHeaded && edgeId(e.to, e.from) < edge.id) return;
      var paint = EDGE_PAINT[edge.state];
      var control = edgeControl(a, b, partner !== undefined && !twoHeaded ? 12 : 0);
      var beam = beamPath(twoHeaded ? trimForHead(a, control) : a, trimForHead(b, control), control);
      var g = svg("g");
      g.appendChild(svg("path", { d: beam, fill: paint.dash ? "none" : paint.stroke, stroke: paint.dash ? paint.stroke : "none", "stroke-width": paint.width, "stroke-dasharray": paint.dash || "none", "stroke-linecap": "round", "stroke-linejoin": "round" }));
      g.appendChild(svg("path", { d: arrowheadPath(control, b), fill: paint.stroke }));
      if (twoHeaded) g.appendChild(svg("path", { d: arrowheadPath(control, a), fill: paint.stroke }));
      s.appendChild(g);
    });

    var draftLayer = svg("g", { fill: "#b87018", "pointer-events": "none" });
    s.appendChild(draftLayer);

    ACTORS.forEach(function (actor) {
      var p = pointOf(actor.id), angle = angleOf(actor.id), outward = Math.cos(angle) >= 0 ? 1 : -1;
      var lit = lens ? has(actor.roles, lens) : false;
      var absent = !!ABSENT[actor.id];
      var selected = interactive && ui.source === actor.id;
      var g = svg("g", { class: "node" + (interactive ? " is-interactive" : ""), "data-actor-id": actor.id });
      if (interactive) {
        g.setAttribute("role", "button"); g.setAttribute("tabindex", "0"); g.setAttribute("aria-pressed", selected ? "true" : "false");
        g.setAttribute("data-key", "node:" + actor.id);
        g.setAttribute("aria-label", ui.source && ui.source !== actor.id ? "Draw an edge from " + labelOf(ui.source) + " to " + actor.label
          : selected ? actor.label + ". Clear the selected source." : actor.label + ". Select as the evidence source.");
        g.appendChild(svg("circle", { class: "hit", cx: p.x, cy: p.y, r: NODE_HIT_RADIUS, fill: "transparent", "pointer-events": "all" }));
        wireNode(g, s, actor.id, draftLayer);
      }
      if (selected) g.appendChild(svg("circle", { cx: p.x, cy: p.y, r: 11, fill: "none", stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "3 2", "pointer-events": "none" }));
      var dot = svg("circle", { cx: p.x, cy: p.y, r: absent ? 7 : lit ? 8 : 6.5, "pointer-events": "none", fill: absent ? "none" : lit ? "#b87018" : "#1a1a1a", opacity: lens && !lit ? 0.3 : 1 });
      if (absent) { dot.setAttribute("stroke", "#5a5a5a"); dot.setAttribute("stroke-width", 1.25); dot.setAttribute("stroke-dasharray", "3 2"); }
      g.appendChild(dot);
      var t = svg("text", { x: p.x + outward * 14, y: p.y + 3.5, "text-anchor": outward > 0 ? "start" : "end", "font-size": 11, "font-weight": lit || selected ? 600 : 400, fill: lit ? "#b87018" : "#1a1a1a", opacity: lens && !lit ? 0.35 : 1, "pointer-events": "none" });
      t.textContent = actor.label;
      g.appendChild(t);
      s.appendChild(g);
    });
    box.appendChild(s);

    if (interactive) {
      var status = para("note"); status.setAttribute("aria-live", "polite"); status.id = "map-status";
      status.textContent = ui.source ? labelOf(ui.source) + " is the source. Drag from it, or select a target point." : "Drag from a source point to a target point, or select the two points in order.";
      box.appendChild(status);
    }
    if (state.edgesDone) {
      var legend = el("div", "legend");
      legend.appendChild(legendItem("right", "solid: in the key"));
      legend.appendChild(legendItem("wrong", "dotted: reversed or not in the key"));
      legend.appendChild(legendItem("missed", "dashed: in the key, not drawn"));
      box.appendChild(legend);
    }
    var note = para("note");
    note.appendChild(document.createTextNode("Rings run outward from the compute use the agreement forbids: who has to declare it, who holds evidence about the declaration, who checks it, and what no declaration covers. The centre is the paper’s own scope: “" + CENTRE.baker.text + "” (Baker et al., " + CENTRE.baker.where + ")."));
    box.appendChild(note);
    root.appendChild(box);
  }
  function legendItem(kind, text) {
    var paint = EDGE_PAINT[kind];
    var sp = el("span");
    var s = svg("svg", { viewBox: "0 0 28 10", "aria-hidden": "true" });
    s.appendChild(svg("line", { x1: 1, y1: 5, x2: 27, y2: 5, stroke: paint.stroke, "stroke-width": 2, "stroke-dasharray": paint.dash || "none" }));
    sp.appendChild(s); sp.appendChild(document.createTextNode(text));
    return sp;
  }

  function pointerPoint(svgEl, event) {
    var rect = svgEl.getBoundingClientRect();
    var w = rect.width || VIEW.w, h = rect.height || VIEW.h;
    return { x: VIEW.x + ((event.clientX - rect.left) / w) * VIEW.w, y: VIEW.y + ((event.clientY - rect.top) / h) * VIEW.h };
  }
  function drawDraft(layer, from, end) {
    while (layer.firstChild) layer.removeChild(layer.firstChild);
    if (!end) return;
    var start = pointOf(from);
    if (Math.hypot(end.x - start.x, end.y - start.y) <= 1) return;
    var control = edgeControl(start, end, 0);
    layer.appendChild(svg("path", { d: beamPath(start, trimForHead(end, control), control) }));
    layer.appendChild(svg("path", { d: arrowheadPath(control, end) }));
  }
  function setHover(svgEl, id) {
    var nodes = svgEl.querySelectorAll(".node");
    for (var i = 0; i < nodes.length; i++) {
      var old = nodes[i].querySelector(".hover-ring");
      if (old) nodes[i].removeChild(old);
      if (id && nodes[i].getAttribute("data-actor-id") === id) {
        var p = pointOf(id);
        nodes[i].insertBefore(svg("circle", { class: "hover-ring", cx: p.x, cy: p.y, r: 11, fill: "none", stroke: "#b87018", "stroke-width": 2, "pointer-events": "none" }), nodes[i].firstChild.nextSibling);
      }
    }
  }
  function wireNode(g, svgEl, id, draftLayer) {
    g.addEventListener("pointerdown", function (event) {
      if (!canDraw()) return;
      event.preventDefault();
      try { g.setPointerCapture(event.pointerId); } catch (e) {}
      var p = pointerPoint(svgEl, event);
      ui.draft = { from: id, hover: null, pointerId: event.pointerId, startX: p.x, startY: p.y, x: p.x, y: p.y };
    });
    g.addEventListener("pointermove", function (event) {
      var d = ui.draft;
      if (!d || d.pointerId !== event.pointerId) return;
      event.preventDefault();
      var p = pointerPoint(svgEl, event);
      d.x = p.x; d.y = p.y;
      var moved = Math.hypot(p.x - d.startX, p.y - d.startY) >= DRAG_THRESHOLD;
      var target = moved ? nearestActor(p, d.from) : null;
      if (target !== d.hover) { d.hover = target; setHover(svgEl, target); }
      drawDraft(draftLayer, d.from, moved ? (target ? pointOf(target) : p) : null);
    });
    g.addEventListener("pointerup", function (event) {
      var d = ui.draft;
      if (!d || d.pointerId !== event.pointerId) return;
      event.preventDefault();
      var p = pointerPoint(svgEl, event);
      var moved = Math.hypot(p.x - d.startX, p.y - d.startY) >= DRAG_THRESHOLD;
      var target = nearestActor(p, d.from);
      try { g.releasePointerCapture(event.pointerId); } catch (e) {}
      ui.draft = null;
      if (moved && target) { ui.source = null; toggleEdge(edgeId(d.from, target)); }
      else if (moved) { ui.source = d.from; render(); }
      else { chooseActor(d.from); }
    });
    g.addEventListener("pointercancel", function () { ui.draft = null; drawDraft(draftLayer, id, null); setHover(svgEl, null); });
    g.addEventListener("keydown", function (event) {
      if (event.key !== "Enter" && event.key !== " ") return;
      event.preventDefault();
      chooseActor(id);
    });
    // Click fallback for environments without pointer events (tap = select source, tap again = target).
    g.addEventListener("click", function (event) {
      if (typeof window.PointerEvent !== "undefined") return;
      event.preventDefault();
      chooseActor(id);
    });
  }

  // ---------- Sections ----------
  function renderBrief(root) {
    var card = el("div", "card");
    card.appendChild(para("eyebrow", "The brief"));
    card.appendChild(para(null, "Same agreement, same board: no training runs above a compute threshold for three months. 1.2 asked what part each actor plays in a declaration. This asks what a verifier could actually do with them: who can produce evidence about whom, and which of the four things a verifier has to establish that evidence would settle."));
    card.appendChild(para("muted", "The rings below are the key from 1.2, not your answer. Placing the board yourself is the workshop in 1.2, and it is worth doing first. Nothing here is gated on it."));
    root.appendChild(card);
  }

  function renderStepHeader(root) {
    var idx = state.edgeStep === "map" ? 1 : 0, step = STEPS[idx];
    var wrap = el("div");
    var row = el("div", "row tight");
    var h = el("h2", null, (idx + 1) + ". " + step.name);
    row.appendChild(h);
    row.appendChild(para("muted small", "Step " + (idx + 1) + " of " + STEPS.length + " · " + step.beeck));
    wrap.appendChild(row);
    var meter = el("div", "meter"); meter.setAttribute("role", "img"); meter.setAttribute("aria-label", "Step " + (idx + 1) + " of " + STEPS.length);
    STEPS.forEach(function (_, i) { meter.appendChild(el("span", i <= idx ? "on" : "")); });
    wrap.appendChild(meter);
    root.appendChild(wrap);
  }

  function renderTask(root) {
    var card = el("div", "card");
    card.appendChild(para("eyebrow", "What an edge means"));
    var p1 = el("p");
    p1.appendChild(inline(["Draw an edge from ", el("strong", null, "A"), " to ", el("strong", null, "B"), " when A can produce evidence about B, for a verifier, that B did not have to volunteer. Not influence, not dependence: evidence. Direction is the claim: a cloud provider holds records about a lab’s training run, and the lab holds nothing comparable about the cloud. A verifier can be its own source, so an edge may start on the third ring."]));
    card.appendChild(p1);
    card.appendChild(para("muted", "On the graph, drag from the actor that produces the evidence to the actor the evidence concerns. You can also select one point and then another; the lists below remain available as a keyboard-friendly alternative."));
    card.appendChild(para("muted", "Some actors will end up with no edge at all. That is an available answer and, for most of them, the right one. One of them can hold no edge in principle: the hollow ring on the map is a body that does not exist, and nothing that does not exist produces evidence."));
    var sep = el("div", "sep");
    sep.appendChild(para("medium", "What a verifier has to establish, in four parts"));
    sep.appendChild(para("muted", "Baker et al. decompose it this way, and the key tags every edge with the part it serves. Draw an edge when you can say which of these four it would help settle."));
    var ol = el("ol", "tight"); ol.style.marginTop = "8px";
    SUBGOALS.forEach(function (sg) { var li = el("li"); li.appendChild(inline([el("span", "medium", sg.label + "."), " ", el("span", "muted", sg.name)])); ol.appendChild(li); });
    sep.appendChild(ol);
    card.appendChild(sep);
    root.appendChild(card);
  }

  function renderLensRow(root) {
    var row = el("div", "chips"); row.style.alignItems = "center";
    row.appendChild(el("span", "muted small", "Light up a role:"));
    ROLES.forEach(function (role) {
      var b = btn(role.name, "chip" + (ui.lens === role.id ? " is-active" : ""), function () { ui.lens = ui.lens === role.id ? null : role.id; render(); }, "lens:" + role.id);
      b.setAttribute("aria-pressed", ui.lens === role.id ? "true" : "false");
      row.appendChild(b);
    });
    root.appendChild(row);
  }

  function renderRoster(root) {
    var row = el("div", "row tight"); row.style.justifyContent = "flex-start";
    row.appendChild(btn(ui.rosterOpen ? "Close the roster" : "Open the roster", "chip", function () {
      var opening = !ui.rosterOpen;
      ui.rosterOpen = opening;
      if (opening && !state.peeked) update(function (s) { s.peeked = true; }); else render();
    }, "roster"));
    row.appendChild(para("muted small", state.peeked ? "Opened during the workshop: the closing map says so." : "Closed since you started. Everything below is from memory."));
    root.appendChild(row);
    if (!ui.rosterOpen) return;
    var card = el("div", "card");
    var ol = el("ol", "list");
    ACTORS.forEach(function (a) {
      var li = el("li");
      li.appendChild(para("strong", a.name));
      li.appendChild(para("muted", a.position + (a.note ? " " + a.note : "")));
      ol.appendChild(li);
    });
    card.appendChild(ol);
    var sep = el("div", "sep");
    sep.appendChild(para("eyebrow", "Four rings: what part of a declaration you play"));
    sep.appendChild(para("muted", "A verification regime runs on declarations: somebody states what they own and what they did with it, somebody else establishes the statement is true and complete. Every actor is somewhere in that."));
    var rl = el("ol", "tight"); rl.style.marginTop = "8px";
    RINGS.forEach(function (r) { var li = el("li"); li.appendChild(inline([el("span", "medium", r.name + "."), " ", el("span", "muted", r.test)])); rl.appendChild(li); });
    sep.appendChild(rl);
    card.appendChild(sep);
    var grid = el("div", "grid2 sep");
    var left = el("div"); left.appendChild(para("eyebrow", "Six functional roles"));
    var ul1 = el("ul", "tight"); ul1.style.marginTop = "6px";
    ROLES.forEach(function (r) { var li = el("li"); li.appendChild(inline([el("span", "medium", r.name), " ", el("span", "muted", r.question)])); ul1.appendChild(li); });
    left.appendChild(ul1);
    var right = el("div"); right.appendChild(para("eyebrow", "Five postures"));
    var ul2 = el("ul", "tight"); ul2.style.marginTop = "6px";
    POSTURES.forEach(function (p) { var li = el("li"); li.appendChild(inline([el("span", "medium", p.name), " ", el("span", "muted", p.means)])); ul2.appendChild(li); });
    right.appendChild(ul2);
    grid.appendChild(left); grid.appendChild(right);
    card.appendChild(grid);
    root.appendChild(card);
  }

  function renderEdgesStep(root) {
    if (state.edgesDone) { renderVerdict(root); return; }
    var wrap = el("div", "stack");
    var src = el("div");
    src.appendChild(para("medium", "Who can produce the evidence?"));
    var chips = el("div", "chips");
    ACTORS.forEach(function (a) {
      var out = state.edges.filter(function (e) { return e.indexOf(a.id + ">") === 0; }).length;
      var b = btn(a.label + (out ? " " : ""), "chip" + (ui.source === a.id ? " is-active" : ""), function () { ui.source = a.id; render(); }, "src:" + a.id);
      if (out) b.appendChild(el("span", "muted", String(out)));
      b.setAttribute("aria-pressed", ui.source === a.id ? "true" : "false");
      b.setAttribute("aria-label", "Draw from " + a.label + (out ? ", " + out + " drawn" : ""));
      chips.appendChild(b);
    });
    src.appendChild(chips);
    wrap.appendChild(src);

    if (ui.source) {
      var tgt = el("div");
      tgt.appendChild(para("medium", "About whom? " + labelOf(ui.source) + " can show a verifier something about…"));
      var tchips = el("div", "chips");
      ACTORS.forEach(function (a) {
        if (a.id === ui.source) return;
        var id = edgeId(ui.source, a.id), on = has(state.edges, id);
        var b = btn((on ? "✓ " : "") + a.label, "chip" + (on ? " is-active" : ""), function () { toggleEdge(id); }, "tgt:" + a.id);
        b.setAttribute("aria-pressed", on ? "true" : "false");
        b.setAttribute("aria-label", labelOf(ui.source) + " can show a verifier something about " + a.label);
        tchips.appendChild(b);
      });
      tgt.appendChild(tchips);
      wrap.appendChild(tgt);
    } else {
      wrap.appendChild(para("muted small", "Select a source on the graph or in the list above, then choose whom its evidence concerns."));
    }

    if (state.edges.length) {
      var card = el("div", "card");
      card.appendChild(para("eyebrow", state.edges.length + " edge" + (state.edges.length === 1 ? "" : "s") + " drawn"));
      var ul = el("ul", "tight"); ul.style.marginTop = "8px";
      state.edges.forEach(function (id) {
        var li = el("li");
        var b = btn(edgeLabel(id) + " ", "link", function () { toggleEdge(id); }, "rm:" + id);
        b.appendChild(el("span", "muted", "✕"));
        b.setAttribute("aria-label", "Remove " + edgeLabel(id));
        li.appendChild(b); ul.appendChild(li);
      });
      card.appendChild(ul);
      wrap.appendChild(card);
    }

    var foot = el("div", "row");
    foot.appendChild(para("muted small", "Commit when the board says what you think it says. There is no target number."));
    var commit = btn("Commit the edges", "primary", function () { ui.source = null; update(function (s) { s.edgesDone = true; }); }, "commit-edges");
    commit.disabled = !state.edges.length;
    foot.appendChild(commit);
    wrap.appendChild(foot);
    root.appendChild(wrap);
  }

  function renderVerdict(root) {
    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var wrap = el("div", "stack");
    var head = el("div", "row");
    var line = el("p");
    line.appendChild(inline([el("span", "strong", score.found.length + " of " + EDGE_KEY.length), " edges in the key." +
      (score.reversed.length ? " " + score.reversed.length + " drawn the other way round." : "") +
      (score.extra.length ? " " + score.extra.length + " the key does not have." : "")]));
    head.appendChild(line);
    head.appendChild(btn("Edit my edges", "", function () { ui.source = null; update(function (s) { s.edgesDone = false; s.edgeStep = "edges"; }); }, "edit-edges"));
    wrap.appendChild(head);

    var ol = el("ol", "list");
    SUBGOALS.forEach(function (sg) {
      var edges = EDGE_KEY.filter(function (e) { return e.subgoal === sg.id; });
      var li = el("li");
      var title = el("p");
      title.appendChild(inline([el("span", "strong", "Subgoal " + sg.label + " · " + sg.name), " ", el("span", "muted", "(" + edges.length + " edge" + (edges.length === 1 ? "" : "s") + ")")]));
      li.appendChild(title);
      li.appendChild(quoteLine(sg.baker));
      var ul = el("ul"); ul.style.marginTop = "12px";
      edges.forEach(function (edge) {
        var id = edgeId(edge.from, edge.to);
        var got = has(score.found, id);
        var flipped = has(score.reversed, edgeId(edge.to, edge.from));
        var item = el("li"); item.style.marginTop = "12px";
        var l = el("p", "verdict-line");
        l.appendChild(icon(got ? "ok" : "alert"));
        var txt = el("span");
        txt.appendChild(el("span", "medium", edgeLabel(id)));
        if (!got) txt.appendChild(el("span", "muted", flipped ? ": you drew it the other way round." : ": not drawn."));
        l.appendChild(txt);
        item.appendChild(l);
        var what = para("muted", edge.what); what.style.marginTop = "4px";
        item.appendChild(what);
        edge.baker.forEach(function (q) { item.appendChild(quoteLine(q)); });
        ul.appendChild(item);
      });
      li.appendChild(ul);
      ol.appendChild(li);
    });
    wrap.appendChild(ol);

    if (score.extra.length) {
      var card = el("div", "card");
      card.appendChild(para("strong", "Edges the key does not have"));
      card.appendChild(para("muted", "Not automatically wrong: the key holds only what this framework supports, and it is a framework about declarations rather than about power. Ask of each one: which of the four subgoals would it complete, and with what mechanism? If you can answer that, argue with the key."));
      var ul2 = el("ul", "tight"); ul2.style.marginTop = "8px";
      score.extra.forEach(function (id) { ul2.appendChild(el("li", null, edgeLabel(id))); });
      card.appendChild(ul2);
      wrap.appendChild(card);
    }

    var notes = el("div");
    var noEdge = EDGE_NOTES.reduce(function (n, x) { return n + x.actorIds.length; }, 0);
    notes.appendChild(para("strong", "The " + noEdge + " with no edge at all"));
    var nl = el("ol", "list"); nl.style.marginTop = "12px";
    EDGE_NOTES.forEach(function (note) {
      var li = el("li");
      li.appendChild(para("medium", note.actorIds.map(labelOf).join(" · ")));
      var why = para("muted", note.why); why.style.marginTop = "2px";
      li.appendChild(why);
      note.baker.forEach(function (q) { li.appendChild(quoteLine(q)); });
      nl.appendChild(li);
    });
    notes.appendChild(nl);
    wrap.appendChild(notes);

    var next = el("div");
    next.appendChild(btn("Read what it says", "primary", function () { update(function (s) { s.edgeStep = "map"; }); scrollTop(); }, "to-map"));
    wrap.appendChild(next);
    root.appendChild(wrap);
  }

  function renderMapStep(root) {
    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var wrap = el("div", "stack");
    var c1 = el("div", "card");
    c1.appendChild(para("strong", MAP_FINDING.title));
    MAP_FINDING.body.forEach(function (p) { c1.appendChild(para(null, p)); });
    wrap.appendChild(c1);
    var c2 = el("div", "card");
    c2.appendChild(para("strong", EDGE_FINDING.title));
    EDGE_FINDING.body.forEach(function (p) { c2.appendChild(para(null, p)); });
    c2.appendChild(quoteLine(EDGE_FINDING.weakLink));
    c2.appendChild(quoteLine(EDGE_FINDING.redundancy));
    wrap.appendChild(c2);

    var so = el("div");
    so.appendChild(para("strong", "Now take one off the board"));
    var stem = para(null, SECOND_ORDER.stem); stem.style.marginTop = "8px";
    so.appendChild(stem);
    var radio = el("div", "radio"); radio.setAttribute("role", "radiogroup"); radio.setAttribute("aria-label", SECOND_ORDER.stem); radio.style.marginTop = "8px";
    var committed = state.secondOrderDone;
    SECOND_ORDER_SHOWN.forEach(function (o) {
      var chosen = state.secondOrder === o.id;
      var cls = "";
      if (!committed && chosen) cls = "is-active";
      if (committed && o.correct) cls = "is-correct";
      if (committed && chosen && !o.correct) cls = "is-wrong";
      if (committed && !o.correct && !chosen) cls = "is-dim";
      var b = btn("", cls, function () { if (!committed) update(function (s) { s.secondOrder = o.id; }); }, "so:" + o.id);
      b.setAttribute("role", "radio"); b.setAttribute("aria-checked", chosen ? "true" : "false");
      b.disabled = committed;
      b.appendChild(inline([committed && o.correct ? "✓ " : "", o.text, committed && chosen ? el("span", "muted", chosen && o.correct ? " (your answer)" : " (your answer, not the key’s)") : ""]));
      radio.appendChild(b);
    });
    so.appendChild(radio);
    if (committed) {
      var ol = el("ol", "tight"); ol.style.marginTop = "12px";
      SECOND_ORDER.options.forEach(function (o) {
        var li = el("li");
        li.appendChild(inline([el("span", o.correct ? "medium" : "medium muted", (o.correct ? "✓ " : "") + o.text), " ", el("span", "muted", o.why)]));
        ol.appendChild(li);
      });
      so.appendChild(ol);
      var lesson = el("div", "card"); lesson.style.marginTop = "12px";
      lesson.appendChild(para(null, SECOND_ORDER.lesson));
      so.appendChild(lesson);
    } else {
      var cb = btn("Commit", "primary", function () { update(function (s) { s.secondOrderDone = true; }); }, "commit-so");
      cb.disabled = !state.secondOrder; cb.style.marginTop = "12px";
      so.appendChild(cb);
    }
    wrap.appendChild(so);

    wrap.appendChild(para("muted small", score.found.length + " of " + EDGE_KEY.length + " edges in the key." + (state.peeked ? " Roster reopened during the workshop." : "")));

    renderWriting(wrap);
    root.appendChild(wrap);
  }

  function criteriaText(q) {
    var lines = [];
    var total = 0;
    q.criteria.forEach(function (i) {
      var c = CLOSING_KEY.criteria[i]; total += c.points;
      lines.push("(" + c.points + " point" + (c.points === 1 ? "" : "s") + ") " + c.text + (c.needsReasoning ? " " + REASONING_LINE : "") + (c.grounds ? " Grounds: " + c.grounds : ""));
    });
    var noCredit = q.noCredit.map(function (i) { return CLOSING_KEY.noCredit[i]; });
    return "Mark against XLab's key, " + total + " point" + (total === 1 ? "" : "s") + " in total; report the score as points earned divided by " + total + ", scaled 0 to 100. Any wording that does not distort the meaning counts; no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing. Criteria: " + lines.join(" ") + " No credit: " + noCredit.join(" ") + " No generic praise.";
  }

  function submitAnswer(q, statusEl, again) {
    if (!window.Lens || !Lens.submit) return;
    var answer = (state.notes.answers[q.id] || "").trim();
    if (!answer) return;
    ui.pending[q.id] = true;
    statusEl.textContent = again ? "Scoring again…" : "Saved. Scoring…";
    Lens.submit({
      item: q.id,
      question: q.title,
      answer: answer,
      assessmentInstructions: criteriaText(q),
      feedbackInstructions: "Say which criteria the answer meets and which it misses, quoting the learner's own words where the reasoning is on the page and asking for it where it is not. Do not supply the missing reasoning yourself. No praise."
    }).then(function (result) {
      ui.pending[q.id] = false;
      if (result && typeof result.score === "number") { state.scores[q.id] = result.score; persist(); }
      statusEl.textContent = (result && typeof result.score === "number") ? "Score: " + result.score + " / 100. Keep editing if you want, it stays saved." : "Saved. Scoring is taking a while; keep editing if you want, it stays saved.";
    }, function () {
      ui.pending[q.id] = false;
      statusEl.textContent = "Saved. Could not score the answer right now.";
    });
  }

  function renderWriting(root) {
    if (!ui.writingOpen) {
      var card = el("div", "card");
      var t = el("p", "strong");
      t.appendChild(inline([el("span", "muted", "Optional: "), "Three questions to take away"]));
      card.appendChild(t);
      card.appendChild(para("muted", "Written answers, about fifteen minutes, with the criteria a marker would use. The exercise is finished without them; they are here for the reader who wants to argue with the board rather than read it."));
      var b = btn("Open them", "", function () { ui.writingOpen = true; render(); }, "open-writing"); b.style.marginTop = "12px";
      card.appendChild(b);
      root.appendChild(card);
      return;
    }
    var wrap = el("div", "stack");
    var answered = CLOSING_QUESTIONS.filter(function (q) { return state.notes.done[q.id]; }).length;
    var count = para("muted small", answered + " of " + CLOSING_QUESTIONS.length + " answered"); count.style.textAlign = "right";
    wrap.appendChild(count);
    CLOSING_QUESTIONS.forEach(function (q) {
      var card = el("div", "card");
      card.appendChild(el("h3", null, q.n + ". " + q.title));
      var ta = el("textarea"); ta.rows = 7; ta.value = state.notes.answers[q.id] || ""; ta.placeholder = "Answer from the map you just drew."; ta.setAttribute("aria-label", q.title); ta.setAttribute("data-key", "ta:" + q.id);
      ta.addEventListener("input", function () { state.notes.answers[q.id] = ta.value; persist(); });
      card.appendChild(ta);
      var foot = el("div", "row"); foot.style.marginTop = "12px";
      var status = para("muted small");
      if (state.notes.done[q.id]) {
        status.textContent = typeof state.scores[q.id] === "number" ? "Score: " + state.scores[q.id] + " / 100. Keep editing if you want, it stays saved." : "Saved. Keep editing if you want, it stays saved.";
        foot.appendChild(status);
        foot.appendChild(btn("Score again", "", function () { submitAnswer(q, status, true); }, "again:" + q.id));
      } else {
        foot.appendChild(status);
        foot.appendChild(btn("Save answer", "primary", function () {
          if (!(state.notes.answers[q.id] || "").trim()) { status.textContent = "Write an answer first."; return; }
          state.notes.done[q.id] = true; persist(); render();
          var fresh = document.querySelector('[data-key="status:' + q.id + '"]');
          if (fresh) submitAnswer(q, fresh, false);
        }, "save:" + q.id));
      }
      status.setAttribute("data-key", "status:" + q.id);
      card.appendChild(foot);
      wrap.appendChild(card);
    });
    renderMarkingKey(wrap);
    root.appendChild(wrap);
  }

  function renderMarkingKey(root) {
    var sec = el("div", "card");
    var head = el("div", "row tight");
    head.appendChild(para("eyebrow", "Marking key"));
    var scored = state.marks.reduce(function (s, i) { return s + CLOSING_KEY.criteria[i].points; }, 0);
    var sc = para("muted small", scored + " / " + keyTotal()); sc.setAttribute("aria-live", "polite");
    head.appendChild(sc);
    sec.appendChild(head);
    sec.appendChild(para("muted", "Mark your own answer. Any wording that does not distort the meaning counts: no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing."));
    var ul = el("ul"); ul.style.marginTop = "12px";
    CLOSING_KEY.criteria.forEach(function (c, i) {
      var on = has(state.marks, i);
      var li = el("li"); if (i) li.style.marginTop = "8px";
      var b = btn("", "crit" + (on ? " is-active" : ""), function () { update(function (s) { s.marks = on ? s.marks.filter(function (n) { return n !== i; }) : s.marks.concat([i]); }); }, "crit:" + i);
      b.setAttribute("aria-pressed", on ? "true" : "false");
      var pts = el("span", "pts", String(c.points)); pts.setAttribute("aria-hidden", "true");
      b.appendChild(pts);
      var body = el("span");
      body.appendChild(el("span", null, (on ? "✓ " : "") + c.text));
      if (c.needsReasoning) { var r = el("span", "muted small", REASONING_LINE); r.style.display = "block"; body.appendChild(r); }
      if (c.grounds) { var g = el("span", "muted small", c.grounds); g.style.display = "block"; body.appendChild(g); }
      b.appendChild(body);
      li.appendChild(b); ul.appendChild(li);
    });
    sec.appendChild(ul);
    var nc = el("div"); nc.style.marginTop = "12px";
    nc.appendChild(para("eyebrow", "No credit"));
    var nl = el("ul", "tight"); nl.style.marginTop = "6px";
    CLOSING_KEY.noCredit.forEach(function (line) { nl.appendChild(el("li", "muted", "· " + line)); });
    nc.appendChild(nl);
    sec.appendChild(nc);
    var foot = para("muted small", "This score is yours. It is not sent anywhere, counts towards nothing, and completes nothing."); foot.style.marginTop = "12px";
    sec.appendChild(foot);
    root.appendChild(sec);
  }

  function scrollTop() { try { document.getElementById("app").scrollIntoView({ block: "nearest" }); } catch (e) {} }

  // ---------- Render ----------
  var app = document.getElementById("app");
  function render() {
    var active = document.activeElement, key = active && active.getAttribute ? active.getAttribute("data-key") : null;
    while (app.firstChild) app.removeChild(app.firstChild);
    renderBrief(app);
    renderStepHeader(app);
    if (canDraw()) renderTask(app);
    renderMap(app);
    if (state.edgeStep === "map") renderLensRow(app);
    renderRoster(app);
    if (state.edgeStep === "edges") renderEdgesStep(app);
    if (state.edgeStep === "map") {
      renderMapStep(app);
      var back = el("div");
      back.appendChild(btn("← " + STEPS[0].name, "chip", function () { update(function (s) { s.edgeStep = "edges"; }); scrollTop(); }, "back"));
      app.appendChild(back);
    }
    if (key) { var n = app.querySelector('[data-key="' + key + '"]'); if (n && n.focus) n.focus(); }
  }

  function hydrate(saved, meta) {
    state = prune(saved);
    completed = !!(meta && meta.completed);
    render();
  }

  if (window.Lens) {
    render();
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY)); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>
