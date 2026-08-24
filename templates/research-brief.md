# Template — Phase 0 Research Brief

Use this during Phase 0. The Research Brief is the constitution for all sub-agents.

## Clarification Questions

Ask these questions. Defaults may be applied if the user gives partial answers, except
subject and the resolved workflow directory are required.

1. Subject: What exactly is being researched?
   - Required. Do not proceed without this.

2. What do you want to understand?
   - Not "what do you want to know" — but what kind of understanding are you after?
   - Options: mechanism (how does it work), causal structure (what causes what and why), landscape (what exists and how it relates), evaluation (comparing competing frameworks or claims), or other.
   - Default: mechanism.

3. Current Knowledge: What do you already understand? Where are your gaps?
   - What are your current mental models or priors on this subject?
   - What do you suspect but haven't confirmed?
   - What specific parts feel like a black box?
   - Default: no prior context.

4. Key Questions: What are the 3–5 most important questions this research must answer?
   - These should be questions whose answers would constitute genuine understanding, not just facts.
   - Default: generate 3–5 questions from subject and understanding goal, then ask user to confirm.

5. Scope:
   - time period;
   - geography;
   - depth: executive overview / medium / exhaustive.
   - Default depth: medium.
   - Time and geography defaults must fit the subject:
       current landscape = last 5 years, relevant jurisdictions;
       historical or conceptual = no automatic date cutoff;
       scientific mechanism = foundational sources plus current reviews;
       legal or regulatory = current law plus necessary legislative history.
     If none fits, use no time or geography restriction and disclose that assumption.
   - Depth controls how many research loops run:
       executive overview = Loop 1 only
       medium = Loops 1–2
       exhaustive = Loops 1–3 (includes deep verification and understanding audit)

6. Workflow location:
   - Check the system prompt and memory first.
   - If either supplies a location, obey it as the default. System instructions
     take precedence over memory when they differ.
   - Show the resulting absolute workflow directory to the user and ask for
     confirmation even when the default came from the system prompt or memory.
   - If neither supplies a location, ask the user, resolve the answer to an
     absolute filesystem path, show it, and ask for confirmation.
   - Do not create workflow files or spawn sub-agents before confirmation.
   - Record the confirmed absolute path and substitute it for every
     `<WORKFLOW_DIR>` in every sub-agent brief.

## Research Brief Output

Save as `<WORKFLOW_DIR>/research_brief.md`.

```markdown
# Research Brief — [Subject]

## Subject
[Exact subject.]

## Understanding Goal
[What kind of understanding is sought: mechanism / causal structure / landscape / evaluation / other.]

## Current Knowledge and Starting Point
[What the user already understands. Existing mental models or priors. Known gaps and black boxes. If none stated, write "none provided".]

## Key Questions
1. [Q1]
2. [Q2]
3. [Q3]
4. [optional Q4]
5. [optional Q5]

## Scope
- Time period: [time period]
- Geography: [geography]
- Depth: [executive overview / medium / exhaustive]
- Loops to run: [1 / 1–2 / 1–3]

## Environment Discovery
- Delegation mechanism: [host capability or unknown]
- Available profiles: [list or unknown]
- Maximum usable concurrency: [number or unknown]
- Skill-resource loader: [host capability or skill-relative local files]
- Resolved skill-resource locator map: [resource name → concrete host-native locator]
- Web search and browser navigation: [available / restricted / unavailable]
- Workflow file read/write: [host capability]
- Path style: absolute filesystem

## Workflow Directory
- Default source: [system prompt / memory / user-provided]
- User confirmed: [yes, with confirmation date/time]
- Absolute workflow directory: [normalized absolute filesystem path]

## Defaults Applied
[List any defaults applied.]

## Blocking Requirements
[Any non-negotiable sources, jurisdictions, languages, exclusions, or constraints.]
```

After drafting, ask the user to confirm or correct the brief before proceeding.
