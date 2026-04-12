# Questions Each Artifact Answers

> **Purpose:** Every artifact exists to answer specific questions. If nobody is asking the question, you don't need the artifact. If people keep asking a question and there's no artifact, that's your gap.
>
> This table covers both the [general artifact reference](./scrum-artifacts-for-epics-stories-tasks.md) and the [S2.1-specific pitch](./small-team-pitch-end-to-end-vision.md).

---

## Strategic Questions — "Why does this product exist?"

| Question | Artifact That Answers It |
|---|---|
| What is this product supposed to become? What future are we building toward? | **Product Vision** |
| How are we going to get there? What bets are we making and what are we *not* doing? | **Product Strategy** |
| What are we focused on now, next, and later — and why in that order? | **Outcome Roadmap** (or **Three-Lane Outcome Roadmap** in our S2.1 context) |
| How do we know if we're winning? What numbers move if this works? | **OKRs / KPI Trees** |
| What is this product worth to the business? Who pays for it and why? | **Business Model / Pricing & Packaging Notes** |
| What do competitors offer? What is table stakes vs. what differentiates us? | **Market & Competitive Analysis** |
| Where is our capacity actually going across legacy, S2, and S2.1? | **Three-Lane Outcome Roadmap** |

---

## Discovery Questions — "Are we building the right thing?"

| Question | Artifact That Answers It |
|---|---|
| Who exactly is our user? What do they care about? What is their context? | **User Personas / ICPs** |
| What is the user actually trying to accomplish, in their own terms? | **Jobs-To-Be-Done (JTBD) Statements** |
| What did real users tell us? What evidence do we have, not just opinions? | **Customer Interview Notes & Research Repository** (includes **Pilot Client Interview** in our context) |
| What user problems map to what outcomes, and what solutions are we testing? | **Opportunity Solution Tree** |
| What does the end-to-end experience look like today, step by step? Where is the pain? | **User Journey Map / Service Blueprint** (or the **Legacy Current-State Journey** and **S2 Current-State Journey** sections of the Experience Vision) |
| What specific problem are we solving here, framed precisely enough to act on? | **Problem Statements** |
| What do we believe but have not yet proven? What could blow up? | **Assumption & Risk Log** |

---

## Experience & Domain Questions — "What is the settlement experience, end to end?"

These are specific to our S2.1 context. The Experience Vision artifact answers a cluster of questions that were previously unanswered.

| Question | Section of the **Experience Vision** That Answers It |
|---|---|
| What does settlement look like in the legacy system today — the system that actually works? | **Legacy Current-State Journey** |
| What does settlement look like for the pilot client in S2 today — and where does S2's architecture cause them pain? | **S2 Current-State Journey** |
| What should the settlement experience look like in S2.1 when we're done? | **S2.1 Target-State Journey** |
| What are the non-negotiable rules the settlement system must honor? What can never be violated? | **Business Rules / Domain Invariants** |
| What did we get wrong in S2? What business assumptions turned out to be false? Where did we draw boundaries in the wrong place? | **"What S2 Taught Us"** (blameless architectural lessons) |
| What are the 3–5 measurable outcomes that bridge where we are to where we're going? | **Outcomes** section |
| What are we deliberately *not* building in this horizon? | **Explicit Non-Goals** |
| Who exactly uses this system? (operations, pilot client, finance, compliance?) | **Personas** section |

---

## Definition Questions — "What exactly are we building for this epic?"

| Question | Artifact That Answers It |
|---|---|
| What is this epic about? What problem does it solve, for whom, and how will we know it worked? | **PRD / Feature Brief / One-Pager** |
| What should this look like? What are the screens, flows, states, and interactions? | **Design Specs & Prototypes** |
| How do I know when this story is done? What are the exact conditions? | **Acceptance Criteria** |
| What are the performance, security, accessibility, and compliance expectations? | **Non-Functional Requirements (NFRs)** |
| How will we measure whether this feature actually moved the outcome? What events do we track? | **Analytics & Instrumentation Plan** |
| What other teams, services, or third parties does this depend on? What could block us? | **Dependency Map** |
| Which business rule from the Experience Vision does this story serve? | **Business Rules / Domain Invariants** (referenced by ID, e.g. BR-07) |

---

## Engineering Questions — "How are we going to build it?"

