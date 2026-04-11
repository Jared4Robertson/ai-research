# Scrum Artifacts That Inform Epics, Stories, and Tasks

> **Question:** In a scrum/agile process, what artifacts should be created, maintained, and iterated on to inform epics, stories, and tasks?

This document describes the artifacts that feed a healthy scrum backlog. It separates the *official Scrum Guide* artifacts from the broader set of **supporting artifacts** that mature product and engineering organizations rely on to make those Scrum artifacts trustworthy.

---

## 1. The Three Official Scrum Artifacts

The Scrum Guide defines only three artifacts. Everything else is a supporting practice that the team adopts to make these three useful.

| Artifact | Purpose | Commitment | Primary Owner |
|---|---|---|---|
| **Product Backlog** | Ordered list of everything that might be needed in the product. Source of all epics, stories, and tasks. | **Product Goal** | Product Manager / Product Owner |
| **Sprint Backlog** | The set of Product Backlog items selected for the Sprint plus a plan for delivering them. | **Sprint Goal** | Development Team |
| **Increment** | A concrete, usable stepping stone toward the Product Goal. Each increment must meet the Definition of Done. | **Definition of Done** | Development Team |

Everything below exists to make these three artifacts accurate, prioritized, and actionable.

---

## 2. Strategic Artifacts (Business → Product Alignment)

These are typically owned by the **Product Director** (with input from the CTO, CEO, and Engineering Director). They set the "why" that epics ultimately trace back to.

- **Product Vision** — A short, durable statement of what the product aspires to be and for whom. Refreshed yearly, not sprint-by-sprint.
- **Product Strategy** — How the vision will be achieved: target segments, differentiation, bets, and constraints.
- **Product Roadmap (Outcome-Based)** — Time-horizoned themes and outcomes (not a feature Gantt chart). Typically now / next / later.
- **OKRs or KPI Trees** — Measurable outcomes that the roadmap themes map to. Every epic should trace to an OKR or KPI.
- **Business Model / Pricing & Packaging Notes** — Anchors what is worth building for which tier of customer.
- **Market & Competitive Analysis** — Keeps the team honest about table stakes vs. differentiators.

**Iteration cadence:** Vision annually. Strategy quarterly. Roadmap and OKRs monthly to quarterly.

---

## 3. Discovery Artifacts (Problem Space)

Owned by **Product Managers** in partnership with **Design** and **Senior Engineers**. These ensure the team builds the right thing before optimizing how it is built.

- **User Personas / ICPs** — Who we are building for.
- **Jobs-To-Be-Done (JTBD) Statements** — What the user is trying to accomplish.
- **Customer Interview Notes & Research Repository** — Raw evidence that justifies the backlog.
- **Opportunity Solution Tree** — Maps outcomes → opportunities (user problems) → solutions → experiments. This is often the *direct feeder* into epics.
- **User Journey Maps / Service Blueprints** — Show where the pain lives end-to-end.
- **Problem Statements** — Concise framing that pins down a specific opportunity before solutioning.
- **Assumption & Risk Logs** — What we believe but have not yet validated; drives spikes and experiments.

**Iteration cadence:** Continuously. Discovery is a parallel track to delivery, not a phase.

---

## 4. Definition Artifacts (Solution Space, Pre-Ready)

These convert validated opportunities into backlog items that engineering can commit to. Jointly owned by **Product Managers**, **Designers**, and **Senior Engineers / Engineering Managers**.

- **Product Requirements Document (PRD) / Feature Brief / One-Pager** — The "what and why" for an epic. Includes problem, target user, success metrics, scope, out-of-scope, open questions.
- **Design Specs & Prototypes** — Wireframes, hi-fi mocks, Figma flows, interaction states.
- **Acceptance Criteria (per story)** — Behavior-level conditions for "done." Often written in Given/When/Then.
- **Non-Functional Requirements (NFRs)** — Performance budgets, accessibility (e.g., WCAG 2.2 AA), security, compliance, observability expectations.
- **Analytics & Instrumentation Plan** — Which events/metrics prove the epic delivered its outcome.
- **Dependency Map** — Upstream/downstream teams, third-party services, shared platforms.

**Iteration cadence:** Per epic, refined in backlog refinement sessions before entering a sprint.

---

## 5. Engineering Artifacts (How We Will Build It)

Owned by **Engineering Managers** and **Senior Engineers**, reviewed by the **Engineering Director** for cross-team concerns. These prevent stories from becoming a source of hidden technical surprises.

- **Technical Design Document (TDD) / RFC** — For any epic with non-trivial architectural impact. Describes approach, alternatives considered, trade-offs, rollout plan.
- **Architecture Decision Records (ADRs)** — Short, immutable records of significant decisions and their context. Lives in the repo.
- **System & Sequence Diagrams** — C4 model, data flow, sequence diagrams for cross-service interactions.
- **API Contracts / Schemas** — OpenAPI, GraphQL SDL, protobuf — agreed *before* story work begins to unblock parallel teams.
- **Data Model Changes / Migration Plans** — Especially important for zero-downtime changes.
- **Spike Reports** — Time-boxed investigation outputs that retire risk before committing to a story estimate.
- **Threat Model / Security Review Notes** — For anything touching auth, PII, payments, or tenancy boundaries.
- **Test Strategy** — What level of testing (unit, integration, contract, e2e, load) is appropriate for this epic.
- **Rollout & Rollback Plan** — Feature flags, canary strategy, migration reversibility.

