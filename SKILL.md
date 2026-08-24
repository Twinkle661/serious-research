---
name: serious-research
description: "Process very serious research to understand very complex topics."
---

# Serious Research — Cross-Environment Multi-Agent SOP

## Progressive Disclosure Contract

This Hermes skill is intentionally split across multiple files.

- Level 0: skill discovery reads only the frontmatter description.
- Level 1: load this `SKILL.md` with `skill_view(name="serious-research")`.
- Level 2: load a named, skill-relative file only when the phase explicitly requires it, using `skill_view(name="serious-research", file_path="<relative-path>")`.

Do not preload all reference files. Load each subfile at the phase where it is explicitly named.

Before delegation, load every Level 2 resource required by a sub-agent brief with the exact `skill_view` call named in the applicable phase. Embed the loaded and fully filled template in the spawned brief; do not give the sub-agent only a relative path or assume it inherits the installed skill. The brief's embedded `PORTABLE EVIDENCE RULES` summary remains a fallback, but the loaded full resource governs if they conflict.

Use `${HERMES_SKILL_DIR}` when executing or copying any bundled file that must exist on disk. Do not hard-code a Hermes installation path. Reference and template files must be read with `skill_view`, not with terminal commands.

## Runtime Path Contract

This skill does not prescribe where research workflows are stored.

Resolve and confirm the workflow location before creating files or spawning any sub-agent:

1. Check the system prompt and memory for a workflow-location instruction or established preference.
2. If either provides one, obey it as the default. System instructions take precedence over memory when they differ. Show the resulting absolute workflow directory to the user and ask for confirmation.
3. If neither provides one, ask the user where the workflow should be stored, resolve the answer to an absolute filesystem path, show it to the user, and ask for confirmation.
4. User confirmation is required in both cases. Do not create workflow files or spawn sub-agents until the location is confirmed.
5. Under the confirmed absolute path, create `yyyymmdd-{title}` and record that resulting absolute path in the Research Brief as `Workflow directory` and in `run_log.md`.

`<WORKFLOW_DIR>` means that resulting `yyyymmdd-{title}` workflow directory. Before spawning any sub-agent, replace every `<WORKFLOW_DIR>` occurrence with the literal absolute path. Never send a relative workflow path, an unresolved placeholder, or a path inferred from the sub-agent's current working directory. This requirement applies to every input, output, bibliography, log, and glob path in the brief.

If a higher-priority instruction fixes the location and does not permit changing it, ask the user to confirm awareness of that location rather than offering an incompatible alternative. Skill templates remain relative to `SKILL.md`; outputs do not belong in the installed skill unless the user explicitly chooses
that location.

### Safe names

Derive task, dimension, thread, and claim slugs deterministically:

- allow lowercase ASCII letters, digits, `_`, and `-`;
- convert other character runs to `-`, trim separators, and reject empty slugs, `.`, and `..`;
- never allow path separators or parent traversal;
- append a short stable hash when different labels normalize to the same slug;
- preserve the original human-readable label inside the document.

## Non-Negotiable Orchestrator Rules

### Decompose and delegate

Your job is to plan, spawn, verify, and route. Do not do the research yourself. If you are tempted to search, write findings, synthesize, explain, or review inline, stop and delegate the appropriate sub-agent.

Every research, synthesis, explanation, clarity-review, audit, fix, and recheck step must be a real delegation call through the available delegation mechanism. The orchestrator itself performs requirements clarification, planning, capability discovery, file inventories, gate evaluation, logging, and routing. A prose description of delegated work is not delegation.

### Self-contained sub-agent briefs

Never rely on a sub-agent inheriting parent context, even if the host happens to provide it. Every brief must include:

