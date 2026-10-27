# PRD: kiss-agentic-product

## Problem Statement

Create a parallel skill framework (`kiss-agentic-product`) that focuses on product management capabilities following the Double Diamond product development framework. Discover and Define should live in this framework, while Develop and Deliver remain in `kiss-agentic-development`. The framework must follow the same conventions, philosophy, and constraints as this repository (skill-first workflows, hooks over rules where appropriate, provider-agnostic, token-efficient, progressive disclosure). An agent will pick up this PRD in an empty directory and need to bootstrap the entire repository from scratch.

## Solution

Create `kiss-agentic-product` as a separate repository with mirrored structure and conventions from `kiss-agentic-development`. Move `brainstorming` from the development framework to the product framework (as it is pre-development exploration and design framing). Define a convention-based handoff (PRD → `writing-plans` in `kiss-agentic-development`) rather than a dedicated handoff skill. Start with a minimal, composable initial skill set and leave optional capabilities out of scope for now. Assert only process adherence and clear handoffs via skills - outcome quality cannot be controlled by skills alone.

## User Stories

1. US-1: As a framework consumer, I want `kiss-agentic-product` to follow Double Diamond (Discover + Define) so that product work is separated from development work (Develop + Deliver stay in `kiss-agentic-development`).
2. US-2: As a framework consumer, I want `brainstorming` moved to the product framework so that exploration/design framing happens in the product domain.
3. US-3: As a framework consumer, I want a convention-based handoff (PRD → `writing-plans`) so that there is no new handoff skill, just documented conventions.
4. US-4: As a framework consumer, I want the repo bootstrapped from this PRD in an empty directory so that an agent can create all necessary files/dirs/symlink.
5. US-5: As a framework consumer, I want a minimal initial skill set (brainstorming, discovering opportunities, conducting user interviews, prioritizing opportunities, prototyping concepts) that can be folded/trimmed so that the framework starts small. Framing problems overlaps with brainstorming and is not needed as separate skill. Metrics, backlog management, reporting insights are deferred to a later pass.
6. US-6: As a framework consumer, I want the framework to follow all repo guidelines (naming, third-person descriptions, gerund form, hooks over rules, provider-agnostic, token-efficient, progressive disclosure, no tables/diagrams, etc.) so that it is compatible with `skill-creator` and any coding agent.
7. US-7: As a framework consumer, I want skill evals to only assert process adherence and clear handoffs so that we don't claim to control outcome quality.

## Implementation Decisions

- US-1, US-2: **Split by Double Diamond** - Move `brainstorming` skill to `kiss-agentic-product`. Keep `writing-plans`, `executing-plans`, `practicing-tdd`, `reviewing-code`, `debugging` in `kiss-agentic-development`. Chosen because brainstorming is pre-implementation exploration/design framing (product/domain work) rather than implementation planning/execution.
- US-3: **Convention over skill** - Document handoff as convention: product framework produces a PRD (following product conventions) that `kiss-agentic-development`'s `writing-plans` consumes. No `handing-off-to-development` skill. Chosen because the user explicitly requested no skill, just convention documents (e.g. PRD → writing-plans).
- US-4: **Bootstrap instructions required** - PRD must include explicit bootstrap section for empty repo: create directory structure, `AGENTS.md` (with skill-first instructions mirroring `kiss-agentic-development`), `instructions/using-skills.md`, `CONTEXT.md` (product glossary), `.opencode/skills/` symlink to `../skills`, `migrations/` (if needed), and initial skill directories. Chosen because agent will pick up PRD in empty dir.
- US-5: **Start small, composable** - Initial skills: `brainstorming` (moved), `discovering-opportunities` (JTBD-focused), `conducting-user-interviews` (conversational discovery), `prioritizing-opportunities` (explicit criteria with rationale), `prototyping-concepts` (progressive low-fi to high-fi/working code reference). `framing-problems` overlaps with brainstorming (not separate). `defining-metrics`, `managing-backlog`, `reporting-insights` deferred to later pass. Each should be foldable - if too granular, merge; if not needed, leave optional/out of scope. Chosen because user wants to start small and avoid over-scoping.
- US-6: **Mirror all guidelines** - Follow naming (lowercase, hyphens, gerund), third-person descriptions starting with "Use when...", hooks over rules by default for open-field skills, provider-agnostic (no tool names/paths), token-efficient (<650 words general, <300 meta), progressive disclosure, flat structures, no tables/diagrams, cross-reference by skill name with requirement markers if needed, evidence-backed TODO blocks only when step has no self-proving prose, etc. Reference relevant files from `kiss-agentic-development`: `AGENTS.md` (structure/conventions), `skills/writing-plans/SKILL.md` (plan structure), `skills/brainstorming/SKILL.md` (process patterns), `CONTEXT.md` (terminology). Chosen because required to follow same guidelines.
- US-7: **Eval philosophy** - Process adherence and clear handoffs are the only things assertable. Document this explicitly. Evals should check procedure followed, artifacts produced in expected form (e.g. problem statement exists, prioritization criteria used, handoff artifacts present), not outcome quality. Chosen because quality depends on model/harness and cannot be controlled via skills alone.

## Testing Decisions

