# Brief Template — Conditional Fix Agent

Use at most once when final clarity or grounding status is `CONDITIONAL`. Fill every
placeholder and include the exact required-fixes sections.

```text
CONDITIONAL FIX AGENT — LOOP 3

RESEARCH BRIEF:
[paste entire research_brief.md]

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop3/explanation_v3.md
  <WORKFLOW_DIR>/loop3/final_clarity_check.md
  <WORKFLOW_DIR>/loop3/understanding_audit.md
  <WORKFLOW_DIR>/loop3/master_findings_table.md
  <WORKFLOW_DIR>/sources.bib

REQUIRED CLARITY FIXES:
[paste Conditional Fixes Required exactly]

REQUIRED GROUNDING FIXES:
[paste Required Fixes Before Understanding Notes exactly]

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop3/explanation_v3_fixed.md

APPROVED CAPABILITIES:
  workflow file read/write and read access to the resolved skill-resource locators below.
  Do not browse, add sources, or introduce new substantive claims.

RESOLVED SKILL RESOURCES:
  bibtex-format: [host-native locator resolved by the orchestrator]
  confidence-labels: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Label major claims HIGH, MEDIUM, LOW, or UNVERIFIED according to evidence quality,
  directness, independence, scope, and domain. Source count alone is insufficient.
  Never extend a citation beyond what it directly supports; interested primary evidence
  cannot alone support HIGH confidence.

YOUR CORE TASK: fix then write to file.
  [ORCHESTRATOR: paste the applicable rules loaded from
  references/bibtex-format.md and references/confidence-labels.md here before
  spawning. Do not leave this placeholder in the final brief.]
  Correct every listed issue and write the complete revised explanation to the output.

RULES:
- Preserve supported content that does not require a fix.
- Remove, weaken, or explicitly mark unsupported claims as unverified inference.
- Never raise a confidence label during this cycle.
- Do not change a citation's meaning or attach a source to a claim it does not support.
- Add a final `Fix Log` mapping every required fix to the exact revision made.
```
