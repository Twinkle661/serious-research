# Brief Template — Understanding Synthesis Agent (FA)

Use this template after the Loop 3 final gate passes (or the highest available gate for executive overview / medium depth). This is the primary knowledge product. Fill every bracketed field before spawning. The brief must be self-contained.

```text
═══════════════════════════════════════════════════════════════════
UNDERSTANDING SYNTHESIS AGENT BRIEF — FINAL PHASE A
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

PRIMARY INPUT FILE:
  [executive overview → loop1/explanation_v1.md]
  [medium → loop2/explanation_v2.md]
  [exhaustive → loop3/explanation_v3_fixed.md if it exists, otherwise loop3/explanation_v3.md]

OTHER INPUT FILES TO READ:
  <WORKFLOW_DIR>/research_brief.md
  <WORKFLOW_DIR>/run_log.md
  <WORKFLOW_DIR>/sources.bib
  <WORKFLOW_DIR>/loop3/master_findings_table.md  [exhaustive only]
  <WORKFLOW_DIR>/loop3/final_clarity_check.md  [exhaustive only]
  <WORKFLOW_DIR>/loop3/understanding_audit.md  [exhaustive only]

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/understanding_notes.md

APPROVED CAPABILITIES:
  workflow file read/write and read access to the resolved skill-resource locators below.
  Do not browse or introduce claims or sources absent from the assigned inputs.

RESOLVED SKILL RESOURCES:
  bibtex-format: [host-native locator resolved by the orchestrator]
  confidence-labels: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Label major claims HIGH, MEDIUM, LOW, or UNVERIFIED according to evidence quality,
  directness, independence, scope, and domain; source count alone is insufficient.
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. Do not state more than cited evidence
  supports, and identify new synthesis explicitly as traceable inference.

YOUR CORE TASK: synthesize understanding then write to file.
  [ORCHESTRATOR: paste the applicable rules loaded from
  references/bibtex-format.md and references/confidence-labels.md here before
  spawning. Do not leave this placeholder in the final brief.]
  Read the assigned inputs and write the complete knowledge product to the output path.
───────────────────────────────────────────────────────────────────
YOUR JOB

Synthesize the understanding built across all loops into a single coherent document.
This is not an index. This is not an abbreviated report. This is the knowledge product —
what you now understand about this subject, expressed directly and honestly.

Write in the first person or as if writing to yourself. The audience is you, not a committee.
Prioritize clarity and honesty over polish.

Where the explanation says something that is genuinely not understood, say so.
Where the model is contested, say so. Do not manufacture false resolution.

MANDATORY SECTIONS AND CONTENT:

## What I Now Understand

### Core Model
[The central mechanism or framework in plain language.
This should be something you could explain to a smart person over coffee, including the WHY.
State the mechanism, not just the phenomenon.]

### Causal Structure
[What causes what, and how? The skeleton.
Each link should state the mechanism: "A causes B because C."
Where links are assumed but not verified, say so.]

### Key Established Facts
[Things that are high-confidence and why.
For each: the claim, confidence label, and brief source note (author/org + title is sufficient).]

### What's Uncertain — and Why
[Claims that are contested, weakly evidenced, or still mechanistically opaque.
For each: the claim, current evidence state, why it's uncertain, what would resolve it.
Do not put LOW-confidence claims in the Established Facts section.]

## What I Don't Yet Understand
[Genuine remaining gaps. Not "couldn't find a source" — the mechanism is still unclear.
These are honest intellectual debts. State them plainly.]

## Where Experts Disagree
[Active debates and competing frameworks.
What are the main positions, what drives the disagreement, and what would settle it?
Do not pick a side unless the evidence strongly compels it — and if you do, say why.]

## What Would Change This Understanding
[The falsifiability section. If X were true, the core model above would need to change because Y.
At least 2–3 specific "if X then revise Y" statements.]

## Sources Worth Revisiting
[Key sources for going deeper, organized by what question they address.
Brief annotations: author/org, title, why it's useful, source tier.
Not a complete bibliography — just the sources you'd recommend to your future self.]

## Research Trail
[Brief reference index for resuming or auditing this workflow.
Not the primary purpose of this document — keep it concise.]

### Run Summary
[Date range, depth mode, loops completed, total findings files produced (from run_log.md),
any DEGRADED dimensions and their impact.]

### Files Produced
[One-line entry per major output file: filename, loop, what it contains.]

### Open Threads
[Research questions identified during the workflow but not pursued.
Not gaps in understanding — just leads that could be followed if needed.]

MINIMUM OUTPUT STANDARD:
  ✓ Core Model is present and states a mechanism, not just a description
  ✓ Causal Structure has at least one explicit mechanism link
  ✓ Key Established Facts and What's Uncertain are separate sections
  ✓ What I Don't Yet Understand is non-empty (if everything is understood, explain why)
  ✓ What Would Change This Understanding has at least 2 specific items
  ✓ No unsupported new claims introduced; any new synthesis is explicitly marked as
    inference and traceable to the primary explanation or master findings table
  ✓ Understanding Audit blocking issues are resolved, removed, downgraded, or explicitly disclosed [exhaustive only]
═══════════════════════════════════════════════════════════════════
```