| Question | Artifact That Answers It |
|---|---|
| What is the technical approach? What alternatives were considered and why was this one chosen? | **Technical Design Document (TDD) / RFC** |
| Why did we make this specific architectural decision? What was the context? | **Architecture Decision Record (ADR)** |
| How do the services, data stores, and integrations fit together? What calls what? | **System & Sequence Diagrams** (and the **S2.1 System Context Diagram** from the Experience Vision) |
| What is the API contract between teams or services? Can we build in parallel? | **API Contracts / Schemas** (OpenAPI, GraphQL SDL, protobuf) |
| What changes to the data model? How do we migrate without downtime? | **Data Model Changes / Migration Plan** |
| We don't know enough to estimate this. Can we investigate first? | **Spike Report** (time-boxed investigation output) |
| What are the security risks? What happens if this gets exploited? | **Threat Model / Security Review Notes** |
| What level of testing is appropriate — unit, integration, contract, e2e, load? | **Test Strategy** |
| How do we ship this safely? How do we roll back if it breaks? | **Rollout & Rollback Plan** |
| Where does S2.1's architecture differ from S2, and why? | **Shared Architecture Doc** ("where we differ from S2 and why" section) |
| Does this engineering decision trace back to a business rule or outcome? | **ADR** (must name the business rule or outcome it serves) |

---

## Coordination Questions — "How do the two teams stay aligned?"

| Question | Artifact That Answers It |
|---|---|
| How does the whole S2.1 system fit together across both teams? | **Shared Architecture Doc** |
| Are the two teams making compatible decisions at the seams? | **Weekly Architecture Sync** (ritual, not artifact — but produces ADRs) |
| What is each team working on next sprint, and where are the dependencies? | **Joint Backlog Refinement** (ritual) → produces updated **Sprint Backlog** with dependency annotations |
| Who owns which part of the system? | **System Context Diagram** (dotted boundaries in the Experience Vision) |
| Is a cross-team decision being made without being documented? | **ADR discipline** — any cross-team change without an ADR is flagged in review |

---

## Readiness & Quality Questions — "Is this story ready to build? Is it done?"

| Question | Artifact That Answers It |
|---|---|
| Can this story enter the sprint? Does it have everything engineering needs to start? | **Definition of Ready (DoR)** |
| Is this story shippable? Does it meet our bar for code review, testing, observability, and deployment? | **Definition of Done (DoD)** |
| How big is this? Can we fit it in a sprint? | **Estimation Convention** (story points, t-shirt sizes, etc.) |
| What are our team norms — core hours, review SLAs, WIP limits, pairing? | **Working Agreements** |

---

## Delivery & Progress Questions — "Are we on track?"

| Question | Artifact That Answers It |
|---|---|
| Why does this sprint exist? What is the one thing that matters? | **Sprint Goal** |
| What did the team commit to this sprint? What is the plan for delivering it? | **Sprint Backlog** |
| Are we burning down or piling up? Is scope creeping? | **Burndown / Burn-up / Cumulative Flow Diagram** |
| What is blocking us? What risks are we carrying? | **Impediment / Risk Log** |
| What shipped? What should stakeholders and customers know about? | **Release Notes & Changelog** |
| What is the usable, deployable thing we produced this sprint? | **Increment** (must meet Definition of Done) |
| Everything that *might* be needed, in priority order — what is the full backlog? | **Product Backlog** |

---

## Learning & Feedback Questions — "Did it work? What do we do differently?"

| Question | Artifact That Answers It |
|---|---|
| Did the feature actually move the outcome it was supposed to move? | **Telemetry Dashboards** |
| What should we change about how we work? | **Retro Action Items** |
| Are we repeating S2's mistakes? Are architectural decisions drifting from business rules? | **ADRs** (checked against **Business Rules / Domain Invariants**) |
| Did the pilot client's experience improve? | **Pilot Client Interview** (repeated periodically) + **Telemetry** |

---

## The Gap Diagnostic

Use this table as a diagnostic tool. For each question, ask: **"Can someone on my team answer this right now by pointing at a written artifact?"**

- **If yes →** the artifact exists and is working. Keep it maintained.
- **If "sort of, it's in someone's head" →** the artifact is missing. That person is a bus-factor-of-one bottleneck. Write it down.
- **If "no, and nobody knows" →** this is a discovery gap. It needs investigation before it can become an artifact.

In our case today, almost every question in the **Experience & Domain** and **Coordination** sections gets a "sort of, it's in someone's head" — which is exactly the gap this pitch is designed to close.
