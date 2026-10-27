# kiss-agentic-product

Collection of AI agent skills focused on product management following the Double Diamond (Discover + Define). Develop and Deliver remain in kiss-agentic-development.

## Structure

```
├── instructions/
│   └── using-skills.md              # Global prompt to bias agents towards using skills
├── skills/                           # All skill directories (source of truth)
│   ├── [skill name]/
│   │   ├── SKILL.md
│   │   └── evals/evals.json
│   └── [skill name]-workspace/      # gitignored
├── migrations/
├── .opencode/
│   ├── skills/ → ../skills           # Symlink for native discovery
│   └── plans/                        # gitignored
├── AGENTS.md
└── CONTEXT.md
```

## Working with Skills

Skills are the unit of process. Load skills before acting when they apply.

### Skill authoring guidelines
- Name: lowercase, hyphens, gerund form required.
- Description: third person, lead with "Use when...", no workflow summary.
- Provider-agnostic: no provider-specific tool names or paths.
- Token-efficient: no tables/diagrams, flat structures, respect word count targets.
- Hooks over rules for open-field skills; narrow contracts keep enforced rules only when necessary.
- Cross-reference by skill name when needed.
- Progressive disclosure via reference files when detailed content grows.

### Handoff convention (no dedicated skill)
Product work in this framework produces artifacts consumable by kiss-agentic-development's `writing-plans`.

Required elements in the PRD/handoff artifact:
- Problem statement (user-centric)
- Success criteria/metrics (measurable)
- Prioritized scope (in/out)
- Assumptions & risks
- Evidence (themes/insights from discovery)

Process: product work → PRD following this structure → hand off to kiss-agentic-development → use `writing-plans`. No separate handoff skill.

### Eval philosophy
Skills assert process adherence and clear handoffs only. Outcome quality depends on model/harness and cannot be controlled via skills alone. Evals verify procedure followed and required artifacts produced, not correctness/quality of insights.
