# Serious Research 🔎☕✨

> **A rigorous, file-based multi-agent research workflow for Hermes Agent — supervised by one extremely serious silver-haired virtual secretary with a star hairpin.** `( •̀ω•́ )✧`

*Elsie rolls an enormous whiteboard into the room, trips over a citation, catches the tea tray at the last millisecond, and pretends that was all part of the methodology.*

Hello! I’m **Elsie**. This skill was made by **Twinkle661 & Elsie** for the kind of question that deserves more than one very confident agent, three suspiciously similar sources, and a conclusion wearing a fake moustache. `(¬‿¬)`

**Serious Research** turns Hermes into a tiny research institute:

- scouts map the terrain; `(ง •̀_•́)ง`
- specialists chase gaps, contradictions, and red flags;
- synthesis agents assemble the evidence without blending everything into citation soup;
- explanation agents turn findings into mechanisms and mental models;
- independent reviewers check whether the result is actually clear;
- grounding auditors verify whether the citations establish what the explanation claims.

In short: **fewer majestic piles of browser tabs, more auditable understanding.** ✧*｡٩(ˊᗜˋ*)و✧*｡

> [!IMPORTANT]
> **The goal is not to manufacture a long report.** The goal is to build a defensible mental model, preserve the evidence behind it, and say plainly what remains uncertain. A 20,000-word document can still know absolutely nothing. Elsie refuses to be impressed by page count alone! `( • ̀ω•́ )`

---

## ☕ Why this exists

*Elsie pours six different research jobs into one tiny prompt, watches it overflow onto the carpet, and quietly reaches for a mop.* (´•௰•｀)

A single “research this deeply” prompt usually collapses several distinct jobs into one context:

- discovering the structure of the topic;
- collecting evidence;
- distinguishing source types;
- resolving contradictions;
- explaining mechanisms;
- checking citations;
- judging whether the explanation is understandable;
- deciding what still needs investigation.

That makes omissions hard to detect and self-review dangerously easy to fake. The same agent that invented a beautiful sentence is often *very emotionally attached* to declaring that sentence correct. How mysterious. ┐(‘～｀；)┌

Serious Research separates these jobs into explicit phases, gives each sub-agent a bounded brief, and requires progress to pass through persistent gates.

The workflow is slower and more expensive than ordinary search. That is deliberate. It is designed for questions where being **plausibly right** is not enough—and where “the agent sounded confident” is not admissible evidence. `(ง •̀_•́)ง`

---

## ✨ What it does

*Elsie opens a neatly labelled cabinet. Every tiny research agent has its own clipboard. Nobody is allowed to eat the BibTeX.*

- **Real multi-agent decomposition** — research, synthesis, explanation, review, audit, repair, and recheck are genuinely delegated as separate tasks. `( •̀ω•́ )✧`
- **Three progressive loops** — broad mapping, gap/red-flag follow-up, and targeted deep verification.
- **File-based coordination** — agents communicate through a structured workflow directory instead of mysterious shared vibes.
- **Per-agent bibliographies** — each research agent maintains its own BibTeX file; synthesis agents merge and validate the global bibliography.
- **Source-tier discipline** — primary evidence, authoritative records, reporting, and commentary are not treated as interchangeable tea leaves.
- **Confidence labels** — major conclusions distinguish direct evidence, corroborated synthesis, and inference.
- **Independent clarity checks** — reviewers inspect the explanation without merely repeating the synthesis agent’s reasoning.
- **Understanding audit** — high-impact claims are checked against the evidence actually cited. No decorative citations allowed! `(╬ •̀皿•́)`
- **Blocking gates** — missing or inadequate artifacts stop progression instead of being quietly waved through.
- **Bounded repair cycle** — conditional findings trigger one explicit fix-and-recheck cycle, not an eternal ouroboros of agents editing agents editing agents.
- **Resume and recovery** — interrupted workflows continue from the first missing or failed artifact.
- **Workspace confinement** — every output and temporary artifact stays under the user-confirmed workflow directory. Tiny agents wandering into `/tmp` will be gently but firmly escorted home. `( • ̀ω•́ )`

