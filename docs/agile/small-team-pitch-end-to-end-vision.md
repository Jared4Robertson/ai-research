# Pitch: Fixing End-to-End Vision and Team Coordination

> **Audience:** Product Director, Engineering Director, PM-A, PM-B, Senior Engineers
> **Author:** Engineering Manager
> **Companion doc:** [`scrum-artifacts-for-epics-stories-tasks.md`](./scrum-artifacts-for-epics-stories-tasks.md) — general reference for artifact types

This document is the pitch to realign how our small product + engineering group works. It is tailored to our actual team shape and our actual problem: **nobody can point at a single artifact and say "this is the end-to-end experience we are building."**

You can lift any section of this into a slide deck or a working doc.

---

## 1. Our Team Shape (the real constraints)

| Role | Count | Notes |
|---|---|---|
| Product Director | 1 (shared) | Oversees multiple products. Effectively part-time on ours. |
| Product Manager | 2 | **PM-A**: strong business context. **PM-B**: sharp, closer to execution, still building business fluency. |
| Engineering Director | 1 | People-focused. Not driving technical vision. |
| Engineering Manager (me) | 1 | Has cross-team architecture capability. |
| Team 1 | 1 senior + 1 junior | |
| Team 2 | 1 senior + 1 junior | |

**Delivery capacity:** 4 engineers across two squads. **Context-holders:** effectively 3 people (me, both seniors). **Business context holders:** effectively 2 people (Product Director part-time, PM-A).

Everything that follows respects those numbers. We cannot adopt a process that assumes a full-time PO, a staff architect, or a dedicated UX researcher. We have to get the leverage from a small number of high-quality artifacts.

---

## 2. What Is Actually Wrong Right Now

Stated plainly, so the pitch does not bury the diagnosis:

1. **No end-to-end experience is documented anywhere.** There is no user journey, no system context diagram, no target-state narrative. New people (and existing ones) reconstruct it in their heads every sprint.
2. **The roadmap is a list of epics, not outcomes.** Epics exist without the "why." It is impossible to tell which ones matter most or how they fit together.
3. **Product Director is a bottleneck for business context** because they are split across products. Waiting on them blocks decisions.
4. **The two teams have no coordination spine.** Architectural drift is happening. Each team makes locally sensible decisions that conflict at the seams.
5. **The Engineering Director is not closing the technical vision gap** — not a criticism, they are people-focused by design. But it means no one *above* me is pulling the technical story together.
6. **Junior engineers have thin context** and senior engineers rebuild context at the start of every sprint. That is waste.

