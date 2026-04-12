# Context

## What this repo is

A knowledge base being built collaboratively between an Engineering Manager and a CTO-perspective AI advisor. The goal is to document how product and engineering teams should coordinate to build software products — specifically in the context of replacing a legacy system.

## The real-world situation

We are working on **Settlement 2.0 (S2)** — a replacement for a legacy settlement system.

- **S2** went live last year with one pilot client, but it was built engineering-led without a clear understanding of business requirements. This led to misaligned architecture decisions.
- **S2.1** is the current effort to build with better business alignment, but those requirements are still unclear.
- There is no documentation of the end-to-end user experience across legacy, S2, or S2.1.
- The roadmap is a list of epics that don't clearly connect to outcomes.
- There is significant confusion about direction and how teams should coordinate.

## The team

| Role | Count | Notes |
|---|---|---|
| Product Director | 1 | Shared across multiple products. Effectively part-time on this one. |
| Product Manager (PM-A) | 1 | Strong business context. |
| Product Manager (PM-B) | 1 | Sharp and execution-focused, still building business fluency. |
| Engineering Director | 1 | More people-focused than engineering-focused. |
| Engineering Manager (the user) | 1 | Capable of cross-team architecture. Driving this effort. |
| Team 1 | 1 senior + 1 junior engineer | |
| Team 2 | 1 senior + 1 junior engineer | |

## What we're building in this repo

A **question chain** (`docs/question-chain.md`) — a step-by-step sequence of simple, unambiguous questions that walks a team from "we need to replace a legacy system" all the way to well-defined epics, stories, and tasks.

### Design principles for the question chain

- **Each question is small and non-intimidating.** No loaded questions that require a week of work to answer.
- **Each question has a clear expected answer format.** Lists, single sentences, role+goal pairs — never vague.
- **Each answer feeds the next question.** The chain builds understanding one layer at a time.
- **No process jargon or frameworks.** Plain language. If someone needs to google a term, the question is too fancy.
- **Grounded in world-class product thinking** (Cagan, Torres, Blank, etc.) but expressed as simple questions, not methodology.

### Current state of the chain

The chain currently covers: Goal → Orient → People → Value → Pain → Vision (Q1–Q8). It still needs to bridge from "we understand the problem" to "here's the well-defined work" (epics, stories, tasks).

## What came before

We previously built detailed pitch documents and artifact reference guides but scrapped them — they were heading in the wrong direction (too much process, too overwhelming). The question chain approach emerged from stripping everything back to first principles: what is the simplest question we should ask first?

## Branch

All work is on `claude/cto-team-coordination-NSgka`.
