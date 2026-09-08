---
id: '4ff6169a-9b62-4cc7-ad56-4f6e8f7ab186'
title: Training Through the Pause
summary_for_tutor: "XLab's worked red-team/blue-team example from the deleted unit 3.0 'What is Covert Development?'. The scenario (Sable Systems continuing a paused Orion-5 run through a Northstar insider and split cloud accounts) is in the lens text above the widget; the widget holds the six prompts: three red-team (most plausible evasion strategy; assumptions that must hold; where the operation is most vulnerable) and three blue-team (what the verifier does first; what each verification layer can establish; what finding and next action are justified). For each prompt the learner either writes an answer and saves it, which reveals XLab's sample student response with its 'Why this is strong' and 'Common weaknesses' lists and sends the answer for scoring against those lists, or opens the model answer without attempting. The widget-state block reports each prompt's status (attempted with score, read without attempting, or not opened) and the learner's text. Done means all six prompts have been opened by either route. Do not reveal a prompt's sample response, strengths or weaknesses before the learner has opened it; after that, help them compare their answer with the model, prompt by prompt."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Training Through the Pause</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "covert-worked-example". -->
<!-- Source: src/content/lessons/verification/covert-what-is-it.mdx at commit a10955c^ (the six worked-example prompts, sample responses, strengths and weaknesses). XLab rendered these as static prose; the write-then-reveal behaviour is the port's. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 26px; line-height: 1.2; }
  h2 { font-size: 19px; margin-top: 24px; }
  h3 { font-size: 17px; line-height: 1.3; }
  p { margin: 0 0 8px; }
  ul { margin: 0 0 8px; padding-left: 20px; }
  li { margin: 2px 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 4px; }
  .lede { color: var(--muted); max-width: 46rem; }
  .task { border: 1px solid var(--border); border-radius: 8px; padding: 12px 16px; background: var(--page); margin: 16px 0 8px; }
  .task p:last-child { margin-bottom: 0; }
  .progress { text-align: right; font-size: 12px; color: var(--muted); margin: 8px 0 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); margin-top: 12px; }
  .card.is-open { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .card-top { display: flex; flex-wrap: wrap; align-items: baseline; justify-content: space-between; gap: 6px 12px; }
  .status { font-size: 12px; color: var(--muted); border: 1px solid var(--border); border-radius: 999px; padding: 2px 10px; white-space: nowrap; }
  .status.is-attempted { color: var(--accent); border-color: var(--accent); }
  .status.is-read { color: var(--text); border-color: var(--text); }
  .prompt-label { font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--accent); margin: 0; }
  .prompt-text { font-family: var(--font-heading); font-size: 18px; font-weight: 500; line-height: 1.3; margin: 4px 0 12px; }
  textarea { display: block; width: 100%; min-height: 150px; font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: var(--bg); resize: vertical; }
  textarea:focus-visible { outline: 2px solid var(--text); outline-offset: 1px; }
  textarea[readonly] { background: var(--page); }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-top: 10px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 8px 12px; cursor: pointer; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); border-color: var(--accent-hover); }
  button:disabled { cursor: default; opacity: 0.55; }
  .note { font-size: 12px; color: var(--muted); }
  .score { font-size: 13px; margin: 0; }
  .score strong { color: var(--accent); }
  .reveal { display: none; border-top: 1px solid var(--border); margin-top: 16px; padding-top: 14px; }
  .reveal.is-open { display: block; }
  .reveal h3 { font-size: 15px; margin: 12px 0 6px; }
  .reveal h3:first-child { margin-top: 0; }
  .reveal .sample { background: var(--page); border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; }
  .reveal .sample p:last-child, .reveal .sample ul:last-child { margin-bottom: 0; }
  .done { display: none; border: 1px solid var(--accent); border-radius: 8px; padding: 12px 16px; margin-top: 16px; background: var(--page); }
  .done.is-open { display: block; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
  @media (max-width: 480px) { body { padding: 12px; } h1 { font-size: 22px; } .prompt-text { font-size: 16px; } }
</style>
</head>
<body>
<section aria-labelledby="we-title">
  <header>
    <p class="eyebrow">Worked example</p>
    <h1 id="we-title">Training Through the Pause</h1>
    <p class="lede">Estimated time: 15 to 20 minutes</p>
    <p class="lede">This is a fictional composite. The organizations and agreement are invented, but the tactics draw on documented cases involving insider exfiltration, format-shifting, cloud intermediaries, dual-use infrastructure, and incomplete declarations.</p>
    <div class="task">
      <p class="eyebrow">Your task</p>
      <p>As the red team, explain the most plausible evasion strategy, its assumptions, and its weakest point.</p>
      <p>As the blue team, explain how evidence from the hardware, cloud, intelligence, and human layers could be combined, and recommend a proportionate response.</p>
    </div>
    <p class="note">Each prompt hides a sample student response and the notes on why it is strong. Write your own answer and save it to open the sample and have your answer scored against those notes, or open the sample without answering.</p>
    <p class="progress" id="progress" aria-live="polite"></p>
  </header>

  <div id="groups"></div>

  <div class="done" id="done" role="status">
    <p class="eyebrow">All six prompts opened</p>
    <p>The answers above show what excellent student work might look like. Read on to the debrief.</p>
  </div>
</section>

<script>
  var STORAGE_KEY = "lens-widget:covert-worked-example";
  var TASK = "As the red team, explain the most plausible evasion strategy, its assumptions, and its weakest point. As the blue team, explain how evidence from the hardware, cloud, intelligence, and human layers could be combined, and recommend a proportionate response.";

  var GROUPS = [
    {
      id: "red",
      title: "The student answers the red-team prompts",
      prompts: [
        {
          id: "red-1",
          n: 1,
          prompt: "Describe the most plausible evasion strategy.",
          sample: [
            { text: "Sable’s cheapest credible strategy is to combine insider access with rented infrastructure." },
            { text: "A Northstar engineer already has a legitimate reason to interact with Orion-4. During an approved maintenance or evaluation window, the engineer could copy or transform enough of the weights to make them reconstructable outside Northstar." },
            { text: "The transfer should not resemble the event Northstar’s monitoring system expects. The engineer might fragment the files, repackage them through an approved workflow, or move them through an intermediate format or storage system. The precise trick matters less than the principle: preserve the information while changing the indicators the detector recognizes." },
            { text: "Lattice would receive or reconstruct the weights. It would then continue the paused Orion-5 development effort on rented cloud infrastructure." },
            { text: "To reduce scrutiny, Lattice could:" },
            { list: [
              "Divide the workload among related accounts;",
              "Use resellers and subcontractors;",
              "Describe the activity as inference, evaluation, or safety research;",
              "Keep each account below a simple reporting threshold."
            ] },
            { text: "The operation does not make the training invisible. It makes each piece look inconclusive." },
            { text: "Northstar sees an engineer performing apparently legitimate work. The reseller sees several medium-sized customers. The data center sees intensive compute but not necessarily the model or legal purpose. Corporate registries show Lattice, not Sable." },
            { text: "The strategy succeeds if these organizations fail to connect the same operation across their records." }
          ],
          strong: [
            "Chooses one coherent pathway rather than listing possibilities.",
            "Begins with the lowest-cost route: trusted access plus existing infrastructure.",
            "Shows how the human, cloud, and hardware layers interact.",
            "Identifies institutional fragmentation as the main concealment strategy.",
            "Avoids assuming that one technical trick makes the operation invisible."
          ],
          weak: [
            "Focusing on a clever exfiltration technique without explaining the full operation.",
            "Assuming the insider can freely export usable weights.",
            "Giving the attacker unlimited nation-state capabilities.",
            "Treating separate cloud accounts as automatically separate workloads."
          ]
        },
        {
          id: "red-2",
          n: 2,
          prompt: "What assumptions must be true for the strategy to work?",
          sample: [
            { text: "The operation is plausible, but several assumptions must hold." },
            { text: "First, the engineer must have access to usable model parameters. Access to source code, documentation, or an inference interface would not be enough." },
            { text: "Second, Northstar’s controls must rely too heavily on known file types, destinations, or transfer patterns. If Northstar monitors access volume, unusual privilege use, reconstruction activity, and behavioral sequences, reformatting alone may fail." },
            { text: "Third, the weights must survive transfer and reconstruction. Fragmentation may conceal the data but also create integrity problems and conspicuous recovery work." },
            { text: "Fourth, Lattice must coordinate enough compute to continue frontier development. Dividing the workload may avoid a simple threshold, but synchronized accounts can still reveal common control through shared administrators, payments, software, storage, timing, or network traffic." },
            { text: "Fifth, the workload must remain plausibly dual-use. A customer claiming to conduct protein inference may struggle to explain sustained training-like synchronization, checkpointing, and storage growth." },
            { text: "Finally, Sable must avoid revealing too much through the resulting model. Behavioral similarity would not prove derivation, but distinctive Orion-4 capabilities or failure patterns could strengthen other evidence." },
            { text: "Each concealment measure creates a tradeoff: more fragmentation reduces visibility in one system but creates more coordination records elsewhere." }
          ],
          strong: [
            "Separates a conceivable plan from a workable one.",
            "States the access, technical, organizational, and attribution assumptions.",
            "Recognizes that evasion creates new evidence.",
            "Gives the blue team concrete dependencies to attack."
          ],
          weak: [
            "Treating “insider” as equivalent to unrestricted weight access.",
            "Assuming training and inference are always indistinguishable.",
            "Treating shell companies as erasing ownership rather than delaying attribution.",
            "Ignoring the operational cost of reconstructing and coordinating the workload."
          ]
        },
        {
          id: "red-3",
          n: 3,
          prompt: "Where is the operation most vulnerable?",
          sample: [
            { text: "The operation is most vulnerable where the stolen weights and rented compute must be brought together." },
            { text: "The insider access is ambiguous by itself. The cloud workload is ambiguous by itself. Lattice’s connection to Sable is ambiguous by itself. But close timing among these events can make them mutually reinforcing." },
            { text: "The operation requires coordination: someone must know when the weights will arrive, where they will be reconstructed, when the cluster should be ready, and how the subcontractor accounts will cooperate. That creates messages, payments, provisioning records, shared credentials, technical tests, and witnesses." },
            { text: "The red team could compartmentalize the operation, but more compartmentalization creates more handoffs and more chances for error." },
            { text: "Its best defense is delay. If the indicators remain disconnected until temporary cloud records, messages, and access logs are deleted, investigators may retain suspicion but lose the evidence needed to prove the chain." }
          ],
          strong: [
            "Identifies one specific operational bottleneck.",
            "Explains why correlation is more dangerous than any single detector.",
            "Treats record retention and timing as central verification issues.",
            "Identifies a real tradeoff between compartmentalization and coordination."
          ],
          weak: [
            "Saying only that “the insider might be caught.”",
            "Naming every layer as equally vulnerable.",
            "Assuming defense in depth guarantees detection.",
            "Ignoring how quickly key evidence may disappear."
          ]
        }
      ]
    },
    {
      id: "blue",
      title: "The student answers the blue-team prompts",
      prompts: [
        {
          id: "blue-1",
          n: 4,
          prompt: "What should the verifier do first?",
          sample: [
            { text: "The verifier should not yet declare that Sable violated the pause. It should issue a coordinated evidence-preservation order and open a targeted investigation." },
            { text: "Northstar should preserve:" },
            { list: [
              "Weight-access and privilege logs;",
              "Maintenance and evaluation records;",
              "Endpoint and storage events;",
              "Internal transfers and unusual format conversions;",
              "Records from systems that could have handled the weights."
            ] },
            { text: "The cloud reseller and infrastructure operator should preserve:" },
            { list: [
              "Account creation and beneficial-ownership records;",
              "Payments and administrative logins;",
              "Accelerator reservations and job timing;",
              "Storage, checkpointing, and network activity;",
              "Links among the subcontractor accounts."
            ] },
            { text: "Government investigators should preserve relevant corporate, financial, procurement, travel, and communications evidence where legally authorized." },
            { text: "Investigators should test several hypotheses:" },
            { list: [
              "The engineer transferred Orion-4 weights, and Lattice continued prohibited training for Sable.",
              "The engineer’s activity and Lattice’s workload were unrelated.",
              "Lattice conducted a different intensive but permitted workload.",
              "The engineer transferred technical material, but not usable weights.",
              "Sable obtained or developed its model through another route."
            ] },
            { text: "The immediate goal is to preserve evidence capable of distinguishing among these explanations." }
          ],
          strong: [
            "Recommends an urgent but proportionate first action.",
            "Separates investigation from adjudication.",
            "Tests alternatives instead of seeking only confirming evidence.",
            "Focuses on records most at risk of deletion."
          ],
          weak: [
            "Jumping immediately to a new international verification architecture.",
            "Treating suspicion as proof of a pause violation.",
            "Demanding vague “full transparency.”",
            "Recommending a total shutdown before establishing the basic facts."
          ]
        },
        {
          id: "blue-2",
          n: 5,
          prompt: "What can each verification layer establish?",
          sample: [
            { text: "No layer can prove the entire case alone." },
            { text: "At the hardware layer, utilization, interconnect activity, power use, accelerator reservations, and attestations could show that the related accounts collectively performed a large, coordinated computation." },
            { text: "This could establish the scale and timing of the workload. It would not establish that Orion-4 was used or that the activity was legally prohibited." },
            { text: "At the cloud layer, investigators could determine whether the accounts shared administrators, payment sources, storage, software, network destinations, or coordinated start times. They could also compare the observed workload with its declared purpose." },
            { text: "This could show that several nominal customers were operating one training-like workload. It might not identify the model or ultimate sponsor." },
            { text: "At the intelligence layer, corporate, financial, procurement, employment, and communications evidence could connect Lattice, its subcontractors, Sable, and the Northstar engineer." },
            { text: "This could establish common control or motive. Some intelligence may remain uncertain, classified, or difficult to use in formal adjudication." },
            { text: "At the human layer, witnesses could explain why the Northstar access was unusual, how the accounts were divided, or what purpose the participants understood the workload to serve." },
            { text: "Human evidence provides context and intent, but it must be corroborated against records." },
            { text: "The strongest case would be a converging timeline: unusual Northstar access, a related data transfer, rapid cloud provisioning, synchronized training-like activity, ownership links to Sable, and testimony explaining the connection." }
          ],
          strong: [
            "Distinguishes observation from inference.",
            "Gives each layer a specific evidentiary role.",
            "Explains how the layers corroborate one another.",
            "Preserves uncertainty even when the evidence converges."
          ],
          weak: [
            "Assuming hardware attestation can certify a lawful purpose.",
            "Treating customer identification as equivalent to beneficial ownership.",
            "Using “intelligence fusion” without discussing provenance or reliability.",
            "Treating a whistleblower report as a completed finding."
          ]
        },
        {
          id: "blue-3",
          n: 6,
          prompt: "What finding and next action are justified?",
          sample: [
            { text: "The verifier should issue a preliminary finding of a credible suspected breach of the Frontier Training Pause requiring targeted inspection." },
            { text: "It currently knows that:" },
            { list: [
              "A Northstar engineer had a relationship with Lattice;",
              "Lattice and related accounts obtained substantial compute;",
              "The accounts ran synchronized workloads inconsistent with their simple declarations;",
              "Sable soon demonstrated a substantially improved Orion-like model."
            ] },
            { text: "It reasonably suspects that Orion-4 material was transferred and used to continue prohibited frontier development." },
            { text: "It does not yet know:" },
            { list: [
              "Whether usable Orion-4 weights were transferred;",
              "Whether the full model was reconstructed;",
              "Whether the workload crossed the pause’s technical threshold;",
              "Whether Sable controlled the accounts;",
              "Whether Northstar leadership authorized or knowingly ignored the conduct."
            ] },
            { text: "The inspection should prioritize:" },
            { list: [
              "Identifying what the engineer accessed and transferred;",
              "Determining whether the cloud accounts formed one coordinated workload;",
              "Establishing Lattice’s beneficial ownership and relationship to Sable;",
              "Comparing the actual workload with its declared purpose;",
              "Examining whether Sable’s model is technically consistent with derivation from Orion-4."
            ] },
            { text: "Interim measures could include suspending the engineer’s access, preserving the cloud environment, and pausing related accounts. A broader shutdown would require stronger evidence or a specific emergency authority." },
            { text: "Missing records, false declarations, or refusal to cooperate may constitute separate compliance violations. They would increase suspicion but would not by themselves prove that prohibited training occurred." }
          ],
          strong: [
            "Gives a clear decision under uncertainty.",
            "Separates known facts, inferences, and unresolved questions.",
            "Matches the response to the strength of the evidence.",
            "Distinguishes procedural violations from the underlying training violation."
          ],
          weak: [
            "Being so cautious that no action is recommended.",
            "Moving directly from suspicion to sanctions.",
            "Treating model similarity as proof of weight theft.",
            "Recommending every possible safeguard instead of prioritizing the investigation."
          ]
        }
      ]
    }
  ];

  var PROMPTS = [];
  GROUPS.forEach(function (g) { g.prompts.forEach(function (p) { p.team = g.id === "red" ? "Red team" : "Blue team"; PROMPTS.push(p); }); });

  // state.done[id] is "attempted" (wrote and saved) or "read" (opened the model answer without answering)
  var state = { answers: {}, done: {}, scores: {} };
  var completed = false;
  var responseIds = {};
  var ui = {};

  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }

  function blocks(container, list) {
    list.forEach(function (b) {
      if (b.list) {
        var ul = el("ul");
        b.list.forEach(function (item) { ul.appendChild(el("li", null, item)); });
        container.appendChild(ul);
      } else {
        container.appendChild(el("p", null, b.text));
      }
    });
  }

  function bullets(container, heading, items) {
    container.appendChild(el("h3", null, heading));
    var ul = el("ul");
    items.forEach(function (item) { ul.appendChild(el("li", null, item)); });
    container.appendChild(ul);
  }

  function markingScheme(p) {
    return "Score 0 to 100 against the worked example's own notes on the sample response. Why this is strong (each criterion met earns an equal share of the marks): " +
      p.strong.join(" ") +
      " Common weaknesses (deduct for each one present): " +
      p.weak.join(" ");
  }

  function openedCount() {
    return PROMPTS.filter(function (p) { return !!state.done[p.id]; }).length;
  }

  function summary() {
    var parts = PROMPTS.map(function (p) {
      var status = state.done[p.id];
      var line = p.team + " prompt " + p.n + " (" + p.prompt + "): ";
      if (!status) return line + "not opened.";
      if (status === "read") return line + "model answer opened without attempting.";
      var s = state.scores[p.id];
      return line + "attempted" + (typeof s === "number" ? ", scored " + s + " out of 100" : "") + ". Learner's answer: " + (state.answers[p.id] || "").trim();
    });
    return "Training Through the Pause worked example. " + openedCount() + " of " + PROMPTS.length + " prompts opened. " + parts.join(" ");
  }

  function persist() {
    var text = summary();
    if (window.Lens) {
      Lens.saveState(state, text);
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
    if (!completed && openedCount() === PROMPTS.length) {
      completed = true;
      if (window.Lens) Lens.complete();
    }
  }

  function build() {
    var root = document.getElementById("groups");
    GROUPS.forEach(function (g) {
      root.appendChild(el("h2", null, g.title));
      g.prompts.forEach(function (p) {
        var card = el("div", "card");
        card.id = "card-" + p.id;

        var top = el("div", "card-top");
        top.appendChild(el("p", "prompt-label", "Prompt " + p.n + " of " + PROMPTS.length + ": " + p.team));
        var status = el("span", "status", "Not opened");
        top.appendChild(status);
        card.appendChild(top);

        var promptText = el("p", "prompt-text", p.prompt);
        promptText.id = "prompt-" + p.id;
        card.appendChild(promptText);

        var ta = document.createElement("textarea");
        ta.setAttribute("aria-labelledby", "prompt-" + p.id);
        ta.placeholder = "Your answer";
        ta.addEventListener("input", function () {
          state.answers[p.id] = ta.value;
          persist();
        });
        card.appendChild(ta);

        var actions = el("div", "actions");
        var saveBtn = el("button", "primary", "Save answer and open the model answer");
        saveBtn.type = "button";
        saveBtn.id = "save-" + p.id;
        saveBtn.addEventListener("click", function () { attempt(p); });
        var readBtn = el("button", null, "Open the model answer without answering");
        readBtn.type = "button";
        readBtn.id = "read-" + p.id;
        readBtn.addEventListener("click", function () { readOnly(p); });
        var note = el("span", "note", "");
        actions.appendChild(saveBtn);
        actions.appendChild(readBtn);
        actions.appendChild(note);
        card.appendChild(actions);

        var score = el("p", "score", "");
        var fbBtn = el("button", null, "Ask the tutor for feedback on this answer");
        fbBtn.type = "button";
        fbBtn.id = "fb-" + p.id;
        fbBtn.hidden = true;
        fbBtn.addEventListener("click", function () {
          if (!window.Lens || !Lens.requestFeedback || responseIds[p.id] == null) return;
          Lens.requestFeedback(responseIds[p.id], "Can I get feedback on my answer to prompt " + p.n + ", " + p.prompt);
        });
        card.appendChild(score);
        card.appendChild(fbBtn);

        var reveal = el("div", "reveal");
        reveal.setAttribute("role", "region");
        reveal.setAttribute("aria-label", "Model answer for prompt " + p.n);
        reveal.appendChild(el("h3", null, "Sample student response"));
        var sample = el("div", "sample");
        blocks(sample, p.sample);
        reveal.appendChild(sample);
        bullets(reveal, "Why this is strong", p.strong);
        bullets(reveal, "Common weaknesses", p.weak);
        card.appendChild(reveal);

        ui[p.id] = { card: card, status: status, ta: ta, saveBtn: saveBtn, readBtn: readBtn, note: note, score: score, fbBtn: fbBtn, reveal: reveal };
        root.appendChild(card);
      });
    });
  }

  function renderPrompt(p) {
    var u = ui[p.id];
    var status = state.done[p.id];
    var answer = state.answers[p.id] || "";
    if (u.ta.value !== answer) u.ta.value = answer;
    u.card.classList.toggle("is-open", !!status);
    u.reveal.classList.toggle("is-open", !!status);
    u.status.className = "status" + (status === "attempted" ? " is-attempted" : status === "read" ? " is-read" : "");
    u.status.textContent = status === "attempted" ? "✓ Answered and opened" : status === "read" ? "✓ Opened without answering" : "Not opened";
    u.ta.readOnly = status === "attempted";
    u.ta.hidden = status === "read";
    u.saveBtn.hidden = !!status;
    u.readBtn.hidden = !!status;
    u.note.textContent = status === "attempted" ? "Answer saved." : status === "read" ? "You chose to read the model answer first." : "";
    var s = state.scores[p.id];
    if (status === "attempted" && typeof s === "number") {
      u.score.textContent = "";
      u.score.appendChild(el("strong", null, "Score: " + s + " / 100"));
      u.score.appendChild(document.createTextNode(" against the worked example's notes."));
    } else if (status !== "attempted") {
      u.score.textContent = "";
    }
    u.fbBtn.hidden = !(status === "attempted" && responseIds[p.id] != null);
  }

  function render() {
    PROMPTS.forEach(renderPrompt);
    var n = openedCount();
    document.getElementById("progress").textContent = n + " of " + PROMPTS.length + " prompts opened";
    document.getElementById("done").classList.toggle("is-open", n === PROMPTS.length);
  }

  function attempt(p) {
    if (state.done[p.id]) return;
    var u = ui[p.id];
    var text = (u.ta.value || "").trim();
    if (!text) {
      u.note.textContent = "Write an answer first, or open the model answer without answering.";
      u.ta.focus();
      return;
    }
    state.answers[p.id] = u.ta.value;
    state.done[p.id] = "attempted";
    render();
    persist();
    if (window.Lens && Lens.submit) {
      u.score.textContent = "Scoring your answer…";
      Lens.submit({
        item: p.id,
        question: "Worked example, Training Through the Pause. " + TASK + " " + p.team + " prompt " + p.n + ": " + p.prompt,
        answer: text,
        assessmentInstructions: markingScheme(p),
        feedbackInstructions: "Say which of the 'why this is strong' points the answer met and which it missed, name any of the common weaknesses it shows, then point the learner to the sample response. Do not rewrite their answer."
      }).then(function (result) {
        if (result && result.responseId != null) responseIds[p.id] = result.responseId;
        if (result && typeof result.score === "number") {
          state.scores[p.id] = result.score;
          persist();
        } else {
          u.score.textContent = "Scoring is taking a while; compare your answer with the sample meanwhile.";
        }
        renderPrompt(p);
      }).catch(function () {
        u.score.textContent = "Scoring did not complete; compare your answer with the sample.";
      });
    }
    u.reveal.scrollIntoView({ behavior: "smooth", block: "nearest" });
  }

  function readOnly(p) {
    if (state.done[p.id]) return;
    state.done[p.id] = "read";
    render();
    persist();
    ui[p.id].reveal.scrollIntoView({ behavior: "smooth", block: "nearest" });
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (saved.answers && typeof saved.answers === "object") {
        PROMPTS.forEach(function (p) { var v = saved.answers[p.id]; if (typeof v === "string") state.answers[p.id] = v; });
      }
      if (saved.done && typeof saved.done === "object") {
        PROMPTS.forEach(function (p) { var v = saved.done[p.id]; if (v === "attempted" || v === "read") state.done[p.id] = v; });
      }
      if (saved.scores && typeof saved.scores === "object") {
        PROMPTS.forEach(function (p) { var v = saved.scores[p.id]; if (typeof v === "number") state.scores[p.id] = v; });
      }
    }
    completed = !!(meta && meta.completed) || openedCount() === PROMPTS.length;
    render();
  }

  build();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var saved = null;
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(saved, null);
  }
</script>
</body>
</html>
