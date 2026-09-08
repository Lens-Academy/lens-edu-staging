---
id: 'c206f69b-2c3a-4c62-aa04-5335adf22f1d'
title: The Anatomy Drill
summary_for_tutor: "A sorting drill on the seven organs of a binding agreement (the rule, the claims, the evidence, the confidentiality bargain, the adversary, the institution & consequences, the gap) plus a No-organ bin for advocacy. The learner reads thirteen short specimen texts one at a time, real and fictional, and drags each onto the organ it implements (or taps the specimen, then a bin). Each placement gets an instant verdict: correct on first read, a defensible near-tag that is accepted and moved to the sharper organ, or a miss; a wrong bin gets one retry, then the drill files the specimen for the learner with the explanation. Sources are hidden until the specimen is placed, so do not name a specimen's source before the learner commits. After the thirteenth specimen a results screen counts clean first reads, defensible near-tags and second looks, shows a table of where the specimens came from and their status in the world, then asks one final pick with no right answer: which organ to put at the top of a negotiating agenda (each pick has XLab's judgment). The full text of the fictional Reykjavik Protocol closes the page. Done means all thirteen specimens have been placed and the results screen is showing."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Anatomy Drill</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "anatomy-drill". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h2 { font-size: 22px; line-height: 1.2; }
  p { margin: 0; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; font-weight: 500; }
  button.primary:hover { background: var(--accent-hover); border-color: var(--accent-hover); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .stack > * + * { margin-top: 16px; }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
  .wrap { max-width: 44rem; margin: 0 auto; }

  /* intro */
  .organ-list { list-style: none; margin: 0; padding: 0; }
  .organ-list li { padding: 8px 0; border-top: 1px solid var(--border); }
  .organ-list li:first-child { border-top: 0; }
  .organ-list .name { font-weight: 600; }

  /* progress */
  .progress { display: flex; align-items: center; gap: 5px; flex-wrap: wrap; }
  .dot { width: 16px; height: 6px; border-radius: 3px; background: var(--border); border: 1px solid var(--border); }
  .dot.now { background: var(--text); border-color: var(--text); }
  .dot.clean { background: var(--accent); border-color: var(--accent); }
  .dot.near { background: #fff; border-color: var(--accent); }
  .dot.miss { background: var(--muted); border-color: var(--muted); }
  .progress .count { margin-left: auto; font-size: 12px; color: var(--muted); }

  /* specimen */
  .specimen { display: block; width: 100%; padding: 16px; cursor: grab; touch-action: none; user-select: none; -webkit-user-select: none; }
  .specimen:active { cursor: grabbing; }
  .specimen.armed { border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent); }
  .specimen.dragging { opacity: 0.4; }
  .specimen.retry { border-color: var(--muted); border-style: dashed; }
  .specimen .top { display: flex; justify-content: space-between; gap: 12px; font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted); margin-bottom: 8px; }
  .specimen .quote { display: block; font-size: 17px; line-height: 1.55; }
  .hint { text-align: center; font-size: 12px; color: var(--muted); font-style: italic; margin-top: 8px; }
  .filed .top { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted); margin-bottom: 6px; }

  /* bins */
  .bins { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  @media (min-width: 640px) { .bins { grid-template-columns: repeat(4, 1fr); } }
  .bin { border: 1px dashed var(--border); border-radius: 8px; padding: 10px; min-height: 86px; display: block; width: 100%; }
  .bin.full { grid-column: 1 / -1; min-height: 56px; display: flex; align-items: center; gap: 12px; }
  .bin:hover { border-color: var(--muted); background: var(--page); }
  .bin.ready { border-style: solid; border-color: var(--accent); }
  .bin.over { border-style: solid; border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent); background: var(--page); }
  .bin .bn { display: block; font-size: 13px; font-weight: 600; }
  .bin .bd { display: block; font-size: 11px; line-height: 1.35; color: var(--muted); margin-top: 4px; }
  .bin.full .bd { margin-top: 0; }

  /* feedback */
  .feedback { border-left-width: 3px; }
  .feedback.clean { border-left-color: var(--accent); }
  .feedback.near { border-left-color: var(--accent); border-left-style: double; }
  .feedback.miss { border-left-color: var(--muted); }
  .fb-head { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; font-weight: 600; margin-bottom: 8px; display: flex; gap: 6px; align-items: center; }
  .fb-head.clean, .fb-head.near { color: var(--accent); }
  .fb-head.miss { color: var(--muted); }
  .feedback p + p { margin-top: 8px; }
  .source { border-top: 1px dashed var(--border); margin-top: 10px; padding-top: 8px; font-size: 12px; color: var(--muted); font-style: italic; }
  .actions { margin-top: 16px; display: flex; gap: 8px; flex-wrap: wrap; }

  /* summary */
  .scores { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; }
  .score { border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 12px; text-align: center; }
  .score .n { font-size: 24px; font-weight: 600; font-family: var(--font-heading); }
  .score.clean .n, .score.near .n { color: var(--accent); }
  .score.miss .n { color: var(--muted); }
  .score .l { font-size: 11px; color: var(--muted); }
  .table-wrap { border: 1px solid var(--border); border-radius: 8px; overflow-x: auto; }
  table { border-collapse: collapse; width: 100%; min-width: 520px; font-size: 13px; }
  th { font-size: 10px; letter-spacing: 0.09em; text-transform: uppercase; color: var(--muted); text-align: left; padding: 8px 12px; border-bottom: 1px solid var(--border); font-weight: 500; }
  td { padding: 8px 12px; border-bottom: 1px solid var(--border); vertical-align: top; }
  tr:last-child td { border-bottom: 0; }
  .punch { border: 1px solid var(--accent); background: var(--page); border-radius: 8px; padding: 12px 16px; }
  .chips { display: flex; flex-wrap: wrap; gap: 8px; }
  .chip { border-radius: 999px; padding: 6px 12px; font-size: 13px; cursor: grab; touch-action: none; user-select: none; -webkit-user-select: none; }
  .chip.picked { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .chip.dragging { opacity: 0.4; }
  .slot { border: 2px dashed var(--border); border-radius: 8px; min-height: 60px; display: flex; align-items: center; justify-content: center; padding: 8px 16px; color: var(--muted); width: 100%; background: #fff; }
  .slot.filled { color: var(--text); font-weight: 600; }
  .slot.over { border-style: solid; border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent); }
  .judgment { border-color: var(--accent); }
  .judgment p + p { margin-top: 8px; }
  .protocol h3 { font-family: var(--font-ui); font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; font-weight: 600; }
  .protocol .art { margin-top: 12px; }
  .protocol .aid { font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); }

  .ghost { position: fixed; left: 0; top: 0; z-index: 50; pointer-events: none; border: 1px solid var(--accent); background: #fff; border-radius: 6px; padding: 4px 10px; font-size: 12px; font-weight: 500; max-width: 240px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; box-shadow: 0 1px 2px rgba(0,0,0,0.08); }
</style>
</head>
<body>
<div class="wrap">
  <p class="eyebrow">The Anatomy Drill</p>
  <div id="root" class="stack" style="margin-top: 12px;"></div>
</div>
<div id="ghost" class="ghost" hidden aria-hidden="true"></div>
<div id="live" class="sr-only" aria-live="polite"></div>

<script>
  // Data: verbatim from XLab's src/lib/verification/data/anatomy-drill.ts (em dashes replaced).
  var ORGANS = [
    { n: 1, key: "rule", name: "The rule", d: "Definitions, thresholds, scope, duration", line: "What exactly is prohibited, for whom, above what line, for how long. Rules live in their definitions." },
    { n: 2, key: "claims", name: "The claims", d: "What parties must be able to prove: declared & undeclared", line: "Everything declared is compliant, and nothing undeclared exists. Every mechanism serves one branch." },
    { n: 3, key: "evid", name: "The evidence", d: "Access, inspections, monitoring, timeliness", line: "How anyone would know. Judge it by access and by speed against the breakout clock." },
    { n: 4, key: "conf", name: "The confidentiality bargain", d: "What the verifier must NOT see", line: "What stays secret, and the machinery that makes intrusion acceptable. No one signs without it." },
    { n: 5, key: "adv", name: "The adversary", d: "The threat model provisions are written against", line: "Reconstructed from clauses that only make sense as answers to a specific evasion." },
    { n: 6, key: "inst", name: "The institution & consequences", d: "Who verifies, who judges, what follows, exit", line: "Findings, consequences, withdrawal. 'Shall' versus 'may' is the whole organ in two verbs." },
    { n: 7, key: "gap", name: "The gap", d: "Verified proxy vs. actual goal; decay; review", line: "Compute is not capability, parties are not the world. Good agreements chase their own proxy." }
  ];
  var NULLBIN = { n: 0, key: "none", name: "No organ", d: "Advocacy: sounds load-bearing, binds no one. The tell is 'should' with no bound actor and no procedure." };
  function organOf(n) { return n === 0 ? NULLBIN : ORGANS[n - 1]; }

  var CARDS = [
    {
      organ: 1,
      text: "New training runs using more than 10²⁴ computational operations (FLOP) are prohibited. Runs between 10²² and 10²⁴ FLOP require monitoring.",
      source: "MIRI Technical Governance Team, example international agreement, 2025 (paraphrased; thresholds per the November 2025 release).",
      ok: "A rule you can violate is a rule you can verify: a named activity, a measurable unit, a bright line. Notice the two-tier structure. The monitored band below the ceiling exists so that anyone playing games near the line is already inside the monitored zone when they do it.",
      wrong: { 3: "The word 'monitoring' is doing rule work here: it defines which runs fall under which obligation. HOW monitoring happens (access, instruments, notice periods) would be the evidence organ. This clause is the line itself." },
      generic: "Ask what this text does: it draws a measurable line around an activity. That is the rule organ."
    },
    {
      organ: 3,
      text: "Each Party shall have the right to conduct eighteen short-notice, on-site inspections of the other Party's declared facilities each year.",
      source: "New START inspection regime, 2011–2026 (paraphrased). Inspections stopped in 2020 and never resumed; the treaty expired February 5, 2026, years after its verification had already died.",
      ok: "Access, a quota, and a timeliness property ('short-notice'). This is what the evidence organ looks like when it has actually been negotiated: who may enter, how often, and on what clock.",
      near: { 6: "Defensible: inspections are run by institutional machinery, and the full protocol names it. But the operative function of this clause is generating evidence: access rights with a timeliness property. Tag clauses by what they do, not by who appears in them. Moved to the evidence." },
      generic: "Rights of access, on a clock. The function is producing evidence about compliance."
    },
    {
      organ: 0,
      text: "This pause should be public and verifiable, and include all key actors.",
      source: "FLI Open Letter, “Pause Giant AI Experiments,” March 2023 (verbatim). More than 30,000 signatures.",
      ok: "'Verifiable' with no verifier, no access, no procedure, no bound actor. This sentence demands the evidence organ; it does not contain one. The letter moved the political window, which is advocacy's job. The failure would be citing it as if it were an agreement, and that failure happens in print constantly.",
      wrong: {
        3: "Compare this to the New START card: eighteen inspections, short notice, declared facilities. That was evidence. This is a wish for evidence. Who verifies? What may they see? On what timeline? The sentence does not say. Demanding evidence and specifying evidence are different acts.",
        1: "There is no rule here either: no threshold, no defined activity, no bound party, no term. 'Pause' gestures at a rule the way 'verifiable' gestures at a regime. The silhouette of anatomy, none of the organs."
      },
      generic: "Read for the tell: 'should,' with no bound actor and no procedure. Sounds load-bearing, binds no one."
    },
    {
      organ: 2,
      text: "Assurance requires establishing two things: that declared facilities are running only permitted workloads, and that no undeclared facilities or chip stockpiles exist.",
      source: "The declared/undeclared decomposition, standard across the verification literature (paraphrase; see the RAND six-layers working paper, 2025).",
      ok: "The claims organ: what each party must be able to prove, split into its two branches. Sort every provision you read by which branch it serves, and you will find texts dense with monitoring language that leave one branch entirely empty.",
      wrong: { 3: "One level up. Evidence is how you would establish these things: inspections, attestation, satellite imagery. This clause states what must be established. Claims first; evidence gets judged against them." },
      generic: "This text names what must be proven, not how. That is the claims organ."
    },
    {
      organ: 4,
      text: "Inspectors shall not access, copy, or transmit model parameters, training data, or source code. Verification shall proceed through managed-access procedures and hardware attestation of workload properties.",
      source: "Reykjavik Protocol, Article VI, amended teaching text (fictional; the design problem it answers is entirely real).",
      ok: "The confidentiality bargain: what verification must never see, plus the machinery (managed access, attestation) that makes intrusion acceptable anyway. No lab and no state signs without this organ, and it is the technically hardest one to build.",
      wrong: { 3: "Understandable: it describes how inspection proceeds. But its function is protective. The evidence organ opens doors; this organ decides which doors stay shut, and makes the open ones tolerable to the inspected. That trade is what gets signatures." },
      generic: "Ask whose interest this clause protects: the inspected party's secrets. That is the bargain that buys consent to verification."
    },
    {
      organ: 3,
      text: "Each State Party has the right to request an on-site challenge inspection of any facility or location in the territory or in any other place under the jurisdiction or control of any other State Party … and to have this inspection conducted anywhere without delay.",
      source: "Chemical Weapons Convention, Article IX(8) (verbatim, condensed). Entered into force 1997. No state has ever invoked it.",
      ok: "The strongest access language ever negotiated: any facility, anywhere, without delay, no right of refusal. And it has never been used in 28 years, through repeated public accusations of noncompliance. The evidence organ's hardest lesson: access on paper still carries a political activation cost the text cannot see.",
      near: { 6: "Defensible: the full article routes through the Director-General and Executive Council, which is institutional machinery. But this paragraph's operative content is access: any facility, anywhere, without delay. Moved to the evidence, where its function lives." },
      generic: "A right of access, at maximum strength. Evidence organ, with an institutional frame around it."
    },
    {
      organ: 6,
      text: "Upon a finding of non-compliance, Parties shall suspend the violating Party's access to covered chips and cloud compute, and the matter shall be referred to the Security Council.",
      source: "Reykjavik Protocol, Article VIII, amended teaching text (fictional). The weak original read: the Council “may recommend measures to restore compliance.”",
      ok: "Institution and consequences: a finding procedure and an automatic, specified response. Now compare the original version in the source line below. 'Shall suspend' versus 'may recommend' is one verb apart and a whole organ apart. Most real regimes carry the weak verb, and it is where they go to die.",
      wrong: { 5: "It responds to a violator, but the adversary organ is the threat model that provisions are designed against, before anything happens. This clause is about after: what follows a finding. Consequences are the institution's teeth." },
      generic: "Follow the sequence: finding, then consequence, then referral. This is the institutional organ doing its job."
    },
    {
      organ: 6,
      text: "A Party may withdraw upon ninety days' notice if it decides that extraordinary events related to the subject matter of this Protocol have jeopardized its supreme interests.",
      source: "Standard withdrawal language, modeled on NPT Article X, the clause North Korea invoked in 2003.",
      ok: "Exit is part of the institution organ, and it is always read against a clock. If withdrawal takes ninety days and a covert sprint to the prohibited capability takes sixty, the exit clause is a hole through every other organ. Always read the exit at the speed of the breakout it permits.",
      wrong: { 1: "It has a rule's grammar, but its subject is the agreement itself, not the prohibited activity. Clauses about how bindingness ends belong to the institution organ. The question they raise is not 'what is banned' but 'what is this ban worth in a crisis.'" },
      generic: "This governs how the agreement's grip ends. Institutional organ: exit is one of its parts."
    },
    {
      organ: 0,
      text: "We call for a prohibition on the development of superintelligence, not lifted before there is (1) broad scientific consensus that it will be done safely and controllably, and (2) strong public buy-in.",
      source: "Statement on Superintelligence, 2025 (verbatim). Over 100,000 signatures within months, including Nobel laureates and two of the three “godfathers” of deep learning.",
      ok: "It has a rule's silhouette: a prohibition, even a lifting condition. But no party is bound, nothing is defined, and no institution exists to judge 'consensus' or run the lifting. It is a demand that a rule exist. As advocacy it may be doing exactly its job; prohibitions get demanded into existence before they get drafted. Just never cite it as if the drafting had happened.",
      wrong: {
        1: "Check what a rule needs: a bound actor ('no State Party shall…'), a measurable line (10²⁴ FLOP), a scope, a term. 'Superintelligence,' by whose measure? Prohibited by whom, on whom? A prohibition-shaped silhouette with none of the anatomy.",
        7: "Sharp instinct: the lifting condition does gesture at review machinery, which is gap-organ work in a real agreement. But there is no institution to run that review and no rule to lift. A condition attached to a nonexistent rule is still advocacy."
      },
      generic: "Apply the tell: who is bound, to what line, judged by whom? No answer, no organ."
    },
    {
      organ: 1,
      text: "The fine-tuning, continued development, or adaptation of models trained before entry into force shall not constitute a covered training run.",
      source: "Reykjavik Protocol, Article I(3) (fictional). Grandfather clauses like it appear throughout real regimes; they are how agreements buy signatures and lose meaning.",
      ok: "Definitions are the rule organ's fine print, and this one has a highway through it: 'continued development' of a pre-existing model is exempt with no compute limit at all. When you stress-test agreements, definitional clauses fail before inspection clauses do. This clause returns in the stress test, where you will be on the other side of it.",
      near: { 5: "Good instinct, and nearly right: this clause is exactly where an adversary goes first. But the clause itself is a definition, part of the rule organ. The adversary organ is provisions written against evasions. This is not the defense; it is the evasion's front door, left open in the definitions. Moved to the rule." },
      generic: "It carves the boundary of the defined term. Definitions belong to the rule, and this one is load-bearing in the worst way."
    },
    {
      organ: 5,
      text: "Because a covert program could evade facility-level monitoring by spreading training across many small sites, unmonitored chip holdings anywhere are capped at the equivalent of 16 H100 chips (roughly $500,000 of hardware).",
      source: "MIRI TGT example agreement, 2025 (paraphrased, including the report's stated rationale and 2025 cost figure).",
      ok: "The adversary organ made visible: a named evasion path, and a provision priced against it. Most agreements never write their threat model down; you reconstruct it from clauses like this one. An agreement with no reconstructible threat model was drafted against no adversary.",
      near: { 1: "Defensible: the cap is a threshold, and thresholds are rule furniture. But read the first half of the sentence. The provision exists as an answer to a specific evasion, and it tells you so. When a clause only makes sense against a particular cheat, the adversary is the organ doing the talking. Moved." },
      generic: "Read the 'because.' This clause is an answer to a named evasion, which is the adversary organ speaking."
    },
    {
      organ: 7,
      text: "Recognizing that training compute is an imperfect proxy for model capability, the thresholds in Article I shall be reviewed annually and may be lowered by a two-thirds vote of the Conference of Parties.",
      source: "Composite review-clause language (fictional drafting; the proxy problem it answers is conceded by regulators and researchers alike).",
      ok: "The gap organ: the agreement admitting that what it measures (FLOP) is not what it is for (capability), and building machinery to chase its own decaying proxy. Note the voting rule, two-thirds rather than consensus. A consensus rule here lets one party freeze the threshold while algorithms quietly erode it to nothing.",
      near: { 1: "Defensible: it amends the rule, so it touches organ one. But its function is managing the distance between the measured proxy and the actual goal. That distance is the gap, and this clause is its maintenance schedule. Moved." },
      generic: "'Imperfect proxy' is the giveaway: this clause manages the space between what is verified and what is wanted. That space is the gap."
    },
    {
      organ: 0,
      text: "AI labs and independent experts should use this pause to jointly develop and implement a set of shared safety protocols for advanced AI design and development that are rigorously audited and overseen by independent outside experts.",
      source: "FLI Open Letter, March 2023 (verbatim).",
      ok: "Every noun of the evidence and institution organs appears (protocols, audits, independent experts) and none is bound to anything. This is the promissory-note pattern, and real agreements carry it too: the BWC's verification protocol stayed 'to be negotiated' from 1975 until the effort collapsed in 2001, and the ban has run on trust ever since. A deferred organ is an absent organ until the day it is drafted.",
      wrong: {
        3: "The vocabulary of evidence is all here: audits, oversight, outside experts. Now ask the two binding questions. Who is bound? ('Labs and experts should' binds no one.) What procedure exists? (None; it is to be developed, jointly, later.) Vocabulary is not anatomy.",
        6: "It names overseers, which smells institutional. But no institution is created, empowered, funded, or given a decision rule. 'Overseen by independent outside experts' is a job posting, not an organ."
      },
      generic: "Run the tell: 'should,' unbound actors, procedures deferred to future joint work. Advocacy."
    }
  ];

  var JUDGMENT = {
    1: "A defensible first pick: definitions fail before inspectors do, and every later organ inherits the rule's precision. The negotiator's caution: definitional fights are where talks stall longest, and a perfect rule with a weak evidence organ is how you get a ban that runs on trust.",
    2: "The analyst's pick. Getting the declared/undeclared decomposition written into the text disciplines everything downstream, because every mechanism must then name the branch it serves. Almost no real treaty makes it explicit, which is why so many have one branch standing empty.",
    3: "The obvious pick, and the one that eats the whole negotiation, because access is precisely what states resist. The CWC's record applies: the strongest access clause ever drafted has waited 28 years for someone willing to pay the political price of invoking it.",
    4: "The professional's pick. Acceptability runs through this organ: managed access and attestation are what let a rival say yes to intrusion, and the RAND authors are blunt that much of this machinery needs years of R&D. Whoever builds it first sets the terms everyone else signs.",
    5: "The red-teamer's pick. An agreement drafted against no adversary collapses on first contact, and such agreements show themselves in unpriced carve-outs. Push to get the threat model in writing; you will be told it is impolitic. It was impolitic in 1972 as well, and the BWC shows the bill.",
    6: "The realist's pick. Findings without automatic consequences produced most of arms control's dead letters; 'may recommend measures' is the genre's epitaph. The caution: automatic consequences are also exactly what makes states hesitate to sign. This organ prices the deal.",
    7: "The forecaster's pick. Compute is a decaying proxy, so an agreement without review machinery is accurate on signing day and a little more wrong every day after. The quiet problem is the voting rule: review that can be vetoed is a freeze with extra steps."
  };

  var PROTOCOL = [
    { id: "Preamble", text: "The States Parties to this Protocol, recognizing that certain applications of advanced artificial intelligence may pose risks to international security, have agreed as follows:" },
    { id: "Article I. Definitions", text: "(1) “Covered training run” means the training of a single general-purpose artificial intelligence model using more than 10²⁶ computational operations. (2) “Covered facility” means any installation with power capacity exceeding 10 megawatts operated for the purpose of artificial intelligence computation. (3) The fine-tuning, continued development, or adaptation of models trained before entry into force of this Protocol shall not constitute a covered training run." },
    { id: "Article II. Core obligation", text: "No State Party shall conduct, authorize, or knowingly permit within its jurisdiction any covered training run for a period of five years from entry into force." },
    { id: "Article III. Declarations", text: "(1) Each State Party shall, within 180 days, declare all covered facilities and all holdings of applicable high-performance computing hardware exceeding one thousand units, as specified in Annex A. (2) Declarations shall be updated annually." },
    { id: "Article IV. Monitoring", text: "Declared covered facilities shall install power metering and workload verification instruments approved by the Technical Secretariat, where technically and commercially feasible." },
    { id: "Article V. Inspections", text: "(1) The Technical Secretariat may conduct routine inspections of declared facilities upon fourteen days’ notice. (2) Any State Party may request a challenge inspection of any facility of another State Party; such inspection shall proceed upon approval by a two-thirds majority of the Executive Council." },
    { id: "Article VI. Confidentiality", text: "Inspectors shall not access, copy, or transmit model parameters, training data, or source code. Managed access procedures shall be specified in Annex B, to be concluded by the Executive Council no later than two years after entry into force." },
    { id: "Article VII. Non-parties", text: "States Parties shall not export applicable high-performance computing hardware to non-parties, except as licensed for verified civilian purposes." },
    { id: "Article VIII. Non-compliance", text: "Upon a finding of non-compliance by the Executive Council, the Council may recommend measures to restore compliance, and may refer the matter to the United Nations Security Council." },
    { id: "Article IX. Withdrawal", text: "A State Party may withdraw from this Protocol upon ninety days’ notice if it decides that extraordinary events related to the subject matter of this Protocol have jeopardized its supreme interests." },
    { id: "Article X. Review and amendment", text: "The thresholds and definitions in Article I may be amended by consensus of all States Parties at a Review Conference, the first of which shall convene three years after entry into force." }
  ];

  var COPY = {
    introNote: "Sources are hidden until you place each card. Read the text, not the letterhead. Where a tag is arguable, a defensible second-best answer is accepted and discussed, because expert readers disagree about these too. Drag with mouse or touch, or click a card and then click a bin.",
    begin: "Begin",
    dragHint: "Drag to a bin, click the card to arm it, or focus it and press Enter, then choose an organ.",
    armedHint: "Picked up. Now choose the organ it implements (Escape puts it down).",
    resultsHead: "Results",
    scoreClean: "clean first reads",
    scoreNear: "defensible near-tags",
    scoreMiss: "needed a second look",
    summaryLead: "Now look at what you just built, sorted by where each specimen came from:",
    tableHead: ["Source", "Organs it supplied", "Status in the world"],
    tableRows: [
      ["Chemical Weapons Convention, New START", "The evidence (twice, at full negotiated strength)", "One never invoked in 28 years; the other expired in February 2026, verification first."],
      ["MIRI TGT example agreement (2025)", "The rule, the adversary", "Fully drafted anatomy. Zero signatures; its own authors say the political will does not yet exist."],
      ["FLI Open Letter, Statement on Superintelligence", "Nothing but the No-organ bin", "Over 130,000 signatures between them."],
      ["The Reykjavik Protocol (fiction)", "Everything else", "Fictional; written for this course. Full text below."]
    ],
    punch: "In AI today, the texts with anatomy have no signatures, and the texts with signatures have no anatomy. Neither fact is an insult to either kind of text. The distance between them is the current state of AI governance.",
    judgmentLeadStrong: "One last drag.",
    judgmentLead: "You are staffing the delegation that will negotiate a real training pause. Resources are finite. Drag the organ you would put at the top of the negotiating agenda:",
    judgmentSlotEmpty: "Drop your priority here (or click a chip)",
    judgmentSlotLabel: "Your top negotiating priority",
    judgmentNoRight: "There is no single right answer here. Bring yours to your cohort session and defend it.",
    whereNextStrong: "Where this goes next:",
    whereNext: "the full dissection applies these seven tags to a real proposed agreement, clause by clause, and the stress test asks you to defeat what you tagged.",
    restart: "Restart drill",
    protocolHead: "The Reykjavik Protocol: full text",
    protocolNote: "The fictional agreement several specimens were drawn from. Two specimens used strengthened versions of Articles VI and VIII; the original text appears here. You will work with this document again in the dissection and the stress test."
  };

  var FEEDBACK_HEAD = {
    "good": "Correct",
    "good-after": "Correct (second read)",
    "near": "Defensible: here is the sharper tag",
    "retry": "Not this organ. Look again",
    "reveal": "Filed for you"
  };
  var TIER_LABEL = { clean: "clean", near: "defensible", miss: "miss" };

  // Engine: XLab's resolveDrop + applyDrop, unchanged in logic.
  function resolveDrop(card, binN) {
    if (binN === card.organ) return { kind: "clean" };
    if (card.near && card.near[binN] !== undefined) return { kind: "near", msg: card.near[binN] };
    var msg = card.wrong && card.wrong[binN] !== undefined ? card.wrong[binN] : card.generic;
    return { kind: "bad", msg: msg };
  }
  function applyDrop(card, binN, attempts) {
    var r = resolveDrop(card, binN);
    if (r.kind === "clean") {
      return { kind: attempts === 0 ? "good" : "good-after", msg: card.ok, attempts: attempts, result: attempts === 0 ? "clean" : "miss" };
    }
    if (r.kind === "near") {
      return { kind: "near", msg: r.msg || "", attempts: attempts, result: attempts === 0 ? "near" : "miss" };
    }
    var nextAttempts = attempts + 1;
    if (nextAttempts >= 2) {
      return { kind: "reveal", msg: r.msg || "", attempts: nextAttempts, result: "miss" };
    }
    return { kind: "retry", msg: r.msg || "", attempts: nextAttempts, result: null };
  }
  function feedbackTier(kind) {
    if (kind === "good") return "clean";
    if (kind === "near") return "near";
    return "miss";
  }
  function feedbackMsg(card, fb) {
    if (fb.kind === "good" || fb.kind === "good-after") return card.ok;
    return resolveDrop(card, fb.bin).msg || "";
  }

  // State
  var state = { phase: "intro", idx: 0, attempts: 0, results: [], fb: null, judgment: null };
  var completed = false;
  var armed = false;          // specimen picked up by click or keyboard
  var STORAGE_KEY = "lens-widget-anatomy-drill";

  var root = document.getElementById("root");
  var ghost = document.getElementById("ghost");
  var live = document.getElementById("live");

  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined && text !== null) node.textContent = text;
    return node;
  }
  function btn(className, text, onClick) {
    var b = el("button", className, text);
    b.type = "button";
    if (onClick) b.addEventListener("click", onClick);
    return b;
  }
  function announce(msg) { live.textContent = msg; }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }

  function counts() {
    var c = { clean: 0, near: 0, miss: 0 };
    state.results.forEach(function (r) { if (r && c[r] !== undefined) c[r]++; });
    return c;
  }

  function summaryText() {
    var c = counts();
    var parts = ["The Anatomy Drill (sort 13 specimen texts onto the seven organs of an agreement or the No-organ bin)."];
    if (state.phase === "intro") {
      parts.push("The learner has not begun the drill yet.");
    } else if (state.phase === "summary") {
      parts.push("All 13 specimens placed. Results: " + c.clean + " clean first reads, " + c.near + " defensible near-tags, " + c.miss + " needed a second look.");
      if (state.judgment) {
        parts.push("Final pick for the top of the negotiating agenda: " + organOf(state.judgment).name + " (no right answer; XLab's judgment for that pick was shown).");
      } else {
        parts.push("The final priority pick (which organ to put at the top of a negotiating agenda) has not been made yet.");
      }
    } else {
      var card = CARDS[state.idx];
      parts.push("Now on specimen " + (state.idx + 1) + " of 13: “" + card.text + "” (correct organ: " + organOf(card.organ).name + "; source still hidden from the learner).");
      parts.push("So far: " + c.clean + " clean first reads, " + c.near + " defensible near-tags, " + c.miss + " needed a second look.");
      if (state.fb) {
        var verdict = state.fb.kind === "retry" ? "wrong bin, one retry left" : (state.fb.kind === "reveal" ? "wrong twice, filed for them as " + organOf(card.organ).name : FEEDBACK_HEAD[state.fb.kind].toLowerCase());
        parts.push("Latest placement: put it on " + organOf(state.fb.bin).name + "; verdict: " + verdict + ".");
      } else if (state.attempts > 0) {
        parts.push("One wrong attempt on this specimen so far; the learner is retrying.");
      } else {
        parts.push("Not placed yet.");
      }
    }
    return parts.join(" ");
  }

  function persist() {
    var snapshot = { phase: state.phase, idx: state.idx, attempts: state.attempts, results: state.results, fb: state.fb, judgment: state.judgment };
    if (window.Lens) {
      Lens.saveState(snapshot, summaryText());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) { /* storage unavailable */ }
    }
  }
  function markComplete() {
    if (completed) return;
    completed = true;
    if (window.Lens) Lens.complete();
  }

  // Actions
  function begin() { state.phase = "drill"; armed = false; render(); persist(); }

  function dropOnBin(binN) {
    if (state.phase !== "drill") return;
    var card = CARDS[state.idx];
    if (!card) return;
    var outcome = applyDrop(card, binN, state.attempts);
    state.attempts = outcome.attempts;
    state.fb = { kind: outcome.kind, bin: binN };
    state.phase = "feedback";
    if (outcome.result) state.results[state.idx] = outcome.result;
    armed = false;
    announce("Placed on " + organOf(binN).name + ". " + FEEDBACK_HEAD[outcome.kind] + ".");
    render();
    persist();
  }

  function nextCard() {
    if (state.phase !== "feedback" || !state.fb) return;
    if (state.fb.kind === "retry") {
      state.phase = "drill";
      state.fb = null;
      render();
      persist();
      return;
    }
    var nextIdx = state.idx + 1;
    state.fb = null;
    state.attempts = 0;
    state.idx = nextIdx;
    if (nextIdx >= CARDS.length) {
      state.phase = "summary";
      render();
      persist();
      markComplete();
    } else {
      state.phase = "drill";
      render();
      persist();
    }
  }

  function pickJudgment(n) {
    state.judgment = n;
    announce("Priority: " + organOf(n).name + ".");
    render();
    persist();
  }

  function restart() {
    state = { phase: "intro", idx: 0, attempts: 0, results: [], fb: null, judgment: null };
    armed = false;
    render();
    persist();
  }

  // Pointer drag (mouse and touch), same mechanics as XLab's kit: a 5px move starts a drag,
  // the ghost follows the pointer, and releasing over a [data-bin] element drops there.
  var drag = null;
  function startDrag(e, item, label, onDropTarget) {
    if (e.button !== 0 && e.pointerType === "mouse") return;
    drag = { pointerId: e.pointerId, startX: e.clientX, startY: e.clientY, active: false, item: item, label: label, onDropTarget: onDropTarget, moved: false };
  }
  function targetAt(x, y) {
    var t = document.elementFromPoint(x, y);
    return t && t.closest ? t.closest("[data-bin]") : null;
  }
  function setOver(target) {
    var all = document.querySelectorAll("[data-bin]");
    for (var i = 0; i < all.length; i++) all[i].classList.toggle("over", all[i] === target);
  }
  window.addEventListener("pointermove", function (e) {
    var d = drag;
    if (!d || d.pointerId !== e.pointerId) return;
    if (!d.active) {
      if (Math.hypot(e.clientX - d.startX, e.clientY - d.startY) < 5) return;
      d.active = true; d.moved = true;
      d.item.classList.add("dragging");
      armed = false;
      ghost.textContent = d.label;
      ghost.hidden = false;
    }
    ghost.style.transform = "translate(" + (e.clientX + 12) + "px, " + (e.clientY + 12) + "px)";
    setOver(targetAt(e.clientX, e.clientY));
  });
  function endDrag(e) {
    var d = drag;
    if (!d || d.pointerId !== e.pointerId) return;
    drag = null;
    if (!d.active) return;
    d.item.classList.remove("dragging");
    ghost.hidden = true;
    setOver(null);
    var target = e.type === "pointerup" ? targetAt(e.clientX, e.clientY) : null;
    if (target) d.onDropTarget(target);
    // Suppress the click that follows a drag on the same element.
    d.item.dataset.justDragged = "1";
    setTimeout(function () { delete d.item.dataset.justDragged; }, 0);
  }
  window.addEventListener("pointerup", endDrag);
  window.addEventListener("pointercancel", endDrag);

  // Rendering
  function render() {
    clear(root);
    if (state.phase === "intro") renderIntro();
    else if (state.phase === "summary") renderSummary();
    else renderDrill();
  }

  function renderIntro() {
    var box = el("div", "stack");
    if (completed) box.appendChild(el("p", "small muted", "You have completed this drill before. Begin again for a fresh run."));
    var ul = el("ul", "organ-list");
    ORGANS.forEach(function (o) {
      var li = el("li");
      li.appendChild(el("span", "name", o.n + ". " + o.name + ". "));
      li.appendChild(el("span", "muted", o.line));
      ul.appendChild(li);
    });
    var liNone = el("li");
    liNone.appendChild(el("span", "name", "No organ. "));
    liNone.appendChild(el("span", "muted", NULLBIN.d));
    ul.appendChild(liNone);
    box.appendChild(ul);
    box.appendChild(el("p", "small muted", COPY.introNote));
    var b = btn("primary", COPY.begin + " →", begin);
    box.appendChild(b);
    root.appendChild(box);
  }

  function renderProgress() {
    var bar = el("div", "progress");
    CARDS.forEach(function (_, i) {
      var r = i < state.idx ? state.results[i] : null;
      var cls = "dot" + (i === state.idx ? " now" : (r ? " " + r : ""));
      var d = el("span", cls);
      d.setAttribute("aria-hidden", "true");
      bar.appendChild(d);
    });
    bar.appendChild(el("span", "count", "Specimen " + (state.idx + 1) + " of " + CARDS.length));
    return bar;
  }

  function renderDrill() {
    var card = CARDS[state.idx];
    var inFeedback = state.phase === "feedback";
    var fb = state.fb;
    var isRetry = inFeedback && fb && fb.kind === "retry";
    var showLive = !inFeedback || isRetry;
    var showFiled = inFeedback && !isRetry;
    var filedOrgan = organOf(card.organ);

    root.appendChild(renderProgress());

    var specimen = null;
    if (showLive) {
      var holder = el("div");
      specimen = btn("card specimen" + (isRetry ? " retry" : "") + (armed ? " armed" : ""));
      specimen.setAttribute("aria-pressed", armed ? "true" : "false");
      specimen.setAttribute("aria-label", "Specimen " + (state.idx + 1) + ": " + card.text.slice(0, 90) + "… Press to pick up, then choose an organ.");
      var top = el("span", "top");
      top.appendChild(el("span", null, "Specimen " + (state.idx + 1)));
      top.appendChild(el("span", null, "source hidden"));
      specimen.appendChild(top);
      specimen.appendChild(el("span", "quote", "“" + card.text + "”"));
      specimen.addEventListener("click", function () {
        if (specimen.dataset.justDragged) return;
        armed = !armed;
        specimen.classList.toggle("armed", armed);
        specimen.setAttribute("aria-pressed", armed ? "true" : "false");
        setReady(armed);
        announce(armed ? "Picked up specimen " + (state.idx + 1) + ". Choose a target." : "Put down.");
      });
      specimen.addEventListener("keydown", function (e) {
        if (e.key === "Escape" && armed) { armed = false; specimen.classList.remove("armed"); specimen.setAttribute("aria-pressed", "false"); setReady(false); }
      });
      specimen.addEventListener("pointerdown", function (e) {
        startDrag(e, specimen, "Specimen " + (state.idx + 1), function (target) { dropOnBin(Number(target.dataset.bin)); });
      });
      holder.appendChild(specimen);
      var hint = el("p", "hint", armed ? COPY.armedHint : COPY.dragHint);
      hint.id = "hint";
      holder.appendChild(hint);
      root.appendChild(holder);
    }

    if (showFiled) {
      var filed = el("div", "card filed");
      filed.appendChild(el("div", "top", "Specimen " + (state.idx + 1) + ". Filed under: " + filedOrgan.name));
      filed.appendChild(el("p", null, "“" + card.text + "”"));
      root.appendChild(filed);
    }

    if (!showFiled) {
      var bins = el("div", "bins");
      ORGANS.forEach(function (o) { bins.appendChild(renderBin(o, false)); });
      bins.appendChild(renderBin(NULLBIN, true));
      root.appendChild(bins);
    }

    if (inFeedback && fb) {
      var tier = feedbackTier(fb.kind);
      var box = el("div", "card feedback " + tier);
      box.setAttribute("role", "status");
      box.setAttribute("aria-live", "polite");
      var head = el("div", "fb-head " + tier);
      head.appendChild(el("span", null, tier === "clean" ? "✓" : (tier === "near" ? "⚖" : "!")));
      head.appendChild(el("span", null, FEEDBACK_HEAD[fb.kind]));
      box.appendChild(head);
      var msg = feedbackMsg(card, fb);
      if (fb.kind === "reveal") {
        box.appendChild(el("p", null, msg));
        var where = el("p");
        where.appendChild(el("strong", null, "Where it belongs: " + filedOrgan.name + ". "));
        where.appendChild(document.createTextNode(card.ok));
        box.appendChild(where);
      } else {
        box.appendChild(el("p", null, msg));
      }
      if (fb.kind !== "retry") box.appendChild(el("p", "source", "Source: " + card.source));
      root.appendChild(box);

      var actions = el("div", "actions");
      if (fb.kind === "retry") {
        actions.appendChild(btn(null, "Try again", nextCard));
      } else {
        actions.appendChild(btn("primary", (state.idx === CARDS.length - 1 ? "Finish" : "Next specimen") + " →", nextCard));
      }
      root.appendChild(actions);
    }
  }

  function setReady(on) {
    var all = document.querySelectorAll(".bin");
    for (var i = 0; i < all.length; i++) all[i].classList.toggle("ready", on);
    var hint = document.getElementById("hint");
    if (hint) hint.textContent = on ? COPY.armedHint : COPY.dragHint;
  }

  function renderBin(organ, full) {
    var b = btn("bin" + (full ? " full" : "") + (armed ? " ready" : ""));
    b.dataset.bin = String(organ.n);
    b.setAttribute("aria-label", organ.n + ". " + organ.name + ". " + organ.d);
    b.appendChild(el("span", "bn", organ.n + ". " + organ.name));
    b.appendChild(el("span", "bd", organ.d));
    b.addEventListener("click", function () {
      if (state.phase !== "drill") return;
      if (!armed) {
        announce("Pick up the specimen first: click it, or focus it and press Enter. Then choose an organ.");
        var s = root.querySelector(".specimen");
        if (s) { s.classList.add("armed"); armed = true; s.setAttribute("aria-pressed", "true"); setReady(true); }
        return;
      }
      dropOnBin(organ.n);
    });
    return b;
  }

  function renderSummary() {
    var c = counts();
    var box = el("div", "stack");
    box.appendChild(el("h2", null, COPY.resultsHead));

    var scores = el("div", "scores");
    [["clean", c.clean, COPY.scoreClean], ["near", c.near, COPY.scoreNear], ["miss", c.miss, COPY.scoreMiss]].forEach(function (s) {
      var sc = el("div", "score " + s[0]);
      sc.appendChild(el("div", "n", String(s[1])));
      sc.appendChild(el("div", "l", s[2]));
      scores.appendChild(sc);
    });
    box.appendChild(scores);

    box.appendChild(el("p", null, COPY.summaryLead));

    var tw = el("div", "table-wrap");
    var table = el("table");
    var thead = el("thead"); var tr = el("tr");
    COPY.tableHead.forEach(function (h) { tr.appendChild(el("th", null, h)); });
    thead.appendChild(tr); table.appendChild(thead);
    var tbody = el("tbody");
    COPY.tableRows.forEach(function (row) {
      var r = el("tr");
      row.forEach(function (cell) { r.appendChild(el("td", null, cell)); });
      tbody.appendChild(r);
    });
    table.appendChild(tbody);
    tw.appendChild(table);
    box.appendChild(tw);

    box.appendChild(el("p", "punch", COPY.punch));

    // Judgment: one last drag
    var jl = el("p");
    jl.appendChild(el("strong", null, COPY.judgmentLeadStrong + " "));
    jl.appendChild(document.createTextNode(COPY.judgmentLead));
    box.appendChild(jl);

    var chips = el("div", "chips");
    var slot = btn("slot" + (state.judgment ? " filled" : ""), state.judgment ? organOf(state.judgment).name : COPY.judgmentSlotEmpty);
    slot.dataset.bin = "slot";
    slot.setAttribute("aria-label", COPY.judgmentSlotLabel);
    ORGANS.forEach(function (o) {
      var chip = btn("chip" + (state.judgment === o.n ? " picked" : ""), o.n + ". " + o.name, function () {
        if (chip.dataset.justDragged) return;
        pickJudgment(o.n);
      });
      chip.setAttribute("aria-pressed", state.judgment === o.n ? "true" : "false");
      chip.addEventListener("pointerdown", function (e) {
        startDrag(e, chip, o.n + ". " + o.name, function (target) { if (target.dataset.bin === "slot") pickJudgment(o.n); });
      });
      chips.appendChild(chip);
    });
    box.appendChild(chips);
    slot.addEventListener("click", function () {
      if (!state.judgment) announce("Click a chip above, or drag one here, to choose your priority.");
    });
    box.appendChild(slot);

    if (state.judgment) {
      var jb = el("div", "card judgment");
      jb.setAttribute("aria-live", "polite");
      var jp = el("p");
      jp.appendChild(el("strong", null, organOf(state.judgment).name + ". "));
      jp.appendChild(document.createTextNode(JUDGMENT[state.judgment]));
      jb.appendChild(jp);
      jb.appendChild(el("p", "small muted", COPY.judgmentNoRight));
      box.appendChild(jb);

      var wn = el("p", "muted");
      wn.appendChild(el("strong", null, COPY.whereNextStrong + " "));
      wn.appendChild(document.createTextNode(COPY.whereNext));
      box.appendChild(wn);
      box.appendChild(btn(null, "↺ " + COPY.restart, restart));
    }

    var proto = el("div", "card protocol");
    proto.appendChild(el("h3", null, COPY.protocolHead));
    proto.appendChild(el("p", "small muted", COPY.protocolNote));
    PROTOCOL.forEach(function (a) {
      var art = el("div", "art");
      art.appendChild(el("div", "aid", a.id));
      art.appendChild(el("p", null, a.text));
      proto.appendChild(art);
    });
    box.appendChild(proto);

    root.appendChild(box);
  }

  // Restore
  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      var phase = saved.phase;
      if (phase === "intro" || phase === "drill" || phase === "feedback" || phase === "summary") state.phase = phase;
      if (typeof saved.idx === "number" && saved.idx >= 0 && saved.idx <= CARDS.length) state.idx = saved.idx;
      if (typeof saved.attempts === "number") state.attempts = saved.attempts;
      if (Array.isArray(saved.results)) state.results = saved.results.map(function (r) { return (r === "clean" || r === "near" || r === "miss") ? r : null; });
      if (saved.fb && typeof saved.fb === "object" && FEEDBACK_HEAD[saved.fb.kind] && typeof saved.fb.bin === "number") state.fb = { kind: saved.fb.kind, bin: saved.fb.bin };
      if (typeof saved.judgment === "number" && saved.judgment >= 1 && saved.judgment <= 7) state.judgment = saved.judgment;
      // Guard inconsistent snapshots.
      if (state.phase === "summary" && state.idx < CARDS.length) state.idx = CARDS.length;
      if (state.phase !== "summary" && state.idx >= CARDS.length) { state.phase = "summary"; }
      if (state.phase === "feedback" && !state.fb) state.phase = "drill";
    }
    completed = !!(meta && meta.completed);
    render();
    if (state.phase === "summary") markComplete();
  }

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
