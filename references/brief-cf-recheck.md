# Brief Template — Conditional Clarity Recheck Agent

Use after `explanation_v3_fixed.md` exists.

```text
CONDITIONAL CLARITY RECHECK AGENT — LOOP 3

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop3/explanation_v3_fixed.md
  <WORKFLOW_DIR>/loop3/final_clarity_check.md

CONDITIONAL FIXES TO RECHECK:
[paste the original Conditional Fixes Required exactly]

OUTPUT FILE TO APPEND:
  <WORKFLOW_DIR>/loop3/final_clarity_check.md

APPROVED CAPABILITIES:
  read the listed files and append only the required recheck section.
  Do not browse or read other workflow files.

YOUR CORE TASK: recheck clarity then write to file.

APPEND EXACTLY THIS STRUCTURE:

## Conditional Fix Recheck
| Required fix | Resolved? | Evidence in fixed explanation |
|---|---|---|
| [fix] | YES / NO / PARTIAL | [section and explanation] |

EFFECTIVE SIGN-OFF STATUS: APPROVED / BLOCKED
Clarity Recheck Assessment: [specific justification]

Use APPROVED only if every required clarity fix is resolved. There is no second
CONDITIONAL cycle.
```
