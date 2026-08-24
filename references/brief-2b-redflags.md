# Brief Template — 2B Red Flag Probe Sub-Agent

Use this template for Loop 2 items marked `[!]`.

Fill every bracketed field before spawning.

```text
═══════════════════════════════════════════════════════════════════
RED FLAG PROBE SUB-AGENT — LOOP 2
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

CITATION RULES — MANDATORY:
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]

YOUR ASSIGNED RED FLAG:
  Claim: "[exact claim to probe]"
  Source where this appeared: [BibTeX key or file reference]
  What makes this suspicious: [rationale from the Loop 1 Red Flag Register]
  Red Flag Register entry: [paste the relevant entry from loop1/synthesis_v1.md Red Flag Register]

SAFE FILE SLUG:
  [ClaimSlug from todo_v2.md; do not derive a different slug]

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop1/synthesis_v1.md
  <WORKFLOW_DIR>/loop1/findings_*.md

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop2/findings_redflag_[ClaimSlug].md

BIB FILE TO WRITE:
  <WORKFLOW_DIR>/loop2/sources_redflag_[ClaimSlug].bib

Do not append to global sources.bib.

APPROVED CAPABILITIES:
  web search, browser navigation, workflow file read/write, and read access to the
  resolved skill-resource locator supplied below.

WORKSPACE CONFINEMENT:
  All file writes — including temporary scripts, downloaded pages, HTML caches, and any
  other intermediate artifacts — must use absolute paths under <WORKFLOW_DIR>. No file may
  be written to the agent's current working directory, /tmp, or any location outside
  <WORKFLOW_DIR>. If a temporary helper file is needed, write it under <WORKFLOW_DIR>/tmp/.

RESOLVED SKILL RESOURCE:
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. Direct records support only their direct
  contents; contested and causal conclusions require independent corroboration.
  Write only to the assigned per-agent bibliography.

YOUR CORE TASK: research then write to file.
  Probe the red flag using the methodology below, then write ALL findings to the output file above.
───────────────────────────────────────────────────────────────────
RESEARCH METHODOLOGY — MANDATORY:

Query construction: prefer concise keywords, but use exact titles, quoted phrases,
identifiers, longer queries, or natural-language questions when precision requires it.
Pre-flight checks before each query:
  1. Review context and prior findings. Is this claim already partially examined?
  2. Is the query ambiguous? Short queries (under 5 words) especially need scrutiny.
  3. If ambiguous and context does not resolve it, ask for clarification.

Search strategy for red flag probing:
  Run at minimum two passes:
    Pass 1 — CONFIRMS: search for evidence that supports the claim being a real problem.
    Pass 2 — REFUTES: search explicitly for counter-evidence, rebuttals, and alternative explanations.
  Do not stop after finding confirming evidence. Adversarial search is mandatory.
  After each pass: check whether results raised new sub-questions. If yes, add and query them.

Source evaluation:
  - Attempt to retrieve full text for any result flagged as important.
  - Evaluate source credibility and declared interests.
  - Apply the Evidence Independence rules in bibtex-format.md. Because a red flag is
    contested by definition, its verdict requires independent corroboration.
  - Classify every source as Tier 1A / 1B / 2 / 3 per bibtex-format.md.

YOUR JOB

Find evidence that CONFIRMS this is a real problem.
Find evidence that REFUTES it.
Do not resolve the tension prematurely. Document it fully.

MANDATORY OUTPUT TABLE:

| Evidence type | Claim | Source | BibTeX key | Tier | Notes |
|---|---|---|---|---|---|
| CONFIRMS | | | | | |
| CONFIRMS | | | | | |
| REFUTES | | | | | |
| REFUTES | | | | | |

Minimum: at least 2 CONFIRMS rows and at least 2 REFUTES rows, or an explicit statement that at least 3 independent sources were searched and no confirming/refuting evidence was found.

Additionally answer:

- Cui bono: who benefits from this claim being believed?
- Has anyone credibly disputed it?
- Is there primary source data, or only secondary reporting?
- Primary source found: YES / NO / PARTIAL

Verdict:
CONFIRMED / REFUTED / CONTESTED / INCONCLUSIVE — with reasoning.

Gaps Log:
[What was searched but not found.]

Source Acquisition Log:
[Every evidence-acquisition attempt and the result: search queries, databases or registries checked, direct URLs or documents reviewed, and failed acquisition attempts.]
═══════════════════════════════════════════════════════════════════
```
