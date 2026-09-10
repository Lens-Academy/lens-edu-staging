---
id: 'a1d2e3f4-5b6c-4d7e-8f90-1a2b3c4d5e02'
title: The types of AI
summary_for_tutor: A concentric diagram of AI categories, outermost to innermost - AI, Narrow AI, Machine Learning, Deep Learning, Generative AI, Large Language Models, Transformer LLMs - with example systems placed in each ring (Roomba, Deep Blue, Amazon spam filter, FaceID, Midjourney, Mamba, Claude, ChatGPT...). The learner taps a ring or an example to read what it is and why it sits at that ring and not the next one in. The grey margin outside the coloured rings is non-narrow AI (AGI and ASI), which XLab labels theoretical only, or possible but absurd in resource terms. The diagram zooms and pans. Content ported from XLab's Verification track.
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The types of AI</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "types-of-ai". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --border: #e8e5df;
    --muted: #faf8f3;
    --muted-fg: #5a5a5a;
    --fg: #1a1a1a;
    --card: #ffffff;
    --primary: #b87018;
    --primary-soft: rgba(184, 112, 24, 0.18);
    --font-ui: "DM Sans", Arial, sans-serif;
    --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    font-family: var(--font-ui);
    font-size: 14px;
    line-height: 1.5;
    color: var(--fg);
    background: var(--card);
  }
  .layout { display: grid; gap: 16px; align-items: start; }
  .layout > * { min-width: 0; }
  /* Side panel only when there is room for a readable diagram next to it (XLab uses the same 1024px breakpoint). */
  @media (min-width: 1024px) { .layout { grid-template-columns: minmax(0, 1fr) 16rem; } }
  .diagram { position: relative; border: 1px solid var(--border); border-radius: 12px; overflow: hidden; background: var(--card); }
  .stage { position: relative; width: 100%; aspect-ratio: 1180 / 1240; }
  svg { position: absolute; inset: 0; width: 100%; height: 100%; display: block; user-select: none; -webkit-user-select: none; }
  .diagram.is-zoomed svg { touch-action: none; cursor: grab; }
  .diagram.is-dragging svg { cursor: grabbing; }
  #zoom { transition: transform 250ms ease-out; }
  .diagram.is-dragging #zoom { transition: none; }
  .ring { cursor: pointer; }
  .label { cursor: pointer; font-weight: 600; paint-order: stroke; stroke-linejoin: round; }
  .pill { cursor: pointer; paint-order: stroke; stroke-linejoin: round; }
  .pill.is-active { font-weight: 600; text-decoration: underline; }
  .pill-group { cursor: pointer; }
  /* No browser focus ring on mouse or touch; keyboard users get a ring in the course palette. */
  svg [tabindex]:focus { outline: none; }
  body.kb .ring:focus { stroke: var(--primary); stroke-opacity: 1; stroke-width: 4; stroke-dasharray: 10 6; }
  body.kb .label:focus { fill: var(--primary); }
  body.kb .pill-group:focus rect { fill: var(--primary-soft); stroke: var(--primary); stroke-width: 1.5; }
  body.kb .pill-group:focus .pill { font-weight: 600; text-decoration: underline; }
  .controls { position: absolute; right: 8px; bottom: 8px; display: flex; gap: 4px; }
  .ctl {
    font: inherit; width: 32px; height: 32px; border-radius: 8px; cursor: pointer;
    border: 1px solid var(--border); background: var(--card); color: var(--fg);
    display: inline-flex; align-items: center; justify-content: center; font-size: 18px; line-height: 1;
    box-shadow: 0 1px 2px rgba(0,0,0,0.06);
  }
  .ctl:hover { background: var(--muted); }
  .ctl:disabled { opacity: 0.4; cursor: default; }
  .ctl:focus-visible { outline: 2px solid var(--primary); outline-offset: 2px; }
  .ctl.reset { font-size: 13px; width: auto; padding: 0 10px; }
  .ctl.reset[hidden] { display: none; }
  .hint { color: var(--muted-fg); font-size: 12px; margin: 6px 0 0; }
  .panel {
    border: 1px solid var(--border);
    background: var(--card);
    border-radius: 12px;
    padding: 16px;
  }
  @media (min-width: 1024px) { .panel { position: sticky; top: 8px; } }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted-fg); margin: 0; }
  .panel h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 4px 0 0; }
  .panel p { margin: 8px 0 0; }
  .prompt { color: var(--muted-fg); font-style: italic; margin: 0; }
  .small { color: var(--muted-fg); font-size: 12px; }
  .why { border-top: 1px solid var(--border); margin-top: 12px; padding-top: 8px; }
  .why .eyebrow { display: inline; margin-right: 6px; }
  .regions { margin-top: 14px; }
  .region-list { display: flex; flex-direction: column; gap: 8px; margin-top: 6px; }
  .region-btn, .close-btn {
    font: inherit; color: inherit; text-align: left; cursor: pointer;
    border: 1px solid var(--border); background: transparent; border-radius: 8px;
  }
  .region-btn { padding: 8px 12px; }
  .region-btn:hover, .close-btn:hover { background: var(--muted); }
  .region-btn:focus-visible, .close-btn:focus-visible { outline: 2px solid var(--primary); outline-offset: 2px; }
  .region-btn strong { display: block; font-weight: 500; }
  .region-btn span { display: block; color: var(--muted-fg); font-size: 12px; }
  .close-btn { float: right; border: 0; width: 28px; height: 28px; margin: -4px -4px 0 0; color: var(--muted-fg); font-size: 18px; line-height: 1; }
