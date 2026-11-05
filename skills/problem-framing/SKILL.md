---
name: problem-framing
description: Use when exploring product ideas and framing problems before implementation. Covers problem framing, opportunities, and requirements discovery.
---

<HARD-GATE>
Do NOT invoke any implementation skill or take implementation actions until you have framed the problem, identified scope, and the user has approved a problem statement and approach.
</HARD-GATE>

## Anti-Pattern: "This Is Too Simple To Need Framing"
Every product idea benefits from clear framing. A small feature still needs assumptions checked. "Simple" ideas hide unclear needs.

## Skill chain

This skill orchestrates Discover + Define. Load the specialist skill at each step:

- Interviewing a human → `conducting-user-interviews` before the first question
- Turning evidence into opportunities → `discovering-opportunities`
- Testing a risky assumption → `prototyping-concepts`

Skipping a specialist is allowed only when its trigger is absent. State why in that step's artifact.

## Artifacts

Write these to the repo's short-term plans directory after confirming it is gitignored (for example `plans/discovery/`; add it to `.gitignore` if needed):

- `context-notes.md` — step 1
- `interview-notes.md` — step 2, only when a human is the evidence source
- `opportunities.md` — step 3
- `options.md` — step 4
- `prd-<slug>.md` — step 6, where `<slug>` is a kebab-case feature name

Each opportunity entry carries its need, job, evidence quote, theme, and confidence; evidence may come from research or documents, and an entry without a quote is marked as an assumption with low confidence rather than invented. A step is complete when its artifact exists; when step 2 has no human source, its resolved or deferred questions are recorded in `context-notes.md`. Step 4 also requires any triggered prototype's learnings and decision in `options.md`. Step 5 is complete when the user approves the problem statement, scope, and chosen approach.

## Workflow

Track these steps before starting — in whatever form the harness provides. Each step names the artifact that proves it.

1. **Explore context** — understand domain, users, existing solutions, and constraints. Gather relevant context without jumping to solutions. Write `context-notes.md`.

2. **Stress-test understanding** — clarify needs vs wants. Probe jobs to be done, context, and pain points. Load the repo glossary `CONTEXT.md` if it exists and resolve terminology conflicts. When a human is the evidence source, load `conducting-user-interviews` before the first question and write quotes and observations to `interview-notes.md`.

3. **Find opportunities** — load `discovering-opportunities`. Turn evidence into jobs, needs, and themes in `opportunities.md`, using the five fields above. Separate needs from solutions.

4. **Propose options** — present 2-3 approaches or opportunity framings with trade-offs and a recommendation. Record them in `options.md`. Load `prototyping-concepts` when an assumption needs a cheap test before specification; record prototype learnings and the go/no-go decision in `options.md`.

5. **Frame the problem** — define problem statement, affected users, constraints, and scope (in/out). Scope is the prioritization mechanism: decide what is in and what is out; do not rank a backlog. Get user approval of the problem statement, scope, and chosen approach.

6. **Prepare handoff** — create the PRD at `prd-<slug>.md` with the approved problem statement, chosen approach, evidence, success criteria/metrics, prioritized scope (in/out), assumptions & risks. Follow the handoff convention in AGENTS.md.

**Terminal state**: hand off to kiss-agentic-development's `writing-plans` with the PRD artifact. No implementation skills.
