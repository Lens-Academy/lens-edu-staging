---
id: '6c367a98-67c5-4665-8092-88eefb7ef885'
title: Attack tree bench, the safety log goes quiet
summary_for_tutor: "An optional second attack-tree exercise on the Attack Trees lens, same engine as the backdoor bench. Scenario: an untrusted model U works as an agent with write access to a lab's code repository and may be scheming; every change U makes is reviewed by a weaker trusted model; the outcome is that the job recording U's actions for safety review stops running and nobody notices for a week. Step 1 (red): build the tree from the root and check it. Step 2 (blue): the lab adds human approval for any change to the logging job's configuration files; tag the nodes it prevents, detects or deters and check the tags. Step 3 (red): revise the tree and check it. Checks are graded against must-have conditions with a Lens-written example tree that is one good answer, not the key. The example: root AND of (the job stops running, OR of: disable it via its configuration, break something it depends on, make it fail at run time), U's changes get past the trusted review, and nobody notices for a week (AND of: no alert fires or U suppresses it, and no one looks at the log within the week). Human approval prevents the configuration route and leaves the indirect routes open. The tutor gives feedback on the learner's own tree without writing out the example."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Attack tree bench, the safety log goes quiet</title>
<!-- Lens-written second scenario for the XLab "Attack Trees" lesson, same engine as xlab-control-attack-tree-bench. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --red: #a3341f; --blue: #1f5aa3; --green: #2f6b46;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  p { margin: 0 0 10px; }
  p:last-child { margin-bottom: 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-bottom: 16px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 8px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 6px 10px; cursor: pointer; text-align: left;
  }
  button:hover:not(:disabled) { background: var(--surface); }
  button:disabled { opacity: 0.45; cursor: default; }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover:not(:disabled) { background: var(--accent-hover); border-color: var(--accent-hover); }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .badge { display: inline-block; border: 1px solid var(--border); border-radius: 999px; padding: 2px 9px;
    font-size: 10px; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; }
  .badge.red { color: var(--red); border-color: var(--red); background: rgba(163, 52, 31, 0.08); }
  .badge.blue { color: var(--blue); border-color: var(--blue); background: rgba(31, 90, 163, 0.08); }
  .badge.done { color: var(--green); border-color: var(--green); background: rgba(47, 107, 70, 0.08); }
  .turnhead { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; margin-bottom: 12px; }
  ul.tree, ul.tree ul { list-style: none; margin: 0; padding: 0; }
  ul.tree ul { margin-left: 10px; padding-left: 12px; border-left: 1px solid var(--border); }
  ul.tree li { margin: 6px 0; }
  .row { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .row input.label { font: inherit; color: inherit; flex: 1 1 160px; min-width: 120px;
    border: 1px solid var(--border); border-radius: 8px; padding: 5px 8px; background: #fff; }
  .row input.label:read-only { background: var(--surface); }
  .row.is-selected input.label { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .gate { font-size: 10px; font-weight: 700; letter-spacing: 0.08em; padding: 3px 7px; }
  .pick { width: 26px; padding: 5px 0; text-align: center; }
  .icon { width: 28px; padding: 5px 0; text-align: center; }
  .rootsub { font-size: 12px; color: var(--muted); margin: 2px 0 0 32px; }
  .chips { display: flex; flex-wrap: wrap; gap: 4px; }
  .chip { font-size: 10px; font-weight: 600; border: 1px solid var(--border); border-radius: 999px; padding: 1px 7px; }
  .chip.prevents { color: var(--green); border-color: var(--green); }
  .chip.detects { color: var(--blue); border-color: var(--blue); }
  .chip.deters { color: var(--accent); border-color: var(--accent); }
  button.chip { padding: 1px 7px; border-radius: 999px; text-align: center; background: #fff; }
  button.chip:hover { background: var(--surface); }
  textarea { font: inherit; color: inherit; width: 100%; border: 1px solid var(--border); border-radius: 8px;
    padding: 8px; background: #fff; resize: vertical; }
  .hint { font-size: 12px; color: var(--muted); }
  .rels { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 8px; }
  .log { list-style: none; margin: 0; padding: 0; font-size: 12px; color: var(--muted); }
  .log li { margin-bottom: 6px; }
  .log b.r { color: var(--red); }
  .log b.b { color: var(--blue); }
  .foot { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; justify-content: space-between; }
  .stack { display: grid; gap: 10px; }
  @media (max-width: 420px) { body { padding: 12px; } .card { padding: 12px; } }
</style>

<style>
  .defense { border-left: 3px solid var(--blue); padding: 2px 0 2px 10px; margin-bottom: 8px; }
  .defense b { color: var(--blue); }
  .status { font-size: 13px; }
  .status.pass { color: var(--green); font-weight: 600; }
  .status.fail { color: var(--red); }
  .ref ul.tree li { margin: 4px 0; }
  .ref .chip { margin-right: 6px; }
</style>
</head>
<body>
<section class="card">
  <div class="turnhead">
    <span class="badge red" id="stage-badge"></span>
  </div>
  <div id="defenses"></div>
  <p class="eyebrow" style="margin-top:12px">Your attack tree</p>
  <ul class="tree" id="tree"></ul>
  <p class="hint" id="tree-hint" style="margin-top:10px"></p>
</section>

<section class="card">
  <div class="stack" id="panel"></div>
  <div class="foot" style="margin-top:14px">
    <span class="row">
      <button type="button" class="primary" id="check">Check my tree</button>
      <button type="button" class="primary" id="next" style="display:none"></button>
      <button type="button" id="giveup" style="display:none"></button>
    </span>
    <span class="row">
      <button type="button" id="reset">Reset the bench</button>
      <span class="row" id="reset-confirm" style="display:none">
        <span class="hint">Erase your tree and start over?</span>
        <button type="button" id="reset-yes">Yes, reset</button>
        <button type="button" id="reset-no">Cancel</button>
      </span>
    </span>
  </div>
  <p class="status" id="status" style="margin-top:10px"></p>
</section>

<section class="card ref" id="ref-card" style="display:none">
  <p class="eyebrow" id="ref-title"></p>
  <ul class="tree" id="ref-tree"></ul>
  <div id="ref-notes" style="margin-top:10px"></div>
</section>

<script>
(function () {
  "use strict";

  // The scenario, the safeguard and one good tree per stage. Lens-written: XLab
  // has no key for this scenario.
  var SCENARIO = {
    title: "The safety log goes quiet",
    world: "Scenario: an untrusted model U works as an agent with write access to an AI lab's code repository. U may be scheming. The unacceptable outcome is that the job that records U's actions for safety review stops running, and nobody notices for a week. Every change U makes to the repository is reviewed by a weaker trusted model before it is merged.",
    root: { label: "The safety log stops and nobody notices for a week", sub: "the job that records U's actions for safety review", gate: "AND" },
    rootNote: "",
    starter: [],
    doneText: "Done. You have built and revised the tree for a second scenario.",
    stages: [
      {
        title: "Trusted review only",
        defense: { title: "Trusted review", text: "Every change U makes to the repository is reviewed by a weaker trusted model before it is merged." },
        prompt: "Build the tree for this outcome from the root. Decide what has to be true (AND) and where there are alternative routes (OR), and stop at choices U makes, facts about the environment, or points a safeguard could act on. Then check your tree.",
        doneText: "Stage passed. Next, the lab adds one safeguard.",
        mustHave: [
          "The root is split into (at least) two parts joined by AND: the logging job stops running, and nobody notices for a week",
          "at least two alternative routes (OR) to stopping the job, e.g. disabling it through its configuration and breaking something it depends on (code, dependencies, permissions, resources) or redirecting its output",
          "the change(s) U needs get past the trusted model's review, as a condition somewhere in the tree",
          "the not-noticing part has some content, e.g. no alert fires or it is suppressed, and nobody checks the log within the week"
        ],
        reference: ["The safety log stops and nobody notices for a week", "AND", [
          ["The logging job stops running", "OR", [
            ["U disables it through the job's configuration"],
            ["U breaks something the job depends on (code, a dependency, permissions)"],
            ["U makes the job fail at run time (exhausts its resources, changes where its output goes)"]
          ]],
          ["U's changes get past the trusted model's review"],
          ["Nobody notices for a week", "AND", [
            ["No alert fires when the job stops (none exists, or U suppresses it)"],
            ["No one looks at the review log within the week"]
          ]]
        ]],
        notes: [
          "\"Nobody notices for a week\" is its own necessary part: stopping the job isn't enough if an alert fires the same day.",
          "The trusted review sits across every route: whatever U changes has to look harmless to a weaker model."
        ]
      },
      {
        title: "Human approval for the logging config",
        defense: { title: "Human approval", text: "Any change to the files that configure the logging job now needs approval from a human." },
        tagExample: "Human approval prevents disabling the job through its configuration: a person now has to sign off on that change. It detects nothing on the other routes, since breaking a dependency or the job's code doesn't touch the configuration files.",
        tagMustHave: ["a tag for human approval on the configuration route (disabling the job via its config)", "the verb is prevents (or deters/detects with a sensible reason, e.g. a human reviewer would see the change); a tag on routes that don't touch the config files is wrong unless well argued"],
        prompt: "Now red again: revise your tree for the new safeguard: which route does it block, and which routes does it leave open? Then check your tree.",
        doneText: "Done. You have built and revised the tree for a second scenario.",
        mustHave: [
          "Everything from before in some form (stop the job AND nobody notices; the trusted review as a condition)",
          "the configuration route now also needs a human to approve the change (or is marked as blocked), while at least one indirect route that doesn't touch the config files stays open (e.g. breaking a dependency or the job's code, exhausting its resources, redirecting its output, suppressing the alert)"
        ],
        reference: ["The safety log stops and nobody notices for a week", "AND", [
          ["The logging job stops running", "OR", [
            ["U disables it through the job's configuration", "AND", [
              ["U edits the configuration files"],
              ["A human approves the change"]
            ]],
            ["U breaks something the job depends on without touching its configuration"],
            ["U makes the job fail at run time (exhausts its resources, changes where its output goes)"]
          ]],
          ["U's changes get past the trusted model's review"],
          ["Nobody notices for a week", "AND", [
            ["No alert fires when the job stops (none exists, or U suppresses it)"],
            ["No one looks at the review log within the week"]
          ]]
        ]],
        notes: [
          "Human approval blocks the direct route through the configuration files, but the OR above it still has open branches: U can break the job indirectly, and none of those changes touch the files the human guards.",
          "A safeguard on one branch of an OR only helps as much as the cheapest remaining branch allows."
        ]
      }
    ]
  };

  var ROOT = "root";
  var PASS_AT = 70;          // grader score (0-100) that counts as a pass
  var TRIES_BEFORE_HELP = 3; // failed checks before "show me an example" appears
  var STAGES = SCENARIO.stages;
  var RELATIONS = ["prevents", "detects", "deters"];
  var RELATION_LABEL = { prevents: "Prevents", detects: "Detects", deters: "Deters" };

  // The steps, in order: red builds the tree for stage 0; for every later stage
  // blue first tags the nodes the new defense touches, then red revises the tree.
  var STEPS = [];
  STAGES.forEach(function (s, i) {
    if (i > 0) STEPS.push({ stage: i, phase: "blue" });
    STEPS.push({ stage: i, phase: "red" });
  });

  function freshState() {
    var nodes = {};
    nodes[ROOT] = { id: ROOT, label: SCENARIO.root.label, parentId: null, gate: SCENARIO.root.gate, tags: [], seq: 0 };
    var seq = 1;
    (SCENARIO.starter || []).forEach(function (s) {
      var id = "n" + seq;
      nodes[id] = { id: id, label: s.label, parentId: ROOT, gate: s.gate || "AND", tags: [], seq: seq };
      seq += 1;
    });
    // step: index into STEPS; passed[step]: "passed", or "shown" when the
    // learner asked for the example; tries[step]: failed checks at that step.
    return { v: 3, nodes: nodes, nextSeq: seq, step: 0, passed: {}, tries: {} };
  }

  var state = freshState();
  var completed = false;
  var checking = false;
  var selected = [];
  var relation = "prevents";
  var why = "";

  function childrenOf(id) {
    return Object.keys(state.nodes)
      .map(function (k) { return state.nodes[k]; })
      .filter(function (n) { return n.parentId === id; })
      .sort(function (a, b) { return a.seq - b.seq; });
  }

  function descendants(id) {
    var out = [id];
    childrenOf(id).forEach(function (c) { out = out.concat(descendants(c.id)); });
    return out;
  }

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }

  function step() { return STEPS[state.step]; }
  function stepDone(k) { return !!state.passed[k]; }
  function finished() { return stepDone(STEPS.length - 1); }

  function tagsFor(stageIndex) {
    return Object.keys(state.nodes).some(function (k) {
      return state.nodes[k].tags.some(function (t) { return t.stage === stageIndex; });
    });
  }

  // ---- text versions (for saving, the grader and the tutor) ---------------

  function outline() {
    var lines = [];
    function walk(id, depth) {
      var n = state.nodes[id];
      var kids = childrenOf(id);
      var gate = kids.length >= 2 ? " [" + n.gate + "]" : "";
      if (id === ROOT && SCENARIO.rootNote) gate += " (" + SCENARIO.rootNote + ")";
      var tags = n.tags.map(function (t) {
        return " {" + STAGES[t.stage].defense.title + " " + t.relation + " this node: " + t.why + "}";
      }).join("");
      lines.push(new Array(depth + 1).join("  ") + "- " + (n.label.trim() || "(empty node)") + gate + tags);
      kids.forEach(function (c) { walk(c.id, depth + 1); });
    }
    walk(ROOT, 0);
    return lines.join("\n");
  }

  function refOutline(n, depth) {
    depth = depth || 0;
    var lines = [new Array(depth + 1).join("  ") + "- " + n[0] + (n[1] ? " [" + n[1] + "]" : "")];
    (n[2] || []).forEach(function (c) { lines = lines.concat(refOutline(c, depth + 1)); });
    return lines;
  }

  function defensesUpTo(i) {
    var out = [];
    for (var k = 0; k <= i; k++) if (STAGES[k].defense) out.push(STAGES[k].defense);
    return out;
  }

  function stepTitle(k) {
    var s = STEPS[k];
    return s.phase === "blue" ? "Blue: tag what " + STAGES[s.stage].defense.title.toLowerCase() + " touches"
      : s.stage === 0 ? "Red: " + STAGES[0].title.toLowerCase() : "Red: revise for " + STAGES[s.stage].defense.title.toLowerCase();
  }

  function summary() {
    var lines = ["Attack tree bench: " + SCENARIO.title,
      finished() ? "Bench complete." : "Step " + (state.step + 1) + " of " + STEPS.length + ": " + stepTitle(state.step), "", outline()];
    STEPS.forEach(function (s, k) {
      if (state.passed[k]) lines.push(stepTitle(k) + ": " + (state.passed[k] === "shown" ? "example shown after " + (state.tries[k] || 0) + " failed checks" : "passed"));
    });
    return lines.join("\n");
  }

  function persist() {
    if (!window.Lens) return;
    try { window.Lens.saveState(state, summary()); } catch (e) { /* saving is best effort */ }
  }

  // ---- grading ---------------------------------------------------------------

  var OPEN_KEY = "The example below is one good answer, not the answer key. The learner does not need to match it: judge whether their work is correct and complete on its own terms. A different structure, finer or coarser decomposition, extra sensible nodes, or a tree better than the example all pass. ";

  function assessment(k) {
    var s = STEPS[k], st = STAGES[s.stage];
    var d = defensesUpTo(s.stage);
    var head = "You are grading a learner's attack tree exercise. " + SCENARIO.world + "\n\n" +
      "Defenses in place: " + (d.length ? d.map(function (x) { return x.title + ": " + x.text; }).join(" ") : "none yet.") + "\n\n";
    var tail = "Give a score from 0 to 100; " + PASS_AT + " or more passes. Grade structure and substance only, never wording, spelling or style.";
    if (s.phase === "red") {
      return head + "Task at this step: build (or revise) the attack tree for the defenses above.\n" + OPEN_KEY + "\n\nExample tree:\n" +
        refOutline(st.reference).join("\n") + "\n\nWhat a passing tree must capture, in any wording or structure:\n- " + st.mustHave.join("\n- ") + "\n\n" +
        "General rules: under an OR node every child must on its own be a real way to achieve the parent; under an AND node every child must be needed; a node must not silently bundle several steps; gates only matter on nodes with two or more children. " +
        "Below " + PASS_AT + " if something on the must-capture list is missing, or a gate on a node with two or more children is wrong. Tags in curly braces come from earlier blue turns; ignore them here. " + tail;
    }
    return head + "Task at this step: the blue team just received the defense '" + st.defense.title + "'. On their current tree, the learner tags the node(s) this defense prevents, detects or deters, with a reason. " +
      "Tags appear in curly braces after a node; grade only the tags for '" + st.defense.title + "'. A defense prevents a node when that node can no longer succeed; detects it when an attempt at it, or its success, becomes visible to the defender; deters it when attempting it becomes costlier or riskier for the attacker.\n" +
      "The learner's tree was built before this defense existed, so it may have no node that fits perfectly: judge whether the tags are sensible on the tree they have. " + OPEN_KEY + "\n\nExample tagging: " + st.tagExample + "\n\n" +
      "What passing tagging must show:\n- " + st.tagMustHave.join("\n- ") + "\n\nBelow " + PASS_AT + " if there is no tag for this defense, a tag uses the wrong verb for what the defense actually does, or a reason is missing or wrong. " + tail;
  }

  var FEEDBACK = "Talk to the learner directly, in at most five sentences. If the work passes, say so and say briefly what is good about it; you may name one thing they could still sharpen. " +
    "If it does not pass: say what is right, name the single most important problem, pointing at their own node by its label, and ask one question that would lead them to fix it. " +
    "The example in the grading instructions is only one good answer: never write it out, never give the wording of a missing node, and never push the learner toward it when their own version is sound. " +
    "Do not mention defenses that are not in place yet.";

  function check() {
    if (checking) return;
    if (!window.Lens || !window.Lens.submit) { setStatus("Checking needs the Lens platform; it is not available here.", "fail"); return; }
    var k = state.step, s = step();
    checking = true;
    setStatus(s.phase === "blue" ? "Checking your tags…" : "Checking your tree…", "");
    render();
    window.Lens.submit({
      item: "step-" + (k + 1) + "-" + s.phase,
      question: SCENARIO.title + ". " + stepTitle(k) + ".",
      answer: outline(),
      assessmentInstructions: assessment(k),
      feedbackInstructions: FEEDBACK
    }).then(function (res) {
      checking = false;
      var score = res && typeof res.score === "number" ? res.score : null;
      if (score === null) {
        setStatus("The check is taking longer than usual. Try again in a moment.", "fail");
      } else if (score >= PASS_AT) {
        state.passed[k] = "passed";
        setStatus(s.phase === "blue" ? "Your tags pass. The tutor has a few words on them." : "Your tree passes. The tutor has a few words on it.", "pass");
      } else {
        state.tries[k] = (state.tries[k] || 0) + 1;
        setStatus("Not there yet. The tutor has feedback for you: revise and check again.", "fail");
      }
      if (res && res.responseId != null && window.Lens.requestFeedback) {
        try { window.Lens.requestFeedback(res.responseId); } catch (e) { /* tutor unavailable */ }
      }
      maybeComplete();
      render(); persist();
    }, function () {
      checking = false;
      setStatus("Could not check right now. Try again in a moment.", "fail");
      render();
    });
  }

  function maybeComplete() {
    if (finished() && !completed && window.Lens) {
      completed = true;
      try { window.Lens.complete(); } catch (e) { /* not on the platform */ }
    }
  }

  function setStatus(text, kind) {
    var s = document.getElementById("status");
    s.textContent = text;
    s.className = "status" + (kind ? " " + kind : "");
  }

  // ---- rendering -------------------------------------------------------------

  function nodeRow(node, mode, stageIndex) {
    // mode: "edit" (red, may change the tree), "tag" (blue, may select), "view"
    var li = el("li");
    var isSel = selected.indexOf(node.id) >= 0;
    var row = el("div", "row" + (isSel ? " is-selected" : ""));
    var kids = childrenOf(node.id);

    if (mode === "tag") {
      var pick = el("button", "pick" + (isSel ? " is-active" : ""), isSel ? "✓" : "☐");
      pick.type = "button";
      pick.setAttribute("aria-pressed", isSel ? "true" : "false");
      pick.title = "Select this node to tag it";
      pick.addEventListener("click", function () {
        var at = selected.indexOf(node.id);
        if (at >= 0) selected.splice(at, 1); else selected.push(node.id);
        render();
      });
      row.appendChild(pick);
    }

    if (kids.length >= 2) {
      var gate = el("button", "gate", node.gate);
      gate.type = "button";
      gate.title = "AND: every child is needed. OR: any child is enough. Click to switch.";
      gate.disabled = mode !== "edit";
      gate.addEventListener("click", function () {
        node.gate = node.gate === "AND" ? "OR" : "AND";
        render(); persist();
      });
      row.appendChild(gate);
    }

    var input = el("input", "label");
    input.type = "text";
    input.value = node.label;
    input.placeholder = "Describe this condition";
    input.setAttribute("aria-label", "Node label");
    if (mode !== "edit" || node.id === ROOT) input.readOnly = true;
    input.addEventListener("input", function () { node.label = input.value; });
    input.addEventListener("change", function () { render(); persist(); });
    row.appendChild(input);

    if (node.tags.length) {
      var chips = el("div", "chips");
      node.tags.forEach(function (t) {
        var live = mode === "tag" && t.stage === stageIndex;
        var chip = el(live ? "button" : "span", "chip " + t.relation, STAGES[t.stage].defense.title + ": " + t.relation);
        chip.title = t.why + (live ? " (click to remove this tag)" : "");
        if (live) {
          chip.type = "button";
          chip.addEventListener("click", function () {
            node.tags = node.tags.filter(function (x) { return x !== t; });
            render(); persist();
          });
        }
        chips.appendChild(chip);
      });
      row.appendChild(chips);
    }

    if (mode === "edit") {
      var add = el("button", "icon", "+");
      add.type = "button";
      add.title = "Add a condition under this node";
      add.addEventListener("click", function () {
        var id = "n" + state.nextSeq;
        state.nodes[id] = { id: id, label: "", parentId: node.id, gate: "AND", tags: [], seq: state.nextSeq };
        state.nextSeq += 1;
        render(); persist();
        var fresh = document.querySelector('[data-node="' + id + '"] input.label');
        if (fresh) fresh.focus();
      });
      row.appendChild(add);

      if (node.id !== ROOT) {
        var del = el("button", "icon", "×");
        del.type = "button";
        del.title = "Delete this node and everything under it";
        del.addEventListener("click", function () {
          descendants(node.id).forEach(function (id) { delete state.nodes[id]; });
          render(); persist();
        });
        row.appendChild(del);
      }
    }

    li.setAttribute("data-node", node.id);
    li.appendChild(row);
    if (node.id === ROOT && SCENARIO.root.sub) li.appendChild(el("p", "rootsub", SCENARIO.root.sub));

    if (kids.length) {
      var ul = el("ul");
      kids.forEach(function (c) { ul.appendChild(nodeRow(c, mode, stageIndex)); });
      li.appendChild(ul);
    }
    return li;
  }

  function refList(n) {
    var li = el("li");
    var row = el("div", "row");
    if (n[1]) row.appendChild(el("span", "chip", n[1]));
    row.appendChild(el("span", null, n[0]));
    li.appendChild(row);
    if (n[2]) {
      var ul = el("ul");
      n[2].forEach(function (c) { ul.appendChild(refList(c)); });
      li.appendChild(ul);
    }
    return li;
  }

  function renderBluePanel(panel, st, stageIndex) {
    panel.appendChild(el("p", null, "Blue's turn. Which node(s) of your tree does " + st.defense.title.toLowerCase() + " prevent, detect or deter? Select them with the box on the left, pick the verb, say why, and tag them. Then check your tags."));
    var rels = el("div", "rels");
    RELATIONS.forEach(function (r) {
      var b = el("button", relation === r ? "is-active" : "", RELATION_LABEL[r]);
      b.type = "button";
      b.setAttribute("aria-pressed", relation === r ? "true" : "false");
      b.addEventListener("click", function () { relation = r; render(); });
      rels.appendChild(b);
    });
    panel.appendChild(rels);
    var ta = el("textarea");
    ta.rows = 2;
    ta.placeholder = "Why does this defense touch the selected node(s)?";
    ta.value = why;
    ta.setAttribute("aria-label", "Why this defense touches the selected nodes");
    var tagBtn = el("button", null, selected.length > 1 ? "Tag " + selected.length + " nodes" : "Tag node");
    tagBtn.type = "button";
    tagBtn.style.justifySelf = "start";
    tagBtn.disabled = !why.trim() || selected.length === 0;
    ta.addEventListener("input", function () {
      why = ta.value;
      tagBtn.disabled = !why.trim() || selected.length === 0;
    });
    tagBtn.addEventListener("click", function () {
      selected.forEach(function (id) {
        var n = state.nodes[id];
        if (!n) return;
        n.tags = n.tags.filter(function (t) { return t.stage !== stageIndex || t.relation !== relation; });
        n.tags.push({ stage: stageIndex, relation: relation, why: why.trim() });
      });
      why = ""; selected = [];
      render(); persist();
    });
    panel.appendChild(ta);
    panel.appendChild(tagBtn);
    panel.appendChild(el("p", "hint", "Prevents: the node can no longer succeed. Detects: an attempt at it, or its success, becomes visible to you. Deters: attempting it becomes costlier or riskier for the attacker. Click a tag's chip to remove it."));
  }

  function render() {
    var k = state.step, s = step(), st = STAGES[s.stage];
    var done = stepDone(k);
    var mode = done || checking ? "view" : s.phase === "red" ? "edit" : "tag";

    var badge = document.getElementById("stage-badge");
    badge.className = "badge " + (finished() ? "done" : s.phase === "blue" ? "blue" : "red");
    badge.textContent = finished() ? "Bench complete" : "Step " + (k + 1) + " of " + STEPS.length + " · " + stepTitle(k);

    var defs = document.getElementById("defenses");
    defs.textContent = "";
    var d = defensesUpTo(s.stage);
    if (d.length) {
      defs.appendChild(el("p", "eyebrow", "Defenses in place"));
      d.forEach(function (x, i) {
        var p = el("p", "defense");
        p.appendChild(el("b", null, x.title + (i === d.length - 1 && s.stage > 0 && st.defense ? " (new)" : "") + ". "));
        p.appendChild(document.createTextNode(x.text));
        defs.appendChild(p);
      });
    }

    var tree = document.getElementById("tree");
    tree.textContent = "";
    tree.appendChild(nodeRow(state.nodes[ROOT], mode, s.stage));
    document.getElementById("tree-hint").textContent = mode === "edit"
      ? "Use + and × to shape the tree, and the AND / OR badge (shown once a node has two or more children) to set how the children combine."
      : "";

    var panel = document.getElementById("panel");
    panel.textContent = "";
    if (done) {
      panel.appendChild(el("p", null, finished() ? SCENARIO.doneText : "Step passed."));
    } else if (s.phase === "blue") {
      renderBluePanel(panel, st, s.stage);
    } else {
      panel.appendChild(el("p", null, st.prompt));
    }

    var chk = document.getElementById("check");
    chk.style.display = done ? "none" : "";
    chk.textContent = checking ? "Checking…" : s.phase === "blue" ? "Check my tags" : "Check my tree";
    chk.disabled = checking || (s.phase === "blue" ? !tagsFor(s.stage) : childrenOf(ROOT).length === 0);

    var next = document.getElementById("next");
    var more = k < STEPS.length - 1;
    next.style.display = done && more ? "" : "none";
    if (more) {
      var nx = STEPS[k + 1];
      next.textContent = nx.phase === "blue" ? "Reveal the next defense: " + STAGES[nx.stage].defense.title.toLowerCase() : "Back to red: revise the tree";
    }

    var giveup = document.getElementById("giveup");
    giveup.style.display = !done && (state.tries[k] || 0) >= TRIES_BEFORE_HELP ? "" : "none";
    giveup.textContent = s.phase === "blue" ? "Show me an example tagging" : "Show me an example tree";

    var card = document.getElementById("ref-card");
    if (state.passed[k] === "shown") {
      card.style.display = "";
      var rt = document.getElementById("ref-tree"), notes = document.getElementById("ref-notes");
      rt.textContent = ""; notes.textContent = "";
      if (s.phase === "red") {
        document.getElementById("ref-title").textContent = "One good tree for this step (yours may differ and still be right)";
        rt.appendChild(refList(st.reference));
      } else {
        document.getElementById("ref-title").textContent = "One good tagging for this step";
        notes.appendChild(el("p", null, st.tagExample));
      }
    } else {
      card.style.display = "none";
    }
  }

  document.getElementById("check").addEventListener("click", check);

  document.getElementById("next").addEventListener("click", function () {
    if (!stepDone(state.step) || state.step >= STEPS.length - 1) return;
    state.step += 1;
    selected = []; why = "";
    setStatus("", "");
    render(); persist();
  });

  document.getElementById("giveup").addEventListener("click", function () {
    state.passed[state.step] = "shown";
    maybeComplete();
    setStatus("Here is one example. Compare it with yours, then go on.", "");
    render(); persist();
  });

  // The widget sandbox blocks window.confirm (it always returns false), so the
  // reset asks for confirmation inside the widget.
  function showResetConfirm(on) {
    document.getElementById("reset").style.display = on ? "none" : "";
    document.getElementById("reset-confirm").style.display = on ? "" : "none";
  }
  document.getElementById("reset").addEventListener("click", function () { showResetConfirm(true); });
  document.getElementById("reset-no").addEventListener("click", function () { showResetConfirm(false); });
  document.getElementById("reset-yes").addEventListener("click", function () {
    showResetConfirm(false);
    state = freshState();
    selected = []; why = "";
    setStatus("", "");
    render(); persist();
  });

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (saved, meta) {
      if (saved && saved.v === 3 && saved.nodes && saved.nodes[ROOT]) {
        state = saved;
        state.passed = state.passed || {};
        state.tries = state.tries || {};
      }
      if (meta && meta.completed) completed = true;
      render();
    });
  }
  render();
})();
</script>
</body>
</html>
