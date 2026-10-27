# Keep it Short and Simple Agentic Product Framework

A library of product management skills that enforce a Discover/Define workflow using the Double Diamond framework. One agent, a library of skills — keep it short and simple.

Drop them into any coding agent — OpenCode, Claude Code, Cursor — and the agent will leverage skills to follow product discovery and definition practices instead of guessing. This repo covers Discover and Define; Develop and Deliver remain in [kiss-agentic-development](https://github.com/MarcosX/kiss-agentic-development).

## Table of Contents

- [How it works](#how-it-works)
- [Double Diamond](#double-diamond)
- [Skills](#skills)
- [Installation](#installation)
- [Using the skills](#using-the-skills)
- [Handoff convention](#handoff-convention)
- [Contributing](#contributing)

## How it works

This framework enforces skill-first workflows for product work. Every session starts with a global instruction to check for applicable skills before acting. The agent must load and follow skills when they apply.

Skills provide tight workflows with clear reasoning. Some skills use hooks (cognitive reframes with observable completion bars) for open-field work, while others keep enforced rules where contracts matter. Skills are agent-first: flat structure, concise prose, provider-agnostic, no visual formatting that wastes tokens.

## Double Diamond

The Double Diamond splits product and development work:

- **Discover + Define** (this repo): Understand users and problems, frame opportunities, validate assumptions, and produce a clear handoff.
- **Develop + Deliver** ([kiss-agentic-development](https://github.com/MarcosX/kiss-agentic-development)): Plan implementation, execute with tests, review, and deliver.

## Skills

Every session is gated by the [global using-skills instruction](instructions/using-skills.md) that forces the agent to find and invoke the right skill before doing anything else.

Product workflow follows Discover → Define:

- `brainstorming` — Explore ideas and frame problems before implementation. Produces a handoff-ready problem statement and scope.
- `discovering-opportunities` — Identify user needs and opportunities through JTBD-focused research. Stays in problem space, separates needs from solutions, captures evidence and themes.
- `conducting-user-interviews` — Plan and conduct conversational discovery interviews. Uses open-ended questions, probes jobs/context/pain points, and synthesizes insights into themes with evidence.
- `prioritizing-opportunities` — Prioritize opportunities using explicit criteria with rationale and trade-offs. Documents reasoning for ranking decisions.
- `prototyping-concepts` — Validate hypotheses with the cheapest way to learn (low-fi first). Focuses on testing assumptions, not polish, and captures learnings for go/no-go decisions.

## Installation

### With `npx skills`
```bash
npx skills add MarcosX/kiss-agentic-product
```

### Manual: clone the repo
```bash
git clone https://github.com/MarcosX/kiss-agentic-product.git
```

### OpenCode
Symlink or copy `skills/` to your OpenCode skills location. The repo includes `.opencode/skills -> ../skills` for local discovery.

### Claude Code
Add the repo to your Claude Code skills path, or copy skills as needed.

### Cursor
Copy `skills/` into your Cursor skills configuration.

## Using the skills

1. Install the skills in your agent environment.
2. Ensure the global using-skills instruction is loaded (mirrors the pattern in kiss-agentic-development).
3. When working on product discovery/definition, the agent will automatically load the appropriate skill based on the task.
4. Follow the skill workflow - skills guide process and produce concrete artifacts (evidence, themes, problem statements, PRDs).

## Handoff convention

Product work produces artifacts consumable by [kiss-agentic-development](https://github.com/MarcosX/kiss-agentic-development)'s `writing-plans`. No dedicated handoff skill - it's a convention.

Required elements in the PRD/handoff artifact:
- Problem statement (user-centric)
- Success criteria/metrics (measurable)
- Prioritized scope (in/out)
- Assumptions & risks
- Evidence (themes/insights from discovery)

Process: product work in this repo → PRD following the structure → hand off to kiss-agentic-development → use `writing-plans`.

## Contributing

Follow the guidelines in [AGENTS.md](AGENTS.md). Skills must be provider-agnostic, token-efficient, follow naming conventions (gerund form, third-person descriptions), and include evals in `evals/evals.json`.