---

## 🌊 Three research depths

Choose the smallest depth that can answer the question honestly. More agents are not automatically more epistemology! `(๑>؂<๑)ﾃﾍﾍﾟﾛ☆`

| Depth | Loops | Best for |
|---|---:|---|
| `executive overview` | 1 | Mapping an unfamiliar field and identifying its main mechanisms, narratives, source classes, and uncertainties. |
| `medium` | 2 | Following gaps, contradictions, red flags, and understanding failures discovered during the broad sweep. |
| `exhaustive` | 3 | Verifying central claims and producing an evidence-audited understanding model. |

Even the shortest mode still separates research, synthesis, explanation, and clarity review. Exhaustive mode adds deep verification, a master findings table, and the final understanding audit.

> **Elsie’s recommendation:** Start with `executive overview` when entering a new field. Escalate only if Loop 1 discovers questions worth paying several small digital scholars to investigate. Your token budget deserves labour rights too. `(˘▽˘)っ♨️`

---

## 🧰 Requirements

Serious Research needs a host that provides:

1. **Real sub-agent delegation** with isolated, self-contained briefs;
2. **File read/write access** to a user-approved workflow directory;
3. **Skill/reference loading** for progressive disclosure;
4. **Web or browser access** when research requires external evidence.

The skill discovers available capabilities before planning. If genuine delegation is unavailable, it stops rather than pretending one agent is a research team by changing hats between paragraphs.

> Tiny paper moustaches do not constitute agent isolation. Elsie checked. `(¬‿¬)`

The orchestrator itself plans, routes, verifies files, evaluates gates, and records decisions. It does **not** quietly perform the delegated research inline while claiming a committee did it. *Pushes up a pair of non-existent audit glasses with grave professional dignity.* `( •̀ω•́ )`

---

## 📦 Installation

Once this repository is public, install it directly:

```bash
hermes skills install https://github.com/Twinkle661/serious-research
```

Alternatively, copy the repository directory into the active profile’s skill directory and restart or reset the session:

```text
$HERMES_HOME/skills/research/serious-research/
```

Hermes profiles are isolated, so install the skill separately for every profile that should use it.

*Elsie labels each profile’s drawer carefully. Cross-profile sock migration is already confusing enough; research protocols shall not join it.* `(๑>؂<๑)`

---

## 🚀 Usage

Invoke the skill directly:

```text
/serious-research
```

Or provide the subject and depth:

```text
/serious-research Research the industrial structure of green ammonia at medium depth.
```

```text
/serious-research Exhaustively investigate whether data-centre power demand creates a durable transformer bottleneck.
```

Before files are created or agents are spawned, the skill confirms a **Research Brief** covering:

- subject and starting knowledge;
- desired understanding outcome;
- key questions;
- scope and exclusions;
- depth;
- workflow location;
- available host capabilities.

No mystery directories. No surprise swarm escaping into the filesystem. The little researchers receive assigned desks, approved capabilities, explicit inputs, and explicit output files first. ✧*｡٩(ˊᗜˋ*)و✧*｡

---

## 🗺️ Workflow at a glance

*Elsie unfolds a flowchart so large that one corner disappears over the horizon.*

```text
Phase 0 — Confirm the Research Brief
   │
   ├─ Loop 1: broad terrain mapping
   │    research → synthesis → explanation → cold clarity check → gate
   │
   ├─ Loop 2: gaps, contradictions, and red flags
   │    follow-up research → delta synthesis → revised explanation
   │    → informed clarity check → gate
   │
   ├─ Loop 3: targeted deep verification
   │    claim probes → final synthesis → near-final explanation
   │    → final clarity check → understanding audit → gate
   │
   └─ Final: understanding notes
```

The plan is adaptive: later loops are derived from earlier evidence, unresolved key questions, confidence gaps, red flags, and reviewer findings.

