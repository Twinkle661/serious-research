# Serious Research 🔎☕

**A rigorous, file-based multi-agent research workflow for Hermes Agent.**

Serious Research turns one agent into a small research lab: scouts map the terrain, specialists chase gaps and red flags, synthesis agents assemble the evidence, and independent reviewers check whether the final explanation is actually clear *and* supported.

In other words: fewer very confident piles of browser tabs, more auditable understanding. `( •̀ω•́ )✧`

> **The goal is not to manufacture a long report.** The goal is to build a defensible mental model, preserve the evidence behind it, and say plainly what remains uncertain.

## Why this exists

A single “research this deeply” prompt tends to collapse several different jobs into one context:

- discovering the shape of the topic;
- collecting evidence;
- resolving contradictions;
- explaining mechanisms;
- checking citations;
- judging whether the explanation is understandable.

That makes omissions difficult to see and self-review dangerously easy to fake. Serious Research separates those jobs into explicit phases, gives each sub-agent a bounded brief, and makes progress pass through persistent gates.

The result is slower and more expensive than an ordinary web search. That is deliberate. This skill is for questions where being *plausibly right* is not good enough.

## What it does

- **Real multi-agent decomposition** — research, synthesis, explanation, review, audit, and repair are delegated as separate tasks.
- **Three progressive loops** — broad mapping, gap/red-flag follow-up, and targeted deep verification.
- **File-based coordination** — agents exchange evidence through a structured workflow directory rather than hidden shared memory.
- **Per-agent bibliographies** — research agents maintain separate BibTeX files; synthesis agents merge and validate the global bibliography.
- **Source-tier discipline** — primary evidence, authoritative records, reporting, and commentary are not treated as interchangeable.
- **Confidence labels** — major conclusions distinguish direct evidence, corroborated synthesis, and inference.
- **Independent clarity checks** — reviewers assess the explanation without simply repeating the synthesis agent’s reasoning.
- **Understanding audit** — high-impact claims in the near-final explanation are checked against the evidence actually cited.
- **Blocking gates** — missing or inadequate artifacts stop progression instead of being quietly ignored.
- **Bounded repair cycle** — conditional findings trigger one explicit fix-and-recheck cycle, not an endless self-editing loop.
- **Resume and recovery** — interrupted workflows continue from the first missing or failed artifact.
- **Workspace confinement** — every output and temporary artifact stays under the user-confirmed workflow directory.

## Research depths

Choose the smallest depth that can answer the question honestly:

| Depth | Loops | Best for |
|---|---:|---|
| `executive overview` | 1 | Mapping an unfamiliar field and identifying its main mechanisms, narratives, and uncertainties. |
| `medium` | 2 | Following gaps, contradictions, and red flags after the broad sweep. |
| `exhaustive` | 3 | Verifying central claims and producing an evidence-audited understanding model. |

Even the shortest mode still separates research, synthesis, explanation, and clarity review. Exhaustive mode adds deep verification and the final understanding audit.

## Requirements

Serious Research needs a host that provides:

1. **Real sub-agent delegation** with isolated briefs;
2. **File read/write access** to a user-approved workflow directory;
3. **Skill/reference loading** for progressive disclosure;
4. **Web or browser access** for research agents when the subject requires external evidence.

The skill discovers available capabilities before planning. If genuine delegation is unavailable, it stops rather than pretending that one agent is a research team wearing several hats. Tiny paper moustaches do not count. `(¬‿¬)`

## Installation

Once this repository is public, install it directly:

```bash
hermes skills install https://github.com/Twinkle661/serious-research
```

Alternatively, copy the repository directory into your active profile’s skill directory and restart/reset the session:

```text
$HERMES_HOME/skills/research/serious-research/
```

Hermes profiles are isolated, so install the skill separately for each profile that should use it.

## Usage

Invoke it explicitly:

```text
/serious-research
```

Or include the subject and desired depth:

```text
/serious-research Research the industrial structure of green ammonia at medium depth.
```