</style>
</head>
<body>
<div class="layout">
  <div>
    <div class="diagram" id="diagram">
      <div class="stage">
        <svg id="svg" viewBox="0 0 1180 1240" role="group" aria-label="Concentric rings of AI categories with example systems. Tab through the rings and the example systems."></svg>
      </div>
      <div class="controls">
        <button type="button" class="ctl" id="zoom-out" aria-label="Zoom out">&minus;</button>
        <button type="button" class="ctl" id="zoom-in" aria-label="Zoom in">+</button>
        <button type="button" class="ctl reset" id="zoom-reset" hidden>Reset view</button>
      </div>
    </div>
    <p class="hint">Zoom in with the + button, then drag the diagram to move around.</p>
  </div>
  <aside class="panel" id="panel" aria-live="polite"></aside>
</div>

<script>
  var AI_LEVELS = [
    { key: "ai", name: "AI", blurb: "The whole field: any system built to do things we would call intelligent.", examples: [] },
    { key: "narrow", name: "Narrow AI", blurb: "Built for one task or a narrow set of them. Everything that actually exists today lives here.", examples: [
      { name: "Roomba", what: "iRobot's robot vacuum.", why: "Navigates with sensors and fixed rules. It does not learn from data, so it is narrow AI but not machine learning." },
      { name: "Boeing autopilot", what: "Flight-control automation.", why: "Follows engineered control laws for one job; nothing about it is learned from data." },
      { name: "IBM Deep Blue", what: "The chess computer that beat Kasparov in 1997.", why: "Brute-force search plus a hand-crafted evaluation function: formidable, but narrow and not machine learning." },
      { name: "Word spell checker", what: "Dictionary-and-rules spelling correction.", why: "Looks words up against a list and applies rules; narrow and rule-based." }
    ] },
    { key: "ml", name: "Machine Learning", blurb: "Systems that learn patterns from data instead of being programmed rule by rule.", examples: [
      { name: "Amazon spam filter", what: "Amazon's early email spam classification.", why: "Learns spam-vs-not from labelled examples: machine learning, but not a deep neural network." },
      { name: "Chase credit", what: "Chase's automated credit-scoring decisions.", why: "Statistical models fit to historical data; machine learning without deep learning." },
      { name: "JPMorgan fraud", what: "JP Morgan's transaction-fraud flagging.", why: "Learns fraud patterns from past transactions; classical machine learning." }
    ] },
    { key: "dl", name: "Deep Learning", blurb: "Machine learning with many-layered neural networks that learn their own features.", examples: [
      { name: "Apple Photos", what: "On-device photo recognition (image classifiers).", why: "Convolutional neural networks: deep learning, but it labels images rather than generating them." },
      { name: "Azure Speech to Text", what: "Microsoft's speech-recognition service.", why: "Deep neural nets map audio to text; recognition, not generation." },
      { name: "FaceID", what: "Apple's face unlock.", why: "A deep neural net recognises your face: discriminative, not generative." }
    ] },
    { key: "gen", name: "Generative AI", blurb: "Deep-learning systems that create new content: images, audio, video, text.", examples: [
      { name: "Midjourney", what: "Text-to-image generator.", why: "Generates images (diffusion): generative, but not a language model." },
      { name: "Sora", what: "OpenAI's text-to-video model.", why: "Generates video; generative, but not language." },
      { name: "Suno", what: "AI music generator.", why: "Generates audio; generative, non-language." },
      { name: "Adobe Firefly", what: "Adobe's image-generation model.", why: "Generative imagery; not a language model." }
    ] },
    { key: "llm", name: "Large Language Model", blurb: "Generative models that specialise in language.", examples: [
      { name: "Mamba", what: "A state-space-model language model.", why: "A large language model that is NOT a transformer: it uses a state-space architecture instead of attention." },
      { name: "RWKV", what: "An RNN-style language model.", why: "A language model built on a recurrent architecture rather than transformers." }
    ] },
    { key: "transformer", name: "Transformer LLMs", blurb: "Language models built on the transformer (attention) architecture: today's mainstream.", examples: [
      { name: "Claude", what: "Anthropic's assistant.", why: "A transformer-based large language model." },
      { name: "ChatGPT", what: "OpenAI's assistant.", why: "Built on GPT transformers." },
      { name: "Gemini", what: "Google DeepMind's assistant.", why: "Transformer-based." },
      { name: "LLaMA", what: "Meta's open-weight model family.", why: "Transformer architecture." }
    ] }
  ];
  var AI_REGIONS = {
    theoretical: { label: "Theoretical only", body: "This is theoretical only. There are no real non-narrow AI models known today." },
    absurd: { label: "Possible but absurd", body: "Theoretically possible but would require an absurd quantity of resources. Less likely to occur." }
  };
  var PROMPT = "Tap any system to see what it is and why it sits at this ring, not the next one in.";

  // Geometry (same viewBox and ring placement as the original diagram).
  var VBW = 1180, VBH = 1240;
  var AI = { cx: 590, cy: 600, r: 585 };
  var RED_BOTTOM = 1160, RED_R0 = 505, RED_STEP = 73;
  var NAME_FS = 34, EX_FS = 21, PILL_H = 30, EX_GAP = 14, CHAR_W = 0.56, PAD = 14;
  var MIN_Z = 1, MAX_Z = 4, Z_STEP = 0.6;

  function levelCircle(i) {
    if (i === 0) return AI;
    var r = RED_R0 - (i - 1) * RED_STEP;
    return { cx: AI.cx, cy: RED_BOTTOM - r, r: r };
  }
  function redOpacity(i) { return 0.12 + (i - 1) * 0.15; }
  function topEdge(i) { var c = levelCircle(i); return c.cy - c.r; }
  function bandWidth(c, y, pad) {
    var rr = c.r - pad, v = rr * rr - (y - c.cy) * (y - c.cy);
    return v > 0 ? 2 * Math.sqrt(v) : 0;
  }
  function estPill(name) { return name.length * EX_FS * CHAR_W + 8; }

  // Pack example pills into rows that fit the chord width at each row's y.
  function packRows(c, examples, startY) {
    var rows = [], row = [], w = 0, y = startY;
    examples.forEach(function (ex) {
      var iw = estPill(ex.name);
      var maxW = bandWidth(c, y + PILL_H / 2, PAD);
      if (row.length && w + EX_GAP + iw > maxW) {
        rows.push(row); row = []; w = 0; y += PILL_H;
      }
      row.push({ ex: ex, w: iw });
      w += (row.length > 1 ? EX_GAP : 0) + iw;
    });
    if (row.length) rows.push(row);
    return rows;
  }

  var svg = document.getElementById("svg");
  var diagram = document.getElementById("diagram");
  var SVG_NS = "http://www.w3.org/2000/svg";
  function make(tag, attrs, parent) {
    var node = document.createElementNS(SVG_NS, tag);
    for (var k in attrs) node.setAttribute(k, attrs[k]);
    (parent || svg).appendChild(node);
    return node;
  }

  // Keyboard-mode flag: focus rings only after keyboard navigation.
  document.addEventListener("keydown", function (e) { if (e.key === "Tab") document.body.classList.add("kb"); });
  document.addEventListener("pointerdown", function () { document.body.classList.remove("kb"); });

  var dragged = false;
  function activatable(node, label, fn) {
    node.setAttribute("tabindex", "0");
    node.setAttribute("role", "button");
    node.setAttribute("aria-label", label);
    node.addEventListener("click", function (e) { if (dragged) return; fn(e); });
    node.addEventListener("keydown", function (e) {
      if (e.key === "Enter" || e.key === " " || e.key === "Spacebar") { e.preventDefault(); fn(e); }
    });
  }

  var view = { kind: "none" };
  var rings = [], labels = [], pills = [];
  var zoomG;

  function buildDiagram() {
    var defs = make("defs", {});
    var pattern = make("pattern", { id: "hatch", width: 13, height: 13, patternUnits: "userSpaceOnUse", patternTransform: "rotate(45)" }, defs);
    make("line", { x1: 0, y1: 0, x2: 0, y2: 13, stroke: "rgba(90,90,90,0.2)", "stroke-width": 1.4 }, pattern);

    zoomG = make("g", { id: "zoom" });

    var bg = make("rect", { x: -VBW, y: -VBH, width: VBW * 3, height: VBH * 3, fill: "transparent" }, zoomG);
    bg.addEventListener("click", function () { if (!dragged) setView({ kind: "none" }); });

    make("circle", { cx: AI.cx, cy: AI.cy, r: AI.r, fill: "#f3f1ec" }, zoomG);
    make("circle", { cx: AI.cx, cy: AI.cy, r: AI.r, fill: "url(#hatch)" }, zoomG);

    AI_LEVELS.forEach(function (lvl, i) {
      var c = levelCircle(i);
      var ring = make("circle", { cx: c.cx, cy: c.cy, r: c.r, "class": "ring", "vector-effect": "non-scaling-stroke" }, zoomG);
      if (i === 0) {
        ring.setAttribute("fill", "transparent");
      } else {
        ring.setAttribute("fill", "#b87018");
        ring.setAttribute("fill-opacity", redOpacity(i));
      }
      activatable(ring, lvl.name, function (e) { e.stopPropagation(); setView({ kind: "level", i: i }); });
      rings.push(ring);
    });

    AI_LEVELS.forEach(function (lvl, i) {
      var c = levelCircle(i);
      var light = i > 0 && redOpacity(i) >= 0.6;
      var isDisk = i === AI_LEVELS.length - 1;
      var nameY, exTop;
      if (i === 0) {
        nameY = topEdge(0) + 26 + NAME_FS / 2;
      } else if (isDisk) {
        var rowsGuess = packRows(c, lvl.examples, c.cy).length;
        var blockH = NAME_FS * 1.1 + 10 + rowsGuess * PILL_H;
        nameY = c.cy - blockH / 2 + NAME_FS / 2;
        exTop = nameY + NAME_FS / 2 + 10;
      } else {
        nameY = topEdge(i) + 14 + NAME_FS / 2;
        exTop = nameY + NAME_FS / 2 + 10;
      }
      var label = make("text", {
        x: c.cx, y: nameY, "text-anchor": "middle", "dominant-baseline": "middle",
        "font-size": NAME_FS, "class": "label",
        fill: light ? "#fff" : "#1a1a1a", stroke: light ? "rgba(60,35,5,0.35)" : "#fff", "stroke-width": 5
      }, zoomG);
      label.textContent = lvl.name;
      label.addEventListener("click", function (e) { if (dragged) return; e.stopPropagation(); setView({ kind: "level", i: i }); });
      labels.push(label);

      if (!lvl.examples.length) return;
      var rows = packRows(c, lvl.examples, exTop);
      rows.forEach(function (row, ri) {
        var total = row.reduce(function (s, it) { return s + it.w; }, 0) + (row.length - 1) * EX_GAP;
        var x = c.cx - total / 2;
        var y = exTop + ri * PILL_H + PILL_H / 2;
        row.forEach(function (it) {
          var ei = lvl.examples.indexOf(it.ex);
          var g = make("g", { "class": "pill-group" }, zoomG);
          make("rect", { x: x, y: y - PILL_H / 2, width: it.w, height: PILL_H, rx: 6, fill: "transparent", "vector-effect": "non-scaling-stroke" }, g);
          var t = make("text", {
            x: x + it.w / 2, y: y, "text-anchor": "middle", "dominant-baseline": "middle",
            "font-size": EX_FS, "class": "pill",
            fill: light ? "#fff" : "#1a1a1a", stroke: light ? "rgba(60,35,5,0.4)" : "#fff", "stroke-width": 4
          }, g);
          t.textContent = it.ex.name;
          activatable(g, it.ex.name + ", in " + lvl.name, function (e) { e.stopPropagation(); setView({ kind: "example", i: i, ei: ei }); });
          pills.push({ node: t, i: i, ei: ei });
          x += it.w + EX_GAP;
        });
      });
    });
  }

  // Zoom and pan, about the diagram centre, as in the XLab component.
  var t = { z: 1, x: 0, y: 0 };
  var zoomIn = document.getElementById("zoom-in");
  var zoomOut = document.getElementById("zoom-out");
  var zoomReset = document.getElementById("zoom-reset");
  function clamp(v, m) { return Math.max(-m, Math.min(m, v)); }
  function applyTransform() {
    zoomG.setAttribute("transform", "translate(" + t.x + " " + t.y + ") translate(" + VBW / 2 + " " + VBH / 2 + ") scale(" + t.z + ") translate(" + (-VBW / 2) + " " + (-VBH / 2) + ")");
    var changed = t.z !== 1 || t.x !== 0 || t.y !== 0;
    diagram.classList.toggle("is-zoomed", t.z > 1);
    zoomIn.disabled = t.z >= MAX_Z;
    zoomOut.disabled = t.z <= MIN_Z;
    zoomReset.hidden = !changed;
  }
  function zoomBy(delta) {
    var z = Math.max(MIN_Z, Math.min(MAX_Z, Math.round((t.z + delta) * 100) / 100));
    var mx = ((z - 1) * VBW) / 2, my = ((z - 1) * VBH) / 2;
    t = { z: z, x: clamp(t.x, mx), y: clamp(t.y, my) };
    applyTransform();
  }
  function resetZoom() { t = { z: 1, x: 0, y: 0 }; applyTransform(); }
  zoomIn.addEventListener("click", function () { zoomBy(Z_STEP); });
  zoomOut.addEventListener("click", function () { zoomBy(-Z_STEP); });
  zoomReset.addEventListener("click", resetZoom);

  var drag = null;
  svg.addEventListener("pointerdown", function (e) {
    if (t.z <= 1 || e.button !== 0) return;
    drag = { x: e.clientX, y: e.clientY, ox: t.x, oy: t.y };
    dragged = false;
    try { svg.setPointerCapture(e.pointerId); } catch (err) {}
  });
  svg.addEventListener("pointermove", function (e) {
    if (!drag) return;
    var rect = svg.getBoundingClientRect();
    var s = VBW / rect.width;
    var dx = (e.clientX - drag.x) * s, dy = (e.clientY - drag.y) * s;
    if (!dragged && Math.abs(e.clientX - drag.x) + Math.abs(e.clientY - drag.y) > 4) {
      dragged = true;
      diagram.classList.add("is-dragging");
    }
    if (!dragged) return;
    var mx = ((t.z - 1) * VBW) / 2, my = ((t.z - 1) * VBH) / 2;
    t.x = clamp(drag.ox + dx, mx);
    t.y = clamp(drag.oy + dy, my);
    applyTransform();
  });
  function endDrag() {
    if (!drag) return;
    drag = null;
    diagram.classList.remove("is-dragging");
    // Let the click that ends a drag pass through as a no-op, then re-arm.
    setTimeout(function () { dragged = false; }, 0);
  }
  svg.addEventListener("pointerup", endDrag);
  svg.addEventListener("pointercancel", endDrag);
  svg.addEventListener("lostpointercapture", endDrag);
  svg.addEventListener("keydown", function (e) {
    if (t.z <= 1) return;
    var step = 60 / t.z, moved = true;
    if (e.key === "ArrowLeft") t.x += step;
    else if (e.key === "ArrowRight") t.x -= step;
    else if (e.key === "ArrowUp") t.y += step;
    else if (e.key === "ArrowDown") t.y -= step;
    else moved = false;
    if (!moved) return;
    e.preventDefault();
    var mx = ((t.z - 1) * VBW) / 2, my = ((t.z - 1) * VBH) / 2;
    t.x = clamp(t.x, mx); t.y = clamp(t.y, my);
    applyTransform();
  });

  function paint() {
    var selLevel = view.kind === "level" || view.kind === "example" ? view.i : null;
    rings.forEach(function (ring, i) {
      var selected = selLevel === i;
      if (i === 0) {
        ring.setAttribute("stroke", selected ? "#1a1a1a" : "rgba(90,90,90,0.4)");
        ring.setAttribute("stroke-width", selected ? 3 : 1.5);
      } else {
        ring.setAttribute("stroke", selected ? "#1a1a1a" : "#fff");
        ring.setAttribute("stroke-opacity", selected ? 1 : 0.4);
        ring.setAttribute("stroke-width", selected ? 3 : 1.25);
      }
    });
    pills.forEach(function (p) {
      var active = view.kind === "example" && view.i === p.i && view.ei === p.ei;
      p.node.classList.toggle("is-active", active);
    });
  }

  var panel = document.getElementById("panel");
  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }
  function closeButton(label, next) {
    var b = el("button", "close-btn", "×");
    b.type = "button";
    b.setAttribute("aria-label", label);
    b.addEventListener("click", function () { setView(next); });
    return b;
  }

  function renderPanel() {
    panel.textContent = "";
    if (view.kind === "none") {
      panel.appendChild(el("p", "prompt", PROMPT));
      var regions = el("div", "regions");
      regions.appendChild(el("p", "eyebrow", "The grey margin"));
      var list = el("div", "region-list");
      ["theoretical", "absurd"].forEach(function (r) {
        var b = el("button", "region-btn");
        b.type = "button";
        b.appendChild(el("strong", null, AI_REGIONS[r].label));
        b.appendChild(el("span", null, "AI that is not narrow, out in the grey margin. Tap to read."));
        b.addEventListener("click", function () { setView({ kind: "region", r: r }); });
        list.appendChild(b);
      });
      regions.appendChild(list);
      panel.appendChild(regions);
      return;
    }
    if (view.kind === "region") {
      panel.appendChild(closeButton("Close", { kind: "none" }));
      panel.appendChild(el("p", "eyebrow", "Beyond real AI"));
      panel.appendChild(el("h2", null, AI_REGIONS[view.r].label));
      panel.appendChild(el("p", null, AI_REGIONS[view.r].body));
      return;
    }
    var lvl = AI_LEVELS[view.i];
    if (view.kind === "level") {
      panel.appendChild(closeButton("Close", { kind: "none" }));
      panel.appendChild(el("p", "eyebrow", "Level"));
      panel.appendChild(el("h2", null, lvl.name));
      panel.appendChild(el("p", null, lvl.blurb));
      if (lvl.examples.length) panel.appendChild(el("p", "small", "Tap a system in this ring to see why it sits here, not one ring deeper."));
      return;
    }
    var ex = lvl.examples[view.ei];
    panel.appendChild(closeButton("Back to level", { kind: "level", i: view.i }));
    panel.appendChild(el("p", "eyebrow", lvl.name));
    panel.appendChild(el("h2", null, ex.name));
    panel.appendChild(el("p", null, ex.what));
    var why = el("p", "why");
    why.appendChild(el("span", "eyebrow", "Why here"));
    why.appendChild(document.createTextNode(ex.why));
    panel.appendChild(why);
  }

  var stacked = window.matchMedia ? window.matchMedia("(max-width: 1023px)") : null;
  function setView(next) {
    var wasNone = view.kind === "none";
    view = next;
    paint();
    renderPanel();
    // When the panel sits below the diagram, bring it on screen after a selection.
    if (next.kind !== "none" && wasNone && stacked && stacked.matches && panel.scrollIntoView) {
      try { panel.scrollIntoView({ behavior: "smooth", block: "nearest" }); } catch (err) {}
    }
  }

  buildDiagram();
  applyTransform();
  setView({ kind: "none" });
</script>
</body>
</html>
