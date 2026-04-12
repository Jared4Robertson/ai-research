# Legacy System Replacement: The Question Chain

A step-by-step sequence of simple questions that walks a team from "we need to replace a legacy system" to well-defined epics, stories, and tasks. Each question has a clear expected answer format, and each answer feeds the next question.

---

## 1. Goal

### Q1: What is the goal of this project?

- Answer in one sentence: "We are building S2 to _____."
- This is the filter for every question that follows. If an answer doesn't move toward this goal, it's noise.

**Expected answer:** A single sentence.

---

## 2. Orient

### Q2: What does the current system do?

- Answer in one sentence: "The settlement system does _____ for _____."
- If different people give different one-sentence answers, that's your first red flag.

**Expected answer:** A single sentence.

---

## 3. People

### Q3: What roles directly use the system?

- List every role title that interacts with the system — e.g. settlement analyst, operations manager, client support rep.
- Roles, not individual names. Each role represents a distinct way someone uses the system.

**Expected answer:** A list of role titles.

### Q4: For each role, what are they trying to accomplish with the system?

- One sentence per role: "[Role] uses the system to _____."
- Stay at the goal level, not the step-by-step level. "Process daily settlements" not "click the reconcile button then export the CSV."

**Expected answer:** A list of role + goal pairs.

### Q5: Who depends on the system's results but doesn't use it directly?

- These are stakeholders — e.g. compliance officer, finance director, client relationship manager.
- They care about outcomes (accuracy, timeliness, compliance) but don't log in.

**Expected answer:** A list of role titles.

---

## 4. Value

### Q6: What would happen if this system stopped working tomorrow?

- What breaks first? What breaks worst?
- Which roles from Q3–Q5 are impacted, and how?
- What would people have to do manually as a workaround?
- What consequences would reach customers, regulators, or the business's bottom line?

**Expected answer:** A list of concrete consequences, naturally sorted by severity.

**Why this matters:** The things that would break worst are the things the replacement must get right first. The things nobody would miss are candidates to drop. This answer becomes your priority map.

---

## 5. Pain

### Q7: Why are we replacing this system instead of just keeping it?

- What can't the current system do that the business needs it to do?
- What is it costing us — in time, money, risk, or missed opportunity?
- What workarounds have people built around its limitations?
- Where is it fragile, slow, or error-prone?

**Expected answer:** A list of specific limitations and their business impact.

**Why this matters:** This is the business case for the replacement. If the answers are vague ("it's old," "it's legacy"), the team doesn't actually understand *why* they're rebuilding — and that's how you end up with a new system that has new problems instead of fewer problems.

---

## 6. Current Workflows

### Q8: For each role, what are the steps they go through in the system to accomplish their goal?

- Take the role + goal pairs from Q4 and walk through each one: "First they _____, then they _____, then they _____."
- Include the ugly parts — manual workarounds, waiting on other people, exporting to spreadsheets, copy-pasting between systems.
- Note where different roles' workflows overlap or hand off to each other.

**Expected answer:** A step-by-step workflow per role, in plain language.

**Why this matters:** This is the ground truth of how the system actually works — not how it was designed to work, not how the docs say it works, but what people actually do. The vision (Q9) can only be specific if it has these workflows to push against.

---

## 7. Rules

### Q9: What are the business rules that any settlement system must follow, regardless of how it's built?

- These are rules of the business, not rules of the software.
- Things like: "settlements must reconcile within 24 hours" or "every transaction must have an audit trail."
- The test: if a rule would still be true even if you did everything on paper and spreadsheets, it belongs here.
- Number each rule so they can be referenced later in stories and technical decisions (e.g. BR-01, BR-02).

**Expected answer:** A numbered list of non-negotiable rules.

**Why this matters:** These rules exist whether you document them or not. If engineering doesn't know them, they make architecture decisions that fight the domain — and that's exactly what happened with S2.

---

## 8. Vision

### Q10: What should the new system make possible that the current one can't?

- Not a technology wish list. Not "microservices" or "cloud-native."
- Answer in terms of what changes for the roles from Q3–Q5: what can they do that they couldn't before?
- Which painful steps from Q8 should disappear, get faster, or get automated?
- What business outcomes become achievable that aren't today?
- The vision must respect the rules from Q9 — if a proposed capability violates a business rule, it needs to be rethought.

**Expected answer:** A short list of concrete capabilities or outcomes, tied to the pain from Q7, the workflows from Q8, and bounded by the rules from Q9.

**Why this matters:** This is the product vision — grounded in real pain, real workflows, and real constraints. If a proposed capability doesn't trace back to a pain from Q7 or a step from Q8, it's scope creep before you've even started.