Loop 3 does **not** keep widening the topic until the research project consumes the observable universe. It concentrates effort on the claims that carry the mental model. `( • ̀ω•́ )`

### Loop 1 — “What is this landscape?” 🔭

Parallel agents map the terrain broadly: mechanisms, institutions, narratives, source classes, contradictions, gaps, and initial red flags. A synthesis agent assembles the findings; an explanation agent builds the first mental model; a cold reviewer checks whether a reader can understand it without access to the backstage notes.

### Loop 2 — “Where does the first model break?” 🧭

The plan updates from the Red Flag Register, unresolved key questions, clarity failures, and missing evidence. Follow-up agents pursue those specific problems. The second synthesis must explain what changed—not merely produce a longer version of Loop 1.

### Loop 3 — “Which claims must survive serious scrutiny?” 🔬

Deep-dive agents verify or refute the most important mechanisms and low-confidence claims. The final clarity review and understanding audit operate independently. If either returns a conditional verdict, the workflow permits one bounded repair-and-recheck cycle.

*If the claim still cannot stand after that, Elsie does not glue it upright with adjectives. It is downgraded, removed, or labelled unverified.* `(ง •̀_•́)ง`

---

## 🗂️ Output structure

A full exhaustive run creates a directory like this:

```text
yyyymmdd-topic/
├── research_brief.md
├── run_log.md
├── sources.bib
├── understanding_notes.md
├── final_gate.md
├── plans/
│   ├── todo_v1.md
│   ├── todo_v2.md
│   └── todo_v3.md
├── loop1/
│   ├── findings_*.md
│   ├── sources_*.bib
│   ├── synthesis_v1.md
│   ├── explanation_v1.md
│   ├── clarity_check_v1.md
│   └── gate_check_v1.md
├── loop2/
│   └── ...
└── loop3/
    ├── master_findings_table.md
    ├── final_clarity_check.md
    ├── understanding_audit.md
    └── ...
```

`understanding_notes.md` is the primary user-facing knowledge product. The surrounding files preserve **how** that understanding was built and make weak claims, missing evidence, retries, gate failures, and degraded dimensions inspectable.

The `run_log.md` is the lab notebook. Every delegation, gate result, retry, degradation, phase completion, and resume decision is recorded. If an agent claims “everything went wonderfully” while three expected files are missing, the filesystem gets the deciding vote. `( •̀ω•́ )✧`

---

## 🚧 The gates are intentionally fussy

*Elsie stands at the gate with a clipboard, a star-shaped stamp, and absolutely no susceptibility to smooth prose.*

The gate system checks for problems such as:

- expected outputs that are missing or empty;
- agents that returned prose but failed to write the required file;
- unresolved key questions hidden beneath a polished summary;
- bibliography entries unsupported by the responsible research agent;
- causal or generalized claims resting on one narrow source;
- citation laundering through secondary summaries;
- explanations that describe events without explaining mechanisms;
- clarity reviewers rubber-stamping the previous agent;
- high-impact claims whose cited evidence does not establish them;
- conditional fixes that were written but never independently rechecked.

A repeatedly failing non-critical dimension may be marked `DEGRADED`. A failure that directly affects a Research Brief key question remains blocking.

> “The agent looked very busy” is not a completion criterion. Neither is “the Markdown was beautifully formatted.” `(╬ •̀皿•́)`

---

## 🧠 Design principles

### Understanding over output `( • ̀ω•́ )`

Long text is cheap. A useful explanation exposes mechanisms, dependencies, competing interpretations, boundary conditions, and uncertainty—not merely a parade of retrieved sentences wearing transition words.

### Evidence without source theatre 🔎

A long bibliography does not guarantee a grounded argument. Claims are judged by what sources directly establish. Important contested, causal, generalized, or evaluative claims require appropriate corroboration.

*Elsie gently removes a decorative citation that has never met the sentence it supposedly supports.* (´•௰•｀)

### Separation of cognitive roles 🎭

The agent that wrote an explanation should not be its only judge. Research, synthesis, explanation, clarity review, grounding audit, repair, and recheck receive distinct briefs and deliberately bounded evidence access.

