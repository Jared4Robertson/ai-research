# Pitch: Fixing End-to-End Vision and Team Coordination

> **Audience:** Product Director, Engineering Director, PM-A, PM-B, Senior Engineers
> **Author:** Engineering Manager
> **Companion doc:** [`scrum-artifacts-for-epics-stories-tasks.md`](./scrum-artifacts-for-epics-stories-tasks.md) — general reference for artifact types

This document is the pitch to realign how our small product + engineering group works. It is tailored to our actual team shape and our actual problem: **we are replacing a legacy settlement system, S2 (Settlement 2.0) was built engineering-led without clear business requirements and landed with misaligned architecture, and S2.1 is at risk of repeating the same failure because those requirements are *still* not clear.**

Nobody can point at a single artifact and say "this is the end-to-end experience we are building." That was the root cause of S2's architectural drift, and it is the risk S2.1 is running into right now.

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

### System context — what's actually running

| System | Status | Notes |
|---|---|---|
| **Legacy settlement** | In production, being replaced | Source of truth for how settlement actually works in the business today. Observable. Can be interviewed. |
| **S2 (Settlement 2.0)** | Live with 1 pilot client | Built engineering-led without clear business requirements. Architecture is misaligned with the business domain. Pilot client is using it daily and has opinions. |
| **S2.1** | In active development (our current work) | Meant to correct S2's misalignment. Business requirements are still unclear. The 4 engineers are working on this across two squads. |

This means the 4 engineers are carrying three systems at once: keeping the legacy reliable enough to sunset, keeping S2 stable for the pilot client, and building S2.1. Any process change has to respect that reality.

Everything that follows respects those numbers. We cannot adopt a process that assumes a full-time PO, a staff architect, or a dedicated UX researcher. We have to get the leverage from a small number of high-quality artifacts.

---

## 2. What Is Actually Wrong Right Now

Stated plainly, so the pitch does not bury the diagnosis:

1. **S2 was built engineering-led without clear business requirements.** The architectural misalignment we are living with today is the direct consequence. We already paid this tuition.
2. **S2.1 is about to repeat the same failure.** Requirements are still not clear, we are deep into epic work, and we have no artifact that says "this is the settlement experience we are building and why."
3. **No end-to-end experience is documented anywhere** — not for legacy (despite it running the business), not for S2 (despite it having a live pilot client), and not for S2.1 (despite it being in active development). Everyone reconstructs the picture in their head every sprint.
4. **The roadmap is a list of epics, not outcomes.** Epics exist without the "why." It is impossible to tell which ones matter most, how they fit together, or whether they're fixing S2's architectural debt or adding net-new capability.
5. **Product Director is a bottleneck for business context** because they are split across products. Waiting on them blocks decisions — and that's exactly the gap S2 was built in.
6. **The two teams have no coordination spine.** Architectural drift is happening inside S2.1 *right now*, and the S2 drift that hurt us is the cautionary tale for why that matters.
7. **The Engineering Director is not closing the technical vision gap** — not a criticism, they are people-focused by design. But it means no one *above* me is pulling the technical story together.
8. **Junior engineers have thin context** on the settlement domain and senior engineers rebuild context at the start of every sprint. That is waste, and it is also how business rules get accidentally re-invented incorrectly.

