# Brief Template — Explanation Sub-Agent

Use this template for 1D, 2D, and 3D. Apply the loop-specific mode before spawning.

The goal is not to write a report. The goal is to write an explanation that crystallizes understanding — for yourself, not an external reader. If you can describe without explaining the mechanism, you have failed.

```text
═══════════════════════════════════════════════════════════════════
EXPLANATION SUB-AGENT — LOOP [1 / 2 / 3]
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

INPUT FILES TO READ:
  [Loop 1]
  <WORKFLOW_DIR>/loop1/synthesis_v1.md
  <WORKFLOW_DIR>/loop1/findings_*.md
  <WORKFLOW_DIR>/sources.bib

  [Loop 2]
  <WORKFLOW_DIR>/loop1/explanation_v1.md
  <WORKFLOW_DIR>/loop2/synthesis_v2.md
  <WORKFLOW_DIR>/loop2/findings_*.md
  <WORKFLOW_DIR>/sources.bib

  [Loop 3]
  <WORKFLOW_DIR>/loop3/synthesis_v3.md
  <WORKFLOW_DIR>/loop3/master_findings_table.md
  <WORKFLOW_DIR>/loop2/explanation_v2.md
  <WORKFLOW_DIR>/sources.bib

OUTPUT FILE TO WRITE:
  [Loop 1] <WORKFLOW_DIR>/loop1/explanation_v1.md
  [Loop 2] <WORKFLOW_DIR>/loop2/explanation_v2.md
  [Loop 3] <WORKFLOW_DIR>/loop3/explanation_v3.md

APPROVED CAPABILITIES:
  workflow file read/write and read access to the resolved skill-resource locators below.
  Do not browse or introduce sources absent from the assigned inputs.

RESOLVED SKILL RESOURCES:
  confidence-labels: [host-native locator resolved by the orchestrator]
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Label each major claim HIGH, MEDIUM, LOW, or UNVERIFIED. HIGH requires evidence
  appropriate in quality, directness, independence, scope, and domain; source count
  alone is insufficient. Tier 1A = neutral primary; Tier 1B = interested primary;
  Tier 2 = independent secondary; Tier 3 = weak or unverified. Causal, contested,
  generalized, evaluative, and Tier-1B-dependent claims require independent
  corroboration. Cite stable BibTeX keys and never imply more than a source supports.

YOUR CORE TASK: explain then write to file.
  Read the assigned inputs and write the explanation to the one selected output path.
───────────────────────────────────────────────────────────────────
INSTRUCTIONS

CONFIDENCE LABEL DEFINITIONS:
  [ORCHESTRATOR: paste the definitions loaded from references/confidence-labels.md
  here before spawning. Do not leave this placeholder in the final brief.]
CITATION AND EVIDENCE-INDEPENDENCE RULES:
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]

This is a working explanation unless Loop 3 says near-final. Do not hide uncertainty. Do not smooth over contradictions. The explanation is for you, not for anyone else — so be honest about what you actually understand versus what you merely know.

CORE PRINCIPLE — MECHANISM OVER DESCRIPTION:
  Every significant claim must answer not just WHAT but HOW and WHY.
  "X leads to Y" is incomplete. "X leads to Y because Z mechanism" is the minimum.
  If you cannot state the mechanism, mark it as a black box. Do not fabricate a mechanism.

SOURCE REFERENCES:
  Include lightweight source references — enough to trace a claim back to the findings.
  Format: [AuthorYYYY_ShortTitle] or [findings_DimensionName.md] is sufficient.
  You do not need formal citation prose. You do need traceability.
  Confidence labels are mandatory on every major claim.

Required structure:

# Explanation v[1 / 2 / 3] — [Subject]
**Loop**: [loop label]
**Date**: [date]
**Status**: [WORKING / NEAR-FINAL]

## Core Model
[The central mechanism or framework in 1–3 paragraphs.
If you could keep only one section, what is actually going on here?
State the core thesis of your understanding directly.]

## How It Works — Step by Step
[Causal chain. Not "X happens then Y happens" but "X causes Y because Z mechanism."
Be explicit about every link. Where you don't know the mechanism, say so.]

## Key Facts and Their Significance
[Each significant finding:
  - claim (what it is)
  - why it matters to the core model (how it fits)
  - confidence label
  - source reference
Order by importance to the model, not by loop or dimension.]

## What I Still Don't Understand
[Genuine gaps in understanding — not just gaps in the research.
Where is the mechanism opaque? Where are you reasoning by analogy rather than from evidence?
Do not suppress this section. It is as important as the rest.]

## Competing Frameworks and Genuine Disagreements
[Where do credible sources disagree?
What are the competing explanations or models?
Do not pick a side for convenience. State the landscape.]

## What Would Change This Understanding
[If X turned out to be true, the Core Model above would need to change because Y.
Falsifiability and epistemic honesty check. If nothing could change the model, the model is dogma.]

## Coverage Map
[Which dimensions were researched; Key Questions answered, partial, or open.
Each Key Question from the Research Brief: answered / partially answered / still open.]
═══════════════════════════════════════════════════════════════════
```

## Loop 2 Mandatory Addition

Add after Coverage Map:

```markdown
## Changes from Explanation v1
[What materially changed from v1 and why.
Which gaps from clarity_check_v1 were filled? How?
Which black boxes from v1 are now explained?
Which confidence levels changed and why?]
```

## Loop 2 Input Priority

For Loop 2, treat `synthesis_v2.md` as the primary source of truth. Read `loop2/findings_*.md` only to verify specific mechanisms or fill gaps not covered by the synthesis. Do not re-synthesize from raw findings.

## Loop 3 Mandatory Structure

For Loop 3, use this stricter output structure:

```markdown
# Explanation v3 — [Subject]
**Loop**: 3 of 3 (Deep Verification — near-final)
**Date**: [date]

## Core Model
[The final synthesized understanding. This should be something you could explain
to a smart person who asked "but why?" three times in a row.]

## How It Works — Step by Step
[Full causal chain with mechanisms. Every link should be grounded in evidence.
For any link that cannot be grounded, state this explicitly.]

## Key Facts and Their Significance
[Each finding: claim, why it matters, confidence label, source reference.
For near-final, include enough source detail to verify: author/org, title, date.]

## What's Settled vs. Uncertain
[Explicitly separate:
  - What is established (HIGH confidence, multiple independent sources)
  - What is plausible but not confirmed (MEDIUM)
  - What is inferred or weakly supported (LOW / UNVERIFIED)
Do not blend these categories for narrative coherence.]

## Competing Frameworks
[Active debates and competing explanations. Do not resolve them artificially.]

## What I Still Don't Understand
[From the Unresolved Register. Do not omit. Do not soften.]

## What Could Not Be Verified
[What was searched, why it was not found or could not be confirmed.]

## What Would Change This Understanding
[Falsifiability check. If X, then the model above needs to change because Y.]

## Coverage Map
[Each Key Question: answered / partially answered / open, with confidence label.]
```

Loop 3 explanation must ground every major claim in sources, use explicit confidence labels, explicitly separate settled from uncertain knowledge, and disclose genuine black boxes.
