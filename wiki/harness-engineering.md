# Harness Engineering

**Summary**: OpenAI's case study of building a ~1M line product with 0 manually-written code using Codex over 5 months — lessons in designing environments for autonomous agents.

**Sources**: raw/Harness engineering leveraging Codex in an agent-first world.md

**Last updated**: 2026-04-18

---

Published March 11, 2026 by Ryan Lopopolo (OpenAI). A team of 3 engineers (later 7) built an internal product with no manually-written code. Every line — application logic, tests, CI, documentation, observability, internal tooling — was written by Codex agents using GPT-5. Throughput: ~3.5 PRs/engineer/day across ~1,500 merged PRs. The team estimates 1/10th the time of hand-written code. (source: raw/Harness engineering leveraging Codex in an agent-first world.md)

## The no-manual-code constraint

This was an intentional design choice, not just an outcome. By committing to never writing code by hand, the team was forced to build what was actually needed to increase engineering velocity by orders of magnitude. When something failed, the fix was never "try harder" — it was: *what capability is missing, and how do we make it legible and enforceable for the agent?*

## AGENTS.md as map, not encyclopedia

Early attempts at a single large `AGENTS.md` failed in predictable ways:
- Context is a scarce resource — a giant instruction file crowds out task, code, and relevant docs
- Too much guidance becomes non-guidance; agents pattern-match locally rather than navigate intentionally
- It rots instantly; agents can't tell what's still true
- It's hard to verify mechanically

Solution: `AGENTS.md` is ~100 lines — a table of contents pointing to a structured `docs/` directory. This is [[repository-as-context]] in practice. See also [[program-md-pattern]] for the analogous pattern in research contexts.

## Application legibility

A key bottleneck was human QA capacity. The solution was making the app itself legible to Codex:
- App bootable per git worktree so Codex can run one isolated instance per change
- Chrome DevTools Protocol wired into agent runtime — DOM snapshots, screenshots, navigation
- Ephemeral observability stack per worktree: logs (LogQL) and metrics (PromQL) visible to agent
- Single agent runs of 6+ hours (while humans sleep) became routine

Prompts like "ensure service startup completes in under 800ms" or "no span in these four critical user journeys exceeds two seconds" became tractable once the agent had these tools. (source: raw/Harness engineering leveraging Codex in an agent-first world.md)

## Architecture enforcement

Documentation alone doesn't keep an agent-generated codebase coherent. The team enforced invariants mechanically:
- Rigid layered architecture per business domain: Types → Config → Repo → Service → Runtime → UI
- Strictly validated dependency directions via custom Codex-generated linters
- "Taste invariants": structured logging, naming conventions, file size limits — all custom lints with remediation instructions in error messages
- Principle: enforce boundaries centrally, allow autonomy locally

This level of architectural rigor is usually deferred until a team has hundreds of engineers. With agents, it's an early prerequisite — the constraints are what enable speed without decay.

## Garbage collection

Full agent autonomy introduces drift: Codex replicates existing patterns, including suboptimal ones. Initially the team spent every Friday (20% of the week) cleaning up manually. Instead:
- "Golden principles" encoded directly into the repo: opinionated mechanical rules for legibility and consistency
- Recurring background Codex tasks scan for deviations, update quality grades, open targeted refactoring PRs
- Most refactoring PRs can be reviewed in under a minute and automerged

Technical debt treated like a high-interest loan: pay it down continuously in small increments rather than compounding bursts. (source: raw/Harness engineering leveraging Codex in an agent-first world.md)

## End-to-end autonomy (current state)

Given a single prompt, Codex can now: validate codebase state → reproduce a bug → record a video of the failure → implement a fix → validate the fix → record a second video → open a PR → respond to feedback → detect and remediate build failures → escalate to human only when judgment is required → merge.

This depends on the specific structure and tooling of this repo and should not be assumed to generalize without similar investment.

## Related pages

- [[agent-harness]]
- [[repository-as-context]]
- [[long-running-agents]]
- [[program-md-pattern]]