**Iteration cadence:** Per epic (TDD/RFC), per significant decision (ADR), continuously (diagrams).

---

## 6. Team Working Agreements

These are owned by the **Scrum Team** collectively and are the guardrails that keep epics, stories, and tasks consistent in quality.

- **Definition of Ready (DoR)** — What a story must look like before it can enter a sprint (e.g., acceptance criteria present, design attached, dependencies identified, estimable).
- **Definition of Done (DoD)** — What must be true before a story is shippable (e.g., tests pass, code reviewed, docs updated, deployed behind flag, observability in place).
- **Estimation Convention** — Story points, t-shirt sizes, or #NoEstimates. Consistency matters more than the choice.
- **Working Agreements** — Team norms: core hours, review SLAs, WIP limits, pairing expectations.

**Iteration cadence:** Reviewed every retrospective; changed deliberately.

---

## 7. Delivery & Feedback Artifacts

These emerge from running the process and feed back into the backlog.

- **Sprint Goal** — The one-sentence reason this sprint exists.
- **Burndown / Burn-up / Cumulative Flow Diagram** — Progress visibility.
- **Impediment / Risk Log** — Owned by the Scrum Master / EM.
- **Release Notes & Changelog** — Communicates increments to stakeholders and customers.
- **Retro Action Items** — Commitments that feed back into working agreements and the backlog.
- **Telemetry Dashboards** — Validate whether shipped increments moved the outcome the epic was meant to move.

---

## 8. How the Artifacts Cascade into Epics, Stories, and Tasks

```
Vision & Strategy
      │
      ▼
OKRs / Outcomes ──────────────┐
      │                       │
      ▼                       │
Opportunity Solution Tree     │   (Discovery)
      │                       │
      ▼                       │
Problem Statement + PRD ──────┤
      │                       │
      ▼                       │
      EPIC  ◄─ Design Specs, TDD/RFC, NFRs, ADRs
      │
      ▼
      STORY  ◄─ Acceptance Criteria, API contracts, Test strategy
      │
      ▼
      TASK   ◄─ Engineering decomposition by the dev team
      │
      ▼
   Increment (meets DoD) ──► Telemetry ──► back to OKRs
```

**Key principle:** every epic traces *up* to a business outcome and *down* to concrete acceptance criteria. If you cannot draw that line, the epic is not ready.

---

## 9. Role Ownership Cheat Sheet

| Artifact | Accountable | Consulted | Informed |
|---|---|---|---|
| Vision, Strategy | Product Director / CPO | CTO, CEO | Whole org |
| Roadmap, OKRs | Product Director + PMs | Eng Director, Design | Whole team |
| Discovery artifacts | Product Manager | Designer, Sr. Engineer | EM |
| PRD / Feature brief | Product Manager | Designer, EM, Sr. Engineer | Team |
| TDD / RFC / ADRs | Senior Engineer / EM | Eng Director, Architects | Team |
| Definition of Ready/Done | Whole team | Scrum Master, EM | Stakeholders |
| Product Backlog | Product Manager (PO) | Team | Stakeholders |
| Sprint Backlog | Development Team | PM | Stakeholders |
| Increment + Telemetry | Development Team | PM | Stakeholders |

---

## 10. Anti-Patterns to Watch For

- **Feature-factory roadmaps.** Roadmaps that list features instead of outcomes detach epics from business value.
- **PRDs written after design is locked.** Design then becomes the requirement, and trade-offs are invisible.
- **Epics without success metrics.** You cannot tell when you are done or whether it worked.
- **Stories with no acceptance criteria.** Estimates become fiction; scope creep is invisible.
- **TDDs only for "big" work.** Small architectural decisions quietly compound into tech debt — use lightweight ADRs liberally.
- **Definition of Done that excludes observability.** You ship blind and cannot close the feedback loop.
- **Backlog as a graveyard.** If items older than ~2 quarters are not pruned, prioritization signal is lost.
- **Discovery and delivery run as phases, not parallel tracks.** Engineering sits idle or builds the wrong thing.

---

## 11. Minimum Viable Set for a Small Team

If you are a small team and the full list feels heavy, start here and grow into the rest:

1. **Outcome-based roadmap** tied to 2–4 OKRs.
2. **One-page PRDs** per epic with success metrics.
3. **Acceptance criteria** on every story.
4. **Lightweight ADRs** in the repo for non-trivial decisions.
5. **Definition of Ready and Definition of Done**, posted and enforced.
6. **A telemetry dashboard** per epic's success metric.

Everything else can be added as the organization scales.

---

## References for Further Reading

- *The Scrum Guide* (Schwaber & Sutherland, current edition)
- *Inspired* and *Empowered* — Marty Cagan
- *Continuous Discovery Habits* — Teresa Torres (Opportunity Solution Tree)
- *Escaping the Build Trap* — Melissa Perri
- *Accelerate* — Forsgren, Humble, Kim (DORA metrics as delivery feedback)
- *Team Topologies* — Skelton & Pais (team structure and ownership)