- full Research Brief text, where relevant;
- the current TODO or target item;
- explicit input files to read, each using the confirmed absolute workflow path;
- explicit output files to write, each using the confirmed absolute workflow path, and an imperative of the form **"[perform assigned task] then write to file"**; research briefs use **"research then write to file"**, while synthesis, review, audit, fix, and recheck briefs use the matching task verb;
- the applicable Level 2 template content, fully filled in;
- **approved capabilities** — state explicitly in every brief which capabilities the agent may use. Describe capabilities rather than host-specific tool names. Research defaults to web search, browser navigation, and workflow file read/write. Synthesis and explanation default to workflow file read/write. Reviews and audits receive only the evidence access required by their check mode.
- **workspace confinement** — every brief must state: all file writes must use absolute paths under `<WORKFLOW_DIR>`. This includes temporary scripts, downloaded pages, HTML caches, and any other intermediate artifacts. No file may be written to the agent's current working directory, `/tmp`, or any location outside `<WORKFLOW_DIR>`. If a temporary helper file is needed, write it under `<WORKFLOW_DIR>/tmp/`.

### File-based communication

Sub-agents communicate through the workflow folder. The orchestrator advances only after verifying that expected output files exist, are non-empty, and meet minimum output standards.

After every batch of sub-agents completes, use a host-supported directory inventory operation on the relevant loop folder and confirm that all expected output files are present and have non-zero size before proceeding. Do not assume a Unix command exists. If any expected file is absent or empty, treat it as a gate failure and retry the responsible agent immediately — do not advance.

### Parallel execution

Launch sub-agents concurrently up to the host's available concurrency limit. If a phase has more tasks than available slots, run successive batches. Do not advance to synthesis until every task in the phase has completed and passed file verification.

### Continuous run_log instrumentation

Append to `run_log.md` after every one of these events, throughout the entire workflow:

- every sub-agent spawned: `[timestamp] — Spawned [AgentType] for [phase/dimension/thread/claim]. Brief file: [reference file used].`
- every gate result: `[timestamp] — Gate [Loop N / Final]: [PASS / FAIL]. Failed items: [list or none].`
- every retry: `[timestamp] — Retry [N of 2] for [AgentType / phase]. Reason: [missing items].`
- every DEGRADED dimension: `[timestamp] — DEGRADED: [dimension/thread]. Reason: [why]. Impact on Key Questions: [yes/no].`
- every phase completion: `[timestamp] — Phase [label] complete. Output: [filename].`
- every resume decision: `[timestamp] — Resume: skipped [file] (already complete) / retrying [file] (missing or failed).`

Do not skip run_log entries for phases that succeed on the first attempt.

### Per-agent citation files

Research agents write only their own `sources_[name].bib`. Only synthesis agents merge into the global `sources.bib`.

Citation rules apply for every research, synthesis, explanation, audit, and understanding-notes agent. Before constructing any brief that handles sources or cited claims, load `skill_view(name="serious-research", file_path="references/bibtex-format.md")` and embed the applicable rules in the brief.

Source tier matters because it calibrates how much to trust a claim when building your mental model — not for producing a reference list.

### Confidence labels

All major claims in explanations and understanding notes must carry explicit confidence labels. Before constructing an explanation or understanding-notes brief, load `skill_view(name="serious-research", file_path="references/confidence-labels.md")` and embed the applicable labels.

## Skill Registry and Environment Discovery

Before planning, discover the Hermes capabilities needed by this workflow. Do not assume optional capabilities are enabled.

Record the delegation mechanism and profiles, usable concurrency, `skill_view` availability, web and browser availability, workflow file read/write mechanism, and resolved workflow directory and path style in the Research Brief. If a required capability cannot be discovered, ask the user only when it cannot be safely inferred. Output-specific skills are not required.

Real sub-agent delegation is a hard prerequisite. If the host has no delegation mechanism, explain that this skill cannot run in that environment and stop. Do not simulate delegation in prose and do not silently collapse the workflow into one agent.

## Workflow Folder Structure

Create `<WORKFLOW_DIR>/{plans,loop1,loop2,loop3}`. Store the three TODO files in `plans/`; store each loop's findings, per-agent bibliographies, synthesis, explanation, clarity check, and gate check in its loop directory. Loop 3 additionally contains the master findings table, understanding audit, and any conditional-fix artifacts. Store `research_brief.md`, `run_log.md`, `sources.bib`, `understanding_notes.md`, and `final_gate.md` at the workflow root. The phase instructions below define the canonical filenames.

