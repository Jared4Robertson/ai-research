# Long-Running Agents

**Summary**: Anthropic's patterns for enabling agents to make consistent progress across multiple context windows, using an initializer agent and structured session handoff artifacts.

**Sources**: raw/Effective harnesses for long-running agents.md

**Last updated**: 2026-04-18

---

Published by Anthropic (Justin Young et al.). The core problem: agents work in discrete sessions, and each new session begins with no memory of what came before. Like engineers working in shifts with no handoff notes, an agent starting fresh has to guess at what happened — and often guesses wrong.

Compaction alone (the Claude Agent SDK's built-in context management) isn't sufficient. Even Opus 4.5 given a high-level prompt like "build a clone of claude.ai" will fail across multiple context windows without additional structure. (source: raw/Effective harnesses for long-running agents.md)

## The two-part solution

### 1. Initializer agent

The very first session uses a specialized prompt. Its job is to set up the environment that all subsequent agents will use:

- **`init.sh`**: script to start the development server and run a basic end-to-end test
- **Feature list** (`feature_list.json`): a structured JSON file with 200+ end-to-end feature descriptions, all initially marked `"passes": false`
- **Progress file** (`claude-progress.txt`): an append-only log of what agents have done
- **Initial git commit**: shows what files were added

### 2. Coding agent

Every subsequent session follows the same protocol:

1. Run `pwd`
2. Read `claude-progress.txt` and git log to get up to speed
3. Read `feature_list.json`, choose the highest-priority failing feature
4. Run `init.sh` to start the dev server and verify baseline functionality
5. Implement the feature incrementally
6. Test end-to-end using browser automation (Puppeteer MCP)
7. Mark the feature as passing only after careful testing
8. Commit with a descriptive message and update the progress file

## Why JSON for the feature list

The feature list is JSON, not markdown. The model is less likely to inappropriately change or overwrite JSON files. Coding agents are instructed with strongly-worded rules: "It is unacceptable to remove or edit tests because this could lead to missing or buggy functionality." (source: raw/Effective harnesses for long-running agents.md)

## Failure modes and solutions

| Problem | Initializer behavior | Coding agent behavior |
|---|---|---|
| Declares victory on the whole project too early | Write feature list with all features marked failing | Read feature list; choose one feature per session |
| Leaves environment in broken or undocumented state | Set up git repo and progress notes file | Read progress notes + git log at start; commit + update progress at end |
| Marks features done without proper testing | Write feature list file | Self-verify all features; only mark passing after careful testing |
| Wastes time figuring out how to run the app | Write `init.sh` | Read `init.sh` at start of every session |

## Connection to [[repository-as-context]]

The progress file and feature list are the lightweight version of the same principle driving [[harness-engineering]]: the repo is the agent's only persistent memory. Every session starts cold — the artifacts in the repo are the handoff note between shifts. See [[agent-harness]] for a comparison of both approaches.

## Open questions (as of publication)

- Whether a single general-purpose coding agent outperforms a multi-agent architecture (testing agent, QA agent, cleanup agent)
- How well these patterns generalize beyond web app development (scientific research, financial modeling)

## Related pages

- [[agent-harness]]
- [[harness-engineering]]
- [[repository-as-context]]
