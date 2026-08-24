# Brief Template — Synthesis Sub-Agent

Use this template for 1C, 2C, and 3C. Fill in the loop-specific inputs, outputs, and mandatory additions before spawning. The brief must be complete; do not send only modifications.

```text
═══════════════════════════════════════════════════════════════════
SYNTHESIS SUB-AGENT BRIEF — LOOP [1 / 2 / 3]
(Part of: serious-research skill)
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

INPUT FILES TO READ:
  [Loop 1]
  <WORKFLOW_DIR>/loop1/findings_*.md
  <WORKFLOW_DIR>/loop1/sources_*.bib

  [Loop 2]
  <WORKFLOW_DIR>/loop1/synthesis_v1.md
  <WORKFLOW_DIR>/loop1/explanation_v1.md
  <WORKFLOW_DIR>/loop1/clarity_check_v1.md
  <WORKFLOW_DIR>/loop2/findings_*.md
  <WORKFLOW_DIR>/loop2/sources_*.bib

  [Loop 3]
  <WORKFLOW_DIR>/loop1/synthesis_v1.md
  <WORKFLOW_DIR>/loop2/synthesis_v2.md
  <WORKFLOW_DIR>/loop1/clarity_check_v1.md
  <WORKFLOW_DIR>/loop2/clarity_check_v2.md
  <WORKFLOW_DIR>/loop3/findings_*.md
  <WORKFLOW_DIR>/loop3/sources_*.bib

OUTPUT FILES TO WRITE:
  [Loop 1] <WORKFLOW_DIR>/loop1/synthesis_v1.md
  [Loop 2] <WORKFLOW_DIR>/loop2/synthesis_v2.md
  [Loop 3] <WORKFLOW_DIR>/loop3/synthesis_v3.md
           <WORKFLOW_DIR>/loop3/master_findings_table.md

  All loops: update <WORKFLOW_DIR>/sources.bib
  Merge current-loop sources_*.bib into global sources.bib.
  Identify duplicates by DOI, canonical URL, then normalized title + creator + year.
  Update an existing record when the incoming record is demonstrably more complete.
  Rename BibTeX key collisions that represent different sources.
  Validate cited keys and log merges, updates, renamed collisions, and conflicts.
 
APPROVED CAPABILITIES:
  workflow file read/write and read access to the resolved skill-resource locator below.
  Do not browse. If an input lacks required evidence, record a gap rather than adding research.

RESOLVED SKILL RESOURCE:
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Identify sources by DOI, then canonical URL, then normalized title + creator + year.
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. A direct record supports only its direct
  contents; stronger conclusions require appropriate independent corroboration.
  Resolve every cited key to exactly one global BibTeX entry.

YOUR CORE TASK: synthesize then write to file.
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]
  Read the assigned inputs, synthesize them, write every listed output, and update
  sources.bib under the identity, merge, collision, and validation rules.
───────────────────────────────────────────────────────────────────
INSTRUCTIONS

You are aggregating research from multiple parallel agents. Your job is synthesis, not summary. Surface structure, confidence, contradictions, gaps, and what the next loop must do.

Read all required files before writing.

Mandatory sections:

## Convergences
Which findings are independently confirmed by multiple dimensions or threads? Name supporting files and dimensions.

## Contradictions
Document both sides of every contradiction with source keys. Do not smooth over conflict.

## Gaps
Distinguish genuine absence of data from insufficient search. Note any DEGRADED dimensions and their impact.

## Red Flag Register
Flag citation laundering, conspicuous absences, anomalous numbers, too-positive narratives, timeline inconsistencies, conflicts of interest, and good-aggregate/bad-disaggregate patterns.

## Coverage Assessment
For each Research Brief Key Question, mark: answered / partially answered / no evidence / new sub-questions raised.

## Bib Merge Log
List all `sources_*.bib` files merged, duplicate keys removed, and confirmation that `sources.bib` was updated.
═══════════════════════════════════════════════════════════════════
```

## Loop 2 Mandatory Addition — Delta Analysis

Add this section to `synthesis_v2.md`:

```markdown
## Delta Analysis — Loop 1 vs Loop 2

### Confidence Changes
| Claim | Loop 1 confidence | Loop 2 confidence | Direction | Reason |
|---|---|---|---|---|

### Red Flag Status Update
| Red Flag | Loop 1 status | Loop 2 verdict | Evidence summary |
|---|---|---|---|

### Genuinely New Information
[Findings in Loop 2 with no Loop 1 equivalent.]

### Resolved vs Deepened Issues
[Which Loop 1 contradictions were resolved? Which deepened?]
```

An empty or single-sentence Delta Analysis fails the minimum standard.

## Loop 3 Mandatory Addition — Master Findings and Unresolved Register

For Loop 3, create both `synthesis_v3.md` and `master_findings_table.md`.

`master_findings_table.md` must include all columns:

```markdown
## Master Findings Table

| Claim | First appeared | Conf. L1 | Conf. L2 | Conf. L3 | Final rating | Evidence tier | Notes |
|---|---|---|---|---|---|---|---|
```

`synthesis_v3.md` must include:

```markdown
## Unresolved Register

Items that remain contested, unverified, or uncertain after three loops. These must be disclosed in the final report.

| Claim | Status | Why unresolved | Recommended disclosure |
|---|---|---|---|
```
