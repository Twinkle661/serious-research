# Template — Gate Check

Run before advancing from each loop and before Final Phase.

Gate checks are blocking.

Persist every completed gate. Write Loop gates to
`<WORKFLOW_DIR>/loop[N]/gate_check_v[N].md` and the Final Understanding Gate to
`<WORKFLOW_DIR>/final_gate.md`. Include the expected-output inventory, PASS/FAIL for
every applicable item, failed items, retry or degradation decision, and an ISO 8601
timestamp with timezone.

```markdown
# Gate Check — Loop [N]

**Check mode**: [Loop 1 / Loop 2 / Loop 3]
**Timestamp**: [ISO 8601 with timezone]

## Required Files

### Current Loop

- [ ] `loop[N]/findings_*.md` — at least one per dimension/thread/claim in TODO v[N]
- [ ] `loop[N]/sources_*.bib` — at least one per research agent
- [ ] `loop[N]/synthesis_v[N].md` — non-empty and all mandatory sections present
- [ ] `loop[N]/explanation_v[N].md` — non-empty and all mandatory sections present
- [ ] `loop[N]/clarity_check_v[N].md` or final clarity check file — non-empty and all mandatory sections present

### Global

- [ ] `sources.bib` — updated and deduplicated after synthesis

## Minimum Output Standards

### Findings Agents

- [ ] task-appropriate substantive coverage: normally at least 5 distinct sourced
      claims for a broad dimension; a narrower task may contain fewer only when it
      explains why the smaller set exhausts the assigned question
- [ ] Source Acquisition Log present
- [ ] Gaps Log present
- [ ] tier labels present
- [ ] per-agent bib file present

### Synthesis Agents

- [ ] Convergences present
- [ ] Contradictions present
- [ ] Gaps present
- [ ] Red Flag Register present
- [ ] Coverage Assessment present
- [ ] Bib Merge Log present
- [ ] Loop-specific required additions present

### Explanation Agents

- [ ] Core Model section present and non-empty
- [ ] How It Works section present (causal chain, not just description)
- [ ] What I Still Don't Understand section present and honest
- [ ] confidence labels on major claims
- [ ] source references present (not necessarily formal citations — enough to trace back to the findings)
- [ ] gaps and open questions disclosed

### Clarity Check — Loop 1

- [ ] Mechanism Checks present (including black box and vocabulary mask labeling)
- [ ] Causal Chain Gaps present
- [ ] Understanding Gaps List present and non-empty
- [ ] Next Loop Priorities present
- [ ] Clarity Assessment rating with specific justification
- [ ] check mode is COLD

### Clarity Check — Loop 2

- [ ] all Loop 1 mechanism, causal-chain, circularity, internal-confidence, missing-angle, confirmation-bias, lead, and understanding-gap checks are present
- [ ] Prior Gaps Review is present and non-empty
- [ ] at least 3 specific Loop 3 priorities are present
- [ ] Clarity Assessment has a specific justification
- [ ] check mode is INFORMED

### Clarity Check — Loop 3

- [ ] every final checklist item is marked PASS / PARTIAL / FAIL with specific notes
- [ ] Prior Gaps Resolution is present
- [ ] Blocking Issues and Conditional Fixes Required are present
- [ ] `SIGN-OFF STATUS` is exactly APPROVED / CONDITIONAL / BLOCKED
- [ ] Clarity Assessment has a specific justification
- [ ] check mode is FINAL INFORMED

## Failure Handling

If any item fails:

1. Do not advance.
2. Identify the responsible phase and agent.
3. Retry the agent with an explicit note:
   "Your previous output did not meet the minimum standard. Specifically: [missing items]. Please redo."
4. Re-run this gate.

Retry limit: 2 per sub-agent.

After two failed retries:

- mark non-critical dimensions as DEGRADED in the next synthesis brief;
- block advancement if the failed dimension directly answers a Research Brief Key Question;
- surface the degradation to the user.
```

Apply only the clarity subsection for the current loop. Do not require Loop 1
`Understanding Gaps List` or `Next Loop Priorities` headings from Loop 3 output.

## Final Gate Additions

Before Final Phase:

```markdown
- [ ] `loop3/final_clarity_check.md` exists
- [ ] `loop3/final_clarity_check.md` has initial `SIGN-OFF STATUS: APPROVED`, or its
      appended conditional recheck has `EFFECTIVE SIGN-OFF STATUS: APPROVED`
- [ ] `loop3/understanding_audit.md` exists
- [ ] Understanding Audit status is `APPROVED`, or a conditional cycle has produced
      `understanding_audit_recheck.md` with `EFFECTIVE GROUNDING STATUS: APPROVED`
- [ ] Understanding Audit covers the key mechanisms and high-confidence claims in the near-final explanation
- [ ] Understanding Audit marks no core mechanism as entirely unsupported unless that mechanism is removed, downgraded, or explicitly disclosed as unverified inference
- [ ] if status was `CONDITIONAL`, conditional fix cycle completed and recheck approved
- [ ] if the audit status was `CONDITIONAL`, audit recheck completed and approved
- [ ] if `explanation_v3_fixed.md` exists, Final Phase uses it as primary input
```

## Final Understanding Gate

Run after understanding notes are produced and before closing the workflow.

```markdown
# Final Understanding Gate — [Subject]

- [ ] `understanding_notes.md` exists and is non-empty.
- [ ] Core Model section directly addresses the Understanding Goal from `research_brief.md`.
- [ ] Every Key Question is answered or explicitly noted as unresolvable with reasons.
- [ ] Major claims have confidence labels.
- [ ] What's Uncertain section is non-empty if the Unresolved Register is non-empty.
- [ ] Open Threads section is honest — no black boxes presented as understood.
- [ ] Understanding Audit blocking issues are resolved, removed, downgraded, or explicitly disclosed. [exhaustive depth only — skip for executive overview and medium]
- [ ] No unsupported new claims introduced. New synthesis is allowed only when it is
      explicitly marked as inference and traceable to claims in the near-final
      explanation or master findings table.
```