- **Process adherence focus**: Tests should verify skills produce expected artifacts and follow procedure (e.g. interview plan created, insights synthesized into themes, problem statement written, priorities scored with stated criteria, handoff doc/PRD structure present). Not subjective quality.
- **Handoff clarity**: Verify convention is documented and that product artifacts can be consumed by `writing-plans` (structure compatible - problem statement, success criteria/metrics, scope, assumptions/risks).
- **Bootstrap verification**: Verify bootstrap instructions are complete and unambiguous for empty repo.
- **Guideline compliance**: Run `skill-creator`'s `scripts/quick_validate.py` on all skills (frontmatter, naming). Ensure no provider-specific references, no tables/diagrams, descriptions follow rules.
- **Tie to stories**: US-1/US-2 (separation) - verify structure; US-3 (handoff) - verify convention doc exists; US-4 (bootstrap) - verify bootstrap section; US-5 (skills) - verify minimal set present; US-6 (guidelines) - verify compliance checks; US-7 (eval philosophy) - verify documented.

## Out of Scope

- **Develop/Deliver capabilities**: Implementation planning/execution/testing/review remain in `kiss-agentic-development`. Not ported.
- **Handoff skill**: No dedicated skill for handoff - convention only.
- **Full PM toolkit**: Market research depth, competitive analysis frameworks, go-to-market, pricing strategy, etc. Start minimal and fold.
- **Outcome quality metrics**: Cannot be asserted by skills; explicitly out of scope.
- **Monorepo integration**: Separate repo only.
- **Tool-specific implementations**: Must remain provider-agnostic.

## Further Notes

### Repo structure (mirror)
```
kiss-agentic-product/
├── instructions/
│   └── using-skills.md              # mirroring kiss-agentic-development/instructions/using-skills.md
├── skills/
│   ├── brainstorming/               # moved from development
│   ├── discovering-opportunities/
│   ├── conducting-user-interviews/
│   ├── prioritizing-opportunities/
│   ├── prototyping-concepts/
│   └── [*-workspace/ gitignored]
├── migrations/
├── .opencode/
│   ├── skills/ → ../skills
│   └── plans/ (gitignored)
├── AGENTS.md                        # skill-first instructions
└── CONTEXT.md                       # product-specific glossary
```

### Bootstrap instructions (for agent in empty dir)
1. Create directory structure as above
2. Copy/adapt `instructions/using-skills.md` from `kiss-agentic-development` (respecting provider-agnostic requirements)
3. Create `AGENTS.md` with skill-first workflow instructions mirroring this repo's approach
4. Create `CONTEXT.md` with product glossary (Double Diamond, Discover/Define, handoff convention, hooks vs rules as applicable)
5. Create `.opencode/skills/` symlink pointing to `../skills`
6. Create skill directories with `SKILL.md` (frontmatter name/description) and `evals/evals.json` for each initial skill
7. Move/adapt `brainstorming` skill from `kiss-agentic-development/skills/brainstorming/` to `kiss-agentic-product/skills/brainstorming/` (update any dev-specific references to be product-appropriate or make provider-agnostic)
8. Create other initial skills following guidelines (discovering-opportunities, conducting-user-interviews, prioritizing-opportunities, prototyping-concepts)
9. Document handoff convention in `AGENTS.md` or a conventions doc (PRD → `writing-plans` in kiss-agentic-development)
10. Create `README.md` explaining the framework (Double Diamond split, Discover/Define vs Develop/Deliver, skill flow, handoff convention, how to use)
11. Add `.gitignore` for workspaces/plans as appropriate

### Handoff convention (document, no skill)
Product framework outputs must be consumable by `kiss-agentic-development`'s `writing-plans`. Document in conventions:
- Handoff artifact: PRD (or equivalent design doc) following clear structure
- Required elements: problem statement (user-centric), success criteria/metrics (measurable), prioritized scope (in/out), assumptions & risks, evidence (themes/insights)
- Process: product work produces PRD → hand off to dev framework → use `writing-plans` (which expects clear requirements/ACs)
- No dedicated handoff skill - just convention

### Initial skill definitions (guidance)
All must follow: gerund name, third-person, "Use when..." trigger, no workflow summary in description, <650 words body. Hooks over rules for open-field skills. Provider-agnostic.

- `brainstorming`: Use when exploring product ideas and framing problems before implementation. Moved from development framework; adapt to product context as needed while keeping structure compatible with existing process.
- `discovering-opportunities`: Use when identifying user needs and opportunities through JTBD-focused research and ideation before defining solutions. Stay in problem space; separate needs from solutions; capture evidence for each opportunity.
- `conducting-user-interviews`: Use when planning and conducting conversational discovery interviews to understand jobs, context, and pain points. Focus on open-ended questions, active listening, and synthesizing insights into themes with evidence.
- `prioritizing-opportunities`: Use when prioritizing opportunities using explicit criteria with rationale and trade-offs. Make criteria explicit, score consistently, document why items rank as they do.
- `prototyping-concepts`: Use when validating hypotheses about solutions. Start with the cheapest/fastest way to learn (low-fi) to get agreement, then progress to higher fidelity or working code as a reference for implementation. Focus on testing assumptions, not polish.

### References to this repo
- `AGENTS.md` - structure, skill-first workflow, conventions, eval guidance
- `skills/writing-plans/SKILL.md` - plan structure, ACs, handoff expectations
- `skills/brainstorming/SKILL.md` - process patterns to adapt
- `CONTEXT.md` - terminology (hooks/rules, open-field/narrow-bridge, evidence-backed TODOs)
- `instructions/using-skills.md` - skill-first instructions to mirror

### Eval philosophy (explicit)
Skills assert process adherence and clear handoffs only. Outcome quality depends on model/harness and cannot be controlled via skills alone. Evals should verify procedure followed and required artifacts produced, not correctness/quality of insights.

## Self-review

reviewed, no findings