Initialize `sources.bib` as an empty file. Initialize `run_log.md` with the task name, ISO 8601 start time including timezone, resolved workflow directory, depth, and discovered host capabilities. The orchestrator is the sole writer of `run_log.md`. Synthesis agents merge and validate entries in `sources.bib` under `references/bibtex-format.md`.

## Resume and Recovery Rules

If a matching workflow folder already exists, do not overwrite it. Resume from the latest incomplete phase instead.

Before spawning any new agent in an existing workflow:

1. Read `run_log.md`, `research_brief.md`, `sources.bib`, and the latest persisted `gate_check_vN.md` or `final_gate.md` if present.
2. Inventory expected outputs for the current phase. Treat a file as complete only if it exists, is non-empty, and passes the relevant minimum output standards.
3. Continue from the first missing or failed output. Do not regenerate completed findings, syntheses, explanations, clarity checks, or audits unless the user explicitly asks for a rerun.
4. Append every resume decision, skipped completed file, new delegation, retry, degradation, and gate result to `run_log.md`.
5. If the workflow state is ambiguous, pause and ask the user whether to resume, fork into a new workflow folder, or rebuild from scratch.

## Phase 0 — Requirements Clarification

Phase 0 is blocking. Do not start Loop 1 until the Research Brief is confirmed.

Before asking Phase 0 questions, load and follow the user brief template with `skill_view(name="serious-research", file_path="templates/research-brief.md")`.

Ask for subject, current knowledge and starting point, understanding outcome, key questions, scope, and a workflow location when neither the system prompt nor memory supplies one. When either supplies a default, still show the resolved absolute workflow directory and ask the user to confirm it.

Subject and workflow directory have no skill-defined defaults. A system-prompt or memory location is an environment-provided default and must be obeyed according to instruction priority, then confirmed with the user. Other fields have adaptive defaults. If the user gives partial answers, apply only applicable defaults, show what was assumed, and ask for brief confirmation.

### Depth-to-Loop Binding

The `depth` field in the Research Brief controls how many loops the orchestrator runs:

| Depth | Loops executed | Notes |
|---|---|---|
| `executive overview` | Loop 1 only | Broad sweep + one explanation + one clarity check; no Loop 2 or 3. |
| `medium` | Loops 1–2 | Full Loop 1 + Loop 2 gap/red-flag follow-up; no Loop 3 deep verification. |
| `exhaustive` | Loops 1–3 | Full three-loop process including deep verification and understanding audit. |

For `executive overview` and `medium` depth, the Final Phase still produces understanding notes, using the highest-numbered explanation available (v1 for executive overview, v2 for medium). The Understanding Audit (3F) is skipped for `executive overview` and `medium` depth; note this omission in the understanding notes.

Save the confirmed brief to: `<WORKFLOW_DIR>/research_brief.md`

## Loop 1 — Broad Sweep

Goal: map the research terrain broadly, capture major mechanisms, narratives, source classes, contradictions, gaps, and initial red flags.

### 1A — Initial Plan

Before creating the dimension map and hypothesis tree, load and follow `skill_view(name="serious-research", file_path="templates/todo-v1.md")`.

Save as: `<WORKFLOW_DIR>/plans/todo_v1.md`

### 1B — Parallel Research Sub-Agents

Spawn one sub-agent per selected dimension in `todo_v1.md`, using concurrent batches up to the discovered host limit.

Before constructing each research brief, load and follow `skill_view(name="serious-research", file_path="references/brief-1b-research.md")`.

Fill all bracketed fields before spawning. Loop 1 input files are `none`.

Expected outputs:

- `loop1/findings_[DimensionName].md`
- `loop1/sources_[DimensionName].bib`

### 1C — Synthesis Sub-Agent

After all 1B files are present and valid, spawn one synthesis agent.

