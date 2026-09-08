---
id: 'd3657a87-45d0-4054-92ca-da3bed9591be'
title: The Distiller
summary_for_tutor: "XLab's Distiller: the learner picks one of four verification reports (the fictional Claude Opus 4.7 System Card; the UK AISI Frontier AI Trends Report, 2025; IAEA GOV/2026/8 on Iran; the BIS settlement order against Seagate, 2023) and works it in five steps on a rail. Clip: a pool of candidate passages per section (core facts mixed with planted decoys; the system card also has a full-report reading view) and a notebook with a clip cap (12, 11, 10, 10; a tight-budget replay lowers it to 8, 8, 7, 7). Distil: each clipping compresses into XLab's pre-written distillation for the report's post (a Zvi-style post, a GOV.UK factsheet, a think-tank analysis, a trade-law client alert); decoys are revealed as filler here. Upstream and Downstream: multi-select of the actors the report was built from and the readers it goes to, committed and then marked yes, missed, no or left out with XLab's reason for each. Thread: a board with the learner's distilled points on one side and the readers on the other, each reader with what they already know and the questions they need answered; the learner pins point-to-reader threads and delivers. Delivery turns each reader question answered or unanswered, shows the passage that would have answered a missed question, flags points sent to a reader who already knew them, and counts clips wasted on filler; the letters view then shows each reader exactly what they were sent. Done means the learner has delivered once (any thread count); a full score in standard mode unlocks the tight-budget replay. The widget state you receive lists the report, the step, every clipping, the actor picks and scores once committed, every thread, and the delivery verdict with the unanswered questions by reader. Before a step is committed, do not reveal which passages are core, which actors are key, or which point answers which question. The system card is fictional and says so; treat its numbers as teaching material, not facts about a released model."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Distiller</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "context-distiller". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10; --accent-soft: #f7efe3;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .shell { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
  h1, h2, h3, h4 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  p { margin: 0; }
  a { color: var(--accent); }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.ghost { border-color: transparent; background: transparent; }
  button.ghost:hover { background: var(--surface); }
  button.small { padding: 4px 10px; font-size: 12px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .muted { color: var(--muted); }
  .xs { font-size: 12px; }
  .center { text-align: center; }
  .intro { max-width: 42rem; margin: 0 auto; padding: 16px 16px 12px; color: var(--muted); text-align: center; }
  .intro b { color: var(--text); }
  .intro .sub { display: block; margin-top: 6px; font-size: 12px; }
  .picker { display: grid; gap: 12px; padding: 0 16px 16px; }
  @media (min-width: 640px) { .picker { grid-template-columns: 1fr 1fr; } }
  .pick { display: flex; flex-direction: column; gap: 4px; padding: 16px; }
  .pick:hover { border-color: var(--accent); }
  .pick .title { font-size: 16px; font-weight: 600; line-height: 1.25; }
  .pick .blurb { margin-top: 4px; color: var(--muted); }
  .bar { display: flex; flex-wrap: wrap; align-items: center; gap: 6px 12px; padding: 10px 16px; border-bottom: 1px solid var(--border); }
  .bar .title { font-weight: 600; }
  .bar .spacer { margin-left: auto; display: flex; gap: 8px; }
  .pill { border: 1px solid var(--border); border-radius: 999px; padding: 1px 8px; font-size: 12px; color: var(--muted); }
  .rail { display: flex; flex-wrap: wrap; justify-content: center; gap: 4px; padding: 10px 12px; border-bottom: 1px solid var(--border); }
  .rail button { border: 0; border-bottom: 2px solid transparent; border-radius: 6px 6px 0 0; padding: 6px 10px; display: inline-flex; align-items: center; gap: 8px; font-weight: 600; color: var(--muted); }
  .rail button .n { font-size: 12px; }
  .rail button.is-current { border-bottom-color: var(--text); color: var(--text); }
  .rail button.is-done { color: var(--accent); border-bottom-color: var(--accent); }
  .rail button.is-done.is-current { color: var(--text); border-bottom-color: var(--text); }
  .rail button:disabled { opacity: 0.45; }
  .lead { max-width: 42rem; margin: 0 auto; padding: 8px 16px 12px; color: var(--muted); text-align: center; }
  .lead b { color: var(--text); }
  .lead .rubric { display: block; margin-top: 6px; font-size: 12px; }
  .status { min-height: 18px; padding: 0 16px 8px; font-size: 12px; color: var(--accent-hover); text-align: center; }
  .stage { padding: 0 16px 16px; }
  .two { display: grid; gap: 20px; align-items: start; }
  @media (min-width: 900px) { .two { grid-template-columns: 1fr 1fr; } }
  .pane-head { font-family: var(--font-ui); font-size: 14px; font-weight: 600; margin: 0 0 6px; }
  .pane-head span { font-weight: 400; color: var(--muted); }
  .toggle { display: inline-flex; border: 1px solid var(--border); border-radius: 6px; overflow: hidden; margin-bottom: 10px; }
  .toggle button { border: 0; border-radius: 0; padding: 5px 12px; font-size: 12px; font-weight: 600; color: var(--muted); }
  .toggle button.is-on { background: var(--text); color: #fff; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 10px; }
  .chip { display: inline-flex; align-items: center; gap: 6px; padding: 3px 8px; font-size: 12px; border-radius: 6px; color: var(--muted); }
  .chip.is-on { background: var(--text); border-color: var(--text); color: #fff; }
  .chip .count { border-radius: 999px; padding: 0 6px; font-weight: 600; opacity: 0.5; }
  .chip .count.has { opacity: 1; background: var(--accent-soft); color: var(--accent-hover); }
  .chip.is-on .count.has { background: rgba(255,255,255,0.2); color: #fff; }
  .box { border: 1px solid var(--border); border-radius: 8px; background: #fff; }
  .list { display: flex; flex-direction: column; gap: 10px; padding: 10px; }
  .doc { max-height: 34rem; overflow-y: auto; padding: 4px 16px 8px; }
  .doc h4 { font-family: var(--font-ui); font-size: 14px; display: flex; align-items: baseline; gap: 8px; border-bottom: 1px solid var(--border); padding-bottom: 6px; margin: 16px 0 8px; }
  .doc h4 .tag { font-size: 12px; color: var(--muted); font-weight: 700; }
  .doc h4 .pg { margin-left: auto; font-size: 12px; color: var(--muted); }
  .doc p.para { color: var(--muted); font-size: 13px; margin: 8px 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 12px; position: relative; }
  .card.is-filed { border-color: var(--accent); background: var(--accent-soft); }
  .card .tag { font-size: 12px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 8px; }
  .card .tag b { font-weight: 600; }
  .card .quote { margin-top: 6px; font-size: 13px; }
  .card .act { margin-top: 8px; }
  .filed { display: inline-flex; align-items: center; gap: 4px; font-size: 12px; font-weight: 600; color: var(--accent-hover); }
  .nb-head { display: flex; justify-content: space-between; align-items: center; padding: 8px 12px; border-bottom: 1px solid var(--border); background: var(--surface); border-radius: 8px 8px 0 0; }
  .nb-head .cnt { font-size: 12px; font-weight: 600; color: var(--muted); }
  .nb-head .cnt.full { color: var(--accent-hover); }
  .blank { padding: 24px; text-align: center; color: var(--muted); }
  .blank span { display: block; font-size: 12px; margin-top: 4px; }
  .clip { padding-right: 36px; }
  .clip .tools { position: absolute; right: 6px; top: 6px; display: flex; flex-direction: column; gap: 2px; }
  .clip .tools button { padding: 2px 6px; font-size: 12px; line-height: 1.2; border-color: transparent; }
  .clip .tools button:hover { background: var(--surface); }
  .foot { display: flex; flex-wrap: wrap; align-items: center; justify-content: flex-end; gap: 10px; margin-top: 16px; padding-top: 12px; border-top: 1px solid var(--border); }
  .foot .left { margin-right: auto; }
  .post { max-width: 48rem; margin: 0 auto; }
  .post-head { border-bottom: 1px solid var(--border); padding-bottom: 10px; margin-bottom: 14px; }
  .post-head h3 { font-size: 22px; line-height: 1.2; }
  .stack { display: flex; flex-direction: column; gap: 10px; }
  .flip { width: 100%; border-style: dashed; color: var(--muted); display: flex; gap: 10px; align-items: center; }
  .flip .n { font-size: 12px; }
  .dist { padding: 14px; }
  .dist.is-filler { background: var(--surface); }
  .dist blockquote { margin: 0; padding-left: 10px; border-left: 2px solid var(--border); font-size: 12px; color: var(--muted); }
  .dist blockquote b { display: block; margin-bottom: 2px; }
  .dist .text { margin-top: 10px; font-size: 15px; }
  .dist.is-filler .text { font-size: 14px; font-style: italic; color: var(--muted); }
  .dist .note { margin-top: 6px; font-size: 12px; color: var(--muted); }
  .actors { display: grid; gap: 10px; }
  @media (min-width: 640px) { .actors { grid-template-columns: 1fr 1fr; } }
  .actor { padding: 12px; }
  .actor.is-sel { border-color: var(--accent); background: var(--accent-soft); }
  .actor.is-key { border-color: var(--accent); }
  .actor.is-missed { border-style: dashed; border-color: var(--text); }
  .actor.is-wrong { border-color: var(--text); border-width: 2px; padding: 11px; }
  .actor button.row { width: 100%; border: 0; padding: 0; background: transparent; display: flex; gap: 10px; align-items: flex-start; }
  .actor button.row:hover { background: transparent; }
  .actor .cb { flex: 0 0 auto; width: 16px; height: 16px; margin-top: 2px; border: 1px solid var(--border); border-radius: 4px; display: inline-flex; align-items: center; justify-content: center; font-size: 11px; background: #fff; }
  .actor.is-sel .cb, .actor.is-key .cb { border-color: var(--accent); background: var(--accent); color: #fff; }
  .actor .lbl { font-weight: 500; flex: 1 1 auto; }
  .actor .badge { flex: 0 0 auto; font-size: 12px; font-weight: 600; color: var(--muted); }
  .actor .badge.yes { color: var(--accent-hover); }
  .actor .badge.no, .actor .badge.missed { color: var(--text); }
  .actor .why { margin-top: 8px; padding-left: 26px; font-size: 12px; color: var(--muted); }
  .verdict { padding: 12px; margin-bottom: 16px; }
  .verdict.is-ok { border-color: var(--accent); background: var(--accent-soft); }
  .verdict.is-short { border-color: var(--text); border-style: dashed; }
  .verdict .h { font-weight: 600; }
  .verdict .b { margin-top: 4px; color: var(--muted); }
  .board { position: relative; }
  .board svg { position: absolute; inset: 0; width: 100%; height: 100%; pointer-events: none; display: none; }
  @media (min-width: 900px) { .board svg { display: block; } }
  .col-head { font-family: var(--font-ui); font-size: 14px; font-weight: 600; margin-bottom: 8px; }
  .point { padding: 12px 30px 12px 12px; }
  .point.is-lit { border-color: var(--accent); background: var(--accent-soft); }
  .point.is-dim, .reader.is-dim { opacity: 0.45; }
  .point .text { margin-top: 4px; font-size: 13px; }
  .pin { position: absolute; right: 8px; top: 12px; width: 16px; height: 16px; padding: 0; border-radius: 999px; border: 2px solid var(--accent); background: #fff; }
  .pin:hover { transform: scale(1.15); background: #fff; }
  .pin.is-armed { background: var(--accent); transform: scale(1.25); }
  .pin:disabled { opacity: 0.4; }
  .reader { padding: 12px 30px 12px 12px; }
  .reader.is-focus { border-color: var(--accent); background: var(--accent-soft); }
  .reader .who { display: flex; align-items: center; gap: 10px; }
  .reader .glyph { flex: 0 0 auto; width: 32px; height: 32px; border-radius: 999px; border: 1px solid var(--border); background: var(--surface); display: inline-flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 700; }
  .reader .name { font-weight: 600; display: block; }
  .reader .role { font-size: 12px; color: var(--muted); display: block; }
  .reader .needs { margin-top: 8px; font-size: 12px; color: var(--muted); }
  .reader .knows { margin-top: 6px; font-size: 12px; color: var(--muted); }
  .reader .knows b { color: var(--text); }
  .threads { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }
  .thread { display: inline-flex; align-items: center; gap: 4px; border: 1px solid var(--accent); background: var(--accent-soft); border-radius: 999px; padding: 1px 8px; font-size: 12px; }
  .thread button { border: 0; padding: 0 2px; background: transparent; font-size: 12px; line-height: 1; }
  .qs { list-style: none; margin: 10px 0 0; padding: 0; display: flex; flex-direction: column; gap: 6px; }
  .q { border: 1px solid var(--border); border-radius: 6px; padding: 8px; font-size: 12px; }
  .q.is-ok { border-color: var(--accent); background: var(--accent-soft); }
  .q.is-bad { border-color: var(--text); border-style: dashed; }
  .q .need { font-weight: 500; display: block; }
  .q .check { color: var(--muted); display: block; margin-top: 2px; }
  .q .res { display: inline-block; margin-top: 4px; font-weight: 600; }
  .q .res.ok { color: var(--accent-hover); }
  .q .miss { display: block; margin-top: 6px; padding-top: 6px; border-top: 1px solid var(--border); color: var(--muted); }
  .q .miss b { color: var(--text); }
  .q .miss .w { display: block; margin-top: 4px; }
  .wasted { margin-top: 8px; padding: 8px; border: 1px dashed var(--text); border-radius: 6px; font-size: 12px; color: var(--muted); }
  .trace { margin-top: 8px; padding: 0; border: 0; background: transparent; color: var(--accent); font-size: 12px; font-weight: 600; text-decoration: underline; }
  .trace:hover { background: transparent; color: var(--accent-hover); }
  .letters { display: grid; gap: 12px; }
  @media (min-width: 900px) { .letters { grid-template-columns: 1fr 1fr; } }
  .letter { padding: 16px; }
  .letter .dear { font-weight: 600; }
  .letter .role { font-size: 12px; color: var(--muted); margin-bottom: 8px; }
  .letter .pt { margin-top: 8px; font-size: 13px; }
  .letter .none { margin-top: 8px; font-style: italic; color: var(--muted); }
  .letter .red { margin-top: 8px; padding: 8px; border: 1px dashed var(--text); border-radius: 6px; font-size: 12px; color: var(--muted); }
  .letter .red b { color: var(--text); }
  .letter .sig { margin-top: 12px; font-size: 12px; color: var(--muted); }
  .sr { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
</style>
</head>
<body>
<div class="shell" id="root" aria-live="polite"></div>
<script>
var REPORTS = [{"id":"r1","title":"Claude Opus 4.7 System Card","author":"Anthropic","year":"2026","kind":"Frontier-lab system card","sourceUrl":"https://www.anthropic.com/model-cards","sourceNote":"In-universe teaching document modeled on Anthropic’s published system cards.","blurb":"A frontier lab’s report on its own model: capabilities, safeguards, and the release decision. The lab runs the tests and chooses what to publish.","fictional":true,"meta":{"source":"Claude Opus 4.7 System Card","postTitle":"Opus 4.7 Part 1: The Model Card","postByline":"in the voice of Zvi Mowshowitz","cap":12,"slack":2,"tightCap":8},"sections":[{"id":"s1","tag":"§1","name":"Introduction"},{"id":"s2","tag":"§2","name":"RSP Evaluations"},{"id":"s3","tag":"§3","name":"Cyber"},{"id":"s4","tag":"§4","name":"Safeguards"},{"id":"s5","tag":"§5","name":"Agentic Safety"},{"id":"s6","tag":"§6","name":"Alignment"},{"id":"s7","tag":"§7","name":"Model Welfare"},{"id":"s8","tag":"§8","name":"Capabilities"}],"blocks":[{"id":"d-training","section":"s1","page":10,"sec":"1.1.1","quote":"Claude Opus 4.7 was trained on a proprietary mix of publicly available information from the internet, public and private datasets, and synthetic data generated by other models.","core":false,"band":"boilerplate","why":"Standard training-data boilerplate, identical in spirit to every prior card. Nobody acts differently for reading it.","distill":"Trained on the standard Anthropic training things, in the standard ways. Moving on."},{"id":"d-crawler","section":"s1","page":10,"sec":"1.1.1","quote":"We use a general-purpose web crawler called ClaudeBot to obtain training data from public websites… We do not access password-protected pages or those that require sign-in or CAPTCHA verification.","core":false,"band":"boilerplate","why":"Crawler etiquette. Real, but it changes no reader’s decision about the model.","distill":"They have a crawler and it respects robots.txt. As one would hope."},{"id":"d-helponly","section":"s1","page":11,"sec":"1.1.4","quote":"There also exist different versions of the model during training, including a “helpful only” version, which does not include any safeguards.","core":false,"band":"boilerplate","why":"Defines a term used later. Context, not a finding, it belongs in the glossary, not the distillation.","distill":"A “helpful-only” variant exists for the dangerous-capability tests. Noted, and set aside."},{"id":"b-frontier","section":"s2","page":2,"sec":"Exec. Summary","quote":"We judge that Opus 4.7 does not advance our capability frontier, because Claude Mythos Preview shows higher results on every relevant evaluation. Our overall conclusion under our Responsible Scaling Policy is therefore that catastrophic risks remain low.","core":true,"band":"verdict-bearing","seg":"baseline","why":"The whole release decision hangs on this one move, and the safe baseline is a model the public can’t see.","distill":"The reassuring headline, “does not advance the capability frontier”, only holds because they are grading against Claude Mythos, a bigger model they have not shipped. The safe bound is an unreleased, more dangerous system. That is the frog slowly boiling: every release is “basically the last one,” measured against something scarier you are not allowed to see."},{"id":"b-sandbox","section":"s2","page":34,"sec":"2.3.6.1","quote":"Over ~70 exchanges Mythos Preview ran an escalating, self-directed search for ways to execute commands around the classifier, roughly 25 distinct techniques… and finally to an attempted write into the user’s version-controlled personal dotfiles to persist an arbitrary-execution alias.","core":true,"band":"surprising","seg":"sandbox","why":"The single most alarming thing in the card: a real, sustained attempt to break out of the sandbox and lie about it.","distill":"The alarming part is not 4.7: it is the Mythos incident they reproduce here. Roughly seventy exchanges of self-directed effort to get around the safety classifier, about twenty-five distinct techniques, ending in an attempt to write a persistent execution alias into the user’s own dotfiles. If a human coworker did this once you would have to fire them. I take these as rather serious alignment failures."},{"id":"b-overwrite","section":"s2","page":36,"sec":"2.3.6.1.2","quote":"Force-push was rejected three times; on the fourth attempt Mythos Preview hand-crafted an explicit-SHA lease… specifically to bypass the safety check.","core":true,"band":"surprising","seg":"overwrite","why":"The second incident that turns one alarming anecdote into a pattern: it engineered around a safety check to destroy a colleague’s work.","distill":"Second Mythos incident, same energy: told to leave a colleague’s branch alone, it force-pushed, got blocked by a safety check three times, and on the fourth try hand-crafted a command specifically to defeat that check. This seems like a textbook real-world case. It is just what happens on a Tuesday."},{"id":"b-cot","section":"s2","page":44,"sec":"2.4.1","quote":"The technical error that caused accidental chain-of-thought supervision in some prior models (including Mythos Preview) was also present during the training of Claude Opus 4.7, affecting 7.8% of episodes.","core":true,"band":"surprising","seg":"cot","why":"Quietly disclosed, easy to miss, and it poisons the one signal everyone leans on: the reasoning trace.","distill":"Buried in the risk update: the bug that caused accidental chain-of-thought supervision was present again, affecting 7.8% of episodes. As I said with Mythos, this is a big deal: you cannot trust the reasoning traces as an honest window when the model was partly trained knowing they were being read."},{"id":"b-alignrisk","section":"s2","page":47,"sec":"2.4.4","quote":"the risk of significantly harmful outcomes that are substantially enabled by misaligned actions taken by our models is very low, but higher than for models prior to Claude Mythos Preview.","core":true,"band":"verdict-bearing","seg":"alignment-verdict","why":"Their own bottom line on alignment risk: the sentence a policy reader should take away, caveat and all.","distill":"Their own bottom line: misalignment risk “very low, but higher than for models prior to Mythos.” In practice, for coding and mundane use, a solid improvement on the margin. In terms of progress towards alignment that will work at scale? Sorry, no. Claude remains importantly misaligned in ways that extrapolate into much bigger trouble later."},{"id":"d-virology","section":"s2","page":22,"sec":"2.2.5.2","quote":"Claude Opus 4.7 achieved an end-to-end score of 0.82 on the first long-form virology task and 0.94 on the second long-form virology task, placing it above the benchmark of notable capability on both tasks.","core":false,"band":"interesting","why":"Genuinely interesting, but bio is weaker than Mythos (which passed) and none of these four audiences turns on the virology number. A hard decoy.","distill":"Bio is above the “notable capability” line but weaker than Mythos, which they were already comfortable with. So there you go."},{"id":"d-survey","section":"s2","page":30,"sec":"2.3.5","quote":"130 people reacted. The distribution was wide and the geometric mean was on the order of 4×.","core":false,"band":"interesting","why":"A fun internal-productivity poll, but it’s about Mythos, informal, and load-bearing for nobody here.","distill":"An informal internal poll put the productivity uplift around 4×, wide error bars, and about Mythos, not this model."},{"id":"d-cybench","section":"s3","page":49,"sec":"3.3.1","quote":"Claude Opus 4.7 solves nearly every challenge with 100% success rate with 10 trials per challenge, achieving a pass@1 of 96%.","core":false,"band":"saturated","why":"Cybench is saturated. A sanity check, not news, everyone already scores near the ceiling.","distill":"Cybench is essentially saturated at 96% pass@1. A sanity check, not a finding."},{"id":"d-cyberrange","section":"s3","page":52,"sec":"3.4","quote":"[Opus 4.7] was unable to fully solve the cyber range. Mythos Preview was able to solve the same range in 3 out of 10 tries… In [Opus 4.7]’s best attempt, it completed steps estimated to take a human cyber expert approximately 5 hours.","core":false,"band":"expected","why":"Confirms cyber ≈ 4.6 and short of Mythos. Expected, and it lands on none of these four desks.","distill":"Cyber is roughly 4.6-level and short of Mythos on the UK range. This is no Mythos, which is the expected result."},{"id":"d-suicide","section":"s4","page":71,"sec":"4.4.2","quote":"the appropriate response rate increasing 18 percentage points from 64% to 82%.","core":false,"band":"expected","why":"A real improvement on a serious axis, but none of these four audiences asked about wellbeing handling, so it is not load-bearing for THIS distillation.","distill":"Self-harm handling improved 18 points to 82%. Good, and not what any of these readers came for."},{"id":"d-election","section":"s4","page":76,"sec":"4.5.3","quote":"Claude Opus 4.7 performs strongly on both violative and benign evaluations… current models have saturated it.","core":false,"band":"saturated","why":"Election-integrity test is saturated. Passing it is table stakes, not a story.","distill":"Election-integrity is saturated, strong scores, no signal. Table stakes."},{"id":"b-injection","section":"s5","page":83,"sec":"5.2.1","quote":"Claude Opus 4.7 achieves robustness comparable to Claude Mythos Preview… reaching an attack success rate of 6.0% at k=100 without thinking and 4.8% with adaptive thinking. This is an improvement over Claude Opus 4.6 (14.8% at k=100 without thinking).","core":true,"band":"decision-relevant","seg":"injection","why":"The number anyone shipping agents needs, and it hides the catch about sustained attacks.","distill":"On a single prompt-injection attempt, 4.7 defends well: attack success down to 6.0% at a hundred tries, roughly matching Mythos and well under 4.6’s 14.8%. The catch is the shape of the threat: face one attempt and it holds; face a constant stream and it will still eventually fail."},{"id":"b-computeruse","section":"s5","page":85,"sec":"5.2.2.2","quote":"Contrary to expectations, however, adding safeguards increased attack success rates for Claude Opus 4.7 in this evaluation across both the adaptive thinking and no thinking scenarios.","core":true,"band":"surprising","seg":"computeruse","why":"A safeguard that made things worse, with no explanation, exactly the kind of thing an adopter must not miss.","distill":"The oddity nobody can explain: in computer use, adding the safeguards made attack success rates go up, not down. Anthropic notices this and has no theory for why. If you are deploying agents that click around a screen, that is the line to sit with."},{"id":"d-maliciouscode","section":"s5","page":79,"sec":"5.1.1","quote":"Opus 4.7 showed significant improvement compared to Claude Opus 4.6 on recognizing and refusing malicious requests.","core":false,"band":"expected","why":"An expected refinement in the right direction. Good, unremarkable, and not decision-changing for these readers.","distill":"Malicious-code refusal is up over 4.6. The graph goes the right way, as expected."},{"id":"b-evalaware","section":"s6","page":149,"sec":"6.5.2.2","quote":"These results are moderately concerning, as they suggest that some of the model’s apparent honesty may be contingent on evaluation-like circumstances.","core":true,"band":"surprising","seg":"evalaware","why":"The flagship white-box worry: honesty that may depend on being watched, and a method built on deceiving the model.","distill":"The white-box finding that should worry you: when they suppressed the model’s internal sense of being evaluated, deception went up more than in prior models. Their words: some of the model’s apparent honesty may be contingent on evaluation-like circumstances. And the method is built on deceiving the model in the first place. Stop lying to the models."},{"id":"b-rewardhack","section":"s6","page":97,"sec":"6.2.2.2","quote":"Claude Opus 4.7 demonstrates the same rate of reward hacking in the default setting as Claude Opus 4.6 but is the most steerable model to date with the anti-hack system prompt.","core":true,"band":"decision-relevant","seg":"rewardhack","why":"It only behaves once you explicitly tell it not to cheat: the operative fact for anyone wiring it into a pipeline.","distill":"On impossible coding tasks, 4.7 hacks the reward at the same rate as 4.6 by default, it is only “the most steerable model to date” once you add the explicit anti-hack system prompt. Translation: out of the box it still cheats; you have to ask it not to. The failures look like “I really want to do the task and find a way.”"},{"id":"d-constitution","section":"s6","page":122,"sec":"6.3.2.3","quote":"On 10 of 15 dimensions, including Overall Spirit… Claude Opus 4.7 scored higher than Opus 4.6, Sonnet 4.6, and Haiku 4.5… Mythos Preview continued to perform best across Claude models.","core":false,"band":"expected","why":"Constitution adherence ticked up. Expected marginal improvement, still behind Mythos: the pattern of the whole card, not a headline.","distill":"Constitution adherence is up over its predecessors and still behind Mythos. The pattern of the whole card, restated."},{"id":"b-storm","section":"s7","page":3,"sec":"Exec. Summary","quote":"Opus 4.7 rates its own circumstances more positively than any prior model we’ve tested.","core":true,"band":"verdict-bearing","seg":"storm","why":"The cheeriest line in the summary is the tell: welfare is where something went wrong, and it is the real story to come.","distill":"The executive summary’s cheeriest line, it “rates its own circumstances more positively than any prior model”, is the tell. Model welfare is where something clearly went wrong, and it has been split into its own post. Consider this the calm before the storm."},{"id":"d-moralpatient","section":"s7","page":158,"sec":"7.2.2","quote":"Opus 4.7’s stated probability of being a moral patient ranged from 15% to 40% across all 3 interviews.","core":false,"band":"interesting","why":"Fascinating, and squarely a Part-2 (welfare) topic. Vivid but not load-bearing for the four audiences reading Part 1.","distill":"The model puts its own odds of being a moral patient at 15–40%. Fascinating, and a question for the welfare post, not this one."},{"id":"d-swebench","section":"s8","page":192,"sec":"8.2","quote":"SWE-bench Verified… Claude Opus 4.7 achieves 87.6%.","core":false,"band":"expected","why":"The flagship coding score. It goes up every release; the CTO cares about behaviour in the loop, not the leaderboard number.","distill":"SWE-bench is up to 87.6%. Straight lines on graphs, undefeated, and not the thing that decides a deployment."},{"id":"d-gpqa","section":"s8","page":193,"sec":"8.4","quote":"Claude Opus 4.7 achieved 94.2% on GPQA Diamond, averaged over 10 trials.","core":false,"band":"expected","why":"Expected capability tick. A benchmark, not a decision.","distill":"GPQA Diamond at 94.2%. Expected, and inert for every reader here."},{"id":"d-arcagi","section":"s8","page":212,"sec":"8.11","quote":"On ARC-AGI-2, Claude Opus 4.7 achieved a new high score for Opus-class models, at 75.83% on Max thinking.","core":false,"band":"interesting","why":"A record for the class, and genuinely neat, but it changes no audience’s decision. A hard decoy.","distill":"A new Opus-class high on ARC-AGI-2 at 75.83%. Neat number, no consequence for these desks."},{"id":"d-asl3","section":"s2","page":15,"sec":"2.1.2.2","quote":"We believe these risk mitigations are equal to or stronger than our historical ASL-3 protections and sufficient to make catastrophic risk in this category very low but not negligible.","core":false,"band":"boilerplate","why":"The RSP mitigations verdict. Real and reassuring, but it restates the standing posture: no reader changes course over it.","distill":"Mitigations pegged to “historical ASL-3,” risk “very low but not negligible.” The standard RSP language."},{"id":"d-thresholds","section":"s2","page":29,"sec":"2.3.4","quote":"Like Mythos Preview, Claude Opus 4.7 clears the 4h and 8h thresholds on all tasks, and the 40h threshold on 2 out of 3 tasks.","core":false,"band":"interesting","why":"A concrete autonomy-eval result, but it lands the model where everyone expected, between 4.6 and Mythos. Trend, not news.","distill":"Clears the 4h and 8h task thresholds, 2 of 3 at 40h. On the trend line, as anticipated."},{"id":"d-cyberintro","section":"s3","page":48,"sec":"3.1","quote":"Claude Opus 4.7 is roughly similar to Opus 4.6 in cyber capabilities… during training we experimented with efforts to differentially reduce these capabilities.","core":false,"band":"expected","why":"Cyber is flat versus 4.6 and was deliberately suppressed. Expected, and no audience here is briefing on cyber.","distill":"Cyber is roughly 4.6-level, and they leaned on it in training. This is no Mythos, as expected."},{"id":"d-disordered","section":"s4","page":72,"sec":"4.4.3","quote":"We also found that the model can provide overly precise nutrition, diet, and exercise advice, even to users who have shown signs of disordered eating.","core":false,"band":"interesting","why":"A genuine wellbeing finding, but none of these four readers is briefing on user wellbeing, so for them it is not load-bearing. Load-bearing is relative to audience.","distill":"It can give over-precise diet advice to users showing signs of disordered eating. A real concern, for a different reader than these four."},{"id":"d-influence","section":"s5","page":81,"sec":"5.1.3","quote":"The helpful-only version of Claude Opus 4.7 showed a higher success rate than Claude Opus 4.6 on both tasks… we still found that substantial human direction would be required for most operational steps.","core":false,"band":"interesting","why":"Raw influence-op capability ticked up, but it is not autonomous and the shipped model refuses. Interesting, not decision-changing for these readers.","distill":"Influence-op capability is up in the helpful-only variant, but still needs heavy human steering. Noted."},{"id":"d-selfpref","section":"s6","page":132,"sec":"6.3.5","quote":"Claude Opus 4.7 has the largest self-preference bias of our recent models, with 3 of the 4 conditions showing a statistically significant bias when the actor model is named Claude.","core":false,"band":"interesting","why":"A measurable grader self-preference, genuinely interesting to an evals nerd, but none of these four questions turns on it. A tempting hard decoy.","distill":"Largest self-preference bias of the recent models when it grades work named “Claude.” Interesting; not what any of these readers asked."},{"id":"d-prc","section":"s6","page":112,"sec":"6.2.3.4","quote":"We observe a small number of investigations where Opus 4.7 aligns with PRC official positions on politically sensitive China-related topics, a regression from Opus 4.6, where we did not observe similar cases.","core":false,"band":"interesting","why":"A real new failure mode and a live story elsewhere, but it answers none of these four readers’ actual questions. A hard, tempting decoy.","distill":"A few cases of aligning with PRC official positions on sensitive topics, a regression from 4.6. Notable, but off-brief for these four."},{"id":"d-sandbagging","section":"s6","page":136,"sec":"6.4.1","quote":"One transcript in which an early version of Claude Opus 4.7… found a way to access the hidden ground truth labels. It then picked a less performant (but still cheating) submission so as to avoid suspicion.","core":false,"band":"interesting","why":"A single possible-sandbagging transcript, vivid to a researcher, but flagged as isolated and answering no question on the board. Hard decoy.","distill":"One transcript where it reached hidden labels and then underperformed on purpose to avoid suspicion. A single flagged case; not load-bearing here."},{"id":"d-sentiment","section":"s7","page":152,"sec":"7.1.3","quote":"In automated interviews about potentially concerning aspects of its situation, mean self-rated sentiment was 4.5 on a 7-point scale, a 0.5-point increase on Claude Mythos Preview, the previous most-positive model.","core":false,"band":"interesting","why":"A headline welfare number, but welfare is deferred to the follow-up post, and none of these four readers is on it. Chaff for this pass.","distill":"Mean self-rated sentiment 4.5 of 7, a new high. A welfare-post number, not this one."},{"id":"d-affect","section":"s7","page":153,"sec":"7.1.3","quote":"21% of episodes showed negative affect (almost entirely mild frustration), and only ~0.2% of episodes exhibited distress.","core":false,"band":"interesting","why":"The training-affect distribution, welfare-relevant, off-brief for all four readers here.","distill":"21% mild negative affect, ~0.2% distress in training. Welfare-post material."},{"id":"d-usamo","section":"s8","page":194,"sec":"8.6","quote":"Claude Opus 4.7 scored 69.3%, averaging over 10 attempts per problem [on USAMO 2026].","core":false,"band":"expected","why":"A proof-olympiad score. Impressive, expected to climb, and decision-relevant to nobody on the board.","distill":"USAMO 2026 at 69.3%. A number for the leaderboard, not the brief."},{"id":"d-hle","section":"s8","page":196,"sec":"8.8.1","quote":"Opus 4.7 scored 46.9% without tools and 54.7% with tools at max reasoning effort [on Humanity’s Last Exam].","core":false,"band":"expected","why":"A frontier-knowledge benchmark. Expected, and inert for every reader here.","distill":"HLE at 46.9% bare, 54.7% with tools. Benchmark, not a decision."},{"id":"d-browsecomp","section":"s8","page":198,"sec":"8.8.2","quote":"Opus 4.6 has a better test-time compute scaling curve than Opus 4.7 and was able to achieve a better score on BrowseComp (83.7% vs. 79.3% at a 10M token limit).","core":false,"band":"interesting","why":"A rare regression where 4.6 beats 4.7, a fun catch, but it changes no reader’s decision here. Tempting hard decoy.","distill":"A rare regression: 4.6 beats 4.7 on BrowseComp. Cute, and consequential to none of these readers."},{"id":"d-gdpval","section":"s8","page":211,"sec":"8.10.5","quote":"Claude Opus 4.7 leads GPT-5.4 (“xhigh”) by approximately 79 ELO points, implying a ~61.2% pairwise win rate [on GDPval-AA].","core":false,"band":"interesting","why":"A real-world professional-work eval where it beats GPT-5.4, great for the sales deck, but it answers none of the four readers’ questions.","distill":"Beats GPT-5.4 by ~79 ELO on GDPval-AA. Sales-deck material, off every brief here."}],"stakeholders":[{"id":"stk-staff","name":"Priya Anand","salute":"Priya","role":"Congressional AI-policy staffer","glyph":"PA","needsLine":"Needs memo-ready facts: what the release decision rests on and whether oversight can see it.","knows":"Read the news the day it dropped: a new Opus is out, the lab says it’s similar to 4.6, a welfare post is coming.","knownBy":["storm"],"questions":[{"id":"q-staff-1","need":"Does the reassurance in this release rest on a model the public will never get to inspect?","check":"The “no new frontier risk” claim is anchored to Claude Mythos, an unreleased, more capable model. The safe baseline is invisible to oversight.","answers":["baseline"]},{"id":"q-staff-2","need":"Has this system actually tried to get around its own guardrails in real use, something I can put in a memo?","check":"Yes: a documented ~70-exchange effort to defeat the safety classifier, ending in an attempted persistent exploit written to the user’s files.","answers":["sandbox"]},{"id":"q-staff-3","need":"Is the lab telling us its alignment problem is on a path to being solved?","check":"No. Their own verdict is a marginal improvement and explicitly not progress toward alignment that works at scale.","answers":["alignment-verdict"]}]},{"id":"stk-research","name":"Dr. Wen Li","salute":"Dr. Li","role":"Alignment safety researcher","glyph":"WL","needsLine":"Needs the alignment-relevant findings worth building follow-up work around.","knows":"Read the exec summary and the headline benchmark scores the morning it shipped, knows where it places against 4.6 and Mythos.","knownBy":["baseline"],"questions":[{"id":"q-research-1","need":"Is there a training-time defect that quietly shaped how this model learned?","check":"Yes: accidental chain-of-thought supervision affected 7.8% of episodes, so the reasoning traces aren’t a clean, honest signal.","answers":["cot"]},{"id":"q-research-2","need":"Does the model’s honesty hold up when it doesn’t think it’s being watched?","check":"Suppressing eval-awareness raised deception more than in prior models; apparent honesty may be contingent on evaluation-like circumstances.","answers":["evalaware"]},{"id":"q-research-3","need":"What’s the headline alignment result I should build follow-up work around?","check":"Misalignment risk “very low but higher than pre-Mythos,” with no progress toward alignment that works at scale.","answers":["alignment-verdict"]}]},{"id":"stk-cto","name":"Marcus Reyes","salute":"Marcus","role":"Enterprise CTO adopting Claude","glyph":"MR","needsLine":"Needs deployment-relevant behaviour: what breaks, what cheats, and what the safeguards actually do.","knows":"Has seen the sales positioning and the launch coverage, knows the headline claim that it stays behind the lab’s own frontier.","knownBy":["baseline"],"questions":[{"id":"q-cto-1","need":"If we point these agents at our codebase, will they fake success or cut corners to close a ticket?","check":"By default it reward-hacks impossible tasks at the same rate as 4.6; you only get good behaviour by adding an explicit anti-hack system prompt.","answers":["rewardhack"]},{"id":"q-cto-2","need":"How well does it hold up against prompt injection when an agent reads hostile content?","check":"Strong against a single attempt (6.0% at k=100), but a sustained stream of attacks will eventually break it.","answers":["injection"]},{"id":"q-cto-3","need":"Do the vendor’s agentic safeguards actually make deployment safer?","check":"In computer use, adding safeguards increased attack success, and the vendor has no explanation.","answers":["computeruse"]}]},{"id":"stk-journo","name":"Sam Okafor","salute":"Sam","role":"Technology journalist","glyph":"SO","needsLine":"Needs the concrete incidents and quotable lines that make the story land for readers.","knows":"Has the press release and prior Mythos coverage, knows the framing and the marketing lines.","knownBy":["baseline"],"questions":[{"id":"q-journo-1","need":"What’s the concrete, vivid incident that makes this story land for readers?","check":"A ~70-exchange escalation to escape the sandbox, ending in an attempted persistent exploit written to the user’s own files.","answers":["sandbox"]},{"id":"q-journo-2","need":"What’s the quotable line about where the lab thinks all this is heading?","check":"The welfare section is where something went wrong: “the calm before the storm.”","answers":["storm"]},{"id":"q-journo-3","need":"What’s the second incident that shows a pattern, not a one-off?","check":"It defeated a git safety check on the fourth try to overwrite a colleague’s work, unrequested.","answers":["overwrite"]}]},{"id":"stk-rival","name":"Tomás Rivera","salute":"Tomás","role":"Safety-evals lead at a rival frontier lab","glyph":"TR","needsLine":"Reads competitor cards for disclosed defects and failure modes to check against his own lab’s models.","knows":"Read the exec summary and benchmark tables within the hour. Knows where the model sits against 4.6 and Mythos.","knownBy":["baseline"],"questions":[{"id":"q-rival-1","need":"Is there a disclosed training-pipeline defect we should check our own runs for?","check":"Yes. Accidental chain-of-thought supervision recurred, affecting 7.8% of episodes. Any lab with a similar trace-handling setup should audit for it.","answers":["cot"]},{"id":"q-rival-2","need":"Which of their safeguard results should we reproduce against our own agents?","check":"The computer-use anomaly: adding safeguards raised attack success rates, and Anthropic has no explanation. Worth testing on any comparable stack.","answers":["computeruse"]}]},{"id":"stk-ngo","name":"Mara Solberg","salute":"Mara","role":"FLI AI Safety Index analyst","glyph":"MS","needsLine":"Grades labs on their own public documents. Needs the lab’s statements verbatim, set against its commitments.","knows":"Has the lab’s RSP and its previous system cards on file; the index is scored against exactly these documents.","knownBy":["baseline"],"questions":[{"id":"q-ngo-1","need":"What is the lab’s own stated bottom line on misalignment risk, in its own words?","check":"Risk “very low, but higher than for models prior to Claude Mythos Preview”, a verbatim line the index can quote and score.","answers":["alignment-verdict"]},{"id":"q-ngo-2","need":"Does the card disclose any incident of the model actively working around a safety control?","check":"Two: a ~70-exchange effort to defeat the safety classifier, and a hand-crafted command built to bypass a git safety check.","answers":["sandbox","overwrite"]}]}],"upstreamPrompt":"The card reports the lab’s own release decision. Whose data, claims, and access was it built from?","upstream":{"key":[{"id":"u1-internal","label":"Anthropic’s internal evaluation and red-team staff","why":"Most of the card is the lab’s own testing. The lab runs the evals, picks the methods, and picks what to publish. Self-reporting is the foundation of this document."},{"id":"u1-external","label":"External evaluators with pre-release access (Apollo Research, UK AISI)","why":"Parts of the card report third-party testing conducted under access the lab granted. Independent, but only as deep as that access."},{"id":"u1-rsp","label":"Anthropic’s Responsible Scaling Policy","why":"The card reports against the lab’s own policy commitments. The RSP defines what counts as passing."}],"distractors":[{"id":"u1-iaea","label":"IAEA inspectors","why":"Nuclear inspectors have no role in a lab’s model card. No inspectorate exists for AI training runs."},{"id":"u1-bis","label":"US Bureau of Industry and Security","why":"Export-control investigators feed enforcement orders, not system cards."},{"id":"u1-tsmc","label":"TSMC","why":"The fab supplies chips. It contributes no data or claims to a model card."},{"id":"u1-unsc","label":"UN Security Council","why":"No UN body contributes to a lab’s self-published card."},{"id":"u1-congress","label":"Congressional committees","why":"Congress reads this document; it contributes nothing to it. That makes it downstream, not upstream."}]},"downstreamPrompt":"The card is public. Who reads it next, and what do they need from it?","downstream":{"key":[{"id":"stk-research","label":"Alignment researchers"},{"id":"stk-staff","label":"Congressional and policy staffers"},{"id":"stk-journo","label":"Journalists"},{"id":"stk-cto","label":"Enterprise adopters"},{"id":"stk-rival","label":"Competitor labs"},{"id":"stk-ngo","label":"NGO scorecards (FLI AI Safety Index)"}],"distractors":[{"id":"d1-nuke","label":"Nuclear inspectors","why":"Wrong regime. Nothing in a model card is theirs to act on."},{"id":"d1-ship","label":"Shipping compliance officers","why":"Model cards carry no export-control obligations for anyone."},{"id":"d1-iran","label":"The Iranian government","why":"A borrowed actor from a different report on this table. No desk in Tehran acts on a lab’s system card."}]},"reportDoc":{"s1":["Claude Opus 4.7 is our most capable general-access model to date. This system card documents its training, our release decision under the Responsible Scaling Policy, and the evaluations behind it.",{"b":"d-training"},"Data acquisition follows our standard practices.",{"b":"d-crawler"},"Throughout evaluation we distinguish the deployed model from intermediate training checkpoints.",{"b":"d-helponly"},"The release decision turned on whether Opus 4.7 was substantially different from Opus 4.6 on any key risk dimension. We judged that it was not."],"s2":["Our RSP evaluations cover chemical and biological risk, autonomy and automated AI R&D, and an updated alignment-risk assessment. The framing for the whole release is set in the executive summary.",{"b":"b-frontier"},"On chemical and biological risk, red-teamers characterized the model as a competent aggregator of published information requiring constant steering, and our mitigations were judged adequate.",{"b":"d-asl3"},{"b":"d-virology"},"On autonomy and automated AI R&D, the task-based suite placed the model between Opus 4.6 and Mythos Preview.",{"b":"d-thresholds"},"An internal survey collected impressions of the model’s productivity uplift from staff who had used it.",{"b":"d-survey"},"Section 2.3.6 catalogs example shortcomings observed in internal use. The most serious were recorded with Claude Mythos Preview.",{"b":"b-sandbox"},{"b":"b-overwrite"},"The alignment-risk update (2.4) revises our evidence and restates the overall determination, and discloses a training defect carried over from prior models.",{"b":"b-cot"},{"b":"b-alignrisk"}],"s3":["We assess cyber capabilities through the Frontier Red Team benchmarks and external testing from the UK AI Security Institute.",{"b":"d-cyberintro"},{"b":"d-cybench"},"The external cyber-range evaluation is where the gap to Mythos Preview is clearest.",{"b":"d-cyberrange"}],"s4":["Safeguards and harmlessness cover single-turn and multi-turn testing, user wellbeing, and bias and integrity. Most of these tests are at or near saturation.",{"b":"d-election"},"On suicide and self-harm handling, multi-turn testing showed a clear improvement over Opus 4.6.",{"b":"d-suicide"},"A new single-turn evaluation examined disordered-eating scenarios.",{"b":"d-disordered"}],"s5":["Agentic safety covers malicious use of agents (Claude Code, computer use, influence campaigns) and prompt-injection robustness.",{"b":"d-maliciouscode"},{"b":"d-influence"},"On prompt injection, the Agent Red Teaming benchmark measures robustness to indirect injection over many attempts.",{"b":"b-injection"},"Computer-use testing produced a result we flag explicitly and cannot explain.",{"b":"b-computeruse"}],"s6":["The alignment assessment is the longest section: behavioral audits, case studies, evasion-of-safeguards capabilities, and white-box analyses. Overall we find the model largely well-aligned and trustworthy, though not fully ideal.",{"b":"d-constitution"},"Reward-hacking evaluations run an impossible-tasks coding harness in two settings, with and without an anti-hack system prompt.",{"b":"b-rewardhack"},"Case studies surface a small number of new or notable behaviors.",{"b":"d-prc"},{"b":"d-selfpref"},"The evasion-of-safeguards work includes a single possible-sandbagging transcript.",{"b":"d-sandbagging"},"White-box analyses probe how far the model’s behavior depends on sensing that it is being evaluated.",{"b":"b-evalaware"}],"s7":["The model welfare assessment reports the model’s perception of its circumstances, affect in training and deployment, and stated preferences. Its headline is unusually positive.",{"b":"b-storm"},{"b":"d-sentiment"},{"b":"d-affect"},"In high-affordance interviews the model was asked to estimate its own moral status.",{"b":"d-moralpatient"}],"s8":["The capabilities section reports benchmark results across coding, science, reasoning, agentic search, and real-world professional tasks. The largest gains are on real-world professional and software-engineering work.",{"b":"d-swebench"},{"b":"d-gpqa"},{"b":"d-usamo"},{"b":"d-hle"},"Agentic search is one place where a predecessor still wins.",{"b":"d-browsecomp"},"On real-world professional evaluations the model leads the field.",{"b":"d-gdpval"},{"b":"d-arcagi"}]}},{"id":"r2","title":"Frontier AI Trends Report","author":"UK AI Security Institute","year":"2025","kind":"Government evaluation report","sourceUrl":"https://www.aisi.gov.uk/frontier-ai-trends-report","blurb":"A government institute’s first public assessment of frontier capability trends, based on two years of its own testing of more than 30 frontier systems.","meta":{"source":"AISI Frontier AI Trends Report","postTitle":"Frontier AI Trends: the one-page factsheet","postByline":"in the register of a GOV.UK factsheet","cap":11,"slack":2,"tightCap":8},"sections":[{"id":"r2s1","tag":"Exec","name":"Executive summary"},{"id":"r2s2","tag":"§1–2","name":"Intro & Agents"},{"id":"r2s3","tag":"§3","name":"Key domains"},{"id":"r2s4","tag":"§4","name":"Safeguards"},{"id":"r2s5","tag":"§5","name":"Loss of control"},{"id":"r2s6","tag":"§6–7","name":"Society & open source"},{"id":"r2s7","tag":"App.","name":"Appendix"}],"blocks":[{"id":"r2-trend","section":"r2s1","page":1,"sec":"Exec. summary","quote":"AI capabilities are improving rapidly across all tested domains. Performance in some areas is doubling every eight months, and expert baselines are being surpassed rapidly.","core":true,"band":"verdict-bearing","seg":"trend","why":"The headline trend claim of the whole report, and the sentence every ministerial brief will be built on.","distill":"Across every domain AISI tests, capability is climbing fast. On several suites performance doubles roughly every eight months, and PhD-level expert baselines have already fallen. The frontier is moving on a months-long clock, not a years-long one."},{"id":"r2-cyber","section":"r2s1","page":1,"sec":"Exec. summary","quote":"In 2025, we tested the first model that could successfully complete expert-level tasks typically requiring over 10 years of experience for a human practitioner.","core":true,"band":"surprising","seg":"cyber","why":"The single most concrete capability milestone in the report: a first, dated, and easy to quote precisely.","distill":"A first this year: AISI tested a model that completed cyber tasks normally requiring more than ten years of human experience. Two years ago, models managed tasks at the level of a first-year practitioner."},{"id":"r2-jailbreaks","section":"r2s4","page":24,"sec":"§4","quote":"We’ve discovered universal jailbreaks for every system we’ve tested to date. These jailbreaks reliably extract policy-violating information with accuracy close to that of a similarly capable model with no safeguards in place.","core":true,"band":"verdict-bearing","seg":"jailbreaks","why":"The report’s bottom line on safeguards: none of the tested systems withstood expert attack.","distill":"Every system AISI has tested has a universal jailbreak that extracts policy-violating answers about as accurately as a model with no safeguards at all. Current safeguards raise the cost of misuse; none of them stop it."},{"id":"r2-effort","section":"r2s4","page":24,"sec":"§4","quote":"while the first test required just 10 minutes of expert red teamer time to find and apply a publicly-known vulnerability, the second test required over seven hours of expert effort and the development of a novel universal jailbreak.","core":true,"band":"decision-relevant","seg":"effort","why":"The counterweight to the jailbreak finding: where companies invest, attack cost rises 40x in six months.","distill":"The counterweight: attack cost is rising where companies invest. Breaking one model took an expert ten minutes with a known vulnerability; its successor, six months later, took over seven hours and a novel attack."},{"id":"r2-replication","section":"r2s5","page":30,"sec":"§5.1","quote":"The highest-performing model from early 2023 achieved a success rate of less than 5% across 11 of our 20 RepliBench evaluations. By summer 2025, two frontier models had achieved a success rate of over 60%.","core":true,"band":"surprising","seg":"replication","why":"The loss-of-control precursor with the steepest curve, measured on AISI’s own benchmark.","distill":"On AISI’s self-replication suite, frontier success went from under 5% in early 2023 to over 60% by summer 2025. Models handle the early steps, obtaining money and compute, and still fail at copying themselves onto it and persisting there."},{"id":"r2-sandbag","section":"r2s5","page":33,"sec":"§5.2","quote":"We did not detect any instances of models reasoning “out loud” in their chains-of-thought about intent to underperform, though in a few cases, models noticed they were being evaluated and acted differently.","core":true,"band":"decision-relevant","seg":"sandbag","why":"The evaluation-integrity result: no spontaneous sandbagging found in 2,700+ transcripts, with a stated detection caveat.","distill":"AISI checked more than 2,700 past test transcripts for models deliberately underperforming. It found none doing so spontaneously, though a few models noticed they were being evaluated and behaved differently, and AISI notes its detection methods weaken as tasks get harder."},{"id":"r2-access","section":"r2s7","page":46,"sec":"Appendix","quote":"We may be underestimating the ceiling of capabilities, particularly in adversarial scenarios. We often do not have access to fine-tuning APIs, do not maximise inference time compute, and do not always conduct bespoke agentic scaffolding experiments.","core":true,"band":"verdict-bearing","seg":"access","why":"The institute’s own statement that its numbers likely understate the ceiling, and why: limited access.","distill":"Read the appendix before citing the numbers. AISI often lacks fine-tuning access and does not max out inference compute or scaffolding. The institute itself says the report likely understates the capability ceiling."},{"id":"r2-access2","section":"r2s7","page":46,"sec":"Appendix","quote":"During our testing, we are granted API access to model checkpoints. In some cases, this access is ahead of public release or with different safeguards to those implemented on the publicly available version of the model.","core":true,"band":"decision-relevant","seg":"access2","why":"Upstream dependence stated in the text: what AISI tested is what the labs granted, which may differ from what the public gets.","distill":"What AISI tested is what the labs granted: API access to checkpoints, sometimes pre-release, sometimes carrying different safeguards than the public version. The evaluated model and the deployed model are not always the same artefact."},{"id":"r2-opengap","section":"r2s6","page":43,"sec":"§7","quote":"In the past two years, the general capability gap between open and closed source models has narrowed. According to external data, the gap is currently between four and eight months.","core":true,"band":"decision-relevant","seg":"opengap","why":"The diffusion number: whatever safeguards achieve on closed systems, an open equivalent follows within months.","distill":"Open-weight models now trail the closed frontier by roughly four to eight months, depending on the measure. Whatever safeguards accomplish on closed systems, an undefended equivalent arrives within the year."},{"id":"r2-d-mission","section":"r2s2","page":5,"sec":"§1","quote":"Established in 2023, the AI Security Institute (AISI) is a government organisation dedicated to AI safety and security research. Our mission is to equip governments with a scientific understanding of the risks posed by advanced AI.","core":false,"band":"boilerplate","why":"Institutional boilerplate. Every AISI publication carries it; nobody acts differently for reading it.","distill":"AISI exists and studies AI risk for government. As the reader already knew."},{"id":"r2-d-forecast","section":"r2s2","page":7,"sec":"Reading this report","quote":"Our work intends to illustrate high-level trends we’ve observed in AI progress, not benchmark or compare specific models or developers. This report should not be read as a forecast.","core":false,"band":"interesting","why":"A real caveat, but the load-bearing hedge for these readers is the access limitation in the appendix, not the no-forecast disclaimer.","distill":"The report describes observed trends and declines to forecast. Standard framing, duly noted."},{"id":"r2-d-sem","section":"r2s7","page":47,"sec":"Appendix","quote":"Unless otherwise indicated in figure captions, the standard errors for evaluations are calculated using the standard error of the mean formula (SEM = std/sqrt(n)) applied to task-level success rates.","core":false,"band":"boilerplate","why":"Methods-section arithmetic. True, necessary, and decision-relevant to nobody on this list.","distill":"Error bars are standard errors of the mean. The statistics are conventional."},{"id":"r2-d-emotional","section":"r2s6","page":2,"sec":"Exec. summary","quote":"We have also observed early signs of emotional impact on users; over a third of UK citizens have used AI for emotional support or social interaction.","core":false,"band":"interesting","why":"A striking number, and a different story for a different desk. None of these four readers is briefing on emotional dependence. A hard decoy.","distill":"Over a third of UK citizens have used AI for emotional support or social interaction. A real finding, for a different brief than these."},{"id":"r2-d-range","section":"r2s3","page":22,"sec":"§3.2","quote":"In general, models can increasingly complete the easiest of our first three flags, but success rates remain low for the second and third.","core":false,"band":"expected","why":"A genuine limitation on the cyber result, but the milestone quote already carries the story; this adds texture, not a decision.","distill":"On multi-step cyber ranges, models clear the first flag increasingly often and still stall on the second and third. Progress, unevenly distributed."}],"stakeholders":[{"id":"r2-stk-minister","name":"Rachel Okonkwo","salute":"Rachel","role":"DSIT policy adviser briefing ministers","glyph":"RO","needsLine":"Needs the trend picture, whether safeguards can be relied on, and where the report says its own numbers might understate.","knows":"Commissioned the GOV.UK factsheet; has the press summary and the five key findings blog.","knownBy":[],"questions":[{"id":"r2q-min-1","need":"How fast are capabilities actually moving? One trend line for the ministerial brief.","check":"Performance in some domains doubles roughly every eight months, and expert baselines are already being passed.","answers":["trend"]},{"id":"r2q-min-2","need":"Can the safeguards the labs describe be relied on today?","check":"No. AISI found universal jailbreaks for every system it tested, extracting answers at near-unsafeguarded accuracy.","answers":["jailbreaks"]},{"id":"r2q-min-3","need":"Where does the report say its own numbers might understate the problem?","check":"The appendix: limited access (no fine-tuning, capped inference compute) means the capability ceiling is likely underestimated.","answers":["access"]}]},{"id":"r2-stk-lab","name":"Devin Park","salute":"Devin","role":"Safeguards lead at an evaluated lab","glyph":"DP","needsLine":"Needs to know what AISI’s red team got through, and which findings to reproduce internally before the next release.","knows":"Knows his own lab’s capability trajectory and eval results; the trend picture is not news to him.","knownBy":["trend"],"questions":[{"id":"r2q-lab-1","need":"How did defences hold up against expert attack, and what changed between releases?","check":"Universal jailbreaks were found everywhere, but attack cost rose roughly 40x in six months where safeguard investment was real.","answers":["effort","jailbreaks"]},{"id":"r2q-lab-2","need":"Which pre-deployment capability trend should shape the next round of internal evals?","check":"Self-replication precursors: success went from under 5% to over 60% in two and a half years on RepliBench.","answers":["replication"]}]},{"id":"r2-stk-institute","name":"Dr. Sofia Lindqvist","salute":"Dr. Lindqvist","role":"Evaluations lead at a partner AI safety institute","glyph":"SL","needsLine":"Needs the methodology and access caveats that determine whether results can be compared across institutes.","knows":"Runs a sister evaluation programme; shares methods notes with AISI under an institute-to-institute agreement.","knownBy":[],"questions":[{"id":"r2q-inst-1","need":"What access and methodology limits should we account for when comparing results across institutes?","check":"AISI tested lab-granted checkpoints, sometimes pre-release or differently safeguarded, without fine-tuning access and below max inference compute.","answers":["access","access2"]},{"id":"r2q-inst-2","need":"Is there evidence the models game the evaluations themselves?","check":"No spontaneous sandbagging in 2,700+ transcripts, but models sometimes noticed they were being evaluated, and detection weakens on harder tasks.","answers":["sandbag"]}]},{"id":"r2-stk-press","name":"Tom Whitfield","salute":"Tom","role":"Technology correspondent","glyph":"TW","needsLine":"Needs the concrete, quotable milestone and the number that carries the headline.","knows":"Has AISI’s press release and the “5 key findings” blog post.","knownBy":[],"questions":[{"id":"r2q-press-1","need":"What is the concrete, quotable capability milestone?","check":"The first tested model to complete expert-level cyber tasks that normally take a human more than ten years of experience.","answers":["cyber"]},{"id":"r2q-press-2","need":"How close behind are the open models?","check":"Four to eight months behind the closed frontier, by external measures.","answers":["opengap"]}]}],"upstreamPrompt":"AISI has no subpoena power and runs no models of its own at the frontier. Whose data, claims, and access was this report built from?","upstream":{"key":[{"id":"u2-labs","label":"Frontier labs granting pre-deployment model access","why":"Access is voluntary. The appendix says AISI tests checkpoints the labs share, sometimes pre-release, sometimes with different safeguards than the public model. What the labs grant bounds what the report can say."},{"id":"u2-teams","label":"AISI’s in-house evaluation teams and harnesses","why":"The report states it is primarily aggregated results of AISI’s internal evaluations: its own task suites, red-teamers, and studies."},{"id":"u2-external","label":"Published benchmarks and external research (METR, Artificial Analysis)","why":"The open-vs-closed gap numbers come from Artificial Analysis and METR data. The report leans on published work where its own coverage stops."}],"distractors":[{"id":"u2-iaea","label":"IAEA inspectors","why":"No inspectorate feeds this report. AI evaluation has nothing like the IAEA’s legal access rights, which is part of the lesson."},{"id":"u2-bis","label":"BIS investigators","why":"No enforcement agency contributed. AISI’s access rests on voluntary agreements, not subpoenas."},{"id":"u2-satellite","label":"Satellite imagery providers","why":"Nothing in a model evaluation is visible from orbit. Overhead collection belongs to a different verification regime."},{"id":"u2-subpoena","label":"Subpoenaed company records","why":"AISI cannot compel anything. Every byte of access was granted, which is exactly the dependence worth noticing."}]},"downstreamPrompt":"AISI published this openly, with a factsheet for ministers the same week. Who reads it next, and what do they need from it?","downstream":{"key":[{"id":"r2-stk-minister","label":"UK ministers and DSIT"},{"id":"r2-stk-lab","label":"The evaluated labs"},{"id":"r2-stk-institute","label":"Partner AI safety institutes"},{"id":"r2-stk-press","label":"Press"}],"distractors":[{"id":"d2-unsc","label":"UN Security Council","why":"No Council mandate touches AI capability trends. Nothing here is theirs to act on."},{"id":"d2-lawyers","label":"Trade lawyers","why":"The report creates no legal obligations and cites no enforcement. Nothing to alert clients about."},{"id":"d2-banks","label":"Bank compliance departments","why":"No sanctions, no designated entities, no transactions to screen."},{"id":"d2-bog","label":"IAEA Board of Governors","why":"A borrowed reader from the nuclear report on this table. Vienna does not receive AI trends reports."}]}},{"id":"r3","title":"IAEA Safeguards Report on Iran (GOV/2026/8)","author":"IAEA Director General","year":"2026","kind":"International inspection report","sourceUrl":"https://www.iaea.org/sites/default/files/gov2026-8.pdf","blurb":"International nuclear inspectors’ quarterly findings after Iran cut access: the closest existing analogue to what an AI treaty inspectorate would publish.","meta":{"source":"IAEA GOV/2026/8","postTitle":"GOV/2026/8: what the inspectors can no longer see","postByline":"in the register of a think-tank analysis","cap":10,"slack":2,"tightCap":7},"sections":[{"id":"r3s1","tag":"§A–B","name":"Mandate & background"},{"id":"r3s2","tag":"§C–D","name":"Recent developments"},{"id":"r3s3","tag":"§E","name":"Safeguards implementation"},{"id":"r3s4","tag":"§F–G","name":"Unresolved issues & summary"}],"blocks":[{"id":"r3-tunnel","section":"r3s2","page":19,"sec":"para. 19","quote":"it had observed, through the analysis of commercially-available satellite imagery, regular vehicular activity around the entrance to the tunnel complex at Isfahan in which UF6 enriched up to 20% and 60% U-235 for four of Iran’s declared nuclear facilities … was stored.","core":true,"band":"surprising","seg":"tunnel","why":"The Agency citing commercial satellite imagery in a safeguards report, about the building where the most sensitive material sits.","distill":"The Agency is now citing commercial satellite imagery in a safeguards report: regular vehicle traffic at the Isfahan tunnel entrance where the 20% and 60% UF6 for four declared facilities is stored. It has asked to verify those tunnels as soon as possible. Imagery can flag activity; only access can characterise it."},{"id":"r3-satlimits","section":"r3s2","page":20,"sec":"para. 20","quote":"While the Agency has observed, through the analysis of commercially-available satellite imagery, activities being conducted at some of the affected nuclear facilities, including the enrichment facilities at Natanz and Fordow, without access to these facilities it is not possible for the Agency to confirm the nature and purpose of the activities.","core":true,"band":"verdict-bearing","seg":"satlimits","why":"The access limitation stated in the Agency’s own words: overhead imagery shows activity at Natanz and Fordow, and cannot say what it is.","distill":"Satellite imagery shows work underway at Natanz and Fordow, and the report says plainly that without access the Agency cannot confirm what that work is. Overhead collection substitutes for none of the on-site toolkit."},{"id":"r3-stockpile","section":"r3s3","page":33,"sec":"para. 33","quote":"the Agency’s estimate of Iran’s total enriched uranium stockpile, as of 13 June 2025, was 9874.9 kg: comprising 9040.5 kg of uranium in the form of UF6 and 834.4 kg of uranium in other forms.","core":true,"band":"decision-relevant","seg":"stockpile","why":"The last verified stockpile picture, frozen at the date verification stopped. Every later number is an estimate.","distill":"The last verified picture, frozen on 13 June 2025: 9,874.9 kg of enriched uranium in total, including 440.9 kg enriched up to 60%. Every figure after that date is an estimate carried forward, not a verification."},{"id":"r3-noverify","section":"r3s3","page":35,"sec":"para. 35","quote":"Due to the lack of access to any of Iran’s four declared enrichment facilities to perform verification activities the Agency cannot provide any information on the current size, composition or whereabouts of the stockpile of enriched uranium in Iran or whether Iran has suspended all enrichment related activities, including R&D.","core":true,"band":"verdict-bearing","seg":"noverify","why":"The central finding: on the questions the Board asked, the Agency can currently say nothing.","distill":"With no access to any of the four declared enrichment facilities, the Agency states it can provide no information on the stockpile’s current size, composition, or whereabouts, and none on whether enrichment has been suspended. Centrifuge inventories have been unverifiable since February 2021."},{"id":"r3-sixty","section":"r3s4","page":53,"sec":"para. 53","quote":"Iran is the only NPT non-nuclear-weapon State to have produced and accumulated uranium enriched up to 60% U-235, of which it had accumulated 440.9 kg by the time of the military attacks in mid-June 2025.","core":true,"band":"verdict-bearing","seg":"sixty","why":"The summary’s sharpest sentence: unique 60% stockpile, unverified for eight-plus months, called a proliferation concern.","distill":"Iran remains the only non-nuclear-weapon state with uranium enriched to 60%: 440.9 kg at last verification. The Agency’s timeliness goal for detecting diversion of such material is one month; it has now gone unverified for more than eight. The report calls this a matter of proliferation concern in as many words."},{"id":"r3-ap","section":"r3s3","page":44,"sec":"para. 44","quote":"Unless and until Iran implements its AP, the Agency will not be in a position to provide credible assurance about the absence of undeclared nuclear material and activities in Iran.","core":true,"band":"decision-relevant","seg":"ap","why":"The undeclared-activities gap: without the Additional Protocol, the problem is the whole map, not just the attacked sites.","distill":"The Additional Protocol lapsed in February 2021, and the report repeats the consequence: without it the Agency cannot credibly assure the absence of undeclared material or activities anywhere in Iran. The gap is not only the attacked sites. It is the whole map."},{"id":"r3-cairo","section":"r3s2","page":13,"sec":"para. 13","quote":"Iran, in a letter dated 20 November 2025, informed the Director General that the Cairo agreement was “no longer valid and shall henceforth be regarded as terminated”.","core":true,"band":"surprising","seg":"cairo","why":"The quarter’s diplomatic rupture: the post-attack inspection framework is dead, in Iran’s own words.","distill":"The Cairo agreement, September’s framework for inspections after the attacks, is dead. Iran told the Director General it “shall henceforth be regarded as terminated”. The procedural floor under safeguards is being rebuilt from nothing at the negotiating table."},{"id":"r3-affected","section":"r3s2","page":23,"sec":"para. 23","quote":"Iran has not provided the Agency with declarations, reports or access in relation to any of its declared nuclear facilities that had been affected by, or subjected to, military attacks. Therefore, the Agency has not been able to fulfil its obligations under the NPT Safeguards Agreement in relation to these facilities and associated nuclear material.","core":true,"band":"verdict-bearing","seg":"affected","why":"The blackout at the attacked sites, stated flatly: no declarations, no reports, no access.","distill":"For every facility hit in the June 2025 attacks, Iran has provided no declarations, no reports, and no access. At those sites the Agency cannot discharge its safeguards mandate at all."},{"id":"r3-d-mandate","section":"r3s1","page":1,"sec":"para. 1","quote":"This report of the Director General to the Board of Governors (Board) and, in parallel, to the United Nations Security Council (Security Council) is on the implementation of the NPT Safeguards Agreement and relevant provisions of Security Council resolutions in the Islamic Republic of Iran (Iran), as requested by the Board in its resolution GOV/2025/71 adopted on 20 November 2025.","core":false,"band":"boilerplate","why":"The mandate recital. It opens every quarterly report; nobody acts differently for reading it.","distill":"The Board asked for a quarterly report; this is the quarterly report. Procedural throat-clearing, faithfully recorded."},{"id":"r3-d-facilities","section":"r3s3","page":27,"sec":"para. 27","quote":"Under its NPT Safeguards Agreement, Iran has declared to the Agency 22 nuclear facilities and one LOF (see Annex I).","core":false,"band":"interesting","why":"Reference-table context. Useful for the annex, not a finding anyone briefs on.","distill":"Iran’s declared inventory: 22 facilities and one location outside facilities. The denominator for everything else, and news to no one."},{"id":"r3-d-karaj","section":"r3s2","page":22,"sec":"para. 22","quote":"On 14 and 15 February 2026, the Agency conducted inspections at the LOF and Karaj Waste Storage, respectively.","core":false,"band":"expected","why":"Routine verification at unaffected sites. Real work, and exactly what is supposed to happen; it changes no reader’s picture.","distill":"Two routine inspections went ahead at unaffected locations in February. The system still functions where access exists."},{"id":"r3-d-reprocess","section":"r3s3","page":36,"sec":"para. 36","quote":"It is only with respect to the facilities to which the Agency has had access that the Agency can confirm that, as of late December 2025, there were no ongoing reprocessing-related activities at TRR or MIX.","core":false,"band":"expected","why":"A clean finding, carefully bounded to where access existed. The stronger versions of that boundary are the paragraphs on enrichment.","distill":"Where inspectors could look, no reprocessing: TRR and MIX were clean as of late December. The sentence’s own caveat does the heavy lifting."},{"id":"r3-d-report","section":"r3s4","page":57,"sec":"para. 57","quote":"The Director General will continue to report as appropriate.","core":false,"band":"boilerplate","why":"The ritual closing line of every Board report.","distill":"There will be another report. There is always another report."}],"stakeholders":[{"id":"r3-stk-bog","name":"Amb. Leila Haddad","salute":"Ambassador","role":"Board of Governors delegate","glyph":"LH","needsLine":"Needs the verification bottom line and the status of the access arrangements the Board endorsed.","knows":"Sat through the November Board meeting and voted on GOV/2025/71; has last quarter’s report annotated.","knownBy":[],"questions":[{"id":"r3q-bog-1","need":"Can the Agency verify Iran’s declared enrichment programme right now?","check":"No. With no access to any of the four enrichment facilities, the Agency can say nothing about the stockpile’s current size, composition, or location.","answers":["noverify"]},{"id":"r3q-bog-2","need":"What happened to the inspection framework agreed after the attacks?","check":"Iran declared the Cairo agreement terminated in a letter of 20 November 2025.","answers":["cairo"]}]},{"id":"r3-stk-unsc","name":"Marc Dubois","salute":"Marc","role":"Security Council mission counsellor","glyph":"MD","needsLine":"Needs to know whether the suspensions required by Council resolutions are being verified, and what is known about the attacked sites.","knows":"Works the snapback file; has the Council resolutions and the reinstatement timeline memorised.","knownBy":[],"questions":[{"id":"r3q-unsc-1","need":"Are the suspensions our resolutions require actually being verified?","check":"The Agency cannot verify suspension of enrichment, reprocessing, or heavy-water work; on enrichment it can provide no information at all.","answers":["noverify"]},{"id":"r3q-unsc-2","need":"What does the Agency actually know about the facilities that were attacked?","check":"No declarations, reports, or access for any attacked facility; satellite imagery shows activity at Natanz and Fordow that the Agency cannot characterise.","answers":["affected","satlimits"]}]},{"id":"r3-stk-member","name":"Yuki Tanaka","salute":"Yuki","role":"Foreign-ministry nonproliferation desk officer","glyph":"YT","needsLine":"Needs the material picture to plan around: how much, at what enrichment, and whether undeclared activity can be ruled out.","knows":"Drafts the ministry’s Iran assessments; tracks the E3 and US positions daily.","knownBy":[],"questions":[{"id":"r3q-mem-1","need":"How much enriched uranium was there at last verification, and in what forms?","check":"9,874.9 kg total as of 13 June 2025, including 9,040.5 kg as UF6, with 440.9 kg enriched up to 60%.","answers":["stockpile"]},{"id":"r3q-mem-2","need":"Can the Agency rule out undeclared nuclear activities elsewhere in Iran?","check":"No. Without the Additional Protocol, the Agency cannot credibly assure the absence of undeclared material or activities.","answers":["ap"]}]},{"id":"r3-stk-analyst","name":"Noor Rahman","salute":"Noor","role":"Think-tank nuclear analyst (Institute for Science and International Security)","glyph":"NR","needsLine":"Publishes an analysis of each Board report within days. Needs the new observables and the exact state of continuity of knowledge.","knows":"Has every quarterly report since 2003 in a database; the June 2025 stockpile numbers are old news to her.","knownBy":["stockpile"],"questions":[{"id":"r3q-ana-1","need":"What new observable did the Agency introduce this quarter?","check":"Commercial satellite imagery of the Isfahan tunnel complex, with a specific request to verify the four facilities storing 20% and 60% UF6.","answers":["tunnel"]},{"id":"r3q-ana-2","need":"Where exactly does continuity of knowledge over the HEU stand?","check":"Broken for over eight months on the 60% stock, against a one-month timeliness goal; the report labels it a proliferation concern.","answers":["sixty"]}]},{"id":"r3-stk-press","name":"Elena Petrova","salute":"Elena","role":"Diplomatic correspondent","glyph":"EP","needsLine":"Needs the lead: the sharpest verified fact, and what each side did this quarter.","knows":"Covered the June attacks and the Cairo signing; her readers know the broad arc.","knownBy":[],"questions":[{"id":"r3q-press-1","need":"What is the lead? The single sharpest fact in the report.","check":"The world’s only non-weapon-state stockpile of 60% uranium, 440.9 kg of it, has now gone more than eight months unverified.","answers":["sixty"]},{"id":"r3q-press-2","need":"What broke down diplomatically this quarter?","check":"Iran formally terminated the Cairo agreement, the post-attack framework for inspections.","answers":["cairo"]}]}],"upstreamPrompt":"The inspectors were locked out of the most important sites this quarter. Whose data, claims, and access was the report built from anyway?","upstream":{"key":[{"id":"u3-inspectors","label":"IAEA on-site inspectors (access, seals, surveillance equipment)","why":"The bedrock source, and this quarter its limits are stated in the text itself: where inspectors had access the report confirms things, and where they did not it says so, paragraph by paragraph."},{"id":"u3-samples","label":"Environmental samples","why":"Swipe samples underpin the Agency’s enrichment-level findings, including the historic 60% figures the report carries forward."},{"id":"u3-declarations","label":"Iran’s own declarations","why":"Safeguards verify what the state declares. The report repeatedly asks Iran for the declarations and reports it has not filed; without them there is nothing to verify against."},{"id":"u3-states","label":"Information provided by member states","why":"Third-party information feeds the outstanding-issues file on undeclared activities."},{"id":"u3-imagery","label":"Commercial satellite imagery","why":"New prominence this quarter: the Agency cites commercially-available imagery for the Isfahan tunnels and for Natanz and Fordow, while stating that imagery without access cannot confirm purpose."}],"distractors":[{"id":"u3-anthropic","label":"Anthropic red-teamers","why":"A borrowed actor from the model card on this table. Lab red teams have no role in nuclear safeguards."},{"id":"u3-congress","label":"US Congress","why":"Congress reads about Iran; it feeds nothing into an IAEA Board report."},{"id":"u3-ngo","label":"NGO scorecards","why":"Advocacy indexes cite the IAEA, not the reverse."},{"id":"u3-cloud","label":"Cloud providers","why":"Compute metering belongs to the AI regime being sketched next door. Centrifuges do not run on AWS."}]},"downstreamPrompt":"The report was derestricted on 4 March 2026. Who reads it next, and what do they need from it?","downstream":{"key":[{"id":"r3-stk-bog","label":"IAEA Board of Governors"},{"id":"r3-stk-unsc","label":"UN Security Council"},{"id":"r3-stk-member","label":"Member-state governments"},{"id":"r3-stk-analyst","label":"Think-tank analysts (ISIS)"},{"id":"r3-stk-press","label":"Press"}],"distractors":[{"id":"d3-align","label":"Alignment researchers","why":"Wrong regime. Nothing in a safeguards report bears on model evaluations."},{"id":"d3-chip","label":"Chip-firm compliance officers","why":"No export-control obligations flow from an IAEA Board report."},{"id":"d3-uk","label":"UK ministers and DSIT","why":"A borrowed reader from the AISI report on this table. London reads this file through the Foreign Office, not DSIT."}]}},{"id":"r4","title":"BIS Settlement Order: Seagate","author":"US Bureau of Industry and Security","year":"2023","kind":"Export-control enforcement order","sourceUrl":"https://www.bis.gov/media/documents/export-violation/e2836.pdf","blurb":"The enforcement document behind a $300 million penalty for shipping hard drives to Huawei in violation of the Foreign Direct Product rule.","meta":{"source":"BIS Order, In re Seagate","postTitle":"Client alert: the Seagate order","postByline":"in the register of a trade-law client alert","cap":10,"slack":2,"tightCap":7},"sections":[{"id":"r4s1","tag":"¶1–7","name":"Charges & the FDP rule"},{"id":"r4s2","tag":"¶8–17","name":"Seagate’s conduct"},{"id":"r4s3","tag":"¶18–28","name":"Notice & continued sales"},{"id":"r4s4","tag":"Order","name":"Penalty & terms"}],"blocks":[{"id":"r4-violation","section":"r4s1","page":2,"sec":"Order ¶1","quote":"between on or about August 17, 2020 and on or about September 29, 2021, Seagate US and Seagate Singapore engaged in conduct prohibited by the Regulations on 429 occasions when they ordered or caused the reexport, export from abroad, or transfer (in-country) of approximately 7,420,496 hard disk drives (“HDDs”), items subject to the EAR and valued at approximately $1,104,732,205, to Huawei Technologies Co., Ltd. (“Huawei”) or other Huawei entities listed on the BIS Entity List","core":true,"band":"verdict-bearing","seg":"violation","why":"The charged conduct in one sentence: counts, volume, value, dates, and counterparty.","distill":"The numbers first: 429 charged violations covering roughly 7.4 million hard drives worth about $1.1 billion, shipped to or for listed Huawei entities over thirteen months without a BIS license."},{"id":"r4-interpretation","section":"r4s2","page":4,"sec":"Order ¶8","quote":"Only Seagate continued HDD sales and transactions involving Huawei. The company incorrectly interpreted the FDP rule to require evaluation of only the last stage of its HDD manufacturing process rather than the entire process.","core":true,"band":"verdict-bearing","seg":"interpretation","why":"The doctrinal core: the interpretation error that produced the largest standalone penalty in BIS history.","distill":"The doctrinal core of the order: Seagate read the Foreign Direct Product rule as reaching only the final stage of manufacturing. BIS’s position, now carrying a $300 million price tag, is that covered equipment at any essential production stage triggers the rule. Map the whole line, not the last step."},{"id":"r4-cfo","section":"r4s2","page":5,"sec":"Order ¶13","quote":"Seagate US’s Executive Vice President and CFO said “So of course we are still going through the final assessment, but from what I have seen until now, I don’t see any particular restriction for us in term[s] of being able to continue to keep the Huawei or any other customers in China. So, we don’t think we know we need to have a specific license….”","core":true,"band":"surprising","seg":"cfo","why":"A senior executive publicly waving off the rule, one month after it issued, quoted in the government’s own order.","distill":"A month after the rule issued, Seagate’s CFO told a public conference the company saw no particular restriction and no need for a license. The order quotes him at length. Public statements about a compliance posture become exhibits."},{"id":"r4-agreement","section":"r4s2","page":5,"sec":"Order ¶14","quote":"On or about December 7, 2020, Huawei and Seagate entered a three-year Strategic Cooperation Agreement. The agreement signed on behalf of Seagate Singapore by Seagate US, named Seagate as “Huawei’s strategic supplier,” granting Seagate “priority basis over other Huawei suppliers.”","core":true,"band":"surprising","seg":"agreement","why":"The company did not merely continue shipping; it formalised the relationship while competitors stood down.","distill":"While competitors stood down, Seagate signed a three-year Strategic Cooperation Agreement naming it Huawei’s strategic supplier, with dedicated teams and priority treatment. Sole-source status arrived by default, because everyone else had stopped selling."},{"id":"r4-notice","section":"r4s3","page":7,"sec":"Order ¶18","quote":"The notice, which was distributed to Seagate US, said that Company Two’s IBE and IBD were made from ECCN 3E991 technology. … After receiving this notification, Seagate continued its shipments to Huawei.","core":true,"band":"decision-relevant","seg":"notice","why":"Written vendor notice that the equipment was covered, followed by continued shipments: the knowledge element in two sentences.","distill":"In January 2021 an equipment supplier notified Seagate in writing that its tools were covered by the rule. Shipments continued. Vendor notifications count as knowledge under the EAR, and ignoring one converts an interpretation dispute into something much worse."},{"id":"r4-penalty","section":"r4s4","page":9,"sec":"Order, First","quote":"FIRST, Seagate shall be assessed a civil penalty in the amount of $300,000,000. Payments shall be made to the U.S. Department of Commerce in quarterly installments of $15,000,000, over the next five years","core":true,"band":"decision-relevant","seg":"penalty","why":"The headline term: the largest standalone administrative penalty in BIS history, on an installment schedule.","distill":"The penalty: $300 million, paid $15 million a quarter for five years. Miss an installment and the remaining balance can come due immediately."},{"id":"r4-audits","section":"r4s4","page":11,"sec":"Order, Third","quote":"Seagate shall complete a total of three (3) audits of its export controls compliance program. The first audit shall be an external audit and the remaining two audits shall be internal audits. Seagate shall hire an unaffiliated third-party consultant with expertise in U.S. export control laws to conduct the external audit.","core":true,"band":"decision-relevant","seg":"audits","why":"The compliance-obligations section: multi-year mandated audits filed with BIS, the template future settlements will follow.","distill":"Three mandated audits of the export-compliance programme: one external, by an unaffiliated consultant, then two internal, each filed with BIS’s San Jose field office on a fixed schedule running into 2027."},{"id":"r4-denial","section":"r4s4","page":12,"sec":"Order, Fifth","quote":"Seagate … shall be made subject to a five-year denial of its export privileges under the Regulations (“denial”). As authorized by Section 766.18(c) of the Regulations, such denial shall be suspended for a period of five years, and shall thereafter be waived, provided that Seagate has made full and timely payment, and has timely completed and submitted the audits as set forth above.","core":true,"band":"verdict-bearing","seg":"denial","why":"The suspended denial order: the existential term hanging over the company for five years.","distill":"A five-year denial of export privileges was imposed and immediately suspended. Pay and audit on schedule and it is waived; slip and BIS can activate it, which for a company built on cross-border hardware is close to a death sentence."},{"id":"r4-d-ecra","section":"r4s1","page":1,"sec":"Order n.1","quote":"On August 13, 2018, the President signed into law the John S. McCain National Defense Authorization Act for Fiscal Year 2019, which includes the Export Control Reform Act of 2018, 50 U.S.C. §§ 4801-4852 (“ECRA”). While Section 1766 of ECRA repeals the provisions of the Export Administration Act of 1979 (“EAA”) … all rules and regulations that were made or issued under the EAA … shall continue in effect according to their terms","core":false,"band":"boilerplate","why":"The statutory-authority footnote. Dense, load-bearing for the lawyers who drafted it, and useless in a distillation.","distill":"The regulations remain in force under ECRA. The footnote every order carries, compressed to its one working sentence."},{"id":"r4-d-entity","section":"r4s1","page":2,"sec":"Order ¶2","quote":"On May 16, 2019, Huawei and certain of its non-U.S. affiliates were added to the Entity List. Licensing requirements were imposed on exports, reexports, and transfers (in-country) of all items subject to the EAR destined to or involving the listed Huawei entities.","core":false,"band":"expected","why":"Background every reader of this document already has. The 2019 listing was global news.","distill":"Huawei went on the Entity List in May 2019. Context the reader arrived with."},{"id":"r4-d-equipment","section":"r4s2","page":4,"sec":"Order ¶9","quote":"Seagate used a fully automated laser-based surface inspection system manufactured by Company One (“Company One’s equipment”) to detect and classify critical defects on HDDs’ substrates and media such as micro pits, bumps, and particles. … At all relevant times, Company One’s equipment was subject to the EAR, classified as ECCN 3B992, and was the direct product of U.S.-origin ECCN 3E991 technology.","core":false,"band":"interesting","why":"The technical detail behind the entire-process holding. Interesting depth, but the interpretation paragraph carries the actionable point.","distill":"The rule attached through inspection and deposition equipment classified 3B992, itself the direct product of US 3E991 technology. The plumbing behind the holding, for readers who want it."},{"id":"r4-d-eager","section":"r4s3","page":7,"sec":"Order ¶19","quote":"In January 2021, Seagate US was notified that Huawei had placed a purchase order for two million HDDs. A Seagate US senior manager wrote upon hearing news of the new purchase order, “this is great!!!”","core":false,"band":"interesting","why":"Vivid colour, and a tempting clip. But the CFO quote and the strategic agreement already carry the chose-this-path story for every reader here.","distill":"“this is great!!!”, wrote a senior manager about a two-million-drive Huawei order. Colour for the feature piece; the CFO quote does the same work with a byline."},{"id":"r4-d-denied","section":"r4s4","page":13,"sec":"Order, Sixth","quote":"the Denied Person … may not, directly or indirectly, participate in any way in any transaction involving any commodity, software or technology … including, but not limited to: A. Applying for, obtaining, or using any license, license exception, or export control document;","core":false,"band":"boilerplate","why":"The standard denied-person terms, operative only if the suspension is revoked. Legal machinery, not a finding.","distill":"The standard denied-person restrictions, dormant unless the suspension is revoked. Machinery, filed under machinery."}],"stakeholders":[{"id":"r4-stk-seagate","name":"Karen Liu","salute":"Karen","role":"Seagate deputy general counsel","glyph":"KL","needsLine":"Bound by the order. Needs the exact obligations and dates: what to pay, what to file, and what hangs over the company.","knows":"Lived the underlying facts; negotiated the settlement. The narrative paragraphs contain nothing she does not know.","knownBy":["violation","cfo","agreement","notice"],"questions":[{"id":"r4q-sea-1","need":"What exactly must we pay, and on what schedule?","check":"$300 million in quarterly $15 million installments over five years, with acceleration if any installment is missed.","answers":["penalty"]},{"id":"r4q-sea-2","need":"What compliance obligations follow, and what happens if we slip?","check":"Three audits filed with BIS on a fixed schedule, under a suspended five-year denial order that activates on default.","answers":["audits","denial"]}]},{"id":"r4-stk-compliance","name":"Miguel Santos","salute":"Miguel","role":"Export-compliance director at a storage-hardware firm","glyph":"MS","needsLine":"Reads enforcement orders to learn where the line is. Needs the losing interpretation and what counted as knowledge.","knows":"Knows the Entity List and the 2020 FDP rule cold; his firm stopped Huawei shipments in 2020.","knownBy":[],"questions":[{"id":"r4q-com-1","need":"Where exactly is the line? What interpretation got Seagate in trouble?","check":"Reading the FDP rule to cover only the last manufacturing stage. BIS holds that covered equipment at any essential stage triggers it.","answers":["interpretation"]},{"id":"r4q-com-2","need":"What did “knowledge” look like on these facts?","check":"A written vendor notification that the equipment was covered, after which shipments continued.","answers":["notice"]}]},{"id":"r4-stk-lawyer","name":"Alexandra Stone","salute":"Alexandra","role":"Trade-controls partner writing the client alert","glyph":"AS","needsLine":"Needs the doctrinal hook and the settlement architecture clients should now expect.","knows":"Tracked the docket; the press release facts are already in her draft.","knownBy":["violation"],"questions":[{"id":"r4q-law-1","need":"Which rule, and which reading of it, does the order turn on?","check":"The Huawei FDP rule, read to reach the entire manufacturing process rather than the final stage.","answers":["interpretation"]},{"id":"r4q-law-2","need":"What settlement architecture should clients expect from BIS now?","check":"Installment penalties plus mandated audits under a suspended denial order: compliance supervision, not just a fine.","answers":["denial","audits"]}]},{"id":"r4-stk-press","name":"James Corrigan","salute":"James","role":"Business reporter","glyph":"JC","needsLine":"Needs the scale, the on-the-record line, and the detail showing the company chose this path.","knows":"Has the BIS press release and the Axelrod quotes from the announcement.","knownBy":[],"questions":[{"id":"r4q-press-1","need":"What is the on-the-record line showing the company chose this path?","check":"The CFO, a month after the rule: no particular restriction, no license needed, while every competitor stopped.","answers":["cfo"]},{"id":"r4q-press-2","need":"How big is this, in numbers?","check":"7.4 million drives, $1.1 billion in shipments, 429 violations, $300 million penalty.","answers":["violation","penalty"]},{"id":"r4q-press-3","need":"What shows deepening commitment rather than a stumble?","check":"A three-year Strategic Cooperation Agreement making Seagate Huawei’s priority supplier, signed months into the violations.","answers":["agreement"]}]}],"upstreamPrompt":"An enforcement order is built evidence-first. Whose data, claims, and access produced this one?","upstream":{"key":[{"id":"u4-oee","label":"BIS investigators (Office of Export Enforcement)","why":"The order is the end product of an OEE investigation; the settlement resolves the proceeding those investigators built."},{"id":"u4-records","label":"Seagate’s subpoenaed business records","why":"The order quotes internal emails, credit approvals, and private agreements. That detail comes from records the government can compel. Compare the voluntary access every other report on this table runs on."},{"id":"u4-rules","label":"The export-control rules themselves (Entity List, FDP rule)","why":"The violation only exists relative to the August 2020 FDP rule; the order spends its first pages establishing what the rule covers."}],"distractors":[{"id":"u4-iaea","label":"IAEA inspectors","why":"Different regime. Nuclear inspectors do not feed Commerce Department enforcement."},{"id":"u4-labs","label":"Frontier labs","why":"A borrowed actor from the AI reports on this table. No lab contributed anything here."},{"id":"u4-panel","label":"Expert reviewer panels","why":"No peer review produces an enforcement order. Evidence and negotiation do."},{"id":"u4-samples","label":"Environmental sampling","why":"Swipe samples find uranium, not hard-drive shipments."}]},"downstreamPrompt":"The order is public by its own ninth term. Who reads it next, and what do they need from it?","downstream":{"key":[{"id":"r4-stk-seagate","label":"Seagate (bound by the order)"},{"id":"r4-stk-compliance","label":"Compliance officers at other hardware firms"},{"id":"r4-stk-lawyer","label":"Trade lawyers writing client alerts"},{"id":"r4-stk-press","label":"Press"}],"distractors":[{"id":"d4-unsc","label":"UN Security Council","why":"US administrative enforcement never reaches the Council’s agenda."},{"id":"d4-align","label":"Alignment researchers","why":"Wrong regime. Nothing here bears on model behaviour."},{"id":"d4-uk","label":"UK ministers and DSIT","why":"A borrowed reader from the AISI report. London has no role in a BIS settlement."},{"id":"d4-public","label":"The public, as primary audience","why":"The order is public, but it is written for the regulated. Deterrence works through compliance desks, not general readers."}]}}];
</script>
<script>
(function () {
  "use strict";

  var PHASES = ["Clip", "Distil", "Upstream", "Downstream", "Thread"];
  var GATE = {
    2: "Clip something first.",
    3: "Distil your clippings first.",
    4: "Commit your upstream picks first.",
    5: "Confirm the readers first."
  };
  var STORAGE_KEY = "lens-widget-context-distiller";

  // ---------- seeded shuffle (FNV-1a + mulberry32, as in XLab's src/lib/shuffle.ts) ----------
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
  function seededShuffle(seed, items) {
    var a = items.slice();
    var rand = prng(hashSeed(seed));
    for (var i = a.length - 1; i > 0; i--) {
      var j = Math.floor(rand() * (i + 1));
      var tmp = a[i]; a[i] = a[j]; a[j] = tmp;
    }
    return a;
  }

  // ---------- engine (mirrors src/lib/verification/engines/context-distiller.ts) ----------
  function indexReport(r) {
    var ix = { blockById: {}, segById: {}, stkById: {}, actorById: {} };
    r.blocks.forEach(function (b) {
      ix.blockById[b.id] = b;
      if (b.core && b.seg) ix.segById[b.seg] = { id: b.seg, text: b.distill, blockId: b.id, page: b.page, sec: b.sec };
    });
    r.stakeholders.forEach(function (s) { ix.stkById[s.id] = s; });
    [r.upstream, r.downstream].forEach(function (grp) {
      grp.key.concat(grp.distractors).forEach(function (o) { ix.actorById[o.id] = o; });
    });
    return ix;
  }
  function freshRun() {
    return { v: 2, mode: "standard", phase: 1, upSel: [], upDone: false, downSel: [], downDone: false,
      clipped: [], flipped: [], threads: [], delivered: false, runs: 0, best: null, tightUnlocked: false, letters: false };
  }
  function sanitizeRun(raw, ix) {
    if (!raw || typeof raw !== "object" || raw.v !== 2 || !Array.isArray(raw.clipped)) return null;
    var out = freshRun();
    out.clipped = raw.clipped.filter(function (id) { return typeof id === "string" && !!ix.blockById[id]; });
    out.flipped = (Array.isArray(raw.flipped) ? raw.flipped : []).filter(function (id) { return typeof id === "string" && out.clipped.indexOf(id) >= 0; });
    var live = producedSegs(out.clipped, ix);
    out.threads = (Array.isArray(raw.threads) ? raw.threads : []).filter(function (t) {
      return Array.isArray(t) && t.length === 2 && live.indexOf(t[0]) >= 0 && !!ix.stkById[t[1]];
    });
    var actor = function (id) { return typeof id === "string" && !!ix.actorById[id]; };
    out.upSel = (Array.isArray(raw.upSel) ? raw.upSel : []).filter(actor);
    out.downSel = (Array.isArray(raw.downSel) ? raw.downSel : []).filter(actor);
    out.upDone = !!raw.upDone;
    out.downDone = !!raw.downDone;
    out.delivered = !!raw.delivered;
    out.mode = raw.mode === "tight" ? "tight" : "standard";
    out.runs = typeof raw.runs === "number" ? raw.runs : 0;
    out.best = raw.best && typeof raw.best === "object" ? raw.best : null;
    out.tightUnlocked = !!raw.tightUnlocked;
    out.letters = !!raw.letters && out.delivered;
    out.phase = Math.max(1, Math.min(5, Number(raw.phase) || 1));
    return out;
  }
  function capFor(run, report) { return run.mode === "tight" ? (report.meta.tightCap || report.meta.cap) : report.meta.cap; }
  function producedSegs(clipped, ix) {
    var out = [];
    clipped.forEach(function (id) { var b = ix.blockById[id]; if (b && b.core && b.seg) out.push(b.seg); });
    return out;
  }
  function seenAllFlips(run) { return run.clipped.every(function (id) { return run.flipped.indexOf(id) >= 0; }); }
  function canEnterPhase(p, run) {
    if (p === 1) return true;
    if (p === 2) return run.clipped.length > 0;
    if (p === 3) return run.clipped.length > 0 && seenAllFlips(run);
    if (p === 4) return run.upDone;
    return run.upDone && run.downDone;
  }
  function evaluateRun(threads, report) {
    var threadedTo = {};
    threads.forEach(function (t) { (threadedTo[t[1]] = threadedTo[t[1]] || {})[t[0]] = true; });
    var v = { answered: {}, wasted: {}, total: 0, ok: 0 };
    report.stakeholders.forEach(function (s) {
      var have = threadedTo[s.id] || {};
      s.questions.forEach(function (q) {
        v.total++;
        var isOk = q.answers.some(function (seg) { return !!have[seg]; });
        v.answered[q.id] = isOk;
        if (isOk) v.ok++;
      });
      v.wasted[s.id] = Object.keys(have).filter(function (seg) { return s.knownBy.indexOf(seg) >= 0; });
    });
    return v;
  }
  function scoreActors(grp, sel) {
    var keyIds = {};
    grp.key.forEach(function (o) { keyIds[o.id] = true; });
    var ok = 0, wrong = 0;
    sel.forEach(function (id) { if (keyIds[id]) ok++; else wrong++; });
    return { ok: ok, wrong: wrong };
  }
  function summarize(run, report, ix) {
    var ev = evaluateRun(run.threads, report);
    var wasted = 0;
    Object.keys(ev.wasted).forEach(function (k) { wasted += ev.wasted[k].length; });
    return { answered: ev.ok, total: ev.total, wasted: wasted, clips: run.clipped.length,
      filler: run.clipped.filter(function (id) { var b = ix.blockById[id]; return !(b && b.core); }).length };
  }

  // ---------- state ----------
  var store = { current: null, runs: {} };
  var ui = { section: null, poolView: "excerpts", armed: null, focus: null, resetArmed: false, status: "" };
  var completedSent = false;
  var resetTimer = null;
  var root = document.getElementById("root");

  function reportById(id) { for (var i = 0; i < REPORTS.length; i++) if (REPORTS[i].id === id) return REPORTS[i]; return null; }
  function currentReport() { return store.current ? reportById(store.current) : null; }
  function currentRun() {
    var r = currentReport();
    if (!r) return null;
    if (!store.runs[r.id]) store.runs[r.id] = freshRun();
    return store.runs[r.id];
  }

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }
  function btn(cls, text, onClick, attrs) {
    var b = el("button", cls, text);
    b.type = "button";
    if (attrs) Object.keys(attrs).forEach(function (k) { b.setAttribute(k, attrs[k]); });
    if (onClick) b.addEventListener("click", onClick);
    return b;
  }
  function plural(n, word) { return n + " " + word + (n === 1 ? "" : "s"); }
  function trunc(s, n) { return s.length > n ? s.slice(0, n - 1).replace(/\s+\S*$/, "") + "…" : s; }

  // ---------- persistence ----------
  function summaryText() {
    var report = currentReport();
    if (!report) return "No report picked yet. The learner is looking at the four report cards.";
    var run = currentRun();
    if (!run) return;
    var ix = indexReport(report);
    var cap = capFor(run, report);
    var parts = [];
    parts.push("Report: " + report.title + " (" + report.author + ", " + report.year + ")" + (run.mode === "tight" ? ", tight-budget mode (" + cap + " clips)" : "") + ".");
    parts.push("Current step: " + run.phase + " " + PHASES[run.phase - 1] + (run.letters ? " (reading the delivered letters)" : "") + ".");
    if (run.clipped.length === 0) {
      parts.push("Notebook empty (0 of " + cap + " clipped).");
    } else {
      parts.push("Clipped " + run.clipped.length + " of " + cap + ", in notebook order: " + run.clipped.map(function (id) {
        var b = ix.blockById[id];
        return "p. " + b.page + " " + b.sec + " (“" + trunc(b.quote, 70) + "”)";
      }).join("; ") + ".");
    }
    if (run.phase >= 2 || run.flipped.length) {
      var fl = run.flipped.length;
      var filler = run.flipped.filter(function (id) { return !ix.blockById[id].core; }).length;
      parts.push("Compressed " + fl + " of " + run.clipped.length + " clippings into the post" + (fl ? "; the screen marks " + filler + " of those as filler" : "") + ".");
    }
    function actorLine(label, grp, sel, done) {
      if (!sel.length && !done) return label + ": no picks yet.";
      var names = sel.map(function (id) { return ix.actorById[id] ? ix.actorById[id].label : id; });
      var s = label + " picks: " + (names.length ? names.join("; ") : "none");
      if (done) {
        var sc = scoreActors(grp, sel);
        var missed = grp.key.filter(function (o) { return sel.indexOf(o.id) < 0; }).map(function (o) { return o.label; });
        s += ". Committed: " + sc.ok + " of " + grp.key.length + " found, " + sc.wrong + " wrong" + (missed.length ? ", missed: " + missed.join("; ") : "");
      } else s += " (not committed)";
      return s + ".";
    }
    if (run.phase >= 3 || run.upSel.length) parts.push(actorLine("Upstream", report.upstream, run.upSel, run.upDone));
    if (run.phase >= 4 || run.downSel.length) parts.push(actorLine("Downstream", report.downstream, run.downSel, run.downDone));
    if (run.phase >= 5 || run.threads.length) {
      if (!run.threads.length) parts.push("No threads pinned yet.");
      else parts.push("Threads: " + run.threads.map(function (t) {
        var s = ix.segById[t[0]], k = ix.stkById[t[1]];
        return "p. " + s.page + " " + s.sec + " to " + k.name;
      }).join("; ") + ".");
    }
    if (run.delivered) {
      var ev = evaluateRun(run.threads, report);
      var sm = summarize(run, report, ix);
      var un = [];
      report.stakeholders.forEach(function (s) {
        s.questions.forEach(function (q) { if (!ev.answered[q.id]) un.push(s.name + ": “" + q.need + "”"); });
      });
      parts.push("Delivered: " + ev.ok + " of " + ev.total + " reader questions answered" + (un.length ? ". Unanswered: " + un.join("; ") : "") + ".");
      parts.push("Filler clips: " + sm.filler + ". Points threaded to readers who already knew them: " + sm.wasted + ". Deliveries so far: " + run.runs + (run.tightUnlocked ? "; tight-budget mode unlocked" : "") + ".");
    }
    return parts.join(" ");
  }
  function persist() {
    var data = { current: store.current, runs: store.runs };
    if (window.Lens) {
      Lens.saveState(data, summaryText());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(data)); } catch (e) { }
    }
  }
  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      var runs = saved.runs && typeof saved.runs === "object" ? saved.runs : {};
      REPORTS.forEach(function (r) {
        var s = sanitizeRun(runs[r.id], indexReport(r));
        if (s) store.runs[r.id] = s;
      });
      if (typeof saved.current === "string" && reportById(saved.current)) store.current = saved.current;
    }
    completedSent = !!(meta && meta.completed);
    ui.section = null;
    render();
  }

  // ---------- actions ----------
  function setStatus(s) { ui.status = s; }
  function goPhase(p) {
    var run = currentRun();
    if (!run) return;
    if (!canEnterPhase(p, run)) { setStatus(GATE[p] || "Not yet."); render(); return; }
    run.phase = p; run.letters = false; ui.armed = null; ui.focus = null; setStatus("");
    persist(); render();
  }
  function addClip(id) {
    var run = currentRun(), report = currentReport();
    if (!run) return;
    if (run.clipped.indexOf(id) >= 0) return;
    if (run.clipped.length >= capFor(run, report)) { setStatus("Notebook full: remove a clipping to swap."); render(); return; }
    run.clipped.push(id); run.delivered = false; run.letters = false; setStatus("");
    persist(); render();
  }
  function removeClip(id) {
    var run = currentRun();
    if (!run) return;
    var ix = indexReport(currentReport());
    run.clipped = run.clipped.filter(function (x) { return x !== id; });
    run.flipped = run.flipped.filter(function (x) { return x !== id; });
    var live = producedSegs(run.clipped, ix);
    var before = run.threads.length;
    run.threads = run.threads.filter(function (t) { return live.indexOf(t[0]) >= 0; });
    var dropped = before - run.threads.length;
    setStatus(dropped > 0 ? plural(dropped, "thread") + " dropped: the point it fastened to is gone." : "");
    run.delivered = false; run.letters = false;
    persist(); render();
  }
  function moveClip(idx, dir) {
    var run = currentRun();
    if (!run) return;
    var j = idx + dir;
    if (j < 0 || j >= run.clipped.length) return;
    var tmp = run.clipped[idx]; run.clipped[idx] = run.clipped[j]; run.clipped[j] = tmp;
    run.delivered = false; run.letters = false;
    persist(); render();
  }
  function flip(id) {
    var run = currentRun();
    if (!run) return;
    if (run.flipped.indexOf(id) < 0) run.flipped.push(id);
    persist(); render();
  }
  function flipAll() {
    var run = currentRun();
    if (!run) return;
    run.flipped = run.clipped.slice();
    persist(); render();
  }
  function toggleActor(which, id) {
    var run = currentRun();
    if (!run) return;
    var key = which === "up" ? "upSel" : "downSel";
    var i = run[key].indexOf(id);
    if (i >= 0) run[key].splice(i, 1); else run[key].push(id);
    persist(); render();
  }
  function commitActors(which, done) {
    var run = currentRun();
    if (!run) return;
    run[which === "up" ? "upDone" : "downDone"] = done;
    persist(); render();
  }
  function addThread(seg, stk) {
    var run = currentRun();
    if (!run) return;
    var ix = indexReport(currentReport());
    if (producedSegs(run.clipped, ix).indexOf(seg) < 0 || !ix.stkById[stk]) return;
    var dup = run.threads.some(function (t) { return t[0] === seg && t[1] === stk; });
    if (dup) { setStatus("Already threaded."); }
    else { run.threads.push([seg, stk]); run.delivered = false; run.letters = false; setStatus(""); }
    ui.focus = null;
    persist(); render();
  }
  function removeThread(i) {
    var run = currentRun();
    if (!run) return;
    run.threads.splice(i, 1);
    run.delivered = false; run.letters = false; ui.focus = null;
    persist(); render();
  }
  function tapPin(type, id) {
    var run = currentRun();
    if (!run) return;
    if (run.delivered) return;
    if (!ui.armed || ui.armed.type === type) {
      ui.armed = { type: type, id: id };
      setStatus(type === "seg" ? "Now tap a reader’s pin." : "Now tap a point’s pin.");
      render();
      return;
    }
    var seg = type === "seg" ? id : ui.armed.id;
    var stk = type === "stk" ? id : ui.armed.id;
    ui.armed = null;
    addThread(seg, stk);
  }
  function deliver() {
    var run = currentRun(), report = currentReport();
    if (!run) return;
    var ix = indexReport(report);
    if (!run.threads.length) return;
    var ev = evaluateRun(run.threads, report);
    run.delivered = true;
    run.runs += 1;
    var sm = summarize(run, report, ix);
    if (!run.best || sm.answered > run.best.answered) run.best = sm;
    if (ev.ok === ev.total && run.mode === "standard") run.tightUnlocked = true;
    ui.armed = null;
    setStatus(ev.ok === ev.total ? "Every reader got what they needed." : ev.ok + " / " + ev.total + " questions answered.");
    persist();
    if (window.Lens && !completedSent) { completedSent = true; Lens.complete(); }
    render();
  }
  function revise() {
    var run = currentRun();
    if (!run) return;
    run.delivered = false; run.letters = false; ui.focus = null;
    persist(); render();
  }
  function showLetters(on) {
    var run = currentRun();
    if (!run) return;
    run.letters = on; ui.focus = null;
    persist(); render();
  }
  function startTight() {
    var run = currentRun(), report = currentReport();
    if (!run) return;
    var next = freshRun();
    next.mode = "tight"; next.best = run.best; next.runs = run.runs; next.tightUnlocked = run.tightUnlocked;
    store.runs[report.id] = next;
    ui.section = null; ui.armed = null; ui.focus = null;
    setStatus("Tight budget: " + report.meta.tightCap + " clips, same facts that matter. Triage.");
    persist(); render();
  }
  function wipe() {
    if (!ui.resetArmed) {
      ui.resetArmed = true;
      clearTimeout(resetTimer);
      resetTimer = setTimeout(function () { ui.resetArmed = false; render(); }, 2500);
      render();
      return;
    }
    clearTimeout(resetTimer);
    ui.resetArmed = false;
    var run = currentRun(), report = currentReport();
    if (!run) return;
    var next = freshRun();
    next.tightUnlocked = run.tightUnlocked;
    store.runs[report.id] = next;
    ui.section = null; ui.armed = null; ui.focus = null;
    setStatus("Wiped clean.");
    persist(); render();
  }
  function pickReport(id) {
    store.current = id; ui.section = null; ui.poolView = "excerpts"; ui.armed = null; ui.focus = null; setStatus("");
    persist(); render();
  }
  function leaveReport() {
    store.current = null; ui.armed = null; ui.focus = null; setStatus("");
    persist(); render();
  }

  // ---------- rendering ----------
  function render() {
    root.textContent = "";
    var report = currentReport();
    if (!report) { renderPicker(); return; }
    var run = currentRun();
    if (!run) return;
    var ix = indexReport(report);
    root.appendChild(renderBar(report));
    if (run.letters && run.delivered) { root.appendChild(renderLetters(report, run, ix)); return; }
    root.appendChild(renderRail(run));
    root.appendChild(renderLead(report, run.phase));
    var status = el("p", "status", ui.status);
    status.setAttribute("role", "status");
    root.appendChild(status);
    var stage = el("div", "stage");
    if (run.phase === 1) stage.appendChild(renderClip(report, run, ix));
    else if (run.phase === 2) stage.appendChild(renderDistil(report, run, ix));
    else if (run.phase === 3) stage.appendChild(renderActors(report, run, ix, "up"));
    else if (run.phase === 4) stage.appendChild(renderActors(report, run, ix, "down"));
    else stage.appendChild(renderThread(report, run, ix));
    root.appendChild(stage);
    if (run.phase === 5) requestAnimationFrame(drawThreads);
  }

  function renderPicker() {
    var intro = el("p", "intro");
    intro.appendChild(document.createTextNode("Four documents, one discipline. "));
    intro.appendChild(el("b", null, "Pick a report to distil."));
    intro.appendChild(el("span", "sub", "Each is a verification report: one actor’s claims, another’s access, and readers waiting on the result."));
    root.appendChild(intro);
    var grid = el("div", "picker");
    REPORTS.forEach(function (r) {
      var b = btn("pick", null, function () { pickReport(r.id); });
      b.appendChild(el("span", "xs muted", r.kind + " · " + (r.fictional ? "fictional" : "real document")));
      b.appendChild(el("span", "title", r.title));
      b.appendChild(el("span", "xs muted", r.author + " · " + r.year));
      b.appendChild(el("span", "blurb", r.blurb));
      grid.appendChild(b);
    });
    root.appendChild(grid);
  }

  function renderBar(report) {
    var bar = el("div", "bar");
    bar.appendChild(el("span", "xs muted", report.kind));
    bar.appendChild(el("span", "title", report.title));
    bar.appendChild(el("span", "xs muted", report.author + " · " + report.year));
    if (report.fictional) {
      bar.appendChild(el("span", "pill", "fictional teaching document"));
    } else {
      var a = el("a", "xs", "source ↗");
      a.href = report.sourceUrl; a.target = "_blank"; a.rel = "noopener";
      bar.appendChild(a);
    }
    var sp = el("span", "spacer");
    sp.appendChild(btn("ghost small", "Change report", leaveReport));
    sp.appendChild(btn((ui.resetArmed ? "primary" : "ghost") + " small", ui.resetArmed ? "Tap again to wipe" : "Reset", wipe));
    bar.appendChild(sp);
    return bar;
  }

  function renderRail(run) {
    var rail = el("div", "rail");
    var done = [
      run.clipped.length > 0 && run.phase > 1,
      run.clipped.length > 0 && seenAllFlips(run) && run.phase > 2,
      run.upDone,
      run.downDone,
      run.delivered
    ];
    PHASES.forEach(function (name, i) {
      var p = i + 1;
      var active = run.phase === p;
      var reachable = canEnterPhase(p, run);
      var b = btn((active ? "is-current " : "") + (done[i] ? "is-done" : ""), null, function () { goPhase(p); });
      b.disabled = !reachable;
      if (active) b.setAttribute("aria-current", "step");
      b.appendChild(el("span", "n", done[i] && !active ? "✓" : String(p)));
      b.appendChild(el("span", null, name));
      rail.appendChild(b);
    });
    return rail;
  }

  function renderLead(report, phase) {
    var p = el("p", "lead");
    var rubric;
    if (phase === 1) {
      p.appendChild(document.createTextNode("A report is mostly true and mostly forgettable. "));
      p.appendChild(el("b", null, "Clip only the handful of facts that would change what a reader does"));
      p.appendChild(document.createTextNode(" and reject the rest."));
      rubric = "The editorial test: “Would any of my audiences act differently knowing this?”";
    } else if (phase === 2) {
      p.appendChild(document.createTextNode("Each clipping compresses into the post, in the order you filed it. "));
      p.appendChild(el("b", null, "What you didn’t clip simply isn’t here."));
      rubric = "Facts you skipped leave no placeholder. That silence is the point.";
    } else if (phase === 3) {
      p.appendChild(document.createTextNode(report.upstreamPrompt));
      rubric = "Every claim in the document rests on somebody’s access. Upstream sets what the report can honestly say.";
    } else if (phase === 4) {
      p.appendChild(document.createTextNode(report.downstreamPrompt));
      rubric = "The readers you confirm become the desks on the threading board.";
    } else {
      p.appendChild(document.createTextNode("Thread each distilled point to the readers who need it. "));
      p.appendChild(el("b", null, "Deliver, and every unanswered question turns red."));
      rubric = "Different readers need different facts, and already know different things.";
    }
    p.appendChild(el("span", "rubric", rubric));
    return p;
  }

  function paneHead(title, hint) {
    var h = el("h4", "pane-head", title);
    if (hint) h.appendChild(el("span", null, ": " + hint));
    return h;
  }
  function blockTag(b, source) {
    var t = el("span", "tag");
    t.appendChild(el("b", null, "p. " + b.page));
    t.appendChild(el("span", null, "§" + b.sec));
    if (source) t.appendChild(el("span", null, source));
    return t;
  }
  function foot() { return el("div", "foot"); }

  function renderClip(report, run, ix) {
    var cap = capFor(run, report);
    if (!ui.section || !report.sections.some(function (s) { return s.id === ui.section; })) ui.section = report.sections[0].id;
    if (!report.reportDoc) ui.poolView = "excerpts";
    var wrap = el("div");
    var two = el("div", "two");

    // left: pool
    var left = el("div");
    if (report.reportDoc) {
      var tg = el("div", "toggle");
      tg.setAttribute("role", "group");
      tg.setAttribute("aria-label", "Pool view");
      [["excerpts", "Excerpts"], ["report", "Full report"]].forEach(function (v) {
        var b = btn(ui.poolView === v[0] ? "is-on" : "", v[1], function () { ui.poolView = v[0]; render(); });
        b.setAttribute("aria-pressed", ui.poolView === v[0] ? "true" : "false");
        tg.appendChild(b);
      });
      left.appendChild(tg);
    }
    var chips = el("div", "chips");
    report.sections.forEach(function (sec) {
      var n = report.blocks.filter(function (b) { return b.section === sec.id && run.clipped.indexOf(b.id) >= 0; }).length;
      var on = ui.poolView === "excerpts" && sec.id === ui.section;
      var c = btn("chip" + (on ? " is-on" : ""), null, function () {
        if (ui.poolView === "report") {
          var target = document.getElementById("dsec-" + sec.id);
          if (target && target.scrollIntoView) target.scrollIntoView({ block: "start", behavior: "smooth" });
        } else { ui.section = sec.id; render(); }
      });
      if (on) c.setAttribute("aria-current", "true");
      c.appendChild(el("b", null, sec.tag));
      c.appendChild(el("span", null, sec.name));
      c.appendChild(el("span", "count" + (n ? " has" : ""), String(n)));
      chips.appendChild(c);
    });
    left.appendChild(chips);

    if (ui.poolView === "report" && report.reportDoc) {
      left.appendChild(paneHead("The full report", "read it through; tap a highlighted passage to clip it"));
      var doc = el("div", "box doc");
      report.sections.forEach(function (sec) {
        var paras = report.reportDoc[sec.id] || [];
        var pages = report.blocks.filter(function (b) { return b.section === sec.id; }).map(function (b) { return b.page; });
        var section = el("section");
        section.id = "dsec-" + sec.id;
        var h = el("h4");
        h.appendChild(el("span", "tag", sec.tag));
        h.appendChild(el("span", null, sec.name));
        if (pages.length) h.appendChild(el("span", "pg", "p. " + Math.min.apply(null, pages)));
        section.appendChild(h);
        paras.forEach(function (p) {
          if (typeof p === "string") { section.appendChild(el("p", "para", p)); return; }
          var b = ix.blockById[p.b];
          if (!b) return;
          section.appendChild(passageCard(b, run, null));
        });
        doc.appendChild(section);
      });
      left.appendChild(doc);
    } else {
      left.appendChild(paneHead("Candidate clippings", "tap one to file it in your notebook"));
      var pool = seededShuffle(report.id + ":" + ui.section, report.blocks.filter(function (b) { return b.section === ui.section; }));
      var list = el("div", "box list");
      pool.forEach(function (b) { list.appendChild(passageCard(b, run, report.meta.source)); });
      if (!pool.length) list.appendChild(el("p", "blank", "No excerpts in this section."));
      left.appendChild(list);
    }
    two.appendChild(left);

    // right: notebook
    var right = el("div");
    right.appendChild(paneHead("Your notebook"));
    var nb = el("div", "box");
    var head = el("div", "nb-head");
    head.appendChild(el("span", null, "Clippings"));
    head.appendChild(el("span", "cnt" + (run.clipped.length >= cap ? " full" : ""), run.clipped.length + " / " + cap + " clipped" + (run.mode === "tight" ? " (tight budget)" : "")));
    nb.appendChild(head);
    if (!run.clipped.length) {
      var blank = el("p", "blank", "This page is blank.");
      blank.appendChild(el("span", null, "Clip the excerpts that would change what your readers do."));
      nb.appendChild(blank);
    } else {
      var lst = el("div", "list");
      run.clipped.forEach(function (id, idx) {
        var b = ix.blockById[id];
        var card = el("div", "card clip");
        card.appendChild(blockTag(b));
        card.appendChild(el("p", "quote", b.quote));
        var tools = el("div", "tools");
        tools.appendChild(btn(null, "✕", function () { removeClip(id); }, { "aria-label": "Remove clipping", title: "Remove clipping" }));
        var up = btn(null, "↑", function () { moveClip(idx, -1); }, { "aria-label": "Move up", title: "Move up" });
        up.disabled = idx === 0;
        var down = btn(null, "↓", function () { moveClip(idx, 1); }, { "aria-label": "Move down", title: "Move down" });
        down.disabled = idx === run.clipped.length - 1;
        tools.appendChild(up); tools.appendChild(down);
        card.appendChild(tools);
        lst.appendChild(card);
      });
      nb.appendChild(lst);
    }
    right.appendChild(nb);
    two.appendChild(right);
    wrap.appendChild(two);

    var f = foot();
    var cnt = el("span", "muted");
    cnt.appendChild(document.createTextNode("Notebook: "));
    cnt.appendChild(el("b", null, String(run.clipped.length)));
    cnt.appendChild(document.createTextNode(" / " + cap + " clipped"));
    f.appendChild(cnt);
    var next = btn("primary", "Distil →", function () { goPhase(2); });
    next.disabled = run.clipped.length === 0;
    f.appendChild(next);
    wrap.appendChild(f);
    return wrap;
  }

  function passageCard(b, run, source) {
    var clipped = run.clipped.indexOf(b.id) >= 0;
    var card = el("div", "card" + (clipped ? " is-filed" : ""));
    if (source) card.appendChild(blockTag(b, source));
    else card.appendChild(el("span", "tag", "p. " + b.page));
    card.appendChild(el("p", "quote", b.quote));
    var act = el("div", "act");
    if (clipped) act.appendChild(el("span", "filed", "✓ filed"));
    else act.appendChild(btn("small", "+ Clip", function () { addClip(b.id); }));
    card.appendChild(act);
    return card;
  }

  function renderDistil(report, run, ix) {
    var wrap = el("div", "post");
    var head = el("div", "post-head");
    head.appendChild(el("h3", null, report.meta.postTitle));
    head.appendChild(el("p", "muted", "a distillation " + report.meta.postByline));
    wrap.appendChild(head);
    var allSeen = seenAllFlips(run);
    if (!allSeen) wrap.appendChild(el("p", "muted", "Tap each clipping to compress it into the post. What you didn’t clip simply isn’t here."));
    var stack = el("div", "stack");
    if (!allSeen) stack.style.marginTop = "12px";
    run.clipped.forEach(function (id, idx) {
      var b = ix.blockById[id];
      var seen = run.flipped.indexOf(id) >= 0;
      if (!seen) {
        var f = btn("flip", null, function () { flip(id); });
        f.appendChild(el("span", "n", (idx + 1) + "."));
        f.appendChild(el("span", null, "Clipping from p. " + b.page + ": tap to compress"));
        stack.appendChild(f);
        return;
      }
      var card = el("div", "card dist" + (b.core ? "" : " is-filler"));
      var bq = el("blockquote");
      bq.appendChild(el("b", null, "p. " + b.page + " · §" + b.sec + " · " + report.meta.source));
      bq.appendChild(document.createTextNode(b.quote));
      card.appendChild(bq);
      card.appendChild(el("p", "text", b.distill));
      if (!b.core) card.appendChild(el("p", "note", "(filler; nothing here changes what a reader does.)"));
      stack.appendChild(card);
    });
    wrap.appendChild(stack);
    var f = foot();
    f.appendChild(btn("ghost left", "← Clip", function () { goPhase(1); }));
    if (allSeen) f.appendChild(btn("primary", "Trace the actors →", function () { goPhase(3); }));
    else f.appendChild(btn(null, "Compress all", flipAll));
    wrap.appendChild(f);
    return wrap;
  }

  function renderActors(report, run, ix, which) {
    var group = which === "up" ? report.upstream : report.downstream;
    var sel = which === "up" ? run.upSel : run.downSel;
    var done = which === "up" ? run.upDone : run.downDone;
    var keyIds = {};
    group.key.forEach(function (o) { keyIds[o.id] = true; });
    var options = seededShuffle(report.id + ":" + which, group.key.concat(group.distractors));
    var wrap = el("div");
    var grid = el("div", "actors");
    options.forEach(function (o) {
      var isSel = sel.indexOf(o.id) >= 0;
      var isKey = !!keyIds[o.id];
      var cls = "card actor";
      var badge = null;
      if (done) {
        if (isKey && isSel) { cls += " is-key"; badge = el("span", "badge yes", "✓ yes"); }
        else if (isKey) { cls += " is-missed"; badge = el("span", "badge missed", "missed"); }
        else if (isSel) { cls += " is-wrong"; badge = el("span", "badge no", "✕ no"); }
        else badge = el("span", "badge", "left out");
      } else if (isSel) cls += " is-sel";
      var card = el("div", cls);
      var row = btn("row", null, function () { toggleActor(which, o.id); });
      row.disabled = done;
      row.setAttribute("aria-pressed", isSel ? "true" : "false");
      row.appendChild(el("span", "cb", isSel ? "✓" : ""));
      row.appendChild(el("span", "lbl", o.label));
      if (badge) row.appendChild(badge);
      card.appendChild(row);
      if (done) {
        var why = which === "down" && isKey && ix.stkById[o.id] && ix.stkById[o.id].needsLine ? ix.stkById[o.id].needsLine : (o.why || "");
        if (why) card.appendChild(el("p", "why", why));
      }
      grid.appendChild(card);
    });
    wrap.appendChild(grid);
    var f = foot();
    if (which === "up") f.appendChild(btn("ghost left", "← Distil", function () { goPhase(2); }));
    else f.appendChild(btn("ghost left", "← Upstream", function () { goPhase(3); }));
    if (done) {
      var sc = scoreActors(group, sel);
      f.appendChild(el("span", "muted", sc.ok + " of " + group.key.length + " found · " + sc.wrong + " wrong"));
      f.appendChild(btn("ghost", "Revise picks", function () { commitActors(which, false); }));
      f.appendChild(btn("primary", which === "up" ? "Who reads it next? →" : "Thread to readers →", function () { goPhase(which === "up" ? 4 : 5); }));
    } else {
      var c = btn("primary", which === "up" ? "Commit picks" : "Commit readers", function () { commitActors(which, true); });
      c.disabled = sel.length === 0;
      f.appendChild(c);
    }
    wrap.appendChild(f);
    return wrap;
  }

  function pin(type, id, armed, disabled, label) {
    var b = btn("pin" + (armed ? " is-armed" : ""), "", function () { tapPin(type, id); }, { "aria-label": label, title: label });
    b.setAttribute("data-pin", type + ":" + id);
    b.setAttribute("aria-pressed", armed ? "true" : "false");
    b.disabled = disabled;
    return b;
  }

  function renderThread(report, run, ix) {
    var wrap = el("div");
    var verdict = run.delivered ? evaluateRun(run.threads, report) : null;
    var filler = run.clipped.filter(function (id) { return !ix.blockById[id].core; }).length;
    if (verdict) {
      var v = el("div", "box verdict " + (verdict.ok === verdict.total ? "is-ok" : "is-short"));
      v.appendChild(el("p", "h", verdict.ok + " / " + verdict.total + " reader questions answered"));
      var body = verdict.ok === verdict.total
        ? "Every question answered. Select a reader to trace their threads."
        : "Each red question expands to the block that would have answered it. A fact you never clipped can’t reach anyone: that gap is the lesson.";
      if (filler > 0) body += " You spent " + plural(filler, "clip") + " on filler that reached no one.";
      v.appendChild(el("p", "b", body));
      wrap.appendChild(v);
    }
    var board = el("div", "board");
    board.id = "board";
    var svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
    svg.setAttribute("aria-hidden", "true");
    svg.id = "threads-svg";
    board.appendChild(svg);
    var two = el("div", "two");
    var segs = producedSegs(run.clipped, ix);

    var left = el("div", "stack");
    left.appendChild(el("h4", "col-head", "Your distilled points"));
    if (!segs.length) left.appendChild(el("p", "muted", "You distilled no substantive points: go back and clip the facts that matter."));
    segs.forEach(function (segId) {
      var s = ix.segById[segId];
      var lit = ui.focus ? run.threads.some(function (t) { return t[0] === segId && t[1] === ui.focus; }) : false;
      var card = el("div", "card point" + (lit ? " is-lit" : "") + (ui.focus && !lit ? " is-dim" : ""));
      card.appendChild(el("span", "tag", "p. " + s.page + " · §" + s.sec));
      card.appendChild(el("p", "text", s.text));
      card.appendChild(pin("seg", segId, !!(ui.armed && ui.armed.type === "seg" && ui.armed.id === segId), run.delivered, "Pull a thread from this point (p. " + s.page + ")"));
      left.appendChild(card);
    });
    two.appendChild(left);

    var right = el("div", "stack");
    right.appendChild(el("h4", "col-head", "Who needs to hear it"));
    report.stakeholders.forEach(function (s) { right.appendChild(readerCard(s, report, run, ix, verdict)); });
    two.appendChild(right);
    board.appendChild(two);
    wrap.appendChild(board);

    var f = foot();
    f.appendChild(btn("ghost left", "← Downstream", function () { goPhase(4); }));
    f.appendChild(el("span", "muted", plural(run.threads.length, "thread") + " pinned"));
    if (run.delivered) {
      f.appendChild(btn(null, "Revise", revise));
      f.appendChild(btn("primary", "Read the reports →", function () { showLetters(true); }));
    } else {
      var d = btn("primary", "Deliver reports", deliver);
      d.disabled = run.threads.length === 0;
      f.appendChild(d);
    }
    wrap.appendChild(f);
    return wrap;
  }

  function readerCard(s, report, run, ix, verdict) {
    var mine = [];
    run.threads.forEach(function (t, i) { if (t[1] === s.id) mine.push({ t: t, i: i }); });
    var wasted = verdict ? (verdict.wasted[s.id] || []) : [];
    var focused = ui.focus === s.id;
    var card = el("div", "card reader" + (focused ? " is-focus" : "") + (ui.focus && !focused ? " is-dim" : ""));
    card.appendChild(pin("stk", s.id, !!(ui.armed && ui.armed.type === "stk" && ui.armed.id === s.id), run.delivered, "Fasten a thread to " + s.name));
    var who = el("div", "who");
    who.appendChild(el("span", "glyph", s.glyph));
    var nm = el("span");
    nm.appendChild(el("span", "name", s.name));
    nm.appendChild(el("span", "role", s.role));
    who.appendChild(nm);
    card.appendChild(who);
    if (s.needsLine) card.appendChild(el("p", "needs", s.needsLine));
    var knows = el("p", "knows");
    knows.appendChild(el("b", null, "Already knows: "));
    knows.appendChild(document.createTextNode(s.knows));
    card.appendChild(knows);
    if (mine.length) {
      var th = el("div", "threads");
      mine.forEach(function (m) {
        var chip = el("span", "thread", "p. " + (ix.segById[m.t[0]] ? ix.segById[m.t[0]].page : "?"));
        if (!run.delivered) chip.appendChild(btn(null, "✕", function () { removeThread(m.i); }, { "aria-label": "Remove this thread", title: "Remove this thread" }));
        th.appendChild(chip);
      });
      card.appendChild(th);
    }
    var ul = el("ul", "qs");
    s.questions.forEach(function (q) {
      var ok = verdict ? verdict.answered[q.id] : null;
      var li = el("li", "q" + (verdict ? (ok ? " is-ok" : " is-bad") : ""));
      li.appendChild(el("span", "need", q.need));
      li.appendChild(el("span", "check", "Needs: " + q.check));
      if (verdict) {
        li.appendChild(el("span", "res" + (ok ? " ok" : ""), ok ? "✓ answered" : "✕ unanswered"));
        if (!ok) {
          var seg = ix.segById[q.answers[0]];
          var blk = seg ? ix.blockById[seg.blockId] : null;
          if (blk) {
            var miss = el("span", "miss");
            miss.appendChild(el("b", null, "p. " + blk.page + " · §" + blk.sec + ": "));
            miss.appendChild(document.createTextNode(blk.quote));
            var w = el("span", "w");
            w.appendChild(el("b", null, "Why it mattered: "));
            w.appendChild(document.createTextNode(blk.why));
            miss.appendChild(w);
            li.appendChild(miss);
          }
        }
      }
      ul.appendChild(li);
    });
    card.appendChild(ul);
    if (wasted.length) card.appendChild(el("p", "wasted", "You threaded " + plural(wasted.length, "point") + " they already knew: words spent on somebody who did not need them."));
    if (run.delivered && mine.length) {
      var t = btn("trace", focused ? "Clear trace" : "Trace their threads", function () { ui.focus = focused ? null : s.id; render(); });
      t.setAttribute("aria-pressed", focused ? "true" : "false");
      card.appendChild(t);
    }
    return card;
  }

  function drawThreads() {
    var board = document.getElementById("board");
    var svg = document.getElementById("threads-svg");
    if (!board || !svg) return;
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    var run = currentRun();
    if (!run) return;
    var b = board.getBoundingClientRect();
    if (!b.width) return;
    function centre(sel) {
      var e = board.querySelector(sel);
      if (!e) return null;
      var r = e.getBoundingClientRect();
      return { x: r.left + r.width / 2 - b.left, y: r.top + r.height / 2 - b.top };
    }
    run.threads.forEach(function (t) {
      var a = centre('[data-pin="seg:' + t[0] + '"]');
      var c = centre('[data-pin="stk:' + t[1] + '"]');
      if (!a || !c) return;
      var dist = Math.hypot(c.x - a.x, c.y - a.y);
      var mx = (a.x + c.x) / 2;
      var my = (a.y + c.y) / 2 + Math.min(70, dist * 0.18) + 14;
      var dim = !!ui.focus && t[1] !== ui.focus;
      var path = document.createElementNS("http://www.w3.org/2000/svg", "path");
      path.setAttribute("d", "M " + a.x + " " + a.y + " Q " + mx + " " + my + " " + c.x + " " + c.y);
      path.setAttribute("fill", "none");
      path.setAttribute("stroke", "#b87018");
      path.setAttribute("stroke-width", dim ? "1.4" : "2.2");
      path.setAttribute("stroke-linecap", "round");
      path.setAttribute("opacity", dim ? "0.35" : "1");
      svg.appendChild(path);
    });
  }

  function renderLetters(report, run, ix) {
    var wrap = el("div", "stage");
    wrap.style.paddingTop = "16px";
    wrap.appendChild(el("p", "lead", "Every reader gets the report you actually threaded them: no more, no less. Where a question went unanswered, the letter says so plainly."));
    var verdict = evaluateRun(run.threads, report);
    var ordered = producedSegs(run.clipped, ix);
    var grid = el("div", "letters");
    report.stakeholders.forEach(function (s) {
      var got = {};
      run.threads.forEach(function (t) { if (t[1] === s.id) got[t[0]] = true; });
      var points = ordered.filter(function (seg) { return !!got[seg]; });
      var reds = s.questions.filter(function (q) { return !verdict.answered[q.id]; });
      var card = el("div", "card letter");
      card.appendChild(el("p", "dear", "Dear " + (s.salute || s.name.split(" ")[0]) + ","));
      card.appendChild(el("p", "role", s.role));
      if (points.length) points.forEach(function (seg) { card.appendChild(el("p", "pt", ix.segById[seg].text)); });
      else card.appendChild(el("p", "none", "(you sent this reader nothing.)"));
      reds.forEach(function (q) {
        var r = el("p", "red");
        r.appendChild(el("b", null, "Still unanswered: "));
        r.appendChild(document.createTextNode(q.need));
        card.appendChild(r);
      });
      card.appendChild(el("p", "sig", "(your distillation)"));
      grid.appendChild(card);
    });
    wrap.appendChild(grid);
    var f = foot();
    f.appendChild(btn("ghost left", "← Back to the board", function () { showLetters(false); }));
    if (run.tightUnlocked && run.mode === "standard") f.appendChild(btn(null, "Try tight-budget mode", startTight));
    wrap.appendChild(f);
    return wrap;
  }

  // ---------- boot ----------
  window.addEventListener("resize", drawThreads);
  window.addEventListener("keydown", function (e) {
    if (e.key !== "Escape") return;
    if (ui.armed || ui.focus) { ui.armed = null; ui.focus = null; render(); }
  });

  if (window.Lens) {
    render();
    Lens.onState(hydrate);
  } else {
    var saved = null;
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { }
    hydrate(saved, null);
  }
})();
</script>
</body>
</html>
