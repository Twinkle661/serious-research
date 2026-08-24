# BibTeX Format and Citation Rules

## File Ownership

Research agents never write to global `sources.bib`.

- Loop 1 research agents write `loop1/sources_[DimensionName].bib`.
- Loop 2 research agents write `loop2/sources_[ThreadName].bib`.
- Loop 3 deep-dive agents write `loop3/sources_[ClaimSlug].bib`.
- Synthesis agents merge per-agent bib files into `sources.bib`.

## Merge Rules

Synthesis agents must:

- collect current-loop `sources_*.bib`;
- identify the same source by DOI first, then canonical URL, then normalized
  title + author or organization + year;
- treat BibTeX keys as labels, not source identity;
- merge duplicate records and retain the most complete non-conflicting fields;
- update an existing global entry when the new record is demonstrably more complete;
- if one key refers to two different sources, assign a new stable key rather than
  overwriting either source;
- append genuinely new sources;
- validate that every cited key resolves to exactly one global entry;
- log merged identities, updated entries, renamed collisions, and unresolved conflicts.

## Evidence Independence

A single authoritative Tier 1A record may directly establish only what that record
itself records: for example, the text of a judgment, a reported measurement, an enacted
rule, or a protocol provision. Label this basis `DIRECT AUTHORITATIVE RECORD`.

Independent corroboration is still required for:

- causal or mechanistic interpretations;
- contested factual claims;
- generalization beyond the record's scope;
- evaluative conclusions; and
- claims resting on an interested Tier 1B source.

Do not manufacture a redundant second citation where one authoritative record is the
fact being described. Do distinguish the record's contents from conclusions inferred
from it.

## Entry Format

Use stable, human-readable keys:

```bibtex
@article{AuthorYYYY_ShortTitle,
  author  = {Last, First and Last2, First2},
  title   = {Full title of the work},
  journal = {Journal or source name},
  year    = {YYYY},
  url     = {https://...},
  note    = {Accessed: YYYY-MM-DD. Tier: [1A|1B|2|3].
             Loop first cited: [1|2|3]. Supports claim: [brief claim description].}
}
```

For non-article sources, use `@misc`, `@report`, `@techreport`, or another appropriate BibTeX type.

## Source Tiers

Use these source tiers consistently. Do not merge Tier 1A and Tier 1B. A source can be primary and still self-interested.

- Tier 1A: neutral primary source — official filing, court/regulatory record, registry, raw dataset, peer-reviewed paper, protocol, direct transcript, or other source close to the evidence with limited promotional incentive.
- Tier 1B: self-interested primary source — company website, press release, investor deck, vendor documentation, sponsor-authored material, advocacy-group material, or direct statement from an interested party.
- Tier 2: independent secondary — journalism, analyst report, review, academic commentary, textbook, or independent expert synthesis.
- Tier 3: weak or unverified — single-source claim, opinion, unsourced summary, vendor/self-promotional claim without independent support, low-credibility page, or source of unknown provenance.

## In-Text Citation Style

Use BibTeX keys in square brackets during working drafts:

```text
The claim is stated here [AuthorYYYY_ShortTitle].
```

Do not cite a source in prose unless the corresponding BibTeX entry exists in either the agent's per-agent bib file or global `sources.bib`.

Understanding notes and final explanations should include enough readable source metadata to trace a claim back to its origin: author or organization, title, and date is sufficient. Full formal citation prose is not required. The purpose is traceability, not a bibliography.
