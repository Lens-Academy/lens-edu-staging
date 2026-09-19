---
id: '378c8a0c-7e2c-4265-a622-29da3f79a89d'
title: "Forge a chip license"
summary_for_tutor: "Interactive version of Figure 8 in O'Gara et al., placed in the authorization lens between the article excerpt that opens section 2.5 on offline licensing and the excerpt with that section's open research questions. The license card carries the figure's own values (License ID 3, Device ID 00001347890, Usage Allowance 1000000000000000, signature 4F2E7ADFB21233D9) and every field is editable; the learner can also re-sign the license with the operator's own key. A chip panel shows the unmodifiable Device ID, the most recently used License ID (2) and the license provider public key in tamper resistant memory. Presenting the license runs the three defenses from section 2.5.3 in the paper's order, marks the fields that fail, and gives the paper's own sentence for that defense when the learner selects a marked field. The lesson is that License ID and Device ID have their own defenses while the Usage Allowance is protected only by the signature, and that any edit after signing breaks the signature. Signing is simulated. Completion fires once all four fields have been altered at least once. The page carries the lesson text on authorization chains and control authority, the article excerpt on offline licensing and its open research questions, plus the build the authorization chain question, so do not repeat those unless asked."
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
.card { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); }
.body { padding: 16px; }
.hint { margin: 0 0 14px; font-size: 12px; color: var(--muted); }
.cols { display: grid; grid-template-columns: 1fr; gap: 14px; }
.panel { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; min-width: 0; }
.panel > h3 { margin: 0; padding: 8px 12px; font-family: var(--font-heading); font-size: 13px; font-weight: 600; border-bottom: 1px solid var(--border); background: var(--page); }
.rows { padding: 4px 0; }
.row { display: flex; align-items: center; gap: 8px; padding: 6px 12px; border-bottom: 1px solid var(--border); }
.row:last-child { border-bottom: 0; }
.row .k { font-size: 12px; color: var(--muted); flex: 1 1 42%; min-width: 0; }
.row .v { flex: 1 1 58%; min-width: 0; font-variant-numeric: tabular-nums; }
.row input { width: 100%; font: inherit; font-size: 13px; font-variant-numeric: tabular-nums; color: inherit; background: var(--bg); border: 1px solid var(--border); border-radius: 6px; padding: 4px 7px; }
.row input:focus { outline: 2px solid var(--accent); outline-offset: 1px; }
.row.bad { background: rgba(184, 112, 24, 0.08); }
.row.bad input { border-color: var(--accent); }
.flag { border: 0; background: none; padding: 0 2px; margin: 0; font: inherit; font-size: 12px; color: var(--accent); cursor: pointer; white-space: nowrap; }
.flag[hidden] { display: none !important; }
.fixed { font-size: 13px; font-variant-numeric: tabular-nums; }
.note { font-size: 11px; color: var(--muted); padding: 8px 12px 10px; margin: 0; }
.acts { display: flex; flex-wrap: wrap; gap: 8px; margin: 14px 0 0; }
button.act { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 7px 11px; cursor: pointer; font-size: 13px; }
button.act:hover { background: var(--page); }
button.act.go { border-color: var(--accent); color: var(--accent); font-weight: 500; }
.verdict { margin: 14px 0 0; font-size: 13px; font-weight: 500; }
.verdict.ok { color: var(--accent); }
.detail { margin: 8px 0 0; border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; font-size: 12px; color: var(--muted); background: var(--page); }
.detail .q { color: var(--text); }
.detail .src { display: block; margin-top: 6px; font-size: 11px; }
body.kb button:focus, body.kb input:focus { outline: 2px solid var(--accent); outline-offset: 2px; }
@media (min-width: 620px) { .cols { grid-template-columns: 1.15fr 1fr; gap: 16px; } }
</style>
</head>
<body>
<!-- Built from ogara-hardware-enabled-mechanisms-for-verifying-responsible-ai-development.md, Figure 8 Example License and section 2.5.3 Attacks (lines 384 to 403). Field values are the figure's; the three rejection reasons are the paper's own sentences. Signing is simulated. -->
<div class="card">
  <div class="body">
    <p class="hint">Change any field of the license, then present it to the chip.</p>
    <div class="cols">
      <div class="panel">
        <h3>License</h3>
        <div class="rows">
          <div class="row" id="row-lid">
            <label class="k" for="f-lid">License ID</label>
            <span class="v"><input id="f-lid" type="text" inputmode="numeric" autocomplete="off" spellcheck="false"></span>
            <button type="button" class="flag" id="flag-lid" hidden>why</button>
          </div>
          <div class="row" id="row-did">
            <label class="k" for="f-did">Device ID</label>
            <span class="v"><input id="f-did" type="text" inputmode="numeric" autocomplete="off" spellcheck="false"></span>
            <button type="button" class="flag" id="flag-did" hidden>why</button>
          </div>
          <div class="row" id="row-use">
            <label class="k" for="f-use">Usage Allowance</label>
            <span class="v"><input id="f-use" type="text" inputmode="numeric" autocomplete="off" spellcheck="false"></span>
            <button type="button" class="flag" id="flag-use" hidden>why</button>
          </div>
          <div class="row" id="row-sig">
            <label class="k" for="f-sig">Signature of Data</label>
            <span class="v"><input id="f-sig" type="text" autocomplete="off" spellcheck="false"></span>
            <button type="button" class="flag" id="flag-sig" hidden>why</button>
          </div>
        </div>
        <p class="note" id="signer"></p>
      </div>
      <div class="panel">
        <h3>Chip</h3>
        <div class="rows">
          <div class="row"><span class="k">Device ID in unmodifiable memory</span><span class="v fixed">00001347890</span></div>
          <div class="row"><span class="k">Most recently used License ID</span><span class="v fixed">2</span></div>
          <div class="row"><span class="k">Key in tamper resistant memory</span><span class="v fixed">License provider public key</span></div>
        </div>
        <p class="note">The chip checks the signature, then the License ID, then the Device ID.</p>
      </div>
    </div>
    <div class="acts">
      <button type="button" class="act go" id="present">Present license to the chip</button>
      <button type="button" class="act" id="selfsign">Sign it with your own key</button>
      <button type="button" class="act" id="restore">Restore the issued license</button>
    </div>
    <p class="verdict" id="verdict"></p>
    <div class="detail" id="detail" hidden></div>
  </div>
