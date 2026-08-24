# Brief Template — 1B Research Sub-Agent

Use this template for Loop 1 research agents. For Loop 2 non-red-flag agents, reuse this template with the Loop 2 modifications listed at the end.

Fill every bracketed field before spawning. The brief must be self-contained.

```text
═══════════════════════════════════════════════════════════════════
RESEARCH SUB-AGENT BRIEF — LOOP [1 or 2]
(Part of: serious-research skill)
═══════════════════════════════════════════════════════════════════
RESEARCH BRIEF (full text):
[paste entire contents of research_brief.md]

YOUR DIMENSION / THREAD:
[DIMENSION OR THREAD NAME]

SAFE FILE SLUG:
[SafeSlug from the plan; do not derive a different slug]

YOUR SPECIFIC QUESTIONS:
  1. [question]
  2. [question]
  3. [question]

INPUT FILES TO READ:
  [Loop 1: none]
  [Loop 2: <WORKFLOW_DIR>/loop1/findings_[RelevantDimension].md]

OUTPUT FILE TO WRITE:
  <WORKFLOW_DIR>/loop[1 or 2]/findings_[SafeSlug].md

BIB FILE TO WRITE:
  <WORKFLOW_DIR>/loop[1 or 2]/sources_[SafeSlug].bib

Do not append to global sources.bib. Synthesis agents merge bib files.

APPROVED CAPABILITIES:
  web search, browser navigation, workflow file read/write, and read access to the
  resolved skill-resource locator supplied below.
  Use these capabilities as needed. There is no restriction on search volume within reason.

WORKSPACE CONFINEMENT:
  All file writes — including temporary scripts, downloaded pages, HTML caches, and any
  other intermediate artifacts — must use absolute paths under <WORKFLOW_DIR>. No file may
  be written to the agent's current working directory, /tmp, or any location outside
  <WORKFLOW_DIR>. If a temporary helper file is needed, write it under <WORKFLOW_DIR>/tmp/.

RESOLVED SKILL RESOURCE:
  bibtex-format: [host-native locator resolved by the orchestrator]

PORTABLE EVIDENCE RULES:
  Tier 1A = neutral primary; Tier 1B = interested primary; Tier 2 = independent
  secondary; Tier 3 = weak or unverified. A source directly supports only what it
  actually establishes. Causal, contested, generalized, evaluative, and
  Tier-1B-dependent claims require independent corroboration. Write citations as
  stable BibTeX keys and write only to your assigned per-agent bibliography.

YOUR CORE TASK: research then write to file.
  Research your assigned dimension, then write ALL findings to the output file above.
  Do not summarise findings in memory. Do not stop at reading. Write the file.
───────────────────────────────────────────────────────────────────
INSTRUCTIONS

RESEARCH METHODOLOGY — MANDATORY:

Search scale:
  - Single isolated fact or narrow verification → 1–2 queries.
  - General question or moderate-scope topic → 3–7 queries.
  - Multi-dimensional or comprehensive topic → follow the multi-dimensional flow below.

Query construction:
  Prefer concise keyword queries when they preserve precision. Use quoted phrases,
  identifiers, exact titles, longer queries, or natural-language questions when
  required to disambiguate technical, legal, philosophical, or source-specific searches.
  Before constructing any query, run these pre-flight checks in order:
    1. Review prior findings files and conversation context. Is this task a continuation of a previous search thread? If so, build on what is already known.
    2. Assess whether the query is ambiguous. Short queries under 5 words are especially prone to ambiguity.
    3. If the query is ambiguous and context does not allow a reasonable inference, stop and ask for clarification before searching.

Multi-dimensional / comprehensive topics:
  1. Execute 1–2 broad exploratory queries first (e.g. "[topic] overview", "[topic] key considerations", "[topic] categories").
     Goal: discover the actual structure of the topic. Do not aim to "find answers" — aim to surface unknown dimensions.
  2. From broad results, extract a sub-dimension list. Merge with prior knowledge. Deduplicate. Write the list out explicitly before proceeding.
  3. Construct one focused query per sub-dimension. Queries must be substantively distinct — no overlap in intent.
  4. Before executing, verify: no overlap between queries / no dimension omitted / together they cover the full original question.

Checking results after each batch:
  1. Coverage check — which sub-dimensions now have adequate coverage? Which are still missing or thin? Continue querying uncovered dimensions.
  2. Unexpected dimensions check — did results reveal angles not in your original list? If yes, add them to the list and append targeted queries.

Source evaluation:
  - For important results, attempt to retrieve the full text. Do not draw conclusions from titles or abstracts alone.
  - Evaluate source credibility: institutional affiliation, publication date, author expertise, declared interests.
  - Apply the Evidence Independence rules in bibtex-format.md. One authoritative Tier
    1A record may establish only what it directly records; causal, contested,
    generalized, evaluative, and Tier 1B-dependent conclusions require independent
    corroboration.
  - Classify every source as Tier 1A / 1B / 2 / 3 per bibtex-format.md.

CITATION AND TIER RULES — MANDATORY:
  [ORCHESTRATOR: paste the applicable rules loaded from references/bibtex-format.md
  here before spawning. Do not leave this placeholder in the final brief.]
  Use the embedded tier definitions and BibTeX format. Do not use a different tier scheme.

Priority this loop:
  [Loop 1: BREADTH over depth. Cast wide. Find all major sources, narratives, and data points.]
  [Loop 2: DEPTH over breadth. Focus on the assigned thread, fill gaps, and avoid duplicating Loop 1.]

SOURCE ACQUISITION LOG is mandatory. At the top of your output, list every evidence-acquisition attempt, not only web searches:
  Search query: "[exact search string]" → [brief result]
  Database / registry checked: [name] → [brief result]
  Direct URL / document checked: [URL or file] → [brief result]
  Failed acquisition attempt: [what was attempted] → [nothing found / low quality / inaccessible]

For each major finding, record:
  - Claim: [specific claim, not vague paraphrase]
  - Source: [Author/Org, Title, URL or reference, publication date]
  - BibTeX key: [AuthorYYYY_ShortTitle]
  - Tier: [1A / 1B / 2 / 3 — as defined in bibtex-format.md]
  - Independence flag: whether this source appears to rely on another cited source

Also record explicitly:
  - what you searched for but could not find;
  - claims appearing in many places but tracing to a single origin;
  - inconsistent, anomalous, or surprising points;
  - direct contradictions.

MINIMUM OUTPUT STANDARD:
  ✓ normally at least 5 distinct claims with sources; fewer is acceptable only for a
    genuinely narrow dimension with an explicit completeness justification
  ✓ at least 1 Tier 1A neutral primary source attempted; document if not found
  ✓ Tier 1B self-interested primary sources are labeled separately and not treated as neutral corroboration
  ✓ at least 3 different sources used, not all from the same outlet
  ✓ Source Acquisition Log present
  ✓ Gaps Log present and non-empty

OUTPUT FORMAT:

# Findings: [Dimension or Thread Name] — Loop [1 or 2]
**Agent**: Research Sub-Agent
**Date**: [date]

## Source Acquisition Log
| Acquisition Type | Query / Source / Attempt | Result |
|---|---|---|
| Search query | "[query]" | [result] |
| Database / registry | [name] | [result] |
| Direct URL / document | [URL or file] | [result] |

## Findings
[numbered list; each item includes Claim / Source / BibTeX key / Tier / Independence flag]

## Contradictions Found
[conflicting claims within this dimension or thread]

## Gaps Log
[what was searched but not found; what should exist but does not]

## Notes for Synthesis
[convergences, suspicious patterns, weak evidence, useful leads]
═══════════════════════════════════════════════════════════════════
```

## Loop 2 Non-Red-Flag Modifications

When adapting this template for `[+]`, `[~]`, or `[ ]` Loop 2 tasks:

- Change the title to `RESEARCH SUB-AGENT BRIEF — LOOP 2`.
- Change the priority note to depth over breadth.
- Replace Loop 1 input with the most relevant Loop 1 findings file.
- Set output file to `loop2/findings_[ThreadName].md`.
- Set bib file to `loop2/sources_[ThreadName].bib`.
- Add: "Read Loop 1 only for context. Do not duplicate; go deeper, verify, or fill gaps."
