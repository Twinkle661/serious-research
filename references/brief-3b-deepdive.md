# Brief Template — 3B Deep-Dive Verification Sub-Agent

Use this template for each Loop 3 target in `todo_v3.md`.

Fill every bracketed field before spawning.

```text
═══════════════════════════════════════════════════════════════════
DEEP-DIVE VERIFICATION SUB-AGENT — LOOP 3
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF:
[paste entire contents of research_brief.md]

YOUR TARGET:
[claim / question / red flag from todo_v3.md]

SAFE FILE SLUG:
[ClaimSlug from todo_v3.md; do not derive a different slug]

CURRENT EVIDENCE STATE:
[paste only relevant findings from loop1 and loop2 for this specific claim]

CURRENT CONFIDENCE RATING:
[HIGH / MEDIUM / LOW / UNVERIFIED]

INPUT FILES TO READ:
  <WORKFLOW_DIR>/loop1/findings_*.md  (relevant sections only)
  <WORKFLOW_DIR>/loop2/findings_*.md  (relevant sections only)

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop3/findings_[ClaimSlug].md

BIB FILE TO WRITE:
  <WORKFLOW_DIR>/loop3/sources_[ClaimSlug].bib

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
  contents; causal, contested, generalized, evaluative, and Tier-1B-dependent
  conclusions require independent corroboration. Write only to the assigned
  per-agent bibliography.

YOUR CORE TASK: research then write to file.
  Verify or refute the assigned claim using the methodology below, then write ALL findings to the output file above.
───────────────────────────────────────────────────────────────────
RESEARCH METHODOLOGY — MANDATORY:

Query construction: prefer concise keywords, but use exact titles, quoted phrases,
identifiers, longer queries, or natural-language questions when precision requires it.
Pre-flight checks before each query:
  1. Review existing findings from Loop 1 and Loop 2 for this claim. What do we already know? What is still unresolved?
  2. Is the query ambiguous? Especially scrutinise queries under 5 words.
  3. If ambiguous and context does not resolve it, ask for clarification.

Search strategy for deep verification:
  Priority: find the PRIMARY SOURCE, not secondary reporting.
    - If the primary source is inaccessible, attempt to retrieve it via browser navigation (DOI, institutional repository, preprint server).
    - If still inaccessible, state this explicitly — do not substitute secondary reporting as if it were primary.
  Adversarial requirement: search explicitly for sources CHALLENGING the claim. If none found, document at least 3 independent search attempts.
  Independence check: verify that cited sources do not simply cite each other. Circular corroboration is not independent evidence.
  After each search batch:
    - Coverage check: which aspects of the claim are now verified, contested, or unresolved?
    - Unexpected dimensions: did results surface new sub-questions? If yes, add and query them.

Source evaluation:
  - Attempt to retrieve full text for every important result.
  - Evaluate source credibility, institutional affiliation, publication date, declared interests.
  - Apply the Evidence Independence rules in bibtex-format.md. One authoritative Tier
    1A record can establish its direct contents, but mechanistic, contested, generalized,
    evaluative, and Tier 1B-dependent conclusions require independent corroboration.
  - Classify every source as Tier 1A / 1B / 2 / 3 per bibtex-format.md.

CITATION AND TIER RULES — MANDATORY:
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]
  Use the embedded tier definitions and BibTeX format.

YOUR JOB

Verify or refute this claim with the highest available evidence tier.

Adversarial checklist:

- Find the primary source, not secondary reporting. If inaccessible, say so explicitly.
- Find at least one credible source challenging the claim. If none exists, document the searches.
- Check whether the evidence base is truly independent or sources cite each other.
- Identify whether the final report should state, downgrade, contest, or exclude the claim.

MANDATORY OUTPUT TABLE:

| Evidence type | Claim | Source | BibTeX key | Tier | Notes |
|---|---|---|---|---|---|
| FOR | | | | | |
| AGAINST | | | | | |

Primary source found: YES / NO / PARTIAL — [explain]

Confidence after verification: HIGH / MEDIUM / LOW / UNVERIFIED

Recommended handling in final report:
STATE AS FACT / FLAG AS UNCERTAIN / REPORT AS CONTESTED / EXCLUDE

Reasoning:
[1–3 sentences]

Source Acquisition Log:
[Every evidence-acquisition attempt and the result: search queries, databases or registries checked, direct URLs or documents reviewed, and failed acquisition attempts.]

Gaps Log:
[What was searched but not found.]
═══════════════════════════════════════════════════════════════════
```
