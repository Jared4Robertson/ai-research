# Pitch: One Artifact to Align S2.1

> **Format:** Walk into the room with this page. Say it in 15 minutes. Leave the depth material in the repo for anyone who wants it.

---

## The problem

S2 was built engineering-led without clear business requirements. The architectural misalignment we live with today is the direct result.

S2.1 is supposed to fix that — but the business requirements are still unclear. We are deep into epic work with no shared picture of the end-to-end settlement experience. Nobody can point at a single artifact and say "this is what we're building and why."

We already paid this tuition once. I don't want us to pay it twice.

---

## One change

We create an **Experience Vision** — a short, living document that captures what we're building, in one place, for the first time.

It has four sections, each owned by someone specific:

| Section | What it captures | Owner | Effort |
|---|---|---|---|
| **Current-State Journey** | What settlement looks like today across legacy and S2 — the real workflow, not the imagined one | PM-B + EM | Observation + interview in Week 2 |
| **Business Rules** | The non-negotiable rules settlement must honor — reconciliation, timing, correctness, audit. Numbered so we can reference them in stories. | PM-A | 2–3 working sessions |
| **What S2 Taught Us** | Blameless architectural lessons — which assumptions were wrong, which boundaries were in the wrong place | Senior Engineers | 90 min each, Week 1 |
| **S2.1 Target State** | The same journey with the pain removed. What the user sees. What the system does differently. | PM-B + EM (synthesized from the above) | Drafted in Week 2 |

**Target length:** 3–4 pages. Readable in one sitting.

---

## The ask

Two weeks. PM-B and I draft it. PM-A fills in the business rules. Each senior engineer writes up S2's lessons. Product Director reviews in one 30-minute session.

At the end of two weeks, we have a reviewable draft. Then we decide together — as a group — whether it's useful and what comes next.

---

## What this gives us that we don't have today

- A shared picture of the end-to-end settlement experience that any team member can point at.
- Business rules written down so architecture decisions can trace back to them — the specific thing S2 lacked.
- S2's hard-won lessons captured as authored material instead of undocumented lore.
- A foundation to restructure our roadmap and epics against, if the group decides to.

---

## What this does *not* do

This is not a process overhaul. It is one document, built in two weeks, with a decision point at the end.

If it proves useful, I have ideas for what comes next (restructuring the roadmap, formalizing coordination between the two teams). But those earn their way in — they are not part of this ask.

---

## Anticipated questions

**"Don't we already know this stuff?"**
Some of us know pieces. Nobody has the full picture, and none of it is written down. Every sprint we reconstruct it in our heads. That's how S2 drifted.

**"Can we afford two weeks?"**
Building without a shared picture is how S2 happened. Two weeks of clarity now prevents months of rework later. And delivery doesn't stop — the seniors and juniors keep shipping during the drafting week.

**"Who decided the EM should drive this?"**
I'm not deciding product direction. PM-A owns business rules, PM-B co-authors the journey, seniors own the lessons, Product Director approves. I'm offering to do the coordination work because I have the cross-team architecture view and this is a gap I see daily.

---

> **Depth material** (in the repo, not in this pitch):
> - [`small-team-pitch-end-to-end-vision.md`](./small-team-pitch-end-to-end-vision.md) — full playbook with role realignment, 30/60/90 plan, risk table, Phase 2 changes
> - [`scrum-artifacts-for-epics-stories-tasks.md`](./scrum-artifacts-for-epics-stories-tasks.md) — general reference on scrum artifacts
> - [`questions-each-artifact-answers.md`](./questions-each-artifact-answers.md) — diagnostic: what question does each artifact answer?