</div>
<script>
(function () {
  "use strict";
  var ISSUED = { lid: "3", did: "00001347890", use: "1000000000000000", sig: "4F2E7ADFB21233D9" };
  var CHIP = { did: "00001347890", lastLid: 2 };
  var REASON = {
    sig: "First, to prevent chip operators from creating their own counterfeit licenses, the license provider could sign each license with their private key, and chips could be built to store the license provider’s public key in secure, tamper-resistant memory, allowing the chip to verify that the license’s signature is authentic.",
    lid: "Second, to prevent the same license from being used multiple times on a single chip, the license could include a license ID that starts at zero for the first license issued to a particular chip operator and increments up with each new license. The chip could be designed to reject any license ID lower than the chip’s most recently used license ID number, thus preventing old licenses from being reused.",
    did: "Third, to prevent the same license from being used for multiple chips, chips could be built with an unmodifiable Device ID, and licenses could specify the Device ID of the chip they’re intended to license."
  };
  var SRC = "O’Gara et al., section 2.5.3 Attacks.";

  var F = {
    lid: document.getElementById("f-lid"),
    did: document.getElementById("f-did"),
    use: document.getElementById("f-use"),
    sig: document.getElementById("f-sig")
  };
  var ROW = {
    lid: document.getElementById("row-lid"),
    did: document.getElementById("row-did"),
    use: document.getElementById("row-use"),
    sig: document.getElementById("row-sig")
  };
  var FLAG = {
    lid: document.getElementById("flag-lid"),
    did: document.getElementById("flag-did"),
    use: document.getElementById("flag-use"),
    sig: document.getElementById("flag-sig")
  };
  var KEYS = ["lid", "did", "use", "sig"];
  var verdictEl = document.getElementById("verdict");
  var detailEl = document.getElementById("detail");
  var signerEl = document.getElementById("signer");

  var signer = "provider";
  var tampered = { lid: false, did: false, use: false, sig: false };
  var checked = null;
  var openKey = null;
  var completed = false;

  function digest(s) {
    var h1 = 0x811c9dc5, h2 = 0x01000193;
    for (var i = 0; i < s.length; i++) {
      h1 = (h1 ^ s.charCodeAt(i)) >>> 0;
      h1 = (h1 * 16777619) >>> 0;
      h2 = (h2 + s.charCodeAt(i) * (i + 7)) >>> 0;
      h2 = (h2 ^ (h2 << 5)) >>> 0;
    }
    var hex = ("00000000" + h1.toString(16)).slice(-8) + ("00000000" + h2.toString(16)).slice(-8);
    return hex.toUpperCase();
  }

  function values() {
    return { lid: F.lid.value.trim(), did: F.did.value.trim(), use: F.use.value.trim(), sig: F.sig.value.trim() };
  }

  function evaluate() {
    var v = values();
    var dataMatches = (v.lid === ISSUED.lid && v.did === ISSUED.did && v.use === ISSUED.use);
    var sigMatches = (v.sig === ISSUED.sig);
    var res = { fail: {}, why: {}, count: 0 };

    if (signer !== "provider") {
      res.fail.sig = "sig";
      res.why.sig = "This signature was made with the operator’s own key, so it does not verify against the license provider’s public key held in the chip.";
    } else if (!sigMatches) {
      res.fail.sig = "sig";
      res.why.sig = "The signature is not the one the license provider issued, so it does not verify against the provider’s public key held in the chip.";
    } else if (!dataMatches) {
      res.fail.sig = "sig";
      res.why.sig = "The data no longer matches the data the license provider signed, so the signature does not verify.";
      KEYS.forEach(function (k) {
        if (k !== "sig" && v[k] !== ISSUED[k]) {
          res.fail[k] = "sig";
          res.why[k] = "This field was changed after signing, so the signature over the data no longer verifies.";
        }
      });
    }

    var lidNum = /^[0-9]+$/.test(v.lid) ? parseInt(v.lid, 10) : null;
    if (lidNum === null) {
      res.fail.lid = "lid";
      res.why.lid = "The chip compares License IDs as numbers, and this one is not a number.";
    } else if (lidNum < CHIP.lastLid) {
      res.fail.lid = "lid";
      res.why.lid = "License ID " + lidNum + " is lower than the chip’s most recently used License ID, " + CHIP.lastLid + ", so the chip treats it as an old license being reused.";
    }

    if (v.did !== CHIP.did) {
      res.fail.did = "did";
      res.why.did = "The license names Device ID " + (v.did || "(empty)") + ", but this chip’s unmodifiable Device ID is " + CHIP.did + ".";
    }

    var defs = {};
    KEYS.forEach(function (k) { if (res.fail[k]) defs[res.fail[k]] = true; });
    res.count = Object.keys(defs).length;
    res.defs = defs;
    return res;
  }

  function paint() {
    KEYS.forEach(function (k) {
      var bad = !!(checked && checked.fail[k]);
      ROW[k].classList.toggle("bad", bad);
      FLAG[k].hidden = !bad;
      FLAG[k].setAttribute("aria-label", "Why the chip rejected the " + labelOf(k));
    });
    signerEl.textContent = signer === "provider"
      ? "Signed by the license provider."
      : "Signed by the chip operator’s own key.";
    if (openKey && !(checked && checked.fail[openKey])) closeDetail();
  }

  function labelOf(k) {
    return k === "lid" ? "License ID" : k === "did" ? "Device ID" : k === "use" ? "Usage Allowance" : "Signature";
  }

  function present() {
    checked = evaluate();
    closeDetail();
    if (checked.count === 0) {
      verdictEl.textContent = "Accepted. The chip unlocks the usage allowance on this license.";
      verdictEl.className = "verdict ok";
    } else {
      verdictEl.textContent = "Rejected by " + checked.count + " of the chip’s 3 defenses. Select a marked field to see why.";
      verdictEl.className = "verdict";
    }
    paint();
    save();
  }

  function openDetail(k) {
    if (!checked || !checked.fail[k]) return;
    openKey = k;
    var def = checked.fail[k];
    detailEl.hidden = false;
    while (detailEl.firstChild) detailEl.removeChild(detailEl.firstChild);
    var head = document.createElement("p");
    head.style.margin = "0 0 6px";
    head.textContent = labelOf(k) + ": " + checked.why[k];
    detailEl.appendChild(head);
    var quote = document.createElement("p");
    quote.className = "q";
    quote.style.margin = "0";
    quote.textContent = REASON[def];
    var src = document.createElement("span");
    src.className = "src";
    src.textContent = SRC;
    quote.appendChild(src);
    detailEl.appendChild(quote);
  }

  function closeDetail() {
    openKey = null;
    detailEl.hidden = true;
    while (detailEl.firstChild) detailEl.removeChild(detailEl.firstChild);
  }

  function markTamper() {
    var v = values();
    KEYS.forEach(function (k) { if (v[k] !== ISSUED[k]) tampered[k] = true; });
    if (signer !== "provider") tampered.sig = true;
  }

  var timer = null;
  function save() {
    if (timer) { clearTimeout(timer); timer = null; }
    var v = values();
    var st = { v: v, signer: signer, tampered: tampered, presented: !!checked };
    var done = KEYS.every(function (k) { return tampered[k]; });
    var summary = "Chip license forgery. Current license: License ID " + v.lid + ", Device ID " + v.did
      + ", Usage Allowance " + v.use + ", signature " + v.sig + ", signed by "
      + (signer === "provider" ? "the license provider" : "the operator") + ". "
      + (checked ? (checked.count === 0 ? "The chip accepted it." : "The chip rejected it on " + checked.count + " of 3 defenses.") : "Not yet presented to the chip.")
      + " Fields altered so far: " + KEYS.filter(function (k) { return tampered[k]; }).map(labelOf).join(", ") + ".";
    if (window.Lens && window.Lens.saveState) window.Lens.saveState(st, summary);
    else { try { window.localStorage.setItem("ogara-license-check", JSON.stringify(st)); } catch (e) { void e; } }
    if (done && !completed) {
      completed = true;
      if (window.Lens && window.Lens.complete) window.Lens.complete();
    }
  }

  function queueSave() {
    if (timer) clearTimeout(timer);
    timer = setTimeout(save, 400);
  }

  function setValues(v) {
    F.lid.value = v.lid; F.did.value = v.did; F.use.value = v.use; F.sig.value = v.sig;
  }

  KEYS.forEach(function (k) {
    F[k].addEventListener("input", function () {
      if (k === "sig") signer = "provider";
      markTamper();
      if (checked) { checked = null; verdictEl.textContent = ""; verdictEl.className = "verdict"; closeDetail(); paint(); }
      else paint();
      queueSave();
    });
    FLAG[k].addEventListener("click", function () {
      if (openKey === k) closeDetail(); else openDetail(k);
    });
  });

  document.getElementById("present").addEventListener("click", present);
  document.getElementById("selfsign").addEventListener("click", function () {
    var v = values();
    signer = "operator";
    F.sig.value = digest(v.lid + "|" + v.did + "|" + v.use);
    markTamper();
    checked = null; verdictEl.textContent = ""; verdictEl.className = "verdict";
    closeDetail(); paint(); save();
  });
  document.getElementById("restore").addEventListener("click", function () {
    setValues(ISSUED);
    signer = "provider";
    checked = null; verdictEl.textContent = ""; verdictEl.className = "verdict";
    closeDetail(); paint(); save();
  });
  document.addEventListener("keydown", function (e) { if (e.key === "Tab") document.body.classList.add("kb"); });
  document.addEventListener("pointerdown", function () { document.body.classList.remove("kb"); });
  document.addEventListener("visibilitychange", function () { if (document.visibilityState === "hidden") save(); });

  function restore(st) {
    if (!st || typeof st !== "object") return;
    if (st.v && typeof st.v === "object") {
      KEYS.forEach(function (k) { if (typeof st.v[k] === "string") F[k].value = st.v[k]; });
    }
    if (st.signer === "operator") signer = "operator";
    if (st.tampered && typeof st.tampered === "object") {
      KEYS.forEach(function (k) { if (st.tampered[k]) tampered[k] = true; });
    }
  }

  setValues(ISSUED);
  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state, meta) {
      restore(state);
      if (meta && meta.completed) completed = true;
      markTamper();
      paint();
    });
  } else {
    try {
      var raw = window.localStorage.getItem("ogara-license-check");
      if (raw) restore(JSON.parse(raw));
    } catch (e2) { void e2; }
  }
  paint();
})();
</script>
</body>
</html>
