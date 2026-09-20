---
id: 'c8aac95d-caaa-4b4b-ae68-f3391ab1b333'
title: "Locating a chip from landmark delays"
summary_for_tutor: "Interactive version of Figure 7 in O'Gara et al., placed in the hardware accounting lens between the article excerpt that opens section 2.4 on location verification and the excerpt with that section's open research questions. Landmark servers time a challenge and response; because routing and congestion can only inflate a delay, each measured delay is an upper bound on the chip's distance, so every landmark contributes a band of consistent distances and the widget shades the locations consistent with all of them at once. The learner drags landmarks and the chip, sets how many landmarks report (1 to 6) and how noisy the delays are (5 to 50 per cent), selects a landmark to read its delay and distance band, and reads a line giving the number of patches in the feasible region, its share of the map and its bounding box. Few landmarks or high noise leave a large or multi-patch region, which is the point. All units are schematic: the paper gives no conversion from delay to distance. Completion fires once the learner has changed both the landmark count and the noise. The page carries the lesson text on identity, location, topology and completeness, the article excerpt on location verification and its open research questions, so do not repeat those unless asked."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
[hidden] { display: none !important; }
body { margin: 0; padding: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.card { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
.body { padding: 16px; }
.hint { margin: 0 0 12px; font-size: 12px; color: var(--muted); }
.map { position: relative; width: 100%; max-width: 720px; margin: 0 auto; aspect-ratio: 100 / 64; background: var(--page); border: 1px solid var(--border); border-radius: 8px; overflow: hidden; touch-action: none; }
.map canvas { display: block; width: 100%; height: 100%; position: absolute; inset: 0; }
.mk { position: absolute; width: 22px; height: 22px; margin: -11px 0 0 -11px; padding: 0; border-radius: 999px; border: 1px solid var(--border); background: var(--bg); cursor: grab; touch-action: none; display: flex; align-items: center; justify-content: center; font: inherit; color: inherit; }
.mk:active { cursor: grabbing; }
.mk .dot { width: 10px; height: 10px; border-radius: 999px; background: #1a1a1a; }
.mk.sel { border-color: var(--accent); border-width: 2px; }
.mk.sel .dot { background: var(--accent); }
.mk.chip { border-color: transparent; background: transparent; }
.mk.chip .x { font-size: 15px; font-weight: 600; line-height: 1; color: var(--accent); text-shadow: 0 0 3px #ffffff, 0 0 3px #ffffff; }
body.kb .mk:focus { outline: 2px solid var(--accent); outline-offset: 2px; }
.mk:focus { outline: none; }
.readout { margin: 14px 0 0; font-size: 13px; font-variant-numeric: tabular-nums; }
.detail { margin: 6px 0 0; font-size: 12px; color: var(--muted); min-height: 32px; }
.legend { display: flex; flex-wrap: wrap; gap: 4px 16px; margin: 12px 0 0; font-size: 11px; color: var(--muted); }
.legend span { display: flex; align-items: center; gap: 6px; }
.sw { width: 14px; height: 10px; border-radius: 2px; display: inline-block; }
.sw.reg { background: rgba(184, 112, 24, 0.32); border: 1px solid var(--accent); }
.sw.band { border-top: 1px solid #5a5a5a; border-bottom: 1px dashed #5a5a5a; height: 8px; }
.sw.lmk { width: 10px; height: 10px; border-radius: 999px; background: #1a1a1a; }
.levers { display: grid; grid-template-columns: 1fr; gap: 12px; margin: 16px 0 0; }
.lever label { display: flex; align-items: baseline; justify-content: space-between; gap: 10px; font-size: 13px; }
.lever .name { color: var(--muted); }
.lever .val { font-weight: 500; font-variant-numeric: tabular-nums; }
input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0 0; }
.foot { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin: 14px 0 0; flex-wrap: wrap; }
button.act { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 6px 10px; cursor: pointer; font-size: 12px; }
button.act:hover { background: var(--page); }
@media (min-width: 560px) { .levers { grid-template-columns: 1fr 1fr; gap: 12px 20px; } }
</style>
</head>
<body>
<!-- Built from ogara-hardware-enabled-mechanisms-for-verifying-responsible-ai-development.md, Figure 7 and section 2.4.2 Technical details (lines 293 to 303). Distances and delays are schematic units: the paper gives no calibration constants. -->
<div class="card">
  <div class="body">
    <p class="hint">Drag a landmark or the chip, and set how many landmarks report and how noisy their delays are.</p>
    <div class="map" id="map">
      <canvas id="cv"></canvas>
    </div>
    <p class="readout" id="readout"></p>
    <p class="detail" id="detail"></p>
    <div class="legend">
      <span><i class="sw lmk"></i>Landmark server</span>
      <span><i class="sw band"></i>Distances consistent with its delay</span>
      <span><i class="sw reg"></i>Locations consistent with every landmark</span>
    </div>
    <div class="levers">
      <div class="lever">
        <label for="cnt"><span class="name">Landmarks reporting</span><span class="val" id="vcnt">3</span></label>
        <input type="range" id="cnt" min="1" max="6" step="1" value="3">
      </div>
      <div class="lever">
        <label for="noi"><span class="name">Delay noise from routing and congestion</span><span class="val" id="vnoi">20%</span></label>
        <input type="range" id="noi" min="5" max="50" step="5" value="20">
      </div>
    </div>
    <div class="foot">
      <button type="button" class="act" id="reset">Reset</button>
    </div>
  </div>
</div>
<script>
(function () {
  "use strict";
  var MAP_W = 100, MAP_H = 64;
  var HOME = [{ x: 12, y: 12 }, { x: 88, y: 14 }, { x: 50, y: 58 }, { x: 16, y: 48 }, { x: 84, y: 52 }, { x: 50, y: 6 }];
  var INFL = [0.85, 0.25, 0.6, 0.05, 0.95, 0.4];
  var DEF_N = 3, DEF_NOISE = 20;
  var HOME_CHIP = { x: 54, y: 30 };

  var pts = HOME.map(function (p) { return { x: p.x, y: p.y }; });
  var chip = { x: HOME_CHIP.x, y: HOME_CHIP.y };
  var sel = -1, movedCount = false, movedNoise = false, completed = false;

  var mapEl = document.getElementById("map");
  var cv = document.getElementById("cv");
  var support = !!(window.CanvasRenderingContext2D && cv.getContext);
  var ctx = support ? cv.getContext("2d") : null;
  var readout = document.getElementById("readout");
  var detail = document.getElementById("detail");
  var cnt = document.getElementById("cnt");
  var noi = document.getElementById("noi");
  var vcnt = document.getElementById("vcnt");
  var vnoi = document.getElementById("vnoi");
  var off = document.createElement("canvas");
  var offCtx = support ? off.getContext("2d") : null;
  var canDraw = !!(ctx && offCtx && offCtx.createImageData);
  var marks = [];
  var lastPointer = 0;

  document.addEventListener("keydown", function (e) { if (e.key === "Tab") document.body.classList.add("kb"); });
  document.addEventListener("pointerdown", function () { document.body.classList.remove("kb"); });

  function activeCount() { return Number(cnt.value); }
  function noiseFrac() { return Number(noi.value) / 100; }

  function radii() {
    var n = activeCount(), f = noiseFrac(), out = [];
    for (var i = 0; i < n; i++) {
      var dx = pts[i].x - chip.x, dy = pts[i].y - chip.y;
      var d = Math.sqrt(dx * dx + dy * dy);
      var t = d * (1 + INFL[i] * f);
      out.push({ x: pts[i].x, y: pts[i].y, t: t, rout: t, rin: t / (1 + f) });
    }
    return out;
  }

  function buildMarks() {
    marks.forEach(function (m) { m.el.remove(); });
    marks = [];
    for (var i = 0; i < HOME.length; i++) addMark(i);
    addMark(-1);
  }

  function addMark(i) {
    var b = document.createElement("button");
    b.type = "button";
    b.className = "mk" + (i < 0 ? " chip" : "");
    var inner = document.createElement("span");
    if (i < 0) { inner.className = "x"; inner.textContent = "X"; }
    else { inner.className = "dot"; }
    b.appendChild(inner);
    b.setAttribute("aria-label", i < 0 ? "AI chip, true location" : "Landmark " + (i + 1));
    b.title = b.getAttribute("aria-label");
    mapEl.appendChild(b);
    var rec = { el: b, idx: i };
    marks.push(rec);
    var moved = false, startX = 0, startY = 0;
    b.addEventListener("pointerdown", function (e) {
      moved = false; startX = e.clientX; startY = e.clientY;
      b.setPointerCapture(e.pointerId);
      e.preventDefault();
    });
    b.addEventListener("pointermove", function (e) {
      if (!b.hasPointerCapture || !b.hasPointerCapture(e.pointerId)) return;
      if (Math.abs(e.clientX - startX) + Math.abs(e.clientY - startY) > 3) moved = true;
      if (!moved) return;
      var r = mapEl.getBoundingClientRect();
      if (!r.width) return;
      var ux = clamp((e.clientX - r.left) / r.width * MAP_W, 1, MAP_W - 1);
      var uy = clamp((e.clientY - r.top) / r.height * MAP_H, 1, MAP_H - 1);
      setPos(i, ux, uy);
      render(true);
    });
    b.addEventListener("pointerup", function (e) {
      if (b.hasPointerCapture && b.hasPointerCapture(e.pointerId)) b.releasePointerCapture(e.pointerId);
      lastPointer = Date.now();
      if (!moved) { sel = (sel === i ? -2 : i); render(true); }
    });
    b.addEventListener("click", function () {
      if (Date.now() - lastPointer < 700) return;
      sel = (sel === i ? -2 : i);
      render(true);
    });
    b.addEventListener("keydown", function (e) {
      var step = e.shiftKey ? 8 : 2, dx = 0, dy = 0;
      if (e.key === "ArrowLeft") dx = -step;
      else if (e.key === "ArrowRight") dx = step;
      else if (e.key === "ArrowUp") dy = -step;
      else if (e.key === "ArrowDown") dy = step;
      else if (e.key === "Enter" || e.key === " ") { sel = (sel === i ? -2 : i); render(true); e.preventDefault(); return; }
      else return;
      e.preventDefault();
      var p = i < 0 ? chip : pts[i];
      setPos(i, clamp(p.x + dx, 1, MAP_W - 1), clamp(p.y + dy, 1, MAP_H - 1));
      render(true);
    });
  }

  function setPos(i, x, y) {
    if (i < 0) { chip.x = x; chip.y = y; } else { pts[i].x = x; pts[i].y = y; }
  }

  function clamp(v, lo, hi) { return v < lo ? lo : (v > hi ? hi : v); }

  function placeMarks() {
    var n = activeCount();
    marks.forEach(function (m) {
      var i = m.idx;
      var p = i < 0 ? chip : pts[i];
      var on = i < 0 || i < n;
      m.el.hidden = !on;
      m.el.style.left = (p.x / MAP_W * 100) + "%";
      m.el.style.top = (p.y / MAP_H * 100) + "%";
      m.el.classList.toggle("sel", i >= 0 && i === sel);
    });
  }

  function render(save) {
    vcnt.textContent = String(activeCount());
    vnoi.textContent = Number(noi.value) + "%";
    if (sel >= activeCount()) sel = -2;

    var cw = Math.max(80, Math.round(mapEl.clientWidth || 0));
    var ch = Math.round(cw * MAP_H / MAP_W);
    var dpr = Math.min(window.devicePixelRatio || 1, 2);
    if (canDraw) {
      cv.width = Math.round(cw * dpr); cv.height = Math.round(ch * dpr);
      off.width = cw; off.height = ch;
    }

    var L = radii();
    var s = MAP_W / cw;
    var rin2 = [], rout2 = [], lx = [], ly = [];
    for (var k = 0; k < L.length; k++) { rin2.push(L[k].rin * L[k].rin); rout2.push(L[k].rout * L[k].rout); lx.push(L[k].x); ly.push(L[k].y); }

    var img = canDraw ? offCtx.createImageData(cw, ch) : null;
    var data = img ? img.data : null;
    var gw = Math.ceil(cw / 4), gh = Math.ceil(ch / 4);
    var grid = new Uint8Array(gw * gh);
    var count = 0, minx = 1e9, maxx = -1e9, miny = 1e9, maxy = -1e9;
    for (var y = 0; y < ch; y++) {
      var uy = (y + 0.5) * s;
      var row = y * cw;
      for (var x = 0; x < cw; x++) {
        var ux = (x + 0.5) * s;
        var ok = L.length > 0;
        for (var j = 0; j < L.length; j++) {
          var ddx = ux - lx[j], ddy = uy - ly[j];
          var d2 = ddx * ddx + ddy * ddy;
          if (d2 < rin2[j] || d2 > rout2[j]) { ok = false; break; }
        }
        if (ok) {
          if (data) {
            var o = (row + x) * 4;
            data[o] = 184; data[o + 1] = 112; data[o + 2] = 24; data[o + 3] = 82;
          }
          grid[((y >> 2) * gw) + (x >> 2)] = 1;
          count += 1;
          if (ux < minx) minx = ux;
          if (ux > maxx) maxx = ux;
          if (uy < miny) miny = uy;
          if (uy > maxy) maxy = uy;
        }
      }
    }
    if (canDraw) {
    offCtx.putImageData(img, 0, 0);

    ctx.setTransform(1, 0, 0, 1, 0, 0);
    ctx.clearRect(0, 0, cv.width, cv.height);
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    drawGrid(ctx, cw, ch);
    ctx.imageSmoothingEnabled = false;
    ctx.drawImage(off, 0, 0, cw, ch);
    ctx.imageSmoothingEnabled = true;
    var px = cw / MAP_W;
    for (var m = 0; m < L.length; m++) {
      var isSel = (m === sel);
      ctx.strokeStyle = isSel ? "#b87018" : "#5a5a5a";
      ctx.lineWidth = isSel ? 1.6 : 1;
      ctx.globalAlpha = isSel ? 0.9 : 0.5;
      ring(ctx, L[m].x * px, L[m].y * px, L[m].rout * px, []);
      ring(ctx, L[m].x * px, L[m].y * px, L[m].rin * px, [4, 4]);
      ctx.globalAlpha = 1;
    }
    }

    placeMarks();
    stats(count, cw * ch, minx, maxx, miny, maxy, grid, gw, gh);
    detailLine(L);

    if (save) scheduleSave(L);
  }

  function ring(c, cx, cy, r, dash) {
    c.save();
    c.setLineDash(dash);
    c.beginPath();
    c.arc(cx, cy, Math.max(r, 0.5), 0, Math.PI * 2);
    c.stroke();
    c.restore();
  }

  function drawGrid(c, cw, ch) {
    c.strokeStyle = "#e8e5df";
    c.lineWidth = 1;
    c.beginPath();
    for (var gx = 10; gx < MAP_W; gx += 10) { var X = Math.round(gx / MAP_W * cw) + 0.5; c.moveTo(X, 0); c.lineTo(X, ch); }
    for (var gy = 10; gy < MAP_H; gy += 10) { var Y = Math.round(gy / MAP_H * ch) + 0.5; c.moveTo(0, Y); c.lineTo(cw, Y); }
    c.stroke();
  }

  function components(grid, gw, gh) {
    var seen = new Uint8Array(gw * gh), n = 0, stack = [];
    for (var i = 0; i < grid.length; i++) {
      if (!grid[i] || seen[i]) continue;
      n += 1; seen[i] = 1; stack.length = 0; stack.push(i);
      while (stack.length) {
        var c = stack.pop(), cx = c % gw, cy = (c - cx) / gw;
        for (var dy = -1; dy <= 1; dy++) {
          for (var dx = -1; dx <= 1; dx++) {
            var nx = cx + dx, ny = cy + dy;
            if (nx < 0 || ny < 0 || nx >= gw || ny >= gh) continue;
            var ni = ny * gw + nx;
            if (grid[ni] && !seen[ni]) { seen[ni] = 1; stack.push(ni); }
          }
        }
      }
    }
    return n;
  }

  var lastStats = null;
  function stats(count, total, minx, maxx, miny, maxy, grid, gw, gh) {
    if (!count) {
      readout.textContent = "No location on this map fits every landmark at once.";
      lastStats = { area: 0, patches: 0, w: 0, h: 0 };
      return;
    }
    var pct = count / total * 100;
    var w = Math.max(1, Math.round(maxx - minx)), h = Math.max(1, Math.round(maxy - miny));
    var patches = components(grid, gw, gh);
    var pctTxt = pct < 0.1 ? pct.toFixed(2) : pct.toFixed(1);
    readout.textContent = "Consistent locations: " + (patches === 1 ? "one patch" : patches + " separate patches")
      + ", " + pctTxt + "% of the map, spread over a box " + w + " by " + h + " units.";
    lastStats = { area: Number(pctTxt), patches: patches, w: w, h: h };
  }

  function detailLine(L) {
    if (sel < 0 || sel >= L.length) {
      detail.textContent = "Select a landmark to read its delay measurement.";
      return;
    }
    var d = L[sel];
    detail.textContent = "Landmark " + (sel + 1) + ": delay " + d.t.toFixed(1) + " units, so the chip lies between "
      + d.rin.toFixed(1) + " and " + d.rout.toFixed(1) + " units away. Routing and congestion can only inflate a delay, so the measurement bounds the distance from above.";
  }

  var saveTimer = null, pending = null;
  function scheduleSave(L) {
    pending = L;
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(flush, 400);
  }
  function flush() {
    if (saveTimer) { clearTimeout(saveTimer); saveTimer = null; }
    if (!pending) return;
    pending = null;
    var st = {
      n: activeCount(), noise: Number(noi.value), chip: { x: chip.x, y: chip.y },
      pts: pts.map(function (p) { return { x: Math.round(p.x * 10) / 10, y: Math.round(p.y * 10) / 10 }; }),
      movedCount: movedCount, movedNoise: movedNoise
    };
    var s = lastStats || { area: 0, patches: 0, w: 0, h: 0 };
    var summary = "Chip locator. " + activeCount() + " landmark server" + (activeCount() === 1 ? "" : "s")
      + " reporting, delay noise " + noi.value + "%. Feasible region: " + s.patches + " patch"
      + (s.patches === 1 ? "" : "es") + " covering " + s.area + "% of the map, inside a box " + s.w + " by " + s.h
      + " schematic units. Landmark count changed: " + (movedCount ? "yes" : "no") + ". Noise changed: " + (movedNoise ? "yes" : "no") + ".";
    if (window.Lens && window.Lens.saveState) window.Lens.saveState(st, summary);
    else { try { window.localStorage.setItem("ogara-chip-locator", JSON.stringify(st)); } catch (e) { void e; } }
    if ((movedCount || movedNoise) && !completed) {
      completed = true;
      if (window.Lens && window.Lens.complete) window.Lens.complete();
    }
  }

  function restore(st) {
    if (!st || typeof st !== "object") return;
    if (typeof st.n === "number") cnt.value = String(clamp(Math.round(st.n), 1, 6));
    if (typeof st.noise === "number") noi.value = String(clamp(Math.round(st.noise / 5) * 5, 5, 50));
    if (st.chip && typeof st.chip.x === "number") { chip.x = clamp(st.chip.x, 1, MAP_W - 1); chip.y = clamp(st.chip.y, 1, MAP_H - 1); }
    if (Object.prototype.toString.call(st.pts) === "[object Array]") {
      for (var i = 0; i < pts.length && i < st.pts.length; i++) {
        var p = st.pts[i];
        if (p && typeof p.x === "number" && typeof p.y === "number") {
          pts[i].x = clamp(p.x, 1, MAP_W - 1); pts[i].y = clamp(p.y, 1, MAP_H - 1);
        }
      }
    }
    if (st.movedCount) movedCount = true;
    if (st.movedNoise) movedNoise = true;
  }

  cnt.addEventListener("input", function () { movedCount = movedCount || Number(cnt.value) !== DEF_N; render(true); });
  noi.addEventListener("input", function () { movedNoise = movedNoise || Number(noi.value) !== DEF_NOISE; render(true); });
  document.getElementById("reset").addEventListener("click", function () {
    pts = HOME.map(function (p) { return { x: p.x, y: p.y }; });
    chip.x = HOME_CHIP.x; chip.y = HOME_CHIP.y;
    cnt.value = String(DEF_N); noi.value = String(DEF_NOISE); sel = -2;
    render(true);
  });
  document.addEventListener("visibilitychange", function () { if (document.visibilityState === "hidden") flush(); });
  if (window.ResizeObserver) {
    var lastW = -1;
    var ro = new ResizeObserver(function () {
      var w = Math.round(mapEl.clientWidth || 0);
      if (w === lastW) return;
      lastW = w;
      render(false);
    });
    ro.observe(mapEl);
  } else {
    window.addEventListener("resize", function () { render(false); });
  }

  buildMarks();
  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state, meta) {
      restore(state);
      if (meta && meta.completed) completed = true;
      render(false);
    });
  } else {
    try {
      var raw = window.localStorage.getItem("ogara-chip-locator");
      if (raw) restore(JSON.parse(raw));
    } catch (e2) { void e2; }
  }
  render(false);
})();
</script>
</body>
</html>