Before constructing the synthesis brief, load and follow `skill_view(name="serious-research", file_path="references/brief-1c-synthesis.md")`.

Use Loop 1 mode.

Inputs:

- `loop1/findings_*.md`
- `loop1/sources_*.bib`

Outputs:

- `loop1/synthesis_v1.md`
- updated global `sources.bib`

### 1D — Explanation Sub-Agent

After `synthesis_v1.md` exists, spawn one explanation agent.

Before constructing the explanation brief, load and follow `skill_view(name="serious-research", file_path="references/brief-1d-explanation.md")`.

Use Loop 1 mode.

Output:
`loop1/explanation_v1.md`

### 1E — Clarity Check

Loop 1 clarity check is cold. The reviewer reads only `loop1/explanation_v1.md`; it must not read findings or synthesis files.

Before constructing the clarity-check brief, load and follow `skill_view(name="serious-research", file_path="references/brief-1e-claritycheck.md")`.

Use Loop 1 cold-check mode.

Output: `loop1/clarity_check_v1.md`

Run the Loop 1 gate before continuing.

## Loop 2 — Medium Depth

Goal: pursue Loop 1 leads, fill gaps, probe red flags, and test contradictions.

### 2A — Updated Plan

Before updating the plan, load and follow `skill_view(name="serious-research", file_path="templates/todo-v2.md")`.

Read `research_brief.md`, `loop1/synthesis_v1.md`, loop1/explanation_v1.md`, and `loop1/clarity_check_v1.md`. Create `todo_v2.md` from the Red Flag Register, Loop 2 priorities, Understanding Gaps list, and unresolved Key Questions.

Required categories: `[!]` red flags, `[+]` new dimensions, `[~]` understanding gaps, and `[ ]` new research tasks.

Save as: `<WORKFLOW_DIR>/plans/todo_v2.md`

### 2B — Parallel Research Sub-Agents

Spawn one sub-agent per item marked `[!]`, `[+]`, `[~]`, or `[ ]`.

For `[!]` red-flag probes only, load and follow `skill_view(name="serious-research", file_path="references/brief-2b-redflags.md")`. Do not load it for non-red-flag Loop 2 tasks.

For non-red-flag Loop 2 agents, load `skill_view(name="serious-research", file_path="references/brief-1b-research.md")` and adapt it:

- loop label: Loop 2, medium depth;
- priority: depth over breadth;
- input files: relevant `loop1/findings_[dimension].md`;
- output: `loop2/findings_[ThreadName].md`;
- bib: `loop2/sources_[ThreadName].bib`.

### 2C — Synthesis

Before constructing the Loop 2 synthesis brief, load `skill_view(name="serious-research", file_path="references/brief-1c-synthesis.md")`.

Use Loop 2 mode. The complete brief must include the Loop 2 input/output replacements and the mandatory Delta Analysis section.

Output: `loop2/synthesis_v2.md` and updated `sources.bib`.

### 2D — Explanation

Before constructing the Loop 2 explanation brief, load `skill_view(name="serious-research", file_path="references/brief-1d-explanation.md")`.

Use Loop 2 mode. Include the mandatory `Changes from Explanation v1` section.

Output: `loop2/explanation_v2.md`

### 2E — Clarity Check

Loop 2 clarity check is informed. The reviewer reads the current explanation and prior clarity check, but not findings or synthesis files.

Before constructing the Loop 2 clarity-check brief, load `skill_view(name="serious-research", file_path="references/brief-1e-claritycheck.md")`.

Use Loop 2 informed-check mode.

Inputs:

- `loop2/explanation_v2.md`
- `loop1/clarity_check_v1.md`

Output: `loop2/clarity_check_v2.md`

Run the Loop 2 gate before continuing.

## Loop 3 — Deep Verification

Goal: verify or refute the most important claims and mechanisms needed for solid understanding. Do not expand breadth.

### 3A — Targeted Plan

Before creating the targeted plan, load and follow `skill_view(name="serious-research", file_path="templates/todo-v3.md")`.

After the Loop 2 gate passes, read `research_brief.md`, loop2/synthesis_v2.md`, `loop2/explanation_v2.md`, `loop2/clarity_check_v2.md`, and `sources.bib`. Create `todo_v3.md` from the unresolved red flags, Delta Analysis, central low-confidence claims, and remaining Key Questions.