**Root cause (using the companion doc's framing):** we skipped the **discovery** and **definition** artifact layers on S2, and we are skipping them again on S2.1. We jumped straight from "roadmap" to "epics." The middle layer — the layer that captures *what the settlement experience actually is and what rules govern it* — is exactly what would have prevented S2's misalignment and is exactly what S2.1 still lacks.

**The good news:** unlike a greenfield project, we don't have to imagine the current state. We can *observe* it. The legacy system is running, S2 is live with a pilot client, and our senior engineers carry hard-won lessons about where S2's architecture rubbed against reality. Discovery here is cheaper than usual — we just have to actually do it.

---

## 3. The Pitch in One Sentence

> **Before we go any further into S2.1, we adopt three lightweight artifacts and one coordination ritual — owned by specific people — so that every epic traces back to a shared end-to-end settlement experience, captures the business rules S2 missed, and both teams ship toward the same picture.**

That is the whole pitch. The rest of this doc is how.

---

## 4. The Three Changes

### Change 1 — Build the missing **Experience Vision** artifact (three states, not two)

A single living document that answers:

- **Who** is our user (2–3 personas max — the operations users, the pilot client, whoever else interacts with settlement)?
- **What** are they trying to accomplish end-to-end (jobs-to-be-done)?
- **Legacy current state** — what the settlement journey actually looks like in the system we are replacing. This is observable today. Mine it, don't guess.
- **S2 current state** — what the pilot client's journey actually looks like in S2, including where the architectural misalignment shows up as user pain. This is interviewable today.
- **S2.1 target state** — the same journey, with the legacy pain and the S2 misalignment both removed. The coherent picture we want to be building toward in 2–4 quarters.
- **System context diagram** for S2.1 — one page showing the major services, the two teams' surfaces, the integrations, and the seams where S2 got the boundaries wrong.
- **Business rules / domain invariants** — the non-negotiable rules that settlement must honor (reconciliation, timing, correctness, audit, money movement, whatever the domain demands). *This is the section whose absence caused S2's architectural drift.* PM-A owns this section. Without it, we will rebuild S2's mistakes.
- **"What S2 taught us"** — a blameless one-page section capturing the architectural lessons from S2: what business assumptions turned out to be wrong, what boundaries we drew in the wrong place, what we would do differently. Senior engineers own this section.
- **The 3–5 outcomes** that get us from the current mess to the target state.
- **Explicit non-goals** — what we are deliberately not doing in this horizon.

**Format:** probably 6–8 pages total now that we have three states plus rules plus lessons. Still readable in one sitting. Lives in this repo alongside the code.

**Why this is the keystone artifact:** it replaces "the thing in everyone's head" with a shared reference, and more importantly, **it is the artifact whose absence caused S2's misalignment in the first place**. Every epic that follows traces to one of the outcomes. Without this, no other change sticks, and S2.1 is on course to be S2 again.

**Who builds it and how it gets sourced:**
- **PM-B + me** draft it in one focused week. PM-B is sharp and close to execution; I have the cross-team architecture view. Together we can write both the user-facing journey and the system context.
- **PM-A** owns the *Business Rules / Domain Invariants* section and reviews for business accuracy. This is their highest-leverage contribution.
- **Both senior engineers** own the *What S2 Taught Us* section and review the system context diagram. They are the richest source of architectural lessons and should be treated as first-class authors on that section.
- **Pilot client** should be interviewed for the S2 current state — 45 minutes, PM-A + me. Their observed pain points become the most credible justification for the S2.1 outcomes.
- **Product Director** reviews and approves async in a single 30–45 minute session, focused on outcomes and rules.

**Discovery sources (cheap, already available):**
1. **Legacy system observation** — shadow an operations user for an hour. Capture the actual workflow.
2. **S2 code archaeology** — have each senior engineer write a one-pager on "where S2's architecture fought the domain." Mine the ADRs (if any) and the post-incident notes.
3. **Pilot client interview** — one 45-min call, recorded. Ask what they do daily, what frustrates them, what workaround they built.
4. **PM-A's existing business knowledge** — this is probably the richest untapped source. Structured extraction in 2–3 working sessions.

**Why PM-B and not PM-A as the drafter:** PM-A is our scarcest business-context resource. Using them as the *reviewer* and the *rules-section owner* is higher leverage than using them as the general scribe. PM-B writing the journey draft builds their business fluency through the review loop. This turns a weakness ("PM-B still learning the business") into a development plan.

### Change 2 — Replace the epic list with a **Three-Lane Outcome Roadmap**

Delete the current roadmap-as-list. Replace it with a roadmap that honors the reality that we are running three systems at once:

```
                    Now (this quarter)        Next (next quarter)      Later (2+ quarters)
                    ──────────────────        ───────────────────      ───────────────────
Legacy sunset       Outcome L1                Outcome L2                —
  lane                • Metric: X → Y           • Metric: X → Y

S2 remediation      Outcome S1                 —                        —
  lane (pilot)        • Metric: X → Y

S2.1 build lane     Outcome N1                Outcome N3                Outcome N5
                      • Metric: X → Y           • Metric: X → Y           • Metric: X → Y
                    Outcome N2                Outcome N4
                      • Metric: X → Y           • Metric: X → Y
```

**Why three lanes, not one:** with only 4 engineers and three systems, pretending it is all "the S2.1 roadmap" hides where capacity actually goes. An explicit lane for legacy sunset and an explicit lane for keeping the S2 pilot client stable force us to budget honestly. They also make it impossible for stakeholders to ask "why is S2.1 slow" without seeing the answer: we spent X% of capacity keeping the old systems alive.

**Rules:**
- At most 5 outcomes in flight across all lanes. We have 4 engineers. More than 5 is a lie.
- Every outcome has a single measurable success metric.
- Every epic is stapled to exactly one outcome. If an epic cannot be stapled to an outcome, it is either a new outcome or it does not get built.
- The roadmap is reviewed monthly, not sprint-by-sprint.
- The **S2 remediation lane must explicitly include the "what S2 taught us" items** from the Experience Vision that are worth fixing for the pilot client now rather than waiting for S2.1. Otherwise we are ignoring our own post-mortem.

**Owner:** PM-A (with Product Director sign-off). PM-B contributes the epic-to-outcome mapping. I contribute the engineering feasibility checkpoint and own the legacy sunset lane's technical side.

### Change 3 — Establish a coordination spine between the two teams

Without changing team structure, introduce a thin connective tissue so the two squads build toward one coherent S2.1 — and so that the architectural drift that happened in S2 does not happen again on my watch:

1. **Weekly 30-minute architecture sync.** Attendees: me + both senior engineers. Agenda: cross-team seams in S2.1, upcoming stories that touch both surfaces, any ADR in flight, any S2 remediation work that affects S2.1 direction. No junior engineers by default — respect their focus time, bring them in for specific topics.
2. **One shared architecture doc** (owned by me, contributed to by both seniors). One page of "how S2.1 fits together," updated when things change. Includes an explicit "where we differ from S2 and why" section, so the architectural deltas are legible.
3. **ADRs in the repo** for any decision that affects both teams. Lightweight — one page each. **This is the specific mechanism that would have caught S2's misalignment early.** I enforce this as a reviewer on PRs that introduce cross-team changes without one. Every ADR must name the business rule or outcome it is serving — if it can't, that's a signal we are making S2's mistake again.
4. **Joint backlog refinement, every two weeks**, 60 minutes. Both teams, both PMs, me. Agenda: next sprint's stories, dependencies between teams, acceptance criteria clarity, and an explicit check for each story: "does this map to a business rule or outcome in the Experience Vision?"
5. **Definition of Ready + Definition of Done**, posted in the repo, enforced in refinement. The DoR must include "traces to an outcome and to at least one business rule from the Experience Vision." This is the single biggest lever for getting the juniors productive faster and for preventing requirements drift.

---

## 5. Role Realignment — What Changes for Each Person

| Person | Stops | Starts | Keeps |
|---|---|---|---|
| **Product Director** | Being the implicit source of business context for every decision | Reviewing the Experience Vision and Outcome Roadmap in scheduled async sessions | Final approval on strategic direction and outcome priority |
| **PM-A** | Writing epic-level tickets as the primary artifact | Owning the Outcome Roadmap *and* the Business Rules / Domain Invariants section of the Experience Vision; being the business translator for PM-B; leading the pilot client interview | Customer and stakeholder relationships |
| **PM-B** | Working ticket-by-ticket without a shared target | Co-drafting the Experience Vision with me; writing the 1-page PRD per epic; shadowing PM-A in the pilot client interview | Close collaboration with engineering |
| **Engineering Director** | Being expected to drive technical vision (they shouldn't) | Acting as air cover for this process change and unblocking people issues; sponsoring the S2 post-mortem so it stays blameless | Career growth, hiring, people management |
| **Me (EM)** | Carrying the end-to-end picture in my head | Owning the cross-team architecture doc, the ADR discipline, and the weekly architecture sync; co-authoring the Experience Vision; owning the S2.1 system context diagram | Cross-team architecture judgment |
| **Senior engineers** | Rebuilding context every sprint | **Owning the "What S2 Taught Us" section of the Experience Vision**; participating in weekly architecture sync; contributing ADRs; mentoring juniors against a shared target | Technical leadership within their team |
| **Junior engineers** | Guessing at intent | Reading the Experience Vision and Outcome Roadmap at the start of every epic; asking "which outcome and which business rule does this serve?" in refinement | Focus on execution quality |

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

### Days 1–14 — Earn the right, mine the evidence
- **Week 1:** I pitch this doc. Get Product Director + Engineering Director buy-in. Lock PM-A and PM-B time for Week 2. Schedule the pilot client interview for Week 2.
- **Week 1:** Each senior engineer writes a one-page "What S2 Taught Us" draft — blameless, architectural, focused on where boundaries or assumptions were wrong. This is 90 minutes of work each, not a project.
- **Week 2:** Legacy system observation (me + PM-B shadow an operations user, 1 hour). Pilot client interview (PM-A + me, 45 min, recorded). PM-B and I draft the Experience Vision in 3 working sessions, 2 hours each, using the senior engineers' S2 lessons and the interview/observation notes as source material.
- **Deliverable by end of Week 2:** a reviewable draft of the Experience Vision that includes the three states (legacy / S2 / S2.1 target), the business rules section (stub for PM-A to complete), the "What S2 Taught Us" section, and the S2.1 system context diagram.

### Days 15–30 — Anchor the process
- **Week 3:** PM-A completes the Business Rules / Domain Invariants section. Review the full Experience Vision with seniors, Eng Director. One async review round with Product Director.
- **Week 3:** PM-A drafts the Three-Lane Outcome Roadmap from the approved Experience Vision. I review for feasibility and own the legacy sunset lane's technical shape.
- **Week 4:** Restructure current S2.1 epics onto the Outcome Roadmap. Kill or defer any epic that doesn't ladder to an outcome or serve a business rule. Identify which S2 remediation items are worth doing now for the pilot client and put them in the S2 lane. Publish the Definition of Ready and Definition of Done.
- **Deliverable by end of Day 30:** Experience Vision, Three-Lane Outcome Roadmap, DoR/DoD, all in the repo.

### Days 31–60 — Make the coordination spine real
- Weekly architecture sync starts Week 5, with the "where we differ from S2 and why" section of the shared architecture doc as the first artifact.
- First joint backlog refinement under the new DoR, Week 5. Every story must trace to an outcome and a business rule.
- First ADRs start appearing, Week 5–6. Each one names the business rule or outcome it serves.
- First cross-team epic refined against the new artifacts, Week 6.
- I publish the shared S2.1 architecture doc, Week 7.
- **Deliverable by end of Day 60:** one full sprint cycle under the new artifacts, with a retro capturing what worked.

### Days 61–90 — Prove the value and tune
- At Day 75, mid-cycle check: are juniors onboarding faster? Are we surfacing fewer cross-team surprises? Is the Three-Lane Outcome Roadmap still honest about capacity split between legacy, S2, and S2.1? Has the pilot client noticed any improvement?
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
| **S2.1 repeats S2's misalignment because requirements work is rushed or skipped** | **High** | **This is the whole reason for the pitch. The two-week Experience Vision drafting is explicitly a gate: no new S2.1 architectural decisions during that window without tracing to a draft outcome or rule.** |
| **S2 pilot client is destabilized by S2.1 work** | Medium | S2 remediation is its own roadmap lane with explicit capacity. Any S2.1 change that touches shared S2 infrastructure requires an ADR. Pilot client gets a heads-up before meaningful changes. |
| **Legacy sunset work gets starved because S2.1 is "shinier"** | Medium | Legacy sunset is its own roadmap lane with named outcomes. Monthly roadmap review checks the capacity split is honest. |
| **Senior engineers' "What S2 Taught Us" section becomes a blame doc** | Medium | Frame explicitly as blameless, architectural-lessons-only. Eng Director sponsors the section. S2 is a team outcome, not an individual failure. Focus on "what we would do differently" not "who was wrong." |
| **Disagreement between seniors on what to keep vs. rebuild from S2** | Medium | The weekly architecture sync is exactly where this gets resolved. Captured as ADRs. If irreconcilable, escalate to me or to an architecture review with the Product Director. |
| Product Director cannot engage even async | High | Structure their review as a single 30-min session with pre-read focused on outcomes and business rules (not epics). Make PM-A the delegated decision-maker between those sessions. |
| Pilot client is reluctant to be interviewed | Low | Frame it as "we want to make your experience better and we want your input on what matters." 45 minutes. Come with specific questions, not open-ended ones. |
| PM-B feels demoted by being "the scribe" | Medium | Frame it explicitly as a growth opportunity and leverage play, not a downgrade. They are co-author, not note-taker. Shadowing the pilot client interview is a concrete investment in their business fluency. |
| We create artifacts no one uses | Medium | Start with ONE artifact (Experience Vision) and earn the right to introduce the next. Do not ship all three changes on Day 1. |
| Eng Director worries this bypasses them | Medium | Brief them privately first. Explicitly position them as air cover and sponsor of the change. Ask for their help specifically on keeping the S2 post-mortem blameless. |
| Teams resent new process | Medium | Kill any ritual the retro says is not pulling its weight. Keep DoR/DoD as the non-negotiable core. |
| Senior engineers see the architecture sync as extra meeting | Low | 30 minutes, fixed agenda, cancel when empty. Frame it as "the meeting that prevents the next S2." |

---

## 10. Why This Works for *Our* Shape Specifically

- **1 Product Director shared across products** → we move them from real-time bottleneck to async reviewer. They sign off on vision, rules, and outcomes — not epics.
- **PM-A strong on business / PM-B sharp on execution** → we split them by strength. PM-A owns the Outcome Roadmap and the Business Rules section (their highest-leverage contribution); PM-B owns the execution-side artifacts and builds business fluency through the review loop and the pilot client interview.
- **EM with cross-team architecture capability (me)** → I become the deliberate owner of the connective tissue between the two teams, which is the single biggest gap today. This is the role I am already partly filling informally; this pitch just makes it explicit. It is also the role that was *missing* in S2, and the one that would have caught the misalignment if it had existed.
- **People-focused Engineering Director** → they get a role that matches their strengths (air cover, people unblock, sponsor of the blameless post-mortem) rather than being expected to drive technical vision they are not positioned to drive.
- **Two squads of sr + jr** → juniors get a shared artifact to learn from; seniors stop rebuilding context and get their hard-won S2 knowledge treated as first-class authored material (not lore); the weekly arch sync is small enough to be high-signal.
- **S2 already happened** → unlike a greenfield effort, we don't have to argue hypothetically about whether this process matters. S2 is the evidence. The pitch is not "we should adopt best practices," it's "we already paid tuition for this lesson — let's not pay it twice."

---

## 11. The Opening Line of the Pitch (ready to say out loud)

> "S2 was built engineering-led without clear business requirements, and we are all living with the architectural misalignment that came from it. S2.1 is supposed to fix that — but the business requirements are still unclear, and we are deep into epic work. I don't want us to pay S2's tuition twice. I'm proposing three lightweight artifacts and one weekly ritual, owned by specific people, and I'd like two weeks to produce the first one — an end-to-end Experience Vision for S2.1 — so we can decide together whether the rest is worth adopting."

That framing is important:
- It names a problem everyone already feels, using the word "S2" that everyone knows.
- It is not a criticism of anyone — it is a claim that the *system* needs a different artifact layer.
- It asks for a small, reversible commitment (two weeks, one artifact).
- It offers a decision point, not a mandate.
- It positions this as collaborative, not a power grab.
- It turns the failure of S2 into the strongest possible argument, without blaming anyone for it.

---

## 12. Appendix — Skeleton of the Experience Vision Artifact (S2.1 edition)

Use this as the outline when PM-B and I draft it in Week 2. Target 6–8 pages.

```
1. Who we serve
   - Persona 1: <name, role, what they care about — e.g. operations user>
   - Persona 2: <name, role — e.g. pilot client settlement operator>
   - Persona 3: <if needed — e.g. internal finance/compliance reviewer>

2. The job to be done
   - When <situation>, they want to <motivation>, so they can <outcome>.
   - Keep this single-paragraph. If you need more than a paragraph,
     you probably have two jobs and should split them.

3. Legacy current-state journey
   - Step-by-step journey AS THE LEGACY SYSTEM RUNS IT TODAY
   - Pain points called out in-line
   - Sourced from: legacy system observation + PM-A's existing knowledge
   - This exists so S2.1 does not accidentally break capabilities
     that legacy quietly handles correctly today.

4. S2 current-state journey (pilot client)
   - Step-by-step journey AS S2 RUNS IT TODAY FOR THE PILOT
   - Where the architectural misalignment shows up as user pain
   - Sourced from: pilot client interview + senior engineers' observations
   - This is the "we already paid tuition" evidence.

5. What S2 taught us (blameless architectural lessons)
   - Business assumptions that turned out to be wrong
   - Boundaries we drew in the wrong place
   - What we would do differently in S2.1
   - Owned by: senior engineers
   - Framed as "what the next system should know" not "what went wrong"

6. S2.1 target-state journey (2–4 quarters out)
   - Same journey, with legacy pain AND S2 misalignment both removed
   - What the user notices that is different
   - What the system does differently
   - Sourced from: synthesis of 3 + 4 + 5

7. S2.1 system context diagram
   - Boxes: services, shared data stores, external integrations
   - Lines: data/control flow
   - Dotted boundary: which team owns what
   - Annotations: "where we differ from S2 and why"

8. Business rules / domain invariants  [OWNED BY PM-A]
   - The non-negotiable settlement rules the system must honor
   - Reconciliation, timing, correctness, audit, money movement,
     regulatory/compliance, tenancy, whatever the domain demands
   - Each rule numbered so stories and ADRs can reference them
     (e.g. "BR-07: settlements must be reversible within 24h")
   - THIS IS THE SECTION WHOSE ABSENCE CAUSED S2'S DRIFT.
     Treat it as load-bearing.

9. Outcomes that bridge current → target
   - Outcome 1: <measurable metric>
   - Outcome 2: <measurable metric>
   - Outcome 3: <measurable metric>
   - (Cap at 5, spread across the three roadmap lanes)

10. Explicit non-goals
    - What we are deliberately not doing in this horizon
    - Especially: what S2 does that S2.1 will deliberately NOT try
      to preserve (and why)
```

Keep the whole thing under 8 pages. If it is longer, it will not be read, and unread artifacts create more confusion than they resolve.

One closing note: the business rules section (#8) is the single most valuable page in the document. If the pitch succeeds at producing *only* that one page and nothing else, S2.1 will still be in a meaningfully better place than it is today.