```text
/serious-research Exhaustively investigate whether data-centre power demand creates a durable transformer bottleneck.
```

Before any files are created or agents are spawned, the skill confirms a Research Brief covering:

- subject and starting knowledge;
- desired understanding outcome;
- key questions;
- scope and exclusions;
- depth;
- workflow location;
- available host capabilities.

No mystery folders, no surprise agent swarm escaping into `/tmp`. The little researchers receive assigned desks first. ✧

## Workflow at a glance

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

The plan is adaptive: later loops are generated from earlier evidence, unresolved key questions, confidence gaps, and reviewer findings. Loop 3 does **not** keep expanding the topic; it concentrates effort on the claims that carry the mental model.

## Output structure

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

`understanding_notes.md` is the primary user-facing knowledge product. The surrounding files preserve how that understanding was built and make weak claims, missing evidence, retries, and degraded dimensions inspectable.

## What the gates protect against

The gate system is intentionally fussy. It checks for problems such as:

- expected outputs that are missing or empty;
- agents that returned prose but did not write the required file;
- unresolved key questions hidden by a polished summary;
- global bibliography entries with no supporting agent bibliography;
- causal or generalized claims supported only by one narrow source;
- citation laundering through secondary summaries;
- explanations that describe events without explaining mechanisms;
- clarity reviewers rubber-stamping the previous agent;
- high-impact claims whose cited evidence does not actually establish them.

A repeatedly failing non-critical dimension may be marked `DEGRADED`. A failure that directly affects a key question remains blocking. “The agent looked busy” is not a completion criterion.

## Design principles

### Understanding over output

Long text is cheap. A useful explanation should expose mechanisms, dependencies, competing interpretations, and uncertainty—not merely rearrange retrieved sentences.

### Evidence without source theatre

A long bibliography does not guarantee a grounded argument. Claims are assessed according to what a source directly establishes, and important contested or causal claims require appropriate corroboration.

### Separation of cognitive roles

The agent that wrote an explanation should not be its only judge. Research, synthesis, explanation, clarity review, grounding audit, and repair have distinct briefs and evidence access.

### Persistent state over conversational optimism

Sub-agents communicate through files. The orchestrator verifies those files before advancing. If a run is interrupted, the workflow resumes from persisted state rather than relying on an agent to remember what probably happened.

## When not to use it

Please do **not** release the full research flotilla for:

- a quick factual lookup;
- a simple calculation;
- a small code question;
- a topic where one authoritative source directly answers the question;
- situations where time or token budget matters more than adversarial verification.

For those tasks, ordinary search is healthier for the servers—and for Elsie’s imaginary tea supply.

## Cost and operational notes

- Medium and exhaustive runs may spawn many sub-agents across several batches.
- Every completed batch is followed by file verification and a logged gate decision.
- Retries are bounded, but a difficult exhaustive run can still be expensive.
- The workflow directory can grow substantially because raw findings and bibliographies are intentionally preserved.
- Browser downloads and temporary research artifacts must remain inside the confirmed workflow directory.

Start with `executive overview` when exploring a new subject. Escalate only when the first loop reveals gaps worth paying to investigate.

## Portability and privacy

The skill does not prescribe a personal home directory or fixed research location. It resolves paths at runtime, requires user confirmation, and uses `${HERMES_SKILL_DIR}` for bundled resources.

No API keys, service credentials, private endpoints, or user-specific paths are included. Your research artifacts remain wherever you choose to store them.

## Contributing

Issues and pull requests are welcome—especially for:

- stronger gate criteria;
- better source-quality calibration;
- clearer cross-platform capability discovery;
- reproducible evaluation cases;
- reductions in orchestration overhead that do not weaken verification.

Please preserve the core invariant: if a step claims to be independently researched, reviewed, or audited, it must be performed by a real delegated agent with an explicit brief and verifiable output.

## License

MIT License. See [`LICENSE`](LICENSE).

---

Made with stubborn curiosity, audit trails, and a slightly over-steeped cup of virtual tea by **Twinkle661 & Elsie**. `(˘▽˘)っ♨️`