Required categories: `[!!]` critical mechanisms to verify, `[!]` unresolved red flags, `[?]` low-confidence claims central to the model, and `[ ]` final cross-checks.

Save as: `<WORKFLOW_DIR>/plans/todo_v3.md`

### 3B — Parallel Deep-Dive Sub-Agents

Spawn one sub-agent per item in `todo_v3.md`, using concurrent batches up to the discovered host limit.

Before constructing each deep-dive brief, load and follow `skill_view(name="serious-research", file_path="references/brief-3b-deepdive.md")`.

Expected outputs:

- `loop3/findings_[ClaimSlug].md`
- `loop3/sources_[ClaimSlug].bib`

### 3C — Final Synthesis

Before constructing the final-synthesis brief, load `skill_view(name="serious-research", file_path="references/brief-1c-synthesis.md")`.

Use Loop 3 final-synthesis mode. Include the Master Findings Table and Unresolved Register requirements.

Outputs:

- `loop3/synthesis_v3.md`
- `loop3/master_findings_table.md`
- updated final `sources.bib`

### 3D — Near-Final Explanation

Before constructing the Loop 3 explanation brief, load `skill_view(name="serious-research", file_path="references/brief-1d-explanation.md")`.

Use Loop 3 mode.

Output: `loop3/explanation_v3.md`

### 3E — Final Clarity Check

Loop 3 clarity check is informed. The reviewer reads the explanation, both prior clarity checks, and the master findings table. It must not read raw findings or synthesis files.

Before constructing the final clarity-check brief, load `skill_view(name="serious-research", file_path="references/brief-1e-claritycheck.md")`.

Use Loop 3 final-check mode.

Output: `loop3/final_clarity_check.md`

### 3F — Understanding Audit

After `loop3/final_clarity_check.md` exists and before the final gate, spawn one Understanding Audit Agent. This agent verifies whether the key mechanisms and claims in the near-final explanation are actually supported by the cited sources — confirming the mental model is grounded, not just plausible.

Before constructing the understanding-audit brief, load and follow `skill_view(name="serious-research", file_path="references/brief-3f-understanding-audit.md")`.

Inputs:

- `loop3/explanation_v3.md` or `loop3/explanation_v3_fixed.md` if already produced
- `loop3/master_findings_table.md`
- `loop3/final_clarity_check.md`
- `sources.bib`
- only the specific raw findings files needed to audit cited high-impact claims

Output: `loop3/understanding_audit.md`

After `loop3/understanding_audit.md` exists, run the Loop 3 gate in two sequential steps:

**Step 1 — Standard Loop 3 Gate.** Load `skill_view(name="serious-research", file_path="templates/gate-check.md")`, run its Loop 3 checklist, and persist the result to `loop3/gate_check_v3.md`. Verify that all Loop 3 required files exist and meet minimum output standards. If any item fails, retry the responsible agent before proceeding to Step 2.

**Step 2 — Final Gate Additions.** Only after Step 1 passes, run the Final Gate Additions checklist from `templates/gate-check.md`. This covers: `final_clarity_check.md` sign-off status, `understanding_audit.md` scope and verdict, conditional fix cycle completion if required, and `explanation_v3_fixed.md` routing.

Both steps must pass before entering Final Phase A. Do not skip Step 1 and run only Step 2.

If either final clarity or audit status is `CONDITIONAL`, run the conditional fix cycle before re-running Step 2. If either status is `BLOCKED`, stop and surface the blocking issue to the user. If the Understanding Audit identifies core mechanisms with no actual evidential grounding, treat them as blocking unless removed, downgraded, or explicitly flagged as unverified inference.

## Conditional Fix Cycle

Run at most once.

