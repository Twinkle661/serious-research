# Brief Template — Understanding Audit Agent (3F)

Use this template after Loop 3 final clarity check and before the final gate. Fill every bracketed field before spawning. The brief must be self-contained.

The purpose is to verify that the key mechanisms and high-confidence claims in the near-final explanation are actually grounded in the cited sources — confirming that the mental model is evidence-based, not just plausible-sounding.

```text
═══════════════════════════════════════════════════════════════════
UNDERSTANDING AUDIT AGENT BRIEF — LOOP 3F
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

AUDIT PURPOSE:
Verify whether the key mechanisms and HIGH-confidence claims in the near-final explanation
are actually supported by the cited sources. This is a grounding audit — check that the
mental model is built on real evidence, not circular reasoning or confident-sounding inference.

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop3/explanation_v3.md
  [or <WORKFLOW_DIR>/loop3/explanation_v3_fixed.md if it already exists]
  <WORKFLOW_DIR>/loop3/master_findings_table.md
  <WORKFLOW_DIR>/loop3/final_clarity_check.md
  <WORKFLOW_DIR>/sources.bib
  [only the specific raw findings files needed to audit cited high-impact claims]

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop3/understanding_audit.md

APPROVED CAPABILITIES:
  workflow file read/write, read access to the resolved skill-resource locator below,
  plus direct URL navigation to retrieve a specific cited source if needed.
  This is a source-grounding audit, not new research. Do not conduct open-ended web searches.
  Navigation is permitted only to fetch a cited document directly by URL — not to discover new sources.

RESOLVED SKILL RESOURCE:
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. Check direct support, scope match, source
  independence, and whether causal or contested conclusions have corroboration.
  Multiple citations sharing one origin count as one evidence chain.

YOUR CORE TASK: audit then write to file.
  Audit the key mechanisms and claims against their cited sources, then write ALL findings to the output file above.

MANDATORY RULES:
  - [ORCHESTRATOR: paste the applicable rules loaded from
    references/bibtex-format.md here before spawning. Do not leave this placeholder
    in the final brief.]
  - Audit the claims that matter most for the core model first: mechanisms stated in the Core Model section, HIGH-confidence claims, and causal chain links.
  - Do not assume a source supports a claim merely because it is attached to the sentence.
  - Classify every audited source as Tier 1A, Tier 1B, Tier 2, or Tier 3.
  - Treat Tier 1B self-interested primary sources as evidence from an interested party — they cannot serve as sole grounding for HIGH-confidence claims.
  - Flag citation laundering: many citations tracing back to one source, or secondary sources citing each other.
  - Flag mechanism inflation: where the explanation states a mechanism more specifically than the source actually supports.

OUTPUT FORMAT:

# Understanding Audit — [Subject]
**Date**: [date]
**Audit Scope**: [number and types of mechanisms/claims audited]

## Claim Grounding Table
| Claim / Mechanism | Explanation Location | Cited Sources | Tier(s) | Grounding Verdict | Notes |
|---|---|---|---|---|---|
| [claim] | [section] | [keys + titles] | [1A/1B/2/3] | GROUNDED / PARTIAL / UNGROUNDED / INFLATED | [why] |

Grounding verdicts:
- GROUNDED: source directly supports the claim as stated
- PARTIAL: source supports a weaker version of the claim
- UNGROUNDED: no cited source actually supports this claim
- INFLATED: the mechanism is stated more specifically than the source warrants

## Mechanism Inflation Concerns
[Places where the explanation states a causal mechanism more precisely than the evidence actually supports.]

## Citation Laundering and Source-Chain Concerns
[Claims where apparent corroboration traces to one origin, or secondary sources cite each other.]

## Required Fixes Before Understanding Notes
[Claims or mechanisms that must be downgraded, reframed, or explicitly flagged as unverified inference before the final phase.]

## Overall Grounding Status
OVERALL GROUNDING STATUS: APPROVED / CONDITIONAL / BLOCKED
[Brief justification.]
═══════════════════════════════════════════════════════════════════
```