**Root cause (using the companion doc's framing):** we skipped the **discovery** and **definition** layers and jumped from "roadmap" straight to "epics." The middle layer is exactly the layer that would have given us a shared end-to-end picture.

---

## 3. The Pitch in One Sentence

> **We adopt three lightweight artifacts and one coordination ritual, owned by specific people, so that every epic traces back to a shared end-to-end experience and both teams ship toward the same picture.**

That is the whole pitch. The rest of this doc is how.

---

## 4. The Three Changes

### Change 1 — Build the missing **Experience Vision** artifact

A single living document that answers:

- **Who** is our user (2–3 personas max)?
- **What** are they trying to accomplish end-to-end (jobs-to-be-done)?
- **Current state journey** — what the experience looks like today, including the painful seams between our two teams' surfaces.
- **Target state journey** — where we are headed in 2–4 quarters, drawn as the same journey with the pain removed.
- **System context diagram** — one page showing the major systems, the two teams' surfaces, and where the integrations live.
- **The 3–5 outcomes** that get us from current to target.

**Format:** one page of journey map + one page of system context + one page of target-state narrative. Probably 3–5 pages total. Lives in this repo.

**Why this is the keystone artifact:** it replaces "the thing in everyone's head" with a shared reference. Every epic that follows traces to one of the 3–5 outcomes on this page. Without this, no other change sticks.

**Who builds it:**
- **PM-B + me** draft it in one focused week. (PM-B is sharp and close to execution; I have the cross-team architecture view. Together we can write both the user-facing journey and the system context.)
- **PM-A** reviews for business accuracy and fills in outcomes/success metrics.
- **Product Director** reviews and approves async in a single 30–45 minute session.
- **Both senior engineers** review the system context diagram and target-state architecture.

**Why PM-B and not PM-A as the drafter:** PM-A is our scarcest business-context resource. Using them as the *reviewer* is higher leverage than using them as the *scribe*. PM-B writing the draft builds their business fluency through the review loop. This turns a weakness ("PM-B still learning the business") into a development plan.

### Change 2 — Replace the epic list with an **Outcome Roadmap**

Delete the current roadmap-as-list. Replace it with:

```
Now (this quarter)        Next (next quarter)        Later (2+ quarters out)
─────────────────         ───────────────────        ──────────────────────
Outcome 1                 Outcome 3                   Outcome 5
  • Metric: X → Y           • Metric: X → Y
  • Epics: A, B, C          • Epics: F, G
Outcome 2                 Outcome 4
  • Metric: X → Y           • Metric: X → Y
  • Epics: D, E             • Epic: H
```

**Rules:**
- At most 5 outcomes in flight at once. We have 4 engineers. More than 5 outcomes means we are lying to ourselves.
- Every outcome has a single measurable success metric.
- Every epic is stapled to exactly one outcome. If an epic cannot be stapled to an outcome, it is either a new outcome or it does not get built.
- The roadmap is reviewed monthly, not sprint-by-sprint.

**Owner:** PM-A (with Product Director sign-off). PM-B contributes the epic-to-outcome mapping. I contribute the engineering feasibility checkpoint.

### Change 3 — Establish a coordination spine between the two teams

Without changing team structure, introduce a thin connective tissue so the two squads build toward one system:

1. **Weekly 30-minute architecture sync.** Attendees: me + both senior engineers. Agenda: cross-team seams, upcoming stories that touch both surfaces, any ADR in flight. No junior engineers by default — respect their focus time, bring them in for specific topics.
2. **One shared architecture doc** (owned by me, contributed to by both seniors). One page of "how the system fits together" updated when things change.
3. **ADRs in the repo** for any decision that affects both teams. Lightweight — one page each. I enforce this as a reviewer on PRs that introduce cross-team changes without one.
4. **Joint backlog refinement, every two weeks**, 60 minutes. Both teams, both PMs, me. Agenda: next sprint's stories, dependencies between teams, acceptance criteria clarity.
5. **Definition of Ready + Definition of Done**, posted in the repo, enforced in refinement. This is the single biggest lever for getting the juniors productive faster.

---

## 5. Role Realignment — What Changes for Each Person

| Person | Stops | Starts | Keeps |
|---|---|---|---|
| **Product Director** | Being the implicit source of business context for every decision | Reviewing the Experience Vision and Outcome Roadmap in scheduled async sessions | Final approval on strategic direction and outcome priority |
| **PM-A** | Writing epic-level tickets as the primary artifact | Owning the Outcome Roadmap and being the business translator for PM-B | Customer and stakeholder relationships |
| **PM-B** | Working ticket-by-ticket without a shared target | Co-drafting the Experience Vision with me; writing the 1-page PRD per epic | Close collaboration with engineering |
| **Engineering Director** | Being expected to drive technical vision (they shouldn't) | Acting as air cover for this process change and unblocking people issues | Career growth, hiring, people management |
| **Me (EM)** | Carrying the end-to-end picture in my head | Owning the cross-team architecture doc, the ADR discipline, and the weekly architecture sync; co-authoring the Experience Vision | Cross-team architecture judgment |
| **Senior engineers** | Rebuilding context every sprint | Participating in weekly architecture sync; contributing ADRs; mentoring juniors against a shared target | Technical leadership within their team |
| **Junior engineers** | Guessing at intent | Reading the Experience Vision and Outcome Roadmap at the start of every epic; asking "which outcome does this serve?" in refinement | Focus on execution quality |

---

## 6. What We Stop Doing (explicit)

Process changes fail when we only add. Here is what we stop:

- Stop treating the epic list as the roadmap.
- Stop writing stories without acceptance criteria.
- Stop letting each team operate independently on shared surfaces.
- Stop assuming the Product Director will fill every business-context gap in real time — we make artifacts they review asynchronously instead.
- Stop doing sprint planning without Definition of Ready enforcement.
- Stop having technical decisions that affect both teams happen in DMs or hallway conversations — they become ADRs.

---

## 7. 30 / 60 / 90 Day Plan

### Days 1–14 — Earn the right
- **Week 1:** I pitch this doc. Get Product Director + Engineering Director buy-in. Lock PM-A and PM-B time for Week 2.
- **Week 2:** PM-B and I draft the Experience Vision (journey + system context + target state). 3 working sessions, 2 hours each.
- **Deliverable by end of Week 2:** a reviewable draft of the Experience Vision.

### Days 15–30 — Anchor the process
- **Week 3:** Review Experience Vision with PM-A, seniors, Eng Director. One async review round with Product Director.
- **Week 3:** PM-A drafts Outcome Roadmap from approved Experience Vision. I review for feasibility.
- **Week 4:** Restructure current epics onto the Outcome Roadmap. Kill or defer any epic that doesn't ladder to an outcome. Publish the Definition of Ready and Definition of Done.
- **Deliverable by end of Day 30:** Experience Vision, Outcome Roadmap, DoR/DoD, all in the repo.

### Days 31–60 — Make the coordination spine real
- Weekly architecture sync starts Week 5.
- First joint backlog refinement under the new DoR, Week 5.
- First ADRs start appearing, Week 5–6.
- First cross-team epic refined against the new artifacts, Week 6.
- I publish the shared architecture doc, Week 7.
- **Deliverable by end of Day 60:** one full sprint cycle under the new artifacts, with a retro capturing what worked.

### Days 61–90 — Prove the value and tune
- At Day 75, we do a mid-cycle check: are the juniors onboarding faster? Are we surfacing fewer cross-team surprises? Is the Outcome Roadmap still honest?
- Tune the cadence and kill any ritual not pulling its weight.
- **Deliverable by end of Day 90:** evidence for/against, and a decision on what to keep.

---

## 8. What Success Looks Like (leading indicators)

These are what I will measure to know the pitch is working. Deliberately qualitative and cheap to observe — we do not have bandwidth for metric theater.

- Any team member, picked at random, can answer "what are we building and why" with a consistent answer.
- The number of epics drops; the number of outcomes stabilizes at 3–5.
- Cross-team surprises (merge conflicts on shared surfaces, duplicated work, incompatible assumptions) drop noticeably.
- Junior engineers can self-onboard to a new epic by reading the Experience Vision + the epic PRD without a 1:1 context download.
- Product Director time per week on our product stays flat or drops, while decision quality goes up (because artifacts are doing the carrying).
- Sprint planning runs shorter because refinement did its job.

---

## 9. Risks and Mitigations

| Risk | Likelihood | Mitigation |
|---|---|---|
| Product Director cannot engage even async | High | Structure their review as a single 30-min session with pre-read. Make PM-A the delegated decision-maker between those sessions. |
| PM-B feels demoted by being "the scribe" | Medium | Frame it explicitly as a growth opportunity and leverage play, not a downgrade. They are co-author, not note-taker. |
| We create artifacts no one uses | Medium | Start with ONE artifact (Experience Vision) and earn the right to introduce the next. Do not ship all three changes on Day 1. |
| Eng Director worries this bypasses them | Medium | Brief them privately first. Explicitly position them as air cover and sponsor of the change. Ask for their help on the people-side of rollout. |
| Teams resent new process | Medium | Kill any ritual the retro says is not pulling its weight. Keep DoR/DoD as the non-negotiable core. |
| Senior engineers see the architecture sync as extra meeting | Low | 30 minutes, fixed agenda, cancel when empty. Frame it as "the meeting that prevents the other three meetings." |

---

## 10. Why This Works for *Our* Shape Specifically

- **1 Product Director shared across products** → we move them from real-time bottleneck to async reviewer. They sign off on vision and outcomes, not epics.
- **PM-A strong on business / PM-B sharp on execution** → we split them by strength. PM-A owns the roadmap and stakeholder translation; PM-B owns the execution-side artifacts and builds business fluency through the review loop.
- **EM with cross-team architecture capability (me)** → I become the deliberate owner of the connective tissue between the two teams, which is the single biggest gap today. This is the role I am already partly filling informally; this pitch just makes it explicit.
- **People-focused Engineering Director** → they get a role that matches their strengths (air cover, people unblock, sponsor) rather than being expected to drive technical vision they are not positioned to drive.
- **Two squads of sr + jr** → juniors get a shared artifact to learn from; seniors stop rebuilding context; the weekly arch sync is small enough to be high-signal.

---

## 11. The Opening Line of the Pitch (ready to say out loud)

> "We have good people and enough capacity, but no one can point at a single artifact and say 'this is the end-to-end experience we are building.' I want to fix that with three lightweight artifacts and one weekly ritual, owned by specific people, and I'd like two weeks to produce the first one so we can decide together whether the rest is worth adopting."

That framing is important:
- It names a problem everyone feels.
- It asks for a small, reversible commitment (two weeks, one artifact).
- It offers a decision point, not a mandate.
- It positions this as collaborative, not a power grab.

---

## 12. Appendix — Skeleton of the Experience Vision Artifact

Use this as the outline when PM-B and I draft it in Week 2.

```
1. Who we serve
   - Persona 1: <name, role, what they care about>
   - Persona 2: <...>

2. The job to be done
   - When <situation>, they want to <motivation>, so they can <outcome>.

3. Current-state journey
   - Step-by-step journey with pain points called out
   - Which team owns which step today
   - Known seams and handoff issues

4. Target-state journey (2–4 quarters out)
   - Same journey, pain removed
   - What the user notices that is different
   - What the system does differently

5. System context diagram
   - Boxes: services, shared data stores, external integrations
   - Lines: data/control flow
   - Dotted boundary: which team owns what

6. Outcomes that bridge current → target
   - Outcome 1: <measurable metric>
   - Outcome 2: <measurable metric>
   - Outcome 3: <measurable metric>
   - (Cap at 5)

7. Explicit non-goals
   - What we are deliberately not doing in this horizon
```

Keep the whole thing under 5 pages. If it is longer, it will not be read, and unread artifacts create more confusion than they resolve.