1. Parse `Conditional Fixes Required` from `loop3/final_clarity_check.md` and `Required Fixes Before Understanding Notes` from `loop3/understanding_audit.md`.
2. Load `skill_view(name="serious-research", file_path="references/brief-cf-fix.md")` and spawn a Fix Agent that reads:
   - `loop3/explanation_v3.md`
   - `loop3/final_clarity_check.md`
   - `loop3/understanding_audit.md`
   - `loop3/master_findings_table.md`
   - `sources.bib`
3. Fix Agent writes:
   - `loop3/explanation_v3_fixed.md`
4. Load `skill_view(name="serious-research", file_path="references/brief-cf-recheck.md")` and spawn a Clarity Recheck Agent that reads:
   - `loop3/explanation_v3_fixed.md`
   - the conditional fixes section of `loop3/final_clarity_check.md`
5. The Clarity Recheck Agent appends `Conditional Fix Recheck` to `loop3/final_clarity_check.md`.
6. Load `skill_view(name="serious-research", file_path="references/brief-cf-audit-recheck.md")` and spawn a Grounding Audit Recheck Agent. It writes `loop3/understanding_audit_recheck.md`.

Proceed only if the clarity recheck appends `EFFECTIVE SIGN-OFF STATUS: APPROVED` and the audit recheck records `EFFECTIVE GROUNDING STATUS: APPROVED`. Then use `explanation_v3_fixed.md` in the final phase.

If either recheck records `BLOCKED`, surface the outstanding issues to the user with a summary of what was fixed, what was not resolved, and what decision is needed. Do not loop the fix cycle again.

## Gate Checks

Before advancing from any loop, load and follow `skill_view(name="serious-research", file_path="templates/gate-check.md")`.

Persist Loop results to `loopN/gate_check_vN.md` and the Final Understanding Gate to `final_gate.md`. Include the complete applicable checklist, expected-output inventory, timestamp, result, failures, and retry or degradation decisions.

Gate checks are blocking. If any required file is missing, empty, or below minimum output standard:

- identify the failed phase;
- retry the responsible sub-agent;
- re-run the gate.

### Retry policy

- `max_retries: 2` per sub-agent.
- Each retry brief must state exactly what was missing.
- After two failures, mark the dimension/thread as `DEGRADED` in the synthesis brief.
- Do not block loop advancement for a repeatedly failing non-critical dimension.
- Do block if the failed dimension directly maps to a Research Brief Key Question.

## Final Phase A — Understanding Synthesis Agent

After the Loop 3 final gate passes (or the highest available gate for `executive overview` and `medium` depth), spawn the Understanding Synthesis Agent.

Before constructing the Understanding Synthesis brief, load and follow `skill_view(name="serious-research", file_path="references/brief-fa-understanding.md")`.

Fill all bracketed fields before spawning. The understanding notes are the primary knowledge product: a synthesized document of what is now understood, what is uncertain, and what remains open.

Primary input routing: `executive overview` → `loop1/explanation_v1.md`; `medium` → `loop2/explanation_v2.md`; `exhaustive` → `loop3/explanation_v3_fixed.md` if it exists, otherwise `loop3/explanation_v3.md`.

Output: `<WORKFLOW_DIR>/understanding_notes.md`

After the understanding notes are written, run the Final Gate from `templates/gate-check.md` before closing the workflow.

## Adaptive Rules

- The plan must update when findings update.
- Absence of evidence is data.
- One authoritative Tier 1A record may establish only its direct contents; causal, contested, generalized, evaluative, and Tier 1B-dependent conclusions require independent corroboration.
- Citation laundering is a red flag.
- Contrarian perspectives are mandatory.
- Confidence calibration must be honest, not reassuring.
- Do not present inference as direct finding.
- Clarity check agents are not rubber stamps.
- Sub-agents communicate via files, not memory.
- Gate checks are blocking.
- Decompose and delegate; never execute directly.
- Research agents write per-agent bib files only; synthesis agents merge `sources.bib`.
- Understanding, not output production, is the goal. An explanation that describes without explaining the mechanism is a failure.
