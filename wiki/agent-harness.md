# Agent Harness

**Summary**: The scaffolding, tooling, and environment design that allows autonomous agents to do reliable, sustained work — the environment a human engineer builds so agents can execute effectively.

**Sources**: raw/Harness engineering leveraging Codex in an agent-first world.md, raw/Effective harnesses for long-running agents.md

**Last updated**: 2026-04-18

---

As coding agents take on more of the software lifecycle, the primary engineering challenge shifts from writing code to building the environment in which agents operate. A harness is the collection of scaffolding, feedback loops, tooling, and conventions that constrain and enable agent behavior.

## The core insight

From both [[harness-engineering]] (OpenAI) and [[long-running-agents]] (Anthropic): **an agent's only memory is what's in its context window.** Everything it needs — architecture decisions, feature requirements, progress state, coding conventions — must be encoded in a form it can read. If it lives in Slack, a person's head, or a Google Doc, it doesn't exist to the agent.

This reframes the engineer's job: design environments, specify intent, build feedback loops. Humans steer; agents execute.

## Two perspectives on harness design

| Concern | OpenAI approach ([[harness-engineering]]) | Anthropic approach ([[long-running-agents]]) |
|---|---|---|
| Knowledge store | [[repository-as-context\|Repo as system of record]], AGENTS.md as map | Progress file + git history per session |
| Task scope | Agents drive PRs end-to-end | One feature per session |
| Architecture enforcement | Mechanical linters, layer constraints | Feature list JSON, incremental commits |
| Testing | Agent-legible observability (LogQL/PromQL, DevTools) | Browser automation (Puppeteer MCP) |
| Drift/entropy | Recurring cleanup agents ("garbage collection") | Clean-state commits at session end |

## Shared principles

- **[[repository-as-context]]**: the repo is the agent's only persistent memory
- **Progressive disclosure**: give agents a map (AGENTS.md, progress file), not an encyclopedia
- **Mechanical enforcement over documentation**: invariants encoded in linters outlast instructions in markdown
- **Incremental progress**: agents working on bounded, well-defined tasks outperform agents attempting to one-shot complex goals
- **End-to-end testing**: agents need tools that let them verify behavior as a user would — browser automation, running the actual app

## Related pages

- [[harness-engineering]]
- [[long-running-agents]]
- [[repository-as-context]]
- [[program-md-pattern]]
- [[autoresearch]]
