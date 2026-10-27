---
name: brainstorming
description: Use when exploring product ideas and framing problems before implementation. Covers problem framing, opportunities, and requirements discovery.
---

<HARD-GATE>
Do NOT invoke any implementation skill or take implementation actions until you have framed the problem, identified scope, and the user has approved a problem statement and approach.
</HARD-GATE>

## Anti-Pattern: "This Is Too Simple To Need Framing"
Every product idea benefits from clear framing. A small feature still needs assumptions checked. "Simple" ideas hide unclear needs.

## Workflow

Track these steps before starting — in whatever form the harness provides. Each step names the artifact that proves it.

- Explore context → context notes
- Stress-test needs → resolved or deferred questions
- Propose approaches/opportunities → options with trade-offs
- Frame the problem → approved problem statement
- Produce handoff artifact → PRD-ready doc for writing-plans
- Hand off → writing-plans in kiss-agentic-development

Complete them in order.

1. **Explore context** — understand domain, users, existing solutions, and constraints. Gather relevant context without jumping to solutions.

2. **Stress-test understanding** — clarify needs vs wants. Probe jobs to be done, context, and pain points. Load CONTEXT.md if exists and resolve terminology conflicts.

3. **Propose options** — present 2-3 approaches or opportunity framings with trade-offs and recommendation. Separate needs from solutions.

4. **Frame the problem** — define problem statement, affected users, constraints. Get user approval.

5. **Prepare handoff** — create PRD with problem statement, success criteria/metrics, prioritized scope (in/out), assumptions & risks, evidence. Follow the handoff convention in AGENTS.md.

**Terminal state**: hand off to kiss-agentic-development's `writing-plans` with the PRD artifact. No implementation skills.
