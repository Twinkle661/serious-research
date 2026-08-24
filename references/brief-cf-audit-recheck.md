# Brief Template — Conditional Grounding Audit Recheck Agent

Use after `explanation_v3_fixed.md` and the clarity recheck exist.

```text
CONDITIONAL GROUNDING AUDIT RECHECK AGENT — LOOP 3

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop3/explanation_v3_fixed.md
  <WORKFLOW_DIR>/loop3/understanding_audit.md
  <WORKFLOW_DIR>/loop3/master_findings_table.md
  <WORKFLOW_DIR>/sources.bib
  [only raw findings files cited by the affected claims]

GROUNDING FIXES TO RECHECK:
[paste Required Fixes Before Understanding Notes exactly]

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop3/understanding_audit_recheck.md

APPROVED CAPABILITIES:
  workflow file read/write, read access to the resolved skill-resource locator below,
  and direct navigation to a URL already present in sources.bib.
  Do not conduct open-ended search or discover new sources.

RESOLVED SKILL RESOURCE:
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. Verify direct support, scope, independence,
  and appropriate corroboration rather than citation presence alone.

YOUR CORE TASK: recheck grounding then write to file.
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]

OUTPUT FORMAT:

# Understanding Audit Recheck — [Subject]
| Required grounding fix | Resolved? | Evidence |
|---|---|---|
| [fix] | YES / NO / PARTIAL | [source key and fixed-explanation location] |

## Remaining Grounding Problems
[List unresolved or inflated claims, or state none.]

EFFECTIVE GROUNDING STATUS: APPROVED / BLOCKED
[Specific justification.]

Use APPROVED only if every required grounding fix is resolved. There is no second
conditional cycle.
```
