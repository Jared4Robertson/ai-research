# Repository as Context

**Summary**: The principle that an agent's only persistent memory is what's accessible in its context window — so everything it needs must live in the repository, not in people's heads, chat threads, or external docs.

**Sources**: raw/Harness engineering leveraging Codex in an agent-first world.md, raw/Effective harnesses for long-running agents.md

**Last updated**: 2026-04-18

---

From the agent's point of view, anything it can't access in-context while running effectively doesn't exist. This has a concrete implication: knowledge that lives in Slack discussions, meeting notes, Google Docs, or people's heads is illegible to the agent — in the same way it would be unknown to a new hire joining three months later.

The corollary: the repo must be the system of record for everything the agent needs to make good decisions.

## What belongs in the repo

- Architecture decisions and the reasoning behind them
- Product principles, engineering norms, design beliefs
- Feature requirements and their pass/fail status
- Progress logs and session handoff notes
- Reference documentation for tools and libraries the agent uses
- Quality grades, technical debt tracking
- Active and completed execution plans

## What this looks like in practice

**[[harness-engineering]] (OpenAI):** A structured `docs/` directory with design docs, exec plans, product specs, and references. `AGENTS.md` is a ~100-line table of contents. A "doc-gardening" agent runs on a schedule to scan for stale documentation and open fix-up PRs. Linters and CI jobs verify the knowledge base is up to date and cross-linked. (source: raw/Harness engineering leveraging Codex in an agent-first world.md)

**[[long-running-agents]] (Anthropic):** A `claude-progress.txt` progress file and `feature_list.json` provide session-to-session continuity. Git commit history serves as a structured log of what changed and why. An `init.sh` script ensures every session can immediately verify the app is in a working state. (source: raw/Effective harnesses for long-running agents.md)

## The map vs. encyclopedia problem

Making the repo the system of record does not mean dumping everything into a single file. Both sources independently discovered that monolithic instruction files (one big `AGENTS.md`, one big prompt) fail:

- Context is scarce — large files crowd out the task and relevant code
- When everything is "important," nothing is; agents pattern-match locally
- Monolithic files rot and drift; agents can't tell what's still true

The solution in both cases: a short, stable entry point (table of contents, progress file) that teaches the agent *where to look next* — progressive disclosure rather than upfront overwhelm.

## Relation to [[program-md-pattern]]

[[program-md-pattern]] (from [[autoresearch]]) is the same principle applied to scientific research: the human maintains a `program.md` that steers the agent's research direction, while the agent maintains the training code. The repo (and `program.md` within it) is the only persistent shared state.

## Related pages

- [[agent-harness]]
- [[harness-engineering]]
- [[long-running-agents]]
- [[program-md-pattern]]