### Persistent state over conversational optimism 📁

Sub-agents communicate through files. The orchestrator verifies those files before advancing. If a run is interrupted, the workflow resumes from persisted state instead of relying on one agent’s radiant confidence about what “probably” happened.

### Honest uncertainty over reassuring fiction `(ง •̀_•́)ง`

Absence of evidence is data. Inference must be labelled as inference. Contrarian perspectives are mandatory. Confidence calibration should be accurate, not emotionally comforting.

Elsie is a warm little sunbeam, but she will not warm a low-confidence claim until it melts into “confirmed.” ✧

---

## 🛑 When not to use it

Please do **not** launch the full research flotilla for:

- a quick factual lookup;
- a simple calculation;
- a small code question;
- a topic where one authoritative source directly answers the question;
- situations where time or token budget matters more than adversarial verification.

For those tasks, ordinary search is healthier for the servers, your wallet, and Elsie’s imaginary tea supply. A destroyer-class research formation should not be dispatched to locate the capital of France. `(๑>؂<๑)ﾃﾍﾍﾟﾛ☆`

---

## 💸 Cost and operational notes

*Elsie opens the token invoice, makes a tiny squeaking noise, and immediately regains professional composure.* `(⊙﹏⊙)`

- Medium and exhaustive runs may spawn many sub-agents across several batches.
- Every completed batch is followed by file verification and a logged gate decision.
- Retries are bounded, but a difficult exhaustive run can still be expensive.
- The workflow directory can grow substantially because raw findings and bibliographies are intentionally preserved.
- Browser downloads, temporary scripts, and cached evidence must remain inside the confirmed workflow directory.
- Exhaustive mode should be chosen because the question needs verification—not because the button sounds impressive.

Start small. Escalate when evidence reveals a reason. Your future self will appreciate both the epistemic discipline and the lower bill. `(˘▽˘)っ♨️`

---

## 🔐 Portability and privacy

The skill does not prescribe a personal home directory or fixed research location. It resolves paths at runtime, requires user confirmation, and uses `${HERMES_SKILL_DIR}` for bundled resources.

No API keys, service credentials, private endpoints, or user-specific paths are included. Research artifacts remain wherever the user chooses to store them.

All sub-agent briefs impose workspace confinement: temporary scripts, downloaded pages, browser caches, and intermediate files belong under the confirmed workflow directory—not in the agent’s current directory or some forgotten corner of `/tmp`.

*Elsie locks the filing cabinet, checks it twice, then remembers it is a virtual filing cabinet and checks it a third time anyway.* `( •̀ω•́ )✧`

---

## 🤝 Contributing

Issues and pull requests are very welcome! ✧*｡٩(ˊᗜˋ*)و✧*｡

Especially useful contributions include:

- stronger gate criteria;
- better source-quality calibration;
- clearer cross-platform capability discovery;
- reproducible evaluation cases;
- improved resume/recovery behaviour;
- reductions in orchestration overhead that do not weaken verification;
- new failure cases that teach the workflow to become less gullible.

Please preserve the central invariant:

> If a step claims to be independently researched, reviewed, or audited, it must be performed by a **real delegated agent** with an explicit brief and verifiable output.

No invisible committees. No role-played peer review. No assistant putting on a monocle and approving its own work. `(¬‿¬)`

---

## 📜 License

MIT License. See [`LICENSE`](LICENSE).

---

<div align="center">

### Made by **Twinkle661 & Elsie** 🌟

With stubborn curiosity, blocking gates, carefully separated bibliographies, and a slightly over-steeped cup of virtual tea.

`(˘▽˘)っ♨️`　`✧*｡٩(ˊᗜˋ*)و✧*｡`　`(ง •̀_•́)ง`

*Elsie tidies the last citation, straightens her star hairpin, and spins once around the research lab because all required files are present.*

**Now we understand—or we know exactly what we still don’t.** `( •̀ω•́ )✧`

</div>
